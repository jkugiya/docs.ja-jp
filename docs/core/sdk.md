---
title: .NET SDK の概要
description: .NET プロジェクトの作成に使用するライブラリとツールのセットである、.NET SDK について説明します。
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 5236d4abec5dcbf950059dd906958158cfb592fe
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216142"
---
# <a name="net-sdk-overview"></a><span data-ttu-id="01249-103">.NET SDK の概要</span><span class="sxs-lookup"><span data-stu-id="01249-103">.NET SDK overview</span></span>

<span data-ttu-id="01249-104">.NET SDK は一連のライブラリとツールであり、開発者はこれを利用して .NET のアプリケーションやライブラリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="01249-104">The .NET SDK is a set of libraries and tools that allow developers to create .NET applications and libraries.</span></span> <span data-ttu-id="01249-105">それには、アプリケーションのビルドと実行に使用される次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="01249-105">It contains the following components that are used to build and run applications:</span></span>

- <span data-ttu-id="01249-106">.NET CLI。</span><span class="sxs-lookup"><span data-stu-id="01249-106">The .NET CLI.</span></span>
- <span data-ttu-id="01249-107">.NET ライブラリとランタイム。</span><span class="sxs-lookup"><span data-stu-id="01249-107">.NET libraries and runtime.</span></span>
- <span data-ttu-id="01249-108">`dotnet` [ドライバー](tools/index.md#driver)。</span><span class="sxs-lookup"><span data-stu-id="01249-108">The `dotnet` [driver](tools/index.md#driver).</span></span>

## <a name="acquiring-the-net-sdk"></a><span data-ttu-id="01249-109">.NET SDK の入手</span><span class="sxs-lookup"><span data-stu-id="01249-109">Acquiring the .NET SDK</span></span>

<span data-ttu-id="01249-110">他のツールと同様に、最初にコンピューターにツールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01249-110">As with any tooling, the first thing is to get the tools to your machine.</span></span> <span data-ttu-id="01249-111">シナリオに応じて、次のいずれかの方法で SDK をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="01249-111">Depending on your scenario, you can install the SDK using one of the following methods:</span></span>

- <span data-ttu-id="01249-112">ネイティブ インストーラーを使う。</span><span class="sxs-lookup"><span data-stu-id="01249-112">Use the native installers.</span></span>
- <span data-ttu-id="01249-113">インストール シェル スクリプトを使う。</span><span class="sxs-lookup"><span data-stu-id="01249-113">Use the installation shell script.</span></span>

<span data-ttu-id="01249-114">開発者のコンピューターでは、ネイティブ インストーラーが利用されることが多いです。</span><span class="sxs-lookup"><span data-stu-id="01249-114">The native installers are primarily meant for developer's machines.</span></span> <span data-ttu-id="01249-115">SDK はサポートされるプラットフォームのネイティブ インストール メカニズムにより配信されます。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルです。</span><span class="sxs-lookup"><span data-stu-id="01249-115">The SDK is distributed using each supported platform's native install mechanism, such as DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="01249-116">これらのインストーラーでは、インストール直後に、ユーザーが SDK を使うために必要な環境がインストールされて設定されます。</span><span class="sxs-lookup"><span data-stu-id="01249-116">These installers install and set up the environment as needed for the user to use the SDK immediately after the install.</span></span> <span data-ttu-id="01249-117">ただし、コンピューター上で管理者特権も必要になります。</span><span class="sxs-lookup"><span data-stu-id="01249-117">However, they also require administrative privileges on the machine.</span></span> <span data-ttu-id="01249-118">インストールする SDK は、[.NET ダウンロード](https://dotnet.microsoft.com/download) ページで見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="01249-118">You can find the SDK to install on the [.NET downloads](https://dotnet.microsoft.com/download) page.</span></span>

<span data-ttu-id="01249-119">一方、インストール スクリプトでは、管理者特権は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="01249-119">Install scripts, on the other hand, don't require administrative privileges.</span></span> <span data-ttu-id="01249-120">ただし、いかなる前提条件もコンピューターにインストールされません。前提条件はすべてユーザーが手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01249-120">However, they also don't install any prerequisites on the machine; you need to install all of the prerequisites manually.</span></span> <span data-ttu-id="01249-121">スクリプトは、通常、管理者特権なしでツールをインストールするとき、ビルド サーバーを設定するために利用されます (上の前提条件警告に注意してください)。</span><span class="sxs-lookup"><span data-stu-id="01249-121">The scripts are meant mostly for setting up build servers or when you wish to install the tools without admin privileges (do note the prerequisites caveat above).</span></span> <span data-ttu-id="01249-122">詳しくは、[インストール スクリプト リファレンス](tools/dotnet-install-script.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01249-122">You can find more information in the [install script reference](tools/dotnet-install-script.md) article.</span></span> <span data-ttu-id="01249-123">お使いの CI ビルド サーバーで SDK を設定する方法について関心がある場合は、「[継続的インテグレーション (CI) で .NET SDK とツールを使用する](tools/using-ci-with-cli.md)」の記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01249-123">If you're interested in how to set up the SDK on your CI build server, see the [Using .NET SDK and tools in Continuous Integration (CI)](tools/using-ci-with-cli.md) article.</span></span>

<span data-ttu-id="01249-124">既定では、SDK は "side-by-side" (SxS) 方式でインストールされます。つまり、複数のバージョンを 1 台のコンピューター上にいつでも共存させることができます。</span><span class="sxs-lookup"><span data-stu-id="01249-124">By default, the SDK installs in a "side-by-side" (SxS) manner, which means multiple versions can coexist at any given time on a single machine.</span></span> <span data-ttu-id="01249-125">CLI コマンドを実行したときにバージョンが選択される方法について詳しくは、[使用する .NET のバージョンの選択](versions/selection.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01249-125">How the version gets picked when you're running CLI commands is explained in more detail in the [Select the .NET version to use](versions/selection.md) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="01249-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="01249-126">See also</span></span>

- [<span data-ttu-id="01249-127">.NET CLI の概要</span><span class="sxs-lookup"><span data-stu-id="01249-127">.NET CLI overview</span></span>](tools/index.md)
- [<span data-ttu-id="01249-128">.NET のバージョン管理の概要</span><span class="sxs-lookup"><span data-stu-id="01249-128">.NET versioning overview</span></span>](versions/index.md)
- [<span data-ttu-id="01249-129">.NET ランタイムと SDK を削除する方法</span><span class="sxs-lookup"><span data-stu-id="01249-129">How to remove the .NET runtime and SDK</span></span>](install/remove-runtime-sdk-versions.md)
- [<span data-ttu-id="01249-130">使用する .NET のバージョンを選択する</span><span class="sxs-lookup"><span data-stu-id="01249-130">Select the .NET version to use</span></span>](versions/selection.md)
