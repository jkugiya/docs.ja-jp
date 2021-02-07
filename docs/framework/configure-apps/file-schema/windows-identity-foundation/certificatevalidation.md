---
description: '詳細情報: <certificateValidation>'
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: a12e46487b4fb2ac8071ba1cf9bc5c6057ded060
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740068"
---
# \<certificateValidation>

<span data-ttu-id="cf83f-102">トークンハンドラーが証明書を検証するために使用する設定を制御します。</span><span class="sxs-lookup"><span data-stu-id="cf83f-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="cf83f-103">特定のハンドラーが独自の検証コントロールを使用して構成されている場合、これらの設定はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="cf83f-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="cf83f-104">構文</span><span class="sxs-lookup"><span data-stu-id="cf83f-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf83f-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cf83f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cf83f-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf83f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf83f-107">属性</span><span class="sxs-lookup"><span data-stu-id="cf83f-107">Attributes</span></span>  
  
|<span data-ttu-id="cf83f-108">属性</span><span class="sxs-lookup"><span data-stu-id="cf83f-108">Attribute</span></span>|<span data-ttu-id="cf83f-109">説明</span><span class="sxs-lookup"><span data-stu-id="cf83f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf83f-110">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="cf83f-110">certificateValidationMode</span></span>|<span data-ttu-id="cf83f-111"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X.509 証明書に使用する検証モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="cf83f-111">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cf83f-112">既定値は "PeerOrChainTrust" です。</span><span class="sxs-lookup"><span data-stu-id="cf83f-112">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="cf83f-113">カスタム検証を指定するには、この属性を "Custom" に設定し、要素を使用して検証コントロールを指定し [\<certificateValidator>](certificatevalidator.md) ます。</span><span class="sxs-lookup"><span data-stu-id="cf83f-113">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="cf83f-114">任意。</span><span class="sxs-lookup"><span data-stu-id="cf83f-114">Optional.</span></span>|  
|<span data-ttu-id="cf83f-115">revocationMode</span><span class="sxs-lookup"><span data-stu-id="cf83f-115">revocationMode</span></span>|<span data-ttu-id="cf83f-116"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X.509 証明書に使用する失効モードを指定する値。</span><span class="sxs-lookup"><span data-stu-id="cf83f-116">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cf83f-117">既定値は "Online" です。</span><span class="sxs-lookup"><span data-stu-id="cf83f-117">The default value is "Online".</span></span> <span data-ttu-id="cf83f-118">任意。</span><span class="sxs-lookup"><span data-stu-id="cf83f-118">Optional.</span></span>|  
|<span data-ttu-id="cf83f-119">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="cf83f-119">trustedStoreLocation</span></span>|<span data-ttu-id="cf83f-120"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 証明書ストアを示す値です。</span><span class="sxs-lookup"><span data-stu-id="cf83f-120">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="cf83f-121">既定値は "LocalMachine" です。</span><span class="sxs-lookup"><span data-stu-id="cf83f-121">The default value is "LocalMachine".</span></span> <span data-ttu-id="cf83f-122">任意。</span><span class="sxs-lookup"><span data-stu-id="cf83f-122">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf83f-123">子要素</span><span class="sxs-lookup"><span data-stu-id="cf83f-123">Child Elements</span></span>  
  
|<span data-ttu-id="cf83f-124">要素</span><span class="sxs-lookup"><span data-stu-id="cf83f-124">Element</span></span>|<span data-ttu-id="cf83f-125">説明</span><span class="sxs-lookup"><span data-stu-id="cf83f-125">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="cf83f-126">証明書の検証に使用するカスタムの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf83f-126">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="cf83f-127">この型は `certificateValidationMode` 、要素の属性 [\<certificateValidation>](certificatevalidation.md) が "Custom" に設定されている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf83f-127">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf83f-128">親要素</span><span class="sxs-lookup"><span data-stu-id="cf83f-128">Parent Elements</span></span>  
  
|<span data-ttu-id="cf83f-129">要素</span><span class="sxs-lookup"><span data-stu-id="cf83f-129">Element</span></span>|<span data-ttu-id="cf83f-130">説明</span><span class="sxs-lookup"><span data-stu-id="cf83f-130">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="cf83f-131">サービスレベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf83f-131">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="cf83f-132">セキュリティトークンハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="cf83f-132">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf83f-133">解説</span><span class="sxs-lookup"><span data-stu-id="cf83f-133">Remarks</span></span>  

 <span data-ttu-id="cf83f-134">要素は `<certificateValidation>` 、要素の下のサービスレベルで指定することも、 `<identityConfiguration>` 要素の下のセキュリティトークンハンドラーコレクションレベルで指定することもでき `<securityTokenHandlerConfiguration>` ます。</span><span class="sxs-lookup"><span data-stu-id="cf83f-134">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="cf83f-135">トークンハンドラーコレクションの設定は、サービスで指定された設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="cf83f-135">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="cf83f-136">一部のトークンハンドラーでは、構成で証明書の検証設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cf83f-136">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="cf83f-137">個々のトークンハンドラーの設定は、サービスレベルとセキュリティトークンハンドラーコレクションの両方で指定された設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="cf83f-137">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf83f-138">例</span><span class="sxs-lookup"><span data-stu-id="cf83f-138">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
