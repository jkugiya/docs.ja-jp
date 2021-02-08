---
description: 詳細については <security> 、 <wsFederationHttpBinding>
title: <security> の <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 6c01c7a50b05f1723b3620407eb5e5761bae35cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786799"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="15f75-103">\<security> の \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="15f75-103">\<security> of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="15f75-104">のセキュリティ設定を定義し [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="15f75-104">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="15f75-105">構文</span><span class="sxs-lookup"><span data-stu-id="15f75-105">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15f75-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="15f75-106">Attributes and Elements</span></span>  

 <span data-ttu-id="15f75-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="15f75-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15f75-108">属性</span><span class="sxs-lookup"><span data-stu-id="15f75-108">Attributes</span></span>  
  
|<span data-ttu-id="15f75-109">属性</span><span class="sxs-lookup"><span data-stu-id="15f75-109">Attribute</span></span>|<span data-ttu-id="15f75-110">説明</span><span class="sxs-lookup"><span data-stu-id="15f75-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15f75-111">モード</span><span class="sxs-lookup"><span data-stu-id="15f75-111">Mode</span></span>|<span data-ttu-id="15f75-112">任意。</span><span class="sxs-lookup"><span data-stu-id="15f75-112">Optional.</span></span> <span data-ttu-id="15f75-113">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="15f75-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="15f75-114">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="15f75-114">The default value is `Message`.</span></span> <span data-ttu-id="15f75-115">この属性は <xref:System.ServiceModel.WSFederationHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="15f75-115">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="15f75-116">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="15f75-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="15f75-117">値</span><span class="sxs-lookup"><span data-stu-id="15f75-117">Value</span></span>|<span data-ttu-id="15f75-118">説明</span><span class="sxs-lookup"><span data-stu-id="15f75-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15f75-119">なし</span><span class="sxs-lookup"><span data-stu-id="15f75-119">None</span></span>|<span data-ttu-id="15f75-120">SOAP メッセージは、転送中はセキュリティで保護されません。</span><span class="sxs-lookup"><span data-stu-id="15f75-120">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="15f75-121">Message</span><span class="sxs-lookup"><span data-stu-id="15f75-121">Message</span></span>|<span data-ttu-id="15f75-122">SOAP メッセージ セキュリティを使用して、整合性、機密性、サーバー認証、およびクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="15f75-122">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="15f75-123">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="15f75-123">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="15f75-124">このサービスは、証明書を使用して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15f75-124">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="15f75-125">クライアント認証は、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="15f75-125">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="15f75-126">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="15f75-126">TransportWithMessageCredential</span></span>|<span data-ttu-id="15f75-127">整合性、機密性、およびサーバー認証は、HTTPS によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="15f75-127">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="15f75-128">このサービスは、証明書を使用して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15f75-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="15f75-129">クライアント認証は、SOAP メッセージ セキュリティによって提供され、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="15f75-129">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15f75-130">子要素</span><span class="sxs-lookup"><span data-stu-id="15f75-130">Child Elements</span></span>  
  
|<span data-ttu-id="15f75-131">要素</span><span class="sxs-lookup"><span data-stu-id="15f75-131">Element</span></span>|<span data-ttu-id="15f75-132">説明</span><span class="sxs-lookup"><span data-stu-id="15f75-132">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="15f75-133">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="15f75-133">Defines the settings for the message-level security.</span></span> <span data-ttu-id="15f75-134">この要素は <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="15f75-134">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15f75-135">親要素</span><span class="sxs-lookup"><span data-stu-id="15f75-135">Parent Elements</span></span>  
  
|<span data-ttu-id="15f75-136">要素</span><span class="sxs-lookup"><span data-stu-id="15f75-136">Element</span></span>|<span data-ttu-id="15f75-137">説明</span><span class="sxs-lookup"><span data-stu-id="15f75-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="15f75-138">のすべてのバインディング機能を定義 [\<wsDualHttpBinding>](wsdualhttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="15f75-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15f75-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="15f75-139">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="15f75-140">方法: WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="15f75-140">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="15f75-141">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="15f75-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="15f75-142">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="15f75-142">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="15f75-143">バインド</span><span class="sxs-lookup"><span data-stu-id="15f75-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="15f75-144">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="15f75-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="15f75-145">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="15f75-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
