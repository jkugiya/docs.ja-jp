---
description: '詳細情報: <baseAddresses>'
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: a32afc23d4332bad149765a318c3ecdc73f99be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749689"
---
# \<baseAddresses>

<span data-ttu-id="70f29-102">自己ホスト環境でのサービス ホストのベース アドレスである `baseAddress` 要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="70f29-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="70f29-103">ベース アドレスが存在すると、そのベース アドレスに関連したアドレスを使用してエンドポイントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="70f29-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="70f29-104">構文</span><span class="sxs-lookup"><span data-stu-id="70f29-104">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="70f29-105">種類</span><span class="sxs-lookup"><span data-stu-id="70f29-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70f29-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="70f29-106">Attributes and Elements</span></span>  

 <span data-ttu-id="70f29-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="70f29-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70f29-108">属性</span><span class="sxs-lookup"><span data-stu-id="70f29-108">Attributes</span></span>  

 <span data-ttu-id="70f29-109">なし。</span><span class="sxs-lookup"><span data-stu-id="70f29-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70f29-110">子要素</span><span class="sxs-lookup"><span data-stu-id="70f29-110">Child Elements</span></span>  
  
|<span data-ttu-id="70f29-111">要素</span><span class="sxs-lookup"><span data-stu-id="70f29-111">Element</span></span>|<span data-ttu-id="70f29-112">説明</span><span class="sxs-lookup"><span data-stu-id="70f29-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="70f29-113">サービス ホストによって使用されるベース アドレスを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="70f29-113">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70f29-114">親要素</span><span class="sxs-lookup"><span data-stu-id="70f29-114">Parent Elements</span></span>  
  
|<span data-ttu-id="70f29-115">要素</span><span class="sxs-lookup"><span data-stu-id="70f29-115">Element</span></span>|<span data-ttu-id="70f29-116">説明</span><span class="sxs-lookup"><span data-stu-id="70f29-116">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="70f29-117">サービス ホストの設定を指定する構成要素です。</span><span class="sxs-lookup"><span data-stu-id="70f29-117">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70f29-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="70f29-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="70f29-119">ホスティング</span><span class="sxs-lookup"><span data-stu-id="70f29-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
