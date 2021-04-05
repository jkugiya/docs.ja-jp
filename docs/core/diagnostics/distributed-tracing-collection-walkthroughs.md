---
title: 分散トレースを収集する - .NET
description: OpenTelemetry、Application Insights、または ActivityListener を使用して .NET アプリケーションの分散トレースを収集するためのチュートリアル
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: f5e2ea6dc09edbc7c51586f4da8d4a6088804cbd
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111520"
---
# <a name="collect-a-distributed-trace"></a>分散トレースを収集する

**この記事の対象: ✔️** .NET Core 2.1 以降のバージョン **および** .NET Framework 4.5 以降のバージョン

インストルメント化されたコードは、分散トレースの一部として <xref:System.Diagnostics.Activity> オブジェクトを作成できますが、後でトレース全体を確認できるように、これらのオブジェクトの情報を集中ストレージに収集する必要があります。 このチュートリアルでは、必要に応じてアプリケーションの問題を診断できるように、分散トレースのテレメトリをさまざまな方法で収集します。 新しいインストルメンテーションを追加する必要がある場合は、[インストルメンテーションのチュートリアル](distributed-tracing-instrumentation-walkthroughs.md)を参照してください。

## <a name="collect-traces-using-opentelemetry"></a>OpenTelemetry を使用してトレースを収集する

### <a name="prerequisites"></a>前提条件

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン

### <a name="create-an-example-application"></a>サンプル アプリケーションを作成する

分散トレースのテレメトリを収集するには、それを生成する必要があります。 多くの場合、このインストルメンテーションはライブラリに含まれていますが、わかりやすくするために、<xref:System.Diagnostics.ActivitySource.StartActivity%2A> を使用して、インストルメンテーションの例を含む小さなアプリを作成します。 この時点では、まだ収集が行われていません。StartActivity () による影響はなく、null 値が返されます。 詳細については、[インストルメンテーションのチュートリアル](distributed-tracing-instrumentation-walkthroughs.md)を参照してください。

```dotnetcli
dotnet new console
```

.NET 5 以降をターゲットとするアプリケーションには、必要な分散トレース API が既に含まれています。 以前のバージョンの .NET をターゲットとするアプリの場合は、[System.Diagnostics.DiagnosticSource NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) バージョン 5 以降を追加します。

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

生成された Program.cs の内容を次のソース例に置き換えます。

```C#
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");

        static async Task Main(string[] args)
        {
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }

        static async Task DoSomeWork()
        {
            using (Activity a = s_source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }

        static async Task StepOne()
        {
            using (Activity a = s_source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity a = s_source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
    }
}
```

アプリを実行しても、まだトレース データは収集されません。

```dotnetcli
> dotnet run
Example work done
```

### <a name="collect-using-opentelemetry"></a>OpenTelemetry を使用して収集する

[OpenTelemetry](https://opentelemetry.io/) は、クラウドネイティブのソフトウェアのテレメトリの生成と収集を標準化することを目的とした、[Cloud Native Computing Foundation](https://www.cncf.io/) によりサポートされる、ベンダーに依存しないオープン ソース プロジェクトです。 この例では、分散トレース情報を収集してコンソールに表示しますが、OpenTelemetry を再構成して別の場所に送信することもできます。 詳細については、[OpenTelemetry の概要ガイド](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md)を参照してください。

[OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet パッケージを追加します。

```dotnetcli
dotnet add package OpenTelemetry.Exporter.Console
```

OpenTelemetry の追加の using ステートメントを使用して、Program.cs を更新します。

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;
```

Main () を更新して、OpenTelemetry の TracerProvider を作成します。

```C#
        public static async Task Main()
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork();
            Console.WriteLine("Example work done");
        }
```

これで、アプリは分散トレース情報を収集して、コンソールに表示します。

```dotnetcli
> dotnet run
Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-6081a9b8041cd840-01
Activity.ParentId:    00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:46.8649754Z
Activity.Duration:    00:00:00.5069226
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-d2b283db91cf774c-01
Activity.ParentId:    00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:47.3838737Z
Activity.Duration:    00:00:01.0142278
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:46.8634510Z
Activity.Duration:    00:00:01.5402045
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Example work done
```

#### <a name="sources"></a>変換元

次のコード例では、OpenTelemetry がコード内に既に存在する ActivitySource によって生成されたアクティビティをキャプチャするように、`AddSource("Sample.DistributedTracing")` を呼び出しています。

```csharp
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");
```

任意の ActivitySource からのテレメトリは、ソース名を指定して AddSource () を呼び出すことによってキャプチャできます。

#### <a name="exporters"></a>エクスポーター

コンソール エクスポーターは、簡単な例やローカル開発に役立ちますが、運用環境の展開では、集中管理されたストアにトレースを送信することをお勧めします。 OpenTelemetry では、異なる[エクスポーター](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library)を使用したさまざまな送信先がサポートされています。
OpenTelemetry の構成の詳細については、[OpenTelemetry の概要ガイド](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started)を参照してください。

## <a name="collect-traces-using-application-insights"></a>Application Insights を使用してトレースを収集する

分散トレースのテレメトリは、Application Insights SDK ([ASP.NET](https://docs.microsoft.com/azure/azure-monitor/app/asp-net)、[ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) を構成した後、または[コードのないインストルメンテーション](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview)を有効にした後に自動的にキャプチャされます。

詳細については、[Application Insights の分散トレースのドキュメント](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing)を参照してください。

> [!NOTE]
> 現在 Application Insights は、特定の既知のアクティビティ インストルメンテーションの収集のみがサポートされ、ユーザーが追加した新しいアクティビティは無視されます。 Application Insights には、カスタム分散トレース情報を追加するためのベンダー固有の API として [TrackDependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) が用意されています。

## <a name="collect-traces-using-custom-logic"></a>カスタム ロジックを使用してトレースを収集する

開発者は、アクティビティ トレース データ用にカスタマイズされた独自の収集ロジックを自由に作成できます。 この例では、.NET によって提供される <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> API を使用してテレメトリを収集し、コンソールに出力しています。

### <a name="prerequisites"></a>前提条件

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン

### <a name="create-an-example-application"></a>サンプル アプリケーションを作成する

まず、いくつかの分散トレース インストルメンテーションを含むサンプル アプリケーションを作成しますが、トレース データは収集されません。

```dotnetcli
dotnet new console
```

.NET 5 以降をターゲットとするアプリケーションには、必要な分散トレース API が既に含まれています。 以前のバージョンの .NET をターゲットとするアプリの場合は、[System.Diagnostics.DiagnosticSource NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) バージョン 5 以降を追加します。

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

生成された Program.cs の内容を次のソース例に置き換えます。

```C#
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");

        static async Task Main(string[] args)
        {
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }

        static async Task DoSomeWork()
        {
            using (Activity a = s_source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }

        static async Task StepOne()
        {
            using (Activity a = s_source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity a = s_source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
    }
}
```

アプリを実行しても、まだトレース データは収集されません。

```dotnetcli
> dotnet run
Example work done
```

### <a name="add-code-to-collect-the-traces"></a>トレースを収集するためのコードを追加する

次のコードで Main() を更新します。

```C#
        static async Task Main(string[] args)
        {
            Activity.DefaultIdFormat = ActivityIdFormat.W3C;
            Activity.ForceDefaultIdFormat = true;

            Console.WriteLine("         {0,-15} {1,-60} {2,-15}", "OperationName", "Id", "Duration");
            ActivitySource.AddActivityListener(new ActivityListener()
            {
                ShouldListenTo = (source) => true,
                Sample = (ref ActivityCreationOptions<ActivityContext> options) => ActivitySamplingResult.AllDataAndRecorded,
                ActivityStarted = activity => Console.WriteLine("Started: {0,-15} {1,-60}", activity.OperationName, activity.Id),
                ActivityStopped = activity => Console.WriteLine("Stopped: {0,-15} {1,-60} {2,-15}", activity.OperationName, activity.Id, activity.Duration)
            });
            
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }
```

出力にログが含まれるようになりました。

```dotnetcli
> dotnet run
         OperationName   Id                                                           Duration
Started: SomeWork        00-bdb5faffc2fc1548b6ba49a31c4a0ae0-c447fb302059784f-01
Started: StepOne         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-a7c77a4e9a02dc4a-01
Stopped: StepOne         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-a7c77a4e9a02dc4a-01      00:00:00.5093849
Started: StepTwo         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-9210ad536cae9e4e-01
Stopped: StepTwo         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-9210ad536cae9e4e-01      00:00:01.0111847
Stopped: SomeWork        00-bdb5faffc2fc1548b6ba49a31c4a0ae0-c447fb302059784f-01      00:00:01.5236391
Example work done
```

<xref:System.Diagnostics.Activity.DefaultIdFormat> と <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> の設定は省略可能ですが、これは .NET ランタイム バージョンが違ってもサンプルで確実に同様の出力が生成されるようにするのに役立ちます。 .NET 5 では、既定で W3C TraceContext ID 形式が使用されますが、以前のバージョンの .NET では既定で <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID 形式が使用されます。 詳細については、「[アクティビティ ID](distributed-tracing-concepts.md#activity-ids)」を参照してください。

<xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> は、アクティビティの有効期間中にコールバックを受信するために使用されます。

- <xref:System.Diagnostics.ActivityListener.ShouldListenTo> - 各アクティビティは、その名前空間およびプロデューサーとして機能する ActivitySource に関連付けられています。
このコールバックは、プロセス内の各 ActivitySource に対して 1 回ずつ呼び出されます。 このソースによって生成されたアクティビティの開始/停止イベントについて、サンプリングを実行したり通知を受けたりする場合は true を返します。
- <xref:System.Diagnostics.ActivityListener.Sample> - いずれかの ActivityListener でサンプリングが必要であると示されていない限り、既定で <xref:System.Diagnostics.ActivitySource.StartActivity%2A> はアクティビティ オブジェクトを作成しません。 <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded> が返される場合、
アクティビティを作成する必要があり、<xref:System.Diagnostics.Activity.IsAllDataRequested> を true に設定する必要があり、<xref:System.Diagnostics.Activity.ActivityTraceFlags> で<xref:System.Diagnostics.ActivityTraceFlags.Recorded> フラグが設定されることを示します。 インストルメント化されたコードによって IsAllDataRequested を監視すると、リスナーでアクティビティの補足情報 (タグやイベントなど) を確実に設定する必要であるというヒントになります。
記録されたフラグは W3C TraceContext ID でエンコードされ、分散トレースに関連する他のプロセスに対してこのトレースをサンプリングする必要があることを示唆します。
- アクティビティが開始され、停止されると、それぞれ <xref:System.Diagnostics.ActivityListener.ActivityStarted> と <xref:System.Diagnostics.ActivityListener.ActivityStopped> が呼び出されます。 これらのコールバックによって、アクティビティに関する関連情報を記録したり、場合によっては変更したりできます。
アクティビティが開始されたばかりのときは、データの多くが不完全である場合がありますが、アクティビティが停止する前に設定されます。

ActivityListener が作成され、コールバックが設定されたら、<xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType> を呼び出すと、
コールバックの呼び出しが開始されます。 <xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType> を呼び出すと、コールバックのフローが停止します。 マルチスレッドのコードでは、進行中のコールバック通知が Dispose () の実行中や、場合によってはそれが返された直後に受信される可能性があることにご注意ください。
