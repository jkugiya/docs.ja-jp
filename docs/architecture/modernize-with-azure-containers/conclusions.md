---
title: まとめ
description: Azure Cloud と Windows コンテナーで既存の .NET アプリケーションを最新化する | 結論
ms.date: 10/26/2017
ms.openlocfilehash: c7c4042b224577238ae74bd786d4803e487998e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "69578485"
---
# <a name="conclusions"></a><span data-ttu-id="bb3ce-103">まとめ</span><span class="sxs-lookup"><span data-stu-id="bb3ce-103">Conclusions</span></span>

- <span data-ttu-id="bb3ce-104">コンテナーベースのソリューションでは、最終的にコストの節約効果が得られます。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-104">Container-based solutions ultimately provide cost savings benefits.</span></span> <span data-ttu-id="bb3ce-105">コンテナーにより、運用環境での依存関係の欠如によって生じる摩擦が取り除かれるため、デプロイの問題に対するソリューションです。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-105">Containers are a solution to deployment problems because they remove the friction caused by an absence of dependencies in production environments.</span></span> <span data-ttu-id="bb3ce-106">これらの問題が取り除かれると、Dev/Test、DevOps、運用の各操作が大幅に改善されます。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-106">By removing those issues, it improves Dev/Test, DevOps, and production operations significantly.</span></span>

- <span data-ttu-id="bb3ce-107">Docker コンテナーは、サーバー ベースのアプリケーションまたはサービスの配置の標準的な単位になっています。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-107">A Docker container is becoming the standard unit of deployment for any server-based application or service.</span></span>

- <span data-ttu-id="bb3ce-108">運用環境の場合、スケーラブルなコンテナーベースのアプリケーションをホストするには、オーケストレーター (Kubernetes など) を使用しする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-108">For production environments, you should use an orchestrator (like Kubernetes) to host scalable containers­­–based applications.</span></span>

- <span data-ttu-id="bb3ce-109">コンテナーをホストする Azure VM は、クラウドで小規模な Dev/Test 環境を作る迅速でシンプルな方法です。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-109">Azure VMs hosting containers are a fast and simple way to create small Dev/Test environments in the cloud.</span></span>

- <span data-ttu-id="bb3ce-110">既存のアプリケーションから Azure にリレーショナル データベースを移行するとき、Azure SQL Database Managed Instance が既定で推奨されています。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-110">Azure SQL Database Managed Instance is recommended by default when migrating your relational databases from existing applications to Azure.</span></span>

- <span data-ttu-id="bb3ce-111">Windows コンテナーを利用して既存の .NET アプリケーションの最新化を始めるとき、Visual Studio 2017 と Image2Docker が基本のツールになります。入門学習曲線を加速します。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-111">Visual Studio 2017 and Image2Docker are basic tools for you to start modernizing your existing .NET applications with Windows Containers by accelerating the getting started learning curve.</span></span>

- <span data-ttu-id="bb3ce-112">コンテナー化されたアプリケーションを運用環境に配置するとき、Azure DevOps Services や Jenkins など、CI/CD パイプライン向けの DevOps カルチャと DevOps ツールを常に作成するか、導入します。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-112">When placing containerized applications in production you will always create or adopt a DevOps culture and DevOps tools for CI/CD pipelines, like Azure DevOps Services or Jenkins.</span></span>

- <span data-ttu-id="bb3ce-113">Microsoft Azure により、Windows コンテナー、クラウド インフラストラクチャ、PaaS サービスを使用して既存の .NET Framework アプリケーションを最新化するための最も包括的で完全な環境が提供されます。</span><span class="sxs-lookup"><span data-stu-id="bb3ce-113">Microsoft Azure provides the most comprehensive and complete environment to modernize your existing .NET Framework applications with Windows Containers, cloud infrastructure and PaaS services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bb3ce-114">[[戻る]](walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="bb3ce-114">[Previous](walkthroughs-technical-get-started-overview.md)</span></span>
