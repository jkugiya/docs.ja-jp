---
description: '詳細情報: <claimTypeRequired>'
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: ba95c56af431a6dd81323751a42ce47160544cc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664172"
---
# \<claimTypeRequired>

<span data-ttu-id="ae31b-102">受信セキュリティトークンに必要な要求のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="ae31b-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="ae31b-103">構文</span><span class="sxs-lookup"><span data-stu-id="ae31b-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae31b-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ae31b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ae31b-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae31b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae31b-106">属性</span><span class="sxs-lookup"><span data-stu-id="ae31b-106">Attributes</span></span>  

 <span data-ttu-id="ae31b-107">なし</span><span class="sxs-lookup"><span data-stu-id="ae31b-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ae31b-108">子要素</span><span class="sxs-lookup"><span data-stu-id="ae31b-108">Child Elements</span></span>  
  
|<span data-ttu-id="ae31b-109">要素</span><span class="sxs-lookup"><span data-stu-id="ae31b-109">Element</span></span>|<span data-ttu-id="ae31b-110">説明</span><span class="sxs-lookup"><span data-stu-id="ae31b-110">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="ae31b-111">入力方向のセキュリティトークンに対して1つの省略可能なクレームまたは必須の要求を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae31b-111">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae31b-112">親要素</span><span class="sxs-lookup"><span data-stu-id="ae31b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ae31b-113">要素</span><span class="sxs-lookup"><span data-stu-id="ae31b-113">Element</span></span>|<span data-ttu-id="ae31b-114">説明</span><span class="sxs-lookup"><span data-stu-id="ae31b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="ae31b-115">サービスレベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae31b-115">Specifies service-level identity settings.</span></span>|
