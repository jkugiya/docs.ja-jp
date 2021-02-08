---
description: 詳細については、「WCF でのセキュリティの動作」を参照してください。
title: Windows Communication Foundation のセキュリティ動作
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: a9ebdc44b3770ab4d0cf931db4bf23c9a4cd8e4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779856"
---
# <a name="security-behaviors-in-wcf"></a><span data-ttu-id="35265-103">Windows Communication Foundation のセキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="35265-103">Security Behaviors in WCF</span></span>

<span data-ttu-id="35265-104">Windows Communication Foundation (WCF) では、動作によって、サービスレベルまたはエンドポイントレベルで実行時の動作が変更されます。</span><span class="sxs-lookup"><span data-stu-id="35265-104">In Windows Communication Foundation (WCF), behaviors modify run-time behavior at the service level or at the endpoint level.</span></span> <span data-ttu-id="35265-105">(一般的な動作の詳細については、「 [サービス Run-Time 動作の指定](../specifying-service-run-time-behavior.md)」を参照してください)。 *セキュリティの動作* により、資格情報、認証、承認、および監査ログの制御が可能になります。</span><span class="sxs-lookup"><span data-stu-id="35265-105">(For more information about behaviors in general, see [Specifying Service Run-Time Behavior](../specifying-service-run-time-behavior.md).) *Security behaviors* allow control over credentials, authentication, authorization, and auditing logs.</span></span> <span data-ttu-id="35265-106">動作は、プログラムまたは構成を通じて使用できます。</span><span class="sxs-lookup"><span data-stu-id="35265-106">You can use behaviors either by programming or through configuration.</span></span> <span data-ttu-id="35265-107">ここでは、セキュリティ機能に関連する以下の動作の構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="35265-107">This topic focuses on configuring the following behaviors related to security functions:</span></span>  
  
- <span data-ttu-id="35265-108">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="35265-108">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
- <span data-ttu-id="35265-109">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="35265-109">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span></span>  
  
- <span data-ttu-id="35265-110">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span><span class="sxs-lookup"><span data-stu-id="35265-110">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span></span>  
  
- <span data-ttu-id="35265-111">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span><span class="sxs-lookup"><span data-stu-id="35265-111">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span></span>  
  
- <span data-ttu-id="35265-112">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md)。クライアントがメタデータにアクセスできるセキュリティで保護されたエンドポイントを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="35265-112">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md), which also enables you to specify a secure endpoint that clients can access for metadata.</span></span>  
  
## <a name="setting-credentials-with-behaviors"></a><span data-ttu-id="35265-113">動作を使用した資格情報の設定</span><span class="sxs-lookup"><span data-stu-id="35265-113">Setting Credentials with Behaviors</span></span>  

 <span data-ttu-id="35265-114">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) サービスまたはクライアントの資格情報の値を設定するには、およびを使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-114">Use the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) and [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) to set credential values for a service or client.</span></span> <span data-ttu-id="35265-115">基になるバインド構成によって、資格情報を設定する必要があるかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="35265-115">The underlying binding configuration determines whether a credential has to be set.</span></span> <span data-ttu-id="35265-116">たとえば、セキュリティ モードが `None` に設定されている場合、クライアントとサービスは相互に認証を行わないため、どの種類の資格情報も必要ありません。</span><span class="sxs-lookup"><span data-stu-id="35265-116">For example, if the security mode is set to `None`, both clients and services do not authenticate each other and require no credentials of any type.</span></span>  
  
 <span data-ttu-id="35265-117">一方、サービス バインディングでは、クライアント資格情報の種類が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="35265-117">On the other hand, the service binding can require a client credential type.</span></span> <span data-ttu-id="35265-118">その場合は、動作を使用して資格情報の値を設定することが必要になる場合があります </span><span class="sxs-lookup"><span data-stu-id="35265-118">In that case, you may have to set a credential value using a behavior.</span></span> <span data-ttu-id="35265-119">(使用できる資格情報の種類の詳細については、「資格情報の [種類の選択](selecting-a-credential-type.md)」を参照してください)。場合によっては、Windows 資格情報を使用して認証するときに、環境によって実際の資格情報の値が自動的に設定されます。資格情報の別のセットを指定しない限り、資格情報の値を明示的に設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="35265-119">(For more information about the possible types of credentials, see [Selecting a Credential Type](selecting-a-credential-type.md).) In some cases, such as when Windows credentials are used to authenticate, the environment automatically establishes the actual credential value and you do not need to explicitly set the credential value (unless you want to specify a different set of credentials).</span></span>  
  
 <span data-ttu-id="35265-120">すべてのサービス資格情報は、の子要素として検出され [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) ます。</span><span class="sxs-lookup"><span data-stu-id="35265-120">All service credentials are found as child elements of the [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md).</span></span> <span data-ttu-id="35265-121">サービス資格情報として使用される証明書を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="35265-121">The following example shows a certificate used as a service credential.</span></span>  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a><span data-ttu-id="35265-122">サービス資格情報</span><span class="sxs-lookup"><span data-stu-id="35265-122">Service Credentials</span></span>  

 <span data-ttu-id="35265-123">には、 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 4 つの子要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="35265-123">The [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) contains four child elements.</span></span> <span data-ttu-id="35265-124">以下のセクションでは、これらの要素とそれぞれの使い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="35265-124">The elements and their usages are discussed in the following sections.</span></span>  
  
### <a name="servicecertificate-element"></a><span data-ttu-id="35265-125">\<serviceCertificate> 要素</span><span class="sxs-lookup"><span data-stu-id="35265-125">\<serviceCertificate> Element</span></span>  

 <span data-ttu-id="35265-126">メッセージ セキュリティ モードを使用しているクライアントへのサービスの認証に使用する X.509 証明書を指定するには、この要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-126">Use this element to specify an X.509 certificate that is used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="35265-127">定期的に更新される証明書を使用している場合は、証明書のサムプリントが変更されます。</span><span class="sxs-lookup"><span data-stu-id="35265-127">If you are using a certificate that is periodically renewed, then its thumbprint changes.</span></span> <span data-ttu-id="35265-128">その場合、証明書を同じサブジェクト名で再発行できるため、`X509FindType` としてサブジェクト名を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-128">In that case, use the subject name as the `X509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 <span data-ttu-id="35265-129">要素の使用方法の詳細については、「 [方法: クライアント資格情報の値を指定する](../how-to-specify-client-credential-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-129">For more information about using the element, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
### <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="35265-130">\<certificate>\<clientCertificate>要素の</span><span class="sxs-lookup"><span data-stu-id="35265-130">\<certificate> of \<clientCertificate> Element</span></span>  

 <span data-ttu-id="35265-131">サービスがクライアント [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) と安全に通信するためにクライアントの証明書を事前に持っている必要がある場合は、要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-131">Use the [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) element when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="35265-132">このような状況は、双方向通信パターンを使用する場合に生じます。</span><span class="sxs-lookup"><span data-stu-id="35265-132">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="35265-133">より一般的な要求/応答パターンでは、クライアントが自身の証明書を要求に含め、サービスはこの証明書を使用して、クライアントへの応答をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="35265-133">In the more typical request-reply pattern, the client includes its certificate in the request, which the service uses to secure its response back to the client.</span></span> <span data-ttu-id="35265-134">ただし、双方向通信パターンには要求も応答もありません。</span><span class="sxs-lookup"><span data-stu-id="35265-134">The duplex communication pattern, however, has no requests and replies.</span></span> <span data-ttu-id="35265-135">サービスは、クライアントの証明書を通信から推測できないため、クライアントへのメッセージをセキュリティで保護するためにクライアントの証明書が前もって必要になります。</span><span class="sxs-lookup"><span data-stu-id="35265-135">The service cannot infer the client's certificate from the communication and therefore the service requires the client's certificate in advance to secure the messages to the client.</span></span> <span data-ttu-id="35265-136">クライアントの証明書を帯域外方式で取得し、この要素を使用して証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-136">You must obtain the client's certificate in an out-of-band manner and specify the certificate using this element.</span></span> <span data-ttu-id="35265-137">双方向サービスの詳細については、「 [方法: 双方向コントラクトを作成](how-to-create-a-duplex-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-137">For more information about duplex services, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
### <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="35265-138">\<authentication>\<clientCertificate>要素の</span><span class="sxs-lookup"><span data-stu-id="35265-138">\<authentication> of \<clientCertificate> Element</span></span>  

 <span data-ttu-id="35265-139">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)要素を使用すると、クライアントの認証方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="35265-139">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) element enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="35265-140">`CertificateValidationMode` 属性は、`None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust`、または `Custom` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="35265-140">You can set the `CertificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="35265-141">既定では、レベルはに設定されています `ChainTrust` 。これは、チェーンの最上位にあるルート証明 *機関* で終了する証明書の階層構造で各証明書を検索する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-141">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="35265-142">これは最もセキュリティで保護されているモードです。</span><span class="sxs-lookup"><span data-stu-id="35265-142">This is the most secure mode.</span></span> <span data-ttu-id="35265-143">また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れるよう指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-143">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="35265-144">自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。</span><span class="sxs-lookup"><span data-stu-id="35265-144">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="35265-145">クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-145">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="35265-146">また、値を `Custom` に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="35265-146">You can also set the value to `Custom`.</span></span> <span data-ttu-id="35265-147">`Custom` 値に設定する場合は、`CustomCertificateValidatorType` 属性を、証明書の検証に使用するアセンブリと型に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="35265-147">When set to the `Custom` value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="35265-148">独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-148">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
### <a name="issuedtokenauthentication-element"></a><span data-ttu-id="35265-149">\<issuedTokenAuthentication> 要素</span><span class="sxs-lookup"><span data-stu-id="35265-149">\<issuedTokenAuthentication> Element</span></span>  

 <span data-ttu-id="35265-150">発行されるトークンのシナリオには、3 つの段階があります。</span><span class="sxs-lookup"><span data-stu-id="35265-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="35265-151">最初の段階では、サービスにアクセスしようとしているクライアントは、 *セキュリティトークンサービス* (STS) と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="35265-151">In the first stage, a client trying to access a service is referred to a *secure token service* (STS).</span></span> <span data-ttu-id="35265-152">次に、STS がクライアントを認証し、その後、クライアントにトークン (通常は、SAML (Security Assertions Markup Language) トークン) を発行します。</span><span class="sxs-lookup"><span data-stu-id="35265-152">The STS then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="35265-153">最後に、クライアントがトークンを持ってサービスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="35265-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="35265-154">サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="35265-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="35265-155">トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-155">To authenticate the token, the certificate that the secure token service uses must be known to the service.</span></span> <span data-ttu-id="35265-156">要素は、 [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) このようなセキュリティトークンサービス証明書のリポジトリです。</span><span class="sxs-lookup"><span data-stu-id="35265-156">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="35265-157">証明書を追加するには、を使用し [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md) ます。</span><span class="sxs-lookup"><span data-stu-id="35265-157">To add certificates, use the [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="35265-158">次の [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) 例に示すように、各証明書のを挿入します。</span><span class="sxs-lookup"><span data-stu-id="35265-158">Insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="35265-159">既定では、証明書はセキュリティ トークン サービスから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="35265-160">このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="35265-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="35265-161">[\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md)セキュリティトークンを発行するセキュリティ *トークンサービス*(STS) を利用するフェデレーションアプリケーションでは、コレクションを使用する必要があり `SamlSecurityToken` ます。</span><span class="sxs-lookup"><span data-stu-id="35265-161">You should use the [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) collection in a federated application that utilizes a *secure token service* (STS) that issues `SamlSecurityToken` security tokens.</span></span> <span data-ttu-id="35265-162">STS がセキュリティ トークンを発行する場合、このセキュリティ トークンに `SamlAudienceRestrictionCondition` を追加して、セキュリティ トークンの提供先となる Web サービスの URI を指定できます。</span><span class="sxs-lookup"><span data-stu-id="35265-162">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a `SamlAudienceRestrictionCondition` to the security token.</span></span> <span data-ttu-id="35265-163">これにより、受け取り側 `SamlSecurityTokenAuthenticator` Web サービスは、次のようにしてこのチェックが行われるように指定することで、発行されたセキュリティ トークンがこの Web サービスを対象としていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="35265-163">That allows the `SamlSecurityTokenAuthenticator` for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="35265-164">`audienceUriMode`の属性 [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) を `Always` またはに設定 `BearerKeyOnly` します。</span><span class="sxs-lookup"><span data-stu-id="35265-164">Set the `audienceUriMode` attribute of [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) to `Always` or `BearerKeyOnly`.</span></span>  
  
- <span data-ttu-id="35265-165">このコレクションに URI を追加して、有効な URI のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-165">Specify the set of valid URIs, by adding the URIs to this collection.</span></span> <span data-ttu-id="35265-166">これを行うには、 [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) URI ごとにを挿入します。</span><span class="sxs-lookup"><span data-stu-id="35265-166">To do this, insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) for each URI</span></span>  
  
 <span data-ttu-id="35265-167">詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-167">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="35265-168">この構成要素の使用方法の詳細については、「 [方法: フェデレーションサービスで資格情報を構成する](how-to-configure-credentials-on-a-federation-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-168">For more information about using this configuration element, see [How to: Configure Credentials on a Federation Service](how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
#### <a name="allowing-anonymous-cardspace-users"></a><span data-ttu-id="35265-169">匿名の CardSpace ユーザーの許可</span><span class="sxs-lookup"><span data-stu-id="35265-169">Allowing Anonymous CardSpace Users</span></span>  

 <span data-ttu-id="35265-170">`AllowUntrustedRsaIssuers` 要素の `<IssuedTokenAuthentication>` 属性を `true` に設定すると、任意の RSA キー ペアで署名された自己発行トークンを提示することがすべてのクライアントに明示的に許可されます。</span><span class="sxs-lookup"><span data-stu-id="35265-170">Setting the `AllowUntrustedRsaIssuers` attribute of the `<IssuedTokenAuthentication>` element to `true` explicitly allows any client to present a self-issued token signed with an arbitrary RSA key pair.</span></span> <span data-ttu-id="35265-171">発行者は、キーに発行者データが関連付けられていないため、 *信頼* されていません。</span><span class="sxs-lookup"><span data-stu-id="35265-171">The issuer is *untrusted* because the key has no issuer data associated with it.</span></span> <span data-ttu-id="35265-172">CardSpace ユーザーは、id の自己提供のクレームを含む自己発行のカードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="35265-172">A CardSpace user can create a self-issued card that includes self-provided claims of identity.</span></span> <span data-ttu-id="35265-173">この機能を使用するときは十分に注意してください。</span><span class="sxs-lookup"><span data-stu-id="35265-173">Use this capability with caution.</span></span> <span data-ttu-id="35265-174">この機能を使用する場合は、RSA 公開キーを、ユーザー名と一緒にデータベースに格納する必要のある比較的安全なパスワードとして考えます。</span><span class="sxs-lookup"><span data-stu-id="35265-174">To use this feature, think of the RSA public key as a more secure password that should be stored in a database along with a user name.</span></span> <span data-ttu-id="35265-175">サービスへのクライアント アクセスを許可する前に、クライアントから提示された RSA 公開キーを、提示されたユーザー名に対応する格納済みの公開キーと比較して検証します。</span><span class="sxs-lookup"><span data-stu-id="35265-175">Before allowing a client access to the service, verify the client-presented RSA public key by comparing it with the stored public key for the presented user name.</span></span> <span data-ttu-id="35265-176">これは、ユーザーが各自のユーザー名を登録し、自己発行の RSA 公開キーに関連付けることができる登録プロセスが確立されていることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="35265-176">This presumes that you have established a registration process whereby users can register their user names and associate them with the self-issued RSA public keys.</span></span>  
  
## <a name="client-credentials"></a><span data-ttu-id="35265-177">クライアントの資格情報</span><span class="sxs-lookup"><span data-stu-id="35265-177">Client Credentials</span></span>  

 <span data-ttu-id="35265-178">クライアント資格情報は、相互認証が必要な場合にサービスに対するクライアントの認証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="35265-178">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="35265-179">また、このセクションを使用して、クライアントがサービスの証明書によってサービスへのメッセージをセキュリティで保護する必要がある場合に使用するサービス証明書を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="35265-179">You can use the section to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
 <span data-ttu-id="35265-180">セキュリティ トークン サービスまたはローカル発行者から発行されたトークンを使用するフェデレーション シナリオの一部として、クライアントを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="35265-180">You can also configure a client as part of a federation scenario to use issued tokens from a secure token service or a local issuer of tokens.</span></span> <span data-ttu-id="35265-181">フェデレーションシナリオの詳細については、「 [フェデレーションと発行済みトークン](federation-and-issued-tokens.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-181">For more information about federated scenarios, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span> <span data-ttu-id="35265-182">すべてのクライアント資格情報は、 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 次のコードに示すように、の下にあります。</span><span class="sxs-lookup"><span data-stu-id="35265-182">All client credentials are found under the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md), as shown in the following code.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a><span data-ttu-id="35265-183">\<clientCertificate> 要素</span><span class="sxs-lookup"><span data-stu-id="35265-183">\<clientCertificate> Element</span></span>  

 <span data-ttu-id="35265-184">この要素で、クライアントの認証に使用する証明書を設定します。</span><span class="sxs-lookup"><span data-stu-id="35265-184">Set the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="35265-185">詳細については、「 [方法: クライアント資格情報の値を指定する](../how-to-specify-client-credential-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-185">For more information, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
#### \<httpDigest>  

 <span data-ttu-id="35265-186">この機能は、Windows の Active Directory およびインターネット インフォメーション サービス (IIS) と共に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-186">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="35265-187">詳細については、「 [IIS 6.0 でのダイジェスト認証](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-187">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
#### <a name="issuedtoken-element"></a><span data-ttu-id="35265-188">\<issuedToken> 要素</span><span class="sxs-lookup"><span data-stu-id="35265-188">\<issuedToken> Element</span></span>  

 <span data-ttu-id="35265-189">には、 [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) トークンのローカル発行者、または Security Token Service で使用される動作を構成するために使用される要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="35265-189">The [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="35265-190">ローカル発行者を使用するようにクライアントを構成する方法については、「 [方法: ローカル発行者を構成](how-to-configure-a-local-issuer.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-190">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span>  
  
#### \<localIssuerAddress>  

 <span data-ttu-id="35265-191">既定のセキュリティ トークン サービス アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-191">Specifies a default security token service address.</span></span> <span data-ttu-id="35265-192">これは、が <xref:System.ServiceModel.WSFederationHttpBinding> Security Token Service の URL を提供しない場合、またはフェデレーションバインディングの発行者アドレスがまたはの場合に使用され `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` ます。</span><span class="sxs-lookup"><span data-stu-id="35265-192">This is used when the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="35265-193">そのような場合、<xref:System.ServiceModel.Description.ClientCredentials> は、ローカルの発行者およびバインディングのアドレスと共に構成し、その発行者と通信するために使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-193">In such cases, the <xref:System.ServiceModel.Description.ClientCredentials> must be configured with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
#### \<issuerChannelBehaviors>  

 <span data-ttu-id="35265-194">[\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)Security Token Service と通信するときに使用される WCF クライアントの動作を追加するには、を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-194">Use the [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) to add WCF client behaviors used when communicating with a security token service.</span></span> <span data-ttu-id="35265-195">「」セクションで、クライアントの動作を定義 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) します。</span><span class="sxs-lookup"><span data-stu-id="35265-195">Define client behaviors in the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) section.</span></span> <span data-ttu-id="35265-196">定義された動作を使用するには、 `add` `<issuerChannelBehaviors>` 2 つの属性を持つ要素に <> 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="35265-196">To use a defined behavior, add an <`add`> element to the `<issuerChannelBehaviors>` element with two attributes.</span></span> <span data-ttu-id="35265-197">次の例に示すように、`issuerAddress` をセキュリティ トークン サービスの URL に設定し、`behaviorConfiguration` 属性を定義済みのエンドポイントの動作の名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="35265-197">Set the `issuerAddress` to the URL of the security token service and set the `behaviorConfiguration` attribute to the name of the defined endpoint behavior, as shown in the following example.</span></span>  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a><span data-ttu-id="35265-198">\<serviceCertificate> 要素</span><span class="sxs-lookup"><span data-stu-id="35265-198">\<serviceCertificate> Element</span></span>  

 <span data-ttu-id="35265-199">サービス証明書の認証を制御するには、この要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-199">Use this element to control authentication of service certificates.</span></span>  
  
 <span data-ttu-id="35265-200">要素には、 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) サービスで証明書が指定されていない場合に使用される1つの証明書を格納できます。</span><span class="sxs-lookup"><span data-stu-id="35265-200">The [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) element can store a single certificate used when the service specifies no certificate.</span></span>  
  
 <span data-ttu-id="35265-201">およびを使用して、 [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) 特定のサービスに関連付けられているサービス証明書を設定します。</span><span class="sxs-lookup"><span data-stu-id="35265-201">Use the [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) and [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) to set service certificates that are associated with specific services.</span></span> <span data-ttu-id="35265-202">`<add>` 要素には、証明書をサービスに関連付けるために使用する `targetUri` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="35265-202">The `<add>` element includes a `targetUri` attribute that is used to associate the certificate with the service.</span></span>  
  
 <span data-ttu-id="35265-203">要素は、 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) 証明書の認証に使用される信頼レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-203">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="35265-204">既定のレベルは "ChainTrust" に設定され、チェーンの最上位の信頼された証明機関で終了する証明書の階層構造で各証明書を検索するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-204">By default, the level is set to "ChainTrust," which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="35265-205">これは最もセキュリティで保護されているモードです。</span><span class="sxs-lookup"><span data-stu-id="35265-205">This is the most secure mode.</span></span> <span data-ttu-id="35265-206">また、値を "PeerOrChainTrust" に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れることを指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-206">You can also set the value to "PeerOrChainTrust", which specifies that self-issued certificates (peer trust) are accepted, as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="35265-207">自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。</span><span class="sxs-lookup"><span data-stu-id="35265-207">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="35265-208">クライアントを展開するときは、代わりに "ChainTrust" 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-208">When deploying a client, use the "ChainTrust" value instead.</span></span> <span data-ttu-id="35265-209">値を "Custom" または "None" に設定できます。</span><span class="sxs-lookup"><span data-stu-id="35265-209">You can also set the value to "Custom" or "None."</span></span> <span data-ttu-id="35265-210">"Custom" 値を使用するには、`CustomCertificateValidatorType` 属性も証明書の検証に使用するアセンブリと型に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-210">To use the "Custom" value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="35265-211">独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-211">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="35265-212">詳細については、「 [方法: カスタム証明書検証を使用するサービスを作成](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-212">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="35265-213">要素には、 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) `RevocationMode` 証明書の失効を確認する方法を指定する属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="35265-213">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element includes a `RevocationMode` attribute that specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="35265-214">既定値は "online" です。この場合、証明書が失効していないかどうかが自動的にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="35265-214">The default is "online", which indicates that certificates are automatically checked for revocation.</span></span> <span data-ttu-id="35265-215">詳細については、「 [証明書の使用](working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-215">For more information, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
## <a name="serviceauthorization"></a><span data-ttu-id="35265-216">ServiceAuthorization</span><span class="sxs-lookup"><span data-stu-id="35265-216">ServiceAuthorization</span></span>  

 <span data-ttu-id="35265-217">要素には、 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 承認、カスタムロールプロバイダー、および偽装に影響する要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="35265-217">The [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) element contains elements that affect authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="35265-218"><xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスは、サービス メソッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="35265-218">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> class is applied to a service method.</span></span> <span data-ttu-id="35265-219">この属性は、保護メソッドの使用を承認するときに使用するユーザー グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-219">The attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="35265-220">既定値は "UseWindowsGroups" で、リソースにアクセスしようとしている ID を Windows グループ ("管理者" や "ユーザー" など) で検索するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="35265-220">The default value is "UseWindowsGroups" and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="35265-221">次のコードに示すように、"UseAspNetRoles" を指定して、<> 要素で構成されたカスタムロールプロバイダーを使用することもでき `system.web` ます。</span><span class="sxs-lookup"><span data-stu-id="35265-221">You can also specify "UseAspNetRoles" to use a custom role provider that is configured under the <`system.web` > element, as shown in the following code.</span></span>  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add
          name="SqlProvider"
          type="System.Web.Security.SqlMembershipProvider"
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 <span data-ttu-id="35265-222">`roleProviderName` 属性で `principalPermissionMode` を使用する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="35265-222">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a><span data-ttu-id="35265-223">セキュリティ監査の構成</span><span class="sxs-lookup"><span data-stu-id="35265-223">Configuring Security Audits</span></span>  

 <span data-ttu-id="35265-224">書き込み先の [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) ログとログに記録するイベントの種類を指定するには、を使用します。</span><span class="sxs-lookup"><span data-stu-id="35265-224">Use the [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) to specify the log written to, and what types of events to log.</span></span> <span data-ttu-id="35265-225">詳細については、「 [監査](auditing-security-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35265-225">For more information, see [Auditing](auditing-security-events.md).</span></span>  
  
```xml  
<behaviors>
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"
             messageAuthenticationAuditLevel="Success" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a><span data-ttu-id="35265-226">セキュリティで保護されたメタデータ交換</span><span class="sxs-lookup"><span data-stu-id="35265-226">Secure Metadata Exchange</span></span>  

 <span data-ttu-id="35265-227">メタデータをクライアントにエクスポートすると、構成やクライアント コードのダウンロードが可能になるため、サービスとクライアントの開発者にとって便利です。</span><span class="sxs-lookup"><span data-stu-id="35265-227">Exporting metadata to clients is convenient for service and client developers, as it enables downloads of configuration and client code.</span></span> <span data-ttu-id="35265-228">サービスが悪意のあるユーザーに公開されないようにするために、SSL over HTTP (HTTPS) 機構を使用して転送をセキュリティで保護できます。</span><span class="sxs-lookup"><span data-stu-id="35265-228">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="35265-229">転送を保護するには、まず、サービスをホストしているコンピューターの特定のポートに適切な X.509 証明書をバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="35265-229">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="35265-230">(詳細については、「 [証明書の使用](working-with-certificates.md)」を参照してください)。次に、 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) サービス構成にを追加し、 `HttpsGetEnabled` 属性をに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="35265-230">(For more information, see [Working with Certificates](working-with-certificates.md).) Second, add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) to the service configuration and set the `HttpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="35265-231">最後に、次の例に示すように、`HttpsGetUrl` 属性をサービス メタデータ エンドポイントの URL に設定します。</span><span class="sxs-lookup"><span data-stu-id="35265-231">Finally, set the `HttpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35265-232">関連項目</span><span class="sxs-lookup"><span data-stu-id="35265-232">See also</span></span>

- [<span data-ttu-id="35265-233">監査</span><span class="sxs-lookup"><span data-stu-id="35265-233">Auditing</span></span>](auditing-security-events.md)
- <span data-ttu-id="35265-234">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="35265-234">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
