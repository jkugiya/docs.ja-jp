---
description: 詳細については <transport> 、 <netMsmqBinding>
title: <transport> の <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 04768f259629277abd758d102f3873bb28f16514
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773499"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="cc090-103">\<transport> の \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="cc090-103">\<transport> of \<netMsmqBinding></span></span>

<span data-ttu-id="cc090-104">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cc090-104">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="cc090-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc090-105">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc090-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cc090-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cc090-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc090-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc090-108">属性</span><span class="sxs-lookup"><span data-stu-id="cc090-108">Attributes</span></span>  
  
|<span data-ttu-id="cc090-109">属性</span><span class="sxs-lookup"><span data-stu-id="cc090-109">Attribute</span></span>|<span data-ttu-id="cc090-110">説明</span><span class="sxs-lookup"><span data-stu-id="cc090-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc090-111">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="cc090-111">msmqAuthenticationMode</span></span>|<span data-ttu-id="cc090-112">MSMQ トランスポートによるメッセージの認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc090-112">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="cc090-113">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc090-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cc090-114">-None: 認証なし。</span><span class="sxs-lookup"><span data-stu-id="cc090-114">-   None: No authentication.</span></span><br /><span data-ttu-id="cc090-115">-WindowsDomain: 認証メカニズムは Active Directory を使用して、メッセージに関連付けられているセキュリティ識別子の x.509 証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc090-115">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="cc090-116">次に、これを使用してキューの ACL がチェックされ、ユーザーがキューへの書き込み権限を持っていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="cc090-116">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="cc090-117">-Certificate: チャネルは、証明書ストアから証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc090-117">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="cc090-118">既定値は、`WindowsDomain` です。</span><span class="sxs-lookup"><span data-stu-id="cc090-118">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="cc090-119">この属性が `None` に設定されている場合、`msmqProtectionLevel` 属性も `None` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc090-119">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="cc090-120">この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="cc090-120">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="cc090-121">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="cc090-121">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="cc090-122">メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc090-122">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="cc090-123">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc090-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cc090-124">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="cc090-124">-   RC4Stream</span></span><br /><span data-ttu-id="cc090-125">-AES</span><span class="sxs-lookup"><span data-stu-id="cc090-125">-   AES</span></span><br /><span data-ttu-id="cc090-126">-既定値は `RC4Stream` です。</span><span class="sxs-lookup"><span data-stu-id="cc090-126">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="cc090-127">この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="cc090-127">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="cc090-128">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="cc090-128">msmqProtectionLevel</span></span>|<span data-ttu-id="cc090-129">MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc090-129">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="cc090-130">暗号化を行うとメッセージの整合性が確保されますが、署名および暗号化を使用するとメッセージの整合性と否認防止の両方が確保されます。</span><span class="sxs-lookup"><span data-stu-id="cc090-130">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="cc090-131">つまり、実際には送信者から送信されたメッセージであり、送信者はその人物であると言います。</span><span class="sxs-lookup"><span data-stu-id="cc090-131">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="cc090-132">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc090-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cc090-133">-None: 保護がありません。</span><span class="sxs-lookup"><span data-stu-id="cc090-133">-   None: No protection.</span></span><br /><span data-ttu-id="cc090-134">-Sign: メッセージは署名されています。</span><span class="sxs-lookup"><span data-stu-id="cc090-134">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="cc090-135">-EncryptAndSign: メッセージは暗号化され、署名されます。</span><span class="sxs-lookup"><span data-stu-id="cc090-135">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="cc090-136">-既定値は `Sign` です。</span><span class="sxs-lookup"><span data-stu-id="cc090-136">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="cc090-137">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="cc090-137">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="cc090-138">メッセージ ダイジェストの計算に使用されるハッシュ アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc090-138">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="cc090-139">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc090-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cc090-140">-MD5</span><span class="sxs-lookup"><span data-stu-id="cc090-140">-   MD5</span></span><br /><span data-ttu-id="cc090-141">-SHA1</span><span class="sxs-lookup"><span data-stu-id="cc090-141">-   SHA1</span></span><br /><span data-ttu-id="cc090-142">-SHA256</span><span class="sxs-lookup"><span data-stu-id="cc090-142">-   SHA256</span></span><br /><span data-ttu-id="cc090-143">-SHA512</span><span class="sxs-lookup"><span data-stu-id="cc090-143">-   SHA512</span></span><br /><br /> <span data-ttu-id="cc090-144">既定値は、`SHA1` です。</span><span class="sxs-lookup"><span data-stu-id="cc090-144">The default is `SHA1`.</span></span> <span data-ttu-id="cc090-145">この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="cc090-145">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="cc090-146">MD5 と SHA1 の衝突の問題のため、SHA256 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cc090-146">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc090-147">子要素</span><span class="sxs-lookup"><span data-stu-id="cc090-147">Child Elements</span></span>  

 <span data-ttu-id="cc090-148">なし</span><span class="sxs-lookup"><span data-stu-id="cc090-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc090-149">親要素</span><span class="sxs-lookup"><span data-stu-id="cc090-149">Parent Elements</span></span>  
  
|<span data-ttu-id="cc090-150">要素</span><span class="sxs-lookup"><span data-stu-id="cc090-150">Element</span></span>|<span data-ttu-id="cc090-151">説明</span><span class="sxs-lookup"><span data-stu-id="cc090-151">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="cc090-152">キューに置かれているトランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cc090-152">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc090-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc090-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="cc090-154">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="cc090-154">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="cc090-155">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="cc090-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cc090-156">バインド</span><span class="sxs-lookup"><span data-stu-id="cc090-156">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cc090-157">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="cc090-157">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cc090-158">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="cc090-158">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
