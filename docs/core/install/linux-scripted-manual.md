---
title: 手動で Linux に .NET をインストールする - .NET
description: Linux でパッケージ マネージャーを使用せずに .NET SDK と .NET ランタイムをインストールする方法を示します。 インストール スクリプトを使用するか、手動でバイナリを抽出します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 414246e472c3d58a6768311bd7a4635100f3b618
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105181"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a>手動で .NET SDK または .NET ランタイムをインストールする

.NET は Linux でサポートされており、この記事では、インストール スクリプトを使用して、またはバイナリを抽出して、Linux に .NET をインストールする方法について説明します。 組み込みパッケージ マネージャーがサポートされているディストリビューションの一覧については、「[Linux に .NET をインストールする](linux.md)」を参照してください。

Snap を使用して .NET をインストールすることもできます。 詳細については、「[Snap を使用して .NET SDK または .NET ランタイムをインストールする](linux-snap.md)」を参照してください。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a>.NET のリリース

次の表は、.NET (および .NET Core) のリリースの一覧です。

| ✔️ Supported | ❌ サポートされていない |
|-------------|---------------|
| 5.0         | 3.0           |
| 3.1 (LTS)   | 2.2           |
| 2.1 (LTS)   | 2.0           |
|             | 1.1           |
|             | 1.0           |

.NET リリースのライフ サイクルの詳細については、「[.NET Core と .NET 5 のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」を参照してください。

## <a name="dependencies"></a>依存関係

.NET をインストールするときに、特定の依存関係がインストールされない可能性があります ([手動インストール](#manual-install)のときなど)。 次の一覧に、Microsoft によってサポートされていて、インストールが必要な可能性のある依存関係がある Linux ディストリビューションの詳細を示します。 詳細については、ディストリビューションのページを確認してください。

- [Alpine](linux-alpine.md#dependencies)
- [Debian](linux-debian.md#dependencies)
- [CentOS](linux-centos.md#dependencies)
- [Fedora](linux-fedora.md#dependencies)
- [RHEL](linux-rhel.md#dependencies)
- [SLES](linux-sles.md#dependencies)
- [Ubuntu](linux-ubuntu.md#dependencies)

依存関係に関する一般的な情報については、「[自己完結型 Linux アプリケーション](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」を参照してください。

### <a name="rpm-dependencies"></a>RPM の依存関係

お使いのディストリビューションが前の一覧になく、RPM ベースの場合は、次の依存関係が必要になることがあります。

- krb5-libs
- libicu
- openssl-libs

ターゲット ランタイム環境の OpenSSL バージョンが 1.1 以降である場合は、**compat-openssl10** をインストールする必要があります。

### <a name="deb-dependencies"></a>DEB の依存関係

お使いのディストリビューションが前の一覧になく、Debian ベースの場合は、次の依存関係が必要になることがあります。

- libc6
- libgcc1
- libgssapi-krb5-2
- libicu67
- libssl1.1
- libstdc++6
- zlib1g

### <a name="common-dependencies"></a>共通の依存関係

*System.Drawing.Common* アセンブリを使用する .NET アプリの場合は、次の依存関係も必要です。

- [libgdiplus (バージョン 6.0.1 以降)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > 最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。 詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。

## <a name="scripted-install"></a>スクリプトでのインストール

[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、**SDK** および **ランタイム** のインストールの自動化および管理者以外によるインストールのために使用されます。 このスクリプトは <https://dot.net/v1/dotnet-install.sh> からダウンロードできます。

スクリプトでは、最新の SDK の[長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) が既定でインストールされます。 (LTS) バージョンではない場合がある現在のリリースをインストールするには、`-c Current` パラメーターを使用します。

```bash
./dotnet-install.sh -c Current
```

SDK の代わりに .NET ランタイムをインストールするには、`--runtime` パラメーターを使用します。

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

特定のバージョンをインストールするには、`-c` パラメーターを変更して特定のバージョンを指定します。 次のコマンドでは、.NET SDK 5.0 がインストールされます。

```bash
./dotnet-install.sh -c 5.0
```

詳細については、「[dotnet-install スクリプト リファレンス](../tools/dotnet-install-script.md)」をご覧ください。

## <a name="manual-install"></a>手動インストール

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

パッケージ マネージャーの代わりに、SDK とランタイムをダウンロードして手動でインストールすることもできます。 手動インストールは、継続的インテグレーション テストの一環として、またはサポートされていない Linux ディストリビューションで、よく使用されます。 開発者またはユーザーの場合は、パッケージ マネージャーを使用することをお勧めします。

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

## <a name="next-steps"></a>次のステップ

- [.NET CLI のタブ補完を有効にする方法](../tools/enable-tab-autocomplete.md)
- [チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する](../tutorials/with-visual-studio-code.md)
