---
description: 詳細については <add> 、 <knownCertificates>
title: <add> の <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 1669495e6119a35543e39230fc5dcc986ee2dec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750287"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="dc035-103">\<add> の \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="dc035-103">\<add> of \<knownCertificates></span></span>

<span data-ttu-id="dc035-104">既知の証明書のコレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc035-104">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="dc035-105">構文</span><span class="sxs-lookup"><span data-stu-id="dc035-105">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc035-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dc035-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dc035-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc035-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc035-108">属性</span><span class="sxs-lookup"><span data-stu-id="dc035-108">Attributes</span></span>  
  
|<span data-ttu-id="dc035-109">属性</span><span class="sxs-lookup"><span data-stu-id="dc035-109">Attribute</span></span>|<span data-ttu-id="dc035-110">説明</span><span class="sxs-lookup"><span data-stu-id="dc035-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc035-111">findValue</span><span class="sxs-lookup"><span data-stu-id="dc035-111">findValue</span></span>|<span data-ttu-id="dc035-112">文字列 をオンにします。</span><span class="sxs-lookup"><span data-stu-id="dc035-112">String.</span></span> <span data-ttu-id="dc035-113">検索する値。</span><span class="sxs-lookup"><span data-stu-id="dc035-113">The value to search for.</span></span>|  
|<span data-ttu-id="dc035-114">storeLocation</span><span class="sxs-lookup"><span data-stu-id="dc035-114">storeLocation</span></span>|<span data-ttu-id="dc035-115">列挙値。</span><span class="sxs-lookup"><span data-stu-id="dc035-115">Enumeration.</span></span> <span data-ttu-id="dc035-116">検索する 2 つの格納場所のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="dc035-116">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="dc035-117">storeName</span><span class="sxs-lookup"><span data-stu-id="dc035-117">storeName</span></span>|<span data-ttu-id="dc035-118">列挙値。</span><span class="sxs-lookup"><span data-stu-id="dc035-118">Enumeration.</span></span> <span data-ttu-id="dc035-119">検索するシステム ストアのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="dc035-119">One of the system stores to search.</span></span>|  
|<span data-ttu-id="dc035-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="dc035-120">x509FindType</span></span>|<span data-ttu-id="dc035-121">列挙値。</span><span class="sxs-lookup"><span data-stu-id="dc035-121">Enumeration.</span></span> <span data-ttu-id="dc035-122">検索する証明書フィールドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="dc035-122">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="dc035-123">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="dc035-123">findValue Attribute</span></span>  
  
|<span data-ttu-id="dc035-124">値</span><span class="sxs-lookup"><span data-stu-id="dc035-124">Value</span></span>|<span data-ttu-id="dc035-125">説明</span><span class="sxs-lookup"><span data-stu-id="dc035-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dc035-126">String</span><span class="sxs-lookup"><span data-stu-id="dc035-126">String</span></span>|<span data-ttu-id="dc035-127">値は、検索されるフィールド (X509FindType 属性により指定される) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="dc035-127">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="dc035-128">たとえば、サムプリント検索する場合、値は 16 進数の文字列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc035-128">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="dc035-129">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="dc035-129">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="dc035-130">値</span><span class="sxs-lookup"><span data-stu-id="dc035-130">Value</span></span>|<span data-ttu-id="dc035-131">説明</span><span class="sxs-lookup"><span data-stu-id="dc035-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dc035-132">列挙</span><span class="sxs-lookup"><span data-stu-id="dc035-132">Enumeration</span></span>|<span data-ttu-id="dc035-133">値は、FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier です。</span><span class="sxs-lookup"><span data-stu-id="dc035-133">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="dc035-134">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="dc035-134">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="dc035-135">値</span><span class="sxs-lookup"><span data-stu-id="dc035-135">Value</span></span>|<span data-ttu-id="dc035-136">説明</span><span class="sxs-lookup"><span data-stu-id="dc035-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dc035-137">列挙</span><span class="sxs-lookup"><span data-stu-id="dc035-137">Enumeration</span></span>|<span data-ttu-id="dc035-138">CurrentUser または LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="dc035-138">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="dc035-139">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="dc035-139">storeName Attribute</span></span>  
  
|<span data-ttu-id="dc035-140">値</span><span class="sxs-lookup"><span data-stu-id="dc035-140">Value</span></span>|<span data-ttu-id="dc035-141">説明</span><span class="sxs-lookup"><span data-stu-id="dc035-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dc035-142">列挙</span><span class="sxs-lookup"><span data-stu-id="dc035-142">Enumeration</span></span>|<span data-ttu-id="dc035-143">値は、AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople、および TrustedPublisher です。</span><span class="sxs-lookup"><span data-stu-id="dc035-143">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc035-144">子要素</span><span class="sxs-lookup"><span data-stu-id="dc035-144">Child Elements</span></span>  

 <span data-ttu-id="dc035-145">なし。</span><span class="sxs-lookup"><span data-stu-id="dc035-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc035-146">親要素</span><span class="sxs-lookup"><span data-stu-id="dc035-146">Parent Elements</span></span>  
  
|<span data-ttu-id="dc035-147">要素</span><span class="sxs-lookup"><span data-stu-id="dc035-147">Element</span></span>|<span data-ttu-id="dc035-148">説明</span><span class="sxs-lookup"><span data-stu-id="dc035-148">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="dc035-149">セキュリティ トークンを検証するためのセキュリティ トークン サービス (STS) によって提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="dc035-149">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc035-150">解説</span><span class="sxs-lookup"><span data-stu-id="dc035-150">Remarks</span></span>  

 <span data-ttu-id="dc035-151">発行されるトークンのシナリオには、3 つの段階があります。</span><span class="sxs-lookup"><span data-stu-id="dc035-151">The issued token scenario has three stages.</span></span> <span data-ttu-id="dc035-152">最初の段階では、サービスにアクセスしようとしているクライアントは、 *セキュリティで保護されたトークンサービス* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="dc035-152">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="dc035-153">次に、セキュリティ トークン サービスがクライアントを認証し、その後、クライアントにトークン (通常は、SAML (Security Assertions Markup Language) トークン) を発行します。</span><span class="sxs-lookup"><span data-stu-id="dc035-153">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="dc035-154">最後に、クライアントがトークンを持ってサービスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dc035-154">The client then returns to the service with the token.</span></span> <span data-ttu-id="dc035-155">サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc035-155">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="dc035-156">トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc035-156">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="dc035-157">要素は、 [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) このようなセキュリティトークンサービス証明書のリポジトリです。</span><span class="sxs-lookup"><span data-stu-id="dc035-157">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="dc035-158">証明書を追加するには、を使用し [\<knownCertificates>](knowncertificates.md) ます。</span><span class="sxs-lookup"><span data-stu-id="dc035-158">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="dc035-159">次の例に示すように、各証明書の[ \<add> 要素 \<knownCertificates> 要素](add-of-knowncertificates.md)を挿入します。</span><span class="sxs-lookup"><span data-stu-id="dc035-159">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="dc035-160">既定では、証明書はセキュリティ トークン サービスから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc035-160">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="dc035-161">このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="dc035-161">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="dc035-162">フェデレーションサービスによってクライアントが認証されるために必要な条件を確認するには、「 [方法: フェデレーションサービスで資格情報を構成](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc035-162">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="dc035-163">フェデレーションシナリオの詳細については、「 [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc035-163">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc035-164">例</span><span class="sxs-lookup"><span data-stu-id="dc035-164">Example</span></span>  

 <span data-ttu-id="dc035-165">以下の例では、STS 証明書のリポジトリに証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc035-165">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="dc035-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc035-166">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="dc035-167">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="dc035-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="dc035-168">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="dc035-168">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dc035-169">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="dc035-169">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="dc035-170">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="dc035-170">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
