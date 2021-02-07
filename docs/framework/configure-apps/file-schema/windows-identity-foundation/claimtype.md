---
description: '詳細情報: <claimType>'
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 55fd32edc7fb810742c3cf678b434675aebba00e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664224"
---
# \<claimType>

<span data-ttu-id="2d520-102">入力方向のセキュリティトークンに対して1つの省略可能なクレームまたは必須の要求を指定します。</span><span class="sxs-lookup"><span data-stu-id="2d520-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="2d520-103">構文</span><span class="sxs-lookup"><span data-stu-id="2d520-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d520-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2d520-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2d520-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d520-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d520-106">属性</span><span class="sxs-lookup"><span data-stu-id="2d520-106">Attributes</span></span>  
  
|<span data-ttu-id="2d520-107">属性</span><span class="sxs-lookup"><span data-stu-id="2d520-107">Attribute</span></span>|<span data-ttu-id="2d520-108">説明</span><span class="sxs-lookup"><span data-stu-id="2d520-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d520-109">type</span><span class="sxs-lookup"><span data-stu-id="2d520-109">type</span></span>|<span data-ttu-id="2d520-110">クレームの種類。</span><span class="sxs-lookup"><span data-stu-id="2d520-110">The claim type.</span></span> <span data-ttu-id="2d520-111">通常は URI です。</span><span class="sxs-lookup"><span data-stu-id="2d520-111">Typically a URI.</span></span> <span data-ttu-id="2d520-112">必須。</span><span class="sxs-lookup"><span data-stu-id="2d520-112">Required.</span></span>|  
|<span data-ttu-id="2d520-113">オプション</span><span class="sxs-lookup"><span data-stu-id="2d520-113">optional</span></span>|<span data-ttu-id="2d520-114">要求の種類が省略可能かどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="2d520-114">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="2d520-115">任意。</span><span class="sxs-lookup"><span data-stu-id="2d520-115">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d520-116">子要素</span><span class="sxs-lookup"><span data-stu-id="2d520-116">Child Elements</span></span>  

 <span data-ttu-id="2d520-117">なし</span><span class="sxs-lookup"><span data-stu-id="2d520-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d520-118">親要素</span><span class="sxs-lookup"><span data-stu-id="2d520-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2d520-119">要素</span><span class="sxs-lookup"><span data-stu-id="2d520-119">Element</span></span>|<span data-ttu-id="2d520-120">説明</span><span class="sxs-lookup"><span data-stu-id="2d520-120">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="2d520-121">受信セキュリティトークンに必要な要求のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="2d520-121">Specifies the set of required claims for incoming security tokens.</span></span>|
