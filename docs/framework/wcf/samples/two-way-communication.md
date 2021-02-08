---
description: 詳細については、「Two-Way 通信」を参照してください。
title: 双方向通信
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 8e7f87c6ecd672d270a673a8e933e3c9ed4b5c00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798252"
---
# <a name="two-way-communication"></a><span data-ttu-id="3a2f5-103">双方向通信</span><span class="sxs-lookup"><span data-stu-id="3a2f5-103">Two-Way Communication</span></span>

<span data-ttu-id="3a2f5-104">このサンプルでは、双方向のトランザクション化キューを MSMQ を介して実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-104">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="3a2f5-105">このサンプルでは、`netMsmqBinding` バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="3a2f5-106">このサンプルのサービスは自己ホスト型コンソール アプリケーションであるので、サンプルを実行すると、キューに置かれたメッセージをサービスが受信するようすを観察できます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-106">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a2f5-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3a2f5-108">このサンプルは、トランザクション処理された [MSMQ バインディング](transacted-msmq-binding.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-108">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="3a2f5-109">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-109">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="3a2f5-110">クライアントはメッセージをキューに送信し、サービスはメッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-110">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="3a2f5-111">したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-111">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="3a2f5-112">このサンプルでは、キューを使用する双方向通信の例を示します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-112">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="3a2f5-113">クライアントは、トランザクションのスコープ内から発注書をキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-113">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="3a2f5-114">サービスは、注文を受信して処理し、注文ステータスをキューからクライアントに返信します。これらの処理を、トランザクションのスコープ内で実行します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-114">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="3a2f5-115">双方向通信を使用するには、クライアントとサービスの両方がキューを使用して、発注書や注文ステータスをキューに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-115">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="3a2f5-116">サービス コントラクト `IOrderProcessor` は、キューの使用に合わせた一方向サービス操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-116">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="3a2f5-117">サービス操作には、注文ステータスの送信に使用される応答エンドポイントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-117">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="3a2f5-118">応答エンドポイントは、注文ステータスをクライアントに返信するためのキューの URI です。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-118">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="3a2f5-119">注文処理アプリケーションは、このコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-119">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="3a2f5-120">注文ステータスを送信する応答コントラクトは、クライアントが指定します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-120">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="3a2f5-121">クライアントは注文ステータス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-121">The client implements the order status contract.</span></span> <span data-ttu-id="3a2f5-122">サービスは、このコントラクトについて生成されたプロキシを使用して、注文ステータスをクライアントに返信します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-122">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="3a2f5-123">サービス操作は、送信された発注書を処理します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-123">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="3a2f5-124">サービス操作に適用される <xref:System.ServiceModel.OperationBehaviorAttribute> では、キューからのメッセージ受信に使用されるトランザクションに自動的に帰属することと、サービス操作の完了時にトランザクションを自動的に完了させることが指定されています。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-124">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="3a2f5-125">`Orders` クラスは、注文処理機能をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-125">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="3a2f5-126">この例では、発注書をディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-126">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="3a2f5-127">このサービス操作が帰属するしているトランザクションは、`Orders` クラス内の操作で使用できます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-127">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="3a2f5-128">サービス操作は、送信された発注書を処理するだけでなく、注文ステータスをクライアントに戻します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-128">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 <span data-ttu-id="3a2f5-129">MSMQ キュー名は、構成ファイルの appSettings セクションで指定されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-129">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="3a2f5-130">サービスのエンドポイントは、構成ファイルの System.ServiceModel セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-130">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a2f5-131">MSMQ のキュー名とエンドポイント アドレスでは、若干異なるアドレス表記が使用されています。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-131">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="3a2f5-132">MSMQ のキュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-132">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="3a2f5-133">Windows Communication Foundation (WCF) エンドポイントアドレスは、net.tcp: scheme を指定し、ローカルコンピューターに "localhost" を使用して、パスにスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-133">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="3a2f5-134">リモート コンピューターでホストされているキューからの読み出しを行うには、"." や "localhost" をリモート コンピューター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-134">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="3a2f5-135">サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-135">The service is self hosted.</span></span> <span data-ttu-id="3a2f5-136">MSMQ トランスポートを使用する場合、使用するキューをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-136">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="3a2f5-137">手動で作成することもコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-137">This can be done manually or through code.</span></span> <span data-ttu-id="3a2f5-138">このサンプルでは、サービスがキューの存在を確認し、必要な場合はキューを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-138">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="3a2f5-139">キュー名は構成ファイルから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-139">The queue name is read from the configuration file.</span></span> <span data-ttu-id="3a2f5-140">このベースアドレスは、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) によって、サービスへのプロキシを生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-140">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```

 <span data-ttu-id="3a2f5-141">クライアントはトランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-141">The client creates a transaction.</span></span> <span data-ttu-id="3a2f5-142">キューとの通信はトランザクションのスコープ内で実行されるので、全体が 1 つのアトミックな単位として扱われ、すべてのメッセージが成功するか、すべてのメッセージが失敗するかのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-142">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="3a2f5-143">クライアント コードは `IOrderStatus` コントラクトを実装して、サービスからの注文ステータスを受信します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-143">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="3a2f5-144">この場合は、注文ステータスを出力します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-144">In this case, it prints out the order status.</span></span>  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 <span data-ttu-id="3a2f5-145">注文ステータス キューは `Main` メソッド内で作成します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-145">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="3a2f5-146">クライアント構成には、注文ステータス サービスをホストするための注文ステータス サービス構成が含まれています。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-146">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="3a2f5-147">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-147">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3a2f5-148">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-148">You can see the service receive messages from the client.</span></span> <span data-ttu-id="3a2f5-149">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-149">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="3a2f5-150">サービスによって発注書の情報が表示され、注文ステータスがサービスから注文ステータス キューに返信されることも表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-150">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 <span data-ttu-id="3a2f5-151">クライアントには、サービスから送信された注文ステータス情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-151">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a2f5-152">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3a2f5-152">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a2f5-153">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-153">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3a2f5-154">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-154">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3a2f5-155">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-155">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3a2f5-156">Svcutil.exe を使用してこのサンプルの構成を再生成した場合は、クライアント コードに一致するように、クライアント構成内のエンドポイント名を変更してください。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-156">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="3a2f5-157"><xref:System.ServiceModel.NetMsmqBinding> を使用する場合の既定では、トランスポート セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-157">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="3a2f5-158">MSMQ トランスポートセキュリティには、2つの関連するプロパティがあり <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ます。既定では、認証モードがに設定され、 `Windows` 保護レベルがに設定されてい `Sign` ます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-158">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="3a2f5-159">MSMQ の認証機能と署名機能を利用するには、ドメインに MSMQ があることと、MSMQ に関する Active Directory の統合オプションがインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-159">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="3a2f5-160">この条件を満たしていないコンピューターでこのサンプルを実行すると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-160">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="3a2f5-161">ワークグループに属しているコンピューターまたは Active Directory 統合のないコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="3a2f5-161">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="3a2f5-162">ドメインに属していないコンピュータ、または Active Directory 統合がインストールされていないコンピュータを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを `None` にします。この構成の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-162">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. <span data-ttu-id="3a2f5-163">クライアント構成のセキュリティをオフにすると、次のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-163">Turning off security for a client configuration generates the following:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. <span data-ttu-id="3a2f5-164">このサンプルのサービスは、`OrderProcessorService` でバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-164">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="3a2f5-165">このバインディングをインスタンス化した後に、コード行を 1 行追加して、セキュリティ モードを `None` に設定します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-165">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="3a2f5-166">サーバーとクライアントの両方の構成を変更したことを確認してから、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-166">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3a2f5-167">`security mode` を `None` に設定することは、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>、または `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-167">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a2f5-168">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-168">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a2f5-169">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-169">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a2f5-170">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-170">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a2f5-171">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3a2f5-171">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
