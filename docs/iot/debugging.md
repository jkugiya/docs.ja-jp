---
title: Raspberry Pi で .NET アプリをデバッグする
description: Raspberry Pi と同様のデバイスで .NET アプリをデバッグする方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
zone_pivot_groups: ide-set-one
ms.openlocfilehash: 58858384c49a296e0b33d663f3ef930caf9cace6
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258066"
---
# <a name="debug-net-apps-on-raspberry-pi"></a>Raspberry Pi で .NET アプリをデバッグする

Raspberry Pi など、ARM ベースの IoT デバイスで実行されている .NET アプリのデバッグは、独自の課題をもたらします。 ARM デバイスで .NET アプリを開発することができます。 ただし、Visual Studio の外部で .NET アプリをデバッグするために必要な OmniSharp は、ARM デバイスと互換性がありません。 そのため、アプリは互換性のあるプラットフォームからリモートでデバッグする必要があります。

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a>Visual Studio Code からのデバッグ (クロスプラットフォーム)

Visual Studio Code から Raspberry Pi で .NET をデバッグするには、Raspberry Pi と、ファイルのプロジェクトの *launch.js* で構成手順が必要です。

### <a name="enable-ssh-on-the-raspberry-pi"></a>Raspberry Pi で SSH を有効にする

リモートデバッグには SSH が必要です。 SSH を有効にするには、 [Raspberry Pi のドキュメントで *Ssh を有効* にする方法を参照してください](https://www.raspberrypi.org/documentation/remote-access/ssh/)。

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a>Raspberry Pi に Visual Studio リモートデバッガーをインストールする

Raspberry Pi の Bash コンソール内 (ローカルまたは SSH 経由) で、次の手順を実行します。

1. 次のコマンドを実行して、Raspberry Pi に Visual Studio リモートデバッガーをダウンロードしてインストールします。

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. デバッガーはとして実行する必要があり `root` ます。 既定で `root` は、Raspberry Pi にパスワードがありません。 次のコマンドを実行し、プロンプトに従って、のパスワードを設定し `root` ます。

    ```bash
    sudo passwd root
    ```

1. Visual Studio Code は、SSH プロトコルを使用してリモートでデバッグします。 セキュリティ上の理由 `root` から、では、既定で SSH 経由でのログオンは許可されていません。 で SSH を使用してログオンできるようにするには `root` 、次の手順を実行します。

    1. [Nano](https://www.nano-editor.org/docs.php)で */etc/ssh/sshd_config* を開くには、次のコマンドを実行します。

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <kbd>Ctrl + W</kbd>キーを押し、 **PermitRootLogin** を検索します。
    1. 必要に応じて、 **PermitRootLogin** で行のコメントを解除します。
    1. 次のように、行を次のように変更します。

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > */Etc/ssh/sshd_config* に **PermitRootLogin** 行がない場合は、上に示した値を使用して新しい行を追加します。

    1. <kbd>Ctrl + X</kbd>キーを押して終了し、可能性を保存します。 プロンプトが表示されたら、[変更したバッファーを保存します **か?**] <kbd>をクリックし</kbd> て確認します。 Enter <kbd>キーを</kbd> 押して、元のファイルの上書きを確定します。
    1. 次のコマンドを実行して、Raspberry Pi を再起動します。

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a>Visual Studio Code での launch.jsのセットアップ

のプロジェクトの *launch.js* に起動構成を追加します。 プロジェクトにファイル *のlaunch.js* がない場合は、[ **実行** ] タブに切り替え、[ **ファイルに launch.jsを作成**] を選択し、ダイアログで [ **.net** ] または [ **.net Core** ] を選択して追加します。

*launch.js* の新しい構成は次のようになります。

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
- `pipeProgram` は、ローカルコンピューター上の SSH クライアントへのパスです。
- `pipeArgs` SSH クライアントに渡されるパラメーターです。 パスワードパラメーターと、の形式のユーザーを指定してください `root` `<user>@<hostname>` 。

> [!IMPORTANT]
> 上の例では、 [PuTTY](https://www.ssh.com/ssh/putty/) SSH クライアントのコンポーネントである *plink* を使用して <span class="docon docon-navigate-external x-hidden-focus"></span> います。 [](https://www.openssh.com/) <span class="docon docon-navigate-external x-hidden-focus"></span> 最近のバージョンの Windows および Linux に含まれる OpenSSH は、代わりに使用することができます。 ただし、OpenSSH は、コマンドラインパラメーターとしてのパスワードの送信をサポートしていません。 OpenSSH を使用するには、 [パスワードなし SSH アクセス用に Raspberry Pi を構成](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md)します。

### <a name="deploy-the-app"></a>アプリを配置する

「 [Raspberry Pi への .net アプリのデプロイ](deployment.md)」の説明に従って、アプリをデプロイします。 配置パスが、 `cwd` 構成 *のlaunch.js* のパラメーターに指定されているパスと同じであることを確認してください。

### <a name="launch-the-debugger"></a>デバッガーを起動します

[ **実行** ] タブで、[ **.net Core Launch (リモートコンソール)** の構成] を選択し、[ **デバッグの開始**] を選択します。 アプリは Raspberry Pi で起動します。 デバッガーを使用して、ブレークポイントの設定、ローカルの検査などを行うことができます。

## <a name="references"></a>関連項目

[ARM で .NET Core を使用して Raspberry Pi に対して Windows で VS Code を使用したリモートデバッグ](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a>Windows の Visual Studio からデバッグする

Visual Studio では、リモートデバイス上の .NET アプリを SSH 経由でデバッグできます。 デバイスに特別な構成は必要ありません。 Visual Studio を使用して .NET をリモートでデバッグする方法の詳細については、「 [SSH を使用した Linux での .net のリモートデバッグ](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019)」を参照してください。

::: zone-end
