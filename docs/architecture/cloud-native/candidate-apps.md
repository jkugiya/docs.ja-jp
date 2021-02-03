---
title: クラウドネイティブ向けアプリ候補
description: クラウドネイティブアプローチによってメリットが得られるアプリケーションの種類について説明します
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: 443a7c1a1aaef078b33f352f597b33b768d989a3
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506189"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="8c6d9-103">クラウドネイティブ向けアプリ候補</span><span class="sxs-lookup"><span data-stu-id="8c6d9-103">Candidate apps for cloud native</span></span>

<span data-ttu-id="8c6d9-104">ポートフォリオ内のアプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="8c6d9-105">クラウドネイティブアーキテクチャについては、そのうちのどれが適していますか。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="8c6d9-106">全部ですか。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-106">All of them?</span></span> <span data-ttu-id="8c6d9-107">おそらく、</span><span class="sxs-lookup"><span data-stu-id="8c6d9-107">Perhaps some?</span></span>

<span data-ttu-id="8c6d9-108">コストと利益の分析を適用すると、クラウドネイティブの hefty price タグがサポートされない可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="8c6d9-109">クラウドネイティブのコストは、アプリケーションのビジネス価値をはるかに超えています。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="8c6d9-110">クラウドネイティブの候補となるアプリケーションの種類</span><span class="sxs-lookup"><span data-stu-id="8c6d9-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="8c6d9-111">ビジネス機能や機能を絶えず進化させる必要がある戦略的エンタープライズシステム</span><span class="sxs-lookup"><span data-stu-id="8c6d9-111">Strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="8c6d9-112">高い信頼性を備えた高いリリース速度を必要とするアプリケーション</span><span class="sxs-lookup"><span data-stu-id="8c6d9-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="8c6d9-113">システム全体を完全に再展開 *せず* に、個々の機能をリリースする必要があるシステム</span><span class="sxs-lookup"><span data-stu-id="8c6d9-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="8c6d9-114">さまざまなテクノロジスタックに専門知識を持つチームによって開発されたアプリケーション</span><span class="sxs-lookup"><span data-stu-id="8c6d9-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="8c6d9-115">個別に拡張する必要があるコンポーネントを含むアプリケーション</span><span class="sxs-lookup"><span data-stu-id="8c6d9-115">An application with components that must scale independently</span></span>

<span data-ttu-id="8c6d9-116">レガシシステムがあります。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-116">Then there are legacy systems.</span></span> <span data-ttu-id="8c6d9-117">新しいアプリケーションを構築する必要がありますが、多くの場合、ビジネスにとって重要な従来のワークロードの最新化を担当しています。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="8c6d9-118">時間の経過と共に、レガシアプリケーションをマイクロサービスに分解し、コンテナー化し、最終的にはクラウドネイティブアーキテクチャに "replatformed" することができます。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="8c6d9-119">最新化レガシアプリ</span><span class="sxs-lookup"><span data-stu-id="8c6d9-119">Modernizing legacy apps</span></span>

<span data-ttu-id="8c6d9-120">[Azure クラウドおよび Windows コンテナーを使用した既存の .net アプリケーション](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)の最新化に関する Microsoft の電子書籍では、オンプレミスのワークロードをクラウドに移行するためのガイダンスが提供されています。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="8c6d9-121">図1-10 に、レガシアプリケーションを最新化するための単一の1つのサイズに適合しない方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![従来のワークロードを移行するための戦略](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="8c6d9-123">**図 1-10**.</span><span class="sxs-lookup"><span data-stu-id="8c6d9-123">**Figure 1-10**.</span></span> <span data-ttu-id="8c6d9-124">従来のワークロードを移行するための戦略</span><span class="sxs-lookup"><span data-stu-id="8c6d9-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="8c6d9-125">非常に重要ではないモノリシックアプリは、迅速なリフトアンドシフト ([クラウドインフラストラクチャ](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)対応) の移行によるメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="8c6d9-126">ここでは、オンプレミスのワークロードは変更なしでクラウドベースの VM に再ホストされます。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="8c6d9-127">このアプローチでは、 [IaaS (Infrastructure as a Service) モデル](https://azure.microsoft.com/overview/what-is-iaas/)を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="8c6d9-128">Azure には、このような移動を容易にするために、 [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/)、 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)、 [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) など、いくつかのツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="8c6d9-129">この戦略ではコストを削減できますが、このようなアプリケーションは通常、クラウドコンピューティングのメリットをロック解除して活用するように設計されていません。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="8c6d9-130">ビジネスにとって重要なモノリシックアプリは、強化されたリフトアンドシフト (*クラウド最適化*) 移行によってメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="8c6d9-131">このアプローチには、アプリケーションのコアアーキテクチャを変更せずに、キークラウドサービスを有効にするデプロイの最適化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="8c6d9-132">たとえば、アプリケーションを [コンテナー化](/virtualization/windowscontainers/about/) して、 [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/)のようなコンテナー orchestrator にデプロイすることがあります。これについては後で説明します。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-132">For example, you might [containerize](/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="8c6d9-133">クラウドでは、アプリケーションは、データベース、メッセージキュー、監視、分散キャッシュなどの他のクラウドサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="8c6d9-134">最後に、戦略的なエンタープライズ機能を実行するモノリシックアプリでは、 *クラウドネイティブ* アプローチ (この書籍の主題) から最適なメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="8c6d9-135">このアプローチは機敏性とベロシティを実現します。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="8c6d9-136">しかし、基幹、再設計、リライトコードのコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="8c6d9-137">お客様とチームがクラウドにネイティブなアプローチを考えている場合は、組織で決定を合理化することを behooves ます。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="8c6d9-138">クラウドネイティブアプローチによって解決されるビジネス上の問題は、どのようなものですか。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="8c6d9-139">ビジネスニーズとどのように連携しますか。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-139">How would it align with business needs?</span></span>

- <span data-ttu-id="8c6d9-140">信頼性が向上した機能の迅速なリリース</span><span class="sxs-lookup"><span data-stu-id="8c6d9-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="8c6d9-141">細かいスケーラビリティ-リソースの効率的な使用</span><span class="sxs-lookup"><span data-stu-id="8c6d9-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="8c6d9-142">システムの回復性が向上しましたか?</span><span class="sxs-lookup"><span data-stu-id="8c6d9-142">Improved system resiliency?</span></span>

- <span data-ttu-id="8c6d9-143">システムパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="8c6d9-143">Improved system performance?</span></span>

- <span data-ttu-id="8c6d9-144">操作の可視性</span><span class="sxs-lookup"><span data-stu-id="8c6d9-144">More visibility into operations?</span></span>

- <span data-ttu-id="8c6d9-145">Blend の開発プラットフォームとデータストアは、ジョブに最適なツールに到達できますか。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="8c6d9-146">将来のアプリケーション投資</span><span class="sxs-lookup"><span data-stu-id="8c6d9-146">Future-proof application investment?</span></span>

<span data-ttu-id="8c6d9-147">適切な移行戦略は、組織の優先順位と対象とするシステムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="8c6d9-148">多くの場合、モノリシックアプリケーションをクラウドで最適化したり、N 層アプリに粗いサービスを追加したりすると、コスト効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="8c6d9-149">このような場合でも、Azure App Service によって提供されるもののようなクラウド PaaS 機能を十分に活用できます。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="8c6d9-150">まとめ</span><span class="sxs-lookup"><span data-stu-id="8c6d9-150">Summary</span></span>

<span data-ttu-id="8c6d9-151">この章では、クラウドネイティブコンピューティングを導入しました。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="8c6d9-152">クラウドネイティブアプリケーションを駆動する主な機能と共に、定義を提供しました。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="8c6d9-153">この投資と労力を正当化するアプリケーションの種類について見てきました。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="8c6d9-154">ここでは、クラウドネイティブの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c6d9-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="8c6d9-155">リファレンス</span><span class="sxs-lookup"><span data-stu-id="8c6d9-155">References</span></span>

- [<span data-ttu-id="8c6d9-156">クラウドネイティブコンピューティングファンデーション</span><span class="sxs-lookup"><span data-stu-id="8c6d9-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="8c6d9-157">.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="8c6d9-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="8c6d9-158">Azure クラウドと Windows コンテナーで既存の .NET アプリケーションを最新式にする</span><span class="sxs-lookup"><span data-stu-id="8c6d9-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="8c6d9-159">Cornelia Davis によるクラウドネイティブパターン</span><span class="sxs-lookup"><span data-stu-id="8c6d9-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="8c6d9-160">Twelve-Factor アプリケーション以外</span><span class="sxs-lookup"><span data-stu-id="8c6d9-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="8c6d9-161">コードとしてのインフラストラクチャとは</span><span class="sxs-lookup"><span data-stu-id="8c6d9-161">What is Infrastructure as Code</span></span>](/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="8c6d9-162">Uber Engineering のマイクロデプロイ: 自信を持って毎日デプロイ</span><span class="sxs-lookup"><span data-stu-id="8c6d9-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="8c6d9-163">Netflix によるコードのデプロイ方法</span><span class="sxs-lookup"><span data-stu-id="8c6d9-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="8c6d9-164">マイクロサービスでの Wat のスケーリングのためのオーバーロードコントロール</span><span class="sxs-lookup"><span data-stu-id="8c6d9-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="8c6d9-165">[前へ](definition.md)
>[次へ](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="8c6d9-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
