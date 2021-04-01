---
title: PerfCollect を使用した .NET アプリケーションのトレース。
description: .NET で PerfCollect を使用してトレースを収集する手順について説明するチュートリアル。
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: d6ee77fea5c419e00e684e8b1472278f752544b0
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874187"
---
# <a name="trace-net-applications-with-perfcollect"></a><span data-ttu-id="ac45b-103">PerfCollect を使用して .NET アプリケーションをトレースする</span><span class="sxs-lookup"><span data-stu-id="ac45b-103">Trace .NET applications with PerfCollect</span></span>

<span data-ttu-id="ac45b-104">**この記事の対象: ✔️** .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="ac45b-104">**This article applies to: ✔️** .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="ac45b-105">Linux でパフォーマンスの問題が発生した場合は、`perfcollect` でトレースを収集することにより、パフォーマンスの問題が発生したときにコンピューターで何が起きていたかに関する詳細な情報を収集できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-105">When performance problems are encountered on Linux, collecting a trace with `perfcollect` can be used to gather detailed information about what was happening on the machine at the time of the performance problem.</span></span>

<span data-ttu-id="ac45b-106">`perfcollect` は Bash スクリプトであり、[Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) を利用して、ランタイムまたは任意の [EventSource](xref:System.Diagnostics.Tracing.EventListener) から書き込まれたイベントを収集すると共に、[perf](https://perf.wiki.kernel.org/) を利用してターゲット プロセスの CPU サンプルを収集します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-106">`perfcollect` is a bash script that leverages [Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) to collect events written from the runtime or any [EventSource](xref:System.Diagnostics.Tracing.EventListener), as well as [perf](https://perf.wiki.kernel.org/) to collect CPU samples of the target process.</span></span>

## <a name="prepare-your-machine"></a><span data-ttu-id="ac45b-107">コンピューターを準備する</span><span class="sxs-lookup"><span data-stu-id="ac45b-107">Prepare your machine</span></span>

<span data-ttu-id="ac45b-108">`perfcollect` を使用してパフォーマンス トレースが収集されるようコンピューターを準備するには、以下の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-108">Follow these steps to prepare your machine to collect a performance trace with `perfcollect`.</span></span>

> [!NOTE]
> <span data-ttu-id="ac45b-109">コンテナー環境にいる場合は、コンテナーが `SYS_ADMIN` 機能を備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-109">If you are in a container environment, your container needs to have `SYS_ADMIN` capability.</span></span> <span data-ttu-id="ac45b-110">PerfCollect を使用してコンテナー内のアプリケーションをトレースする方法の詳細については、「[コンテナーでの診断の収集](./diagnostics-in-containers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac45b-110">For more information on tracing applications inside containers using PerfCollect, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

1. <span data-ttu-id="ac45b-111">`perfcollect` をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-111">Download `perfcollect`.</span></span>

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. <span data-ttu-id="ac45b-112">スクリプトを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-112">Make the script executable.</span></span>

    > ```bash
    > chmod +x perfcollect
    > ```

3. <span data-ttu-id="ac45b-113">トレースの前提条件をインストールします。これらは実際のトレース ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="ac45b-113">Install tracing prerequisites - these are the actual tracing libraries.</span></span>

    > ```bash
    > sudo ./perfcollect install
    > ```

    <span data-ttu-id="ac45b-114">これにより、次の前提条件がコンピューターにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-114">This will install the following prerequisites on your machine:</span></span>

    1. <span data-ttu-id="ac45b-115">`perf`: Linux Performance Events サブシステムと、コンパニオン ユーザーモード コレクションおよびビューアー アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="ac45b-115">`perf`: the Linux Performance Events subsystem and companion user-mode collection/viewer application.</span></span> <span data-ttu-id="ac45b-116">`perf` は Linux カーネル ソースの一部ですが、通常は既定ではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="ac45b-116">`perf` is part of the Linux kernel source, but is not usually installed by default.</span></span>

    2. <span data-ttu-id="ac45b-117">`LTTng`: 実行時に CoreCLR によって生成されるイベント データをキャプチャするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-117">`LTTng`: Used to capture event data emitted at runtime by CoreCLR.</span></span> <span data-ttu-id="ac45b-118">その後、このデータを使用して、GC、JIT、スレッド プールなどのさまざまなランタイム コンポーネントの動作が分析されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-118">This data is then used to analyze the behavior of various runtime components such as the GC, JIT, and thread pool.</span></span>

<span data-ttu-id="ac45b-119">最新のバージョンの .NET Core および Linux perf ツールでは、フレームワーク コードのためのメソッド名の自動解決がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ac45b-119">Recent versions of .NET Core and the Linux perf tool support automatic resolution of method names for framework code.</span></span> <span data-ttu-id="ac45b-120">.NET Core バージョン 3.1 以下を使用している場合は、追加の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="ac45b-120">If you are working with .NET Core version 3.1 or less, an extra step is necessary.</span></span> <span data-ttu-id="ac45b-121">詳細については、[フレームワーク シンボルの解決](#resolve-framework-symbols)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac45b-121">See [Resolving Framework Symbols](#resolve-framework-symbols) for details.</span></span>

<span data-ttu-id="ac45b-122">ネイティブ ランタイム DLL (libcoreclr.so など) のメソッド名の解決の場合は、`perfcollect` によってデータの変換時にそれらのシンボルが解決されますが、それが行われるのはこれらのバイナリのシンボルが存在する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="ac45b-122">For resolving method names of native runtime DLLs (such as libcoreclr.so), `perfcollect` will resolve symbols for them when it converts the data, but only if the symbols for these binaries are present.</span></span> <span data-ttu-id="ac45b-123">詳細については、[ネイティブ ランタイムのシンボルの取得](#get-symbols-for-the-native-runtime)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac45b-123">See [Getting Symbols for the Native Runtime](#get-symbols-for-the-native-runtime) section for details.</span></span>

## <a name="collect-a-trace"></a><span data-ttu-id="ac45b-124">トレースを収集する</span><span class="sxs-lookup"><span data-stu-id="ac45b-124">Collect a trace</span></span>

1. <span data-ttu-id="ac45b-125">2 つのシェルを使用できるようにします。1 つはトレースの制御用で ( **[Trace]** と呼びます)、もう 1 つはアプリケーションの実行用です ( **[App]** と呼びます)。</span><span class="sxs-lookup"><span data-stu-id="ac45b-125">Have two shells available - one for controlling tracing, referred to as **[Trace]**, and one for running the application, referred to as **[App]**.</span></span>

2. <span data-ttu-id="ac45b-126">**[Trace]** 収集を開始します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-126">**[Trace]** Start collection.</span></span>

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    <span data-ttu-id="ac45b-127">予想される出力:</span><span class="sxs-lookup"><span data-stu-id="ac45b-127">Expected Output:</span></span>

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. <span data-ttu-id="ac45b-128">**[App]** 次の環境変数を使用して、アプリケーションのシェルを設定します。これにより、CoreCLR のトレース構成が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-128">**[App]** Set up the application shell with the following environment variables - this enables tracing configuration of CoreCLR.</span></span>

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. <span data-ttu-id="ac45b-129">**[App]** アプリを実行します。パフォーマンスの問題をキャプチャするために必要な限り実行させておきます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-129">**[App]** Run the app - let it run as long as you need to in order to capture the performance problem.</span></span> <span data-ttu-id="ac45b-130">正確な長さは、調査する必要があるパフォーマンスの問題が発生した時間帯を十分に把握できる限り、必要なだけ短くできます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-130">The exact length can be as short as you need as long as it sufficiently captures the window of time where the performance problem you want to investigate occurs.</span></span>

    > ```bash
    > dotnet run
    > ```

5. <span data-ttu-id="ac45b-131">**[Trace]** 収集を停止します。Ctrl + C キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-131">**[Trace]** Stop collection - hit CTRL+C.</span></span>

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    <span data-ttu-id="ac45b-132">圧縮されたトレース ファイルが、現在の作業ディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-132">The compressed trace file is now stored in the current working directory.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="ac45b-133">トレースを表示する</span><span class="sxs-lookup"><span data-stu-id="ac45b-133">View a trace</span></span>

<span data-ttu-id="ac45b-134">収集されたトレースを表示するには、いくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-134">There are a number of options for viewing the trace that was collected.</span></span> <span data-ttu-id="ac45b-135">トレースは、Windows で [PerfView](https://aka.ms/perfview) を使用すると最も適切に表示されますが、`PerfCollect` 自体または `TraceCompass` を使用して Linux で直接表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-135">Traces are best viewed using [PerfView](https://aka.ms/perfview) on Windows, but they can be viewed directly on Linux using `PerfCollect` itself or `TraceCompass`.</span></span>

### <a name="use-perfcollect-to-view-the-trace-file"></a><span data-ttu-id="ac45b-136">PerfCollect を使用してトレース ファイルを表示する</span><span class="sxs-lookup"><span data-stu-id="ac45b-136">Use PerfCollect to view the trace file</span></span>

<span data-ttu-id="ac45b-137">Perfcollect 自体を使用して、収集したトレースを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-137">You can use perfcollect itself to view the trace that you collected.</span></span> <span data-ttu-id="ac45b-138">これを行うには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-138">To do this, use the following command:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip
```

<span data-ttu-id="ac45b-139">このようにすると、既定では、`perf` を使用しているアプリケーションの CPU トレースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-139">By default, this will show the CPU trace of the application using `perf`.</span></span>

<span data-ttu-id="ac45b-140">`LTTng` によって収集されたイベントを見るには、フラグ `-viewer lttng` を渡して個々のイベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-140">To look at the events that were collected via `LTTng`, you can pass in the flag `-viewer lttng` to see the individual events:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

<span data-ttu-id="ac45b-141">このようにすると、`babeltrace` ビューアーを使用してイベントのペイロードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-141">This will use `babeltrace` viewer to print the events payload:</span></span>

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a><span data-ttu-id="ac45b-142">PerfView を使用してトレース ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="ac45b-142">Use PerfView to open the trace file</span></span>

<span data-ttu-id="ac45b-143">CPU サンプルとイベント両方の集約ビューを表示するには、Windows コンピューターで `PerfView` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-143">To see an aggregate view of both the CPU sample and the events, you can use `PerfView` on a Windows machine.</span></span>

1. <span data-ttu-id="ac45b-144">trace.zip ファイルを Linux から Windows コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-144">Copy the trace.zip file from Linux to a Windows machine.</span></span>

2. <span data-ttu-id="ac45b-145"><https://aka.ms/perfview> から PerfView をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-145">Download PerfView from <https://aka.ms/perfview>.</span></span>

3. <span data-ttu-id="ac45b-146">PerfView.exe を実行する</span><span class="sxs-lookup"><span data-stu-id="ac45b-146">Run PerfView.exe</span></span>

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

<span data-ttu-id="ac45b-147">PerfView により、トレース ファイルに含まれるデータに基づいてサポートされるビューの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-147">PerfView will display the list of views that are supported based on the data contained in the trace file.</span></span>

- <span data-ttu-id="ac45b-148">CPU の調査の場合は、 **[CPU stacks]\(CPU スタック\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-148">For CPU investigations, choose **CPU stacks**.</span></span>

- <span data-ttu-id="ac45b-149">GC の詳細な情報の場合は、 **[GCStats]\(GC 統計\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-149">For detailed GC information, choose **GCStats**.</span></span>

- <span data-ttu-id="ac45b-150">プロセス、モジュール、メソッドごとの JIT の情報の場合は、 **[JITStats]\(JIT 統計\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-150">For per-process/module/method JIT information, choose **JITStats**.</span></span>

- <span data-ttu-id="ac45b-151">必要な情報のビューがない場合は、生のイベント ビューでイベントを検索してみることができます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-151">If there is not a view for the information you need, you can try looking for the events in the raw events view.</span></span>  <span data-ttu-id="ac45b-152">**[Events]\(イベント\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-152">Choose **Events**.</span></span>

<span data-ttu-id="ac45b-153">PerfView でのビューの解釈方法の詳細については、ビュー自体のヘルプ リンクを参照するか、PerfView のメイン ウィンドウで **[Help]\(ヘルプ\) > [Users Guide]\(ユーザー ガイド\)** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="ac45b-153">For more information on how to interpret views in PerfView, see help links in the view itself, or from the main window in PerfView, choose **Help->Users Guide**.</span></span>

> [!NOTE]
> <span data-ttu-id="ac45b-154"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> API を使用して書き込まれたイベント (フレームワークからのイベントを含む) は、プロバイダー名の下に表示されません。</span><span class="sxs-lookup"><span data-stu-id="ac45b-154">Events written via <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> API (including the events from Framework) won't show up under their provider name.</span></span> <span data-ttu-id="ac45b-155">代わりに、`Microsoft-Windows-DotNETRuntime` プロバイダーの下に `EventSourceEvent` イベントとして書き込まれ、そのペイロードは JSON でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-155">Instead, they are written as `EventSourceEvent` events under `Microsoft-Windows-DotNETRuntime` provider and their payloads are JSON serialized.</span></span>

### <a name="use-tracecompass-to-open-the-trace-file"></a><span data-ttu-id="ac45b-156">TraceCompass を使用してトレース ファイルを開く</span><span class="sxs-lookup"><span data-stu-id="ac45b-156">Use TraceCompass to open the trace file</span></span>

<span data-ttu-id="ac45b-157">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) は、トレースを表示するために使用できるもう 1 つのオプションです。</span><span class="sxs-lookup"><span data-stu-id="ac45b-157">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) is another option you can use to view the traces.</span></span> <span data-ttu-id="ac45b-158">`TraceCompass` は Linux マシンでも動作するので、トレースを Windows コンピューターに移動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ac45b-158">`TraceCompass` works on Linux machines as well, so you don't need to move your trace over to a Windows machine.</span></span> <span data-ttu-id="ac45b-159">`TraceCompass` を使用してトレース ファイルを開くには、ファイルを解凍する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-159">To use `TraceCompass` to open your trace file, you will need to unzip the file.</span></span>

```bash
unzip myTrace.trace.zip
```

<span data-ttu-id="ac45b-160">`perfcollect` によって収集された LTTng トレースは、`lttngTrace` 内のサブディレクトリに CTF ファイル形式で保存されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-160">`perfcollect` will save the LTTng trace it collected into a CTF file format in a subdirectory in the `lttngTrace`.</span></span> <span data-ttu-id="ac45b-161">具体的には、CTF ファイルは `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` のようなディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-161">Specifically, the CTF file will be located in a directory that looks like `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\`.</span></span>

<span data-ttu-id="ac45b-162">`File -> Open Trace` を選択して `metadata` ファイルを選択することにより、`TraceCompass` で CTF トレースファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-162">You can open the CTF trace file in `TraceCompass` by selecting `File -> Open Trace` and select the `metadata` file.</span></span>

<span data-ttu-id="ac45b-163">詳細については、[`TraceCompass` のドキュメント](https://www.eclipse.org/tracecompass/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac45b-163">For more details, please refer to [`TraceCompass` documentation](https://www.eclipse.org/tracecompass/).</span></span>

## <a name="resolve-framework-symbols"></a><span data-ttu-id="ac45b-164">フレームワークのシンボルを解決する</span><span class="sxs-lookup"><span data-stu-id="ac45b-164">Resolve framework symbols</span></span>

<span data-ttu-id="ac45b-165">フレームワークのシンボルは、トレースが収集されるときに手動で生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-165">Framework symbols need to be manually generated at the time the trace is collected.</span></span> <span data-ttu-id="ac45b-166">フレームワークがプリコンパイルされるのに対して、アプリのコードは Just-In-Time コンパイルされるため、それらはアプリ レベルのシンボルとは異なります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-166">They are different than app-level symbols because the framework is pre-compiled while app code is just-in-time-compiled.</span></span> <span data-ttu-id="ac45b-167">ネイティブ コードにプリコンパイルされたフレームワーク コードの場合は、ネイティブ コードからメソッドの名前へのマッピングを生成する方法を認識している `crossgen` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-167">For framework code that was precompiled to native code, you need to call `crossgen` that knows how to generate the mapping from the native code to the name of the methods.</span></span>

<span data-ttu-id="ac45b-168">`perfcollect` を使用するとほとんどの詳細を自動的に処理できますが、`crossgen` を使用できるようにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-168">`perfcollect` can handle most of the details for you, but it needs to have `crossgen` available.</span></span> <span data-ttu-id="ac45b-169">既定では、それは .NET ディストリビューションと共にインストールされません。</span><span class="sxs-lookup"><span data-stu-id="ac45b-169">By default it is not installed with .NET distribution.</span></span> <span data-ttu-id="ac45b-170">`crossgen` がない場合は、`perfcollect` の警告が表示され、以下の手順が示されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-170">If `crossgen` is not there, `perfcollect` warns you and refers you to these instructions.</span></span> <span data-ttu-id="ac45b-171">問題を解決するには、使用しているランタイム用の適切なバージョンの crossgen を正確にフェッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-171">To fix things you need to fetch exactly the right version of crossgen for the runtime you are using.</span></span> <span data-ttu-id="ac45b-172">crossgen ツールを .NET ランタイム DLL (libcoreclr.so など) と同じディレクトリに配置した場合は、`perfcollect` によってそれが検索され、フレームワーク シンボルがトレース ファイルに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-172">If you place the crossgen tool in the same directory as the .NET Runtime DLLs (for example, libcoreclr.so), then `perfcollect` can find it and add the framework symbols to the trace file for you.</span></span>

<span data-ttu-id="ac45b-173">通常、.NET アプリケーションを作成すると、記述されたコードの DLL だけが生成され、それ以外の部分についてはランタイムの共有コピーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-173">Normally when you create a .NET application, it just generates the DLL for the code you wrote, using a shared copy of the runtime for the rest.</span></span>   <span data-ttu-id="ac45b-174">ただし、アプリケーションの "自己完結型" バージョンと呼ばれる、すべてのランタイム DLL が含まれるものを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-174">However you can also generate what is called a 'self-contained' version of an application and this contains all runtime DLLs.</span></span> <span data-ttu-id="ac45b-175">`crossgen` は自己完結型アプリの作成に使用される NuGet パッケージの一部であるため、適切なバージョンの `crossgen` を取得する方法の 1 つは、アプリケーションの自己完結型パッケージを作成することです。</span><span class="sxs-lookup"><span data-stu-id="ac45b-175">`crossgen` is part of the NuGet package that is used to create self-contained apps, so one way of getting the right version of `crossgen` is to create a self-contained package of your application.</span></span>

<span data-ttu-id="ac45b-176">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-176">For example:</span></span>

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

<span data-ttu-id="ac45b-177">これにより、新しい Hello World アプリケーションが作成され、自己完結型アプリとしてビルドされます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-177">This creates a new Hello World application and builds it as a self-contained app.</span></span>

<span data-ttu-id="ac45b-178">自己完結型アプリケーションを作成する副作用として、dotnet ツールにより runtime.linux-x64.microsoft.netcore.app という名前の NuGet パッケージがダウンロードされて、ディレクトリ ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION に配置されます。VERSION は、.NET Core ランタイムのバージョン番号です (例: 2.1.0)。</span><span class="sxs-lookup"><span data-stu-id="ac45b-178">As a side effect of creating the self-contained application the dotnet tool will download a NuGet package called runtime.linux-x64.microsoft.netcore.app and place it in the directory ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, where VERSION is the version number of your .NET Core runtime (for example, 2.1.0).</span></span> <span data-ttu-id="ac45b-179">その下にある tools ディレクトリ内に、必要な crossgen ツールがあります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-179">Under that is a tools directory and inside there is the crossgen tool you need.</span></span> <span data-ttu-id="ac45b-180">.NET Core 3.0 以降でのパッケージの場所は、~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION です。</span><span class="sxs-lookup"><span data-stu-id="ac45b-180">Starting with .NET Core 3.0, the package location is ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span></span>

<span data-ttu-id="ac45b-181">`crossgen` ツールは、アプリケーションによって実際に使用されるランタイムに並べて配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-181">The `crossgen` tool needs to be put next to the runtime that is actually used by your application.</span></span> <span data-ttu-id="ac45b-182">通常は、/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION にインストールされている .NET Core の共有バージョンが、アプリで使用されます。VERSION は、.NET ランタイムのバージョン番号です。</span><span class="sxs-lookup"><span data-stu-id="ac45b-182">Typically your app uses the shared version of .NET Core that is installed at /usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION where VERSION is the version number of the .NET Runtime.</span></span> <span data-ttu-id="ac45b-183">これは共有の場所であるため、それを変更するにはスーパーユーザーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-183">This is a shared location, so you need to be super-user to modify it.</span></span> <span data-ttu-id="ac45b-184">VERSION が 2.1.0 の場合、`crossgen` を更新するためのコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-184">If the VERSION is 2.1.0 the commands to update `crossgen` would be:</span></span>

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

<span data-ttu-id="ac45b-185">これが完了すると、`perfcollect` により crossgen を使用してフレームワーク シンボルが組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-185">Once you have done this, `perfcollect` will use crossgen to include framework symbols.</span></span> <span data-ttu-id="ac45b-186">前に `perfcollect` によって表示されていた警告は出なくなります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-186">The warning that `perfcollect` used to issue should go away.</span></span> <span data-ttu-id="ac45b-187">これは、コンピューターごとに 1 回だけ行う必要があります (ランタイムを更新するまで)。</span><span class="sxs-lookup"><span data-stu-id="ac45b-187">This only has to be one once per machine (until you update your runtime).</span></span>

### <a name="alternative-turn-off-use-of-precompiled-code"></a><span data-ttu-id="ac45b-188">代替手段: プリコンパイル済みコードの使用をオフにする</span><span class="sxs-lookup"><span data-stu-id="ac45b-188">Alternative: Turn off use of precompiled code</span></span>

<span data-ttu-id="ac45b-189">(`crossgen` を追加するために) .NET ランタイムを更新することができない場合、または上記の手順がなんらかの理由で機能しない場合は、フレームワーク シンボルを取得するための別の方法があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-189">If you don't have the ability to update the .NET Runtime (to add `crossgen`), or if the above procedure did not work for some reason, there is another approach to getting framework symbols.</span></span> <span data-ttu-id="ac45b-190">プリコンパイルされたフレームワーク コードを単に使用しないよう、ランタイムに指示することができます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-190">You can tell the runtime to simply not use the precompiled framework code.</span></span> <span data-ttu-id="ac45b-191">コードは Just-in-time でコンパイルされるので、`crossgen` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ac45b-191">The code will be Just-In-Time compiled and `crossgen` is not needed.</span></span>

> [!NOTE]
> <span data-ttu-id="ac45b-192">この方法を選択すると、アプリケーションの起動時間が長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-192">Choosing this approach may increase the startup time for your application.</span></span>

<span data-ttu-id="ac45b-193">これを行うには、次の環境変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-193">To do this, you can add the following environment variable:</span></span>

```bash
export COMPlus_ZapDisable=1
```

<span data-ttu-id="ac45b-194">このように変更すると、すべての .NET コードに対するシンボルが取得されるはずです。</span><span class="sxs-lookup"><span data-stu-id="ac45b-194">With this change, you should get the symbols for all .NET code.</span></span>

## <a name="get-symbols-for-the-native-runtime"></a><span data-ttu-id="ac45b-195">ネイティブ ランタイムのシンボルを取得する</span><span class="sxs-lookup"><span data-stu-id="ac45b-195">Get symbols for the native runtime</span></span>

<span data-ttu-id="ac45b-196">ほとんどの場合、関心があるのは独自のコードであり、それは `perfcollect` によって既定で解決されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-196">Most of the time you are interested in your own code, which `perfcollect` resolves by default.</span></span> <span data-ttu-id="ac45b-197">場合によっては、NET DLL の内部で起こっていること (最後のセクションの内容) を確認すると役に立つことがありますが、ネイティブ ランタイム dll (通常は libcoreclr.so) で何が起こっているかは興味深いものです。</span><span class="sxs-lookup"><span data-stu-id="ac45b-197">Sometimes it is useful to see what is going on inside the .NET DLLs (which is what the last section was about), but sometimes what is going on in the native runtime dlls (typically libcoreclr.so), is interesting.</span></span>  <span data-ttu-id="ac45b-198">`perfcollect` によってデータの変換時にこれらに対するシンボルが解決されますが、これらのネイティブ DLL のシンボルが存在する場合 (および、それらが対象のライブラリの隣にある場合) に限られます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-198">`perfcollect` will resolve the symbols for these when it converts its data, but only if the symbols for these native DLLs are present (and are beside the library they are for).</span></span>

<span data-ttu-id="ac45b-199">これを行う [dotnet-symbol](https://github.com/dotnet/symstore/blob/main/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) という名前のグローバル コマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-199">There is a global command called [dotnet-symbol](https://github.com/dotnet/symstore/blob/main/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) that does this.</span></span> <span data-ttu-id="ac45b-200">dotnet-symbol を使用してネイティブ ランタイム シンボルを取得するには:</span><span class="sxs-lookup"><span data-stu-id="ac45b-200">To use dotnet-symbol to get native runtime symbols:</span></span>

1. <span data-ttu-id="ac45b-201">`dotnet-symbol` をインストールします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-201">Install `dotnet-symbol`:</span></span>

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. <span data-ttu-id="ac45b-202">シンボルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-202">Download the symbols.</span></span> <span data-ttu-id="ac45b-203">インストールされている .NET Core ランタイムのバージョンが 2.1.0 の場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-203">If your installed version of the .NET Core runtime is 2.1.0, the command to do this is:</span></span>

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. <span data-ttu-id="ac45b-204">シンボルを正しい場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-204">Copy the symbols to the correct place.</span></span>

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    <span data-ttu-id="ac45b-205">適切なディレクトリへの書き込みアクセス権がないためにこの操作を実行できない場合は、`perf buildid-cache` を使用してシンボルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-205">If this cannot be done because you do not have write access to the appropriate directory, you can use `perf buildid-cache` to add the symbols.</span></span>

<span data-ttu-id="ac45b-206">その後、`perfcollect` を実行するときに、ネイティブ dll のシンボル名を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-206">After this, you should get symbolic names for the native dlls when you run `perfcollect`.</span></span>

## <a name="collect-in-a-docker-container"></a><span data-ttu-id="ac45b-207">Docker コンテナー内で収集する</span><span class="sxs-lookup"><span data-stu-id="ac45b-207">Collect in a Docker container</span></span>

<span data-ttu-id="ac45b-208">コンテナー環境で `perfcollect` を使用する方法の詳細については、「[コンテナーでの診断の収集](./diagnostics-in-containers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac45b-208">For more information on how to use `perfcollect` in container environments, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

## <a name="learn-more-about-collection-options"></a><span data-ttu-id="ac45b-209">収集オプションについての詳細情報</span><span class="sxs-lookup"><span data-stu-id="ac45b-209">Learn more about collection options</span></span>

<span data-ttu-id="ac45b-210">診断のニーズに合わせて、`perfcollect` を使用して次のオプションのフラグを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-210">You can specify the following optional flags with `perfcollect` to better suit your diagnostic needs.</span></span>

### <a name="collect-for-a-specific-duration"></a><span data-ttu-id="ac45b-211">特定の期間について収集する</span><span class="sxs-lookup"><span data-stu-id="ac45b-211">Collect for a specific duration</span></span>

<span data-ttu-id="ac45b-212">特定の期間についてトレースを収集する場合は、`-collectsec` オプションに続けて、トレースを収集する合計秒数を数値で指定できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-212">When you want to collect a trace for a specific duration, you can use `-collectsec` option followed by a number specifying the total seconds to collect a trace for.</span></span>

### <a name="collect-threadtime-traces"></a><span data-ttu-id="ac45b-213">threadtime のトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="ac45b-213">Collect threadtime traces</span></span>

<span data-ttu-id="ac45b-214">`-threadtime` と共に `perfcollect` を指定すると、スレッドごとの CPU 使用率データを収集できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-214">Specifying `-threadtime` with `perfcollect` lets you collect per-thread CPU usage data.</span></span> <span data-ttu-id="ac45b-215">これにより、各スレッドが CPU 時間を費やしていた場所を分析できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-215">This lets you analyze where every thread was spending its CPU time.</span></span>

### <a name="collect-traces-for-managed-memory-and-garbage-collector-performance"></a><span data-ttu-id="ac45b-216">マネージド メモリとガベージ コレクターのパフォーマンスのトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="ac45b-216">Collect traces for managed memory and garbage collector performance</span></span>

<span data-ttu-id="ac45b-217">次のオプションを使用すると、ランタイムから特に GC イベントを収集できます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-217">The following options let you specifically collect the GC events from the runtime.</span></span>

* `perfcollect collect -gccollectonly`

<span data-ttu-id="ac45b-218">GC 収集イベントの最小セットのみを収集します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-218">Collect only a minimal set of GC Collection events.</span></span> <span data-ttu-id="ac45b-219">これは、ターゲット アプリのパフォーマンスへの影響が最も少ない、最も詳細度の低い GC イベント収集プロファイルです。</span><span class="sxs-lookup"><span data-stu-id="ac45b-219">This is the least verbose GC eventing collection profile with the lowest impact on the target app's performance.</span></span> <span data-ttu-id="ac45b-220">このコマンドは PerfView の `PerfView.exe /GCCollectOnly collect` コマンドと似ています。</span><span class="sxs-lookup"><span data-stu-id="ac45b-220">This command is analogous to `PerfView.exe /GCCollectOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gconly`

<span data-ttu-id="ac45b-221">JIT、ローダー、例外イベントを使用して、より詳細な GC 収集イベントを収集します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-221">Collect more verbose GC collection events with JIT, Loader, and Exception events.</span></span> <span data-ttu-id="ac45b-222">これにより、より詳細なイベント (割り当て情報や GC 結合情報など) が要求され、`-gccollectonly` オプションよりもターゲット アプリのパフォーマンスに大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="ac45b-222">This requests more verbose events (such as the allocation information and GC join information) and will have more impact to the target app's performance than `-gccollectonly` option.</span></span> <span data-ttu-id="ac45b-223">このコマンドは PerfView の `PerfView.exe /GCOnly collect` コマンドと似ています。</span><span class="sxs-lookup"><span data-stu-id="ac45b-223">This command is analogous to `PerfView.exe /GCOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gcwithheap`

<span data-ttu-id="ac45b-224">最も詳細な GC コレクション イベントを収集します。これにより、ヒープの存続と移動も追跡されます。</span><span class="sxs-lookup"><span data-stu-id="ac45b-224">Collect the most verbose GC collection events which tracks the heap survival and movements as well.</span></span> <span data-ttu-id="ac45b-225">これにより、GC の動作を詳細に分析できますが、各 GC に 2 倍以上の時間がかかるおそれがあるため、パフォーマンス コストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="ac45b-225">This gives in-depth analysis of the GC behavior but will incur high performance cost as each GC can take more than two times longer.</span></span> <span data-ttu-id="ac45b-226">運用環境でトレースするときにこのトレース オプションを使用した場合のパフォーマンスへの影響を理解しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ac45b-226">It is recommended you understand the performance implication of using this trace option when tracing in production environments.</span></span>
