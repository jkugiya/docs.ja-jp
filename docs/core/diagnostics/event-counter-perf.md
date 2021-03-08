---
title: .NET Core で EventCounters を使用してパフォーマンスを測定する
description: このチュートリアルでは、EventCounters を使用してパフォーマンスを測定する方法について説明します。
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: bde54ce1996b2f4e2a703c23384eadece06e66cb
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105311"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="3e788-103">チュートリアル: .NET Core で EventCounters を使用してパフォーマンスを測定する</span><span class="sxs-lookup"><span data-stu-id="3e788-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="3e788-104">**この記事の対象: ✔️** .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="3e788-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="3e788-105">このチュートリアルでは、<xref:System.Diagnostics.Tracing.EventCounter> を使用して、イベントの頻度が高い状態でパフォーマンスを測定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e788-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="3e788-106">さまざまな公式 .NET Core パッケージまたはサードパーティ プロバイダーによって発行された[使用可能なカウンター](available-counters.md)を使用することも、監視用に独自のメトリックを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e788-106">You can use the [available counters](available-counters.md) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="3e788-107">このチュートリアルでは、次のことについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3e788-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3e788-108"><xref:System.Diagnostics.Tracing.EventSource> の実装。</span><span class="sxs-lookup"><span data-stu-id="3e788-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="3e788-109">[dotnet-counters](dotnet-counters.md) を使用したカウンターの監視。</span><span class="sxs-lookup"><span data-stu-id="3e788-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e788-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3e788-110">Prerequisites</span></span>

<span data-ttu-id="3e788-111">このチュートリアルでは次のものを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e788-111">The tutorial uses:</span></span>

- <span data-ttu-id="3e788-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="3e788-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version.</span></span>
- <span data-ttu-id="3e788-113">イベント カウンターを監視するための [dotnet-counters](dotnet-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="3e788-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="3e788-114">診断する[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios) アプリ。</span><span class="sxs-lookup"><span data-stu-id="3e788-114">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="3e788-115">ソースを入手する</span><span class="sxs-lookup"><span data-stu-id="3e788-115">Get the source</span></span>

<span data-ttu-id="3e788-116">監視のための基礎としてサンプル アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e788-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="3e788-117">[サンプルの ASP.NET Core リポジトリ](/samples/dotnet/samples/diagnostic-scenarios)をサンプル ブラウザーから利用できます。</span><span class="sxs-lookup"><span data-stu-id="3e788-117">The [sample ASP.NET Core repository](/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="3e788-118">zip ファイルをダウンロードし、ダウンロード後に展開して、普段使用している IDE で開きます。</span><span class="sxs-lookup"><span data-stu-id="3e788-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="3e788-119">アプリケーションをビルドして実行し、正常に動作することを確実にしてから、アプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="3e788-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="3e788-120">EventSource を実装する</span><span class="sxs-lookup"><span data-stu-id="3e788-120">Implement an EventSource</span></span>

<span data-ttu-id="3e788-121">数ミリ秒ごとに発生するイベントの場合は、イベントごとのオーバーヘッドを低くする必要があります (ミリ秒未満)。</span><span class="sxs-lookup"><span data-stu-id="3e788-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="3e788-122">そうしないと、パフォーマンスへの影響が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="3e788-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="3e788-123">イベントをログに記録すると、ディスクに何かが書き込まれることになります。</span><span class="sxs-lookup"><span data-stu-id="3e788-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="3e788-124">ディスクの速度が十分でない場合は、イベントが失われます。</span><span class="sxs-lookup"><span data-stu-id="3e788-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="3e788-125">イベント自体をログに記録する以外の解決策が必要です。</span><span class="sxs-lookup"><span data-stu-id="3e788-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="3e788-126">多数のイベントを処理する場合、イベントごとの測定値を知ることも役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="3e788-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="3e788-127">ほとんどの場合、必要なのはそれから得られる統計情報だけです。</span><span class="sxs-lookup"><span data-stu-id="3e788-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="3e788-128">そのため、プロセス自体に含まれる統計情報を取得し、ときどきイベントを書き込んで統計情報を報告することができます。それが <xref:System.Diagnostics.Tracing.EventCounter> で行われることです。</span><span class="sxs-lookup"><span data-stu-id="3e788-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="3e788-129"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> を実装する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3e788-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="3e788-130">*MinimalEventCounterSource.cs* という名前の新しいファイルを作成し、そのソースとして次のコード スニペットを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e788-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="3e788-131"><xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> の行は <xref:System.Diagnostics.Tracing.EventSource> パーツであり、<xref:System.Diagnostics.Tracing.EventCounter> のパーツではありません。イベント カウンターと共にメッセージをログに記録できることを示すために記述されています。</span><span class="sxs-lookup"><span data-stu-id="3e788-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="3e788-132">アクション フィルターを追加する</span><span class="sxs-lookup"><span data-stu-id="3e788-132">Add an action filter</span></span>

<span data-ttu-id="3e788-133">サンプルのソース コードは、ASP.NET Core プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="3e788-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="3e788-134">要求の合計時間をログに記録する[アクション フィルター](/aspnet/core/mvc/controllers/filters#action-filters)をグローバルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="3e788-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="3e788-135">*LogRequestTimeFilterAttribute.cs* という名前の新しいファイルを作成し、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e788-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="3e788-136">アクション フィルターによって要求の開始時に <xref:System.Diagnostics.Stopwatch> を開始し、完了後に停止して、経過時間をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="3e788-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="3e788-137">合計時間 (ミリ秒) は `MinimalEventCounterSource` シングルトン インスタンスに記録されます。</span><span class="sxs-lookup"><span data-stu-id="3e788-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="3e788-138">このフィルターを適用するには、フィルター コレクションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e788-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="3e788-139">*Startup.cs* ファイルで、このフィルターを含めるように `ConfigureServices` メソッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="3e788-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="3e788-140">イベント カウンターを監視する</span><span class="sxs-lookup"><span data-stu-id="3e788-140">Monitor event counter</span></span>

<span data-ttu-id="3e788-141"><xref:System.Diagnostics.Tracing.EventSource> の実装とカスタム アクション フィルターを使用して、アプリケーションをビルドして起動します。</span><span class="sxs-lookup"><span data-stu-id="3e788-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="3e788-142"><xref:System.Diagnostics.Tracing.EventCounter> にメトリックを記録しましたが、それから得られる統計情報にアクセスしない限り、それは役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="3e788-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="3e788-143">統計を取得するには、イベントをキャプチャするリスナーだけでなく、必要な頻度で起動するタイマーを作成して、<xref:System.Diagnostics.Tracing.EventCounter> を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e788-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="3e788-144">これを行うために、[dotnet-counters](dotnet-counters.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e788-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="3e788-145">[dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) コマンドを使用して、監視できる .NET プロセスの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="3e788-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="3e788-146">`dotnet-counters ps` コマンドの出力にあるプロセス識別子を使用し、次の `dotnet-counters monitor` コマンドを使ってイベント カウンターの監視を開始できます。</span><span class="sxs-lookup"><span data-stu-id="3e788-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="3e788-147">`dotnet-counters monitor` コマンドの実行中に、`https://localhost:5001/api/values` エンドポイントへの継続的な要求の発行を開始するために、ブラウザーで <kbd>F5</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3e788-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="3e788-148">数秒後に <kbd>q</kbd> キーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="3e788-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="3e788-149">`dotnet-counters monitor` コマンドは、アクティブな監視に適しています。</span><span class="sxs-lookup"><span data-stu-id="3e788-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="3e788-150">ただし、これらの診断メトリックを収集して、後処理や分析を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="3e788-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="3e788-151">そのためには、`dotnet-counters collect` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e788-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="3e788-152">`collect` スイッチ コマンドは、`monitor` コマンドに似ていますが、いくつかの追加パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3e788-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="3e788-153">目的の出力ファイル名と形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e788-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="3e788-154">*diagnostics.json* という名前の JSON ファイルの場合、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e788-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="3e788-155">コマンドの実行中に再度ブラウザーで <kbd>F5</kbd> キーを押して、`https://localhost:5001/api/values` エンドポイントへの継続的な要求の発行を開始します。</span><span class="sxs-lookup"><span data-stu-id="3e788-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="3e788-156">数秒後に <kbd>q</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3e788-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="3e788-157">*diagnostics.json* ファイルが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="3e788-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="3e788-158">ただし、書き込まれた JSON ファイルはインデントされません。ここでは読みやすくするためにインデントしています。</span><span class="sxs-lookup"><span data-stu-id="3e788-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="3e788-159">次のステップ</span><span class="sxs-lookup"><span data-stu-id="3e788-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3e788-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="3e788-160">EventCounters</span></span>](event-counters.md)
