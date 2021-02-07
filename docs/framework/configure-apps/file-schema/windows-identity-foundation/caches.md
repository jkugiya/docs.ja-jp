---
description: '詳細情報: <caches>'
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: ebc2fa66ab8b657f7cc3741668c9f27fc60510b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681839"
---
# \<caches>

<span data-ttu-id="dead7-102">セッショントークンとトークンリプレイ検出に使用されるキャッシュを登録します。</span><span class="sxs-lookup"><span data-stu-id="dead7-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="dead7-103">構文</span><span class="sxs-lookup"><span data-stu-id="dead7-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dead7-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dead7-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dead7-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dead7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dead7-106">属性</span><span class="sxs-lookup"><span data-stu-id="dead7-106">Attributes</span></span>  

 <span data-ttu-id="dead7-107">なし</span><span class="sxs-lookup"><span data-stu-id="dead7-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dead7-108">子要素</span><span class="sxs-lookup"><span data-stu-id="dead7-108">Child Elements</span></span>  
  
|<span data-ttu-id="dead7-109">要素</span><span class="sxs-lookup"><span data-stu-id="dead7-109">Element</span></span>|<span data-ttu-id="dead7-110">説明</span><span class="sxs-lookup"><span data-stu-id="dead7-110">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="dead7-111">セッショントークンのキャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="dead7-111">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="dead7-112">トークン再生キャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="dead7-112">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dead7-113">親要素</span><span class="sxs-lookup"><span data-stu-id="dead7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="dead7-114">要素</span><span class="sxs-lookup"><span data-stu-id="dead7-114">Element</span></span>|<span data-ttu-id="dead7-115">説明</span><span class="sxs-lookup"><span data-stu-id="dead7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="dead7-116">サービスレベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="dead7-116">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="dead7-117">セキュリティトークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="dead7-117">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dead7-118">解説</span><span class="sxs-lookup"><span data-stu-id="dead7-118">Remarks</span></span>  

 <span data-ttu-id="dead7-119">要素は `<caches>` 、要素の下のサービスレベルで指定することも、 `<identityConfiguration>` 要素の下のセキュリティトークンハンドラーコレクションレベルで指定することもでき `<securityTokenHandlerConfiguration>` ます。</span><span class="sxs-lookup"><span data-stu-id="dead7-119">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="dead7-120">トークンハンドラーコレクションの設定は、サービスで指定された設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="dead7-120">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="dead7-121">`<caches>`要素は、クラスによって表され <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> ます。</span><span class="sxs-lookup"><span data-stu-id="dead7-121">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="dead7-122">構成されたキャッシュは、クラスによって表され <xref:System.IdentityModel.Configuration.IdentityModelCaches> ます。</span><span class="sxs-lookup"><span data-stu-id="dead7-122">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dead7-123">例</span><span class="sxs-lookup"><span data-stu-id="dead7-123">Example</span></span>  

 <span data-ttu-id="dead7-124">次の XML は、セッションセキュリティトークン () を保持するためのカスタムキャッシュの構成を示して <xref:System.IdentityModel.Tokens.SessionSecurityToken> います。</span><span class="sxs-lookup"><span data-stu-id="dead7-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="dead7-125">この構成は、サンプルから取得され `ClaimsAwareWebFarm` ます。</span><span class="sxs-lookup"><span data-stu-id="dead7-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
