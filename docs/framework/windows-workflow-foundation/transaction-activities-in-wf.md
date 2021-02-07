---
description: '詳細情報: WF でのトランザクションアクティビティ'
title: WF におけるトランザクションのアクティビティ
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: f088c586998d3dbec8b94dcf0f02603a68b55a40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755136"
---
# <a name="transaction-activities-in-wf"></a><span data-ttu-id="946b0-103">WF におけるトランザクションのアクティビティ</span><span class="sxs-lookup"><span data-stu-id="946b0-103">Transaction Activities in WF</span></span>

<span data-ttu-id="946b0-104">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、トランザクションや、補正、取り消しをモデル化するためのシステム指定のアクティビティがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="946b0-104">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] has several system-provided activities for modeling transactions, compensation, and cancellation.</span></span> <span data-ttu-id="946b0-105">これらのプログラミング モデルにより、ビジネス ロジックとエラー処理の変更の場合に、ワークフローは進行を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="946b0-105">These programming models allow the workflow to continue forward progress in the event of changes in business logic and error handling.</span></span> <span data-ttu-id="946b0-106">トランザクション、補正、およびキャンセルの詳細については、「 [トランザクション](workflow-transactions.md)、 [補正](compensation.md)、および [キャンセル](modeling-cancellation-behavior-in-workflows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="946b0-106">For more information about transactions, compensation, and cancellation, see [Transactions](workflow-transactions.md), [Compensation](compensation.md), and [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
## <a name="transaction-activities"></a><span data-ttu-id="946b0-107">トランザクションのアクティビティ</span><span class="sxs-lookup"><span data-stu-id="946b0-107">Transaction Activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|<span data-ttu-id="946b0-108">アクティビティの形式のキャンセル ロジックを、アクティビティとしても表される実行のメイン パスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="946b0-108">Associates cancellation logic, in the form of an activity, with a main path of execution, also expressed as an activity.</span></span>|  
|<xref:System.Activities.Statements.CompensableActivity>|<span data-ttu-id="946b0-109">子アクティビティの補正をサポートします。</span><span class="sxs-lookup"><span data-stu-id="946b0-109">Supports compensation of its child activities.</span></span>|  
|<xref:System.Activities.Statements.Compensate>|<span data-ttu-id="946b0-110"><xref:System.Activities.Statements.CompensableActivity> の補正ハンドラーを明示的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="946b0-110">Explicitly invokes the compensation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.Confirm>|<span data-ttu-id="946b0-111"><xref:System.Activities.Statements.CompensableActivity> の確認ハンドラーを明示的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="946b0-111">Explicitly invokes the confirmation handler of a <xref:System.Activities.Statements.CompensableActivity>.</span></span>|  
|<xref:System.Activities.Statements.TransactionScope>|<span data-ttu-id="946b0-112">トランザクションの境界を設定します。</span><span class="sxs-lookup"><span data-stu-id="946b0-112">Demarcates a transaction boundary.</span></span>|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|<span data-ttu-id="946b0-113">受信したメッセージによって開始されるトランザクションの有効期間のスコープを設定します。</span><span class="sxs-lookup"><span data-stu-id="946b0-113">Scopes the lifetime of a transaction that is initiated by a received message.</span></span> <span data-ttu-id="946b0-114">トランザクションは、開始メッセージでワークフローにフローすることも、メッセージの受信時にディスパッチャーが作成することも可能です。</span><span class="sxs-lookup"><span data-stu-id="946b0-114">The transaction may be flowed into the workflow on the initiating message, or created by the dispatcher when the message is received.</span></span> <span data-ttu-id="946b0-115">**注:** は、 <xref:System.ServiceModel.Activities.TransactedReceiveScope> **ツールボックス** の [**メッセージング**] セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="946b0-115">**Note:**  The <xref:System.ServiceModel.Activities.TransactedReceiveScope> is located in the **Messaging** section of the **Toolbox**.</span></span>|
