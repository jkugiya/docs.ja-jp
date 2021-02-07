---
description: '詳細情報: <serviceDiscovery>'
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: d6df5b8d51763429829c2ea3c2593003720b7179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682853"
---
# \<serviceDiscovery>

<span data-ttu-id="76d86-102">サービス エンドポイントの探索可能性を指定します。</span><span class="sxs-lookup"><span data-stu-id="76d86-102">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="76d86-103">構文</span><span class="sxs-lookup"><span data-stu-id="76d86-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76d86-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="76d86-104">Attributes and Elements</span></span>  

 <span data-ttu-id="76d86-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="76d86-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76d86-106">属性</span><span class="sxs-lookup"><span data-stu-id="76d86-106">Attributes</span></span>  

 <span data-ttu-id="76d86-107">なし。</span><span class="sxs-lookup"><span data-stu-id="76d86-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76d86-108">子要素</span><span class="sxs-lookup"><span data-stu-id="76d86-108">Child Elements</span></span>  
  
|<span data-ttu-id="76d86-109">要素</span><span class="sxs-lookup"><span data-stu-id="76d86-109">Element</span></span>|<span data-ttu-id="76d86-110">説明</span><span class="sxs-lookup"><span data-stu-id="76d86-110">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="76d86-111">アナウンス エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="76d86-111">A collection of announcement endpoints.</span></span> <span data-ttu-id="76d86-112">このセクションを使用して、アナウンス メッセージの送信に使用するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="76d86-112">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="76d86-113">探索エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="76d86-113">A collection of discovery endpoints.</span></span> <span data-ttu-id="76d86-114">このセクションを使用して、探索メッセージをリッスンするエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="76d86-114">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76d86-115">親要素</span><span class="sxs-lookup"><span data-stu-id="76d86-115">Parent Elements</span></span>  
  
|<span data-ttu-id="76d86-116">要素</span><span class="sxs-lookup"><span data-stu-id="76d86-116">Element</span></span>|<span data-ttu-id="76d86-117">説明</span><span class="sxs-lookup"><span data-stu-id="76d86-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="76d86-118">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="76d86-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76d86-119">解説</span><span class="sxs-lookup"><span data-stu-id="76d86-119">Remarks</span></span>  

 <span data-ttu-id="76d86-120">サービスの動作構成に追加すると、この構成要素により、サービスの探索可能性はすべてのエンドポイントで有効になります。</span><span class="sxs-lookup"><span data-stu-id="76d86-120">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="76d86-121">または子要素を使用して、このようなエンドポイントの探索機能をさらに構成でき [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) ます。</span><span class="sxs-lookup"><span data-stu-id="76d86-121">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="76d86-122">[\<announcementEndpoint>](announcementendpoint.md)サービスのお知らせを送信するために使用するエンドポイント構成 (オンライン/Hello およびオフライン/Bye) を指定することにより、セクションを使用してアナウンスを構成します。</span><span class="sxs-lookup"><span data-stu-id="76d86-122">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="76d86-123">[\<discoveryEndpoint>](discoveryendpoint.md)探索メッセージをリッスンするエンドポイントを手動で指定するには、「」セクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="76d86-123">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76d86-124">例</span><span class="sxs-lookup"><span data-stu-id="76d86-124">Example</span></span>  

 <span data-ttu-id="76d86-125">次の構成例では、CalculatorService を探索可能に指定しています。また、オプションで、使用するアナウンス エンドポイントを指定しています。</span><span class="sxs-lookup"><span data-stu-id="76d86-125">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="76d86-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="76d86-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
