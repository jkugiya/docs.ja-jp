---
description: 詳細については <diagnostics> 、「アクティブ化」を参照してください。
title: <diagnostics> アクティブ化の場合
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: aa1529a478ac367ea89c8926571c6c6f2f57cf74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698363"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="2775f-103">\<diagnostics> アクティブ化の場合</span><span class="sxs-lookup"><span data-stu-id="2775f-103">\<diagnostics> for Activation</span></span>

<span data-ttu-id="2775f-104">Windows Communication Foundation (WCF) リスナーの診断機能を構成します。</span><span class="sxs-lookup"><span data-stu-id="2775f-104">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="2775f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2775f-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="2775f-106">Type</span><span class="sxs-lookup"><span data-stu-id="2775f-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2775f-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2775f-107">Attributes and Elements</span></span>  

 <span data-ttu-id="2775f-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2775f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2775f-109">属性</span><span class="sxs-lookup"><span data-stu-id="2775f-109">Attributes</span></span>  
  
|<span data-ttu-id="2775f-110">属性</span><span class="sxs-lookup"><span data-stu-id="2775f-110">Attribute</span></span>|<span data-ttu-id="2775f-111">説明</span><span class="sxs-lookup"><span data-stu-id="2775f-111">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="2775f-112">診断用パフォーマンス カウンターが有効であるかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="2775f-112">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2775f-113">子要素</span><span class="sxs-lookup"><span data-stu-id="2775f-113">Child Elements</span></span>  

 <span data-ttu-id="2775f-114">なし。</span><span class="sxs-lookup"><span data-stu-id="2775f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2775f-115">親要素</span><span class="sxs-lookup"><span data-stu-id="2775f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2775f-116">要素</span><span class="sxs-lookup"><span data-stu-id="2775f-116">Element</span></span>|<span data-ttu-id="2775f-117">説明</span><span class="sxs-lookup"><span data-stu-id="2775f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="2775f-118">リスナー プロセス SMSvcHost.exe の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2775f-118">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2775f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2775f-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
