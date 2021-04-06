---
title: 分散トレースを収集する - .NET
description: OpenTelemetry、Application Insights、または ActivityListener を使用して .NET アプリケーションの分散トレースを収集するためのチュートリアル
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: de10145dcf731e2fe6293461f127463c9dee3cf5
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231181"
---
# <a name="collect-a-distributed-trace"></a><span data-ttu-id="94836-103">分散トレースを収集する</span><span class="sxs-lookup"><span data-stu-id="94836-103">Collect a distributed trace</span></span>

<span data-ttu-id="94836-104">**この記事の対象: ✔️** .NET Core 2.1 以降のバージョン **および** .NET Framework 4.5 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="94836-104">**This article applies to: ✔️** .NET Core 2.1 and later versions **and** .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="94836-105">インストルメント化されたコードは、分散トレースの一部として <xref:System.Diagnostics.Activity> オブジェクトを作成できますが、後でトレース全体を確認できるように、これらのオブジェクトの情報を集中ストレージに収集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94836-105">Instrumented code can create <xref:System.Diagnostics.Activity> objects as part of a distributed trace, but the information in these objects needs to be collected into centralized storage so that the entire trace can be reviewed later.</span></span> <span data-ttu-id="94836-106">このチュートリアルでは、必要に応じてアプリケーションの問題を診断できるように、分散トレースのテレメトリをさまざまな方法で収集します。</span><span class="sxs-lookup"><span data-stu-id="94836-106">In this tutorial you will collect the distributed trace telemetry in different ways so that it is available to diagnose application issues when needed.</span></span> <span data-ttu-id="94836-107">新しいインストルメンテーションを追加する必要がある場合は、[インストルメンテーションのチュートリアル](distributed-tracing-instrumentation-walkthroughs.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94836-107">See [the instrumentation tutorial](distributed-tracing-instrumentation-walkthroughs.md) if you need to add new instrumentation.</span></span>

## <a name="collect-traces-using-opentelemetry"></a><span data-ttu-id="94836-108">OpenTelemetry を使用してトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="94836-108">Collect traces using OpenTelemetry</span></span>

### <a name="prerequisites"></a><span data-ttu-id="94836-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="94836-109">Prerequisites</span></span>

- <span data-ttu-id="94836-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="94836-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

### <a name="create-an-example-application"></a><span data-ttu-id="94836-111">サンプル アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="94836-111">Create an example application</span></span>

<span data-ttu-id="94836-112">分散トレースのテレメトリを収集するには、それを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94836-112">Before any distributed trace telemetry can be collected we need to produce it.</span></span> <span data-ttu-id="94836-113">多くの場合、このインストルメンテーションはライブラリに含まれていますが、わかりやすくするために、<xref:System.Diagnostics.ActivitySource.StartActivity%2A> を使用して、インストルメンテーションの例を含む小さなアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="94836-113">Often this instrumentation might be in libraries but for simplicity you will create a small app that has some example instrumentation using <xref:System.Diagnostics.ActivitySource.StartActivity%2A>.</span></span> <span data-ttu-id="94836-114">この時点では、まだ収集が行われていません。StartActivity () による影響はなく、null 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="94836-114">At this point no collection is happening yet, StartActivity() has no side-effect and returns null.</span></span> <span data-ttu-id="94836-115">詳細については、[インストルメンテーションのチュートリアル](distributed-tracing-instrumentation-walkthroughs.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94836-115">See [the instrumentation tutorial](distributed-tracing-instrumentation-walkthroughs.md) for more details.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="94836-116">.NET 5 以降をターゲットとするアプリケーションには、必要な分散トレース API が既に含まれています。</span><span class="sxs-lookup"><span data-stu-id="94836-116">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="94836-117">以前のバージョンの .NET をターゲットとするアプリの場合は、[System.Diagnostics.DiagnosticSource NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) バージョン 5 以降を追加します。</span><span class="sxs-lookup"><span data-stu-id="94836-117">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="94836-118">生成された Program.cs の内容を次のソース例に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="94836-118">Replace the contents of the generated Program.cs with this example source:</span></span>

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

<span data-ttu-id="94836-119">アプリを実行しても、まだトレース データは収集されません。</span><span class="sxs-lookup"><span data-stu-id="94836-119">Running the app does not collect any trace data yet:</span></span>

```dotnetcli
> dotnet run
Example work done
```

### <a name="collect-using-opentelemetry"></a><span data-ttu-id="94836-120">OpenTelemetry を使用して収集する</span><span class="sxs-lookup"><span data-stu-id="94836-120">Collect using OpenTelemetry</span></span>

<span data-ttu-id="94836-121">[OpenTelemetry](https://opentelemetry.io/) は、クラウドネイティブのソフトウェアのテレメトリの生成と収集を標準化することを目的とした、[Cloud Native Computing Foundation](https://www.cncf.io/) によりサポートされる、ベンダーに依存しないオープン ソース プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="94836-121">[OpenTelemetry](https://opentelemetry.io/) is a vendor neutral open source project supported by the [Cloud Native Computing Foundation](https://www.cncf.io/) that aims to standardize generating and collecting telemetry for cloud-native software.</span></span> <span data-ttu-id="94836-122">この例では、分散トレース情報を収集してコンソールに表示しますが、OpenTelemetry を再構成して別の場所に送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="94836-122">In this example you will collect and display distributed trace information on the console though OpenTelemetry can be reconfigured to send it elsewhere.</span></span> <span data-ttu-id="94836-123">詳細については、[OpenTelemetry の概要ガイド](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94836-123">See the [OpenTelemetry getting started guide](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) for more information.</span></span>

<span data-ttu-id="94836-124">[OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="94836-124">Add the [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet package.</span></span>

```dotnetcli
dotnet add package OpenTelemetry.Exporter.Console
```

<span data-ttu-id="94836-125">OpenTelemetry の追加の using ステートメントを使用して、Program.cs を更新します。</span><span class="sxs-lookup"><span data-stu-id="94836-125">Update Program.cs with additional OpenTelemetry using statments:</span></span>

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;
```

<span data-ttu-id="94836-126">Main () を更新して、OpenTelemetry の TracerProvider を作成します。</span><span class="sxs-lookup"><span data-stu-id="94836-126">Update Main() to create the OpenTelemetry TracerProvider:</span></span>

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

<span data-ttu-id="94836-127">これで、アプリは分散トレース情報を収集して、コンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="94836-127">Now the app collects distributed trace information and displays it to the console:</span></span>

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

#### <a name="sources"></a><span data-ttu-id="94836-128">変換元</span><span class="sxs-lookup"><span data-stu-id="94836-128">Sources</span></span>

<span data-ttu-id="94836-129">次のコード例では、OpenTelemetry がコード内に既に存在する ActivitySource によって生成されたアクティビティをキャプチャするように、`AddSource("Sample.DistributedTracing")` を呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="94836-129">In the example code you invoked `AddSource("Sample.DistributedTracing")` so that OpenTelemetry would capture the Activities produced by the ActivitySource that was already present in the code:</span></span>

```csharp
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");
```

<span data-ttu-id="94836-130">任意の ActivitySource からのテレメトリは、ソース名を指定して AddSource () を呼び出すことによってキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="94836-130">Telemetry from any ActivitySource can captured by calling AddSource() with the source's name.</span></span>

#### <a name="exporters"></a><span data-ttu-id="94836-131">エクスポーター</span><span class="sxs-lookup"><span data-stu-id="94836-131">Exporters</span></span>

<span data-ttu-id="94836-132">コンソール エクスポーターは、簡単な例やローカル開発に役立ちますが、運用環境の展開では、集中管理されたストアにトレースを送信することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94836-132">The console exporter is helpful for quick examples or local development but in a production deployment you will probably want to send traces to a centralized store.</span></span> <span data-ttu-id="94836-133">OpenTelemetry では、異なる[エクスポーター](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library)を使用したさまざまな送信先がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="94836-133">OpenTelemetry supports a variety of destinations using different [exporters](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library).</span></span>
<span data-ttu-id="94836-134">OpenTelemetry の構成の詳細については、[OpenTelemetry の概要ガイド](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94836-134">See the [OpenTelemetry getting started guide](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started) for more information on configuring OpenTelemetry.</span></span>

## <a name="collect-traces-using-application-insights"></a><span data-ttu-id="94836-135">Application Insights を使用してトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="94836-135">Collect traces using Application Insights</span></span>

<span data-ttu-id="94836-136">分散トレースのテレメトリは、Application Insights SDK ([ASP.NET](https://docs.microsoft.com/azure/azure-monitor/app/asp-net)、[ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) を構成した後、または[コードのないインストルメンテーション](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview)を有効にした後に自動的にキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="94836-136">Distributed tracing telemetry is automatically captured after configuring the Application Insights SDK ([ASP.NET](https://docs.microsoft.com/azure/azure-monitor/app/asp-net), [ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) or by enabling [code-less instrumentation](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview).</span></span>

<span data-ttu-id="94836-137">詳細については、[Application Insights の分散トレースのドキュメント](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94836-137">See the [Application Insights distributed tracing documentation](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="94836-138">現在 Application Insights は、特定の既知のアクティビティ インストルメンテーションの収集のみがサポートされ、ユーザーが追加した新しいアクティビティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="94836-138">Currently Application Insights only supports collecting specific well-known Activity instrumentation and will ignore new user added Activities.</span></span> <span data-ttu-id="94836-139">Application Insights には、カスタム分散トレース情報を追加するためのベンダー固有の API として [TrackDependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="94836-139">Application Insights offers [TrackDependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) as a vendor specific API for adding custom distributed tracing information.</span></span>

## <a name="collect-traces-using-custom-logic"></a><span data-ttu-id="94836-140">カスタム ロジックを使用してトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="94836-140">Collect traces using custom logic</span></span>

<span data-ttu-id="94836-141">開発者は、アクティビティ トレース データ用にカスタマイズされた独自の収集ロジックを自由に作成できます。</span><span class="sxs-lookup"><span data-stu-id="94836-141">Developers are free to create their own customized collection logic for Activity trace data.</span></span> <span data-ttu-id="94836-142">この例では、.NET によって提供される <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> API を使用してテレメトリを収集し、コンソールに出力しています。</span><span class="sxs-lookup"><span data-stu-id="94836-142">This example collects the telemetry using the <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> API provided by .NET and prints it to the console.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="94836-143">前提条件</span><span class="sxs-lookup"><span data-stu-id="94836-143">Prerequisites</span></span>

- <span data-ttu-id="94836-144">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="94836-144">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

### <a name="create-an-example-application"></a><span data-ttu-id="94836-145">サンプル アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="94836-145">Create an example application</span></span>

<span data-ttu-id="94836-146">まず、いくつかの分散トレース インストルメンテーションを含むサンプル アプリケーションを作成しますが、トレース データは収集されません。</span><span class="sxs-lookup"><span data-stu-id="94836-146">First you will create an example application that has some distributed trace instrumentation but no trace data is being collected.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="94836-147">.NET 5 以降をターゲットとするアプリケーションには、必要な分散トレース API が既に含まれています。</span><span class="sxs-lookup"><span data-stu-id="94836-147">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="94836-148">以前のバージョンの .NET をターゲットとするアプリの場合は、[System.Diagnostics.DiagnosticSource NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) バージョン 5 以降を追加します。</span><span class="sxs-lookup"><span data-stu-id="94836-148">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="94836-149">生成された Program.cs の内容を次のソース例に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="94836-149">Replace the contents of the generated Program.cs with this example source:</span></span>

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

<span data-ttu-id="94836-150">アプリを実行しても、まだトレース データは収集されません。</span><span class="sxs-lookup"><span data-stu-id="94836-150">Running the app does not collect any trace data yet:</span></span>

```dotnetcli
> dotnet run
Example work done
```

### <a name="add-code-to-collect-the-traces"></a><span data-ttu-id="94836-151">トレースを収集するためのコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94836-151">Add code to collect the traces</span></span>

<span data-ttu-id="94836-152">次のコードで Main() を更新します。</span><span class="sxs-lookup"><span data-stu-id="94836-152">Update Main() with this code:</span></span>

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

<span data-ttu-id="94836-153">出力にログが含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="94836-153">The output now includes logging:</span></span>

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

<span data-ttu-id="94836-154"><xref:System.Diagnostics.Activity.DefaultIdFormat> と <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> の設定は省略可能ですが、これは .NET ランタイム バージョンが違ってもサンプルで確実に同様の出力が生成されるようにするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="94836-154">Setting <xref:System.Diagnostics.Activity.DefaultIdFormat> and <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> is optional but helps ensure the sample produces similar output on different .NET runtime versions.</span></span> <span data-ttu-id="94836-155">.NET 5 では、既定で W3C TraceContext ID 形式が使用されますが、以前のバージョンの .NET では既定で <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID 形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="94836-155">.NET 5 uses the W3C TraceContext ID format by default but earlier .NET versions default to using <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID format.</span></span> <span data-ttu-id="94836-156">詳細については、「[アクティビティ ID](distributed-tracing-concepts.md#activity-ids)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94836-156">See [Activity IDs](distributed-tracing-concepts.md#activity-ids) for more details.</span></span>

<span data-ttu-id="94836-157"><xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> は、アクティビティの有効期間中にコールバックを受信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="94836-157"><xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> is used to receive callbacks during the lifetime of an Activity.</span></span>

- <span data-ttu-id="94836-158"><xref:System.Diagnostics.ActivityListener.ShouldListenTo> - 各アクティビティは、その名前空間およびプロデューサーとして機能する ActivitySource に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="94836-158"><xref:System.Diagnostics.ActivityListener.ShouldListenTo> - Each Activity is associated with an ActivitySource which acts as its namespace and producer.</span></span>
<span data-ttu-id="94836-159">このコールバックは、プロセス内の各 ActivitySource に対して 1 回ずつ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="94836-159">This callback is invoked once for each ActivitySource in the process.</span></span> <span data-ttu-id="94836-160">このソースによって生成されたアクティビティの開始/停止イベントについて、サンプリングを実行したり通知を受けたりする場合は true を返します。</span><span class="sxs-lookup"><span data-stu-id="94836-160">Return true if you are interested in performing sampling or being notified about start/stop events for Activities produced by this source.</span></span>
- <span data-ttu-id="94836-161"><xref:System.Diagnostics.ActivityListener.Sample> - いずれかの ActivityListener でサンプリングが必要であると示されていない限り、既定で <xref:System.Diagnostics.ActivitySource.StartActivity%2A> はアクティビティ オブジェクトを作成しません。</span><span class="sxs-lookup"><span data-stu-id="94836-161"><xref:System.Diagnostics.ActivityListener.Sample> - By default <xref:System.Diagnostics.ActivitySource.StartActivity%2A> does not create an Activity object unless some ActivityListener indicates it should be sampled.</span></span> <span data-ttu-id="94836-162"><xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded> が返される場合、</span><span class="sxs-lookup"><span data-stu-id="94836-162">Returning <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded></span></span>
<span data-ttu-id="94836-163">アクティビティを作成する必要があり、<xref:System.Diagnostics.Activity.IsAllDataRequested> を true に設定する必要があり、<xref:System.Diagnostics.Activity.ActivityTraceFlags> で<xref:System.Diagnostics.ActivityTraceFlags.Recorded> フラグが設定されることを示します。</span><span class="sxs-lookup"><span data-stu-id="94836-163">indicates that the Activity should be created, <xref:System.Diagnostics.Activity.IsAllDataRequested> should be set to true, and <xref:System.Diagnostics.Activity.ActivityTraceFlags> will have the <xref:System.Diagnostics.ActivityTraceFlags.Recorded> flag set.</span></span> <span data-ttu-id="94836-164">インストルメント化されたコードによって IsAllDataRequested を監視すると、リスナーでアクティビティの補足情報 (タグやイベントなど) を確実に設定する必要であるというヒントになります。</span><span class="sxs-lookup"><span data-stu-id="94836-164">IsAllDataRequested can be observed by the instrumented code as a hint that a listener wants to ensure that auxilliary Activity information such as Tags and Events are populated.</span></span>
<span data-ttu-id="94836-165">記録されたフラグは W3C TraceContext ID でエンコードされ、分散トレースに関連する他のプロセスに対してこのトレースをサンプリングする必要があることを示唆します。</span><span class="sxs-lookup"><span data-stu-id="94836-165">The Recorded flag is encoded in the W3C TraceContext ID and is a hint to other processes involved in the distributed trace that this trace should be sampled.</span></span>
- <span data-ttu-id="94836-166">アクティビティが開始され、停止されると、それぞれ <xref:System.Diagnostics.ActivityListener.ActivityStarted> と <xref:System.Diagnostics.ActivityListener.ActivityStopped> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="94836-166"><xref:System.Diagnostics.ActivityListener.ActivityStarted> and <xref:System.Diagnostics.ActivityListener.ActivityStopped> are called when an Activity is started and stopped respectively.</span></span> <span data-ttu-id="94836-167">これらのコールバックによって、アクティビティに関する関連情報を記録したり、場合によっては変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="94836-167">These callbacks provide an oportunity to record relevant information about the Activity or potentially to modify it.</span></span>
<span data-ttu-id="94836-168">アクティビティが開始されたばかりのときは、データの多くが不完全である場合がありますが、アクティビティが停止する前に設定されます。</span><span class="sxs-lookup"><span data-stu-id="94836-168">When an Activity has just started much of the data may still be incomplete and it will be populated before the Activity stops.</span></span>

<span data-ttu-id="94836-169">ActivityListener が作成され、コールバックが設定されたら、<xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType> を呼び出すと、</span><span class="sxs-lookup"><span data-stu-id="94836-169">Once an ActivityListener has been created and the callbacks are populated, calling <xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType></span></span>
<span data-ttu-id="94836-170">コールバックの呼び出しが開始されます。</span><span class="sxs-lookup"><span data-stu-id="94836-170">initiates invoking the callbacks.</span></span> <span data-ttu-id="94836-171"><xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType> を呼び出すと、コールバックのフローが停止します。</span><span class="sxs-lookup"><span data-stu-id="94836-171">Call <xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType> to stop the flow of callbacks.</span></span> <span data-ttu-id="94836-172">マルチスレッドのコードでは、進行中のコールバック通知が Dispose () の実行中や、場合によってはそれが返された直後に受信される可能性があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="94836-172">Beware that in multi-threaded code callback notifications in progress could be received while Dispose() is running or even very shortly after it has returned.</span></span>
