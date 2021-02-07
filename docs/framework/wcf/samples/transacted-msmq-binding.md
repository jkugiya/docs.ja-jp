---
description: 詳細については、「トランザクション MSMQ バインディング」を参照してください。
title: トランザクション MSMQ バインディング
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 17fdcdb169c9e57c1a95d5aea4c79654e3739664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668527"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="0fe06-103">トランザクション MSMQ バインディング</span><span class="sxs-lookup"><span data-stu-id="0fe06-103">Transacted MSMQ Binding</span></span>

<span data-ttu-id="0fe06-104">このサンプルでは、メッセージ キュー (MSMQ) を使用して、トランザクション キューによる通信を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-104">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="0fe06-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe06-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="0fe06-106">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="0fe06-107">厳密には、クライアントはメッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="0fe06-108">サービスは、メッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-108">The service receives messages from the queue.</span></span> <span data-ttu-id="0fe06-109">このため、キューを使用する通信では、サービスとクライアントは同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="0fe06-109">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="0fe06-110">メッセージの送受信にトランザクションが使用されている場合、実際には 2 つの別個のトランザクションが存在しています。</span><span class="sxs-lookup"><span data-stu-id="0fe06-110">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="0fe06-111">クライアントがトランザクションのスコープ内でメッセージを送信する場合、トランザクションはクライアントおよびクライアント キュー マネージャにとってローカルとなります。</span><span class="sxs-lookup"><span data-stu-id="0fe06-111">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="0fe06-112">サービスがトランザクションのスコープ内でメッセージを受信する場合、トランザクションはサービスおよび受信キュー マネージャにとってローカルとなります。</span><span class="sxs-lookup"><span data-stu-id="0fe06-112">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="0fe06-113">クライアントとサービスは同じトランザクションに参加していません。むしろ、キューに対して操作 (送信や受信など) を実行する場合は異なるトランザクションを使用するので、注意してください。</span><span class="sxs-lookup"><span data-stu-id="0fe06-113">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="0fe06-114">このサンプルでは、クライアントはトランザクションのスコープ内からメッセージのバッチをサービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-114">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="0fe06-115">キューに送信されたメッセージは、サービスによって定義されたトランザクション スコープ内のサービスによって受信されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-115">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="0fe06-116">サービス コントラクトは `IOrderProcessor` です。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe06-116">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="0fe06-117">インターフェイスは、キューでの使用に適した一方向サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-117">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="0fe06-118">サービス動作は、`TransactionScopeRequired` が `true` に設定された操作動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-118">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="0fe06-119">これにより、キューからのメッセージの取得に使用されるものと同じトランザクション スコープが、このメソッドによってアクセスされる任意のリソース マネージャにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-119">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="0fe06-120">さらに、メソッドから例外がスローされた場合にメッセージがキューに返されることも保証されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-120">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="0fe06-121">このサービス動作を設定しない場合、キューに置かれたチャネルはトランザクションを作成して、キューからのメッセージを読み取り、操作が失敗した場合には、ディスパッチによってメッセージが失われる前に、自動的にそのメッセージをコミットします。</span><span class="sxs-lookup"><span data-stu-id="0fe06-121">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="0fe06-122">最もよく見られるシナリオは、キューからのメッセージの読み込みに使用するトランザクションにサービス操作をリストすることです。次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe06-122">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

```csharp
 // This service class that implements the service contract.
 // This added code writes output to the console window.
 public class OrderProcessorService : IOrderProcessor
 {
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
     public void SubmitPurchaseOrder(PurchaseOrder po)
     {
         Orders.Add(po);
         Console.WriteLine("Processing {0} ", po);
     }
  …
}
```

<span data-ttu-id="0fe06-123">サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="0fe06-123">The service is self hosted.</span></span> <span data-ttu-id="0fe06-124">MSMQ トランスポートを使用する場合、使用するキューをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fe06-124">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="0fe06-125">手動で作成することもコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-125">This can be done manually or through code.</span></span> <span data-ttu-id="0fe06-126">このサンプルでは、キューの存在を確認して、存在しない場合は作成するためのコードがサービスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fe06-126">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="0fe06-127">キュー名は構成ファイルから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-127">The queue name is read from the configuration file.</span></span> <span data-ttu-id="0fe06-128">このベースアドレスは、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) によって、サービスへのプロキシを生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-128">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get the MSMQ queue name from appSettings in configuration.
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

        // Close the ServiceHost to shut down the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="0fe06-129">MSMQ キュー名は、構成ファイルの appSettings セクションに指定されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe06-129">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="0fe06-130"><xref:System.Messaging> を使用してキューを作成する場合、キュー名では、ローカル コンピューターを表すのにドット (.) を使用し、パスの区切りにはバックスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-130">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="0fe06-131">Windows Communication Foundation (WCF) エンドポイントは、キューアドレスを使用して、net.tcp スキームを使用し、ローカルコンピューターを示すために "localhost" を使用して、パスにスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-131">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="0fe06-132">クライアントはトランザクション スコープを作成します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-132">The client creates a transaction scope.</span></span> <span data-ttu-id="0fe06-133">キューとの通信はトランザクションのスコープ内で実行されるため、すべてのメッセージがキューに送信されるか、またはメッセージがキューにまったく送信されないかを示す、アトミック単位として扱われます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-133">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="0fe06-134">トランザクションは、トランザクション スコープで <xref:System.Transactions.TransactionScope.Complete%2A> を呼び出すことでコミットされます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-134">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

```csharp
// Create a client.
OrderProcessorClient client = new OrderProcessorClient();

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

// Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    // Make a queued call to submit the purchase order.
    client.SubmitPurchaseOrder(po);
    // Complete the transaction.
    scope.Complete();
}

// Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="0fe06-135">トランザクションが動作していることを確認するには、次のサンプル コードで示すようにトランザクション スコープをコメント化してクライアントを変更し、ソリューションを再ビルドしてクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-135">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="0fe06-136">トランザクションは完了していないので、メッセージはキューに送信されません。</span><span class="sxs-lookup"><span data-stu-id="0fe06-136">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="0fe06-137">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-137">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0fe06-138">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-138">You can see the service receive messages from the client.</span></span> <span data-ttu-id="0fe06-139">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-139">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="0fe06-140">キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0fe06-140">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="0fe06-141">クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-141">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0fe06-142">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="0fe06-142">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0fe06-143">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-143">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0fe06-144">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-144">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="0fe06-145">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-145">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="0fe06-146">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-146">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="0fe06-147">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0fe06-147">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="0fe06-148">Visual Studio 2012 でサーバーマネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-148">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="0fe06-149">[ **機能** ] タブを展開します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-149">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="0fe06-150">[ **プライベートメッセージキュー**] を右クリックし、[ **新規**]、[ **プライベートキュー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-150">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="0fe06-151">[ **トランザクション** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0fe06-151">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="0fe06-152">`ServiceModelSamplesTransacted`新しいキューの名前として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-152">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="0fe06-153">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0fe06-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="0fe06-154">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0fe06-154">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="0fe06-155"><xref:System.ServiceModel.NetMsmqBinding> を使用する場合の既定では、トランスポート セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="0fe06-155">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="0fe06-156">MSMQ トランスポート セキュリティには、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> および <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> という 2 つの関連プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="0fe06-156">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="0fe06-157">既定では、認証モードは `Windows` に、保護レベルは `Sign` に、それぞれ設定されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-157">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="0fe06-158">MSMQ で認証機能と署名機能を実現するには、MSMQ をドメインに含め、MSMQ の Active Directory 統合オプションをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fe06-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="0fe06-159">この条件を満たしていないコンピューターでこのサンプルを実行すると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="0fe06-159">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="0fe06-160">ワークグループに属しているコンピューターまたは Active Directory 統合のないコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="0fe06-160">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="0fe06-161">ドメインに属していないコンピューター、または Active Directory 統合がインストールされていないコンピューターを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを `None` にします。この構成コードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-161">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

    ```xml
    <system.serviceModel>
      <services>
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"
                 behaviorConfiguration="OrderProcessorServiceBehavior">
          <host>
            <baseAddresses>
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
            </baseAddresses>
          </host>
          <!-- Define NetMsmqEndpoint. -->
          <endpoint
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"
              binding="netMsmqBinding"
              bindingConfiguration="Binding1"
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
          <endpoint address="mex"
                    binding="mexHttpBinding"
                    contract="IMetadataExchange" />
        </service>
      </services>

      <bindings>
        <netMsmqBinding>
          <binding name="Binding1">
            <security mode="None" />
          </binding>
        </netMsmqBinding>
      </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="OrderProcessorServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="0fe06-162">サーバーとクライアントの両方の構成を変更したことを確認してから、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-162">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0fe06-163">`security mode` を `None` に設定することは、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>、および `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="0fe06-163">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fe06-164">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0fe06-164">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0fe06-165">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0fe06-165">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0fe06-166">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="0fe06-166">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0fe06-167">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0fe06-167">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
