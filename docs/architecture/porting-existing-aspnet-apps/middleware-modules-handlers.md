---
title: ミドルウェアとモジュールおよびハンドラーの比較
description: このセクションでは、ハンドラーとモジュールを使用する ASP.NET アプリと、要求処理パイプライン用にミドルウェアを定義する ASP.NET Core アプリ間の構造の違いについて説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 3bc3c30a1ee988550cca907d7289583161337cb9
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122873"
---
# <a name="compare-middleware-to-modules-and-handlers"></a>ミドルウェアとモジュールおよびハンドラーの比較

既存の ASP.NET MVC アプリや Web API アプリで OWIN/Katana を使用している方はおそらく、ミドルウェアの概念と、それを ASP.NET Core に移植するのは非常に簡単であることを既によくご存知でしょう。 しかし、ほとんどの ASP.NET アプリでは、ミドルウェアではなく HTTP モジュールと HTTP ハンドラーが使用されています。 これらを ASP.NET Core に移行するには、追加の作業が必要になります。

## <a name="aspnet-modules-and-handlers"></a>ASP.NET のモジュールとハンドラー

[HTTP モジュールと HTTP ハンドラー](/troubleshoot/aspnet/http-modules-handlers)は、ASP.NET アーキテクチャに不可欠な部分です。 要求が処理されている間、各要求は複数の HTTP モジュール (たとえば、認証モジュールとセッション モジュール) によって処理され、その後、1 つの HTTP ハンドラーによって処理されます。 ハンドラーが要求を処理した後、要求は HTTP モジュールを経由して戻されます。

アプリでカスタムの HTTP モジュールまたは HTTP ハンドラーを使用している場合は、それらを ASP.NET Core に移行するための計画が必要になります。 ASP.NET Core での最も有力な代替候補となるのは、ミドルウェアです。

## <a name="aspnet-core-middleware"></a>ASP.NET Core のミドルウェア

ASP.NET Core では、各アプリの `Configure` メソッド内で要求パイプラインが定義されます。 この要求パイプラインでは、アプリでの受信要求の処理方法が定義されます。パイプライン内の各メソッドは、最終的に 1 つのメソッドが終了し、"*ミドルウェア*" のチェーンが終了してスタックの上位に戻るまで、次のメソッドを呼び出します。 ミドルウェアはすべての要求をターゲットにすることも、要求されたパスまたはその他の要素に基づいて特定の要求のみにマップするように構成することもできます。 アプリの `Configure` メソッド内に完全に構成することも、別のクラスに実装することもできます。

HTTP モジュールを使用する ASP.NET MVC アプリでの動作は、おそらく[カスタム ミドルウェア](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)に最も適しています。 カスタム HTTP ハンドラーは、同じパスに応答するカスタムのルートまたはエンドポイントに置き換えることができます。

## <a name="accessing-httpcontext"></a>HttpContext へのアクセス

多くの .NET アプリでは、`HttpContext.Current` を使用して現在の要求のコンテキストを参照します。 この静的アクセスは、個々の要求以外での、テストやその他のコード使用に関する問題の一般的な原因になる可能性があります。 ASP.NET Core アプリを構築する場合、現在の HttpContext へのアクセスは、次のサンプルで示すように、ミドルウェアでメソッド パラメーターとして提供される必要があります。

```csharp
public class Middleware
{
    private readonly RequestDelegate _next;

    public Middleware(RequestDelegate next)
    {
        _next = next;
    }

    public Task Invoke(HttpContext httpContext)
    {
        return _next(httpContext);
    }
}
```

同様に、ASP.NET Core フィルターでは、コンテキスト引数がメソッドに渡され、そこから現在の HttpContext にアクセスできます。

```csharp
public class MyActionFilterAttribute : ActionFilterAttribute
{
    public override void OnResultExecuting(ResultExecutingContext context)
    {
        var headers = context.HttpContext.Request.Headers;
        // do something based on a header

        base.OnResultExecuting(context);
    }
}
```

HttpContext へのアクセスを必要とするコンポーネントまたはサービスがある場合は、`HttpContext.Current` のような静的呼び出しを使用するのではなく、代わりにコンストラクターの依存関係の挿入と [IHttpContextAccessor](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.http.ihttpcontextaccessor) インターフェイスを使用する必要があります。

```csharp
public class MyService
{
    private readonly IHttpContextAccessor _httpContextAccessor;

    public MyService(IHttpContextAccessor httpContextAccessor)
    {
        _httpContextAccessor = httpContextAccessor;
    }

    public void DoSomething()
    {
        var currentContext = _httpContextAccessor.HttpContext;
    }
}
```

このアプローチによって、メソッドから現在のコンテキストへの静的な結合を排除しつつ、テスト可能な方法でアクセスが提供されます。

## <a name="references"></a>References

- [ASP.NET HTTP モジュールと HTTP ハンドラー](/troubleshoot/aspnet/http-modules-handlers)
- [ASP.NET Core のミドルウェア](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
>[前へ](dependency-injection-differences.md)
>[次へ](configuration-differences.md)
