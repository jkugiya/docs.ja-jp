---
description: 詳細については <security> 、 <peerTransport>
title: <security> の <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 592f886377a2d5f2008be900a9e7586385fb3782
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786825"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="843be-103">\<security> の \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="843be-103">\<security> of \<peerTransport></span></span>

<span data-ttu-id="843be-104">ピア チャネルに関連付けられたセキュリティ設定を格納します。使用される認証の種類とメッセージ トランスポートで使用されるセキュリティを含みます。</span><span class="sxs-lookup"><span data-stu-id="843be-104">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="843be-105">構文</span><span class="sxs-lookup"><span data-stu-id="843be-105">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="843be-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="843be-106">Attributes and Elements</span></span>  

 <span data-ttu-id="843be-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="843be-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="843be-108">属性</span><span class="sxs-lookup"><span data-stu-id="843be-108">Attributes</span></span>  
  
|<span data-ttu-id="843be-109">属性</span><span class="sxs-lookup"><span data-stu-id="843be-109">Attribute</span></span>|<span data-ttu-id="843be-110">説明</span><span class="sxs-lookup"><span data-stu-id="843be-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="843be-111">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="843be-111">Specifies the type of security to be applied.</span></span> <span data-ttu-id="843be-112">既定値は Message です。</span><span class="sxs-lookup"><span data-stu-id="843be-112">The default value is Message.</span></span> <span data-ttu-id="843be-113">この属性は <xref:System.ServiceModel.SecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="843be-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="843be-114">mode 属性</span><span class="sxs-lookup"><span data-stu-id="843be-114">mode Attribute</span></span>  
  
|<span data-ttu-id="843be-115">値</span><span class="sxs-lookup"><span data-stu-id="843be-115">Value</span></span>|<span data-ttu-id="843be-116">説明</span><span class="sxs-lookup"><span data-stu-id="843be-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="843be-117">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="843be-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="843be-118">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="843be-118">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="843be-119">SOAP セキュリティにより、認証、整合性、および機密性が実現します。</span><span class="sxs-lookup"><span data-stu-id="843be-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="843be-120">HTTPS により、認証および機密性が実現します。</span><span class="sxs-lookup"><span data-stu-id="843be-120">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="843be-121">SOAP メッセージには、豊富な資格情報の種類が用意されています。</span><span class="sxs-lookup"><span data-stu-id="843be-121">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="843be-122">子要素</span><span class="sxs-lookup"><span data-stu-id="843be-122">Child Elements</span></span>  
  
|<span data-ttu-id="843be-123">要素</span><span class="sxs-lookup"><span data-stu-id="843be-123">Element</span></span>|<span data-ttu-id="843be-124">説明</span><span class="sxs-lookup"><span data-stu-id="843be-124">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="843be-125">カスタム バインドのピア トランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="843be-125">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="843be-126">この要素には、サービスと対話するときに使用される資格情報を指定する `clientCredentialType` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="843be-126">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="843be-127">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="843be-127">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="843be-128">この要素は <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="843be-128">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="843be-129">親要素</span><span class="sxs-lookup"><span data-stu-id="843be-129">Parent Elements</span></span>  
  
|<span data-ttu-id="843be-130">要素</span><span class="sxs-lookup"><span data-stu-id="843be-130">Element</span></span>|<span data-ttu-id="843be-131">説明</span><span class="sxs-lookup"><span data-stu-id="843be-131">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="843be-132">カスタム バインドのピア トランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="843be-132">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="843be-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="843be-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="843be-134">トランスポートセキュリティ</span><span class="sxs-lookup"><span data-stu-id="843be-134">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="843be-135">トランスポート</span><span class="sxs-lookup"><span data-stu-id="843be-135">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="843be-136">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="843be-136">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="843be-137">バインド</span><span class="sxs-lookup"><span data-stu-id="843be-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="843be-138">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="843be-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="843be-139">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="843be-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
