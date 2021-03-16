---
title: Fedora に .NET をインストールする - .NET
description: Fedora に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 02/17/2021
ms.openlocfilehash: efaad4788db2200b1a47f9b4ae2414730588c6ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255759"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="fdf46-103">Fedora に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="fdf46-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="fdf46-104">.NET は Fedora でサポートされており、この記事では Fedora に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fdf46-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="fdf46-105">Fedora のバージョンがサポート対象外となった場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="fdf46-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="fdf46-106">パッケージ マネージャーを使用せずに .NET をインストールする方法の詳細については、次の記事のいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdf46-106">For more information on installing .NET without a package manager, see one of the following articles:</span></span>

- [<span data-ttu-id="fdf46-107">Snap を使用して .NET SDK または .NET ランタイムをインストールする。</span><span class="sxs-lookup"><span data-stu-id="fdf46-107">Install the .NET SDK or the .NET Runtime with Snap.</span></span>](linux-snap.md)
- [<span data-ttu-id="fdf46-108">スクリプトを使用して .NET SDK または .NET ランタイムをインストールする。</span><span class="sxs-lookup"><span data-stu-id="fdf46-108">Install the .NET SDK or the .NET Runtime with a script.</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="fdf46-109">手動で .NET SDK または .NET ランタイムをインストールする。</span><span class="sxs-lookup"><span data-stu-id="fdf46-109">Install the .NET SDK or the .NET Runtime manually.</span></span>](linux-scripted-manual.md#manual-install)

## <a name="install-net-50"></a><span data-ttu-id="fdf46-110">.NET 5.0 をインストールする</span><span class="sxs-lookup"><span data-stu-id="fdf46-110">Install .NET 5.0</span></span>

<span data-ttu-id="fdf46-111">Fedora の既定のパッケージ リポジトリで利用可能な最新バージョンの .NET は、.NET 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="fdf46-111">The latest version of .NET available in the default package repositories for Fedora is .NET 5.0.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="fdf46-112">.NET Core 3.1 をインストールする</span><span class="sxs-lookup"><span data-stu-id="fdf46-112">Install .NET Core 3.1</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="fdf46-113">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="fdf46-113">Supported distributions</span></span>

<span data-ttu-id="fdf46-114">現在サポートされている .NET リリースと、それらがサポートされている Fedora のバージョンの一覧は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fdf46-114">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="fdf46-115">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Fedora のバージョンがサポート終了になる](https://fedoraproject.org/wiki/End_of_life)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="fdf46-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="fdf46-116">✔️ は、Fedora または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fdf46-116">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="fdf46-117">❌ は、Fedora または .NET のバージョンがその Fedora のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="fdf46-117">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="fdf46-118">Fedora のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fdf46-118">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="fdf46-119">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="fdf46-119">.NET Version</span></span>  | <span data-ttu-id="fdf46-120">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-120">Fedora 33 ✔️</span></span> | <span data-ttu-id="fdf46-121">32 ✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-121">32 ✔️</span></span> | <span data-ttu-id="fdf46-122">31 ❌</span><span class="sxs-lookup"><span data-stu-id="fdf46-122">31 ❌</span></span> | <span data-ttu-id="fdf46-123">30 ❌</span><span class="sxs-lookup"><span data-stu-id="fdf46-123">30 ❌</span></span> | <span data-ttu-id="fdf46-124">29 ❌</span><span class="sxs-lookup"><span data-stu-id="fdf46-124">29 ❌</span></span> | <span data-ttu-id="fdf46-125">28 ❌</span><span class="sxs-lookup"><span data-stu-id="fdf46-125">28 ❌</span></span> | <span data-ttu-id="fdf46-126">27 ❌</span><span class="sxs-lookup"><span data-stu-id="fdf46-126">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="fdf46-127">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="fdf46-127">.NET 5.0</span></span>      | <span data-ttu-id="fdf46-128">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-128">✔️</span></span>        | <span data-ttu-id="fdf46-129">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-129">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="fdf46-130">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="fdf46-130">.NET Core 3.1</span></span> | <span data-ttu-id="fdf46-131">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-131">✔️</span></span>        | <span data-ttu-id="fdf46-132">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-132">✔️</span></span> | <span data-ttu-id="fdf46-133">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-133">✔️</span></span>|<span data-ttu-id="fdf46-134">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-134">✔️</span></span> |<span data-ttu-id="fdf46-135">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-135">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="fdf46-136">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fdf46-136">.NET Core 2.1</span></span> | <span data-ttu-id="fdf46-137">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-137">✔️</span></span>        | <span data-ttu-id="fdf46-138">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-138">✔️</span></span> | <span data-ttu-id="fdf46-139">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-139">✔️</span></span>|<span data-ttu-id="fdf46-140">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-140">✔️</span></span> |<span data-ttu-id="fdf46-141">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-141">✔️</span></span> |<span data-ttu-id="fdf46-142">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-142">✔️</span></span>  |<span data-ttu-id="fdf46-143">✔️</span><span class="sxs-lookup"><span data-stu-id="fdf46-143">✔️</span></span> |

<span data-ttu-id="fdf46-144">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="fdf46-144">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="fdf46-145">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="fdf46-145">The downloads for these still remain published:</span></span>

- <span data-ttu-id="fdf46-146">3.0</span><span class="sxs-lookup"><span data-stu-id="fdf46-146">3.0</span></span>
- <span data-ttu-id="fdf46-147">2.2</span><span class="sxs-lookup"><span data-stu-id="fdf46-147">2.2</span></span>
- <span data-ttu-id="fdf46-148">2.0</span><span class="sxs-lookup"><span data-stu-id="fdf46-148">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="fdf46-149">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="fdf46-149">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="fdf46-150">依存関係</span><span class="sxs-lookup"><span data-stu-id="fdf46-150">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="fdf46-151">古いディストリビューションにインストールする</span><span class="sxs-lookup"><span data-stu-id="fdf46-151">Install on older distributions</span></span>

<span data-ttu-id="fdf46-152">古いバージョンの Fedora の既定のパッケージ リポジトリには、.NET Core が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="fdf46-152">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="fdf46-153">[snap](linux-snap.md)、[_dotnet-install.sh_ スクリプト](linux-scripted-manual.md#scripted-install)、または Microsoft のリポジトリを使用して、.NET をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="fdf46-153">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="fdf46-154">最初に、Microsoft 署名キーを信頼されたキーのリストに追加します。</span><span class="sxs-lookup"><span data-stu-id="fdf46-154">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="fdf46-155">次に、Microsoft パッケージ リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="fdf46-155">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="fdf46-156">リポジトリのソースは、お使いの Fedora のバージョンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="fdf46-156">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="fdf46-157">Fedora のバージョン</span><span class="sxs-lookup"><span data-stu-id="fdf46-157">Fedora Version</span></span> | <span data-ttu-id="fdf46-158">パッケージ リポジトリ</span><span class="sxs-lookup"><span data-stu-id="fdf46-158">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="fdf46-159">31</span><span class="sxs-lookup"><span data-stu-id="fdf46-159">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="fdf46-160">30</span><span class="sxs-lookup"><span data-stu-id="fdf46-160">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="fdf46-161">29</span><span class="sxs-lookup"><span data-stu-id="fdf46-161">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="fdf46-162">28</span><span class="sxs-lookup"><span data-stu-id="fdf46-162">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="fdf46-163">27</span><span class="sxs-lookup"><span data-stu-id="fdf46-163">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fdf46-164">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="fdf46-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="fdf46-165">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fdf46-165">Troubleshoot the package manager</span></span>

<span data-ttu-id="fdf46-166">このセクションでは、パッケージ マネージャーを使用して .NET または .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fdf46-166">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="fdf46-167">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="fdf46-167">Unable to find package</span></span>

<span data-ttu-id="fdf46-168">パッケージ マネージャーを使用せずに .NET をインストールする方法の詳細については、次の記事のいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdf46-168">For more information on installing .NET without a package manager, see one of the following articles:</span></span>

- [<span data-ttu-id="fdf46-169">Snap を使用して .NET SDK または .NET ランタイムをインストールする。</span><span class="sxs-lookup"><span data-stu-id="fdf46-169">Install the .NET SDK or the .NET Runtime with Snap.</span></span>](linux-snap.md)
- [<span data-ttu-id="fdf46-170">スクリプトを使用して .NET SDK または .NET ランタイムをインストールする。</span><span class="sxs-lookup"><span data-stu-id="fdf46-170">Install the .NET SDK or the .NET Runtime with a script.</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="fdf46-171">手動で .NET SDK または .NET ランタイムをインストールする。</span><span class="sxs-lookup"><span data-stu-id="fdf46-171">Install the .NET SDK or the .NET Runtime manually.</span></span>](linux-scripted-manual.md#manual-install)

### <a name="failed-to-fetch"></a><span data-ttu-id="fdf46-172">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="fdf46-172">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="fdf46-173">次のステップ</span><span class="sxs-lookup"><span data-stu-id="fdf46-173">Next steps</span></span>

- [<span data-ttu-id="fdf46-174">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="fdf46-174">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="fdf46-175">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="fdf46-175">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
