---
description: '詳細情報: <webSocketSettings>'
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: a0b67a0088491c73ed0214191283ae5292a654b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682489"
---
# \<webSocketSettings>

<span data-ttu-id="d3ee0-102">Web ソケット設定を指定するために使用される構成要素。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-102">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="d3ee0-103">構文</span><span class="sxs-lookup"><span data-stu-id="d3ee0-103">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3ee0-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d3ee0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d3ee0-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3ee0-106">属性</span><span class="sxs-lookup"><span data-stu-id="d3ee0-106">Attributes</span></span>  
  
|<span data-ttu-id="d3ee0-107">属性</span><span class="sxs-lookup"><span data-stu-id="d3ee0-107">Attribute</span></span>|<span data-ttu-id="d3ee0-108">説明</span><span class="sxs-lookup"><span data-stu-id="d3ee0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3ee0-109">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="d3ee0-109">createNotificationOnConnection</span></span>|<span data-ttu-id="d3ee0-110">通知を接続時に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-110">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="d3ee0-111">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="d3ee0-111">disablePayloadMasking</span></span>|<span data-ttu-id="d3ee0-112">Web ソケットのマスクが無効であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-112">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="d3ee0-113">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="d3ee0-113">keepAliveInterval</span></span>|<span data-ttu-id="d3ee0-114">接続維持の間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-114">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="d3ee0-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="d3ee0-115">maxPendingConnections</span></span>|<span data-ttu-id="d3ee0-116">サービスでのディスパッチを待機している接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-116">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="d3ee0-117">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="d3ee0-117">receiveBufferSize</span></span>|<span data-ttu-id="d3ee0-118">受信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-118">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="d3ee0-119">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="d3ee0-119">sendBufferSize</span></span>|<span data-ttu-id="d3ee0-120">送信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-120">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="d3ee0-121">subProtocol</span><span class="sxs-lookup"><span data-stu-id="d3ee0-121">subProtocol</span></span>|<span data-ttu-id="d3ee0-122">Web ソケットのサブプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-122">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="d3ee0-123">transportUsage</span><span class="sxs-lookup"><span data-stu-id="d3ee0-123">transportUsage</span></span>|<span data-ttu-id="d3ee0-124">Web ソケットを使用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-124">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="d3ee0-125">transportUsage 属性</span><span class="sxs-lookup"><span data-stu-id="d3ee0-125">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="d3ee0-126">値</span><span class="sxs-lookup"><span data-stu-id="d3ee0-126">Value</span></span>|<span data-ttu-id="d3ee0-127">説明</span><span class="sxs-lookup"><span data-stu-id="d3ee0-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3ee0-128">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="d3ee0-128">WhenDuplex</span></span>|<span data-ttu-id="d3ee0-129">コントラクトが双方向の場合に、Web ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-129">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="d3ee0-130">Always</span><span class="sxs-lookup"><span data-stu-id="d3ee0-130">Always</span></span>|<span data-ttu-id="d3ee0-131">コントラクトにかかわらず、常にWeb ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-131">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="d3ee0-132">行わない</span><span class="sxs-lookup"><span data-stu-id="d3ee0-132">Never</span></span>|<span data-ttu-id="d3ee0-133">Web ソケット プロトコルを使用しません。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-133">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3ee0-134">子要素</span><span class="sxs-lookup"><span data-stu-id="d3ee0-134">Child Elements</span></span>  

 <span data-ttu-id="d3ee0-135">なし</span><span class="sxs-lookup"><span data-stu-id="d3ee0-135">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3ee0-136">親要素</span><span class="sxs-lookup"><span data-stu-id="d3ee0-136">Parent Elements</span></span>  
  
|<span data-ttu-id="d3ee0-137">要素</span><span class="sxs-lookup"><span data-stu-id="d3ee0-137">Element</span></span>|<span data-ttu-id="d3ee0-138">説明</span><span class="sxs-lookup"><span data-stu-id="d3ee0-138">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="d3ee0-139">NetHttpBinding を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-139">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d3ee0-140">例</span><span class="sxs-lookup"><span data-stu-id="d3ee0-140">Example</span></span>  

 <span data-ttu-id="d3ee0-141">\<webSocketSettings> 要素を使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d3ee0-141">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="d3ee0-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3ee0-142">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="d3ee0-143">バインド</span><span class="sxs-lookup"><span data-stu-id="d3ee0-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d3ee0-144">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="d3ee0-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d3ee0-145">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="d3ee0-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
