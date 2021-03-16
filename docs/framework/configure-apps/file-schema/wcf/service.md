---
description: '詳細情報: <service>'
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c3870a170847d773996625235c75591ced75e315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786786"
---
# \<service>

<span data-ttu-id="5586c-102">`service` 要素には Windows Communication Foundation (WCF) サービスの設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5586c-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="5586c-103">また、サービスを公開するエンドポイントも含まれます。</span><span class="sxs-lookup"><span data-stu-id="5586c-103">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="5586c-104">構文</span><span class="sxs-lookup"><span data-stu-id="5586c-104">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5586c-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5586c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5586c-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5586c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5586c-107">属性</span><span class="sxs-lookup"><span data-stu-id="5586c-107">Attributes</span></span>  
  
|<span data-ttu-id="5586c-108">属性</span><span class="sxs-lookup"><span data-stu-id="5586c-108">Attribute</span></span>|<span data-ttu-id="5586c-109">説明</span><span class="sxs-lookup"><span data-stu-id="5586c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5586c-110">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="5586c-110">behaviorConfiguration</span></span>|<span data-ttu-id="5586c-111">サービスのインスタンス化に使用される動作の動作名を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="5586c-111">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="5586c-112">動作名は、サービスが定義される時点でスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="5586c-112">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="5586c-113">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="5586c-113">The default value is an empty string.</span></span>|  
|<span data-ttu-id="5586c-114">name</span><span class="sxs-lookup"><span data-stu-id="5586c-114">name</span></span>|<span data-ttu-id="5586c-115">インスタンス化するサービスの型を指定する必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="5586c-115">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="5586c-116">この設定は有効な型と同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="5586c-116">This setting must equate to a valid type.</span></span> <span data-ttu-id="5586c-117">形式は、`Namespace.Class.` です。</span><span class="sxs-lookup"><span data-stu-id="5586c-117">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5586c-118">子要素</span><span class="sxs-lookup"><span data-stu-id="5586c-118">Child Elements</span></span>  
  
|<span data-ttu-id="5586c-119">要素</span><span class="sxs-lookup"><span data-stu-id="5586c-119">Element</span></span>|<span data-ttu-id="5586c-120">説明</span><span class="sxs-lookup"><span data-stu-id="5586c-120">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="5586c-121">このサービスを公開する `endpoint` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="5586c-121">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="5586c-122">このサービス インスタンスのホストを指定します。</span><span class="sxs-lookup"><span data-stu-id="5586c-122">Specifies the host of this service instance.</span></span> <span data-ttu-id="5586c-123">この要素は <xref:System.ServiceModel.Configuration.HostElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="5586c-123">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5586c-124">親要素</span><span class="sxs-lookup"><span data-stu-id="5586c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5586c-125">要素</span><span class="sxs-lookup"><span data-stu-id="5586c-125">Element</span></span>|<span data-ttu-id="5586c-126">説明</span><span class="sxs-lookup"><span data-stu-id="5586c-126">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="5586c-127">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="5586c-127">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5586c-128">解説</span><span class="sxs-lookup"><span data-stu-id="5586c-128">Remarks</span></span>  

 <span data-ttu-id="5586c-129">サービスは、設定ファイルの `services` セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="5586c-129">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="5586c-130">アセンブリには、任意の数のサービスを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5586c-130">An assembly can contain any number of services.</span></span> <span data-ttu-id="5586c-131">各サービスには、独自の `service` 設定セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="5586c-131">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="5586c-132">このセクションとその内容は、サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="5586c-132">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="5586c-133">`behaviorConfiguration` 要素も省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5586c-133">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="5586c-134">サービスが使用する動作を識別します。</span><span class="sxs-lookup"><span data-stu-id="5586c-134">It identifies the behavior the service uses.</span></span> <span data-ttu-id="5586c-135">この属性で指定された動作は、同じ設定ファイルの範囲にある動作にリンクしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5586c-135">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="5586c-136">各サービスでは、固有のアドレスとバインディングを持つ 1 つまたは複数のエンドポイントが公開されます。</span><span class="sxs-lookup"><span data-stu-id="5586c-136">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="5586c-137">構成ファイル内で使用されるすべてのバインディングは、そのファイルのスコープ内で定義される必要があります。</span><span class="sxs-lookup"><span data-stu-id="5586c-137">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="5586c-138">バインディングは、`name` 属性と `bindingConfiguration` 属性の組み合わせによってエンドポイントにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="5586c-138">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="5586c-139">`name` 属性は、バインディングが定義されているセクションを示します。</span><span class="sxs-lookup"><span data-stu-id="5586c-139">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="5586c-140">`bindingConfiguration` 属性は、バインディング セクション内の使用される構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="5586c-140">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="5586c-141">バインディング セクションでは、複数の設定を定義できます。</span><span class="sxs-lookup"><span data-stu-id="5586c-141">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5586c-142">例</span><span class="sxs-lookup"><span data-stu-id="5586c-142">Example</span></span>  

 <span data-ttu-id="5586c-143">これはサービスの構成の例です。</span><span class="sxs-lookup"><span data-stu-id="5586c-143">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="5586c-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="5586c-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="5586c-145">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="5586c-145">Configuring Services</span></span>](../../../wcf/configuring-services.md)
