---
description: '詳細情報: <remove> の要素 <namedCaches>'
title: <namedCaches> の <remove> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 5b39fc596735d746c52cdb5623962f5b9952fa3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802463"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="9a6b1-103">\<namedCaches> の \<remove> 要素</span><span class="sxs-lookup"><span data-stu-id="9a6b1-103">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="9a6b1-104">名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="9a6b1-104">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="9a6b1-105">構文</span><span class="sxs-lookup"><span data-stu-id="9a6b1-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="9a6b1-106">Type</span><span class="sxs-lookup"><span data-stu-id="9a6b1-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a6b1-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9a6b1-107">Attributes and Elements</span></span>  

 <span data-ttu-id="9a6b1-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a6b1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a6b1-109">属性</span><span class="sxs-lookup"><span data-stu-id="9a6b1-109">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="9a6b1-110">子要素</span><span class="sxs-lookup"><span data-stu-id="9a6b1-110">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="9a6b1-111">親要素</span><span class="sxs-lookup"><span data-stu-id="9a6b1-111">Parent Elements</span></span>  
  
|<span data-ttu-id="9a6b1-112">要素</span><span class="sxs-lookup"><span data-stu-id="9a6b1-112">Element</span></span>|<span data-ttu-id="9a6b1-113">説明</span><span class="sxs-lookup"><span data-stu-id="9a6b1-113">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="9a6b1-114">名前付きインスタンスの構成設定のコレクションを格納 <xref:System.Runtime.Caching.MemoryCache> します。</span><span class="sxs-lookup"><span data-stu-id="9a6b1-114">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a6b1-115">解説</span><span class="sxs-lookup"><span data-stu-id="9a6b1-115">Remarks</span></span>  

 <span data-ttu-id="9a6b1-116">要素は、 `remove` `namedCache` メモリキャッシュの名前付きキャッシュコレクションからエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="9a6b1-116">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6b1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a6b1-117">See also</span></span>

- [<span data-ttu-id="9a6b1-118">\<namedCaches> 要素 (キャッシュ設定)</span><span class="sxs-lookup"><span data-stu-id="9a6b1-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
