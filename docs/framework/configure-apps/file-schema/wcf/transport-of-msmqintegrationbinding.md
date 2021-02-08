---
description: 詳細については <transport> 、 <msmqIntegrationBinding>
title: <transport> の <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: bcca714320f333a16d518248531efe8039ff566e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773525"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="cd327-103">\<transport> の \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="cd327-103">\<transport> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="cd327-104">メッセージ キュー統合トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd327-104">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="cd327-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd327-105">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd327-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cd327-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cd327-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd327-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd327-108">属性</span><span class="sxs-lookup"><span data-stu-id="cd327-108">Attributes</span></span>  
  
|<span data-ttu-id="cd327-109">属性</span><span class="sxs-lookup"><span data-stu-id="cd327-109">Attribute</span></span>|<span data-ttu-id="cd327-110">説明</span><span class="sxs-lookup"><span data-stu-id="cd327-110">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="cd327-111">MSMQ トランスポートによるメッセージの認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd327-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="cd327-112">これが `None` に設定されている場合、`msmqProtectionLevel` 属性の値も `None` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd327-112">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="cd327-113">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cd327-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cd327-114">-None: 認証なし。</span><span class="sxs-lookup"><span data-stu-id="cd327-114">-   None: No authentication.</span></span><br /><span data-ttu-id="cd327-115">-WindowsDomain: 認証メカニズムは Active Directory を使用して、メッセージに関連付けられている SID の x.509 証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="cd327-115">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="cd327-116">次に、これを使用してキューの ACL がチェックされ、ユーザーがキューに書き込む権限を持っていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="cd327-116">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="cd327-117">-Certificate: チャネルは、証明書ストアから証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="cd327-117">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="cd327-118">既定値は WindowsDomain です。</span><span class="sxs-lookup"><span data-stu-id="cd327-118">The default value is WindowsDomain.</span></span> <span data-ttu-id="cd327-119">この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="cd327-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="cd327-120">メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd327-120">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="cd327-121">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cd327-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cd327-122">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="cd327-122">-   RC4Stream</span></span><br /><span data-ttu-id="cd327-123">-AES</span><span class="sxs-lookup"><span data-stu-id="cd327-123">-   AES</span></span><br /><br /> <span data-ttu-id="cd327-124">既定値は RC4Stream です。</span><span class="sxs-lookup"><span data-stu-id="cd327-124">The default value is RC4Stream.</span></span> <span data-ttu-id="cd327-125">この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="cd327-125">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="cd327-126">MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd327-126">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="cd327-127">暗号化によってメッセージの整合性が確保されますが、EncryptAndSign ではメッセージの整合性と否認不可が保証されます。つまり、メッセージは実際には送信者から送信され、送信者はそのことを伝えるものです。</span><span class="sxs-lookup"><span data-stu-id="cd327-127">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="cd327-128">-有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cd327-128">-   Valid values include the following:</span></span><br /><span data-ttu-id="cd327-129">-None: 保護がありません。</span><span class="sxs-lookup"><span data-stu-id="cd327-129">-   None: No protection.</span></span><br /><span data-ttu-id="cd327-130">-Sign: メッセージは署名されています。</span><span class="sxs-lookup"><span data-stu-id="cd327-130">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="cd327-131">-EncryptAndSign: メッセージは暗号化され、署名されます。</span><span class="sxs-lookup"><span data-stu-id="cd327-131">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="cd327-132">既定値は Sign です。</span><span class="sxs-lookup"><span data-stu-id="cd327-132">The default value is Sign.</span></span> <span data-ttu-id="cd327-133">この属性は、ProtectionLevel 型です。</span><span class="sxs-lookup"><span data-stu-id="cd327-133">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="cd327-134">-署名の一部としてダイジェストを計算するために使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd327-134">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="cd327-135">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cd327-135">Valid values include the following:</span></span><br /><span data-ttu-id="cd327-136">-MD5</span><span class="sxs-lookup"><span data-stu-id="cd327-136">-   MD5</span></span><br /><span data-ttu-id="cd327-137">-SHA1</span><span class="sxs-lookup"><span data-stu-id="cd327-137">-   SHA1</span></span><br /><span data-ttu-id="cd327-138">-SHA256</span><span class="sxs-lookup"><span data-stu-id="cd327-138">-   SHA256</span></span><br /><span data-ttu-id="cd327-139">-SHA512</span><span class="sxs-lookup"><span data-stu-id="cd327-139">-   SHA512</span></span><br /><br /> <span data-ttu-id="cd327-140">既定値は SHA1 です。</span><span class="sxs-lookup"><span data-stu-id="cd327-140">The default value is SHA1.</span></span> <span data-ttu-id="cd327-141">この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="cd327-141">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="cd327-142">MD5 と SHA1 の衝突の問題のため、SHA256 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd327-142">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd327-143">子要素</span><span class="sxs-lookup"><span data-stu-id="cd327-143">Child Elements</span></span>  

 <span data-ttu-id="cd327-144">なし</span><span class="sxs-lookup"><span data-stu-id="cd327-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd327-145">親要素</span><span class="sxs-lookup"><span data-stu-id="cd327-145">Parent Elements</span></span>  
  
|<span data-ttu-id="cd327-146">要素</span><span class="sxs-lookup"><span data-stu-id="cd327-146">Element</span></span>|<span data-ttu-id="cd327-147">説明</span><span class="sxs-lookup"><span data-stu-id="cd327-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="cd327-148">MSMQ バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd327-148">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd327-149">解説</span><span class="sxs-lookup"><span data-stu-id="cd327-149">Remarks</span></span>  

 <span data-ttu-id="cd327-150">この要素は、メッセージ キュー統合トランスポートのセキュリティ設定をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="cd327-150">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="cd327-151">設定は、メッセージ キュー統合トランスポートとキューに置かれているトランスポートの両方で同じです。</span><span class="sxs-lookup"><span data-stu-id="cd327-151">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="cd327-152">この設定を使用すると、認証モード、暗号化アルゴリズム、セキュア ハッシュ アルゴリズム、および保護レベルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="cd327-152">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd327-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd327-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="cd327-154">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="cd327-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cd327-155">バインド</span><span class="sxs-lookup"><span data-stu-id="cd327-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cd327-156">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="cd327-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cd327-157">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="cd327-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
