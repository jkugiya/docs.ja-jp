---
description: '詳細情報: <endpoint> 要素'
title: <endpoint> 要素
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: d5555ae895e6655d1ce6e3dcb026ddec3ff8cf44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725806"
---
# <a name="endpoint-element"></a><span data-ttu-id="10257-103">\<endpoint> 要素</span><span class="sxs-lookup"><span data-stu-id="10257-103">\<endpoint> element</span></span>

<span data-ttu-id="10257-104">サービスの公開に使用されるサービス エンドポイントのバインディング、コントラクト、およびアドレスのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="10257-104">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="10257-105">構文</span><span class="sxs-lookup"><span data-stu-id="10257-105">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10257-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="10257-106">Attributes and Elements</span></span>  

 <span data-ttu-id="10257-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="10257-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10257-108">属性</span><span class="sxs-lookup"><span data-stu-id="10257-108">Attributes</span></span>  
  
|<span data-ttu-id="10257-109">属性</span><span class="sxs-lookup"><span data-stu-id="10257-109">Attribute</span></span>|<span data-ttu-id="10257-110">説明</span><span class="sxs-lookup"><span data-stu-id="10257-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10257-111">address</span><span class="sxs-lookup"><span data-stu-id="10257-111">address</span></span>|<span data-ttu-id="10257-112">エンドポイントのアドレスを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-112">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="10257-113">アドレスは、絶対または相対アドレスとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="10257-113">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="10257-114">相対アドレスが提供されている場合、ホストは、そのバインディングで使用されるトランスポート スキームに適したベース アドレスが提供されることを想定します。</span><span class="sxs-lookup"><span data-stu-id="10257-114">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="10257-115">アドレスが構成されていない場合、ベース アドレスはそのエンドポイントのアドレスと見なされます。</span><span class="sxs-lookup"><span data-stu-id="10257-115">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="10257-116">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="10257-116">The default is an empty string.</span></span>|  
|<span data-ttu-id="10257-117">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="10257-117">behaviorConfiguration</span></span>|<span data-ttu-id="10257-118">エンドポイントで使用される動作の名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-118">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="10257-119">binding</span><span class="sxs-lookup"><span data-stu-id="10257-119">binding</span></span>|<span data-ttu-id="10257-120">使用するバインディングの種類を指定する必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="10257-120">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="10257-121">参照できるようにするには、種類は登録された構成セクションを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="10257-121">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="10257-122">種類は、バインディングの種類の名前ではなくセクション名で登録されます。</span><span class="sxs-lookup"><span data-stu-id="10257-122">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="10257-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="10257-123">bindingConfiguration</span></span>|<span data-ttu-id="10257-124">エンドポイントがインスタンス化されるときに使用するバインディングのバインディング名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-124">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="10257-125">バインディング名は、エンドポイントが定義される時点でスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="10257-125">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="10257-126">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="10257-126">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="10257-127">この属性は、構成ファイル内の特定のバインディング構成を参照するために、`binding` と組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="10257-127">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="10257-128">カスタム バインドを使用しようとする場合にこの属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="10257-128">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="10257-129">そうでない場合は、例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="10257-129">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="10257-130">bindingName</span><span class="sxs-lookup"><span data-stu-id="10257-130">bindingName</span></span>|<span data-ttu-id="10257-131">WSDL を介した定義エクスポートに使用するバインディングの一意の修飾名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-131">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="10257-132">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="10257-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="10257-133">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="10257-133">bindingNamespace</span></span>|<span data-ttu-id="10257-134">WSDL を介した定義エクスポートに使用するバインディングの名前空間の修飾名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-134">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="10257-135">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="10257-135">The default is an empty string.</span></span>|  
|<span data-ttu-id="10257-136">コントラクト (contract)</span><span class="sxs-lookup"><span data-stu-id="10257-136">contract</span></span>|<span data-ttu-id="10257-137">このエンドポイントが公開するコントラクトを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="10257-138">アセンブリは、コントラクト型を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10257-138">The assembly must implement the contract type.</span></span> <span data-ttu-id="10257-139">サービス実装が単一のコントラクトの型を実装する場合は、このプロパティを省略できます。</span><span class="sxs-lookup"><span data-stu-id="10257-139">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="10257-140">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="10257-140">The default is an empty string.</span></span>|  
|<span data-ttu-id="10257-141">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="10257-141">endpointConfiguration</span></span>|<span data-ttu-id="10257-142">この標準エンドポイントの追加の構成情報を参照する `kind` 属性によって設定される標準エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-142">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="10257-143">同じ名前を `<standardEndpoints>` セクションに定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10257-143">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="10257-144">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="10257-144">isSystemEndpoint</span></span>|<span data-ttu-id="10257-145">インフラストラクチャ エンドポイントであるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="10257-145">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="10257-146">kind</span><span class="sxs-lookup"><span data-stu-id="10257-146">kind</span></span>|<span data-ttu-id="10257-147">適用する標準エンドポイントの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-147">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="10257-148">`<extensions>` セクションまたは machine.config に種類を登録する必要があります。何も指定していない場合は、共通のサービス エンドポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="10257-148">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="10257-149">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="10257-149">listenUriMode</span></span>|<span data-ttu-id="10257-150">リッスンするサービスに提供される `ListenUri` をトランスポートが処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="10257-150">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="10257-151">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="10257-151">Valid values are</span></span><br /><br /> <span data-ttu-id="10257-152">-Explicit</span><span class="sxs-lookup"><span data-stu-id="10257-152">-   Explicit</span></span><br /><span data-ttu-id="10257-153">-一意</span><span class="sxs-lookup"><span data-stu-id="10257-153">-   Unique</span></span><br /><br /> <span data-ttu-id="10257-154">既定値は Explicit です。</span><span class="sxs-lookup"><span data-stu-id="10257-154">The default value is Explicit.</span></span>|  
|<span data-ttu-id="10257-155">listenUri</span><span class="sxs-lookup"><span data-stu-id="10257-155">listenUri</span></span>|<span data-ttu-id="10257-156">サービス エンドポイントがリッスンする URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-156">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="10257-157">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="10257-157">The default is an empty string.</span></span>|  
|<span data-ttu-id="10257-158">name</span><span class="sxs-lookup"><span data-stu-id="10257-158">name</span></span>|<span data-ttu-id="10257-159">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="10257-159">Optional attribute.</span></span> <span data-ttu-id="10257-160">サービス エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10257-160">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="10257-161">既定値は、バインディング名とコントラクトの説明の名前を連結した値です。</span><span class="sxs-lookup"><span data-stu-id="10257-161">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="10257-162">サービスには複数のエンドポイントが存在する場合があるため、エンドポイントの `name` 属性はサービスの名前とは異なります。</span><span class="sxs-lookup"><span data-stu-id="10257-162">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10257-163">子要素</span><span class="sxs-lookup"><span data-stu-id="10257-163">Child Elements</span></span>  
  
|<span data-ttu-id="10257-164">要素</span><span class="sxs-lookup"><span data-stu-id="10257-164">Element</span></span>|<span data-ttu-id="10257-165">説明</span><span class="sxs-lookup"><span data-stu-id="10257-165">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="10257-166">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="10257-166">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="10257-167">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="10257-167">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10257-168">親要素</span><span class="sxs-lookup"><span data-stu-id="10257-168">Parent Elements</span></span>  
  
|<span data-ttu-id="10257-169">要素</span><span class="sxs-lookup"><span data-stu-id="10257-169">Element</span></span>|<span data-ttu-id="10257-170">説明</span><span class="sxs-lookup"><span data-stu-id="10257-170">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="10257-171">クライアントが接続可能なエンドポイントの一覧を定義する設定セクションです。</span><span class="sxs-lookup"><span data-stu-id="10257-171">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="10257-172">例</span><span class="sxs-lookup"><span data-stu-id="10257-172">Example</span></span>  

 <span data-ttu-id="10257-173">これはサービス エンドポイントの構成の例です。</span><span class="sxs-lookup"><span data-stu-id="10257-173">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="10257-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="10257-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="10257-175">エンドポイント:アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="10257-175">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="10257-176">方法: 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="10257-176">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
