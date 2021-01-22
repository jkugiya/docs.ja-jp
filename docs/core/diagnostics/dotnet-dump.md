---
title: dotnet-dump 診断ツール - .NET CLI
description: dotnet-dump CLI ツールをインストールして使用し、ネイティブ デバッガーなしで Windows と Linux のダンプを収集して分析する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: 84b3796f4ee92880e6d432df606a6addfd2471b0
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189805"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="c56d3-103">ダンプの収集と分析のユーティリティ (dotnet-dump)</span><span class="sxs-lookup"><span data-stu-id="c56d3-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="c56d3-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="c56d3-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="c56d3-105">macOS の `dotnet-dump` は、.NET 5.0 以降のバージョンでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c56d3-105">`dotnet-dump` for macOS is only supported with .NET 5.0 and later versions.</span></span>

## <a name="install"></a><span data-ttu-id="c56d3-106">インストール</span><span class="sxs-lookup"><span data-stu-id="c56d3-106">Install</span></span>

<span data-ttu-id="c56d3-107">`dotnet-dump` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="c56d3-107">There are two ways to download and install `dotnet-dump`:</span></span>

- <span data-ttu-id="c56d3-108">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="c56d3-108">**dotnet global tool:**</span></span>

  <span data-ttu-id="c56d3-109">`dotnet-dump` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-dump)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-109">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- <span data-ttu-id="c56d3-110">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="c56d3-110">**Direct download:**</span></span>

  <span data-ttu-id="c56d3-111">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c56d3-111">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="c56d3-112">OS</span><span class="sxs-lookup"><span data-stu-id="c56d3-112">OS</span></span>  | <span data-ttu-id="c56d3-113">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="c56d3-113">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="c56d3-114">Windows</span><span class="sxs-lookup"><span data-stu-id="c56d3-114">Windows</span></span> | <span data-ttu-id="c56d3-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="c56d3-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span></span> |
  | <span data-ttu-id="c56d3-116">macOS</span><span class="sxs-lookup"><span data-stu-id="c56d3-116">macOS</span></span>   | [<span data-ttu-id="c56d3-117">x64</span><span class="sxs-lookup"><span data-stu-id="c56d3-117">x64</span></span>](https://aka.ms/dotnet-dump/osx-x64) |
  | <span data-ttu-id="c56d3-118">Linux</span><span class="sxs-lookup"><span data-stu-id="c56d3-118">Linux</span></span>   | <span data-ttu-id="c56d3-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="c56d3-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="c56d3-120">x86 アプリ上で `dotnet-dump` を使用するには、対応する x86 バージョンのツールが必要です。</span><span class="sxs-lookup"><span data-stu-id="c56d3-120">To use `dotnet-dump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c56d3-121">構文</span><span class="sxs-lookup"><span data-stu-id="c56d3-121">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="c56d3-122">説明</span><span class="sxs-lookup"><span data-stu-id="c56d3-122">Description</span></span>

<span data-ttu-id="c56d3-123">`dotnet-dump` グローバル ツールを使用すると、Linux の `lldb` などの任意のネイティブ デバッガーを使用せずに、Windows と Linux のダンプを収集して分析できます。</span><span class="sxs-lookup"><span data-stu-id="c56d3-123">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="c56d3-124">このツールは、`lldb` が完全に動作しない Alpine Linux などのプラットフォームで重要です。</span><span class="sxs-lookup"><span data-stu-id="c56d3-124">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="c56d3-125">`dotnet-dump` ツールでは、SOS コマンドを実行してクラッシュとガベージ コレクター (GC) を分析できますが、これはネイティブのデバッガーではないため、ネイティブ スタック フレームの表示などの操作はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c56d3-125">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="c56d3-126">オプション</span><span class="sxs-lookup"><span data-stu-id="c56d3-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="c56d3-127">dotnet-dump ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-127">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c56d3-128">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-128">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="c56d3-129">コマンド</span><span class="sxs-lookup"><span data-stu-id="c56d3-129">Commands</span></span>

| <span data-ttu-id="c56d3-130">コマンド</span><span class="sxs-lookup"><span data-stu-id="c56d3-130">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="c56d3-131">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="c56d3-131">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="c56d3-132">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="c56d3-132">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="c56d3-133">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="c56d3-133">dotnet-dump collect</span></span>

<span data-ttu-id="c56d3-134">プロセスからダンプをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="c56d3-134">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c56d3-135">構文</span><span class="sxs-lookup"><span data-stu-id="c56d3-135">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="c56d3-136">オプション</span><span class="sxs-lookup"><span data-stu-id="c56d3-136">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="c56d3-137">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-137">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="c56d3-138">ダンプを収集するプロセスの ID 番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-138">Specifies the process ID number to collect a dump from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="c56d3-139">ダンプを収集するプロセスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-139">Specifies the name of the process to collect a dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="c56d3-140">プロセスから収集する情報の種類を決定する、ダンプの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-140">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="c56d3-141">次の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="c56d3-141">There are three types:</span></span>

  - <span data-ttu-id="c56d3-142">`Full` - モジュール イメージを含むメモリをすべて含む最大のダンプ。</span><span class="sxs-lookup"><span data-stu-id="c56d3-142">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="c56d3-143">`Heap`: モジュールの一覧、スレッドの一覧、すべてのスタック、例外情報、ハンドル情報、およびマップされたイメージを除くすべてのメモリを含む、大規模で比較的包括的なダンプです。</span><span class="sxs-lookup"><span data-stu-id="c56d3-143">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="c56d3-144">`Mini`: モジュールの一覧、スレッドの一覧、例外情報、およびすべてのスタックを含む小さいダンプです。</span><span class="sxs-lookup"><span data-stu-id="c56d3-144">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="c56d3-145">指定しない場合の既定は、`Full` です。</span><span class="sxs-lookup"><span data-stu-id="c56d3-145">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="c56d3-146">収集したダンプを書き込む完全なパスとファイル名。</span><span class="sxs-lookup"><span data-stu-id="c56d3-146">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="c56d3-147">指定していない場合は、次になります。</span><span class="sxs-lookup"><span data-stu-id="c56d3-147">If not specified:</span></span>

  - <span data-ttu-id="c56d3-148">Windows での既定は、 *.\dump_YYYYMMDD_HHMMSS.dmp* です。</span><span class="sxs-lookup"><span data-stu-id="c56d3-148">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="c56d3-149">Linux での既定は、 *./core_YYYYMMDD_HHMMSS* です。</span><span class="sxs-lookup"><span data-stu-id="c56d3-149">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="c56d3-150">YYYYMMDD は、年/月/日で、HHMMSS は時間/分/秒です。</span><span class="sxs-lookup"><span data-stu-id="c56d3-150">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="c56d3-151">ダンプの収集の診断ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c56d3-151">Enables dump collection diagnostic logging.</span></span>

> [!NOTE]
> <span data-ttu-id="c56d3-152">Linux と macOS 上でこのコマンドを使用するには、ターゲット アプリケーションと `dotnet-dump` で同じ `TMPDIR` 環境変数が共有されることが前提とされています。</span><span class="sxs-lookup"><span data-stu-id="c56d3-152">On Linux and macOS, this command expects the target application and `dotnet-dump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="c56d3-153">それ以外の場合、このコマンドはタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="c56d3-153">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="c56d3-154">`dotnet-dump` を使用してダンプを収集するには、ターゲット プロセスを実行しているユーザーと同じユーザーとして、またはルートとしてそれを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d3-154">To collect a dump using `dotnet-dump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="c56d3-155">それ以外の場合、このツールでターゲット プロセスとの接続を確立することはできません。</span><span class="sxs-lookup"><span data-stu-id="c56d3-155">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="c56d3-156">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="c56d3-156">dotnet-dump analyze</span></span>

<span data-ttu-id="c56d3-157">ダンプを検索する対話型シェルを開始します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-157">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="c56d3-158">このシェルでは、さまざまな [SOS コマンド](#analyze-sos-commands)を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c56d3-158">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="c56d3-159">構文</span><span class="sxs-lookup"><span data-stu-id="c56d3-159">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="c56d3-160">引数</span><span class="sxs-lookup"><span data-stu-id="c56d3-160">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="c56d3-161">分析のためにファイルをダンプするパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-161">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="c56d3-162">オプション</span><span class="sxs-lookup"><span data-stu-id="c56d3-162">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="c56d3-163">起動時にシェルで実行する[コマンド](#analyze-sos-commands)を指定します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-163">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="c56d3-164">SOS コマンドを分析する</span><span class="sxs-lookup"><span data-stu-id="c56d3-164">Analyze SOS commands</span></span>

| <span data-ttu-id="c56d3-165">コマンド</span><span class="sxs-lookup"><span data-stu-id="c56d3-165">Command</span></span>                             | <span data-ttu-id="c56d3-166">関数</span><span class="sxs-lookup"><span data-stu-id="c56d3-166">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="c56d3-167">使用可能なコマンドをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-167">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="c56d3-168">指定したコマンドを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-168">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="c56d3-169">対話モードを終了します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-169">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="c56d3-170">マネージド コードのみのスタック トレースを提供します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-170">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="c56d3-171">実行中のマネージド スレッドを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-171">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="c56d3-172">ガベージ コレクトされたヒープ上の非同期状態のマシンに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-172">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="c56d3-173">指定されたアドレスにあるアセンブリに関する詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-173">Displays details about the assembly at the specified address.</span></span>                                 |
| `dumpclass <arguments>`             | <span data-ttu-id="c56d3-174">指定されたアドレスにある `EEClass` 構造体に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-174">Displays information about the `EEClass` structure at the specified address.</span></span>                  |
| `dumpdelegate <arguments>`          | <span data-ttu-id="c56d3-175">指定されたアドレスにあるデリゲートに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-175">Displays information about the delegate at the specified address.</span></span>                             |
| `dumpdomain <arguments>`            | <span data-ttu-id="c56d3-176">すべての AppDomain と、指定されたドメイン内のすべてのアセンブリに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-176">Displays information all the AppDomains and all assemblies within the specified domain.</span></span>       |
| `dumpheap <arguments>`              | <span data-ttu-id="c56d3-177">ガベージ コレクトされたヒープと、オブジェクトの収集統計に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-177">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="c56d3-178">マネージド メソッドに関連付けられている Microsoft Intermediate Language (MSIL) を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-178">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="c56d3-179">メモリ内ストレス ログの内容を、指定したファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="c56d3-179">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="c56d3-180">指定されたアドレスにある `MethodDesc` 構造体に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-180">Displays information about the `MethodDesc` structure at the specified address.</span></span>               |
| `dumpmodule <arguments>`            | <span data-ttu-id="c56d3-181">指定されたアドレスにあるモジュールに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-181">Displays information about the module at the specified address.</span></span>                               |
| `dumpmt <arguments>`                | <span data-ttu-id="c56d3-182">指定されたアドレスにある `MethodTable` に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-182">Displays information about the `MethodTable` at the specified address.</span></span>                        |
| `dumpobj <arguments>`               | <span data-ttu-id="c56d3-183">指定したアドレスにあるオブジェクトに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-183">Displays info about the object at the specified address.</span></span>                                      |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="c56d3-184">現在のスタックの範囲内で見つかったすべてのマネージド オブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-184">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="c56d3-185">内部のランタイム データ構造体によって消費されたプロセス メモリに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-185">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="c56d3-186">完了の目的で登録されているすべてのオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-186">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="c56d3-187">指定されたアドレスにあるオブジェクトへの参照 (またはルート) に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-187">Displays info about references (or roots) to the object at the specified address.</span></span>             |
| `gcwhere <arguments>`               | <span data-ttu-id="c56d3-188">渡された引数の GC ヒープ内の場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-188">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="c56d3-189">指定したアドレスにある JIT コード内の `MethodDesc` 構造体に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-189">Displays the `MethodDesc` structure at the specified address in JIT code.</span></span>                     |
| `histclear <arguments>`             | <span data-ttu-id="c56d3-190">`hist*` コマンドのファミリによって使用されているすべてのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-190">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="c56d3-191">デバッグ対象に保存されているストレス ログから SOS 構造体を初期化します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-191">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="c56d3-192">`<arguments>` に関連するガベージ コレクションのストレス ログの再配置を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-192">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="c56d3-193">指定されたアドレスにあるオブジェクトを参照するすべてのログ エントリを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-193">Displays all the log entries that reference the object at the specified address.</span></span>              |
| `histroot <arguments>`              | <span data-ttu-id="c56d3-194">指定したルートの上位変換と再配置の両方に関係する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-194">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="c56d3-195">プロセス内のネイティブ モジュールを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-195">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="c56d3-196">`<argument>` の `MethodTable` 構造体と `EEClass` 構造体を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-196">Displays the `MethodTable` and `EEClass` structures for the `<argument>`.</span></span>                     |
| `pe|printexception <arguments>`     | <span data-ttu-id="c56d3-197">`<argument>` の <xref:System.Exception> クラスから派生したオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-197">Displays any object derived from the <xref:System.Exception> class for the `<argument>`.</span></span>      |
| `setsymbolserver <arguments>`       | <span data-ttu-id="c56d3-198">シンボル サーバーのサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c56d3-198">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="c56d3-199">SyncBlock の所有者の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-199">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="c56d3-200">SOS コマンドの現在のスレッド ID を設定するか表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-200">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

> [!NOTE]
> <span data-ttu-id="c56d3-201">その他の詳細は、「[.NET 用 SOS デバッガー拡張](sos-debugging-extension.md)」に記載されています。</span><span class="sxs-lookup"><span data-stu-id="c56d3-201">Additional details can be found in [SOS Debugging Extension for .NET](sos-debugging-extension.md).</span></span>

## <a name="using-dotnet-dump"></a><span data-ttu-id="c56d3-202">`dotnet-dump` を使用する</span><span class="sxs-lookup"><span data-stu-id="c56d3-202">Using `dotnet-dump`</span></span>

<span data-ttu-id="c56d3-203">まずはダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-203">The first step is to collect a dump.</span></span> <span data-ttu-id="c56d3-204">コア ダンプを既に生成している場合、この手順をスキップできます。</span><span class="sxs-lookup"><span data-stu-id="c56d3-204">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="c56d3-205">コア ダンプは、オペレーティング システムまたは .NET Core ランタイムに組み込まれているそれぞれの[ダンプ生成機能](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md)で作成できます。</span><span class="sxs-lookup"><span data-stu-id="c56d3-205">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="c56d3-206">ここで、次のように `analyze` コマンドを使用して、コア ダンプを分析します。</span><span class="sxs-lookup"><span data-stu-id="c56d3-206">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="c56d3-207">この操作により、次のようなコマンドを受け取る対話型セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="c56d3-207">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="c56d3-208">アプリを強制終了させた未処理の例外を表示するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c56d3-208">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="c56d3-209">Docker 用の特別な手順</span><span class="sxs-lookup"><span data-stu-id="c56d3-209">Special instructions for Docker</span></span>

<span data-ttu-id="c56d3-210">ダンプの収集を Docker で実行している場合、`SYS_PTRACE` 機能 (`--cap-add=SYS_PTRACE` または `--privileged`) が必要です。</span><span class="sxs-lookup"><span data-stu-id="c56d3-210">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="c56d3-211">Microsoft .NET Core SDK Linux Docker イメージでは、一部の `dotnet-dump` コマンドで次の例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c56d3-211">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="c56d3-212">未処理の例外:System.DllNotFoundException:共有ライブラリ 'libdl.so' またはその依存関係の 1 つを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="c56d3-212">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="c56d3-213">"libc6-dev" パッケージをインストールすると、この問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="c56d3-213">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="c56d3-214">関連項目</span><span class="sxs-lookup"><span data-stu-id="c56d3-214">See also</span></span>

- [<span data-ttu-id="c56d3-215">メモリ ダンプの収集と分析に関するブログ</span><span class="sxs-lookup"><span data-stu-id="c56d3-215">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="c56d3-216">ヒープ分析ツール (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="c56d3-216">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
