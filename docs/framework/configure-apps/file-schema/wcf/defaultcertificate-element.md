---
description: '詳細情報: <defaultCertificate> 要素'
title: <defaultCertificate> 要素
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 580236e521e91c8b475586f6c6378630960f233c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803920"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="431fe-103">\<defaultCertificate> 要素</span><span class="sxs-lookup"><span data-stu-id="431fe-103">\<defaultCertificate> Element</span></span>

<span data-ttu-id="431fe-104">ネゴシエーション プロトコル経由でサービスまたは STS が証明書を提供しないときに使用される X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="431fe-104">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="431fe-105">構文</span><span class="sxs-lookup"><span data-stu-id="431fe-105">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="431fe-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="431fe-106">Attributes and Elements</span></span>  

 <span data-ttu-id="431fe-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="431fe-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="431fe-108">属性</span><span class="sxs-lookup"><span data-stu-id="431fe-108">Attributes</span></span>  
  
|<span data-ttu-id="431fe-109">属性</span><span class="sxs-lookup"><span data-stu-id="431fe-109">Attribute</span></span>|<span data-ttu-id="431fe-110">説明</span><span class="sxs-lookup"><span data-stu-id="431fe-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="431fe-111">findValue</span><span class="sxs-lookup"><span data-stu-id="431fe-111">findValue</span></span>|<span data-ttu-id="431fe-112">文字列 をオンにします。</span><span class="sxs-lookup"><span data-stu-id="431fe-112">String.</span></span> <span data-ttu-id="431fe-113">検索する値。</span><span class="sxs-lookup"><span data-stu-id="431fe-113">The value to search for.</span></span>|  
|<span data-ttu-id="431fe-114">x509FindType</span><span class="sxs-lookup"><span data-stu-id="431fe-114">x509FindType</span></span>|<span data-ttu-id="431fe-115">列挙値。</span><span class="sxs-lookup"><span data-stu-id="431fe-115">Enumeration.</span></span> <span data-ttu-id="431fe-116">検索する証明書フィールドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="431fe-116">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="431fe-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="431fe-117">storeLocation</span></span>|<span data-ttu-id="431fe-118">列挙値。</span><span class="sxs-lookup"><span data-stu-id="431fe-118">Enumeration.</span></span> <span data-ttu-id="431fe-119">検索する 2 つのシステム格納場所のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="431fe-119">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="431fe-120">storeName</span><span class="sxs-lookup"><span data-stu-id="431fe-120">storeName</span></span>|<span data-ttu-id="431fe-121">列挙値。</span><span class="sxs-lookup"><span data-stu-id="431fe-121">Enumeration.</span></span> <span data-ttu-id="431fe-122">検索するシステム ストアのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="431fe-122">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="431fe-123">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="431fe-123">findValue Attribute</span></span>  
  
|<span data-ttu-id="431fe-124">値</span><span class="sxs-lookup"><span data-stu-id="431fe-124">Value</span></span>|<span data-ttu-id="431fe-125">説明</span><span class="sxs-lookup"><span data-stu-id="431fe-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="431fe-126">String</span><span class="sxs-lookup"><span data-stu-id="431fe-126">String</span></span>|<span data-ttu-id="431fe-127">値は、検索されるフィールド (X509FindType 属性により指定される) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="431fe-127">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="431fe-128">たとえば、サムプリント検索する場合、値は 16 進数の文字列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="431fe-128">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="431fe-129">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="431fe-129">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="431fe-130">値</span><span class="sxs-lookup"><span data-stu-id="431fe-130">Value</span></span>|<span data-ttu-id="431fe-131">説明</span><span class="sxs-lookup"><span data-stu-id="431fe-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="431fe-132">列挙</span><span class="sxs-lookup"><span data-stu-id="431fe-132">Enumeration</span></span>|<span data-ttu-id="431fe-133">値は、FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier です。</span><span class="sxs-lookup"><span data-stu-id="431fe-133">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="431fe-134">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="431fe-134">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="431fe-135">値</span><span class="sxs-lookup"><span data-stu-id="431fe-135">Value</span></span>|<span data-ttu-id="431fe-136">説明</span><span class="sxs-lookup"><span data-stu-id="431fe-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="431fe-137">列挙</span><span class="sxs-lookup"><span data-stu-id="431fe-137">Enumeration</span></span>|<span data-ttu-id="431fe-138">CurrentUser または LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="431fe-138">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="431fe-139">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="431fe-139">storeName Attribute</span></span>  
  
|<span data-ttu-id="431fe-140">値</span><span class="sxs-lookup"><span data-stu-id="431fe-140">Value</span></span>|<span data-ttu-id="431fe-141">説明</span><span class="sxs-lookup"><span data-stu-id="431fe-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="431fe-142">列挙</span><span class="sxs-lookup"><span data-stu-id="431fe-142">Enumeration</span></span>|<span data-ttu-id="431fe-143">値は、AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople、および TrustedPublisher です。</span><span class="sxs-lookup"><span data-stu-id="431fe-143">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="431fe-144">子要素</span><span class="sxs-lookup"><span data-stu-id="431fe-144">Child Elements</span></span>  

 <span data-ttu-id="431fe-145">なし。</span><span class="sxs-lookup"><span data-stu-id="431fe-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="431fe-146">親要素</span><span class="sxs-lookup"><span data-stu-id="431fe-146">Parent Elements</span></span>  
  
|<span data-ttu-id="431fe-147">要素</span><span class="sxs-lookup"><span data-stu-id="431fe-147">Element</span></span>|<span data-ttu-id="431fe-148">説明</span><span class="sxs-lookup"><span data-stu-id="431fe-148">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="431fe-149">クライアントに対してサービスを認証する際に使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="431fe-149">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="431fe-150">解説</span><span class="sxs-lookup"><span data-stu-id="431fe-150">Remarks</span></span>  

 <span data-ttu-id="431fe-151">証明書ベースのメッセージ セキュリティを使用するバインディングでは、この構成要素で指定された証明書を使用して、サービスへのメッセージが暗号化されます。この証明書は、サービスがクライアントへの応答に署名するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="431fe-151">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="431fe-152">この要素には、サービスで証明書が指定されていないときに使用する証明書を 1 つ格納できます。</span><span class="sxs-lookup"><span data-stu-id="431fe-152">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="431fe-153">例</span><span class="sxs-lookup"><span data-stu-id="431fe-153">Example</span></span>  

 <span data-ttu-id="431fe-154">次の例では、URI がで始まるエンドポイントに使用する証明書 `http://www.contoso.com` と、証明書ネゴシエーションを実行しない他のすべてのエンドポイントに使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="431fe-154">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="431fe-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="431fe-155">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="431fe-156">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="431fe-156">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="431fe-157">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="431fe-157">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="431fe-158">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="431fe-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
