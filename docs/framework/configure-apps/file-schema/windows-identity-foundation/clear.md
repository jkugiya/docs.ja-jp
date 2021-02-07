---
description: '詳細情報: <clear>'
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: 460add2722779a61dacc5c7510ea0a94aaef4a3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664133"
---
# \<clear>

<span data-ttu-id="0c70d-102">現在のトークンハンドラーコレクションからすべてのセキュリティトークンハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="0c70d-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="0c70d-103">構文</span><span class="sxs-lookup"><span data-stu-id="0c70d-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c70d-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0c70d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0c70d-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0c70d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c70d-106">属性</span><span class="sxs-lookup"><span data-stu-id="0c70d-106">Attributes</span></span>  

 <span data-ttu-id="0c70d-107">なし</span><span class="sxs-lookup"><span data-stu-id="0c70d-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c70d-108">子要素</span><span class="sxs-lookup"><span data-stu-id="0c70d-108">Child Elements</span></span>  

 <span data-ttu-id="0c70d-109">なし</span><span class="sxs-lookup"><span data-stu-id="0c70d-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c70d-110">親要素</span><span class="sxs-lookup"><span data-stu-id="0c70d-110">Parent Elements</span></span>  
  
|<span data-ttu-id="0c70d-111">要素</span><span class="sxs-lookup"><span data-stu-id="0c70d-111">Element</span></span>|<span data-ttu-id="0c70d-112">説明</span><span class="sxs-lookup"><span data-stu-id="0c70d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="0c70d-113">エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0c70d-113">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
