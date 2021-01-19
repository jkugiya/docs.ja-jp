---
title: ダンプ - .NET
description: .NET でのダンプの概要。
ms.date: 10/12/2020
ms.openlocfilehash: f68d9bd804350366625df014df4d9ca0641d5d4d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188557"
---
# <a name="dumps"></a><span data-ttu-id="aab70-103">ダンプ</span><span class="sxs-lookup"><span data-stu-id="aab70-103">Dumps</span></span>

<span data-ttu-id="aab70-104">ダンプは、その作成時におけるプロセスのスナップショットを含むファイルであり、アプリケーションの状態を調べるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aab70-104">A dump is a file that contains a snapshot of the process at the time it was created and can be useful for examining the state of your application.</span></span> <span data-ttu-id="aab70-105">運用または CI 環境などにデバッガーをアタッチするのが困難な場合に、.NET アプリケーションをデバッグするためにタンプを使用できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-105">Dumps can be used to debug your .NET application when it is difficult to attach a debugger to it such as production or CI environments.</span></span> <span data-ttu-id="aab70-106">ダンプを使用すると、アプリケーションを停止しなくても、問題のあるプロセスの状態をキャプチャして調べることができます。</span><span class="sxs-lookup"><span data-stu-id="aab70-106">Using dumps allows you to capture the state of the problematic process and examine it without having to stop the application.</span></span>

## <a name="collect-dumps"></a><span data-ttu-id="aab70-107">ダンプを収集する</span><span class="sxs-lookup"><span data-stu-id="aab70-107">Collect dumps</span></span>

<span data-ttu-id="aab70-108">ダンプは、アプリを実行しているプラットフォームに応じてさまざまな方法で収集できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-108">Dumps can be collected in a variety of ways depending on which platform you are running your app on.</span></span>

> [!NOTE]
> <span data-ttu-id="aab70-109">コンテナー内のダンプを収集するには、PTRACE 機能が必要です。これは、`--cap-add=SYS_PTRACE` または `--privileged` を使用して追加できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-109">Collecting a dump inside a container requires PTRACE capability, which can be added via `--cap-add=SYS_PTRACE` or `--privileged`.</span></span>
> [!NOTE]
> <span data-ttu-id="aab70-110">ダンプには、実行中のプロセスの完全なメモリが含まれている可能性があるため、機密情報が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="aab70-110">Dumps may contain sensitive information because they can contain the full memory of the running process.</span></span> <span data-ttu-id="aab70-111">セキュリティに関する制限事項とガイダンスを考慮して扱うようにしてください。</span><span class="sxs-lookup"><span data-stu-id="aab70-111">Handle them with any security restrictions and guidances in mind.</span></span>

### <a name="collecting-dumps-on-crash"></a><span data-ttu-id="aab70-112">クラッシュ時のダンプの収集</span><span class="sxs-lookup"><span data-stu-id="aab70-112">Collecting dumps on crash</span></span>

<span data-ttu-id="aab70-113">環境変数を使用すると、クラッシュ時にダンプを収集するようにアプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-113">You can use environment variables to configure your application to collect a dump upon a crash.</span></span> <span data-ttu-id="aab70-114">これは、クラッシュが発生した理由を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aab70-114">This is helpful when you want to get an understanding of why a crash happened.</span></span> <span data-ttu-id="aab70-115">たとえば、例外がスローされたときにダンプをキャプチャすると、クラッシュ時にアプリの状態を調べて問題を特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aab70-115">For example, capturing a dump when an exception is thrown helps you identify an issue by examining the state of the app when it crashed.</span></span>

<span data-ttu-id="aab70-116">次の表には、クラッシュ時にダンプを収集するために構成できる環境変数が示されています。</span><span class="sxs-lookup"><span data-stu-id="aab70-116">The following table shows the environment variables you can configure for collecting dumps on a crash.</span></span>

|<span data-ttu-id="aab70-117">環境変数</span><span class="sxs-lookup"><span data-stu-id="aab70-117">Environment variable</span></span>|<span data-ttu-id="aab70-118">説明</span><span class="sxs-lookup"><span data-stu-id="aab70-118">Description</span></span>|<span data-ttu-id="aab70-119">既定値</span><span class="sxs-lookup"><span data-stu-id="aab70-119">Default value</span></span>|
|-------|---------|---|
|`COMPlus_DbgEnableMiniDump`|<span data-ttu-id="aab70-120">1 に設定すると、コア ダンプ生成が有効になります。</span><span class="sxs-lookup"><span data-stu-id="aab70-120">If set to 1, enable core dump generation.</span></span>|<span data-ttu-id="aab70-121">0</span><span class="sxs-lookup"><span data-stu-id="aab70-121">0</span></span>|
|`COMPlus_DbgMiniDumpType`|<span data-ttu-id="aab70-122">収集されるダンプの種類。</span><span class="sxs-lookup"><span data-stu-id="aab70-122">Type of dump to be collected.</span></span> <span data-ttu-id="aab70-123">詳細については、以下の表を参照してください</span><span class="sxs-lookup"><span data-stu-id="aab70-123">For more information, see the table below</span></span>|<span data-ttu-id="aab70-124">2 (`MiniDumpWithPrivateReadWriteMemory`)</span><span class="sxs-lookup"><span data-stu-id="aab70-124">2 (`MiniDumpWithPrivateReadWriteMemory`)</span></span>|
|`COMPlus_DbgMiniDumpName`|<span data-ttu-id="aab70-125">ダンプの書き込み先ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="aab70-125">Path to a file to write the dump to.</span></span>|`/tmp/coredump.<pid>`|
|`COMPlus_CreateDumpDiagnostics`|<span data-ttu-id="aab70-126">1 に設定すると、ダンプ プロセスの診断ログが有効になります。</span><span class="sxs-lookup"><span data-stu-id="aab70-126">If set to 1, enable diagnostic logging of dump process.</span></span>|<span data-ttu-id="aab70-127">0</span><span class="sxs-lookup"><span data-stu-id="aab70-127">0</span></span>|

<span data-ttu-id="aab70-128">次の表には、`COMPlus_DbgMiniDumpType` に使用できるすべてのオプションが示されています。これは値として指定できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-128">The table below shows all the options you may use for `COMPlus_DbgMiniDumpType` which can be specified as a value.</span></span> <span data-ttu-id="aab70-129">たとえば、`COMPlus_DbgMiniDumpType` を 1 に設定した場合、クラッシュ時に `MiniDumpNormal` 型ダンプが収集されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="aab70-129">For example, setting `COMPlus_DbgMiniDumpType` to 1 means `MiniDumpNormal` type dump will be collected on a crash.</span></span>

|<span data-ttu-id="aab70-130">値</span><span class="sxs-lookup"><span data-stu-id="aab70-130">Value</span></span>|<span data-ttu-id="aab70-131">名前</span><span class="sxs-lookup"><span data-stu-id="aab70-131">Name</span></span>|<span data-ttu-id="aab70-132">説明</span><span class="sxs-lookup"><span data-stu-id="aab70-132">Description</span></span>|
|-----|----|-----------|
|<span data-ttu-id="aab70-133">1</span><span class="sxs-lookup"><span data-stu-id="aab70-133">1</span></span>|`MiniDumpNormal`|<span data-ttu-id="aab70-134">プロセス内のすべての既存のスレッドのスタック トレースをキャプチャするために必要な情報のみを含めます。</span><span class="sxs-lookup"><span data-stu-id="aab70-134">Include just the information necessary to capture stack traces for all existing threads in a process.</span></span> <span data-ttu-id="aab70-135">GC ヒープ メモリと情報が制限されます。</span><span class="sxs-lookup"><span data-stu-id="aab70-135">Limited GC heap memory and information.</span></span>|
|<span data-ttu-id="aab70-136">2</span><span class="sxs-lookup"><span data-stu-id="aab70-136">2</span></span>|`MiniDumpWithPrivateReadWriteMemory`|<span data-ttu-id="aab70-137">プロセス内のすべての既存のスレッドのスタック トレースをキャプチャするために必要な GC ヒープと情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aab70-137">Includes the GC heaps and information necessary to capture stack traces for all existing threads in a process.</span></span>|
|<span data-ttu-id="aab70-138">3</span><span class="sxs-lookup"><span data-stu-id="aab70-138">3</span></span>|`MiniDumpFilterTriage`|<span data-ttu-id="aab70-139">プロセス内のすべての既存のスレッドのスタック トレースをキャプチャするために必要な情報のみを含めます。</span><span class="sxs-lookup"><span data-stu-id="aab70-139">Include just the information necessary to capture stack traces for all existing threads in a process.</span></span> <span data-ttu-id="aab70-140">GC ヒープ メモリと情報が制限されます。</span><span class="sxs-lookup"><span data-stu-id="aab70-140">Limited GC heap memory and information.</span></span>|
|<span data-ttu-id="aab70-141">4</span><span class="sxs-lookup"><span data-stu-id="aab70-141">4</span></span>|`MiniDumpWithFullMemory`|<span data-ttu-id="aab70-142">プロセス内のすべてのアクセス可能なメモリを含めます。</span><span class="sxs-lookup"><span data-stu-id="aab70-142">Include all accessible memory in the process.</span></span> <span data-ttu-id="aab70-143">生のメモリ データは最後に含まれるため、初期構造は生のメモリ情報なしで直接マップできます。</span><span class="sxs-lookup"><span data-stu-id="aab70-143">The raw memory data is included at the end, so that the initial structures can be mapped directly without the raw memory information.</span></span> <span data-ttu-id="aab70-144">このオプションを使用すると、ファイルが非常に大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aab70-144">This option can result in a very large file.</span></span>|

### <a name="collecting-dumps-at-specific-point-in-time"></a><span data-ttu-id="aab70-145">特定の時点でのダンプの収集</span><span class="sxs-lookup"><span data-stu-id="aab70-145">Collecting dumps at specific point in time</span></span>

<span data-ttu-id="aab70-146">アプリがまだクラッシュしていない場合は、ダンプを収集することができます。</span><span class="sxs-lookup"><span data-stu-id="aab70-146">You may want to collect a dump when the app hasn't crashed yet.</span></span> <span data-ttu-id="aab70-147">たとえば、デッドロックが発生していると思われるアプリケーションの状態を確認する場合、クラッシュ時にダンプを収集するように環境変数を構成しても役に立ちません。これは、アプリがまだ実行中であるためです。</span><span class="sxs-lookup"><span data-stu-id="aab70-147">For example, if you want to examine the state of an application that seems to be in a deadlock, configuring the environment variables to collect dumps on crash will not be helpful because the app is still running.</span></span>

<span data-ttu-id="aab70-148">独自の要求でダンプを収集するために、ダンプを収集して分析するための CLI ツールである `dotnet-dump` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-148">To collect dump at your own request, you can use `dotnet-dump`, which is a CLI tool for collecting and analyzing dumps.</span></span> <span data-ttu-id="aab70-149">`dotnet-dump` を使用してダンプを収集する方法について詳しくは、「[ダンプの収集と分析のユーティリティ](dotnet-dump.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aab70-149">For more information on how to use it to collect dumps with `dotnet-dump`, see [Dump collection and analysis utility](dotnet-dump.md).</span></span>

## <a name="analyze-dumps"></a><span data-ttu-id="aab70-150">ダンプを分析する</span><span class="sxs-lookup"><span data-stu-id="aab70-150">Analyze dumps</span></span>

<span data-ttu-id="aab70-151">[`dotnet-dump`](dotnet-dump.md) CLI ツールか [Visual Studio](/visualstudio/debugger/using-dump-files) を使用し、ダンプを分析できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-151">You can anlayze dumps using the [`dotnet-dump`](dotnet-dump.md) CLI tool or with [Visual Studio](/visualstudio/debugger/using-dump-files).</span></span>

> [!NOTE]
> <span data-ttu-id="aab70-152">Visual Studio バージョン 16.8 以降では、.NET Core 3.1.7 以降で生成された [Linux ダンプ](https://devblogs.microsoft.com/visualstudio/linux-managed-memory-dump-debugging/)を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="aab70-152">Visual Studio version 16.8 and later allows you to [open Linux dumps](https://devblogs.microsoft.com/visualstudio/linux-managed-memory-dump-debugging/) generated on .NET Core 3.1.7 or later.</span></span>  
> [!NOTE]
> <span data-ttu-id="aab70-153">ネイティブ デバッグが必要な場合、[SOS デバッガー拡張機能](sos-debugging-extension.md)を [Linux と macOS で LLDB](debug-linux-dumps.md#analyze-dumps-on-linux) と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="aab70-153">If native debugging is necessary, the [SOS debugger extension](sos-debugging-extension.md) can be used with [LLDB on Linux and macOS](debug-linux-dumps.md#analyze-dumps-on-linux).</span></span> <span data-ttu-id="aab70-154">SOS は、Windows の場合、[Windbg/cdb](/windows-hardware/drivers/debugger/debugger-download-tools) でもサポートされています。ただし、Visual Studio が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="aab70-154">SOS is also supported with [Windbg/cdb](/windows-hardware/drivers/debugger/debugger-download-tools) on Windows, although Visual Studio is recommended.</span></span>

## <a name="see-also"></a><span data-ttu-id="aab70-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="aab70-155">See also</span></span>

<span data-ttu-id="aab70-156">.NET アプリケーションでの問題を診断するのに役立つようにダンプを活用する方法について、さらに詳しく学習します。</span><span class="sxs-lookup"><span data-stu-id="aab70-156">Learn more about how you can leverage dumps to help diagnosing problems in your .NET application.</span></span>

* <span data-ttu-id="aab70-157">[Linux ダンプのデバッグ](debug-linux-dumps.md) チュートリアルでは、Linux で収集されたダンプをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aab70-157">[Debug Linux dumps](debug-linux-dumps.md) tutorial walks you through how to debug a dump that was collected in Linux.</span></span>

* <span data-ttu-id="aab70-158">[デッドロックのデバッグ](debug-deadlock.md) チュートリアルでは、ダンプを使用して .NET アプリケーションでデッドロックをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aab70-158">[Debug deadlock](debug-deadlock.md) tutorial walks you through how to debug a deadlock in your .NET application using dumps.</span></span>
