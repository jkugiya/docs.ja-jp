---
description: 詳細については <transport> 、 <peerTransport>
title: <transport> の <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: ba3405c5dfadb513f92ebd537409a3f7b12fa291
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664510"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="98d7f-103">\<transport> の \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="98d7f-103">\<transport> of \<peerTransport></span></span>

<span data-ttu-id="98d7f-104">このバインドで構成されたピアが送信する、セキュリティで保護されたメッセージのトランスポートの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="98d7f-104">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="98d7f-105">構文</span><span class="sxs-lookup"><span data-stu-id="98d7f-105">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98d7f-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="98d7f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="98d7f-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="98d7f-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98d7f-108">属性</span><span class="sxs-lookup"><span data-stu-id="98d7f-108">Attributes</span></span>  
  
|<span data-ttu-id="98d7f-109">属性</span><span class="sxs-lookup"><span data-stu-id="98d7f-109">Attribute</span></span>|<span data-ttu-id="98d7f-110">説明</span><span class="sxs-lookup"><span data-stu-id="98d7f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98d7f-111">credentialType</span><span class="sxs-lookup"><span data-stu-id="98d7f-111">credentialType</span></span>|<span data-ttu-id="98d7f-112">任意。</span><span class="sxs-lookup"><span data-stu-id="98d7f-112">Optional.</span></span> <span data-ttu-id="98d7f-113">ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="98d7f-113">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="98d7f-114">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="98d7f-114">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="98d7f-115">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="98d7f-115">credentialType Attribute</span></span>  
  
|<span data-ttu-id="98d7f-116">値</span><span class="sxs-lookup"><span data-stu-id="98d7f-116">Value</span></span>|<span data-ttu-id="98d7f-117">説明</span><span class="sxs-lookup"><span data-stu-id="98d7f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98d7f-118">Certificate</span><span class="sxs-lookup"><span data-stu-id="98d7f-118">Certificate</span></span>|<span data-ttu-id="98d7f-119">ピア チャネル トランスポートの認証には X 509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="98d7f-119">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="98d7f-120">Password</span><span class="sxs-lookup"><span data-stu-id="98d7f-120">Password</span></span>|<span data-ttu-id="98d7f-121">ピア チャネル トランスポートの認証には正しいパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="98d7f-121">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98d7f-122">子要素</span><span class="sxs-lookup"><span data-stu-id="98d7f-122">Child Elements</span></span>  

 <span data-ttu-id="98d7f-123">なし</span><span class="sxs-lookup"><span data-stu-id="98d7f-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98d7f-124">親要素</span><span class="sxs-lookup"><span data-stu-id="98d7f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="98d7f-125">要素</span><span class="sxs-lookup"><span data-stu-id="98d7f-125">Element</span></span>|<span data-ttu-id="98d7f-126">説明</span><span class="sxs-lookup"><span data-stu-id="98d7f-126">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="98d7f-127">ピア トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="98d7f-127">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98d7f-128">解説</span><span class="sxs-lookup"><span data-stu-id="98d7f-128">Remarks</span></span>  

 <span data-ttu-id="98d7f-129">この要素は、の mode 属性 [\<security>](security-of-peertransport.md) がまたはに設定されている場合にのみ設定され `Transport` `TransportWithMessageCredential` ます。</span><span class="sxs-lookup"><span data-stu-id="98d7f-129">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d7f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="98d7f-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="98d7f-131">トランスポートセキュリティ</span><span class="sxs-lookup"><span data-stu-id="98d7f-131">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="98d7f-132">トランスポート</span><span class="sxs-lookup"><span data-stu-id="98d7f-132">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="98d7f-133">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="98d7f-133">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="98d7f-134">バインド</span><span class="sxs-lookup"><span data-stu-id="98d7f-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="98d7f-135">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="98d7f-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="98d7f-136">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="98d7f-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
