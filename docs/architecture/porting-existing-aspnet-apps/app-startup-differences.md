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
# <a name="app-startup-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="f5513-104">ASP.NET MVC と ASP.NET Core のアプリの起動の違い</span><span class="sxs-lookup"><span data-stu-id="f5513-104">App startup differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="f5513-105">ASP.NET MVC アプリは、Windows オペレーティングシステムで使用できるプライマリ web サーバーであるインターネットインフォメーションサーバー (IIS) 内で完全に有効期間があります。</span><span class="sxs-lookup"><span data-stu-id="f5513-105">ASP.NET MVC apps lived entirely within Internet Information Server (IIS), the primary web server available on Windows operating systems.</span></span> <span data-ttu-id="f5513-106">ASP.NET MVC とは異なり、ASP.NET Core アプリは実行可能アプリです。</span><span class="sxs-lookup"><span data-stu-id="f5513-106">Unlike ASP.NET MVC, ASP.NET Core apps are executable apps.</span></span> <span data-ttu-id="f5513-107">これらは、を使用してコマンドラインから実行でき `dotnet run` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-107">You can run them from the command line, using `dotnet run`.</span></span> <span data-ttu-id="f5513-108">これらのメソッドには、すべての C# プログラムと同様に、通常 `public static void Main()` は同様のバリエーション (引数やサポートなど) が含まれてい `async` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-108">They have an entry point method like all C# programs, typically `public static void Main()` or a similar variation (perhaps with arguments or `async` support).</span></span> <span data-ttu-id="f5513-109">これは、ASP.NET Core MVC と ASP.NET MVC の間で最も大きなアーキテクチャの違いであり、Windows 以外のシステムでの ASP.NET Core の実行を可能にするいくつかの違いの1つです。</span><span class="sxs-lookup"><span data-stu-id="f5513-109">This is perhaps the biggest architectural difference between ASP.NET Core and ASP.NET MVC, and is one of several differences that allows ASP.NET Core to run on non-Windows systems.</span></span>

## <a name="aspnet-mvc-startup"></a><span data-ttu-id="f5513-110">ASP.NET MVC のスタートアップ</span><span class="sxs-lookup"><span data-stu-id="f5513-110">ASP.NET MVC Startup</span></span>

<span data-ttu-id="f5513-111">IIS 内でホストされる ASP.NET アプリでは、特定のオブジェクトをインスタンス化し、要求が到着したときに特定のメソッドを呼び出すために IIS に依存しています。</span><span class="sxs-lookup"><span data-stu-id="f5513-111">Hosted within IIS, ASP.NET apps rely on IIS to instantiate certain objects and call certain methods when a request arrives.</span></span> <span data-ttu-id="f5513-112">ASP.NET は、から派生した *global.asax* ファイルのクラスのインスタンスを作成し `HttpApplication` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-112">ASP.NET creates an instance of the *Global.asax* file's class, which derives from `HttpApplication`.</span></span> <span data-ttu-id="f5513-113">最初の要求を受信すると、要求自体を処理する前に、ASP.NET が `Application_Start` *global.asax* ファイルのクラスのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f5513-113">When the first request is received, before handling the request itself, ASP.NET calls the `Application_Start` method in the *Global.asax* file's class.</span></span> <span data-ttu-id="f5513-114">ASP.NET MVC アプリの開始時に実行する必要のあるロジックは、このメソッドに追加できます。</span><span class="sxs-lookup"><span data-stu-id="f5513-114">Any logic that needs to run when the ASP.NET MVC app begins can be added to this method.</span></span>

<span data-ttu-id="f5513-115">ASP.NET MVC および Web API 用の多くの NuGet パッケージでは、 [Webactivator](https://github.com/davidebbo/WebActivator) パッケージを使用して、アプリの起動時に一部のコードを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f5513-115">Many NuGet packages for ASP.NET MVC and Web API use the [WebActivator](https://github.com/davidebbo/WebActivator) package to let them run some code during app startup.</span></span> <span data-ttu-id="f5513-116">慣例により、このコードは通常、 *App_Start* フォルダーに追加されます。属性を使用して構成され、の直前または直後に実行され `Application_Start` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-116">By convention, this code would typically be added to an *App_Start* folder and would be configured via attribute to run either immediately before or just after `Application_Start`.</span></span>

<span data-ttu-id="f5513-117">また、 [ASP.NET MVC で Open Web Interface for .net (OWIN) および Project Katana](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5513-117">It's also possible to use the [Open Web Interface for .NET (OWIN) and Project Katana with ASP.NET MVC](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana).</span></span> <span data-ttu-id="f5513-118">この場合、アプリには、ASP.NET Core の動作と非常によく似た方法で要求ミドルウェアを設定する *Startup.cs* ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5513-118">When doing so, the app will include a *Startup.cs* file that is responsible for setting up request middleware in a way that's very similar to how ASP.NET Core behaves.</span></span>

<span data-ttu-id="f5513-119">ASP.NET MVC アプリの起動時にコードを実行する必要がある場合は、通常、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="f5513-119">If you need to run code when your ASP.NET MVC app starts up, it will typically use one of these approaches.</span></span>

## <a name="aspnet-core-startup"></a><span data-ttu-id="f5513-120">ASP.NET Core スタートアップ</span><span class="sxs-lookup"><span data-stu-id="f5513-120">ASP.NET Core Startup</span></span>

<span data-ttu-id="f5513-121">前述のように、ASP.NET Core アプリはスタンドアロンプログラムです。</span><span class="sxs-lookup"><span data-stu-id="f5513-121">As noted previously, ASP.NET Core apps are standalone programs.</span></span> <span data-ttu-id="f5513-122">そのため、通常はアプリのエントリポイントを含む *Program.cs* ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5513-122">As such, they typically include a *Program.cs* file containing the entry point for the app.</span></span> <span data-ttu-id="f5513-123">このファイルの典型的な例を図2-1 に示します。</span><span class="sxs-lookup"><span data-stu-id="f5513-123">A typical example of this file is shown in Figure 2-1.</span></span>

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

<span data-ttu-id="f5513-124">**(図 2-1)** 。</span><span class="sxs-lookup"><span data-stu-id="f5513-124">**Figure 2-1**.</span></span> <span data-ttu-id="f5513-125">一般的な ASP.NET Core *Program.cs* ファイル。</span><span class="sxs-lookup"><span data-stu-id="f5513-125">A typical ASP.NET Core *Program.cs* file.</span></span>

<span data-ttu-id="f5513-126">図2-1 に示すコードでは、アプリの *ホスト* を作成し、ビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="f5513-126">The code shown in Figure 2-1 creates a *host* for the app, builds it, and runs it.</span></span> <span data-ttu-id="f5513-127">ASP.NET Core アプリは、表示されたによって構成されるホスト内で実行され `IHostBuilder` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-127">The ASP.NET Core app runs within the host configured by the `IHostBuilder` shown.</span></span> <span data-ttu-id="f5513-128">を使用して ASP.NET Core アプリを完全に構成することもできますが、 `IHostBuilder` 通常、この作業の大部分はクラスで行われ `Startup` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-128">While it's possible to completely configure an ASP.NET Core app using the `IHostBuilder`, typically the bulk of this work is done in a `Startup` class.</span></span>

<span data-ttu-id="f5513-129">クラスは、 `Startup` ホストとの2つのメソッドを公開します。 `ConfigureServices` `Configure`</span><span class="sxs-lookup"><span data-stu-id="f5513-129">The `Startup` class exposes two methods to the host: `ConfigureServices` and `Configure`.</span></span> <span data-ttu-id="f5513-130">`ConfigureServices`メソッドは、アプリが使用するサービスと、それぞれの有効期間を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f5513-130">The `ConfigureServices` method is used to define the services the app will use and their respective lifetimes.</span></span> <span data-ttu-id="f5513-131">メソッドを使用して、ミドルウェアで構成される `Configure` 要求パイプラインを設定することによって、アプリへの各要求を処理する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="f5513-131">The `Configure` method is used to define how each request to the app will be handled by setting up a request pipeline composed of middleware.</span></span>

<span data-ttu-id="f5513-132">アプリのサービスまたは要求パイプラインの構成に関連するコードに加えて、アプリの開始時に実行する必要のある他のコードが含まれている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f5513-132">In addition to code related to configuring the app's services or request pipeline, apps may have other code that must run when the app begins.</span></span> <span data-ttu-id="f5513-133">通常、このようなコードは *Program.cs* に配置されるか、として登録され `IHostedService` ます。これは、アプリの起動時に [汎用ホスト](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1) によって開始されます。</span><span class="sxs-lookup"><span data-stu-id="f5513-133">Such code is typically placed in *Program.cs* or registered as an `IHostedService`, which will be started by the [generic host](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1) when the app starts.</span></span>

<span data-ttu-id="f5513-134">インターフェイスは、 `IHostedService` とという2つのメソッドを公開し `StartAsync` `StopAsync` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-134">The `IHostedService` interface just exposes two methods, `StartAsync` and `StopAsync`.</span></span> <span data-ttu-id="f5513-135">インターフェイスをに登録し、 `ConfigureServices` ホストが残りの部分を実行して、 `StartAsync` アプリが起動する前にメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f5513-135">You register the interface in `ConfigureServices` and the host does the rest, calling the `StartAsync` method before the app starts up.</span></span>

## <a name="porting-considerations"></a><span data-ttu-id="f5513-136">移植に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="f5513-136">Porting considerations</span></span>

<span data-ttu-id="f5513-137">アプリを ASP.NET MVC から ASP.NET Core に移行することを検討しているチームは、アプリの起動時に実行されているコードを特定し、ASP.NET Core アプリでそのようなコードの適切な場所を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5513-137">Teams looking to migrate their apps from ASP.NET MVC to ASP.NET Core need to identify what code is being run when their app starts up and determine the appropriate location for such code in their ASP.NET Core app.</span></span> <span data-ttu-id="f5513-138">アプリの起動時に実行する必要があるカスタムコード (特に非同期コード) については、通常、このようなコードを実装に配置することをお勧めし `IHostedService` ます。</span><span class="sxs-lookup"><span data-stu-id="f5513-138">For custom code needed to run when the app starts up, especially async code, the recommended approach is typically to put such code into `IHostedService` implementations.</span></span>

## <a name="references"></a><span data-ttu-id="f5513-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5513-139">References</span></span>

- <span data-ttu-id="f5513-140">[IIS 7 の ASP.NET アプリケーションライフサイクルの概要](/previous-versions/aspnet/bb470252(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f5513-140">[ASP.NET Application Life Cycle Overview for IIS 7](/previous-versions/aspnet/bb470252(v=vs.100))</span></span>
- <span data-ttu-id="f5513-141">[IIS 5 および6の ASP.NET アプリケーションライフサイクルの概要](/previous-versions/aspnet/ms178473(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f5513-141">[ASP.NET Application Life Cycle Overview for IIS 5 and 6](/previous-versions/aspnet/ms178473(v=vs.100))</span></span>
- [<span data-ttu-id="f5513-142">OWIN と Katana の概要</span><span class="sxs-lookup"><span data-stu-id="f5513-142">Getting Started with OWIN and Katana</span></span>](/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)
- [<span data-ttu-id="f5513-143">WebActivator</span><span class="sxs-lookup"><span data-stu-id="f5513-143">WebActivator</span></span>](https://github.com/davidebbo/WebActivator)
- [<span data-ttu-id="f5513-144">ASP.NET Core でのアプリの起動</span><span class="sxs-lookup"><span data-stu-id="f5513-144">App Startup in ASP.NET Core</span></span>](/aspnet/core/fundamentals/startup?preserve-view=true&view=aspnetcore-3.1)
- [<span data-ttu-id="f5513-145">ASP.NET Core の .NET 汎用ホスト</span><span class="sxs-lookup"><span data-stu-id="f5513-145">.NET Generic Host in ASP.NET Core</span></span>](/aspnet/core/fundamentals/host/generic-host?preserve-view=true&view=aspnetcore-3.1)
- [<span data-ttu-id="f5513-146">IHostedService</span><span class="sxs-lookup"><span data-stu-id="f5513-146">IHostedService</span></span>](../microservices/multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)

>[!div class="step-by-step"]
><span data-ttu-id="f5513-147">[前へ](architectural-differences.md)
>[次へ](hosting-differences.md)</span><span class="sxs-lookup"><span data-stu-id="f5513-147">[Previous](architectural-differences.md)
[Next](hosting-differences.md)</span></span>
