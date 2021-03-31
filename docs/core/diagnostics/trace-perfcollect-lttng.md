---
title: PerfCollect を使用した .NET アプリケーションのトレース。
description: .NET で PerfCollect を使用してトレースを収集する手順について説明するチュートリアル。
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 20e1bf56714fb32b5231d45b0ba35cdfcedaea2e
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189931"
---
# <a name="trace-net-applications-with-perfcollect"></a>PerfCollect を使用して .NET アプリケーションをトレースする

**この記事の対象: ✔️** .NET Core 2.1 SDK 以降のバージョン

Linux でパフォーマンスの問題が発生した場合は、`perfcollect` でトレースを収集することにより、パフォーマンスの問題が発生したときにコンピューターで何が起きていたかに関する詳細な情報を収集できます。

`perfcollect` は Bash スクリプトであり、[Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) を利用して、ランタイムまたは任意の [EventSource](xref:System.Diagnostics.Tracing.EventListener) から書き込まれたイベントを収集すると共に、[perf](https://perf.wiki.kernel.org/) を利用してターゲット プロセスの CPU サンプルを収集します。

## <a name="prepare-your-machine"></a>コンピューターを準備する

`perfcollect` を使用してパフォーマンス トレースが収集されるようコンピューターを準備するには、以下の手順のようにします。

> [!NOTE]
> コンテナー環境にいる場合は、コンテナーが `SYS_ADMIN` 機能を備えている必要があります。 PerfCollect を使用してコンテナー内のアプリケーションをトレースする方法の詳細については、「[コンテナーでの診断の収集](./diagnostics-in-containers.md)」を参照してください。

1. `perfcollect` をダウンロードします。

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. スクリプトを実行できるようにします。

    > ```bash
    > chmod +x perfcollect
    > ```

3. トレースの前提条件をインストールします。これらは実際のトレース ライブラリです。

    > ```bash
    > sudo ./perfcollect install
    > ```

    これにより、次の前提条件がコンピューターにインストールされます。

    1. `perf`: Linux Performance Events サブシステムと、コンパニオン ユーザーモード コレクションおよびビューアー アプリケーション。 `perf` は Linux カーネル ソースの一部ですが、通常は既定ではインストールされません。

    2. `LTTng`: 実行時に CoreCLR によって生成されるイベント データをキャプチャするために使用されます。 その後、このデータを使用して、GC、JIT、スレッド プールなどのさまざまなランタイム コンポーネントの動作が分析されます。

最新のバージョンの .NET Core および Linux perf ツールでは、フレームワーク コードのためのメソッド名の自動解決がサポートされています。 .NET Core バージョン 3.1 以下を使用している場合は、追加の手順が必要です。 詳細については、[フレームワーク シンボルの解決](#resolve-framework-symbols)に関するセクションを参照してください。

ネイティブ ランタイム DLL (libcoreclr.so など) のメソッド名の解決の場合は、`perfcollect` によってデータの変換時にそれらのシンボルが解決されますが、それが行われるのはこれらのバイナリのシンボルが存在する場合だけです。 詳細については、[ネイティブ ランタイムのシンボルの取得](#get-symbols-for-the-native-runtime)に関するセクションを参照してください。

## <a name="collect-a-trace"></a>トレースを収集する

1. 2 つのシェルを使用できるようにします。1 つはトレースの制御用で ( **[Trace]** と呼びます)、もう 1 つはアプリケーションの実行用です ( **[App]** と呼びます)。

2. **[Trace]** 収集を開始します。

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    予想される出力:

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. **[App]** 次の環境変数を使用して、アプリケーションのシェルを設定します。これにより、CoreCLR のトレース構成が有効になります。

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. **[App]** アプリを実行します。パフォーマンスの問題をキャプチャするために必要な限り実行させておきます。 正確な長さは、調査する必要があるパフォーマンスの問題が発生した時間帯を十分に把握できる限り、必要なだけ短くできます。

    > ```bash
    > dotnet run
    > ```

5. **[Trace]** 収集を停止します。Ctrl + C キーを押します。

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

    圧縮されたトレース ファイルが、現在の作業ディレクトリに格納されます。

## <a name="view-a-trace"></a>トレースを表示する

収集されたトレースを表示するには、いくつかのオプションがあります。 トレースは、Windows で [PerfView](https://aka.ms/perfview) を使用すると最も適切に表示されますが、`PerfCollect` 自体または `TraceCompass` を使用して Linux で直接表示することもできます。

### <a name="use-perfcollect-to-view-the-trace-file"></a>PerfCollect を使用してトレース ファイルを表示する

Perfcollect 自体を使用して、収集したトレースを表示できます。 これを行うには、次のコマンドを使用します。

```bash
./perfcollect view sampleTrace.trace.zip
```

このようにすると、既定では、`perf` を使用しているアプリケーションの CPU トレースが表示されます。

`LTTng` によって収集されたイベントを見るには、フラグ `-viewer lttng` を渡して個々のイベントを表示します。

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

このようにすると、`babeltrace` ビューアーを使用してイベントのペイロードが出力されます。

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a>PerfView を使用してトレース ファイルを開く

CPU サンプルとイベント両方の集約ビューを表示するには、Windows コンピューターで `PerfView` を使用します。

1. trace.zip ファイルを Linux から Windows コンピューターにコピーします。

2. <https://aka.ms/perfview> から PerfView をダウンロードします。

3. PerfView.exe を実行する

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

PerfView により、トレース ファイルに含まれるデータに基づいてサポートされるビューの一覧が表示されます。

- CPU の調査の場合は、 **[CPU stacks]\(CPU スタック\)** を選択します。

- GC の詳細な情報の場合は、 **[GCStats]\(GC 統計\)** を選択します。

- プロセス、モジュール、メソッドごとの JIT の情報の場合は、 **[JITStats]\(JIT 統計\)** を選択します。

- 必要な情報のビューがない場合は、生のイベント ビューでイベントを検索してみることができます。  **[Events]\(イベント\)** を選択します。

PerfView でのビューの解釈方法の詳細については、ビュー自体のヘルプ リンクを参照するか、PerfView のメイン ウィンドウで **[Help]\(ヘルプ\) > [Users Guide]\(ユーザー ガイド\)** を選択してください。

> [!NOTE]
> <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> API を使用して書き込まれたイベント (フレームワークからのイベントを含む) は、プロバイダー名の下に表示されません。 代わりに、`Microsoft-Windows-DotNETRuntime` プロバイダーの下に `EventSourceEvent` イベントとして書き込まれ、そのペイロードは JSON でシリアル化されます。

### <a name="use-tracecompass-to-open-the-trace-file"></a>TraceCompass を使用してトレース ファイルを開く

[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) は、トレースを表示するために使用できるもう 1 つのオプションです。 `TraceCompass` は Linux マシンでも動作するので、トレースを Windows コンピューターに移動する必要はありません。 `TraceCompass` を使用してトレース ファイルを開くには、ファイルを解凍する必要があります。

```bash
unzip myTrace.trace.zip
```

`perfcollect` によって収集された LTTng トレースは、`lttngTrace` 内のサブディレクトリに CTF ファイル形式で保存されます。 具体的には、CTF ファイルは `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` のようなディレクトリに格納されます。

`File -> Open Trace` を選択して `metadata` ファイルを選択することにより、`TraceCompass` で CTF トレースファイルを開くことができます。

詳細については、[`TraceCompass` のドキュメント](https://www.eclipse.org/tracecompass/)を参照してください。

## <a name="resolve-framework-symbols"></a>フレームワークのシンボルを解決する

フレームワークのシンボルは、トレースが収集されるときに手動で生成する必要があります。 フレームワークがプリコンパイルされるのに対して、アプリのコードは Just-In-Time コンパイルされるため、それらはアプリ レベルのシンボルとは異なります。 ネイティブ コードにプリコンパイルされたフレームワーク コードの場合は、ネイティブ コードからメソッドの名前へのマッピングを生成する方法を認識している `crossgen` を呼び出す必要があります。

`perfcollect` を使用するとほとんどの詳細を自動的に処理できますが、`crossgen` を使用できるようにしておく必要があります。 既定では、それは .NET ディストリビューションと共にインストールされません。 `crossgen` がない場合は、`perfcollect` の警告が表示され、以下の手順が示されます。 問題を解決するには、使用しているランタイム用の適切なバージョンの crossgen を正確にフェッチする必要があります。 crossgen ツールを .NET ランタイム DLL (libcoreclr.so など) と同じディレクトリに配置した場合は、`perfcollect` によってそれが検索され、フレームワーク シンボルがトレース ファイルに自動的に追加されます。

通常、.NET アプリケーションを作成すると、記述されたコードの DLL だけが生成され、それ以外の部分についてはランタイムの共有コピーが使用されます。   ただし、アプリケーションの "自己完結型" バージョンと呼ばれる、すべてのランタイム DLL が含まれるものを生成することもできます。 `crossgen` は自己完結型アプリの作成に使用される NuGet パッケージの一部であるため、適切なバージョンの `crossgen` を取得する方法の 1 つは、アプリケーションの自己完結型パッケージを作成することです。

次に例を示します。

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

これにより、新しい Hello World アプリケーションが作成され、自己完結型アプリとしてビルドされます。

自己完結型アプリケーションを作成する副作用として、dotnet ツールにより runtime.linux-x64.microsoft.netcore.app という名前の NuGet パッケージがダウンロードされて、ディレクトリ ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION に配置されます。VERSION は、.NET Core ランタイムのバージョン番号です (例: 2.1.0)。 その下にある tools ディレクトリ内に、必要な crossgen ツールがあります。 .NET Core 3.0 以降でのパッケージの場所は、~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION です。

`crossgen` ツールは、アプリケーションによって実際に使用されるランタイムに並べて配置する必要があります。 通常は、/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION にインストールされている .NET Core の共有バージョンが、アプリで使用されます。VERSION は、.NET ランタイムのバージョン番号です。 これは共有の場所であるため、それを変更するにはスーパーユーザーである必要があります。 VERSION が 2.1.0 の場合、`crossgen` を更新するためのコマンドは次のようになります。

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

これが完了すると、`perfcollect` により crossgen を使用してフレームワーク シンボルが組み込まれます。 前に `perfcollect` によって表示されていた警告は出なくなります。 これは、コンピューターごとに 1 回だけ行う必要があります (ランタイムを更新するまで)。

### <a name="alternative-turn-off-use-of-precompiled-code"></a>代替手段: プリコンパイル済みコードの使用をオフにする

(`crossgen` を追加するために) .NET ランタイムを更新することができない場合、または上記の手順がなんらかの理由で機能しない場合は、フレームワーク シンボルを取得するための別の方法があります。 プリコンパイルされたフレームワーク コードを単に使用しないよう、ランタイムに指示することができます。 コードは Just-in-time でコンパイルされるので、`crossgen` は必要ありません。

> [!NOTE]
> この方法を選択すると、アプリケーションの起動時間が長くなる可能性があります。

これを行うには、次の環境変数を追加します。

```bash
export COMPlus_ZapDisable=1
```

このように変更すると、すべての .NET コードに対するシンボルが取得されるはずです。

## <a name="get-symbols-for-the-native-runtime"></a>ネイティブ ランタイムのシンボルを取得する

ほとんどの場合、関心があるのは独自のコードであり、それは `perfcollect` によって既定で解決されます。 場合によっては、NET DLL の内部で起こっていること (最後のセクションの内容) を確認すると役に立つことがありますが、ネイティブ ランタイム dll (通常は libcoreclr.so) で何が起こっているかは興味深いものです。  `perfcollect` によってデータの変換時にこれらに対するシンボルが解決されますが、これらのネイティブ DLL のシンボルが存在する場合 (および、それらが対象のライブラリの隣にある場合) に限られます。

これを行う [dotnet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) という名前のグローバル コマンドがあります。 dotnet-symbol を使用してネイティブ ランタイム シンボルを取得するには:

1. `dotnet-symbol` をインストールします。

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. シンボルをダウンロードします。 インストールされている .NET Core ランタイムのバージョンが 2.1.0 の場合は、次のコマンドを実行します。

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. シンボルを正しい場所にコピーします。

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    適切なディレクトリへの書き込みアクセス権がないためにこの操作を実行できない場合は、`perf buildid-cache` を使用してシンボルを追加できます。

その後、`perfcollect` を実行するときに、ネイティブ dll のシンボル名を取得する必要があります。

## <a name="collect-in-a-docker-container"></a>Docker コンテナー内で収集する

コンテナー環境で `perfcollect` を使用する方法の詳細については、「[コンテナーでの診断の収集](./diagnostics-in-containers.md)」を参照してください。

## <a name="learn-more-about-collection-options"></a>収集オプションについての詳細情報

診断のニーズに合わせて、`perfcollect` を使用して次のオプションのフラグを指定できます。

### <a name="collect-for-a-specific-duration"></a>特定の期間について収集する

特定の期間についてトレースを収集する場合は、`-collectsec` オプションに続けて、トレースを収集する合計秒数を数値で指定できます。

### <a name="collect-threadtime-traces"></a>threadtime のトレースを収集する

`-threadtime` と共に `perfcollect` を指定すると、スレッドごとの CPU 使用率データを収集できます。 これにより、各スレッドが CPU 時間を費やしていた場所を分析できます。

### <a name="collect-traces-for-managed-memory-and-garbage-collector-performance"></a>マネージド メモリとガベージ コレクターのパフォーマンスのトレースを収集する

次のオプションを使用すると、ランタイムから特に GC イベントを収集できます。

* `perfcollect collect -gccollectonly`

GC 収集イベントの最小セットのみを収集します。 これは、ターゲット アプリのパフォーマンスへの影響が最も少ない、最も詳細度の低い GC イベント収集プロファイルです。 このコマンドは PerfView の `PerfView.exe /GCCollectOnly collect` コマンドと似ています。

* `perfcollect collect -gconly`

JIT、ローダー、例外イベントを使用して、より詳細な GC 収集イベントを収集します。 これにより、より詳細なイベント (割り当て情報や GC 結合情報など) が要求され、`-gccollectonly` オプションよりもターゲット アプリのパフォーマンスに大きく影響します。 このコマンドは PerfView の `PerfView.exe /GCOnly collect` コマンドと似ています。

* `perfcollect collect -gcwithheap`

最も詳細な GC コレクション イベントを収集します。これにより、ヒープの存続と移動も追跡されます。 これにより、GC の動作を詳細に分析できますが、各 GC に 2 倍以上の時間がかかるおそれがあるため、パフォーマンス コストが高くなります。 運用環境でトレースするときにこのトレース オプションを使用した場合のパフォーマンスへの影響を理解しておくことをお勧めします。
