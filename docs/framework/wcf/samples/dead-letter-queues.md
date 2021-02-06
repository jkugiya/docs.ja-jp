---
description: 配信不能キューについての詳細情報
title: 配信不能キュー
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 5cec218f993fd99d1419aab884addfba686337c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632153"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="f1bdd-103">配信不能キュー</span><span class="sxs-lookup"><span data-stu-id="f1bdd-103">Dead Letter Queues</span></span>

<span data-ttu-id="f1bdd-104">このサンプルでは、配信できなかったメッセージの処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-104">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="f1bdd-105">これは、トランザクション処理された [MSMQ バインディング](transacted-msmq-binding.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-105">It is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="f1bdd-106">このサンプルでは、`netMsmqBinding` バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-106">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="f1bdd-107">サービスは自己ホスト型コンソール アプリケーションであるので、キューに置かれたメッセージをサービスが受信するようすを観察できます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-107">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bdd-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bdd-109">このサンプルでは、Windows Vista でのみ使用できるアプリケーション配信不能キューを示します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-109">This sample demonstrates each application dead letter queue that is only available on Windows Vista.</span></span> <span data-ttu-id="f1bdd-110">このサンプルは、Windows Server 2003 および Windows XP 上の MSMQ 3.0 の既定のシステム全体のキューを使用するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-110">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on Windows Server 2003 and Windows XP.</span></span>

 <span data-ttu-id="f1bdd-111">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f1bdd-112">厳密には、クライアントはメッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f1bdd-113">サービスは、メッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-113">The service receives messages from the queue.</span></span> <span data-ttu-id="f1bdd-114">したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="f1bdd-115">キューを使用する通信では一定の活動停止状態が生じるので、メッセージの有効期間を設定して、有効期間経過後はメッセージをアプリケーションに配信しないようにすることが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-115">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="f1bdd-116">また、アプリケーションによっては、メッセージの配信が失敗したかどうかを通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-116">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="f1bdd-117">このような場合に、メッセージの有効期間が経過すると、あるいはメッセージの配信に失敗すると、メッセージは配信不能キューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-117">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="f1bdd-118">このとき、送信元のアプリケーションは、配信不能キューに置かれたメッセージを読み取って是正措置を行います。是正措置とは、何も行わない場合から、配信失敗の原因を解消してメッセージを再送信する場合までさまざまです。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-118">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="f1bdd-119">`NetMsmqBinding` バインディングの配信不能キューは、次のプロパティとして表されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-119">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="f1bdd-120"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> プロパティは、クライアントが必要とする配信不能キューの種類を表します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-120"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="f1bdd-121">この列挙体には、次の値があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-121">This enumeration has the following values:</span></span>

- <span data-ttu-id="f1bdd-122">`None` : クライアントは配信不能キューを必要としません。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-122">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="f1bdd-123">`System`: システムの配信不能キューを使用して配信不能メッセージを保存します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-123">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="f1bdd-124">システムの配信不能キューは、そのコンピューターで実行されているすべてのアプリケーションで共有されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-124">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="f1bdd-125">`Custom`: <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> プロパティで指定されるカスタムの配信不能キューを使用して配信不能メッセージを保存します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-125">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="f1bdd-126">この機能は、Windows Vista でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-126">This feature is only available on Windows Vista.</span></span> <span data-ttu-id="f1bdd-127">同じコンピューターで実行されている他のアプリケーションとキューを共有するのではなく、そのアプリケーション専用の配信不能キューが必要な場合に、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-127">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="f1bdd-128"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> プロパティは、配信不能キューとして使用される特定のキューを表します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-128"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="f1bdd-129">これは、Windows Vista でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-129">This is available only in Windows Vista.</span></span>

 <span data-ttu-id="f1bdd-130">このサンプルでは、クライアントがトランザクションのスコープ内からメッセージをまとめてサービスに送信しますが、メッセージの "有効期間" には意図的に小さい値 (約 2 秒) を指定しています。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-130">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="f1bdd-131">さらに、有効期限切れのメッセージを入れるために使用するカスタムの配信不能キューを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-131">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="f1bdd-132">クライアント アプリケーションは、配信不能キューからメッセージを読み取った後で、そのメッセージの再送信を試みるか、元のメッセージが配信不能となった原因のエラーを解消してメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-132">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="f1bdd-133">このサンプルでは、クライアントはエラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-133">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="f1bdd-134">サービス コントラクトは `IOrderProcessor` です。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-134">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="f1bdd-135">このサンプルのサービスコードは、トランザクション処理された [MSMQ バインド](transacted-msmq-binding.md)のコードです。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-135">The service code in the sample is that of the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="f1bdd-136">サービスとの通信はトランザクションのスコープ内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-136">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="f1bdd-137">サービスはキューからメッセージを読み取って操作を実行し、操作の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-137">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="f1bdd-138">このアプリケーションでは、配信不能メッセージ用の配信不能キューも作成します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-138">The application also creates a dead-letter queue for dead-letter messages.</span></span>

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

        // Create the purchase order
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

        //Create a transaction scope.
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 <span data-ttu-id="f1bdd-139">クライアントの構成では、メッセージがサービスに到達するまでの時間が短く設定されています。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-139">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="f1bdd-140">指定された時間内にメッセージを送信できなかった場合は、メッセージが有効期限切れとなり、配信不能キューに移動します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-140">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bdd-141">クライアントがメッセージを指定時間内にサービス キューに配信できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-141">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="f1bdd-142">配信不能サービスが動作していることを確認するには、サービスを開始する前にクライアントを実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-142">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="f1bdd-143">メッセージはタイムアウトして、配信不能サービスに配信されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-143">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="f1bdd-144">アプリケーションでは、どのキューを配信不能キューとして使用するかを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-144">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="f1bdd-145">キューが指定されていない場合は、既定のシステム全体のトランザクション配信不能キューが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-145">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="f1bdd-146">この例のクライアント アプリケーションは、アプリケーション専用の配信不能キューを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-146">In this example, the client application specifies its own application dead-letter queue.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="f1bdd-147">配信不能メッセージ サービスは、メッセージを配信不能キューから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-147">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="f1bdd-148">この配信不能メッセージ サービスは、`IOrderProcessor` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-148">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="f1bdd-149">ただし、この実装は注文を処理するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-149">Its implementation however is not to process orders.</span></span> <span data-ttu-id="f1bdd-150">配信不能メッセージ サービスはクライアント サービスの 1 つで、注文処理機能は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-150">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bdd-151">配信不能キューはクライアント キューであり、クライアントのキュー マネージャに対してローカルです。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-151">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="f1bdd-152">配信不能メッセージ サービスの実装の中で、メッセージの配信に失敗した原因を調べて修正処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-152">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="f1bdd-153">メッセージ配信失敗の原因は、<xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> と <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A> の 2 つの列挙体に記録されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-153">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="f1bdd-154"><xref:System.ServiceModel.Channels.MsmqMessageProperty> は <xref:System.ServiceModel.OperationContext> から取得できます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-154">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 <span data-ttu-id="f1bdd-155">配信不能キューの中のメッセージは、メッセージを処理するサービス宛てのメッセージです。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-155">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="f1bdd-156">このため、配信不能メッセージサービスがキューからメッセージを読み取る場合、Windows Communication Foundation (WCF) チャネル層はエンドポイントで不一致を検出し、メッセージをディスパッチしません。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-156">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="f1bdd-157">この場合、メッセージの宛先は注文処理サービスですが、受信するのは配信不能メッセージ サービスです。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-157">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="f1bdd-158">別のエンドポイント宛てのメッセージを受信するには、どのアドレスにも一致するアドレス フィルタを `ServiceBehavior` で指定します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-158">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="f1bdd-159">これは、配信不能キューから読み取ったメッセージを正常に処理するために必要です。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-159">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="f1bdd-160">このサンプルでは、エラーの原因がメッセージのタイムアウトである場合に、配信不能メッセージサービスによってメッセージが再送信されます。その他のすべての理由により、次のサンプルコードに示すように、配信エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-160">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 <span data-ttu-id="f1bdd-161">配信不能メッセージ用の構成を次のサンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-161">The following sample shows the configuration for a dead-letter message:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="f1bdd-162">このサンプルを実行するときは、3 つの実行可能ファイル (クライアント、サービス、および各アプリケーションの配信不能キューを読み取ってメッセージをサービスに再送信する配信不能サービス) が実行され、各アプリケーションに対して配信不能キューがどのように機能するかがわかります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-162">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="f1bdd-163">これらはすべてコンソール アプリケーションで、コンソール ウィンドウに出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-163">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bdd-164">キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-164">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f1bdd-165">クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-165">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="f1bdd-166">キューが作成されるように、サービスを起動してシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-166">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="f1bdd-167">クライアントを実行すると、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-167">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="f1bdd-168">クライアントはメッセージの送信を試みますが、タイムアウトまでの時間が短いのでメッセージは期限切れとなり、メッセージが各アプリケーションの配信不能キューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-168">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="f1bdd-169">次に、配信不能サービスを実行すると、メッセージが読み取られてエラー コードが表示され、メッセージがサービスに再送信されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-169">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="f1bdd-170">サービスを起動すると、再送信されたメッセージが読み取られて処理されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-170">The service starts and then reads the resent message and processes it.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f1bdd-171">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="f1bdd-171">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f1bdd-172">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-172">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f1bdd-173">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-173">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f1bdd-174">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-174">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f1bdd-175">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-175">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f1bdd-176">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-176">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f1bdd-177">Visual Studio 2012 でサーバーマネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-177">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f1bdd-178">[ **機能** ] タブを展開します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-178">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f1bdd-179">[ **プライベートメッセージキュー**] を右クリックし、[ **新規**]、[ **プライベートキュー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-179">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f1bdd-180">[ **トランザクション** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-180">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f1bdd-181">`ServiceModelSamplesTransacted`新しいキューの名前として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-181">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f1bdd-182">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-182">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="f1bdd-183">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、キュー名を適切に変更し、localhost をコンピューターの完全な名前に置き換えて、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-183">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="f1bdd-184">ワークグループに参加しているコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="f1bdd-184">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="f1bdd-185">ドメインに属していないコンピューターを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードとセキュリティ レベルを `None` に設定します。サンプル構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-185">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="f1bdd-186">エンドポイントの `bindingConfiguration` 属性が設定されて、エンドポイントとバインディングとが関連付けられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-186">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="f1bdd-187">DeadLetterService、サーバー、およびクライアントの構成を変更したことを確認してから、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-187">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f1bdd-188">`security mode` を `None` に設定することは、`MsmqAuthenticationMode`、`MsmqProtectionLevel`、および `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-188">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="f1bdd-189">コメント</span><span class="sxs-lookup"><span data-stu-id="f1bdd-189">Comments</span></span>

 <span data-ttu-id="f1bdd-190">`netMsmqBinding` バインディング トランスポートを使用する場合の既定では、セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-190">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="f1bdd-191">トランスポート セキュリティの種類は、`MsmqAuthenticationMode` と `MsmqProtectionLevel` の 2 つのプロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-191">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="f1bdd-192">既定の設定では、認証モードは `Windows`、保護レベルは `Sign` です。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-192">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f1bdd-193">MSMQ の認証および署名の機能を利用するには、ドメインに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-193">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="f1bdd-194">ドメインに属していないコンピューターでこのサンプルを実行すると、"User's internal message queuing certificate does not exist" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-194">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1bdd-195">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-195">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f1bdd-196">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-196">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f1bdd-197">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-197">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1bdd-198">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f1bdd-198">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
