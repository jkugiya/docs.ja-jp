---
description: 詳細については、Windows Communication Foundation するメッセージキューに関するページを参照してください。
title: Windows Communication Foundation へのメッセージ キュー
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 53c535379584bcb8fa50d1b550f87ea7acc15175
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704005"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="820fa-103">Windows Communication Foundation へのメッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="820fa-103">Message Queuing to Windows Communication Foundation</span></span>

<span data-ttu-id="820fa-104">このサンプルでは、メッセージキュー (MSMQ) アプリケーションが MSMQ メッセージを Windows Communication Foundation (WCF) サービスに送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="820fa-104">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="820fa-105">サービスは自己ホスト型コンソール アプリケーションであるので、キューに置かれたメッセージをサービスが受信するようすを観察できます。</span><span class="sxs-lookup"><span data-stu-id="820fa-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="820fa-106">サービス コントラクトは `IOrderProcessor` です。これは、キューでの使用に適した一方向サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="820fa-106">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="820fa-107">MSMQ メッセージには Action ヘッダーがないので、さまざまな MSMQ メッセージを操作コントラクトに自動的にマッピングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="820fa-107">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="820fa-108">したがって、存在する操作コントラクトは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="820fa-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="820fa-109">サービスに対して複数の操作コントラクトを定義する場合は、ディスパッチする操作コントラクトを決定するために使用できる、MSMQ メッセージ内のヘッダー (ラベルや correlationID など) に関する情報をアプリケーションで提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="820fa-109">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="820fa-110">MSMQ メッセージには、操作コントラクトの別のパラメータにマッピングされるヘッダーに関する情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="820fa-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="820fa-111">パラメータは <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> 型の `MsmqMessage<T>` です。これには、基になる MSMQ メッセージが含まれます。</span><span class="sxs-lookup"><span data-stu-id="820fa-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="820fa-112"><xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> (`MsmqMessage<T>`) クラスの型 "T" は、シリアル化されて MSMQ メッセージ本文に含まれているデータを表します。</span><span class="sxs-lookup"><span data-stu-id="820fa-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="820fa-113">このサンプルでは、`PurchaseOrder` 型がシリアル化されて MSMQ メッセージ本文になっています。</span><span class="sxs-lookup"><span data-stu-id="820fa-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

 <span data-ttu-id="820fa-114">発注書処理サービスのサービス コントラクトを次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="820fa-114">The following sample code shows the service contract of the order processing service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="820fa-115">サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="820fa-115">The service is self hosted.</span></span> <span data-ttu-id="820fa-116">MSMQ を使用する場合、使用するキューをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="820fa-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="820fa-117">手動で作成することもコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="820fa-117">This can be done manually or through code.</span></span> <span data-ttu-id="820fa-118">このサンプルでは、サービスはキューの存在を確認し、必要な場合はキューを作成します。</span><span class="sxs-lookup"><span data-stu-id="820fa-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="820fa-119">キュー名は構成ファイルから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="820fa-119">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 <span data-ttu-id="820fa-120">サービスは、<xref:System.ServiceModel.ServiceHost> の `OrderProcessorService` を作成して開きます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="820fa-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 <span data-ttu-id="820fa-121">MSMQ キュー名は、構成ファイルの appSettings セクションに指定されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="820fa-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="820fa-122">キュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="820fa-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="820fa-123">WCF エンドポイントアドレスは、formatname スキーマを指定し、ローカルコンピューターに localhost を使用します。</span><span class="sxs-lookup"><span data-stu-id="820fa-123">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="820fa-124">それぞれの MSMQ 形式名のアドレス指定ガイドラインに対するキューのアドレスが msmq.formatname スキームの後に続きます。</span><span class="sxs-lookup"><span data-stu-id="820fa-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="820fa-125">クライアント アプリケーションは MSMQ アプリケーションです。このアプリケーションでは <xref:System.Messaging.MessageQueue.Send%2A> メソッドを使用して、非揮発性メッセージとトランザクション メッセージをキューに送信します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="820fa-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

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

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="820fa-126">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="820fa-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="820fa-127">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="820fa-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="820fa-128">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="820fa-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="820fa-129">キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="820fa-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="820fa-130">たとえば、クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="820fa-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="820fa-131">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="820fa-131">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="820fa-132">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="820fa-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="820fa-133">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="820fa-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="820fa-134">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="820fa-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="820fa-135">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="820fa-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="820fa-136">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="820fa-136">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="820fa-137">Visual Studio 2012 でサーバーマネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="820fa-137">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="820fa-138">[ **機能** ] タブを展開します。</span><span class="sxs-lookup"><span data-stu-id="820fa-138">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="820fa-139">[ **プライベートメッセージキュー**] を右クリックし、[ **新規**]、[ **プライベートキュー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="820fa-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="820fa-140">[ **トランザクション** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="820fa-140">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="820fa-141">`ServiceModelSamplesTransacted`新しいキューの名前として「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="820fa-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="820fa-142">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="820fa-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="820fa-143">1台のコンピューター構成でサンプルを実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="820fa-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="820fa-144">コンピューター間でサンプルを実行する</span><span class="sxs-lookup"><span data-stu-id="820fa-144">Run the sample across computers</span></span>

1. <span data-ttu-id="820fa-145">サービスのプログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="820fa-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="820fa-146">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="820fa-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="820fa-147">Client.exe.config ファイルを開き、orderQueueName を変更して "." の代わりにサービス コンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="820fa-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="820fa-148">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="820fa-148">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="820fa-149">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="820fa-149">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="820fa-150">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="820fa-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="820fa-151">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="820fa-151">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="820fa-152">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="820fa-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="820fa-153">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="820fa-153">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a><span data-ttu-id="820fa-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="820fa-154">See also</span></span>

- [<span data-ttu-id="820fa-155">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="820fa-155">Queues in WCF</span></span>](../feature-details/queues-in-wcf.md)
- [<span data-ttu-id="820fa-156">方法: WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="820fa-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="820fa-157">[メッセージ キューイング (Message Queuing)](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="820fa-157">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
