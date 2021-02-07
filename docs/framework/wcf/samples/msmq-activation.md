---
description: MSMQ のアクティブ化に関する詳細情報
title: MSMQ アクティベーション
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 3360ae560cba9c3b42551617beb295154668814b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752232"
---
# <a name="msmq-activation"></a><span data-ttu-id="4077e-103">MSMQ アクティベーション</span><span class="sxs-lookup"><span data-stu-id="4077e-103">MSMQ Activation</span></span>

<span data-ttu-id="4077e-104">このサンプルでは、メッセージ キューから読み取ったアプリケーションを、Windows プロセス アクティブ化サービス (WAS) でホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4077e-104">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="4077e-105">このサンプルでは、を使用し、 `netMsmqBinding` [双方向の通信](two-way-communication.md) サンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="4077e-105">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](two-way-communication.md) sample.</span></span> <span data-ttu-id="4077e-106">この場合、サービスは Web ホスト アプリケーションの 1 つであり、クライアントは自己ホスト型です。クライアントはコンソールに出力して、送信された発注書のステータスを確認します。</span><span class="sxs-lookup"><span data-stu-id="4077e-106">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>

> [!NOTE]
> <span data-ttu-id="4077e-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4077e-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="4077e-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4077e-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4077e-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4077e-109">Check for the following (default) directory before continuing.</span></span>
>
> <span data-ttu-id="4077e-110">\<InstallDrive>: \ WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="4077e-110">\<InstallDrive>:\WF_WCF_Samples</span></span>
>
> <span data-ttu-id="4077e-111">このディレクトリが存在しない場合は、 [.NET Framework 4 の Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプル](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WCF とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="4077e-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4077e-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-112">This sample is located in the following directory.</span></span>
>
> <span data-ttu-id="4077e-113">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="4077e-113">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>

<span data-ttu-id="4077e-114">Windows プロセスアクティブ化サービス (WAS) は、Windows Server 2008 用の新しいプロセスアクティブ化機構であり、以前は HTTP ベースのアプリケーションのみが http 以外のプロトコルを使用するアプリケーションに対して使用できるようになった IIS に似た機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="4077e-114">Windows Process Activation Service (WAS), the new process activation mechanism for Windows Server 2008, provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="4077e-115">Windows Communication Foundation (WCF) は、リスナーアダプターインターフェイスを使用して、WCF でサポートされている HTTP 以外のプロトコル (TCP、名前付きパイプ、MSMQ など) を介して受信されるアクティブ化要求を伝達します。</span><span class="sxs-lookup"><span data-stu-id="4077e-115">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="4077e-116">HTTP 以外のプロトコルを介して要求を受信する機能は、SMSvcHost.exe で実行されるマネージド Windows サービスによってホストされます。</span><span class="sxs-lookup"><span data-stu-id="4077e-116">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>

<span data-ttu-id="4077e-117">Net.Msmq リスナ アダプタ サービス (NetMsmqActivator) は、キュー内のメッセージに基づいてキューに置かれたアプリケーションをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="4077e-117">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>

<span data-ttu-id="4077e-118">クライアントはトランザクションのスコープ内から発注書をサービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="4077e-118">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="4077e-119">サービスはトランザクション内で注文を受信して、処理します。</span><span class="sxs-lookup"><span data-stu-id="4077e-119">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="4077e-120">その後、サービスは注文ステータスをクライアントに返信します。</span><span class="sxs-lookup"><span data-stu-id="4077e-120">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="4077e-121">双方向通信を使用するには、クライアントとサービスの両方がキューを使用して、発注書や注文ステータスをキューに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4077e-121">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>

<span data-ttu-id="4077e-122">`IOrderProcessor` サービス コントラクトは、キューを使用する一方向サービス操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="4077e-122">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="4077e-123">サービス操作は、注文ステータスをクライアントに送信するために応答エンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4077e-123">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="4077e-124">応答エンドポイントのアドレスは、注文ステータスをクライアントに返信する際に使用されるキューの URI です。</span><span class="sxs-lookup"><span data-stu-id="4077e-124">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="4077e-125">注文処理アプリケーションは、このコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="4077e-125">The order processing application implements this contract.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

<span data-ttu-id="4077e-126">注文ステータスを送信する応答コントラクトは、クライアントが指定します。</span><span class="sxs-lookup"><span data-stu-id="4077e-126">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="4077e-127">クライアントは注文ステータス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="4077e-127">The client implements the order status contract.</span></span> <span data-ttu-id="4077e-128">サービスは、このコントラクトについて生成されたクライアントを使用して、注文ステータスをクライアントに返信します。</span><span class="sxs-lookup"><span data-stu-id="4077e-128">The service uses the generated client of this contract to send order status back to the client.</span></span>

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

<span data-ttu-id="4077e-129">サービス操作は、送信された発注書を処理します。</span><span class="sxs-lookup"><span data-stu-id="4077e-129">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="4077e-130"><xref:System.ServiceModel.OperationBehaviorAttribute> はサービス操作に適用され、キューからのメッセージの受信に使用されるトランザクション内で登録リストを自動で作成し、サービス操作が完了したときにトランザクションを自動で完了するように指定します。</span><span class="sxs-lookup"><span data-stu-id="4077e-130">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="4077e-131">`Orders` クラスは、注文処理機能をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="4077e-131">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="4077e-132">この例では、発注書をディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="4077e-132">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="4077e-133">このサービス操作が帰属するしているトランザクションは、`Orders` クラス内の操作で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4077e-133">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>

<span data-ttu-id="4077e-134">サービス操作は、送信された発注書を処理するだけでなく、注文ステータスをクライアントに戻します。</span><span class="sxs-lookup"><span data-stu-id="4077e-134">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>

```csharp
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
        Console.WriteLine("Sending back order status information");
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));
        // please note that the same transaction that is used to dequeue purchase order is used
        // to send back order status
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.OrderStatus(po.PONumber, po.Status);
            scope.Complete();
        }
    }
}
```

<span data-ttu-id="4077e-135">使用するクライアント バインディングの指定には、構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="4077e-135">The client binding to use is specified using a configuration file.</span></span>

<span data-ttu-id="4077e-136">MSMQ キュー名は、構成ファイルの appSettings セクションで指定されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-136">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="4077e-137">サービスのエンドポイントは、構成ファイルの System.serviceModel セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-137">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="4077e-138">MSMQ のキュー名とエンドポイント アドレスでは、若干異なるアドレス表記が使用されています。</span><span class="sxs-lookup"><span data-stu-id="4077e-138">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="4077e-139">MSMQ のキュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="4077e-139">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="4077e-140">WCF エンドポイントアドレスは、net.tcp: scheme を指定し、ローカルコンピューターに "localhost" を使用して、パスにスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="4077e-140">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="4077e-141">リモート コンピューターでホストされているキューからの読み出しを行うには、"." や "localhost" をリモート コンピューター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4077e-141">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>

<span data-ttu-id="4077e-142">クラスの名前が付いた .svc ファイルは、WAS でのサービス コードのホストに使用されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-142">A .svc file with the name of the class is used to host the service code in WAS.</span></span>

<span data-ttu-id="4077e-143">Service.svc ファイル自体には、`OrderProcessorService` を作成するディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4077e-143">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

<span data-ttu-id="4077e-144">さらに、Service.svc ファイルには、System.Transactions.dll を読み込むためのアセンブリ ディレクティブも含まれます。</span><span class="sxs-lookup"><span data-stu-id="4077e-144">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

<span data-ttu-id="4077e-145">クライアントはトランザクション スコープを作成します。</span><span class="sxs-lookup"><span data-stu-id="4077e-145">The client creates a transaction scope.</span></span> <span data-ttu-id="4077e-146">サービスとの通信はトランザクションのスコープ内で実行され、すべてのメッセージが成功か失敗かを示すアトミックな単位として扱われます。</span><span class="sxs-lookup"><span data-stu-id="4077e-146">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="4077e-147">トランザクションは、トランザクション スコープで `Complete` を呼び出すことでコミットされます。</span><span class="sxs-lookup"><span data-stu-id="4077e-147">The transaction is committed by calling `Complete` on the transaction scope.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))
{
    // Open the ServiceHostBase to create listeners and start listening
    // for order status messages.
    serviceHost.Open();

    // Create a proxy with given client endpoint configuration
    OrderProcessorClient client = new OrderProcessorClient();

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
    using (TransactionScope scope = new
        TransactionScope(TransactionScopeOption.Required))
    {
        // Make a queued call to submit the purchase order
        client.SubmitPurchaseOrder(po,
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");
        // Complete the transaction.
        scope.Complete();
    }

    //Closing the client gracefully closes the connection and cleans up
    //resources
    client.Close();

    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();

    // Close the ServiceHostBase to shutdown the service.
    serviceHost.Close();
    }
```

<span data-ttu-id="4077e-148">クライアント コードは `IOrderStatus` コントラクトを実装して、サービスからの注文ステータスを受信します。</span><span class="sxs-lookup"><span data-stu-id="4077e-148">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="4077e-149">この場合は、注文ステータスを出力します。</span><span class="sxs-lookup"><span data-stu-id="4077e-149">In this case, it prints out the order status.</span></span>

```csharp
[ServiceBehavior]
public class OrderStatusService : IOrderStatus
{
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]
    public void OrderStatus(string poNumber, string status)
    {
        Console.WriteLine("Status of order {0}:{1} ",
                                         poNumber , status);
    }
}
```

<span data-ttu-id="4077e-150">注文ステータス キューは `Main` メソッド内で作成します。</span><span class="sxs-lookup"><span data-stu-id="4077e-150">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="4077e-151">クライアント構成には、注文ステータス サービスをホストするための注文ステータス サービス構成が含まれています。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4077e-151">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <!-- use appSetting to configure MSMQ queue name -->
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />
  </appSettings>

<system.serviceModel>

    <services>
      <service
         name="Microsoft.ServiceModel.Samples.OrderStatusService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
    </client>

  </system.serviceModel>
```

<span data-ttu-id="4077e-152">サンプルを実行すると、クライアントとサービスのアクティビティがサーバーとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-152">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="4077e-153">サーバーがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="4077e-153">You can see the server receive messages from the client.</span></span> <span data-ttu-id="4077e-154">どちらかのコンソールで Enter キーを押すと、サーバーとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="4077e-154">Press ENTER in each console window to shut down the server and client.</span></span>

<span data-ttu-id="4077e-155">クライアントには、サーバーから送信された注文ステータス情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-155">The client displays the order status information sent by the server:</span></span>

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4077e-156">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="4077e-156">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4077e-157">WAS のアクティブ化に必要な IIS 7.0 がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4077e-157">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>

2. <span data-ttu-id="4077e-158">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4077e-158">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="4077e-159">さらに、WCF 非 HTTP アクティブ化コンポーネントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4077e-159">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="4077e-160">**[スタート]** メニューの **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4077e-160">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="4077e-161">[ **プログラムと機能**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4077e-161">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="4077e-162">[ **Windows の機能の有効化または無効化] を** クリックします。</span><span class="sxs-lookup"><span data-stu-id="4077e-162">Click **Turn Windows Features on or off**.</span></span>

    4. <span data-ttu-id="4077e-163">[ **機能の概要**] で、[ **機能の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4077e-163">Under **Features Summary**, click **Add Features**.</span></span>

    5. <span data-ttu-id="4077e-164">[ **Microsoft .NET Framework 3.0** ] ノードを展開し、[ **WINDOWS COMMUNICATION FOUNDATION の非 HTTP アクティブ化** ] 機能をオンにします。</span><span class="sxs-lookup"><span data-stu-id="4077e-164">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="4077e-165">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4077e-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="4077e-166">コマンド ウィンドウで client.exe を実行することにより、クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4077e-166">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="4077e-167">これによってキューが作成され、メッセージがそのキューに送信されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-167">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="4077e-168">クライアントを実行しながら、メッセージを読み取るサービスの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="4077e-168">Leave the client running to see the result of the service reading the message</span></span>

5. <span data-ttu-id="4077e-169">MSMQ アクティベーション サービスは、既定では NETWORK SERVICE として動作します。</span><span class="sxs-lookup"><span data-stu-id="4077e-169">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="4077e-170">そのため、アプリケーションのアクティブ化に使用されるキューには、NETWORK SERVICE アカウントによる受信およびピーク権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4077e-170">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="4077e-171">この権限は、メッセージ キュー MMC を使用して追加できます。</span><span class="sxs-lookup"><span data-stu-id="4077e-171">This can be added by using the Message Queuing MMC:</span></span>

    1. <span data-ttu-id="4077e-172">[ **スタート** ] メニューの [ **実行**] をクリックし、「」と入力して、 `Compmgmt.msc` enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4077e-172">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>

    2. <span data-ttu-id="4077e-173">[ **サービスとアプリケーション**] で、[ **メッセージキュー**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="4077e-173">Under **Services and Applications**, expand **Message Queuing**.</span></span>

    3. <span data-ttu-id="4077e-174">[ **専用キュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4077e-174">Click **Private Queues**.</span></span>

    4. <span data-ttu-id="4077e-175">キュー (servicemodelsamples/Service .svc) を右クリックし、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4077e-175">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>

    5. <span data-ttu-id="4077e-176">[ **セキュリティ** ] タブで [ **追加** ] をクリックし、ネットワークサービスに対して [ピーク] および [受信] アクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="4077e-176">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>

6. <span data-ttu-id="4077e-177">MSMQ アクティブ化をサポートするよう Windows プロセス アクティブ化サービス (WAS) を設定します。</span><span class="sxs-lookup"><span data-stu-id="4077e-177">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>

    <span data-ttu-id="4077e-178">便宜上次の 2 つの手順が、サンプル ディレクトリにある AddMsmqSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="4077e-178">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="4077e-179">net.msmq アクティベーションをサポートするには、既定の Web サイトをあらかじめ net.msmq プロトコルにバインドしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4077e-179">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="4077e-180">これは、IIS7.0 管理ツール セットと共にインストールされる appcmd.exe を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="4077e-180">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="4077e-181">権限のレベルが高い (管理者の) コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4077e-181">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="4077e-182">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="4077e-182">This command is a single line of text.</span></span>

        <span data-ttu-id="4077e-183">このコマンドによって、既定の Web サイトに net.msmq サイト バインディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="4077e-183">This command adds a net.msmq site binding to the default Web site.</span></span>

    2. <span data-ttu-id="4077e-184">サイト内のすべてのアプリケーションが同じ net.msmq バインディングを共有しますが、net.msmq サポートの有効化はアプリケーションごとに指定できます。</span><span class="sxs-lookup"><span data-stu-id="4077e-184">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="4077e-185">/servicemodelsamples アプリケーションで net.msmq を有効にするには、権限のレベルが高いコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4077e-185">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > <span data-ttu-id="4077e-186">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="4077e-186">This command is a single line of text.</span></span>

        <span data-ttu-id="4077e-187">このコマンドは、およびを使用して/servicemodelsamples アプリケーションにアクセスできるようにし `http://localhost/servicemodelsamples` `net.msmq://localhost/servicemodelsamples` ます。</span><span class="sxs-lookup"><span data-stu-id="4077e-187">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>

7. <span data-ttu-id="4077e-188">まだ確認していない場合は、MSMQ アクティベーション サービスが有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4077e-188">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="4077e-189">[ **スタート** ] メニューの [ **実行**] をクリックし、「」と入力し `Services.msc` ます。</span><span class="sxs-lookup"><span data-stu-id="4077e-189">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="4077e-190">サービスの一覧で、 **Net.tcp リスナーアダプター** を検索します。</span><span class="sxs-lookup"><span data-stu-id="4077e-190">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="4077e-191">右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4077e-191">Right-click and select **Properties**.</span></span> <span data-ttu-id="4077e-192">[ **スタートアップの種類** ] を [ **自動**] に設定し、[ **適用** ] をクリックして、[ **開始** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4077e-192">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="4077e-193">この手順は、Net.Msmq リスナー アダプター サービスを初めて使用する前に 1 回だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4077e-193">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>

8. <span data-ttu-id="4077e-194">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4077e-194">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="4077e-195">さらに、発注書を送信するときのキューの URI 内のコンピューター名を反映するように、発注書を送信するクライアントのコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="4077e-195">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="4077e-196">次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="4077e-196">Use the following code:</span></span>

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. <span data-ttu-id="4077e-197">このサンプル用に追加した net.msmq サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="4077e-197">Remove the net.msmq site binding you added for this sample.</span></span>

    <span data-ttu-id="4077e-198">便宜上次の 2 つの手順が、サンプル ディレクトリにある RemoveMsmqSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="4077e-198">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="4077e-199">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、有効なプロトコルの一覧から net.msmq を削除します。</span><span class="sxs-lookup"><span data-stu-id="4077e-199">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="4077e-200">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="4077e-200">This command is a single line of text.</span></span>

    2. <span data-ttu-id="4077e-201">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、net.msmq サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="4077e-201">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="4077e-202">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="4077e-202">This command is a single line of text.</span></span>

    > [!WARNING]
    > <span data-ttu-id="4077e-203">バッチ ファイルを実行すると、DefaultAppPool がリセットされて .NET Framework Version 2.0 で実行されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-203">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>

<span data-ttu-id="4077e-204">`netMsmqBinding` バインディング トランスポートを使用する場合の既定では、セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="4077e-204">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="4077e-205">トランスポート セキュリティの種類は、`MsmqAuthenticationMode` と `MsmqProtectionLevel` の 2 つのプロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="4077e-205">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="4077e-206">既定の設定では、認証モードは `Windows`、保護レベルは `Sign` です。</span><span class="sxs-lookup"><span data-stu-id="4077e-206">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="4077e-207">MSMQ の認証および署名の機能を利用するには、ドメインに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="4077e-207">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="4077e-208">このサンプルをドメインに属していないコンピューターで実行すると、"ユーザーの内部メッセージ キュー認証情報は存在しません" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4077e-208">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="4077e-209">ワークグループに参加しているコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="4077e-209">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="4077e-210">ドメインに属していないコンピューターを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを "none" に設定します。サンプル構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4077e-210">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. <span data-ttu-id="4077e-211">サンプルを実行する前に、サーバーとクライアントの両方の構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="4077e-211">Change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4077e-212">`security mode` を `None` に設定することは、`MsmqAuthenticationMode`、`MsmqProtectionLevel`、および `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="4077e-212">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

3. <span data-ttu-id="4077e-213">ワークグループに参加しているコンピューターでアクティブ化を有効にするには、アクティベーション サービスとワーカー プロセスの両方を特定のユーザー アカウントで実行する必要があります (どちらも同じアカウントを使用する必要があります)。さらに、キューはその特定のユーザー アカウントの ACL に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4077e-213">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>

     <span data-ttu-id="4077e-214">ワーカー プロセスが実行される ID を変更するには</span><span class="sxs-lookup"><span data-stu-id="4077e-214">To change the identity that the worker process runs under:</span></span>

    1. <span data-ttu-id="4077e-215">Inetmgr.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="4077e-215">Run Inetmgr.exe.</span></span>

    2. <span data-ttu-id="4077e-216">[ **アプリケーションプール**] で、 **AppPool** (通常は **DefaultAppPool**) を右クリックし、[ **アプリケーションプールの既定値の設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4077e-216">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>

    3. <span data-ttu-id="4077e-217">特定のユーザー アカウントを使用するように、[ID] プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="4077e-217">Change the Identity properties to use the specific user account.</span></span>

     <span data-ttu-id="4077e-218">アクティブ化サービスが実行される ID を変更するには</span><span class="sxs-lookup"><span data-stu-id="4077e-218">To change the identity that the Activation Service runs under:</span></span>

    1. <span data-ttu-id="4077e-219">Services.msc を実行します。</span><span class="sxs-lookup"><span data-stu-id="4077e-219">Run Services.msc.</span></span>

    2. <span data-ttu-id="4077e-220">**Net.tcp リスナーアダプター** を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4077e-220">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>

4. <span data-ttu-id="4077e-221">[ **ログオン** ] タブでアカウントを変更します。</span><span class="sxs-lookup"><span data-stu-id="4077e-221">Change the account in the **LogOn** tab.</span></span>

5. <span data-ttu-id="4077e-222">ワークグループでは、無制限のトークンを使用してサービスを実行する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="4077e-222">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="4077e-223">この操作を行うには、コマンド ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4077e-223">To do this, run the following in a command window:</span></span>

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a><span data-ttu-id="4077e-224">関連項目</span><span class="sxs-lookup"><span data-stu-id="4077e-224">See also</span></span>

- <span data-ttu-id="4077e-225">[AppFabric のホストおよび永続化のサンプル](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4077e-225">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
