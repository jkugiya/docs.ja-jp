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
# <a name="troubleshoot-net-tool-usage-issues"></a><span data-ttu-id="10a0e-103">.NET ツールの使用に関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="10a0e-103">Troubleshoot .NET tool usage issues</span></span>

<span data-ttu-id="10a0e-104">.NET ツールをグローバル ツールまたはローカル ツールとしてインストールまたは実行しようとすると、問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-104">You might come across issues when trying to install or run a .NET tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="10a0e-105">この記事では、一般的な根本原因と考えられる解決策について説明します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-tool-fails-to-run"></a><span data-ttu-id="10a0e-106">インストールした .NET ツールを実行できない</span><span class="sxs-lookup"><span data-stu-id="10a0e-106">Installed .NET tool fails to run</span></span>

<span data-ttu-id="10a0e-107">.NET ツールの実行が失敗する場合、次のいずれかの問題が発生した可能性が高いです。</span><span class="sxs-lookup"><span data-stu-id="10a0e-107">When a .NET tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="10a0e-108">ツールの実行可能ファイルが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="10a0e-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="10a0e-109">正しいバージョンの .NET ランタイムが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="10a0e-109">The correct version of the .NET runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="10a0e-110">実行可能ファイルが見つからない</span><span class="sxs-lookup"><span data-stu-id="10a0e-110">Executable file not found</span></span>

<span data-ttu-id="10a0e-111">実行可能ファイルが見つからない場合は、次のようなメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="10a0e-112">実行可能ファイルの名前によって、ツールの呼び出し方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="10a0e-113">次の表ではその形式について説明します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-113">The following table describes the format:</span></span>

| <span data-ttu-id="10a0e-114">実行可能ファイル名の形式</span><span class="sxs-lookup"><span data-stu-id="10a0e-114">Executable name format</span></span>  | <span data-ttu-id="10a0e-115">呼び出し方式</span><span class="sxs-lookup"><span data-stu-id="10a0e-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="10a0e-116">グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="10a0e-116">Global tools</span></span>

  <span data-ttu-id="10a0e-117">グローバル ツールは、既定のディレクトリ内または特定の場所にインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="10a0e-118">既定のディレクトリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="10a0e-118">The default directories are:</span></span>

  | <span data-ttu-id="10a0e-119">OS</span><span class="sxs-lookup"><span data-stu-id="10a0e-119">OS</span></span>          | <span data-ttu-id="10a0e-120">パス</span><span class="sxs-lookup"><span data-stu-id="10a0e-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="10a0e-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="10a0e-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="10a0e-122">Windows</span><span class="sxs-lookup"><span data-stu-id="10a0e-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="10a0e-123">グローバル ツールを実行しようとしている場合は、コンピューター上の `PATH` 環境変数にグローバル ツールをインストールしたパスが含まれること、およびそのパスに実行可能ファイルが存在することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="10a0e-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="10a0e-124">.NET CLI では、初めて使用したときに、既定の場所を PATH 環境変数に追加する処理が試行されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-124">The .NET CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="10a0e-125">ただし、次のようなシナリオでは、その場所が PATH に自動的に追加されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="10a0e-126">Linux を使用していて、apt-get または rpm ではなく *.tar.gz* ファイルを使用して .NET SDK をインストールしている場合。</span><span class="sxs-lookup"><span data-stu-id="10a0e-126">If you're using Linux and you've installed the .NET SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="10a0e-127">macOS 10.15 "Catalina" またはそれ以降のバージョンを使用している場合。</span><span class="sxs-lookup"><span data-stu-id="10a0e-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="10a0e-128">macOS 10.14 "Mojave" 以前のバージョンを使用していて、 *.pkg* ではなく *.tar.gz* ファイルを使用して .NET SDK をインストールしている場合。</span><span class="sxs-lookup"><span data-stu-id="10a0e-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="10a0e-129">.NET Core 3.0 SDK をインストールしてあり、`DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` 環境変数を `false` に設定している場合。</span><span class="sxs-lookup"><span data-stu-id="10a0e-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="10a0e-130">.NET Core 2.2 SDK 以前のバージョンをインストールしてあり、`DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 環境変数を `true` に設定している場合。</span><span class="sxs-lookup"><span data-stu-id="10a0e-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="10a0e-131">これらのシナリオでは、または `--tool-path` オプションを指定した場合、ご利用のコンピューター上の `PATH` 環境変数には、グローバル ツールをインストールしたパスが自動的に含められません。</span><span class="sxs-lookup"><span data-stu-id="10a0e-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="10a0e-132">その場合は、ご利用のシェルで提供されている、環境変数を更新するための任意の方法を使用して、ツールの場所 (たとえば、`$HOME/.dotnet/tools`) を `PATH` 環境変数に追加します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="10a0e-133">詳細については、[.NET ツール](global-tools.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10a0e-133">For more information, see [.NET tools](global-tools.md).</span></span>

* <span data-ttu-id="10a0e-134">ローカル ツール</span><span class="sxs-lookup"><span data-stu-id="10a0e-134">Local tools</span></span>

  <span data-ttu-id="10a0e-135">ローカル ツールを実行しようとしている場合は、*dotnet-tools.json* という名前のマニフェストファイルが、現在のディレクトリまたはそのいずれかの親ディレクトリにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="10a0e-136">このファイルは、ルート フォルダーではなく、プロジェクト フォルダー階層のどこかにある *.config* という名前のフォルダーに存在することもあります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="10a0e-137">*dotnet-tools.json* が存在する場合は、それを開き、実行しようとしているツールを確認します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="10a0e-138">ファイルに `"isRoot": true` のエントリが含まれていない場合は、さらに上のファイル階層で他のツール マニフェスト ファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="10a0e-139">指定したパスでインストールされた .NET ツールを実行しようとしている場合は、ツールを使用するときにそのパスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-139">If you're trying to run a .NET tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="10a0e-140">ツールパスにインストールされたツールを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="10a0e-141">ランタイムが見つからない</span><span class="sxs-lookup"><span data-stu-id="10a0e-141">Runtime not found</span></span>

<span data-ttu-id="10a0e-142">.NET ツールは、[フレームワーク依存のアプリケーション](../deploying/index.md#publish-framework-dependent)です。つまり、お使いのマシンにインストールされている .NET ランタイムに依存します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-142">.NET tools are [framework-dependent applications](../deploying/index.md#publish-framework-dependent), which means they rely on a .NET runtime installed on your machine.</span></span> <span data-ttu-id="10a0e-143">予定のランタイムが見つからない場合、次のような通常の .NET ランタイムのロール フォワード ルールに従います。</span><span class="sxs-lookup"><span data-stu-id="10a0e-143">If the expected runtime isn't found, they follow normal .NET runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="10a0e-144">アプリケーションは、指定されたメジャー バージョンおよびマイナー バージョンの最上位の修正プログラム リリースにロール フォワードされます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="10a0e-145">一致するメジャー バージョン番号とマイナー バージョン番号と一致するランタイムがない場合は、次に高いマイナー バージョンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="10a0e-146">ランタイムのプレビュー バージョン間、またはプレビュー バージョンとリリース バージョン間では、ロール フォワードは発生しません。</span><span class="sxs-lookup"><span data-stu-id="10a0e-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="10a0e-147">したがって、プレビュー バージョンを使用して作成された .NET ツールは、作成者がリビルドして再パブリッシュしてから再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-147">So, .NET tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="10a0e-148">次の 2 つの一般的なシナリオでは、ロールフォワードは既定では実行されません。</span><span class="sxs-lookup"><span data-stu-id="10a0e-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="10a0e-149">使用できるのが古いバージョンのランタイムだけの場合。</span><span class="sxs-lookup"><span data-stu-id="10a0e-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="10a0e-150">ロールフォワードでは、ランタイムの新しいバージョンのみが選択されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="10a0e-151">使用できるのが高いメジャー バージョンのランタイムだけの場合。</span><span class="sxs-lookup"><span data-stu-id="10a0e-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="10a0e-152">ロールフォワードでは、メジャー バージョンの境界を越えることはありません。</span><span class="sxs-lookup"><span data-stu-id="10a0e-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="10a0e-153">アプリケーションで適切なランタイムが見つからない場合は、実行が失敗し、エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="10a0e-154">次のいずれかのコマンドを使用して、お使いのマシンにインストールされている .NET ランタイムを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-154">You can find out which .NET runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="10a0e-155">現在インストールされているランタイム バージョンがツールでサポートされている必要があると思われる場合は、ツールの作成者に連絡して、バージョン番号またはマルチターゲットを更新できるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="10a0e-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="10a0e-156">更新されたバージョン番号でツール パッケージが再コンパイルされて NuGet に再発行された後、コピーを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="10a0e-157">それまでの間の最も簡単な解決策は、実行しようとしているツールで動作するランタイムのバージョンをインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="10a0e-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="10a0e-158">特定の .NET ランタイム バージョンをダウンロードするには、[.NET ダウンロード ページ](https://dotnet.microsoft.com/download/dotnet)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="10a0e-158">To download a specific .NET runtime version, visit the [.NET download page](https://dotnet.microsoft.com/download/dotnet).</span></span>

<span data-ttu-id="10a0e-159">.NET SDK を既定以外の場所にインストールする場合は、環境変数 `DOTNET_ROOT` を `dotnet` 実行可能ファイルが格納されているディレクトリに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-159">If you install the .NET SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-tool-installation-fails"></a><span data-ttu-id="10a0e-160">.NET ツールのインストールが失敗する</span><span class="sxs-lookup"><span data-stu-id="10a0e-160">.NET tool installation fails</span></span>

<span data-ttu-id="10a0e-161">いろいろな理由で、.NET のグローバル ツールまたはローカル ツールのインストールが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-161">There are a number of reasons the installation of a .NET global or local tool may fail.</span></span> <span data-ttu-id="10a0e-162">ツールのインストールが失敗すると、次のようなメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="10a0e-163">これらのエラーの診断に役立つよう、上のメッセージと共に、NuGet のメッセージがユーザーに直接表示されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="10a0e-164">NuGet のメッセージは、問題の特定に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="10a0e-165">パッケージの名前付けの適用</span><span class="sxs-lookup"><span data-stu-id="10a0e-165">Package naming enforcement</span></span>

<span data-ttu-id="10a0e-166">Microsoft では、ツールのパッケージ ID に関するガイダンスを変更したため、いくつかのツールが予測される名前で見つからなくなっています。</span><span class="sxs-lookup"><span data-stu-id="10a0e-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="10a0e-167">新しいガイダンスでは、すべての Microsoft ツールに "Microsoft" というプレフィックスが付いています。</span><span class="sxs-lookup"><span data-stu-id="10a0e-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="10a0e-168">このプレフィックスは予約されており、Microsoft が承認した証明書で署名されたパッケージにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="10a0e-169">移行の間は、古い形式のパッケージ ID を持つ Microsoft ツールと、新しい形式を持つツールが混在します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="10a0e-170">パッケージ ID が更新されると、最新の更新プログラムを取得するには、新しいパッケージ ID に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="10a0e-171">ツール名が簡略化されているパッケージは非推奨となります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="10a0e-172">プレビュー リリース</span><span class="sxs-lookup"><span data-stu-id="10a0e-172">Preview releases</span></span>

* <span data-ttu-id="10a0e-173">プレビュー リリースをインストールしようとして、`--version` オプションを使用してバージョンを指定しませんでした。</span><span class="sxs-lookup"><span data-stu-id="10a0e-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="10a0e-174">プレビュー段階にある .NET ツールを名前の一部に指定して、プレビュー段階であることを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-174">.NET tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="10a0e-175">プレビュー全体を含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="10a0e-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="10a0e-176">バージョン番号が想定される形式であると仮定すると、次の例のようなものを使用できます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-tool"></a><span data-ttu-id="10a0e-177">パッケージが .NET ツールではない</span><span class="sxs-lookup"><span data-stu-id="10a0e-177">Package isn't a .NET tool</span></span>

* <span data-ttu-id="10a0e-178">この名前の NuGet パッケージは見つかりましたが、.NET ツールではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="10a0e-178">A NuGet package by this name was found, but it wasn't a .NET tool.</span></span>

<span data-ttu-id="10a0e-179">.NET ツールではなく、通常の NuGet パッケージである NuGet パッケージをインストールしようとすると、次のようなエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="10a0e-180">NU1212:`<ToolName>` のプロジェクトとパッケージの組み合わせが無効です。</span><span class="sxs-lookup"><span data-stu-id="10a0e-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="10a0e-181">DotnetToolReference プロジェクト形式には、DotnetTool タイプの参照のみ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="10a0e-182">NuGet フィードにアクセスできない</span><span class="sxs-lookup"><span data-stu-id="10a0e-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="10a0e-183">おそらくインターネット接続に問題があるため、必要な NuGet フィードにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="10a0e-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="10a0e-184">ツールをインストールするには、ツール パッケージが含まれている NuGet フィードにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="10a0e-185">フィードが使用できない場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="10a0e-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="10a0e-186">`nuget.config` でフィードを変更するか、特定の `nuget.config` ファイルを要求するか、`--add-source` スイッチを使用して追加のフィードを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="10a0e-187">既定では、NuGet では接続できないフィードに対してエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="10a0e-188">フラグ `--ignore-failed-sources` を指定すると、これらの到達できないソースをスキップできます。</span><span class="sxs-lookup"><span data-stu-id="10a0e-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="10a0e-189">パッケージ ID が正しくない</span><span class="sxs-lookup"><span data-stu-id="10a0e-189">Package ID incorrect</span></span>

* <span data-ttu-id="10a0e-190">ツールの名前が間違って入力されています。</span><span class="sxs-lookup"><span data-stu-id="10a0e-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="10a0e-191">失敗でよくある理由は、ツール名が正しくないことです。</span><span class="sxs-lookup"><span data-stu-id="10a0e-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="10a0e-192">これは、入力ミスや、ツールが移動されたか非推奨になったために、発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="10a0e-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="10a0e-193">NuGet.org のツールで、確実に正しい名前を使用する方法の 1 つは、NuGet.org でツールを検索し、インストール コマンドをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="10a0e-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="10a0e-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="10a0e-194">See also</span></span>

* [<span data-ttu-id="10a0e-195">.NET ツール</span><span class="sxs-lookup"><span data-stu-id="10a0e-195">.NET tools</span></span>](global-tools.md)
