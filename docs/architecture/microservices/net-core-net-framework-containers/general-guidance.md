---
title: 一般的なガイダンス
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 一般的なガイダンス'
ms.date: 01/13/2021
ms.openlocfilehash: 4fd2d936c524cb3e5ae463038eaffe88b459d2bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187952"
---
# <a name="general-guidance"></a><span data-ttu-id="90018-103">一般的なガイダンス</span><span class="sxs-lookup"><span data-stu-id="90018-103">General guidance</span></span>

<span data-ttu-id="90018-104">このセクションでは、.NET 5 または .NET Framework を選択する場合の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="90018-104">This section provides a summary of when to choose .NET 5 or .NET Framework.</span></span> <span data-ttu-id="90018-105">後続のセクションでこれらの選択の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="90018-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="90018-106">次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET 5 と Linux または Windows のコンテナーを併用します。</span><span class="sxs-lookup"><span data-stu-id="90018-106">Use .NET 5, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="90018-107">クロスプラット フォームが必要である。</span><span class="sxs-lookup"><span data-stu-id="90018-107">You have cross-platform needs.</span></span> <span data-ttu-id="90018-108">たとえば、Linux と Windows のコンテナーの両方を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="90018-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="90018-109">アプリケーション アーキテクチャがマイクロサービスに基づく場合。</span><span class="sxs-lookup"><span data-stu-id="90018-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="90018-110">コンテナーを高速で起動する必要があり、かつコンテナーあたりのフットプリントを小さくして密度を高めたり、ハードウェア ユニットあたりのコンテナーを増やしてコストを削減したりしたい場合。</span><span class="sxs-lookup"><span data-stu-id="90018-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="90018-111">つまり、コンテナー化された .NET アプリケーションを新たに作成する場合には、.NET 5 を既定の選択肢として考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90018-111">In short, when you create new containerized .NET applications, you should consider .NET 5 as the default choice.</span></span> <span data-ttu-id="90018-112">これには多くの利点があり、コンテナーの理念や作業スタイルとぴったりと適合します。</span><span class="sxs-lookup"><span data-stu-id="90018-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="90018-113">さらに .NET 5 を使用する利点は、同じマシンで複数の .NET バージョンのアプリケーションを同時に実行できることです。</span><span class="sxs-lookup"><span data-stu-id="90018-113">An extra benefit of using .NET 5 is that you can run side-by-side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="90018-114">この利点は、コンテナーを使用しないサーバーまたは VM にとってはさらに重要になります。コンテナーは、アプリが必要とする .NET バージョンを特定するためです。</span><span class="sxs-lookup"><span data-stu-id="90018-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="90018-115">(基礎となる OS と互換性がある場合。)</span><span class="sxs-lookup"><span data-stu-id="90018-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="90018-116">次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET Framework を使用します。</span><span class="sxs-lookup"><span data-stu-id="90018-116">Use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="90018-117">現在、アプリケーションで .NET Framework を使用し、Windows で強い依存関係がある場合。</span><span class="sxs-lookup"><span data-stu-id="90018-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="90018-118">.NET 5 でサポートされていない Windows API を使用する必要がある。</span><span class="sxs-lookup"><span data-stu-id="90018-118">You need to use Windows APIs that are not supported by .NET 5.</span></span>

- <span data-ttu-id="90018-119">.NET 5 で使用できないサードパーティ製の .NET ライブラリまたは NuGet パッケージを使用する必要がある。</span><span class="sxs-lookup"><span data-stu-id="90018-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET 5.</span></span>

<span data-ttu-id="90018-120">Docker で .NET Framework を使用すると、展開に関する問題を最小限に抑えて、展開のエクスペリエンスを改善できます。</span><span class="sxs-lookup"><span data-stu-id="90018-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="90018-121">この ["リスト アンド シフト" シナリオ](https://aka.ms/liftandshiftwithcontainersebook)は、ASP.NET WebForms、MVC Web アプリ、WCF (Windows Communication Foundation) サービスなどの従来の .NET Framework を使用して開発されたレガシー アプリケーションをコンテナー化する場合に重要です。</span><span class="sxs-lookup"><span data-stu-id="90018-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="90018-122">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="90018-122">Additional resources</span></span>

- <span data-ttu-id="90018-123">**電子書籍: Modernize existing .NET Framework applications with Azure and Windows Containers (Azure および Windows コンテナーで既存の .NET Framework アプリケーションを最新化する)**</span><span class="sxs-lookup"><span data-stu-id="90018-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    <https://aka.ms/liftandshiftwithcontainersebook>

- <span data-ttu-id="90018-124">**サンプル アプリ:Windows コンテナーを使用した従来の ASP.NET Web アプリの最新化**</span><span class="sxs-lookup"><span data-stu-id="90018-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
><span data-ttu-id="90018-125">[前へ](index.md)
>[次へ](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="90018-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
