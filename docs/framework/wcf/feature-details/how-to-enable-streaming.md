---
title: '方法: ストリーミングを有効にする'
description: 既定のバッファー転送ではなく、WCF 内でストリーム メッセージを有効にする方法について説明します。これは、処理前に完全に受信する必要があります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 7f77c406e1cfd4def116a1abe24aa92be74c6abe
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237743"
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="90b93-103">方法: ストリーミングを有効にする</span><span class="sxs-lookup"><span data-stu-id="90b93-103">How to: Enable Streaming</span></span>

<span data-ttu-id="90b93-104">Windows Communication Foundation (WCF) では、バッファーまたはストリーム転送を使用してメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="90b93-104">Windows Communication Foundation (WCF) can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="90b93-105">既定のバッファー転送モードでは、受信側がメッセージを読み取る前に、メッセージの送信が完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b93-105">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="90b93-106">ストリーミング転送モードでは、送信が完了していなくても、受信側でメッセージの処理を開始できます。</span><span class="sxs-lookup"><span data-stu-id="90b93-106">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="90b93-107">ストリーミング モードは、渡される情報が長い場合、または連続的に処理する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="90b93-107">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="90b93-108">ストリーミング モードは、メッセージが大きすぎてすべてをバッファーできない場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="90b93-108">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="90b93-109">ストリーミングを有効にするには、`OperationContract` を適切に定義し、トランスポート レベルでストリーミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="90b93-109">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="90b93-110">データをストリーミングするには</span><span class="sxs-lookup"><span data-stu-id="90b93-110">To stream data</span></span>  
  
1. <span data-ttu-id="90b93-111">データをストリーミングするには、サービスの `OperationContract` が次の 2 つの要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b93-111">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1. <span data-ttu-id="90b93-112">ストリーミングするデータを保持するパラメーターが、メソッド内の唯一のパラメーターになるようにします。</span><span class="sxs-lookup"><span data-stu-id="90b93-112">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="90b93-113">たとえば、入力メッセージをストリーミングする場合、厳密に 1 つの入力パラメーターが操作に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b93-113">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="90b93-114">同様に、出力メッセージをストリーミングする場合、厳密に 1 つの出力パラメーターまたは戻り値が操作に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b93-114">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2. <span data-ttu-id="90b93-115">パラメーターおよび戻り値の型の少なくとも 1 つが、<xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message> または <xref:System.Xml.Serialization.IXmlSerializable> になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b93-115">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="90b93-116">ストリーミングされたデータのコントラクトの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b93-116">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="90b93-117">`GetStream` 操作は、バッファーされた入力データを `string` として受信し、ストリーミングされた `Stream` を返します。</span><span class="sxs-lookup"><span data-stu-id="90b93-117">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="90b93-118">逆に言えば、`UploadStream` は `Stream` (ストリーミング) を取り込んで、`bool` (バッファー) を返します。</span><span class="sxs-lookup"><span data-stu-id="90b93-118">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="90b93-119">`EchoStream` は `Stream` を出し入れします。これは、入力および出力メッセージがどちらもストリーミングされる操作の例です。</span><span class="sxs-lookup"><span data-stu-id="90b93-119">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="90b93-120">最後に、`GetReversedStream` は入力を行わずに `Stream` (ストリーミング) を返します。</span><span class="sxs-lookup"><span data-stu-id="90b93-120">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2. <span data-ttu-id="90b93-121">バインディングではストリーミングを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b93-121">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="90b93-122">`TransferMode` プロパティを次の値のいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="90b93-122">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1. <span data-ttu-id="90b93-123">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="90b93-123">`Buffered`,</span></span>  
  
    2. <span data-ttu-id="90b93-124">`Streamed` (両方向のストリーミング通信を有効にする)。</span><span class="sxs-lookup"><span data-stu-id="90b93-124">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3. <span data-ttu-id="90b93-125">`StreamedRequest` (要求に対してのみストリーミングを有効にする)。</span><span class="sxs-lookup"><span data-stu-id="90b93-125">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4. <span data-ttu-id="90b93-126">`StreamedResponse` (応答に対してのみストリーミングを有効にする)。</span><span class="sxs-lookup"><span data-stu-id="90b93-126">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="90b93-127">`BasicHttpBinding` は、バインディングの `TransferMode` プロパティを公開し、`NetTcpBinding` と `NetNamedPipeBinding` も公開します。</span><span class="sxs-lookup"><span data-stu-id="90b93-127">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="90b93-128">`TransferMode` プロパティをトランスポート バインド要素に設定し、カスタム バインドで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="90b93-128">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="90b93-129">次のサンプルは、コードで `TransferMode` を設定する方法と、構成ファイルを変更して設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="90b93-129">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="90b93-130">どちらのサンプルも、受信可能なメッセージの最大サイズを決定する `maxReceivedMessageSize` プロパティを 64 MB に設定します。</span><span class="sxs-lookup"><span data-stu-id="90b93-130">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="90b93-131">既定の `maxReceivedMessageSize` は 64 KB です。これは、多くの場合ストリーミングを行うには小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="90b93-131">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="90b93-132">アプリケーションでの受信が予想されるメッセージ最大サイズに応じて、このクォータ設定を適切に変更してください。</span><span class="sxs-lookup"><span data-stu-id="90b93-132">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="90b93-133">また、`maxBufferSize` によりバッファーの最大サイズが決定されるので、適切に設定してください。</span><span class="sxs-lookup"><span data-stu-id="90b93-133">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1. <span data-ttu-id="90b93-134">次のサンプルの構成スニペットでは、`TransferMode` とカスタム HTTP バインディングで、`basicHttpBinding` プロパティをストリーミングに設定しています。</span><span class="sxs-lookup"><span data-stu-id="90b93-134">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. <span data-ttu-id="90b93-135">次のコード スニペットでは、`TransferMode` とカスタム HTTP バインディングで、`basicHttpBinding` プロパティをストリーミングに設定しています。</span><span class="sxs-lookup"><span data-stu-id="90b93-135">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. <span data-ttu-id="90b93-136">次のコード スニペットでは、カスタム TCP バインディングで、`TransferMode` プロパティをストリーミングに設定しています。</span><span class="sxs-lookup"><span data-stu-id="90b93-136">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. <span data-ttu-id="90b93-137">`GetStream`、`UploadStream`、および `EchoStream` の各操作では、ファイルからデータを直接送信したり、受信したデータを直接ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="90b93-137">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="90b93-138">次のコードは、`GetStream` の例です。</span><span class="sxs-lookup"><span data-stu-id="90b93-138">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="90b93-139">カスタム ストリームの書き込み</span><span class="sxs-lookup"><span data-stu-id="90b93-139">Writing a custom stream</span></span>  
  
1. <span data-ttu-id="90b93-140">送受信中のデータ ストリームの各チャンクに対して特殊な処理を行うには、<xref:System.IO.Stream> からカスタム ストリーム クラスを派生します。</span><span class="sxs-lookup"><span data-stu-id="90b93-140">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="90b93-141">カスタム ストリームの例として、`GetReversedStream` メソッドと `ReverseStream` クラスのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="90b93-141">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="90b93-142">`GetReversedStream` では、`ReverseStream` の新しいインスタンスを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="90b93-142">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="90b93-143">実際の処理は、システムが `ReverseStream` オブジェクトの読み取りを行うときに発生します。</span><span class="sxs-lookup"><span data-stu-id="90b93-143">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="90b93-144">`ReverseStream.Read` メソッドは、基になるファイルからバイトのチャンクを読み取り、バイトを反転し、その反転したバイトを返します。</span><span class="sxs-lookup"><span data-stu-id="90b93-144">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="90b93-145">このメソッドは、ファイル全体の内容を反転しません。一度に 1 つのバイト チャンクを反転します。</span><span class="sxs-lookup"><span data-stu-id="90b93-145">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="90b93-146">この例では、ストリームの内容の読み取りやストリームへの書き込み時に、ストリーミング処理を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90b93-146">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="90b93-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="90b93-147">See also</span></span>

- [<span data-ttu-id="90b93-148">大規模データとストリーミング</span><span class="sxs-lookup"><span data-stu-id="90b93-148">Large Data and Streaming</span></span>](large-data-and-streaming.md)
- [<span data-ttu-id="90b93-149">Stream</span><span class="sxs-lookup"><span data-stu-id="90b93-149">Stream</span></span>](../samples/stream.md)
