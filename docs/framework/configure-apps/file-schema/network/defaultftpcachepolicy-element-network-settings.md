---
description: '詳細情報: <defaultFtpCachePolicy> 要素 (ネットワーク設定)'
title: <defaultFtpCachePolicy> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 77150ce0980e96dd949df4b5ad7e4557ed1b991a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740367"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="70b49-103">\<defaultFtpCachePolicy> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="70b49-103">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="70b49-104">FTP キャッシュがアクティブかどうか、および既定のキャッシュポリシーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="70b49-104">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="70b49-105">構文</span><span class="sxs-lookup"><span data-stu-id="70b49-105">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70b49-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="70b49-106">Attributes and Elements</span></span>  

 <span data-ttu-id="70b49-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="70b49-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70b49-108">属性</span><span class="sxs-lookup"><span data-stu-id="70b49-108">Attributes</span></span>  
  
|<span data-ttu-id="70b49-109">属性</span><span class="sxs-lookup"><span data-stu-id="70b49-109">Attribute</span></span>|<span data-ttu-id="70b49-110">説明</span><span class="sxs-lookup"><span data-stu-id="70b49-110">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="70b49-111">FTP キャッシュポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="70b49-111">Specifies the FTP caching policy.</span></span> <span data-ttu-id="70b49-112">既定値は `Default` です。</span><span class="sxs-lookup"><span data-stu-id="70b49-112">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="70b49-113">policyLevel 属性</span><span class="sxs-lookup"><span data-stu-id="70b49-113">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="70b49-114">値</span><span class="sxs-lookup"><span data-stu-id="70b49-114">Value</span></span>|<span data-ttu-id="70b49-115">説明</span><span class="sxs-lookup"><span data-stu-id="70b49-115">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="70b49-116">リソースが最新で、コンテンツの長さが正確で、有効期限、変更、およびコンテンツの長さの属性が存在する場合、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="70b49-116">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="70b49-117">サーバーからリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="70b49-117">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="70b49-118">コンテンツの長さが存在し、エントリのサイズと一致する場合、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="70b49-118">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="70b49-119">コンテンツの長さが指定され、エントリのサイズと一致する場合に、キャッシュされたリソースを返します。それ以外の場合は、リソースがサーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="70b49-119">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="70b49-120">キャッシュされたリソースのタイムスタンプがサーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースを返します。それ以外の場合は、リソースがサーバーからダウンロードされ、キャッシュに格納されて、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="70b49-120">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="70b49-121">サーバーからリソースをダウンロードし、キャッシュに格納して、リソースを呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="70b49-121">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="70b49-122">キャッシュされたリソースが存在する場合は、削除されます。</span><span class="sxs-lookup"><span data-stu-id="70b49-122">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="70b49-123">リソースはサーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="70b49-123">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="70b49-124">タイムスタンプがサーバーのリソースのタイムスタンプと同じ場合は、キャッシュされたリソースのコピーを使用して要求に応じます。それ以外の場合は、リソースがサーバーからダウンロードされ、呼び出し元に提示され、キャッシュに格納されます。</span><span class="sxs-lookup"><span data-stu-id="70b49-124">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70b49-125">子要素</span><span class="sxs-lookup"><span data-stu-id="70b49-125">Child Elements</span></span>  

 <span data-ttu-id="70b49-126">なし。</span><span class="sxs-lookup"><span data-stu-id="70b49-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70b49-127">親要素</span><span class="sxs-lookup"><span data-stu-id="70b49-127">Parent Elements</span></span>  
  
|<span data-ttu-id="70b49-128">要素</span><span class="sxs-lookup"><span data-stu-id="70b49-128">Element</span></span>|<span data-ttu-id="70b49-129">説明</span><span class="sxs-lookup"><span data-stu-id="70b49-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70b49-130">Requestcaching></span><span class="sxs-lookup"><span data-stu-id="70b49-130">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="70b49-131">ネットワーク要求のキャッシュメカニズムを制御します。</span><span class="sxs-lookup"><span data-stu-id="70b49-131">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70b49-132">解説</span><span class="sxs-lookup"><span data-stu-id="70b49-132">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b49-133">例</span><span class="sxs-lookup"><span data-stu-id="70b49-133">Example</span></span>  

 <span data-ttu-id="70b49-134">次の例は、の FTP キャッシュポリシーを指定する方法を示して `NoCacheNoStore` います。</span><span class="sxs-lookup"><span data-stu-id="70b49-134">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="70b49-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="70b49-135">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="70b49-136">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="70b49-136">Network Settings Schema</span></span>](index.md)
