---
description: '詳細情報: <messageSenderAuthentication>'
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: e98388eafce24b0f19647364b6bbec94ee6ba135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749324"
---
# \<messageSenderAuthentication>

<span data-ttu-id="d5f7a-102">メッセージ送信者により使用されるピア証明書の認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-102">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="d5f7a-103">構文</span><span class="sxs-lookup"><span data-stu-id="d5f7a-103">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5f7a-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d5f7a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d5f7a-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5f7a-106">属性</span><span class="sxs-lookup"><span data-stu-id="d5f7a-106">Attributes</span></span>  
  
|<span data-ttu-id="d5f7a-107">属性</span><span class="sxs-lookup"><span data-stu-id="d5f7a-107">Attribute</span></span>|<span data-ttu-id="d5f7a-108">説明</span><span class="sxs-lookup"><span data-stu-id="d5f7a-108">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="d5f7a-109">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-109">Optional enumeration.</span></span> <span data-ttu-id="d5f7a-110">資格情報の検証に使用される 5 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-110">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="d5f7a-111">この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-111">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="d5f7a-112">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-112">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="d5f7a-113">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-113">Optional string.</span></span> <span data-ttu-id="d5f7a-114">ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-114">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="d5f7a-115">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-115">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="d5f7a-116">この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-116">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d5f7a-117">Windows Communication Foundation (WCF) は、信頼された people ストアに対してピア証明書を検証する既定のピア証明書検証コントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-117">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="d5f7a-118">証明書が有効なルートまでつながっていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-118">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="d5f7a-119">カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-119">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="d5f7a-120">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-120">Optional enumeration.</span></span> <span data-ttu-id="d5f7a-121">証明書失効モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-121">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="d5f7a-122">この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-122">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="d5f7a-123">システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-123">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="d5f7a-124">このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-124">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="d5f7a-125">失効チェックは、この属性を NoCheck に設定することにより無効にできます。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-125">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="d5f7a-126">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-126">Optional enumeration.</span></span> <span data-ttu-id="d5f7a-127">WCF セキュリティシステムによってピア証明書が検証される、信頼されたストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-127">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="d5f7a-128">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-128">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5f7a-129">子要素</span><span class="sxs-lookup"><span data-stu-id="d5f7a-129">Child Elements</span></span>  

 <span data-ttu-id="d5f7a-130">なし。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5f7a-131">親要素</span><span class="sxs-lookup"><span data-stu-id="d5f7a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d5f7a-132">要素</span><span class="sxs-lookup"><span data-stu-id="d5f7a-132">Element</span></span>|<span data-ttu-id="d5f7a-133">説明</span><span class="sxs-lookup"><span data-stu-id="d5f7a-133">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="d5f7a-134">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-134">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5f7a-135">解説</span><span class="sxs-lookup"><span data-stu-id="d5f7a-135">Remarks</span></span>  

 <span data-ttu-id="d5f7a-136">メッセージ認証を選択した場合は、この要素を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-136">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="d5f7a-137">出力チャネルの場合、各メッセージはによって提供される証明書を使用して署名され [\<certificate>](certificate-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-137">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="d5f7a-138">すべてのメッセージは、アプリケーションに配信される前に、この要素の `customCertificateValidatorType` 属性で指定した検証を使用してメッセージ資格情報がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-138">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="d5f7a-139">検証は、資格情報を受け入れることも拒否することもできます。</span><span class="sxs-lookup"><span data-stu-id="d5f7a-139">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f7a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5f7a-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="d5f7a-141">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="d5f7a-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d5f7a-142">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="d5f7a-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="d5f7a-143">[ピア チャネル メッセージの認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d5f7a-143">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="d5f7a-144">[ピア チャネル カスタム認証](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d5f7a-144">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="d5f7a-145">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="d5f7a-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
