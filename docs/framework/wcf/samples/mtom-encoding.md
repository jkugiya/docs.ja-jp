---
description: MTOM エンコードの詳細について説明します。
title: MTOM エンコーディング
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 0663ab07b27dc8d1458af9935f3402432c00ee25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752263"
---
# <a name="mtom-encoding"></a><span data-ttu-id="3298a-103">MTOM エンコーディング</span><span class="sxs-lookup"><span data-stu-id="3298a-103">MTOM Encoding</span></span>

<span data-ttu-id="3298a-104">このサンプルでは、WSHttpBinding で Message Transmission Optimization Mechanism (MTOM) メッセージ エンコーディングを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3298a-104">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="3298a-105">MTOM は、大きなサイズのバイナリ添付データを、SOAP メッセージを使用して未処理のバイトとして転送するための機構です。これにより、メッセージのサイズを縮小できます。</span><span class="sxs-lookup"><span data-stu-id="3298a-105">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3298a-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3298a-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3298a-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3298a-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3298a-108">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="3298a-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3298a-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3298a-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="3298a-110">既定では、WSHttpBinding はメッセージを標準のテキスト XML として送受信します。</span><span class="sxs-lookup"><span data-stu-id="3298a-110">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="3298a-111">MTOM メッセージの送受信を有効にするには、バインディングの構成で `messageEncoding` 属性を設定するか (次のコード サンプルを参照)、または `MessageEncoding` プロパティを使用して、バインディング上で直接有効にします。</span><span class="sxs-lookup"><span data-stu-id="3298a-111">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="3298a-112">これにより、サービスまたはクライアントで MTOM メッセージを送受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3298a-112">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="3298a-113">MTOM エンコーダでは、バイト配列とストリームを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="3298a-113">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="3298a-114">このサンプルでは、操作に `Stream` パラメータを使用して、最適化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3298a-114">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="3298a-115">このサンプル用に選択されたコントラクトは、バイナリ データをサービスに転送し、アップロードされたバイト数を戻り値として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3298a-115">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="3298a-116">サービスをインストールしてクライアントを実行すると、数字の 1000 が出力されます。これは、合計 1,000 バイトのデータが受信されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="3298a-116">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="3298a-117">出力の残りの部分には、さまざまなペイロードの最適化されたメッセージのサイズと最適化されなかったメッセージのサイズが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3298a-117">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3298a-118">MTOM を使用する目的は、大きいサイズのバイナリ ペイロードの転送を最適化することです。</span><span class="sxs-lookup"><span data-stu-id="3298a-118">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="3298a-119">MTOM を使用して SOAP メッセージを送信すると、小さなサイズのバイナリ ペイロードでオーバーヘッドが顕著に表れますが、数千バイトを越すようになるとオーバーヘッドは大きく減少します。</span><span class="sxs-lookup"><span data-stu-id="3298a-119">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="3298a-120">この理由は、標準のテキスト XML が Base64 を使用してバイナリ データをエンコードするためです。このエンコードには 3 バイトごとに 4 文字が必要で、データのサイズは 3 分の 1 増加します。</span><span class="sxs-lookup"><span data-stu-id="3298a-120">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="3298a-121">MTOM はバイナリ データを未処理のバイトとして転送できます。これによりエンコードとデコードの時間が節約でき、その結果メッセージのサイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="3298a-121">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="3298a-122">数千バイトというしきい値は、現在のビジネス ドキュメントやデジタル写真のサイズを考えると小さい値です。</span><span class="sxs-lookup"><span data-stu-id="3298a-122">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3298a-123">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3298a-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3298a-124">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3298a-124">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="3298a-125">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3298a-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="3298a-126">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3298a-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3298a-127">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3298a-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
