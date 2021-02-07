---
description: 詳細については <security> 、 <netHttpBinding>
title: <security> の <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 70d6363c0ac7fa00d83880ddc8c873548b385a29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683126"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="f2ccb-103">\<security> の \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f2ccb-103">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="f2ccb-104">のセキュリティ機能を定義 [\<netHttpBinding>](nethttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-104">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="f2ccb-105">構文</span><span class="sxs-lookup"><span data-stu-id="f2ccb-105">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2ccb-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="f2ccb-106">Attributes and elements</span></span>

<span data-ttu-id="f2ccb-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2ccb-108">属性</span><span class="sxs-lookup"><span data-stu-id="f2ccb-108">Attributes</span></span>

|<span data-ttu-id="f2ccb-109">属性</span><span class="sxs-lookup"><span data-stu-id="f2ccb-109">Attribute</span></span>|<span data-ttu-id="f2ccb-110">説明</span><span class="sxs-lookup"><span data-stu-id="f2ccb-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f2ccb-111">mode</span><span class="sxs-lookup"><span data-stu-id="f2ccb-111">mode</span></span>|<span data-ttu-id="f2ccb-112">任意。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-112">Optional.</span></span> <span data-ttu-id="f2ccb-113">使用されるセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-113">Specifies the type of security that is used.</span></span> <span data-ttu-id="f2ccb-114">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-114">The default is `None`.</span></span> <span data-ttu-id="f2ccb-115">この属性は <xref:System.ServiceModel.BasicHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-115">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="f2ccb-116">mode 属性</span><span class="sxs-lookup"><span data-stu-id="f2ccb-116">mode attribute</span></span>

|<span data-ttu-id="f2ccb-117">値</span><span class="sxs-lookup"><span data-stu-id="f2ccb-117">Value</span></span>|<span data-ttu-id="f2ccb-118">説明</span><span class="sxs-lookup"><span data-stu-id="f2ccb-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="f2ccb-119">なし</span><span class="sxs-lookup"><span data-stu-id="f2ccb-119">None</span></span>|<span data-ttu-id="f2ccb-120">-メッセージは、転送中にセキュリティ保護されません。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-120">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="f2ccb-121">トランスポート</span><span class="sxs-lookup"><span data-stu-id="f2ccb-121">Transport</span></span>|<span data-ttu-id="f2ccb-122">セキュリティは、HTTPS トランスポートを使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-122">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="f2ccb-123">SOAP メッセージは、HTTPS を使用してセキュリティ保護されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-123">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="f2ccb-124">サービスは、サービスの X.509 証明書を使用してクライアントに認証されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-124">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="f2ccb-125">クライアントは、提供される ClientCredentialType を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-125">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="f2ccb-126">Message</span><span class="sxs-lookup"><span data-stu-id="f2ccb-126">Message</span></span>|<span data-ttu-id="f2ccb-127">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f2ccb-128">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="f2ccb-129">このバインディングの場合、サーバー証明書をクライアントの帯域外で提供するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="f2ccb-130">このバインディングの唯一の有効な `ClientCredentialType` は、`Certificate` です。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="f2ccb-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f2ccb-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="f2ccb-132">整合性、機密性、およびサーバー認証は、トランスポート セキュリティによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="f2ccb-133">クライアント認証は、SOAP メッセージ セキュリティで提供されます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="f2ccb-134">このモードは、ユーザーがユーザー名およびパスワードを使用して認証し、メッセージ転送をセキュリティで保護するために既存の HTTP が配置されている場合に関連します。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="f2ccb-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="f2ccb-135">TransportCredentialOnly</span></span>|<span data-ttu-id="f2ccb-136">このモードは、メッセージの整合性と機密性を提供しません。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f2ccb-137">http ベースのクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-137">It provides http-based client authentication.</span></span> <span data-ttu-id="f2ccb-138">このモードを使用するときは、十分に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-138">This mode should be used with caution.</span></span> <span data-ttu-id="f2ccb-139">トランスポートセキュリティが他の方法 (IPSec など) によって提供され、WCF インフラストラクチャによってクライアント認証のみが提供される環境で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f2ccb-140">子要素</span><span class="sxs-lookup"><span data-stu-id="f2ccb-140">Child elements</span></span>

|<span data-ttu-id="f2ccb-141">要素</span><span class="sxs-lookup"><span data-stu-id="f2ccb-141">Element</span></span>|<span data-ttu-id="f2ccb-142">説明</span><span class="sxs-lookup"><span data-stu-id="f2ccb-142">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="f2ccb-143">基本 HTTP サービスのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="f2ccb-144">この要素は、<xref:System.ServiceModel.HttpTransportSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="f2ccb-145">基本 HTTP サービスのメッセージ セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="f2ccb-146">この要素は、<xref:System.ServiceModel.BasicHttpMessageSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2ccb-147">親要素</span><span class="sxs-lookup"><span data-stu-id="f2ccb-147">Parent elements</span></span>

|<span data-ttu-id="f2ccb-148">要素</span><span class="sxs-lookup"><span data-stu-id="f2ccb-148">Element</span></span>|<span data-ttu-id="f2ccb-149">説明</span><span class="sxs-lookup"><span data-stu-id="f2ccb-149">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="f2ccb-150">binding</span><span class="sxs-lookup"><span data-stu-id="f2ccb-150">binding</span></span>|<span data-ttu-id="f2ccb-151">のバインディング要素 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2ccb-152">解説</span><span class="sxs-lookup"><span data-stu-id="f2ccb-152">Remarks</span></span>

 <span data-ttu-id="f2ccb-153">既定では、SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="f2ccb-154">この要素を使用すると、`netHttpBinding` 要素に追加のセキュリティ設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="f2ccb-154">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2ccb-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2ccb-155">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="f2ccb-156">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f2ccb-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f2ccb-157">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="f2ccb-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f2ccb-158">バインド</span><span class="sxs-lookup"><span data-stu-id="f2ccb-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f2ccb-159">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="f2ccb-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f2ccb-160">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="f2ccb-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
