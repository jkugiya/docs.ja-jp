---
description: '詳細情報: <requestCaching> 要素 (ネットワーク設定)'
title: <requestCaching> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: d09da8ad7a38ac363aaa740cca4de25e33fa8c56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698558"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="28218-103">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="28218-103">\<requestCaching> Element (Network Settings)</span></span>

<span data-ttu-id="28218-104">ネットワーク要求のキャッシュメカニズムを制御します。</span><span class="sxs-lookup"><span data-stu-id="28218-104">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="28218-105">構文</span><span class="sxs-lookup"><span data-stu-id="28218-105">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28218-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="28218-106">Attributes and Elements</span></span>  

 <span data-ttu-id="28218-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="28218-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28218-108">属性</span><span class="sxs-lookup"><span data-stu-id="28218-108">Attributes</span></span>  
  
|<span data-ttu-id="28218-109">属性</span><span class="sxs-lookup"><span data-stu-id="28218-109">Attribute</span></span>|<span data-ttu-id="28218-110">説明</span><span class="sxs-lookup"><span data-stu-id="28218-110">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="28218-111">キャッシュがさまざまなユーザーの情報の分離を提供するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="28218-111">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="28218-112">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="28218-112">The default value is `true`.</span></span> <span data-ttu-id="28218-113">中間層アプリケーションの場合は、この値をにする必要があり `false` ます。</span><span class="sxs-lookup"><span data-stu-id="28218-113">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="28218-114">すべての Web 応答に対してキャッシュを無効にし、プログラムでオーバーライドすることはできないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="28218-114">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="28218-115"><xref:System.Net.Cache.RequestCacheLevel> 列挙値の値の 1 つ。</span><span class="sxs-lookup"><span data-stu-id="28218-115">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="28218-116">既定値は `BypassCache` です。</span><span class="sxs-lookup"><span data-stu-id="28218-116">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="28218-117">コンテンツが期限切れとしてマークされるまでの既定の時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="28218-117">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="28218-118">policyLevel 属性</span><span class="sxs-lookup"><span data-stu-id="28218-118">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="28218-119">値</span><span class="sxs-lookup"><span data-stu-id="28218-119">Value</span></span>|<span data-ttu-id="28218-120">説明</span><span class="sxs-lookup"><span data-stu-id="28218-120">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="28218-121">リソースが最新で、コンテンツの長さが正確で、有効期限、変更、およびコンテンツの長さの属性が存在する場合、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="28218-121">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="28218-122">サーバーからリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="28218-122">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="28218-123">コンテンツの長さが存在し、エントリのサイズと一致する場合、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="28218-123">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="28218-124">コンテンツの長さが指定され、エントリのサイズと一致する場合に、キャッシュされたリソースを返します。それ以外の場合は、リソースがサーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="28218-124">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="28218-125">キャッシュされたリソースのタイムスタンプがサーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースを返します。それ以外の場合は、リソースがサーバーからダウンロードされ、キャッシュに格納されて、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="28218-125">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="28218-126">サーバーからリソースをダウンロードし、キャッシュに格納して、リソースを呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="28218-126">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="28218-127">キャッシュされたリソースが存在する場合は、削除されます。</span><span class="sxs-lookup"><span data-stu-id="28218-127">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="28218-128">リソースはサーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="28218-128">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="28218-129">タイムスタンプがサーバー上のリソースのタイムスタンプと同じ場合は、リソースのキャッシュされたコピーを使用して要求を満たします。それ以外の場合、リソースはサーバーからダウンロードされ、呼び出し元に渡され、キャッシュに格納されます。</span><span class="sxs-lookup"><span data-stu-id="28218-129">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28218-130">子要素</span><span class="sxs-lookup"><span data-stu-id="28218-130">Child Elements</span></span>  
  
|<span data-ttu-id="28218-131">要素</span><span class="sxs-lookup"><span data-stu-id="28218-131">Element</span></span>|<span data-ttu-id="28218-132">説明</span><span class="sxs-lookup"><span data-stu-id="28218-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28218-133">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="28218-133">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="28218-134">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="28218-134">Optional element.</span></span><br /><br /> <span data-ttu-id="28218-135">HTTP キャッシュがアクティブかどうか、および既定のキャッシュポリシーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28218-135">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="28218-136">\<defaultFtpCachePolicy> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="28218-136">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="28218-137">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="28218-137">Optional element.</span></span><br /><br /> <span data-ttu-id="28218-138">FTP キャッシュがアクティブかどうか、および既定のキャッシュポリシーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28218-138">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28218-139">親要素</span><span class="sxs-lookup"><span data-stu-id="28218-139">Parent Elements</span></span>  
  
|<span data-ttu-id="28218-140">要素</span><span class="sxs-lookup"><span data-stu-id="28218-140">Element</span></span>|<span data-ttu-id="28218-141">説明</span><span class="sxs-lookup"><span data-stu-id="28218-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28218-142">system.net</span><span class="sxs-lookup"><span data-stu-id="28218-142">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="28218-143">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="28218-143">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28218-144">例</span><span class="sxs-lookup"><span data-stu-id="28218-144">Example</span></span>  

 <span data-ttu-id="28218-145">次の例では、すべてのキャッシュを無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="28218-145">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28218-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="28218-146">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="28218-147">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="28218-147">Network Settings Schema</span></span>](index.md)
