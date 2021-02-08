---
description: '詳細情報: <endpointDiscovery>'
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 01913de37ae426484d5bb1ff6a815a64302024fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782131"
---
# \<endpointDiscovery>

<span data-ttu-id="bbcb4-102">エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="bbcb4-103">構文</span><span class="sxs-lookup"><span data-stu-id="bbcb4-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbcb4-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bbcb4-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bbcb4-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbcb4-106">属性</span><span class="sxs-lookup"><span data-stu-id="bbcb4-106">Attributes</span></span>  
  
|<span data-ttu-id="bbcb4-107">属性</span><span class="sxs-lookup"><span data-stu-id="bbcb4-107">Attribute</span></span>|<span data-ttu-id="bbcb4-108">説明</span><span class="sxs-lookup"><span data-stu-id="bbcb4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbcb4-109">enabled</span><span class="sxs-lookup"><span data-stu-id="bbcb4-109">enabled</span></span>|<span data-ttu-id="bbcb4-110">このエンドポイントで探索可能性が有効かどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-110">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="bbcb4-111">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-111">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbcb4-112">子要素</span><span class="sxs-lookup"><span data-stu-id="bbcb4-112">Child Elements</span></span>  
  
|<span data-ttu-id="bbcb4-113">要素</span><span class="sxs-lookup"><span data-stu-id="bbcb4-113">Element</span></span>|<span data-ttu-id="bbcb4-114">説明</span><span class="sxs-lookup"><span data-stu-id="bbcb4-114">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="bbcb4-115">エンドポイントのスコープ URI のコレクション。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-115">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="bbcb4-116">複数の URI を 1 つのエンドポイントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-116">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="bbcb4-117">[\<extensions>](extensions.md) [/ \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="bbcb4-117">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="bbcb4-118">エンドポイントで発行されるカスタム メタデータを指定できる、XML 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-118">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="bbcb4-119">検索するインターフェイスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-119">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbcb4-120">親要素</span><span class="sxs-lookup"><span data-stu-id="bbcb4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bbcb4-121">要素</span><span class="sxs-lookup"><span data-stu-id="bbcb4-121">Element</span></span>|<span data-ttu-id="bbcb4-122">説明</span><span class="sxs-lookup"><span data-stu-id="bbcb4-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bbcb4-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-123">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="bbcb4-124">解説</span><span class="sxs-lookup"><span data-stu-id="bbcb4-124">Remarks</span></span>  

 <span data-ttu-id="bbcb4-125">エンドポイントの動作構成に追加し、`enabled` 属性を `true` に設定すると、この構成要素の探索可能性が有効になります。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-125">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="bbcb4-126">また、子要素を使用して、 [\<scopes>](scopes.md) クエリ中にサービスエンドポイントをフィルター処理するために使用できるカスタムスコープ uri を指定したり、 [\<extensions>](extensions.md) 標準の探索可能なメタデータ (EPR、Contracttypename、Bindingname、Scope、ListenURI) と共に発行する必要があるカスタムメタデータを指定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-126">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="bbcb4-127">この構成要素は、探索可能性 [\<serviceDiscovery>](servicediscovery.md) のサービスレベルコントロールを提供する要素に依存します。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-127">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="bbcb4-128">これは [\<serviceDiscovery>](servicediscovery.md) 、が構成内に存在しない場合に、この要素の設定が無視されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-128">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbcb4-129">例</span><span class="sxs-lookup"><span data-stu-id="bbcb4-129">Example</span></span>  

 <span data-ttu-id="bbcb4-130">次の構成例では、フィルターのスコープと、エンドポイントで発行される拡張メタデータを指定しています。</span><span class="sxs-lookup"><span data-stu-id="bbcb4-130">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="bbcb4-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbcb4-131">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
