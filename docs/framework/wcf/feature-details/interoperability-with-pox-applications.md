---
description: '詳細情報: POX アプリケーションとの相互運用性'
title: POX アプリケーションとの相互運用性
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 832b9ae93f6046ca9995b57bdcbbfbfeb46d2a09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802711"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="c1aff-103">POX アプリケーションとの相互運用性</span><span class="sxs-lookup"><span data-stu-id="c1aff-103">Interoperability with POX applications</span></span>

<span data-ttu-id="c1aff-104">"Plain Old XML" (POX) アプリケーションは、SOAP エンベロープで囲まれていない XML アプリケーションデータのみを含む未加工の HTTP メッセージを交換することによって通信します。</span><span class="sxs-lookup"><span data-stu-id="c1aff-104">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="c1aff-105">Windows Communication Foundation (WCF) では、POX メッセージを使用するサービスとクライアントの両方を提供できます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-105">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="c1aff-106">サービスでは、WCF を使用して、Web ブラウザーや、POX メッセージを送受信するスクリプト言語などのクライアントにエンドポイントを公開するサービスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-106">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="c1aff-107">クライアントでは、WCF プログラミングモデルを使用して、POX ベースのサービスと通信するクライアントを実装できます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-107">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1aff-108">このドキュメントは、もともと .NET Framework 3.0 用に書かれています。</span><span class="sxs-lookup"><span data-stu-id="c1aff-108">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="c1aff-109">.NET Framework 3.5 には、POX アプリケーションを操作するためのサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="c1aff-109">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="c1aff-110">の詳細については、「 [WCF WEB HTTP プログラミングモデル](wcf-web-http-programming-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1aff-110">For more information about see [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="c1aff-111">WCF を使用した POX プログラミング</span><span class="sxs-lookup"><span data-stu-id="c1aff-111">POX programming with WCF</span></span>

<span data-ttu-id="c1aff-112">POX メッセージを使用して HTTP で通信する WCF サービスでは、を使用し [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-112">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="c1aff-113">このカスタム バインドには、次の 2 つの要素があります。</span><span class="sxs-lookup"><span data-stu-id="c1aff-113">This custom binding contains two elements:</span></span>

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="c1aff-114">標準の WCF テキストメッセージエンコーダーは、値を使用するように特別に構成されています。これに <xref:System.ServiceModel.Channels.MessageVersion.None%2A> より、SOAP エンベロープにラップされていない XML メッセージペイロードを処理できます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-114">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="c1aff-115">POX メッセージを使用して HTTP で通信する WCF クライアントは、同様のバインディングを使用します (次の命令型コードを参照)。</span><span class="sxs-lookup"><span data-stu-id="c1aff-115">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="c1aff-116">POX クライアントでは、メッセージの送信先となる URI を明示的に指定する必要があるため、クライアントの <xref:System.ServiceModel.Channels.HttpTransportBindingElement> プロパティを <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> に設定することで、通常、`true` を手動アドレス指定モードに構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1aff-116">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="c1aff-117">これにより、アプリケーション コードによってメッセージのアドレスが明示的に指定されることになり、アプリケーションで異なる HTTP URI にメッセージを送信するたびに、新しい <xref:System.ServiceModel.ChannelFactory> を作成する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c1aff-117">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="c1aff-118">POX メッセージでは重要なプロトコル情報の搬送に SOAP ヘッダーを使用しないため、POX クライアントおよびサービスでは、メッセージの送受信に使用される、基になる HTTP 要求の情報を操作する必要が生じる場合がよく起こります。</span><span class="sxs-lookup"><span data-stu-id="c1aff-118">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="c1aff-119">HTTP ヘッダーや状態コードなどの HTTP 固有のプロトコル情報は、次の2つのクラスを通じて WCF プログラミングモデルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-119">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="c1aff-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty> には、HTTP メソッドと要求ヘッダーなど、HTTP 要求についての情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="c1aff-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty> には、HTTP ステータス コード、ステータスの説明、および任意の HTTP 応答ヘッダーなど、HTTP 応答についての情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="c1aff-122">に対応する HTTP GET 要求メッセージを作成する方法を次のコード例に示し `http://localhost:8100/customers` ます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-122">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="c1aff-123">初めに、<xref:System.ServiceModel.Channels.Message> を呼び出すことで、空の <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> 要求を作成します。</span><span class="sxs-lookup"><span data-stu-id="c1aff-123">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="c1aff-124"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> パラメーターを使用して SOAP エンベロープが不要であることを示し、<xref:System.String.Empty> パラメーターをアクションとして渡します。</span><span class="sxs-lookup"><span data-stu-id="c1aff-124">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="c1aff-125">次に、<xref:System.ServiceModel.Channels.MessageHeaders.To%2A> を目的の URI に設定することで、要求メッセージをアドレス指定します。</span><span class="sxs-lookup"><span data-stu-id="c1aff-125">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="c1aff-126">さらに、<xref:System.ServiceModel.Channels.HttpRequestMessageProperty> を作成し、<xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> を HTTP 動詞の GET メソッドに設定し、また <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> を `true` に設定して、送信 HTTP 要求メッセージの本文でデータが送信されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c1aff-126">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="c1aff-127">最後に、要求プロパティを要求メッセージの <xref:System.ServiceModel.Channels.Message.Properties%2A> コレクションに追加して、HTTP トランスポートによる要求の送信方法に影響を与えることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="c1aff-127">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="c1aff-128">これで <xref:System.ServiceModel.Channels.IRequestChannel> の適切なインスタンスを使用してメッセージを送信する用意が整いました。</span><span class="sxs-lookup"><span data-stu-id="c1aff-128">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="c1aff-129">サービスにおいても、受信メッセージから <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> を抽出して応答を構築する際に同様のテクニックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1aff-129">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
