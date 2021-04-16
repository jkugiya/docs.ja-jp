---
description: '詳細情報: <client>'
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 9765460602738f49963ea521b3f00ed7c63cc568
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638861"
---
# \<client>

<span data-ttu-id="67388-102">`client` 要素は、クライアントが接続可能なエンドポイントの一覧を定義します。</span><span class="sxs-lookup"><span data-stu-id="67388-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="67388-103">構文</span><span class="sxs-lookup"><span data-stu-id="67388-103">Syntax</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67388-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="67388-104">Attributes and Elements</span></span>

 <span data-ttu-id="67388-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="67388-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="67388-106">属性</span><span class="sxs-lookup"><span data-stu-id="67388-106">Attributes</span></span>

 <span data-ttu-id="67388-107">なし</span><span class="sxs-lookup"><span data-stu-id="67388-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="67388-108">子要素</span><span class="sxs-lookup"><span data-stu-id="67388-108">Child Elements</span></span>

|<span data-ttu-id="67388-109">要素</span><span class="sxs-lookup"><span data-stu-id="67388-109">Element</span></span>|<span data-ttu-id="67388-110">説明</span><span class="sxs-lookup"><span data-stu-id="67388-110">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="67388-111">このクライアントが接続可能なエンドポイントを指定するエンドポイント要素のコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="67388-111">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="67388-112">メタデータを処理するための設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="67388-112">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67388-113">親要素</span><span class="sxs-lookup"><span data-stu-id="67388-113">Parent Elements</span></span>

|<span data-ttu-id="67388-114">要素</span><span class="sxs-lookup"><span data-stu-id="67388-114">Element</span></span>|<span data-ttu-id="67388-115">説明</span><span class="sxs-lookup"><span data-stu-id="67388-115">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="67388-116">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="67388-116">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67388-117">解説</span><span class="sxs-lookup"><span data-stu-id="67388-117">Remarks</span></span>

 <span data-ttu-id="67388-118">`client` セクションは、クライアントが接続可能なエンドポイントの一覧を定義します。</span><span class="sxs-lookup"><span data-stu-id="67388-118">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="67388-119">クライアント セクションに示される各エンドポイントは、独自のバインディング、動作、およびコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="67388-119">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="67388-120">各エンドポイントは、`name` 属性と `contract` 属性の組み合わせで一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="67388-120">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="67388-121">クライアント コードは、クライアントが実装するサービスのエンドポイントに接続するための `name` を指定します。</span><span class="sxs-lookup"><span data-stu-id="67388-121">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="67388-122">`name` 属性が省略されている場合、クライアントが実装するコントラクトのエンドポイントが既定のエンドポイントとして機能します。</span><span class="sxs-lookup"><span data-stu-id="67388-122">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="67388-123">さらに、このセクションはメタデータを処理するための設定も指定します。</span><span class="sxs-lookup"><span data-stu-id="67388-123">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="67388-124">例</span><span class="sxs-lookup"><span data-stu-id="67388-124">Example</span></span>

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a><span data-ttu-id="67388-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="67388-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="67388-126">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="67388-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="67388-127">クライアント</span><span class="sxs-lookup"><span data-stu-id="67388-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
