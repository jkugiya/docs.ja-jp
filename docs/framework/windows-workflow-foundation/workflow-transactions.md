---
description: 詳細については、「ワークフロートランザクション」を参照してください。
title: ワークフロー トランザクション
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 105876179bcfe685bc65b209f0fbacb1d6eae5bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754876"
---
# <a name="workflow-transactions"></a><span data-ttu-id="62e76-103">ワークフロー トランザクション</span><span class="sxs-lookup"><span data-stu-id="62e76-103">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="62e76-104">は、<xref:System.Transactions> アクティビティを使用してトランザクション済み作業単位のスコープを設定することで、<xref:System.Activities.Statements.TransactionScope> トランザクションへの参加をサポートします。</span><span class="sxs-lookup"><span data-stu-id="62e76-104">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="62e76-105"><xref:System.Transactions.TransactionScope?displayProperty=nameWithType> は明示的に完了する必要がありますが、<xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> アクティビティは正常完了時にトランザクション上で暗黙的に完了を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="62e76-105">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="62e76-106"><xref:System.Activities.Statements.TransactionScope.Body%2A> アクティビティの <xref:System.Activities.Statements.TransactionScope> に含まれるすべてのアクティビティは、トランザクションに参加します。</span><span class="sxs-lookup"><span data-stu-id="62e76-106">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="62e76-107">WF は、<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを使用してワークフローにトランザクションをフローできます。</span><span class="sxs-lookup"><span data-stu-id="62e76-107">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="62e76-108"><xref:System.Activities.Statements.TransactionScope> アクティビティと同様に、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> に含まれるすべてのアクティビティはトランザクションに参加します。</span><span class="sxs-lookup"><span data-stu-id="62e76-108">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="62e76-109">WF は、<xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> に依存するアクティビティが、<xref:System.Activities.Statements.TransactionScope> と <xref:System.ServiceModel.Activities.TransactedReceiveScope> の両方で確実に動作するようにします。</span><span class="sxs-lookup"><span data-stu-id="62e76-109">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="62e76-110">システム標準アクティビティがすべての要件を満たさない場合、高度なフロー シナリオやトランザクション制御シナリオを可能にするには、<xref:System.Activities.RuntimeTransactionHandle> を使用してカスタム アクティビティを構築します。</span><span class="sxs-lookup"><span data-stu-id="62e76-110">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="62e76-111">次の例では、 <xref:System.Activities.Statements.Sequence> アクティビティを含む子アクティビティを含むアクティビティで構成されるワークフローを作成し <xref:System.Activities.Statements.TransactionScope> ます。</span><span class="sxs-lookup"><span data-stu-id="62e76-111">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="62e76-112"><xref:System.Activities.Statements.TransactionScope.Body%2A> の <xref:System.Activities.Statements.TransactionScope> アクティビティは、<xref:System.Activities.Statements.TransactionScope> アクティビティにより初期化されるトランザクションの下で実行されます。</span><span class="sxs-lookup"><span data-stu-id="62e76-112">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
<span data-ttu-id="62e76-113">詳細については、「の使用について」を参照してください <xref:System.ServiceModel.Activities.TransactedReceiveScope> 。[ワークフローサービスとの間でのトランザクションのフロー](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)</span><span class="sxs-lookup"><span data-stu-id="62e76-113">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e76-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="62e76-114">See also</span></span>

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
