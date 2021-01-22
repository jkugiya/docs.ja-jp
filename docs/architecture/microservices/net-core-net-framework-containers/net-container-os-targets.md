---
title: .NET コンテナーで対象とする OS
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | .NET コンテナーで対象とする OS'
ms.date: 01/13/2021
ms.openlocfilehash: 1b914d9afca9ade37f13e639f73001b91f338d26
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187985"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="12abd-103">.NET コンテナーで対象とする OS</span><span class="sxs-lookup"><span data-stu-id="12abd-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="12abd-104">Docker でサポートされているオペレーティング システムの多様性と、.NET Framework と .NET 5 の違いを考慮し、使用しているフレームワークに応じて特定の OS と特定のバージョンをターゲットにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="12abd-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET 5, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="12abd-105">Windows の場合、Windows Server Core または Windows Nano Server を使用できます。</span><span class="sxs-lookup"><span data-stu-id="12abd-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="12abd-106">これらの Windows バージョンには、.NET Framework または .NET 5 でそれぞれ必要になる可能性がある異なる特性 (Windows Server Core の IIS と Nano Server の Kestrel のような自己ホスト型 Web サーバー) があります。</span><span class="sxs-lookup"><span data-stu-id="12abd-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET 5, respectively.</span></span>

<span data-ttu-id="12abd-107">Linux の場合、複数のディストリビューションを利用できます。また、Linux は公式の .NET Docker イメージ (Debian など) でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="12abd-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="12abd-108">図 3-1 では、使用されている .NET Framework に応じて利用可能な OS のバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="12abd-108">In Figure 3-1, you can see the possible OS version depending on the .NET framework used.</span></span>

![どの .NET コンテナーでどの OS を使用するかを示す図。](./media/net-container-os-targets/targeting-operating-systems.png)

<span data-ttu-id="12abd-110">**図 3-1.**</span><span class="sxs-lookup"><span data-stu-id="12abd-110">**Figure 3-1.**</span></span> <span data-ttu-id="12abd-111">.NET Framework のバージョンに応じて対象にすることができるオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="12abd-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="12abd-112">.NET Framework のレガシー アプリケーションをデプロイする場合は、レガシー アプリと IIS と互換性がある、Windows Server Core をターゲットにする必要がありますが、より大きなイメージが含まれます。</span><span class="sxs-lookup"><span data-stu-id="12abd-112">When deploying legacy .NET Framework applications you have to target Windows Server Core, compatible with legacy apps and IIS, but it has a larger image.</span></span> <span data-ttu-id="12abd-113">.NET 5 アプリケーションをデプロイする場合は、クラウドに最適化され、Kestrel を使用し、小型で起動が速い Windows Nano Server をターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="12abd-113">When deploying .NET 5 applications, you can target Windows Nano Server, which is cloud optimized, uses Kestrel and is smaller and starts faster.</span></span> <span data-ttu-id="12abd-114">Debian や Alpine などをサポートしている Linux もターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="12abd-114">You can also target Linux, supporting Debian, Alpine, and others.</span></span> <span data-ttu-id="12abd-115">同様に、Kestrel を使用し、より小さく起動が速くなります。</span><span class="sxs-lookup"><span data-stu-id="12abd-115">Also uses Kestrel, is smaller, and starts faster.</span></span>

<span data-ttu-id="12abd-116">別の Linux ディストリビューションを使用したい場合や、Microsoft が提供していないバージョンのイメージが必要な場合は、独自の Docker イメージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="12abd-116">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="12abd-117">たとえば、従来の .NET Framework と Windows Server Core 上で実行されている ASP.NET Core を使用してイメージを作成することができます (ただし、Docker の場合はあまり一般的ではないシナリオです)。</span><span class="sxs-lookup"><span data-stu-id="12abd-117">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12abd-118">Windows Server Core イメージを使用する場合、完全な Windows イメージと比較すると、一部の DLL が不足している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="12abd-118">When using Windows Server Core images, you might find that some DLLs are missing, when compared to full Windows images.</span></span> <span data-ttu-id="12abd-119">この [GitHub コメント](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)に記載されているように、カスタムの Server Core イメージを作成し、不足しているファイルをイメージのビルド時に追加することで、この問題を解決できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="12abd-119">You might be able to solve this problem by creating a custom Server Core image, adding the missing files at image build time, as mentioned in this [GitHub comment](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).</span></span>

<span data-ttu-id="12abd-120">Dockerfile ファイルにイメージ名を追加すると、次の例のように、使用するタグに応じてオペレーティング システムとバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="12abd-120">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="12abd-121">イメージ</span><span class="sxs-lookup"><span data-stu-id="12abd-121">Image</span></span> | <span data-ttu-id="12abd-122">コメント</span><span class="sxs-lookup"><span data-stu-id="12abd-122">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="12abd-123">mcr.microsoft.com/dotnet/runtime:5.0</span><span class="sxs-lookup"><span data-stu-id="12abd-123">mcr.microsoft.com/dotnet/runtime:5.0</span></span> | <span data-ttu-id="12abd-124">.NET 5 マルチアーキテクチャ: Docker ホストに応じて、Linux と Windows Nano Server をサポートします。</span><span class="sxs-lookup"><span data-stu-id="12abd-124">.NET 5 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="12abd-125">mcr.microsoft.com/dotnet/aspnet:5.0</span><span class="sxs-lookup"><span data-stu-id="12abd-125">mcr.microsoft.com/dotnet/aspnet:5.0</span></span> | <span data-ttu-id="12abd-126">ASP.NET Core 5.0 マルチアーキテクチャ: Docker ホストに応じて、Linux と Windows Nano Server をサポートします。</span><span class="sxs-lookup"><span data-stu-id="12abd-126">ASP.NET Core 5.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="12abd-127">aspnetcore イメージでは、ASP.NET Core 用に 少しの最適化が行われています。</span><span class="sxs-lookup"><span data-stu-id="12abd-127">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="12abd-128">mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim</span><span class="sxs-lookup"><span data-stu-id="12abd-128">mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim</span></span> | <span data-ttu-id="12abd-129">Linux Debian ディストリビューションの .NET 5 ランタイムのみ</span><span class="sxs-lookup"><span data-stu-id="12abd-129">.NET 5 runtime-only on Linux Debian distro</span></span> |
| <span data-ttu-id="12abd-130">mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809</span><span class="sxs-lookup"><span data-stu-id="12abd-130">mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809</span></span> | <span data-ttu-id="12abd-131">Windows Nano Server (Windows Server バージョン 1809) の .NET 5 ランタイムのみ</span><span class="sxs-lookup"><span data-stu-id="12abd-131">.NET 5 runtime-only on Windows Nano Server (Windows Server version 1809)</span></span> |

## <a name="additional-resources"></a><span data-ttu-id="12abd-132">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="12abd-132">Additional resources</span></span>

- <span data-ttu-id="12abd-133">**WindowsCodecsExt.dll が見つからないため、BitmapDecoder が失敗する (GitHub の問題)**</span><span class="sxs-lookup"><span data-stu-id="12abd-133">**BitmapDecoder fails due to missing WindowsCodecsExt.dll (GitHub issue)**</span></span>  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> <span data-ttu-id="12abd-134">[前へ](container-framework-choice-factors.md)
> [次へ](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="12abd-134">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
