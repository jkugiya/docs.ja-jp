---
description: '詳細情報: <knownCertificates>'
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 0180db56c775f4f6f17de8da58781c15a412bc81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802230"
---
# \<knownCertificates>

<span data-ttu-id="74ba0-102">セキュリティ トークン サービス (STS) から発行されるセキュリティ資格情報を認証するために提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="74ba0-103">構文</span><span class="sxs-lookup"><span data-stu-id="74ba0-103">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74ba0-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="74ba0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="74ba0-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74ba0-106">属性</span><span class="sxs-lookup"><span data-stu-id="74ba0-106">Attributes</span></span>  

 <span data-ttu-id="74ba0-107">なし。</span><span class="sxs-lookup"><span data-stu-id="74ba0-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74ba0-108">子要素</span><span class="sxs-lookup"><span data-stu-id="74ba0-108">Child Elements</span></span>  
  
|<span data-ttu-id="74ba0-109">要素</span><span class="sxs-lookup"><span data-stu-id="74ba0-109">Element</span></span>|<span data-ttu-id="74ba0-110">説明</span><span class="sxs-lookup"><span data-stu-id="74ba0-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="74ba0-111">コレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-111">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74ba0-112">親要素</span><span class="sxs-lookup"><span data-stu-id="74ba0-112">Parent Elements</span></span>  
  
|<span data-ttu-id="74ba0-113">要素</span><span class="sxs-lookup"><span data-stu-id="74ba0-113">Element</span></span>|<span data-ttu-id="74ba0-114">説明</span><span class="sxs-lookup"><span data-stu-id="74ba0-114">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="74ba0-115">サービス資格情報として発行されるトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-115">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74ba0-116">解説</span><span class="sxs-lookup"><span data-stu-id="74ba0-116">Remarks</span></span>  

 <span data-ttu-id="74ba0-117">発行されるトークンのシナリオには、3 つの段階があります。</span><span class="sxs-lookup"><span data-stu-id="74ba0-117">The issued token scenario has three stages.</span></span> <span data-ttu-id="74ba0-118">最初の段階では、サービスにアクセスしようとしているクライアントは、 *セキュリティで保護されたトークンサービス* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="74ba0-118">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="74ba0-119">次に、セキュリティ トークン サービスがクライアントを認証し、その後、クライアントにトークン (通常は、SAML (Security Assertions Markup Language) トークン) を発行します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-119">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="74ba0-120">最後に、クライアントがトークンを持ってサービスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="74ba0-120">The client then returns to the service with the token.</span></span> <span data-ttu-id="74ba0-121">サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-121">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="74ba0-122">トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="74ba0-122">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="74ba0-123">要素は、 [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) このようなセキュリティトークンサービス証明書のリポジトリです。</span><span class="sxs-lookup"><span data-stu-id="74ba0-123">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="74ba0-124">証明書を追加するには、 [ \<knownCertificates> 要素](knowncertificates.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-124">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="74ba0-125">次の [\<add>](add-of-knowncertificates.md) 例に示すように、各証明書のを挿入します。</span><span class="sxs-lookup"><span data-stu-id="74ba0-125">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="74ba0-126">既定では、証明書はセキュリティ トークン サービスから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74ba0-126">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="74ba0-127">このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="74ba0-127">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="74ba0-128">フェデレーションサービスによってクライアントが認証されるために必要な条件を確認するには、「 [方法: フェデレーションサービスで資格情報を構成](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74ba0-128">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="74ba0-129">フェデレーションシナリオの詳細については、「 [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74ba0-129">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="74ba0-130">構成のコレクションにデータを設定する方法を示す例については、「」を参照してください [\<add>](add-of-knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="74ba0-130">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ba0-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="74ba0-131">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="74ba0-132">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="74ba0-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="74ba0-133">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="74ba0-133">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="74ba0-134">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="74ba0-134">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="74ba0-135">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="74ba0-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="74ba0-136">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="74ba0-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
