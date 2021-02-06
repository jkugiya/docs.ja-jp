---
description: '詳細情報: 既定のメッセージコントラクト'
title: 既定のメッセージ コントラクト
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 3587f6ce81e085a4915af8162f8d76aed30bf8df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632088"
---
# <a name="default-message-contract"></a><span data-ttu-id="b423c-103">既定のメッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="b423c-103">Default Message Contract</span></span>

<span data-ttu-id="b423c-104">既定のメッセージ コントラクトのサンプルでは、ユーザー定義のカスタム メッセージをサービス操作に渡したり、サービス操作から渡されたりするサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="b423c-104">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="b423c-105">このサンプルは、型指定されたサービスとして電卓インターフェイスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="b423c-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="b423c-106">このサンプルでは、 [はじめに](getting-started-sample.md)で使用される加算、減算、乗算、および除算の個々のサービス操作ではなく、オペランドと演算子の両方を含むカスタムメッセージを渡し、算術計算の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="b423c-106">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="b423c-107">クライアントはコンソール プログラム (.exe) であり、サービス ライブラリはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="b423c-107">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b423c-108">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b423c-108">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b423c-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b423c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b423c-110">このサービスでは、型 `MyMessage` のカスタム メッセージを受け入れて返す、1 つのサービス操作が定義されます。</span><span class="sxs-lookup"><span data-stu-id="b423c-110">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="b423c-111">このサンプルでは要求および応答のメッセージの型は同じですが、もちろん、メッセージ コントラクトは必要に応じて変えることができます。</span><span class="sxs-lookup"><span data-stu-id="b423c-111">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="b423c-112">カスタム メッセージ `MyMessage` は、<xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute>、および <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性で注釈が付いたクラスで定義されます。</span><span class="sxs-lookup"><span data-stu-id="b423c-112">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="b423c-113">このサンプルで使用するのは 3 番目のコンストラクタだけです。</span><span class="sxs-lookup"><span data-stu-id="b423c-113">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="b423c-114">メッセージ コントラクトを使用すると、SOAP メッセージを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="b423c-114">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="b423c-115">このサンプルでは、<xref:System.ServiceModel.MessageHeaderAttribute> 属性を使用して SOAP ヘッダーに `Operation` を格納します。</span><span class="sxs-lookup"><span data-stu-id="b423c-115">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="b423c-116">オペランド `N1`、`N2`、および `Result` は SOAP 本文内に示されます。これらのオペランドには <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性が適用されているためです。</span><span class="sxs-lookup"><span data-stu-id="b423c-116">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="b423c-117">実装クラスには、`Calculate` サービス処理用のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b423c-117">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="b423c-118">`CalculateService` クラスは、オペランドと演算子を要求メッセージから取得し、要求された計算結果が含まれる応答メッセージを作成します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b423c-118">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="b423c-119">クライアント用に生成されたクライアントコードは、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="b423c-119">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="b423c-120">このツールでは、必要に応じて、生成済みのクライアント コード内にメッセージ コントラクト型が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b423c-120">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="b423c-121">`/messageContract` コマンド オプションを指定すると、メッセージ コントラクトを強制的に生成できます。</span><span class="sxs-lookup"><span data-stu-id="b423c-121">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="b423c-122">`MyMessage` メッセージを使用するクライアントを次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="b423c-122">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage()
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="b423c-123">サンプルを実行すると、クライアント コンソール ウィンドウに計算が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b423c-123">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="b423c-124">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b423c-124">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="b423c-125">この時点で、ユーザー定義のカスタム メッセージがクライアントとサービスの操作間で渡されます。</span><span class="sxs-lookup"><span data-stu-id="b423c-125">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="b423c-126">メッセージ コントラクトでは、オペランドと結果はメッセージ本文内にあり、演算子はメッセージ ヘッダー内にあることが定義されました。</span><span class="sxs-lookup"><span data-stu-id="b423c-126">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="b423c-127">このメッセージ構造を監視するために、メッセージ ログ記録を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b423c-127">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b423c-128">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b423c-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b423c-129">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b423c-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b423c-130">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b423c-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b423c-131">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b423c-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b423c-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b423c-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b423c-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b423c-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b423c-134">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b423c-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b423c-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b423c-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
