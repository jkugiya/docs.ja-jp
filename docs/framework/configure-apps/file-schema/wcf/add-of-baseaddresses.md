---
description: 詳細については <add> 、 <baseAddresses>
title: <add> の <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: b25a4b5551784ecd8e67569c82c1388a144a9c9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804063"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="2894e-103">\<add> の \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="2894e-103">\<add> of \<baseAddresses></span></span>

<span data-ttu-id="2894e-104">サービス ホストによって使用されるベース アドレスを指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="2894e-104">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="2894e-105">構文</span><span class="sxs-lookup"><span data-stu-id="2894e-105">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="2894e-106">Type</span><span class="sxs-lookup"><span data-stu-id="2894e-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2894e-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2894e-107">Attributes and Elements</span></span>  

 <span data-ttu-id="2894e-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2894e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2894e-109">属性</span><span class="sxs-lookup"><span data-stu-id="2894e-109">Attributes</span></span>  
  
|<span data-ttu-id="2894e-110">属性</span><span class="sxs-lookup"><span data-stu-id="2894e-110">Attribute</span></span>|<span data-ttu-id="2894e-111">説明</span><span class="sxs-lookup"><span data-stu-id="2894e-111">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="2894e-112">サービス ホストによって使用されるベース アドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2894e-112">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2894e-113">子要素</span><span class="sxs-lookup"><span data-stu-id="2894e-113">Child Elements</span></span>  

 <span data-ttu-id="2894e-114">なし。</span><span class="sxs-lookup"><span data-stu-id="2894e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2894e-115">親要素</span><span class="sxs-lookup"><span data-stu-id="2894e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2894e-116">要素</span><span class="sxs-lookup"><span data-stu-id="2894e-116">Element</span></span>|<span data-ttu-id="2894e-117">説明</span><span class="sxs-lookup"><span data-stu-id="2894e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="2894e-118">`baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="2894e-118">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2894e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2894e-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="2894e-120">ホスティング</span><span class="sxs-lookup"><span data-stu-id="2894e-120">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
