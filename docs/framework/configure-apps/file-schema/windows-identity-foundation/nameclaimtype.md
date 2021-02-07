---
description: '詳細情報: <nameClaimType>'
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: d5bc2f96c2753febdb61c3495b7067c0e31e52d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664055"
---
# \<nameClaimType>

<span data-ttu-id="d3a6d-102">プロパティを指定するクレームの種類を設定し <xref:System.Security.Principal.IIdentity.Name%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d3a6d-103">要求の種類は、 <xref:System.Security.Claims.Claim> <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> このトークンハンドラーのメソッドによって返されたオブジェクトのコレクション内のを検索するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="d3a6d-104">次に、一致する要求の値が、 <xref:System.Security.Principal.IIdentity> このトークンハンドラーから生成されたの名前として設定されます。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="d3a6d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d3a6d-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3a6d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d3a6d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d3a6d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3a6d-108">属性</span><span class="sxs-lookup"><span data-stu-id="d3a6d-108">Attributes</span></span>  
  
|<span data-ttu-id="d3a6d-109">属性</span><span class="sxs-lookup"><span data-stu-id="d3a6d-109">Attribute</span></span>|<span data-ttu-id="d3a6d-110">説明</span><span class="sxs-lookup"><span data-stu-id="d3a6d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3a6d-111">value</span><span class="sxs-lookup"><span data-stu-id="d3a6d-111">value</span></span>|<span data-ttu-id="d3a6d-112">プロパティに使用するクレームのクレームの種類を表す URI を指定する文字列 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-112">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d3a6d-113">必須。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3a6d-114">子要素</span><span class="sxs-lookup"><span data-stu-id="d3a6d-114">Child Elements</span></span>  

 <span data-ttu-id="d3a6d-115">なし</span><span class="sxs-lookup"><span data-stu-id="d3a6d-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3a6d-116">親要素</span><span class="sxs-lookup"><span data-stu-id="d3a6d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d3a6d-117">要素</span><span class="sxs-lookup"><span data-stu-id="d3a6d-117">Element</span></span>|<span data-ttu-id="d3a6d-118">説明</span><span class="sxs-lookup"><span data-stu-id="d3a6d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="d3a6d-119">クラス、クラス、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> またはこれらのクラスの派生クラスの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-119">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3a6d-120">解説</span><span class="sxs-lookup"><span data-stu-id="d3a6d-120">Remarks</span></span>  

 <span data-ttu-id="d3a6d-121">要素は、 `<nameClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> オブジェクトが構成から初期化されるときにプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d3a6d-121">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3a6d-122">例</span><span class="sxs-lookup"><span data-stu-id="d3a6d-122">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3a6d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3a6d-123">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
