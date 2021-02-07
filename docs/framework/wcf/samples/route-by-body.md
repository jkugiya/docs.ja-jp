---
description: 詳細については、「本文によるルーティング」を参照してください。
title: 本文別のルーティング
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 1c9505484c4af34c5e1f2f98524c01fb378c005f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703784"
---
# <a name="route-by-body"></a><span data-ttu-id="63623-103">本文別のルーティング</span><span class="sxs-lookup"><span data-stu-id="63623-103">Route by Body</span></span>

<span data-ttu-id="63623-104">このサンプルでは、任意の SOAP アクションでメッセージ オブジェクトを受け入れるサービスを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="63623-104">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="63623-105">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="63623-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="63623-106">このサービスは、`Calculate` 要求パラメータを受け入れる 1 つの <xref:System.ServiceModel.Channels.Message> 操作を実装して、<xref:System.ServiceModel.Channels.Message> 応答を返します。</span><span class="sxs-lookup"><span data-stu-id="63623-106">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="63623-107">このサンプルでは、クライアントはコンソール アプリケーション (.exe) で、サービスは IIS によってホストされています。</span><span class="sxs-lookup"><span data-stu-id="63623-107">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63623-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63623-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="63623-109">このサンプルでは、本文の内容に基づくメッセージ ディスパッチを示します。</span><span class="sxs-lookup"><span data-stu-id="63623-109">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="63623-110">組み込みの Windows Communication Foundation (WCF) サービスモデルメッセージのディスパッチメカニズムは、メッセージアクションに基づいています。</span><span class="sxs-lookup"><span data-stu-id="63623-110">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="63623-111">ただし既存の多くの Web サービスでは、すべての操作が Action="" で定義されています。</span><span class="sxs-lookup"><span data-stu-id="63623-111">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="63623-112">アクション情報に基づいてディスパッチ要求メッセージを保持する WSDL を基準として、サービスを構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="63623-112">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="63623-113">このサンプルでは、WSDL に基づくサービス コントラクトを示します (WSDL はこのサンプルに含まれる Service.wsdl 内に格納されています)。</span><span class="sxs-lookup"><span data-stu-id="63623-113">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="63623-114">サービスコントラクトは、 [はじめに](getting-started-sample.md)で使用されるものと同様に、計算ツールです。</span><span class="sxs-lookup"><span data-stu-id="63623-114">The service contract is Calculator, similar to the one used in [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="63623-115">ただし、`[OperationContract]` は、すべての操作に対して `Action=""` を指定します。</span><span class="sxs-lookup"><span data-stu-id="63623-115">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="63623-116">コントラクトが指定されている場合、サービスはカスタムのディスパッチ動作 `DispatchByBodyBehavior` に対して、複数の操作間でメッセージをディスパッチするように要求します。</span><span class="sxs-lookup"><span data-stu-id="63623-116">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="63623-117">このディスパッチ動作は、 `DispatchByBodyElementOperationSelector` カスタム操作セレクターを、それぞれのラッパー要素の QName をキーとする操作名のテーブルを使用して初期化します。</span><span class="sxs-lookup"><span data-stu-id="63623-117">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="63623-118">`DispatchByBodyElementOperationSelector` は本文の最初の子の開始タグを参照し、前述のテーブルを使用して操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="63623-118">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="63623-119">クライアントは、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、サービスによってエクスポートされた WSDL から自動生成されたプロキシを使用します。</span><span class="sxs-lookup"><span data-stu-id="63623-119">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="63623-120">すべての操作のアクションが空であっても、クライアント コードには影響ありません。ただし、自動生成されたプロキシ内の Action パラメータは例外です。</span><span class="sxs-lookup"><span data-stu-id="63623-120">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="63623-121">クライアント コードは、複数の計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="63623-121">The client code performs several calculations.</span></span> <span data-ttu-id="63623-122">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="63623-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="63623-123">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="63623-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="63623-124">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="63623-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="63623-125">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="63623-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="63623-126">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="63623-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="63623-127">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="63623-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="63623-128">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="63623-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="63623-129">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="63623-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="63623-130">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="63623-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="63623-131">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="63623-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
