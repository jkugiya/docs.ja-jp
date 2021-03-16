---
description: '詳細情報: <clientVia>'
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 651af0c310504f7672ca172d7df609365c319506
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638773"
---
# \<clientVia>

<span data-ttu-id="ff378-102">トランスポート チャネルの作成対象となる URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff378-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ff378-103">詳細については、「<xref:System.ServiceModel.Description.ClientViaBehavior>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff378-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="ff378-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff378-104">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff378-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ff378-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ff378-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff378-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff378-107">属性</span><span class="sxs-lookup"><span data-stu-id="ff378-107">Attributes</span></span>  
  
|<span data-ttu-id="ff378-108">属性</span><span class="sxs-lookup"><span data-stu-id="ff378-108">Attribute</span></span>|<span data-ttu-id="ff378-109">説明</span><span class="sxs-lookup"><span data-stu-id="ff378-109">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ff378-110">メッセージの経路を示す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="ff378-110">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff378-111">子要素</span><span class="sxs-lookup"><span data-stu-id="ff378-111">Child Elements</span></span>  

 <span data-ttu-id="ff378-112">なし</span><span class="sxs-lookup"><span data-stu-id="ff378-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff378-113">親要素</span><span class="sxs-lookup"><span data-stu-id="ff378-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ff378-114">要素</span><span class="sxs-lookup"><span data-stu-id="ff378-114">Element</span></span>|<span data-ttu-id="ff378-115">説明</span><span class="sxs-lookup"><span data-stu-id="ff378-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff378-116">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff378-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff378-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff378-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
