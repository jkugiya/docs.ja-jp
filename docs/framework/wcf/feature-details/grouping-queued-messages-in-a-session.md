---
description: 詳細については、「セッションでキューに置かれたメッセージをグループ化する」をご覧ください
title: セッションでキューに置かれたメッセージのグループ化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 5a23133090ebfd5db9f59bb37a69cdca83ce2bc0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793845"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="ac381-103">セッションでキューに置かれたメッセージのグループ化</span><span class="sxs-lookup"><span data-stu-id="ac381-103">Grouping Queued Messages in a Session</span></span>

<span data-ttu-id="ac381-104">Windows Communication Foundation (WCF) は、1つの受信アプリケーションで処理するために、一連の関連メッセージをまとめてグループ化できるセッションを提供します。</span><span class="sxs-lookup"><span data-stu-id="ac381-104">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="ac381-105">セッションに含まれるメッセージは、同じトランザクションに含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac381-105">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="ac381-106">すべてのメッセージが同じトランザクションに含まれるため、1 つのメッセージの処理が失敗すると、セッション全体がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="ac381-106">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="ac381-107">各セッションは、配信不能キューや有害キューに関してよく似た動作をします。</span><span class="sxs-lookup"><span data-stu-id="ac381-107">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="ac381-108">キューに置かれたバインディングに設定される有効期間 (TTL: Time To Live) プロパティがセッションに構成されている場合は、セッション全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ac381-108">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="ac381-109">したがって、TTL が切れる前にセッション内の一部のメッセージが送信された場合は、セッション全体が配信不能キューに配置されます。</span><span class="sxs-lookup"><span data-stu-id="ac381-109">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="ac381-110">同様に、アプリケーション キューからアプリケーションにセッション内のメッセージを送信できなかった場合は、セッション全体が有害キューに配置されます (有害キューを使用できる場合)。</span><span class="sxs-lookup"><span data-stu-id="ac381-110">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="ac381-111">メッセージのグループ化の例</span><span class="sxs-lookup"><span data-stu-id="ac381-111">Message Grouping Example</span></span>  

 <span data-ttu-id="ac381-112">メッセージのグループ化が役立つ例の1つは、注文処理アプリケーションを WCF サービスとして実装する場合です。</span><span class="sxs-lookup"><span data-stu-id="ac381-112">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="ac381-113">たとえば、クライアントがこのアプリケーションに多数の項目を含む注文を送信するとします。</span><span class="sxs-lookup"><span data-stu-id="ac381-113">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="ac381-114">このクライアントは、項目ごとにサービスを呼び出すため、個別のメッセージが送信されることになります。</span><span class="sxs-lookup"><span data-stu-id="ac381-114">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="ac381-115">このため、最初の項目はサーバー A で受信され、2 番目の項目はサーバー B で受信される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac381-115">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="ac381-116">項目が追加されるたびに、この項目を処理するサーバーは適切な注文を見つけて項目を追加する必要があるため、効率が非常に悪くなります。</span><span class="sxs-lookup"><span data-stu-id="ac381-116">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="ac381-117">すべての要求を 1 台のサーバーのみで処理する場合でも、現在処理中のすべての注文をこのサーバーによって常に把握し、新しい項目がどの注文に属するものなのかを判別する必要があるため、同様の非効率が生じます。</span><span class="sxs-lookup"><span data-stu-id="ac381-117">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="ac381-118">単一の注文に属するすべての要求をグループ化すると、このようなアプリケーションの実装は大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="ac381-118">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="ac381-119">1 つの注文に属するすべての項目が 1 セッションとしてクライアント アプリケーションから送信されるため、サービスは注文を処理するときにセッション全体を 1 回で処理できます。</span><span class="sxs-lookup"><span data-stu-id="ac381-119">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="ac381-120">手順</span><span class="sxs-lookup"><span data-stu-id="ac381-120">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="ac381-121">セッションを使用するようにサービス コントラクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="ac381-121">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="ac381-122">セッションを必要とするサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="ac381-122">Define a service contract that requires a session.</span></span> <span data-ttu-id="ac381-123">次のように指定して、属性を使用してこれを行い <xref:System.ServiceModel.ServiceContractAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="ac381-123">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="ac381-124">これらのメソッドは何も返さないため、コントラクト内の操作を一方向としてマークします。</span><span class="sxs-lookup"><span data-stu-id="ac381-124">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="ac381-125">これを行うには、 <xref:System.ServiceModel.OperationContractAttribute> 次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="ac381-125">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="ac381-126">サービス コントラクトを実装し、<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> に <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType> を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac381-126">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac381-127">これにより、セッションごとに 1 回だけサービスがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="ac381-127">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="ac381-128">各サービス操作には、トランザクションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="ac381-128">Each service operation requires a transaction.</span></span> <span data-ttu-id="ac381-129">これを指定するには <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac381-129">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="ac381-130">トランザクションを完了する操作では、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> を `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac381-130">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. <span data-ttu-id="ac381-131">システム指定の `NetMsmqBinding` バインディングを使用するエンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="ac381-131">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="ac381-132"><xref:System.Messaging> を使用してトランザクション キューを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac381-132">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="ac381-133">代わりに、MSMQ (メッセージ キュー) または MMC を使用してキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac381-133">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="ac381-134">この場合、トランザクション キューを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac381-134">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="ac381-135"><xref:System.ServiceModel.ServiceHost> を使用して、サービスのサービス ホストを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac381-135">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="ac381-136">サービス ホストを開いてサービスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ac381-136">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="ac381-137">サービス ホストを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ac381-137">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="ac381-138">クライアントを設定するには</span><span class="sxs-lookup"><span data-stu-id="ac381-138">To set up a client</span></span>  
  
1. <span data-ttu-id="ac381-139">トランザクションのスコープを作成してトランザクション キューに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ac381-139">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="ac381-140">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)ツールを使用して、WCF クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac381-140">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="ac381-141">注文を行います。</span><span class="sxs-lookup"><span data-stu-id="ac381-141">Place the order.</span></span>  
  
4. <span data-ttu-id="ac381-142">WCF クライアントを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ac381-142">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac381-143">例</span><span class="sxs-lookup"><span data-stu-id="ac381-143">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ac381-144">説明</span><span class="sxs-lookup"><span data-stu-id="ac381-144">Description</span></span>  

 <span data-ttu-id="ac381-145">次の例では、`IProcessOrder` サービス、およびこのサービスを使用するクライアントのコードを示します。</span><span class="sxs-lookup"><span data-stu-id="ac381-145">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="ac381-146">ここでは、WCF がキューに置かれたセッションを使用してグループ化の動作を提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ac381-146">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="ac381-147">サービスのコード</span><span class="sxs-lookup"><span data-stu-id="ac381-147">Code for the Service</span></span>  

 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="ac381-148">クライアントのコード</span><span class="sxs-lookup"><span data-stu-id="ac381-148">Code for the Client</span></span>  

 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="ac381-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac381-149">See also</span></span>

- [<span data-ttu-id="ac381-150">セッションとキュー</span><span class="sxs-lookup"><span data-stu-id="ac381-150">Sessions and Queues</span></span>](../samples/sessions-and-queues.md)
- [<span data-ttu-id="ac381-151">キューの概要</span><span class="sxs-lookup"><span data-stu-id="ac381-151">Queues Overview</span></span>](queues-overview.md)
