---
title: Snap を使用して Linux に .NET をインストールする - .NET
description: Snap を使用して Linux に .NET SDK または .NET ランタイムをインストールする方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 0d91f5049c92df240e2c3e26bc67952abe17fedc
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190100"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a><span data-ttu-id="729e9-103">Snap を使用して .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="729e9-103">Install the .NET SDK or the .NET Runtime with Snap</span></span>

<span data-ttu-id="729e9-104">Snap パッケージを使用して、.NET SDK または .NET ランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="729e9-104">Use a Snap package to install the .NET SDK or .NET Runtime.</span></span> <span data-ttu-id="729e9-105">Snap は、Linux ディストリビューションに組み込まれているパッケージ マネージャーに代わる優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="729e9-105">Snaps are a great alternative to the package manager built into your Linux distribution.</span></span> <span data-ttu-id="729e9-106">この記事では、[Snap](https://snapcraft.io/dotnet-sdk) を使用して .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="729e9-106">This article describes how to install .NET through [Snap](https://snapcraft.io/dotnet-sdk).</span></span>

<span data-ttu-id="729e9-107">Snap は、アプリとその依存関係のバンドルであり、さまざまな Linux ディストリビューション間で変更を加えることなく動作します。</span><span class="sxs-lookup"><span data-stu-id="729e9-107">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="729e9-108">Snap は、Snap Store で見つけてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="729e9-108">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="729e9-109">Snap の詳細については、[Snap の概要](https://snapcraft.io/docs/getting-started)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="729e9-109">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

> [!CAUTION]
> <span data-ttu-id="729e9-110">Snap パッケージは、Windows 10 の WSL2 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="729e9-110">Snap packages aren't supported in WSL2 on Windows 10.</span></span> <span data-ttu-id="729e9-111">別の方法としては、[`dotnet-install` スクリプト](linux-scripted-manual.md#scripted-install)または特定の WSL2 ディストリビューション用のパッケージ マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="729e9-111">As an alternative, use the [`dotnet-install` script](linux-scripted-manual.md#scripted-install) or the package manager for the particular WSL2 distribution.</span></span> <span data-ttu-id="729e9-112">推奨されませんが、[snapcraft フォーラムからサポートされていない回避策](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)を使用して Snap を有効にしてみることができます。</span><span class="sxs-lookup"><span data-stu-id="729e9-112">It's not recommended but you can try to enable snap with an [unsupported workaround from the snapcraft forums](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span></span>

## <a name="net-releases"></a><span data-ttu-id="729e9-113">.NET のリリース</span><span class="sxs-lookup"><span data-stu-id="729e9-113">.NET releases</span></span>

<span data-ttu-id="729e9-114">Snap では、✔️ サポートされているバージョンの .NET SDK のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="729e9-114">Only ✔️ supported versions of .NET SDK are available through Snap.</span></span> <span data-ttu-id="729e9-115">.NET ランタイムのすべてのバージョンは、バージョン 2.1 以降の Snap から使用できます。</span><span class="sxs-lookup"><span data-stu-id="729e9-115">All versions of the .NET Runtime are available through snap starting with version 2.1.</span></span> <span data-ttu-id="729e9-116">次の表は、.NET (および .NET Core) のリリースの一覧です。</span><span class="sxs-lookup"><span data-stu-id="729e9-116">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="729e9-117">✔️ Supported</span><span class="sxs-lookup"><span data-stu-id="729e9-117">✔️ Supported</span></span> | <span data-ttu-id="729e9-118">❌ サポートされていない</span><span class="sxs-lookup"><span data-stu-id="729e9-118">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="729e9-119">5.0</span><span class="sxs-lookup"><span data-stu-id="729e9-119">5.0</span></span>         | <span data-ttu-id="729e9-120">3.0</span><span class="sxs-lookup"><span data-stu-id="729e9-120">3.0</span></span>           |
| <span data-ttu-id="729e9-121">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="729e9-121">3.1 (LTS)</span></span>   | <span data-ttu-id="729e9-122">2.2</span><span class="sxs-lookup"><span data-stu-id="729e9-122">2.2</span></span>           |
| <span data-ttu-id="729e9-123">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="729e9-123">2.1 (LTS)</span></span>   | <span data-ttu-id="729e9-124">2.0</span><span class="sxs-lookup"><span data-stu-id="729e9-124">2.0</span></span>           |
|             | <span data-ttu-id="729e9-125">1.1</span><span class="sxs-lookup"><span data-stu-id="729e9-125">1.1</span></span>           |
|             | <span data-ttu-id="729e9-126">1.0</span><span class="sxs-lookup"><span data-stu-id="729e9-126">1.0</span></span>           |

<span data-ttu-id="729e9-127">.NET リリースのライフ サイクルの詳細については、「[.NET Core と .NET 5 のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="729e9-127">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="sdk-or-runtime"></a><span data-ttu-id="729e9-128">SDK またはランタイム</span><span class="sxs-lookup"><span data-stu-id="729e9-128">SDK or Runtime</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a><span data-ttu-id="729e9-129">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="729e9-129">Install the SDK</span></span>

<span data-ttu-id="729e9-130">.NET SDK 用の Snap パッケージはすべて、同じ識別子 `dotnet-sdk` で公開されます。</span><span class="sxs-lookup"><span data-stu-id="729e9-130">Snap packages for the .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="729e9-131">特定のバージョンの SDK は、チャネルを指定することによってインストールできます。</span><span class="sxs-lookup"><span data-stu-id="729e9-131">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="729e9-132">SDK には、対応するランタイムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="729e9-132">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="729e9-133">次の表に、チャネルの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="729e9-133">The following table lists the channels:</span></span>

| <span data-ttu-id="729e9-134">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="729e9-134">.NET version</span></span> | <span data-ttu-id="729e9-135">Snap パッケージまたはチャネル</span><span class="sxs-lookup"><span data-stu-id="729e9-135">Snap package or channel</span></span>  |
|--------------|--------------------------|
| <span data-ttu-id="729e9-136">5.0</span><span class="sxs-lookup"><span data-stu-id="729e9-136">5.0</span></span>          | <span data-ttu-id="729e9-137">`5.0` または `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="729e9-137">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="729e9-138">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="729e9-138">3.1 (LTS)</span></span>    | <span data-ttu-id="729e9-139">`3.1` または `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="729e9-139">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="729e9-140">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="729e9-140">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="729e9-141">`snap install` コマンドを使用して、.NET SDK の Snap パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="729e9-141">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="729e9-142">`--channel` パラメーターを使用して、インストールするバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="729e9-142">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="729e9-143">このパラメーターを省略すると、`latest/stable` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="729e9-143">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="729e9-144">この例では、`5.0` が指定されています。</span><span class="sxs-lookup"><span data-stu-id="729e9-144">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="729e9-145">次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。</span><span class="sxs-lookup"><span data-stu-id="729e9-145">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="729e9-146">このコマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="729e9-146">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="729e9-147">`{alias}` の名前は自由に選択できます。</span><span class="sxs-lookup"><span data-stu-id="729e9-147">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="729e9-148">たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-sdk.dotnet dotnet50`。</span><span class="sxs-lookup"><span data-stu-id="729e9-148">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="729e9-149">コマンド `dotnet50` を使用すると、この特定のバージョンの .NET が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="729e9-149">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="729e9-150">ただし、異なるエイリアスの選択は、ほとんどのチュートリアルや例と互換性がありません。それらでは、`dotnet` コマンドを使用することが想定されているためです。</span><span class="sxs-lookup"><span data-stu-id="729e9-150">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be used.</span></span>

## <a name="install-the-runtime"></a><span data-ttu-id="729e9-151">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="729e9-151">Install the runtime</span></span>

<span data-ttu-id="729e9-152">.NET ランタイム用の Snap パッケージはそれぞれ、独自のパッケージ識別子で公開されます。</span><span class="sxs-lookup"><span data-stu-id="729e9-152">Snap packages for the .NET Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="729e9-153">次の表に、パッケージ識別子の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="729e9-153">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="729e9-154">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="729e9-154">.NET version</span></span>      | <span data-ttu-id="729e9-155">Snap パッケージ</span><span class="sxs-lookup"><span data-stu-id="729e9-155">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="729e9-156">5.0</span><span class="sxs-lookup"><span data-stu-id="729e9-156">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="729e9-157">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="729e9-157">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="729e9-158">3.0</span><span class="sxs-lookup"><span data-stu-id="729e9-158">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="729e9-159">2.2</span><span class="sxs-lookup"><span data-stu-id="729e9-159">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="729e9-160">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="729e9-160">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="729e9-161">`snap install` コマンドを使用して、.NET ランタイムの Snap パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="729e9-161">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="729e9-162">この例では、.NET 5.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="729e9-162">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="729e9-163">次に、`snap alias` コマンドを使用して、システムの `dotnet` コマンドを登録します。</span><span class="sxs-lookup"><span data-stu-id="729e9-163">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="729e9-164">コマンドの形式は次のとおりです: `sudo snap alias {package}.{command} {alias}`。</span><span class="sxs-lookup"><span data-stu-id="729e9-164">The command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="729e9-165">`{alias}` の名前は自由に選択できます。</span><span class="sxs-lookup"><span data-stu-id="729e9-165">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="729e9-166">たとえば、snap によってインストールされた特定のバージョンにちなんでコマンドの名前を指定できます: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`。</span><span class="sxs-lookup"><span data-stu-id="729e9-166">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="729e9-167">コマンド `dotnet50` を使用すると、特定のバージョンの .NET が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="729e9-167">When you use the command `dotnet50`, you'll invoke a specific version of .NET.</span></span> <span data-ttu-id="729e9-168">ただし、異なるエイリアスの選択は、ほとんどのチュートリアルや例と互換性がありません。それらでは、`dotnet` コマンドを使用できることが想定されているためです。</span><span class="sxs-lookup"><span data-stu-id="729e9-168">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

## <a name="export-the-install-location"></a><span data-ttu-id="729e9-169">インストール場所をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="729e9-169">Export the install location</span></span>

<span data-ttu-id="729e9-170">`DOTNET_ROOT` 環境変数は、.NET がインストールされている場所を判断するためにツールによって使用されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="729e9-170">The `DOTNET_ROOT` environment variable is often used by tools to determine where .NET is installed.</span></span> <span data-ttu-id="729e9-171">スナップを使用して .NET をインストールすると、この環境変数は構成されません。</span><span class="sxs-lookup"><span data-stu-id="729e9-171">When .NET is installed through Snap, this environment variable isn't configured.</span></span> <span data-ttu-id="729e9-172">プロファイルで *DOTNET_ROOT* 環境変数を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="729e9-172">You should configure the *DOTNET_ROOT* environment variable in your profile.</span></span> <span data-ttu-id="729e9-173">スナップへのパスは、`/snap/{package}/current` の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="729e9-173">The path to the snap uses the following format: `/snap/{package}/current`.</span></span> <span data-ttu-id="729e9-174">たとえば、`dotnet-sdk` スナップをインストールした場合は、次のコマンドを使用して、.NET が配置されている場所に環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="729e9-174">For example, if you installed the `dotnet-sdk` snap, use the following command to set the environment variable to where .NET is located:</span></span>

```bash
export DOTNET_ROOT=/snap/dotnet-sdk/current
```

> [!TIP]
> <span data-ttu-id="729e9-175">上記の `export` コマンドは、コマンドを実行したターミナル セッションの環境変数のみを設定します。</span><span class="sxs-lookup"><span data-stu-id="729e9-175">The preceding `export` command only sets the environment variable for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="729e9-176">シェル プロファイルを編集して、コマンドを永続的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="729e9-176">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="729e9-177">Linux ではさまざまなシェルを使用でき、それぞれに異なるプロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="729e9-177">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="729e9-178">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="729e9-178">For example:</span></span>
>
> - <span data-ttu-id="729e9-179">**Bash シェル**: *~/.bash_profile*、 *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="729e9-179">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="729e9-180">**Korn シェル**: *~/.kshrc* または *.profile*</span><span class="sxs-lookup"><span data-stu-id="729e9-180">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="729e9-181">**Z シェル**: *~/.zshrc* または *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="729e9-181">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="729e9-182">シェルの適切なソース ファイルを編集し、`export DOTNET_ROOT=/snap/dotnet-sdk/current` を追加します。</span><span class="sxs-lookup"><span data-stu-id="729e9-182">Edit the appropriate source file for your shell and add `export DOTNET_ROOT=/snap/dotnet-sdk/current`.</span></span>

## <a name="tlsssl-certificate-errors"></a><span data-ttu-id="729e9-183">TLS/SSL 証明書のエラー</span><span class="sxs-lookup"><span data-stu-id="729e9-183">TLS/SSL Certificate errors</span></span>

<span data-ttu-id="729e9-184">Snap を使用して .NET をインストールする場合、一部のディストリビューションでは .NET の TLS/SSL 証明書が見つからないことがあり、`restore` の間にエラーが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="729e9-184">When .NET is installed through Snap, it's possible that on some distros the .NET TLS/SSL certificates may not be found and you may receive an error during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="729e9-185">この問題を解決するには、いくつかの環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="729e9-185">To resolve this problem, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="729e9-186">証明書の場所は、ディストリビューションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="729e9-186">The certificate location will vary by distro.</span></span> <span data-ttu-id="729e9-187">次に、問題が発生したディストリビューションの場所を示します。</span><span class="sxs-lookup"><span data-stu-id="729e9-187">Here are the locations for the distros where the issue has been experienced.</span></span>

| <span data-ttu-id="729e9-188">Distribution</span><span class="sxs-lookup"><span data-stu-id="729e9-188">Distribution</span></span> | <span data-ttu-id="729e9-189">場所</span><span class="sxs-lookup"><span data-stu-id="729e9-189">Location</span></span>                                            |
|--------------|-----------------------------------------------------|
| <span data-ttu-id="729e9-190">**Fedora**</span><span class="sxs-lookup"><span data-stu-id="729e9-190">**Fedora**</span></span>   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| <span data-ttu-id="729e9-191">**OpenSUSE**</span><span class="sxs-lookup"><span data-stu-id="729e9-191">**OpenSUSE**</span></span> | `/etc/ssl/ca-bundle.pem`                            |
| <span data-ttu-id="729e9-192">**Solus**</span><span class="sxs-lookup"><span data-stu-id="729e9-192">**Solus**</span></span>    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a><span data-ttu-id="729e9-193">次のステップ</span><span class="sxs-lookup"><span data-stu-id="729e9-193">Next steps</span></span>

- [<span data-ttu-id="729e9-194">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="729e9-194">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="729e9-195">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="729e9-195">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
