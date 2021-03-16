---
description: '詳細情報: <oneWay>'
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 8e3314dd14525b5f7585a7336c00b615da56d1c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683841"
---
# \<oneWay>

<span data-ttu-id="67625-102">カスタム バインドのパケット ルーティングを有効にし、一方向メソッドを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="67625-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="67625-103">構文</span><span class="sxs-lookup"><span data-stu-id="67625-103">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67625-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="67625-104">Attributes and Elements</span></span>  

 <span data-ttu-id="67625-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="67625-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67625-106">属性</span><span class="sxs-lookup"><span data-stu-id="67625-106">Attributes</span></span>  
  
|<span data-ttu-id="67625-107">属性</span><span class="sxs-lookup"><span data-stu-id="67625-107">Attribute</span></span>|<span data-ttu-id="67625-108">説明</span><span class="sxs-lookup"><span data-stu-id="67625-108">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="67625-109">パケット ルーティングが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="67625-109">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="67625-110">既定では、 `false`です。</span><span class="sxs-lookup"><span data-stu-id="67625-110">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="67625-111">許容できるチャネルの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="67625-111">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67625-112">子要素</span><span class="sxs-lookup"><span data-stu-id="67625-112">Child Elements</span></span>  
  
|<span data-ttu-id="67625-113">要素</span><span class="sxs-lookup"><span data-stu-id="67625-113">Element</span></span>|<span data-ttu-id="67625-114">説明</span><span class="sxs-lookup"><span data-stu-id="67625-114">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="67625-115">現在のチャネルのチャネル プールのプロパティを格納する <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="67625-115">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67625-116">親要素</span><span class="sxs-lookup"><span data-stu-id="67625-116">Parent Elements</span></span>  
  
|<span data-ttu-id="67625-117">要素</span><span class="sxs-lookup"><span data-stu-id="67625-117">Element</span></span>|<span data-ttu-id="67625-118">説明</span><span class="sxs-lookup"><span data-stu-id="67625-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="67625-119">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="67625-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67625-120">解説</span><span class="sxs-lookup"><span data-stu-id="67625-120">Remarks</span></span>  

 <span data-ttu-id="67625-121">パケット ルーティングを有効にするには、この要素が提供する "一方向の変換" 層が必要です。</span><span class="sxs-lookup"><span data-stu-id="67625-121">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="67625-122">カスタム バインドを作成し、このバインディングをセッション対応または要求応答のトランスポートの上に重ねて、パケット ルーティング可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="67625-122">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="67625-123">この要素は、一方向メソッドをよりネイティブな形式で公開するときにも役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="67625-123">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="67625-124">複合二重や信頼できるメッセージ機能などのさらに大きい変換は、この層に対して適用できます。</span><span class="sxs-lookup"><span data-stu-id="67625-124">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67625-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="67625-125">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="67625-126">バインド</span><span class="sxs-lookup"><span data-stu-id="67625-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="67625-127">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="67625-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="67625-128">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="67625-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
