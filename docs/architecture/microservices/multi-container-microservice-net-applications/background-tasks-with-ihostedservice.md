---
title: IHostedService と BackgroundService クラスを使ってマイクロサービスのバックグラウンド タスクを実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービスの .NET Core でバックグラウンド タスクを実装する IHostedService と BackgroundService を使用する新しいオプションについて理解します。
ms.date: 01/13/2021
ms.openlocfilehash: 26bc06c4a63cddcd32bf7da705f6258fab8eaafa
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188804"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="17dbb-103">IHostedService と BackgroundService クラスを使ってマイクロサービスのバックグラウンド タスクを実装する</span><span class="sxs-lookup"><span data-stu-id="17dbb-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="17dbb-104">バックグラウンド タスクとスケジュールされたジョブは、マイクロサービス アーキテクチャのパターンに従っているかどうかにかかわらず、すべてのアプリケーションで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-104">Background tasks and scheduled jobs are something you might need to use in any application, whether or not it follows the microservices architecture pattern.</span></span> <span data-ttu-id="17dbb-105">マイクロサービス アーキテクチャを使用する場合との違いは、自分のニーズに応じてスケールアップおよびスケールダウンできるように、バックグラウンド タスクをホスト用の別のプロセスまたはコンテナーに実装することです。</span><span class="sxs-lookup"><span data-stu-id="17dbb-105">The difference when using a microservices architecture is that you can implement the background task in a separate process/container for hosting so you can scale it down/up based on your need.</span></span>

<span data-ttu-id="17dbb-106">これらの種類のタスクは、ホスト、アプリケーション、マイクロサービス内でホストするサービス、ロジックであるため、全体的な観点から、.NET では "*ホステッド サービス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-106">From a generic point of view, in .NET we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="17dbb-107">このケースでは、ホステッド サービスは、単にバックグラウンド タスク ロジックを持つクラスを意味していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="17dbb-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="17dbb-108">.NET Core 2.0 以降では、ホステッド サービスを簡単に実装できるようにする <xref:Microsoft.Extensions.Hosting.IHostedService> という名前の新しいインターフェイスが、フレームワークによって提供されています。</span><span class="sxs-lookup"><span data-stu-id="17dbb-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="17dbb-109">基本的な考え方は、図 6-26 に示すように、ご利用の Web ホストまたはホストが実行されているときに、バックグラウンドで実行される複数のバックグラウンド タスク (ホステッド サービス) を登録できることです。</span><span class="sxs-lookup"><span data-stu-id="17dbb-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core IWebHost と .NET Core IHost を比較した図。](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="17dbb-111">**図 6-26**。</span><span class="sxs-lookup"><span data-stu-id="17dbb-111">**Figure 6-26**.</span></span> <span data-ttu-id="17dbb-112">WebHost と Host で IHostedService を使用した場合の比較</span><span class="sxs-lookup"><span data-stu-id="17dbb-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="17dbb-113">ASP.NET Core 1.x および 2.x では、Web アプリのバックグラウンド プロセスの `IWebHost` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="17dbb-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="17dbb-114">.NET Core 2.1 以降のバージョンでは、プレーンなコンソール アプリを使用したバックグラウンド プロセス用の `IHost` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="17dbb-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="17dbb-115">`WebHost` と `Host` の違いに注目してください。</span><span class="sxs-lookup"><span data-stu-id="17dbb-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="17dbb-116">ASP.NET Core 2.0 の `WebHost` (`IWebHost` を実装する基底クラス) は、MVC Web アプリや Web API サービスを実装する場合など、HTTP サーバー機能をプロセスに提供するために使用されるインフラストラクチャ成果物です。</span><span class="sxs-lookup"><span data-stu-id="17dbb-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="17dbb-117">ASP.NET Core の新しいインフラストラクチャのすべての長所を提供することで、依存関係の挿入の使用や、要求パイプラインへのミドルウェアの挿入などを実行できます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="17dbb-118">`WebHost` では、これらが、バックグラウンド タスク用の `IHostedServices` を同じように使用されます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="17dbb-119">`Host` (`IHost` を実装する基底クラス) は .NET Core 2.1 で実装されました。</span><span class="sxs-lookup"><span data-stu-id="17dbb-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="17dbb-120">基本的に、`Host` を使用すると、`WebHost` を使用した場合と同様のインフラストラクチャ (依存関係の挿入、ホステッド サービスなど) ができますが、このケースでは、ホストとしてシンプルでより軽量なプロセスが必要なだけで、MVC、Web API または HTTP サーバー機能は関係ありません。</span><span class="sxs-lookup"><span data-stu-id="17dbb-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="17dbb-121">そのため、`IHost` を使用して特殊化されたホスト プロセスを作成してホステッド サービス以外 (`IHostedServices` をホスティングするためだけに作成されたマイクロサービスなど) は処理しないことを選択するか、代わりに既存の ASP.NET Core `WebHost` (既存の ASP.NET Core Web API または MVC アプリ) を拡張することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="17dbb-122">ビジネスと拡張性のニーズに応じて、いずれの方法にも長所と短所があります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="17dbb-123">つまり、基本的には、バックグラウンド タスクが HTTP (`IWebHost`) と関係ない場合は、`IHost` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="17dbb-124">WebHost または Host でホステッド サービスを登録する</span><span class="sxs-lookup"><span data-stu-id="17dbb-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="17dbb-125">`IHostedService` インターフェイスの使用は、`WebHost` と `Host`で非常に似ているので、詳しく見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="17dbb-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="17dbb-126">SignalR はホステッド サービスを使用している成果物の一例ですが、次のようなより単純なことにも使用することができます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="17dbb-127">変更を検索するデータベースをポーリングするバックグラウンド タスク。</span><span class="sxs-lookup"><span data-stu-id="17dbb-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="17dbb-128">いくつかのキャッシュを定期的に更新するスケジュールされたタスク。</span><span class="sxs-lookup"><span data-stu-id="17dbb-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="17dbb-129">タスクをバックグラウンド スレッドで実行することを可能にする QueueBackgroundWorkItem の実装。</span><span class="sxs-lookup"><span data-stu-id="17dbb-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="17dbb-130">`ILogger` などの共通サービスを共有しながら、Web アプリのバックグラウンドでメッセージ キューからのメッセージの処理。</span><span class="sxs-lookup"><span data-stu-id="17dbb-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="17dbb-131">`Task.Run()` で開始されるバックグラウンド タスク。</span><span class="sxs-lookup"><span data-stu-id="17dbb-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="17dbb-132">基本的に、`IHostedService` を実装するバックグラウンド タスクにこれらのアクションのいずれかをオフロードできます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="17dbb-133">1 つまたは複数の `IHostedServices` を `WebHost` または `Host` に追加するには、ASP.NET Core `WebHost` (または .NET Core 2.1 以降の `Host`) の <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> 拡張メソッドでそれらを登録します。</span><span class="sxs-lookup"><span data-stu-id="17dbb-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="17dbb-134">基本的に、次のコードのように、一般的な ASP.NET WebHost から、`Startup` クラスの使い慣れた `ConfigureServices()` メソッド内でホステッド サービスを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="17dbb-135">そのコードで、`GracePeriodManagerService` ホステッド サービスは eShopOnContainers の Ordering business microservice からの実際のコードですが、他の 2 つは単に追加の 2 つのサンプルです。</span><span class="sxs-lookup"><span data-stu-id="17dbb-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="17dbb-136">`IHostedService` バックグラウンド タスクの実行は、アプリケーション (さらに言えば、ホストまたはマイクロサービス) の有効期間に合わせて調整されます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="17dbb-137">アプリケーションの起動時にタスクを登録して、いくつかの正常なアクションを行うか、アプリケーションのシャットダウン時にクリーンアップすることができます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="17dbb-138">`IHostedService` を使用しない場合は、いつでもバックグラウンド スレッドを開始して任意のタスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="17dbb-139">正常なクリーンアップ アクションを実行する機会がないままスレッドが単に強制終了される場合、差はちょうどアプリのシャットダウン時間になります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="17dbb-140">IHostedService インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17dbb-140">The IHostedService interface</span></span>

<span data-ttu-id="17dbb-141">`IHostedService` を登録すると、アプリケーションの起動時と停止時にそれぞれ、.NET によって `IHostedService` 型の `StartAsync()` および `StopAsync()` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-141">When you register an `IHostedService`, .NET will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="17dbb-142">詳細については、「[IHostedService インターフェイス](/aspnet/core/fundamentals/host/hosted-services?tabs=visual-studio&view=aspnetcore-3.1#ihostedservice-interface)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17dbb-142">For more details, refer [IHostedService interface](/aspnet/core/fundamentals/host/hosted-services?tabs=visual-studio&view=aspnetcore-3.1#ihostedservice-interface)</span></span>

<span data-ttu-id="17dbb-143">ご想像のとおり、以前に示したように、IHostedService の複数の実装を作成し、`ConfigureService()` メソッドでそれらを DI コンテナーに登録することができます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="17dbb-144">これらすべてのホステッド サービスが、アプリケーション/マイクロサービスと共に開始および停止されます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="17dbb-145">開発者は、`StopAsync()` メソッドがホストによってトリガーされるときに、サービスの停止アクションを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="17dbb-146">BackgroundService 基底クラスから派生したカスタムのホステッド サービス クラスを使用して IHostedService を実装する</span><span class="sxs-lookup"><span data-stu-id="17dbb-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="17dbb-147">続行して、ホステッド サービスのカスタム クラスをゼロから作成し、`IHostedService` を実装します。これは .NET Core 2.0 以降を使用する場合に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0 and later.</span></span>

<span data-ttu-id="17dbb-148">ただし、ほとんどのバックグラウンド タスクでは、キャンセル トークンの管理およびその他の一般的な操作で同様のニーズがあるため、派生元として使用できる非常に便利な `BackgroundService` という名前の抽象基底クラスがあります (.NET Core 2.1 以降で利用できます)。</span><span class="sxs-lookup"><span data-stu-id="17dbb-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="17dbb-149">そのクラスは、バックグラウンド タスクを設定するために必要な主要な作業を提供します。</span><span class="sxs-lookup"><span data-stu-id="17dbb-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="17dbb-150">次のコードは、.NET に実装されている BackgroundService 抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="17dbb-150">The next code is the abstract BackgroundService base class as implemented in .NET.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="17dbb-151">前の抽象基底クラスから派生する場合、データベースをポーリングして、必要に応じてイベント バスに統合イベントをパブリッシュする eShopOnContainers からの簡素化された次のコードのように、継承された実装により、独自のカスタムのホステッド サービス クラスで `ExecuteAsync()` メソッドを実装するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        // Constructor's parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="17dbb-152">eShopOnContainers のこの特定のケースでは、特定の状態を持つ注文を検索するデータベース テーブルに対してクエリを実行するアプリケーション メソッドを実行し、変更を適用するときに、イベント バスを介して統合イベントをパブリッシュします (その下で RabbitMQ または Azure Service Bus を使用できます)。</span><span class="sxs-lookup"><span data-stu-id="17dbb-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="17dbb-153">もちろん、代わりに他の任意のビジネス バックグラウンド タスクを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="17dbb-154">既定では、キャンセル トークンには 5 秒のタイムアウトが設定されていますが、この値は、`IWebHostBuilder` の `UseShutdownTimeout` 拡張機能を使用し、お使いの `WebHost` をビルドする際に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-154">By default, the cancellation token is set with a 5 seconds timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="17dbb-155">これは、サービスが 5 秒以内にキャンセルされることが想定されていて、そうでない場合は突然強制終了される可能性が高くなることを意味します。</span><span class="sxs-lookup"><span data-stu-id="17dbb-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="17dbb-156">次のコードでは、その時間を 10 秒に変更します。</span><span class="sxs-lookup"><span data-stu-id="17dbb-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="17dbb-157">クラス図の概要</span><span class="sxs-lookup"><span data-stu-id="17dbb-157">Summary class diagram</span></span>

<span data-ttu-id="17dbb-158">次の図は、IHostedServices を実装する場合のクラスとインターフェイスの概要を視覚的に示しています。</span><span class="sxs-lookup"><span data-stu-id="17dbb-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![IWebHost と IHost で多数のサービスをホストできることを示す図。](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="17dbb-160">**図 6-27**。</span><span class="sxs-lookup"><span data-stu-id="17dbb-160">**Figure 6-27**.</span></span> <span data-ttu-id="17dbb-161">IHostedService に関連する複数のクラスとインターフェイスを示すクラス図</span><span class="sxs-lookup"><span data-stu-id="17dbb-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="17dbb-162">クラス ダイアグラム:IWebHost と IHost は、BackgroundService から継承され、IHostedService を実装する多くのサービスをホストできます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="17dbb-163">展開に関する注意事項と習得事項</span><span class="sxs-lookup"><span data-stu-id="17dbb-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="17dbb-164">ASP.NET Core `WebHost` または .NET`Host` を展開する方法が最終的なソリューションに影響を与える可能性があることに注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="17dbb-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET `Host` might impact the final solution.</span></span> <span data-ttu-id="17dbb-165">たとえば、`WebHost` を IIS または正規の Azure App Service に展開する場合、アプリ プールのリサイクルが原因でホストがシャットダウンされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="17dbb-166">ただし、ホストをコンテナーとして Kubernetes などのオーケストレーターに展開する場合は、ご利用のホストのライブ インスタンスの確実な数を制御することができます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-166">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="17dbb-167">さらに、Azure Functions のように、これらのシナリオ用に特別に作成されたクラウド内で、他の方法を検討することができます。</span><span class="sxs-lookup"><span data-stu-id="17dbb-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="17dbb-168">最後になりますが、サービスを常時実行する必要があるとき、および Windows Server にデプロイする場合、Windows Service を使用できることがあります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="17dbb-169">ただし、アプリ プールに展開された `WebHost` に対しても、適用可能なアプリケーションのメモリ内キャッシュの再作成またはフラッシュのようなシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="17dbb-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="17dbb-170">`IHostedService` インターフェイスには、(.NET Core 2.0 以降のバージョンの) ASP.NET Core Web アプリケーションで、または (`IHost` を使用して .NET Core 2.1 で開始する) 任意のプロセス/ホストでバックグラウンド タスクを開始する便利な方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="17dbb-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="17dbb-171">その主な利点は、ホスト自体がシャットダウンされるときに、正常なキャンセルの機会が得られ、お使いのバックグラウンド タスクのコードがクリーンアップされることです。</span><span class="sxs-lookup"><span data-stu-id="17dbb-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up the code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="17dbb-172">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="17dbb-172">Additional resources</span></span>

- <span data-ttu-id="17dbb-173">**ASP.NET Core/Standard 2.0 でスケジュールされたタスクをビルドする** </span><span class="sxs-lookup"><span data-stu-id="17dbb-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="17dbb-174">**ASP.NET Core 2.0 で IHostedService を実装する** </span><span class="sxs-lookup"><span data-stu-id="17dbb-174">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="17dbb-175">**ASP.NET Core 2.1 を使用した GenericHost サンプル** </span><span class="sxs-lookup"><span data-stu-id="17dbb-175">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="17dbb-176">[前へ](test-aspnet-core-services-web-apps.md)
> [次へ](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="17dbb-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
