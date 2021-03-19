---
description: 詳細については <security> 、 <wsDualHttpBinding>
title: <security> の <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 6d2e87912aef6114d7dcb99b82e4a7804317b28a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683035"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="e9a15-103">\<security> の \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e9a15-103">\<security> of \<wsDualHttpBinding></span></span>

<span data-ttu-id="e9a15-104">のセキュリティ機能を定義 [\<wsDualHttpBinding>](wsdualhttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="e9a15-104">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="e9a15-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9a15-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9a15-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e9a15-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e9a15-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9a15-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9a15-108">属性</span><span class="sxs-lookup"><span data-stu-id="e9a15-108">Attributes</span></span>  
  
|<span data-ttu-id="e9a15-109">属性</span><span class="sxs-lookup"><span data-stu-id="e9a15-109">Attribute</span></span>|<span data-ttu-id="e9a15-110">説明</span><span class="sxs-lookup"><span data-stu-id="e9a15-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9a15-111">mode</span><span class="sxs-lookup"><span data-stu-id="e9a15-111">mode</span></span>|<span data-ttu-id="e9a15-112">Optional.</span><span class="sxs-lookup"><span data-stu-id="e9a15-112">-   Optional.</span></span> <span data-ttu-id="e9a15-113">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9a15-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e9a15-114">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="e9a15-114">The default value is `Message`.</span></span> <span data-ttu-id="e9a15-115">この属性は <xref:System.ServiceModel.WSDualHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="e9a15-115">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e9a15-116">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="e9a15-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="e9a15-117">値</span><span class="sxs-lookup"><span data-stu-id="e9a15-117">Value</span></span>|<span data-ttu-id="e9a15-118">説明</span><span class="sxs-lookup"><span data-stu-id="e9a15-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9a15-119">なし</span><span class="sxs-lookup"><span data-stu-id="e9a15-119">None</span></span>|<span data-ttu-id="e9a15-120">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="e9a15-120">Security is disabled.</span></span>|  
|<span data-ttu-id="e9a15-121">Message</span><span class="sxs-lookup"><span data-stu-id="e9a15-121">Message</span></span>|<span data-ttu-id="e9a15-122">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="e9a15-122">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9a15-123">子要素</span><span class="sxs-lookup"><span data-stu-id="e9a15-123">Child Elements</span></span>  
  
|<span data-ttu-id="e9a15-124">要素</span><span class="sxs-lookup"><span data-stu-id="e9a15-124">Element</span></span>|<span data-ttu-id="e9a15-125">説明</span><span class="sxs-lookup"><span data-stu-id="e9a15-125">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="e9a15-126">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="e9a15-126">Defines the settings for the message-level security.</span></span> <span data-ttu-id="e9a15-127">この要素は <xref:System.ServiceModel.MessageSecurityOverHttp> 型です。</span><span class="sxs-lookup"><span data-stu-id="e9a15-127">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9a15-128">親要素</span><span class="sxs-lookup"><span data-stu-id="e9a15-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e9a15-129">要素</span><span class="sxs-lookup"><span data-stu-id="e9a15-129">Element</span></span>|<span data-ttu-id="e9a15-130">説明</span><span class="sxs-lookup"><span data-stu-id="e9a15-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e9a15-131">のすべてのバインディング機能を定義 [\<wsDualHttpBinding>](wsdualhttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="e9a15-131">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9a15-132">解説</span><span class="sxs-lookup"><span data-stu-id="e9a15-132">Remarks</span></span>  

 <span data-ttu-id="e9a15-133">二重バインディングでは、クライアントの IP アドレスをサービスに公開します。</span><span class="sxs-lookup"><span data-stu-id="e9a15-133">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="e9a15-134">クライアントは、セキュリティを使用して信頼するサービスに対して接続のみを可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9a15-134">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a15-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9a15-135">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="e9a15-136">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="e9a15-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e9a15-137">バインド</span><span class="sxs-lookup"><span data-stu-id="e9a15-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9a15-138">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="e9a15-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e9a15-139">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="e9a15-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
