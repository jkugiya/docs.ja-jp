---
description: 詳細については <peer> 、 <serviceCredentials>
title: <peer> の <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 4d959f5061bb8069623b277219576dbd77ea52c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683737"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="41770-103">\<peer> の \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="41770-103">\<peer> of \<serviceCredentials></span></span>

<span data-ttu-id="41770-104">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="41770-104">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="41770-105">構文</span><span class="sxs-lookup"><span data-stu-id="41770-105">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41770-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="41770-106">Attributes and Elements</span></span>  

 <span data-ttu-id="41770-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="41770-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41770-108">属性</span><span class="sxs-lookup"><span data-stu-id="41770-108">Attributes</span></span>  

 <span data-ttu-id="41770-109">なし。</span><span class="sxs-lookup"><span data-stu-id="41770-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41770-110">子要素</span><span class="sxs-lookup"><span data-stu-id="41770-110">Child Elements</span></span>  
  
|<span data-ttu-id="41770-111">要素</span><span class="sxs-lookup"><span data-stu-id="41770-111">Element</span></span>|<span data-ttu-id="41770-112">説明</span><span class="sxs-lookup"><span data-stu-id="41770-112">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="41770-113">ピアツーピア サービスのメッセージの署名と暗号化に使用する X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="41770-113">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="41770-114">.</span><span class="sxs-lookup"><span data-stu-id="41770-114">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="41770-115">メッセージ送信者の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="41770-115">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="41770-116">ピア サービスの認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="41770-116">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41770-117">親要素</span><span class="sxs-lookup"><span data-stu-id="41770-117">Parent Elements</span></span>  
  
|<span data-ttu-id="41770-118">要素</span><span class="sxs-lookup"><span data-stu-id="41770-118">Element</span></span>|<span data-ttu-id="41770-119">説明</span><span class="sxs-lookup"><span data-stu-id="41770-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="41770-120">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="41770-120">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41770-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="41770-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="41770-122">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="41770-122">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="41770-123">[ピア チャネル メッセージの認証](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="41770-123">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="41770-124">[ピア チャネル カスタム認証](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="41770-124">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="41770-125">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="41770-125">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="41770-126">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="41770-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
