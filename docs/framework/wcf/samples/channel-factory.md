---
description: 詳細については、「Channel Factory」を参照してください。
title: チャネル ファクトリ
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: fad406e14887524fc69900e9775f1b6fbbcbecda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704135"
---
# <a name="channel-factory"></a><span data-ttu-id="b336b-103">チャネル ファクトリ</span><span class="sxs-lookup"><span data-stu-id="b336b-103">Channel Factory</span></span>

<span data-ttu-id="b336b-104">このサンプルでは、クライアント アプリケーションが、生成されたクライアントではなく <xref:System.ServiceModel.ChannelFactory> クラスを含むチャネルを作成できる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b336b-104">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="b336b-105">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="b336b-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="b336b-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b336b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b336b-107">このサンプルは、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して、サービス エンドポイントにチャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b336b-107">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="b336b-108">通常、サービスエンドポイントへのチャネルを作成するには、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用してクライアント型を生成し、生成された型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b336b-108">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="b336b-109">また、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用してチャネルを作成することもできます。サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b336b-109">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="b336b-110">次のサンプルコードによって作成されたサービスは、 [はじめに](getting-started-sample.md)のサービスと同じです。</span><span class="sxs-lookup"><span data-stu-id="b336b-110">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="b336b-111">このサンプルを複数コンピュータのシナリオで実行している場合は、前述のコードの "localhost" を、サービスを実行中のコンピュータの完全修飾名に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="b336b-111">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="b336b-112">このサンプルは、エンドポイント アドレスを設定する構成を使用していません。したがって、コード内でアドレスを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b336b-112">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="b336b-113">チャネルが作成されたら、生成されたクライアントと同様にサービス操作を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b336b-113">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="b336b-114">チャネルを閉じるには、最初にチャネルを <xref:System.ServiceModel.IClientChannel> インターフェイスにキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b336b-114">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="b336b-115">これは、生成されたチャネルが `ICalculator` インターフェイスによってクライアント アプリケーション内で宣言されているからです。このインターフェイスには `Add` および `Subtract` などのメソッドは含まれていますが、`Close` は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="b336b-115">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="b336b-116">`Close` メソッドは、<xref:System.ServiceModel.ICommunicationObject> インターフェイスで発生します。</span><span class="sxs-lookup"><span data-stu-id="b336b-116">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="b336b-117">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b336b-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b336b-118">クライアント アプリケーションをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b336b-118">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b336b-119">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b336b-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b336b-120">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b336b-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b336b-121">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b336b-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="b336b-122">このサンプルではメタデータの公開は有効化されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b336b-122">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="b336b-123">最初にこのサンプルのメタデータ公開を有効にして、クライアント型を再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b336b-123">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="b336b-124">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b336b-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="b336b-125">サンプルを複数コンピュータで実行するには</span><span class="sxs-lookup"><span data-stu-id="b336b-125">To run the sample cross machine</span></span>

1. <span data-ttu-id="b336b-126">次のコードの "localhost" を、サービスを実行中のコンピューターの完全修飾名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b336b-126">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="b336b-127">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b336b-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b336b-128">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b336b-128">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b336b-129">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b336b-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b336b-130">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b336b-130">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
