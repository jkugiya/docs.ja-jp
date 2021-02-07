---
description: '詳細については、次を参照してください: <peer> of <clientCredentials> 要素'
title: <peer><clientCredentials>要素の
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 1ff9386ba51dcf6bab6df71bd345cdaa59f18e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683789"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="66a77-103">\<peer>\<clientCredentials>要素の</span><span class="sxs-lookup"><span data-stu-id="66a77-103">\<peer> of \<clientCredentials> Element</span></span>

<span data-ttu-id="66a77-104">ピアツーピア クライアントの認証時に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="66a77-104">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="66a77-105">構文</span><span class="sxs-lookup"><span data-stu-id="66a77-105">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66a77-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="66a77-106">Attributes and Elements</span></span>  

 <span data-ttu-id="66a77-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="66a77-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66a77-108">属性</span><span class="sxs-lookup"><span data-stu-id="66a77-108">Attributes</span></span>  

 <span data-ttu-id="66a77-109">なし。</span><span class="sxs-lookup"><span data-stu-id="66a77-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66a77-110">子要素</span><span class="sxs-lookup"><span data-stu-id="66a77-110">Child Elements</span></span>  
  
|<span data-ttu-id="66a77-111">要素</span><span class="sxs-lookup"><span data-stu-id="66a77-111">Element</span></span>|<span data-ttu-id="66a77-112">説明</span><span class="sxs-lookup"><span data-stu-id="66a77-112">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="66a77-113">ピアツーピア クライアントのメッセージの署名と暗号化に使用する X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="66a77-113">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="66a77-114">.</span><span class="sxs-lookup"><span data-stu-id="66a77-114">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="66a77-115">ピア クライアントの認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="66a77-115">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="66a77-116">メッセージ送信者の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="66a77-116">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66a77-117">親要素</span><span class="sxs-lookup"><span data-stu-id="66a77-117">Parent Elements</span></span>  
  
|<span data-ttu-id="66a77-118">要素</span><span class="sxs-lookup"><span data-stu-id="66a77-118">Element</span></span>|<span data-ttu-id="66a77-119">説明</span><span class="sxs-lookup"><span data-stu-id="66a77-119">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="66a77-120">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="66a77-120">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66a77-121">解説</span><span class="sxs-lookup"><span data-stu-id="66a77-121">Remarks</span></span>  

 <span data-ttu-id="66a77-122">この構成要素は、ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報と、ピア ノードが他のピア ノードを認証するために使用する認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="66a77-122">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="66a77-123">詳細については、「 [ピアチャネルメッセージ認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) 」および「 [ピアチャネルアプリケーションのセキュリティ保護](../../../wcf/feature-details/securing-peer-channel-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a77-123">For more information, see [Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a77-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="66a77-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="66a77-125">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="66a77-125">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="66a77-126">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="66a77-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="66a77-127">[ピア チャネル メッセージの認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="66a77-127">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="66a77-128">[ピア チャネル カスタム認証](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="66a77-128">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="66a77-129">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="66a77-129">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="66a77-130">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="66a77-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
