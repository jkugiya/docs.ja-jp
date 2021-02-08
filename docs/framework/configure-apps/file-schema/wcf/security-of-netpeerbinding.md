---
description: 詳細については <security> 、 <netPeerBinding>
title: <security> の <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: f67cfa445a5a605b99783cfd67dd1bae6e17b51e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786838"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="61ef2-103">\<security> の \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="61ef2-103">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="61ef2-104">[\<netPeerTcpBinding>](netpeertcpbinding.md)使用される認証の種類とメッセージトランスポートに使用されるセキュリティを含む、のセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="61ef2-104">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="61ef2-105">構文</span><span class="sxs-lookup"><span data-stu-id="61ef2-105">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61ef2-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="61ef2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="61ef2-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="61ef2-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61ef2-108">属性</span><span class="sxs-lookup"><span data-stu-id="61ef2-108">Attributes</span></span>  
  
|<span data-ttu-id="61ef2-109">属性</span><span class="sxs-lookup"><span data-stu-id="61ef2-109">Attribute</span></span>|<span data-ttu-id="61ef2-110">説明</span><span class="sxs-lookup"><span data-stu-id="61ef2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61ef2-111">mode</span><span class="sxs-lookup"><span data-stu-id="61ef2-111">mode</span></span>|<span data-ttu-id="61ef2-112">任意。</span><span class="sxs-lookup"><span data-stu-id="61ef2-112">Optional.</span></span> <span data-ttu-id="61ef2-113">このバインディングで構成されたピアが使用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="61ef2-113">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="61ef2-114">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="61ef2-114">The default value is `Message`.</span></span> <span data-ttu-id="61ef2-115">この属性は <xref:System.ServiceModel.SecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="61ef2-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="61ef2-116">mode 属性</span><span class="sxs-lookup"><span data-stu-id="61ef2-116">mode Attribute</span></span>  
  
|<span data-ttu-id="61ef2-117">値</span><span class="sxs-lookup"><span data-stu-id="61ef2-117">Value</span></span>|<span data-ttu-id="61ef2-118">説明</span><span class="sxs-lookup"><span data-stu-id="61ef2-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61ef2-119">Message</span><span class="sxs-lookup"><span data-stu-id="61ef2-119">Message</span></span>|<span data-ttu-id="61ef2-120">SOAP セキュリティにより、認証、整合性、および機密性が実現します。</span><span class="sxs-lookup"><span data-stu-id="61ef2-120">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="61ef2-121">なし</span><span class="sxs-lookup"><span data-stu-id="61ef2-121">None</span></span>|<span data-ttu-id="61ef2-122">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="61ef2-122">Security is disabled.</span></span>|  
|<span data-ttu-id="61ef2-123">トランスポート</span><span class="sxs-lookup"><span data-stu-id="61ef2-123">Transport</span></span>|<span data-ttu-id="61ef2-124">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="61ef2-124">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="61ef2-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="61ef2-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="61ef2-126">HTTPS により、認証および機密性が実現します。</span><span class="sxs-lookup"><span data-stu-id="61ef2-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="61ef2-127">SOAP メッセージには、豊富な資格情報の種類が用意されています。</span><span class="sxs-lookup"><span data-stu-id="61ef2-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61ef2-128">子要素</span><span class="sxs-lookup"><span data-stu-id="61ef2-128">Child Elements</span></span>  
  
|<span data-ttu-id="61ef2-129">要素</span><span class="sxs-lookup"><span data-stu-id="61ef2-129">Element</span></span>|<span data-ttu-id="61ef2-130">説明</span><span class="sxs-lookup"><span data-stu-id="61ef2-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="61ef2-131">このバインディングで構成されたピアが送信するセキュリティで保護されたメッセージのトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="61ef2-131">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="61ef2-132">この要素は <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="61ef2-132">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61ef2-133">親要素</span><span class="sxs-lookup"><span data-stu-id="61ef2-133">Parent Elements</span></span>  
  
|<span data-ttu-id="61ef2-134">要素</span><span class="sxs-lookup"><span data-stu-id="61ef2-134">Element</span></span>|<span data-ttu-id="61ef2-135">説明</span><span class="sxs-lookup"><span data-stu-id="61ef2-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="61ef2-136">のすべてのバインディング機能を定義 [\<netPeerTcpBinding>](netpeertcpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="61ef2-136">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61ef2-137">解説</span><span class="sxs-lookup"><span data-stu-id="61ef2-137">Remarks</span></span>  

 <span data-ttu-id="61ef2-138">セキュリティは、メッセージ固有にすることも、トランスポート固有にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="61ef2-138">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ef2-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="61ef2-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="61ef2-140">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="61ef2-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="61ef2-141">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="61ef2-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="61ef2-142">バインド</span><span class="sxs-lookup"><span data-stu-id="61ef2-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="61ef2-143">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="61ef2-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="61ef2-144">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="61ef2-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
