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
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core で使用できる診断ツール

ソフトウェアは期待どおりに動作するとは限りませんが、.NET Core には、そのような問題を迅速かつ効果的に診断するために役立つツールと API が用意されています。

この記事は、必要な各種ツールを見つけるために役立ちます。

## <a name="managed-debuggers"></a>マネージド デバッガー

[マネージド デバッガー](managed-debuggers.md)を使用すると、プログラムと対話することができます。 一時停止、段階的な実行、調査、および再開によって、コードの動作を分析できます。 デバッガーは、簡単に再現できる機能の問題を診断するための最初の選択肢です。

## <a name="logging-and-tracing"></a>ログとトレース

[ログとトレース](logging-tracing.md)は、関連する手法です。 ログ ファイルを作成するためのコードのインストルメント化を指します。 ファイルには、プログラムの機能の詳細が記録されます。 これらの詳細は、複雑度の高い問題を診断するために使用できます。 タイム スタンプと組み合わせると、これらの手法はパフォーマンスの調査にも役立ちます。

## <a name="metrics"></a>メトリック

[EventCounters](event-counters.md) を使用すると、パフォーマンスの問題を特定して監視するためのメトリックを作成できます。 メトリックを使用すると、トレースと比較してパフォーマンスのオーバーヘッドが低くなるため、常時接続のパフォーマンスの監視に適しています。 .NET ランタイムとライブラリでは、いくつかの[既知の EventCounters](available-counters.md) を発行して、同様に監視することができます。

## <a name="unit-testing"></a>単体テスト

[単体テスト](../testing/index.md)は、高品質のソフトウェアを継続的に統合して展開するための重要なコンポーネントです。 単体テストは、何かを中断するときに早期警告を提供するように設計されています。

## <a name="dumps"></a>ダンプ

[ダンプ](./dumps.md)は、作成時のプロセスのスナップショットを含むファイルです。 これらは、デバッグのためにアプリケーションの状態を調べるのに役立ちます。

## <a name="symbols"></a>シンボル

[シンボル](./symbols.md)は、ソース コードとコンパイラによって生成されるバイナリとの間のマッピングです。 これらは一般的に、ソースの行番号、ローカル変数名、その他の種類の診断情報などを解決するために .NET デバッガーによって使用されます。

## <a name="collect-diagnostics-in-containers"></a>コンテナーでの診断の収集

コンテナー化されていない Linux 環境で使用されているのと同じ診断ツールを使用して、[コンテナーで診断を収集](diagnostics-in-containers.md)することもできます。 Docker コンテナーでツールを動作させるために必要ないくつかの使用方法が変更されています。

## <a name="net-core-diagnostic-global-tools"></a>.NET Core 診断グローバル ツール

### <a name="dotnet-counters"></a>dotnet-カウンター

[dotnet-カウンター](dotnet-counters.md)は、第 1 レベルの正常性監視とパフォーマンス調査のためのパフォーマンス監視ツールです。 <xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視します。 たとえば、CPU 使用率や、.NET Core アプリケーションでスローされる例外の発生率などをすばやく監視できます。

### <a name="dotnet-dump"></a>dotnet-ダンプ

[dotnet-ダンプ](dotnet-dump.md) ツールは、ネイティブ デバッガーを使用せずに Windows と Linux のコア ダンプを収集して分析する方法です。

### <a name="dotnet-gcdump"></a>dotnet-gcdump

[dotnet-gcdump](dotnet-gcdump.md) ツールは、ライブ .NET プロセスの GC (ガベージ コレクター) ダンプを収集する手段です。

### <a name="dotnet-trace"></a>dotnet-トレース

.NET Core には、診断データが公開される `EventPipe` と呼ばれるものが含まれています。 [dotnet-トレース](dotnet-trace.md) ツールを使用すると、アプリから興味深いプロファイル データを使用できます。これは、アプリケーションの実行速度が低下する可能性のあるシナリオに役立ちます。

### <a name="dotnet-symbol"></a>dotnet-symbol

[dotnet-symbol](dotnet-symbol.md) によって、コア ダンプまたはミニダンプを開くために必要なファイル (シンボル、DAC/DBI、ホスト ファイルなど) をダウンロードできます。 別のコンピューターでキャプチャされたダンプ ファイルをデバッグするためにシンボルとモジュールが必要な場合は、このツールを使用します。

### <a name="dotnet-sos"></a>dotnet-sos

[dotnet-sos](dotnet-sos.md) によって、Linux と macOS に [SOS デバッグ拡張機能](sos-debugging-extension.md) がインストールされます ([Windbg/cdb](/windows-hardware/drivers/debugger/debugger-download-tools) を使用している場合は Windows でも)。

### <a name="perfcollect"></a>PerfCollect

[PerfCollect](trace-perfcollect-lttng.md) は、Linux ディストリビューションで実行されている .NET アプリのより詳細なパフォーマンス分析を行うために `perf` と `LTTng` でトレースを収集するために使用できる bash スクリプトです。

## <a name="net-core-diagnostics-tutorials"></a>.NET Core 診断チュートリアル

### <a name="debug-a-memory-leak"></a>メモリ リークをデバッグする

[チュートリアル: メモリ リークをデバッグする](debug-memory-leak.md)では、メモリ リークを検出する手順について説明します。 リークを確認するには [dotnet-counters](dotnet-counters.md) ツールを使用し、リークを診断するには [dotnet-dump](dotnet-dump.md) ツールを使用します。

### <a name="debug-high-cpu-usage"></a>高い CPU 使用率をデバッグする

[チュートリアル: 高い CPU 使用率をデバッグする](debug-highcpu.md) に関するページに、高い CPU 使用率の調査方法が示されています。 高い CPU 使用率を確認するために、[dotnet-counters](dotnet-counters.md) ツールが使用されます。 次に、[パフォーマンス分析ユーティリティ (`dotnet-trace`) 用のトレース](dotnet-trace.md)または Linux `perf` を使用して、CPU 使用率プロファイルを収集および表示する手順について説明します。

### <a name="debug-deadlock"></a>デッドロックをデバッグする

[チュートリアル: デッドロックのデバッグ](debug-deadlock.md)に関するページに、[dotnet-dump](dotnet-dump.md) ツールを使用してスレッドとロックを調査する方法が示されています。

### <a name="debug-a-stackoverflow"></a>スタック オーバーフローのデバッグ

[チュートリアル: スタック オーバーフローのデバッグ](debug-stackoverflow.md)」は、Linux で <xref:System.StackOverflowException> をデバッグする方法を示します。

### <a name="debug-linux-dumps"></a>Linux ダンプのデバッグ

「[Linux ダンプのデバッグ](debug-linux-dumps.md)」では、Linux でダンプを収集して分析する方法について説明します。

### <a name="measure-performance-using-eventcounters"></a>EventCounters を使用してパフォーマンスを測定する

[チュートリアル: .NET で EventCounters を使用してパフォーマンスを測定する](event-counter-perf.md)」は、<xref:System.Diagnostics.Tracing.EventCounter> API を使用して .NET アプリのパフォーマンスを測定する方法を示します。
