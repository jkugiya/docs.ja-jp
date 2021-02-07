---
description: '詳細については、次を参照してください: <add> of <scopedCertificates> 要素'
title: <add><scopedCertificates>要素の
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 4c267164ccf065edee79a6aaaa9aaddc14d95909
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750274"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="98389-103">\<add>\<scopedCertificates>要素の</span><span class="sxs-lookup"><span data-stu-id="98389-103">\<add> of \<scopedCertificates> Element</span></span>

<span data-ttu-id="98389-104">範囲指定された証明書のコレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="98389-104">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="98389-105">構文</span><span class="sxs-lookup"><span data-stu-id="98389-105">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98389-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="98389-106">Attributes and Elements</span></span>  

 <span data-ttu-id="98389-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="98389-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98389-108">属性</span><span class="sxs-lookup"><span data-stu-id="98389-108">Attributes</span></span>  
  
|<span data-ttu-id="98389-109">属性</span><span class="sxs-lookup"><span data-stu-id="98389-109">Attribute</span></span>|<span data-ttu-id="98389-110">説明</span><span class="sxs-lookup"><span data-stu-id="98389-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98389-111">targetUri</span><span class="sxs-lookup"><span data-stu-id="98389-111">targetUri</span></span>|<span data-ttu-id="98389-112">文字列 をオンにします。</span><span class="sxs-lookup"><span data-stu-id="98389-112">String.</span></span> <span data-ttu-id="98389-113">証明書に関連付けられているサービスの URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="98389-113">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="98389-114">findValue</span><span class="sxs-lookup"><span data-stu-id="98389-114">findValue</span></span>|<span data-ttu-id="98389-115">文字列 をオンにします。</span><span class="sxs-lookup"><span data-stu-id="98389-115">String.</span></span> <span data-ttu-id="98389-116">検索する値。</span><span class="sxs-lookup"><span data-stu-id="98389-116">The value to search for.</span></span>|  
|<span data-ttu-id="98389-117">x509FindType</span><span class="sxs-lookup"><span data-stu-id="98389-117">x509FindType</span></span>|<span data-ttu-id="98389-118">列挙値。</span><span class="sxs-lookup"><span data-stu-id="98389-118">Enumeration.</span></span> <span data-ttu-id="98389-119">検索する証明書フィールドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="98389-119">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="98389-120">storeLocation</span><span class="sxs-lookup"><span data-stu-id="98389-120">storeLocation</span></span>|<span data-ttu-id="98389-121">列挙値。</span><span class="sxs-lookup"><span data-stu-id="98389-121">Enumeration.</span></span> <span data-ttu-id="98389-122">検索する 2 つの格納場所のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="98389-122">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="98389-123">storeName</span><span class="sxs-lookup"><span data-stu-id="98389-123">storeName</span></span>|<span data-ttu-id="98389-124">列挙値。</span><span class="sxs-lookup"><span data-stu-id="98389-124">Enumeration.</span></span> <span data-ttu-id="98389-125">検索するシステム ストアのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="98389-125">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="98389-126">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="98389-126">findValue Attribute</span></span>  
  
|<span data-ttu-id="98389-127">値</span><span class="sxs-lookup"><span data-stu-id="98389-127">Value</span></span>|<span data-ttu-id="98389-128">説明</span><span class="sxs-lookup"><span data-stu-id="98389-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98389-129">String</span><span class="sxs-lookup"><span data-stu-id="98389-129">String</span></span>|<span data-ttu-id="98389-130">値は、検索されるフィールド (X509FindType 属性により指定される) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="98389-130">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="98389-131">たとえば、サムプリント検索する場合、値は 16 進数の文字列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98389-131">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="98389-132">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="98389-132">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="98389-133">値</span><span class="sxs-lookup"><span data-stu-id="98389-133">Value</span></span>|<span data-ttu-id="98389-134">説明</span><span class="sxs-lookup"><span data-stu-id="98389-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98389-135">列挙</span><span class="sxs-lookup"><span data-stu-id="98389-135">Enumeration</span></span>|<span data-ttu-id="98389-136">値は、FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier です。</span><span class="sxs-lookup"><span data-stu-id="98389-136">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="98389-137">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="98389-137">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="98389-138">値</span><span class="sxs-lookup"><span data-stu-id="98389-138">Value</span></span>|<span data-ttu-id="98389-139">説明</span><span class="sxs-lookup"><span data-stu-id="98389-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98389-140">列挙</span><span class="sxs-lookup"><span data-stu-id="98389-140">Enumeration</span></span>|<span data-ttu-id="98389-141">CurrentUser または LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="98389-141">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="98389-142">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="98389-142">storeName Attribute</span></span>  
  
|<span data-ttu-id="98389-143">値</span><span class="sxs-lookup"><span data-stu-id="98389-143">Value</span></span>|<span data-ttu-id="98389-144">説明</span><span class="sxs-lookup"><span data-stu-id="98389-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98389-145">列挙</span><span class="sxs-lookup"><span data-stu-id="98389-145">Enumeration</span></span>|<span data-ttu-id="98389-146">値は、AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople、および TrustedPublisher です。</span><span class="sxs-lookup"><span data-stu-id="98389-146">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98389-147">子要素</span><span class="sxs-lookup"><span data-stu-id="98389-147">Child Elements</span></span>  

 <span data-ttu-id="98389-148">なし。</span><span class="sxs-lookup"><span data-stu-id="98389-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98389-149">親要素</span><span class="sxs-lookup"><span data-stu-id="98389-149">Parent Elements</span></span>  
  
|<span data-ttu-id="98389-150">要素</span><span class="sxs-lookup"><span data-stu-id="98389-150">Element</span></span>|<span data-ttu-id="98389-151">説明</span><span class="sxs-lookup"><span data-stu-id="98389-151">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="98389-152">認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="98389-152">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98389-153">解説</span><span class="sxs-lookup"><span data-stu-id="98389-153">Remarks</span></span>  

 <span data-ttu-id="98389-154">この要素を使用すると、クライアントは、通信するサービスの URL に基づいて、使用するサービス証明書を構成できます。</span><span class="sxs-lookup"><span data-stu-id="98389-154">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="98389-155">これは、クライアントが複数のサービス (エンド サービスと中間セキュリティ トークン サービス) と通信している可能性がある発行済みトークンのシナリオで特に便利です。</span><span class="sxs-lookup"><span data-stu-id="98389-155">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="98389-156">証明書に基づくメッセージ セキュリティを使用したバインドにおいて、この証明書を使用してサービスへのメッセージを暗号化します。サービスがクライアントへの応答に署名する際には、この証明書を使用することが要求されます。</span><span class="sxs-lookup"><span data-stu-id="98389-156">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="98389-157">バインディングにサービスの証明書が必要で、サービスの URL に対する特定の証明書が ScopedCertificates 内に存在しない場合は、既定の証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="98389-157">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="98389-158">詳細については、「 [方法: フェデレーションクライアントを作成](../../../wcf/feature-details/how-to-create-a-federated-client.md)する」の「スコープ付き証明書」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="98389-158">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98389-159">例</span><span class="sxs-lookup"><span data-stu-id="98389-159">Example</span></span>  

 <span data-ttu-id="98389-160">次の例は、コレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="98389-160">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="98389-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="98389-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="98389-162">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="98389-162">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="98389-163">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="98389-163">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="98389-164">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="98389-164">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="98389-165">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="98389-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
