---
description: '詳細情報: <enableWebScript>'
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: f357bf1ab726cd434a16b2daa9c8115afe7d4430
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725884"
---
# \<enableWebScript>

<span data-ttu-id="f621d-102">この要素は、ASP.NET AJAX Web ページからサービスを使用できるようにするエンドポイントの動作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f621d-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="f621d-103">構文</span><span class="sxs-lookup"><span data-stu-id="f621d-103">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f621d-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f621d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f621d-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f621d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f621d-106">属性</span><span class="sxs-lookup"><span data-stu-id="f621d-106">Attributes</span></span>  

 <span data-ttu-id="f621d-107">なし。</span><span class="sxs-lookup"><span data-stu-id="f621d-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f621d-108">子要素</span><span class="sxs-lookup"><span data-stu-id="f621d-108">Child Elements</span></span>  

 <span data-ttu-id="f621d-109">なし。</span><span class="sxs-lookup"><span data-stu-id="f621d-109">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f621d-110">親要素</span><span class="sxs-lookup"><span data-stu-id="f621d-110">Parent Elements</span></span>  
  
|<span data-ttu-id="f621d-111">要素</span><span class="sxs-lookup"><span data-stu-id="f621d-111">Element</span></span>|<span data-ttu-id="f621d-112">説明</span><span class="sxs-lookup"><span data-stu-id="f621d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f621d-113">エンドポイントの動作のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="f621d-113">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f621d-114">解説</span><span class="sxs-lookup"><span data-stu-id="f621d-114">Remarks</span></span>  

 <span data-ttu-id="f621d-115">この動作は、 [\<webHttpBinding>](webhttpbinding.md) 標準バインディングまたはバインディング要素と組み合わせて使用する必要があり [\<webMessageEncoding>](webmessageencoding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="f621d-115">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="f621d-116">この動作の詳細については、「<xref:System.ServiceModel.Description.WebScriptEnablingBehavior>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f621d-116">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f621d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f621d-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="f621d-118">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="f621d-118">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
