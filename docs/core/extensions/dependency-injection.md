---
title: .NET での依存関係の挿入
description: .NET で依存関係の挿入を実装する方法とそれを使う方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 10/28/2020
ms.topic: overview
ms.openlocfilehash: 0b5526f24f3ac658123acd030c3adf32c346422a
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079519"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="89fb0-103">.NET での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="89fb0-103">Dependency injection in .NET</span></span>

<span data-ttu-id="89fb0-104">.NET では依存関係の挿入 (DI) ソフトウェア設計パターンがサポートされています。これは、クラスとその依存関係の間で[制御の反転 (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) を実現するための手法です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="89fb0-105">.NET での依存関係の挿入は、構成、ログ、オプション パターンと並び、[第一級オブジェクト](https://en.wikipedia.org/wiki/First-class_citizen)です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="89fb0-106">"*依存関係*" とは、他のオブジェクトが依存するオブジェクトのことです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="89fb0-107">他のクラスが依存している、次の `Write` メソッドを備えた `MessageWriter` クラスを調べます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="89fb0-108">クラスは、`MessageWriter` クラスのインスタンスを作成して、その `Write` メソッドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="89fb0-109">次の例で、`MessageWriter` クラスは `Worker` クラスの依存関係です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="89fb0-110">このクラスは `MessageWriter` クラスを作成し、これに直接依存しています。</span><span class="sxs-lookup"><span data-stu-id="89fb0-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="89fb0-111">ハードコーディングされた依存関係には、前の例のような問題があり、次の理由から回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="89fb0-112">`MessageWriter` を別の実装で置き換えるには、`Worker` クラスを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-112">To replace `MessageWriter` with a different implementation, the `Worker` class must be modified.</span></span>
- <span data-ttu-id="89fb0-113">`MessageWriter` が依存関係を含んでいる場合、これらは `Worker` クラスによって構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-113">If `MessageWriter` has dependencies, they must also be configured by the `Worker` class.</span></span> <span data-ttu-id="89fb0-114">複数のクラスが `MessageWriter` に依存している大規模なプロジェクトでは、構成コードがアプリ全体に分散するようになります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="89fb0-115">このような実装では、単体テストを行うことが困難です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="89fb0-116">アプリはモックまたはスタブの `MessageWriter` クラスを使用する必要がありますが、この方法では不可能です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="89fb0-117">依存関係の挿入は、次の方法によってこれらの問題に対応します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="89fb0-118">依存関係の実装を抽象化するための、インターフェイスまたは基底クラスの使用。</span><span class="sxs-lookup"><span data-stu-id="89fb0-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="89fb0-119">サービス コンテナー内の依存関係の登録。</span><span class="sxs-lookup"><span data-stu-id="89fb0-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="89fb0-120">.NET には、組み込みのサービス コンテナー <xref:System.IServiceProvider> が用意されています。</span><span class="sxs-lookup"><span data-stu-id="89fb0-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="89fb0-121">通常、サービスは、アプリの起動時に登録され、<xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="89fb0-122">すべてのサービスが追加されたら、<xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> を使用してサービス コンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="89fb0-123">サービスを使用するクラスのコンストラクターへの、サービスの "*挿入*"。</span><span class="sxs-lookup"><span data-stu-id="89fb0-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="89fb0-124">依存関係のインスタンスの作成、およびインスタンスが不要になったときの廃棄の役割を、フレームワークが担当します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="89fb0-125">たとえば、`IMessageWriter` インターフェイスに `Write` メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="89fb0-126">このインターフェイスは、具象型 `MessageWriter` によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="89fb0-127">このサンプル コードの場合、具象型 `MessageWriter` を使用して `IMessageWriter` サービスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="89fb0-128"><xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> メソッドによって、サービスは、1 つの要求の有効期間であるスコープ付き有効期間で登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="89fb0-129">[サービスの有効期間](#service-lifetimes)については、この記事の後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-129">[Service lifetimes](#service-lifetimes) are described later in this article.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="89fb0-130">サンプル アプリでは、`IMessageWriter` サービスが要求され、`Write` メソッドを呼び出すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="89fb0-131">DI パターンを使用することにより、Worker サービスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="89fb0-132">具象型 `MessageWriter` は使用されず、実装される `IMessageWriter` インターフェイスのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="89fb0-133">これにより、コントローラーが使用する実装は、コントローラーを変更することなく、簡単に変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="89fb0-134">`MessageWriter` のインスタンスは作成されず、DI コンテナーによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="89fb0-135">組み込みのログ API を使用すると、`IMessageWriter` インターフェイスの実装を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="89fb0-136">更新された `ConfigureServices` メソッドでは、新しい `IMessageWriter` の実装が登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="89fb0-137">`LoggingMessageWriter` は、コンストラクターで要求される <xref:Microsoft.Extensions.Logging.ILogger%601> によって異なります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="89fb0-138">`ILogger<TCategoryName>` は、[フレームワークで提供されるサービス](#framework-provided-services)です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="89fb0-139">依存関係の挿入をチェーン形式で使用することはよくあります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="89fb0-140">次に、要求されたそれぞれの依存関係が、それ自身の依存関係を要求します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="89fb0-141">コンテナーによってグラフ内の依存関係が解決され、完全に解決されたサービスが返されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="89fb0-142">解決する必要がある依存関係の集合的なセットは、通常、"*依存関係ツリー*"、"*依存関係グラフ*"、または "*オブジェクト グラフ*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree*, *dependency graph*, or *object graph*.</span></span>

<span data-ttu-id="89fb0-143">コンテナーでは、[(ジェネリック) オープン型](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types)を活用し、すべての [(ジェネリック) 構築型](/dotnet/csharp/language-reference/language-specification/types#constructed-types)を登録する必要をなくすことで、`ILogger<TCategoryName>` を解決します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="89fb0-144">依存関係の挿入に関する用語では、サービスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="89fb0-145">通常、他のオブジェクト (`IMessageWriter` サービスなど) にサービスを提供するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="89fb0-146">Web サービスを使用する場合はありますが、サービスは Web サービスに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="89fb0-147">フレームワークは、堅牢な ログ システムを備えています。</span><span class="sxs-lookup"><span data-stu-id="89fb0-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="89fb0-148">前の例に示されている `IMessageWriter` の実装は、ログを実装するのではなく、基本的な DI を実演するために記述されています。</span><span class="sxs-lookup"><span data-stu-id="89fb0-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="89fb0-149">ほとんどのアプリでは、ロガーを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="89fb0-150">次のコードは、既定のログを使用する方法を示しています。この場合、`Worker` をホステッド サービス <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> として `ConfigureServices` に登録するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="89fb0-151">前のコードを使用すると、ログ がフレームワークによって提供されるため、`ConfigureServices` を更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="89fb0-152">拡張メソッドを使用したサービスのグループを登録する</span><span class="sxs-lookup"><span data-stu-id="89fb0-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="89fb0-153">Microsoft 拡張機能には、関連するサービスのグループを登録するための規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="89fb0-154">規則は、単一の `Add{GROUP_NAME}` 拡張メソッドを使用して、フレームワーク機能に必要なすべてのサービスを登録するというものです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="89fb0-155">たとえば、<xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> 拡張メソッドにより、オプションの使用に必要なすべてのサービスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="89fb0-156">フレームワークが提供するサービス</span><span class="sxs-lookup"><span data-stu-id="89fb0-156">Framework-provided services</span></span>

<span data-ttu-id="89fb0-157">`ConfigureServices` メソッドにより、プラットフォーム機能など、アプリに使用されるサービスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="89fb0-158">最初に、`ConfigureServices` に提供される `IServiceCollection` には、フレームワークによって定義されたサービスがあります ([ホストの構成方法](generic-host.md#host-configuration)によって異なります)。</span><span class="sxs-lookup"><span data-stu-id="89fb0-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="89fb0-159">.NET テンプレートに基づくアプリの場合、フレームワークにより、数百単位のサービスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="89fb0-160">次の表に、フレームワークによって登録されるサービスのごく一部を示します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="89fb0-161">サービスの種類</span><span class="sxs-lookup"><span data-stu-id="89fb0-161">Service Type</span></span>                                                                       | <span data-ttu-id="89fb0-162">有効期間</span><span class="sxs-lookup"><span data-stu-id="89fb0-162">Lifetime</span></span>  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | <span data-ttu-id="89fb0-163">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | <span data-ttu-id="89fb0-164">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | <span data-ttu-id="89fb0-165">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | <span data-ttu-id="89fb0-166">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | <span data-ttu-id="89fb0-167">一時的</span><span class="sxs-lookup"><span data-stu-id="89fb0-167">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | <span data-ttu-id="89fb0-168">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-168">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | <span data-ttu-id="89fb0-169">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | <span data-ttu-id="89fb0-170">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-170">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="89fb0-171">サービスの有効期間</span><span class="sxs-lookup"><span data-stu-id="89fb0-171">Service lifetimes</span></span>

<span data-ttu-id="89fb0-172">サービスは、次のいずれかの有効期間で構成できます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-172">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="89fb0-173">一時的</span><span class="sxs-lookup"><span data-stu-id="89fb0-173">Transient</span></span>
- <span data-ttu-id="89fb0-174">スコープ</span><span class="sxs-lookup"><span data-stu-id="89fb0-174">Scoped</span></span>
- <span data-ttu-id="89fb0-175">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-175">Singleton</span></span>

<span data-ttu-id="89fb0-176">次のセクションでは、前の有効期間について個別に説明します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-176">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="89fb0-177">登録される各サービスの適切な有効期間を選択します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-177">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="89fb0-178">一時的</span><span class="sxs-lookup"><span data-stu-id="89fb0-178">Transient</span></span>

<span data-ttu-id="89fb0-179">有効期間が一時的なサービスは、サービス コンテナーから要求されるたびに作成されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-179">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="89fb0-180">この有効期間は、軽量でステートレスのサービスに最適です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-180">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="89fb0-181"><xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> で一時的なサービスを登録します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-181">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="89fb0-182">要求を処理するアプリでは、一時的なサービスが要求の最後に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-182">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="89fb0-183">スコープ</span><span class="sxs-lookup"><span data-stu-id="89fb0-183">Scoped</span></span>

<span data-ttu-id="89fb0-184">Web アプリケーションの場合、スコープ付き有効期間は、クライアント要求 (接続) ごとにサービスが 1 回作成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-184">For web applications, a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="89fb0-185"><xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> でスコープ付きサービスを登録します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-185">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="89fb0-186">要求を処理するアプリでは、スコープ付きサービスは要求の最後で破棄されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-186">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="89fb0-187">Entity Framework Core を使用する場合、既定では <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> 拡張メソッドによって、スコープ付き有効期間を持つ `DbContext` 型が登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-187">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="89fb0-188">シングルトンからスコープ付きサービスを解決 ***しない*** でください。また、たとえば一時的なサービスにより、間接的に解決しないようにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-188">Do ***not*** resolve a scoped service from a singleton and be careful not to do so indirectly, for example, through a transient service.</span></span> <span data-ttu-id="89fb0-189">後続の要求を処理する際に、サービスが正しくない状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-189">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="89fb0-190">次の場合は問題ありません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-190">It's fine to:</span></span>
>
> - <span data-ttu-id="89fb0-191">スコープ付きまたは一時的なサービスからシングルトン サービスを解決する。</span><span class="sxs-lookup"><span data-stu-id="89fb0-191">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="89fb0-192">スコープ付きサービスを、別のスコープ付きまたは一時的なサービスから解決する。</span><span class="sxs-lookup"><span data-stu-id="89fb0-192">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="89fb0-193">既定では、開発環境で、より長い有効期間を持つ別のサービスからサービスを解決すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-193">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="89fb0-194">詳しくは、「[スコープの検証](#scope-validation)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-194">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="89fb0-195">シングルトン</span><span class="sxs-lookup"><span data-stu-id="89fb0-195">Singleton</span></span>

<span data-ttu-id="89fb0-196">シングルトン有効期間サービスが作成されるのは、次のいずれかの場合です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-196">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="89fb0-197">それらが初めて要求された場合。</span><span class="sxs-lookup"><span data-stu-id="89fb0-197">The first time they're requested.</span></span>
- <span data-ttu-id="89fb0-198">開発者によって、実装インスタンスがコンテナーに直接提供される場合。</span><span class="sxs-lookup"><span data-stu-id="89fb0-198">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="89fb0-199">このアプローチはほとんど必要ありません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-199">This approach is rarely needed.</span></span>

<span data-ttu-id="89fb0-200">依存関係の挿入コンテナーから送信されるサービス実装の後続の要求すべてには、同じインスタンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-200">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="89fb0-201">アプリをシングルトンで動作させる必要がある場合は、サービス コンテナーによるサービスの有効期間の管理を許可してください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-201">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="89fb0-202">シングルトン デザイン パターンを実装したり、シングルトンを破棄するコードを提供したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-202">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="89fb0-203">コンテナーからサービスを解決したコードによって、サービスが破棄されることはありません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-203">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="89fb0-204">型またはファクトリがシングルトンとして登録されている場合、コンテナーによってシングルトンが自動的に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-204">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="89fb0-205">シングルトン サービスを <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> で登録します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-205">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="89fb0-206">シングルトン サービスはスレッド セーフである必要があり、ほとんどの場合、ステートレス サービスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-206">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="89fb0-207">要求を処理するアプリでは、アプリのシャットダウン時に <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> が破棄されるとき、シングルトン サービスが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-207">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="89fb0-208">アプリがシャットダウンされるまでメモリは解放されないため、シングルトン サービスでのメモリ使用を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-208">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="89fb0-209">サービス登録メソッド</span><span class="sxs-lookup"><span data-stu-id="89fb0-209">Service registration methods</span></span>

<span data-ttu-id="89fb0-210">このフレームワークでは、特定のシナリオで役立つサービス登録拡張メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-210">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="89fb0-211">メソッド</span><span class="sxs-lookup"><span data-stu-id="89fb0-211">Method</span></span> | <span data-ttu-id="89fb0-212">自動</span><span class="sxs-lookup"><span data-stu-id="89fb0-212">Automatic</span></span><br><span data-ttu-id="89fb0-213">object</span><span class="sxs-lookup"><span data-stu-id="89fb0-213">object</span></span><br><span data-ttu-id="89fb0-214">破棄</span><span class="sxs-lookup"><span data-stu-id="89fb0-214">disposal</span></span> | <span data-ttu-id="89fb0-215">複数</span><span class="sxs-lookup"><span data-stu-id="89fb0-215">Multiple</span></span><br><span data-ttu-id="89fb0-216">実装</span><span class="sxs-lookup"><span data-stu-id="89fb0-216">implementations</span></span> | <span data-ttu-id="89fb0-217">引数を渡す</span><span class="sxs-lookup"><span data-stu-id="89fb0-217">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="89fb0-218">例:</span><span class="sxs-lookup"><span data-stu-id="89fb0-218">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="89fb0-219">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-219">Yes</span></span> | <span data-ttu-id="89fb0-220">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-220">Yes</span></span> | <span data-ttu-id="89fb0-221">いいえ</span><span class="sxs-lookup"><span data-stu-id="89fb0-221">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="89fb0-222">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-222">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="89fb0-223">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-223">Yes</span></span> | <span data-ttu-id="89fb0-224">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-224">Yes</span></span> | <span data-ttu-id="89fb0-225">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-225">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="89fb0-226">例:</span><span class="sxs-lookup"><span data-stu-id="89fb0-226">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="89fb0-227">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-227">Yes</span></span> | <span data-ttu-id="89fb0-228">いいえ</span><span class="sxs-lookup"><span data-stu-id="89fb0-228">No</span></span> | <span data-ttu-id="89fb0-229">いいえ</span><span class="sxs-lookup"><span data-stu-id="89fb0-229">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="89fb0-230">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-230">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="89fb0-231">いいえ</span><span class="sxs-lookup"><span data-stu-id="89fb0-231">No</span></span> | <span data-ttu-id="89fb0-232">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-232">Yes</span></span> | <span data-ttu-id="89fb0-233">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-233">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="89fb0-234">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-234">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="89fb0-235">いいえ</span><span class="sxs-lookup"><span data-stu-id="89fb0-235">No</span></span> | <span data-ttu-id="89fb0-236">いいえ</span><span class="sxs-lookup"><span data-stu-id="89fb0-236">No</span></span> | <span data-ttu-id="89fb0-237">はい</span><span class="sxs-lookup"><span data-stu-id="89fb0-237">Yes</span></span> |

<span data-ttu-id="89fb0-238">型の廃棄の詳細については、「[サービスの破棄](dependency-injection-guidelines.md#disposal-of-services)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-238">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="89fb0-239">実装型のみでサービスを登録することは、同じ実装とサービスの型でそのサービスを登録することと同じです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-239">Registering a service with only an implementation type is equivalent to registering that service with the same implementation and service type.</span></span> <span data-ttu-id="89fb0-240">明示的なサービス型を使用しないメソッドを使用してサービスの複数の実装を登録できないのは、このためです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-240">This is why multiple implementations of a service cannot be registered using the methods that don't take an explicit service type.</span></span> <span data-ttu-id="89fb0-241">これらのメソッドでは、サービスの複数の "*インスタンス*" を登録できますが、すべて同じ "*実装*" 型になります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-241">These methods can register multiple *instances* of a service, but they will all have the same *implementation* type.</span></span>

<span data-ttu-id="89fb0-242">上記のサービス登録メソッドのずれかを使用して、同じサービス型の複数のサービス インスタンスを登録できます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-242">Any of the above service registration methods can be used to register multiple service instances of the same service type.</span></span> <span data-ttu-id="89fb0-243">次の例では、`IMessageWriter` をサービス型として使用して、`AddSingleton` を 2 回呼び出します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-243">In the following example, `AddSingleton` is called twice with `IMessageWriter` as the service type.</span></span> <span data-ttu-id="89fb0-244">2 回目の `AddSingleton` の呼び出しにより、`IMessageWriter` として解決された場合は前のものがオーバーライドされ、`IEnumerable<IMessageWriter>` を介して複数のサービスが解決された場合は前のものに追加されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-244">The second call to `AddSingleton` overrides the previous one when resolved as `IMessageWriter` and adds to the previous one when multiple services are resolved via `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="89fb0-245">`IEnumerable<{SERVICE}>` を介して解決された場合、サービスは登録された順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-245">Services appear in the order they were registered when resolved via `IEnumerable<{SERVICE}>`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

<span data-ttu-id="89fb0-246">上記のサンプル ソース コードを使用すると、`IMessageWriter` の 2 つの実装が登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-246">The preceding sample source code registers two implementations of the `IMessageWriter`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

<span data-ttu-id="89fb0-247">`ExampleService` により、2 つのコンストラクター パラメーター (1 つの `IMessageWriter` と `IEnumerable<IMessageWriter>`) が定義されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-247">The `ExampleService` defines two constructor parameters; a single `IMessageWriter`, and an `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="89fb0-248">1 つの `IMessageWriter` は登録された最後の実装です。一方、`IEnumerable<IMessageWriter>` は登録されたすべての実装を表します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-248">The single `IMessageWriter` is the last implementation to have been registered, whereas the `IEnumerable<IMessageWriter>` represents all registered implementations.</span></span>

<span data-ttu-id="89fb0-249">フレームワークには `TryAdd{LIFETIME}` 拡張メソッドも用意されており、実装がまだ登録されていない場合にのみ、サービスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-249">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="89fb0-250">次の例では、`AddSingleton` の呼び出しによって、`IMessageWriter` の実装として `ConsoleMessageWriter` が登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-250">In the following example, the call to `AddSingleton` registers `ConsoleMessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="89fb0-251">`TryAddSingleton` の呼び出しでは何も行われません。`IMessageWriter` には登録された実装が既に含まれているからです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-251">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

<span data-ttu-id="89fb0-252">`TryAddSingleton` は、既に追加されており、"試行" は失敗するため、効果はありません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-252">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span> <span data-ttu-id="89fb0-253">`ExampleService` により、以下がアサートされます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-253">The `ExampleService` would assert the following:</span></span>

```csharp
public class ExampleService
{
    public ExampleService(
        IMessageWriter messageWriter,
        IEnumerable<IMessageWriter> messageWriters)
    {
        Trace.Assert(messageWriter is ConsoleMessageWriter);
        Trace.Assert(messageWriters.Single() is ConsoleMessageWriter);
    }
}
```

<span data-ttu-id="89fb0-254">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-254">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="89fb0-255">[TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) メソッドでは、"*同じ型*" の実装がまだ存在しない場合にのみサービスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-255">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation *of the same type*.</span></span> <span data-ttu-id="89fb0-256">複数のサービスは、`IEnumerable<{SERVICE}>` によって解決されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-256">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="89fb0-257">サービスを登録するときに、同じ型のいずれかがまだ追加されていない場合は、インスタンスを追加します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-257">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="89fb0-258">ライブラリの作成者は、コンテナー内の実装の複数のコピーを登録しないようにするため `TryAddEnumerable` を使用します。</span><span class="sxs-lookup"><span data-stu-id="89fb0-258">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="89fb0-259">次の例では、`TryAddEnumerable` の最初の呼び出しで、`IMessageWriter1` の実装として `MessageWriter` が登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-259">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="89fb0-260">2 番目の呼び出しでは `IMessageWriter2` に `MessageWriter` が登録されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-260">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="89fb0-261">3 番目の呼び出しでは何も行われません。`IMessageWriter1` には `MessageWriter` の登録済みの実装が既に含まれているからです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-261">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

<span data-ttu-id="89fb0-262">サービスの登録は、通常、同じ種類の複数の実装を登録する場合を除き、順序に依存しません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-262">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="89fb0-263">`IServiceCollection` は <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> オブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-263">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="89fb0-264">次の例は、`ServiceDescriptor` の作成と追加によってサービスを登録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="89fb0-264">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="89fb0-265">組み込みの `Add{LIFETIME}` メソッドでも同じ方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-265">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="89fb0-266">たとえば、[AddScoped のソース コード](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="89fb0-266">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="89fb0-267">コンストラクターの挿入の動作</span><span class="sxs-lookup"><span data-stu-id="89fb0-267">Constructor injection behavior</span></span>

<span data-ttu-id="89fb0-268">サービスは次を使用することによって解決できます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-268">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="89fb0-269"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="89fb0-269"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="89fb0-270">コンテナーに登録されていないオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-270">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="89fb0-271">一部のフレームワーク機能に使用されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-271">Used with some framework features.</span></span>

<span data-ttu-id="89fb0-272">コンストラクターは、依存関係の挿入によって提供されない引数を受け取ることができますが、引数は既定値を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-272">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="89fb0-273">`IServiceProvider` または `ActivatorUtilities` によってサービスを解決する場合、コンストラクターの挿入には、"*パブリック*" コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="89fb0-273">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="89fb0-274">`ActivatorUtilities` によってサービスを解決する場合、コンストラクターの挿入に必要なことは、該当するコンストラクターが 1 つだけ存在することです。</span><span class="sxs-lookup"><span data-stu-id="89fb0-274">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="89fb0-275">コンストラクターのオーバーロードはサポートされていますが、依存関係の挿入によってすべての引数を設定できるオーバーロードは 1 つしか存在できません。</span><span class="sxs-lookup"><span data-stu-id="89fb0-275">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="89fb0-276">スコープの検証</span><span class="sxs-lookup"><span data-stu-id="89fb0-276">Scope validation</span></span>

<span data-ttu-id="89fb0-277">アプリが `Development` 環境で実行されていて、ホストを構築するために [CreateDefaultBuilder](generic-host.md#default-builder-settings) が呼び出される場合、既定のサービス プロバイダーによって次を確認するためのチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-277">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="89fb0-278">スコープ付きサービスが、ルート サービス プロバイダーによって解決されない。</span><span class="sxs-lookup"><span data-stu-id="89fb0-278">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="89fb0-279">スコープ付きサービスが、シングルトンに挿入されない。</span><span class="sxs-lookup"><span data-stu-id="89fb0-279">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="89fb0-280"><xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> が呼び出されると、ルート サービス プロバイダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-280">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="89fb0-281">ルート サービス プロバイダーの有効期間は、プロバイダーがアプリで開始されるとアプリの有効期間に対応し、アプリのシャットダウン時には破棄されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-281">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="89fb0-282">スコープ サービスは、それを作成したコンテナーによって破棄されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-282">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="89fb0-283">ルート コンテナーに作成されたスコープ付きサービスは、アプリのシャットダウン時に、ルート コンテナーによってのみ破棄されるため、サービスの有効期間は実質的にシングルトンに昇格されます。</span><span class="sxs-lookup"><span data-stu-id="89fb0-283">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="89fb0-284">`BuildServiceProvider` が呼び出されると、サービス スコープの検証がこれらの状況をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="89fb0-284">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="89fb0-285">関連項目</span><span class="sxs-lookup"><span data-stu-id="89fb0-285">See also</span></span>

- [<span data-ttu-id="89fb0-286">.NET で依存関係の挿入を使用する</span><span class="sxs-lookup"><span data-stu-id="89fb0-286">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="89fb0-287">依存関係の挿入のガイドライン</span><span class="sxs-lookup"><span data-stu-id="89fb0-287">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="89fb0-288">ASP.NET Core での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="89fb0-288">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
- [<span data-ttu-id="89fb0-289">NDC カンファレンス DI アプリ開発のパターン</span><span class="sxs-lookup"><span data-stu-id="89fb0-289">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="89fb0-290">明示的な依存関係の原則</span><span class="sxs-lookup"><span data-stu-id="89fb0-290">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="89fb0-291">制御の反転コンテナーと依存関係の挿入パターン (Martin Fowler)</span><span class="sxs-lookup"><span data-stu-id="89fb0-291">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)
- <span data-ttu-id="89fb0-292">DI のバグは、[github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) リポジトリに作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89fb0-292">DI bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
