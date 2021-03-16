---
description: '詳細情報: <serviceAuthenticationManager>'
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: ae9c8d7f74b3ad7d0c61a77d20f38f228c695970
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786773"
---
# \<serviceAuthenticationManager>

<span data-ttu-id="55fe6-102">サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="55fe6-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="55fe6-103">構文</span><span class="sxs-lookup"><span data-stu-id="55fe6-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55fe6-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="55fe6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="55fe6-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="55fe6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55fe6-106">属性</span><span class="sxs-lookup"><span data-stu-id="55fe6-106">Attributes</span></span>  
  
|<span data-ttu-id="55fe6-107">属性</span><span class="sxs-lookup"><span data-stu-id="55fe6-107">Attribute</span></span>|<span data-ttu-id="55fe6-108">説明</span><span class="sxs-lookup"><span data-stu-id="55fe6-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55fe6-109">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="55fe6-109">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="55fe6-110">現在の動作の認証ポリシーの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="55fe6-110">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55fe6-111">子要素</span><span class="sxs-lookup"><span data-stu-id="55fe6-111">Child Elements</span></span>  

 <span data-ttu-id="55fe6-112">なし。</span><span class="sxs-lookup"><span data-stu-id="55fe6-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55fe6-113">親要素</span><span class="sxs-lookup"><span data-stu-id="55fe6-113">Parent Elements</span></span>  
  
|<span data-ttu-id="55fe6-114">要素</span><span class="sxs-lookup"><span data-stu-id="55fe6-114">Element</span></span>|<span data-ttu-id="55fe6-115">説明</span><span class="sxs-lookup"><span data-stu-id="55fe6-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="55fe6-116">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="55fe6-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55fe6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="55fe6-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
