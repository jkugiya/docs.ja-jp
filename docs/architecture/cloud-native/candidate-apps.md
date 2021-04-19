---
title: クラウド ネイティブ向けアプリの候補
description: クラウドネイティブ アプローチが適しているアプリケーションの種類について説明します。
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: 443a7c1a1aaef078b33f352f597b33b768d989a3
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506189"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="65d9f-103">クラウド ネイティブ向けアプリの候補</span><span class="sxs-lookup"><span data-stu-id="65d9f-103">Candidate apps for cloud native</span></span>

<span data-ttu-id="65d9f-104">ポートフォリオ内のアプリを確認します。</span><span class="sxs-lookup"><span data-stu-id="65d9f-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="65d9f-105">そのうち、クラウドネイティブ アーキテクチャに適したアプリはいくつありますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="65d9f-106">全部ですか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-106">All of them?</span></span> <span data-ttu-id="65d9f-107">一部でしょうか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-107">Perhaps some?</span></span>

<span data-ttu-id="65d9f-108">費用便益分析を適用すると、クラウド ネイティブにするために必要な高額なコストに見合わない可能性が高いものがほとんどです。</span><span class="sxs-lookup"><span data-stu-id="65d9f-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="65d9f-109">クラウド ネイティブにするためのコストは、アプリケーションのビジネス価値をはるかに上回ります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="65d9f-110">どのようなアプリケーションがクラウド ネイティブの候補になる可能性があるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="65d9f-111">ビジネスの機能や特徴を常に進化させる必要がある戦略的なエンタープライズ システム</span><span class="sxs-lookup"><span data-stu-id="65d9f-111">Strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="65d9f-112">高い信頼性を備え、高いリリース速度を必要とするアプリケーション</span><span class="sxs-lookup"><span data-stu-id="65d9f-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="65d9f-113">システム全体を完全に再デプロイすること "*なく*"、個々の機能をリリースする必要があるシステム</span><span class="sxs-lookup"><span data-stu-id="65d9f-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="65d9f-114">さまざまなテクノロジ スタックの専門知識を持つチームによって開発されたアプリケーション</span><span class="sxs-lookup"><span data-stu-id="65d9f-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="65d9f-115">独立してスケーリングする必要のあるコンポーネントを持つアプリケーション</span><span class="sxs-lookup"><span data-stu-id="65d9f-115">An application with components that must scale independently</span></span>

<span data-ttu-id="65d9f-116">また、レガシ システムもあります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-116">Then there are legacy systems.</span></span> <span data-ttu-id="65d9f-117">誰もが新しいアプリケーションを構築したいと思うものですが、ビジネスにとって重要なレガシ ワークロードのモダン化を担当することもよくあります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="65d9f-118">時間の経過と共に、レガシ アプリケーションはマイクロサービスに分解され、コンテナー化され、最終的にはクラウドネイティブ アーキテクチャへと "プラットフォームの再構築" が行われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="65d9f-119">レガシ アプリのモダン化</span><span class="sxs-lookup"><span data-stu-id="65d9f-119">Modernizing legacy apps</span></span>

<span data-ttu-id="65d9f-120">無料の Microsoft の電子書籍「[Azure クラウドおよび Windows コンテナーを使用した既存の .NET アプリケーションのモダン化](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)」には、オンプレミスのワークロードをクラウドに移行するためのガイダンスが説明されています。</span><span class="sxs-lookup"><span data-stu-id="65d9f-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="65d9f-121">図 1-10 は、レガシ アプリケーションをモダン化する際に、1 つの汎用的な戦略はないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="65d9f-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![レガシ ワークロードを移行するための戦略](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="65d9f-123">**図 1-10**.</span><span class="sxs-lookup"><span data-stu-id="65d9f-123">**Figure 1-10**.</span></span> <span data-ttu-id="65d9f-124">レガシ ワークロードを移行するための戦略</span><span class="sxs-lookup"><span data-stu-id="65d9f-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="65d9f-125">重要ではないモノリシック アプリには、迅速なリフト アンド シフト ([クラウド インフラストラクチャ対応](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) による移行が適しています。</span><span class="sxs-lookup"><span data-stu-id="65d9f-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="65d9f-126">この場合、オンプレミスのワークロードは変更なしでクラウドベースの VM に再ホストされます。</span><span class="sxs-lookup"><span data-stu-id="65d9f-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="65d9f-127">このアプローチでは、[IaaS (サービスとしてのインフラストラクチャ)](https://azure.microsoft.com/overview/what-is-iaas/) モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="65d9f-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="65d9f-128">Azure には、このような移行を容易にするために、[Azure Migrate](https://azure.microsoft.com/services/azure-migrate/)、[Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)、[Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) など、いくつかのツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="65d9f-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="65d9f-129">この戦略により、ある程度のコストを削減できますが、通常、そのようなアプリケーションは、クラウド コンピューティングの利点を引き出して活用するようには設計されていません。</span><span class="sxs-lookup"><span data-stu-id="65d9f-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="65d9f-130">ビジネスに不可欠なモノリシック アプリは、多くの場合、強化されたリフト アンド シフト (*クラウド最適化型*) による移行が適しています。</span><span class="sxs-lookup"><span data-stu-id="65d9f-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="65d9f-131">このアプローチには、アプリケーションのコア アーキテクチャを変更することなく、主要なクラウド サービスを有効にするデプロイの最適化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="65d9f-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="65d9f-132">たとえば、アプリケーションを[コンテナー化](/virtualization/windowscontainers/about/)して、本書で後述する [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/) などのコンテナー オーケストレーターにデプロイすることができます。</span><span class="sxs-lookup"><span data-stu-id="65d9f-132">For example, you might [containerize](/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="65d9f-133">クラウド内では、データベース、メッセージ キュー、監視、分散キャッシュなどの他のクラウド サービスがアプリケーションに使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="65d9f-134">最後に、戦略的なエンタープライズ機能を実行するモノリシック アプリの場合、本書の主題である "*クラウドネイティブ*" アプローチが最適な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="65d9f-135">このアプローチには機敏性とベロシティがあります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="65d9f-136">ただし、プラットフォームの再構築、再設計、コードの書き換えにはコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="65d9f-137">あなたとチームがクラウドネイティブ アプローチが適切であると考えるなら、その決定について組織に理論的に説明することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="65d9f-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="65d9f-138">クラウドネイティブ アプローチによって解決するビジネス上の問題とは、正確には何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="65d9f-139">ビジネス ニーズとどのように調和しますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-139">How would it align with business needs?</span></span>

- <span data-ttu-id="65d9f-140">より高い信頼性で機能を迅速にリリースできますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="65d9f-141">きめ細かいスケーラビリティを備え、リソースをより効率的に使用していますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="65d9f-142">システムの回復性は向上しますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-142">Improved system resiliency?</span></span>

- <span data-ttu-id="65d9f-143">システムのパフォーマンスは向上しますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-143">Improved system performance?</span></span>

- <span data-ttu-id="65d9f-144">操作の可視性は向上しますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-144">More visibility into operations?</span></span>

- <span data-ttu-id="65d9f-145">開発プラットフォームとデータ ストアを融合させ、仕事に最適なツールを実現できますか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="65d9f-146">将来を見据えたアプリケーションへの投資ですか。</span><span class="sxs-lookup"><span data-stu-id="65d9f-146">Future-proof application investment?</span></span>

<span data-ttu-id="65d9f-147">適切な移行戦略は、組織の優先順位と対象とするシステムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="65d9f-148">モノリシック アプリケーションをクラウドに最適化するか、n 層アプリに粒度の粗いサービスを追加する方が費用効果が高いことはよくあります。</span><span class="sxs-lookup"><span data-stu-id="65d9f-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="65d9f-149">このような場合でも、Azure App Service によって提供されるようなクラウド PaaS 機能を十分に活用できます。</span><span class="sxs-lookup"><span data-stu-id="65d9f-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="65d9f-150">まとめ</span><span class="sxs-lookup"><span data-stu-id="65d9f-150">Summary</span></span>

<span data-ttu-id="65d9f-151">この章では、クラウドネイティブ コンピューティングについて紹介しました。</span><span class="sxs-lookup"><span data-stu-id="65d9f-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="65d9f-152">クラウドネイティブ アプリケーションを推進する主要な機能と共に、定義について説明しました。</span><span class="sxs-lookup"><span data-stu-id="65d9f-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="65d9f-153">このような投資と労力を正当化できるようなアプリケーションの種類についても説明しました。</span><span class="sxs-lookup"><span data-stu-id="65d9f-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="65d9f-154">導入部を終えて、これからクラウド ネイティブについてさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="65d9f-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="65d9f-155">リファレンス</span><span class="sxs-lookup"><span data-stu-id="65d9f-155">References</span></span>

- [<span data-ttu-id="65d9f-156">Cloud Native Computing Foundation</span><span class="sxs-lookup"><span data-stu-id="65d9f-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="65d9f-157">.NET Microservices: Architecture for Containerized .NET applications (.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ)</span><span class="sxs-lookup"><span data-stu-id="65d9f-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="65d9f-158">Azure クラウドと Windows コンテナーで既存の .NET アプリケーションを最新式にする</span><span class="sxs-lookup"><span data-stu-id="65d9f-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="65d9f-159">Cloud Native Patterns (クラウド ネイティブ パターン) (Cornelia Davis 著)</span><span class="sxs-lookup"><span data-stu-id="65d9f-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="65d9f-160">Beyond the Twelve-Factor Application (Twelve-Factor アプリケーションを超えて)</span><span class="sxs-lookup"><span data-stu-id="65d9f-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="65d9f-161">コードとしてのインフラストラクチャとは</span><span class="sxs-lookup"><span data-stu-id="65d9f-161">What is Infrastructure as Code</span></span>](/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="65d9f-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence (Uber エンジニアリングのマイクロ デプロイ: 自信を持って毎日デプロイする)</span><span class="sxs-lookup"><span data-stu-id="65d9f-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="65d9f-163">How Netflix Deploys Code (Netflix によるコードのデプロイ方法)</span><span class="sxs-lookup"><span data-stu-id="65d9f-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="65d9f-164">Overload Control for Scaling WeChat Microservices (WeChat マイクロサービスをスケーリングするためのオーバーロード制御)</span><span class="sxs-lookup"><span data-stu-id="65d9f-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="65d9f-165">[前へ](definition.md)
>[次へ](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="65d9f-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
