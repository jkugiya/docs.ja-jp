---
description: 詳細については、「XmlReader Sample」を参照してください。
title: XmlReader サンプル
ms.date: 03/30/2017
helpviewer_keywords:
- XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
ms.openlocfilehash: 07e54c6f8ccfe36bc378bd8c839cd7dd7f6ecb42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668267"
---
# <a name="xmlreader-sample"></a><span data-ttu-id="6b63a-103">XmlReader サンプル</span><span class="sxs-lookup"><span data-stu-id="6b63a-103">XmlReader Sample</span></span>

<span data-ttu-id="6b63a-104">XmlReader サンプルでは、<xref:System.Xml.XmlReader> を使用したメッセージ本文の処理を示します。</span><span class="sxs-lookup"><span data-stu-id="6b63a-104">The XmlReader sample demonstrates the processing of a message body using an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="6b63a-105">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6b63a-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="6b63a-106">`Sum` という 1 つのサービス操作が追加され、このサービス操作は、合計する値の配列を含むメッセージを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="6b63a-106">An additional service operation, `Sum`, has been added that accepts a message that contains an array of values to add together.</span></span> <span data-ttu-id="6b63a-107">サービスは、<xref:System.Xml.XmlReader> を使用してメッセージを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="6b63a-107">The service reads the message using an <xref:System.Xml.XmlReader>.</span></span>

> [!NOTE]
> <span data-ttu-id="6b63a-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b63a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="6b63a-109">電卓インターフェイスには、`Sum` パラメータを受け取る <xref:System.ServiceModel.Channels.Message> という名前のサービス操作が含まれます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b63a-109">The calculator interface includes a service operation named `Sum` that accepts a <xref:System.ServiceModel.Channels.Message> parameter, as shown in the following sample code.</span></span>

```csharp
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
    [OperationContract]
    Message Sum(Message message);
}
```

<span data-ttu-id="6b63a-110">クライアントは、最初に整数値の配列を作成してこの配列からメッセージを作成し、次に作成されたメッセージを使用して `Sum` メソッドを呼び出すことによって、`Sum` にアクセスします。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b63a-110">The client accesses `Sum` by first creating an array of integer values, then creating a message from the array, and then calling the `Sum` method using the created message, as shown in the following sample code.</span></span>

```csharp
CalculatorClient client = new CalculatorClient();
//...

// Call the Sum service operation.
int[] values = { 1, 2, 3, 4, 5 };
using (new OperationContextScope(client.InnerChannel))
{
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);
    Message reply = client.Sum(request);
    int sum = reply.GetBody<int>();

    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);
}
```

<span data-ttu-id="6b63a-111">このサービスでは、サービス操作 `Sum` を実装し、<xref:System.Xml.XmlReader> オブジェクトを使用してメッセージ本文にアクセスすることによって、値を反復処理して合計します。</span><span class="sxs-lookup"><span data-stu-id="6b63a-111">In the service, the implementation of the service operation `Sum` accesses the message body using an <xref:System.Xml.XmlReader> object to iterate through the values to sum.</span></span> <span data-ttu-id="6b63a-112"><xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> メソッドが呼び出されると、メッセージ本文へのアクセスが行われます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b63a-112">The <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> method is called to access the message body, as shown in the following sample code.</span></span>

```csharp
public int Sum(Message message)
{
    int sum = 0;
    string text = "";

    //The body of the message contains a list of numbers that are read
    //directly using an XmlReader.
    XmlReader body = message.GetReaderAtBodyContents ();
    while (body.Read())
    {
        text = body.ReadString().Trim();
        if (text.Length>0)
        {
            sum += Convert.ToInt32(text);
        }
    }
    body.Close();
    Message response = Message.CreateMessage(
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",
       sum);
    return response;
}
```

<span data-ttu-id="6b63a-113">このサンプルを実行する場合は、操作の要求や応答はクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b63a-113">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="6b63a-114">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6b63a-114">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Sum(1,2,3,4,5) = 15

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b63a-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6b63a-115">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6b63a-116">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="6b63a-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6b63a-117">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6b63a-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="6b63a-118">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6b63a-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b63a-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6b63a-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b63a-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6b63a-120">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6b63a-121">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="6b63a-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b63a-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6b63a-122">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`
