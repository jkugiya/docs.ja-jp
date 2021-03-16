---
title: .NET での汎用ホスト
author: IEvangelist
description: アプリの起動と有効期間の管理を行う .NET 汎用ホストについて説明します。
ms.author: dapine
ms.date: 12/18/2020
ms.openlocfilehash: bf6d5ad624bbed46994633abace0af64712757f3
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "102402119"
---
# <a name="net-generic-host"></a><span data-ttu-id="2c582-103">.NET での汎用ホスト</span><span class="sxs-lookup"><span data-stu-id="2c582-103">.NET Generic Host</span></span>

<span data-ttu-id="2c582-104">Worker サービス テンプレートを使用すると、.NET 汎用ホスト <xref:Microsoft.Extensions.Hosting.HostBuilder> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-104">The Worker Service templates create a .NET Generic Host, <xref:Microsoft.Extensions.Hosting.HostBuilder>.</span></span> <span data-ttu-id="2c582-105">汎用ホストは、コンソール アプリなど、他の種類の .NET アプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c582-105">The Generic Host can be used with other types of .NET applications, such as Console apps.</span></span>

<span data-ttu-id="2c582-106">"*ホスト*" とは、以下のようなアプリのリソースをカプセル化するオブジェクトです:</span><span class="sxs-lookup"><span data-stu-id="2c582-106">A *host* is an object that encapsulates an app's resources, such as:</span></span>

- <span data-ttu-id="2c582-107">依存関係の挿入 (DI)</span><span class="sxs-lookup"><span data-stu-id="2c582-107">Dependency injection (DI)</span></span>
- <span data-ttu-id="2c582-108">ログの記録</span><span class="sxs-lookup"><span data-stu-id="2c582-108">Logging</span></span>
- <span data-ttu-id="2c582-109">構成</span><span class="sxs-lookup"><span data-stu-id="2c582-109">Configuration</span></span>
- <span data-ttu-id="2c582-110">`IHostedService` の実装</span><span class="sxs-lookup"><span data-stu-id="2c582-110">`IHostedService` implementations</span></span>

<span data-ttu-id="2c582-111">ホストが起動すると、サービス コンテナーのホステッド サービスのコレクションに登録されている <xref:Microsoft.Extensions.Hosting.IHostedService> の各実装で <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-111">When a host starts, it calls <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> on each implementation of <xref:Microsoft.Extensions.Hosting.IHostedService> registered in the service container's collection of hosted services.</span></span> <span data-ttu-id="2c582-112">Worker サービス アプリでは、<xref:Microsoft.Extensions.Hosting.BackgroundService> インスタンスを含むすべての `IHostedService` 実装で、<xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-112">In a worker service app, all `IHostedService` implementations that contain <xref:Microsoft.Extensions.Hosting.BackgroundService> instances have their <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> methods called.</span></span>

<span data-ttu-id="2c582-113">アプリの相互依存するすべてのリソースを 1 つのオブジェクトに含める主な理由は、アプリの起動と正常なシャットダウンの制御の有効期間の管理のためです。</span><span class="sxs-lookup"><span data-stu-id="2c582-113">The main reason for including all of the app's interdependent resources in one object is lifetime management: control over app startup and graceful shutdown.</span></span> <span data-ttu-id="2c582-114">これを実行するには、[Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c582-114">This is achieved with the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package.</span></span>

## <a name="set-up-a-host"></a><span data-ttu-id="2c582-115">ホストを設定する</span><span class="sxs-lookup"><span data-stu-id="2c582-115">Set up a host</span></span>

<span data-ttu-id="2c582-116">ホストは通常、`Program` クラス内のコードによって構成、ビルド、および実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-116">The host is typically configured, built, and run by code in the `Program` class.</span></span> <span data-ttu-id="2c582-117">`Main` メソッド:</span><span class="sxs-lookup"><span data-stu-id="2c582-117">The `Main` method:</span></span>

- <span data-ttu-id="2c582-118"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> メソッドを呼び出して、builder オブジェクトを作成および構成します。</span><span class="sxs-lookup"><span data-stu-id="2c582-118">Calls a <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> method to create and configure a builder object.</span></span>
- <span data-ttu-id="2c582-119"><xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> を呼び出して <xref:Microsoft.Extensions.Hosting.IHost> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c582-119">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> to create an <xref:Microsoft.Extensions.Hosting.IHost> instance.</span></span>
- <span data-ttu-id="2c582-120">ホスト オブジェクトに対して <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> または <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2c582-120">Calls <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> or <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> method on the host object.</span></span>

<span data-ttu-id="2c582-121">.NET Worker サービス テンプレートを使用すると、汎用ホストを作成する次のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-121">The .NET Worker Service templates generate the following code to create a Generic Host:</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a><span data-ttu-id="2c582-122">既定の builder 設定</span><span class="sxs-lookup"><span data-stu-id="2c582-122">Default builder settings</span></span>

<span data-ttu-id="2c582-123"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> メソッド:</span><span class="sxs-lookup"><span data-stu-id="2c582-123">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> method:</span></span>

- <span data-ttu-id="2c582-124"><xref:System.IO.Directory.GetCurrentDirectory> によって返されるパスにコンテンツ ルートを設定します。</span><span class="sxs-lookup"><span data-stu-id="2c582-124">Sets the content root to the path returned by <xref:System.IO.Directory.GetCurrentDirectory>.</span></span>
- <span data-ttu-id="2c582-125">次から[ ホスト構成](#host-configuration)を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2c582-125">Loads [host configuration](#host-configuration) from:</span></span>
  - <span data-ttu-id="2c582-126">プレフィックス `DOTNET_` が付いた環境変数。</span><span class="sxs-lookup"><span data-stu-id="2c582-126">Environment variables prefixed with `DOTNET_`.</span></span>
  - <span data-ttu-id="2c582-127">コマンド ライン引数。</span><span class="sxs-lookup"><span data-stu-id="2c582-127">Command-line arguments.</span></span>
- <span data-ttu-id="2c582-128">次からアプリの構成を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2c582-128">Loads app configuration from:</span></span>
  - <span data-ttu-id="2c582-129">*appsettings.json*。</span><span class="sxs-lookup"><span data-stu-id="2c582-129">*appsettings.json*.</span></span>
  - <span data-ttu-id="2c582-130">*appsettings.{Environment}.json*。</span><span class="sxs-lookup"><span data-stu-id="2c582-130">*appsettings.{Environment}.json*.</span></span>
  - <span data-ttu-id="2c582-131">`Development` 環境でアプリが実行される場合に使用されるシークレット マネージャー。</span><span class="sxs-lookup"><span data-stu-id="2c582-131">Secret Manager when the app runs in the `Development` environment.</span></span>
  - <span data-ttu-id="2c582-132">環境変数。</span><span class="sxs-lookup"><span data-stu-id="2c582-132">Environment variables.</span></span>
  - <span data-ttu-id="2c582-133">コマンド ライン引数。</span><span class="sxs-lookup"><span data-stu-id="2c582-133">Command-line arguments.</span></span>
- <span data-ttu-id="2c582-134">次のログ プロバイダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c582-134">Adds the following logging providers:</span></span>
  - <span data-ttu-id="2c582-135">コンソール</span><span class="sxs-lookup"><span data-stu-id="2c582-135">Console</span></span>
  - <span data-ttu-id="2c582-136">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2c582-136">Debug</span></span>
  - <span data-ttu-id="2c582-137">EventSource</span><span class="sxs-lookup"><span data-stu-id="2c582-137">EventSource</span></span>
  - <span data-ttu-id="2c582-138">イベント ログ (Windows で実行されている場合のみ)</span><span class="sxs-lookup"><span data-stu-id="2c582-138">EventLog (only when running on Windows)</span></span>
- <span data-ttu-id="2c582-139">環境が `Development` である場合は、スコープの検証と[依存関係の検証](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild)を有効にします。</span><span class="sxs-lookup"><span data-stu-id="2c582-139">Enables scope validation and [dependency validation](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) when the environment is `Development`.</span></span>

<span data-ttu-id="2c582-140">`ConfigureServices` メソッドには、サービスを <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> インスタンスに追加する機能があります。</span><span class="sxs-lookup"><span data-stu-id="2c582-140">The `ConfigureServices` method exposes the ability to add services to the <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="2c582-141">これらのサービスは、後で、依存関係の挿入から使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2c582-141">Later, these services can be made available from dependency injection.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="2c582-142">フレームワークが提供するサービス</span><span class="sxs-lookup"><span data-stu-id="2c582-142">Framework-provided services</span></span>

<span data-ttu-id="2c582-143">以下のサービスは、自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-143">The following services are registered automatically:</span></span>

- [<span data-ttu-id="2c582-144">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="2c582-144">IHostApplicationLifetime</span></span>](#ihostapplicationlifetime)
- [<span data-ttu-id="2c582-145">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="2c582-145">IHostLifetime</span></span>](#ihostlifetime)
- [<span data-ttu-id="2c582-146">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="2c582-146">IHostEnvironment</span></span>](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a><span data-ttu-id="2c582-147">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="2c582-147">IHostApplicationLifetime</span></span>

<span data-ttu-id="2c582-148">起動後タスクとグレースフル シャットダウン タスクを処理するために <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> サービスを任意のクラスに注入します。</span><span class="sxs-lookup"><span data-stu-id="2c582-148">Inject the <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service into any class to handle post-startup and graceful shutdown tasks.</span></span> <span data-ttu-id="2c582-149">インターフェイス上の 3 つのプロパティは、アプリの起動およびアプリの停止のイベント ハンドラー メソッドを登録するために使用されるキャンセル トークンです。</span><span class="sxs-lookup"><span data-stu-id="2c582-149">Three properties on the interface are cancellation tokens used to register app start and app stop event handler methods.</span></span> <span data-ttu-id="2c582-150">インターフェイスには <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> メソッドも含まれています。</span><span class="sxs-lookup"><span data-stu-id="2c582-150">The interface also includes a <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> method.</span></span>

<span data-ttu-id="2c582-151">次の例は、`IHostApplicationLifetime` イベントを登録する `IHostedService` の実装です。</span><span class="sxs-lookup"><span data-stu-id="2c582-151">The following example is an `IHostedService` implementation that registers `IHostApplicationLifetime` events:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

<span data-ttu-id="2c582-152">`ExampleHostedService` 実装を追加するように Worker サービス テンプレートを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2c582-152">The Worker Service template could be modified to add the `ExampleHostedService` implementation:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

<span data-ttu-id="2c582-153">アプリケーションにより、次のサンプル出力が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="2c582-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a><span data-ttu-id="2c582-154">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="2c582-154">IHostLifetime</span></span>

<span data-ttu-id="2c582-155"><xref:Microsoft.Extensions.Hosting.IHostLifetime> 実装では、ホストを開始および停止するタイミングが制御されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-155">The <xref:Microsoft.Extensions.Hosting.IHostLifetime> implementation controls when the host starts and when it stops.</span></span> <span data-ttu-id="2c582-156">登録されている最後の実装が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-156">The last implementation registered is used.</span></span>

<span data-ttu-id="2c582-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` は、既定の `IHostLifetime` 実装です。</span><span class="sxs-lookup"><span data-stu-id="2c582-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` is the default `IHostLifetime` implementation.</span></span> <span data-ttu-id="2c582-158">`ConsoleLifetime`:</span><span class="sxs-lookup"><span data-stu-id="2c582-158">`ConsoleLifetime`:</span></span>

- <span data-ttu-id="2c582-159"><kbd>Ctrl</kbd>+<kbd>C</kbd>、[SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)、または [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) をリッスンし、<xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> を呼び出して、シャットダウン プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="2c582-159">Listens for <kbd>Ctrl</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT), or [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) and calls <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> to start the shutdown process.</span></span>
- <span data-ttu-id="2c582-160">`RunAsync` や `WaitForShutdownAsync` などの拡張機能のブロックを解除します。</span><span class="sxs-lookup"><span data-stu-id="2c582-160">Unblocks extensions such as `RunAsync` and `WaitForShutdownAsync`.</span></span>

## <a name="ihostenvironment"></a><span data-ttu-id="2c582-161">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="2c582-161">IHostEnvironment</span></span>

<span data-ttu-id="2c582-162">次の設定に関する情報を取得するため、クラスに <xref:Microsoft.Extensions.Hosting.IHostEnvironment> サービスを注入します。</span><span class="sxs-lookup"><span data-stu-id="2c582-162">Inject the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service into a class to get information about the following settings:</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a><span data-ttu-id="2c582-163">ホストの構成</span><span class="sxs-lookup"><span data-stu-id="2c582-163">Host configuration</span></span>

<span data-ttu-id="2c582-164">ホスト構成は、[IHostEnvironment](#ihostenvironment) 実装のプロパティを構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-164">Host configuration is used to configure properties of the [IHostEnvironment](#ihostenvironment) implementation.</span></span>

<span data-ttu-id="2c582-165">ホスト構成は、<xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> メソッド内の [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c582-165">The host configuration is available in [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) within the <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> method.</span></span> <span data-ttu-id="2c582-166">`ConfigureAppConfiguration` メソッドを呼び出すと、`HostBuilderContext` と `IConfigurationBuilder` が `configureDelegate` に渡されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-166">When calling the `ConfigureAppConfiguration` method, the `HostBuilderContext` and `IConfigurationBuilder` are passed into the `configureDelegate`.</span></span> <span data-ttu-id="2c582-167">`configureDelegate` は `Action<HostBuilderContext, IConfigurationBuilder>` として定義されています。</span><span class="sxs-lookup"><span data-stu-id="2c582-167">The `configureDelegate` is defined as an `Action<HostBuilderContext, IConfigurationBuilder>`.</span></span> <span data-ttu-id="2c582-168">このホスト ビルダー コンテキストには、`IConfiguration` のインスタンスである `.Configuration` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2c582-168">The host builder context exposes the `.Configuration` property, which is an instance of `IConfiguration`.</span></span> <span data-ttu-id="2c582-169">これはホストから構築された構成を表します。一方、`IConfigurationBuilder` はアプリの構成に使用されるビルダー オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="2c582-169">It represents the configuration built from the host, whereas the `IConfigurationBuilder` is the builder object used to configure the app.</span></span>

> [!TIP]
> <span data-ttu-id="2c582-170">`ConfigureAppConfiguration` が呼び出された後、`HostBuilderContext.Configuration` は[アプリの構成](#app-configuration)に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2c582-170">After `ConfigureAppConfiguration` is called the `HostBuilderContext.Configuration` is replaced with the [app config](#app-configuration).</span></span>

<span data-ttu-id="2c582-171">ホストの構成を追加するには、`IHostBuilder` 上で <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2c582-171">To add host configuration, call <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="2c582-172">`ConfigureHostConfiguration` を複数回呼び出して結果を追加できます。</span><span class="sxs-lookup"><span data-stu-id="2c582-172">`ConfigureHostConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="2c582-173">ホストは、指定されたキーで最後に値を設定したオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c582-173">The host uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="2c582-174">次の例では、ホストの構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="2c582-174">The following example creates host configuration:</span></span>

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="19-25":::

## <a name="app-configuration"></a><span data-ttu-id="2c582-175">アプリの構成</span><span class="sxs-lookup"><span data-stu-id="2c582-175">App configuration</span></span>

<span data-ttu-id="2c582-176">アプリの構成は、`IHostBuilder` 上で <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> を呼び出すことで作成されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-176">App configuration is created by calling <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="2c582-177">`ConfigureAppConfiguration` を複数回呼び出して結果を追加できます。</span><span class="sxs-lookup"><span data-stu-id="2c582-177">`ConfigureAppConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="2c582-178">アプリは、指定されたキーで最後に値を設定したオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c582-178">The app uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="2c582-179">`ConfigureAppConfiguration` によって作成された構成は、[ HostBuilderContext.Configuration ](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) で、以降の操作のために、かつ DI からのサービスとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="2c582-179">The configuration created by `ConfigureAppConfiguration` is available in [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) for subsequent operations and as a service from DI.</span></span> <span data-ttu-id="2c582-180">ホストの構成はアプリの構成にも追加されます。</span><span class="sxs-lookup"><span data-stu-id="2c582-180">The host configuration is also added to the app configuration.</span></span>

<span data-ttu-id="2c582-181">詳細については、「[.NET での構成](configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c582-181">For more information, see [Configuration in .NET](configuration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c582-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c582-182">See also</span></span>

- [<span data-ttu-id="2c582-183">.NET での構成</span><span class="sxs-lookup"><span data-stu-id="2c582-183">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="2c582-184">ASP.NET Core の Web ホスト</span><span class="sxs-lookup"><span data-stu-id="2c582-184">ASP.NET Core Web Host</span></span>](/aspnet/core/fundamentals/host/web-host)
- <span data-ttu-id="2c582-185">汎用ホストのバグは、[github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) リポジトリに作成する必要があります</span><span class="sxs-lookup"><span data-stu-id="2c582-185">Generic host bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
