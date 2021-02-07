---
description: '詳細情報: <udpBinding>'
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 33f8f6abaebe24364273ab43e7ef9ade39a969b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749221"
---
# \<udpBinding>

<span data-ttu-id="6b01f-102"><xref:System.ServiceModel.UdpBinding> バインディングの構成に使用する構成要素です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="6b01f-103">構文</span><span class="sxs-lookup"><span data-stu-id="6b01f-103">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b01f-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6b01f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6b01f-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b01f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b01f-106">属性</span><span class="sxs-lookup"><span data-stu-id="6b01f-106">Attributes</span></span>  
  
|<span data-ttu-id="6b01f-107">属性</span><span class="sxs-lookup"><span data-stu-id="6b01f-107">Attribute</span></span>|<span data-ttu-id="6b01f-108">説明</span><span class="sxs-lookup"><span data-stu-id="6b01f-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6b01f-109">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="6b01f-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6b01f-110">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b01f-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b01f-111">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-111">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="6b01f-112">重複するメッセージの履歴の長さを指定する整数値。</span><span class="sxs-lookup"><span data-stu-id="6b01f-112">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="6b01f-113">チャネルからメッセージを受け取るメッセージ バッファーのマネージャーが使用するために割り当てられる、最大メモリ量を指定する整数値。</span><span class="sxs-lookup"><span data-stu-id="6b01f-113">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="6b01f-114">既定値は 524288 (0x80000) バイトです。</span><span class="sxs-lookup"><span data-stu-id="6b01f-114">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="6b01f-115">このバインディングで構成されるエンドポイントのメッセージが処理されるときのメッセージを格納するバッファーの最大サイズを指定する整数値 (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6b01f-115">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="6b01f-116">既定値は 65,536 バイトです。</span><span class="sxs-lookup"><span data-stu-id="6b01f-116">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="6b01f-117">受信して、各チャネル インスタンスの入力キューからまだ削除していないメッセージの最大数を指定する整数値。</span><span class="sxs-lookup"><span data-stu-id="6b01f-117">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="6b01f-118">このバインディングで構成されるチャネルが受信可能なメッセージの最大メッセージ サイズ (ヘッダーを含む) をバイト単位で定義する正の整数。</span><span class="sxs-lookup"><span data-stu-id="6b01f-118">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6b01f-119">受信側のメッセージが大きすぎると、送信側は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6b01f-119">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="6b01f-120">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6b01f-120">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6b01f-121">既定値は 65,536 バイトです。</span><span class="sxs-lookup"><span data-stu-id="6b01f-121">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="6b01f-122">再送信メッセージの最大数を指定する整数値。</span><span class="sxs-lookup"><span data-stu-id="6b01f-122">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="6b01f-123">マルチキャストのインターフェイス ID を指定する整数値。</span><span class="sxs-lookup"><span data-stu-id="6b01f-123">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="6b01f-124">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-124">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6b01f-125">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b01f-125">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6b01f-126">.NET Framework 4 以降では、バインドと動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6b01f-126">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6b01f-127">既定の構成と無名のバインドおよび動作の詳細については、「 [WCF サービスの](../../../wcf/samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../../../wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b01f-127">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6b01f-128">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6b01f-129">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b01f-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b01f-130">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-130">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6b01f-131">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6b01f-132">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b01f-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b01f-133">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-133">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6b01f-134">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6b01f-135">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b01f-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b01f-136">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-136">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="6b01f-137">バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="6b01f-137">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6b01f-138">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6b01f-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6b01f-139">-BigEndianUnicode: Unicode BigEndian エンコード。</span><span class="sxs-lookup"><span data-stu-id="6b01f-139">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="6b01f-140">-Unicode:16 ビットエンコード。</span><span class="sxs-lookup"><span data-stu-id="6b01f-140">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="6b01f-141">-UTF8: 8 ビットエンコーディング</span><span class="sxs-lookup"><span data-stu-id="6b01f-141">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="6b01f-142">既定値は UTF8 です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-142">The default is UTF8.</span></span> <span data-ttu-id="6b01f-143">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-143">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="6b01f-144">バインディングに対する有効期間を指定する期間値。</span><span class="sxs-lookup"><span data-stu-id="6b01f-144">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b01f-145">子要素</span><span class="sxs-lookup"><span data-stu-id="6b01f-145">Child Elements</span></span>  
  
|<span data-ttu-id="6b01f-146">要素</span><span class="sxs-lookup"><span data-stu-id="6b01f-146">Element</span></span>|<span data-ttu-id="6b01f-147">説明</span><span class="sxs-lookup"><span data-stu-id="6b01f-147">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="6b01f-148">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="6b01f-148">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6b01f-149">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="6b01f-149">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b01f-150">親要素</span><span class="sxs-lookup"><span data-stu-id="6b01f-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6b01f-151">要素</span><span class="sxs-lookup"><span data-stu-id="6b01f-151">Element</span></span>|<span data-ttu-id="6b01f-152">説明</span><span class="sxs-lookup"><span data-stu-id="6b01f-152">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="6b01f-153">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="6b01f-153">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b01f-154">解説</span><span class="sxs-lookup"><span data-stu-id="6b01f-154">Remarks</span></span>  

 <span data-ttu-id="6b01f-155">UdpBinding により、WCF サービスが UDP トランスポートを介して通信することができます。</span><span class="sxs-lookup"><span data-stu-id="6b01f-155">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="6b01f-156">これにより、クライアントがメッセージをサービスに送信し、応答が返されないというメッセージ交換が可能になります。</span><span class="sxs-lookup"><span data-stu-id="6b01f-156">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b01f-157">例</span><span class="sxs-lookup"><span data-stu-id="6b01f-157">Example</span></span>  

 <span data-ttu-id="6b01f-158">次の例は、<> 要素を使用してを構成する方法を示して <xref:System.ServiceModel.UdpBinding> `udpBinding` います。</span><span class="sxs-lookup"><span data-stu-id="6b01f-158">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="6b01f-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b01f-159">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="6b01f-160">バインド</span><span class="sxs-lookup"><span data-stu-id="6b01f-160">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6b01f-161">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="6b01f-161">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6b01f-162">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="6b01f-162">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
