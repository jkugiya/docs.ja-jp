---
description: 詳細については、「メッセージングプロトコル」を参照してください。
title: メッセージング プロトコル
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: f4dd15d41266d3e5492b584f9f8e31f456a70ef7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733971"
---
# <a name="messaging-protocols"></a><span data-ttu-id="60c8f-103">メッセージング プロトコル</span><span class="sxs-lookup"><span data-stu-id="60c8f-103">Messaging Protocols</span></span>

<span data-ttu-id="60c8f-104">Windows Communication Foundation (WCF) チャネルスタックは、エンコードおよびトランスポートチャネルを使用して内部メッセージ表現をワイヤ形式に変換し、特定のトランスポートを使用して送信します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-104">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="60c8f-105">Web サービスの相互運用性を確保するために、最も一般的に使用されるトランスポートは HTTP です。また、Web サービスが使用する最も一般的なエンコーディングは、XML ベースの SOAP 1.1、SOAP 1.2、および MTOM (Message Transmission Optimization Mechanism) です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-105">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="60c8f-106">このトピックでは、で採用されている次のプロトコルの WCF 実装の詳細について説明 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-106">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="60c8f-107">仕様/ドキュメント:</span><span class="sxs-lookup"><span data-stu-id="60c8f-107">Specification/document:</span></span>

- [<span data-ttu-id="60c8f-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="60c8f-108">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="60c8f-109">[SOAP 1.1 HTTP バインド](https://www.w3.org/TR/2000/NOTE-SOAP-20000508)、セクション7</span><span class="sxs-lookup"><span data-stu-id="60c8f-109">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="60c8f-110">[SOAP 1.2 HTTP バインド](https://www.w3.org/TR/soap12-part2) セクション7</span><span class="sxs-lookup"><span data-stu-id="60c8f-110">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="60c8f-111">このトピックでは、およびが使用する次のプロトコルの WCF 実装の詳細について説明し <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-111">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="60c8f-112">仕様/ドキュメント:</span><span class="sxs-lookup"><span data-stu-id="60c8f-112">Specification/Document:</span></span>

- [<span data-ttu-id="60c8f-113">XML</span><span class="sxs-lookup"><span data-stu-id="60c8f-113">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="60c8f-114">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="60c8f-114">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="60c8f-115">SOAP 1.2 コア</span><span class="sxs-lookup"><span data-stu-id="60c8f-115">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="60c8f-116">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="60c8f-116">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="60c8f-117">W3C Web Services Addressing 1.0 - コア</span><span class="sxs-lookup"><span data-stu-id="60c8f-117">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="60c8f-118">W3C Web Services Addressing 1.0 - SOAP バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-118">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="60c8f-119">W3C Web サービスアドレス指定 1.0-WSDL バインド</span><span class="sxs-lookup"><span data-stu-id="60c8f-119">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="60c8f-120">W3C Web Services Addressing 1.0 - メタデータ</span><span class="sxs-lookup"><span data-stu-id="60c8f-120">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="60c8f-121">WSDL SOAP1.1 バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-121">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="60c8f-122">WSDL SOAP1.2 バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-122">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="60c8f-123">このトピックでは、を使用する次のプロトコルの WCF 実装の詳細について説明 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-123">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="60c8f-124">仕様/ドキュメント:</span><span class="sxs-lookup"><span data-stu-id="60c8f-124">Specification/document:</span></span>

- [<span data-ttu-id="60c8f-125">XOP</span><span class="sxs-lookup"><span data-stu-id="60c8f-125">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="60c8f-126">MTOM および SOAP 1.2 バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-126">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="60c8f-127">MTOM SOAP 1.1 バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-127">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="60c8f-128">MTOM WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="60c8f-128">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="60c8f-129">このトピックでは、次の XML 名前空間と関連付けられているプレフィックスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-129">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="60c8f-130">Prefix</span><span class="sxs-lookup"><span data-stu-id="60c8f-130">Prefix</span></span> | <span data-ttu-id="60c8f-131">名前空間 URI (Uniform Resource Identifier)</span><span class="sxs-lookup"><span data-stu-id="60c8f-131">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="60c8f-132">s11</span><span class="sxs-lookup"><span data-stu-id="60c8f-132">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="60c8f-133">s12</span><span class="sxs-lookup"><span data-stu-id="60c8f-133">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="60c8f-134">wsa</span><span class="sxs-lookup"><span data-stu-id="60c8f-134">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="60c8f-135">wsam</span><span class="sxs-lookup"><span data-stu-id="60c8f-135">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="60c8f-136">wsap</span><span class="sxs-lookup"><span data-stu-id="60c8f-136">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="60c8f-137">wsa10</span><span class="sxs-lookup"><span data-stu-id="60c8f-137">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="60c8f-138">wsaw10</span><span class="sxs-lookup"><span data-stu-id="60c8f-138">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="60c8f-139">xop</span><span class="sxs-lookup"><span data-stu-id="60c8f-139">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="60c8f-140">xmime</span><span class="sxs-lookup"><span data-stu-id="60c8f-140">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="60c8f-141">dp</span><span class="sxs-lookup"><span data-stu-id="60c8f-141">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="60c8f-142">SOAP 1.1 と SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="60c8f-142">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="60c8f-143">エンベロープと処理モデル</span><span class="sxs-lookup"><span data-stu-id="60c8f-143">Envelope and Processing Model</span></span>

<span data-ttu-id="60c8f-144">WCF は、Basic Profile 1.1 (BP11) および Basic Profile 1.0 (SSBP10) に従って、SOAP 1.1 エンベロープ処理を実装します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-144">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="60c8f-145">SOAP 1.2 エンベロープの処理は、SOAP12-Part1 に従って実装されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-145">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="60c8f-146">このセクションでは、BP11 と SOAP12 に関して、WCF によって実行される特定の実装の選択肢について説明します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-146">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="60c8f-147">必須のヘッダー処理</span><span class="sxs-lookup"><span data-stu-id="60c8f-147">Mandatory Header Processing</span></span>

<span data-ttu-id="60c8f-148">WCF は、SOAP 1.1 および SOAP 1.2 仕様で説明されているようにマークされたヘッダーを処理するための規則に従い `mustUnderstand` ます。次のような違いがあります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-148">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="60c8f-149">WCF チャネルスタックに入るメッセージは、関連付けられたバインド要素によって構成された個々のチャネル (テキストメッセージエンコーディング、セキュリティ、信頼できるメッセージング、トランザクションなど) によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-149">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="60c8f-150">各チャネルは、関連付けられた名前空間からヘッダーを認識し、認識済みとしてマークします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-150">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="60c8f-151">メッセージがディスパッチャーに入ると、操作フォーマッタは対応するメッセージ コントラクトと操作コントラクトで想定されたヘッダーを読み取り、認識済みとしてマークします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-151">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="60c8f-152">次に、ディスパッチャーは、`mustUnderstand` としてマークされているにもかかわらず、認識されていないヘッダーが残っていないかどうかを検証し、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-152">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="60c8f-153">受信者を対象とする `mustUnderstand` ヘッダーが含まれたメッセージが、受信者のアプリケーション コードで処理されることはありません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-153">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="60c8f-154">このようなレイヤー化された処理により、SOAP ノードのインフラストラクチャ レイヤーとアプリケーション レイヤーを次のように分離することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-154">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="60c8f-155">B1111: 認識されていないヘッダーは、メッセージが WCF インフラストラクチャチャネルスタックによって処理された後、アプリケーションによって処理される前に検出されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-155">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="60c8f-156">`mustUnderstand` ヘッダーの値は、SOAP 1.1 と SOAP 1.2 で異なります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-156">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="60c8f-157">Basic Profile 1.1 では、SOAP 1.1 メッセージの `mustUnderstand` の値が 0 または 1 である必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-157">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="60c8f-158">SOAP 1.2 では、値として 0、1、`false`、および `true` を使用できますが、`xs:boolean` 値の正規表現 (`false`、`true`) を出力することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-158">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="60c8f-159">B1112: WCF は、soap `mustUnderstand` 1.1 と soap 1.2 の両方のバージョンの soap エンベロープに対して、値0および1を出力します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-159">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="60c8f-160">WCF は、ヘッダーのの値空間全体 `xs:boolean` `mustUnderstand` (0、1、 `false` 、 `true` ) を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-160">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="60c8f-161">SOAP エラー</span><span class="sxs-lookup"><span data-stu-id="60c8f-161">SOAP Faults</span></span>

<span data-ttu-id="60c8f-162">WCF 固有の SOAP エラーの実装の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-162">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="60c8f-163">B2121: WCF は、、、およびの各 SOAP 1.1 エラーコードを返します `s11:mustUnderstand` `s11:Client` `s11:Server` 。</span><span class="sxs-lookup"><span data-stu-id="60c8f-163">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="60c8f-164">B2122: WCF は、、、およびの各 SOAP 1.2 エラーコードを返します `s12:MustUnderstand` `s12:Sender` `s12:Receiver` 。</span><span class="sxs-lookup"><span data-stu-id="60c8f-164">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="60c8f-165">HTTP バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-165">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="60c8f-166">SOAP 1.1 HTTP バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-166">SOAP 1.1 HTTP Binding</span></span>

<span data-ttu-id="60c8f-167">WCF では、次の説明に従って、Basic Profile 1.1 specification セクション3.4 に従った SOAP 1.1 HTTP バインディングが実装されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-167">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="60c8f-168">B2211: WCF サービスは、HTTP POST 要求のリダイレクトを実装していません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-168">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="60c8f-169">B2212: WCF クライアントは、3.4.8 に従って HTTP クッキーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-169">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="60c8f-170">SOAP 1.2 HTTP バインディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-170">SOAP 1.2 HTTP Binding</span></span>

<span data-ttu-id="60c8f-171">WCF では、SOAP 1.2-part 2 (SOAP12Part2) 仕様で説明されている SOAP 1.2 HTTP バインディングを実装しています。これについては、次の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60c8f-171">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="60c8f-172">SOAP 1.2 では、`application/soap+xml` メディア タイプの省略可能なアクション パラメーターが導入されました。</span><span class="sxs-lookup"><span data-stu-id="60c8f-172">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="60c8f-173">このパラメーターは、WS-Addressing を使用していない場合に、SOAP メッセージの本文を解析する必要なく、メッセージ ディスパッチを最適化する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-173">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="60c8f-174">R2221 : `application/soap+xml` のアクション パラメーターが SOAP 1.2 要求に含まれている場合、対応する WSDL バインディング内の `soapAction` 要素の `wsoap12:operation` 属性と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-174">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="60c8f-175">R2222 : WS-Addressing 2004/08 または WS-Addressing 1.0 を使用しているときに、`application/soap+xml` のアクション パラメーターが SOAP 1.2 メッセージに含まれている場合、`wsa:Action` と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-175">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="60c8f-176">WS-Addressing が無効になっているときに、受信要求にアクション パラメーターが含まれていない場合、メッセージの `Action` は指定されていないものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-176">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="60c8f-177">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="60c8f-177">WS-Addressing</span></span>

<span data-ttu-id="60c8f-178">WCF は、次の3つのバージョンの WS-ADDRESSING を実装します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-178">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="60c8f-179">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="60c8f-179">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="60c8f-180">W3C Web Services Addressing 1.0 コア (ADDR10-CORE) - SOAP バインディング (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="60c8f-180">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="60c8f-181">WS-Addressing 1.0 - メタデータ</span><span class="sxs-lookup"><span data-stu-id="60c8f-181">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="60c8f-182">エンドポイント参照</span><span class="sxs-lookup"><span data-stu-id="60c8f-182">Endpoint References</span></span>

<span data-ttu-id="60c8f-183">WCF が実装する WS-Addressing のすべてのバージョンでエンドポイント参照を使用してエンドポイントを記述します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-183">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="60c8f-184">エンドポイント参照と WS-Addressing のバージョン</span><span class="sxs-lookup"><span data-stu-id="60c8f-184">Endpoint References and WS-Addressing Versions</span></span>

<span data-ttu-id="60c8f-185">WCF は、WS-Addressing を使用する多数のインフラストラクチャプロトコルと、特に `EndpointReference` 要素と `W3C.WsAddressing.EndpointReferenceType` クラス (Ws-reliablemessaging、WS-SECURECONVERSATION、ws-trust など) を実装します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-185">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="60c8f-186">WCF では、他のインフラストラクチャプロトコルでのいずれかのバージョンの WS-Addressing の使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-186">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="60c8f-187">WCF エンドポイントは、エンドポイントごとに1つのバージョンの WS-Addressing をサポートします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-187">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="60c8f-188">R3111 の場合、 `EndpointReference` WCF エンドポイントと交換されるメッセージで使用される要素または型の名前空間は、このエンドポイントによって実装される WS-Addressing のバージョンと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-188">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="60c8f-189">たとえば、WCF エンドポイントで ws-reliablemessaging が実装されている場合、 `AcksTo` 内部のエンドポイントによって返されるヘッダーは、 `CreateSequenceResponse` `EncodingBinding` このエンドポイントに対して要素が指定した WS-Addressing バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-189">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="60c8f-190">エンドポイント参照とメタデータ</span><span class="sxs-lookup"><span data-stu-id="60c8f-190">Endpoint References and Metadata</span></span>

<span data-ttu-id="60c8f-191">多くのシナリオでは、指定されたエンドポイントのメタデータまたはメタデータへの参照を伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-191">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="60c8f-192">B3121: WCF は、WS-MetadataExchange (MEX) 仕様のセクション6で説明されているメカニズムを使用して、エンドポイント参照のメタデータを値または参照渡しで含めます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-192">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="60c8f-193">でトークン発行者によって発行されたセキュリティアサーションマークアップ言語 (SAML) トークンを使用して、WCF サービスが認証を必要とするシナリオについて考えてみ `http://sts.fabrikam123.com` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-193">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="60c8f-194">WCF エンドポイントは、 `sp:IssuedToken` `sp:Issuer` トークン発行者を指す入れ子になったアサーションと共にアサーションを使用して、この認証要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-194">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="60c8f-195">`sp:Issuer` アサーションにアクセスするクライアント アプリケーションは、トークン発行者のエンドポイントとの通信方法を知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-195">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="60c8f-196">クライアントは、トークン発行者に関するメタデータを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-196">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="60c8f-197">MEX で定義されているエンドポイント参照メタデータ拡張を使用して、WCF はトークン発行者のメタデータへの参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-197">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a><span data-ttu-id="60c8f-198">メッセージのアドレス指定ヘッダー</span><span class="sxs-lookup"><span data-stu-id="60c8f-198">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="60c8f-199">メッセージ ヘッダー</span><span class="sxs-lookup"><span data-stu-id="60c8f-199">Message Headers</span></span>

<span data-ttu-id="60c8f-200">どちらの WS-Addressing バージョンでも、WCF では、仕様、、、、およびの指定に従って、次のメッセージヘッダーが使用され `wsa:To` `wsa:ReplyTo` `wsa:Action` `wsa:MessageID` `wsa:RelatesTo` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-200">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="60c8f-201">B3211: すべての WS-Addressing バージョンでは、WCF では、メッセージヘッダーと WS-Addressing の既定のメッセージヘッダーとが受け入れられません `wsa:FaultTo` `wsa:From` 。</span><span class="sxs-lookup"><span data-stu-id="60c8f-201">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="60c8f-202">WCF アプリケーションと対話するアプリケーションは、これらのメッセージヘッダーを追加することができ、WCF はそれに応じてそれらを処理します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-202">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="60c8f-203">参照パラメーターと参照プロパティ</span><span class="sxs-lookup"><span data-stu-id="60c8f-203">Reference Parameters and Properties</span></span>

<span data-ttu-id="60c8f-204">WCF は、それぞれの仕様に従って、エンドポイント参照パラメーターと参照プロパティの処理を実装します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-204">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="60c8f-205">B3221: WS-Addressing 2004/08 を使用するように構成されている場合、WCF エンドポイントでは、参照プロパティと参照パラメーターの処理が区別されません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-205">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="60c8f-206">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="60c8f-206">Message Exchange Patterns</span></span>

<span data-ttu-id="60c8f-207">Web サービス操作の呼び出しに関連する一連のメッセージは、 *メッセージ交換パターン* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-207">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="60c8f-208">WCF は、一方向、要求/応答、および双方向のメッセージ交換パターンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-208">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="60c8f-209">このセクションでは、使用するメッセージ交換パターンによって異なるメッセージ処理に関する WS-Addressing の要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-209">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="60c8f-210">このセクション全体を通して、リクエスターが最初のメッセージを送信し、レスポンダーが最初のメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-210">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="60c8f-211">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="60c8f-211">One-Way Message</span></span>

<span data-ttu-id="60c8f-212">WCF エンドポイントが一方向パターンに従うために指定されたを持つメッセージをサポートするように構成されている場合 `Action` 、wcf エンドポイントは次の動作と要件に従います。</span><span class="sxs-lookup"><span data-stu-id="60c8f-212">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="60c8f-213">特に指定がない限り、WCF でサポートされている WS-Addressing の両方のバージョンに対して動作とルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-213">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="60c8f-214">R3311 : リクエスターは、`wsa:To`、`wsa:Action`、およびエンドポイント参照によって指定されたすべての参照パラメーターのヘッダーを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-214">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="60c8f-215">WS-Addressing 2004/08 を使用し、エンドポイント参照によって参照プロパティが指定されている場合、対応するヘッダーもメッセージに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-215">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="60c8f-216">B3312 : リクエスターは、`MessageID`、`ReplyTo`、および `FaultTo` の各ヘッダーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-216">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="60c8f-217">受信側のインフラストラクチャはこれらのヘッダーを無視し、ヘッダーはアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-217">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="60c8f-218">R3313 : HTTP を使用し、HTTP 応答レッグで送信するメッセージがない場合、レスポンダーは空の本文と HTTP 202 ステータス コードを含む HTTP 応答を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-218">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="60c8f-219">HTTP トランスポートを使用しており、操作コントラクトで一方向のメッセージが宣言されている場合でも、HTTP 応答を使用してインフラストラクチャ メッセージを送信できます。たとえば、信頼できるメッセージングでは、HTTP 応答で `SequenceAcknowledgement` メッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-219">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="60c8f-220">B3314: WCF レスポンダーは、一方向のメッセージへの応答としてエラーメッセージを送信しません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-220">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="60c8f-221">要求/応答</span><span class="sxs-lookup"><span data-stu-id="60c8f-221">Request-Reply</span></span>

<span data-ttu-id="60c8f-222">要求/応答パターンに従うために、が指定されたメッセージに対して WCF エンドポイントが構成されている場合 `Action` 、wcf エンドポイントは以下の動作と要件に従います。</span><span class="sxs-lookup"><span data-stu-id="60c8f-222">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="60c8f-223">特に指定しない限り、WCF でサポートされている WS-Addressing の両方のバージョンに対して動作とルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-223">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="60c8f-224">R3321: 要求元は、 `wsa:To` `wsa:Action` `wsa:MessageID` エンドポイント参照によって指定されたすべての参照パラメーターまたは参照プロパティ (またはその両方) の要求、、、およびの各ヘッダーにを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-224">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="60c8f-225">R3322 : WS-Addressing 2004/08 を使用する場合、`ReplyTo` も要求に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-225">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="60c8f-226">R3323: WS-Addressing 1.0 が使用されていて、要求に含まれて `ReplyTo` いない場合、[address] プロパティがに設定された既定のエンドポイント参照 `http://www.w3.org/2005/08/addressing/anonymous` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-226">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="60c8f-227">R3324: 要求元は `wsa:To` 、 `wsa:Action` 応答メッセージに、、およびの各 `wsa:RelatesTo` ヘッダーと、 `ReplyTo` 要求内のエンドポイント参照によって指定されたすべての参照パラメーターまたは参照プロパティ (またはその両方) のヘッダーを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-227">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="60c8f-228">Web Services Addressing エラー</span><span class="sxs-lookup"><span data-stu-id="60c8f-228">Web Services Addressing Faults</span></span>

<span data-ttu-id="60c8f-229">R3411: WCF は WS-Addressing 2004/08 で定義されている次の障害を生成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-229">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="60c8f-230">コード</span><span class="sxs-lookup"><span data-stu-id="60c8f-230">Code</span></span> | <span data-ttu-id="60c8f-231">原因</span><span class="sxs-lookup"><span data-stu-id="60c8f-231">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="60c8f-232">このチャネル用に確立された応答アドレスとは異なる `ReplyTo` を使用してメッセージが到着しました。To ヘッダーに指定されたアドレスをリッスンしているエンドポイントはありません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-232">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="60c8f-233">`Action` ヘッダーに指定されたアクションは、エンドポイントに関連付けられたインフラストラクチャ チャネルまたはディスパッチャーによって認識されません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-233">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="60c8f-234">R3412: WCF は WS-Addressing 1.0 で定義されている次の障害を生成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-234">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="60c8f-235">コード</span><span class="sxs-lookup"><span data-stu-id="60c8f-235">Code</span></span> | <span data-ttu-id="60c8f-236">原因</span><span class="sxs-lookup"><span data-stu-id="60c8f-236">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="60c8f-237">`wsa:To`、 `wsa:ReplyTo` 、またはが重複して `wsa:From` `wsa:MessageID` います。</span><span class="sxs-lookup"><span data-stu-id="60c8f-237">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="60c8f-238">`wsa:RelatesTo`同じを使用して重複 `RelationshipType` しています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-238">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="60c8f-239">必須の Addressing ヘッダーがありません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-239">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="60c8f-240">このチャネル用に確立された応答アドレスとは異なる `ReplyTo` を使用してメッセージが到着しました。</span><span class="sxs-lookup"><span data-stu-id="60c8f-240">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="60c8f-241">To ヘッダーに指定されたアドレスをリッスンしているエンドポイントはありません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-241">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="60c8f-242">`Action` ヘッダーに指定されたアクションは、エンドポイントに関連付けられたインフラストラクチャ チャネルまたはディスパッチャーによって認識されません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-242">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="60c8f-243">RM チャネルは、`CreateSequence` メッセージのアドレス指定ヘッダーの検査に基づいて、エンドポイントでシーケンスが処理されないことを示すために、このエラーを返しました。</span><span class="sxs-lookup"><span data-stu-id="60c8f-243">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="60c8f-244">上記の 2 つの表に示すコードは、SOAP 1.1 の `FaultCode`、および SOAP 1.2 の `SubCode` (Code=Sender) に対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-244">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="60c8f-245">WSDL 1.1 バインディングと WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="60c8f-245">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="60c8f-246">WS-Addressing の使用の提示</span><span class="sxs-lookup"><span data-stu-id="60c8f-246">Indicating Use of WS-Addressing</span></span>

<span data-ttu-id="60c8f-247">WCF では、ポリシーアサーションを使用して、特定の WS-Addressing バージョンのエンドポイントサポートを示します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-247">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="60c8f-248">次のポリシー アサーションには、エンドポイント ポリシー サブジェクト [WS-PA] が含まれており、そのエンドポイントで送受信されるメッセージでは WS-Addressing 2004/08 を使用する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-248">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="60c8f-249">このポリシー アサーションは、WS-Addressing 2004/08 仕様を補うものです。</span><span class="sxs-lookup"><span data-stu-id="60c8f-249">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="60c8f-250">次のポリシー アサーションは、送受信されるメッセージでは WS-Addressing 1.0 を使用する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-250">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="60c8f-251">次のポリシー アサーションには、エンドポイント ポリシー サブジェクト [WS-PA] が含まれており、そのエンドポイントで送受信されるメッセージでは WS-Addressing 2004/08 を使用する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-251">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="60c8f-252">`wsaw10:UsingAddressing` 要素は、WS-Addressing-WSDL から借用したものです。この要素は、この仕様のセクション 3.1.2 に従って、WS-Policy のコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-252">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="60c8f-253">Addressing を使用しても、WSDL 1.1、SOAP 1.1、および SOAP 1.2 HTTP バインディングのセマンティクスが変更されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-253">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="60c8f-254">たとえば、Addressing と WSDL SOAP 1.x HTTP バインディングを使用するエンドポイントに送信する要求に対して応答が求められている場合、この応答は HTTP 応答を使用して送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-254">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="60c8f-255">HTTP 応答を使用して送信された応答の場合、WS-AM アサーションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-255">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="60c8f-256">完全なポリシー アサーションは次のようになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-256">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="60c8f-257">ただし、リクエスターとレスポンダー間で 2 つの独立した逆方向の HTTP 接続を確立することによってメリットのあるメッセージ交換パターンがあります。たとえば、レスポンダーによって送信される要求されていない一方向のメッセージなどです。</span><span class="sxs-lookup"><span data-stu-id="60c8f-257">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="60c8f-258">WCF には、2つの基になるトランスポートチャネルが複合二重チャネルを形成する機能が用意されています。このチャネルでは、1つのチャネルが入力メッセージに使用され、もう1つは出力メッセージに使用されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-258">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="60c8f-259">HTTP トランスポートの場合、複合二重によって 2 つの逆方向の HTTP 接続が実現します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-259">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="60c8f-260">一方の接続はリクエスターがレスポンダーにメッセージを送信するために使用し、もう一方はレスポンダーがリクエスターにメッセージを返すために使用します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-260">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="60c8f-261">個別の HTTP 要求を使用して送信された応答の場合、WS-AM アサーションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-261">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="60c8f-262">完全なポリシー アサーションは次のようになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-262">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="60c8f-263">WSDL 1.1 SOAP 1.x HTTP バインディングを使用するエンドポイントで、エンドポイント ポリシー サブジェクト [WS-PA] を含む次のアサーションを使用する場合、リクエスターからレスポンダーおよびレスポンダーからリクエスターへのメッセージ フローにそれぞれ別の逆方向の HTTP 接続を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-263">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="60c8f-264">上記のステートメントにより、要求メッセージの `wsa:ReplyTo` ヘッダーに関する以下の要件が発生します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-264">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="60c8f-265">R3514: エンドポイントが `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` WSDL 1.1 SOAP 1.x HTTP バインディングを使用していて、 `wsap10:UsingAddressing` または `wsap:UsingAddressing` アサーションが添付と結合されたポリシー代替がある場合 `cdp:CompositeDuplex` 、エンドポイントに送信される要求メッセージには、プロパティがと等しくないヘッダーが必要です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-265">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="60c8f-266">R3515: エンドポイントに送信される要求メッセージには、プロパティがであるヘッダーが必要です `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` 。また、 `ReplyTo` エンドポイントが WSDL 1.1 SOAP 1.x HTTP バインディングを使用していて、アサーションと `wsap10:UsingAddressing` アサーションが関連付けられていないポリシーがある場合は、ヘッダーをまったく含んでいない必要があり `cdp:CompositeDuplex` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-266">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="60c8f-267">R3516: エンドポイントが `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` WSDL 1.1 SOAP 1.x HTTP バインディングを使用していて、アサーションが適用されていないポリシーがある場合、エンドポイントに送信される要求メッセージには、と等しいプロパティを持つヘッダーが必要 `wsap:UsingAddressing` `cdp:CompositeDuplex` です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-267">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="60c8f-268">WS-Addressing の WSDL 仕様では、`<wsaw:Anonymous/>` ヘッダーの要件を示す 3 つのテキスト値 (required、optional、および prohibited) を持つ `wsa:ReplyTo` 要素を導入することにより、同様のプロトコル バインディングを記述することを試みています (セクション 3.2)。</span><span class="sxs-lookup"><span data-stu-id="60c8f-268">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="60c8f-269">残念ながら、このような要素の定義では、要素をアサーションとして使用する代替手段の共通部分をサポートするために、ドメイン固有の拡張を必要とするため、特に WS-Policy のコンテキストではアサーションとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-269">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="60c8f-270">また、このような要素の定義は、ネットワーク上のエンドポイントの動作に相反する `ReplyTo` ヘッダーの値を示すため、HTTP トランスポートに固有のものになります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-270">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="60c8f-271">アクション定義</span><span class="sxs-lookup"><span data-stu-id="60c8f-271">Action Definition</span></span>

<span data-ttu-id="60c8f-272">WS-Addressing 2004/08 では、`wsa:Action` 要素の `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` 属性が定義されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-272">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="60c8f-273">WS-Addressing 1.0 WSDL バインディング (WS-ADDR10-WSDL) では、同様の属性として `wsaw10:Action` が定義されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-273">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="60c8f-274">この 2 つの属性の唯一の違いは、既定の Action パターンのセマンティクスです。これは、WS-ADDR のセクション 3.3.2 および WS-ADDR10-WSDL のセクション 4.4.4 にそれぞれ記載されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-274">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="60c8f-275">2つのエンドポイントを、同じ `portType` (または WCF の用語ではコントラクト) を共有しながら、異なるバージョンの ws-addressing を使用するのが妥当です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-275">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="60c8f-276">しかし、Action は `portType` によって定義され、`portType` を実装するエンドポイント間で変更できないことを考えると、両方の既定のアクション パターンをサポートすることは不可能になります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-276">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="60c8f-277">この論争を解決するために、WCF では属性の1つのバージョンがサポートされてい `Action` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-277">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="60c8f-278">B3521: WCF は、 `wsaw10:Action` `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` ws-addr10-wsdl で定義されている要素の属性を使用して、 `Action` エンドポイントで使用される WS-Addressing のバージョンに関係なく、対応するメッセージの URI を特定します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-278">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="60c8f-279">WSDL ポート内でのエンドポイント参照の使用</span><span class="sxs-lookup"><span data-stu-id="60c8f-279">Use Endpoint Reference Inside WSDL Port</span></span>

<span data-ttu-id="60c8f-280">WS-ADDR10-WSDL のセクション 4.1 では、`wsdl:port` 要素を拡張して、WS-Addressing の観点でエンドポイントを記述する `<wsa10:EndpointReference…/>` 子要素を含めています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-280">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="60c8f-281">WCF は WS-Addressing 2004/08 でこのユーティリティを拡張し、 `<wsa:EndpointReference…/>` をの子要素として表示できるように `wsdl:port` します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-281">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="60c8f-282">R3531 : エンドポイントが `<wsaw10:UsingAddressing/>` ポリシー アサーションに関連付けられたポリシー代替手段を持つ場合、対応する `wsdl:port` 要素に `<wsa10:EndpointReference …/>` 子要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-282">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="60c8f-283">R3532: に `wsdl:port` 子要素が含まれている場合 `<wsa10:EndpointReference …/>` 、 `wsa10:EndpointReference/wsa10:Address` 子要素の値は、 `@address` 兄弟要素の属性の値と一致する必要があり `wsdl:port` / `wsdl:location` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-283">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="60c8f-284">R3533 : エンドポイントが `<wsap:UsingAddressing/>` ポリシー アサーションに関連付けられたポリシー代替手段を持つ場合、対応する `wsdl:port` 要素に `<wsa:EndpointReference …/>` 子要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-284">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="60c8f-285">R3534: に `wsdl:port` 子要素が含まれている場合 `<wsa:EndpointReference …/>` 、 `wsa:EndpointReference/wsa:Address` 子要素の値は、 `@address` 兄弟要素の属性の値と一致する必要があり `wsdl:port` / `wsdl:location` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-285">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="60c8f-286">WS-Security によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="60c8f-286">Composition with WS-Security</span></span>

<span data-ttu-id="60c8f-287">WS-ADDR および WS-ADDR10 のセキュリティに関する考慮事項のセクションに従って、メッセージ本文と共にすべてのアドレス指定メッセージ ヘッダーに署名し、これらをバインドすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-287">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="60c8f-288">メッセージの整合性を保護するために WS-Security を使用する場合は、メッセージの本文と共に、WS-Addressing メッセージ ヘッダーと、参照パラメーターまたは参照プロパティ (または両方) によって生成されたヘッダーに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-288">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="60c8f-289">例</span><span class="sxs-lookup"><span data-stu-id="60c8f-289">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="60c8f-290">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="60c8f-290">One-Way Message</span></span>

<span data-ttu-id="60c8f-291">このシナリオでは、送信者は一方向のメッセージを受信者に送信します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-291">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="60c8f-292">SOAP 1.2、HTTP 1.1、および W3C WS-Addressing 1.0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-292">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="60c8f-293">要求メッセージの構造 : メッセージ ヘッダーには、`wsa10:To` 要素と `wsa10:Action` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-293">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="60c8f-294">メッセージ本文には、アプリケーション名前空間の特定の `<app:Ping>` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-294">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="60c8f-295">HTTP ヘッダー: POST の送信先は、要素内の URI と一致し `wsa10:To` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-295">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="60c8f-296">Content-Type ヘッダーには、SOAP 1.2 で必要とされる値 `application/soap+xml` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-296">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="60c8f-297">また、`charset` パラメーターと `action` パラメーターも含まれます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-297">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="60c8f-298">Content-Type ヘッダーの `action` パラメーターは、`wsa10:Action` メッセージ ヘッダーの値に一致します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-298">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```http
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

<span data-ttu-id="60c8f-299">受信側は、空の HTTP 応答と 202 ステータスで応答します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-299">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="60c8f-300">HTTP 応答の一例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-300">An example of the HTTP response:</span></span>

```http
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="60c8f-301">SOAP Message Transmission Optimization Mechanism</span><span class="sxs-lookup"><span data-stu-id="60c8f-301">SOAP Message Transmission Optimization Mechanism</span></span>

<span data-ttu-id="60c8f-302">ここでは、HTTP SOAP MTOM の WCF 実装の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-302">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="60c8f-303">MTOM テクノロジは、従来の text/XML エンコーディングまたは WCF バイナリエンコードと同じクラスの SOAP メッセージエンコーディング機構です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-303">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="60c8f-304">MTOM には、次のような機能があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-304">MTOM includes the following:</span></span>

- <span data-ttu-id="60c8f-305">XOP によって記述された XML エンコーディングおよびパッケージング機構。XOP は、Base64 で個別のバイナリ部分にエンコードされたバイナリ データを含む XML 情報項目を最適化します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-305">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="60c8f-306">XML Infoset と XOP パッケージの各バイナリ部分を個別の MIME パートにシリアル化する、XOP パッケージの MIME カプセル化。</span><span class="sxs-lookup"><span data-stu-id="60c8f-306">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="60c8f-307">SOAP 1.x エンベロープに適用される MIME XOP エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="60c8f-307">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="60c8f-308">HTTP トランスポート バインディング。</span><span class="sxs-lookup"><span data-stu-id="60c8f-308">An HTTP transport binding.</span></span>

<span data-ttu-id="60c8f-309">WCF では、HTTP 以外のトランスポートで MTOM を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-309">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="60c8f-310">しかし、ここでは HTTP に焦点を合わせます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-310">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="60c8f-311">MTOM 形式では、MTOM 自体、XOP、および MIME に適用されるさまざまな仕様を利用します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-311">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="60c8f-312">この仕様セットのモジュール性により、形式と処理のセマンティクスの要件を正確に再構築することが若干難しくなります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-312">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="60c8f-313">このセクションでは、MTOM HTTP バインディングの形式と処理の要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-313">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="60c8f-314">MTOM メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="60c8f-314">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="60c8f-315">MTOM メッセージの生成</span><span class="sxs-lookup"><span data-stu-id="60c8f-315">Generating MTOM messages</span></span>

<span data-ttu-id="60c8f-316">XOP のセクション 3.1 には、Base64 値を抽象的に定義された XOP パッケージに格納する要素情報項目を使用して、XML をエンコーディングするプロセスが記載されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-316">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="60c8f-317">次の一連の手順は、MTOM 固有のエンコーディング プロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-317">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="60c8f-318">エンコードされる SOAP エンベロープに、とのを持つ要素情報項目が含まれていないことを確認し `[namespace name]` `http://www.w3.org/2004/08/xop/include` `[local name]` `Include` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-318">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="60c8f-319">空の MIME パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-319">Create an empty MIME package.</span></span>

3. <span data-ttu-id="60c8f-320">元の XML Infoset 内で、最適化する要素情報項目を特定します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-320">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="60c8f-321">最適化する項目については、要素情報項目のを構成する文字は、 `[children]` の正規の形式 `xs:base64Binary` (「XSD-2, xsd-2 セクション 3.2.16 base64Binary」を参照) にする必要があります。また、空白以外のコンテンツの前、インライン、またはその後に続く空白文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-321">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="60c8f-322">元の SOAP エンベロープのコピーである XOP SOAP エンベロープを作成します。ただし、このコピーには、前の手順で特定した各要素情報項目の子が含まれます。これらの子は、以下の手順に従って構築された `xop:Include` 要素情報項目に置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-322">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="60c8f-323">置換対象の文字を Base64 でエンコードされたデータとして処理することにより、バイナリ データに変換します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-323">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="60c8f-324">R3133 および R3134 の各要件を満たす Content-ID ヘッダーの一意の値を生成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-324">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="60c8f-325">バイナリ値を使用して、Content-Transfer-Encoding MIME ヘッダーを生成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-325">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="60c8f-326">最適化する要素情報項目 (新しく挿入する `xop:Include` 要素情報項目の [parent]) に、`xmime:contentType` 属性情報項目が含まれている場合、`xmime:contentType` 属性の値を使用して Content-Type MIME ヘッダーを生成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-326">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="60c8f-327">Base64 として処理された置換対象文字からデコードされたバイナリ データ、Content-ID ヘッダー (手順 4b. で生成)、Content- Transfer-Encoding ヘッダー (手順 4c. で生成)、および Content-Type ヘッダー (手順 4d. で生成した場合) で構成されたコンテンツを含む、新しいバイナリ MIME パートを生成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-327">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="60c8f-328">値 cid: uri を持つ `href` 要素に `xop:Include` 属性を追加します。uri は、手順 4b. で生成した Content-ID ヘッダーの値から派生したものです。</span><span class="sxs-lookup"><span data-stu-id="60c8f-328">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="60c8f-329">囲んでいる " \<" and "> " 文字を削除し、残りの文字列を URL エスケープして、プレフィックスを追加し `cid:` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-329">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="60c8f-330">RFC1738 と RFC2396 に従って、次の最小限の文字セットをエスケープする必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-330">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="60c8f-331">その他の文字もエスケープすることができます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-331">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="60c8f-332">手順 4. の XOP SOAP エンベロープを含むルート MIME パートを作成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-332">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="60c8f-333">HTTP Content-Type ヘッダーなどの HTTP ヘッダーを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-333">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="60c8f-334">MIME パッケージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-334">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="60c8f-335">MTOM メッセージの処理</span><span class="sxs-lookup"><span data-stu-id="60c8f-335">Processing MTOM messages</span></span>

<span data-ttu-id="60c8f-336">MTOM メッセージの処理は、前述の「MTOM メッセージの生成」で説明したプロセスと正反対のプロセスになります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-336">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="60c8f-337">ルート MIME パートに Content-Type `application/xop+xml` が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-337">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="60c8f-338">パッケージのルート MIME パートを XML ドキュメントとして解析して、SOAP エンベロープを作成します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-338">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="60c8f-339">文字エンコーディングは、ルート MIME パートの Content-Type の `charset` パラメーターによって決まります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-339">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="60c8f-340">作成した SOAP エンベロープ内の各要素情報項目について、以下の処理を行います。これらの要素情報項目には、[children] プロパティの唯一のメンバーとして、`xop:Include` 要素情報項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-340">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="60c8f-341">プレフィックス `cid:` を削除し、`@href` 要素の `xop:Include` 属性の値に含まれるすべての URI エスケープ シーケンスのエスケープを解除します (RFC 2396)。</span><span class="sxs-lookup"><span data-stu-id="60c8f-341">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="60c8f-342">結果の文字列を "" に囲み \<", "> ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-342">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="60c8f-343">Content-ID ヘッダーの値が手順 3a. で取得した文字列に一致する MIME パートを検索します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-343">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="60c8f-344">各項目の `xop:Include` プロパティに出現する `children` 要素情報項目を、手順 3b. で特定した MIME パートのエンティティ本体の正規 Base64 エンコーディング (XSD-2 セクション 3.2.16 の base64Binary を参照) を表す文字情報項目に置き換えます (`xop:Include` 要素情報項目をパッケージ パーツから再構築したデータに効率的に置き換えます)。</span><span class="sxs-lookup"><span data-stu-id="60c8f-344">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="60c8f-345">HTTP Content-Type ヘッダー</span><span class="sxs-lookup"><span data-stu-id="60c8f-345">HTTP Content-Type Header</span></span>

<span data-ttu-id="60c8f-346">次に示すのは、SOAP 1.x の MTOM でエンコードされたメッセージの HTTP Content-type ヘッダーの形式に関する WCF の説明です。 MTOM 仕様に記載されている要件から派生したものであり、MTOM と RFC 2387 から派生します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-346">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="60c8f-347">R4131 : HTTP Content-Type ヘッダーには、multipart/related (大文字と小文字は区別されません) とそのパラメーターの値が必要です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-347">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="60c8f-348">パラメーター名では、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-348">Parameter names are case-insensitive.</span></span> <span data-ttu-id="60c8f-349">パラメーターの順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="60c8f-349">Parameter order is not significant.</span></span>

- <span data-ttu-id="60c8f-350">MIME メッセージの Content-Type ヘッダーのすべての Backus-Naur Form (BNF) については、RFC 2045 のセクション 5.1 に記載されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-350">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="60c8f-351">R4132 : HTTP Content-Type ヘッダーには、二重引用符で囲まれた値 `application/xop+xml` が指定された型パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-351">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="60c8f-352">RFC 2387 では二重引用符を使用するための要件が明示されていませんが、テキストは、すべてのマルチパート/関連メディアの種類のパラメーターに "" や "/" などの予約文字が含まれている可能性がある \@ ため、二重引用符が必要です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-352">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="60c8f-353">R4133 : HTTP Content-Type ヘッダーには、start パラメーターを含める必要があります。このパラメーターには、SOAP 1.x エンベロープを含む MIME パートの Content-ID ヘッダーの値を二重引用符で囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-353">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="60c8f-354">start パラメーターを省略する場合は、最初の MIME パートに SOAP 1.x エンベロープを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-354">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="60c8f-355">R4134 : SOAP 1.1 MTOM でエンコードされたメッセージの HTTP Content-Type ヘッダーには、start-info パラメーターを含める必要があります。このパラメーターには、値 text/xml を二重引用符で囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-355">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="60c8f-356">R4135 : SOAP 1.2 MTOM でエンコードされたメッセージの HTTP Content-Type ヘッダーには、start-info パラメーターを含める必要があります。このパラメーターには、値 `application/soap+xml` を二重引用符で囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-356">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="60c8f-357">R4136 : SOAP 1.x MTOM でエンコードされたメッセージの HTTP Content-Type ヘッダーには、boundary パラメーターを含める必要があります。このパラメーターには、RFC 2046 のセクション 5.1.1 で定義された MIME 境界の BNF に一致する (二重引用符で囲まれた) 値を指定します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-357">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="60c8f-358">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-358">Examples:</span></span>

     <span data-ttu-id="60c8f-359">正</span><span class="sxs-lookup"><span data-stu-id="60c8f-359">CORRECT</span></span>

    ```http
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="60c8f-360">正</span><span class="sxs-lookup"><span data-stu-id="60c8f-360">CORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="60c8f-361">誤</span><span class="sxs-lookup"><span data-stu-id="60c8f-361">INCORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="60c8f-362">Infoset MIME パート</span><span class="sxs-lookup"><span data-stu-id="60c8f-362">Infoset MIME Part</span></span>

<span data-ttu-id="60c8f-363">SOAP 1.x エンベロープは、XOP MIME パッケージのルート部分としてカプセル化され、多くの場合、`infoset` パートと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-363">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="60c8f-364">R4141 : SOAP 1.x エンベロープは、XOP MIME パッケージのルート部分としてカプセル化する必要があります。これは `infoset` パートと呼ばれ、HTTP Content-Type から参照されます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-364">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="60c8f-365">R4142 : SOAP `Infoset` パートには、`Content-ID`、`Content-Transfer-Encoding`、および `Content-Type` の各 MIME ヘッダーを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-365">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="60c8f-366">Content-ID ヘッダーの形式は、RFC 2045 で次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-366">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="60c8f-367">ここで、`msg-id` は、RFC 2822 で次のように定義されています (RFC 2045 で参照されている RFC 822 は、RFC 2822 に置き換えられています)。</span><span class="sxs-lookup"><span data-stu-id="60c8f-367">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="60c8f-368">とは、事実上 "" で囲まれた電子メールアドレスです \<" and  "> 。</span><span class="sxs-lookup"><span data-stu-id="60c8f-368">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="60c8f-369">`[CFWS]` プレフィックスとサフィックスは、コメントを伝達するために RFC 2822 で追加されたものですが、相互運用性を維持する場合は、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-369">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="60c8f-370">R4143 : Infoset MIME パートの Content-ID ヘッダーの値は、RFC 2822 の `msg-id` の定義内容から `[CFWS]` プレフィックスとサフィックスの部分を省略した形式に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-370">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="60c8f-371">多くの MIME 実装では、"" 内に囲まれた値が \<" and "> 電子メールアドレスであり、 `absoluteURI` \<" , "> 電子メールアドレスに加えて "" で囲まれて使用されるように要件が緩和されています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-371">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="60c8f-372">このバージョンの WCF では、次の形式の Content-type MIME ヘッダーの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-372">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="60c8f-373">R4144 : MTOM プロセッサは、次の厳密でない `msg-id` に一致する Content-ID ヘッダーの値を受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-373">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="60c8f-374">MIME (RFC 2045) では、MIME パートのコンテンツのエンコーディングを伝達する Content-Transfer-Encoding ヘッダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-374">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="60c8f-375">Content-Transfer-Encoding に定義されている既定値は 7 ビットですが、これはほとんどの SOAP メッセージに適していません。そのため、Content-Transfer-Encoding ヘッダーの相互運用性を高めるために、以下を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-375">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="60c8f-376">R4145 : SOAP Infoset パートに、Content-Transfer-Encoding ヘッダーを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-376">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="60c8f-377">R4146 : SOAP エンベロープの文字エンコーディングが UTF-8 の場合、Content-Transfer-Encoding ヘッダーの値は 8 ビットであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-377">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="60c8f-378">R4147 : SOAP エンベロープの文字エンコーディングが UTF-16 の場合、Content-Transfer-Encoding ヘッダーの値はバイナリであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-378">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="60c8f-379">以下の要件は、XOP のセクション 5 に基づいています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-379">According to [XOP] section 5,</span></span>

- <span data-ttu-id="60c8f-380">R4148: SOAP 1.1 Infoset パートには、media type application/xop + xml と parameters type = "text/xml" および charset の Content-type ヘッダーが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-380">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="60c8f-381">R4149: SOAP 1.2 Infoset パーツには、メディアの種類がで、パラメーターの種類が "" である Content-type ヘッダーが含まれている必要があり `application/xop+xml` `application/soap+xml` `charset` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-381">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="60c8f-382">XOP では、`charset` の `application/xop+xml` パラメーターは省略可能と定義されていますが、`charset` メディア タイプの `text/xml` パラメーターについては、BP 1.1 の要件と同様の相互運用性が必要とされます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-382">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="60c8f-383">R41410 : `type` パラメーターと `charset` パラメーターは、SOAP 1.x Infoset パートの Content-Type ヘッダーに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="60c8f-383">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="60c8f-384">WCF エンドポイントによる MTOM のサポート</span><span class="sxs-lookup"><span data-stu-id="60c8f-384">WCF Endpoint Support for MTOM</span></span>

<span data-ttu-id="60c8f-385">MTOM の目的は、SOAP メッセージをエンコードして、Base64 でエンコードされたデータを最適化することです。</span><span class="sxs-lookup"><span data-stu-id="60c8f-385">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="60c8f-386">制約は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="60c8f-386">The following is a list of constraints:</span></span>

- <span data-ttu-id="60c8f-387">R4151 : Base64 でエンコードされたデータを含むすべての要素情報項目を最適化できます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-387">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="60c8f-388">B4152: WCF は、base64 でエンコードされたデータを含み、長さが1024バイトを超える要素情報項目を最適化します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-388">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="60c8f-389">MTOM を使用するように構成された WCF エンドポイントは、常に MTOM でエンコードされたメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-389">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="60c8f-390">必要な条件を満たすパートがない場合でも、メッセージは MTOM でエンコードされます (SOAP エンベロープを含む単一の MIME パートを持つ MIME パッケージとしてシリアル化されます)。</span><span class="sxs-lookup"><span data-stu-id="60c8f-390">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="60c8f-391">MTOM の WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="60c8f-391">WS-Policy Assertion for MTOM</span></span>

<span data-ttu-id="60c8f-392">WCF では、次のポリシーアサーションを使用して、エンドポイントによる MTOM の使用状況を示します。</span><span class="sxs-lookup"><span data-stu-id="60c8f-392">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="60c8f-393">R4211 : 上記のポリシー アサーションには、エンドポイント ポリシー サブジェクトが含まれており、MTOM を使用して、エンドポイントで送受信されるすべてのメッセージを最適化する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="60c8f-393">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="60c8f-394">B4212: MTOM の最適化を使用するように構成されている場合、WCF エンドポイントは、対応するに関連付けられているポリシーに MTOM ポリシーアサーションを追加し `wsdl:binding` ます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-394">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="60c8f-395">WS-Security によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="60c8f-395">Composition with WS-Security</span></span>

<span data-ttu-id="60c8f-396">MTOM は `text/xml` 、および WCF バイナリ XML に似たエンコーディング機構です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-396">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="60c8f-397">MTOM は、WS-Security とその他の WS-\* プロトコルによる自然なコンポジションを提供します。WS-Security を使用してセキュリティ保護されたメッセージは、MTOM を使用して最適化できます。</span><span class="sxs-lookup"><span data-stu-id="60c8f-397">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="60c8f-398">例</span><span class="sxs-lookup"><span data-stu-id="60c8f-398">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="60c8f-399">MTOM を使用してエンコードされた WCF SOAP 1.1 メッセージ</span><span class="sxs-lookup"><span data-stu-id="60c8f-399">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```http
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="60c8f-400">MTOM を使用してエンコードされた WCF Secure SOAP 1.2 メッセージ</span><span class="sxs-lookup"><span data-stu-id="60c8f-400">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>

<span data-ttu-id="60c8f-401">この例では、WS-Security を使用して保護されたメッセージを MTOM と SOAP 1.2 を使用してエンコードします。</span><span class="sxs-lookup"><span data-stu-id="60c8f-401">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="60c8f-402">エンコーディングの対象として特定されたバイナリ部分は、`BinarySecurityToken`、暗号化された署名に対応する `CipherValue` の `EncryptedData`、および暗号化された本文の内容です。</span><span class="sxs-lookup"><span data-stu-id="60c8f-402">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="60c8f-403">のは、その `CipherValue` `EncryptedKey` 長さが1024バイト未満であるため、WCF による最適化のためにのが識別されなかったことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="60c8f-403">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```http
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml";
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```
