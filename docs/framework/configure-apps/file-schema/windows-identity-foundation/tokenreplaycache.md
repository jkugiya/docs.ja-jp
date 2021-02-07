---
description: '詳細情報: <tokenReplayCache>'
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 793b1f88a9eeb0ebce4cd440e248e81377f17e9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749000"
---
# \<tokenReplayCache>

<span data-ttu-id="8a793-102">トークン再生キャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="8a793-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="8a793-103">構文</span><span class="sxs-lookup"><span data-stu-id="8a793-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a793-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8a793-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8a793-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a793-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a793-106">属性</span><span class="sxs-lookup"><span data-stu-id="8a793-106">Attributes</span></span>  
  
|<span data-ttu-id="8a793-107">属性</span><span class="sxs-lookup"><span data-stu-id="8a793-107">Attribute</span></span>|<span data-ttu-id="8a793-108">説明</span><span class="sxs-lookup"><span data-stu-id="8a793-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a793-109">type</span><span class="sxs-lookup"><span data-stu-id="8a793-109">type</span></span>|<span data-ttu-id="8a793-110">クラスから派生する型 <xref:System.IdentityModel.Tokens.TokenReplayCache> 。</span><span class="sxs-lookup"><span data-stu-id="8a793-110">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="8a793-111">カスタムを指定する方法の詳細については `type` 、「[カスタム型参照]」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a793-111">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="8a793-112">子要素</span><span class="sxs-lookup"><span data-stu-id="8a793-112">Child Elements</span></span>  

 <span data-ttu-id="8a793-113">なし</span><span class="sxs-lookup"><span data-stu-id="8a793-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a793-114">親要素</span><span class="sxs-lookup"><span data-stu-id="8a793-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8a793-115">要素</span><span class="sxs-lookup"><span data-stu-id="8a793-115">Element</span></span>|<span data-ttu-id="8a793-116">説明</span><span class="sxs-lookup"><span data-stu-id="8a793-116">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="8a793-117">サービスまたはセキュリティトークンハンドラーコレクションによって使用されるキャッシュを登録します。</span><span class="sxs-lookup"><span data-stu-id="8a793-117">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a793-118">解説</span><span class="sxs-lookup"><span data-stu-id="8a793-118">Remarks</span></span>  

 <span data-ttu-id="8a793-119">トークン再生キャッシュは、再生されたトークンを検出するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a793-119">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="8a793-120">トークンリプレイ検出は、要素によって有効にされ [\<tokenReplayDetection>](tokenreplaydetection.md) ます。これは、トークンの最大有効期間も指定します。</span><span class="sxs-lookup"><span data-stu-id="8a793-120">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a793-121">例</span><span class="sxs-lookup"><span data-stu-id="8a793-121">Example</span></span>  

 <span data-ttu-id="8a793-122">次の XML は、再生されたトークンを検出するためのカスタムキャッシュの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="8a793-122">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a793-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a793-123">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
