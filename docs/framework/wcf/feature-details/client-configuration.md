---
title: クライアント構成
description: WCF クライアント構成を使用して、サービスへの接続に使用されるエンドポイントのアドレス、バインディング、動作、およびコントラクトを指定する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: af9101be0067311fb1a3c0e6e575f186e8ccf161
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265974"
---
# <a name="client-configuration"></a><span data-ttu-id="be419-103">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="be419-103">Client Configuration</span></span>

<span data-ttu-id="be419-104">Windows Communication Foundation (WCF) クライアント構成を使用して、クライアント エンドポイントのアドレス (Address)、バインディング (Binding)、動作 (Behavior)、およびコントラクト (Contract) (頭文字を取って "ABC" プロパティと呼ばれます) を指定できます。これらは、クライアントがサービス エンドポイントに接続するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="be419-104">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="be419-105">[\<client>](../../configure-apps/file-schema/wcf/client.md) 要素には [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) 要素があり、その属性はエンドポイントの ABC を構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="be419-105">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="be419-106">これらの属性については、[「エンドポイントの構成」](#configuring-endpoints)セクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="be419-106">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="be419-107">また、[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) 要素には、メタデータのインポートおよびエクスポート設定を指定するために使用される [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) 要素、カスタムのアドレス ヘッダーのコレクションを格納する [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 要素、およびメッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 要素も含まれます。</span><span class="sxs-lookup"><span data-stu-id="be419-107">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="be419-108">[\<headers>](../../configure-apps/file-schema/wcf/headers.md) および [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 要素は <xref:System.ServiceModel.EndpointAddress> の一部であり、[アドレス](endpoint-addresses.md)に関する記事で説明されています。</span><span class="sxs-lookup"><span data-stu-id="be419-108">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](endpoint-addresses.md) article.</span></span> <span data-ttu-id="be419-109">メタデータ拡張の使用法を説明しているトピックへのリンクは、「[メタデータの構成](#configuring-metadata)」セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="be419-109">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="be419-110">エンドポイントの構成</span><span class="sxs-lookup"><span data-stu-id="be419-110">Configuring Endpoints</span></span>  

 <span data-ttu-id="be419-111">クライアント構成は、クライアントがエンドポイントを 1 つ以上指定できるように設計されます。それぞれが、独自の名前、アドレス、およびコントラクトを持ち、そのエンドポイントを構成するために使用されるクライアント構成の [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) および [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 要素を参照します。</span><span class="sxs-lookup"><span data-stu-id="be419-111">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="be419-112">クライアント構成ファイルには、"App.config" という名前を付ける必要があります。これは、WCF ランタイムが想定している名前です。</span><span class="sxs-lookup"><span data-stu-id="be419-112">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="be419-113">クライアント構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be419-113">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
            <!-- Add another endpoint by adding another <endpoint> element. -->
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
          <!-- Configure this binding here. -->  
        </binding>  
          </wsHttpBinding>  
     </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="be419-114">省略可能な `name` 属性は、特定のコントラクトのエンドポイントを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="be419-114">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="be419-115">この属性は、サービスへのチャネルの作成時に、クライアント構成のどのエンドポイントをターゲットとし、読み込む必要があるかを指定するために、<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> または <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> が使用します。</span><span class="sxs-lookup"><span data-stu-id="be419-115">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="be419-116">エンドポイント構成名としてワイルドカード "\*" を使用できます。これは、ファイル内に使用できるエンドポイント構成が 1 つだけ存在する場合にそれを読み込み、それ以外の場合は例外をスローするように <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> メソッドに指示します。</span><span class="sxs-lookup"><span data-stu-id="be419-116">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="be419-117">この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="be419-117">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="be419-118">`name` 属性の既定値は、他の名前と同様に一致する空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="be419-118">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="be419-119">すべてのエンドポイントには、エンドポイントを検索および識別するために、アドレスが関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="be419-119">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="be419-120">`address` 属性は、エンドポイントの場所を示す URL を指定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="be419-120">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="be419-121">ただし、サービス エンドポイントのアドレスは、コードで指定することもできます。その場合は、URI (Uniform Resource Identifier) を作成し、<xref:System.ServiceModel.ServiceHost> メソッドのいずれかを使用して、この URI を <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。</span><span class="sxs-lookup"><span data-stu-id="be419-121">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="be419-122">詳細については、[アドレス](endpoint-addresses.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be419-122">For more information, see [Addresses](endpoint-addresses.md).</span></span> <span data-ttu-id="be419-123">最初に説明したように、[\<headers>](../../configure-apps/file-schema/wcf/headers.md) および [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 要素は <xref:System.ServiceModel.EndpointAddress> の一部であるため、これらについては[アドレス](endpoint-addresses.md)に関する記事でも説明されています。</span><span class="sxs-lookup"><span data-stu-id="be419-123">As the introduction indicates, the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="be419-124">`binding` 属性は、エンドポイントがサービスに接続する際に使用するバインディングの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="be419-124">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="be419-125">参照できるようにするには、種類は登録された構成セクションを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="be419-125">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="be419-126">上の例では、[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) セクションがこれであり、エンドポイントによって <xref:System.ServiceModel.WSHttpBinding> が使用されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="be419-126">In the previous example, this is the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="be419-127">ただし、エンドポイントが使用できる、指定された種類のバインディングが複数存在することもあります。</span><span class="sxs-lookup"><span data-stu-id="be419-127">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="be419-128">これらは、それぞれ (バインディングの) 種類を表す要素内に独自の [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 要素を持ちます。</span><span class="sxs-lookup"><span data-stu-id="be419-128">Each of these has its own [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element within the (binding) type element.</span></span> <span data-ttu-id="be419-129">`bindingconfiguration` 属性は、同じ種類のバインディングを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="be419-129">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="be419-130">この値は、[\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 要素の `name` 属性と一致します。</span><span class="sxs-lookup"><span data-stu-id="be419-130">Its value is matched with the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span> <span data-ttu-id="be419-131">構成を使用してクライアント バインディングを構成する方法の詳細については、「[方法: 構成でクライアント バインディングを指定する](../how-to-specify-a-client-binding-in-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be419-131">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="be419-132">`behaviorConfiguration` 属性は、エンドポイントで使用する必要がある [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) の [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="be419-132">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="be419-133">この値は、[\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 要素の `name` 属性と一致します。</span><span class="sxs-lookup"><span data-stu-id="be419-133">Its value is matched with the `name` attribute of the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="be419-134">構成を使用してクライアントの動作を指定する例については、「[クライアントの動作の構成](../configuring-client-behaviors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be419-134">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="be419-135">`contract` 属性は、エンドポイントが公開するコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="be419-135">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="be419-136">この値は、<xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> の <xref:System.ServiceModel.ServiceContractAttribute> にマップされます。</span><span class="sxs-lookup"><span data-stu-id="be419-136">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="be419-137">既定値は、サービスを実装するクラスの完全な型名です。</span><span class="sxs-lookup"><span data-stu-id="be419-137">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="be419-138">メタデータの構成</span><span class="sxs-lookup"><span data-stu-id="be419-138">Configuring Metadata</span></span>  

 <span data-ttu-id="be419-139">[\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) 要素は、メタデータのインポート拡張を登録するための設定を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="be419-139">The [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="be419-140">メタデータ システムの拡張の詳細については、「[メタデータ システムの拡張](../extending/extending-the-metadata-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be419-140">For more information about extending the metadata system, see [Extending the Metadata System](../extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be419-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="be419-141">See also</span></span>

- [<span data-ttu-id="be419-142">エンドポイント:アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="be419-142">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="be419-143">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="be419-143">Configuring Client Behaviors</span></span>](../configuring-client-behaviors.md)
