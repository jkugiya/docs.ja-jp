---
title: Raspberry Pi で .NET アプリをデバッグする
description: Raspberry Pi や同様のデバイスで .NET アプリをデバッグする方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
zone_pivot_groups: ide-set-one
ms.openlocfilehash: 58858384c49a296e0b33d663f3ef930caf9cace6
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "102258066"
---
# <a name="debug-net-apps-on-raspberry-pi"></a>Raspberry Pi で .NET アプリをデバッグする

Raspberry Pi など、ARM ベースの IoT デバイスで実行されている .NET アプリをデバッグする場合は、独自の課題が発生します。 ARM デバイスで .NET アプリを開発することが可能です。 しかし、Visual Studio の外部で .NET アプリをデバッグするために必要な OmniSharp は、ARM デバイスと互換性がありません。 そのため、互換性のあるプラットフォームからリモートでアプリをデバッグする必要があります。

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a>Visual Studio Code からのデバッグ (クロスプラットフォーム)

Visual Studio Code から Raspberry Pi 上の .NET をデバッグするには、Raspberry Pi とプロジェクトの *launch.json* ファイルで、構成手順が必要です。

### <a name="enable-ssh-on-the-raspberry-pi"></a>Raspberry Pi で SSH を有効にする

リモート デバッグには SSH が必要です。 SSH を有効にするには、[Raspberry Pi のドキュメントの「*Enable SSH (SSH の有効化)* 」を参照してください](https://www.raspberrypi.org/documentation/remote-access/ssh/)。

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a>Raspberry Pi に Visual Studio リモート デバッガーをインストールする

Raspberry Pi 上の Bash コンソール内で (ローカルまたは SSH 経由で)、次の手順を実行します。

1. 次のコマンドを実行して、Raspberry Pi に Visual Studio リモート デバッガーをダウンロードしてインストールします。

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. デバッガーは `root` として実行する必要があります。 既定では、Raspberry Pi には `root` にパスワードがありません。 次のコマンドを実行し、プロンプトに従って、`root` のパスワードを設定します。

    ```bash
    sudo passwd root
    ```

1. Visual Studio Code では、リモートでデバッグを行うために SSH プロトコルが使用されます。 セキュリティ上の理由から、既定では `root` による SSH 経由でのログオンは許可されていません。 `root` による SSH 経由でのログオンを可能にするには、次の手順を実行します。

    1. 次のコマンドを実行して、[nano](https://www.nano-editor.org/docs.php) で */etc/ssh/sshd_config* を開きます。

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <kbd>Ctrl + W</kbd> キーを押して、「**PermitRootLogin**」を検索します。
    1. 必要に応じて、**PermitRootLogin** を含む行をコメント解除します。
    1. 次のように行を変更します。

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > */etc/ssh/sshd_config* に **PermitRootLogin** の行がない場合は、上に示した値を含む新しい行を追加します。

    1. <kbd>Ctrl + X</kbd> キーを押して終了し、変更内容を保存します。 **[Save modified buffer?]\(変更したバッファーを保存しますか?\)** というメッセージが表示されたら、「<kbd>Y</kbd>」と入力して確認します。 <kbd>Enter</kbd> キーを押して、元のファイルの上書きを確認します。
    1. 次のコマンドを実行して、Raspberry Pi を再起動します。

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a>Visual Studio Code で launch.json をセットアップする

プロジェクトの *launch.json* に起動構成を追加します。 プロジェクトに *launch.json* ファイルがない場合は、 **[実行]** タブに切り替え、 **[create a launch.json file]\(launch.json ファイルの作成\)** を選択し、ダイアログで **[.NET]** または **[.NET Core]** を選択して追加します。

*launch.json* の新しい構成は次のようになるはずです。

```json
"configurations": [
    {
        "name": ".NET Core Launch (remote console)",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "/home/pi/.dotnet/dotnet",
        "args": ["/home/pi/sample/Sample.dll"],
        "cwd": "/home/pi/sample",
        "stopAtEntry": false,
        "console": "internalConsole",
        "pipeTransport": {
            "pipeCwd": "${workspaceFolder}",
            "pipeProgram": "C:\\Program Files\\PuTTY\\PLINK.EXE",
            "pipeArgs": [
                "-pw",
                "P@ssw0rd",
                "root@raspberrypi"
            ],
            "debuggerPath": "/home/pi/vsdbg/vsdbg"
        }
    },
```

次に注意してください。

- `program` は Pi 上の .NET ランタイムへのパスです。
- `args` は、Pi 上でデバッグするアセンブリへのパスです。
- `cwd` は、Pi 上でアプリを起動するときに使用する作業ディレクトリです。
- `pipeProgram` は、ローカル コンピューター上の SSH クライアントへのパスです。
- `pipeArgs` は、SSH クライアントに渡されるパラメーターです。 パスワード パラメーターを、`root` ユーザーと共に `<user>@<hostname>` の形式で指定してください。

> [!IMPORTANT]
> 上の例では、[PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH クライアントのコンポーネントである *plink* が使用されています。 代わりに、最近のバージョンの Windows および Linux に含まれている [OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span> を使用することもできます。 ただし、OpenSSH では、コマンド ライン パラメーターとしてパスワードを送信することがサポートされていません。 OpenSSH を使用する場合は、[パスワードレス SSH アクセス用に Raspberry Pi を構成します](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md)。

### <a name="deploy-the-app"></a>アプリケーションのデプロイ

「[Raspberry Pi に .NET アプリを展開する](deployment.md)」の説明に従って、アプリを展開します。 配置パスは、*launch.json* 構成の `cwd` パラメーターに指定されているのと同じパスにしてください。

### <a name="launch-the-debugger"></a>デバッガーを起動します

**[実行]** タブで、 **[.NET Core Launch (remote console)]\(.NET Core の起動 (リモート コンソール)\)** 構成を選択し、 **[デバッグの開始]** を選択します。 Raspberry Pi 上でアプリが起動します。 デバッガーを使用して、ブレークポイントの設定、ローカルの検査などを行うことができます。

## <a name="references"></a>References

[Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM (Windows 上の VS Code を使用して、ARM 上の .NET Core を使用した Raspberry Pi をリモート デバッグする)](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a>Windows 上の Visual Studio からデバッグする

Visual Studio では、リモート デバイス上の .NET アプリを SSH 経由でデバッグできます。 デバイス上で特殊な構成は必要ありません。 Visual Studio を使用して .NET をリモートでデバッグする方法の詳細については、[SSH を使用した Linux 上の .NET のリモート デバッグ](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019)に関する記事を参照してください。

::: zone-end
