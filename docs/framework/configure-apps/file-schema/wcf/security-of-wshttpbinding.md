---
description: 詳細については <security> 、 <wsHttpBinding>
title: <security> の <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 646d49bd67b2b544ae2616f206bfdeabf7806579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683061"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="f3672-103">\<security> の \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f3672-103">\<security> of \<wsHttpBinding></span></span>

<span data-ttu-id="f3672-104">のセキュリティ機能を表し [\<wsHttpBinding>](wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="f3672-104">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f3672-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3672-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3672-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f3672-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f3672-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3672-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3672-108">属性</span><span class="sxs-lookup"><span data-stu-id="f3672-108">Attributes</span></span>  
  
|<span data-ttu-id="f3672-109">属性</span><span class="sxs-lookup"><span data-stu-id="f3672-109">Attribute</span></span>|<span data-ttu-id="f3672-110">説明</span><span class="sxs-lookup"><span data-stu-id="f3672-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3672-111">mode</span><span class="sxs-lookup"><span data-stu-id="f3672-111">mode</span></span>|<span data-ttu-id="f3672-112">Optional.</span><span class="sxs-lookup"><span data-stu-id="f3672-112">-   Optional.</span></span> <span data-ttu-id="f3672-113">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3672-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="f3672-114">既定値は、`Message` です。</span><span class="sxs-lookup"><span data-stu-id="f3672-114">The default is `Message`.</span></span><br /><span data-ttu-id="f3672-115">-この属性の型は <xref:System.ServiceModel.SecurityMode> です。</span><span class="sxs-lookup"><span data-stu-id="f3672-115">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f3672-116">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="f3672-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="f3672-117">値</span><span class="sxs-lookup"><span data-stu-id="f3672-117">Value</span></span>|<span data-ttu-id="f3672-118">説明</span><span class="sxs-lookup"><span data-stu-id="f3672-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3672-119">なし</span><span class="sxs-lookup"><span data-stu-id="f3672-119">None</span></span>|<span data-ttu-id="f3672-120">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f3672-120">Security is disabled.</span></span>|  
|<span data-ttu-id="f3672-121">トランスポート</span><span class="sxs-lookup"><span data-stu-id="f3672-121">Transport</span></span>|<span data-ttu-id="f3672-122">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="f3672-122">Security is provided using HTTPS.</span></span> <span data-ttu-id="f3672-123">サービスは、SSL 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3672-123">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="f3672-124">メッセージは、HTTPS を使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="f3672-124">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="f3672-125">クライアント認証は、`ClientCredentials` 属性を使用して制御されます。</span><span class="sxs-lookup"><span data-stu-id="f3672-125">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="f3672-126">の [\<transport>](transport-of-wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="f3672-126">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="f3672-127">Message</span><span class="sxs-lookup"><span data-stu-id="f3672-127">Message</span></span>|<span data-ttu-id="f3672-128">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="f3672-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f3672-129">既定では、SOAP 本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="f3672-129">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="f3672-130">このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、Security.Message プロパティを使用してメッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3672-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="f3672-131">クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="f3672-131">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="f3672-132">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f3672-132">TransportWithMessageCredential</span></span>|<span data-ttu-id="f3672-133">このモードでは、HTTPS は、整合性、機密性、およびサーバー認証を提供し、SOAP メッセージ セキュリティはクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3672-133">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="f3672-134">既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="f3672-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3672-135">子要素</span><span class="sxs-lookup"><span data-stu-id="f3672-135">Child Elements</span></span>  
  
|<span data-ttu-id="f3672-136">要素</span><span class="sxs-lookup"><span data-stu-id="f3672-136">Element</span></span>|<span data-ttu-id="f3672-137">説明</span><span class="sxs-lookup"><span data-stu-id="f3672-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="f3672-138">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="f3672-138">Defines the transport security settings.</span></span> <span data-ttu-id="f3672-139">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f3672-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="f3672-140">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="f3672-140">Defines the security settings for the message.</span></span> <span data-ttu-id="f3672-141">この要素は、<xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f3672-141">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3672-142">親要素</span><span class="sxs-lookup"><span data-stu-id="f3672-142">Parent Elements</span></span>  
  
|<span data-ttu-id="f3672-143">要素</span><span class="sxs-lookup"><span data-stu-id="f3672-143">Element</span></span>|<span data-ttu-id="f3672-144">説明</span><span class="sxs-lookup"><span data-stu-id="f3672-144">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="f3672-145">HTTP トランスポート アプリケーションのセキュリティで保護されたバインド。</span><span class="sxs-lookup"><span data-stu-id="f3672-145">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3672-146">解説</span><span class="sxs-lookup"><span data-stu-id="f3672-146">Remarks</span></span>  

 <span data-ttu-id="f3672-147">WSHttpBinding クラスは、WS-\* 仕様を実装するサービスと相互運用するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="f3672-147">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="f3672-148">このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。</span><span class="sxs-lookup"><span data-stu-id="f3672-148">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3672-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3672-149">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="f3672-150">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f3672-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f3672-151">バインド</span><span class="sxs-lookup"><span data-stu-id="f3672-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3672-152">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="f3672-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f3672-153">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="f3672-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
