---
description: 詳細については <security> 、 <basicHttpBinding>
title: <security> の <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 92d938d062d56cbb066a1170a9d3b8f3f5ba0186
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683256"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="f3cfb-103">\<security> の \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f3cfb-103">\<security> of \<basicHttpBinding></span></span>

<span data-ttu-id="f3cfb-104">のセキュリティ機能を定義 [\<basicHttpBinding>](basichttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-104">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f3cfb-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3cfb-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3cfb-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f3cfb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f3cfb-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3cfb-108">属性</span><span class="sxs-lookup"><span data-stu-id="f3cfb-108">Attributes</span></span>  
  
|<span data-ttu-id="f3cfb-109">属性</span><span class="sxs-lookup"><span data-stu-id="f3cfb-109">Attribute</span></span>|<span data-ttu-id="f3cfb-110">説明</span><span class="sxs-lookup"><span data-stu-id="f3cfb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3cfb-111">mode</span><span class="sxs-lookup"><span data-stu-id="f3cfb-111">mode</span></span>|<span data-ttu-id="f3cfb-112">任意。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-112">Optional.</span></span> <span data-ttu-id="f3cfb-113">使用されるセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-113">Specifies the type of security that is used.</span></span> <span data-ttu-id="f3cfb-114">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-114">The default is `None`.</span></span> <span data-ttu-id="f3cfb-115">この属性は <xref:System.ServiceModel.BasicHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-115">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f3cfb-116">mode 属性</span><span class="sxs-lookup"><span data-stu-id="f3cfb-116">mode Attribute</span></span>  
  
|<span data-ttu-id="f3cfb-117">値</span><span class="sxs-lookup"><span data-stu-id="f3cfb-117">Value</span></span>|<span data-ttu-id="f3cfb-118">説明</span><span class="sxs-lookup"><span data-stu-id="f3cfb-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3cfb-119">なし</span><span class="sxs-lookup"><span data-stu-id="f3cfb-119">None</span></span>|<span data-ttu-id="f3cfb-120">-メッセージは、転送中にセキュリティ保護されません。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-120">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="f3cfb-121">トランスポート</span><span class="sxs-lookup"><span data-stu-id="f3cfb-121">Transport</span></span>|<span data-ttu-id="f3cfb-122">セキュリティは、HTTPS トランスポートを使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-122">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="f3cfb-123">SOAP メッセージは、HTTPS を使用してセキュリティ保護されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-123">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="f3cfb-124">サービスは、サービスの X.509 証明書を使用してクライアントに認証されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-124">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="f3cfb-125">クライアントは、提供される ClientCredentialType を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-125">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="f3cfb-126">「」を参照してください [\<transport>](transport-of-basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-126">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="f3cfb-127">Message</span><span class="sxs-lookup"><span data-stu-id="f3cfb-127">Message</span></span>|<span data-ttu-id="f3cfb-128">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f3cfb-129">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-129">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="f3cfb-130">このバインディングの場合、サーバー証明書をクライアントの帯域外で提供するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-130">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="f3cfb-131">このバインディングの唯一の有効な `ClientCredentialType` は、`Certificate` です。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-131">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="f3cfb-132">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f3cfb-132">TransportWithMessageCredential</span></span>|<span data-ttu-id="f3cfb-133">整合性、機密性、およびサーバー認証は、トランスポート セキュリティによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-133">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="f3cfb-134">クライアント認証は、SOAP メッセージ セキュリティで提供されます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-134">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="f3cfb-135">このモードは、ユーザーがユーザー名およびパスワードを使用して認証し、メッセージ転送をセキュリティで保護するために既存の HTTP が配置されている場合に関連します。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-135">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="f3cfb-136">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="f3cfb-136">TransportCredentialOnly</span></span>|<span data-ttu-id="f3cfb-137">このモードは、メッセージの整合性と機密性を提供しません。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-137">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f3cfb-138">http ベースのクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-138">It provides http-based client authentication.</span></span> <span data-ttu-id="f3cfb-139">このモードを使用するときは、十分に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-139">This mode should be used with caution.</span></span> <span data-ttu-id="f3cfb-140">トランスポートセキュリティが他の方法 (IPSec など) によって提供され、WCF インフラストラクチャによってクライアント認証のみが提供される環境で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-140">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3cfb-141">子要素</span><span class="sxs-lookup"><span data-stu-id="f3cfb-141">Child Elements</span></span>  
  
|<span data-ttu-id="f3cfb-142">要素</span><span class="sxs-lookup"><span data-stu-id="f3cfb-142">Element</span></span>|<span data-ttu-id="f3cfb-143">説明</span><span class="sxs-lookup"><span data-stu-id="f3cfb-143">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="f3cfb-144">基本 HTTP サービスのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-144">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="f3cfb-145">この要素は、<xref:System.ServiceModel.HttpTransportSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-145">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="f3cfb-146">基本 HTTP サービスのメッセージ セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-146">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="f3cfb-147">この要素は、<xref:System.ServiceModel.BasicHttpMessageSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-147">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3cfb-148">親要素</span><span class="sxs-lookup"><span data-stu-id="f3cfb-148">Parent Elements</span></span>  
  
|<span data-ttu-id="f3cfb-149">要素</span><span class="sxs-lookup"><span data-stu-id="f3cfb-149">Element</span></span>|<span data-ttu-id="f3cfb-150">説明</span><span class="sxs-lookup"><span data-stu-id="f3cfb-150">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3cfb-151">binding</span><span class="sxs-lookup"><span data-stu-id="f3cfb-151">binding</span></span>|<span data-ttu-id="f3cfb-152">のバインディング要素 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-152">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3cfb-153">解説</span><span class="sxs-lookup"><span data-stu-id="f3cfb-153">Remarks</span></span>  

 <span data-ttu-id="f3cfb-154">既定では、SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-154">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="f3cfb-155">この要素を使用すると、`basicHttpBinding` 要素に追加のセキュリティ設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="f3cfb-155">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3cfb-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3cfb-156">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="f3cfb-157">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f3cfb-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f3cfb-158">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="f3cfb-158">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f3cfb-159">バインド</span><span class="sxs-lookup"><span data-stu-id="f3cfb-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3cfb-160">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="f3cfb-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f3cfb-161">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="f3cfb-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
