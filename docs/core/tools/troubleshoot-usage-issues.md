---
title: .NET ツールの使用に関する問題のトラブルシューティング
description: .NET ツールを実行するときの一般的な問題と、考えられる解決策について説明します。
author: kdollard
ms.topic: troubleshooting
ms.date: 02/14/2020
ms.openlocfilehash: 9cf0320ec5b5d6f317a4ef7f9052c0068b3ad8e5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104090"
---
# <a name="troubleshoot-net-tool-usage-issues"></a>.NET ツールの使用に関する問題のトラブルシューティング

.NET ツールをグローバル ツールまたはローカル ツールとしてインストールまたは実行しようとすると、問題が発生することがあります。 この記事では、一般的な根本原因と考えられる解決策について説明します。

## <a name="installed-net-tool-fails-to-run"></a>インストールした .NET ツールを実行できない

.NET ツールの実行が失敗する場合、次のいずれかの問題が発生した可能性が高いです。

* ツールの実行可能ファイルが見つかりませんでした。
* 正しいバージョンの .NET ランタイムが見つかりませんでした。

### <a name="executable-file-not-found"></a>実行可能ファイルが見つからない

実行可能ファイルが見つからない場合は、次のようなメッセージが表示されます。

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

実行可能ファイルの名前によって、ツールの呼び出し方法が決まります。 次の表ではその形式について説明します。

| 実行可能ファイル名の形式  | 呼び出し方式   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* グローバル ツール

  グローバル ツールは、既定のディレクトリ内または特定の場所にインストールすることができます。 既定のディレクトリは次のとおりです。

  | OS          | パス                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  | Windows     | `%USERPROFILE%\.dotnet\tools` |

  グローバル ツールを実行しようとしている場合は、コンピューター上の `PATH` 環境変数にグローバル ツールをインストールしたパスが含まれること、およびそのパスに実行可能ファイルが存在することを確認してください。

  .NET CLI では、初めて使用したときに、既定の場所を PATH 環境変数に追加する処理が試行されます。 ただし、次のようなシナリオでは、その場所が PATH に自動的に追加されない場合があります。

  * Linux を使用していて、apt-get または rpm ではなく *.tar.gz* ファイルを使用して .NET SDK をインストールしている場合。
  * macOS 10.15 "Catalina" またはそれ以降のバージョンを使用している場合。
  * macOS 10.14 "Mojave" 以前のバージョンを使用していて、 *.pkg* ではなく *.tar.gz* ファイルを使用して .NET SDK をインストールしている場合。
  * .NET Core 3.0 SDK をインストールしてあり、`DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` 環境変数を `false` に設定している場合。
  * .NET Core 2.2 SDK 以前のバージョンをインストールしてあり、`DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 環境変数を `true` に設定している場合。

  これらのシナリオでは、または `--tool-path` オプションを指定した場合、ご利用のコンピューター上の `PATH` 環境変数には、グローバル ツールをインストールしたパスが自動的に含められません。 その場合は、ご利用のシェルで提供されている、環境変数を更新するための任意の方法を使用して、ツールの場所 (たとえば、`$HOME/.dotnet/tools`) を `PATH` 環境変数に追加します。 詳細については、[.NET ツール](global-tools.md)に関するページを参照してください。

* ローカル ツール

  ローカル ツールを実行しようとしている場合は、*dotnet-tools.json* という名前のマニフェストファイルが、現在のディレクトリまたはそのいずれかの親ディレクトリにあることを確認します。 このファイルは、ルート フォルダーではなく、プロジェクト フォルダー階層のどこかにある *.config* という名前のフォルダーに存在することもあります。 *dotnet-tools.json* が存在する場合は、それを開き、実行しようとしているツールを確認します。 ファイルに `"isRoot": true` のエントリが含まれていない場合は、さらに上のファイル階層で他のツール マニフェスト ファイルを確認します。

  指定したパスでインストールされた .NET ツールを実行しようとしている場合は、ツールを使用するときにそのパスを含める必要があります。 ツールパスにインストールされたツールを使用する例を次に示します。

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>ランタイムが見つからない

.NET ツールは、[フレームワーク依存のアプリケーション](../deploying/index.md#publish-framework-dependent)です。つまり、お使いのマシンにインストールされている .NET ランタイムに依存します。 予定のランタイムが見つからない場合、次のような通常の .NET ランタイムのロール フォワード ルールに従います。

* アプリケーションは、指定されたメジャー バージョンおよびマイナー バージョンの最上位の修正プログラム リリースにロール フォワードされます。
* 一致するメジャー バージョン番号とマイナー バージョン番号と一致するランタイムがない場合は、次に高いマイナー バージョンが使用されます。
* ランタイムのプレビュー バージョン間、またはプレビュー バージョンとリリース バージョン間では、ロール フォワードは発生しません。 したがって、プレビュー バージョンを使用して作成された .NET ツールは、作成者がリビルドして再パブリッシュしてから再インストールする必要があります。

次の 2 つの一般的なシナリオでは、ロールフォワードは既定では実行されません。

* 使用できるのが古いバージョンのランタイムだけの場合。 ロールフォワードでは、ランタイムの新しいバージョンのみが選択されます。
* 使用できるのが高いメジャー バージョンのランタイムだけの場合。 ロールフォワードでは、メジャー バージョンの境界を越えることはありません。

アプリケーションで適切なランタイムが見つからない場合は、実行が失敗し、エラーが報告されます。

次のいずれかのコマンドを使用して、お使いのマシンにインストールされている .NET ランタイムを確認することができます。

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

現在インストールされているランタイム バージョンがツールでサポートされている必要があると思われる場合は、ツールの作成者に連絡して、バージョン番号またはマルチターゲットを更新できるかどうかを確認してください。 更新されたバージョン番号でツール パッケージが再コンパイルされて NuGet に再発行された後、コピーを更新することができます。 それまでの間の最も簡単な解決策は、実行しようとしているツールで動作するランタイムのバージョンをインストールすることです。 特定の .NET ランタイム バージョンをダウンロードするには、[.NET ダウンロード ページ](https://dotnet.microsoft.com/download/dotnet)にアクセスしてください。

.NET SDK を既定以外の場所にインストールする場合は、環境変数 `DOTNET_ROOT` を `dotnet` 実行可能ファイルが格納されているディレクトリに設定する必要があります。

## <a name="net-tool-installation-fails"></a>.NET ツールのインストールが失敗する

いろいろな理由で、.NET のグローバル ツールまたはローカル ツールのインストールが失敗する可能性があります。 ツールのインストールが失敗すると、次のようなメッセージが表示されます。

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

これらのエラーの診断に役立つよう、上のメッセージと共に、NuGet のメッセージがユーザーに直接表示されます。 NuGet のメッセージは、問題の特定に役立つ場合があります。

### <a name="package-naming-enforcement"></a>パッケージの名前付けの適用

Microsoft では、ツールのパッケージ ID に関するガイダンスを変更したため、いくつかのツールが予測される名前で見つからなくなっています。 新しいガイダンスでは、すべての Microsoft ツールに "Microsoft" というプレフィックスが付いています。 このプレフィックスは予約されており、Microsoft が承認した証明書で署名されたパッケージにのみ使用できます。

移行の間は、古い形式のパッケージ ID を持つ Microsoft ツールと、新しい形式を持つツールが混在します。

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

パッケージ ID が更新されると、最新の更新プログラムを取得するには、新しいパッケージ ID に変更する必要があります。 ツール名が簡略化されているパッケージは非推奨となります。

### <a name="preview-releases"></a>プレビュー リリース

* プレビュー リリースをインストールしようとして、`--version` オプションを使用してバージョンを指定しませんでした。

プレビュー段階にある .NET ツールを名前の一部に指定して、プレビュー段階であることを示す必要があります。 プレビュー全体を含める必要はありません。 バージョン番号が想定される形式であると仮定すると、次の例のようなものを使用できます。

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-tool"></a>パッケージが .NET ツールではない

* この名前の NuGet パッケージは見つかりましたが、.NET ツールではありませんでした。

.NET ツールではなく、通常の NuGet パッケージである NuGet パッケージをインストールしようとすると、次のようなエラーが表示されます。

> NU1212:`<ToolName>` のプロジェクトとパッケージの組み合わせが無効です。 DotnetToolReference プロジェクト形式には、DotnetTool タイプの参照のみ含めることができます。

### <a name="nuget-feed-cant-be-accessed"></a>NuGet フィードにアクセスできない

* おそらくインターネット接続に問題があるため、必要な NuGet フィードにアクセスできません。

ツールをインストールするには、ツール パッケージが含まれている NuGet フィードにアクセスする必要があります。 フィードが使用できない場合は失敗します。 `nuget.config` でフィードを変更するか、特定の `nuget.config` ファイルを要求するか、`--add-source` スイッチを使用して追加のフィードを指定することができます。 既定では、NuGet では接続できないフィードに対してエラーがスローされます。 フラグ `--ignore-failed-sources` を指定すると、これらの到達できないソースをスキップできます。

### <a name="package-id-incorrect"></a>パッケージ ID が正しくない

* ツールの名前が間違って入力されています。

失敗でよくある理由は、ツール名が正しくないことです。 これは、入力ミスや、ツールが移動されたか非推奨になったために、発生する可能性があります。 NuGet.org のツールで、確実に正しい名前を使用する方法の 1 つは、NuGet.org でツールを検索し、インストール コマンドをコピーすることです。

## <a name="see-also"></a>関連項目

* [.NET ツール](global-tools.md)
