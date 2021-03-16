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
# <a name="logging-providers-in-net"></a>.NET でのログ プロバイダー

ログ プロバイダーはログを保持します。ただし、`Console` プロバイダーはログを標準出力としてのみ表示します。 たとえば、Azure Application Insights プロバイダーでは、Azure Application Insights にログが保存されます。 複数のプロバイダーを有効にすることができます。

既定の .NET Worker アプリ テンプレート:

- [汎用ホスト](generic-host.md)が使用されます。
- <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> が呼び出されます。これにより、次のログ プロバイダーが追加されます。
  - [コンソール](#console)
  - [デバッグ](#debug)
  - [EventSource](#event-source)
  - [EventLog](#windows-eventlog):Windows のみ

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

上記のコードは、.NET Worker アプリ テンプレートを使用して作成された `Program` クラスを示しています。 以降のいくつかのセクションでは、汎用ホストを使用する .NET Worker アプリ テンプレートに基づくサンプルを提供します。

`Host.CreateDefaultBuilder` によって追加されたログ プロバイダーの既定のセットをオーバーライドするには、`ClearProviders` を呼び出し、必要なログ プロバイダーを追加します。 コード例を次に示します。

- <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> を呼び出して、ビルダーからすべての <xref:Microsoft.Extensions.Logging.ILoggerProvider> インスタンスを削除します。
- [Console](#console) ログ プロバイダーを追加します。

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

その他のプロバイダーについては、以下を参照してください。

- [組み込みのログ プロバイダー](#built-in-logging-providers)。
- [サードパーティ製のログ プロバイダー](#third-party-logging-providers)

## <a name="configure-a-service-that-depends-on-ilogger"></a>ILogger に依存するサービスを構成する

`ILogger<T>` に依存するサービスを構成するには、コンストラクターの挿入を使用するか、ファクトリ メソッドを指定します。 ファクトリ メソッドの方法は、他の選択肢がない場合にのみお勧めします。 たとえば、DI によって提供される `ILogger<T>` インスタンスを必要とするサービスについて考えてみます。

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

上記のコードは、DI コンテナーで `IExampleService` のインスタンスを初めて構築する必要があるときに実行される [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) です。 この方法では、任意の登録済みサービスにアクセスできます。

## <a name="built-in-logging-providers"></a>組み込みのログ プロバイダー

Microsoft 拡張機能には、ランタイム ライブラリの一部として次のログ プロバイダーが含まれています。

- [コンソール](#console)
- [デバッグ](#debug)
- [EventSource](#event-source)
- [EventLog](#windows-eventlog)

次のログ プロバイダーは、Microsoft によって出荷されますが、ランタイム ライブラリの一部としては提供されません。 これらは追加の NuGet パッケージとしてインストールする必要があります。

- [AzureAppServicesFile と AzureAppServicesBlob](#azure-app-service)
- [ApplicationInsights](#azure-application-insights)

### <a name="console"></a>コンソール

`Console` プロバイダーでは、コンソールへの出力がログに記録されます。

### <a name="debug"></a>デバッグ

`Debug` プロバイダーでは、[System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) クラスを使用してログ出力が書き込まれます。 `Debug` プロバイダーに書き込むために `System.Diagnostics.Debug.WriteLine` が呼び出されます。

Linux では、`Debug` プロバイダーのログの場所は配布によって異なり、次のいずれかになります。

- */var/log/message*
- */var/log/syslog*

### <a name="event-source"></a>イベント ソース

`EventSource` プロバイダーでは、`Microsoft-Extensions-Logging` という名前のクロスプラットフォーム イベント ソースに書き込まれます。 Windows では、プロバイダーによって [ETW](/windows/win32/etw/event-tracing-portal) が使用されます。

#### <a name="dotnet-trace-tooling"></a>dotnet trace ツール

[dotnet-trace](../diagnostics/dotnet-trace.md) ツールは、実行中のプロセスの .NET Core のトレースのコレクションを有効にする、クロスプラットフォームの CLI グローバル ツールです。 このツールでは、<xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> を使用して <xref:Microsoft.Extensions.Logging.EventSource> プロバイダー データを収集します。

インストール手順については、[dotnet-trace](../diagnostics/dotnet-trace.md) に関するページを参照してください。 `dotnet-trace` を使用した診断チュートリアルについては、「[.NET Core で高い CPU 使用率をデバッグする](../diagnostics/debug-highcpu.md)」を参照してください。

### <a name="windows-eventlog"></a>Windows EventLog

`EventLog` プロバイダーにより、ログ出力が Windows イベント ログに送信されます。 他のプロバイダーとは異なり、`EventLog` プロバイダーでは既定のプロバイダー以外の設定が継承 "***されません***"。 `EventLog` ログ設定が指定されていない場合は、既定の `LogLevel.Warning` になります。

<xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> より下のイベントをログに記録するには、ログ レベルを明示的に設定してください。 次の例では、イベント ログの既定のログ レベルを <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> に設定します。

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

[AddEventLog のオーバーロード](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions)を使用すると、<xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> を渡すことができます。 `null` または指定しない場合は、次の既定の設定が使用されます。

- `LogName`:"Application"
- `SourceName`: ".NET Runtime"
- `MachineName`:ローカル コンピューター名が使用されます。

次のコードでは、`SourceName` が既定値の `".NET Runtime"` から `CustomLogs` に変更されます。

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

### <a name="azure-app-service"></a>Azure App Service

[Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) プロバイダー パッケージは、Azure App Service アプリのファイル システムのテキスト ファイルと、Azure Storage アカウントの [BLOB ストレージ](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage)にログを書き込みます。

プロバイダー パッケージは、ランタイム ライブラリに含まれていません。 プロバイダーを使用するには、プロバイダー パッケージをプロジェクトに追加します。

プロバイダーの設定を構成するには、次の例のように <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> と <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions> を使用します。

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

Azure App Service にデプロイされると、Azure portal の **[App Service]** ページの [[App Service ログ]](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) セクションの設定がアプリで使用されます。 次の設定が更新されると、アプリの再起動や再デプロイを必要とせずに、変更がすぐに有効になります。

- **[アプリケーション ログ (ファイル システム)]**
- **[アプリケーション ログ (BLOB)]**

ログ ファイルの既定の場所は、*D:\\home\\LogFiles\\Application* です。既定のファイル名は *diagnostics-yyyymmdd.txt* です。 既定のファイル サイズ制限は 10 MB です。保持されるファイルの既定の最大数は 2 です。 既定の BLOB 名は *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt* です。

このプロバイダーは、プロジェクトが Azure 環境で実行される場合にのみログを記録します。

#### <a name="azure-log-streaming"></a>Azure ログのストリーミング

Azure ログのストリーミングでは、以下からのリアル タイムでのログ アクティビティの表示がサポートされています。

- アプリ サーバー
- Web サーバー
- 失敗した要求のトレース

Azure ログのストリーミングを構成するには

- アプリのポータル ページから **[App Service ログ]** ページに移動します。
- **[アプリケーション ログ (ファイル システム)]** を **[オン]** に設定します。
- ログ **[レベル]** を選択します。 この設定は、Azure ログ ストリーミングにのみ適用されます。

**[ログ ストリーム]** ページに移動して、ログを表示します。 ログに記録されたメッセージは、`ILogger` インターフェイスを使用してログに記録されます。

### <a name="azure-application-insights"></a>Azure Application Insights

[Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) プロバイダー パッケージでは、[Azure Application Insights](/azure/azure-monitor/app/cloudservices) にログが書き込まれます。 Application Insights は、Web アプリを監視するサービスであり、クエリを実行してテレメトリ データを分析するためのツールを提供します。 このプロバイダーを使用する場合は、Application Insights ツールを使ってクエリを実行し、ログを分析できます。

詳細については、次のリソースを参照してください。

- [Application Insights の概要](/azure/application-insights/app-insights-overview)
- [ApplicationInsightsLoggerProvider for .NET Core ILogger ログ](/azure/azure-monitor/app/ilogger) - ログ プロバイダーを実装し、Application Insights テレメトリのそれ以外の部分は除く場合は、ここから開始します。
- [Application Insights のログ アダプター](/azure/azure-monitor/app/asp-net-trace-logs)。
- [Application Insights SDK のインストール、構成、および初期化](/learn/modules/instrument-web-app-code-with-application-insights) - Microsoft Learn サイト上にある対話型のチュートリアルです。

## <a name="third-party-logging-providers"></a>サードパーティ製のログ プロバイダー

ここでは、さまざまな .NET ワークロードで使用できるサードパーティ製のログ記録フレームワークをいくつか紹介します。

- [elmah.io](https://elmah.io) ([GitHub リポジトリ](https://github.com/elmahio/Elmah.Io.Extensions.Logging))
- [Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub リポジトリ](https://github.com/mattwcole/gelf-extensions-logging))
- [JSNLog](http://jsnlog.com) ([GitHub リポジトリ](https://github.com/mperdeck/jsnlog))
- [KissLog.net](https://kisslog.net) ([GitHub リポジトリ](https://github.com/catalingavan/KissLog-net))
- [Log4Net](https://logging.apache.org/log4net) ([GitHub リポジトリ](https://github.com/apache/logging-log4net))
- [Loggr](https://loggr.net) ([GitHub リポジトリ](https://github.com/imobile3/Loggr.Extensions.Logging))
- [NLog](https://nlog-project.org) ([GitHub リポジトリ](https://github.com/NLog/NLog.Extensions.Logging))
- [NReco.Logging](https://github.com/nreco/logging/blob/master/README.md) ([GitHub リポジトリ](https://github.com/nreco/logging))
- [Sentry](https://sentry.io/welcome) ([GitHub リポジトリ](https://github.com/getsentry/sentry-dotnet))
- [Serilog](https://serilog.net) ([GitHub リポジトリ](https://github.com/serilog/serilog-sinks-console))
- [Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub リポジトリ](https://github.com/googleapis/google-cloud-dotnet))

一部のサードパーティ製フレームワークは、[セマンティック ログ記録 (構造化ログ記録とも呼ばれます)](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging) を実行できます。

サード パーティ製フレームワークを使用することは、組み込みのプロバイダーのいずれかを使用することと似ています。

1. プロジェクトに NuGet パッケージを追加します。
1. ログ記録フレームワークによって提供される `ILoggerFactory` または `ILoggingBuilder` 拡張メソッドを呼び出します。

詳細については、各プロバイダーのドキュメントをご覧ください。 サード パーティ製のログ プロバイダーは、Microsoft ではサポートされていません。

## <a name="see-also"></a>関連項目

- [.NET でのログ](logging.md)。
- [.NET にカスタム ログ プロバイダーを実装する](custom-logging-provider.md)。
- [.NET での高パフォーマンスのログ](high-performance-logging.md)。
