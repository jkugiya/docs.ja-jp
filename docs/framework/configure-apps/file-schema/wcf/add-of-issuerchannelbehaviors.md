---
description: 詳細については <add> 、 <issuerChannelBehaviors>
title: <add> の <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: ccd8ba015b7a6837c74ce2c051a794d36ce8ceaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750300"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="d3b43-103">\<add> の \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="d3b43-103">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="d3b43-104">STS と通信するときに使用されるエンドポイントの動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3b43-104">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="d3b43-105">いずれかのエンドポイント動作に要素が含まれている場合は [\<clientCredentials>](clientcredentials.md) 、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d3b43-105">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="d3b43-106">構文</span><span class="sxs-lookup"><span data-stu-id="d3b43-106">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3b43-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d3b43-107">Attributes and Elements</span></span>

<span data-ttu-id="d3b43-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3b43-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="d3b43-109">属性</span><span class="sxs-lookup"><span data-stu-id="d3b43-109">Attributes</span></span>

|<span data-ttu-id="d3b43-110">属性</span><span class="sxs-lookup"><span data-stu-id="d3b43-110">Attribute</span></span>|<span data-ttu-id="d3b43-111">説明</span><span class="sxs-lookup"><span data-stu-id="d3b43-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d3b43-112">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="d3b43-112">issuerAddress</span></span>|<span data-ttu-id="d3b43-113">通信するためのセキュリティ トークン発行者の URI。</span><span class="sxs-lookup"><span data-stu-id="d3b43-113">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="d3b43-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="d3b43-114">behaviorConfiguration</span></span>|<span data-ttu-id="d3b43-115">同じ構成ファイルに定義されたエンドポイントの動作の名前。</span><span class="sxs-lookup"><span data-stu-id="d3b43-115">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d3b43-116">子要素</span><span class="sxs-lookup"><span data-stu-id="d3b43-116">Child Elements</span></span>

<span data-ttu-id="d3b43-117">なし。</span><span class="sxs-lookup"><span data-stu-id="d3b43-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d3b43-118">親要素</span><span class="sxs-lookup"><span data-stu-id="d3b43-118">Parent Elements</span></span>

|<span data-ttu-id="d3b43-119">要素</span><span class="sxs-lookup"><span data-stu-id="d3b43-119">Element</span></span>|<span data-ttu-id="d3b43-120">説明</span><span class="sxs-lookup"><span data-stu-id="d3b43-120">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="d3b43-121">指定されたサービストークンサービスと通信するときに使用される Windows Communication Foundation (WCF) クライアントエンドポイントの動作のコレクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="d3b43-121">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3b43-122">解説</span><span class="sxs-lookup"><span data-stu-id="d3b43-122">Remarks</span></span>

<span data-ttu-id="d3b43-123">`issuerAddress` には、クライアントの通信相手となるセキュリティ トークン サービスの URI が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3b43-123">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="d3b43-124">`behaviorConfiguration` セキュリティトークンサービスから発行済みトークンを取得するために Windows Communication Foundation (WCF) によって作成されたチャネルでアプリケーションが使用するエンドポイント動作を指します。</span><span class="sxs-lookup"><span data-stu-id="d3b43-124">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3b43-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3b43-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="d3b43-126">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="d3b43-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d3b43-127">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="d3b43-127">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d3b43-128">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="d3b43-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d3b43-129">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d3b43-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d3b43-130">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d3b43-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d3b43-131">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="d3b43-131">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d3b43-132">方法: ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="d3b43-132">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d3b43-133">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="d3b43-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
