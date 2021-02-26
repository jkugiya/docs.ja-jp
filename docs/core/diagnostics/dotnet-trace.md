---
title: dotnet-trace 診断ツール - .NET CLI
description: dotnet-trace CLI ツールをインストールして使用し、.NET EventPipe を使って、ネイティブ プロファイラーなしで実行中のプロセスの .NET トレースを収集する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: abf98df6e31747ea3e8013fc77b246613a3402ad
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583010"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="9bb81-103">dotnet-trace パフォーマンス分析ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="9bb81-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="9bb81-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="9bb81-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="9bb81-105">インストール</span><span class="sxs-lookup"><span data-stu-id="9bb81-105">Install</span></span>

<span data-ttu-id="9bb81-106">`dotnet-trace` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="9bb81-107">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="9bb81-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="9bb81-108">`dotnet-trace` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-trace)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="9bb81-109">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="9bb81-109">**Direct download:**</span></span>

  <span data-ttu-id="9bb81-110">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9bb81-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="9bb81-111">OS</span><span class="sxs-lookup"><span data-stu-id="9bb81-111">OS</span></span>  | <span data-ttu-id="9bb81-112">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="9bb81-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="9bb81-113">Windows</span><span class="sxs-lookup"><span data-stu-id="9bb81-113">Windows</span></span> | <span data-ttu-id="9bb81-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="9bb81-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="9bb81-115">macOS</span><span class="sxs-lookup"><span data-stu-id="9bb81-115">macOS</span></span>   | [<span data-ttu-id="9bb81-116">x64</span><span class="sxs-lookup"><span data-stu-id="9bb81-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="9bb81-117">Linux</span><span class="sxs-lookup"><span data-stu-id="9bb81-117">Linux</span></span>   | <span data-ttu-id="9bb81-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="9bb81-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="9bb81-119">x86 アプリ上で `dotnet-trace` を使用するには、対応する x86 バージョンのツールが必要です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-119">To use `dotnet-trace` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9bb81-120">構文</span><span class="sxs-lookup"><span data-stu-id="9bb81-120">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="9bb81-121">説明</span><span class="sxs-lookup"><span data-stu-id="9bb81-121">Description</span></span>

<span data-ttu-id="9bb81-122">`dotnet-trace` ツール:</span><span class="sxs-lookup"><span data-stu-id="9bb81-122">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="9bb81-123">クロスプラットフォーム .NET Core ツールです。</span><span class="sxs-lookup"><span data-stu-id="9bb81-123">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="9bb81-124">ネイティブ プロファイラーなしで実行中のプロセスの .NET Core トレースを回収できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-124">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="9bb81-125">.NET Core ランタイムの [`EventPipe`](./eventpipe.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="9bb81-125">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="9bb81-126">Windows、Linux または macOS でも同じエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-126">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="9bb81-127">オプション</span><span class="sxs-lookup"><span data-stu-id="9bb81-127">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9bb81-128">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-128">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="9bb81-129">dotnet-trace ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-129">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="9bb81-130">コマンド</span><span class="sxs-lookup"><span data-stu-id="9bb81-130">Commands</span></span>

| <span data-ttu-id="9bb81-131">コマンド</span><span class="sxs-lookup"><span data-stu-id="9bb81-131">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="9bb81-132">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="9bb81-132">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="9bb81-133">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="9bb81-133">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="9bb81-134">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="9bb81-134">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="9bb81-135">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="9bb81-135">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="9bb81-136">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="9bb81-136">dotnet-trace collect</span></span>

<span data-ttu-id="9bb81-137">実行中のプロセスから診断トレースを収集します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-137">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9bb81-138">構文</span><span class="sxs-lookup"><span data-stu-id="9bb81-138">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="9bb81-139">オプション</span><span class="sxs-lookup"><span data-stu-id="9bb81-139">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="9bb81-140">メモリ内の循環バッファーのサイズをメガバイトに設定します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-140">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="9bb81-141">既定は 256 MB です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-141">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="9bb81-142">生成される CLR イベントの詳細度。</span><span class="sxs-lookup"><span data-stu-id="9bb81-142">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="9bb81-143">有効にする CLR ランタイム プロバイダーのキーワードの、`+` 記号で区切られたリスト。</span><span class="sxs-lookup"><span data-stu-id="9bb81-143">A list of CLR runtime provider keywords to enable separated by `+` signs.</span></span> <span data-ttu-id="9bb81-144">これは、16 進値ではなく文字列の別名を使用してイベント キーワードを指定できるようにする、単純なマッピングです。</span><span class="sxs-lookup"><span data-stu-id="9bb81-144">This is a simple mapping that lets you specify event keywords via string aliases rather than their hex values.</span></span> <span data-ttu-id="9bb81-145">たとえば、`dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` では、`dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational` と同じイベントのセットが要求されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-145">For example, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` requests the same set of events as `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`.</span></span> <span data-ttu-id="9bb81-146">次の表に、使用できるキーワードの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-146">The table below shows the list of available keywords:</span></span>

  | <span data-ttu-id="9bb81-147">キーワードの文字列別名</span><span class="sxs-lookup"><span data-stu-id="9bb81-147">Keyword String Alias</span></span> | <span data-ttu-id="9bb81-148">キーワードの 16 進値</span><span class="sxs-lookup"><span data-stu-id="9bb81-148">Keyword Hex Value</span></span> |
  | ------------ | ------------------- |
  | `gc` | `0x1` |
  | `gchandle` | `0x2` |
  | `fusion` | `0x4` |
  | `loader` | `0x8` |
  | `jit` | `0x10` |
  | `ngen` | `0x20` |
  | `startenumeration` | `0x40` |
  | `endenumeration` | `0x80` |
  | `security` | `0x400` |
  | `appdomainresourcemanagement` | `0x800` |
  | `jittracing` | `0x1000` |
  | `interop` | `0x2000` |
  | `contention` | `0x4000` |
  | `exception` | `0x8000` |
  | `threading` | `0x10000` |
  | `jittedmethodiltonativemap` | `0x20000` |
  | `overrideandsuppressngenevents` | `0x40000` |
  | `type` | `0x80000` |
  | `gcheapdump` | `0x100000` |
  | `gcsampledobjectallocationhigh` | `0x200000` |
  | `gcheapsurvivalandmovement` | `0x400000` |
  | `gcheapcollect` | `0x800000` |
  | `gcheapandtypenames` | `0x1000000` |
  | `gcsampledobjectallocationlow` | `0x2000000` |
  | `perftrack` | `0x20000000` |
  | `stack` | `0x40000000` |
  | `threadtransfer` | `0x80000000` |
  | `debugger` | `0x100000000` |
  | `monitoring` | `0x200000000` |
  | `codesymbols` | `0x400000000` |
  | `eventsource` | `0x800000000` |
  | `compilation` | `0x1000000000` |
  | `compilationdiagnostic` | `0x2000000000` |
  | `methoddiagnostic` | `0x4000000000` |
  | `typediagnostic` | `0x8000000000` |

  <span data-ttu-id="9bb81-149">CLR プロバイダーの詳細については、[.NET ランタイム プロバイダーのリファレンス ドキュメント](../../fundamentals/diagnostics/runtime-events.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bb81-149">You can read about the CLR provider more in detail on the [.NET runtime provider reference documentation](../../fundamentals/diagnostics/runtime-events.md).</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="9bb81-150">トレース ファイルの出力の変換形式を設定します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-150">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="9bb81-151">既定値は、`NetTrace` です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-151">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="9bb81-152">トレースを収集するプロセスの名前。</span><span class="sxs-lookup"><span data-stu-id="9bb81-152">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="9bb81-153">作成する診断ポートの名前。</span><span class="sxs-lookup"><span data-stu-id="9bb81-153">The name of the diagnostic port to create.</span></span> <span data-ttu-id="9bb81-154">このオプションを使用してアプリの起動からトレースを収集する方法については、「[診断ポートを使用してアプリの起動からトレースを収集する](#use-diagnostic-port-to-collect-a-trace-from-app-startup)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bb81-154">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="9bb81-155">収集されたトレース データの出力パス。</span><span class="sxs-lookup"><span data-stu-id="9bb81-155">The output path for the collected trace data.</span></span> <span data-ttu-id="9bb81-156">指定しない場合の既定値は `trace.nettrace` です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-156">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9bb81-157">トレースを収集するプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="9bb81-157">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="9bb81-158">共通のトレース シナリオを簡潔に指定できるようにする、事前定義されたプロバイダーの名前付き構成のセット。</span><span class="sxs-lookup"><span data-stu-id="9bb81-158">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="9bb81-159">次のプロファイルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-159">The following profiles are available:</span></span>

 | <span data-ttu-id="9bb81-160">[プロファイル]</span><span class="sxs-lookup"><span data-stu-id="9bb81-160">Profile</span></span> | <span data-ttu-id="9bb81-161">説明</span><span class="sxs-lookup"><span data-stu-id="9bb81-161">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="9bb81-162">CPU 使用率および一般的な .NET ランタイム情報の追跡に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-162">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="9bb81-163">プロファイルまたはプロバイダーが指定されていない場合は、これが既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="9bb81-163">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="9bb81-164">GC コレクションを追跡し、オブジェクトの割り当てをサンプリングします。</span><span class="sxs-lookup"><span data-stu-id="9bb81-164">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="9bb81-165">オーバーヘッドが非常に低い場合にのみ GC コレクションを追跡します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-165">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="9bb81-166">有効にする `EventPipe` プロバイダーのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="9bb81-166">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="9bb81-167">これらのプロバイダーは、`--profile <profile-name>` で示されている任意のプロバイダーを補完します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-167">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="9bb81-168">特定のプロバイダーに不整合がある場合、この構成がプロファイルの暗黙的な構成に優先されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-168">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="9bb81-169">プロバイダーの一覧の形式は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9bb81-169">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="9bb81-170">`Provider` は、`KnownProviderName[:Flags[:Level][:KeyValueArgs]]` という形式です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-170">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="9bb81-171">`KeyValueArgs` は、`[key1=value1][;key2=value2]` という形式です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-171">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

  <span data-ttu-id="9bb81-172">.NET でのいくつかの既知のプロバイダーの詳細については、[既知のイベント プロバイダー](./well-known-event-providers.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bb81-172">To learn more about some of the well-known providers in .NET, refer to [Well-known Event Providers](./well-known-event-providers.md).</span></span>

- <span data-ttu-id="9bb81-173">**`-- <command>` (.NET 5.0 のみを実行しているターゲット アプリケーションの場合)**</span><span class="sxs-lookup"><span data-stu-id="9bb81-173">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="9bb81-174">ユーザーは、コレクション構成パラメーターの後にまず `--`、次にコマンドを追加すれば、5.0 以降のランタイムで .NET アプリケーションを起動することができます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-174">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="9bb81-175">これは、起動時のパフォーマンスの問題やアセンブリ ローダーおよびバインダーのエラーなど、プロセスの早い段階で発生する問題を診断するのに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-175">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9bb81-176">このオプションを使用すると、ツールに返信する最初の .NET 5.0 プロセスが監視されます。つまり、ご利用のコマンドで複数の .NET アプリケーションが起動される場合、収集されるのは最初のアプリのみとなります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-176">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="9bb81-177">このため、このオプションについては、自己完結型アプリケーションに対して使用するか、または `dotnet exec <app.dll>` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9bb81-177">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb81-178">大きなアプリケーションの場合、トレースの停止に時間がかかることがあります (最大数分)。</span><span class="sxs-lookup"><span data-stu-id="9bb81-178">Stopping the trace may take a long time (up to minutes) for large applications.</span></span> <span data-ttu-id="9bb81-179">ランタイムでは、トレースにキャプチャされたすべてのマネージド コードを対象に、型キャッシュを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-179">The runtime needs to send over the type cache for all managed code that was captured in the trace.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb81-180">Linux と macOS 上でこのコマンドを使用するには、ターゲット アプリケーションと `dotnet-trace` で同じ `TMPDIR` 環境変数が共有されることが前提とされています。</span><span class="sxs-lookup"><span data-stu-id="9bb81-180">On Linux and macOS, this command expects the target application and `dotnet-trace` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="9bb81-181">それ以外の場合、このコマンドはタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="9bb81-181">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb81-182">`dotnet-trace` を使用してトレースを収集するには、ターゲット プロセスを実行しているユーザーと同じユーザーとして、またはルートとしてそれを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-182">To collect a trace using `dotnet-trace`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="9bb81-183">それ以外の場合、このツールでターゲット プロセスとの接続を確立することはできません。</span><span class="sxs-lookup"><span data-stu-id="9bb81-183">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb81-184">`[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.` のようなエラー メッセージが表示される場合は、ターゲット プロセスとビットが一致しない `dotnet-trace` を使用しようとしています。</span><span class="sxs-lookup"><span data-stu-id="9bb81-184">If you see an error message similar to the following one: `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, you are trying to use `dotnet-trace` that has mismatched bitness against the target process.</span></span> <span data-ttu-id="9bb81-185">「[インストール](#install)」のリンクで、正しいビットのツールをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9bb81-185">Make sure to download the correct bitness of the tool in the [install](#install) link.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="9bb81-186">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="9bb81-186">dotnet-trace convert</span></span>

<span data-ttu-id="9bb81-187">`nettrace` トレースを、別のトレース分析ツールで使用するために、別の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-187">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9bb81-188">構文</span><span class="sxs-lookup"><span data-stu-id="9bb81-188">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="9bb81-189">引数</span><span class="sxs-lookup"><span data-stu-id="9bb81-189">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="9bb81-190">変換する入力トレース ファイル。</span><span class="sxs-lookup"><span data-stu-id="9bb81-190">Input trace file to be converted.</span></span> <span data-ttu-id="9bb81-191">既定は *trace.nettrace* です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-191">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="9bb81-192">オプション</span><span class="sxs-lookup"><span data-stu-id="9bb81-192">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="9bb81-193">トレース ファイルの出力の変換形式を設定します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-193">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="9bb81-194">出力ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="9bb81-194">Output filename.</span></span> <span data-ttu-id="9bb81-195">ターゲットの形式の拡張子が追加されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-195">Extension of target format will be added.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb81-196">`nettrace` ファイルを `chromium` または `speedscope` ファイルに変換した場合、元に戻せません。</span><span class="sxs-lookup"><span data-stu-id="9bb81-196">Converting `nettrace` files to `chromium` or `speedscope` files is irreversible.</span></span> <span data-ttu-id="9bb81-197">`speedscope` ファイルと `chromium` ファイルには、`nettrace` ファイルを再構築するために必要な情報が一部含まれていません。</span><span class="sxs-lookup"><span data-stu-id="9bb81-197">`speedscope` and `chromium` files don't have all the information necessary to reconstruct `nettrace` files.</span></span> <span data-ttu-id="9bb81-198">ただし、`convert` コマンドによって元の `nettrace` ファイルが保持されます。今後開くことがある場合、このファイルは削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="9bb81-198">However, the `convert` command preserves the original `nettrace` file, so don't delete this file if you plan to open it in the future.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="9bb81-199">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="9bb81-199">dotnet-trace ps</span></span>

 <span data-ttu-id="9bb81-200">トレースを収集できる dotnet プロセスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-200">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9bb81-201">構文</span><span class="sxs-lookup"><span data-stu-id="9bb81-201">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="9bb81-202">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="9bb81-202">dotnet-trace list-profiles</span></span>

<span data-ttu-id="9bb81-203">各プロファイルに含まれるプロバイダーとフィルターの記述と共に、事前に構築されているトレースのプロファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-203">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9bb81-204">構文</span><span class="sxs-lookup"><span data-stu-id="9bb81-204">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="9bb81-205">dotnet-trace を使用してトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="9bb81-205">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="9bb81-206">`dotnet-trace` を使用してトレースを収集するには:</span><span class="sxs-lookup"><span data-stu-id="9bb81-206">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="9bb81-207">トレースを収集する .NET Core アプリケーションのプロセス識別子 (PID) を取得します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-207">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="9bb81-208">Windows で、タスク マネージャーや、たとえば、`tasklist` コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-208">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="9bb81-209">Linux の場合、たとえば、`ps` コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-209">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="9bb81-210">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="9bb81-210">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="9bb81-211">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-211">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="9bb81-212">上のコマンドを実行すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-212">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="9bb81-213">`<Enter>` キーを押すと、コレクションが停止します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-213">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="9bb81-214">`dotnet-trace` では、*trace.nettrace* ファイルにイベントをログ記録する作業が完了します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-214">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="9bb81-215">子アプリケーションを起動し、そのスタートアップからトレースを dotnet-trace を使用して収集します</span><span class="sxs-lookup"><span data-stu-id="9bb81-215">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9bb81-216">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-216">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="9bb81-217">場合によっては、プロセスのトレースをそのスタートアップから収集すると便利なことがあります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-217">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="9bb81-218">.NET 5.0 以降を実行しているアプリでは、dotnet-trace を使用してこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-218">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="9bb81-219">これを使用すると、コマンドライン引数として `arg1` と `arg2` を含む `hello.exe` が起動され、そのランタイム スタートアップからトレースが収集されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-219">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="9bb81-220">上のコマンドを実行すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-220">The preceding command generates output similar to the following:</span></span>

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

<span data-ttu-id="9bb81-221">トレースの収集を停止するには、`<Enter>` または `<Ctrl + C>` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-221">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="9bb81-222">この操作を行うと、`hello.exe` も終了します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-222">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb81-223">dotnet-trace を介して `hello.exe` を起動すると、その入力/出力がリダイレクトされ、その stdin/stdout とやりとりができなくなります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-223">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="9bb81-224">CTRL + C または SIGTERM を介してツールを終了すると、ツールと子プロセスの両方が安全に終了します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-224">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="9bb81-225">ツールの前に子プロセスが終了すると、ツールも終了し、トレースを安全に表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-225">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="9bb81-226">診断ポートを使用してアプリの起動からトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="9bb81-226">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9bb81-227">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-227">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="9bb81-228">診断ポートは、.NET 5 で追加された新しいランタイム機能で、アプリの起動からトレースを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-228">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="9bb81-229">`dotnet-trace` を使用してこれを行うには、上記の例の説明に従って `dotnet-trace collect -- <command>` を使用するか、`--diagnostic-port` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-229">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="9bb81-230">起動からすばやくトレースする方法としては、アプリケーションを子プロセスとして起動するために `dotnet-trace <collect|monitor> -- <command>` を使用するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-230">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="9bb81-231">ただし、(アプリを最初の 10 分だけ監視し、実行を継続するなど) トレースしているアプリの有効期間をより細かく制御する場合、または CLI を使用してアプリと対話する必要がある場合は、`--diagnostic-port` オプションを使用すると、監視対象アプリと `dotnet-trace` の両方を制御できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-231">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="9bb81-232">次のコマンドにより、`dotnet-trace` で `myport.sock` という名前の診断ソケットを作成し、接続を待機します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-232">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="9bb81-233">出力:</span><span class="sxs-lookup"><span data-stu-id="9bb81-233">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="9bb81-234">別のコンソールで、`dotnet-trace` の出力値に設定された環境変数 `DOTNET_DiagnosticPorts` を使用して対象アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-234">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="9bb81-235">これにより、`dotnet-trace` による `my-dotnet-app` のトレースが開始します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-235">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="9bb81-236">`dotnet run` を使用してアプリを起動すると、dotnet CLI によってお使いのアプリのものではない子プロセスが多数生成され、お使いのアプリよりも先にそれらが `dotnet-trace` に接続されてしまい、実行時にお使いのアプリが中断されることで、問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-236">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="9bb81-237">アプリケーションの起動には、アプリの自己完結型バージョンを直接使用するか、`dotnet exec` を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9bb81-237">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="9bb81-238">dotnet-trace からキャプチャされたトレースを表示する</span><span class="sxs-lookup"><span data-stu-id="9bb81-238">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="9bb81-239">Windows の場合、 *.nettrace* ファイルを [PerfView](https://github.com/microsoft/perfview) で表示し、分析できます。他のプラットフォームで収集されたトレースについては、トレース ファイルを Windows コンピューターに移動し、PerfView で表示できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-239">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="9bb81-240">Linux の場合、`dotnet-trace` の出力形式を `speedscope` に変更することでトレースを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-240">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="9bb81-241">出力ファイル形式は `-f|--format` オプションで変更できます。`-f speedscope` により、`dotnet-trace` で `speedscope` ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-241">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="9bb81-242">`nettrace` (既定のオプション) か `speedscope` を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-242">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="9bb81-243">`Speedscope` ファイルは <https://www.speedscope.app> で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-243">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb81-244">.NET Core ランタイムにより、`nettrace` 形式でトレースが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-244">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="9bb81-245">トレースの完了後、トレースは speedscope に変換されます (指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="9bb81-245">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="9bb81-246">変換によってはデータが失われる場合もあるため、元の `nettrace` ファイルが変換されたファイルの横に保持されます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-246">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="9bb81-247">dotnet-trace を使用して経時的なカウンター値を収集する</span><span class="sxs-lookup"><span data-stu-id="9bb81-247">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="9bb81-248">`dotnet-trace` でできること:</span><span class="sxs-lookup"><span data-stu-id="9bb81-248">`dotnet-trace` can:</span></span>

* <span data-ttu-id="9bb81-249">パフォーマンスで左右される環境で基本的な正常性監視を行うには `EventCounter` を使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-249">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="9bb81-250">たとえば、運用環境です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-250">For example, in production.</span></span>
* <span data-ttu-id="9bb81-251">リアルタイムで表示する必要がないようにトレースを収集します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-251">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="9bb81-252">たとえば、実行時のパフォーマンス カウンター値を収集するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-252">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="9bb81-253">先のコマンドでは、正常性の簡易監視を 1 秒ごとに報告するようにランタイム カウンターに命令します。</span><span class="sxs-lookup"><span data-stu-id="9bb81-253">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="9bb81-254">`EventCounterIntervalSec=1` の値を (60 など) 大きい値に置き換えた場合、カウンター データの細分性の詳細度がより低いトレースをより少数収集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-254">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="9bb81-255">次のコマンドでは、先のコマンドよりオーバーヘッドとトレース サイズが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-255">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="9bb81-256">上のコマンドでは、ランタイム イベントとマネージド スタック プロファイラーが無効になります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-256">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a><span data-ttu-id="9bb81-257">.rsp ファイルを使用し、長いコマンドの入力を避ける</span><span class="sxs-lookup"><span data-stu-id="9bb81-257">Use .rsp file to avoid typing long commands</span></span>

<span data-ttu-id="9bb81-258">渡す引数が含まれる `.rsp` ファイルで `dotnet-trace` を起動できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-258">You can launch `dotnet-trace` with an `.rsp` file that contains the arguments to pass.</span></span> <span data-ttu-id="9bb81-259">これは、文字を取り除くシェル環境を使用しているとき、長い引数を求めるプロバイダーを有効にするときに便利です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-259">This can be useful when enabling providers that expect lengthy arguments or when using a shell environment that strips characters.</span></span>

<span data-ttu-id="9bb81-260">たとえば、次のプロバイダーの場合、トレースのたびに入力するのが面倒です。</span><span class="sxs-lookup"><span data-stu-id="9bb81-260">For example, the following provider can be cumbersome to type out each time you want to trace:</span></span>

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="9bb81-261">また、前の例には、引数の一部として `"` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9bb81-261">In addition, the previous example contains `"` as part of the argument.</span></span> <span data-ttu-id="9bb81-262">引用符の処理がシェルごとに異なるため、異なるシェルを使用するとき、さまざまな問題が発生するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-262">Because quotes are not handled equally by each shell, you may experience various issues when using different shells.</span></span> <span data-ttu-id="9bb81-263">たとえば、`zsh` に入力するコマンドは、`cmd` のコマンドとは異なります。</span><span class="sxs-lookup"><span data-stu-id="9bb81-263">For example, the command to enter in `zsh` is different to the command in `cmd`.</span></span>

<span data-ttu-id="9bb81-264">これを毎回入力する代わりに、`myprofile.rsp` という名称のファイルに次のテキストを保存できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-264">Instead of typing this each time, you can save the following text into a file called `myprofile.rsp`.</span></span>

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="9bb81-265">`myprofile.rsp` を保存したら、次のコマンドを使用し、この構成で `dotnet-trace` を起動できます。</span><span class="sxs-lookup"><span data-stu-id="9bb81-265">Once you've saved `myprofile.rsp`, you can launch `dotnet-trace` with this configuration using the following command:</span></span>

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a><span data-ttu-id="9bb81-266">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bb81-266">See also</span></span>

- [<span data-ttu-id="9bb81-267">.NET の既知のイベント プロバイダー</span><span class="sxs-lookup"><span data-stu-id="9bb81-267">Well-known event providers from .NET</span></span>](well-known-event-providers.md)
