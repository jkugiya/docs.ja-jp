---
description: '詳細情報: <entries>'
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: e5aefce4328c341b6d132765c8e726910241aae1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782105"
---
# \<entries>

<span data-ttu-id="5dc9e-102">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納するルーティング エントリ。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5dc9e-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="5dc9e-103">構文</span><span class="sxs-lookup"><span data-stu-id="5dc9e-103">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dc9e-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5dc9e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5dc9e-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5dc9e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dc9e-106">属性</span><span class="sxs-lookup"><span data-stu-id="5dc9e-106">Attributes</span></span>  

 <span data-ttu-id="5dc9e-107">なし。</span><span class="sxs-lookup"><span data-stu-id="5dc9e-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5dc9e-108">子要素</span><span class="sxs-lookup"><span data-stu-id="5dc9e-108">Child Elements</span></span>  
  
|<span data-ttu-id="5dc9e-109">要素</span><span class="sxs-lookup"><span data-stu-id="5dc9e-109">Element</span></span>|<span data-ttu-id="5dc9e-110">説明</span><span class="sxs-lookup"><span data-stu-id="5dc9e-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="5dc9e-111">以前に定義されたクライアント エンドポイントにフィルターをマップします。</span><span class="sxs-lookup"><span data-stu-id="5dc9e-111">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="5dc9e-112">このフィルターに一致するメッセージは、この宛先に送信されます。</span><span class="sxs-lookup"><span data-stu-id="5dc9e-112">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5dc9e-113">親要素</span><span class="sxs-lookup"><span data-stu-id="5dc9e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5dc9e-114">要素</span><span class="sxs-lookup"><span data-stu-id="5dc9e-114">Element</span></span>|<span data-ttu-id="5dc9e-115">説明</span><span class="sxs-lookup"><span data-stu-id="5dc9e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="5dc9e-116">ルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="5dc9e-116">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5dc9e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dc9e-117">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
