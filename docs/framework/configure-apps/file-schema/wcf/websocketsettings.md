---
description: '詳細情報: <webSocketSettings>'
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: a0b67a0088491c73ed0214191283ae5292a654b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682489"
---
# \<webSocketSettings>

<span data-ttu-id="24f39-102">Web ソケット設定を指定するために使用される構成要素。</span><span class="sxs-lookup"><span data-stu-id="24f39-102">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="24f39-103">構文</span><span class="sxs-lookup"><span data-stu-id="24f39-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24f39-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="24f39-104">Attributes and Elements</span></span>  

 <span data-ttu-id="24f39-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="24f39-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24f39-106">属性</span><span class="sxs-lookup"><span data-stu-id="24f39-106">Attributes</span></span>  
  
|<span data-ttu-id="24f39-107">属性</span><span class="sxs-lookup"><span data-stu-id="24f39-107">Attribute</span></span>|<span data-ttu-id="24f39-108">説明</span><span class="sxs-lookup"><span data-stu-id="24f39-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24f39-109">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="24f39-109">createNotificationOnConnection</span></span>|<span data-ttu-id="24f39-110">通知を接続時に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-110">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="24f39-111">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="24f39-111">disablePayloadMasking</span></span>|<span data-ttu-id="24f39-112">Web ソケットのマスクが無効であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-112">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="24f39-113">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="24f39-113">keepAliveInterval</span></span>|<span data-ttu-id="24f39-114">接続維持の間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-114">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="24f39-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="24f39-115">maxPendingConnections</span></span>|<span data-ttu-id="24f39-116">サービスでのディスパッチを待機している接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-116">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="24f39-117">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="24f39-117">receiveBufferSize</span></span>|<span data-ttu-id="24f39-118">受信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-118">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="24f39-119">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="24f39-119">sendBufferSize</span></span>|<span data-ttu-id="24f39-120">送信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-120">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="24f39-121">subProtocol</span><span class="sxs-lookup"><span data-stu-id="24f39-121">subProtocol</span></span>|<span data-ttu-id="24f39-122">Web ソケットのサブプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-122">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="24f39-123">transportUsage</span><span class="sxs-lookup"><span data-stu-id="24f39-123">transportUsage</span></span>|<span data-ttu-id="24f39-124">Web ソケットを使用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-124">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="24f39-125">transportUsage 属性</span><span class="sxs-lookup"><span data-stu-id="24f39-125">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="24f39-126">[値]</span><span class="sxs-lookup"><span data-stu-id="24f39-126">Value</span></span>|<span data-ttu-id="24f39-127">説明</span><span class="sxs-lookup"><span data-stu-id="24f39-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24f39-128">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="24f39-128">WhenDuplex</span></span>|<span data-ttu-id="24f39-129">コントラクトが双方向の場合に、Web ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="24f39-129">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="24f39-130">常時</span><span class="sxs-lookup"><span data-stu-id="24f39-130">Always</span></span>|<span data-ttu-id="24f39-131">コントラクトにかかわらず、常にWeb ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="24f39-131">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="24f39-132">行わない</span><span class="sxs-lookup"><span data-stu-id="24f39-132">Never</span></span>|<span data-ttu-id="24f39-133">Web ソケット プロトコルを使用しません。</span><span class="sxs-lookup"><span data-stu-id="24f39-133">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24f39-134">子要素</span><span class="sxs-lookup"><span data-stu-id="24f39-134">Child Elements</span></span>  

 <span data-ttu-id="24f39-135">なし</span><span class="sxs-lookup"><span data-stu-id="24f39-135">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24f39-136">親要素</span><span class="sxs-lookup"><span data-stu-id="24f39-136">Parent Elements</span></span>  
  
|<span data-ttu-id="24f39-137">要素</span><span class="sxs-lookup"><span data-stu-id="24f39-137">Element</span></span>|<span data-ttu-id="24f39-138">説明</span><span class="sxs-lookup"><span data-stu-id="24f39-138">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="24f39-139">NetHttpBinding を指定します。</span><span class="sxs-lookup"><span data-stu-id="24f39-139">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24f39-140">例</span><span class="sxs-lookup"><span data-stu-id="24f39-140">Example</span></span>  

 <span data-ttu-id="24f39-141">\<webSocketSettings> 要素を使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="24f39-141">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24f39-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="24f39-142">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="24f39-143">バインド</span><span class="sxs-lookup"><span data-stu-id="24f39-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="24f39-144">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="24f39-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="24f39-145">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="24f39-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
