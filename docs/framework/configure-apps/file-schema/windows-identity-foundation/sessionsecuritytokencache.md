---
description: '詳細情報: <sessionSecurityTokenCache>'
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 6fc0bb518f546ffd80c68df95a9c0fab145423b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698285"
---
# \<sessionSecurityTokenCache>

<span data-ttu-id="75498-102">セッショントークンのキャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="75498-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="75498-103">構文</span><span class="sxs-lookup"><span data-stu-id="75498-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75498-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="75498-104">Attributes and Elements</span></span>  

 <span data-ttu-id="75498-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="75498-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75498-106">属性</span><span class="sxs-lookup"><span data-stu-id="75498-106">Attributes</span></span>  
  
|<span data-ttu-id="75498-107">属性</span><span class="sxs-lookup"><span data-stu-id="75498-107">Attribute</span></span>|<span data-ttu-id="75498-108">説明</span><span class="sxs-lookup"><span data-stu-id="75498-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75498-109">type</span><span class="sxs-lookup"><span data-stu-id="75498-109">type</span></span>|<span data-ttu-id="75498-110">クラスから派生する型 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 。</span><span class="sxs-lookup"><span data-stu-id="75498-110">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75498-111">子要素</span><span class="sxs-lookup"><span data-stu-id="75498-111">Child Elements</span></span>  

 <span data-ttu-id="75498-112">なし</span><span class="sxs-lookup"><span data-stu-id="75498-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75498-113">親要素</span><span class="sxs-lookup"><span data-stu-id="75498-113">Parent Elements</span></span>  
  
|<span data-ttu-id="75498-114">要素</span><span class="sxs-lookup"><span data-stu-id="75498-114">Element</span></span>|<span data-ttu-id="75498-115">説明</span><span class="sxs-lookup"><span data-stu-id="75498-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="75498-116">サービスまたはセキュリティトークンハンドラーコレクションによって使用されるキャッシュを登録します。</span><span class="sxs-lookup"><span data-stu-id="75498-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="75498-117">例</span><span class="sxs-lookup"><span data-stu-id="75498-117">Example</span></span>  

 <span data-ttu-id="75498-118">次の XML は、セッションセキュリティトークン () を保持するためのカスタムキャッシュの構成を示して <xref:System.IdentityModel.Tokens.SessionSecurityToken> います。</span><span class="sxs-lookup"><span data-stu-id="75498-118">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="75498-119">この構成は、サンプルから取得され `ClaimsAwareWebFarm` ます。</span><span class="sxs-lookup"><span data-stu-id="75498-119">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="75498-120">このサンプルの詳細については、「 [WIF Code Sample Index](/previous-versions/dotnet/framework/security/wif-code-sample-index)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75498-120">For more information about this sample, see [WIF Code Sample Index](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="75498-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="75498-121">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
