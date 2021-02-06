---
description: 詳細については、「Request-Reply 関連付け」を参照してください。
title: 要求/応答の相関関係
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: e745c9061f227e08400973f43613da73e68c8d70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632842"
---
# <a name="request-reply-correlation"></a><span data-ttu-id="0ef85-103">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="0ef85-103">Request-Reply Correlation</span></span>

<span data-ttu-id="0ef85-104">要求/応答の相関関係は、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ワークフローサービスに双方向の操作を実装するためにペアと共に使用され、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 別の Web サービスで双方向の操作を実行するペアと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-104">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="0ef85-105">WCF サービスで双方向の操作を呼び出す場合、サービスは、従来の命令型コードベースの Windows Communication Foundation (WCF) サービスにすることも、ワークフローサービスにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-105">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="0ef85-106">要求/応答の相関関係を使用するには、<xref:System.ServiceModel.BasicHttpBinding> などの双方向のバインドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ef85-106">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="0ef85-107">双方向の操作を呼び出す場合と実装する場合では、相関関係の初期化に同様の手順が使用されます。これらの手順については、このセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="0ef85-107">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="0ef85-108">Receive/SendReply による双方向の操作での相関関係の使用</span><span class="sxs-lookup"><span data-stu-id="0ef85-108">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  

 <span data-ttu-id="0ef85-109"><xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ペアは、ワークフローサービスに双方向の操作を実装するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-109">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="0ef85-110">ランタイムは、要求/応答の相関関係を使用して、応答が正しい呼び出し元にディスパッチされるようにします。</span><span class="sxs-lookup"><span data-stu-id="0ef85-110">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="0ef85-111">ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合、つまり、ワークフロー サービスの場合は、既定の相関関係の初期化で十分です。</span><span class="sxs-lookup"><span data-stu-id="0ef85-111">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="0ef85-112">このシナリオでは、1つの <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ペアがワークフローによって使用され、特定の相関関係の構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="0ef85-112">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="0ef85-113">要求/応答の相関関係の明示的な初期化</span><span class="sxs-lookup"><span data-stu-id="0ef85-113">Explicitly Initializing Request-Reply Correlation</span></span>  

 <span data-ttu-id="0ef85-114">他の双方向の操作が並列実行される場合、相関関係を明示的に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ef85-114">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="0ef85-115">これを行うには、とを指定する <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> か、を内に配置し <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.CorrelationScope> ます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-115">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="0ef85-116">この例では、要求/応答の相関関係がペアで構成されてい <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-116">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="0ef85-117">相関関係を明示的に構成する代わりに、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-117">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="0ef85-118"><xref:System.ServiceModel.Activities.CorrelationScope> は、内包しているメッセージング アクティビティに暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> を提供します。</span><span class="sxs-lookup"><span data-stu-id="0ef85-118"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="0ef85-119">この例では、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ペアは内に含まれてい <xref:System.ServiceModel.Activities.CorrelationScope> ます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-119">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="0ef85-120">明示的な相関関係の構成は不要です。</span><span class="sxs-lookup"><span data-stu-id="0ef85-120">No explicit correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 <span data-ttu-id="0ef85-121">追加の相関関係が必要な場合は、目的の種類の <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> を使用する各メッセージング アクティビティの `CorrelationInitializer` プロパティを使用して、追加の相関関係を構成します。</span><span class="sxs-lookup"><span data-stu-id="0ef85-121">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="0ef85-122">Send/ReceiveReply による双方向の操作での相関関係の使用</span><span class="sxs-lookup"><span data-stu-id="0ef85-122">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  

 <span data-ttu-id="0ef85-123">アクティビティは、 <xref:System.ServiceModel.Activities.Receive> によってホストされるワークフローサービスでのみ使用できますが、この <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> ペアは、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> Web サービスでメソッドを呼び出す必要がある任意のワークフローで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-123">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="0ef85-124">ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされる場合は、前のセクションで説明した既定の相関関係が適用されますが、そうでない場合は、目的の <xref:System.ServiceModel.Activities.CorrelationInitializer> と <xref:System.ServiceModel.Activities.CorrelationHandle> を明示的に使用するか、<xref:System.ServiceModel.Activities.CorrelationScope> による暗黙の処理管理を使用して、相関関係を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ef85-124">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="0ef85-125">双方向の操作を使用するサービスで **サービス参照の追加** を使用する場合、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 明示的に指定された要求/応答の相関関係を使用してペアアクティビティを内部的にラップするアクティビティが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0ef85-125">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
