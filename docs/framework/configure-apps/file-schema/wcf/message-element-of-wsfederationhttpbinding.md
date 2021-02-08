---
description: '詳細情報: <message> の要素 <wsFederationHttpBinding>'
title: <message> の要素 <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 64978902081ec9e5a603804fed3b378da12fe42e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802191"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="11b42-103">\<message> の要素 \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="11b42-103">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="11b42-104">のメッセージレベルセキュリティの設定を定義し [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="11b42-104">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="11b42-105">構文</span><span class="sxs-lookup"><span data-stu-id="11b42-105">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11b42-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="11b42-106">Attributes and Elements</span></span>  

 <span data-ttu-id="11b42-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="11b42-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11b42-108">属性</span><span class="sxs-lookup"><span data-stu-id="11b42-108">Attributes</span></span>  
  
|<span data-ttu-id="11b42-109">属性</span><span class="sxs-lookup"><span data-stu-id="11b42-109">Attribute</span></span>|<span data-ttu-id="11b42-110">説明</span><span class="sxs-lookup"><span data-stu-id="11b42-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11b42-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="11b42-111">algorithmSuite</span></span>|<span data-ttu-id="11b42-112">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="11b42-112">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="11b42-113">この属性の有効な値については、「algorithmSuite 属性」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11b42-113">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="11b42-114">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="11b42-114">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="11b42-115">この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="11b42-115">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="11b42-116">これらのアルゴリズムは、セキュリティ ポリシー言語 (WS-SecurityPolicy) 仕様で指定されたアルゴリズムにマップされます。</span><span class="sxs-lookup"><span data-stu-id="11b42-116">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="11b42-117">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="11b42-117">issuedKeyType</span></span>|<span data-ttu-id="11b42-118">発行されるキーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="11b42-118">Specifies the type of key to be issued.</span></span> <span data-ttu-id="11b42-119">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="11b42-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="11b42-120">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="11b42-120">-   SymmetricKey</span></span><br /><span data-ttu-id="11b42-121">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="11b42-121">-   PublicKey</span></span><br /><br /> <span data-ttu-id="11b42-122">既定値は、`SymmetricKey` です。</span><span class="sxs-lookup"><span data-stu-id="11b42-122">The default is `SymmetricKey`.</span></span> <span data-ttu-id="11b42-123">この属性は <xref:System.IdentityModel.Tokens.SecurityKeyType> 型です。</span><span class="sxs-lookup"><span data-stu-id="11b42-123">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="11b42-124">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="11b42-124">issuedTokenType</span></span>|<span data-ttu-id="11b42-125">発行されるトークンの型を指定する URI を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="11b42-125">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="11b42-126">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="11b42-126">The default is `null`.</span></span>|  
|<span data-ttu-id="11b42-127">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="11b42-127">negotiateServiceCredential</span></span>|<span data-ttu-id="11b42-128">サービス資格情報がネゴシエーションの一部として交換されるか、帯域外で使用できるかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="11b42-128">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="11b42-129">既定値は `true` で、サービス資格情報がネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="11b42-129">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="11b42-130">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="11b42-130">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="11b42-131">値</span><span class="sxs-lookup"><span data-stu-id="11b42-131">Value</span></span>|<span data-ttu-id="11b42-132">説明</span><span class="sxs-lookup"><span data-stu-id="11b42-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11b42-133">Basic128</span><span class="sxs-lookup"><span data-stu-id="11b42-133">Basic128</span></span>|<span data-ttu-id="11b42-134">Basic128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-134">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-135">Basic192</span><span class="sxs-lookup"><span data-stu-id="11b42-135">Basic192</span></span>|<span data-ttu-id="11b42-136">Basic192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-136">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-137">Basic256</span><span class="sxs-lookup"><span data-stu-id="11b42-137">Basic256</span></span>|<span data-ttu-id="11b42-138">Basic256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-138">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-139">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-139">Basic256Rsa15</span></span>|<span data-ttu-id="11b42-140">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-140">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="11b42-141">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-141">Basic192Rsa15</span></span>|<span data-ttu-id="11b42-142">メッセージの暗号化には Basic192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-142">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="11b42-143">TripleDes</span><span class="sxs-lookup"><span data-stu-id="11b42-143">TripleDes</span></span>|<span data-ttu-id="11b42-144">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-144">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-145">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-145">Basic128Rsa15</span></span>|<span data-ttu-id="11b42-146">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-146">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="11b42-147">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-147">TripleDesRsa15</span></span>|<span data-ttu-id="11b42-148">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-148">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="11b42-149">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="11b42-149">Basic128Sha256</span></span>|<span data-ttu-id="11b42-150">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-150">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-151">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="11b42-151">Basic192Sha256</span></span>|<span data-ttu-id="11b42-152">メッセージの暗号化には Basic192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-152">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-153">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="11b42-153">Basic256Sha256</span></span>|<span data-ttu-id="11b42-154">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-154">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-155">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="11b42-155">TripleDesSha256</span></span>|<span data-ttu-id="11b42-156">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-156">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="11b42-157">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-157">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="11b42-158">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-158">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="11b42-159">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-159">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="11b42-160">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-160">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="11b42-161">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-161">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="11b42-162">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-162">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="11b42-163">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="11b42-163">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="11b42-164">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="11b42-164">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11b42-165">子要素</span><span class="sxs-lookup"><span data-stu-id="11b42-165">Child Elements</span></span>  
  
|<span data-ttu-id="11b42-166">要素</span><span class="sxs-lookup"><span data-stu-id="11b42-166">Element</span></span>|<span data-ttu-id="11b42-167">説明</span><span class="sxs-lookup"><span data-stu-id="11b42-167">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="11b42-168">このバインディングのクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="11b42-168">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="11b42-169">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="11b42-169">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="11b42-170">発行者</span><span class="sxs-lookup"><span data-stu-id="11b42-170">issuer</span></span>|<span data-ttu-id="11b42-171">セキュリティ トークンを発行するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="11b42-171">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="11b42-172">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="11b42-172">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="11b42-173">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="11b42-173">issuerMetadata</span></span>|<span data-ttu-id="11b42-174">発行者のエンドポイント アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="11b42-174">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="11b42-175">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="11b42-175">A collection of token request parameters.</span></span> <span data-ttu-id="11b42-176">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="11b42-176">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11b42-177">親要素</span><span class="sxs-lookup"><span data-stu-id="11b42-177">Parent Elements</span></span>  
  
|<span data-ttu-id="11b42-178">要素</span><span class="sxs-lookup"><span data-stu-id="11b42-178">Element</span></span>|<span data-ttu-id="11b42-179">説明</span><span class="sxs-lookup"><span data-stu-id="11b42-179">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="11b42-180">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="11b42-180">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11b42-181">関連項目</span><span class="sxs-lookup"><span data-stu-id="11b42-181">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="11b42-182">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="11b42-182">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="11b42-183">バインド</span><span class="sxs-lookup"><span data-stu-id="11b42-183">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="11b42-184">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="11b42-184">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="11b42-185">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="11b42-185">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
