---
description: 詳細については <endpoint> 、 <client>
title: <endpoint> の <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 4ace6d49ba18524729925b20cf08e5d57bcc40c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725781"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="000be-103">\<endpoint> の \<client></span><span class="sxs-lookup"><span data-stu-id="000be-103">\<endpoint> of \<client></span></span>

<span data-ttu-id="000be-104">サーバーのサービス エンドポイントに接続するためにクライアントによって使用されるチャネル エンドポイントのコントラクト、バインディング、およびアドレスのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="000be-104">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="000be-105">構文</span><span class="sxs-lookup"><span data-stu-id="000be-105">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="000be-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="000be-106">Attributes and Elements</span></span>  

 <span data-ttu-id="000be-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="000be-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="000be-108">属性</span><span class="sxs-lookup"><span data-stu-id="000be-108">Attributes</span></span>  
  
|<span data-ttu-id="000be-109">属性</span><span class="sxs-lookup"><span data-stu-id="000be-109">Attribute</span></span>|<span data-ttu-id="000be-110">説明</span><span class="sxs-lookup"><span data-stu-id="000be-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="000be-111">address</span><span class="sxs-lookup"><span data-stu-id="000be-111">address</span></span>|<span data-ttu-id="000be-112">必須の文字列属性です。</span><span class="sxs-lookup"><span data-stu-id="000be-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="000be-113">エンドポイントのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="000be-113">Specifies the address of the endpoint.</span></span> <span data-ttu-id="000be-114">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="000be-114">The default is an empty string.</span></span> <span data-ttu-id="000be-115">アドレスは、絶対 URI にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="000be-115">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="000be-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="000be-116">behaviorConfiguration</span></span>|<span data-ttu-id="000be-117">エンドポイントのインスタンス化に使用される動作の動作名を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="000be-117">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="000be-118">動作名は、サービスが定義される時点でスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="000be-118">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="000be-119">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="000be-119">The default is an empty string.</span></span>|  
|<span data-ttu-id="000be-120">binding</span><span class="sxs-lookup"><span data-stu-id="000be-120">binding</span></span>|<span data-ttu-id="000be-121">必須の文字列属性です。</span><span class="sxs-lookup"><span data-stu-id="000be-121">Required string attribute.</span></span><br /><br /> <span data-ttu-id="000be-122">使用するバインディングの種類を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="000be-122">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="000be-123">参照できるようにするには、種類は登録された構成セクションを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="000be-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="000be-124">種類は、バインディングの種類の名前ではなくセクション名で登録されます。</span><span class="sxs-lookup"><span data-stu-id="000be-124">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="000be-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="000be-125">bindingConfiguration</span></span>|<span data-ttu-id="000be-126">任意。</span><span class="sxs-lookup"><span data-stu-id="000be-126">Optional.</span></span> <span data-ttu-id="000be-127">エンドポイントがインスタンス化されるときに使用するバインディング構成の名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="000be-127">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="000be-128">バインド構成は、エンドポイントが定義される時点でスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="000be-128">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="000be-129">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="000be-129">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="000be-130">この属性は、構成ファイル内の特定のバインディング構成を参照するために、`binding` と組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="000be-130">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="000be-131">カスタム バインドを使用しようとする場合にこの属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="000be-131">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="000be-132">そうでない場合は、例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="000be-132">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="000be-133">コントラクト (contract)</span><span class="sxs-lookup"><span data-stu-id="000be-133">contract</span></span>|<span data-ttu-id="000be-134">必須の文字列属性です。</span><span class="sxs-lookup"><span data-stu-id="000be-134">Required string attribute.</span></span><br /><br /> <span data-ttu-id="000be-135">このエンドポイントが公開するコントラクトを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="000be-135">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="000be-136">アセンブリは、コントラクト型を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="000be-136">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="000be-137">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="000be-137">endpointConfiguration</span></span>|<span data-ttu-id="000be-138">この標準エンドポイントの追加の構成情報を参照する `kind` 属性によって設定される標準エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="000be-138">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="000be-139">同じ名前を `<standardEndpoints>` セクションに定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="000be-139">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="000be-140">kind</span><span class="sxs-lookup"><span data-stu-id="000be-140">kind</span></span>|<span data-ttu-id="000be-141">適用する標準エンドポイントの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="000be-141">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="000be-142">`<extensions>` セクションまたは machine.config に種類を登録する必要があります。何も指定していない場合は、共通のチャネル エンドポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="000be-142">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="000be-143">name</span><span class="sxs-lookup"><span data-stu-id="000be-143">name</span></span>|<span data-ttu-id="000be-144">省略可能な文字列属性。</span><span class="sxs-lookup"><span data-stu-id="000be-144">Optional string attribute.</span></span> <span data-ttu-id="000be-145">この属性は、特定のコントラクトのエンドポイントを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="000be-145">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="000be-146">特定のコントラクトの種類に、複数のクライアントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="000be-146">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="000be-147">それぞれの定義は、一意の構成名で区別できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="000be-147">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="000be-148">この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="000be-148">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="000be-149">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="000be-149">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="000be-150">バインディングの `name` 属性は、WSDL を介した定義エクスポートに使用されます。</span><span class="sxs-lookup"><span data-stu-id="000be-150">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="000be-151">子要素</span><span class="sxs-lookup"><span data-stu-id="000be-151">Child Elements</span></span>  
  
|<span data-ttu-id="000be-152">要素</span><span class="sxs-lookup"><span data-stu-id="000be-152">Element</span></span>|<span data-ttu-id="000be-153">説明</span><span class="sxs-lookup"><span data-stu-id="000be-153">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="000be-154">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="000be-154">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="000be-155">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="000be-155">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="000be-156">親要素</span><span class="sxs-lookup"><span data-stu-id="000be-156">Parent Elements</span></span>  
  
|<span data-ttu-id="000be-157">要素</span><span class="sxs-lookup"><span data-stu-id="000be-157">Element</span></span>|<span data-ttu-id="000be-158">説明</span><span class="sxs-lookup"><span data-stu-id="000be-158">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="000be-159">クライアントが接続可能なエンドポイントの一覧を定義する設定セクションです。</span><span class="sxs-lookup"><span data-stu-id="000be-159">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="000be-160">例</span><span class="sxs-lookup"><span data-stu-id="000be-160">Example</span></span>  

 <span data-ttu-id="000be-161">これはチャネル エンドポイントの構成の例です。</span><span class="sxs-lookup"><span data-stu-id="000be-161">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="000be-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="000be-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="000be-163">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="000be-163">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="000be-164">クライアント</span><span class="sxs-lookup"><span data-stu-id="000be-164">Clients</span></span>](../../../wcf/feature-details/clients.md)
