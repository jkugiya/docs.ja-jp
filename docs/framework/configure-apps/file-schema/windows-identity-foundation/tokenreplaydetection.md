---
description: '詳細情報: <tokenReplayDetection>'
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a8a6b754a3282afe4f2932296b06b84c09fb6f1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786539"
---
# \<tokenReplayDetection>

<span data-ttu-id="52dc3-102">トークンリプレイ検出を有効にし、トークンの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="52dc3-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="52dc3-103">構文</span><span class="sxs-lookup"><span data-stu-id="52dc3-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="52dc3-104">Type</span><span class="sxs-lookup"><span data-stu-id="52dc3-104">Type</span></span>  

 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52dc3-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="52dc3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="52dc3-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="52dc3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52dc3-107">属性</span><span class="sxs-lookup"><span data-stu-id="52dc3-107">Attributes</span></span>  
  
|<span data-ttu-id="52dc3-108">属性</span><span class="sxs-lookup"><span data-stu-id="52dc3-108">Attribute</span></span>|<span data-ttu-id="52dc3-109">説明</span><span class="sxs-lookup"><span data-stu-id="52dc3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52dc3-110">enabled</span><span class="sxs-lookup"><span data-stu-id="52dc3-110">enabled</span></span>|<span data-ttu-id="52dc3-111">トークンリプレイ検出が有効かどうかを示す値です。"true" を使用してトークンリプレイ検出を有効にします。</span><span class="sxs-lookup"><span data-stu-id="52dc3-111">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="52dc3-112">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="52dc3-112">expirationPeriod</span></span>|<span data-ttu-id="52dc3-113"><xref:System.TimeSpan>項目が期限切れと見なされ、キャッシュから削除されるまでの最大時間を指定する。</span><span class="sxs-lookup"><span data-stu-id="52dc3-113">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="52dc3-114">値を指定する方法の詳細について <xref:System.TimeSpan> は、「 [Timespan values](../windows-workflow-foundation/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc3-114">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52dc3-115">子要素</span><span class="sxs-lookup"><span data-stu-id="52dc3-115">Child Elements</span></span>  

 <span data-ttu-id="52dc3-116">なし</span><span class="sxs-lookup"><span data-stu-id="52dc3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52dc3-117">親要素</span><span class="sxs-lookup"><span data-stu-id="52dc3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="52dc3-118">要素</span><span class="sxs-lookup"><span data-stu-id="52dc3-118">Element</span></span>|<span data-ttu-id="52dc3-119">説明</span><span class="sxs-lookup"><span data-stu-id="52dc3-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="52dc3-120">サービスレベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="52dc3-120">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="52dc3-121">セキュリティトークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="52dc3-121">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52dc3-122">解説</span><span class="sxs-lookup"><span data-stu-id="52dc3-122">Remarks</span></span>  

 <span data-ttu-id="52dc3-123">要素は `<tokenReplayDetection>` 、要素の下のサービスレベルで指定することも、 `<identityConfiguration>` 要素の下のセキュリティトークンハンドラーコレクションレベルで指定することもでき `<securityTokenHandlerConfiguration>` ます。</span><span class="sxs-lookup"><span data-stu-id="52dc3-123">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="52dc3-124">トークンハンドラーコレクションの設定は、サービスで指定された設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="52dc3-124">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="52dc3-125">トークン再生キャッシュの種類は、要素によって指定され [\<tokenReplayCache>](tokenreplaycache.md) ます。</span><span class="sxs-lookup"><span data-stu-id="52dc3-125">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
