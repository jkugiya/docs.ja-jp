---
title: ML.NET コマンドライン インターフェイス (CLI) ツールをインストールする方法
description: ML.NET コマンド ライン インターフェイス (CLI) ツールをインストール、アップグレード、ダウングレード、およびアンインストールする方法を説明します。
ms.date: 06/08/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: a99ffa30dcbacba3341125fd0e37e617e0f4cd1e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103947"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="bad82-103">ML.NET コマンドライン インターフェイス (CLI) ツールをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="bad82-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="bad82-104">Windows、Mac、または Linux で ML.NET CLI (コマンド ライン インターフェイス) ツールをインストールする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="bad82-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="bad82-105">ML.NET CLI では、自動機械学習 (AutoML) とトレーニング データセットを使用して、高品質 ML.NET モデルとソース コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bad82-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="bad82-106">このトピックは、現在プレビュー段階の ML.NET CLI と ML.NET AutoML について述べており、内容が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="bad82-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="bad82-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="bad82-107">Pre-requisites</span></span>

- [<span data-ttu-id="bad82-108">.NET Core 3.1 SDK</span><span class="sxs-lookup"><span data-stu-id="bad82-108">.NET Core 3.1 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/3.1)

- <span data-ttu-id="bad82-109">(省略可能) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="bad82-109">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="bad82-110">生成された C# コード プロジェクトを Visual Studio で実行するには、`F5` キーを押すか、`dotnet run` (.NET Core CLI) を使用します。</span><span class="sxs-lookup"><span data-stu-id="bad82-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="bad82-111">メモ:.NET Core SDK のインストール後に `dotnet tool` コマンドが機能しない場合は、Windows からサインアウトしてから再度サインインします。</span><span class="sxs-lookup"><span data-stu-id="bad82-111">Note: If after installing .NET Core SDK the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="bad82-112">インストール</span><span class="sxs-lookup"><span data-stu-id="bad82-112">Install</span></span>

<span data-ttu-id="bad82-113">ML.NET CLI のインストール方法は他の .NET グローバル ツールと同様です。</span><span class="sxs-lookup"><span data-stu-id="bad82-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="bad82-114">`dotnet tool install` .NET Core CLI コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bad82-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="bad82-115">次の例は、既定の NuGet フィードの場所に ML.NET CLI をインストールする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bad82-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="bad82-116">ツールをインストールできない場合 (つまり、既定の NuGet フィードで利用できない場合) は、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bad82-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="bad82-117">予定していたフィードがチェックされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bad82-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="bad82-118">インストールが成功すると、ツールの呼び出しに使用したコマンドとインストールされたバージョンを示す、次の例のようなメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bad82-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="bad82-119">インストールが成功したことを確認するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="bad82-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="bad82-120">"classification" コマンドなど、mlnet ツールに利用できるコマンドのヘルプを参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bad82-120">You should see the help for available commands for the mlnet tool such as the 'classification' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="bad82-121">特定のリリース バージョンをインストールする</span><span class="sxs-lookup"><span data-stu-id="bad82-121">Install a specific release version</span></span>

<span data-ttu-id="bad82-122">ツールのプレリリース バージョンまたは特定のバージョンをインストールしようとしている場合は、次の形式を使用して、[フレームワーク](../../standard/frameworks.md)を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bad82-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="bad82-123">次のコマンドを入力して、パッケージが正しくインストールされているかどうかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="bad82-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="bad82-124">CLI パッケージをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="bad82-124">Uninstall the CLI package</span></span>

<span data-ttu-id="bad82-125">ローカル コンピューターからパッケージをアンインストールするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="bad82-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="bad82-126">CLI パッケージを更新する</span><span class="sxs-lookup"><span data-stu-id="bad82-126">Update the CLI package</span></span>

<span data-ttu-id="bad82-127">ローカル コンピューターからパッケージを更新するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="bad82-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="bad82-128">CLI の候補を設定する (タブベースのオートコンプリート)</span><span class="sxs-lookup"><span data-stu-id="bad82-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="bad82-129">ML.NET CLI は `System.CommandLine` に基づいているので、タブ補完のサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="bad82-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="bad82-130">次のアニメーションでタブのオートコンプリートのしくみの例を示します。</span><span class="sxs-lookup"><span data-stu-id="bad82-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![イメージ](./media/cli-tab-completion.gif)

<span data-ttu-id="bad82-132">"タブベースのオートコンプリート" (パラメーターの候補) は *Windows PowerShell* と *macOS/Linux bash* では機能しますが、*Windows CMD* では機能しません。</span><span class="sxs-lookup"><span data-stu-id="bad82-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="bad82-133">これを有効にするには、現在のプレビュー バージョンでは、エンド ユーザーが、シェルごとに 1 回、以下に示すいくつかの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bad82-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="bad82-134">これが完了すると、ML.NET CLI などの `System.CommandLine` を使用して作成されるすべてのアプリに対して補完が機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="bad82-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="bad82-135">補完を有効にするマシンでは、2 つのことを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bad82-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="bad82-136">次のコマンドを実行して、`dotnet-suggest` グローバル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bad82-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="bad82-137">適切な shim スクリプトをシェル プロファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="bad82-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="bad82-138">必要に応じてシェル プロファイル ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bad82-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="bad82-139">shim スクリプトによって、シェルからの完了要求が `dotnet-suggest` ツールに転送され、適切な `System.CommandLine` ベースのアプリに委任されます。</span><span class="sxs-lookup"><span data-stu-id="bad82-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="bad82-140">bash の場合、[dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) の内容を `~/.bash_profile` に追加します。</span><span class="sxs-lookup"><span data-stu-id="bad82-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="bad82-141">PowerShell の場合は、[dotnet-recommend-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) の内容を PowerShell プロファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="bad82-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="bad82-142">コンソールで次のコマンドを実行して、PowerShell プロファイルへの予想されるパスを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="bad82-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="bad82-143">(他のシェルについては、[検索する](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22)か、[問題](https://github.com/dotnet/System.CommandLine/issues)を開いてください。)</span><span class="sxs-lookup"><span data-stu-id="bad82-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="bad82-144">インストール ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="bad82-144">Installation directory</span></span>

<span data-ttu-id="bad82-145">ML.NET CLI は、既定のディレクトリまたは特定の場所にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="bad82-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="bad82-146">既定のディレクトリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bad82-146">The default directories are:</span></span>

| <span data-ttu-id="bad82-147">OS</span><span class="sxs-lookup"><span data-stu-id="bad82-147">OS</span></span>          | <span data-ttu-id="bad82-148">パス</span><span class="sxs-lookup"><span data-stu-id="bad82-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="bad82-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="bad82-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="bad82-150">Windows</span><span class="sxs-lookup"><span data-stu-id="bad82-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="bad82-151">これらの場所は、そこにインストールされたグローバル ツールを直接呼び出せるように、SDK が最初に実行されるときにユーザーのパスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="bad82-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="bad82-152">注: グローバル ツールは、マシン全体ではなく、ユーザー固有のものです。</span><span class="sxs-lookup"><span data-stu-id="bad82-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="bad82-153">ユーザーに固有であることは、そのマシンのすべてのユーザーが使用できるグローバル ツールをインストールできないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="bad82-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="bad82-154">このツールは、ツールがインストールされた各ユーザー プロファイルでしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="bad82-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="bad82-155">グローバル ツールは、特定のディレクトリにインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bad82-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="bad82-156">特定のディレクトリにインストールした場合は、ユーザーはコマンドが使用できることを確認する必要があります。それには、そのディレクトリをパスに含めるか、指定されたディレクトリでコマンドを呼び出すか、指定したディレクトリ内からツールを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bad82-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="bad82-157">この場合、.NET Core CLI によりこの場所が PATH 環境変数に自動的に追加されることはありません。</span><span class="sxs-lookup"><span data-stu-id="bad82-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="bad82-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="bad82-158">See also</span></span>

- [<span data-ttu-id="bad82-159">ML.NET CLI の概要</span><span class="sxs-lookup"><span data-stu-id="bad82-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="bad82-160">チュートリアル: ML.NET CLI を使用してセンチメントを分析する</span><span class="sxs-lookup"><span data-stu-id="bad82-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="bad82-161">ML.NET CLI auto-train コマンド リファレンス ガイド</span><span class="sxs-lookup"><span data-stu-id="bad82-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="bad82-162">ML.NET CLI のテレメトリ</span><span class="sxs-lookup"><span data-stu-id="bad82-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
