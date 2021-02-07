---
description: '詳細情報: <x509SecurityTokenHandlerRequirement>'
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 21a05cfeee6365bd677a6f35e984cb64fa4dd078
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748974"
---
# \<x509SecurityTokenHandlerRequirement>

<span data-ttu-id="f4117-102">クラスまたは派生クラスのオプションの構成を提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> します。</span><span class="sxs-lookup"><span data-stu-id="f4117-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="f4117-103">構文</span><span class="sxs-lookup"><span data-stu-id="f4117-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4117-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f4117-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f4117-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4117-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4117-106">属性</span><span class="sxs-lookup"><span data-stu-id="f4117-106">Attributes</span></span>  
  
|<span data-ttu-id="f4117-107">属性</span><span class="sxs-lookup"><span data-stu-id="f4117-107">Attribute</span></span>|<span data-ttu-id="f4117-108">説明</span><span class="sxs-lookup"><span data-stu-id="f4117-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4117-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="f4117-109">certificateValidationMode</span></span>|<span data-ttu-id="f4117-110"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X.509 証明書に使用する検証モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="f4117-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f4117-111">既定値は "PeerOrChainTrust" です。</span><span class="sxs-lookup"><span data-stu-id="f4117-111">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="f4117-112">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="f4117-112">mapToWindows</span></span>|<span data-ttu-id="f4117-113">受信 UPN 要求を使用して、トークンハンドラーが検証トークンを Windows アカウントにマップする必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f4117-113">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="f4117-114">既定値は "false" です。</span><span class="sxs-lookup"><span data-stu-id="f4117-114">The default is "false".</span></span>|  
|<span data-ttu-id="f4117-115">revocationMode</span><span class="sxs-lookup"><span data-stu-id="f4117-115">revocationMode</span></span>|<span data-ttu-id="f4117-116"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X.509 証明書に使用する失効モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="f4117-116">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f4117-117">既定値は "Online" です。</span><span class="sxs-lookup"><span data-stu-id="f4117-117">The default value is "Online".</span></span>|  
|<span data-ttu-id="f4117-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="f4117-118">trustedStoreLocation</span></span>|<span data-ttu-id="f4117-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 証明書ストアを示す値です。</span><span class="sxs-lookup"><span data-stu-id="f4117-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="f4117-120">既定値は "LocalMachine" です。</span><span class="sxs-lookup"><span data-stu-id="f4117-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="f4117-121">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="f4117-121">certificateValidator</span></span>|<span data-ttu-id="f4117-122">から派生するカスタム型 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="f4117-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="f4117-123">`certificateValidationMode`属性が "Custom" の場合、この型のインスタンスは発行者の証明書の検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4117-123">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4117-124">子要素</span><span class="sxs-lookup"><span data-stu-id="f4117-124">Child Elements</span></span>  

 <span data-ttu-id="f4117-125">なし</span><span class="sxs-lookup"><span data-stu-id="f4117-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4117-126">親要素</span><span class="sxs-lookup"><span data-stu-id="f4117-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f4117-127">要素</span><span class="sxs-lookup"><span data-stu-id="f4117-127">Element</span></span>|<span data-ttu-id="f4117-128">説明</span><span class="sxs-lookup"><span data-stu-id="f4117-128">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="f4117-129">指定されたセキュリティトークンハンドラーをトークンハンドラーコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f4117-129">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f4117-130">例</span><span class="sxs-lookup"><span data-stu-id="f4117-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
