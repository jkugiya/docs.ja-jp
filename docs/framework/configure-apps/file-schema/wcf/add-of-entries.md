---
description: 詳細については <add> 、 <entries>
title: <add> の <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 0be24fb9d2327d411368dd05afc21156dfaf3d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803972"
---
# <a name="add-of-entries"></a><span data-ttu-id="b99a3-103">\<add> の \<entries></span><span class="sxs-lookup"><span data-stu-id="b99a3-103">\<add> of \<entries></span></span>

<span data-ttu-id="b99a3-104">以前に定義されたクライアント エンドポイントにフィルターをマップするルーティング エントリを表します。</span><span class="sxs-lookup"><span data-stu-id="b99a3-104">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="b99a3-105">このフィルターに一致するメッセージは、この宛先に送信されます。</span><span class="sxs-lookup"><span data-stu-id="b99a3-105">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b99a3-106">構文</span><span class="sxs-lookup"><span data-stu-id="b99a3-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b99a3-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b99a3-107">Attributes and Elements</span></span>  

 <span data-ttu-id="b99a3-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b99a3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b99a3-109">属性</span><span class="sxs-lookup"><span data-stu-id="b99a3-109">Attributes</span></span>  
  
|<span data-ttu-id="b99a3-110">属性</span><span class="sxs-lookup"><span data-stu-id="b99a3-110">Attribute</span></span>|<span data-ttu-id="b99a3-111">説明</span><span class="sxs-lookup"><span data-stu-id="b99a3-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b99a3-112">backupList</span><span class="sxs-lookup"><span data-stu-id="b99a3-112">backupList</span></span>|<span data-ttu-id="b99a3-113">エンドポイントのバックアップ リストへの参照を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b99a3-113">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="b99a3-114">endpoint</span><span class="sxs-lookup"><span data-stu-id="b99a3-114">endpoint</span></span>|<span data-ttu-id="b99a3-115">`filterName` 属性で指定されたフィルターに一致するメッセージを受信するクライアント エンドポイントへの参照を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b99a3-115">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="b99a3-116">filterName</span><span class="sxs-lookup"><span data-stu-id="b99a3-116">filterName</span></span>|<span data-ttu-id="b99a3-117">フィルター要素への参照を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b99a3-117">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="b99a3-118">priority</span><span class="sxs-lookup"><span data-stu-id="b99a3-118">priority</span></span>|<span data-ttu-id="b99a3-119">このエントリの優先順位を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="b99a3-119">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="b99a3-120">ルーティング テーブルのエントリは、優先順位に基づいて評価されます。0 が最下位の優先順位です。</span><span class="sxs-lookup"><span data-stu-id="b99a3-120">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="b99a3-121">特定の優先順位について、すべてのエントリが同時に評価されます。現在の優先順位について一致するエントリが見つからない場合は、次の優先順位が評価されます。</span><span class="sxs-lookup"><span data-stu-id="b99a3-121">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="b99a3-122">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b99a3-122">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b99a3-123">子要素</span><span class="sxs-lookup"><span data-stu-id="b99a3-123">Child Elements</span></span>  

 <span data-ttu-id="b99a3-124">なし。</span><span class="sxs-lookup"><span data-stu-id="b99a3-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b99a3-125">親要素</span><span class="sxs-lookup"><span data-stu-id="b99a3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b99a3-126">要素</span><span class="sxs-lookup"><span data-stu-id="b99a3-126">Element</span></span>|<span data-ttu-id="b99a3-127">説明</span><span class="sxs-lookup"><span data-stu-id="b99a3-127">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="b99a3-128">ルーティング マッピング エントリを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="b99a3-128">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b99a3-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="b99a3-129">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
