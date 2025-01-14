---
title: macOS に .NET をインストールする
description: .NET をインストールできる macOS のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 9961d3e3ddb5f38be1c9c13c01af2e41815f50c9
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875253"
---
# <a name="install-net-on-macos"></a>macOS に .NET をインストールする

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

この記事では、macOS に .NET をインストールする方法について説明します。 .NET は、ランタイムと SDK で構成されています。 ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。 SDK は、.NET アプリとライブラリの作成に使用されます。 .NET ランタイムは、常に SDK と共にインストールされます。

.NET の最新バージョンは 5.0 です。

> [!div class="button"]
> [.NET Core のダウンロード](https://dotnet.microsoft.com/download/dotnet)

## <a name="supported-releases"></a>サポートされているリリース

次の表に、現在サポートされている .NET リリースと、それらがサポートされている macOS のバージョンの一覧を示します。 これらのバージョンは、いずれかのバージョンの [.NET がサポート終了に達する](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)まで、サポートされています。

- ✔️ は、.NET Core のバージョンがまだサポートされていることを示します。
- ❌ は、.NET Core のバージョンがサポートされていないことを示します。

| オペレーティング システム          | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|---------------------------|---------------|---------------|----------------|
| macOS 11.0 "Big Sur"        | ✔️ 2.1 ([リリース ノート][release-notes-21]) | ✔️ 3.1 ([リリース ノート][release-notes-31]) | ✔️ 5.0 ([リリース ノート][release-notes-50]) |
| macOS 10.15 "Catalina"    | ✔️ 2.1 ([リリース ノート][release-notes-21]) | ✔️ 3.1 ([リリース ノート][release-notes-31]) | ✔️ 5.0 ([リリース ノート][release-notes-50]) |
| macOS 10.14 "Mojave"      | ✔️ 2.1 ([リリース ノート][release-notes-21]) | ✔️ 3.1 ([リリース ノート][release-notes-31]) | ✔️ 5.0 ([リリース ノート][release-notes-50]) |
| macOS 10.13 "High Sierra" | ✔️ 2.1 ([リリース ノート][release-notes-21]) | ✔️ 3.1 ([リリース ノート][release-notes-31]) | ✔️ 5.0 ([リリース ノート][release-notes-50]) |
| macOS 10.12 "Sierra"      | ✔️ 2.1 ([リリース ノート][release-notes-21]) | ❌ 3.1 ([リリース ノート][release-notes-31]) | ❌ 5.0 ([リリース ノート][release-notes-50]) |

## <a name="unsupported-releases"></a>サポートされていないリリース

次のバージョンの .NET は、❌ サポート対象外となりました。 これらのダウンロードは、まだ公開されています。

- 3.0 ([リリース ノート][release-notes-30])
- 2.2 ([リリース ノート][release-notes-22])
- 2.0 ([リリース ノート][release-notes-20])

## <a name="runtime-information"></a>ランタイムに関する情報

ランタイムは、.NET で作成されたアプリを実行するために使用されます。 アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。 ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。

macOS には、2 つの異なるランタイムをインストールできます。

- *ASP.NET Core ランタイム*\
  ASP.NET Core アプリを実行します。 .NET ランタイムが含まれます。

- *.NET ランタイム*\
  このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。 .NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" をインストールすることを強くお勧めします。

> [!div class="button"]
> [.NET ランタイムをダウンロードする](https://dotnet.microsoft.com/download/dotnet)

## <a name="sdk-information"></a>SDK に関する情報

SDK は、.NET アプリとライブラリを作成して公開するために使用されます。 SDK のインストールには、次の両方の[ランタイム](#runtime-information)が含まれます: ASP.NET Core と .NET。

## <a name="dependencies"></a>依存関係

.NET は、次の macOS のリリースでサポートされています。

> [!NOTE]
> `+` 記号は、最小バージョンを表します。

| .NET Core のバージョン | macOS                 | アーキテクチャ | 詳細情報    |
| ----------------- | --------------------- | --------------| --- |
| 5.0               | High Sierra (10.13+)  | X64 | [詳細情報](https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md) |
| 3.1               | High Sierra (10.13+)  | X64 | [詳細情報](https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | High Sierra (10.13+)  | X64 | [詳細情報](https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12+)       | X64 | [詳細情報](https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12+)       | X64 | [詳細情報](https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md) |

macOS Catalina (バージョン 10.15) 以降では、2019 年 6 月 1 日より後に作成され、Developer ID と共に配布されたすべてのソフトウェアは公証される必要があります。 この要件は、.NET ランタイム、.NET SDK、および .NET を使用して作成されたソフトウェアに適用されます。

.NET 5.0 と .NET Core 3.1、3.0、2.1 のランタイムおよび SDK のインストーラーは、2020 年 2 月 18 日から公証されています。 それより前にリリースされたバージョンは、公証されていません。 公証されていないアプリを実行すると、次のイメージのようなエラーが表示されます。

![macOS Catalina の公証に関するアラート](media/dependencies/macos-notarized-pkg-warning.png)

公証の強制が .NET (および .NET アプリ) に与える影響の詳細については、[macOS Catalina の公証への対応](macos-notarization-issues.md)に関するページを参照してください。

## <a name="libgdiplus"></a>libgdiplus

*System.Drawing.Common* アセンブリを使用する .NET アプリケーションの場合は、libgdiplus をインストールする必要があります。

libgdiplus を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。 *brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して libgdiplus をインストールします。

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a>インストーラーを使用してインストールする

macOS には、.NET 5.0 SDK のインストールに使用できるスタンドアロン インストーラーが用意されています。

- [x64 (64 ビット) CPU](https://dotnet.microsoft.com/download/dotnet/5.0)

## <a name="download-and-manually-install"></a>手動でダウンロードしてインストールする

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

.NET 用 macOS インストーラーの代わりに、SDK とランタイムをダウンロードして手動でインストールすることもできます。 手動インストールは、通常、継続的インテグレーション テストの一環として実行されます。 開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet)を使用することをお勧めします。

.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 まず、次のいずれかのサイトから SDK またはランタイムの **バイナリ** リリースをダウンロードします。

- ✔️ [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet/3.1)
- ✔️ [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet/2.1)
- [すべての .NET Core のダウンロード](https://dotnet.microsoft.com/download/dotnet)

次に、ダウンロードしたファイルを抽出し、`export` コマンドを使用して .NET で使用される変数を設定してから、.NET が PATH に含まれていることを確認します。

ランタイムを抽出し、.NET CLI コマンドをターミナルで使用できるようにするには、最初に .NET のバイナリ リリースをダウンロードします。 次に、ターミナルを開き、ファイルが保存されているディレクトリから次のコマンドを実行します。 アーカイブ ファイル名は、ダウンロードした内容によって異なる場合があります。

**次のコマンドを使用して、ダウンロードしたランタイムまたは SDK を抽出します。** 必ず `DOTNET_FILE` の値を実際のファイル名に変更してください。

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> 上記の `export` コマンドを使用すると、それを実行したターミナル セッションでのみ .NET CLI コマンドを使用できるようになります。
>
> シェル プロファイルを編集して、コマンドを永続的に追加することができます。 Linux ではさまざまなシェルを使用でき、それぞれに異なるプロファイルがあります。 次に例を示します。
>
> - **Bash シェル**: *~/.bash_profile*、 *~/.bashrc*
> - **Korn シェル**: *~/.kshrc* または *.profile*
> - **Z シェル**: *~/.zshrc* または *.zprofile*
>
> シェルの適切なソース ファイルを編集し、既存の `PATH` ステートメントの末尾に `:$HOME/dotnet` を追加します。 `PATH` ステートメントが含まれていない場合は、`export PATH=$PATH:$HOME/dotnet` を含む新しい行を追加します。
>
> また、ファイルの末尾に `export DOTNET_ROOT=$HOME/dotnet` を追加します。

この方法では、別々の場所に異なるバージョンをインストールして、どのアプリケーションにどれを使用するかを明示的に選択できます。

## <a name="install-with-visual-studio-for-mac"></a>Visual Studio for Mac を使用してインストールする

Visual Studio for Mac を使用し、 **.NET** ワークロードを選択すると、.NET SDK がインストールされます。 macOS で .NET の開発を始めるには、「[Visual Studio 2019 for Mac をインストールする](/visualstudio/mac/installation)」を参照してください。

| .NET SDK バージョン      | Visual Studio のバージョン                      |
| --------------------- | ------------------------------------------ |
| 5.0                   | Visual Studio 2019 for Mac バージョン 8.8 以降。 |
| 3.1                   | Visual Studio 2019 for Mac バージョン 8.4 以降。 |
| 2.1                   | Visual Studio 2019 for Mac バージョン 8.0 以降。 |

[![macOS Visual Studio 2019 for Mac と .NET ワークロード機能](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Visual Studio Code と共にインストールする

Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。 Visual Studio Code は、Windows、macOS、Linux で利用できます。

Visual Studio Code には、Visual Studio のような自動化された .NET インストーラーは付属していませんが、.NET のサポートを簡単に追加できます。

01. [Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。
01. [.NET SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet)。
01. [Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。

## <a name="install-with-bash-automation"></a>bash オートメーションを使用してインストールする

[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの自動化および管理者以外によるインストールに使用されます。 スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。

スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。 `current` スイッチを指定することで、特定のリリースを選択できます。 ランタイムをインストールするには、`runtime` スイッチを含めます。 それ以外の場合は、スクリプトによって [SDK](./windows.md) がインストールされます。

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> 前述のコマンドにより、互換性を最大限に高めるために ASP.NET Core ランタイムをインストールします。 ASP.NET Core ランタイムには、標準の .NET ランタイムも含まれています。

## <a name="docker"></a>Docker

コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。 同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。

.NET は Docker コンテナー内で実行できます。 公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET Core の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet/)で見つけられます。 各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。

Microsoft は、特定のシナリオに対応したイメージを用意しています。 たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。

Docker コンテナー内で .NET Core を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md)に関するページを参照してください。

## <a name="next-steps"></a>次の手順

- [.NET Core が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-macos)。
- [macOS Catalina の公証に対応する](macos-notarization-issues.md)。
- [チュートリアル: macOS での作業を始める](../tutorials/with-visual-studio-mac.md).
- [チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。
- [チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。

[release-notes-21]: https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/main/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md
