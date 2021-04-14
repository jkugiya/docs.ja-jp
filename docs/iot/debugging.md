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
# <a name="debug-net-apps-on-raspberry-pi"></a><span data-ttu-id="70401-103">Raspberry Pi で .NET アプリをデバッグする</span><span class="sxs-lookup"><span data-stu-id="70401-103">Debug .NET apps on Raspberry Pi</span></span>

<span data-ttu-id="70401-104">Raspberry Pi など、ARM ベースの IoT デバイスで実行されている .NET アプリをデバッグする場合は、独自の課題が発生します。</span><span class="sxs-lookup"><span data-stu-id="70401-104">Debugging .NET apps running on ARM-based IoT devices like Raspberry Pi presents a unique challenge.</span></span> <span data-ttu-id="70401-105">ARM デバイスで .NET アプリを開発することが可能です。</span><span class="sxs-lookup"><span data-stu-id="70401-105">It is possible to develop .NET apps on ARM devices.</span></span> <span data-ttu-id="70401-106">しかし、Visual Studio の外部で .NET アプリをデバッグするために必要な OmniSharp は、ARM デバイスと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="70401-106">However, OmniSharp, which is required for debugging .NET apps outside of Visual Studio, is not compatible with ARM devices.</span></span> <span data-ttu-id="70401-107">そのため、互換性のあるプラットフォームからリモートでアプリをデバッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="70401-107">As a result, apps must be debugged remotely from a compatible platform.</span></span>

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a><span data-ttu-id="70401-108">Visual Studio Code からのデバッグ (クロスプラットフォーム)</span><span class="sxs-lookup"><span data-stu-id="70401-108">Debug from Visual Studio Code (cross-platform)</span></span>

<span data-ttu-id="70401-109">Visual Studio Code から Raspberry Pi 上の .NET をデバッグするには、Raspberry Pi とプロジェクトの *launch.json* ファイルで、構成手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="70401-109">Debugging .NET on Raspberry Pi from Visual Studio Code requires configuration steps on the Raspberry Pi and in the project's *launch.json* file.</span></span>

### <a name="enable-ssh-on-the-raspberry-pi"></a><span data-ttu-id="70401-110">Raspberry Pi で SSH を有効にする</span><span class="sxs-lookup"><span data-stu-id="70401-110">Enable SSH on the Raspberry Pi</span></span>

<span data-ttu-id="70401-111">リモート デバッグには SSH が必要です。</span><span class="sxs-lookup"><span data-stu-id="70401-111">SSH is required for remote debugging.</span></span> <span data-ttu-id="70401-112">SSH を有効にするには、[Raspberry Pi のドキュメントの「*Enable SSH (SSH の有効化)* 」を参照してください](https://www.raspberrypi.org/documentation/remote-access/ssh/)。</span><span class="sxs-lookup"><span data-stu-id="70401-112">To enable SSH, [refer to *Enable SSH* in the Raspberry Pi documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/).</span></span>

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a><span data-ttu-id="70401-113">Raspberry Pi に Visual Studio リモート デバッガーをインストールする</span><span class="sxs-lookup"><span data-stu-id="70401-113">Install the Visual Studio Remote Debugger on the Raspberry Pi</span></span>

<span data-ttu-id="70401-114">Raspberry Pi 上の Bash コンソール内で (ローカルまたは SSH 経由で)、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="70401-114">Within a Bash console on the Raspberry Pi (either locally or via SSH), complete the following steps:</span></span>

1. <span data-ttu-id="70401-115">次のコマンドを実行して、Raspberry Pi に Visual Studio リモート デバッガーをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="70401-115">Execute the following command to download and install the Visual Studio Remote Debugger on the Raspberry Pi:</span></span>

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. <span data-ttu-id="70401-116">デバッガーは `root` として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70401-116">The debugger requires running as `root`.</span></span> <span data-ttu-id="70401-117">既定では、Raspberry Pi には `root` にパスワードがありません。</span><span class="sxs-lookup"><span data-stu-id="70401-117">By default, `root` has no password on Raspberry Pi.</span></span> <span data-ttu-id="70401-118">次のコマンドを実行し、プロンプトに従って、`root` のパスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="70401-118">Set a password for `root` by executing the following command and following the prompts.</span></span>

    ```bash
    sudo passwd root
    ```

1. <span data-ttu-id="70401-119">Visual Studio Code では、リモートでデバッグを行うために SSH プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="70401-119">Visual Studio Code uses the SSH protocol to debug remotely.</span></span> <span data-ttu-id="70401-120">セキュリティ上の理由から、既定では `root` による SSH 経由でのログオンは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="70401-120">For security purposes, `root` is not permitted to log on via SSH by default.</span></span> <span data-ttu-id="70401-121">`root` による SSH 経由でのログオンを可能にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="70401-121">To enable `root` to log on via SSH, complete the following steps:</span></span>

    1. <span data-ttu-id="70401-122">次のコマンドを実行して、[nano](https://www.nano-editor.org/docs.php) で */etc/ssh/sshd_config* を開きます。</span><span class="sxs-lookup"><span data-stu-id="70401-122">Execute the following command to open */etc/ssh/sshd_config* in [nano](https://www.nano-editor.org/docs.php).</span></span>

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <span data-ttu-id="70401-123"><kbd>Ctrl + W</kbd> キーを押して、「**PermitRootLogin**」を検索します。</span><span class="sxs-lookup"><span data-stu-id="70401-123">Press <kbd>Ctrl+W</kbd> and search for **PermitRootLogin**.</span></span>
    1. <span data-ttu-id="70401-124">必要に応じて、**PermitRootLogin** を含む行をコメント解除します。</span><span class="sxs-lookup"><span data-stu-id="70401-124">Uncomment the line with **PermitRootLogin** if needed.</span></span>
    1. <span data-ttu-id="70401-125">次のように行を変更します。</span><span class="sxs-lookup"><span data-stu-id="70401-125">Change the line to read as follows:</span></span>

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > <span data-ttu-id="70401-126">*/etc/ssh/sshd_config* に **PermitRootLogin** の行がない場合は、上に示した値を含む新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="70401-126">If there is no **PermitRootLogin** line in */etc/ssh/sshd_config*, add a new line with the value shown above.</span></span>

    1. <span data-ttu-id="70401-127"><kbd>Ctrl + X</kbd> キーを押して終了し、変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="70401-127">Press <kbd>Ctrl+X</kbd> to exit and save your chances.</span></span> <span data-ttu-id="70401-128">**[Save modified buffer?]\(変更したバッファーを保存しますか?\)** というメッセージが表示されたら、「<kbd>Y</kbd>」と入力して確認します。</span><span class="sxs-lookup"><span data-stu-id="70401-128">When prompted **Save modified buffer?**, press <kbd>Y</kbd> to confirm.</span></span> <span data-ttu-id="70401-129"><kbd>Enter</kbd> キーを押して、元のファイルの上書きを確認します。</span><span class="sxs-lookup"><span data-stu-id="70401-129">Press <kbd>Enter</kbd> to confirm overwriting the original file.</span></span>
    1. <span data-ttu-id="70401-130">次のコマンドを実行して、Raspberry Pi を再起動します。</span><span class="sxs-lookup"><span data-stu-id="70401-130">Reboot the Raspberry Pi by executing the following command:</span></span>

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a><span data-ttu-id="70401-131">Visual Studio Code で launch.json をセットアップする</span><span class="sxs-lookup"><span data-stu-id="70401-131">Setup launch.json in Visual Studio Code</span></span>

<span data-ttu-id="70401-132">プロジェクトの *launch.json* に起動構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="70401-132">Add a launch configuration to the project's *launch.json*.</span></span> <span data-ttu-id="70401-133">プロジェクトに *launch.json* ファイルがない場合は、 **[実行]** タブに切り替え、 **[create a launch.json file]\(launch.json ファイルの作成\)** を選択し、ダイアログで **[.NET]** または **[.NET Core]** を選択して追加します。</span><span class="sxs-lookup"><span data-stu-id="70401-133">If the project doesn't have a *launch.json* file, add one by switching to the **Run** tab, selecting **create a launch.json file**, and selecting **.NET** or **.NET Core** in the dialog.</span></span>

<span data-ttu-id="70401-134">*launch.json* の新しい構成は次のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="70401-134">The new configuration in *launch.json* should look similar to this:</span></span>

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

<span data-ttu-id="70401-135">次に注意してください。</span><span class="sxs-lookup"><span data-stu-id="70401-135">Notice the following:</span></span>

- <span data-ttu-id="70401-136">`program` は Pi 上の .NET ランタイムへのパスです。</span><span class="sxs-lookup"><span data-stu-id="70401-136">`program` is the path to the .NET runtime on the Pi.</span></span>
- <span data-ttu-id="70401-137">`args` は、Pi 上でデバッグするアセンブリへのパスです。</span><span class="sxs-lookup"><span data-stu-id="70401-137">`args` is the path to the assembly to debug on the Pi.</span></span>
- <span data-ttu-id="70401-138">`cwd` は、Pi 上でアプリを起動するときに使用する作業ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="70401-138">`cwd` is the working directory to use when launching the app on the Pi.</span></span>
- <span data-ttu-id="70401-139">`pipeProgram` は、ローカル コンピューター上の SSH クライアントへのパスです。</span><span class="sxs-lookup"><span data-stu-id="70401-139">`pipeProgram` is the path to an SSH client on the local machine.</span></span>
- <span data-ttu-id="70401-140">`pipeArgs` は、SSH クライアントに渡されるパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="70401-140">`pipeArgs` are the parameters to be passed to the SSH client.</span></span> <span data-ttu-id="70401-141">パスワード パラメーターを、`root` ユーザーと共に `<user>@<hostname>` の形式で指定してください。</span><span class="sxs-lookup"><span data-stu-id="70401-141">Be sure to specify the password parameter, as well as the `root` user in the format `<user>@<hostname>`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70401-142">上の例では、[PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH クライアントのコンポーネントである *plink* が使用されています。</span><span class="sxs-lookup"><span data-stu-id="70401-142">The above example uses *plink*, a component of the [PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH client.</span></span> <span data-ttu-id="70401-143">代わりに、最近のバージョンの Windows および Linux に含まれている [OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span> を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="70401-143">[OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span>, which is included in recent versions of Windows and Linux, may be used instead.</span></span> <span data-ttu-id="70401-144">ただし、OpenSSH では、コマンド ライン パラメーターとしてパスワードを送信することがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="70401-144">However, OpenSSH doesn't support sending passwords as a command-line parameter.</span></span> <span data-ttu-id="70401-145">OpenSSH を使用する場合は、[パスワードレス SSH アクセス用に Raspberry Pi を構成します](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md)。</span><span class="sxs-lookup"><span data-stu-id="70401-145">To use OpenSSH, [configure your Raspberry Pi for passwordless SSH access](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md).</span></span>

### <a name="deploy-the-app"></a><span data-ttu-id="70401-146">アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="70401-146">Deploy the app</span></span>

<span data-ttu-id="70401-147">「[Raspberry Pi に .NET アプリを展開する](deployment.md)」の説明に従って、アプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="70401-147">Deploy the app as described in [Deploy .NET apps to Raspberry Pi](deployment.md).</span></span> <span data-ttu-id="70401-148">配置パスは、*launch.json* 構成の `cwd` パラメーターに指定されているのと同じパスにしてください。</span><span class="sxs-lookup"><span data-stu-id="70401-148">Ensure the deployment path is the same path specified in the `cwd` parameter in the *launch.json* configuration.</span></span>

### <a name="launch-the-debugger"></a><span data-ttu-id="70401-149">デバッガーを起動します</span><span class="sxs-lookup"><span data-stu-id="70401-149">Launch the debugger</span></span>

<span data-ttu-id="70401-150">**[実行]** タブで、 **[.NET Core Launch (remote console)]\(.NET Core の起動 (リモート コンソール)\)** 構成を選択し、 **[デバッグの開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="70401-150">On the **Run** tab, select the **.NET Core Launch (remote console)** configuration and select **Start Debugging**.</span></span> <span data-ttu-id="70401-151">Raspberry Pi 上でアプリが起動します。</span><span class="sxs-lookup"><span data-stu-id="70401-151">The app launches on the Raspberry Pi.</span></span> <span data-ttu-id="70401-152">デバッガーを使用して、ブレークポイントの設定、ローカルの検査などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="70401-152">The debugger may be used to set breakpoints, inspect locals, and more.</span></span>

## <a name="references"></a><span data-ttu-id="70401-153">References</span><span class="sxs-lookup"><span data-stu-id="70401-153">References</span></span>

[<span data-ttu-id="70401-154">Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM (Windows 上の VS Code を使用して、ARM 上の .NET Core を使用した Raspberry Pi をリモート デバッグする)</span><span class="sxs-lookup"><span data-stu-id="70401-154">Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM</span></span>](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a><span data-ttu-id="70401-155">Windows 上の Visual Studio からデバッグする</span><span class="sxs-lookup"><span data-stu-id="70401-155">Debug from Visual Studio on Windows</span></span>

<span data-ttu-id="70401-156">Visual Studio では、リモート デバイス上の .NET アプリを SSH 経由でデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="70401-156">Visual Studio can debug .NET apps on remote devices via SSH.</span></span> <span data-ttu-id="70401-157">デバイス上で特殊な構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="70401-157">No specialized configuration is required on the device.</span></span> <span data-ttu-id="70401-158">Visual Studio を使用して .NET をリモートでデバッグする方法の詳細については、[SSH を使用した Linux 上の .NET のリモート デバッグ](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70401-158">For details on using Visual Studio to debug .NET remotely, see [Remote debug .NET on Linux using SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span></span>

::: zone-end
