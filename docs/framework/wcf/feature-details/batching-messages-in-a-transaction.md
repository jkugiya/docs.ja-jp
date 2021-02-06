---
description: 詳細については、「トランザクション内のメッセージのバッチ処理」を参照してください。
title: トランザクションに含まれるメッセージのバッチ処理
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 0c84d87bc043f4ce1ae4d0a7674e862aa10011ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643697"
---
# <a name="batching-messages-in-a-transaction"></a><span data-ttu-id="08d98-103">トランザクションに含まれるメッセージのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="08d98-103">Batching Messages in a Transaction</span></span>

<span data-ttu-id="08d98-104">キューに置かれたアプリケーションは、トランザクションを使用してメッセージの正確性および信頼性のある配信を確保します。</span><span class="sxs-lookup"><span data-stu-id="08d98-104">Queued applications use transactions to ensure correctness and reliable delivery of messages.</span></span> <span data-ttu-id="08d98-105">ただし、トランザクション操作には負荷がかかるため、メッセージのスループットが大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08d98-105">Transactions, however, are expensive operations and can dramatically reduce message throughput.</span></span> <span data-ttu-id="08d98-106">メッセージ スループットを向上する方法の 1 つは、アプリケーションにより、単一のトランザクション内で複数のメッセージを読み取って処理することです。</span><span class="sxs-lookup"><span data-stu-id="08d98-106">One way to improve message throughput is to have an application read and process multiple messages within a single transaction.</span></span> <span data-ttu-id="08d98-107">ただし、その場合、バッチ内のメッセージ数が増えるにつれて、トランザクションをロールバックしたときに必要な回復の作業量も増えるため、パフォーマンスと回復の間のトレードオフを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08d98-107">The trade-off is between performance and recovery: as the number of messages in a batch increases, so does the amount of recovery work that required if transactions are rolled back.</span></span> <span data-ttu-id="08d98-108">したがって、トランザクションでのメッセージのバッチ処理とセッションの違いに注目することが重要です。</span><span class="sxs-lookup"><span data-stu-id="08d98-108">It is important to note the difference between batching messages in a transaction and sessions.</span></span> <span data-ttu-id="08d98-109">*セッション* とは、1つのアプリケーションによって処理され、1つの単位としてコミットされる、関連するメッセージのグループです。</span><span class="sxs-lookup"><span data-stu-id="08d98-109">A *session* is a grouping of related messages that are processed by a single application and committed as a single unit.</span></span> <span data-ttu-id="08d98-110">セッションは、一般に、関連メッセージのグループをまとめて処理する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-110">Sessions are generally used when a group of related messages must be processed together.</span></span> <span data-ttu-id="08d98-111">この例として、オンライン ショッピング Web サイトがあります。</span><span class="sxs-lookup"><span data-stu-id="08d98-111">An example of this is an online shopping Web site.</span></span> <span data-ttu-id="08d98-112">*バッチ* は、メッセージのスループットを向上させる方法で、関連のない複数のメッセージを処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-112">*Batches* are used to process multiple, unrelated messages in a way that increases message throughput.</span></span> <span data-ttu-id="08d98-113">セッションの詳細については、「 [セッションでキューに置かれたメッセージをグループ化する](grouping-queued-messages-in-a-session.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d98-113">For more information about sessions, see [Grouping Queued Messages in a Session](grouping-queued-messages-in-a-session.md).</span></span> <span data-ttu-id="08d98-114">バッチ内のメッセージもまた、単一のアプリケーションによって処理され、1 つの単位としてコミットされますが、バッチ内のメッセージが関連している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="08d98-114">Messages in a batch are also processed by a single application and committed as a single unit, but there may be no relationship between the messages in the batch.</span></span> <span data-ttu-id="08d98-115">トランザクションでのメッセージのバッチ処理は、アプリケーションの実行方法を変更しない最適化です。</span><span class="sxs-lookup"><span data-stu-id="08d98-115">Batching messages in a transaction is an optimization that does not change how the application runs.</span></span>  
  
## <a name="entering-batching-mode"></a><span data-ttu-id="08d98-116">バッチ処理モードの開始</span><span class="sxs-lookup"><span data-stu-id="08d98-116">Entering Batching Mode</span></span>  

 <span data-ttu-id="08d98-117">バッチ処理は、<xref:System.ServiceModel.Description.TransactedBatchingBehavior> エンドポイント動作によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-117">The <xref:System.ServiceModel.Description.TransactedBatchingBehavior> endpoint behavior controls batching.</span></span> <span data-ttu-id="08d98-118">このエンドポイント動作をサービスエンドポイントに追加すると、トランザクション内のメッセージをバッチ処理するように Windows Communication Foundation (WCF) に指示されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-118">Adding this endpoint behavior to a service endpoint tells Windows Communication Foundation (WCF) to batch messages in a transaction.</span></span> <span data-ttu-id="08d98-119">すべてのメッセージでトランザクションが要求されるわけではないので、トランザクションを必要とするメッセージのみがバッチに格納され、とでマークされた操作から送信されたメッセージのみがバッチで考慮され `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` ます。</span><span class="sxs-lookup"><span data-stu-id="08d98-119">Not all messages require a transaction, so only messages that require a transaction are placed in a batch, and only messages sent from operations marked with `TransactionScopeRequired` = `true` and `TransactionAutoComplete` = `true` are considered for a batch.</span></span> <span data-ttu-id="08d98-120">サービスコントラクトに対するすべての操作がとでマークされている場合 `TransactionScopeRequired`  =  `false` `TransactionAutoComplete`  =  `false` 、バッチモードは入力されません。</span><span class="sxs-lookup"><span data-stu-id="08d98-120">If all operations on the service contract are marked with `TransactionScopeRequired` = `false` and `TransactionAutoComplete` = `false`, then batching mode is never entered.</span></span>  
  
## <a name="committing-a-transaction"></a><span data-ttu-id="08d98-121">トランザクションのコミット</span><span class="sxs-lookup"><span data-stu-id="08d98-121">Committing a Transaction</span></span>  

 <span data-ttu-id="08d98-122">バッチ トランザクションは、次の基準に基づいてコミットされます。</span><span class="sxs-lookup"><span data-stu-id="08d98-122">A batched transaction is committed based on the following:</span></span>  
  
- <span data-ttu-id="08d98-123">`MaxBatchSize`.</span><span class="sxs-lookup"><span data-stu-id="08d98-123">`MaxBatchSize`.</span></span> <span data-ttu-id="08d98-124"><xref:System.ServiceModel.Description.TransactedBatchingBehavior> 動作のプロパティ。</span><span class="sxs-lookup"><span data-stu-id="08d98-124">A property of the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> behavior.</span></span> <span data-ttu-id="08d98-125">このプロパティは、バッチに含められるメッセージの最大数を決定します。</span><span class="sxs-lookup"><span data-stu-id="08d98-125">This property determines the maximum number of messages that are placed into a batch.</span></span> <span data-ttu-id="08d98-126">この数に達すると、バッチがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="08d98-126">When this number is reached, the batch is committed.</span></span> <span data-ttu-id="08d98-127">この値は厳密に定められたものではないため、この数のメッセージを受信する前にバッチをコミットすることもできます。</span><span class="sxs-lookup"><span data-stu-id="08d98-127">This is value is not a strict limit, it is possible to commit a batch before receiving this number of messages.</span></span>  
  
- <span data-ttu-id="08d98-128">`Transaction Timeout`.</span><span class="sxs-lookup"><span data-stu-id="08d98-128">`Transaction Timeout`.</span></span> <span data-ttu-id="08d98-129">トランザクションのタイムアウトの 80% が経過すると、バッチがコミットされ、新しいバッチが作成されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-129">After 80 percent of the transaction's time-out has elapsed, the batch is committed and a new batch is created.</span></span> <span data-ttu-id="08d98-130">つまり、トランザクションが完了するために指定された時間の残りが 20% 以下になると、バッチがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="08d98-130">This means that if 20 percent or less of the time given for a transaction to complete remains, the batch is committed.</span></span>  
  
- <span data-ttu-id="08d98-131">`TransactionScopeRequired`.</span><span class="sxs-lookup"><span data-stu-id="08d98-131">`TransactionScopeRequired`.</span></span> <span data-ttu-id="08d98-132">メッセージのバッチを処理するときに、があるバッチを検出すると、そのバッチが `TransactionScopeRequired`  =  `false` コミットされ、との最初のメッセージの受信時に新しいバッチが再度開かれ `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` ます。</span><span class="sxs-lookup"><span data-stu-id="08d98-132">When processing a batch of messages, if WCF finds one that has `TransactionScopeRequired` = `false`, it commits the batch and reopens a new batch on receipt of the first message with `TransactionScopeRequired` = `true` and `TransactionAutoComplete` = `true`.</span></span>  
  
- <span data-ttu-id="08d98-133">キューのメッセージがなくなると、`MaxBatchSize` に達していない場合やトランザクションのタイムアウトの 80% が経過していない場合でも、現在のバッチがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="08d98-133">If no more messages exist in the queue, then the current batch is committed, even if the `MaxBatchSize` has not been reached or 80 percent of the transaction's time-out has not elapsed.</span></span>  
  
## <a name="leaving-batching-mode"></a><span data-ttu-id="08d98-134">バッチ処理モードの終了</span><span class="sxs-lookup"><span data-stu-id="08d98-134">Leaving Batching Mode</span></span>  

 <span data-ttu-id="08d98-135">バッチ内のメッセージによってトランザクションが中止されたときの動作は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="08d98-135">If a message in a batch causes the transaction to abort, the following steps occur:</span></span>  
  
1. <span data-ttu-id="08d98-136">メッセージのバッチ全体がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="08d98-136">The entire batch of messages is rolled back.</span></span>  
  
2. <span data-ttu-id="08d98-137">読み取られたメッセージの数がバッチの最大サイズの 2 倍を超えるまで、一度に 1 つのメッセージが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="08d98-137">Messages are read one at a time until the number of messages read exceeds twice the maximum batch size.</span></span>  
  
3. <span data-ttu-id="08d98-138">再度、バッチ モードに入ります。</span><span class="sxs-lookup"><span data-stu-id="08d98-138">Batch mode is re-entered.</span></span>  
  
## <a name="choosing-the-batch-size"></a><span data-ttu-id="08d98-139">バッチ サイズの選択</span><span class="sxs-lookup"><span data-stu-id="08d98-139">Choosing the Batch Size</span></span>  

 <span data-ttu-id="08d98-140">バッチのサイズは、アプリケーションに依存します。</span><span class="sxs-lookup"><span data-stu-id="08d98-140">The size of a batch is application-dependent.</span></span> <span data-ttu-id="08d98-141">アプリケーションに最適なバッチ サイズは、経験に基づいて決定するのが最良の方法です。</span><span class="sxs-lookup"><span data-stu-id="08d98-141">The empirical method is the best way to arrive at an optimal batch size for the application.</span></span> <span data-ttu-id="08d98-142">バッチ サイズを選択する際には、アプリケーションの実際の展開モデルに応じたサイズを選択することが重要です。</span><span class="sxs-lookup"><span data-stu-id="08d98-142">It is important to remember when choosing a batch size to choose the size according to your application's actual deployment model.</span></span> <span data-ttu-id="08d98-143">たとえば、アプリケーションの展開で、リモート コンピューターに SQL サーバーを配置し、キューとその SQL サーバーにまたがるトランザクションを実行する必要がある場合は、そのとおりの構成を実行してバッチ サイズを決定するのが最良の方法です。</span><span class="sxs-lookup"><span data-stu-id="08d98-143">For example, when deploying the application, if you need an SQL server on a remote machine and a transaction that spans the queue and the SQL server, then the batch size is best determined by running this exact configuration.</span></span>  
  
## <a name="concurrency-and-batching"></a><span data-ttu-id="08d98-144">コンカレンシーとバッチ処理</span><span class="sxs-lookup"><span data-stu-id="08d98-144">Concurrency and Batching</span></span>  

 <span data-ttu-id="08d98-145">スループットを向上させるために、多数のバッチを同時に実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="08d98-145">To increase throughput, you can also have many batches run concurrently.</span></span> <span data-ttu-id="08d98-146">同時バッチ処理を有効にするには、`ConcurrencyMode.Multiple` の `ServiceBehaviorAttribute` を設定します。</span><span class="sxs-lookup"><span data-stu-id="08d98-146">By setting `ConcurrencyMode.Multiple` in `ServiceBehaviorAttribute`, you enable concurrent batching.</span></span>  
  
 <span data-ttu-id="08d98-147">サービスの *調整* とは、サービスに対して同時に実行できる最大呼び出し数を示すために使用されるサービスの動作です。</span><span class="sxs-lookup"><span data-stu-id="08d98-147">*Service throttling* is a service behavior that is used to indicate how many maximum concurrent calls can be made on the service.</span></span> <span data-ttu-id="08d98-148">この動作をバッチ処理で使用すると、実行できる同時バッチの数と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-148">When used with batching, this is interpreted as how many concurrent batches can be run.</span></span> <span data-ttu-id="08d98-149">サービス調整が設定されていない場合、WCF では、同時呼び出しの最大数が既定で16に設定されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-149">If the service throttling is not set, WCF defaults the maximum concurrent calls to 16.</span></span> <span data-ttu-id="08d98-150">したがって、バッチ動作が既定で追加されると、最大で 16 個のバッチが同時にアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="08d98-150">Thus, if batching behavior were added by default, a maximum of 16 batches can be active at the same time.</span></span> <span data-ttu-id="08d98-151">容量に基づいてサービス調整とバッチ処理を調整することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="08d98-151">It is best to tune the service throttling and batching based on your capacity.</span></span> <span data-ttu-id="08d98-152">たとえば、キューに 100 個のメッセージがあり、20 個のメッセージを含むバッチを実行する必要がある場合、同時呼び出しの最大数を 16 に設定しても実用的ではありません。それは、スループットによっては、バッチ処理をオンにしていない場合と同様に、16 個のトランザクションがアクティブになる可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="08d98-152">For example, if the queue has 100 messages and a batch of 20 is desired, having the maximum concurrent calls set to 16 is not useful because, depending on throughput, 16 transactions could be active, similar to not having batching turned on.</span></span> <span data-ttu-id="08d98-153">したがって、パフォーマンスを微調整するためには、同時バッチ処理を設定しないか、正しいサービス調整のサイズで同時バッチ処理を設定します。</span><span class="sxs-lookup"><span data-stu-id="08d98-153">Therefore, when fine-tuning for performance, either do not have concurrent batching or have concurrent batching with the correct service throttle size.</span></span>  
  
## <a name="batching-and-multiple-endpoints"></a><span data-ttu-id="08d98-154">バッチ処理と複数のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="08d98-154">Batching and Multiple Endpoints</span></span>  

 <span data-ttu-id="08d98-155">エンドポイントは、アドレスとコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="08d98-155">An endpoint is composed of an address and a contract.</span></span> <span data-ttu-id="08d98-156">同じバインディングを共有するエンドポイントが複数ある場合があります。</span><span class="sxs-lookup"><span data-stu-id="08d98-156">There may be multiple endpoints that share the same binding.</span></span> <span data-ttu-id="08d98-157">2 つのエンドポイントが同じバインディングと、リッスン URI (Uniform Resource Identifier) つまりキュー アドレスを共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="08d98-157">It is possible for two endpoints to share the same binding and listen Uniform Resource Identifier (URI), or queue address.</span></span> <span data-ttu-id="08d98-158">2 つのエンドポイントが同じキューから読み取りを行っている場合、トランザクション バッチ動作を両方のエンドポイントに追加すると、指定したバッチ サイズ間で競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08d98-158">If two endpoints are reading from the same queue, and transacted batching behavior is added to both endpoints, a conflict in the batch sizes specified could arise.</span></span> <span data-ttu-id="08d98-159">この問題を解決するには、2 つのトランザクション バッチ動作の間に指定される最小バッチ サイズを使用してバッチを実装します。</span><span class="sxs-lookup"><span data-stu-id="08d98-159">This is resolved by implementing batching using the minimal batch size specified between the two transacted batching behaviors.</span></span> <span data-ttu-id="08d98-160">このシナリオでは、どちらかのエンドポイントがトランザクション バッチを指定していない場合、両方のエンドポイントがバッチ処理を使用しません。</span><span class="sxs-lookup"><span data-stu-id="08d98-160">In this scenario, if one of the endpoints does not specify transacted batching, then both endpoints would not use batching.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08d98-161">例</span><span class="sxs-lookup"><span data-stu-id="08d98-161">Example</span></span>  

 <span data-ttu-id="08d98-162">構成ファイルで `TransactedBatchingBehavior` を指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="08d98-162">The following example shows how to specify the `TransactedBatchingBehavior` in a configuration file.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 <span data-ttu-id="08d98-163">コードで <xref:System.ServiceModel.Description.TransactedBatchingBehavior> を指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="08d98-163">The following example shows how to specify the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> in code.</span></span>  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));

     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="08d98-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="08d98-164">See also</span></span>

- [<span data-ttu-id="08d98-165">キューの概要</span><span class="sxs-lookup"><span data-stu-id="08d98-165">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="08d98-166">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="08d98-166">Queuing in WCF</span></span>](queuing-in-wcf.md)
