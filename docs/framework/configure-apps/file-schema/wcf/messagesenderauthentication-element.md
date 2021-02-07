---
description: '詳細情報: <messageSenderAuthentication> 要素'
title: <messageSenderAuthentication> 要素
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 03c1cd626e7c3ad71026c076df3d757419810d74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749338"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="68f97-103">\<messageSenderAuthentication> 要素</span><span class="sxs-lookup"><span data-stu-id="68f97-103">\<messageSenderAuthentication> element</span></span>

<span data-ttu-id="68f97-104">ピアツーピア メッセージ送信者の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="68f97-104">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="68f97-105">ピアツーピアプログラミングの詳細については、「 [ピアツーピアネットワーク](../../../wcf/feature-details/peer-to-peer-networking.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68f97-105">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="68f97-106">構文</span><span class="sxs-lookup"><span data-stu-id="68f97-106">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68f97-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="68f97-107">Attributes and Elements</span></span>  

 <span data-ttu-id="68f97-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="68f97-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68f97-109">属性</span><span class="sxs-lookup"><span data-stu-id="68f97-109">Attributes</span></span>  
  
|<span data-ttu-id="68f97-110">属性</span><span class="sxs-lookup"><span data-stu-id="68f97-110">Attribute</span></span>|<span data-ttu-id="68f97-111">説明</span><span class="sxs-lookup"><span data-stu-id="68f97-111">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="68f97-112">カスタム型の検証に使用される型およびアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="68f97-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="68f97-113">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68f97-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="68f97-114">資格情報の検証に使用される 3 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="68f97-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="68f97-115">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68f97-115">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="68f97-116">証明書失効リスト (CRL) のチェックに使用されるモードのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="68f97-116">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="68f97-117">2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="68f97-117">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="68f97-118">この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="68f97-118">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="68f97-119">指定されたストアの場所にある **信頼さ** れた People ストアに対して検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="68f97-119">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="68f97-120">customCertificateValidatorType 属性</span><span class="sxs-lookup"><span data-stu-id="68f97-120">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="68f97-121">値</span><span class="sxs-lookup"><span data-stu-id="68f97-121">Value</span></span>|<span data-ttu-id="68f97-122">説明</span><span class="sxs-lookup"><span data-stu-id="68f97-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68f97-123">String</span><span class="sxs-lookup"><span data-stu-id="68f97-123">String</span></span>|<span data-ttu-id="68f97-124">任意。</span><span class="sxs-lookup"><span data-stu-id="68f97-124">Optional.</span></span> <span data-ttu-id="68f97-125">タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="68f97-125">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="68f97-126">少なくとも、名前空間とタイプ名が必要です。</span><span class="sxs-lookup"><span data-stu-id="68f97-126">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="68f97-127">省略可能な情報は、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンです。</span><span class="sxs-lookup"><span data-stu-id="68f97-127">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="68f97-128">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="68f97-128">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="68f97-129">値</span><span class="sxs-lookup"><span data-stu-id="68f97-129">Value</span></span>|<span data-ttu-id="68f97-130">説明</span><span class="sxs-lookup"><span data-stu-id="68f97-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68f97-131">列挙</span><span class="sxs-lookup"><span data-stu-id="68f97-131">Enumeration</span></span>|<span data-ttu-id="68f97-132">任意。</span><span class="sxs-lookup"><span data-stu-id="68f97-132">Optional.</span></span> <span data-ttu-id="68f97-133">`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="68f97-133">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="68f97-134">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="68f97-134">The default is `ChainTrust`.</span></span> <span data-ttu-id="68f97-135">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="68f97-135">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="68f97-136">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68f97-136">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="68f97-137">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="68f97-137">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="68f97-138">値</span><span class="sxs-lookup"><span data-stu-id="68f97-138">Value</span></span>|<span data-ttu-id="68f97-139">説明</span><span class="sxs-lookup"><span data-stu-id="68f97-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68f97-140">列挙</span><span class="sxs-lookup"><span data-stu-id="68f97-140">Enumeration</span></span>|<span data-ttu-id="68f97-141">`NoCheck`、`Online`、`Offline` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="68f97-141">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="68f97-142">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="68f97-142">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="68f97-143">詳細については、「 [証明書の使用](../../../wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68f97-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="68f97-144">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="68f97-144">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="68f97-145">値</span><span class="sxs-lookup"><span data-stu-id="68f97-145">Value</span></span>|<span data-ttu-id="68f97-146">説明</span><span class="sxs-lookup"><span data-stu-id="68f97-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68f97-147">列挙</span><span class="sxs-lookup"><span data-stu-id="68f97-147">Enumeration</span></span>|<span data-ttu-id="68f97-148">次のいずれかの値を指定できます。`LocalMachine` または `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="68f97-148">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="68f97-149">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="68f97-149">The default is `CurrentUser`.</span></span> <span data-ttu-id="68f97-150">クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="68f97-150">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="68f97-151">クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="68f97-151">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="68f97-152">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="68f97-152">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68f97-153">子要素</span><span class="sxs-lookup"><span data-stu-id="68f97-153">Child Elements</span></span>  

 <span data-ttu-id="68f97-154">なし。</span><span class="sxs-lookup"><span data-stu-id="68f97-154">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68f97-155">親要素</span><span class="sxs-lookup"><span data-stu-id="68f97-155">Parent Elements</span></span>  
  
|<span data-ttu-id="68f97-156">要素</span><span class="sxs-lookup"><span data-stu-id="68f97-156">Element</span></span>|<span data-ttu-id="68f97-157">説明</span><span class="sxs-lookup"><span data-stu-id="68f97-157">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="68f97-158">ピア サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="68f97-158">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68f97-159">解説</span><span class="sxs-lookup"><span data-stu-id="68f97-159">Remarks</span></span>  

 <span data-ttu-id="68f97-160">メッセージ認証を選択した場合は、この要素を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68f97-160">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="68f97-161">出力チャネルの場合、各メッセージはによって提供される証明書を使用して署名され [\<certificate>](certificate-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="68f97-161">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="68f97-162">すべてのメッセージは、アプリケーションに配信される前に、この要素の `customCertificateValidatorType` 属性で指定した検証を使用してメッセージ資格情報がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="68f97-162">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="68f97-163">検証は、資格情報を受け入れることも拒否することもできます。</span><span class="sxs-lookup"><span data-stu-id="68f97-163">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68f97-164">例</span><span class="sxs-lookup"><span data-stu-id="68f97-164">Example</span></span>  

 <span data-ttu-id="68f97-165">次のコードは、メッセージ送信者検証モードを `PeerOrChainTrust` に設定します。</span><span class="sxs-lookup"><span data-stu-id="68f97-165">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="68f97-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="68f97-166">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="68f97-167">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="68f97-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="68f97-168">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="68f97-168">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="68f97-169">[ピア チャネル メッセージの認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="68f97-169">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="68f97-170">[ピア チャネル カスタム認証](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="68f97-170">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="68f97-171">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="68f97-171">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
