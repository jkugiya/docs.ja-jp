---
description: '詳細情報: <sessionTokenRequirement>'
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 8f2868df4939dc0dc7c779eb9ca5a35a6b996fc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698272"
---
# \<sessionTokenRequirement>

<span data-ttu-id="74cb7-102"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラスまたは派生クラスの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="74cb7-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="74cb7-103">構文</span><span class="sxs-lookup"><span data-stu-id="74cb7-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74cb7-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="74cb7-104">Attributes and Elements</span></span>  

 <span data-ttu-id="74cb7-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="74cb7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74cb7-106">属性</span><span class="sxs-lookup"><span data-stu-id="74cb7-106">Attributes</span></span>  
  
|<span data-ttu-id="74cb7-107">属性</span><span class="sxs-lookup"><span data-stu-id="74cb7-107">Attribute</span></span>|<span data-ttu-id="74cb7-108">説明</span><span class="sxs-lookup"><span data-stu-id="74cb7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74cb7-109">有効期間</span><span class="sxs-lookup"><span data-stu-id="74cb7-109">lifetime</span></span>|<span data-ttu-id="74cb7-110">セッショントークンの有効期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="74cb7-110">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74cb7-111">子要素</span><span class="sxs-lookup"><span data-stu-id="74cb7-111">Child Elements</span></span>  

 <span data-ttu-id="74cb7-112">なし</span><span class="sxs-lookup"><span data-stu-id="74cb7-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74cb7-113">親要素</span><span class="sxs-lookup"><span data-stu-id="74cb7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="74cb7-114">要素</span><span class="sxs-lookup"><span data-stu-id="74cb7-114">Element</span></span>|<span data-ttu-id="74cb7-115">説明</span><span class="sxs-lookup"><span data-stu-id="74cb7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="74cb7-116">指定されたセキュリティトークンハンドラーをトークンハンドラーコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="74cb7-116">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="74cb7-117">例</span><span class="sxs-lookup"><span data-stu-id="74cb7-117">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
