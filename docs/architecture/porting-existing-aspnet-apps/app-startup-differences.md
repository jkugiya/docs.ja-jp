---
title: ASP.NET MVC と ASP.NET Core のアプリの起動の違い
description: ASP.NET MVC と ASP.NET Core は、アプリの起動時に大きく異なります。 重要な違いと、ASP.NET MVC から ASP.NET Core に移行する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: eaf8d8fac42ddebbb944273b672666e0bd2b1a67
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401419"
---
# <a name="app-startup-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core のアプリの起動の違い

ASP.NET MVC アプリは、Windows オペレーティングシステムで使用できるプライマリ web サーバーであるインターネットインフォメーションサーバー (IIS) 内で完全に有効期間があります。 ASP.NET MVC とは異なり、ASP.NET Core アプリは実行可能アプリです。 これらは、を使用してコマンドラインから実行でき `dotnet run` ます。 これらのメソッドには、すべての C# プログラムと同様に、通常 `public static void Main()` は同様のバリエーション (引数やサポートなど) が含まれてい `async` ます。 これは、ASP.NET Core MVC と ASP.NET MVC の間で最も大きなアーキテクチャの違いであり、Windows 以外のシステムでの ASP.NET Core の実行を可能にするいくつかの違いの1つです。

## <a name="aspnet-mvc-startup"></a>ASP.NET MVC のスタートアップ

IIS 内でホストされる ASP.NET アプリでは、特定のオブジェクトをインスタンス化し、要求が到着したときに特定のメソッドを呼び出すために IIS に依存しています。 ASP.NET は、から派生した *global.asax* ファイルのクラスのインスタンスを作成し `HttpApplication` ます。 最初の要求を受信すると、要求自体を処理する前に、ASP.NET が `Application_Start` *global.asax* ファイルのクラスのメソッドを呼び出します。 ASP.NET MVC アプリの開始時に実行する必要のあるロジックは、このメソッドに追加できます。

ASP.NET MVC および Web API 用の多くの NuGet パッケージでは、 [Webactivator](https://github.com/davidebbo/WebActivator) パッケージを使用して、アプリの起動時に一部のコードを実行できるようにします。 慣例により、このコードは通常、 *App_Start* フォルダーに追加されます。属性を使用して構成され、の直前または直後に実行され `Application_Start` ます。

また、 [ASP.NET MVC で Open Web Interface for .net (OWIN) および Project Katana](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)を使用することもできます。 この場合、アプリには、ASP.NET Core の動作と非常によく似た方法で要求ミドルウェアを設定する *Startup.cs* ファイルが含まれます。

ASP.NET MVC アプリの起動時にコードを実行する必要がある場合は、通常、次のいずれかの方法を使用します。

## <a name="aspnet-core-startup"></a>ASP.NET Core スタートアップ

前述のように、ASP.NET Core アプリはスタンドアロンプログラムです。 そのため、通常はアプリのエントリポイントを含む *Program.cs* ファイルが含まれます。 このファイルの典型的な例を図2-1 に示します。

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

**(図 2-1)** 。 一般的な ASP.NET Core *Program.cs* ファイル。

図2-1 に示すコードでは、アプリの *ホスト* を作成し、ビルドして実行します。 ASP.NET Core アプリは、表示されたによって構成されるホスト内で実行され `IHostBuilder` ます。 を使用して ASP.NET Core アプリを完全に構成することもできますが、 `IHostBuilder` 通常、この作業の大部分はクラスで行われ `Startup` ます。

クラスは、 `Startup` ホストとの2つのメソッドを公開します。 `ConfigureServices` `Configure` `ConfigureServices`メソッドは、アプリが使用するサービスと、それぞれの有効期間を定義するために使用されます。 メソッドを使用して、ミドルウェアで構成される `Configure` 要求パイプラインを設定することによって、アプリへの各要求を処理する方法を定義します。

アプリのサービスまたは要求パイプラインの構成に関連するコードに加えて、アプリの開始時に実行する必要のある他のコードが含まれている場合もあります。 通常、このようなコードは *Program.cs* に配置されるか、として登録され `IHostedService` ます。これは、アプリの起動時に [汎用ホスト](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1) によって開始されます。

インターフェイスは、 `IHostedService` とという2つのメソッドを公開し `StartAsync` `StopAsync` ます。 インターフェイスをに登録し、 `ConfigureServices` ホストが残りの部分を実行して、 `StartAsync` アプリが起動する前にメソッドを呼び出します。

## <a name="porting-considerations"></a>移植に関する考慮事項

アプリを ASP.NET MVC から ASP.NET Core に移行することを検討しているチームは、アプリの起動時に実行されているコードを特定し、ASP.NET Core アプリでそのようなコードの適切な場所を決定する必要があります。 アプリの起動時に実行する必要があるカスタムコード (特に非同期コード) については、通常、このようなコードを実装に配置することをお勧めし `IHostedService` ます。

## <a name="references"></a>関連項目

- [IIS 7 の ASP.NET アプリケーションライフサイクルの概要](/previous-versions/aspnet/bb470252(v=vs.100))
- [IIS 5 および6の ASP.NET アプリケーションライフサイクルの概要](/previous-versions/aspnet/ms178473(v=vs.100))
- [OWIN と Katana の概要](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)
- [WebActivator](https://github.com/davidebbo/WebActivator)
- [ASP.NET Core でのアプリの起動](/aspnet/core/fundamentals/startup?preserve-view=true&view=aspnetcore-3.1)
- [ASP.NET Core の .NET 汎用ホスト](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1)
- [IHostedService](../microservices/multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)

>[!div class="step-by-step"]
>[前へ](architectural-differences.md)
>[次へ](hosting-differences.md)
