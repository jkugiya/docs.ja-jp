---
description: 詳細については <add> 、 <backupList>
title: <add> の <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 9855d93be011b4eaa2890c4d24392fde3b65d05a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804076"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="ef896-103">\<add> の \<backupList></span><span class="sxs-lookup"><span data-stu-id="ef896-103">\<add> of \<backupList></span></span>

<span data-ttu-id="ef896-104">バックアップ エンドポイント要素を定義する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="ef896-104">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ef896-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef896-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef896-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ef896-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ef896-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef896-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef896-108">属性</span><span class="sxs-lookup"><span data-stu-id="ef896-108">Attributes</span></span>  
  
|<span data-ttu-id="ef896-109">属性</span><span class="sxs-lookup"><span data-stu-id="ef896-109">Attribute</span></span>|<span data-ttu-id="ef896-110">説明</span><span class="sxs-lookup"><span data-stu-id="ef896-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef896-111">name</span><span class="sxs-lookup"><span data-stu-id="ef896-111">name</span></span>|<span data-ttu-id="ef896-112">バックアップ エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="ef896-112">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef896-113">子要素</span><span class="sxs-lookup"><span data-stu-id="ef896-113">Child Elements</span></span>  

 <span data-ttu-id="ef896-114">なし。</span><span class="sxs-lookup"><span data-stu-id="ef896-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef896-115">親要素</span><span class="sxs-lookup"><span data-stu-id="ef896-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ef896-116">要素</span><span class="sxs-lookup"><span data-stu-id="ef896-116">Element</span></span>|<span data-ttu-id="ef896-117">説明</span><span class="sxs-lookup"><span data-stu-id="ef896-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="ef896-118">プライマリ エンドポイントに接続できないときにルーティング サービスが使用するエンドポイントのリストを格納します。</span><span class="sxs-lookup"><span data-stu-id="ef896-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef896-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef896-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
