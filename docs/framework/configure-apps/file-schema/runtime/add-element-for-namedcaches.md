---
description: '詳細情報: <add> の要素 <namedCaches>'
title: <namedCaches> の <add> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 1485b80fa84268f68759bfb50744133744142d72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802425"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="d111c-103">\<namedCaches> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="d111c-103">\<add> Element for \<namedCaches></span></span>

<span data-ttu-id="d111c-104">`namedCache`メモリキャッシュのコレクションにエントリを追加し `namedCaches` ます。</span><span class="sxs-lookup"><span data-stu-id="d111c-104">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d111c-105">構文</span><span class="sxs-lookup"><span data-stu-id="d111c-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="d111c-106">Type</span><span class="sxs-lookup"><span data-stu-id="d111c-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d111c-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d111c-107">Attributes and Elements</span></span>  

 <span data-ttu-id="d111c-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d111c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d111c-109">属性</span><span class="sxs-lookup"><span data-stu-id="d111c-109">Attributes</span></span>  
  
|<span data-ttu-id="d111c-110">属性</span><span class="sxs-lookup"><span data-stu-id="d111c-110">Attribute</span></span>|<span data-ttu-id="d111c-111">説明</span><span class="sxs-lookup"><span data-stu-id="d111c-111">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="d111c-112">のインスタンスを拡張できる最大許容サイズ (メガバイト単位) を指定する整数値 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="d111c-112">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="d111c-113">既定値は0です。これは、 <xref:System.Runtime.Caching.MemoryCache> クラスの自動サイズ調整ヒューリスティックが既定で使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="d111c-113">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="d111c-114">キャッシュの名前。</span><span class="sxs-lookup"><span data-stu-id="d111c-114">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="d111c-115">物理的にインストールされたコンピューターメモリのうち、キャッシュで使用できる最大パーセンテージを指定する 0 ~ 100 の整数値。</span><span class="sxs-lookup"><span data-stu-id="d111c-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="d111c-116">既定値は0です。これは、 <xref:System.Runtime.Caching.MemoryCache> クラスの自動サイズ調整ヒューリスティックが既定で使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="d111c-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="d111c-117">時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。</span><span class="sxs-lookup"><span data-stu-id="d111c-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="d111c-118">この値は、"HH: MM: SS" 形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="d111c-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d111c-119">子要素</span><span class="sxs-lookup"><span data-stu-id="d111c-119">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="d111c-120">親要素</span><span class="sxs-lookup"><span data-stu-id="d111c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d111c-121">要素</span><span class="sxs-lookup"><span data-stu-id="d111c-121">Element</span></span>|<span data-ttu-id="d111c-122">説明</span><span class="sxs-lookup"><span data-stu-id="d111c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="d111c-123">名前付きインスタンスの構成設定のコレクションを格納 <xref:System.Runtime.Caching.MemoryCache> します。</span><span class="sxs-lookup"><span data-stu-id="d111c-123">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d111c-124">解説</span><span class="sxs-lookup"><span data-stu-id="d111c-124">Remarks</span></span>  

 <span data-ttu-id="d111c-125">要素は、 `add` メモリキャッシュのコレクションにエントリを追加し `namedCaches` ます。</span><span class="sxs-lookup"><span data-stu-id="d111c-125">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="d111c-126">要素を使用する前に [clear](clear-element-for-namedcaches.md) 要素を使用して、 `add` コレクション内に他の名前付きキャッシュが存在しないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d111c-126">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="d111c-127">この要素は、machine.config ファイルと Web.config ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d111c-127">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d111c-128">例</span><span class="sxs-lookup"><span data-stu-id="d111c-128">Example</span></span>  

 <span data-ttu-id="d111c-129">次の例は、 `namedCache` メモリキャッシュのコレクションに対する既定のエントリの設定を定義する方法を示して `namedCaches` います。</span><span class="sxs-lookup"><span data-stu-id="d111c-129">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d111c-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="d111c-130">See also</span></span>

- [<span data-ttu-id="d111c-131">\<namedCaches> 要素 (キャッシュ設定)</span><span class="sxs-lookup"><span data-stu-id="d111c-131">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
