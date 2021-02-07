---
description: 詳細については <transport> 、 <netPeerTcpBinding>
title: <transport> の <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: e93885234577e4f3c7a99be66e4798d33ffb5893
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664575"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="d20a6-103">\<transport> の \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="d20a6-103">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="d20a6-104">を使用する場合のトランスポートレベルのセキュリティ設定を指定し [\<netPeerTcpBinding>](netpeertcpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-104">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="d20a6-105">構文</span><span class="sxs-lookup"><span data-stu-id="d20a6-105">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d20a6-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d20a6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d20a6-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d20a6-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d20a6-108">属性</span><span class="sxs-lookup"><span data-stu-id="d20a6-108">Attributes</span></span>  
  
|<span data-ttu-id="d20a6-109">属性</span><span class="sxs-lookup"><span data-stu-id="d20a6-109">Attribute</span></span>|<span data-ttu-id="d20a6-110">説明</span><span class="sxs-lookup"><span data-stu-id="d20a6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d20a6-111">credentialType</span><span class="sxs-lookup"><span data-stu-id="d20a6-111">credentialType</span></span>|<span data-ttu-id="d20a6-112">任意。</span><span class="sxs-lookup"><span data-stu-id="d20a6-112">Optional.</span></span> <span data-ttu-id="d20a6-113">ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="d20a6-113">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="d20a6-114">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="d20a6-114">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="d20a6-115">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="d20a6-115">credentialType Attribute</span></span>  
  
|<span data-ttu-id="d20a6-116">値</span><span class="sxs-lookup"><span data-stu-id="d20a6-116">Value</span></span>|<span data-ttu-id="d20a6-117">説明</span><span class="sxs-lookup"><span data-stu-id="d20a6-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d20a6-118">Certificate</span><span class="sxs-lookup"><span data-stu-id="d20a6-118">Certificate</span></span>|<span data-ttu-id="d20a6-119">ピア チャネル トランスポートの認証には X 509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="d20a6-119">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="d20a6-120">Password</span><span class="sxs-lookup"><span data-stu-id="d20a6-120">Password</span></span>|<span data-ttu-id="d20a6-121">ピア チャネル トランスポートの認証には正しいパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="d20a6-121">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d20a6-122">子要素</span><span class="sxs-lookup"><span data-stu-id="d20a6-122">Child Elements</span></span>  

 <span data-ttu-id="d20a6-123">なし</span><span class="sxs-lookup"><span data-stu-id="d20a6-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d20a6-124">親要素</span><span class="sxs-lookup"><span data-stu-id="d20a6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d20a6-125">要素</span><span class="sxs-lookup"><span data-stu-id="d20a6-125">Element</span></span>|<span data-ttu-id="d20a6-126">説明</span><span class="sxs-lookup"><span data-stu-id="d20a6-126">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="d20a6-127">のセキュリティ設定を定義し [\<netPeerTcpBinding>](netpeertcpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="d20a6-127">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d20a6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d20a6-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="d20a6-129">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d20a6-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d20a6-130">バインド</span><span class="sxs-lookup"><span data-stu-id="d20a6-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d20a6-131">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="d20a6-131">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d20a6-132">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="d20a6-132">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
