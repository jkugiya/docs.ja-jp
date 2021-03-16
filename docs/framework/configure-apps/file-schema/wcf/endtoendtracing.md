---
description: '詳細情報: <endToEndTracing>'
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 2ac4a7563d7d7881cdb503e843d34f84fd9c95a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782118"
---
# \<endToEndTracing>

<span data-ttu-id="a8a38-102">サービス アプリケーションの実行中にエンドツーエンドのトレースのさまざまな側面を有効または無効にするための構成要素。</span><span class="sxs-lookup"><span data-stu-id="a8a38-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="a8a38-103">構文</span><span class="sxs-lookup"><span data-stu-id="a8a38-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8a38-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a8a38-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a8a38-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8a38-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8a38-106">属性</span><span class="sxs-lookup"><span data-stu-id="a8a38-106">Attributes</span></span>  
  
|<span data-ttu-id="a8a38-107">属性</span><span class="sxs-lookup"><span data-stu-id="a8a38-107">Attribute</span></span>|<span data-ttu-id="a8a38-108">説明</span><span class="sxs-lookup"><span data-stu-id="a8a38-108">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="a8a38-109">アクティビティのトレースが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="a8a38-109">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="a8a38-110">メッセージ フローのトレースが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="a8a38-110">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="a8a38-111">伝達属性が true に設定されているかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="a8a38-111">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8a38-112">子要素</span><span class="sxs-lookup"><span data-stu-id="a8a38-112">Child Elements</span></span>  

 <span data-ttu-id="a8a38-113">なし。</span><span class="sxs-lookup"><span data-stu-id="a8a38-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8a38-114">親要素</span><span class="sxs-lookup"><span data-stu-id="a8a38-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a8a38-115">要素</span><span class="sxs-lookup"><span data-stu-id="a8a38-115">Element</span></span>|<span data-ttu-id="a8a38-116">説明</span><span class="sxs-lookup"><span data-stu-id="a8a38-116">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="a8a38-117">管理者が行うランタイムの検査と管理の WCF 設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a8a38-117">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8a38-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8a38-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="a8a38-119">エンドツーエンドのトレース</span><span class="sxs-lookup"><span data-stu-id="a8a38-119">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
