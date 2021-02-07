---
description: '詳細情報: メッセージの相関関係'
title: メッセージ相関
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: e38e2e8d6936132e165fd3372ac57fef27240d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704031"
---
# <a name="message-correlation"></a><span data-ttu-id="f1f5a-103">メッセージ相関</span><span class="sxs-lookup"><span data-stu-id="f1f5a-103">Message Correlation</span></span>

<span data-ttu-id="f1f5a-104">このサンプルでは、メッセージキュー (MSMQ) アプリケーションが MSMQ メッセージを Windows Communication Foundation (WCF) サービスに送信する方法と、要求/応答シナリオでメッセージを送信側と受信側のアプリケーション間で相互に関連付ける方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-104">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="f1f5a-105">このサンプルでは、msmqIntegrationBinding バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-105">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="f1f5a-106">この場合、サービスは自己ホスト型コンソール アプリケーションで、サービスがキュー内のメッセージを受信したかどうかを監視できます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-106">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="f1f5a-107">k</span><span class="sxs-lookup"><span data-stu-id="f1f5a-107">k</span></span>

 <span data-ttu-id="f1f5a-108">サービスは、送信側からの受信メッセージを処理し、送信側に応答メッセージを返信します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-108">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="f1f5a-109">送信側は、受信した応答を、最初に送信した要求に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-109">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="f1f5a-110">メッセージの `MessageID` プロパティと `CorrelationID` プロパティを使用すると、要求メッセージと応答メッセージが関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-110">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>

 <span data-ttu-id="f1f5a-111">`IOrderProcessor` サービス コントラクトは、キューでの使用に適した一方向サービス操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-111">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="f1f5a-112">MSMQ メッセージには Action ヘッダーがないので、さまざまな MSMQ メッセージを操作コントラクトに自動的にマッピングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-112">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="f1f5a-113">したがってこの場合、存在する操作コントラクトは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-113">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="f1f5a-114">サービス内に複数の操作コントラクトを定義する場合は、ディスパッチする操作コントラクトを決定するために使用できる、MSMQ メッセージ内のヘッダー (ラベルや correlationID など) に関する情報をアプリケーションで提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-114">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="f1f5a-115">さらに、MSMQ メッセージには、操作コントラクトの別のパラメータにマッピングされるヘッダーに関する情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="f1f5a-116">したがって、操作コントラクトに存在するパラメータは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="f1f5a-117">パラメーターの型は <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> で、基になる MSMQ メッセージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-117">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="f1f5a-118">`MsmqMessage<T>` クラスの型 "T" は、シリアル化されて MSMQ メッセージ本文に含まれているデータを表します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="f1f5a-119">このサンプルでは、`PurchaseOrder` 型がシリアル化されて MSMQ メッセージ本文になっています。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="f1f5a-120">このサービス操作は発注書を処理し、サービス コンソール ウィンドウにその発注書の内容と状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="f1f5a-121"><xref:System.ServiceModel.OperationBehaviorAttribute> はこの操作を構成してキューを伴うトランザクションに登録し、操作が返されたときにトランザクションに完了とマークします。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="f1f5a-122">`PurchaseOrder` には、サービスで処理する必要のある発注の詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 <span data-ttu-id="f1f5a-123">サービスは、MSMQ メッセージをキューに送信するためにカスタム クライアント `OrderResponseClient` を使用します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="f1f5a-124">メッセージを受信して処理するアプリケーションは MSMQ アプリケーションであり、WCF アプリケーションではないため、2つのアプリケーション間に暗黙のサービスコントラクトはありません。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-124">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="f1f5a-125">したがって、このシナリオでは Svcutil.exe ツールを使用してプロキシを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="f1f5a-126">カスタムプロキシは、バインディングを使用してメッセージを送信するすべての WCF アプリケーションで基本的に同じです `msmqIntegrationBinding` 。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-126">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="f1f5a-127">他のプロキシと異なり、サービス操作の範囲は含まれません。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="f1f5a-128">メッセージ送信操作のみです。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-128">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 <span data-ttu-id="f1f5a-129">サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-129">The service is self hosted.</span></span> <span data-ttu-id="f1f5a-130">MSMQ 統合トランスポートを使用する場合、使用するキューをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="f1f5a-131">手動で作成することもコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-131">This can be done manually or through code.</span></span> <span data-ttu-id="f1f5a-132">このサンプルでは、キューの存在を確認して、必要な場合は作成するための <xref:System.Messaging> コードがサービスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="f1f5a-133">キュー名は構成ファイルから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-133">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 <span data-ttu-id="f1f5a-134">発注要求が送信される MSMQ キューは、構成ファイルの appSettings セクションで指定されます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="f1f5a-135">クライアントおよびサービスのエンドポイントは、構成ファイルの system.serviceModel セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="f1f5a-136">どちらも `msmqIntegrationbinding` バインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-136">Both specify the `msmqIntegrationbinding` binding.</span></span>

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 <span data-ttu-id="f1f5a-137">クライアント アプリケーションは <xref:System.Messaging> を使用して、非揮発性メッセージとトランザクション メッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="f1f5a-138">メッセージの本文には発注書が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-138">The message's body contains the purchase order.</span></span>

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
    // Create the purchase order.
    PurchaseOrder po = new PurchaseOrder();
    po.CustomerId = "somecustomer.com";
    po.PONumber = Guid.NewGuid().ToString();
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
    lineItem1.ProductId = "Blue Widget";
    lineItem1.Quantity = 54;
    lineItem1.UnitCost = 29.99F;

    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
    lineItem2.ProductId = "Red Widget";
    lineItem2.Quantity = 890;
    lineItem2.UnitCost = 45.89F;

    po.orderLineItems = new PurchaseOrderLineItem[2];
    po.orderLineItems[0] = lineItem1;
    po.orderLineItems[1] = lineItem2;

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 <span data-ttu-id="f1f5a-139">発注の応答を受信する MSMQ キューは、構成ファイルの appSettings セクションで指定されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f1f5a-140">キュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="f1f5a-141">WCF エンドポイントアドレスでは、formatname スキーマを指定し、ローカルコンピューターに "localhost" を使用します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-141">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="f1f5a-142">URI の msmq.formatname の後には、MSMQ ガイドラインに沿って正しく書式設定された形式名が続きます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="f1f5a-143">クライアント アプリケーションは、サービスに送信する発注要求メッセージの `messageID` を保存し、サービスからの応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="f1f5a-144">応答がキューに到着すると、クライアントは発注メッセージの `correlationID` プロパティを使用して、送信した発注メッセージと応答を関連付けます。このプロパティには、クライアントが最初にサービスに送信した発注メッセージの `messageID` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 <span data-ttu-id="f1f5a-145">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f1f5a-146">サービスがクライアントからメッセージを受信し、クライアントに応答を返信するアクティビティを参照できます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="f1f5a-147">クライアントでは、サービスから受信した応答が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-147">The client displays the response received from the service.</span></span> <span data-ttu-id="f1f5a-148">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-148">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="f1f5a-149">このサンプルを実行するには、メッセージ キュー (MSMQ) がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="f1f5a-150">インストールの手順については、「参照」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-150">See the MSMQ installation instructions in the See Also section.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="f1f5a-151">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="f1f5a-151">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="f1f5a-152">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f1f5a-153">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f1f5a-154">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f1f5a-155">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f1f5a-156">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-156">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f1f5a-157">Visual Studio 2012 でサーバーマネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-157">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f1f5a-158">[ **機能** ] タブを展開します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-158">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f1f5a-159">[ **プライベートメッセージキュー**] を右クリックし、[ **新規**]、[ **プライベートキュー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f1f5a-160">[ **トランザクション** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-160">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f1f5a-161">`ServiceModelSamplesTransacted`新しいキューの名前として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f1f5a-162">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="f1f5a-163">1台のコンピューター構成でサンプルを実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="f1f5a-164">コンピューター間でサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="f1f5a-164">Run the sample across computers</span></span>

1. <span data-ttu-id="f1f5a-165">サービスのプログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="f1f5a-166">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="f1f5a-167">Client.exe.config ファイルを開き、orderQueueName を変更して "." の代わりにサービス コンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="f1f5a-168">Service.exe.config ファイルで、クライアント エンドポイントのアドレスを変更して "." の代わりにクライアント コンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="f1f5a-169">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-169">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="f1f5a-170">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-170">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1f5a-171">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f1f5a-172">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-172">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f1f5a-173">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1f5a-174">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f1f5a-174">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a><span data-ttu-id="f1f5a-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1f5a-175">See also</span></span>

- [<span data-ttu-id="f1f5a-176">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="f1f5a-176">Queuing in WCF</span></span>](../feature-details/queuing-in-wcf.md)
- <span data-ttu-id="f1f5a-177">[メッセージ キューイング (Message Queuing)](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f1f5a-177">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
