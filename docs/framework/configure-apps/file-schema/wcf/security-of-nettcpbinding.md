---
description: 詳細については <security> 、 <netTcpBinding>
title: <security> の <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: ad924f5a6ea9e003f6427ee76d3aef3afde9d083
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683074"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="05e62-103">\<security> の \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="05e62-103">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="05e62-104">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="05e62-104">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="05e62-105">構文</span><span class="sxs-lookup"><span data-stu-id="05e62-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05e62-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="05e62-106">Attributes and Elements</span></span>  

 <span data-ttu-id="05e62-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="05e62-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05e62-108">属性</span><span class="sxs-lookup"><span data-stu-id="05e62-108">Attributes</span></span>  
  
|<span data-ttu-id="05e62-109">属性</span><span class="sxs-lookup"><span data-stu-id="05e62-109">Attribute</span></span>|<span data-ttu-id="05e62-110">説明</span><span class="sxs-lookup"><span data-stu-id="05e62-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05e62-111">mode</span><span class="sxs-lookup"><span data-stu-id="05e62-111">mode</span></span>|<span data-ttu-id="05e62-112">任意。</span><span class="sxs-lookup"><span data-stu-id="05e62-112">Optional.</span></span> <span data-ttu-id="05e62-113">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="05e62-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="05e62-114">有効な値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="05e62-114">Valid values are shown below.</span></span> <span data-ttu-id="05e62-115">既定値は `Transport` です。</span><span class="sxs-lookup"><span data-stu-id="05e62-115">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="05e62-116">この属性は <xref:System.ServiceModel.SecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="05e62-116">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="05e62-117">mode 属性</span><span class="sxs-lookup"><span data-stu-id="05e62-117">mode Attribute</span></span>  
  
|<span data-ttu-id="05e62-118">値</span><span class="sxs-lookup"><span data-stu-id="05e62-118">Value</span></span>|<span data-ttu-id="05e62-119">説明</span><span class="sxs-lookup"><span data-stu-id="05e62-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05e62-120">なし</span><span class="sxs-lookup"><span data-stu-id="05e62-120">None</span></span>|<span data-ttu-id="05e62-121">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="05e62-121">Security is disabled.</span></span>|  
|<span data-ttu-id="05e62-122">トランスポート</span><span class="sxs-lookup"><span data-stu-id="05e62-122">Transport</span></span>|<span data-ttu-id="05e62-123">トランスポート セキュリティは、TCP 経由の TLS または SPNaego を使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="05e62-123">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="05e62-124">サービスは、SSL 証明書を使用して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05e62-124">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="05e62-125">このモードでは保護レベルを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="05e62-125">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="05e62-126">Message</span><span class="sxs-lookup"><span data-stu-id="05e62-126">Message</span></span>|<span data-ttu-id="05e62-127">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="05e62-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="05e62-128">既定では、SOAP 本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="05e62-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="05e62-129">このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、メッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="05e62-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="05e62-130">クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="05e62-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="05e62-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="05e62-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="05e62-132">トランスポート セキュリティは、メッセージ セキュリティと組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="05e62-132">Transport security is coupled with message security.</span></span> <span data-ttu-id="05e62-133">トランスポート セキュリティは、TCP 経由の TLS または SPNego によって提供され、整合性、機密性、およびサーバー認証が保証されます。</span><span class="sxs-lookup"><span data-stu-id="05e62-133">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="05e62-134">SOAP メッセージ セキュリティは、クライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="05e62-134">SOAP message security provides client authentication.</span></span> <span data-ttu-id="05e62-135">既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="05e62-135">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05e62-136">子要素</span><span class="sxs-lookup"><span data-stu-id="05e62-136">Child Elements</span></span>  
  
|<span data-ttu-id="05e62-137">要素</span><span class="sxs-lookup"><span data-stu-id="05e62-137">Element</span></span>|<span data-ttu-id="05e62-138">説明</span><span class="sxs-lookup"><span data-stu-id="05e62-138">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="05e62-139">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="05e62-139">Defines the security settings for the transport.</span></span> <span data-ttu-id="05e62-140">この要素は <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="05e62-140">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="05e62-141">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="05e62-141">Defines the security settings for the message.</span></span> <span data-ttu-id="05e62-142">この要素は <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="05e62-142">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05e62-143">親要素</span><span class="sxs-lookup"><span data-stu-id="05e62-143">Parent Elements</span></span>  
  
|<span data-ttu-id="05e62-144">要素</span><span class="sxs-lookup"><span data-stu-id="05e62-144">Element</span></span>|<span data-ttu-id="05e62-145">説明</span><span class="sxs-lookup"><span data-stu-id="05e62-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05e62-146">binding</span><span class="sxs-lookup"><span data-stu-id="05e62-146">binding</span></span>|<span data-ttu-id="05e62-147">のバインディング要素 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="05e62-147">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05e62-148">解説</span><span class="sxs-lookup"><span data-stu-id="05e62-148">Remarks</span></span>  

 <span data-ttu-id="05e62-149">標準バインディングにはそれぞれ、転送セキュリティ要件を制御するためのパラメーターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="05e62-149">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="05e62-150">通常、これらのパラメーターには、使用されるセキュリティ レベル (メッセージ レベルまたはトランスポート レベル) を指定したセキュリティ モードと、クライアント資格情報の種類が含まれています。</span><span class="sxs-lookup"><span data-stu-id="05e62-150">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="05e62-151">これらのパラメーターが提示するオプションの選択に基づいて、適切なセキュリティが設定されたチャネル スタックが構築されます。</span><span class="sxs-lookup"><span data-stu-id="05e62-151">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="05e62-152">WCF (Windows Communication Foundation) に用意されているシステム標準のバインディグは、最も一般的なシナリオ要件の一部を満たすように設計されたセットです。</span><span class="sxs-lookup"><span data-stu-id="05e62-152">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="05e62-153">これらのバイディングでは、特定のシナリオを対象とするセキュリティ要件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="05e62-153">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="05e62-154">この構成要素によって、`netTcpBinding` のセキュリティ仕様が提供されます。</span><span class="sxs-lookup"><span data-stu-id="05e62-154">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="05e62-155">これは、コンピューター間通信に適した、安全で信頼できる最適化されたバインディングです。</span><span class="sxs-lookup"><span data-stu-id="05e62-155">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="05e62-156">既定では、このバインディングは、メッセージを配信するための TCP、メッセージの保護と認証を行うための Windows セキュリティ、信頼性を高めるための WS-ReliableMessaging、およびバイナリ メッセージのエンコーディングをサポートするランタイム通信スタックを生成します。</span><span class="sxs-lookup"><span data-stu-id="05e62-156">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e62-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="05e62-157">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="05e62-158">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="05e62-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="05e62-159">バインド</span><span class="sxs-lookup"><span data-stu-id="05e62-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="05e62-160">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="05e62-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="05e62-161">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="05e62-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
