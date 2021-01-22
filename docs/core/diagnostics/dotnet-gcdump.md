---
title: dotnet-gcdump 診断ツール - .NET CLI
description: dotnet-gcdump CLI ツールをインストールして使用し、.NET EventPipe を使ってライブ .NET プロセスの GC (ガベージ コレクター) ダンプを収集する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: fe7772eed642daadbd1754627751f58d0ab57b8e
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188570"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="db587-103">ヒープ分析ツール (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="db587-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="db587-104">**この記事の対象:** ✔️ .NET Core 3.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="db587-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="db587-105">インストール</span><span class="sxs-lookup"><span data-stu-id="db587-105">Install</span></span>

<span data-ttu-id="db587-106">`dotnet-gcdump` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="db587-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="db587-107">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="db587-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="db587-108">`dotnet-gcdump` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-gcdump)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="db587-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="db587-109">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="db587-109">**Direct download:**</span></span>

  <span data-ttu-id="db587-110">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="db587-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="db587-111">OS</span><span class="sxs-lookup"><span data-stu-id="db587-111">OS</span></span>  | <span data-ttu-id="db587-112">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="db587-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="db587-113">Windows</span><span class="sxs-lookup"><span data-stu-id="db587-113">Windows</span></span> | <span data-ttu-id="db587-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="db587-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="db587-115">macOS</span><span class="sxs-lookup"><span data-stu-id="db587-115">macOS</span></span>   | [<span data-ttu-id="db587-116">x64</span><span class="sxs-lookup"><span data-stu-id="db587-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="db587-117">Linux</span><span class="sxs-lookup"><span data-stu-id="db587-117">Linux</span></span>   | <span data-ttu-id="db587-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="db587-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="db587-119">x86 アプリ上で `dotnet-gcdump` を使用するには、対応する x86 バージョンのツールが必要です。</span><span class="sxs-lookup"><span data-stu-id="db587-119">To use `dotnet-gcdump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db587-120">構文</span><span class="sxs-lookup"><span data-stu-id="db587-120">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="db587-121">説明</span><span class="sxs-lookup"><span data-stu-id="db587-121">Description</span></span>

<span data-ttu-id="db587-122">`dotnet-gcdump` グローバル ツールで [EventPipe](./eventpipe.md) を使用して、ライブ .NET プロセスの GC (ガベージ コレクター) ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="db587-122">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="db587-123">GC ダンプを作成するには、ターゲット プロセスで GC をトリガーし、特殊なイベントを有効にし、イベント ストリームからオブジェクト ルートのグラフを再生成します。</span><span class="sxs-lookup"><span data-stu-id="db587-123">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="db587-124">このプロセスにより、プロセスの実行中のオーバーヘッドを最小限に抑えながら GC ダンプを収集できます。</span><span class="sxs-lookup"><span data-stu-id="db587-124">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="db587-125">このようなダンプは、いくつかのシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="db587-125">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="db587-126">複数の時点でヒープ上にあるオブジェクト数を比較する。</span><span class="sxs-lookup"><span data-stu-id="db587-126">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="db587-127">オブジェクトのルートを分析する ("この種類に対する参照がまだ残っているものはあるか" などの質問に回答する場合)。</span><span class="sxs-lookup"><span data-stu-id="db587-127">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="db587-128">ヒープ上のオブジェクト数に関する一般的な統計情報を収集する。</span><span class="sxs-lookup"><span data-stu-id="db587-128">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="db587-129">dotnet-gcdump からキャプチャされた GC ダンプを表示する</span><span class="sxs-lookup"><span data-stu-id="db587-129">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="db587-130">Windows では、分析のために [PerfView](https://github.com/microsoft/perfview) で、または Visual Studio で `.gcdump` ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="db587-130">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="db587-131">現在、Windows 以外のプラットフォームで `.gcdump` を開く方法はありません。</span><span class="sxs-lookup"><span data-stu-id="db587-131">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="db587-132">複数の `.gcdump` を収集し、それらを Visual Studio で同時に開いて、比較を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="db587-132">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="db587-133">Options</span><span class="sxs-lookup"><span data-stu-id="db587-133">Options</span></span>

- **`--version`**

  <span data-ttu-id="db587-134">`dotnet-gcdump` ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="db587-134">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="db587-135">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="db587-135">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="db587-136">現在実行中のプロセスから GC ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="db587-136">Collects a GC dump from a currently running process.</span></span>

> [!WARNING]
> <span data-ttu-id="db587-137">GC ヒープをウォークするために、このコマンドによって第 2 世代の (完全な) ガベージ コレクションがトリガーされます。これにより、特に GC ヒープが大きい場合に、ランタイムが長時間中断されるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="db587-137">To walk the GC heap, this command triggers a generation 2 (full) garbage collection, which can suspend the runtime for a long time, especially when the GC heap is large.</span></span> <span data-ttu-id="db587-138">GC ヒープが大きい場合、パフォーマンスを重視する環境ではこのコマンドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="db587-138">Don't use this command in performance-sensitive environments when the GC heap is large.</span></span>

### <a name="synopsis"></a><span data-ttu-id="db587-139">構文</span><span class="sxs-lookup"><span data-stu-id="db587-139">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="db587-140">オプション</span><span class="sxs-lookup"><span data-stu-id="db587-140">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="db587-141">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="db587-141">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="db587-142">GC ダンプを収集するプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="db587-142">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="db587-143">収集された GC ダンプが書き込まれるパス。</span><span class="sxs-lookup"><span data-stu-id="db587-143">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="db587-144">既定値は *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump* です。</span><span class="sxs-lookup"><span data-stu-id="db587-144">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="db587-145">GC ダンプの収集時にログを出力します。</span><span class="sxs-lookup"><span data-stu-id="db587-145">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="db587-146">この秒数より長くかかる場合は、GC ダンプの収集をあきらめてください。</span><span class="sxs-lookup"><span data-stu-id="db587-146">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="db587-147">既定値は 30 です。</span><span class="sxs-lookup"><span data-stu-id="db587-147">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="db587-148">GC ダンプを収集するプロセスの名前。</span><span class="sxs-lookup"><span data-stu-id="db587-148">The name of the process to collect the GC dump from.</span></span>

> [!NOTE]
> <span data-ttu-id="db587-149">Linux と macOS 上でこのコマンドを使用するには、ターゲット アプリケーションと `dotnet-gcdump` で同じ `TMPDIR` 環境変数が共有されることが前提とされています。</span><span class="sxs-lookup"><span data-stu-id="db587-149">On Linux and macOS, this command expects the target application and `dotnet-gcdump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="db587-150">それ以外の場合、このコマンドはタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="db587-150">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="db587-151">`dotnet-gcdump` を使用して GC ダンプを収集するには、ターゲット プロセスを実行しているユーザーと同じユーザーとして、またはルートとしてそれを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db587-151">To collect a GC dump using `dotnet-gcdump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="db587-152">それ以外の場合、このツールでターゲット プロセスとの接続を確立することはできません。</span><span class="sxs-lookup"><span data-stu-id="db587-152">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="db587-153">GC ダンプを収集できる dotnet プロセスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="db587-153">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="db587-154">概要</span><span class="sxs-lookup"><span data-stu-id="db587-154">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="db587-155">以前に生成された GC ダンプまたは実行中のプロセスからレポートを生成し、`stdout` に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="db587-155">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="db587-156">構文</span><span class="sxs-lookup"><span data-stu-id="db587-156">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="db587-157">オプション</span><span class="sxs-lookup"><span data-stu-id="db587-157">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="db587-158">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="db587-158">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="db587-159">GC ダンプを収集するプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="db587-159">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="db587-160">生成するレポートの種類。</span><span class="sxs-lookup"><span data-stu-id="db587-160">The type of report to generate.</span></span> <span data-ttu-id="db587-161">使用可能なオプション: heapstat (既定値)。</span><span class="sxs-lookup"><span data-stu-id="db587-161">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="db587-162">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="db587-162">Troubleshoot</span></span>

- <span data-ttu-id="db587-163">gcdump に型情報はありません。</span><span class="sxs-lookup"><span data-stu-id="db587-163">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="db587-164">.NET Core 3.1 より前のバージョンでは、EventPipe を使って呼び出されたときに、gcdump 間で型キャッシュがクリアされない問題がありました。</span><span class="sxs-lookup"><span data-stu-id="db587-164">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="db587-165">これにより、型情報を判別するために必要なイベントが 2 番目以降の gcdump に対して送信されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="db587-165">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="db587-166">これは .NET Core 3.1-preview2 で修正されました。</span><span class="sxs-lookup"><span data-stu-id="db587-166">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="db587-167">COM 型と静的な型は GC ダンプに含まれていません。</span><span class="sxs-lookup"><span data-stu-id="db587-167">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="db587-168">.NET Core 3.1-preview2 より前のバージョンでは、EventPipe を介して GC ダンプが呼び出されたときに静的な型と COM 型が送信されない問題がありました。</span><span class="sxs-lookup"><span data-stu-id="db587-168">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="db587-169">これは .NET Core 3.1-preview2 で修正されました。</span><span class="sxs-lookup"><span data-stu-id="db587-169">This has been fixed in .NET Core 3.1-preview2.</span></span>
