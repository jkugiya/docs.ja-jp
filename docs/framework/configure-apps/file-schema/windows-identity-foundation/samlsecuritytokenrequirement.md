---
description: '詳細情報: <samlSecurityTokenRequirement>'
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: 21e584480aae6f620e0809be77e02789536db426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786565"
---
# \<samlSecurityTokenRequirement>

<span data-ttu-id="80ae2-102">クラス、クラス、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> またはこれらのクラスの派生クラスの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="80ae2-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="80ae2-103">クラスによって表さ <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> れます。</span><span class="sxs-lookup"><span data-stu-id="80ae2-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="80ae2-104">構文</span><span class="sxs-lookup"><span data-stu-id="80ae2-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80ae2-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="80ae2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="80ae2-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="80ae2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80ae2-107">属性</span><span class="sxs-lookup"><span data-stu-id="80ae2-107">Attributes</span></span>  
  
|<span data-ttu-id="80ae2-108">属性</span><span class="sxs-lookup"><span data-stu-id="80ae2-108">Attribute</span></span>|<span data-ttu-id="80ae2-109">説明</span><span class="sxs-lookup"><span data-stu-id="80ae2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80ae2-110">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="80ae2-110">mapToWindows</span></span>|<span data-ttu-id="80ae2-111">受信 UPN 要求を使用して、トークンハンドラーが検証トークンを Windows アカウントにマップする必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="80ae2-111">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="80ae2-112">既定値は "false" です。</span><span class="sxs-lookup"><span data-stu-id="80ae2-112">The default is "false".</span></span>|  
|<span data-ttu-id="80ae2-113">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="80ae2-113">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="80ae2-114"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X.509 証明書に使用する失効モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="80ae2-114">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="80ae2-115">既定値は "Online" です。</span><span class="sxs-lookup"><span data-stu-id="80ae2-115">The default value is "Online".</span></span>|  
|<span data-ttu-id="80ae2-116">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="80ae2-116">issuerCertificateValidationMode</span></span>|<span data-ttu-id="80ae2-117"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X.509 証明書に使用する検証モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="80ae2-117">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="80ae2-118">既定値は "PeerOrChainTrust" です。</span><span class="sxs-lookup"><span data-stu-id="80ae2-118">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="80ae2-119">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="80ae2-119">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="80ae2-120"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 証明書ストアを示す値です。</span><span class="sxs-lookup"><span data-stu-id="80ae2-120">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="80ae2-121">既定値は "LocalMachine" です。</span><span class="sxs-lookup"><span data-stu-id="80ae2-121">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="80ae2-122">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="80ae2-122">issuerCertificateValidator</span></span>|<span data-ttu-id="80ae2-123">から派生するカスタム型 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="80ae2-123">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="80ae2-124">`issuerCertificateValidationMode`属性が "Custom" の場合、この型のインスタンスは発行者の証明書の検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="80ae2-124">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80ae2-125">子要素</span><span class="sxs-lookup"><span data-stu-id="80ae2-125">Child Elements</span></span>  
  
|<span data-ttu-id="80ae2-126">要素</span><span class="sxs-lookup"><span data-stu-id="80ae2-126">Element</span></span>|<span data-ttu-id="80ae2-127">説明</span><span class="sxs-lookup"><span data-stu-id="80ae2-127">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="80ae2-128">プロパティを指定するクレームの種類を設定し <xref:System.Security.Principal.IIdentity.Name%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="80ae2-128">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="80ae2-129"><xref:System.Security.Claims.ClaimsIdentity>トークンハンドラーのメソッドによって返されるオブジェクトのコレクション内でのロールの種類の要求を定義する要求の種類を指定し <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="80ae2-129">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80ae2-130">親要素</span><span class="sxs-lookup"><span data-stu-id="80ae2-130">Parent Elements</span></span>  
  
|<span data-ttu-id="80ae2-131">要素</span><span class="sxs-lookup"><span data-stu-id="80ae2-131">Element</span></span>|<span data-ttu-id="80ae2-132">説明</span><span class="sxs-lookup"><span data-stu-id="80ae2-132">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="80ae2-133">指定されたセキュリティトークンハンドラーをトークンハンドラーコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="80ae2-133">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80ae2-134">解説</span><span class="sxs-lookup"><span data-stu-id="80ae2-134">Remarks</span></span>  

 <span data-ttu-id="80ae2-135">要素は、 `<samlSecurityTokenRequirement>` オブジェクトモデルのクラスによって表され、 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` またはでプロパティを構成するために使用され <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="80ae2-135">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80ae2-136">例</span><span class="sxs-lookup"><span data-stu-id="80ae2-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
