---
title: コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
description: Azure Cloud および Windows コンテナーで既存の .NET アプリケーションを最新化する |コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択
ms.date: 02/18/2020
ms.openlocfilehash: fcb9a0e7277f5ce31309f52aff63d579b0bb9a02
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079610"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="f3a3a-103">コンテナー ベース アプリケーション用の Azure コンピューティング プラットフォームの選択</span><span class="sxs-lookup"><span data-stu-id="f3a3a-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="f3a3a-104">前のセクションを読まれたらお気づきのように、Azure は複数の選択肢を提供するオープン クラウドです。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="f3a3a-105">ニーズに最適なものを使用できますが、ここにはコンテナー化されたアプリケーションに使用する製品やテクノロジに関する質問も表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="f3a3a-106">*既定の* 推奨事項として、このガイダンスで推奨される主な条件を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="f3a3a-107">**単一モノリシック アプリ:** Azure App Service を選ぶ</span><span class="sxs-lookup"><span data-stu-id="f3a3a-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="f3a3a-108">**n 層アプリ:** バックエンド サービスが 1 つまたは少数の場合は、Azure Kubernetes Service (AKS) や App Service などのオーケストレーターを選択する</span><span class="sxs-lookup"><span data-stu-id="f3a3a-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS) or App Service if you have a single or a few back-end services</span></span>
- <span data-ttu-id="f3a3a-109">**マイクロサービス:** AKS または Azure Web Apps for Containers を選ぶ</span><span class="sxs-lookup"><span data-stu-id="f3a3a-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="f3a3a-110">**サーバーレス関数とイベント ハンドラー:** Azure Functions を選ぶ</span><span class="sxs-lookup"><span data-stu-id="f3a3a-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="f3a3a-111">**大規模なバッチ:** Azure Batch を選ぶ</span><span class="sxs-lookup"><span data-stu-id="f3a3a-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="f3a3a-112">ただし、製品の選択は、特定のアプリケーションのニーズと特性によって異なるため、この推奨事項が全面的に該当するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-112">However, this recommendation should be taken with a pinch of salt, as the product's selection will depend on your specific application's needs and characteristics.</span></span> <span data-ttu-id="f3a3a-113">すべてのアプリケーションが同様の種類のように見えても、すべてが同じというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="f3a3a-114">アプリケーションのニーズをより詳しく分析した後、選択した製品がニーズとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-114">After a deeper analysis of the application's needs, the product selected could be different.</span></span> <span data-ttu-id="f3a3a-115">しかし、出発点として、特定の優先順位に基づいて評価とテストを開始できる最初のガイダンスを用意することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="f3a3a-116">次の図で、さまざまな種類のアプリの内訳と、実行可能な推奨される Azure ホスティング シナリオを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3a3a-116">In the following table, you can see a breakdown of different kinds of apps and their possible and recommended Azure hosting scenarios.</span></span>

| <span data-ttu-id="f3a3a-117">アプリケーションのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="f3a3a-117">Application Architecture</span></span> | <span data-ttu-id="f3a3a-118">VM - Azure Virtual Machines</span><span class="sxs-lookup"><span data-stu-id="f3a3a-118">VMs - Azure Virtual Machines</span></span> | <span data-ttu-id="f3a3a-119">ACI - Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="f3a3a-119">ACI - Azure Container Instances</span></span> | <span data-ttu-id="f3a3a-120">Azure App Service (コンテナーあり/なし)</span><span class="sxs-lookup"><span data-stu-id="f3a3a-120">Azure App Service (w-w/o containers)</span></span> | <span data-ttu-id="f3a3a-121">AKS - Azure Kubernetes Services</span><span class="sxs-lookup"><span data-stu-id="f3a3a-121">AKS - Azure Kubernetes Services</span></span> | <span data-ttu-id="f3a3a-122">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="f3a3a-122">Azure Functions</span></span> | <span data-ttu-id="f3a3a-123">Azure Batch</span><span class="sxs-lookup"><span data-stu-id="f3a3a-123">Azure Batch</span></span> |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| <span data-ttu-id="f3a3a-124">**Web アプリ (モノリシック)**</span><span class="sxs-lookup"><span data-stu-id="f3a3a-124">**Web apps (Monolithic)**</span></span>         | ![VM で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![App Service で推奨](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| <span data-ttu-id="f3a3a-129">**N 層アプリ (サービス)**</span><span class="sxs-lookup"><span data-stu-id="f3a3a-129">**N-Tier apps (Services)**</span></span>        | ![VM で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![App Service で推奨](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Azure Fuctions で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| <span data-ttu-id="f3a3a-135">**クラウドネイティブ (マイクロサービス)**</span><span class="sxs-lookup"><span data-stu-id="f3a3a-135">**Cloud-Native (Microservices)**</span></span>  | | ![ACI で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) <br/> <span data-ttu-id="f3a3a-138">(&nbsp;コンテナーあり)</span><span class="sxs-lookup"><span data-stu-id="f3a3a-138">(With&nbsp;containers)</span></span> | ![AKS で推奨](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> <span data-ttu-id="f3a3a-140">(Linux&nbsp;コンテナー)</span><span class="sxs-lookup"><span data-stu-id="f3a3a-140">(Linux&nbsp;containers)</span></span>| ![Azure Functions で推奨](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> <span data-ttu-id="f3a3a-142">(イベントドリブン)</span><span class="sxs-lookup"><span data-stu-id="f3a3a-142">(Event&#x2011;driven)</span></span> | |
| <span data-ttu-id="f3a3a-143">**バッチ/ジョブ (バックグラウンド タスク)**</span><span class="sxs-lookup"><span data-stu-id="f3a3a-143">**Batch/Jobs (Background tasks)**</span></span> | ![VM で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![App Service で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![AKS で可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Azure Functions で推奨](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> <span data-ttu-id="f3a3a-149">(バックグラウンド&nbsp;タスク)</span><span class="sxs-lookup"><span data-stu-id="f3a3a-149">(Background&nbsp;tasks)</span></span> | ![Azure Batch で推奨](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> <span data-ttu-id="f3a3a-151">(大規模)</span><span class="sxs-lookup"><span data-stu-id="f3a3a-151">(Large&#x2011;scale)</span></span> |

<span data-ttu-id="f3a3a-152">**凡例**</span><span class="sxs-lookup"><span data-stu-id="f3a3a-152">**Legend**</span></span>

![推奨アイコン](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <span data-ttu-id="f3a3a-154">推奨 </span><span class="sxs-lookup"><span data-stu-id="f3a3a-154">Recommended </span></span>\
![可能アイコン](media/choosing-azure-compute-options-for-container-based-applications/possible.png) <span data-ttu-id="f3a3a-156">可能</span><span class="sxs-lookup"><span data-stu-id="f3a3a-156">Possible</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f3a3a-157">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="f3a3a-157">Additional resources</span></span>

- <span data-ttu-id="f3a3a-158">**アプリケーションの Azure コンピューティング サービスを選択する**</span><span class="sxs-lookup"><span data-stu-id="f3a3a-158">**Choose an Azure compute service for your application**</span></span>

    <https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree>

> [!div class="step-by-step"]
> <span data-ttu-id="f3a3a-159">[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="f3a3a-159">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
