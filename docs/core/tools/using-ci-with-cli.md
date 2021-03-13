---
title: .NET SDK とツールを使用した継続的インテグレーション (CI)
description: 継続的インテグレーションで .NET SDK とそのツールをビルド サーバー上で使用する方法について説明します。
ms.date: 05/18/2017
ms.openlocfilehash: fd1548f5c2d0a5191dd54c315c90a8ce3f8a5305
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189996"
---
# <a name="using-the-net-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="5b811-103">継続的インテグレーション (CI) で .NET SDK とツールを使用する</span><span class="sxs-lookup"><span data-stu-id="5b811-103">Using the .NET SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="5b811-104">このドキュメントでは、.NET SDK とそのツールをビルド サーバーで使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b811-104">This document outlines using the .NET SDK and its tools on a build server.</span></span> <span data-ttu-id="5b811-105">.NET ツールセットは、開発者がコマンド プロンプトにコマンドを入力する対話式と継続的インテグレーション (CI) サーバーによりビルド スクリプトが実行される自動の両方に対応しています。</span><span class="sxs-lookup"><span data-stu-id="5b811-105">The .NET toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="5b811-106">コマンド、オプション、入力、出力は同じです。ユーザーは、ツールの取得方法とアプリを構築するシステムだけを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b811-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="5b811-107">このドキュメントでは、CI のツール取得のシナリオと、ビルド スクリプトの設計と構造化の方法に関する推奨事項を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="5b811-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="5b811-108">CI ビルド サーバーのインストール オプション</span><span class="sxs-lookup"><span data-stu-id="5b811-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="5b811-109">ネイティブ インストーラーの使用</span><span class="sxs-lookup"><span data-stu-id="5b811-109">Using the native installers</span></span>

<span data-ttu-id="5b811-110">macOS、Linux、Windows の場合、ネイティブ インストーラーを利用できます。</span><span class="sxs-lookup"><span data-stu-id="5b811-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="5b811-111">このインストーラーは、ビルド サーバーへの admin (sudo) アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="5b811-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="5b811-112">ネイティブ インストーラーを使用することの利点は、ツールを実行するために必要なあらゆるネイティブ依存性がインストールされることです。</span><span class="sxs-lookup"><span data-stu-id="5b811-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="5b811-113">ネイティブ インストーラーはまた、システム全体に SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="5b811-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="5b811-114">macOS をご利用の場合、PKG インストーラーをお使いください。</span><span class="sxs-lookup"><span data-stu-id="5b811-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="5b811-115">Linux の場合、フィードベースのパッケージ マネージャーを利用できます。Ubuntu の apt-get や CentOS の yum などです。あるいは、パッケージ自体、DEB または RPM を利用できます。</span><span class="sxs-lookup"><span data-stu-id="5b811-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="5b811-116">Windows の場合、MSI インストーラーをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="5b811-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="5b811-117">最新の安定したバイナリは、[.NET ダウンロード](https://dotnet.microsoft.com/download)のページにあります。</span><span class="sxs-lookup"><span data-stu-id="5b811-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="5b811-118">最新の (安定性に欠ける可能性がある) プレリリース ツールを使用する場合、[dotnet/core-sdk GitHub リポジトリ](https://github.com/dotnet/core-sdk#installers-and-binaries)のリンクをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="5b811-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="5b811-119">Linux ディストリビューションの場合、`tar.gz` アーカイブ (別名、`tarballs`) をご利用いただけます。アーカイブ内のインストール スクリプトを利用して .NET Core をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="5b811-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="5b811-120">インストーラー スクリプトの使用</span><span class="sxs-lookup"><span data-stu-id="5b811-120">Using the installer script</span></span>

<span data-ttu-id="5b811-121">インストーラー スクリプトを使用すると、ビルド サーバーで管理者以外のインストールが可能になり、ツールの取得を簡単に自動化できます。</span><span class="sxs-lookup"><span data-stu-id="5b811-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="5b811-122">スクリプトにツールがダウンロードされ、既定の場所か指定された場所に抽出されます。</span><span class="sxs-lookup"><span data-stu-id="5b811-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="5b811-123">インストールするツールのバージョンと、SDK 全体をインストールするか、それとも共有ランタイムだけをインストールするかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="5b811-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="5b811-124">インストーラー スクリプトは、ビルドの開始時に実行され、必要なバージョンの SDK を取得し、インストールするように自動化されています。</span><span class="sxs-lookup"><span data-stu-id="5b811-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="5b811-125">*必要なバージョン* とは、プロジェクトのビルドに必要な SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="5b811-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="5b811-126">このスクリプトでは、サーバーのローカル ディレクトリに SDK をインストールし、インストールした場所からツールを実行し、ビルド後にクリーンアップできます (あるいは、CI サービスにクリーンアップさせます)。</span><span class="sxs-lookup"><span data-stu-id="5b811-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="5b811-127">これにより、ビルド プロセス全体にカプセル化と分離性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="5b811-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="5b811-128">インストール スクリプト参照は [dotnet-install](dotnet-install-script.md) の記事にあります。</span><span class="sxs-lookup"><span data-stu-id="5b811-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="5b811-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="5b811-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="5b811-130">インストーラー スクリプトの使用時、ネイティブ依存性は自動的にはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="5b811-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="5b811-131">オペレーティング システムにネイティブ依存性がない場合、それをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b811-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="5b811-132">詳細については、[.NET の依存関係と要件](../install/windows.md#dependencies)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b811-132">For more information, see [.NET dependencies and requirements](../install/windows.md#dependencies).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="5b811-133">CI セットアップ例</span><span class="sxs-lookup"><span data-stu-id="5b811-133">CI setup examples</span></span>

<span data-ttu-id="5b811-134">このセクションでは、PowerShell またはバッシュ スクリプトを利用した手動セットアップについて説明し、SaaS (サービスとしてのソフトウェア) CI (継続的インテグレーション) ソリューションをいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="5b811-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="5b811-135">対象となる SaaS CI ソリューションは [Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/)、および [Azure Pipelines](/azure/devops/pipelines/index) です。</span><span class="sxs-lookup"><span data-stu-id="5b811-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="5b811-136">手動セットアップ</span><span class="sxs-lookup"><span data-stu-id="5b811-136">Manual setup</span></span>

<span data-ttu-id="5b811-137">各 SaaS サービスには、ビルド プロセスを作成し、構成するための独自の方法があります。</span><span class="sxs-lookup"><span data-stu-id="5b811-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="5b811-138">一覧に記載されている以外の SaaS ソリューションを使用する場合、あるいは事前にパッケージに含まれているサポート以上のカスタマイズが必要な場合、少なくとも一部に手動構成が必要になります。</span><span class="sxs-lookup"><span data-stu-id="5b811-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="5b811-139">全般的に、手動セットアップでは、あるバージョンのツール (あるいはツールの最新のナイトリー ビルド) を取得し、ビルド スクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b811-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="5b811-140">PowerShell またはバッシュ スクリプトを使用し、.NET コマンドを調整したり、プロジェクト ファイルを使用してビルド プロセスの概要を伝えたりできます。</span><span class="sxs-lookup"><span data-stu-id="5b811-140">You can use a PowerShell or bash script to orchestrate the .NET commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="5b811-141">[オーケストレーション セクション](#orchestrating-the-build)で、これらのオプションについて詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="5b811-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="5b811-142">手動 CI ビルド サーバー セットアップを実行するスクリプトを作成したら、それを開発マシンで使用し、テスト目的でコードをローカルでビルドします。</span><span class="sxs-lookup"><span data-stu-id="5b811-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="5b811-143">スクリプトがローカルで問題なく動作していることを確認したら、CI ビルド サーバーに展開します。</span><span class="sxs-lookup"><span data-stu-id="5b811-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="5b811-144">比較的単純な PowerShell スクリプトを使用して、.NET SDK を取得し、Windows ビルド サーバーにインストールする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5b811-144">A relatively simple PowerShell script demonstrates how to obtain the .NET SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="5b811-145">スクリプトの終わりで、自分のビルド プロセスの実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="5b811-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="5b811-146">スクリプトはツールを取得し、ビルド プロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="5b811-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="5b811-147">UNIX マシンの場合、次のバッシュ スクリプトが PowerShell スクリプトに記載されているアクションを同様の方法で実行します。</span><span class="sxs-lookup"><span data-stu-id="5b811-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="5b811-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="5b811-148">Travis CI</span></span>

<span data-ttu-id="5b811-149">`csharp` 言語と `dotnet` キーを使用して .NET SDK をインストールするように [Travis CI](https://travis-ci.org/) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="5b811-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="5b811-150">詳細については、公式 Travis CI ドキュメントの「[Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/)」(C#、F#、または Visual Basic プロジェクトのビルド) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b811-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="5b811-151">Travis CI 情報にアクセスするときは、コミュニティが保守管理している `language: csharp` 言語識別子は F# や Mono を含む、あらゆる .NET 言語で機能することにご留意ください。</span><span class="sxs-lookup"><span data-stu-id="5b811-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="5b811-152">Travis CI は、*ビルド マトリックス* において、macOS ジョブと Linux ジョブの両方を実行できます。ビルド マトリックスでは、ランタイム、環境、除外/追加の組み合わせを指定し、アプリのビルド組み合わせを範囲に含めます。</span><span class="sxs-lookup"><span data-stu-id="5b811-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="5b811-153">詳細については、Travis CI ドキュメントの「[Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build)」 (ビルドをカスタマイズする) の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b811-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="5b811-154">MSBuild ベースのツールのパッケージには、LTS (1.0.x) ランタイムと Current (1.1.x) ランタイムが含まれています。SDK をインストールすることで、ビルドに必要なすべてが与えられます。</span><span class="sxs-lookup"><span data-stu-id="5b811-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="5b811-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="5b811-155">AppVeyor</span></span>

<span data-ttu-id="5b811-156">[AppVeyor](https://www.appveyor.com/) は、`Visual Studio 2017` worker イメージで .NET Core 1.0.1 SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="5b811-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="5b811-157">異なるバージョンの .NET SDK を含む他のビルド イメージも利用できます。</span><span class="sxs-lookup"><span data-stu-id="5b811-157">Other build images with different versions of the .NET SDK are available.</span></span> <span data-ttu-id="5b811-158">詳細については、[appveyor.yml の例](https://github.com/dotnet/docs/blob/main/appveyor.yml)と AppVoyor ドキュメントの [worker イメージのビルド](https://www.appveyor.com/docs/build-environment/#build-worker-images)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b811-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/main/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="5b811-159">.NET SDK バイナリがインストール スクリプトを使用してダウンロードおよび解凍され、`PATH` 環境変数に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5b811-159">The .NET SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="5b811-160">複数の .NET SDK バージョンとの統合テストを実行するためにビルド マトリックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="5b811-160">Add a build matrix to run integration tests with multiple versions of the .NET SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="5b811-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="5b811-161">Azure DevOps Services</span></span>

<span data-ttu-id="5b811-162">以下のいずれかの手法で .NET プロジェクトをビルドするように Azure DevOps Services を構成します。</span><span class="sxs-lookup"><span data-stu-id="5b811-162">Configure Azure DevOps Services to build .NET projects using one of these approaches:</span></span>

1. <span data-ttu-id="5b811-163">コマンドを利用し、[手動セットアップ手順](#manual-setup)からスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="5b811-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="5b811-164">.NET ツールを使用するように構成された、Azure DevOps Services の複数の組み込みビルド タスクで構成されるビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b811-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET tools.</span></span>

<span data-ttu-id="5b811-165">いずれのソリューションも有効です。</span><span class="sxs-lookup"><span data-stu-id="5b811-165">Both solutions are valid.</span></span> <span data-ttu-id="5b811-166">ツールはビルドの一部としてダウンロードしているので、手動セットアップ スクリプトを使用し、取得したツールのバージョンを管理します。</span><span class="sxs-lookup"><span data-stu-id="5b811-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="5b811-167">ビルドはスクリプトから実行されます。そのスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b811-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="5b811-168">この記事では、手動オプションについてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="5b811-168">This article only covers the manual option.</span></span> <span data-ttu-id="5b811-169">Azure DevOps Services ビルド タスクを使用したビルドの構築の詳細については、[Azure Pipelines](/azure/devops/pipelines/index) のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b811-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="5b811-170">Azure DevOps Services で手動セットアップ スクリプトを使用するには、新しいビルド定義を作成し、ビルド手順で実行するスクリプトを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b811-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="5b811-171">これは Azure DevOps Services ユーザー インターフェイスを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="5b811-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="5b811-172">最初に新しいビルド定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="5b811-172">Start by creating a new build definition.</span></span> <span data-ttu-id="5b811-173">作成するビルドの種類を定義するためのオプションを指定する画面が表示されたら、 **[空]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5b811-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![ビルド定義で空を選択する](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="5b811-175">ビルドするリポジトリを構成すると、ビルド定義が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b811-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="5b811-176">**[ビルド ステップの追加...]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5b811-176">Select **Add build step**:</span></span>

   ![ビルド ステップの追加](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="5b811-178">**[タスク カタログ]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5b811-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="5b811-179">このカタログには、ビルドで使用するタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5b811-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="5b811-180">スクリプトがあるので、**PowerShell: Run a PowerShell スクリプト** の **[追加]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="5b811-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![PowerShell スクリプトの追加手順](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="5b811-182">ビルド手順を構成します。</span><span class="sxs-lookup"><span data-stu-id="5b811-182">Configure the build step.</span></span> <span data-ttu-id="5b811-183">ビルドしているリポジトリからスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="5b811-183">Add the script from the repository that you're building:</span></span>

   ![実行する PowerShell スクリプトを指定する](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="5b811-185">ビルドの調整</span><span class="sxs-lookup"><span data-stu-id="5b811-185">Orchestrating the build</span></span>

<span data-ttu-id="5b811-186">このドキュメントの多くは、.NET ツールを取得し、さまざまな CI サービスを構成する方法についての説明であり、"*実際にビルドする*" (.NET Core を使ってコードを書く) 方法についての説明はありません。</span><span class="sxs-lookup"><span data-stu-id="5b811-186">Most of this document describes how to acquire the .NET tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="5b811-187">ビルド プロセスの構造化方法の選択肢は、ここでは取り上げることができないさまざまな要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="5b811-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="5b811-188">[Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/)、[Azure Pipelines](/azure/devops/pipelines/index) でビルドを調整する方法については、それぞれの文書に記載されている資料とサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b811-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="5b811-189">.NET ツールを使用して .NET コードのビルド プロセスを構築するには、MSBuild を直接使用する方法と .NET コマンドライン コマンドを使用する方法の 2 つが一般的です。</span><span class="sxs-lookup"><span data-stu-id="5b811-189">Two general approaches that you take in structuring the build process for .NET code using the .NET tools are using MSBuild directly or using the .NET command-line commands.</span></span> <span data-ttu-id="5b811-190">いずれの手法を採用するかは、手法と複雑性との兼ね合いで使いやすいものを選択してください。</span><span class="sxs-lookup"><span data-stu-id="5b811-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="5b811-191">MSBuild を利用すれば、タスクやターゲットとしてビルド プロセスを表現できますが、MSBuild プロジェクト ファイルの構文は複雑で、学習の難易度が上がります。</span><span class="sxs-lookup"><span data-stu-id="5b811-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="5b811-192">.NET コマンドライン ツールを使用する方が簡単ですが、`bash` や PowerShell などのスクリプト言語でオーケストレーション ロジックを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b811-192">Using the .NET command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b811-193">参照</span><span class="sxs-lookup"><span data-stu-id="5b811-193">See also</span></span>

- [<span data-ttu-id="5b811-194">.NET ダウンロード - Linux</span><span class="sxs-lookup"><span data-stu-id="5b811-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
