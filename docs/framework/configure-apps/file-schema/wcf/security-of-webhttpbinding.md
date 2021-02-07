---
description: 詳細については <security> 、 <webHttpBinding>
title: <security> の <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: a80a919ef877f01503e5ceaeb4fe7432e46f288c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683048"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="e514f-103">\<security> の \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e514f-103">\<security> of \<webHttpBinding></span></span>

<span data-ttu-id="e514f-104">で構成されるエンドポイントのセキュリティ要件を指定し [\<webHttpBinding>](webhttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="e514f-104">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="e514f-105">構文</span><span class="sxs-lookup"><span data-stu-id="e514f-105">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e514f-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e514f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e514f-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e514f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e514f-108">属性</span><span class="sxs-lookup"><span data-stu-id="e514f-108">Attributes</span></span>  
  
|<span data-ttu-id="e514f-109">属性</span><span class="sxs-lookup"><span data-stu-id="e514f-109">Attribute</span></span>|<span data-ttu-id="e514f-110">説明</span><span class="sxs-lookup"><span data-stu-id="e514f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e514f-111">mode</span><span class="sxs-lookup"><span data-stu-id="e514f-111">mode</span></span>|<span data-ttu-id="e514f-112">トランスポート レベルのセキュリティをエンドポイントで使用するか、セキュリティを使用しないかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e514f-112">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="e514f-113">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="e514f-113">The default is `None`.</span></span> <span data-ttu-id="e514f-114">この属性は <xref:System.ServiceModel.WebHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="e514f-114">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e514f-115">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="e514f-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="e514f-116">値</span><span class="sxs-lookup"><span data-stu-id="e514f-116">Value</span></span>|<span data-ttu-id="e514f-117">説明</span><span class="sxs-lookup"><span data-stu-id="e514f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e514f-118">なし</span><span class="sxs-lookup"><span data-stu-id="e514f-118">None</span></span>|<span data-ttu-id="e514f-119">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="e514f-119">Security is disabled.</span></span>|  
|<span data-ttu-id="e514f-120">トランスポート</span><span class="sxs-lookup"><span data-stu-id="e514f-120">Transport</span></span>|<span data-ttu-id="e514f-121">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="e514f-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="e514f-122">サービスは、SSL 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e514f-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="e514f-123">メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="e514f-123">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="e514f-124">クライアント認証は、の属性によって制御され `ClientCredentialType` [\<transport>](transport-of-webhttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="e514f-124">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="e514f-125">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="e514f-125">TransportCredentialOnly</span></span>|<span data-ttu-id="e514f-126">このモードは、メッセージの整合性と機密性を提供しません。</span><span class="sxs-lookup"><span data-stu-id="e514f-126">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="e514f-127">HTTP ベースのクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="e514f-127">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="e514f-128">このモードを使用するときは、十分に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e514f-128">This mode should be used with caution.</span></span> <span data-ttu-id="e514f-129">トランスポートセキュリティが他の方法 (IPSec など) によって提供され、WCF インフラストラクチャによってクライアント認証のみが提供される環境で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e514f-129">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e514f-130">子要素</span><span class="sxs-lookup"><span data-stu-id="e514f-130">Child Elements</span></span>  
  
|<span data-ttu-id="e514f-131">要素</span><span class="sxs-lookup"><span data-stu-id="e514f-131">Element</span></span>|<span data-ttu-id="e514f-132">説明</span><span class="sxs-lookup"><span data-stu-id="e514f-132">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="e514f-133">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="e514f-133">Defines the transport security settings.</span></span> <span data-ttu-id="e514f-134">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="e514f-134">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e514f-135">親要素</span><span class="sxs-lookup"><span data-stu-id="e514f-135">Parent Elements</span></span>  
  
|<span data-ttu-id="e514f-136">要素</span><span class="sxs-lookup"><span data-stu-id="e514f-136">Element</span></span>|<span data-ttu-id="e514f-137">説明</span><span class="sxs-lookup"><span data-stu-id="e514f-137">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="e514f-138">SOAP メッセージではなく HTTP 要求に応答する Windows Communication Foundation (WCF) Web サービスのエンドポイントを構成するために使用されるバインド要素。</span><span class="sxs-lookup"><span data-stu-id="e514f-138">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e514f-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="e514f-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="e514f-140">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="e514f-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e514f-141">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="e514f-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="e514f-142">バインド</span><span class="sxs-lookup"><span data-stu-id="e514f-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e514f-143">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="e514f-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e514f-144">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="e514f-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="e514f-145">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="e514f-145">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
