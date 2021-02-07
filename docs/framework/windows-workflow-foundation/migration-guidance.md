---
description: '詳細情報: 移行ガイダンス'
title: 移行のガイドライン
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 05aede02d7ad615ddeeceab6d71a545db9bcf5ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755355"
---
# <a name="migration-guidance"></a><span data-ttu-id="2ba64-103">移行のガイドライン</span><span class="sxs-lookup"><span data-stu-id="2ba64-103">Migration Guidance</span></span>

<span data-ttu-id="2ba64-104">.NET Framework 4 では、Microsoft は、Windows Workflow Foundation (WF) の2番目のメジャーバージョンをリリースしています。</span><span class="sxs-lookup"><span data-stu-id="2ba64-104">In the .NET Framework 4, Microsoft is releasing the second major version of Windows Workflow Foundation (WF).</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="2ba64-105">は WinFX でリリースされました (これには WF3 の型が含まれるようになり、現在はと呼ばれるようになりました \* )。また .NET Framework 3.5 でも強化されました。</span><span class="sxs-lookup"><span data-stu-id="2ba64-105">was released in WinFX (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in .NET Framework 3.5.</span></span> <span data-ttu-id="2ba64-106">WF3 も .NET Framework 4 に含まれていますが、新しいワークフローテクノロジ (WF4 と呼ばれる型) と共に存在し \* ます。</span><span class="sxs-lookup"><span data-stu-id="2ba64-106">WF3 is also part of the .NET Framework 4, but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="2ba64-107">WF4 の導入時期を検討する場合は、最初にそのタイミングの管理を認識することが重要です。</span><span class="sxs-lookup"><span data-stu-id="2ba64-107">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>

- <span data-ttu-id="2ba64-108">WF3 は .NET Framework 4 の完全にサポートされている部分です。</span><span class="sxs-lookup"><span data-stu-id="2ba64-108">WF3 is a fully supported part of the .NET Framework 4.</span></span>

- <span data-ttu-id="2ba64-109">WF3 アプリケーションは、変更せずに .NET Framework 4 で実行され、引き続き完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2ba64-109">WF3 applications run on the .NET Framework 4 without modification and continue to be fully supported.</span></span>

- <span data-ttu-id="2ba64-110">新しい WF3 アプリケーションを作成し、既存のアプリケーションを Visual Studio 2012 で編集し、完全にサポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="2ba64-110">New WF3 applications can be created and your existing applications can be edited in Visual Studio 2012 and are fully supported.</span></span>

 <span data-ttu-id="2ba64-111">したがって、.NET Framework 4 を採用するかどうかの決定は、 \* WF3 (WF4) から () に移動するかどうかを決定するものとは分離されています。 \*</span><span class="sxs-lookup"><span data-stu-id="2ba64-111">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.\*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="2ba64-112">このトピックでは、WF の移行のガイドラインへのリンクを提供し、WF3 および WF4 での作業に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-112">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>

## <a name="wf-migration-white-papers-and-cookbooks"></a><span data-ttu-id="2ba64-113">WF の移行に関するホワイトペーパーと料理</span><span class="sxs-lookup"><span data-stu-id="2ba64-113">WF migration white papers and cookbooks</span></span>

 <span data-ttu-id="2ba64-114">[WF の移行の概要](/previous-versions/appfabric/ff383417(v=azure.10))に関するトピックでは、WF3 と WF4 の間の関係と移行戦略の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-114">The [WF Migration Overview](/previous-versions/appfabric/ff383417(v=azure.10)) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="2ba64-115">関連トピックでは、特定のトピックを掘り下げて説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-115">Companion topics drill into specific topics.</span></span>

 <span data-ttu-id="2ba64-116">[WF の移行の概要](/previous-versions/appfabric/ff383417(v=azure.10)) WF3 と WF4 の関係、および .NET Framework 4 のワークフローテクノロジのユーザーまたは潜在的なユーザーとしての選択肢について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-116">[WF Migration Overview](/previous-versions/appfabric/ff383417(v=azure.10)) Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET Framework 4.</span></span>

 <span data-ttu-id="2ba64-117">[WF の移行: WF3 開発のベストプラクティス](/previous-versions/appfabric/ff383417(v=azure.10)) WF4 に簡単に移行できるように WF3 アーティファクトを設計する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-117">[WF Migration: Best Practices for WF3 Development](/previous-versions/appfabric/ff383417(v=azure.10)) Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>

 <span data-ttu-id="2ba64-118">[WF のガイダンス: ルール](/previous-versions/appfabric/ff383417(v=azure.10)) .NET Framework 4 つのソリューションにルール関連の投資を進める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-118">[WF Guidance: Rules](/previous-versions/appfabric/ff383417(v=azure.10)) Discusses how to bring rules-related investments forward into .NET Framework 4 solutions.</span></span>

 <span data-ttu-id="2ba64-119">[WF のガイダンス: ステートマシン](/previous-versions/appfabric/ff383417(v=azure.10)) State-Machine アクティビティが存在しない場合の WF4 制御フローのモデリングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-119">[WF Guidance: State Machine](/previous-versions/appfabric/ff383417(v=azure.10)) Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>

 <span data-ttu-id="2ba64-120">このガイダンスは、.NET Framework 4 を対象とするワークフロー プロジェクトにのみ該当することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2ba64-120">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="2ba64-121">ステートマシンのワークフローは、Platform Update 1 のリリースで .NET Framework 4.0.1 に追加され、.NET Framework 4.5 の一部として含まれていました。</span><span class="sxs-lookup"><span data-stu-id="2ba64-121">State Machine workflows were added in .NET Framework 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> <span data-ttu-id="2ba64-122">.NET Framework 4.0.1-4.0.3 と .NET Framework 4.5 のステートマシンワークフローの詳細については、「 [Update 4.0.1 for Microsoft .NET Framework 4 Features](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) And [state machine ワークフロー](state-machine-workflows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ba64-122">For more information about state machine workflows in .NET Framework 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) and [State Machine Workflows](state-machine-workflows.md).</span></span>

 <span data-ttu-id="2ba64-123">[WF の移行のクックブック: カスタムアクティビティ](/previous-versions/appfabric/ff383417(v=azure.10)) WF4 で WF3 カスタムアクティビティを再設計するための例と手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-123">[WF Migration Cookbook: Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10)) Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>

 <span data-ttu-id="2ba64-124">[WF の移行のクックブック: 高度なカスタムアクティビティ](/previous-versions/appfabric/ff383417(v=azure.10)) WF3 キューを使用する advanced WF3 カスタムアクティビティを再設計し、子アクティビティを WF4 カスタムアクティビティとしてスケジュール設定するためのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-124">[WF Migration Cookbook: Advanced Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10)) Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>

 <span data-ttu-id="2ba64-125">[WF の移行のクックブック: ワークフロー](/previous-versions/appfabric/ff383417(v=azure.10)) WF4 で WF3 ワークフローを再設計するための例と手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-125">[WF Migration Cookbook: Workflows](/previous-versions/appfabric/ff383417(v=azure.10)) Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>

 <span data-ttu-id="2ba64-126">[WF の移行のクックブック: ワークフローホスティング](/previous-versions/appfabric/ff383417(v=azure.10)) WF3 ホスティングコードを WF4 ホスティングコードとして再設計するためのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-126">[WF Migration Cookbook: Workflow Hosting](/previous-versions/appfabric/ff383417(v=azure.10)) Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="2ba64-127">この目的は、WF3 と WF4 のワークフロー ホスティングの主な違いを説明することです。</span><span class="sxs-lookup"><span data-stu-id="2ba64-127">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>

 <span data-ttu-id="2ba64-128">[WF の移行のクックブック: ワークフロー追跡](/previous-versions/appfabric/ff383417(v=azure.10)) 同等の WF4 追跡コードと構成を使用して、WF3 追跡コードと構成を再設計するためのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-128">[WF Migration Cookbook: Workflow Tracking](/previous-versions/appfabric/ff383417(v=azure.10)) Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>

 <span data-ttu-id="2ba64-129">[WF のガイダンス: ワークフローサービス](/previous-versions/appfabric/ff383417(v=azure.10)) 既定のアクティビティの一般的なシナリオで WF4 を使用するために、WF3 で作成された Windows Communication Foundation (WCF) web サービス (一般的にはワークフローサービスと呼ばれます) を実装するワークフローを再設計する例を示します。</span><span class="sxs-lookup"><span data-stu-id="2ba64-129">[WF Guidance: Workflow Services](/previous-versions/appfabric/ff383417(v=azure.10)) Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ba64-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ba64-130">See also</span></span>

- <xref:System.Activities.Statements.Interop>
