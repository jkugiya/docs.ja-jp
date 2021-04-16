---
title: Raspberry Pi に .NET アプリを展開する
description: Raspberry Pi に .NET アプリを展開する方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594127"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a>Raspberry Pi に .NET アプリを展開する

Raspberry Pi への .NET アプリの展開は、他のプラットフォームと同じです。 アプリは、*自己完結型* または *フレームワーク依存* の配置モードとして実行できます。 それぞれの戦略に利点があります。 詳細については、「[.NET アプリケーションの発行の概要](../core/deploying/index.md)」を参照してください。

## <a name="deploying-a-framework-dependent-app"></a>フレームワーク依存アプリの展開

アプリをフレームワーク依存アプリとして展開するには、次の手順を実行します。

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. [dotnet-install スクリプト](../core/tools/dotnet-install-script.md)を使用して、Raspberry Pi に .NET をインストールします。 Raspberry Pi (ローカルまたは SSH) で Bash プロンプトから次の手順を実行します。
    1. .NET をインストールするには次のコマンドを実行します。

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > これにより、最新バージョンがインストールされます。 特定のバージョンが必要な場合は、末尾に `--version <VERSION>` を追加します。ここで、`<VERSION>` は特定のビルド バージョンです。

    1. パスの解決を簡単にするには、次のコマンドを使用して、`DOTNET_ROOT` 環境変数を追加し、 *.dotnet* ディレクトリを `$PATH` に追加します。

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. 次のコマンドを使用して、.NET インストールを確認します。

        ```dotnetcli
        dotnet --version
        ```

        表示されているバージョンが、インストールしたバージョンと一致していることを確認します。

1. 開発環境に応じて、次のようにして、開発用コンピューターにアプリを発行します。
    - **Visual Studio** を使用している場合は、[アプリをローカル フォルダーに配置します](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)。 発行する前に、発行プロファイルの概要で **[編集]** を選択し、 **[設定]** タブを選択します。 **[配置モード]** が *[フレームワーク依存]* に、 **[ターゲット ランタイム]** が *[ポータブル]* に設定されていることを確認します。
    - **.NET CLI** を使用している場合は、[dotnet publish](../core/tools/dotnet-publish.md) コマンドを使用します。 追加の引数は必要ありません。

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Raspberry Pi (ローカルまたは SSH) の Bash プロンプトから、アプリを実行します。 これを行うには、展開フォルダーを現在のディレクトリに設定し、次のコマンドを実行します (*HelloWorld.dll* はアプリのエントリ ポイントです)。

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a>自己完結型アプリの展開

自己完結型アプリとしてアプリを展開するには、次の手順を実行します。

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. 開発環境に応じて、次のようにして、開発用コンピューターにアプリを発行します。
    - **Visual Studio** を使用している場合は、[アプリをローカル フォルダーに配置します](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)。 発行する前に、発行プロファイルの概要で **[編集]** を選択し、 **[設定]** タブを選択します。 **[配置モード]** が *[自己完結]* に、 **[ターゲット ランタイム]** が *[linux-arm]* に設定されていることを確認します。
    - **.NET CLI** を使用している場合は、`-r linux-arm` 引数を指定して [dotnet publish](../core/tools/dotnet-publish.md) コマンドを使用します。

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Raspberry Pi (ローカルまたは SSH) の Bash プロンプトから、アプリを実行します。 これを行うには、現在のディレクトリを配置場所に設定し、次の手順を実行します。
    1. 実行可能ファイルの *実行* アクセス許可を指定します (`HelloWorld` は実行可能ファイルの名前です)。

        ```bash
        chmod +x HelloWorld
        ```

    1. 実行可能ファイルを実行します。

        ```bash
        ./HelloWorld
        ```
