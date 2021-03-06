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
# <a name="debug-net-apps-on-raspberry-pi"></a><span data-ttu-id="18648-103">Raspberry Pi で .NET アプリをデバッグする</span><span class="sxs-lookup"><span data-stu-id="18648-103">Debug .NET apps on Raspberry Pi</span></span>

<span data-ttu-id="18648-104">Raspberry Pi など、ARM ベースの IoT デバイスで実行されている .NET アプリのデバッグは、独自の課題をもたらします。</span><span class="sxs-lookup"><span data-stu-id="18648-104">Debugging .NET apps running on ARM-based IoT devices like Raspberry Pi presents a unique challenge.</span></span> <span data-ttu-id="18648-105">ARM デバイスで .NET アプリを開発することができます。</span><span class="sxs-lookup"><span data-stu-id="18648-105">It is possible to develop .NET apps on ARM devices.</span></span> <span data-ttu-id="18648-106">ただし、Visual Studio の外部で .NET アプリをデバッグするために必要な OmniSharp は、ARM デバイスと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="18648-106">However, OmniSharp, which is required for debugging .NET apps outside of Visual Studio, is not compatible with ARM devices.</span></span> <span data-ttu-id="18648-107">そのため、アプリは互換性のあるプラットフォームからリモートでデバッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="18648-107">As a result, apps must be debugged remotely from a compatible platform.</span></span>

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a><span data-ttu-id="18648-108">Visual Studio Code からのデバッグ (クロスプラットフォーム)</span><span class="sxs-lookup"><span data-stu-id="18648-108">Debug from Visual Studio Code (cross-platform)</span></span>

<span data-ttu-id="18648-109">Visual Studio Code から Raspberry Pi で .NET をデバッグするには、Raspberry Pi と、ファイルのプロジェクトの *launch.js* で構成手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="18648-109">Debugging .NET on Raspberry Pi from Visual Studio Code requires configuration steps on the Raspberry Pi and in the project's *launch.json* file.</span></span>

### <a name="enable-ssh-on-the-raspberry-pi"></a><span data-ttu-id="18648-110">Raspberry Pi で SSH を有効にする</span><span class="sxs-lookup"><span data-stu-id="18648-110">Enable SSH on the Raspberry Pi</span></span>

<span data-ttu-id="18648-111">リモートデバッグには SSH が必要です。</span><span class="sxs-lookup"><span data-stu-id="18648-111">SSH is required for remote debugging.</span></span> <span data-ttu-id="18648-112">SSH を有効にするには、 [Raspberry Pi のドキュメントで *Ssh を有効* にする方法を参照してください](https://www.raspberrypi.org/documentation/remote-access/ssh/)。</span><span class="sxs-lookup"><span data-stu-id="18648-112">To enable SSH, [refer to *Enable SSH* in the Raspberry Pi documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/).</span></span>

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a><span data-ttu-id="18648-113">Raspberry Pi に Visual Studio リモートデバッガーをインストールする</span><span class="sxs-lookup"><span data-stu-id="18648-113">Install the Visual Studio Remote Debugger on the Raspberry Pi</span></span>

<span data-ttu-id="18648-114">Raspberry Pi の Bash コンソール内 (ローカルまたは SSH 経由) で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="18648-114">Within a Bash console on the Raspberry Pi (either locally or via SSH), complete the following steps:</span></span>

1. <span data-ttu-id="18648-115">次のコマンドを実行して、Raspberry Pi に Visual Studio リモートデバッガーをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="18648-115">Execute the following command to download and install the Visual Studio Remote Debugger on the Raspberry Pi:</span></span>

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. <span data-ttu-id="18648-116">デバッガーはとして実行する必要があり `root` ます。</span><span class="sxs-lookup"><span data-stu-id="18648-116">The debugger requires running as `root`.</span></span> <span data-ttu-id="18648-117">既定で `root` は、Raspberry Pi にパスワードがありません。</span><span class="sxs-lookup"><span data-stu-id="18648-117">By default, `root` has no password on Raspberry Pi.</span></span> <span data-ttu-id="18648-118">次のコマンドを実行し、プロンプトに従って、のパスワードを設定し `root` ます。</span><span class="sxs-lookup"><span data-stu-id="18648-118">Set a password for `root` by executing the following command and following the prompts.</span></span>

    ```bash
    sudo passwd root
    ```

1. <span data-ttu-id="18648-119">Visual Studio Code は、SSH プロトコルを使用してリモートでデバッグします。</span><span class="sxs-lookup"><span data-stu-id="18648-119">Visual Studio Code uses the SSH protocol to debug remotely.</span></span> <span data-ttu-id="18648-120">セキュリティ上の理由 `root` から、では、既定で SSH 経由でのログオンは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="18648-120">For security purposes, `root` is not permitted to log on via SSH by default.</span></span> <span data-ttu-id="18648-121">で SSH を使用してログオンできるようにするには `root` 、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="18648-121">To enable `root` to log on via SSH, complete the following steps:</span></span>

    1. <span data-ttu-id="18648-122">[Nano](https://www.nano-editor.org/docs.php)で */etc/ssh/sshd_config* を開くには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="18648-122">Execute the following command to open */etc/ssh/sshd_config* in [nano](https://www.nano-editor.org/docs.php).</span></span>

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <span data-ttu-id="18648-123"><kbd>Ctrl + W</kbd>キーを押し、 **PermitRootLogin** を検索します。</span><span class="sxs-lookup"><span data-stu-id="18648-123">Press <kbd>Ctrl+W</kbd> and search for **PermitRootLogin**.</span></span>
    1. <span data-ttu-id="18648-124">必要に応じて、 **PermitRootLogin** で行のコメントを解除します。</span><span class="sxs-lookup"><span data-stu-id="18648-124">Uncomment the line with **PermitRootLogin** if needed.</span></span>
    1. <span data-ttu-id="18648-125">次のように、行を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="18648-125">Change the line to read as follows:</span></span>

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > <span data-ttu-id="18648-126">*/Etc/ssh/sshd_config* に **PermitRootLogin** 行がない場合は、上に示した値を使用して新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="18648-126">If there is no **PermitRootLogin** line in */etc/ssh/sshd_config*, add a new line with the value shown above.</span></span>

    1. <span data-ttu-id="18648-127"><kbd>Ctrl + X</kbd>キーを押して終了し、可能性を保存します。</span><span class="sxs-lookup"><span data-stu-id="18648-127">Press <kbd>Ctrl+X</kbd> to exit and save your chances.</span></span> <span data-ttu-id="18648-128">プロンプトが表示されたら、[変更したバッファーを保存します **か?**] <kbd>をクリックし</kbd> て確認します。</span><span class="sxs-lookup"><span data-stu-id="18648-128">When prompted **Save modified buffer?**, press <kbd>Y</kbd> to confirm.</span></span> <span data-ttu-id="18648-129">Enter <kbd>キーを</kbd> 押して、元のファイルの上書きを確定します。</span><span class="sxs-lookup"><span data-stu-id="18648-129">Press <kbd>Enter</kbd> to confirm overwriting the original file.</span></span>
    1. <span data-ttu-id="18648-130">次のコマンドを実行して、Raspberry Pi を再起動します。</span><span class="sxs-lookup"><span data-stu-id="18648-130">Reboot the Raspberry Pi by executing the following command:</span></span>

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a><span data-ttu-id="18648-131">Visual Studio Code での launch.jsのセットアップ</span><span class="sxs-lookup"><span data-stu-id="18648-131">Setup launch.json in Visual Studio Code</span></span>

<span data-ttu-id="18648-132">のプロジェクトの *launch.js* に起動構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="18648-132">Add a launch configuration to the project's *launch.json*.</span></span> <span data-ttu-id="18648-133">プロジェクトにファイル *のlaunch.js* がない場合は、[ **実行** ] タブに切り替え、[ **ファイルに launch.jsを作成**] を選択し、ダイアログで [ **.net** ] または [ **.net Core** ] を選択して追加します。</span><span class="sxs-lookup"><span data-stu-id="18648-133">If the project doesn't have a *launch.json* file, add one by switching to the **Run** tab, selecting **create a launch.json file**, and selecting **.NET** or **.NET Core** in the dialog.</span></span>

<span data-ttu-id="18648-134">*launch.js* の新しい構成は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18648-134">The new configuration in *launch.json* should look similar to this:</span></span>

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

<span data-ttu-id="18648-135">次に注意してください。</span><span class="sxs-lookup"><span data-stu-id="18648-135">Notice the following:</span></span>

- <span data-ttu-id="18648-136">`program` は Pi 上の .NET ランタイムへのパスです。</span><span class="sxs-lookup"><span data-stu-id="18648-136">`program` is the path to the .NET runtime on the Pi.</span></span>
- <span data-ttu-id="18648-137">`args` は、Pi 上でデバッグするアセンブリへのパスです。</span><span class="sxs-lookup"><span data-stu-id="18648-137">`args` is the path to the assembly to debug on the Pi.</span></span>
- <span data-ttu-id="18648-138">`cwd` は、Pi 上でアプリを起動するときに使用する作業ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="18648-138">`cwd` is the working directory to use when launching the app on the Pi.</span></span>
- <span data-ttu-id="18648-139">`pipeProgram` は、ローカルコンピューター上の SSH クライアントへのパスです。</span><span class="sxs-lookup"><span data-stu-id="18648-139">`pipeProgram` is the path to an SSH client on the local machine.</span></span>
- <span data-ttu-id="18648-140">`pipeArgs` SSH クライアントに渡されるパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="18648-140">`pipeArgs` are the parameters to be passed to the SSH client.</span></span> <span data-ttu-id="18648-141">パスワードパラメーターと、の形式のユーザーを指定してください `root` `<user>@<hostname>` 。</span><span class="sxs-lookup"><span data-stu-id="18648-141">Be sure to specify the password parameter, as well as the `root` user in the format `<user>@<hostname>`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18648-142">上の例では、 [PuTTY](https://www.ssh.com/ssh/putty/) SSH クライアントのコンポーネントである *plink* を使用して <span class="docon docon-navigate-external x-hidden-focus"></span> います。</span><span class="sxs-lookup"><span data-stu-id="18648-142">The above example uses *plink*, a component of the [PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH client.</span></span> <span data-ttu-id="18648-143">[](https://www.openssh.com/) <span class="docon docon-navigate-external x-hidden-focus"></span> 最近のバージョンの Windows および Linux に含まれる OpenSSH は、代わりに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="18648-143">[OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span>, which is included in recent versions of Windows and Linux, may be used instead.</span></span> <span data-ttu-id="18648-144">ただし、OpenSSH は、コマンドラインパラメーターとしてのパスワードの送信をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="18648-144">However, OpenSSH doesn't support sending passwords as a command-line parameter.</span></span> <span data-ttu-id="18648-145">OpenSSH を使用するには、 [パスワードなし SSH アクセス用に Raspberry Pi を構成](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md)します。</span><span class="sxs-lookup"><span data-stu-id="18648-145">To use OpenSSH, [configure your Raspberry Pi for passwordless SSH access](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md).</span></span>

### <a name="deploy-the-app"></a><span data-ttu-id="18648-146">アプリを配置する</span><span class="sxs-lookup"><span data-stu-id="18648-146">Deploy the app</span></span>

<span data-ttu-id="18648-147">「 [Raspberry Pi への .net アプリのデプロイ](deployment.md)」の説明に従って、アプリをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="18648-147">Deploy the app as described in [Deploy .NET apps to Raspberry Pi](deployment.md).</span></span> <span data-ttu-id="18648-148">配置パスが、 `cwd` 構成 *のlaunch.js* のパラメーターに指定されているパスと同じであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18648-148">Ensure the deployment path is the same path specified in the `cwd` parameter in the *launch.json* configuration.</span></span>

### <a name="launch-the-debugger"></a><span data-ttu-id="18648-149">デバッガーを起動します</span><span class="sxs-lookup"><span data-stu-id="18648-149">Launch the debugger</span></span>

<span data-ttu-id="18648-150">[ **実行** ] タブで、[ **.net Core Launch (リモートコンソール)** の構成] を選択し、[ **デバッグの開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18648-150">On the **Run** tab, select the **.NET Core Launch (remote console)** configuration and select **Start Debugging**.</span></span> <span data-ttu-id="18648-151">アプリは Raspberry Pi で起動します。</span><span class="sxs-lookup"><span data-stu-id="18648-151">The app launches on the Raspberry Pi.</span></span> <span data-ttu-id="18648-152">デバッガーを使用して、ブレークポイントの設定、ローカルの検査などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="18648-152">The debugger may be used to set breakpoints, inspect locals, and more.</span></span>

## <a name="references"></a><span data-ttu-id="18648-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="18648-153">References</span></span>

[<span data-ttu-id="18648-154">ARM で .NET Core を使用して Raspberry Pi に対して Windows で VS Code を使用したリモートデバッグ</span><span class="sxs-lookup"><span data-stu-id="18648-154">Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM</span></span>](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a><span data-ttu-id="18648-155">Windows の Visual Studio からデバッグする</span><span class="sxs-lookup"><span data-stu-id="18648-155">Debug from Visual Studio on Windows</span></span>

<span data-ttu-id="18648-156">Visual Studio では、リモートデバイス上の .NET アプリを SSH 経由でデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="18648-156">Visual Studio can debug .NET apps on remote devices via SSH.</span></span> <span data-ttu-id="18648-157">デバイスに特別な構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="18648-157">No specialized configuration is required on the device.</span></span> <span data-ttu-id="18648-158">Visual Studio を使用して .NET をリモートでデバッグする方法の詳細については、「 [SSH を使用した Linux での .net のリモートデバッグ](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18648-158">For details on using Visual Studio to debug .NET remotely, see [Remote debug .NET on Linux using SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span></span>

::: zone-end
