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
# <a name="debug-linux-dumps"></a>Linux ダンプのデバッグ

**この記事の対象: ✔️** .NET Core 3.0 SDK 以降のバージョン

## <a name="collect-dumps-on-linux"></a>Linux でダンプを収集する

Linux でダンプを収集するための推奨される 2 つの方法:

* [`dotnet-dump`](dotnet-dump.md) CLI ツール
* クラッシュ時にダンプを収集する[環境変数](dumps.md#collecting-dumps-on-crash)

### <a name="managed-dumps-with-dotnet-dump"></a>`dotnet-dump` を使用するマネージド ダンプ

[`dotnet-dump`](dotnet-dump.md) ツールは使いやすく、ネイティブ デバッガーとの依存関係はありません。 `dotnet-dump` は、従来のデバッグ ツールを使用できない場合があるさまざまな Linux プラットフォーム (Alpine や ARM32 または ARM64 など) で動作します。 しかし、`dotnet-dump` によって、マネージド状態のみがキャプチャされるため、ネイティブ コードでの問題のデバッグには使用できません。 `dotnet-dump` によって収集されるダンプは、ダンプが作成されたのと同じ OS とアーキテクチャがある環境で分析されます。 [`dotnet-gcdump`](dotnet-gcdump.md) ツールは、キャプチャされるのが GC ヒープ情報のみではあるものの、Windows で分析できるダンプを生成する代替手段として使用できます。

### <a name="core-dumps-with-createdump"></a>`createdump` を使用するコア ダンプ

マネージドのみのダンプを作成する `dotnet-dump` の代替手段として、[`createdump`](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md) は、ネイティブとマネージドの両方の情報を含む Linux のコア ダンプを作成するための推奨ツールです。 gdb や gcore などの他のツールを使用して、コア ダンプを作成することもできますが、マネージド デバッグに必要な状態を見逃してしまう可能性があり、その結果、分析中に "不明な" 種類または関数名が検出されることになります。

`createdump` ツールは .NET Core ランタイムと共にインストールされ、libcoreclr.so の隣にあります(通常は、"/usr/share/dotnet/shared/Microsoft.NETCore.App/[バージョン]" 内)。 このツールにより、そのプライマリ引数としてダンプを収集するプロセス ID が受け取られ、収集するダンプの種類 (既定値はヒープ付きのミニダンプ) を指定する省略可能なパラメーターも受け取られます。 次のオプションがあります。

- **`<input-filename>`**

  変換する入力トレース ファイル。 既定は *trace.nettrace* です。

### <a name="options"></a>オプション

- **`-f|--name <output-filename>`**

  ダンプの書き込み先のファイル。 既定値は '/tmp/coredump.%p' です。ここで、%p はターゲットプ ロセスのプロセス ID です。

- **`-n|--normal`**

  ミニダンプを作成します。

- **`-h|--withheap`**

  ヒープ付きミニダンプを作成します (既定値)。

- **`-t|--triage`**

  トリアージ ミニダンプを作成します。

- **`-u|--full`**

  完全なコア ダンプを作成します。

- **`-d|--diag`**

  診断メッセージを有効にします。

コア ダンプを収集するには、`SYS_PTRACE` 機能を使用するか、sudo または su で `createdump` を実行する必要があります。

## <a name="analyze-dumps-on-linux"></a>Linux でダンプを分析する

`dotnet-dump` で収集されるマネージド ダンプと `createdump` で収集されるコア ダンプは両方とも、`dotnet-dump` ツールで `dotnet-dump analyze` コマンドを使用して分析することができます。 `dotnet dump` には、ダンプを分析する環境に、ダンプがキャプチャされた環境と同じ OS とアーキテクチャが必要とされます。

[LLDB](https://lldb.llvm.org/) を使用して、Linux でコア ダンプを分析することもできます。これにより、マネージドとネイティブの両方のフレームを分析できます。 LLDB によって SOS 拡張機能が使用され、マネージド コードがデバッグされます。 [`dotnet-sos`](dotnet-sos.md) CLI ツールを使用すると、マネージド コードをデバッグするための[多くの便利なコマンド](https://github.com/dotnet/diagnostics/blob/main/documentation/sos-debugging-extension.md)がある SOS をインストールできます。 .NET Core ダンプを分析するために、LLDB と SOS には、ダンプが作成された環境の次の .NET Core バイナリが必要です。

1. libmscordaccore.so
2. libcoreclr.so
3. dotnet (アプリを起動するために使用されるホスト)

ほとんどの場合、これらのバイナリは、[`dotnet-symbol`](dotnet-symbol.md) ツールを使用してダウンロードできます。 必要なバイナリを `dotnet-symbol` と共にダウンロードできない場合 (たとえば、ソースから構築された .NET Core のプライベート バージョンが使用中だった場合)、ダンプが作成された環境から、上に一覧表示されているファイルをコピーする必要がある場合があります。 ファイルがダンプ ファイルの横にない場合は、LLDB または SOS コマンドの `setclrpath <path>` を使用して、読み込み元のパスを設定し、`setsymbolserver -directory <path>` を使用して、シンボル ファイルの参照先のパスを設定することができます。

必要なファイルが使用できるようになったら、デバッグする実行可能ファイルとして dotnet ホストを指定し、LLDB にダンプを読み込むことができます。

```console
lldb --core <dump-file> <host-program>
```

上記のコマンド ラインでは、`<dump-file>` は分析するダンプのパスであり、`<host-program>` は .NET Core アプリケーションを起動したネイティブ プログラムです。 アプリが自己完結型である場合を除き、これは通常、`dotnet` バイナリです。この場合、dll 拡張子のないアプリケーションの名前になります。

LLDB が起動したら、`setsymbolserver` コマンドを使用して、正しいシンボルの場所をポイントする必要がある場合があります (Microsoft のシンボル サーバーを使用する場合は `setsymbolserver -ms`、ローカル パスを指定する場合は `setsymbolserver -directory <path>`)。 ネイティブ シンボルは、`loadsymbols` を実行することで読み込むことができます。 この時点で、[SOS コマンド](https://github.com/dotnet/diagnostics/blob/main/documentation/sos-debugging-extension.md)を使用して、ダンプを分析することができます。

## <a name="see-also"></a>関連項目

- SOS 拡張機能のインストールの詳細については、[dotnet-sos](dotnet-sos.md) に関するページを参照してください。
- シンボルのダウンロード ツールのインストールと使用の詳細については、[dotnet-symbol](dotnet-symbol.md)に関するページを参照してください。
- 役立つ FAQ を含め、デバッグの詳細については、[.NET Core 診断のリポジトリ](https://github.com/dotnet/diagnostics/blob/main/documentation/)を参照してください。
- Linux または Mac に LLDB をインストールする手順については、[LLDB のインストール](https://github.com/dotnet/diagnostics/blob/main/documentation/sos.md#getting-lldb)に関する記述を参照してください。
