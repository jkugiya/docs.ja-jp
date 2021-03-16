---
description: '詳細情報: <useRequestHeadersForMetadataAddress>'
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 53636b5890eb54095737e2ed62a75e9b81c1c1f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664432"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="8dab3-102">メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8dab3-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="8dab3-103">構文</span><span class="sxs-lookup"><span data-stu-id="8dab3-103">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dab3-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8dab3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8dab3-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dab3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dab3-106">属性</span><span class="sxs-lookup"><span data-stu-id="8dab3-106">Attributes</span></span>  

 <span data-ttu-id="8dab3-107">なし。</span><span class="sxs-lookup"><span data-stu-id="8dab3-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8dab3-108">子要素</span><span class="sxs-lookup"><span data-stu-id="8dab3-108">Child Elements</span></span>  
  
|<span data-ttu-id="8dab3-109">要素</span><span class="sxs-lookup"><span data-stu-id="8dab3-109">Element</span></span>|<span data-ttu-id="8dab3-110">説明</span><span class="sxs-lookup"><span data-stu-id="8dab3-110">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="8dab3-111">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="8dab3-111">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dab3-112">親要素</span><span class="sxs-lookup"><span data-stu-id="8dab3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8dab3-113">要素</span><span class="sxs-lookup"><span data-stu-id="8dab3-113">Element</span></span>|<span data-ttu-id="8dab3-114">説明</span><span class="sxs-lookup"><span data-stu-id="8dab3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8dab3-115">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="8dab3-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dab3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8dab3-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
