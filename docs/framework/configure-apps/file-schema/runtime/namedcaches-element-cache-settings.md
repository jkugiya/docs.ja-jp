---
description: '詳細情報: <namedCaches> 要素 (キャッシュ設定)'
title: <namedCaches> 要素 (キャッシュ設定)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 543650513270c0cee24d965b8efe98a75d7b8f9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782326"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="c867b-103">\<namedCaches> 要素 (キャッシュ設定)</span><span class="sxs-lookup"><span data-stu-id="c867b-103">\<namedCaches> Element (Cache Settings)</span></span>

<span data-ttu-id="c867b-104">名前付きインスタンスの構成設定のコレクションを指定し <xref:System.Runtime.Caching.MemoryCache> ます。</span><span class="sxs-lookup"><span data-stu-id="c867b-104">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="c867b-105">プロパティは、構成 <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> ファイルの1つ以上の要素から構成設定のコレクションを参照し `namedCaches` ます。</span><span class="sxs-lookup"><span data-stu-id="c867b-105">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="c867b-106">構文</span><span class="sxs-lookup"><span data-stu-id="c867b-106">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c867b-107">Type</span><span class="sxs-lookup"><span data-stu-id="c867b-107">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c867b-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c867b-108">Attributes and Elements</span></span>  

 <span data-ttu-id="c867b-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c867b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c867b-110">属性</span><span class="sxs-lookup"><span data-stu-id="c867b-110">Attributes</span></span>  
  
|<span data-ttu-id="c867b-111">属性</span><span class="sxs-lookup"><span data-stu-id="c867b-111">Attribute</span></span>|<span data-ttu-id="c867b-112">説明</span><span class="sxs-lookup"><span data-stu-id="c867b-112">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="c867b-113">のインスタンスを拡張できる最大許容サイズを mb 単位で指定する整数値 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="c867b-113">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="c867b-114">既定値は0です。これは、クラスの自動サイズ調整ヒューリスティックが <xref:System.Runtime.Caching.MemoryCache> 既定で使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c867b-114">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="c867b-115">キャッシュの名前。</span><span class="sxs-lookup"><span data-stu-id="c867b-115">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="c867b-116">物理的にインストールされたコンピューターメモリのうち、キャッシュで使用できる最大パーセンテージを指定する 0 ~ 100 の整数値。</span><span class="sxs-lookup"><span data-stu-id="c867b-116">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="c867b-117">既定値は0です。これは、クラスの自動サイズ調整ヒューリスティックが <xref:System.Runtime.Caching.MemoryCache> 既定で使用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c867b-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="c867b-118">時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。</span><span class="sxs-lookup"><span data-stu-id="c867b-118">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="c867b-119">この値は、"HH: MM: SS" 形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="c867b-119">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c867b-120">子要素</span><span class="sxs-lookup"><span data-stu-id="c867b-120">Child Elements</span></span>  
  
|<span data-ttu-id="c867b-121">要素</span><span class="sxs-lookup"><span data-stu-id="c867b-121">Element</span></span>|<span data-ttu-id="c867b-122">説明</span><span class="sxs-lookup"><span data-stu-id="c867b-122">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="c867b-123">名前付きキャッシュを、メモリ キャッシュの `namedCaches` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="c867b-123">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="c867b-124">メモリ キャッシュの `namedCaches` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="c867b-124">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="c867b-125">名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="c867b-125">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c867b-126">親要素</span><span class="sxs-lookup"><span data-stu-id="c867b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="c867b-127">要素</span><span class="sxs-lookup"><span data-stu-id="c867b-127">Element</span></span>|<span data-ttu-id="c867b-128">説明</span><span class="sxs-lookup"><span data-stu-id="c867b-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="c867b-129">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="c867b-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="c867b-130"><xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="c867b-130">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="c867b-131">.NET Framework に組み込まれているアプリケーションに出力キャッシュを実装できる型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c867b-131">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c867b-132">解説</span><span class="sxs-lookup"><span data-stu-id="c867b-132">Remarks</span></span>  

 <span data-ttu-id="c867b-133">Web.config ファイルのメモリキャッシュ構成セクションには `add` 、コレクションの、、の各属性を含めることができ `remove` `clear` `namedCaches` ます。</span><span class="sxs-lookup"><span data-stu-id="c867b-133">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="c867b-134">各 `namedCaches` エントリは、属性によって一意に識別され `name` ます。</span><span class="sxs-lookup"><span data-stu-id="c867b-134">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="c867b-135">メモリキャッシュエントリのインスタンスを取得するには、アプリケーション構成ファイル内の情報を参照します。</span><span class="sxs-lookup"><span data-stu-id="c867b-135">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="c867b-136">既定では、構成ファイルにエントリが存在するのは既定のキャッシュインスタンスだけです。</span><span class="sxs-lookup"><span data-stu-id="c867b-136">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="c867b-137">既定のキャッシュインスタンスは、プロパティから返されるインスタンスです <xref:System.Runtime.Caching.MemoryCache.Default%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c867b-137">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="c867b-138">Name 属性を "default" に設定した場合、要素は既定のメモリキャッシュインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c867b-138">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c867b-139">例</span><span class="sxs-lookup"><span data-stu-id="c867b-139">Example</span></span>  

 <span data-ttu-id="c867b-140">次の例は、属性を "default" に設定することによって、キャッシュの名前を既定のキャッシュエントリ名に設定する方法を示して `name` います。</span><span class="sxs-lookup"><span data-stu-id="c867b-140">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="c867b-141">`cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。</span><span class="sxs-lookup"><span data-stu-id="c867b-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c867b-142">これらの属性を0に設定すると、クラスの自動サイズ調整ヒューリスティックが <xref:System.Runtime.Caching.MemoryCache> 使用されます。</span><span class="sxs-lookup"><span data-stu-id="c867b-142">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="c867b-143">キャッシュの実装では、現在のメモリ負荷と、絶対値および割合に基づくメモリ制限を2分ごとに比較します。</span><span class="sxs-lookup"><span data-stu-id="c867b-143">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c867b-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="c867b-144">See also</span></span>

- [<span data-ttu-id="c867b-145">\<memoryCache> 要素 (キャッシュ設定)</span><span class="sxs-lookup"><span data-stu-id="c867b-145">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
