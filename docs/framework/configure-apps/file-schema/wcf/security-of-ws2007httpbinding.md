---
description: 詳細については <security> 、 <ws2007HttpBinding>
title: <security> の <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ef8b82d34b318db79db061b9c01b147e619d39c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786812"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="a8c3e-103">\<security> の \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="a8c3e-103">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="a8c3e-104">要素で使用されるセキュリティ設定を表し [\<ws2007HttpBinding>](ws2007httpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-104">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="a8c3e-105">構文</span><span class="sxs-lookup"><span data-stu-id="a8c3e-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8c3e-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a8c3e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a8c3e-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8c3e-108">属性</span><span class="sxs-lookup"><span data-stu-id="a8c3e-108">Attributes</span></span>  
  
|<span data-ttu-id="a8c3e-109">属性</span><span class="sxs-lookup"><span data-stu-id="a8c3e-109">Attribute</span></span>|<span data-ttu-id="a8c3e-110">説明</span><span class="sxs-lookup"><span data-stu-id="a8c3e-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="a8c3e-111">Optional.</span><span class="sxs-lookup"><span data-stu-id="a8c3e-111">-   Optional.</span></span> <span data-ttu-id="a8c3e-112">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a8c3e-113">既定値は、`Message` です。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-113">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="a8c3e-114">この属性は <xref:System.ServiceModel.SecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a8c3e-115">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="a8c3e-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="a8c3e-116">値</span><span class="sxs-lookup"><span data-stu-id="a8c3e-116">Value</span></span>|<span data-ttu-id="a8c3e-117">説明</span><span class="sxs-lookup"><span data-stu-id="a8c3e-117">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="a8c3e-118">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-118">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="a8c3e-119">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-119">Security is provided using HTTPS.</span></span> <span data-ttu-id="a8c3e-120">サービスは、Secure Sockets Layer (SSL) 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-120">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="a8c3e-121">メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-121">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="a8c3e-122">クライアント認証は、要素の属性によって制御され `ClientCredentials` [\<transport>](transport-of-ws2007httpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-122">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="a8c3e-123">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-123">Security is provided using SOAP message security.</span></span> <span data-ttu-id="a8c3e-124">既定では、SOAP 本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-124">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="a8c3e-125">このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、<xref:System.ServiceModel.Security.SecurityMessageProperty> によってメッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-125">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="a8c3e-126">クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-126">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="a8c3e-127">このモードでは、HTTPS は、整合性、機密性、およびサーバー認証を提供し、SOAP メッセージ セキュリティはクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-127">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="a8c3e-128">既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-128">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8c3e-129">子要素</span><span class="sxs-lookup"><span data-stu-id="a8c3e-129">Child Elements</span></span>  
  
|<span data-ttu-id="a8c3e-130">要素</span><span class="sxs-lookup"><span data-stu-id="a8c3e-130">Element</span></span>|<span data-ttu-id="a8c3e-131">説明</span><span class="sxs-lookup"><span data-stu-id="a8c3e-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="a8c3e-132">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-132">Defines the transport security settings.</span></span> <span data-ttu-id="a8c3e-133">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="a8c3e-134">これらの設定は、モードが Transport に設定されている場合のみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-134">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="a8c3e-135">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-135">Defines the security settings for the message.</span></span> <span data-ttu-id="a8c3e-136">この要素は、<xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-136">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="a8c3e-137">これらの設定は、モードが Transport に設定されている場合は適用されません。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-137">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8c3e-138">親要素</span><span class="sxs-lookup"><span data-stu-id="a8c3e-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a8c3e-139">要素</span><span class="sxs-lookup"><span data-stu-id="a8c3e-139">Element</span></span>|<span data-ttu-id="a8c3e-140">説明</span><span class="sxs-lookup"><span data-stu-id="a8c3e-140">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="a8c3e-141">HTTP トランスポート アプリケーションのセキュリティで保護されたバインド。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-141">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8c3e-142">解説</span><span class="sxs-lookup"><span data-stu-id="a8c3e-142">Remarks</span></span>  

 <span data-ttu-id="a8c3e-143">この要素は、WS-\* 仕様を実装するサービスと相互運用するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-143">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="a8c3e-144">このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。</span><span class="sxs-lookup"><span data-stu-id="a8c3e-144">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c3e-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8c3e-145">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="a8c3e-146">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="a8c3e-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a8c3e-147">バインド</span><span class="sxs-lookup"><span data-stu-id="a8c3e-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a8c3e-148">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="a8c3e-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a8c3e-149">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="a8c3e-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
