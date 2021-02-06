---
description: '詳細については、次を参照してください: <clientCertificate> of <clientCredentials> 要素'
title: <clientCertificate><clientCredentials>要素の
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: 4305b94e62c76436a6bce91251049b3eebd2db2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638835"
---
# <a name="clientcertificate-of-clientcredentials-element"></a><span data-ttu-id="3f360-103">\<clientCertificate>\<clientCredentials>要素の</span><span class="sxs-lookup"><span data-stu-id="3f360-103">\<clientCertificate> of \<clientCredentials> Element</span></span>

<span data-ttu-id="3f360-104">サービスに対するクライアントの認証に使用する X.509 証明書を定義します。</span><span class="sxs-lookup"><span data-stu-id="3f360-104">Defines an X.509 certificate used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="3f360-105">構文</span><span class="sxs-lookup"><span data-stu-id="3f360-105">Syntax</span></span>  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f360-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3f360-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3f360-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f360-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f360-108">属性</span><span class="sxs-lookup"><span data-stu-id="3f360-108">Attributes</span></span>  
  
|<span data-ttu-id="3f360-109">属性</span><span class="sxs-lookup"><span data-stu-id="3f360-109">Attribute</span></span>|<span data-ttu-id="3f360-110">説明</span><span class="sxs-lookup"><span data-stu-id="3f360-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="3f360-111">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="3f360-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="3f360-112">属性に格納されている型は、`X509FindType` 属性値の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f360-112">The type contained in the attribute must satisfy the requirements of the `X509FindType` attribute value.</span></span> <span data-ttu-id="3f360-113">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="3f360-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="3f360-114">クライアントがサービスに対して自身を認証するために使用する X.509 証明書の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f360-114">Specifies the location of the X.509 certificate that the client uses to authenticate itself to the service.</span></span> <span data-ttu-id="3f360-115">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f360-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3f360-116">-LocalMachine: ローカルコンピューターに割り当てられた証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="3f360-117">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="3f360-118">既定値は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="3f360-118">The default is LocalMachine.</span></span> <span data-ttu-id="3f360-119">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="3f360-119">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|`storeName`|<span data-ttu-id="3f360-120">検索する X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f360-120">Specifies the name of the X.509 certificate store to search.</span></span> <span data-ttu-id="3f360-121">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f360-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3f360-122">-アドレス帳: 他のユーザーの証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-122">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="3f360-123">-AuthRoot: サードパーティの証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-123">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="3f360-124">-CertificateAuthority: 中間証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-124">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="3f360-125">-許可されていません: 失効した証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-125">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="3f360-126">-My: 個人証明書の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-126">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="3f360-127">-Root: 信頼されたルート証明機関 (Ca) の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-127">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="3f360-128">-TrustedPeople: 直接信頼されている人間とリソースの証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-128">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="3f360-129">-TrustedPublisher: 直接信頼された発行元の証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="3f360-129">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="3f360-130">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="3f360-130">The default is My.</span></span> <span data-ttu-id="3f360-131">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreName> 型です。</span><span class="sxs-lookup"><span data-stu-id="3f360-131">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="3f360-132">X509FindType</span><span class="sxs-lookup"><span data-stu-id="3f360-132">X509FindType</span></span>|<span data-ttu-id="3f360-133">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="3f360-133">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="3f360-134">`findValue` 属性に格納されている型は、この属性の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f360-134">The type contained in the `findValue` attribute must satisfy the requirements of this attribute.</span></span> <span data-ttu-id="3f360-135">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f360-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3f360-136">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="3f360-136">-   FindByThumbPrint</span></span><br /><span data-ttu-id="3f360-137">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="3f360-137">-   FindBySubjectName</span></span><br /><span data-ttu-id="3f360-138">-Findbysubjectdistinguishedname です</span><span class="sxs-lookup"><span data-stu-id="3f360-138">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="3f360-139">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="3f360-139">-   FindByIssuerName</span></span><br /><span data-ttu-id="3f360-140">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3f360-140">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="3f360-141">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="3f360-141">-   FindBySerialNumber</span></span><br /><span data-ttu-id="3f360-142">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="3f360-142">-   FindByTimeValid</span></span><br /><span data-ttu-id="3f360-143">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="3f360-143">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="3f360-144">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="3f360-144">-   FindByTemplateName</span></span><br /><span data-ttu-id="3f360-145">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="3f360-145">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="3f360-146">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3f360-146">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="3f360-147">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="3f360-147">-   FindByExtension</span></span><br /><span data-ttu-id="3f360-148">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="3f360-148">-   FindByKeyUsage</span></span><br /><span data-ttu-id="3f360-149">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="3f360-149">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="3f360-150">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="3f360-150">The default value is FindBySubjectDistinguishedName.</span></span> <span data-ttu-id="3f360-151">この属性は <xref:System.Security.Cryptography.X509Certificates.X509FindType> 型です。</span><span class="sxs-lookup"><span data-stu-id="3f360-151">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f360-152">子要素</span><span class="sxs-lookup"><span data-stu-id="3f360-152">Child Elements</span></span>  

 <span data-ttu-id="3f360-153">なし。</span><span class="sxs-lookup"><span data-stu-id="3f360-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f360-154">親要素</span><span class="sxs-lookup"><span data-stu-id="3f360-154">Parent Elements</span></span>  
  
|<span data-ttu-id="3f360-155">要素</span><span class="sxs-lookup"><span data-stu-id="3f360-155">Element</span></span>|<span data-ttu-id="3f360-156">説明</span><span class="sxs-lookup"><span data-stu-id="3f360-156">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="3f360-157">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f360-157">Specifies the credentials used to authenticate the client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f360-158">解説</span><span class="sxs-lookup"><span data-stu-id="3f360-158">Remarks</span></span>  

 <span data-ttu-id="3f360-159">この構成要素は、この要素によるクライアントの認証に使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f360-159">This configuration element specifies the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="3f360-160">詳細については、「 [方法: クライアント資格情報の値を指定する](../../../wcf/how-to-specify-client-credential-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f360-160">For more information, see [How to: Specify Client Credential Values](../../../wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f360-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f360-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="3f360-162">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="3f360-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3f360-163">方法: クライアントの資格情報の値を指定する</span><span class="sxs-lookup"><span data-stu-id="3f360-163">How to: Specify Client Credential Values</span></span>](../../../wcf/how-to-specify-client-credential-values.md)
- [<span data-ttu-id="3f360-164">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3f360-164">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="3f360-165">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="3f360-165">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3f360-166">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3f360-166">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
