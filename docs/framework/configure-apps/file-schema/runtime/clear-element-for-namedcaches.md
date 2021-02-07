---
description: '詳細情報: <clear> の要素 <namedCaches>'
title: <namedCaches> の <clear> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: 9d883c102fc76875ce155f353920f730bf9700c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719098"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="76ad5-103">\<namedCaches> の \<clear> 要素</span><span class="sxs-lookup"><span data-stu-id="76ad5-103">\<clear> Element for \<namedCaches></span></span>

<span data-ttu-id="76ad5-104">`namedCache`メモリキャッシュのコレクション内のすべてのエントリをクリア `namedCaches` します。</span><span class="sxs-lookup"><span data-stu-id="76ad5-104">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="76ad5-105">構文</span><span class="sxs-lookup"><span data-stu-id="76ad5-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="76ad5-106">Type</span><span class="sxs-lookup"><span data-stu-id="76ad5-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76ad5-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="76ad5-107">Attributes and Elements</span></span>  

 <span data-ttu-id="76ad5-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="76ad5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76ad5-109">属性</span><span class="sxs-lookup"><span data-stu-id="76ad5-109">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="76ad5-110">子要素</span><span class="sxs-lookup"><span data-stu-id="76ad5-110">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="76ad5-111">親要素</span><span class="sxs-lookup"><span data-stu-id="76ad5-111">Parent Elements</span></span>  
  
|<span data-ttu-id="76ad5-112">要素</span><span class="sxs-lookup"><span data-stu-id="76ad5-112">Element</span></span>|<span data-ttu-id="76ad5-113">説明</span><span class="sxs-lookup"><span data-stu-id="76ad5-113">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="76ad5-114">名前付きインスタンスの構成設定のコレクションを格納 <xref:System.Runtime.Caching.MemoryCache> します。</span><span class="sxs-lookup"><span data-stu-id="76ad5-114">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76ad5-115">解説</span><span class="sxs-lookup"><span data-stu-id="76ad5-115">Remarks</span></span>  

 <span data-ttu-id="76ad5-116">要素は、 `clear` `namedCache` メモリキャッシュの名前付きキャッシュコレクション内のすべてのエントリをクリアします。</span><span class="sxs-lookup"><span data-stu-id="76ad5-116">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="76ad5-117">要素を使用して、 `clear` `add` コレクション内に他の名前付きキャッシュが存在しないことを特定するために、要素を使用して新しい名前付きキャッシュエントリを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="76ad5-117">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ad5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="76ad5-118">See also</span></span>

- [<span data-ttu-id="76ad5-119">\<namedCaches> 要素 (キャッシュ設定)</span><span class="sxs-lookup"><span data-stu-id="76ad5-119">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
