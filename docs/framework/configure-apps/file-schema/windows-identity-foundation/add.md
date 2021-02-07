---
description: '詳細情報: <add>'
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: c79fb66fb4e87f15c2bf7f2c02e57f473c7262a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681865"
---
# \<add>

<span data-ttu-id="5c5b1-102">指定されたセキュリティトークンハンドラーをトークンハンドラーコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5c5b1-103">構文</span><span class="sxs-lookup"><span data-stu-id="5c5b1-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c5b1-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5c5b1-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5c5b1-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c5b1-106">属性</span><span class="sxs-lookup"><span data-stu-id="5c5b1-106">Attributes</span></span>  
  
|<span data-ttu-id="5c5b1-107">属性</span><span class="sxs-lookup"><span data-stu-id="5c5b1-107">Attribute</span></span>|<span data-ttu-id="5c5b1-108">説明</span><span class="sxs-lookup"><span data-stu-id="5c5b1-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c5b1-109">type</span><span class="sxs-lookup"><span data-stu-id="5c5b1-109">type</span></span>|<span data-ttu-id="5c5b1-110">追加するトークンハンドラーの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-110">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="5c5b1-111">属性を指定する方法の詳細については `type` 、「 [カスタム型参照](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-111">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c5b1-112">子要素</span><span class="sxs-lookup"><span data-stu-id="5c5b1-112">Child Elements</span></span>  
  
|<span data-ttu-id="5c5b1-113">要素</span><span class="sxs-lookup"><span data-stu-id="5c5b1-113">Element</span></span>|<span data-ttu-id="5c5b1-114">説明</span><span class="sxs-lookup"><span data-stu-id="5c5b1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="5c5b1-115">クラス、クラス、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> またはこれらのクラスの派生クラスの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="5c5b1-116"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラスまたは派生クラスの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-116">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="5c5b1-117"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>クラスまたは派生クラスの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-117">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="5c5b1-118">クラスまたは派生クラスのオプションの構成を提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-118">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c5b1-119">親要素</span><span class="sxs-lookup"><span data-stu-id="5c5b1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5c5b1-120">要素</span><span class="sxs-lookup"><span data-stu-id="5c5b1-120">Element</span></span>|<span data-ttu-id="5c5b1-121">説明</span><span class="sxs-lookup"><span data-stu-id="5c5b1-121">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="5c5b1-122">エンドポイントに登録されているセキュリティトークンハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-122">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c5b1-123">解説</span><span class="sxs-lookup"><span data-stu-id="5c5b1-123">Remarks</span></span>  

 <span data-ttu-id="5c5b1-124">要素は、 `<add>` トークンハンドラーの構成を指定する1つの子要素を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-124">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="5c5b1-125">これは、要素の属性を通じて参照されるハンドラークラスが `type` この機能をサポートするかどうかによって異なり `<add>` ます。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-125">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="5c5b1-126">この機能を提供するトークンハンドラークラスは、オブジェクトを受け取るコンストラクターを公開する必要があり <xref:System.Xml.XmlElement> ます。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-126">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="5c5b1-127">いくつかの組み込みセキュリティトークンハンドラークラスは、この機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-127">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="5c5b1-128">これらのクラスは、、、、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 、および <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> です。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-128">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c5b1-129">トークンハンドラーコレクションには、指定された任意の型の1つのハンドラーのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-129">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="5c5b1-130">これは、たとえば、クラスから派生したハンドラーをコレクションに追加する場合は、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 最初にコレクションから既定で存在するを削除する必要があることを意味し <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-130">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="5c5b1-131">要素を使用して、 [\<remove>](remove.md) コレクションから1つのハンドラーを削除することも、要素を使用してコレクションからすべてのハンドラーを削除することもでき [\<clear>](clear.md) ます。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-131">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="5c5b1-132">ハンドラーに指定された設定は、要素の下のトークンハンドラーコレクションで指定された同等 [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) の設定をオーバーライドし、要素の下のサービスレベルで指定され [\<identityConfiguration>](identityconfiguration.md) ます。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-132">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5b1-133">例</span><span class="sxs-lookup"><span data-stu-id="5c5b1-133">Example</span></span>  

 <span data-ttu-id="5c5b1-134">次の XML は、および要素を使用して、 `<add>` `<remove>` 既定のセッショントークンハンドラーをカスタムセッショントークンハンドラーに置き換える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-134">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="5c5b1-135">XML は、「」のサンプルから抜粋したものです `ClaimsAwareWebFarm` 。</span><span class="sxs-lookup"><span data-stu-id="5c5b1-135">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
