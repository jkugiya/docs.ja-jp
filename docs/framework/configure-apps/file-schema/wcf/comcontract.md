---
description: '詳細情報: <comContract>'
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: fde1188a087f13da6629460bcebcea16ceefc0e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638666"
---
# \<comContract>

<span data-ttu-id="7f8ff-102">COM+ 統合サービス コントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-102">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="7f8ff-103">構文</span><span class="sxs-lookup"><span data-stu-id="7f8ff-103">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f8ff-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7f8ff-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7f8ff-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f8ff-106">属性</span><span class="sxs-lookup"><span data-stu-id="7f8ff-106">Attributes</span></span>  
  
|<span data-ttu-id="7f8ff-107">属性</span><span class="sxs-lookup"><span data-stu-id="7f8ff-107">Attribute</span></span>|<span data-ttu-id="7f8ff-108">説明</span><span class="sxs-lookup"><span data-stu-id="7f8ff-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f8ff-109">コントラクト (contract)</span><span class="sxs-lookup"><span data-stu-id="7f8ff-109">contract</span></span>|<span data-ttu-id="7f8ff-110">コントラクトの種類を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-110">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="7f8ff-111">name</span><span class="sxs-lookup"><span data-stu-id="7f8ff-111">name</span></span>|<span data-ttu-id="7f8ff-112">コントラクト名を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-112">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="7f8ff-113">namespace</span><span class="sxs-lookup"><span data-stu-id="7f8ff-113">namespace</span></span>|<span data-ttu-id="7f8ff-114">コントラクトの名前空間を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-114">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="7f8ff-115">requiresSession</span><span class="sxs-lookup"><span data-stu-id="7f8ff-115">requiresSession</span></span>|<span data-ttu-id="7f8ff-116">コントラクトをセッションの多いバインディングでのみ使用できるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-116">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="7f8ff-117">サービスが初期化される場合、統合ランタイムは、この設定が、使用されるバインディングの種類と一貫していることを保証します。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-117">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="7f8ff-118">コントラクト内の 1 つ以上のバインディングが競合する場合は、例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-118">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="7f8ff-119">このプロパティが `false` で、一方向のチャネルを使用し、いずれかの [out] パラメーターが存在する場合は、例外も発生します。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-119">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f8ff-120">子要素</span><span class="sxs-lookup"><span data-stu-id="7f8ff-120">Child Elements</span></span>  
  
|<span data-ttu-id="7f8ff-121">要素</span><span class="sxs-lookup"><span data-stu-id="7f8ff-121">Element</span></span>|<span data-ttu-id="7f8ff-122">説明</span><span class="sxs-lookup"><span data-stu-id="7f8ff-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f8ff-123">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="7f8ff-123">persistableTypes</span></span>|<span data-ttu-id="7f8ff-124">すべての永続型。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-124">All the persistable types.</span></span>|  
|<span data-ttu-id="7f8ff-125">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="7f8ff-125">userDefinedTypes</span></span>|<span data-ttu-id="7f8ff-126">サービス コントラクトに含まれるユーザー定義型 (UDT) のコレクション。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-126">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="7f8ff-127">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="7f8ff-127">exposedMethods</span></span>|<span data-ttu-id="7f8ff-128">COM+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM+ メソッドのコレクション。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-128">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f8ff-129">親要素</span><span class="sxs-lookup"><span data-stu-id="7f8ff-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7f8ff-130">要素</span><span class="sxs-lookup"><span data-stu-id="7f8ff-130">Element</span></span>|<span data-ttu-id="7f8ff-131">説明</span><span class="sxs-lookup"><span data-stu-id="7f8ff-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f8ff-132">comContracts</span><span class="sxs-lookup"><span data-stu-id="7f8ff-132">comContracts</span></span>|<span data-ttu-id="7f8ff-133">`comContract` 要素のコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-133">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f8ff-134">解説</span><span class="sxs-lookup"><span data-stu-id="7f8ff-134">Remarks</span></span>  

 <span data-ttu-id="7f8ff-135">COM+ 統合サービス コントラクトは、現在 `http://tempuri.org` 名前空間に制限されており、コントラクト名はサポートする COM インターフェイスから派生します。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-135">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="7f8ff-136">ただし、構成ファイルの `comContracts` セクションと `comContract` 要素を使用して代替を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-136">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="7f8ff-137">たとえば、次の構成を使用して、名前空間、コントラクト名、組み込まれるユーザー定義型、およびサービス コントラクトのその他の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-137">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="7f8ff-138">サービスが初期化される場合、指定した名前空間およびコントラクト名が、生成されるサービスの説明に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7f8ff-138">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8ff-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f8ff-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="7f8ff-140">COM+ アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="7f8ff-140">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="7f8ff-141">方法: COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="7f8ff-141">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
