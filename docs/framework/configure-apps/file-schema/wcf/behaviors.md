---
description: '詳細情報: <behaviors>'
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 3cb8edea76f6e7af3c3b387e5b04b89e58a28305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639511"
---
# \<behaviors>

<span data-ttu-id="a89d1-102">この要素は、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="a89d1-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="a89d1-103">各コレクションは、エンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="a89d1-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="a89d1-104">各動作要素は、その一意の `name` 属性で識別されます。</span><span class="sxs-lookup"><span data-stu-id="a89d1-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="a89d1-105">.NET Framework 4 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a89d1-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a89d1-106">既定の構成と、名前のないバインディングと動作については、「[簡略化された構成](../../../wcf/simplified-configuration.md)」と「[WCF サービスの簡略化された構成](../../../wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a89d1-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="a89d1-107">構文</span><span class="sxs-lookup"><span data-stu-id="a89d1-107">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a89d1-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a89d1-108">Attributes and Elements</span></span>  

 <span data-ttu-id="a89d1-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a89d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a89d1-110">属性</span><span class="sxs-lookup"><span data-stu-id="a89d1-110">Attributes</span></span>  

 <span data-ttu-id="a89d1-111">なし</span><span class="sxs-lookup"><span data-stu-id="a89d1-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a89d1-112">子要素</span><span class="sxs-lookup"><span data-stu-id="a89d1-112">Child Elements</span></span>  
  
|<span data-ttu-id="a89d1-113">要素</span><span class="sxs-lookup"><span data-stu-id="a89d1-113">Element</span></span>|<span data-ttu-id="a89d1-114">説明</span><span class="sxs-lookup"><span data-stu-id="a89d1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="a89d1-115">この構成セクションは、特定のエンドポイントに対して定義されたすべての動作を表します。</span><span class="sxs-lookup"><span data-stu-id="a89d1-115">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="a89d1-116">この構成セクションは、特定のサービスに対して定義されたすべての動作を表します。</span><span class="sxs-lookup"><span data-stu-id="a89d1-116">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a89d1-117">親要素</span><span class="sxs-lookup"><span data-stu-id="a89d1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a89d1-118">要素</span><span class="sxs-lookup"><span data-stu-id="a89d1-118">Element</span></span>|<span data-ttu-id="a89d1-119">説明</span><span class="sxs-lookup"><span data-stu-id="a89d1-119">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="a89d1-120">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a89d1-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a89d1-121">解説</span><span class="sxs-lookup"><span data-stu-id="a89d1-121">Remarks</span></span>  

 <span data-ttu-id="a89d1-122">`<remove>` 要素を使用して、コレクションから特定の動作を削除できます。</span><span class="sxs-lookup"><span data-stu-id="a89d1-122">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="a89d1-123">これを行うには、`name` 要素の `<remove>` 属性に、削除する動作の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a89d1-123">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="a89d1-124">また、`<clear>` 要素を使用してコレクションの内容をすべて消去し、動作コレクションの初期値を確実に空にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a89d1-124">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89d1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a89d1-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="a89d1-126">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="a89d1-126">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="a89d1-127">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="a89d1-127">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="a89d1-128">クライアントのランタイム動作の指定</span><span class="sxs-lookup"><span data-stu-id="a89d1-128">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="a89d1-129">サービスのランタイム動作の指定</span><span class="sxs-lookup"><span data-stu-id="a89d1-129">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="a89d1-130">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="a89d1-130">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
