---
description: '詳細情報: <issuerChannelBehaviors> 要素'
title: <issuerChannelBehaviors> 要素
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: 6be79f2ee6afb442a7a399ce49df4ad59dff2db5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725546"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="47fef-103">\::: なし ( <issuerChannelBehaviors> )::: 要素</span><span class="sxs-lookup"><span data-stu-id="47fef-103">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="47fef-104">指定されたサービストークンサービスとの通信時に使用される Windows Communication Foundation (WCF) クライアントエンドポイントの動作 (構成で定義されている) のコレクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="47fef-104">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="47fef-105">定義された動作には、: [ \: : no loc ( <clientCredentials> ):::](clientcredentials.md)要素を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="47fef-105">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
<span data-ttu-id="47fef-106">&nbsp;&nbsp;[\::: no loc (<System.servicemodel>):::](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="47fef-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="47fef-107">&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <behaviors> ):::](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="47fef-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="47fef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <endpointBehaviors> ):::](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="47fef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="47fef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <behavior> ):::](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="47fef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="47fef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <clientCredentials> ):::](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="47fef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="47fef-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: no loc ( <issuedToken> ):::](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="47fef-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="47fef-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\::: no loc ( <issuerChannelBehaviors> ):::</span><span class="sxs-lookup"><span data-stu-id="47fef-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="47fef-113">構文</span><span class="sxs-lookup"><span data-stu-id="47fef-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47fef-114">属性と要素</span><span class="sxs-lookup"><span data-stu-id="47fef-114">Attributes and elements</span></span>

<span data-ttu-id="47fef-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="47fef-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="47fef-116">属性</span><span class="sxs-lookup"><span data-stu-id="47fef-116">Attributes</span></span>

<span data-ttu-id="47fef-117">なし。</span><span class="sxs-lookup"><span data-stu-id="47fef-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47fef-118">子要素</span><span class="sxs-lookup"><span data-stu-id="47fef-118">Child elements</span></span>

|<span data-ttu-id="47fef-119">要素</span><span class="sxs-lookup"><span data-stu-id="47fef-119">Element</span></span>|<span data-ttu-id="47fef-120">説明</span><span class="sxs-lookup"><span data-stu-id="47fef-120">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="47fef-121">コレクションに動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="47fef-121">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47fef-122">親要素</span><span class="sxs-lookup"><span data-stu-id="47fef-122">Parent elements</span></span>

|<span data-ttu-id="47fef-123">要素</span><span class="sxs-lookup"><span data-stu-id="47fef-123">Element</span></span>|<span data-ttu-id="47fef-124">説明</span><span class="sxs-lookup"><span data-stu-id="47fef-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47fef-125">\::: no loc ( <issuedToken> ):::</span><span class="sxs-lookup"><span data-stu-id="47fef-125">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="47fef-126">サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="47fef-126">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47fef-127">解説</span><span class="sxs-lookup"><span data-stu-id="47fef-127">Remarks</span></span>

<span data-ttu-id="47fef-128">この要素を使用するのは、なんらかの動作 (`<clientCredentials>` 要素を含む動作以外) を使用してサービスと通信する必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="47fef-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="47fef-129">たとえば、 [ \: :: no loc ( <dataContractSerializer> ):](datacontractserializer-element.md) :: behavior 要素を含める必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="47fef-129">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="47fef-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="47fef-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="47fef-131">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="47fef-131">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="47fef-132">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="47fef-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="47fef-133">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="47fef-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="47fef-134">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="47fef-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="47fef-135">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="47fef-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="47fef-136">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="47fef-136">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="47fef-137">方法: ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="47fef-137">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="47fef-138">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="47fef-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
