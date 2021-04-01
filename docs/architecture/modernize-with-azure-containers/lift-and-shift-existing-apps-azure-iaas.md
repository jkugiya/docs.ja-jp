---
title: 既存の .NET アプリを Azure IaaS にリフトアンドシフトする (クラウド インフラストラクチャ対応)
description: Azure Cloud および Windows コンテナーを使用して既存の .NET アプリケーションを最新化します。
ms.date: 12/21/2020
ms.openlocfilehash: 69e89702b41cd7388ee6c90e77efafc7cd2bebe8
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605114"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="c8227-103">既存の .NET アプリを Azure IaaS にリフトアンドシフトする (クラウド インフラストラクチャ対応)</span><span class="sxs-lookup"><span data-stu-id="c8227-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="c8227-104">展望:最初の手順として、オンプレミスの投資と、ハードウェアとネットワークのメンテナンスの総コストを削減するために、既存のアプリケーションを単純にクラウド内にホストし直します。</span><span class="sxs-lookup"><span data-stu-id="c8227-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="c8227-105">既存のアプリケーションを Azure Infrastructure as a Service (IaaS) プラットフォームに移行するには、"*方法*" より前に、Azure の IaaS に直接移行したい "*理由*" を分析することが重要です。</span><span class="sxs-lookup"><span data-stu-id="c8227-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="c8227-106">この最新化成熟度レベルのシナリオでは、基本的に、現在のオンプレミス インフラストラクチャを引き続き使用するのではなく、クラウドで VM の使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="c8227-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="c8227-107">もう 1 つの分析ポイントでは、より高度なマネージド サービスを単に Azure に追加するのではなく、純粋な IaaS クラウドに移行したい "*理由*" を分析します。</span><span class="sxs-lookup"><span data-stu-id="c8227-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="c8227-108">最初に、IaaS が必要となる状況を特定します。</span><span class="sxs-lookup"><span data-stu-id="c8227-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="c8227-109">図 2-1 では、クラウド インフラストラクチャ対応アプリケーションを最新化成熟度レベルに位置付けています。</span><span class="sxs-lookup"><span data-stu-id="c8227-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![クラウド インフラストラクチャ対応アプリケーションの位置付け](./media/image2-1.png)

<span data-ttu-id="c8227-111">**図 2-1**</span><span class="sxs-lookup"><span data-stu-id="c8227-111">**Figure 2-1.**</span></span> <span data-ttu-id="c8227-112">クラウド インフラストラクチャ対応アプリケーションの位置付け</span><span class="sxs-lookup"><span data-stu-id="c8227-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="c8227-113">既存の .NET Web アプリケーションを Azure IaaS に移行する理由</span><span class="sxs-lookup"><span data-stu-id="c8227-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="c8227-114">最初の IaaS レベルであってもクラウドに移行する主な理由は、コスト削減の実現です。</span><span class="sxs-lookup"><span data-stu-id="c8227-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="c8227-115">より管理されたインフラストラクチャ サービスを使用することで、組織はハードウェア メンテナンス、サーバーまたは VM のプロビジョニングとデプロイ、インフラストラクチャ管理への投資を削減できます。</span><span class="sxs-lookup"><span data-stu-id="c8227-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="c8227-116">アプリをクラウドに移行することを決定した後、PaaS のようなより高度なオプションではなく IaaS を選択するのは、単に IaaS 環境の方がなじみやすいだろうというのが主な理由です。</span><span class="sxs-lookup"><span data-stu-id="c8227-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="c8227-117">現在のオンプレミス環境に似た環境に移行することで、より低い学習曲線が得られ、クラウドへの最短パスを実現します。</span><span class="sxs-lookup"><span data-stu-id="c8227-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="c8227-118">しかしながら、クラウドへの最短パスを通ることが、アプリケーションをクラウドで実行することによって最大のメリットを得られることを意味するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="c8227-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="c8227-119">どの組織でも、既に導入されているクラウド最適化およびクラウドネイティブの成熟度レベルでのクラウド移行によって最も大きなメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="c8227-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="c8227-120">また、アプリケーションが既にクラウド、さらに言えば IaaS で実行されている場合は、アプリケーションの最新化と再設計が容易になることも明らかになっています。</span><span class="sxs-lookup"><span data-stu-id="c8227-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="c8227-121">アプリケーション データの移行は既に完了しています。</span><span class="sxs-lookup"><span data-stu-id="c8227-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="c8227-122">また、組織はクラウドでの作業に必要なスキルを獲得し、"クラウド文化" での運用にシフトしていることでしょう。</span><span class="sxs-lookup"><span data-stu-id="c8227-122">Also, your organization will have gained the skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="c8227-123">PaaS ではなく IaaS に移行する場合</span><span class="sxs-lookup"><span data-stu-id="c8227-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="c8227-124">以降のセクションでは、ほとんどが PaaS プラットフォームとサービスに基づいているクラウド最適化アプリケーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c8227-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="c8227-125">これらのアプリでは、クラウドへの移行によって最も大きなメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="c8227-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="c8227-126">単に既存のアプリケーションをクラウドに移行することが目標の場合は、まず、Azure App Service で実行するために大幅な変更を必要としない既存のアプリケーションを特定します。</span><span class="sxs-lookup"><span data-stu-id="c8227-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="c8227-127">これらのアプリが、クラウド最適化の最初の候補になるはずです。</span><span class="sxs-lookup"><span data-stu-id="c8227-127">These apps should be the first candidates for Cloud-Optimized.</span></span>

<span data-ttu-id="c8227-128">次に、Windows コンテナーと、App Service などの PaaS または Azure Kubernetes Service のようなオーケストレーターにまだ移行できないアプリの場合は、それらのアプリをシンプルでわかりやすい VM (IaaS) に移行します。</span><span class="sxs-lookup"><span data-stu-id="c8227-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Kubernetes Service, migrate those apps to simple plain VMs (IaaS).</span></span>

<span data-ttu-id="c8227-129">ただし、VM の構成、セキュリティ保護、メンテナンスを正しく行うためには、Azure で PaaS サービスを使用する場合よりもずっと多くの時間がかかり、IT の専門知識が要求されることに留意します。</span><span class="sxs-lookup"><span data-stu-id="c8227-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="c8227-130">Azure Virtual Machines を選択する場合は必ず、VM 環境に対する修正プログラムの適用、更新、管理に伴って日々発生するメンテナンスの労力を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="c8227-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="c8227-131">Azure Virtual Machines は IaaS です。</span><span class="sxs-lookup"><span data-stu-id="c8227-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="c8227-132">Azure Migrate を使用して、既存のアプリケーションを分析し、Azure に移行する</span><span class="sxs-lookup"><span data-stu-id="c8227-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="c8227-133">クラウドへの移行は必ず難しいというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="c8227-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="c8227-134">ところが、多くの組織では、環境を深く可視化して、アプリケーション、ワークロード、データ間の密接な相互依存関係を把握する最初の段階で苦労しています。</span><span class="sxs-lookup"><span data-stu-id="c8227-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="c8227-135">そうした可視化ができないと、その後のパスの計画が困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c8227-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="c8227-136">移行を成功させるために何が必要なのかについて詳細な情報がないと、組織内で適切な会話を交わすことはできません。</span><span class="sxs-lookup"><span data-stu-id="c8227-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="c8227-137">潜在的なコスト上の利点について、またはワークロードを単にリフトアンドシフトできるかどうか、移行を成功させるために大幅な手直しが必要になるのかについてよくわかりません。</span><span class="sxs-lookup"><span data-stu-id="c8227-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="c8227-138">多くの組織がためらうのも無理はありません。</span><span class="sxs-lookup"><span data-stu-id="c8227-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="c8227-139">[Azure Migrate](https://aka.ms/azuremigrate) は、Azure への移行を支援するために必要なガイダンス、分析情報、メカニズムが提供される新しいサービスです。</span><span class="sxs-lookup"><span data-stu-id="c8227-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="c8227-140">Azure Migrate では次のものが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c8227-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="c8227-141">オンプレミスの仮想マシンを対象にした検出と評価</span><span class="sxs-lookup"><span data-stu-id="c8227-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="c8227-142">多階層アプリケーションの信頼性の高い検出を行うための組み込みの依存関係マッピング</span><span class="sxs-lookup"><span data-stu-id="c8227-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="c8227-143">Azure 仮想マシンへのインテリジェントな適切なサイズ変更</span><span class="sxs-lookup"><span data-stu-id="c8227-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="c8227-144">潜在的な問題を修正するためのガイドラインを含む互換性レポート</span><span class="sxs-lookup"><span data-stu-id="c8227-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="c8227-145">データベースの検出と移行のための Azure Database Management Service との統合</span><span class="sxs-lookup"><span data-stu-id="c8227-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="c8227-146">Azure Migrate により、ビジネスへの影響を最小限に抑えてワークロードを移行し、Azure で期待どおりに実行できるという自信が得られます。</span><span class="sxs-lookup"><span data-stu-id="c8227-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="c8227-147">適切なツールとガイダンスを使用すると、重要なパフォーマンスと信頼性のニーズを確実に満たしながら、投資収益率を最大限に高めることができます。</span><span class="sxs-lookup"><span data-stu-id="c8227-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="c8227-148">図 2-2 は、Azure Migrate によって実行されるすべてのサーバーとアプリケーションの接続に対する組み込みの依存関係マッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="c8227-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![サーバーとアプリケーションの接続の依存関係](./media/image2-2.png)

<span data-ttu-id="c8227-150">**図 2-2**</span><span class="sxs-lookup"><span data-stu-id="c8227-150">**Figure 2-2.**</span></span> <span data-ttu-id="c8227-151">クラウド インフラストラクチャ対応アプリケーションの位置付け</span><span class="sxs-lookup"><span data-stu-id="c8227-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="c8227-152">Azure Site Recovery を使用して既存の VM を Azure VM に移行する</span><span class="sxs-lookup"><span data-stu-id="c8227-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="c8227-153">エンドツーエンドの [Azure Migrate](https://aka.ms/azuremigrate) に含まれている [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) は、Web アプリを Azure の VM に簡単に移行するために使用できるツールです。</span><span class="sxs-lookup"><span data-stu-id="c8227-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="c8227-154">Site Recovery を使用すると、オンプレミスの VM と物理サーバーを Azure にレプリケートすることも、オンプレミスのセカンダリ ロケーションにレプリケートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c8227-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="c8227-155">さらには、サポートされている Azure VM、オンプレミスの "*Hyper-V*" VM、"*VMware*" VM、Windows 物理サーバー、または Linux 物理サーバー上で実行されているワークロードをレプリケートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c8227-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="c8227-156">Azure へのレプリケートにより、セカンダリ データセンターの管理に伴うコストと手間が削減されます。</span><span class="sxs-lookup"><span data-stu-id="c8227-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="c8227-157">Site Recovery は、一部がオンプレミスで、一部が Azure 上にあるハイブリッド環境専用にも作成されています。</span><span class="sxs-lookup"><span data-stu-id="c8227-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="c8227-158">Site Recovery の利点は、サイトがダウンした場合でも VM やオンプレミスの物理サーバー上で実行されているアプリの可用性が維持されて、ビジネス継続性が確保されることです。</span><span class="sxs-lookup"><span data-stu-id="c8227-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="c8227-159">VM や物理サーバー上で実行されているワークロードは、プライマリ サイトが利用できなくなった場合でもセカンダリ ロケーションで利用できるようにレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="c8227-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="c8227-160">ワークロードは、プライマリ サイトが稼働状態に戻った時点でプライマリ サイトに復元されます。</span><span class="sxs-lookup"><span data-stu-id="c8227-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="c8227-161">図 2-3 は Azure Site Recovery を使用して複数の VM 移行が実行されていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="c8227-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![Azure Site Recovery を使用して VM を移行する](./media/image2-3.png)

<span data-ttu-id="c8227-163">**図 2-3**</span><span class="sxs-lookup"><span data-stu-id="c8227-163">**Figure 2-3.**</span></span> <span data-ttu-id="c8227-164">クラウド インフラストラクチャ対応アプリケーションの位置付け</span><span class="sxs-lookup"><span data-stu-id="c8227-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c8227-165">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c8227-165">Additional resources</span></span>

- <span data-ttu-id="c8227-166">**Azure Migrate データシート**</span><span class="sxs-lookup"><span data-stu-id="c8227-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="c8227-167">**Azure Migrate**</span><span class="sxs-lookup"><span data-stu-id="c8227-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="c8227-168">**Azure Migration Center**</span><span class="sxs-lookup"><span data-stu-id="c8227-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="c8227-169">**Site Recovery を使用した Azure への移行**</span><span class="sxs-lookup"><span data-stu-id="c8227-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="c8227-170">**Azure Site Recovery サービスの概要**</span><span class="sxs-lookup"><span data-stu-id="c8227-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="c8227-171">**AWS の VM の Azure VM への移行**</span><span class="sxs-lookup"><span data-stu-id="c8227-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="c8227-172">[前へ](index.md)
>[次へ](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="c8227-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span> <!-- Next Chapter -->
