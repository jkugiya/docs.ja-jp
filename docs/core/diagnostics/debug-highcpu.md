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
# <a name="debug-high-cpu-usage-in-net-core"></a>.NET Core で高い CPU 使用率をデバッグする

**この記事の対象: ✔️** .NET Core 3.1 SDK 以降のバージョン

このチュートリアルでは、過剰な CPU 使用率のシナリオをデバッグする方法について説明します。 示されている例の [ASP.NET Core Web アプリ](/samples/dotnet/samples/diagnostic-scenarios) ソース コード リポジトリを使用して、デッドロックを意図的に発生させることができます。 エンドポイントでは、ハングとスレッドが蓄積します。 さまざまなツールを使用して、診断データのいくつかの重要な部分でこのシナリオを診断する方法について説明します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
>
> - 高い CPU 使用率を調査する
> - [dotnet-counters](dotnet-counters.md) を使って CPU 使用率を確認する
> - [dotnet-trace](dotnet-trace.md) を使ってトレース生成を行う
> - PerfView でパフォーマンスをプロファイリングする
> - 過剰な CPU 使用率を診断して解決する

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは次のものを使用します。

- [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン。
- シナリオをトリガーする[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)
- [dotnet-trace](dotnet-trace.md) を使ってプロセスを一覧表示し、プロファイルを生成する
- [dotnet-counters](dotnet-counters.md) を使って CPU 使用率を監視する

## <a name="cpu-counters"></a>CPU カウンター

診断データの収集を試行する前に、高い CPU 状態を確認する必要があります。 プロジェクトのルート ディレクトリから次のコマンドを使用して、[サンプル アプリケーション](/samples/dotnet/samples/diagnostic-scenarios)を実行します。

```dotnetcli
dotnet run
```

このプロセス ID を検索するには、次のコマンドを使用します。

```dotnetcli
dotnet-trace ps
```

ご自分のコマンド出力からプロセス ID をメモしておきます。 プロセス ID は `22884` でしたが、この ID は異なります。 現在の CPU 使用率を確認するには、[dotnet-counters](dotnet-counters.md) ツール コマンドを使用します。

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

`refresh-interval` は、CPU 値をポーリングするカウンターの間隔を秒数で示します。 出力は次のようになります。

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

Web アプリを実行している状態で、スタートアップ直後に CPU が使用されておらず、`0%` で報告されます。 ルート パラメーターとして `60000` を使用して `api/diagscenario/highcpu` ルートに移動します。

`https://localhost:5001/api/diagscenario/highcpu/60000`

次に、[dotnet-counters](dotnet-counters.md) コマンドを再実行します。 `cpu-usage` だけを監視するには、コマンドの一部として `System.Runtime[cpu-usage]` を指定します。

```dotnetcli
dotnet-counters monitor --counters System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

次に示すように、CPU 使用率が増加していることがわかります。

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

要求の間、CPU 使用率は 25% 前後で推移します。 ホスト コンピューターに応じて、CPU 使用率が変わることが予想されます。

> [!TIP]
> さらに高い CPU 使用率を視覚化するには、複数のブラウザー タブでこのエンドポイントを同時に実行します。

この時点で、CPU が予想以上に高くなっていることを確認できます。

## <a name="trace-generation"></a>トレース生成

低速の要求を分析する場合は、コードの実行内容に関する分析情報を提供できる診断ツールが必要です。 通常はプロファイラーが適しており、さまざまなプロファイラー オプションを選択できます。

### <a name="linux"></a>[Linux](#tab/linux)

`perf` ツールを使用すると、.NET Core アプリ プロファイルを生成できます。 [サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)の前のインスタンスを終了します。

`COMPlus_PerfMapEnabled` 環境変数を設定して、.NET Core アプリによって `/tmp` ディレクトリ内に `map` ファイルが作成されるようにします。 この `map` ファイルは、CPU アドレスを名前順に JIT 生成関数にマップするために `perf` によって使用されます。 詳細については、「[パフォーマンス マップの作成](../run-time-config/debugging-profiling.md#write-perf-map)」を参照してください。

同じターミナル セッションで、[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)を実行します。

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

高 CPU API エンドポイント (`https://localhost:5001/api/diagscenario/highcpu/60000`) をもう一度実行します。 それが 1 分間の要求内で実行されている間に、プロセス ID を使用して `perf` コマンドを実行します。

```bash
sudo perf record -p 2266 -g
```

`perf` コマンドを実行すると、パフォーマンス コレクション プロセスが開始されます。 約 20 から 30 秒間実行してから、<kbd>Ctrl + C</kbd> キーを押してコレクション プロセスを終了します。 同じ `perf` コマンドを使用して、トレースの出力を確認できます。

```bash
sudo perf report -f
```

次のコマンドを使用して "_フレーム グラフ_" を生成することもできます。

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

このコマンドを実行すると、`flamegraph.svg` が生成され、これをブラウザーに表示してパフォーマンスの問題を調査することができます。

[![フレーム グラフの SVG イメージ](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)

### <a name="windows"></a>[Windows](#tab/windows)

Windows では、プロファイラーとして [dotnet-trace](dotnet-trace.md) ツールを使用できます。 前の[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios)を使用して、高 CPU エンドポイント (`https://localhost:5001/api/diagscenario/highcpu/60000`) をもう一度実行します。 それが 1 分間の要求内で実行されている間に、次のように `collect` コマンドを使用します。

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

[dotnet-trace](dotnet-trace.md) を約 20 から 30 秒間実行してから、<kbd>Enter</kbd> キーを押してコレクションを終了します。 その結果、同じフォルダー内に `nettrace` ファイルが生成されます。 `nettrace` ファイルは、Windows 上の既存の分析ツールを使用するのに最適な方法です。

次に示すように、[`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) を使用して `nettrace` を開きます。

[![PerfView イメージ](media/perfview.jpg)](media/perfview.jpg#lightbox)

---

## <a name="see-also"></a>関連項目

- [dotnet-trace](dotnet-trace.md) を使ってプロセスを一覧表示する
- [dotnet-counters](dotnet-counters.md) を使ってマネージド メモリ使用量を確認する
- [dotnet-dump](dotnet-dump.md) を使ってダンプ ファイルを収集して分析する
- [dotnet/診断](https://github.com/dotnet/diagnostics/tree/main/documentation/tutorial)

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [.NET Core でデッドロックをデバッグする](debug-deadlock.md)
