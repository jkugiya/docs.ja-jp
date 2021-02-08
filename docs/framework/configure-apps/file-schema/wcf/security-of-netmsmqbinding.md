---
description: 詳細については <security> 、 <netMsmqBinding>
title: <security> の <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1b60d9e390e371555f4c3abf4988e79bb0f04fe8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786851"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="efce2-103">\<security> の \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="efce2-103">\<security> of \<netMsmqBinding></span></span>

<span data-ttu-id="efce2-104">MSMQ バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="efce2-104">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="efce2-105">トランスポートまたは SOAP セキュリティが有効であるかどうか、および有効である場合は、どの認証モードと保護レベルを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="efce2-105">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="efce2-106">構文</span><span class="sxs-lookup"><span data-stu-id="efce2-106">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efce2-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="efce2-107">Attributes and Elements</span></span>  

 <span data-ttu-id="efce2-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="efce2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efce2-109">属性</span><span class="sxs-lookup"><span data-stu-id="efce2-109">Attributes</span></span>  
  
|<span data-ttu-id="efce2-110">属性</span><span class="sxs-lookup"><span data-stu-id="efce2-110">Attribute</span></span>|<span data-ttu-id="efce2-111">説明</span><span class="sxs-lookup"><span data-stu-id="efce2-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efce2-112">mode</span><span class="sxs-lookup"><span data-stu-id="efce2-112">mode</span></span>|<span data-ttu-id="efce2-113">整合性、機密性、および認証を制御するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="efce2-113">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="efce2-114">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="efce2-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="efce2-115">-None: セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="efce2-115">-   None: This disables security.</span></span><br /><span data-ttu-id="efce2-116">-Transport: 保護と認証はトランスポートによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="efce2-116">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="efce2-117">これは、2 つのキュー マネージャー間のメッセージ セキュリティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="efce2-117">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="efce2-118">アプリケーションとキュー マネージャーとの間にセキュリティは提供されません。</span><span class="sxs-lookup"><span data-stu-id="efce2-118">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="efce2-119">既存の Msmq アプリケーションは、この種類のセキュリティ モードと機能的に等価です。</span><span class="sxs-lookup"><span data-stu-id="efce2-119">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="efce2-120">-Message: エンドツーエンドアプリケーションのセキュリティを指定します。</span><span class="sxs-lookup"><span data-stu-id="efce2-120">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="efce2-121">トランスポート層で提供されるセキュリティありません。</span><span class="sxs-lookup"><span data-stu-id="efce2-121">There is no security offered at the transport layer.</span></span> <span data-ttu-id="efce2-122">これは、他の標準バインディングによって提供されたセキュリティと同様です。</span><span class="sxs-lookup"><span data-stu-id="efce2-122">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="efce2-123">-Both: トランスポートと SOAP メッセージング層の両方でセキュリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="efce2-123">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="efce2-124">同じ資格情報が、両方のレベルで要求されます。</span><span class="sxs-lookup"><span data-stu-id="efce2-124">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="efce2-125">既定値は、Transport です。</span><span class="sxs-lookup"><span data-stu-id="efce2-125">The default value is Transport.</span></span> <span data-ttu-id="efce2-126">この属性は <xref:System.ServiceModel.NetMsmqSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="efce2-126">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efce2-127">子要素</span><span class="sxs-lookup"><span data-stu-id="efce2-127">Child Elements</span></span>  
  
|<span data-ttu-id="efce2-128">要素</span><span class="sxs-lookup"><span data-stu-id="efce2-128">Element</span></span>|<span data-ttu-id="efce2-129">説明</span><span class="sxs-lookup"><span data-stu-id="efce2-129">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="efce2-130">SOAP メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="efce2-130">Defines the SOAP message security settings.</span></span> <span data-ttu-id="efce2-131">この要素は <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="efce2-131">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="efce2-132">MSMQ トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="efce2-132">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="efce2-133">この要素は <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="efce2-133">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efce2-134">親要素</span><span class="sxs-lookup"><span data-stu-id="efce2-134">Parent Elements</span></span>  
  
|<span data-ttu-id="efce2-135">要素</span><span class="sxs-lookup"><span data-stu-id="efce2-135">Element</span></span>|<span data-ttu-id="efce2-136">説明</span><span class="sxs-lookup"><span data-stu-id="efce2-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="efce2-137">binding</span><span class="sxs-lookup"><span data-stu-id="efce2-137">binding</span></span>|<span data-ttu-id="efce2-138">のバインド要素 [\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="efce2-138">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efce2-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="efce2-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="efce2-140">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="efce2-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="efce2-141">バインド</span><span class="sxs-lookup"><span data-stu-id="efce2-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="efce2-142">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="efce2-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="efce2-143">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="efce2-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="efce2-144">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="efce2-144">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
