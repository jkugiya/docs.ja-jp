---
description: '詳細については、次を参照してください: <authentication> of <serviceCertificate> 要素'
title: <authentication><serviceCertificate>要素の
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 35a94f4f9c089f86aef38e7e9a1115a7cd22a325
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749884"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="93ae5-103">\<authentication>\<serviceCertificate>要素の</span><span class="sxs-lookup"><span data-stu-id="93ae5-103">\<authentication> of \<serviceCertificate> Element</span></span>

<span data-ttu-id="93ae5-104">SSL/TLS ネゴシエーションを使用して取得されたサービス証明書を認証するためにクライアント プロキシが使用する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-104">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="93ae5-105">構文</span><span class="sxs-lookup"><span data-stu-id="93ae5-105">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93ae5-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="93ae5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="93ae5-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93ae5-108">属性</span><span class="sxs-lookup"><span data-stu-id="93ae5-108">Attributes</span></span>  
  
|<span data-ttu-id="93ae5-109">属性</span><span class="sxs-lookup"><span data-stu-id="93ae5-109">Attribute</span></span>|<span data-ttu-id="93ae5-110">説明</span><span class="sxs-lookup"><span data-stu-id="93ae5-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93ae5-111">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="93ae5-111">customCertificateValidatorType</span></span>|<span data-ttu-id="93ae5-112">文字列 をオンにします。</span><span class="sxs-lookup"><span data-stu-id="93ae5-112">String.</span></span> <span data-ttu-id="93ae5-113">カスタム型の検証に使用される型およびアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="93ae5-113">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="93ae5-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="93ae5-114">certificateValidationMode</span></span>|<span data-ttu-id="93ae5-115">資格情報の検証に使用される 3 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="93ae5-116">`Custom` に設定されている場合、customCertificateValidator も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93ae5-116">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="93ae5-117">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="93ae5-117">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="93ae5-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="93ae5-118">revocationMode</span></span>|<span data-ttu-id="93ae5-119">証明書失効リスト (CRL) のチェックに使用されるモードのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="93ae5-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="93ae5-120">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="93ae5-120">The default is `Online`.</span></span>|  
|<span data-ttu-id="93ae5-121">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="93ae5-121">trustedStoreLocation</span></span>|<span data-ttu-id="93ae5-122">2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="93ae5-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="93ae5-123">この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="93ae5-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="93ae5-124">指定されたストアの場所にある **信頼さ** れた People ストアに対して検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="93ae5-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="93ae5-125">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="93ae5-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="93ae5-126">customCertificateValidator 属性</span><span class="sxs-lookup"><span data-stu-id="93ae5-126">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="93ae5-127">値</span><span class="sxs-lookup"><span data-stu-id="93ae5-127">Value</span></span>|<span data-ttu-id="93ae5-128">説明</span><span class="sxs-lookup"><span data-stu-id="93ae5-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93ae5-129">String</span><span class="sxs-lookup"><span data-stu-id="93ae5-129">String</span></span>|<span data-ttu-id="93ae5-130">タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-130">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="93ae5-131">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="93ae5-131">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="93ae5-132">値</span><span class="sxs-lookup"><span data-stu-id="93ae5-132">Value</span></span>|<span data-ttu-id="93ae5-133">説明</span><span class="sxs-lookup"><span data-stu-id="93ae5-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93ae5-134">列挙</span><span class="sxs-lookup"><span data-stu-id="93ae5-134">Enumeration</span></span>|<span data-ttu-id="93ae5-135">None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="93ae5-135">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="93ae5-136">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93ae5-136">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="93ae5-137">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="93ae5-137">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="93ae5-138">値</span><span class="sxs-lookup"><span data-stu-id="93ae5-138">Value</span></span>|<span data-ttu-id="93ae5-139">説明</span><span class="sxs-lookup"><span data-stu-id="93ae5-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93ae5-140">列挙</span><span class="sxs-lookup"><span data-stu-id="93ae5-140">Enumeration</span></span>|<span data-ttu-id="93ae5-141">NoCheck、Online、Offline のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="93ae5-141">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="93ae5-142">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93ae5-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="93ae5-143">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="93ae5-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="93ae5-144">値</span><span class="sxs-lookup"><span data-stu-id="93ae5-144">Value</span></span>|<span data-ttu-id="93ae5-145">説明</span><span class="sxs-lookup"><span data-stu-id="93ae5-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93ae5-146">列挙</span><span class="sxs-lookup"><span data-stu-id="93ae5-146">Enumeration</span></span>|<span data-ttu-id="93ae5-147">LocalMachine または CurrentUser のいずれかの値。</span><span class="sxs-lookup"><span data-stu-id="93ae5-147">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="93ae5-148">既定の値は CurrentUser です。</span><span class="sxs-lookup"><span data-stu-id="93ae5-148">The default is CurrentUser.</span></span> <span data-ttu-id="93ae5-149">クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 LocalMachine の下にあります。</span><span class="sxs-lookup"><span data-stu-id="93ae5-149">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="93ae5-150">クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 CurrentUser の下にあります。</span><span class="sxs-lookup"><span data-stu-id="93ae5-150">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93ae5-151">子要素</span><span class="sxs-lookup"><span data-stu-id="93ae5-151">Child Elements</span></span>  

 <span data-ttu-id="93ae5-152">なし。</span><span class="sxs-lookup"><span data-stu-id="93ae5-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93ae5-153">親要素</span><span class="sxs-lookup"><span data-stu-id="93ae5-153">Parent Elements</span></span>  
  
|<span data-ttu-id="93ae5-154">要素</span><span class="sxs-lookup"><span data-stu-id="93ae5-154">Element</span></span>|<span data-ttu-id="93ae5-155">説明</span><span class="sxs-lookup"><span data-stu-id="93ae5-155">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="93ae5-156">クライアントに対してサービスを認証する際に使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93ae5-157">解説</span><span class="sxs-lookup"><span data-stu-id="93ae5-157">Remarks</span></span>  

 <span data-ttu-id="93ae5-158">この構成要素の `certificateValidationMode` 属性は、証明書の認証に使用される信頼レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-158">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="93ae5-159">既定のレベルは `ChainTrust` に設定され、チェーンの最上位の信頼された証明機関で終了する証明書の階層構造で各証明書を検索するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-159">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="93ae5-160">これは最もセキュリティで保護されているモードです。</span><span class="sxs-lookup"><span data-stu-id="93ae5-160">This is the most secure mode.</span></span> <span data-ttu-id="93ae5-161">また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れるよう指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-161">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="93ae5-162">自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。</span><span class="sxs-lookup"><span data-stu-id="93ae5-162">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="93ae5-163">クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-163">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="93ae5-164">値を `Custom` または `None` に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="93ae5-164">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="93ae5-165">`Custom` 値を使用するには、`customCertificateValidator` 属性を証明書の検証に使用するアセンブリと型に設定することも必要です。</span><span class="sxs-lookup"><span data-stu-id="93ae5-165">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="93ae5-166">独自のカスタム検証を作成するには、抽象 X509CertificateValidator クラスを継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93ae5-166">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="93ae5-167">詳細については、「 [方法: カスタム証明書検証を使用するサービスを作成](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93ae5-167">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="93ae5-168">`revocationMode` 属性は、証明書が失効していないかどうかをチェックする方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-168">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="93ae5-169">既定値は `online` です。この場合、証明書が失効していないかどうかを自動的にチェックします。</span><span class="sxs-lookup"><span data-stu-id="93ae5-169">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="93ae5-170">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93ae5-170">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ae5-171">例</span><span class="sxs-lookup"><span data-stu-id="93ae5-171">Example</span></span>  

 <span data-ttu-id="93ae5-172">次の例は、2 つのタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-172">The following example does two tasks.</span></span> <span data-ttu-id="93ae5-173">まず、クライアントが HTTP プロトコル経由でドメイン名を持つエンドポイントと通信するときに使用するサービス証明書を指定し `www.contoso.com` ます。</span><span class="sxs-lookup"><span data-stu-id="93ae5-173">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="93ae5-174">次に、認証中に使用される失効モードとストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="93ae5-174">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93ae5-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="93ae5-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="93ae5-176">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="93ae5-176">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="93ae5-177">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="93ae5-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="93ae5-178">方法: カスタム証明書検証を使用するサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="93ae5-178">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="93ae5-179">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="93ae5-179">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="93ae5-180">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="93ae5-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
