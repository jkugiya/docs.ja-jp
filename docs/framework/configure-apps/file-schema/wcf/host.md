---
description: '詳細情報: <host>'
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: ff240c85af3aab7c1208a6a49b1943f3c6a8cd99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802282"
---
# \<host>

<span data-ttu-id="993dd-102">サービス ホストの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="993dd-102">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="993dd-103">構文</span><span class="sxs-lookup"><span data-stu-id="993dd-103">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="993dd-104">Type</span><span class="sxs-lookup"><span data-stu-id="993dd-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="993dd-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="993dd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="993dd-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="993dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="993dd-107">属性</span><span class="sxs-lookup"><span data-stu-id="993dd-107">Attributes</span></span>  

 <span data-ttu-id="993dd-108">なし。</span><span class="sxs-lookup"><span data-stu-id="993dd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="993dd-109">子要素</span><span class="sxs-lookup"><span data-stu-id="993dd-109">Child Elements</span></span>  
  
|<span data-ttu-id="993dd-110">要素</span><span class="sxs-lookup"><span data-stu-id="993dd-110">Element</span></span>|<span data-ttu-id="993dd-111">説明</span><span class="sxs-lookup"><span data-stu-id="993dd-111">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="993dd-112">サービス ホストによって使用されるベース アドレスを指定する `baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="993dd-112">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="993dd-113">サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="993dd-113">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="993dd-114">親要素</span><span class="sxs-lookup"><span data-stu-id="993dd-114">Parent Elements</span></span>  
  
|<span data-ttu-id="993dd-115">要素</span><span class="sxs-lookup"><span data-stu-id="993dd-115">Element</span></span>|<span data-ttu-id="993dd-116">説明</span><span class="sxs-lookup"><span data-stu-id="993dd-116">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="993dd-117">Windows Communication Foundation (WCF) サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="993dd-117">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="993dd-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="993dd-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="993dd-119">ホスティング</span><span class="sxs-lookup"><span data-stu-id="993dd-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
