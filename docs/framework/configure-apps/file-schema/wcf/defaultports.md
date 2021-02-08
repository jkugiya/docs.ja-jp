---
description: '詳細情報: <defaultPorts>'
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 7cd0635568bf80734900f5e54f918150ea657322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803907"
---
# \<defaultPorts>

<span data-ttu-id="26e63-102">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="26e63-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="26e63-103">構文</span><span class="sxs-lookup"><span data-stu-id="26e63-103">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26e63-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="26e63-104">Attributes and Elements</span></span>  

 <span data-ttu-id="26e63-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="26e63-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26e63-106">属性</span><span class="sxs-lookup"><span data-stu-id="26e63-106">Attributes</span></span>  

 <span data-ttu-id="26e63-107">なし。</span><span class="sxs-lookup"><span data-stu-id="26e63-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="26e63-108">子要素</span><span class="sxs-lookup"><span data-stu-id="26e63-108">Child Elements</span></span>  
  
|<span data-ttu-id="26e63-109">要素</span><span class="sxs-lookup"><span data-stu-id="26e63-109">Element</span></span>|<span data-ttu-id="26e63-110">説明</span><span class="sxs-lookup"><span data-stu-id="26e63-110">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26e63-111">\<defaultPorts> の \<add></span><span class="sxs-lookup"><span data-stu-id="26e63-111">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="26e63-112">クライアント アプリケーションがリッスンする既定の通信エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26e63-112">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26e63-113">親要素</span><span class="sxs-lookup"><span data-stu-id="26e63-113">Parent Elements</span></span>  
  
|<span data-ttu-id="26e63-114">要素</span><span class="sxs-lookup"><span data-stu-id="26e63-114">Element</span></span>|<span data-ttu-id="26e63-115">説明</span><span class="sxs-lookup"><span data-stu-id="26e63-115">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="26e63-116">既定のポートの一覧。</span><span class="sxs-lookup"><span data-stu-id="26e63-116">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26e63-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="26e63-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
