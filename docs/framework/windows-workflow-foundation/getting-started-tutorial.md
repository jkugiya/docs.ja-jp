---
title: チュートリアル入門 2
description: この記事では、Windows Workflow Foundation アプリケーションのプログラミングの概要を説明する一連のチュートリアルを開始します。
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: e9856320faa82becf12dda04d02f6f1c08081feb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293599"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="1e06f-103">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="1e06f-103">Getting Started Tutorial</span></span>

<span data-ttu-id="1e06f-104">このセクションには、Windows Workflow Foundation (WF) アプリケーションのプログラミングの概要を説明する一連のチュートリアル トピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e06f-104">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="1e06f-105">これらのトピックの手順に従って、数値推測ゲーム アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-105">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="1e06f-106">チュートリアルの最初のトピックでは、ワークフローに必要なカスタム アクティビティを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-106">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="1e06f-107">2 番目のトピックでは、カスタム アクティビティをビルトイン ワークフロー アクティビティと共にフローチャート ワークフローにアセンブルします。</span><span class="sxs-lookup"><span data-stu-id="1e06f-107">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="1e06f-108">3 番目のトピックでは、ホスト アプリケーションを構成してワークフローを実行します。最後のトピックでは永続化の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-108">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="1e06f-109">このプロセスの各手順はその前の手順に基づいているため、順番に完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1e06f-109">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e06f-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1e06f-110">In This Section</span></span>  

 [<span data-ttu-id="1e06f-111">方法: アクティビティを作成する</span><span class="sxs-lookup"><span data-stu-id="1e06f-111">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="1e06f-112"><xref:System.Activities.NativeActivity%601> から派生するカスタム アクティビティを作成する方法、およびアクティビティ デザイナーを使用してカスタム アクティビティをビルトイン アクティビティと共に複合アクティビティへと構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-112">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="1e06f-113">方法: ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="1e06f-113">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="1e06f-114">ビルトイン アクティビティと前のチュートリアルのカスタム アクティビティを使用して、フローチャート、シーケンシャル、およびステート マシンのワークフローを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-114">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="1e06f-115">方法: ワークフローを実行する</span><span class="sxs-lookup"><span data-stu-id="1e06f-115">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="1e06f-116">ホスト環境からワークフローを呼び出す方法、データをワークフローとの間でやり取りする方法、およびブックマークを再開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-116">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="1e06f-117">方法: 長時間にわたって実行されるワークフローを作成して実行する</span><span class="sxs-lookup"><span data-stu-id="1e06f-117">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="1e06f-118">永続性をワークフロー アプリケーションに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-118">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="1e06f-119">方法: カスタム追跡参加要素を作成する</span><span class="sxs-lookup"><span data-stu-id="1e06f-119">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="1e06f-120">カスタムの追跡参加要素と追跡プロファイルを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-120">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="1e06f-121">方法: ワークフローの複数のバージョンを同時にホストする</span><span class="sxs-lookup"><span data-stu-id="1e06f-121">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="1e06f-122">`WorkflowIdentity` を使用して、ワークフローの複数バージョンを同時にホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-122">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="1e06f-123">方法: 実行中のワークフロー インスタンスの定義を更新する</span><span class="sxs-lookup"><span data-stu-id="1e06f-123">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="1e06f-124">動的更新を使用して、実行中のワークフロー インスタンスを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1e06f-124">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e06f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e06f-125">See also</span></span>

- [<span data-ttu-id="1e06f-126">Windows Workflow Foundation プログラミングの新機能</span><span class="sxs-lookup"><span data-stu-id="1e06f-126">Windows Workflow Foundation Programming</span></span>](programming.md)
