---
description: '詳細情報: <userNameSecurityTokenHandlerRequirement>'
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: c2bca086d06738699517fe140173f321a3233a4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786500"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="93480-102"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>クラスまたは派生クラスの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="93480-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="93480-103">構文</span><span class="sxs-lookup"><span data-stu-id="93480-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93480-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="93480-104">Attributes and Elements</span></span>  

 <span data-ttu-id="93480-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="93480-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93480-106">属性</span><span class="sxs-lookup"><span data-stu-id="93480-106">Attributes</span></span>  
  
|<span data-ttu-id="93480-107">属性</span><span class="sxs-lookup"><span data-stu-id="93480-107">Attribute</span></span>|<span data-ttu-id="93480-108">説明</span><span class="sxs-lookup"><span data-stu-id="93480-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93480-109">メンバーシップ Providername</span><span class="sxs-lookup"><span data-stu-id="93480-109">membershipProviderName</span></span>|<span data-ttu-id="93480-110"><xref:System.Web.Security.MembershipProvider>セキュリティトークンハンドラーによって使用されるを指定します。</span><span class="sxs-lookup"><span data-stu-id="93480-110">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93480-111">子要素</span><span class="sxs-lookup"><span data-stu-id="93480-111">Child Elements</span></span>  

 <span data-ttu-id="93480-112">なし</span><span class="sxs-lookup"><span data-stu-id="93480-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93480-113">親要素</span><span class="sxs-lookup"><span data-stu-id="93480-113">Parent Elements</span></span>  
  
|<span data-ttu-id="93480-114">要素</span><span class="sxs-lookup"><span data-stu-id="93480-114">Element</span></span>|<span data-ttu-id="93480-115">説明</span><span class="sxs-lookup"><span data-stu-id="93480-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="93480-116">指定されたセキュリティトークンハンドラーをトークンハンドラーコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="93480-116">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93480-117">解説</span><span class="sxs-lookup"><span data-stu-id="93480-117">Remarks</span></span>  

 <span data-ttu-id="93480-118">要素は、 `<userNameSecurityTokenHandlerRequirement>` <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> オブジェクトが構成から初期化されるときにプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="93480-118">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93480-119">例</span><span class="sxs-lookup"><span data-stu-id="93480-119">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
