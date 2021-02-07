---
description: '詳細情報: <certificateReference>'
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 3404d44457849fb78ae88617d049a2199f2b5509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681787"
---
# \<certificateReference>

<span data-ttu-id="ff86c-102">証明書ストアの x.509 証明書を検索して検証するために使用する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff86c-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="ff86c-103">構文</span><span class="sxs-lookup"><span data-stu-id="ff86c-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff86c-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ff86c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ff86c-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff86c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff86c-106">属性</span><span class="sxs-lookup"><span data-stu-id="ff86c-106">Attributes</span></span>  
  
|<span data-ttu-id="ff86c-107">属性</span><span class="sxs-lookup"><span data-stu-id="ff86c-107">Attribute</span></span>|<span data-ttu-id="ff86c-108">説明</span><span class="sxs-lookup"><span data-stu-id="ff86c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff86c-109">storeName</span><span class="sxs-lookup"><span data-stu-id="ff86c-109">storeName</span></span>|<span data-ttu-id="ff86c-110">X.509 証明書ストアの名前。</span><span class="sxs-lookup"><span data-stu-id="ff86c-110">The name of the X.509 certificate store.</span></span> <span data-ttu-id="ff86c-111">既定値は "My" です。</span><span class="sxs-lookup"><span data-stu-id="ff86c-111">The default is "My".</span></span> <span data-ttu-id="ff86c-112">任意。</span><span class="sxs-lookup"><span data-stu-id="ff86c-112">Optional.</span></span>|  
|<span data-ttu-id="ff86c-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="ff86c-113">storeLocation</span></span>|<span data-ttu-id="ff86c-114"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 証明書ストアの場所を示す値です。</span><span class="sxs-lookup"><span data-stu-id="ff86c-114">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="ff86c-115">既定値は "LocalMachine" です。</span><span class="sxs-lookup"><span data-stu-id="ff86c-115">The default value is "LocalMachine".</span></span> <span data-ttu-id="ff86c-116">任意。</span><span class="sxs-lookup"><span data-stu-id="ff86c-116">Optional.</span></span>|  
|<span data-ttu-id="ff86c-117">x509FindType</span><span class="sxs-lookup"><span data-stu-id="ff86c-117">x509FindType</span></span>|<span data-ttu-id="ff86c-118"><xref:System.Security.Cryptography.X509Certificates.X509FindType>実行する検索の種類を示す値です。</span><span class="sxs-lookup"><span data-stu-id="ff86c-118">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="ff86c-119">既定値は "Findbysubjectdistinguishedname です" です。</span><span class="sxs-lookup"><span data-stu-id="ff86c-119">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="ff86c-120">任意。</span><span class="sxs-lookup"><span data-stu-id="ff86c-120">Optional.</span></span>|  
|<span data-ttu-id="ff86c-121">findValue</span><span class="sxs-lookup"><span data-stu-id="ff86c-121">findValue</span></span>|<span data-ttu-id="ff86c-122">X.509 証明書ストアで検索する値。</span><span class="sxs-lookup"><span data-stu-id="ff86c-122">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="ff86c-123">任意。</span><span class="sxs-lookup"><span data-stu-id="ff86c-123">Optional.</span></span>|  
|<span data-ttu-id="ff86c-124">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="ff86c-124">isChainIncluded</span></span>|<span data-ttu-id="ff86c-125">証明書チェーンを使用して検証を実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ff86c-125">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="ff86c-126">既定値は "true" です。検証は、証明書チェーンを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="ff86c-126">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="ff86c-127">任意。</span><span class="sxs-lookup"><span data-stu-id="ff86c-127">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff86c-128">子要素</span><span class="sxs-lookup"><span data-stu-id="ff86c-128">Child Elements</span></span>  

 <span data-ttu-id="ff86c-129">なし</span><span class="sxs-lookup"><span data-stu-id="ff86c-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff86c-130">親要素</span><span class="sxs-lookup"><span data-stu-id="ff86c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="ff86c-131">要素</span><span class="sxs-lookup"><span data-stu-id="ff86c-131">Element</span></span>|<span data-ttu-id="ff86c-132">説明</span><span class="sxs-lookup"><span data-stu-id="ff86c-132">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="ff86c-133">トークンの暗号化と復号化に使用される証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="ff86c-133">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff86c-134">解説</span><span class="sxs-lookup"><span data-stu-id="ff86c-134">Remarks</span></span>  

 <span data-ttu-id="ff86c-135">要素は、 `<certificateReference>` 証明書ストア内の x.509 証明書の検索と検証に使用される設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff86c-135">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="ff86c-136">要素の子要素として指定されている場合は、 `<serviceCertificate>` トークンの暗号化と復号化に使用される x.509 証明書の場所と検証の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff86c-136">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="ff86c-137">`<certificateReference>`要素は、クラスによって表され <xref:System.ServiceModel.Configuration.CertificateReferenceElement> ます。</span><span class="sxs-lookup"><span data-stu-id="ff86c-137">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
