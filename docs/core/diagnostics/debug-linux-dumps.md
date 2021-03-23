---
title: Linux ダンプのデバッグ
description: この記事では、Linux 環境からダンプを収集して分析する方法について学習します。
ms.date: 08/27/2020
ms.openlocfilehash: 42038c685c3ad0043c91df140b0133a9ddecec3b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874272"
---
# <a name="debug-linux-dumps"></a><span data-ttu-id="1ac66-103">Linux ダンプのデバッグ</span><span class="sxs-lookup"><span data-stu-id="1ac66-103">Debug Linux dumps</span></span>

<span data-ttu-id="1ac66-104">**この記事の対象: ✔️** .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="1ac66-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

## <a name="collect-dumps-on-linux"></a><span data-ttu-id="1ac66-105">Linux でダンプを収集する</span><span class="sxs-lookup"><span data-stu-id="1ac66-105">Collect dumps on Linux</span></span>

<span data-ttu-id="1ac66-106">Linux でダンプを収集するための推奨される 2 つの方法:</span><span class="sxs-lookup"><span data-stu-id="1ac66-106">The two recommended ways of collecting dumps on Linux are:</span></span>

* <span data-ttu-id="1ac66-107">[`dotnet-dump`](dotnet-dump.md) CLI ツール</span><span class="sxs-lookup"><span data-stu-id="1ac66-107">[`dotnet-dump`](dotnet-dump.md) CLI tool</span></span>
* <span data-ttu-id="1ac66-108">クラッシュ時にダンプを収集する[環境変数](dumps.md#collecting-dumps-on-crash)</span><span class="sxs-lookup"><span data-stu-id="1ac66-108">[Environment variables](dumps.md#collecting-dumps-on-crash) that collect dumps on crashes</span></span>

### <a name="managed-dumps-with-dotnet-dump"></a><span data-ttu-id="1ac66-109">`dotnet-dump` を使用するマネージド ダンプ</span><span class="sxs-lookup"><span data-stu-id="1ac66-109">Managed dumps with `dotnet-dump`</span></span>

<span data-ttu-id="1ac66-110">[`dotnet-dump`](dotnet-dump.md) ツールは使いやすく、ネイティブ デバッガーとの依存関係はありません。</span><span class="sxs-lookup"><span data-stu-id="1ac66-110">The [`dotnet-dump`](dotnet-dump.md) tool is simple to use, and does not have a dependency on any native debuggers.</span></span> <span data-ttu-id="1ac66-111">`dotnet-dump` は、従来のデバッグ ツールを使用できない場合があるさまざまな Linux プラットフォーム (Alpine や ARM32 または ARM64 など) で動作します。</span><span class="sxs-lookup"><span data-stu-id="1ac66-111">`dotnet-dump` works on a wide variety of Linux platforms (like Alpine or ARM32/ARM64) where traditional debugging tools may not be available.</span></span> <span data-ttu-id="1ac66-112">しかし、`dotnet-dump` によって、マネージド状態のみがキャプチャされるため、ネイティブ コードでの問題のデバッグには使用できません。</span><span class="sxs-lookup"><span data-stu-id="1ac66-112">However, `dotnet-dump` only captures managed state so it can't be used for debugging issues in native code.</span></span> <span data-ttu-id="1ac66-113">`dotnet-dump` によって収集されるダンプは、ダンプが作成されたのと同じ OS とアーキテクチャがある環境で分析されます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-113">Dumps collected by `dotnet-dump` are analyzed in an environment with the same OS and architecture the dump was created on.</span></span> <span data-ttu-id="1ac66-114">[`dotnet-gcdump`](dotnet-gcdump.md) ツールは、キャプチャされるのが GC ヒープ情報のみではあるものの、Windows で分析できるダンプを生成する代替手段として使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-114">The [`dotnet-gcdump`](dotnet-gcdump.md) tool can be used as an alternative that only captures GC heap information but produces dumps that can be analyzed on Windows.</span></span>

### <a name="core-dumps-with-createdump"></a><span data-ttu-id="1ac66-115">`createdump` を使用するコア ダンプ</span><span class="sxs-lookup"><span data-stu-id="1ac66-115">Core dumps with `createdump`</span></span>

<span data-ttu-id="1ac66-116">マネージドのみのダンプを作成する `dotnet-dump` の代替手段として、[`createdump`](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md) は、ネイティブとマネージドの両方の情報を含む Linux のコア ダンプを作成するための推奨ツールです。</span><span class="sxs-lookup"><span data-stu-id="1ac66-116">As an alternative to `dotnet-dump`, which creates managed-only dumps, [`createdump`](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md) is the recommended tool for creating core dumps on Linux containing both native and managed information.</span></span> <span data-ttu-id="1ac66-117">gdb や gcore などの他のツールを使用して、コア ダンプを作成することもできますが、マネージド デバッグに必要な状態を見逃してしまう可能性があり、その結果、分析中に "不明な" 種類または関数名が検出されることになります。</span><span class="sxs-lookup"><span data-stu-id="1ac66-117">Other tools like gdb or gcore can also be used to create core dumps but may miss state needed for managed debugging, resulting in "UNKNOWN" type or function names during analysis.</span></span>

<span data-ttu-id="1ac66-118">`createdump` ツールは .NET Core ランタイムと共にインストールされ、libcoreclr.so の隣にあります(通常は、"/usr/share/dotnet/shared/Microsoft.NETCore.App/[バージョン]" 内)。</span><span class="sxs-lookup"><span data-stu-id="1ac66-118">The `createdump` tool is installed with the .NET Core runtime and can be found next to libcoreclr.so (typically in "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]").</span></span> <span data-ttu-id="1ac66-119">このツールにより、そのプライマリ引数としてダンプを収集するプロセス ID が受け取られ、収集するダンプの種類 (既定値はヒープ付きのミニダンプ) を指定する省略可能なパラメーターも受け取られます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-119">The tool takes a process ID to collect a dump from as its primary argument and can also take optional parameters specifying what kind of dump to collect (a minidump with heap is the default).</span></span> <span data-ttu-id="1ac66-120">次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1ac66-120">Options include:</span></span>

- **`<input-filename>`**

  <span data-ttu-id="1ac66-121">変換する入力トレース ファイル。</span><span class="sxs-lookup"><span data-stu-id="1ac66-121">Input trace file to be converted.</span></span> <span data-ttu-id="1ac66-122">既定は *trace.nettrace* です。</span><span class="sxs-lookup"><span data-stu-id="1ac66-122">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="1ac66-123">オプション</span><span class="sxs-lookup"><span data-stu-id="1ac66-123">Options</span></span>

- **`-f|--name <output-filename>`**

  <span data-ttu-id="1ac66-124">ダンプの書き込み先のファイル。</span><span class="sxs-lookup"><span data-stu-id="1ac66-124">The file to write the dump to.</span></span> <span data-ttu-id="1ac66-125">既定値は '/tmp/coredump.%p' です。ここで、%p はターゲットプ ロセスのプロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="1ac66-125">Default is '/tmp/coredump.%p' where %p is the process ID of the target process.</span></span>

- **`-n|--normal`**

  <span data-ttu-id="1ac66-126">ミニダンプを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ac66-126">Create a minidump.</span></span>

- **`-h|--withheap`**

  <span data-ttu-id="1ac66-127">ヒープ付きミニダンプを作成します (既定値)。</span><span class="sxs-lookup"><span data-stu-id="1ac66-127">Create a minidump with heap (default).</span></span>

- **`-t|--triage`**

  <span data-ttu-id="1ac66-128">トリアージ ミニダンプを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ac66-128">Create a triage minidump.</span></span>

- **`-u|--full`**

  <span data-ttu-id="1ac66-129">完全なコア ダンプを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ac66-129">Create a full core dump.</span></span>

- **`-d|--diag`**

  <span data-ttu-id="1ac66-130">診断メッセージを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1ac66-130">Enable diagnostic messages.</span></span>

<span data-ttu-id="1ac66-131">コア ダンプを収集するには、`SYS_PTRACE` 機能を使用するか、sudo または su で `createdump` を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ac66-131">Collecting core dumps requires either the `SYS_PTRACE` capability or that `createdump` be run with sudo or su.</span></span>

## <a name="analyze-dumps-on-linux"></a><span data-ttu-id="1ac66-132">Linux でダンプを分析する</span><span class="sxs-lookup"><span data-stu-id="1ac66-132">Analyze dumps on Linux</span></span>

<span data-ttu-id="1ac66-133">`dotnet-dump` で収集されるマネージド ダンプと `createdump` で収集されるコア ダンプは両方とも、`dotnet-dump` ツールで `dotnet-dump analyze` コマンドを使用して分析することができます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-133">Both managed dumps collected with `dotnet-dump` and core dumps collected with `createdump` can be analyzed with the `dotnet-dump` tool using the `dotnet-dump analyze` command.</span></span> <span data-ttu-id="1ac66-134">`dotnet dump` には、ダンプを分析する環境に、ダンプがキャプチャされた環境と同じ OS とアーキテクチャが必要とされます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-134">The `dotnet dump` requires that the environment analyzing the dump has the same OS and architecture as the environment the dump was captured in.</span></span>

<span data-ttu-id="1ac66-135">[LLDB](https://lldb.llvm.org/) を使用して、Linux でコア ダンプを分析することもできます。これにより、マネージドとネイティブの両方のフレームを分析できます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-135">Alternatively, [LLDB](https://lldb.llvm.org/) can be used to analyze core dumps on Linux, which allows analysis of both managed and native frames.</span></span> <span data-ttu-id="1ac66-136">LLDB によって SOS 拡張機能が使用され、マネージド コードがデバッグされます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-136">LLDB uses the SOS extension to debug managed code.</span></span> <span data-ttu-id="1ac66-137">[`dotnet-sos`](dotnet-sos.md) CLI ツールを使用すると、マネージド コードをデバッグするための[多くの便利なコマンド](https://github.com/dotnet/diagnostics/blob/main/documentation/sos-debugging-extension.md)がある SOS をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-137">The [`dotnet-sos`](dotnet-sos.md) CLI tool can be used to install SOS, which has [many useful commands](https://github.com/dotnet/diagnostics/blob/main/documentation/sos-debugging-extension.md) for debugging managed code.</span></span> <span data-ttu-id="1ac66-138">.NET Core ダンプを分析するために、LLDB と SOS には、ダンプが作成された環境の次の .NET Core バイナリが必要です。</span><span class="sxs-lookup"><span data-stu-id="1ac66-138">In order to analyze .NET Core dumps, LLDB and SOS require the following .NET Core binaries from the environment the dump was created in:</span></span>

1. <span data-ttu-id="1ac66-139">libmscordaccore.so</span><span class="sxs-lookup"><span data-stu-id="1ac66-139">libmscordaccore.so</span></span>
2. <span data-ttu-id="1ac66-140">libcoreclr.so</span><span class="sxs-lookup"><span data-stu-id="1ac66-140">libcoreclr.so</span></span>
3. <span data-ttu-id="1ac66-141">dotnet (アプリを起動するために使用されるホスト)</span><span class="sxs-lookup"><span data-stu-id="1ac66-141">dotnet (the host used to launch the app)</span></span>

<span data-ttu-id="1ac66-142">ほとんどの場合、これらのバイナリは、[`dotnet-symbol`](dotnet-symbol.md) ツールを使用してダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-142">In most cases, these binaries can be downloaded using the [`dotnet-symbol`](dotnet-symbol.md) tool.</span></span> <span data-ttu-id="1ac66-143">必要なバイナリを `dotnet-symbol` と共にダウンロードできない場合 (たとえば、ソースから構築された .NET Core のプライベート バージョンが使用中だった場合)、ダンプが作成された環境から、上に一覧表示されているファイルをコピーする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="1ac66-143">If the necessary binaries can't be downloaded with `dotnet-symbol` (for example, if a private version of .NET Core built from source was in use), it may be necessary to copy the files listed above from the environment the dump was created in.</span></span> <span data-ttu-id="1ac66-144">ファイルがダンプ ファイルの横にない場合は、LLDB または SOS コマンドの `setclrpath <path>` を使用して、読み込み元のパスを設定し、`setsymbolserver -directory <path>` を使用して、シンボル ファイルの参照先のパスを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-144">If the files aren't located next to the dump file, you can use the LLDB/SOS command `setclrpath <path>` to set the path they should be loaded from and `setsymbolserver -directory <path>` to set the path to look in for symbol files.</span></span>

<span data-ttu-id="1ac66-145">必要なファイルが使用できるようになったら、デバッグする実行可能ファイルとして dotnet ホストを指定し、LLDB にダンプを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-145">Once the necessary files are available, the dump can be loaded in LLDB by specifying the dotnet host as the executable to debug:</span></span>

```console
lldb --core <dump-file> <host-program>
```

<span data-ttu-id="1ac66-146">上記のコマンド ラインでは、`<dump-file>` は分析するダンプのパスであり、`<host-program>` は .NET Core アプリケーションを起動したネイティブ プログラムです。</span><span class="sxs-lookup"><span data-stu-id="1ac66-146">In the above command line, `<dump-file>` is the path of the dump to analyze and `<host-program>` is the native program that started the .NET Core application.</span></span> <span data-ttu-id="1ac66-147">アプリが自己完結型である場合を除き、これは通常、`dotnet` バイナリです。この場合、dll 拡張子のないアプリケーションの名前になります。</span><span class="sxs-lookup"><span data-stu-id="1ac66-147">This is typically the `dotnet` binary unless the app is self-contained, in which case it is the name of the application without the dll extension.</span></span>

<span data-ttu-id="1ac66-148">LLDB が起動したら、`setsymbolserver` コマンドを使用して、正しいシンボルの場所をポイントする必要がある場合があります (Microsoft のシンボル サーバーを使用する場合は `setsymbolserver -ms`、ローカル パスを指定する場合は `setsymbolserver -directory <path>`)。</span><span class="sxs-lookup"><span data-stu-id="1ac66-148">Once LLDB starts, it may be necessary to use the `setsymbolserver` command to point at the correct symbol location (`setsymbolserver -ms` to use Microsoft's symbol server or `setsymbolserver -directory <path>` to specify a local path).</span></span> <span data-ttu-id="1ac66-149">ネイティブ シンボルは、`loadsymbols` を実行することで読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-149">Native symbols can be loaded by running `loadsymbols`.</span></span> <span data-ttu-id="1ac66-150">この時点で、[SOS コマンド](https://github.com/dotnet/diagnostics/blob/main/documentation/sos-debugging-extension.md)を使用して、ダンプを分析することができます。</span><span class="sxs-lookup"><span data-stu-id="1ac66-150">At this point, [SOS commands](https://github.com/dotnet/diagnostics/blob/main/documentation/sos-debugging-extension.md) can be used to analyze the dump.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ac66-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ac66-151">See also</span></span>

- <span data-ttu-id="1ac66-152">SOS 拡張機能のインストールの詳細については、[dotnet-sos](dotnet-sos.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ac66-152">[dotnet-sos](dotnet-sos.md) for more details on installing the SOS extension.</span></span>
- <span data-ttu-id="1ac66-153">シンボルのダウンロード ツールのインストールと使用の詳細については、[dotnet-symbol](dotnet-symbol.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ac66-153">[dotnet-symbol](dotnet-symbol.md) for more details on installing and using the symbol download tool.</span></span>
- <span data-ttu-id="1ac66-154">役立つ FAQ を含め、デバッグの詳細については、[.NET Core 診断のリポジトリ](https://github.com/dotnet/diagnostics/blob/main/documentation/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ac66-154">[.NET Core diagnostics repo](https://github.com/dotnet/diagnostics/blob/main/documentation/) for more details on debugging, including a useful FAQ.</span></span>
- <span data-ttu-id="1ac66-155">Linux または Mac に LLDB をインストールする手順については、[LLDB のインストール](https://github.com/dotnet/diagnostics/blob/main/documentation/sos.md#getting-lldb)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ac66-155">[Installing LLDB](https://github.com/dotnet/diagnostics/blob/main/documentation/sos.md#getting-lldb) for instructions on installing LLDB on Linux or Mac.</span></span>
