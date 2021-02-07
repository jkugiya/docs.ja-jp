---
description: 詳細については <security> 、 <netNamedPipeBinding>
title: <security> の <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: d64917c53390cade00d9e104c8581ce45355ac34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683100"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="65b3b-103">\<security> の \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="65b3b-103">\<security> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="65b3b-104">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="65b3b-104">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="65b3b-105">構文</span><span class="sxs-lookup"><span data-stu-id="65b3b-105">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65b3b-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="65b3b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="65b3b-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="65b3b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65b3b-108">属性</span><span class="sxs-lookup"><span data-stu-id="65b3b-108">Attributes</span></span>  
  
|<span data-ttu-id="65b3b-109">属性</span><span class="sxs-lookup"><span data-stu-id="65b3b-109">Attribute</span></span>|<span data-ttu-id="65b3b-110">説明</span><span class="sxs-lookup"><span data-stu-id="65b3b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65b3b-111">mode</span><span class="sxs-lookup"><span data-stu-id="65b3b-111">mode</span></span>|<span data-ttu-id="65b3b-112">このバインディングに適用されるセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="65b3b-112">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="65b3b-113">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65b3b-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="65b3b-114">-None: セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="65b3b-114">-   None: This disables security.</span></span><br /><span data-ttu-id="65b3b-115">-Transport: セキュリティは、基になるトランスポートベースのセキュリティを使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="65b3b-115">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="65b3b-116">このモードでは保護レベルを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="65b3b-116">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="65b3b-117">-既定値は Transport です。</span><span class="sxs-lookup"><span data-stu-id="65b3b-117">-   The default value is Transport.</span></span> <span data-ttu-id="65b3b-118">この属性は <xref:System.ServiceModel.NetNamedPipeSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="65b3b-118">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65b3b-119">子要素</span><span class="sxs-lookup"><span data-stu-id="65b3b-119">Child Elements</span></span>  
  
|<span data-ttu-id="65b3b-120">要素</span><span class="sxs-lookup"><span data-stu-id="65b3b-120">Element</span></span>|<span data-ttu-id="65b3b-121">説明</span><span class="sxs-lookup"><span data-stu-id="65b3b-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65b3b-122">transport</span><span class="sxs-lookup"><span data-stu-id="65b3b-122">transport</span></span>|<span data-ttu-id="65b3b-123">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="65b3b-123">Defines the security settings for the transport.</span></span> <span data-ttu-id="65b3b-124">この要素は <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="65b3b-124">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65b3b-125">親要素</span><span class="sxs-lookup"><span data-stu-id="65b3b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="65b3b-126">要素</span><span class="sxs-lookup"><span data-stu-id="65b3b-126">Element</span></span>|<span data-ttu-id="65b3b-127">説明</span><span class="sxs-lookup"><span data-stu-id="65b3b-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65b3b-128">binding</span><span class="sxs-lookup"><span data-stu-id="65b3b-128">binding</span></span>|<span data-ttu-id="65b3b-129">のバインディング要素 [\<netNamedPipeBinding>](netnamedpipebinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="65b3b-129">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65b3b-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="65b3b-130">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="65b3b-131">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="65b3b-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="65b3b-132">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="65b3b-132">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="65b3b-133">バインド</span><span class="sxs-lookup"><span data-stu-id="65b3b-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="65b3b-134">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="65b3b-134">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="65b3b-135">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="65b3b-135">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
