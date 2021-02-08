---
description: 詳細については、「MSMQ 4.0 での有害メッセージの処理」を参照してください。
title: MSMQ 4.0 での有害メッセージ処理
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: fadbce9379b63f47f80c38551c1c71b81df5fee0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793169"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="2c2c7-103">MSMQ 4.0 での有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="2c2c7-103">Poison Message Handling in MSMQ 4.0</span></span>

<span data-ttu-id="2c2c7-104">このサンプルでは、サービスで有害メッセージの処理を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-104">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="2c2c7-105">このサンプルは、トランザクション処理された [MSMQ バインディング](transacted-msmq-binding.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-105">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="2c2c7-106">このサンプルでは、`netMsmqBinding` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-106">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="2c2c7-107">サービスは自己ホスト型コンソール アプリケーションであるので、キューに置かれたメッセージをサービスが受信するようすを観察できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-107">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="2c2c7-108">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="2c2c7-109">厳密には、クライアントはメッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-109">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="2c2c7-110">サービスは、メッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-110">The service receives messages from the queue.</span></span> <span data-ttu-id="2c2c7-111">したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-111">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="2c2c7-112">有害メッセージとは、メッセージを読み取るサービスがメッセージを処理できないためメッセージの読み取りが行われるトランザクションを終了する場合に、キューから繰り返し読み取られるメッセージのことです。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-112">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="2c2c7-113">そのような場合、メッセージは再試行されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-113">In such cases, the message is retried again.</span></span> <span data-ttu-id="2c2c7-114">メッセージに問題がある場合、この再試行は理論上、永久に継続します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-114">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="2c2c7-115">これは、トランザクションを使用してキューから読み取り、サービス操作を呼び出す場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-115">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="2c2c7-116">MSMQ のバージョンによって、NetMsmqBinding がサポートする有害メッセージの検出が制限されている場合と、制限されていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-116">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="2c2c7-117">メッセージが有害として検出されたら、いくつかの方法で処理できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-117">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="2c2c7-118">また、MSMQ のバージョンによって、NetMsmqBinding がサポートする有害メッセージの処理が制限されている場合と、制限されていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-118">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="2c2c7-119">このサンプルでは、windows Server 2003 および Windows XP プラットフォームに用意されている制限付きの有害機能、および Windows Vista で提供される完全な有害機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-119">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="2c2c7-120">どちらのサンプルでも、有害メッセージをキューから別のキューに移動することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-120">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="2c2c7-121">そのキューは、有害メッセージサービスによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-121">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="2c2c7-122">MSMQ v4.0 の有害メッセージ処理サンプル</span><span class="sxs-lookup"><span data-stu-id="2c2c7-122">MSMQ v4.0 Poison Handling Sample</span></span>

 <span data-ttu-id="2c2c7-123">Windows Vista では、有害メッセージの格納に使用できる有害なサブキュー機能が MSMQ に用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-123">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="2c2c7-124">このサンプルでは、Windows Vista を使用して有害なメッセージを処理するためのベストプラクティスを示します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-124">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="2c2c7-125">Windows Vista での有害メッセージの検出は洗練されています。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-125">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="2c2c7-126">検出に役立つ 3 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-126">There are 3 properties that help with detection.</span></span> <span data-ttu-id="2c2c7-127"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> は、指定したメッセージをキューから再度読み取り、処理するためにアプリケーションにディスパッチする回数です。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-127">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="2c2c7-128">メッセージをアプリケーションにディスパッチできないか、またはアプリケーションがサービス操作内のトランザクションをロールバックしたため、メッセージはキューに戻ったときにキューから再度読み取られます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-128">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="2c2c7-129"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> は、メッセージが再試行キューに移動する回数です。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-129"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="2c2c7-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> に達すると、メッセージは再試行キューに移動されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-130">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="2c2c7-131">メッセージが再試行キューからメイン キューに移動されると、<xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> プロパティは時間遅延となります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-131">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="2c2c7-132"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> が 0 にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-132">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="2c2c7-133">メッセージは再試行されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-133">The message is tried again.</span></span> <span data-ttu-id="2c2c7-134">メッセージを読み取るすべての試行に失敗すると、メッセージが有害としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-134">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="2c2c7-135">メッセージが有害としてマークされると、メッセージは <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> 列挙体の設定に従って処理されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-135">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="2c2c7-136">次にもう一度、使用可能な値を示します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-136">To reiterate the possible values:</span></span>

- <span data-ttu-id="2c2c7-137">Fault (既定値): リスナーとサービス ホストをエラーにします。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-137">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="2c2c7-138">Drop: メッセージを破棄します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-138">Drop: To drop the message.</span></span>

- <span data-ttu-id="2c2c7-139">移動: メッセージを有害メッセージサブキューに移動します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-139">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="2c2c7-140">この値は、Windows Vista でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-140">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="2c2c7-141">Reject: メッセージを送信者の配信不能キューに戻すことにより、メッセージを拒否します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-141">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="2c2c7-142">この値は、Windows Vista でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-142">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="2c2c7-143">このサンプルは有害なメッセージに対する `Move` 処置の使用法を示します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-143">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="2c2c7-144">`Move` メッセージを有害サブキューに移動させます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-144">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="2c2c7-145">サービス コントラクトは `IOrderProcessor` です。これは、キューでの使用に適した一方向サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-145">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="2c2c7-146">サービス操作により、注文を処理していることを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-146">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="2c2c7-147">有害なメッセージ機能を示すために、サービス操作は例外をスローして、 `SubmitPurchaseOrder` サービスのランダム呼び出しでトランザクションをロールバックします。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-147">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="2c2c7-148">これにより、メッセージがキューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-148">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="2c2c7-149">最終的に、メッセージは有害とマークされます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-149">Eventually the message is marked as poison.</span></span> <span data-ttu-id="2c2c7-150">この構成は、有害メッセージを有害サブキューに移動するように設定されています。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-150">The configuration is set to move the poison message to the poison subqueue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="2c2c7-151">サービス構成には、`receiveRetryCount`、`maxRetryCycles`、`retryCycleDelay`、および `receiveErrorHandling` という有害メッセージ プロパティが含まれています。次の構成ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-151">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="2c2c7-152">有害メッセージ キューのメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="2c2c7-152">Processing messages from the poison message queue</span></span>

 <span data-ttu-id="2c2c7-153">有害メッセージ サービスは、最終的な有害メッセージ キューからメッセージを読み取って、それを処理します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-153">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="2c2c7-154">有害メッセージ キューのメッセージは、メッセージを処理するサービスに対応付けられたメッセージで、有害メッセージ サービスのエンドポイントとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-154">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="2c2c7-155">したがって、有害メッセージサービスがキューからメッセージを読み取る場合、WCF チャネル層はエンドポイントで不一致を検出し、メッセージをディスパッチしません。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-155">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="2c2c7-156">この場合、メッセージは注文処理サービス宛てになりますが、有害メッセージ サービスが受信します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-156">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="2c2c7-157">別のエンドポイント宛のメッセージも含めてメッセージの受信を続けるには、`ServiceBehavior` を追加して、メッセージの任意の宛先サービス エンドポイントを一致条件としてアドレスをフィルタする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-157">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="2c2c7-158">これは、有害メッセージ キューから読み込んだメッセージを正常に処理するために必要です。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-158">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="2c2c7-159">有害メッセージ サービス実装そのものは、サービス実装と非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-159">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="2c2c7-160">コントラクトを実装し、注文を処理します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-160">It implements the contract and processes the orders.</span></span> <span data-ttu-id="2c2c7-161">コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-161">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="2c2c7-162">注文キューからメッセージを読み取る注文処理サービスとは異なり、有害メッセージサービスは有害サブキューからメッセージを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-162">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="2c2c7-163">有害キューはメインキューのサブキューであり、"有害" という名前で、MSMQ によって自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-163">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="2c2c7-164">このファイルにアクセスするには、次のサンプル構成に示すように、メインキュー名の後に ";" とサブキュー名 (この例では "有害") を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-164">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="2c2c7-165">MSMQ v3.0 用のサンプルでは、有害キュー名はサブキューではなく、メッセージの移動先キューになります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-165">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="2c2c7-166">サンプルを実行すると、クライアント、サービス、および有害メッセージ サービスのアクティビティがコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-166">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="2c2c7-167">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-167">You can see the service receive messages from the client.</span></span> <span data-ttu-id="2c2c7-168">いずれかのコンソール ウィンドウで Enter キーを押すと、サービスがシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-168">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="2c2c7-169">サービスが実行を開始し、注文を処理し、処理の終了をランダムに開始します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-169">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="2c2c7-170">メッセージに注文処理の完了が示されていた場合、クライアントをもう一度実行して、サービスが実際にメッセージを終了したことを確認するまで別のメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-170">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="2c2c7-171">構成されている有害設定に基づき、メッセージは 1 度処理を試行されてから、最後の有害キューに移されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-171">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="2c2c7-172">有害メッセージ サービスを起動して、有害メッセージを有害キューから読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-172">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="2c2c7-173">この例では、有害メッセージ サービスはメッセージを読み込んで処理します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-173">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="2c2c7-174">終了され有害指定された発注書が有害メッセージ サービスによって読み込まれるのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-174">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2c2c7-175">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="2c2c7-175">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2c2c7-176">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2c2c7-177">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-177">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="2c2c7-178">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-178">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="2c2c7-179">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-179">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="2c2c7-180">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-180">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="2c2c7-181">Visual Studio 2012 でサーバーマネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-181">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="2c2c7-182">[ **機能** ] タブを展開します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-182">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="2c2c7-183">[ **プライベートメッセージキュー**] を右クリックし、[ **新規**]、[ **プライベートキュー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-183">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="2c2c7-184">[ **トランザクション** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-184">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="2c2c7-185">`ServiceModelSamplesTransacted`新しいキューの名前として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-185">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="2c2c7-186">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-186">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="2c2c7-187">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、キュー名を変更し、localhost ではなく実際のホスト名を反映させ、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-187">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

 <span data-ttu-id="2c2c7-188">`netMsmqBinding` バインディング トランスポートを使用する場合の既定では、セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-188">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="2c2c7-189">トランスポート セキュリティの種類は、`MsmqAuthenticationMode` と `MsmqProtectionLevel` の 2 つのプロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-189">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="2c2c7-190">既定では、認証モードは `Windows` に、保護レベルは `Sign` に、それぞれ設定されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-190">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="2c2c7-191">MSMQ の認証および署名の機能を利用するには、ドメインに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-191">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="2c2c7-192">ドメインに属していないコンピューターでこのサンプルを実行すると、"User's internal message queuing certificate does not exist" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-192">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="2c2c7-193">ワークグループに参加しているコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="2c2c7-193">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="2c2c7-194">ドメインに属していないコンピューターを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードとセキュリティ レベルを `None` に設定します。サンプル構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-194">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="2c2c7-195">エンドポイントの bindingConfiguration 属性を設定して、エンドポイントがこのバインディングに関連付けられるようにします。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-195">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="2c2c7-196">サンプルを実行する前に、PoisonMessageServer、サーバー、およびクライアントで構成が変更されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-196">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2c2c7-197">`security mode` を `None` に設定することは、`MsmqAuthenticationMode`、`MsmqProtectionLevel`、および `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-197">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="2c2c7-198">Metadata Exchange を機能させるため、URL を HTTP バインディングに登録します。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-198">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="2c2c7-199">これを行うには、サービスが権限の高いコマンド ウィンドウで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-199">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="2c2c7-200">それ以外の場合は、などの例外が発生し `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied` ます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-200">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2c2c7-201">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-201">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2c2c7-202">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2c2c7-203">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c2c7-204">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c7-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
