---
title: クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する
description: Azure クラウドおよび Windows コンテナーを使用して既存の .NET アプリケーションを最新化する | クラウドの CI/CD パイプラインと DevOps ツールを使用してアプリのライフサイクルを最新化する
ms.date: 12/21/2020
ms.openlocfilehash: f8517ebe8570b8d2be7b49c3cb9e1bc436076af2
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235340"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="e6c63-103">クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する</span><span class="sxs-lookup"><span data-stu-id="e6c63-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="e6c63-104">今日の企業は、市場での競争力を高めるために、迅速にイノベーションを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6c63-104">Today's businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="e6c63-105">高品質で最新のアプリケーションを提供するには DevOps ツールおよびプロセスが必要で、この繰り返されるイノベーション サイクルの実装に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="e6c63-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="e6c63-106">適切な DevOps ツールを使用すると、開発者は継続的デプロイを効率化し、革新的なアプリケーションをより迅速にユーザーに届けることができます。</span><span class="sxs-lookup"><span data-stu-id="e6c63-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="e6c63-107">継続的インテグレーションとデプロイの方法は確立されていますが、コンテナーを導入することにより、複数コンテナー アプリケーションを使用している場合は特に、新たな考慮事項が生じます。</span><span class="sxs-lookup"><span data-stu-id="e6c63-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="e6c63-108">Azure DevOps Services では、Azure DevOps Services の公式のデプロイ タスクにより、さまざまな環境への複数コンテナー アプリケーションの継続的インテグレーションとデプロイがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e6c63-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to various environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="e6c63-109">Azure Web App for Containers にデプロイする</span><span class="sxs-lookup"><span data-stu-id="e6c63-109">Deploy to an Azure Web App for Containers</span></span>](/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="e6c63-110">Azure Kubernetes Service にデプロイする</span><span class="sxs-lookup"><span data-stu-id="e6c63-110">Deploy to Azure Kubernetes Service</span></span>](/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="e6c63-111">ただし、Azure DevOps Services スクリプトベースのタスクを使用して、[Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) または DC/OS にデプロイすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e6c63-111">But you can also deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="e6c63-112">デプロイのアジリティを促進し続けるために、これらのツールにより、開発および CI/CD ソリューションを選択して、コンテナーのワークロードに対して、開発からテスト、運用までの優れたデプロイ エクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e6c63-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="e6c63-113">図 4-12 は、Azure Container Service で Kubernetes クラスターにデプロイする継続的デプロイ パイプラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="e6c63-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Kubernetes クラスターにデプロイする Azure DevOps Services のスクリーンショット。](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="e6c63-115">**図 4-12**</span><span class="sxs-lookup"><span data-stu-id="e6c63-115">**Figure 4-12.**</span></span> <span data-ttu-id="e6c63-116">Kubernetes クラスターにデプロイする、Azure DevOps Services の継続的デプロイ パイプライン</span><span class="sxs-lookup"><span data-stu-id="e6c63-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e6c63-117">[前へ](modernize-your-apps-with-monitoring-and-telemetry.md)
>[次へ](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="e6c63-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
