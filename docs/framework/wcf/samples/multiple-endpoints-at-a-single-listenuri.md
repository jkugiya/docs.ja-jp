---
description: 詳細については、単一の ListenUri での複数のエンドポイントに関するページをご覧ください。
title: 単一 ListenUri に対する複数のエンドポイント
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 20506b05528727a7db2a0720c5c89d237ebd7f5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752203"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="26653-103">単一 ListenUri に対する複数のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="26653-103">Multiple Endpoints at a Single ListenUri</span></span>

<span data-ttu-id="26653-104">このサンプルでは、単一 `ListenUri` で複数のエンドポイントをホストするサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="26653-104">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="26653-105">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="26653-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26653-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26653-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="26653-107">[複数のエンドポイント](multiple-endpoints.md)サンプルで説明したように、1つのサービスは複数のエンドポイントをホストできます。各エンドポイントは異なるアドレスを持ち、場合によっては異なるバインディングもあります。</span><span class="sxs-lookup"><span data-stu-id="26653-107">As demonstrated in the [Multiple Endpoints](multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="26653-108">このサンプルは、同じアドレスで複数のエンドポイントをホストできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="26653-108">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="26653-109">さらに、サービス エンドポイントが持つ、`EndpointAddress` と `ListenUri` の 2 種類のアドレスの違いも示します。</span><span class="sxs-lookup"><span data-stu-id="26653-109">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="26653-110">`EndpointAddress` とは、サービスの論理アドレスです。</span><span class="sxs-lookup"><span data-stu-id="26653-110">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="26653-111">これは、SOAP メッセージの宛先となるアドレスです。</span><span class="sxs-lookup"><span data-stu-id="26653-111">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="26653-112">`ListenUri` とはサービスの物理アドレスです。</span><span class="sxs-lookup"><span data-stu-id="26653-112">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="26653-113">これには、サービス エンドポイントが現在のコンピュータで実際にメッセージをリッスンする、ポートとアドレスの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="26653-113">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="26653-114">ほとんどの場合、これらのアドレスが異なっている必要はありません。`ListenUri` が明示的に指定されていない場合は、エンドポイントの `EndpointAddress` の URI が既定値になります。</span><span class="sxs-lookup"><span data-stu-id="26653-114">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="26653-115">ただし、複数の異なるサービス宛てのメッセージを受け入れることができるルーターを構成する場合など、2 つのアドレスを区別すると便利な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="26653-115">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="26653-116">サービス</span><span class="sxs-lookup"><span data-stu-id="26653-116">Service</span></span>  

 <span data-ttu-id="26653-117">このサンプルのサービスには、`ICalculator` と `IEcho` という 2 つのコントラクトがあります。</span><span class="sxs-lookup"><span data-stu-id="26653-117">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="26653-118">また、一般的な `IMetadataExchange` エンドポイントに加え、次のコードに示すように 3 つのアプリケーション エンドポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="26653-118">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="26653-119">3 つすべてのエンドポイントは、同じ `ListenUri` でホストされ、同じ `binding` を使用します。`ListenUri` が同じエンドポイントは、コンピュータの物理アドレスでメッセージをリッスンする 1 つのチャネル スタックを共有するので、同じバインディングを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26653-119">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="26653-120">各エンドポイントの `address` は URN です。通常、アドレスは物理的な場所を表し、実際は任意の種類の URI を設定できますが、サンプルで示すようにこのアドレスは照合とフィルタ処理を行う目的で使用されるので、このように設定されています。</span><span class="sxs-lookup"><span data-stu-id="26653-120">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="26653-121">3つのエンドポイントはすべて同じを共有するため、 `ListenUri` メッセージがそこに到着すると Windows Communication Foundation (WCF) は、メッセージの送信先のエンドポイントを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26653-121">Because all three endpoints share the same `ListenUri`, when a message arrives there, Windows Communication Foundation (WCF) must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="26653-122">各エンドポイントにはメッセージ フィルタがあり、これはアドレス フィルタとコントラクト フィルタの 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="26653-122">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="26653-123">アドレス フィルタは、SOAP メッセージの `To` とサービス エンドポイントのアドレスを照合します。</span><span class="sxs-lookup"><span data-stu-id="26653-123">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="26653-124">たとえば、`To "Urn:OtherEcho"` 宛てのメッセージだけが、このサービスの 3 つ目のエンドポイントの対象となります。</span><span class="sxs-lookup"><span data-stu-id="26653-124">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="26653-125">コントラクト フィルタは、特定のコントラクトの操作に関連付けられたアクションを照合します。</span><span class="sxs-lookup"><span data-stu-id="26653-125">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="26653-126">たとえば、`IEcho` のアクションが含まれるメッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="26653-126">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="26653-127">`Echo` は、このサービスの 2 つ目と 3 つ目の、両方のエンドポイントのコントラクト フィルターと照合します。これらのエンドポイントは、どちらも `IEcho` コントラクトをホストするからです。</span><span class="sxs-lookup"><span data-stu-id="26653-127">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="26653-128">このように、アドレス フィルタとコントラクト フィルタを組み合わせることによって、このサービスの `ListenUri` に到着する各メッセージを、正しいエンドポイントにルーティングすることができます。</span><span class="sxs-lookup"><span data-stu-id="26653-128">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="26653-129">3 つ目のエンドポイントは、他の 2 つのエンドポイントと区別されます。このエンドポイントは、他のエンドポイントとは異なるアドレスに送信されるメッセージを受け入れるからです。</span><span class="sxs-lookup"><span data-stu-id="26653-129">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="26653-130">1 つ目のエンドポイントと 2 つ目のエンドポイントは、コントラクト (受信メッセージのアクション) に基づいて相互に区別されます。</span><span class="sxs-lookup"><span data-stu-id="26653-130">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="26653-131">クライアント</span><span class="sxs-lookup"><span data-stu-id="26653-131">Client</span></span>  

 <span data-ttu-id="26653-132">サーバー上のエンドポイントに 2 つの異なるアドレスがあるのと同様に、クライアント エンドポイントにも 2 つのアドレスがあります。</span><span class="sxs-lookup"><span data-stu-id="26653-132">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="26653-133">サーバーとクライアントのどちらでも、論理アドレスは `EndpointAddress` と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="26653-133">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="26653-134">ただし、サーバーの物理アドレスは `ListenUri` と呼ばれるのに対し、クライアントの物理アドレスは `Via` と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="26653-134">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="26653-135">これら 2 つのアドレスがサーバー上にある場合、既定では同じアドレスを示します。</span><span class="sxs-lookup"><span data-stu-id="26653-135">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="26653-136">クライアントで、エンドポイントのアドレスとは異なる `Via` を指定するには、次のように `ClientViaBehavior` を使用します。</span><span class="sxs-lookup"><span data-stu-id="26653-136">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="26653-137">このアドレスは、通常どおりクライアントの構成ファイルで指定します。この構成ファイルは Svcutil.exe によって生成されたものです。</span><span class="sxs-lookup"><span data-stu-id="26653-137">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="26653-138">`Via` (サービスの `ListenUri` に相当) は、サービスのメタデータ内では示されません。したがってこの情報は、(サービスのメタデータ アドレスと同様に) クライアントに帯域外で伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26653-138">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="26653-139">このサンプルでは、クライアントはサーバーの 3 つの各アプリケーション エンドポイントにメッセージを送信し、3 つすべてのエンドポイントと通信できる (さらにそれらのエンドポイントを区別できる) ことを示します。これらすべてのエンドポイントが同じ `Via` を持つ場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="26653-139">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="26653-140">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="26653-140">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="26653-141">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="26653-141">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="26653-142">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="26653-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="26653-143">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="26653-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="26653-144">複数コンピューターの場合は、Client.cs ファイルで、localhost をサービス コンピューターの名前に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="26653-144">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26653-145">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="26653-145">The samples may already be installed on your machine.</span></span> <span data-ttu-id="26653-146">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="26653-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="26653-147">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="26653-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26653-148">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="26653-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
