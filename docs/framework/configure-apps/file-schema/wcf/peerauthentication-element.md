---
description: '詳細情報: <peerAuthentication> 要素'
title: <peerAuthentication> 要素
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 887b65a4a2a7da9d545bc25636be0ea6c646f6fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683724"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="686e5-103">\<peerAuthentication> 要素</span><span class="sxs-lookup"><span data-stu-id="686e5-103">\<peerAuthentication> Element</span></span>

<span data-ttu-id="686e5-104">ピアツーピア クライアントの認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="686e5-104">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="686e5-105">ピアツーピアプログラミングの詳細については、「 [ピアツーピアネットワーク](../../../wcf/feature-details/peer-to-peer-networking.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="686e5-105">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="686e5-106">構文</span><span class="sxs-lookup"><span data-stu-id="686e5-106">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="686e5-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="686e5-107">Attributes and Elements</span></span>  

 <span data-ttu-id="686e5-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="686e5-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="686e5-109">属性</span><span class="sxs-lookup"><span data-stu-id="686e5-109">Attributes</span></span>  
  
|<span data-ttu-id="686e5-110">属性</span><span class="sxs-lookup"><span data-stu-id="686e5-110">Attribute</span></span>|<span data-ttu-id="686e5-111">説明</span><span class="sxs-lookup"><span data-stu-id="686e5-111">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="686e5-112">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="686e5-112">Optional string.</span></span> <span data-ttu-id="686e5-113">カスタム型の検証に使用される型およびアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="686e5-113">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="686e5-114">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="686e5-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="686e5-115">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="686e5-115">Optional enumeration.</span></span> <span data-ttu-id="686e5-116">資格情報の検証に使用される 3 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="686e5-116">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="686e5-117">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="686e5-117">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="686e5-118">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="686e5-118">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="686e5-119">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="686e5-119">Optional enumeration.</span></span> <span data-ttu-id="686e5-120">証明書失効リスト (CRL) のチェックに使用されるモードのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="686e5-120">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="686e5-121">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="686e5-121">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="686e5-122">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="686e5-122">Optional enumeration.</span></span> <span data-ttu-id="686e5-123">2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="686e5-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="686e5-124">この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="686e5-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="686e5-125">指定されたストアの場所にある **信頼さ** れた People ストアに対して検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="686e5-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="686e5-126">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="686e5-126">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="686e5-127">customCertificateValidatorType 属性</span><span class="sxs-lookup"><span data-stu-id="686e5-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="686e5-128">値</span><span class="sxs-lookup"><span data-stu-id="686e5-128">Value</span></span>|<span data-ttu-id="686e5-129">説明</span><span class="sxs-lookup"><span data-stu-id="686e5-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="686e5-130">String</span><span class="sxs-lookup"><span data-stu-id="686e5-130">String</span></span>|<span data-ttu-id="686e5-131">タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="686e5-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="686e5-132">少なくとも、名前空間とタイプ名が必要です。</span><span class="sxs-lookup"><span data-stu-id="686e5-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="686e5-133">省略可能な情報は、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンです。</span><span class="sxs-lookup"><span data-stu-id="686e5-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="686e5-134">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="686e5-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="686e5-135">値</span><span class="sxs-lookup"><span data-stu-id="686e5-135">Value</span></span>|<span data-ttu-id="686e5-136">説明</span><span class="sxs-lookup"><span data-stu-id="686e5-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="686e5-137">列挙</span><span class="sxs-lookup"><span data-stu-id="686e5-137">Enumeration</span></span>|<span data-ttu-id="686e5-138">`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="686e5-138">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="686e5-139">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="686e5-139">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="686e5-140">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="686e5-140">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="686e5-141">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="686e5-141">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="686e5-142">値</span><span class="sxs-lookup"><span data-stu-id="686e5-142">Value</span></span>|<span data-ttu-id="686e5-143">説明</span><span class="sxs-lookup"><span data-stu-id="686e5-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="686e5-144">列挙</span><span class="sxs-lookup"><span data-stu-id="686e5-144">Enumeration</span></span>|<span data-ttu-id="686e5-145">`NoCheck`、`Online`、`Offline` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="686e5-145">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="686e5-146">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="686e5-146">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="686e5-147">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="686e5-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="686e5-148">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="686e5-148">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="686e5-149">値</span><span class="sxs-lookup"><span data-stu-id="686e5-149">Value</span></span>|<span data-ttu-id="686e5-150">説明</span><span class="sxs-lookup"><span data-stu-id="686e5-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="686e5-151">列挙</span><span class="sxs-lookup"><span data-stu-id="686e5-151">Enumeration</span></span>|<span data-ttu-id="686e5-152">次のいずれかの値を指定できます。`LocalMachine` または `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="686e5-152">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="686e5-153">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="686e5-153">The default is `CurrentUser`.</span></span> <span data-ttu-id="686e5-154">クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="686e5-154">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="686e5-155">クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="686e5-155">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="686e5-156">子要素</span><span class="sxs-lookup"><span data-stu-id="686e5-156">Child Elements</span></span>  

 <span data-ttu-id="686e5-157">なし。</span><span class="sxs-lookup"><span data-stu-id="686e5-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="686e5-158">親要素</span><span class="sxs-lookup"><span data-stu-id="686e5-158">Parent Elements</span></span>  
  
|<span data-ttu-id="686e5-159">要素</span><span class="sxs-lookup"><span data-stu-id="686e5-159">Element</span></span>|<span data-ttu-id="686e5-160">説明</span><span class="sxs-lookup"><span data-stu-id="686e5-160">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="686e5-161">ピア サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="686e5-161">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="686e5-162">解説</span><span class="sxs-lookup"><span data-stu-id="686e5-162">Remarks</span></span>  

 <span data-ttu-id="686e5-163">`<authentication>` 要素は、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> クラスに対応します。</span><span class="sxs-lookup"><span data-stu-id="686e5-163">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="686e5-164">この要素は、メッシュ内の近隣ノード間の認証時に呼び出される検証コントロールを指定します。</span><span class="sxs-lookup"><span data-stu-id="686e5-164">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="686e5-165">新しいピアが近隣ノードとの接続を確立しようとするとき、自身の資格情報を応答側のピアに渡します。</span><span class="sxs-lookup"><span data-stu-id="686e5-165">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="686e5-166">リモート パーティの資格情報を検証するために、応答側の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="686e5-166">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="686e5-167">メッシュ内でピア接続が確立されるたびに、両方のピアが相互に認証されます。つまり、双方の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="686e5-167">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="686e5-168">例</span><span class="sxs-lookup"><span data-stu-id="686e5-168">Example</span></span>  

 <span data-ttu-id="686e5-169">次のコードは、証明書検証モードを `PeerOrChainTrust` に設定します。</span><span class="sxs-lookup"><span data-stu-id="686e5-169">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="686e5-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="686e5-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="686e5-171">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="686e5-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="686e5-172">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="686e5-172">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="686e5-173">[ピア チャネル メッセージの認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="686e5-173">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="686e5-174">[ピア チャネル カスタム認証](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="686e5-174">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="686e5-175">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="686e5-175">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
