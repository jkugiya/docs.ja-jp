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
# <a name="app-startup-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="63a29-104">ASP.NET MVC と ASP.NET Core のアプリの起動の相違点</span><span class="sxs-lookup"><span data-stu-id="63a29-104">App startup differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="63a29-105">ASP.NET MVC アプリは、Windows オペレーティング システムで使用できるプライマリ Web サーバーであるインターネット インフォメーション サーバー (IIS) 内に存在していました。</span><span class="sxs-lookup"><span data-stu-id="63a29-105">ASP.NET MVC apps lived entirely within Internet Information Server (IIS), the primary web server available on Windows operating systems.</span></span> <span data-ttu-id="63a29-106">ASP.NET MVC とは異なり、ASP.NET Core アプリは実行可能なアプリです。</span><span class="sxs-lookup"><span data-stu-id="63a29-106">Unlike ASP.NET MVC, ASP.NET Core apps are executable apps.</span></span> <span data-ttu-id="63a29-107">これらは、`dotnet run` を使用してコマンド ラインから実行できます。</span><span class="sxs-lookup"><span data-stu-id="63a29-107">You can run them from the command line, using `dotnet run`.</span></span> <span data-ttu-id="63a29-108">これらには、すべての C# プログラムと同様にエントリ ポイント メソッド (通常は `public static void Main()` または同様のバリエーション (多くの場合、引数や `async` のサポートを使用)) があります。</span><span class="sxs-lookup"><span data-stu-id="63a29-108">They have an entry point method like all C# programs, typically `public static void Main()` or a similar variation (perhaps with arguments or `async` support).</span></span> <span data-ttu-id="63a29-109">これがおそらく ASP.NET Core と ASP.NET MVC における最も大きなアーキテクチャの違いであり、Windows 以外のシステムで ASP.NET Core の実行を可能にするいくつかの違いのうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="63a29-109">This is perhaps the biggest architectural difference between ASP.NET Core and ASP.NET MVC, and is one of several differences that allows ASP.NET Core to run on non-Windows systems.</span></span>

## <a name="aspnet-mvc-startup"></a><span data-ttu-id="63a29-110">ASP.NET MVC の起動</span><span class="sxs-lookup"><span data-stu-id="63a29-110">ASP.NET MVC Startup</span></span>

<span data-ttu-id="63a29-111">IIS 内でホストされる ASP.NET アプリは、IIS を使用して特定のオブジェクトのインスタンスを作成し、要求が届いたときに特定のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63a29-111">Hosted within IIS, ASP.NET apps rely on IIS to instantiate certain objects and call certain methods when a request arrives.</span></span> <span data-ttu-id="63a29-112">ASP.NET は、*Global.asax* ファイルのクラスのインスタンスを作成します。これは `HttpApplication` から派生します。</span><span class="sxs-lookup"><span data-stu-id="63a29-112">ASP.NET creates an instance of the *Global.asax* file's class, which derives from `HttpApplication`.</span></span> <span data-ttu-id="63a29-113">最初の要求を受け取ると、その要求自体を処理する前に、ASP.NET は *Global.asax* ファイルのクラス内の `Application_Start` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63a29-113">When the first request is received, before handling the request itself, ASP.NET calls the `Application_Start` method in the *Global.asax* file's class.</span></span> <span data-ttu-id="63a29-114">ASP.NET MVC アプリの開始時に実行する必要のあるロジックをこのメソッドに追加できます。</span><span class="sxs-lookup"><span data-stu-id="63a29-114">Any logic that needs to run when the ASP.NET MVC app begins can be added to this method.</span></span>

<span data-ttu-id="63a29-115">ASP.NET MVC および Web API 用の多くの NuGet パッケージでは、[WebActivator](https://github.com/davidebbo/WebActivator) パッケージを使用して、アプリの起動時に一部のコードを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="63a29-115">Many NuGet packages for ASP.NET MVC and Web API use the [WebActivator](https://github.com/davidebbo/WebActivator) package to let them run some code during app startup.</span></span> <span data-ttu-id="63a29-116">規約に従って、このコードは通常 *App_Start* フォルダーに追加され、`Application_Start` の直前または直後に実行するよう属性を使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="63a29-116">By convention, this code would typically be added to an *App_Start* folder and would be configured via attribute to run either immediately before or just after `Application_Start`.</span></span>

<span data-ttu-id="63a29-117">また、[ASP.NET MVC で Open Web Interface for .NET (OWIN) とプロジェクト Katana](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="63a29-117">It's also possible to use the [Open Web Interface for .NET (OWIN) and Project Katana with ASP.NET MVC](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana).</span></span> <span data-ttu-id="63a29-118">この場合、アプリには、ASP.NET Core の動作と非常によく似た方法で要求のミドルウェアを設定する *Startup.cs* ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="63a29-118">When doing so, the app will include a *Startup.cs* file that is responsible for setting up request middleware in a way that's very similar to how ASP.NET Core behaves.</span></span>

<span data-ttu-id="63a29-119">ASP.NET MVC アプリの起動時にコードを実行する必要がある場合、通常はこれらのいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="63a29-119">If you need to run code when your ASP.NET MVC app starts up, it will typically use one of these approaches.</span></span>

## <a name="aspnet-core-startup"></a><span data-ttu-id="63a29-120">ASP.NET Core の起動</span><span class="sxs-lookup"><span data-stu-id="63a29-120">ASP.NET Core Startup</span></span>

<span data-ttu-id="63a29-121">前述のとおり、ASP.NET Core アプリはスタンドアロン プログラムです。</span><span class="sxs-lookup"><span data-stu-id="63a29-121">As noted previously, ASP.NET Core apps are standalone programs.</span></span> <span data-ttu-id="63a29-122">そのため、通常はアプリのエントリ ポイントを格納する *Program.cs* ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="63a29-122">As such, they typically include a *Program.cs* file containing the entry point for the app.</span></span> <span data-ttu-id="63a29-123">図 2-1 は、このファイルの一般的な例を示しています。</span><span class="sxs-lookup"><span data-stu-id="63a29-123">A typical example of this file is shown in Figure 2-1.</span></span>

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

<span data-ttu-id="63a29-124">**(図 2-1)** 。</span><span class="sxs-lookup"><span data-stu-id="63a29-124">**Figure 2-1**.</span></span> <span data-ttu-id="63a29-125">一般的な ASP.NET Core の *Program.cs* ファイル。</span><span class="sxs-lookup"><span data-stu-id="63a29-125">A typical ASP.NET Core *Program.cs* file.</span></span>

<span data-ttu-id="63a29-126">図 2-1 に示すコードでは、アプリの "*ホスト*" を作成し、ビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="63a29-126">The code shown in Figure 2-1 creates a *host* for the app, builds it, and runs it.</span></span> <span data-ttu-id="63a29-127">ASP.NET Core アプリは、表示されている `IHostBuilder` で構成されたホスト内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="63a29-127">The ASP.NET Core app runs within the host configured by the `IHostBuilder` shown.</span></span> <span data-ttu-id="63a29-128">`IHostBuilder` を使用して ASP.NET Core アプリを完全に構成することもできますが、通常、この処理の大部分は `Startup` クラスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="63a29-128">While it's possible to completely configure an ASP.NET Core app using the `IHostBuilder`, typically the bulk of this work is done in a `Startup` class.</span></span>

<span data-ttu-id="63a29-129">`Startup` クラスは、ホストに対して 2 つのメソッド (`ConfigureServices` および `Configure`) を公開します。</span><span class="sxs-lookup"><span data-stu-id="63a29-129">The `Startup` class exposes two methods to the host: `ConfigureServices` and `Configure`.</span></span> <span data-ttu-id="63a29-130">`ConfigureServices` メソッドは、アプリが使用するサービスと、それぞれの有効期間を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="63a29-130">The `ConfigureServices` method is used to define the services the app will use and their respective lifetimes.</span></span> <span data-ttu-id="63a29-131">`Configure` メソッドは、ミドルウェアで構成される要求パイプラインを設定することによって、アプリに対する各要求を処理する方法を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="63a29-131">The `Configure` method is used to define how each request to the app will be handled by setting up a request pipeline composed of middleware.</span></span>

<span data-ttu-id="63a29-132">アプリのサービスまたは要求パイプラインの構成に関連するコードに加えて、アプリの開始時に実行する必要のある他のコードがアプリに含まれている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="63a29-132">In addition to code related to configuring the app's services or request pipeline, apps may have other code that must run when the app begins.</span></span> <span data-ttu-id="63a29-133">通常、このようなコードは *Program.cs* に配置されるか、`IHostedService` として登録されます。これは、アプリの起動時に[汎用ホスト](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1)によって開始されます。</span><span class="sxs-lookup"><span data-stu-id="63a29-133">Such code is typically placed in *Program.cs* or registered as an `IHostedService`, which will be started by the [generic host](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1) when the app starts.</span></span>

<span data-ttu-id="63a29-134">`IHostedService` インターフェイスは 2 つのメソッド (`StartAsync` および `StopAsync`) を公開します。</span><span class="sxs-lookup"><span data-stu-id="63a29-134">The `IHostedService` interface just exposes two methods, `StartAsync` and `StopAsync`.</span></span> <span data-ttu-id="63a29-135">このインターフェイスを `ConfigureServices` に登録し、ホストが残りの部分を実行して、アプリの起動前に `StartAsync` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63a29-135">You register the interface in `ConfigureServices` and the host does the rest, calling the `StartAsync` method before the app starts up.</span></span>

## <a name="porting-considerations"></a><span data-ttu-id="63a29-136">移植に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="63a29-136">Porting considerations</span></span>

<span data-ttu-id="63a29-137">アプリを ASP.NET MVC から ASP.NET Core に移行することを検討しているチームは、アプリの起動時に実行されるコードを特定し、ASP.NET Core アプリでのそのコードに適した場所を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63a29-137">Teams looking to migrate their apps from ASP.NET MVC to ASP.NET Core need to identify what code is being run when their app starts up and determine the appropriate location for such code in their ASP.NET Core app.</span></span> <span data-ttu-id="63a29-138">通常、アプリの起動時に実行する必要のあるカスタム コード (特に非同期コード) は、`IHostedService` の実装に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="63a29-138">For custom code needed to run when the app starts up, especially async code, the recommended approach is typically to put such code into `IHostedService` implementations.</span></span>

## <a name="references"></a><span data-ttu-id="63a29-139">リファレンス</span><span class="sxs-lookup"><span data-stu-id="63a29-139">References</span></span>

- <span data-ttu-id="63a29-140">[IIS 7 の ASP.NET アプリケーション ライフ サイクルの概要](/previous-versions/aspnet/bb470252(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="63a29-140">[ASP.NET Application Life Cycle Overview for IIS 7](/previous-versions/aspnet/bb470252(v=vs.100))</span></span>
- <span data-ttu-id="63a29-141">[IIS 5 および 6 の ASP.NET アプリケーション ライフ サイクルの概要](/previous-versions/aspnet/ms178473(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="63a29-141">[ASP.NET Application Life Cycle Overview for IIS 5 and 6](/previous-versions/aspnet/ms178473(v=vs.100))</span></span>
- [<span data-ttu-id="63a29-142">OWIN と Katana の概要</span><span class="sxs-lookup"><span data-stu-id="63a29-142">Getting Started with OWIN and Katana</span></span>](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)
- [<span data-ttu-id="63a29-143">WebActivator</span><span class="sxs-lookup"><span data-stu-id="63a29-143">WebActivator</span></span>](https://github.com/davidebbo/WebActivator)
- [<span data-ttu-id="63a29-144">ASP.NET Core でのアプリケーションのスタートアップ</span><span class="sxs-lookup"><span data-stu-id="63a29-144">App Startup in ASP.NET Core</span></span>](/aspnet/core/fundamentals/startup?preserve-view=true&view=aspnetcore-3.1)
- [<span data-ttu-id="63a29-145">ASP.NET Core の .NET 汎用ホスト</span><span class="sxs-lookup"><span data-stu-id="63a29-145">.NET Generic Host in ASP.NET Core</span></span>](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1)
- [<span data-ttu-id="63a29-146">IHostedService</span><span class="sxs-lookup"><span data-stu-id="63a29-146">IHostedService</span></span>](../microservices/multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)

>[!div class="step-by-step"]
><span data-ttu-id="63a29-147">[前へ](architectural-differences.md)
>[次へ](hosting-differences.md)</span><span class="sxs-lookup"><span data-stu-id="63a29-147">[Previous](architectural-differences.md)
[Next](hosting-differences.md)</span></span>
