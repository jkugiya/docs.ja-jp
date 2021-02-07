---
description: '詳細情報: <filterTables>'
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 932d0e162c3fdeba8b166d3adaaa73cc3b5293a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664588"
---
# \<filterTables>

<span data-ttu-id="080ec-102">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納するルーティング テーブルを定義する構成セクションを表します。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="080ec-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="080ec-103">構文</span><span class="sxs-lookup"><span data-stu-id="080ec-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="080ec-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="080ec-104">Attributes and Elements</span></span>  

 <span data-ttu-id="080ec-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="080ec-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="080ec-106">属性</span><span class="sxs-lookup"><span data-stu-id="080ec-106">Attributes</span></span>  

 <span data-ttu-id="080ec-107">なし。</span><span class="sxs-lookup"><span data-stu-id="080ec-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="080ec-108">子要素</span><span class="sxs-lookup"><span data-stu-id="080ec-108">Child Elements</span></span>  
  
|<span data-ttu-id="080ec-109">要素</span><span class="sxs-lookup"><span data-stu-id="080ec-109">Element</span></span>|<span data-ttu-id="080ec-110">説明</span><span class="sxs-lookup"><span data-stu-id="080ec-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="080ec-111">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納するルーティング テーブル。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="080ec-111">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="080ec-112">親要素</span><span class="sxs-lookup"><span data-stu-id="080ec-112">Parent Elements</span></span>  
  
|<span data-ttu-id="080ec-113">要素</span><span class="sxs-lookup"><span data-stu-id="080ec-113">Element</span></span>|<span data-ttu-id="080ec-114">説明</span><span class="sxs-lookup"><span data-stu-id="080ec-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="080ec-115">ルーティング フィルターおよびルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="080ec-115">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="080ec-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="080ec-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
