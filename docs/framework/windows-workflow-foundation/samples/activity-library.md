---
description: '詳細情報: アクティビティライブラリ'
title: アクティビティ ライブラリ
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e59846d34b63683266fed2c4ec1ad4ed5cb9566
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792610"
---
# <a name="activity-library"></a><span data-ttu-id="3ccb2-103">アクティビティ ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3ccb2-103">Activity Library</span></span>

<span data-ttu-id="3ccb2-104">このセクションには、Windows Workflow Foundation (WF) の高度なカスタムアクティビティを示すサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-104">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ccb2-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3ccb2-105">In This Section</span></span>

 [<span data-ttu-id="3ccb2-106">SendMail カスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3ccb2-106">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="3ccb2-107"><xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-107">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="3ccb2-108">制限された並列 ForEach</span><span class="sxs-lookup"><span data-stu-id="3ccb2-108">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="3ccb2-109">ph x="1" /&gt; アクティビティは、実行するコンカレンシー分岐の数を制限するためのコンカレンシー要因を設定できるという 1 つの例外を除き、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティと似ていることについて示します。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-109">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="3ccb2-110">データベース アクセス アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3ccb2-110">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="3ccb2-111">データベースにアクセスして情報を取得または変更し、 [ADO.NET](../../data/adonet/index.md) を使用してデータベースにアクセスできるようにするアクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-111">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="3ccb2-112">.NET Framework 4.5 の外部化されたポリシー アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3ccb2-112">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="3ccb2-113">ExternalizedPolicy4 アクティビティを使用して、 <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] wf 3.5 に付属するルールエンジンを使用して、(wf 4.5) の Windows Workflow Foundation の .NET Framework 3.5 (wf 3.5) オブジェクトの既存の Windows Workflow Foundation を直接実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-113">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="3ccb2-114">非ジェネリックの ForEach</span><span class="sxs-lookup"><span data-stu-id="3ccb2-114">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="3ccb2-115"><xref:System.Activities.Statements.ForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-115">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3ccb2-116">非ジェネリックの ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="3ccb2-116">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="3ccb2-117"><xref:System.Activities.Statements.ParallelForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-117">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3ccb2-118">WorkflowInstanceId の取得</span><span class="sxs-lookup"><span data-stu-id="3ccb2-118">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="3ccb2-119">カスタム アクティビティ `GetWorkflowInstanceId` を使用して、ワークフロー インスタンス ID を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-119">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
