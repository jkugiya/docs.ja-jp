---
title: SLES 上に .NET をインストールする - .NET
description: SLES に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: db8773c82417eda0deac04f95cfe8199621d04c4
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875266"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a><span data-ttu-id="9b4d8-103">SLES に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="9b4d8-103">Install the .NET SDK or the .NET Runtime on SLES</span></span>

<span data-ttu-id="9b4d8-104">.NET は SLES 上でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-104">.NET is supported on SLES.</span></span> <span data-ttu-id="9b4d8-105">この記事では、SLES 上に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-105">This article describes how to install .NET on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="9b4d8-106">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="9b4d8-106">Supported distributions</span></span>

<span data-ttu-id="9b4d8-107">次の表は、SLES 12 SP2 と SLES 15 の両方で現在サポートされている .NET リリースの一覧です。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-107">The following table is a list of currently supported .NET releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="9b4d8-108">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、SLES のバージョンがサポート終了になるまでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="9b4d8-109">✔️ は、SLES または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-109">A ✔️ indicates that the version of SLES or .NET is still supported.</span></span>
- <span data-ttu-id="9b4d8-110">❌ は、SLES または .NET のバージョンがその SLES のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-110">A ❌ indicates that the version of SLES or .NET isn't supported on that SLES release.</span></span>
- <span data-ttu-id="9b4d8-111">SLES のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-111">When both a version of SLES and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="9b4d8-112">SLES</span><span class="sxs-lookup"><span data-stu-id="9b4d8-112">SLES</span></span>                   | <span data-ttu-id="9b4d8-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9b4d8-113">.NET Core 2.1</span></span> | <span data-ttu-id="9b4d8-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9b4d8-114">.NET Core 3.1</span></span> | <span data-ttu-id="9b4d8-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="9b4d8-115">.NET 5.0</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="9b4d8-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="9b4d8-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="9b4d8-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="9b4d8-117">✔️ 2.1</span></span>        | <span data-ttu-id="9b4d8-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="9b4d8-118">✔️ 3.1</span></span>        | <span data-ttu-id="9b4d8-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="9b4d8-119">✔️ 5.0</span></span> |
| <span data-ttu-id="9b4d8-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="9b4d8-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="9b4d8-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="9b4d8-121">✔️ 2.1</span></span>        | <span data-ttu-id="9b4d8-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="9b4d8-122">✔️ 3.1</span></span>        | <span data-ttu-id="9b4d8-123">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="9b4d8-123">✔️ 5.0</span></span> |

<span data-ttu-id="9b4d8-124">次のバージョンの .NET Core は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="9b4d8-125">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="9b4d8-126">3.0</span><span class="sxs-lookup"><span data-stu-id="9b4d8-126">3.0</span></span>
- <span data-ttu-id="9b4d8-127">2.2</span><span class="sxs-lookup"><span data-stu-id="9b4d8-127">2.2</span></span>
- <span data-ttu-id="9b4d8-128">2.0</span><span class="sxs-lookup"><span data-stu-id="9b4d8-128">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="9b4d8-129">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="9b4d8-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="sles-15-"></a><span data-ttu-id="9b4d8-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="9b4d8-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="9b4d8-131">現時点では、SLES 15 Microsoft リポジトリ セットアップ パッケージによって "*microsoft-prod.repo*" ファイルが間違ったディレクトリにインストールされるため、zypper が .NET パッケージを見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET packages.</span></span> <span data-ttu-id="9b4d8-132">この問題を解決するには、正しいディレクトリにシンボリックリンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="9b4d8-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="9b4d8-133">SLES 12 ✔️</span></span>

<span data-ttu-id="9b4d8-134">.NET では、SLES 12 ファミリの最小要件として SP2 が必要です。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-134">.NET requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9b4d8-135">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="9b4d8-135">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="9b4d8-136">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9b4d8-136">Troubleshoot the package manager</span></span>

<span data-ttu-id="9b4d8-137">このセクションでは、パッケージ マネージャーを使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-137">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="9b4d8-138">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="9b4d8-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="9b4d8-139">依存関係</span><span class="sxs-lookup"><span data-stu-id="9b4d8-139">Dependencies</span></span>

<span data-ttu-id="9b4d8-140">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-140">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="9b4d8-141">ただし、手動で .NET をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-141">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="9b4d8-142">krb5</span><span class="sxs-lookup"><span data-stu-id="9b4d8-142">krb5</span></span>
- <span data-ttu-id="9b4d8-143">libicu</span><span class="sxs-lookup"><span data-stu-id="9b4d8-143">libicu</span></span>
- <span data-ttu-id="9b4d8-144">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="9b4d8-144">libopenssl1_1</span></span>

<span data-ttu-id="9b4d8-145">ターゲット ランタイム環境の OpenSSL バージョンが 1.1 以降である場合は、**compat-openssl10** をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-145">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="9b4d8-146">依存関係の詳細については、「[Self-contained Linux applications](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md)」(自己完結型 Linux アプリケーション) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-146">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="9b4d8-147">*System.Drawing.Common* アセンブリを使用する .NET アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-147">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="9b4d8-148">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="9b4d8-148">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="9b4d8-149">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-149">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="9b4d8-150">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b4d8-150">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b4d8-151">次の手順</span><span class="sxs-lookup"><span data-stu-id="9b4d8-151">Next steps</span></span>

- [<span data-ttu-id="9b4d8-152">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="9b4d8-152">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="9b4d8-153">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="9b4d8-153">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
