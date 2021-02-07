---
description: '詳細情報: 順序を超えたメッセージの処理'
title: 順番を無視したメッセージの処理
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4349b7d72c080dff579eda18ce51de99ab5e91fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733607"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="1ee98-103">順番を無視したメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="1ee98-103">Out-of-Order Message Processing</span></span>

<span data-ttu-id="1ee98-104">ワークフロー サービスは、特定の順序で送信されるメッセージに依存する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1ee98-104">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="1ee98-105">ワークフロー サービスには 1 つ以上の <xref:System.ServiceModel.Activities.Receive> アクティビティが含まれ、それぞれの <xref:System.ServiceModel.Activities.Receive> アクティビティは特定のメッセージに対応しています。</span><span class="sxs-lookup"><span data-stu-id="1ee98-105">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="1ee98-106">特定のトランスポート配信保証がないと、クライアントから送信されるメッセージに遅延が生じ、それによって、ワークフロー サービスが予期しない順序でメッセージが配信されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1ee98-106">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="1ee98-107">特定の順序でメッセージが送信されることを必要としないワークフローは、通常、Parallel アクティビティを使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="1ee98-107">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="1ee98-108">アプリケーション プロトコルがより複雑な場合は、ワークフローがすぐに複雑になります。</span><span class="sxs-lookup"><span data-stu-id="1ee98-108">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="1ee98-109">Windows Communication Foundation (WCF) の順序を指定しないメッセージ処理機能を使用すると、入れ子になった並列アクティビティがすべて複雑になることなく、このようなワークフローを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1ee98-109">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="1ee98-110">順序を区別しないメッセージ処理は、WCF MSMQ バインドなどをサポートするチャネルでのみサポートされてい <xref:System.ServiceModel.Channels.ReceiveContext> ます。</span><span class="sxs-lookup"><span data-stu-id="1ee98-110">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="1ee98-111">順番を無視したメッセージ処理の有効化</span><span class="sxs-lookup"><span data-stu-id="1ee98-111">Enabling Out-Of-Order Message Processing</span></span>  

 <span data-ttu-id="1ee98-112">順番を無視したメッセージ処理は、ワークフロー サービスで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを `true` に設定することで有効化できます。</span><span class="sxs-lookup"><span data-stu-id="1ee98-112">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="1ee98-113">次の例は、コードで <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> プロパティを設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1ee98-113">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="1ee98-114">また、次の例に示すように、XAML で `AllowBufferedReceive` 属性をワークフロー サービスに適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ee98-114">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ee98-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ee98-115">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="1ee98-116">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="1ee98-116">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="1ee98-117">キューと信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="1ee98-117">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
