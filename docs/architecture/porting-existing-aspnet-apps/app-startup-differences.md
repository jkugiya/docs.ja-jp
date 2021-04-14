---
title: ASP.NET MVC と ASP.NET Core のアプリの起動の相違点
description: ASP.NET MVC と ASP.NET Core では、アプリの起動方法が大きく異なります。 重要な相違点と、ASP.NET MVC から ASP.NET Core に移行する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: eaf8d8fac42ddebbb944273b672666e0bd2b1a67
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401419"
---
# <a name="app-startup-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core のアプリの起動の相違点

ASP.NET MVC アプリは、Windows オペレーティング システムで使用できるプライマリ Web サーバーであるインターネット インフォメーション サーバー (IIS) 内に存在していました。 ASP.NET MVC とは異なり、ASP.NET Core アプリは実行可能なアプリです。 これらは、`dotnet run` を使用してコマンド ラインから実行できます。 これらには、すべての C# プログラムと同様にエントリ ポイント メソッド (通常は `public static void Main()` または同様のバリエーション (多くの場合、引数や `async` のサポートを使用)) があります。 これがおそらく ASP.NET Core と ASP.NET MVC における最も大きなアーキテクチャの違いであり、Windows 以外のシステムで ASP.NET Core の実行を可能にするいくつかの違いのうちの 1 つです。

## <a name="aspnet-mvc-startup"></a>ASP.NET MVC の起動

IIS 内でホストされる ASP.NET アプリは、IIS を使用して特定のオブジェクトのインスタンスを作成し、要求が届いたときに特定のメソッドを呼び出します。 ASP.NET は、*Global.asax* ファイルのクラスのインスタンスを作成します。これは `HttpApplication` から派生します。 最初の要求を受け取ると、その要求自体を処理する前に、ASP.NET は *Global.asax* ファイルのクラス内の `Application_Start` メソッドを呼び出します。 ASP.NET MVC アプリの開始時に実行する必要のあるロジックをこのメソッドに追加できます。

ASP.NET MVC および Web API 用の多くの NuGet パッケージでは、[WebActivator](https://github.com/davidebbo/WebActivator) パッケージを使用して、アプリの起動時に一部のコードを実行できるようにします。 規約に従って、このコードは通常 *App_Start* フォルダーに追加され、`Application_Start` の直前または直後に実行するよう属性を使用して構成されます。

また、[ASP.NET MVC で Open Web Interface for .NET (OWIN) とプロジェクト Katana](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana) を使用することもできます。 この場合、アプリには、ASP.NET Core の動作と非常によく似た方法で要求のミドルウェアを設定する *Startup.cs* ファイルが含まれます。

ASP.NET MVC アプリの起動時にコードを実行する必要がある場合、通常はこれらのいずれかの方法を使用します。

## <a name="aspnet-core-startup"></a>ASP.NET Core の起動

前述のとおり、ASP.NET Core アプリはスタンドアロン プログラムです。 そのため、通常はアプリのエントリ ポイントを格納する *Program.cs* ファイルが含まれます。 図 2-1 は、このファイルの一般的な例を示しています。

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

**(図 2-1)** 。 一般的な ASP.NET Core の *Program.cs* ファイル。

図 2-1 に示すコードでは、アプリの "*ホスト*" を作成し、ビルドして実行します。 ASP.NET Core アプリは、表示されている `IHostBuilder` で構成されたホスト内で実行されます。 `IHostBuilder` を使用して ASP.NET Core アプリを完全に構成することもできますが、通常、この処理の大部分は `Startup` クラスで実行されます。

`Startup` クラスは、ホストに対して 2 つのメソッド (`ConfigureServices` および `Configure`) を公開します。 `ConfigureServices` メソッドは、アプリが使用するサービスと、それぞれの有効期間を定義するために使用されます。 `Configure` メソッドは、ミドルウェアで構成される要求パイプラインを設定することによって、アプリに対する各要求を処理する方法を定義するために使用されます。

アプリのサービスまたは要求パイプラインの構成に関連するコードに加えて、アプリの開始時に実行する必要のある他のコードがアプリに含まれている場合もあります。 通常、このようなコードは *Program.cs* に配置されるか、`IHostedService` として登録されます。これは、アプリの起動時に[汎用ホスト](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1)によって開始されます。

`IHostedService` インターフェイスは 2 つのメソッド (`StartAsync` および `StopAsync`) を公開します。 このインターフェイスを `ConfigureServices` に登録し、ホストが残りの部分を実行して、アプリの起動前に `StartAsync` メソッドを呼び出します。

## <a name="porting-considerations"></a>移植に関する考慮事項

アプリを ASP.NET MVC から ASP.NET Core に移行することを検討しているチームは、アプリの起動時に実行されるコードを特定し、ASP.NET Core アプリでのそのコードに適した場所を決定する必要があります。 通常、アプリの起動時に実行する必要のあるカスタム コード (特に非同期コード) は、`IHostedService` の実装に配置することをお勧めします。

## <a name="references"></a>リファレンス

- [IIS 7 の ASP.NET アプリケーション ライフ サイクルの概要](/previous-versions/aspnet/bb470252(v=vs.100))
- [IIS 5 および 6 の ASP.NET アプリケーション ライフ サイクルの概要](/previous-versions/aspnet/ms178473(v=vs.100))
- [OWIN と Katana の概要](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)
- [WebActivator](https://github.com/davidebbo/WebActivator)
- [ASP.NET Core でのアプリケーションのスタートアップ](/aspnet/core/fundamentals/startup?preserve-view=true&view=aspnetcore-3.1)
- [ASP.NET Core の .NET 汎用ホスト](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1)
- [IHostedService](../microservices/multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)

>[!div class="step-by-step"]
>[前へ](architectural-differences.md)
>[次へ](hosting-differences.md)
