---
title: 診断ツールの概要 - .NET Core
description: .NET Core アプリケーションの診断に使用できるツールと手法の概要。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 9836ea11e7f17d6ed6e04bcba8bc0ed851bb368f
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105285"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="a82e2-103">.NET Core で使用できる診断ツール</span><span class="sxs-lookup"><span data-stu-id="a82e2-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="a82e2-104">ソフトウェアは期待どおりに動作するとは限りませんが、.NET Core には、そのような問題を迅速かつ効果的に診断するために役立つツールと API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a82e2-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="a82e2-105">この記事は、必要な各種ツールを見つけるために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="a82e2-106">マネージド デバッガー</span><span class="sxs-lookup"><span data-stu-id="a82e2-106">Managed debuggers</span></span>

<span data-ttu-id="a82e2-107">[マネージド デバッガー](managed-debuggers.md)を使用すると、プログラムと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="a82e2-108">一時停止、段階的な実行、調査、および再開によって、コードの動作を分析できます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="a82e2-109">デバッガーは、簡単に再現できる機能の問題を診断するための最初の選択肢です。</span><span class="sxs-lookup"><span data-stu-id="a82e2-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="a82e2-110">ログとトレース</span><span class="sxs-lookup"><span data-stu-id="a82e2-110">Logging and tracing</span></span>

<span data-ttu-id="a82e2-111">[ログとトレース](logging-tracing.md)は、関連する手法です。</span><span class="sxs-lookup"><span data-stu-id="a82e2-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="a82e2-112">ログ ファイルを作成するためのコードのインストルメント化を指します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="a82e2-113">ファイルには、プログラムの機能の詳細が記録されます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-113">The files record the details of what a program does.</span></span> <span data-ttu-id="a82e2-114">これらの詳細は、複雑度の高い問題を診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="a82e2-115">タイム スタンプと組み合わせると、これらの手法はパフォーマンスの調査にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="metrics"></a><span data-ttu-id="a82e2-116">メトリック</span><span class="sxs-lookup"><span data-stu-id="a82e2-116">Metrics</span></span>

<span data-ttu-id="a82e2-117">[EventCounters](event-counters.md) を使用すると、パフォーマンスの問題を特定して監視するためのメトリックを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-117">[EventCounters](event-counters.md) allows you to write metrics to identify and monitor performance issues.</span></span> <span data-ttu-id="a82e2-118">メトリックを使用すると、トレースと比較してパフォーマンスのオーバーヘッドが低くなるため、常時接続のパフォーマンスの監視に適しています。</span><span class="sxs-lookup"><span data-stu-id="a82e2-118">Metrics incur lower performance overhead compared to tracing, making it more suitable for an always-on performance monitoring.</span></span> <span data-ttu-id="a82e2-119">.NET ランタイムとライブラリでは、いくつかの[既知の EventCounters](available-counters.md) を発行して、同様に監視することができます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-119">The .NET runtime and libraries publish several [well-known EventCounters](available-counters.md) that you can monitor as well.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="a82e2-120">単体テスト</span><span class="sxs-lookup"><span data-stu-id="a82e2-120">Unit testing</span></span>

<span data-ttu-id="a82e2-121">[単体テスト](../testing/index.md)は、高品質のソフトウェアを継続的に統合して展開するための重要なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a82e2-121">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="a82e2-122">単体テストは、何かを中断するときに早期警告を提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a82e2-122">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="a82e2-123">ダンプ</span><span class="sxs-lookup"><span data-stu-id="a82e2-123">Dumps</span></span>

<span data-ttu-id="a82e2-124">[ダンプ](./dumps.md)は、作成時のプロセスのスナップショットを含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="a82e2-124">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="a82e2-125">これらは、デバッグのためにアプリケーションの状態を調べるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-125">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="symbols"></a><span data-ttu-id="a82e2-126">シンボル</span><span class="sxs-lookup"><span data-stu-id="a82e2-126">Symbols</span></span>

<span data-ttu-id="a82e2-127">[シンボル](./symbols.md)は、ソース コードとコンパイラによって生成されるバイナリとの間のマッピングです。</span><span class="sxs-lookup"><span data-stu-id="a82e2-127">[Symbols](./symbols.md) are a mapping between the source code and the binary produced by the compiler.</span></span> <span data-ttu-id="a82e2-128">これらは一般的に、ソースの行番号、ローカル変数名、その他の種類の診断情報などを解決するために .NET デバッガーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-128">These are commonly used by .NET debuggers to resolve source line numbers, local variable names, and other types of diagnostic information.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="a82e2-129">コンテナーでの診断の収集</span><span class="sxs-lookup"><span data-stu-id="a82e2-129">Collect diagnostics in containers</span></span>

<span data-ttu-id="a82e2-130">コンテナー化されていない Linux 環境で使用されているのと同じ診断ツールを使用して、[コンテナーで診断を収集](diagnostics-in-containers.md)することもできます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-130">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="a82e2-131">Docker コンテナーでツールを動作させるために必要ないくつかの使用方法が変更されています。</span><span class="sxs-lookup"><span data-stu-id="a82e2-131">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="a82e2-132">.NET Core 診断グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="a82e2-132">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="a82e2-133">dotnet-カウンター</span><span class="sxs-lookup"><span data-stu-id="a82e2-133">dotnet-counters</span></span>

<span data-ttu-id="a82e2-134">[dotnet-カウンター](dotnet-counters.md)は、第 1 レベルの正常性監視とパフォーマンス調査のためのパフォーマンス監視ツールです。</span><span class="sxs-lookup"><span data-stu-id="a82e2-134">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="a82e2-135"><xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-135">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="a82e2-136">たとえば、CPU 使用率や、.NET Core アプリケーションでスローされる例外の発生率などをすばやく監視できます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-136">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="a82e2-137">dotnet-ダンプ</span><span class="sxs-lookup"><span data-stu-id="a82e2-137">dotnet-dump</span></span>

<span data-ttu-id="a82e2-138">[dotnet-ダンプ](dotnet-dump.md) ツールは、ネイティブ デバッガーを使用せずに Windows と Linux のコア ダンプを収集して分析する方法です。</span><span class="sxs-lookup"><span data-stu-id="a82e2-138">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="a82e2-139">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="a82e2-139">dotnet-gcdump</span></span>

<span data-ttu-id="a82e2-140">[dotnet-gcdump](dotnet-gcdump.md) ツールは、ライブ .NET プロセスの GC (ガベージ コレクター) ダンプを収集する手段です。</span><span class="sxs-lookup"><span data-stu-id="a82e2-140">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="a82e2-141">dotnet-トレース</span><span class="sxs-lookup"><span data-stu-id="a82e2-141">dotnet-trace</span></span>

<span data-ttu-id="a82e2-142">.NET Core には、診断データが公開される `EventPipe` と呼ばれるものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a82e2-142">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="a82e2-143">[dotnet-トレース](dotnet-trace.md) ツールを使用すると、アプリから興味深いプロファイル データを使用できます。これは、アプリケーションの実行速度が低下する可能性のあるシナリオに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-143">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="a82e2-144">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="a82e2-144">dotnet-symbol</span></span>

<span data-ttu-id="a82e2-145">[dotnet-symbol](dotnet-symbol.md) によって、コア ダンプまたはミニダンプを開くために必要なファイル (シンボル、DAC/DBI、ホスト ファイルなど) をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-145">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="a82e2-146">別のコンピューターでキャプチャされたダンプ ファイルをデバッグするためにシンボルとモジュールが必要な場合は、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-146">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="a82e2-147">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="a82e2-147">dotnet-sos</span></span>

<span data-ttu-id="a82e2-148">[dotnet-sos](dotnet-sos.md) によって、Linux と macOS に [SOS デバッグ拡張機能](sos-debugging-extension.md) がインストールされます ([Windbg/cdb](/windows-hardware/drivers/debugger/debugger-download-tools) を使用している場合は Windows でも)。</span><span class="sxs-lookup"><span data-stu-id="a82e2-148">[dotnet-sos](dotnet-sos.md) installs the [SOS debugging extension](sos-debugging-extension.md) on Linux and macOS (and on Windows if you're using [Windbg/cdb](/windows-hardware/drivers/debugger/debugger-download-tools)).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="a82e2-149">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="a82e2-149">PerfCollect</span></span>

<span data-ttu-id="a82e2-150">[PerfCollect](trace-perfcollect-lttng.md) は、Linux ディストリビューションで実行されている .NET アプリのより詳細なパフォーマンス分析を行うために `perf` と `LTTng` でトレースを収集するために使用できる bash スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="a82e2-150">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="a82e2-151">.NET Core 診断チュートリアル</span><span class="sxs-lookup"><span data-stu-id="a82e2-151">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="a82e2-152">メモリ リークをデバッグする</span><span class="sxs-lookup"><span data-stu-id="a82e2-152">Debug a memory leak</span></span>

<span data-ttu-id="a82e2-153">[チュートリアル: メモリ リークをデバッグする](debug-memory-leak.md)では、メモリ リークを検出する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-153">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="a82e2-154">リークを確認するには [dotnet-counters](dotnet-counters.md) ツールを使用し、リークを診断するには [dotnet-dump](dotnet-dump.md) ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-154">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="a82e2-155">高い CPU 使用率をデバッグする</span><span class="sxs-lookup"><span data-stu-id="a82e2-155">Debug high CPU usage</span></span>

<span data-ttu-id="a82e2-156">[チュートリアル: 高い CPU 使用率をデバッグする](debug-highcpu.md) に関するページに、高い CPU 使用率の調査方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="a82e2-156">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="a82e2-157">高い CPU 使用率を確認するために、[dotnet-counters](dotnet-counters.md) ツールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a82e2-157">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="a82e2-158">次に、[パフォーマンス分析ユーティリティ (`dotnet-trace`) 用のトレース](dotnet-trace.md)または Linux `perf` を使用して、CPU 使用率プロファイルを収集および表示する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-158">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="a82e2-159">デッドロックをデバッグする</span><span class="sxs-lookup"><span data-stu-id="a82e2-159">Debug deadlock</span></span>

<span data-ttu-id="a82e2-160">[チュートリアル: デッドロックのデバッグ](debug-deadlock.md)に関するページに、[dotnet-dump](dotnet-dump.md) ツールを使用してスレッドとロックを調査する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="a82e2-160">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="debug-a-stackoverflow"></a><span data-ttu-id="a82e2-161">スタック オーバーフローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a82e2-161">Debug a StackOverflow</span></span>

<span data-ttu-id="a82e2-162">[チュートリアル: スタック オーバーフローのデバッグ](debug-stackoverflow.md)」は、Linux で <xref:System.StackOverflowException> をデバッグする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-162">[Tutorial: Debug a StackOverflow](debug-stackoverflow.md) demonstrates how to debug a <xref:System.StackOverflowException> on Linux.</span></span>

### <a name="debug-linux-dumps"></a><span data-ttu-id="a82e2-163">Linux ダンプのデバッグ</span><span class="sxs-lookup"><span data-stu-id="a82e2-163">Debug Linux dumps</span></span>

<span data-ttu-id="a82e2-164">「[Linux ダンプのデバッグ](debug-linux-dumps.md)」では、Linux でダンプを収集して分析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-164">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="a82e2-165">EventCounters を使用してパフォーマンスを測定する</span><span class="sxs-lookup"><span data-stu-id="a82e2-165">Measure performance using EventCounters</span></span>

<span data-ttu-id="a82e2-166">[チュートリアル: .NET で EventCounters を使用してパフォーマンスを測定する](event-counter-perf.md)」は、<xref:System.Diagnostics.Tracing.EventCounter> API を使用して .NET アプリのパフォーマンスを測定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a82e2-166">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
