---
title: dotnet tool install コマンド
description: dotnet tool install コマンドを実行すると、指定した .NET ツールがお使いのコンピューターにインストールされます。
ms.date: 02/14/2020
ms.openlocfilehash: b04e7fd24edce5d5da67cdd83fbea797118689b4
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206482"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet tool install` - 指定した [.NET ツール](global-tools.md)をお使いのコンピューターにインストールします。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>説明

`dotnet tool install` コマンドを実行すると、.NET ツールがお使いのコンピューターにインストールされます。 コマンドを使用するには、次のいずれかのインストール オプションを指定します。

* 既定の場所にグローバル ツールをインストールするには、`--global` オプションを使用します。
* カスタムの場所にグローバル ツールをインストールするには、`--tool-path` オプションを使用します。
* ローカル ツールをインストールするには、`--global` および `--tool-path` オプションを省略します。

**ローカル ツールは .NET Core SDK 3.0 以降で使用できます。**

グローバル ツールは、`-g` または `--global` オプションを指定した場合、既定で次のディレクトリにインストールされます。

| OS          | パス                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

ローカル ツールは、現在のディレクトリ下にある *.config* ディレクトリ内の *dotnet-tools.json* ファイルに追加されます。 マニフェスト ファイルがまだ存在しない場合は、次のコマンドを実行して作成します。

```dotnetcli
dotnet new tool-manifest
```

詳細については、「[ローカル ツールのインストール](global-tools.md#install-a-local-tool)」を参照してください。

## <a name="arguments"></a>引数

- **`PACKAGE_NAME`**

  インストールする .NET ツールが格納されている NuGet パッケージの名前または ID。

## <a name="options"></a>オプション

- **`--add-source <SOURCE>`**

  インストール時に使用するために追加の NuGet パッケージ ソースを追加します。 フィードは、何らかの順番ではなく、並列でアクセスされます。 同じパッケージとバージョンが複数のフィードに存在する場合、最も速いフィードが優先されます。 詳細については、「[NuGet パッケージのインストールのしくみ](/nuget/concepts/package-installation-process)」を参照してください。

- **`--configfile <FILE>`**

  使用する NuGet 構成 (*nuget.config*) ファイル。

- **`--framework <FRAMEWORK>`**

  ツールをインストールする[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。 既定では、.NET SDK によって、最適なターゲット フレームワークの選択が試行されます。

- **`-g|--global`**

  ユーザー全体のインストールを指定します。 `--tool-path` オプションと組み合わせることはできません。 `--global` と `--tool-path` の両方を省略すると、ローカル ツールのインストールが指定されます。

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

- **`--tool-path <PATH>`**

  グローバル ツールをインストールする場所を指定します。 PATH は絶対パスでも相対パスでもかまいません。 PATH が存在しない場合、コマンドではパスの作成を試みます。 `--global` と `--tool-path` の両方を省略すると、ローカル ツールのインストールが指定されます。

- **`-v|--verbosity <LEVEL>`**

  コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

- **`--version <VERSION_NUMBER>`**

  インストールするツールのバージョン。 既定では、安定した最新バージョンのパッケージがインストールされます。 このオプションを使用して、プレビューまたは古いバージョンのツールをインストールします。

## <a name="examples"></a>使用例

- **`dotnet tool install -g dotnetsay`**

  既定の場所に [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  特定の Windows ディレクトリに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  特定の Linux/macOS ディレクトリに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  バージョン 2.0.0 の [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をグローバル ツールとしてインストールします。

- **`dotnet tool install dotnetsay`**

  現在のディレクトリに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) をローカル ツールとしてインストールします。

## <a name="see-also"></a>関連項目

- [.NET ツール](global-tools.md)
- [チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する](global-tools-how-to-use.md)
- [チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する](local-tools-how-to-use.md)
