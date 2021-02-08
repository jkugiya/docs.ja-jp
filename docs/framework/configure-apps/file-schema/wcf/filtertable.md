---
description: '詳細情報: <filterTable>'
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 2051bb0e778e5676f39d91b7d7ba415fd7e523af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782040"
---
# \<filterTable>

<span data-ttu-id="c07bd-102">メッセージを評価するフィルターの一覧と、フィルターが true に評価された場合にメッセージをルーティングするクライアント エンドポイントを格納するルーティング テーブルを表します。</span><span class="sxs-lookup"><span data-stu-id="c07bd-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="c07bd-103">構文</span><span class="sxs-lookup"><span data-stu-id="c07bd-103">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c07bd-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c07bd-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c07bd-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c07bd-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c07bd-106">属性</span><span class="sxs-lookup"><span data-stu-id="c07bd-106">Attributes</span></span>  
  
|<span data-ttu-id="c07bd-107">要素</span><span class="sxs-lookup"><span data-stu-id="c07bd-107">Element</span></span>|<span data-ttu-id="c07bd-108">説明</span><span class="sxs-lookup"><span data-stu-id="c07bd-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c07bd-109">name</span><span class="sxs-lookup"><span data-stu-id="c07bd-109">name</span></span>|<span data-ttu-id="c07bd-110">この構成要素の一意の名前を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="c07bd-110">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c07bd-111">子要素</span><span class="sxs-lookup"><span data-stu-id="c07bd-111">Child Elements</span></span>  
  
|<span data-ttu-id="c07bd-112">要素</span><span class="sxs-lookup"><span data-stu-id="c07bd-112">Element</span></span>|<span data-ttu-id="c07bd-113">説明</span><span class="sxs-lookup"><span data-stu-id="c07bd-113">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="c07bd-114">ルーティング フィルターとターゲット エンドポイントとのマッピング。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c07bd-114">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c07bd-115">親要素</span><span class="sxs-lookup"><span data-stu-id="c07bd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c07bd-116">要素</span><span class="sxs-lookup"><span data-stu-id="c07bd-116">Element</span></span>|<span data-ttu-id="c07bd-117">説明</span><span class="sxs-lookup"><span data-stu-id="c07bd-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="c07bd-118">ルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="c07bd-118">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c07bd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c07bd-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
