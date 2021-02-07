---
description: 詳細については <transport> 、 <netTcpBinding>
title: <transport> の <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 9005de300b41c9f53c62875ee185d0f8a3ee8d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664549"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="0fc1d-103">\<transport> の \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="0fc1d-103">\<transport> of \<netTcpBinding></span></span>

<span data-ttu-id="0fc1d-104">で構成されるエンドポイントのメッセージレベルのセキュリティ要件の種類を定義し [\<netTcpBinding>](nettcpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-104">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0fc1d-105">構文</span><span class="sxs-lookup"><span data-stu-id="0fc1d-105">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fc1d-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0fc1d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0fc1d-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fc1d-108">属性</span><span class="sxs-lookup"><span data-stu-id="0fc1d-108">Attributes</span></span>  
  
|<span data-ttu-id="0fc1d-109">属性</span><span class="sxs-lookup"><span data-stu-id="0fc1d-109">Attribute</span></span>|<span data-ttu-id="0fc1d-110">説明</span><span class="sxs-lookup"><span data-stu-id="0fc1d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fc1d-111">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="0fc1d-111">clientCredentialType</span></span>|<span data-ttu-id="0fc1d-112">任意。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-112">Optional.</span></span> <span data-ttu-id="0fc1d-113">トランスポート セキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-113">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="0fc1d-114">-既定値は `Windows` です。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-114">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="0fc1d-115">-この属性の型は <xref:System.ServiceModel.TcpClientCredentialType> です。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-115">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="0fc1d-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="0fc1d-116">protectionLevel</span></span>|<span data-ttu-id="0fc1d-117">任意。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-117">Optional.</span></span> <span data-ttu-id="0fc1d-118">TCP トランスポートのレベルでセキュリティを定義します。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-118">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="0fc1d-119">メッセージに署名を付けることで、メッセージの転送中に第三者によって改ざんされるリスクが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="0fc1d-120">暗号化によって、トランスポート中にデータ レベルのプライバシーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-120">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="0fc1d-121">既定値は `EncryptAndSign` です。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-121">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="0fc1d-122">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="0fc1d-122">sslProtocols</span></span>|<span data-ttu-id="0fc1d-123">どの SslProtocols がサポートされているのかを指定する SslProtocols 列挙型フラグの値。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-123">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="0fc1d-124">既定値は Tls&#124;Tls11&#124;Tls12 です。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-124">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="0fc1d-125">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="0fc1d-125">policyEnforcement</span></span>|<span data-ttu-id="0fc1d-126">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="0fc1d-127">1. never –ポリシーは適用されません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="0fc1d-128">2. WhenSupported –ポリシーは、クライアントが拡張保護をサポートしている場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="0fc1d-129">3. always –ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="0fc1d-130">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="0fc1d-131">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="0fc1d-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="0fc1d-132">値</span><span class="sxs-lookup"><span data-stu-id="0fc1d-132">Value</span></span>|<span data-ttu-id="0fc1d-133">説明</span><span class="sxs-lookup"><span data-stu-id="0fc1d-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fc1d-134">なし</span><span class="sxs-lookup"><span data-stu-id="0fc1d-134">None</span></span>|<span data-ttu-id="0fc1d-135">クライアントは匿名です。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-135">The client is anonymous.</span></span> <span data-ttu-id="0fc1d-136">これには、サービスの証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-136">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="0fc1d-137">Windows</span><span class="sxs-lookup"><span data-stu-id="0fc1d-137">Windows</span></span>|<span data-ttu-id="0fc1d-138">SP ネゴシエーション (Kerberos ネゴシエーション) を使用して、クライアントの Windows 認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-138">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="0fc1d-139">Certificate</span><span class="sxs-lookup"><span data-stu-id="0fc1d-139">Certificate</span></span>|<span data-ttu-id="0fc1d-140">クライアントは、証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-140">The client is authenticated using a certificate.</span></span> <span data-ttu-id="0fc1d-141">これは SSL ネゴシエーションを使用し、サービスの証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-141">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="0fc1d-142">protectionLevel 属性</span><span class="sxs-lookup"><span data-stu-id="0fc1d-142">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="0fc1d-143">値</span><span class="sxs-lookup"><span data-stu-id="0fc1d-143">Value</span></span>|<span data-ttu-id="0fc1d-144">説明</span><span class="sxs-lookup"><span data-stu-id="0fc1d-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fc1d-145">なし</span><span class="sxs-lookup"><span data-stu-id="0fc1d-145">None</span></span>|<span data-ttu-id="0fc1d-146">保護されません。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-146">No protection.</span></span>|  
|<span data-ttu-id="0fc1d-147">Sign</span><span class="sxs-lookup"><span data-stu-id="0fc1d-147">Sign</span></span>|<span data-ttu-id="0fc1d-148">メッセージは署名されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-148">Messages are signed.</span></span>|  
|<span data-ttu-id="0fc1d-149">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="0fc1d-149">EncryptAndSign</span></span>|<span data-ttu-id="0fc1d-150">-メッセージは暗号化され、署名されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-150">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fc1d-151">子要素</span><span class="sxs-lookup"><span data-stu-id="0fc1d-151">Child Elements</span></span>  

 <span data-ttu-id="0fc1d-152">なし</span><span class="sxs-lookup"><span data-stu-id="0fc1d-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fc1d-153">親要素</span><span class="sxs-lookup"><span data-stu-id="0fc1d-153">Parent Elements</span></span>  
  
|<span data-ttu-id="0fc1d-154">要素</span><span class="sxs-lookup"><span data-stu-id="0fc1d-154">Element</span></span>|<span data-ttu-id="0fc1d-155">説明</span><span class="sxs-lookup"><span data-stu-id="0fc1d-155">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="0fc1d-156">のセキュリティ機能を指定し [\<netTcpBinding>](nettcpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-156">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fc1d-157">解説</span><span class="sxs-lookup"><span data-stu-id="0fc1d-157">Remarks</span></span>  

 <span data-ttu-id="0fc1d-158">トランスポート セキュリティは、SOAP メッセージの整合性と機密性の保護、および相互認証に使用します。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-158">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="0fc1d-159">このセキュリティ モードがバインディング上で選択された場合、チャネル スタックはセキュリティ トランスポートを使用して構成され、SOAP メッセージは Windows (ネゴシエート) や TCP 上の SSL などのトランスポート セキュリティを使用して保護されます。</span><span class="sxs-lookup"><span data-stu-id="0fc1d-159">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc1d-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fc1d-160">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="0fc1d-161">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="0fc1d-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0fc1d-162">バインド</span><span class="sxs-lookup"><span data-stu-id="0fc1d-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0fc1d-163">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="0fc1d-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0fc1d-164">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="0fc1d-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
