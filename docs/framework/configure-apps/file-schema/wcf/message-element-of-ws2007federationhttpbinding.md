---
description: '詳細情報: <message> の要素 <ws2007FederationHttpBinding>'
title: <message> の要素 <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: f9116a5075f30421dfb26adc29ec0b167db33673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725455"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="cd9c8-103">\<message> の要素 \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cd9c8-103">\<message> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="cd9c8-104">要素のメッセージレベルセキュリティの設定を定義 [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-104">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="cd9c8-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd9c8-105">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd9c8-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cd9c8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cd9c8-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd9c8-108">属性</span><span class="sxs-lookup"><span data-stu-id="cd9c8-108">Attributes</span></span>  
  
|<span data-ttu-id="cd9c8-109">属性</span><span class="sxs-lookup"><span data-stu-id="cd9c8-109">Attribute</span></span>|<span data-ttu-id="cd9c8-110">説明</span><span class="sxs-lookup"><span data-stu-id="cd9c8-110">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="cd9c8-111">任意。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-111">Optional.</span></span> <span data-ttu-id="cd9c8-112">メッセージの暗号化、署名、およびキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-112">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="cd9c8-113">アルゴリズムとキー サイズは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> クラスにより決まります。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-113">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="cd9c8-114">これらのアルゴリズムは、セキュリティ ポリシー言語 (WS-SecurityPolicy) 仕様で指定されたアルゴリズムにマップされます。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-114">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="cd9c8-115">それぞれの値については次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-115">See the following table for possible values.</span></span> <span data-ttu-id="cd9c8-116">既定値は Basic256 です。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-116">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="cd9c8-117">発行されるキーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="cd9c8-118">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cd9c8-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="cd9c8-119">-   SymmetricKey</span></span><br /><span data-ttu-id="cd9c8-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="cd9c8-120">-   PublicKey</span></span><br /><span data-ttu-id="cd9c8-121">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="cd9c8-121">-   BearerKey</span></span><br /><br /> <span data-ttu-id="cd9c8-122">既定値は SymmetricKey です。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-122">The default is SymmetricKey.</span></span> <span data-ttu-id="cd9c8-123">この属性は <xref:System.IdentityModel.Tokens.SecurityKeyType> 型です。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-123">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="cd9c8-124">発行されるトークンの型を指定する URI。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-124">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="cd9c8-125">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-125">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="cd9c8-126">サービス資格情報がネゴシエーションの一部として交換されるか、帯域外で使用できるかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-126">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="cd9c8-127">既定値は `true` で、サービス資格情報がネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-127">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="cd9c8-128">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="cd9c8-128">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="cd9c8-129">値</span><span class="sxs-lookup"><span data-stu-id="cd9c8-129">Value</span></span>|<span data-ttu-id="cd9c8-130">説明</span><span class="sxs-lookup"><span data-stu-id="cd9c8-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd9c8-131">Basic128</span><span class="sxs-lookup"><span data-stu-id="cd9c8-131">Basic128</span></span>|<span data-ttu-id="cd9c8-132">Aes128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-132">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-133">Basic192</span><span class="sxs-lookup"><span data-stu-id="cd9c8-133">Basic192</span></span>|<span data-ttu-id="cd9c8-134">Aes192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-134">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-135">Basic256</span><span class="sxs-lookup"><span data-stu-id="cd9c8-135">Basic256</span></span>|<span data-ttu-id="cd9c8-136">Aes256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-136">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-137">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-137">Basic256Rsa15</span></span>|<span data-ttu-id="cd9c8-138">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-138">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-139">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-139">Basic192Rsa15</span></span>|<span data-ttu-id="cd9c8-140">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-140">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-141">TripleDes</span><span class="sxs-lookup"><span data-stu-id="cd9c8-141">TripleDes</span></span>|<span data-ttu-id="cd9c8-142">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-142">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-143">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-143">Basic128Rsa15</span></span>|<span data-ttu-id="cd9c8-144">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-144">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-145">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-145">TripleDesRsa15</span></span>|<span data-ttu-id="cd9c8-146">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-146">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-147">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="cd9c8-147">Basic128Sha256</span></span>|<span data-ttu-id="cd9c8-148">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-148">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-149">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="cd9c8-149">Basic192Sha256</span></span>|<span data-ttu-id="cd9c8-150">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-150">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-151">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="cd9c8-151">Basic256Sha256</span></span>|<span data-ttu-id="cd9c8-152">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-152">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-153">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="cd9c8-153">TripleDesSha256</span></span>|<span data-ttu-id="cd9c8-154">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-154">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-155">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-155">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="cd9c8-156">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-156">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-157">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-157">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="cd9c8-158">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-158">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-159">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-159">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="cd9c8-160">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-160">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cd9c8-161">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cd9c8-161">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="cd9c8-162">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd9c8-163">子要素</span><span class="sxs-lookup"><span data-stu-id="cd9c8-163">Child Elements</span></span>  
  
|<span data-ttu-id="cd9c8-164">要素</span><span class="sxs-lookup"><span data-stu-id="cd9c8-164">Element</span></span>|<span data-ttu-id="cd9c8-165">説明</span><span class="sxs-lookup"><span data-stu-id="cd9c8-165">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="cd9c8-166">このバインディングのクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-166">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="cd9c8-167">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-167">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="cd9c8-168">セキュリティ トークンを発行するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-168">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="cd9c8-169">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-169">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="cd9c8-170">発行者のエンドポイント アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-170">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="cd9c8-171">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-171">A collection of token request parameters.</span></span> <span data-ttu-id="cd9c8-172">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-172">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd9c8-173">親要素</span><span class="sxs-lookup"><span data-stu-id="cd9c8-173">Parent Elements</span></span>  
  
|<span data-ttu-id="cd9c8-174">要素</span><span class="sxs-lookup"><span data-stu-id="cd9c8-174">Element</span></span>|<span data-ttu-id="cd9c8-175">説明</span><span class="sxs-lookup"><span data-stu-id="cd9c8-175">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="cd9c8-176">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd9c8-176">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd9c8-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd9c8-177">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="cd9c8-178">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="cd9c8-178">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cd9c8-179">バインド</span><span class="sxs-lookup"><span data-stu-id="cd9c8-179">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cd9c8-180">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="cd9c8-180">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cd9c8-181">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="cd9c8-181">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
