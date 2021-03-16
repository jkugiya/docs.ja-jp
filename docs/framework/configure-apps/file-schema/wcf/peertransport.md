---
description: '詳細情報: <peerTransport>'
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: babc4196c63d46b7515ac67812d5d584eb3ffcac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683620"
---
# \<peerTransport>

<span data-ttu-id="6983e-102">カスタム バインドのピア トランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="6983e-102">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="6983e-103">構文</span><span class="sxs-lookup"><span data-stu-id="6983e-103">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6983e-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6983e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6983e-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6983e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6983e-106">属性</span><span class="sxs-lookup"><span data-stu-id="6983e-106">Attributes</span></span>  
  
|<span data-ttu-id="6983e-107">属性</span><span class="sxs-lookup"><span data-stu-id="6983e-107">Attribute</span></span>|<span data-ttu-id="6983e-108">説明</span><span class="sxs-lookup"><span data-stu-id="6983e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6983e-109">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="6983e-109">listenIpAddress</span></span>|<span data-ttu-id="6983e-110">ピア ノードが TCP メッセージをリッスンする IP アドレスを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="6983e-110">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="6983e-111">既定では、 `null`です。</span><span class="sxs-lookup"><span data-stu-id="6983e-111">The default is `null`.</span></span>|  
|<span data-ttu-id="6983e-112">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6983e-112">maxBufferPoolSize</span></span>|<span data-ttu-id="6983e-113">バッファー プールの最大サイズを指定する正の整数です。</span><span class="sxs-lookup"><span data-stu-id="6983e-113">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="6983e-114">既定値は 524288 です。</span><span class="sxs-lookup"><span data-stu-id="6983e-114">The default is 524288.</span></span><br /><br /> <span data-ttu-id="6983e-115">WCF の多くの部分でバッファーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6983e-115">Many parts of WCF use buffers.</span></span> <span data-ttu-id="6983e-116">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="6983e-116">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6983e-117">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="6983e-117">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6983e-118">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="6983e-118">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6983e-119">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6983e-119">maxReceivedMessageSize</span></span>|<span data-ttu-id="6983e-120">ヘッダーなどのメッセージの最大サイズ (バイト単位) を定義する正の整数。</span><span class="sxs-lookup"><span data-stu-id="6983e-120">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="6983e-121">受信側にとってメッセージが大きすぎると、メッセージの送信側は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6983e-121">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="6983e-122">メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6983e-122">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6983e-123">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="6983e-123">The default is 65536.</span></span>|  
|<span data-ttu-id="6983e-124">port</span><span class="sxs-lookup"><span data-stu-id="6983e-124">port</span></span>|<span data-ttu-id="6983e-125">このバインディングがピア チャネルの TCP メッセージを処理するネットワーク インターフェイス ポートを指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="6983e-125">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="6983e-126">この値の有効値の範囲は <xref:System.Net.IPEndPoint.MinPort> ～ <xref:System.Net.IPEndPoint.MaxPort> です。</span><span class="sxs-lookup"><span data-stu-id="6983e-126">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="6983e-127">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="6983e-127">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6983e-128">子要素</span><span class="sxs-lookup"><span data-stu-id="6983e-128">Child Elements</span></span>  
  
|<span data-ttu-id="6983e-129">要素</span><span class="sxs-lookup"><span data-stu-id="6983e-129">Element</span></span>|<span data-ttu-id="6983e-130">説明</span><span class="sxs-lookup"><span data-stu-id="6983e-130">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="6983e-131">このトランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6983e-131">Defines the security settings for this transport.</span></span> <span data-ttu-id="6983e-132">この要素は <xref:System.ServiceModel.Configuration.PeerSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="6983e-132">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6983e-133">親要素</span><span class="sxs-lookup"><span data-stu-id="6983e-133">Parent Elements</span></span>  
  
|<span data-ttu-id="6983e-134">要素</span><span class="sxs-lookup"><span data-stu-id="6983e-134">Element</span></span>|<span data-ttu-id="6983e-135">説明</span><span class="sxs-lookup"><span data-stu-id="6983e-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="6983e-136">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="6983e-136">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6983e-137">解説</span><span class="sxs-lookup"><span data-stu-id="6983e-137">Remarks</span></span>  

 <span data-ttu-id="6983e-138">このトランスポートは、要求/応答操作を含むコントラクトと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="6983e-138">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6983e-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="6983e-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6983e-140">トランスポート</span><span class="sxs-lookup"><span data-stu-id="6983e-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="6983e-141">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="6983e-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="6983e-142">バインド</span><span class="sxs-lookup"><span data-stu-id="6983e-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6983e-143">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="6983e-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6983e-144">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="6983e-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
