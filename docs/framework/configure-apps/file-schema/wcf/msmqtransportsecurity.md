---
description: '詳細情報: <msmqTransportSecurity>'
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: d5a681c287749598c8c80470ea6d800f1687a80d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684166"
---
# \<msmqTransportSecurity>

<span data-ttu-id="81e6b-102">カスタム バインディングの MSMQ トランスポート セキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-102">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="81e6b-103">構文</span><span class="sxs-lookup"><span data-stu-id="81e6b-103">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81e6b-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="81e6b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="81e6b-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81e6b-106">属性</span><span class="sxs-lookup"><span data-stu-id="81e6b-106">Attributes</span></span>  
  
|<span data-ttu-id="81e6b-107">属性</span><span class="sxs-lookup"><span data-stu-id="81e6b-107">Attribute</span></span>|<span data-ttu-id="81e6b-108">説明</span><span class="sxs-lookup"><span data-stu-id="81e6b-108">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="81e6b-109">MSMQ トランスポートによるメッセージの認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-109">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="81e6b-110">これが `None` に設定されている場合、`msmqProtectionLevel` 属性の値も `None` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81e6b-110">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="81e6b-111">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="81e6b-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="81e6b-112">-None: 認証なし。</span><span class="sxs-lookup"><span data-stu-id="81e6b-112">-   None: No authentication.</span></span><br /><span data-ttu-id="81e6b-113">-Windows: 認証メカニズムは Active Directory を使用して、メッセージに関連付けられている SID の x.509 証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-113">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="81e6b-114">次に、これを使用してキューの ACL がチェックされ、ユーザーがキューに書き込む権限を持っていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="81e6b-114">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="81e6b-115">-Certificate: チャネルは、証明書ストアから証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-115">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="81e6b-116">既定値は Windows です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-116">The default value is Windows.</span></span> <span data-ttu-id="81e6b-117">この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-117">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="81e6b-118">メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-118">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="81e6b-119">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="81e6b-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="81e6b-120">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="81e6b-120">-   RC4Stream</span></span><br /><span data-ttu-id="81e6b-121">-AES</span><span class="sxs-lookup"><span data-stu-id="81e6b-121">-   AES</span></span><br /><br /> <span data-ttu-id="81e6b-122">既定値は RC4Stream です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-122">The default value is RC4Stream.</span></span> <span data-ttu-id="81e6b-123">この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-123">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="81e6b-124">MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-124">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="81e6b-125">暗号化によってメッセージの整合性が確保されますが、EncryptAndSign ではメッセージの整合性と否認不可が保証されます。つまり、メッセージは実際には送信者から送信され、送信者はそのことを伝えるものです。</span><span class="sxs-lookup"><span data-stu-id="81e6b-125">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="81e6b-126">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="81e6b-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="81e6b-127">-None: 保護がありません。</span><span class="sxs-lookup"><span data-stu-id="81e6b-127">-   None: No protection.</span></span><br /><span data-ttu-id="81e6b-128">-Sign: メッセージは署名されています。</span><span class="sxs-lookup"><span data-stu-id="81e6b-128">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="81e6b-129">-EncryptAndSign: メッセージは暗号化され、署名されます。</span><span class="sxs-lookup"><span data-stu-id="81e6b-129">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="81e6b-130">既定値は Sign です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-130">The default value is Sign.</span></span> <span data-ttu-id="81e6b-131">この属性は <xref:System.Net.Security.ProtectionLevel> 型です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-131">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="81e6b-132">署名の一部としてダイジェストの計算に使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-132">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="81e6b-133">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="81e6b-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="81e6b-134">-MD5</span><span class="sxs-lookup"><span data-stu-id="81e6b-134">-   MD5</span></span><br /><span data-ttu-id="81e6b-135">-SHA1</span><span class="sxs-lookup"><span data-stu-id="81e6b-135">-   SHA1</span></span><br /><span data-ttu-id="81e6b-136">-SHA256</span><span class="sxs-lookup"><span data-stu-id="81e6b-136">-   SHA256</span></span><br /><span data-ttu-id="81e6b-137">-SHA512</span><span class="sxs-lookup"><span data-stu-id="81e6b-137">-   SHA512</span></span><br /><br /> <span data-ttu-id="81e6b-138">既定値は SHA1 です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-138">The default value is SHA1.</span></span> <span data-ttu-id="81e6b-139">この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="81e6b-139">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="81e6b-140">MD5 と SHA1 の衝突の問題のため、SHA256 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="81e6b-140">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81e6b-141">子要素</span><span class="sxs-lookup"><span data-stu-id="81e6b-141">Child Elements</span></span>  

 <span data-ttu-id="81e6b-142">なし。</span><span class="sxs-lookup"><span data-stu-id="81e6b-142">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81e6b-143">親要素</span><span class="sxs-lookup"><span data-stu-id="81e6b-143">Parent Elements</span></span>  
  
|<span data-ttu-id="81e6b-144">要素</span><span class="sxs-lookup"><span data-stu-id="81e6b-144">Element</span></span>|<span data-ttu-id="81e6b-145">説明</span><span class="sxs-lookup"><span data-stu-id="81e6b-145">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="81e6b-146">Message Queuing (MSMQ) の送信側または受信側とのやり取りに必要な設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-146">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="81e6b-147">ネイティブ MSMQ プロトコルを使用する Windows Communication Foundation (WCF) サービスのキュー通信プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="81e6b-147">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e6b-148">解説</span><span class="sxs-lookup"><span data-stu-id="81e6b-148">Remarks</span></span>  

 <span data-ttu-id="81e6b-149">トランスポートセキュリティの詳細については、「 [トランスポートセキュリティ](../../../wcf/feature-details/transport-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81e6b-149">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e6b-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="81e6b-150">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="81e6b-151">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="81e6b-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="81e6b-152">トランスポート</span><span class="sxs-lookup"><span data-stu-id="81e6b-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="81e6b-153">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="81e6b-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="81e6b-154">バインド</span><span class="sxs-lookup"><span data-stu-id="81e6b-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81e6b-155">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="81e6b-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="81e6b-156">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="81e6b-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="81e6b-157">トランスポートセキュリティ</span><span class="sxs-lookup"><span data-stu-id="81e6b-157">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
