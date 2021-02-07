---
description: '詳細情報: 二重'
title: 二重
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 2681506e186cb38eedc1888987fa46ddf2c0b7b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755786"
---
# <a name="duplex"></a><span data-ttu-id="d4ec0-103">二重</span><span class="sxs-lookup"><span data-stu-id="d4ec0-103">Duplex</span></span>

<span data-ttu-id="d4ec0-104">双方向サンプルでは、双方向コントラクトを定義して実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-104">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="d4ec0-105">双方向通信は、クライアントがサービスとのセッションを確立し、サービスからクライアントにメッセージを返信できるチャネルがサービスに提供されると発生します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-105">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="d4ec0-106">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-106">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="d4ec0-107">双方向コントラクトは、クライアントからサービスへのプライマリ インターフェイスとサービスからクライアントへのコールバック インターフェイスという 2 つのインターフェイスのペアとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-107">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="d4ec0-108">このサンプルでは、`ICalculatorDuplex` インターフェイスを使用することにより、クライアントは算術演算を実行し、セッション経由で結果を計算できます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-108">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="d4ec0-109">サービスは、`ICalculatorDuplexCallback` インターフェイスで結果を返します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-109">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="d4ec0-110">コンテキストを確立して、クライアントとサービスの間で送信される一連のメッセージを相互に関連付ける必要があるため、二重のコントラクトにはセッションが必要です。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-110">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>

> [!NOTE]
> <span data-ttu-id="d4ec0-111">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d4ec0-112">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-112">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="d4ec0-113">双方向コントラクトは、次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-113">The duplex contract is defined as follows:</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,
                 CallbackContract=typeof(ICalculatorDuplexCallback))]
public interface ICalculatorDuplex
{
    [OperationContract(IsOneWay = true)]
    void Clear();
    [OperationContract(IsOneWay = true)]
    void AddTo(double n);
    [OperationContract(IsOneWay = true)]
    void SubtractFrom(double n);
    [OperationContract(IsOneWay = true)]
    void MultiplyBy(double n);
    [OperationContract(IsOneWay = true)]
    void DivideBy(double n);
}

public interface ICalculatorDuplexCallback
{
    [OperationContract(IsOneWay = true)]
    void Result(double result);
    [OperationContract(IsOneWay = true)]
    void Equation(string eqn);
}
```

<span data-ttu-id="d4ec0-114">`CalculatorService` クラスは、プライマリ `ICalculatorDuplex` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="d4ec0-115">このサービスは <xref:System.ServiceModel.InstanceContextMode.PerSession> インスタンス モードを使用して、各セッションの結果を保持します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="d4ec0-116">クライアントへのコールバック チャネルへのアクセスには、`Callback` というプライベート プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-116">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="d4ec0-117">サービスはこのコールバックを使用し、コールバック インターフェイスを介してメッセージをクライアントに返信します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-117">The service uses the callback for sending messages back to the client through the callback interface.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorDuplex
{
    double result = 0.0D;
    string equation;

    public CalculatorService()
    {
        equation = result.ToString();
    }

    public void Clear()
    {
        Callback.Equation($"{equation} = {result}");
        equation = result.ToString();
    }

    public void AddTo(double n)
    {
        result += n;
        equation += $" + {n}";
        Callback.Result(result);
    }

    //...

    ICalculatorDuplexCallback Callback
    {
        get
        {
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();
        }
    }
}
```

<span data-ttu-id="d4ec0-118">クライアントは、サービスからのメッセージを受信するために、双方向コントラクトのコールバック インターフェイスを実装するクラスを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="d4ec0-119">このサンプルでは、`CallbackHandler` クラスは `ICalculatorDuplexCallback` インターフェイスを実装するように定義されています。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-119">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>

```csharp
public class CallbackHandler : ICalculatorDuplexCallback
{
   public void Result(double result)
   {
      Console.WriteLine("Result({0})", result);
   }

   public void Equation(string equation)
   {
      Console.WriteLine("Equation({0}", equation);
   }
}
```

<span data-ttu-id="d4ec0-120">双方向コントラクト用に生成されるプロキシは、コンストラクト時に <xref:System.ServiceModel.InstanceContext> が提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-120">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="d4ec0-121">この <xref:System.ServiceModel.InstanceContext> がコールバック インターフェイスを実装するオブジェクトのサイトとして使用され、サービスから返信されるメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-121">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="d4ec0-122"><xref:System.ServiceModel.InstanceContext> は、`CallbackHandler` クラスのインスタンスを使用して構築されます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-122">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="d4ec0-123">このオブジェクトは、コールバック インターフェイスでサービスからクライアントに送信されるメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

```csharp
// Construct InstanceContext to handle messages on callback interface.
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());

// Create a client.
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);

Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");
Console.WriteLine();

// Call the AddTo service operation.
double value = 100.00D;
client.AddTo(value);

// Call the SubtractFrom service operation.
value = 50.00D;
client.SubtractFrom(value);

// Call the MultiplyBy service operation.
value = 17.65D;
client.MultiplyBy(value);

// Call the DivideBy service operation.
value = 2.00D;
client.DivideBy(value);

// Complete equation.
client.Clear();

Console.ReadLine();

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();
```

<span data-ttu-id="d4ec0-124">この構成は、セッション通信と双方向通信の両方をサポートするバインディングを提供するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-124">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="d4ec0-125">`wsDualHttpBinding` はセッション通信をサポートし、どちらの方向にも HTTP 接続が 1 つ用意される双方向 HTTP 接続を提供して双方向通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-125">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="d4ec0-126">サービスでの構成の唯一の違いは、使用されるバインディングです。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-126">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="d4ec0-127">クライアントで、サーバーがクライアントへの接続に使用するアドレスを構成する必要があります。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-127">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<client>
  <endpoint name=""
            address="http://localhost/servicemodelsamples/service.svc"
            binding="wsDualHttpBinding"
            bindingConfiguration="DuplexBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
</client>

<bindings>
  <!-- Configure a binding that support duplex communication. -->
  <wsDualHttpBinding>
    <binding name="DuplexBinding"
             clientBaseAddress="http://localhost:8000/myClient/">
    </binding>
  </wsDualHttpBinding>
</bindings>
```

<span data-ttu-id="d4ec0-128">サンプルを実行すると、クライアントに戻ってきたメッセージがサービスから送信されたコールバック インターフェイスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-128">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="d4ec0-129">それぞれの中間結果が表示され、その後にすべての操作が完了したときの数式全体が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-129">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="d4ec0-130">Enter キーを押してクライアントをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-130">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4ec0-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d4ec0-131">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d4ec0-132">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d4ec0-133">ソリューションの C#、C++、または Visual Basic .NET エディションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-133">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="d4ec0-134">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d4ec0-135">複数コンピューター構成でクライアントを実行する場合は、 `address` 次に示すように、要素の[ \<endpoint> \<client> の](../../configure-apps/file-schema/wcf/endpoint-of-client.md)属性と要素の要素の属性の両方の "localhost" を、 `clientBaseAddress` [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) 適切なコンピューターの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-135">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>

    ```xml
    <client>
        <endpoint name = ""
        address="http://service_machine_name/servicemodelsamples/service.svc"
        ... />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```

> [!IMPORTANT]
> <span data-ttu-id="d4ec0-136">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4ec0-137">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d4ec0-138">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4ec0-139">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d4ec0-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
