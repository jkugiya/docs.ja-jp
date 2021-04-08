---
title: 手動で Linux に .NET をインストールする - .NET
description: Linux でパッケージ マネージャーを使用せずに .NET SDK と .NET ランタイムをインストールする方法を示します。 インストール スクリプトを使用するか、手動でバイナリを抽出します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9176f7477cf80c26ef0b5b7c438c47afcb423799
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231298"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a><span data-ttu-id="49c30-104">手動で .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="49c30-104">Install the .NET SDK or the .NET Runtime manually</span></span>

<span data-ttu-id="49c30-105">.NET は Linux でサポートされており、この記事では、インストール スクリプトを使用して、またはバイナリを抽出して、Linux に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49c30-105">.NET is supported on Linux and this article describes how to install .NET on Linux using the install script or by extracting the binaries.</span></span> <span data-ttu-id="49c30-106">組み込みパッケージ マネージャーがサポートされているディストリビューションの一覧については、「[Linux に .NET をインストールする](linux.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c30-106">For a list of distributions that support the built-in package manager, see [Install .NET on Linux](linux.md).</span></span>

<span data-ttu-id="49c30-107">Snap を使用して .NET をインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="49c30-107">You can also install .NET with snap.</span></span> <span data-ttu-id="49c30-108">詳細については、「[Snap を使用して .NET SDK または .NET ランタイムをインストールする](linux-snap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c30-108">For more information, see [Install the .NET SDK or the .NET Runtime with Snap](linux-snap.md).</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a><span data-ttu-id="49c30-109">.NET のリリース</span><span class="sxs-lookup"><span data-stu-id="49c30-109">.NET releases</span></span>

<span data-ttu-id="49c30-110">次の表は、.NET (および .NET Core) のリリースの一覧です。</span><span class="sxs-lookup"><span data-stu-id="49c30-110">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="49c30-111">✔️ Supported</span><span class="sxs-lookup"><span data-stu-id="49c30-111">✔️ Supported</span></span> | <span data-ttu-id="49c30-112">❌ サポートされていない</span><span class="sxs-lookup"><span data-stu-id="49c30-112">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="49c30-113">5.0</span><span class="sxs-lookup"><span data-stu-id="49c30-113">5.0</span></span>         | <span data-ttu-id="49c30-114">3.0</span><span class="sxs-lookup"><span data-stu-id="49c30-114">3.0</span></span>           |
| <span data-ttu-id="49c30-115">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="49c30-115">3.1 (LTS)</span></span>   | <span data-ttu-id="49c30-116">2.2</span><span class="sxs-lookup"><span data-stu-id="49c30-116">2.2</span></span>           |
| <span data-ttu-id="49c30-117">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="49c30-117">2.1 (LTS)</span></span>   | <span data-ttu-id="49c30-118">2.0</span><span class="sxs-lookup"><span data-stu-id="49c30-118">2.0</span></span>           |
|             | <span data-ttu-id="49c30-119">1.1</span><span class="sxs-lookup"><span data-stu-id="49c30-119">1.1</span></span>           |
|             | <span data-ttu-id="49c30-120">1.0</span><span class="sxs-lookup"><span data-stu-id="49c30-120">1.0</span></span>           |

<span data-ttu-id="49c30-121">.NET リリースのライフ サイクルの詳細については、「[.NET Core と .NET 5 のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c30-121">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="dependencies"></a><span data-ttu-id="49c30-122">依存関係</span><span class="sxs-lookup"><span data-stu-id="49c30-122">Dependencies</span></span>

<span data-ttu-id="49c30-123">.NET をインストールするときに、特定の依存関係がインストールされない可能性があります ([手動インストール](#manual-install)のときなど)。</span><span class="sxs-lookup"><span data-stu-id="49c30-123">It's possible that when you install .NET, specific dependencies may not be installed, such as when [manually installing](#manual-install).</span></span> <span data-ttu-id="49c30-124">次の一覧に、Microsoft によってサポートされていて、インストールが必要な可能性のある依存関係がある Linux ディストリビューションの詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="49c30-124">The following list details Linux distributions that are supported by Microsoft and have dependencies you may need to install.</span></span> <span data-ttu-id="49c30-125">詳細については、ディストリビューションのページを確認してください。</span><span class="sxs-lookup"><span data-stu-id="49c30-125">Check the distribution page for more information:</span></span>

- [<span data-ttu-id="49c30-126">Alpine</span><span class="sxs-lookup"><span data-stu-id="49c30-126">Alpine</span></span>](linux-alpine.md#dependencies)
- [<span data-ttu-id="49c30-127">Debian</span><span class="sxs-lookup"><span data-stu-id="49c30-127">Debian</span></span>](linux-debian.md#dependencies)
- [<span data-ttu-id="49c30-128">CentOS</span><span class="sxs-lookup"><span data-stu-id="49c30-128">CentOS</span></span>](linux-centos.md#dependencies)
- [<span data-ttu-id="49c30-129">Fedora</span><span class="sxs-lookup"><span data-stu-id="49c30-129">Fedora</span></span>](linux-fedora.md#dependencies)
- [<span data-ttu-id="49c30-130">RHEL</span><span class="sxs-lookup"><span data-stu-id="49c30-130">RHEL</span></span>](linux-rhel.md#dependencies)
- [<span data-ttu-id="49c30-131">SLES</span><span class="sxs-lookup"><span data-stu-id="49c30-131">SLES</span></span>](linux-sles.md#dependencies)
- [<span data-ttu-id="49c30-132">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="49c30-132">Ubuntu</span></span>](linux-ubuntu.md#dependencies)

<span data-ttu-id="49c30-133">依存関係に関する一般的な情報については、「[自己完結型 Linux アプリケーション](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c30-133">For generic information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span></span>

### <a name="rpm-dependencies"></a><span data-ttu-id="49c30-134">RPM の依存関係</span><span class="sxs-lookup"><span data-stu-id="49c30-134">RPM dependencies</span></span>

<span data-ttu-id="49c30-135">お使いのディストリビューションが前の一覧になく、RPM ベースの場合は、次の依存関係が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="49c30-135">If your distribution wasn't previously listed, and is RPM-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="49c30-136">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="49c30-136">krb5-libs</span></span>
- <span data-ttu-id="49c30-137">libicu</span><span class="sxs-lookup"><span data-stu-id="49c30-137">libicu</span></span>
- <span data-ttu-id="49c30-138">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="49c30-138">openssl-libs</span></span>

<span data-ttu-id="49c30-139">ターゲット ランタイム環境の OpenSSL バージョンが 1.1 以降である場合は、**compat-openssl10** をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49c30-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

### <a name="deb-dependencies"></a><span data-ttu-id="49c30-140">DEB の依存関係</span><span class="sxs-lookup"><span data-stu-id="49c30-140">DEB dependencies</span></span>

<span data-ttu-id="49c30-141">お使いのディストリビューションが前の一覧になく、Debian ベースの場合は、次の依存関係が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="49c30-141">If your distribution wasn't previously listed, and is debian-based, you may need the following dependencies:</span></span>

- <span data-ttu-id="49c30-142">libc6</span><span class="sxs-lookup"><span data-stu-id="49c30-142">libc6</span></span>
- <span data-ttu-id="49c30-143">libgcc1</span><span class="sxs-lookup"><span data-stu-id="49c30-143">libgcc1</span></span>
- <span data-ttu-id="49c30-144">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="49c30-144">libgssapi-krb5-2</span></span>
- <span data-ttu-id="49c30-145">libicu67</span><span class="sxs-lookup"><span data-stu-id="49c30-145">libicu67</span></span>
- <span data-ttu-id="49c30-146">libssl1.1</span><span class="sxs-lookup"><span data-stu-id="49c30-146">libssl1.1</span></span>
- <span data-ttu-id="49c30-147">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="49c30-147">libstdc++6</span></span>
- <span data-ttu-id="49c30-148">zlib1g</span><span class="sxs-lookup"><span data-stu-id="49c30-148">zlib1g</span></span>

### <a name="common-dependencies"></a><span data-ttu-id="49c30-149">共通の依存関係</span><span class="sxs-lookup"><span data-stu-id="49c30-149">Common dependencies</span></span>

<span data-ttu-id="49c30-150">*System.Drawing.Common* アセンブリを使用する .NET アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="49c30-150">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="49c30-151">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="49c30-151">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="49c30-152">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="49c30-152">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="49c30-153">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c30-153">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="49c30-154">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="49c30-154">Scripted install</span></span>

<span data-ttu-id="49c30-155">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、**SDK** および **ランタイム** のインストールの自動化および管理者以外によるインストールのために使用されます。</span><span class="sxs-lookup"><span data-stu-id="49c30-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="49c30-156">このスクリプトは <https://dot.net/v1/dotnet-install.sh> からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="49c30-156">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

> <span data-ttu-id="49c30-157">![重要] スクリプトを実行するには Bash が必要です。</span><span class="sxs-lookup"><span data-stu-id="49c30-157">![IMPORTANT] Bash is required to run the script.</span></span>

<span data-ttu-id="49c30-158">スクリプトでは、最新の SDK の[長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) が既定でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="49c30-158">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="49c30-159">(LTS) バージョンではない場合がある現在のリリースをインストールするには、`-c Current` パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="49c30-159">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="49c30-160">SDK の代わりに .NET ランタイムをインストールするには、`--runtime` パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="49c30-160">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="49c30-161">特定のバージョンをインストールするには、`-c` パラメーターを変更して特定のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="49c30-161">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="49c30-162">次のコマンドでは、.NET SDK 5.0 がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="49c30-162">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="49c30-163">詳細については、「[dotnet-install スクリプト リファレンス](../tools/dotnet-install-script.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="49c30-163">For more information, see [dotnet-install scripts reference](../tools/dotnet-install-script.md).</span></span>

## <a name="manual-install"></a><span data-ttu-id="49c30-164">手動インストール</span><span class="sxs-lookup"><span data-stu-id="49c30-164">Manual install</span></span>

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="49c30-165">パッケージ マネージャーの代わりに、SDK とランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="49c30-165">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="49c30-166">手動インストールは、継続的インテグレーション テストの一環として、またはサポートされていない Linux ディストリビューションで、よく使用されます。</span><span class="sxs-lookup"><span data-stu-id="49c30-166">Manual install is commonly used as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="49c30-167">開発者またはユーザーの場合は、パッケージ マネージャーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="49c30-167">For a developer or user, it's better to use a package manager.</span></span>

<span data-ttu-id="49c30-168">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="49c30-168">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="49c30-169">まず、次のいずれかのサイトから SDK またはランタイムの **バイナリ** リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="49c30-169">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="49c30-170">✔️ [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="49c30-170">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="49c30-171">✔️ [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet/3.1)</span><span class="sxs-lookup"><span data-stu-id="49c30-171">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet/3.1)</span></span>
- <span data-ttu-id="49c30-172">✔️ [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet/2.1)</span><span class="sxs-lookup"><span data-stu-id="49c30-172">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet/2.1)</span></span>
- [<span data-ttu-id="49c30-173">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="49c30-173">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet)

<span data-ttu-id="49c30-174">次に、ダウンロードしたファイルを抽出し、`export` コマンドを使用して .NET で使用される変数を設定してから、.NET が PATH に含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="49c30-174">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="49c30-175">ランタイムを抽出し、.NET CLI コマンドをターミナルで使用できるようにするには、最初に .NET のバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="49c30-175">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="49c30-176">次に、ターミナルを開き、ファイルが保存されているディレクトリから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="49c30-176">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="49c30-177">アーカイブ ファイル名は、ダウンロードした内容によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="49c30-177">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="49c30-178">**次のコマンドを使用して、ダウンロードしたランタイムまたは SDK を抽出します。**</span><span class="sxs-lookup"><span data-stu-id="49c30-178">**Use the following commands to extract the runtime or SDK that you downloaded.**</span></span> <span data-ttu-id="49c30-179">必ず `DOTNET_FILE` の値を実際のファイル名に変更してください。</span><span class="sxs-lookup"><span data-stu-id="49c30-179">Remember to change the `DOTNET_FILE` value to your file name:</span></span>

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> <span data-ttu-id="49c30-180">上記の `export` コマンドを使用すると、それを実行したターミナル セッションでのみ .NET CLI コマンドを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="49c30-180">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="49c30-181">シェル プロファイルを編集して、コマンドを永続的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="49c30-181">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="49c30-182">Linux ではさまざまなシェルを使用でき、それぞれに異なるプロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="49c30-182">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="49c30-183">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="49c30-183">For example:</span></span>
>
> - <span data-ttu-id="49c30-184">**Bash シェル**: *~/.bash_profile*、 *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="49c30-184">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="49c30-185">**Korn シェル**: *~/.kshrc* または *.profile*</span><span class="sxs-lookup"><span data-stu-id="49c30-185">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="49c30-186">**Z シェル**: *~/.zshrc* または *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="49c30-186">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="49c30-187">シェルの適切なソース ファイルを編集し、既存の `PATH` ステートメントの末尾に `:$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="49c30-187">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="49c30-188">`PATH` ステートメントが含まれていない場合は、`export PATH=$PATH:$HOME/dotnet` を含む新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="49c30-188">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="49c30-189">また、ファイルの末尾に `export DOTNET_ROOT=$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="49c30-189">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="49c30-190">この方法では、別々の場所に異なるバージョンをインストールして、どのアプリケーションにどれを使用するかを明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="49c30-190">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="49c30-191">次のステップ</span><span class="sxs-lookup"><span data-stu-id="49c30-191">Next steps</span></span>

- [<span data-ttu-id="49c30-192">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="49c30-192">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="49c30-193">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="49c30-193">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
