---
title: .NET でのログ プロバイダー
description: .NET アプリケーションでのログ プロバイダー API の使用方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 02/16/2021
ms.openlocfilehash: 7265e51a4d92cd99abebef2ebf0bc5db37b306e3
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "102402154"
---
# <a name="logging-providers-in-net"></a><span data-ttu-id="db77d-103">.NET でのログ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="db77d-103">Logging providers in .NET</span></span>

<span data-ttu-id="db77d-104">ログ プロバイダーはログを保持します。ただし、`Console` プロバイダーはログを標準出力としてのみ表示します。</span><span class="sxs-lookup"><span data-stu-id="db77d-104">Logging providers persist logs, except for the `Console` provider, which only displays logs as standard output.</span></span> <span data-ttu-id="db77d-105">たとえば、Azure Application Insights プロバイダーでは、Azure Application Insights にログが保存されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-105">For example, the Azure Application Insights provider stores logs in Azure Application Insights.</span></span> <span data-ttu-id="db77d-106">複数のプロバイダーを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="db77d-106">Multiple providers can be enabled.</span></span>

<span data-ttu-id="db77d-107">既定の .NET Worker アプリ テンプレート:</span><span class="sxs-lookup"><span data-stu-id="db77d-107">The default .NET Worker app templates:</span></span>

- <span data-ttu-id="db77d-108">[汎用ホスト](generic-host.md)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-108">Use the [Generic Host](generic-host.md).</span></span>
- <span data-ttu-id="db77d-109"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> が呼び出されます。これにより、次のログ プロバイダーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-109">Call <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, which adds the following logging providers:</span></span>
  - [<span data-ttu-id="db77d-110">コンソール</span><span class="sxs-lookup"><span data-stu-id="db77d-110">Console</span></span>](#console)
  - [<span data-ttu-id="db77d-111">デバッグ</span><span class="sxs-lookup"><span data-stu-id="db77d-111">Debug</span></span>](#debug)
  - [<span data-ttu-id="db77d-112">EventSource</span><span class="sxs-lookup"><span data-stu-id="db77d-112">EventSource</span></span>](#event-source)
  - <span data-ttu-id="db77d-113">[EventLog](#windows-eventlog):Windows のみ</span><span class="sxs-lookup"><span data-stu-id="db77d-113">[EventLog](#windows-eventlog): Windows only</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

<span data-ttu-id="db77d-114">上記のコードは、.NET Worker アプリ テンプレートを使用して作成された `Program` クラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="db77d-114">The preceding code shows the `Program` class created with the .NET Worker app templates.</span></span> <span data-ttu-id="db77d-115">以降のいくつかのセクションでは、汎用ホストを使用する .NET Worker アプリ テンプレートに基づくサンプルを提供します。</span><span class="sxs-lookup"><span data-stu-id="db77d-115">The next several sections provide samples based on the .NET Worker app templates, which use the Generic Host.</span></span>

<span data-ttu-id="db77d-116">`Host.CreateDefaultBuilder` によって追加されたログ プロバイダーの既定のセットをオーバーライドするには、`ClearProviders` を呼び出し、必要なログ プロバイダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="db77d-116">To override the default set of logging providers added by `Host.CreateDefaultBuilder`, call `ClearProviders` and add the logging providers you want.</span></span> <span data-ttu-id="db77d-117">コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="db77d-117">For example, the following code:</span></span>

- <span data-ttu-id="db77d-118"><xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> を呼び出して、ビルダーからすべての <xref:Microsoft.Extensions.Logging.ILoggerProvider> インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="db77d-118">Calls <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> to remove all the <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances from the builder.</span></span>
- <span data-ttu-id="db77d-119">[Console](#console) ログ プロバイダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="db77d-119">Adds the [Console](#console) logging provider.</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

<span data-ttu-id="db77d-120">その他のプロバイダーについては、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db77d-120">For additional providers, see:</span></span>

- <span data-ttu-id="db77d-121">[組み込みのログ プロバイダー](#built-in-logging-providers)。</span><span class="sxs-lookup"><span data-stu-id="db77d-121">[Built-in logging providers](#built-in-logging-providers).</span></span>
- <span data-ttu-id="db77d-122">[サードパーティ製のログ プロバイダー](#third-party-logging-providers)</span><span class="sxs-lookup"><span data-stu-id="db77d-122">[Third-party logging providers](#third-party-logging-providers).</span></span>

## <a name="configure-a-service-that-depends-on-ilogger"></a><span data-ttu-id="db77d-123">ILogger に依存するサービスを構成する</span><span class="sxs-lookup"><span data-stu-id="db77d-123">Configure a service that depends on ILogger</span></span>

<span data-ttu-id="db77d-124">`ILogger<T>` に依存するサービスを構成するには、コンストラクターの挿入を使用するか、ファクトリ メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="db77d-124">To configure a service that depends on `ILogger<T>`, use constructor injection or provide a factory method.</span></span> <span data-ttu-id="db77d-125">ファクトリ メソッドの方法は、他の選択肢がない場合にのみお勧めします。</span><span class="sxs-lookup"><span data-stu-id="db77d-125">The factory method approach is recommended only if there is no other option.</span></span> <span data-ttu-id="db77d-126">たとえば、DI によって提供される `ILogger<T>` インスタンスを必要とするサービスについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="db77d-126">For example, consider a service that needs an `ILogger<T>` instance provided by DI:</span></span>

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

<span data-ttu-id="db77d-127">上記のコードは、DI コンテナーで `IExampleService` のインスタンスを初めて構築する必要があるときに実行される [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) です。</span><span class="sxs-lookup"><span data-stu-id="db77d-127">The preceding code is a [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) that runs the first time the DI container needs to construct an instance of `IExampleService`.</span></span> <span data-ttu-id="db77d-128">この方法では、任意の登録済みサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="db77d-128">You can access any of the registered services in this way.</span></span>

## <a name="built-in-logging-providers"></a><span data-ttu-id="db77d-129">組み込みのログ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="db77d-129">Built-in logging providers</span></span>

<span data-ttu-id="db77d-130">Microsoft 拡張機能には、ランタイム ライブラリの一部として次のログ プロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="db77d-130">Microsoft Extensions include the following logging providers as part of the runtime libraries:</span></span>

- [<span data-ttu-id="db77d-131">コンソール</span><span class="sxs-lookup"><span data-stu-id="db77d-131">Console</span></span>](#console)
- [<span data-ttu-id="db77d-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="db77d-132">Debug</span></span>](#debug)
- [<span data-ttu-id="db77d-133">EventSource</span><span class="sxs-lookup"><span data-stu-id="db77d-133">EventSource</span></span>](#event-source)
- [<span data-ttu-id="db77d-134">EventLog</span><span class="sxs-lookup"><span data-stu-id="db77d-134">EventLog</span></span>](#windows-eventlog)

<span data-ttu-id="db77d-135">次のログ プロバイダーは、Microsoft によって出荷されますが、ランタイム ライブラリの一部としては提供されません。</span><span class="sxs-lookup"><span data-stu-id="db77d-135">The following logging providers are shipped by Microsoft, but not as part of the runtime libraries.</span></span> <span data-ttu-id="db77d-136">これらは追加の NuGet パッケージとしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="db77d-136">They must be installed as additional NuGet packages.</span></span>

- [<span data-ttu-id="db77d-137">AzureAppServicesFile と AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="db77d-137">AzureAppServicesFile and AzureAppServicesBlob</span></span>](#azure-app-service)
- [<span data-ttu-id="db77d-138">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="db77d-138">ApplicationInsights</span></span>](#azure-application-insights)

### <a name="console"></a><span data-ttu-id="db77d-139">コンソール</span><span class="sxs-lookup"><span data-stu-id="db77d-139">Console</span></span>

<span data-ttu-id="db77d-140">`Console` プロバイダーでは、コンソールへの出力がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-140">The `Console` provider logs output to the console.</span></span>

### <a name="debug"></a><span data-ttu-id="db77d-141">デバッグ</span><span class="sxs-lookup"><span data-stu-id="db77d-141">Debug</span></span>

<span data-ttu-id="db77d-142">`Debug` プロバイダーでは、[System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) クラスを使用してログ出力が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="db77d-142">The `Debug` provider writes log output by using the [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) class.</span></span> <span data-ttu-id="db77d-143">`Debug` プロバイダーに書き込むために `System.Diagnostics.Debug.WriteLine` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-143">Calls to `System.Diagnostics.Debug.WriteLine` write to the `Debug` provider.</span></span>

<span data-ttu-id="db77d-144">Linux では、`Debug` プロバイダーのログの場所は配布によって異なり、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="db77d-144">On Linux, the `Debug` provider log location is distribution-dependent and may be one of the following:</span></span>

- <span data-ttu-id="db77d-145">*/var/log/message*</span><span class="sxs-lookup"><span data-stu-id="db77d-145">*/var/log/message*</span></span>
- <span data-ttu-id="db77d-146">*/var/log/syslog*</span><span class="sxs-lookup"><span data-stu-id="db77d-146">*/var/log/syslog*</span></span>

### <a name="event-source"></a><span data-ttu-id="db77d-147">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="db77d-147">Event Source</span></span>

<span data-ttu-id="db77d-148">`EventSource` プロバイダーでは、`Microsoft-Extensions-Logging` という名前のクロスプラットフォーム イベント ソースに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="db77d-148">The `EventSource` provider writes to a cross-platform event source with the name `Microsoft-Extensions-Logging`.</span></span> <span data-ttu-id="db77d-149">Windows では、プロバイダーによって [ETW](/windows/win32/etw/event-tracing-portal) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-149">On Windows, the provider uses [ETW](/windows/win32/etw/event-tracing-portal).</span></span>

#### <a name="dotnet-trace-tooling"></a><span data-ttu-id="db77d-150">dotnet trace ツール</span><span class="sxs-lookup"><span data-stu-id="db77d-150">dotnet trace tooling</span></span>

<span data-ttu-id="db77d-151">[dotnet-trace](../diagnostics/dotnet-trace.md) ツールは、実行中のプロセスの .NET Core のトレースのコレクションを有効にする、クロスプラットフォームの CLI グローバル ツールです。</span><span class="sxs-lookup"><span data-stu-id="db77d-151">The [dotnet-trace](../diagnostics/dotnet-trace.md) tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process.</span></span> <span data-ttu-id="db77d-152">このツールでは、<xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> を使用して <xref:Microsoft.Extensions.Logging.EventSource> プロバイダー データを収集します。</span><span class="sxs-lookup"><span data-stu-id="db77d-152">The tool collects <xref:Microsoft.Extensions.Logging.EventSource> provider data using a <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.</span></span>

<span data-ttu-id="db77d-153">インストール手順については、[dotnet-trace](../diagnostics/dotnet-trace.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="db77d-153">See [dotnet-trace](../diagnostics/dotnet-trace.md) for installation instructions.</span></span> <span data-ttu-id="db77d-154">`dotnet-trace` を使用した診断チュートリアルについては、「[.NET Core で高い CPU 使用率をデバッグする](../diagnostics/debug-highcpu.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db77d-154">For a diagnostic tutorial using `dotnet-trace`, see [Debug high CPU usage in .NET Core](../diagnostics/debug-highcpu.md).</span></span>

### <a name="windows-eventlog"></a><span data-ttu-id="db77d-155">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="db77d-155">Windows EventLog</span></span>

<span data-ttu-id="db77d-156">`EventLog` プロバイダーにより、ログ出力が Windows イベント ログに送信されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-156">The `EventLog` provider sends log output to the Windows Event Log.</span></span> <span data-ttu-id="db77d-157">他のプロバイダーとは異なり、`EventLog` プロバイダーでは既定のプロバイダー以外の設定が継承 "***されません***"。</span><span class="sxs-lookup"><span data-stu-id="db77d-157">Unlike the other providers, the `EventLog` provider does ***not*** inherit the default non-provider settings.</span></span> <span data-ttu-id="db77d-158">`EventLog` ログ設定が指定されていない場合は、既定の `LogLevel.Warning` になります。</span><span class="sxs-lookup"><span data-stu-id="db77d-158">If `EventLog` log settings aren't specified, they default to `LogLevel.Warning`.</span></span>

<span data-ttu-id="db77d-159"><xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> より下のイベントをログに記録するには、ログ レベルを明示的に設定してください。</span><span class="sxs-lookup"><span data-stu-id="db77d-159">To log events lower than <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, explicitly set the log level.</span></span> <span data-ttu-id="db77d-160">次の例では、イベント ログの既定のログ レベルを <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="db77d-160">The following example sets the Event Log default log level to <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:</span></span>

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

<span data-ttu-id="db77d-161">[AddEventLog のオーバーロード](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions)を使用すると、<xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="db77d-161">[AddEventLog overloads](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) can pass in <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>.</span></span> <span data-ttu-id="db77d-162">`null` または指定しない場合は、次の既定の設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-162">If `null` or not specified, the following default settings are used:</span></span>

- <span data-ttu-id="db77d-163">`LogName`:"Application"</span><span class="sxs-lookup"><span data-stu-id="db77d-163">`LogName`: "Application"</span></span>
- <span data-ttu-id="db77d-164">`SourceName`: ".NET Runtime"</span><span class="sxs-lookup"><span data-stu-id="db77d-164">`SourceName`: ".NET Runtime"</span></span>
- <span data-ttu-id="db77d-165">`MachineName`:ローカル コンピューター名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-165">`MachineName`: The local machine name is used.</span></span>

<span data-ttu-id="db77d-166">次のコードでは、`SourceName` が既定値の `".NET Runtime"` から `CustomLogs` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-166">The following code changes the `SourceName` from the default value of `".NET Runtime"` to `CustomLogs`:</span></span>

```csharp
public class Program
{
    static async Task Main(string[] args)
    {
        using IHost host = CreateHostBuilder(args).Build();

        // Application code should start here.

        await host.RunAsync();
    }

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddEventLog(configuration =>
                    configuration.SourceName = "CustomLogs"));
}
```

### <a name="azure-app-service"></a><span data-ttu-id="db77d-167">Azure App Service</span><span class="sxs-lookup"><span data-stu-id="db77d-167">Azure App Service</span></span>

<span data-ttu-id="db77d-168">[Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) プロバイダー パッケージは、Azure App Service アプリのファイル システムのテキスト ファイルと、Azure Storage アカウントの [BLOB ストレージ](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage)にログを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="db77d-168">The [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) provider package writes logs to text files in an Azure App Service app's file system and to [blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) in an Azure Storage account.</span></span>

<span data-ttu-id="db77d-169">プロバイダー パッケージは、ランタイム ライブラリに含まれていません。</span><span class="sxs-lookup"><span data-stu-id="db77d-169">The provider package isn't included in the runtime libraries.</span></span> <span data-ttu-id="db77d-170">プロバイダーを使用するには、プロバイダー パッケージをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="db77d-170">To use the provider, add the provider package to the project.</span></span>

<span data-ttu-id="db77d-171">プロバイダーの設定を構成するには、次の例のように <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> と <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions> を使用します。</span><span class="sxs-lookup"><span data-stu-id="db77d-171">To configure provider settings, use <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> and <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, as shown in the following example:</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using IHost host = CreateHostBuilder(args).Build();

        // Application code should start here.

        await host.RunAsync();
    }

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddAzureWebAppDiagnostics())
            .ConfigureServices(services =>
                services.Configure<AzureFileLoggerOptions>(options =>
                {
                    options.FileName = "azure-diagnostics-";
                    options.FileSizeLimit = 50 * 1024;
                    options.RetainedFileCountLimit = 5;
                })
                .Configure<AzureBlobLoggerOptions>(options =>
                {
                    options.BlobName = "log.txt";
                }));
}
```

<span data-ttu-id="db77d-172">Azure App Service にデプロイされると、Azure portal の **[App Service]** ページの [[App Service ログ]](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) セクションの設定がアプリで使用されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-172">When deployed to Azure App Service, the app uses the settings in the [App Service logs](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) section of the **App Service** page of the Azure portal.</span></span> <span data-ttu-id="db77d-173">次の設定が更新されると、アプリの再起動や再デプロイを必要とせずに、変更がすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="db77d-173">When the following settings are updated, the changes take effect immediately without requiring a restart or redeployment of the app.</span></span>

- <span data-ttu-id="db77d-174">**[アプリケーション ログ (ファイル システム)]**</span><span class="sxs-lookup"><span data-stu-id="db77d-174">**Application Logging (Filesystem)**</span></span>
- <span data-ttu-id="db77d-175">**[アプリケーション ログ (BLOB)]**</span><span class="sxs-lookup"><span data-stu-id="db77d-175">**Application Logging (Blob)**</span></span>

<span data-ttu-id="db77d-176">ログ ファイルの既定の場所は、*D:\\home\\LogFiles\\Application* です。既定のファイル名は *diagnostics-yyyymmdd.txt* です。</span><span class="sxs-lookup"><span data-stu-id="db77d-176">The default location for log files is in the *D:\\home\\LogFiles\\Application* folder, and the default file name is *diagnostics-yyyymmdd.txt*.</span></span> <span data-ttu-id="db77d-177">既定のファイル サイズ制限は 10 MB です。保持されるファイルの既定の最大数は 2 です。</span><span class="sxs-lookup"><span data-stu-id="db77d-177">The default file size limit is 10 MB, and the default maximum number of files retained is 2.</span></span> <span data-ttu-id="db77d-178">既定の BLOB 名は *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt* です。</span><span class="sxs-lookup"><span data-stu-id="db77d-178">The default blob name is *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.</span></span>

<span data-ttu-id="db77d-179">このプロバイダーは、プロジェクトが Azure 環境で実行される場合にのみログを記録します。</span><span class="sxs-lookup"><span data-stu-id="db77d-179">This provider only logs when the project runs in the Azure environment.</span></span>

#### <a name="azure-log-streaming"></a><span data-ttu-id="db77d-180">Azure ログのストリーミング</span><span class="sxs-lookup"><span data-stu-id="db77d-180">Azure log streaming</span></span>

<span data-ttu-id="db77d-181">Azure ログのストリーミングでは、以下からのリアル タイムでのログ アクティビティの表示がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="db77d-181">Azure log streaming supports viewing log activity in real time from:</span></span>

- <span data-ttu-id="db77d-182">アプリ サーバー</span><span class="sxs-lookup"><span data-stu-id="db77d-182">The app server</span></span>
- <span data-ttu-id="db77d-183">Web サーバー</span><span class="sxs-lookup"><span data-stu-id="db77d-183">The web server</span></span>
- <span data-ttu-id="db77d-184">失敗した要求のトレース</span><span class="sxs-lookup"><span data-stu-id="db77d-184">Failed request tracing</span></span>

<span data-ttu-id="db77d-185">Azure ログのストリーミングを構成するには</span><span class="sxs-lookup"><span data-stu-id="db77d-185">To configure Azure log streaming:</span></span>

- <span data-ttu-id="db77d-186">アプリのポータル ページから **[App Service ログ]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="db77d-186">Navigate to the **App Service logs** page from the app's portal page.</span></span>
- <span data-ttu-id="db77d-187">**[アプリケーション ログ (ファイル システム)]** を **[オン]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="db77d-187">Set **Application Logging (Filesystem)** to **On**.</span></span>
- <span data-ttu-id="db77d-188">ログ **[レベル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="db77d-188">Choose the log **Level**.</span></span> <span data-ttu-id="db77d-189">この設定は、Azure ログ ストリーミングにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-189">This setting only applies to Azure log streaming.</span></span>

<span data-ttu-id="db77d-190">**[ログ ストリーム]** ページに移動して、ログを表示します。</span><span class="sxs-lookup"><span data-stu-id="db77d-190">Navigate to the **Log Stream** page to view logs.</span></span> <span data-ttu-id="db77d-191">ログに記録されたメッセージは、`ILogger` インターフェイスを使用してログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="db77d-191">The logged messages are logged with the `ILogger` interface.</span></span>

### <a name="azure-application-insights"></a><span data-ttu-id="db77d-192">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="db77d-192">Azure Application Insights</span></span>

<span data-ttu-id="db77d-193">[Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) プロバイダー パッケージでは、[Azure Application Insights](/azure/azure-monitor/app/cloudservices) にログが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="db77d-193">The [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) provider package writes logs to [Azure Application Insights](/azure/azure-monitor/app/cloudservices).</span></span> <span data-ttu-id="db77d-194">Application Insights は、Web アプリを監視するサービスであり、クエリを実行してテレメトリ データを分析するためのツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="db77d-194">Application Insights is a service that monitors a web app and provides tools for querying and analyzing the telemetry data.</span></span> <span data-ttu-id="db77d-195">このプロバイダーを使用する場合は、Application Insights ツールを使ってクエリを実行し、ログを分析できます。</span><span class="sxs-lookup"><span data-stu-id="db77d-195">If you use this provider, you can query and analyze your logs by using the Application Insights tools.</span></span>

<span data-ttu-id="db77d-196">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="db77d-196">For more information, see the following resources:</span></span>

- [<span data-ttu-id="db77d-197">Application Insights の概要</span><span class="sxs-lookup"><span data-stu-id="db77d-197">Application Insights overview</span></span>](/azure/application-insights/app-insights-overview)
- <span data-ttu-id="db77d-198">[ApplicationInsightsLoggerProvider for .NET Core ILogger ログ](/azure/azure-monitor/app/ilogger) - ログ プロバイダーを実装し、Application Insights テレメトリのそれ以外の部分は除く場合は、ここから開始します。</span><span class="sxs-lookup"><span data-stu-id="db77d-198">[ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) - Start here if you want to implement the logging provider without the rest of Application Insights telemetry.</span></span>
- <span data-ttu-id="db77d-199">[Application Insights のログ アダプター](/azure/azure-monitor/app/asp-net-trace-logs)。</span><span class="sxs-lookup"><span data-stu-id="db77d-199">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs).</span></span>
- <span data-ttu-id="db77d-200">[Application Insights SDK のインストール、構成、および初期化](/learn/modules/instrument-web-app-code-with-application-insights) - Microsoft Learn サイト上にある対話型のチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="db77d-200">[Install, configure, and initialize the Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights) - Interactive tutorial on the Microsoft Learn site.</span></span>

## <a name="third-party-logging-providers"></a><span data-ttu-id="db77d-201">サードパーティ製のログ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="db77d-201">Third-party logging providers</span></span>

<span data-ttu-id="db77d-202">ここでは、さまざまな .NET ワークロードで使用できるサードパーティ製のログ記録フレームワークをいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="db77d-202">Here are some third-party logging frameworks that work with various .NET workloads:</span></span>

- <span data-ttu-id="db77d-203">[elmah.io](https://elmah.io) ([GitHub リポジトリ](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="db77d-203">[elmah.io](https://elmah.io) ([GitHub repo](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span></span>
- <span data-ttu-id="db77d-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub リポジトリ](https://github.com/mattwcole/gelf-extensions-logging))</span><span class="sxs-lookup"><span data-stu-id="db77d-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub repo](https://github.com/mattwcole/gelf-extensions-logging))</span></span>
- <span data-ttu-id="db77d-205">[JSNLog](http://jsnlog.com) ([GitHub リポジトリ](https://github.com/mperdeck/jsnlog))</span><span class="sxs-lookup"><span data-stu-id="db77d-205">[JSNLog](http://jsnlog.com) ([GitHub repo](https://github.com/mperdeck/jsnlog))</span></span>
- <span data-ttu-id="db77d-206">[KissLog.net](https://kisslog.net) ([GitHub リポジトリ](https://github.com/catalingavan/KissLog-net))</span><span class="sxs-lookup"><span data-stu-id="db77d-206">[KissLog.net](https://kisslog.net) ([GitHub repo](https://github.com/catalingavan/KissLog-net))</span></span>
- <span data-ttu-id="db77d-207">[Log4Net](https://logging.apache.org/log4net) ([GitHub リポジトリ](https://github.com/apache/logging-log4net))</span><span class="sxs-lookup"><span data-stu-id="db77d-207">[Log4Net](https://logging.apache.org/log4net) ([GitHub repo](https://github.com/apache/logging-log4net))</span></span>
- <span data-ttu-id="db77d-208">[Loggr](https://loggr.net) ([GitHub リポジトリ](https://github.com/imobile3/Loggr.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="db77d-208">[Loggr](https://loggr.net) ([GitHub repo](https://github.com/imobile3/Loggr.Extensions.Logging))</span></span>
- <span data-ttu-id="db77d-209">[NLog](https://nlog-project.org) ([GitHub リポジトリ](https://github.com/NLog/NLog.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="db77d-209">[NLog](https://nlog-project.org) ([GitHub repo](https://github.com/NLog/NLog.Extensions.Logging))</span></span>
- <span data-ttu-id="db77d-210">[NReco.Logging](https://github.com/nreco/logging/blob/master/README.md) ([GitHub リポジトリ](https://github.com/nreco/logging))</span><span class="sxs-lookup"><span data-stu-id="db77d-210">[NReco.Logging](https://github.com/nreco/logging/blob/master/README.md) ([GitHub repo](https://github.com/nreco/logging))</span></span>
- <span data-ttu-id="db77d-211">[Sentry](https://sentry.io/welcome) ([GitHub リポジトリ](https://github.com/getsentry/sentry-dotnet))</span><span class="sxs-lookup"><span data-stu-id="db77d-211">[Sentry](https://sentry.io/welcome) ([GitHub repo](https://github.com/getsentry/sentry-dotnet))</span></span>
- <span data-ttu-id="db77d-212">[Serilog](https://serilog.net) ([GitHub リポジトリ](https://github.com/serilog/serilog-sinks-console))</span><span class="sxs-lookup"><span data-stu-id="db77d-212">[Serilog](https://serilog.net) ([GitHub repo](https://github.com/serilog/serilog-sinks-console))</span></span>
- <span data-ttu-id="db77d-213">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub リポジトリ](https://github.com/googleapis/google-cloud-dotnet))</span><span class="sxs-lookup"><span data-stu-id="db77d-213">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub repo](https://github.com/googleapis/google-cloud-dotnet))</span></span>

<span data-ttu-id="db77d-214">一部のサードパーティ製フレームワークは、[セマンティック ログ記録 (構造化ログ記録とも呼ばれます)](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging) を実行できます。</span><span class="sxs-lookup"><span data-stu-id="db77d-214">Some third-party frameworks can perform [semantic logging, also known as structured logging](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span></span>

<span data-ttu-id="db77d-215">サード パーティ製フレームワークを使用することは、組み込みのプロバイダーのいずれかを使用することと似ています。</span><span class="sxs-lookup"><span data-stu-id="db77d-215">Using a third-party framework is similar to using one of the built-in providers:</span></span>

1. <span data-ttu-id="db77d-216">プロジェクトに NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="db77d-216">Add a NuGet package to your project.</span></span>
1. <span data-ttu-id="db77d-217">ログ記録フレームワークによって提供される `ILoggerFactory` または `ILoggingBuilder` 拡張メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="db77d-217">Call an `ILoggerFactory` or `ILoggingBuilder` extension method provided by the logging framework.</span></span>

<span data-ttu-id="db77d-218">詳細については、各プロバイダーのドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="db77d-218">For more information, see each provider's documentation.</span></span> <span data-ttu-id="db77d-219">サード パーティ製のログ プロバイダーは、Microsoft ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db77d-219">Third-party logging providers aren't supported by Microsoft.</span></span>

## <a name="see-also"></a><span data-ttu-id="db77d-220">関連項目</span><span class="sxs-lookup"><span data-stu-id="db77d-220">See also</span></span>

- <span data-ttu-id="db77d-221">[.NET でのログ](logging.md)。</span><span class="sxs-lookup"><span data-stu-id="db77d-221">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="db77d-222">[.NET にカスタム ログ プロバイダーを実装する](custom-logging-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="db77d-222">[Implement a custom logging provider in .NET](custom-logging-provider.md).</span></span>
- <span data-ttu-id="db77d-223">[.NET での高パフォーマンスのログ](high-performance-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="db77d-223">[High-performance logging in .NET](high-performance-logging.md).</span></span>
