---
title: 高い CPU 使用率をデバッグする - .NET Core
description: .NET Core での高い CPU 使用率のデバッグについて説明するチュートリアルです。
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: ed22da3d53dfd1197de1f9b3c11ef31389cad690
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872796"
---
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="d6f43-103">.NET Core で高い CPU 使用率をデバッグする</span><span class="sxs-lookup"><span data-stu-id="d6f43-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="d6f43-104">**この記事の対象: ✔️** .NET Core 3.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="d6f43-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="d6f43-105">このチュートリアルでは、過剰な CPU 使用率のシナリオをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="d6f43-106">示されている例の [ASP.NET Core Web アプリ](/samples/dotnet/samples/diagnostic-scenarios) ソース コード リポジトリを使用して、デッドロックを意図的に発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="d6f43-107">エンドポイントでは、ハングとスレッドが蓄積します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="d6f43-108">さまざまなツールを使用して、診断データのいくつかの重要な部分でこのシナリオを診断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="d6f43-109">このチュートリアルでは、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="d6f43-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d6f43-110">高い CPU 使用率を調査する</span><span class="sxs-lookup"><span data-stu-id="d6f43-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="d6f43-111">[dotnet-counters](dotnet-counters.md) を使って CPU 使用率を確認する</span><span class="sxs-lookup"><span data-stu-id="d6f43-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="d6f43-112">[dotnet-trace](dotnet-trace.md) を使ってトレース生成を行う</span><span class="sxs-lookup"><span data-stu-id="d6f43-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="d6f43-113">PerfView でパフォーマンスをプロファイリングする</span><span class="sxs-lookup"><span data-stu-id="d6f43-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="d6f43-114">過剰な CPU 使用率を診断して解決する</span><span class="sxs-lookup"><span data-stu-id="d6f43-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6f43-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d6f43-115">Prerequisites</span></span>

<span data-ttu-id="d6f43-116">このチュートリアルでは次のものを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-116">The tutorial uses:</span></span>

- <span data-ttu-id="d6f43-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="d6f43-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version.</span></span>
- <span data-ttu-id="d6f43-118">シナリオをトリガーする[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)</span><span class="sxs-lookup"><span data-stu-id="d6f43-118">[Sample debug target](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="d6f43-119">[dotnet-trace](dotnet-trace.md) を使ってプロセスを一覧表示し、プロファイルを生成する</span><span class="sxs-lookup"><span data-stu-id="d6f43-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="d6f43-120">[dotnet-counters](dotnet-counters.md) を使って CPU 使用率を監視する</span><span class="sxs-lookup"><span data-stu-id="d6f43-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="d6f43-121">CPU カウンター</span><span class="sxs-lookup"><span data-stu-id="d6f43-121">CPU counters</span></span>

<span data-ttu-id="d6f43-122">診断データの収集を試行する前に、高い CPU 状態を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6f43-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="d6f43-123">プロジェクトのルート ディレクトリから次のコマンドを使用して、[サンプル アプリケーション](/samples/dotnet/samples/diagnostic-scenarios)を実行します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-123">Run the [sample application](/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="d6f43-124">このプロセス ID を検索するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="d6f43-125">ご自分のコマンド出力からプロセス ID をメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="d6f43-126">プロセス ID は `22884` でしたが、この ID は異なります。</span><span class="sxs-lookup"><span data-stu-id="d6f43-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="d6f43-127">現在の CPU 使用率を確認するには、[dotnet-counters](dotnet-counters.md) ツール コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="d6f43-128">`refresh-interval` は、CPU 値をポーリングするカウンターの間隔を秒数で示します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="d6f43-129">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d6f43-129">The output should be similar to the following:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

<span data-ttu-id="d6f43-130">Web アプリを実行している状態で、スタートアップ直後に CPU が使用されておらず、`0%` で報告されます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="d6f43-131">ルート パラメーターとして `60000` を使用して `api/diagscenario/highcpu` ルートに移動します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

`https://localhost:5001/api/diagscenario/highcpu/60000`

<span data-ttu-id="d6f43-132">次に、[dotnet-counters](dotnet-counters.md) コマンドを再実行します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="d6f43-133">`cpu-usage` だけを監視するには、コマンドの一部として `System.Runtime[cpu-usage]` を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor --counters System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="d6f43-134">次に示すように、CPU 使用率が増加していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="d6f43-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="d6f43-135">要求の間、CPU 使用率は 25% 前後で推移します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="d6f43-136">ホスト コンピューターに応じて、CPU 使用率が変わることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="d6f43-137">さらに高い CPU 使用率を視覚化するには、複数のブラウザー タブでこのエンドポイントを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="d6f43-138">この時点で、CPU が予想以上に高くなっていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="d6f43-139">トレース生成</span><span class="sxs-lookup"><span data-stu-id="d6f43-139">Trace generation</span></span>

<span data-ttu-id="d6f43-140">低速の要求を分析する場合は、コードの実行内容に関する分析情報を提供できる診断ツールが必要です。</span><span class="sxs-lookup"><span data-stu-id="d6f43-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="d6f43-141">通常はプロファイラーが適しており、さまざまなプロファイラー オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="d6f43-142">Linux</span><span class="sxs-lookup"><span data-stu-id="d6f43-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="d6f43-143">`perf` ツールを使用すると、.NET Core アプリ プロファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="d6f43-144">[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)の前のインスタンスを終了します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-144">Exit the previous instance of the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="d6f43-145">`COMPlus_PerfMapEnabled` 環境変数を設定して、.NET Core アプリによって `/tmp` ディレクトリ内に `map` ファイルが作成されるようにします。</span><span class="sxs-lookup"><span data-stu-id="d6f43-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="d6f43-146">この `map` ファイルは、CPU アドレスを名前順に JIT 生成関数にマップするために `perf` によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="d6f43-147">詳細については、「[パフォーマンス マップの作成](../run-time-config/debugging-profiling.md#write-perf-map)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6f43-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="d6f43-148">同じターミナル セッションで、[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)を実行します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-148">Run the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="d6f43-149">高 CPU API エンドポイント (`https://localhost:5001/api/diagscenario/highcpu/60000`) をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-149">Exercise the high CPU API endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="d6f43-150">それが 1 分間の要求内で実行されている間に、プロセス ID を使用して `perf` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="d6f43-151">`perf` コマンドを実行すると、パフォーマンス コレクション プロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="d6f43-152">約 20 から 30 秒間実行してから、<kbd>Ctrl + C</kbd> キーを押してコレクション プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="d6f43-153">同じ `perf` コマンドを使用して、トレースの出力を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="d6f43-154">次のコマンドを使用して "_フレーム グラフ_" を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="d6f43-155">このコマンドを実行すると、`flamegraph.svg` が生成され、これをブラウザーに表示してパフォーマンスの問題を調査することができます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="d6f43-156">[![フレーム グラフの SVG イメージ](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d6f43-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="d6f43-157">Windows</span><span class="sxs-lookup"><span data-stu-id="d6f43-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="d6f43-158">Windows では、プロファイラーとして [dotnet-trace](dotnet-trace.md) ツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="d6f43-159">前の[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)を使用して、高 CPU エンドポイント (`https://localhost:5001/api/diagscenario/highcpu/60000`) をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-159">Using the previous [sample debug target](/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="d6f43-160">それが 1 分間の要求内で実行されている間に、次のように `collect` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="d6f43-161">[dotnet-trace](dotnet-trace.md) を約 20 から 30 秒間実行してから、<kbd>Enter</kbd> キーを押してコレクションを終了します。</span><span class="sxs-lookup"><span data-stu-id="d6f43-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="d6f43-162">その結果、同じフォルダー内に `nettrace` ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="d6f43-163">`nettrace` ファイルは、Windows 上の既存の分析ツールを使用するのに最適な方法です。</span><span class="sxs-lookup"><span data-stu-id="d6f43-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="d6f43-164">次に示すように、[`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) を使用して `nettrace` を開きます。</span><span class="sxs-lookup"><span data-stu-id="d6f43-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="d6f43-165">[![PerfView イメージ](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d6f43-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="d6f43-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6f43-166">See also</span></span>

- <span data-ttu-id="d6f43-167">[dotnet-trace](dotnet-trace.md) を使ってプロセスを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="d6f43-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="d6f43-168">[dotnet-counters](dotnet-counters.md) を使ってマネージド メモリ使用量を確認する</span><span class="sxs-lookup"><span data-stu-id="d6f43-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="d6f43-169">[dotnet-dump](dotnet-dump.md) を使ってダンプ ファイルを収集して分析する</span><span class="sxs-lookup"><span data-stu-id="d6f43-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="d6f43-170">dotnet/診断</span><span class="sxs-lookup"><span data-stu-id="d6f43-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/main/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="d6f43-171">次の手順</span><span class="sxs-lookup"><span data-stu-id="d6f43-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6f43-172">.NET Core でデッドロックをデバッグする</span><span class="sxs-lookup"><span data-stu-id="d6f43-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
