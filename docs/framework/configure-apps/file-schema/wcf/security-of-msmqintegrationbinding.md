---
description: 詳細については <security> 、 <msmqIntegrationBinding>
title: <security> の <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 4ad4cb89599198661d764cfeb985609be027c0eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683204"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="ac230-103">\<security> の \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="ac230-103">\<security> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="ac230-104">メッセージ キュー (MSMQ) 統合チャネルのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac230-104">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="ac230-105">構文</span><span class="sxs-lookup"><span data-stu-id="ac230-105">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac230-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ac230-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ac230-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac230-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac230-108">属性</span><span class="sxs-lookup"><span data-stu-id="ac230-108">Attributes</span></span>  
  
|<span data-ttu-id="ac230-109">属性</span><span class="sxs-lookup"><span data-stu-id="ac230-109">Attribute</span></span>|<span data-ttu-id="ac230-110">説明</span><span class="sxs-lookup"><span data-stu-id="ac230-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac230-111">mode</span><span class="sxs-lookup"><span data-stu-id="ac230-111">mode</span></span>|<span data-ttu-id="ac230-112">メッセージ キュー統合チャネルの整合性、機密性、および認証を制御するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac230-112">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="ac230-113">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac230-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ac230-114">-None: セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ac230-114">-   None: This disables security.</span></span><br /><span data-ttu-id="ac230-115">-Transport: 保護と認証はトランスポートによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="ac230-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="ac230-116">これは、2 つのキュー マネージャー間のメッセージ セキュリティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ac230-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="ac230-117">アプリケーションとキュー マネージャーとの間にセキュリティは提供されません。</span><span class="sxs-lookup"><span data-stu-id="ac230-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="ac230-118">既存の Msmq アプリケーションは、この種類のセキュリティ モードと機能的に等価です。</span><span class="sxs-lookup"><span data-stu-id="ac230-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="ac230-119">既定値は `Transport` です。</span><span class="sxs-lookup"><span data-stu-id="ac230-119">The default value is `Transport`.</span></span> <span data-ttu-id="ac230-120">この属性は <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="ac230-120">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac230-121">子要素</span><span class="sxs-lookup"><span data-stu-id="ac230-121">Child Elements</span></span>  
  
|<span data-ttu-id="ac230-122">要素</span><span class="sxs-lookup"><span data-stu-id="ac230-122">Element</span></span>|<span data-ttu-id="ac230-123">説明</span><span class="sxs-lookup"><span data-stu-id="ac230-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="ac230-124">メッセージ キュー統合トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac230-124">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="ac230-125">この要素は <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="ac230-125">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac230-126">親要素</span><span class="sxs-lookup"><span data-stu-id="ac230-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ac230-127">要素</span><span class="sxs-lookup"><span data-stu-id="ac230-127">Element</span></span>|<span data-ttu-id="ac230-128">説明</span><span class="sxs-lookup"><span data-stu-id="ac230-128">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="ac230-129">のバインディング要素 [\<msmqIntegrationBinding>](msmqintegrationbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="ac230-129">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac230-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac230-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="ac230-131">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="ac230-131">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="ac230-132">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ac230-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ac230-133">バインド</span><span class="sxs-lookup"><span data-stu-id="ac230-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ac230-134">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="ac230-134">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ac230-135">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="ac230-135">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
