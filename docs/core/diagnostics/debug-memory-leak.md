---
title: メモリ リークのデバッグ チュートリアル
description: .NET Core でメモリ リークをデバッグする方法について説明します。
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: 09777b6c9f80c28e1eec28983d605f2a2e261c92
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872744"
---
# <a name="debug-a-memory-leak-in-net-core"></a><span data-ttu-id="8f004-103">.NET Core でメモリ リークをデバッグする</span><span class="sxs-lookup"><span data-stu-id="8f004-103">Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="8f004-104">**この記事の対象:** ✔️ .NET Core 3.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="8f004-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="8f004-105">アプリで必要なタスクを実行する必要がなくなったオブジェクトを参照すると、メモリ リークが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="8f004-105">A memory leak may happen when your app references objects that it no longer needs to perform the desired task.</span></span> <span data-ttu-id="8f004-106">このようなオブジェクトを参照すると、ガベージ コレクターが使用済みメモリを再利用できなくなるため、多くの場合、パフォーマンスが低下し、<xref:System.OutOfMemoryException> がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8f004-106">Referencing said objects makes the garbage collector to be unable to reclaim the memory used, often resulting in performance degradation and potentially end up throwing a <xref:System.OutOfMemoryException>.</span></span>

<span data-ttu-id="8f004-107">このチュートリアルでは、.NET 診断 CLI ツールを使用して .NET Core アプリのメモリ リークを分析するためのツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8f004-107">This tutorial demonstrates the tools to analyze a memory leak in a .NET Core app using the .NET diagnostics CLI tools.</span></span> <span data-ttu-id="8f004-108">Windows を使用している場合は、[Visual Studio のメモリ診断ツール](/visualstudio/profiling/memory-usage)を使用して、メモリ リークをデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="8f004-108">If you are on Windows, you may be able to [use Visual Studio's Memory Diagnostic tools](/visualstudio/profiling/memory-usage) to debug the memory leak.</span></span>

<span data-ttu-id="8f004-109">このチュートリアルでは、意図的にメモリをリークするように設計されたサンプル アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="8f004-109">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="8f004-110">このサンプルは演習として提供されています。</span><span class="sxs-lookup"><span data-stu-id="8f004-110">The sample is provided as an exercise.</span></span> <span data-ttu-id="8f004-111">意図せずにメモリをリークしているアプリも分析できます。</span><span class="sxs-lookup"><span data-stu-id="8f004-111">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="8f004-112">このチュートリアルでは、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="8f004-112">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8f004-113">[dotnet-counters](dotnet-counters.md) を使用してマネージド メモリの使用量を確認します。</span><span class="sxs-lookup"><span data-stu-id="8f004-113">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="8f004-114">ダンプ ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="8f004-114">Generate a dump file.</span></span>
> - <span data-ttu-id="8f004-115">ダンプ ファイルを使用してメモリ使用量を分析します。</span><span class="sxs-lookup"><span data-stu-id="8f004-115">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8f004-116">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8f004-116">Prerequisites</span></span>

<span data-ttu-id="8f004-117">このチュートリアルでは次のものを使用します。</span><span class="sxs-lookup"><span data-stu-id="8f004-117">The tutorial uses:</span></span>

- <span data-ttu-id="8f004-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="8f004-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version.</span></span>
- <span data-ttu-id="8f004-119">マネージド メモリ使用量を確認するための [dotnet-counters](dotnet-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="8f004-119">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="8f004-120">ダンプ ファイルを収集して分析するための [dotnet-dump](dotnet-dump.md)。</span><span class="sxs-lookup"><span data-stu-id="8f004-120">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="8f004-121">診断する[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios/) アプリ。</span><span class="sxs-lookup"><span data-stu-id="8f004-121">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="8f004-122">このチュートリアルでは、サンプルとツールがインストールされ、使用できる状態であることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="8f004-122">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="8f004-123">マネージド メモリ使用量を確認する</span><span class="sxs-lookup"><span data-stu-id="8f004-123">Examine managed memory usage</span></span>

<span data-ttu-id="8f004-124">このシナリオの根本原因を突き止めるのに役立つ診断データの収集を開始する前に、メモリ リーク (メモリの増加) が実際に発生していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f004-124">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="8f004-125">それを確認するには、[dotnet-counters](dotnet-counters.md) ツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f004-125">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="8f004-126">コンソール ウィンドウを開き、[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios/)をダウンロードして解凍したディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="8f004-126">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="8f004-127">ターゲットを実行します。</span><span class="sxs-lookup"><span data-stu-id="8f004-127">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="8f004-128">別のコンソールから、プロセス ID を見つけます。</span><span class="sxs-lookup"><span data-stu-id="8f004-128">From a separate console, find the process ID:</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="8f004-129">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8f004-129">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="8f004-130">次に、[dotnet-counters](dotnet-counters.md) ツールを使用してマネージド メモリ使用量を確認します。</span><span class="sxs-lookup"><span data-stu-id="8f004-130">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="8f004-131">`--refresh-interval` は、更新間隔を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="8f004-131">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="8f004-132">ライブ出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8f004-132">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="8f004-133">次の行に焦点を当てます。</span><span class="sxs-lookup"><span data-stu-id="8f004-133">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="8f004-134">スタートアップの直後、マネージド ヒープ メモリは 4 MB であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8f004-134">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="8f004-135">次に、URL `https://localhost:5001/api/diagscenario/memleak/20000` を指定します。</span><span class="sxs-lookup"><span data-stu-id="8f004-135">Now, hit the URL `https://localhost:5001/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="8f004-136">メモリ使用量が 30 MB に増加していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8f004-136">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="8f004-137">メモリ使用量を監視することにより、メモリが増加していること、またはリークしていることを確実に知ることができます。</span><span class="sxs-lookup"><span data-stu-id="8f004-137">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="8f004-138">次の手順では、メモリ分析に適切なデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="8f004-138">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="8f004-139">メモリ ダンプを生成する</span><span class="sxs-lookup"><span data-stu-id="8f004-139">Generate memory dump</span></span>

<span data-ttu-id="8f004-140">メモリ リークの可能性について分析するときは、アプリのメモリ ヒープにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f004-140">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="8f004-141">その後、メモリーの内容を分析できます。</span><span class="sxs-lookup"><span data-stu-id="8f004-141">Then you can analyze the memory contents.</span></span> <span data-ttu-id="8f004-142">オブジェクト間の関係を確認して、メモリが解放されない理由についての理論を作成します。</span><span class="sxs-lookup"><span data-stu-id="8f004-142">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="8f004-143">一般的な診断データのソースは、Windows 上のメモリ ダンプ、または Linux 上の同等のコア ダンプです。</span><span class="sxs-lookup"><span data-stu-id="8f004-143">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="8f004-144">.NET Core アプリケーションのダンプを生成するには、[dotnet-dump](dotnet-dump.md) ツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f004-144">To generate a dump of a .NET Core application, you can use the [dotnet-dump](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="8f004-145">前に開始した[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios/)を使用して、次のコマンドを実行し、Linux コア ダンプを生成します。</span><span class="sxs-lookup"><span data-stu-id="8f004-145">Using the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="8f004-146">結果として、同じフォルダーにコア ダンプが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8f004-146">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="8f004-147">失敗したプロセスを再起動する</span><span class="sxs-lookup"><span data-stu-id="8f004-147">Restart the failed process</span></span>

<span data-ttu-id="8f004-148">ダンプが収集されると、失敗したプロセスを診断するのに十分な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="8f004-148">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="8f004-149">失敗したプロセスが運用サーバーで実行されている場合は、今が、そのプロセスを再起動して短期的な修復を行うのに最適なタイミングです。</span><span class="sxs-lookup"><span data-stu-id="8f004-149">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="8f004-150">このチュートリアルでは、[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios/)を終了したので、閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="8f004-150">In this tutorial, you're now done with the [Sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="8f004-151">サーバーを起動したターミナルに移動して、<kbd>Ctrl + C</kbd> を押します。</span><span class="sxs-lookup"><span data-stu-id="8f004-151">Navigate to the terminal that started the server, and press <kbd>Ctrl+C</kbd>.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="8f004-152">コア ダンプを分析する</span><span class="sxs-lookup"><span data-stu-id="8f004-152">Analyze the core dump</span></span>

<span data-ttu-id="8f004-153">コア ダンプが生成されたので、[dotnet-dump](dotnet-dump.md) ツールを使用してダンプを分析します。</span><span class="sxs-lookup"><span data-stu-id="8f004-153">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="8f004-154">ここで、`core_20190430_185145` は、分析するコア ダンプの名前です。</span><span class="sxs-lookup"><span data-stu-id="8f004-154">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="8f004-155">*libdl.so* が見つからないことを示すエラーが表示された場合は、*libc6-dev* パッケージのインストールが必要な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8f004-155">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="8f004-156">詳細については、「[Linux における .NET Core の前提条件](../install/linux.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f004-156">For more information, see [Prerequisites for .NET Core on Linux](../install/linux.md).</span></span>

<span data-ttu-id="8f004-157">SOS コマンドを入力できるプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f004-157">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="8f004-158">一般的に、最初に調べる必要があるのは、マネージド ヒープの全体的な状態です。</span><span class="sxs-lookup"><span data-stu-id="8f004-158">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="8f004-159">ここで、ほとんどのオブジェクトが `String` または `Customer` オブジェクトであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8f004-159">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="8f004-160">メソッド テーブル (MT) を指定して `dumpheap` コマンドを再び使用すると、すべての `String` インスタンスの一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="8f004-160">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="8f004-161">次に、`System.String` インスタンスで `gcroot` コマンドを使用して、このオブジェクトがルート指定されている方法と理由を確認します。</span><span class="sxs-lookup"><span data-stu-id="8f004-161">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="8f004-162">このコマンドは 30 MB のヒープで数分かかるため、しばらくお待ちください。</span><span class="sxs-lookup"><span data-stu-id="8f004-162">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="8f004-163">`String` が `Customer` オブジェクトによって直接保持され、`CustomerCache` オブジェクトによって間接的に保持されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8f004-163">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="8f004-164">オブジェクトのダンプを続けて、ほとんどの `String` オブジェクトが同様のパターンに従っていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8f004-164">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="8f004-165">この時点で、コードの根本原因を特定するのに十分な情報が調査によって提供されています。</span><span class="sxs-lookup"><span data-stu-id="8f004-165">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="8f004-166">この一般的な手順では、主要なメモリ リークの原因を特定できます。</span><span class="sxs-lookup"><span data-stu-id="8f004-166">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="8f004-167">リソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="8f004-167">Clean up resources</span></span>

<span data-ttu-id="8f004-168">このチュートリアルでは、サンプル Web サーバーを開始しました。</span><span class="sxs-lookup"><span data-stu-id="8f004-168">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="8f004-169">このサーバーは、「[失敗したプロセスを再起動する](#restart-the-failed-process)」セクションの説明に従ってシャットダウンされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f004-169">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="8f004-170">また、作成されたダンプ ファイルを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="8f004-170">You can also delete the dump file that was created.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f004-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f004-171">See also</span></span>

- <span data-ttu-id="8f004-172">[dotnet-trace](dotnet-trace.md) を使ってプロセスを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="8f004-172">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="8f004-173">[dotnet-counters](dotnet-counters.md) を使ってマネージド メモリ使用量を確認する</span><span class="sxs-lookup"><span data-stu-id="8f004-173">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="8f004-174">[dotnet-dump](dotnet-dump.md) を使ってダンプ ファイルを収集して分析する</span><span class="sxs-lookup"><span data-stu-id="8f004-174">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="8f004-175">dotnet/診断</span><span class="sxs-lookup"><span data-stu-id="8f004-175">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/main/documentation/tutorial)
- [<span data-ttu-id="8f004-176">Visual Studio を使用してメモリ リークをデバッグする</span><span class="sxs-lookup"><span data-stu-id="8f004-176">Use Visual Studio to debug memory leaks</span></span>](/visualstudio/profiling/memory-usage)

## <a name="next-steps"></a><span data-ttu-id="8f004-177">次の手順</span><span class="sxs-lookup"><span data-stu-id="8f004-177">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f004-178">.NET Core で高 CPU 使用率をデバッグする</span><span class="sxs-lookup"><span data-stu-id="8f004-178">Debug high CPU in .NET Core</span></span>](debug-highcpu.md)
