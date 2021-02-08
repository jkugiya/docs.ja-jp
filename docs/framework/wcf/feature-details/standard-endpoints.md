---
description: '詳細情報: Standard エンドポイント'
title: 標準エンドポイント
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 5879bab5dff4dee8ac574bad1c4452a60cf7c323
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793442"
---
# <a name="standard-endpoints"></a><span data-ttu-id="4b847-103">標準エンドポイント</span><span class="sxs-lookup"><span data-stu-id="4b847-103">Standard Endpoints</span></span>

<span data-ttu-id="4b847-104">エンドポイントは、アドレス、バインディング、およびコントラクトを指定して定義します。</span><span class="sxs-lookup"><span data-stu-id="4b847-104">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="4b847-105">エンドポイントに設定できるその他のパラメーターには、動作構成、ヘッダー、リッスン URI などがあります。</span><span class="sxs-lookup"><span data-stu-id="4b847-105">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="4b847-106">特定の種類のエンドポイントでは、これらの値が変化しません。</span><span class="sxs-lookup"><span data-stu-id="4b847-106">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="4b847-107">たとえば、メタデータ交換エンドポイントでは、常に <xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b847-107">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="4b847-108"><xref:System.ServiceModel.Description.WebHttpEndpoint> などのその他のエンドポイントでは、指定されたエンドポイント動作が必要です。</span><span class="sxs-lookup"><span data-stu-id="4b847-108">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="4b847-109">一般的に使用されるエンドポイント プロパティの既定の値を設定することによって、エンドポイントの操作性を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="4b847-109">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="4b847-110">開発者は、標準エンドポイントを使用して、既定値を持つエンドポイント、またはエンドポイントの 1 つ以上のプロパティが変化しないエンドポイントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="4b847-110">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="4b847-111">これらのエンドポイントによって、静的な性質の情報を指定する必要がないエンドポイントの使用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="4b847-111">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="4b847-112">標準エンドポイントは、インフラストラクチャ エンドポイントおよびアプリケーション エンドポイントに使用できます。</span><span class="sxs-lookup"><span data-stu-id="4b847-112">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="4b847-113">インフラストラクチャ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="4b847-113">Infrastructure Endpoints</span></span>  

 <span data-ttu-id="4b847-114">サービスの作成者が明示的に実装していないいくつかのプロパティを持つエンドポイントを、サービスが公開することがあります。</span><span class="sxs-lookup"><span data-stu-id="4b847-114">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="4b847-115">たとえば、メタデータ交換エンドポイントは <xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを公開しますが、そのインターフェイスを実装するのは、サービスの作成者ではなく、WCF です。</span><span class="sxs-lookup"><span data-stu-id="4b847-115">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="4b847-116">このようなインフラストラクチャ エンドポイントには、1 つ以上のプロパティの既定値があり、そのいくつかは変更できません。</span><span class="sxs-lookup"><span data-stu-id="4b847-116">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="4b847-117">メタデータ交換エンドポイントの <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> プロパティは <xref:System.ServiceModel.Description.IMetadataExchange> である必要がありますが、バインディングなど、その他のプロパティは開発者が提供できます。</span><span class="sxs-lookup"><span data-stu-id="4b847-117">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="4b847-118">インフラストラクチャ エンドポイントは、<xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> プロパティを `true` に設定することによって識別されます。</span><span class="sxs-lookup"><span data-stu-id="4b847-118">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="4b847-119">アプリケーション エンドポイント</span><span class="sxs-lookup"><span data-stu-id="4b847-119">Application Endpoints</span></span>  

 <span data-ttu-id="4b847-120">アプリケーション開発者は独自の標準エンドポイントを定義でき、このエンドポイントでアドレス、バインディング、またはコントラクトの既定値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="4b847-120">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="4b847-121">標準エンドポイントを定義するには、<xref:System.ServiceModel.Description.ServiceEndpoint> からクラスを派生させ、適切なエンドポイント プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4b847-121">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="4b847-122">変更可能な既定値をプロパティに設定できます。</span><span class="sxs-lookup"><span data-stu-id="4b847-122">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="4b847-123">他のいくつかのプロパティには、変更できない静的な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="4b847-123">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="4b847-124">次の例は、標準エンドポイントの実装方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b847-124">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  

    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="4b847-125">構成ファイルでユーザー定義のカスタムエンドポイントを使用するには、からクラスを派生させ <xref:System.ServiceModel.Configuration.StandardEndpointElement> 、からクラスを派生させ、 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> app.config または machine.config の extensions セクションに新しい標準エンドポイントを登録する必要があります。 では、 <xref:System.ServiceModel.Configuration.StandardEndpointElement> 次の例に示すように、標準エンドポイントの構成がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4b847-125">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="4b847-126">は、 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> `standardEndpoints` 標準エンドポイントの構成の <> セクションの下に表示されるコレクションのバッキング型を提供します。</span><span class="sxs-lookup"><span data-stu-id="4b847-126">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="4b847-127">次の例は、このクラスを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b847-127">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="4b847-128">次の例は、拡張セクションで標準エンドポイントを登録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b847-128">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
      </standardEndpointExtensions>
</extensions>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="4b847-129">標準エンドポイントの構成</span><span class="sxs-lookup"><span data-stu-id="4b847-129">Configuring a Standard Endpoint</span></span>  

 <span data-ttu-id="4b847-130">標準エンドポイントは、コードまたは構成で追加できます。</span><span class="sxs-lookup"><span data-stu-id="4b847-130">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="4b847-131">標準エンドポイントをコードで追加するには、次の例に示すように、適切な標準エンドポイントの種類をインスタンス化し、それをサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="4b847-131">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="4b847-132">構成に標準エンドポイントを追加するには、 `endpoint` <> 要素に <> 要素を追加し、 `service` <> 要素に必要な構成設定を追加し `standardEndpoints` ます。</span><span class="sxs-lookup"><span data-stu-id="4b847-132">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="4b847-133">次の例は、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を追加する方法を示しています。これは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] に付属する標準エンドポイントの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="4b847-133">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="4b847-134">標準エンドポイントの種類は、<> 要素の kind 属性を使用して指定され `endpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="4b847-134">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="4b847-135">エンドポイントは <> 要素内で構成され `standardEndpoints` ます。</span><span class="sxs-lookup"><span data-stu-id="4b847-135">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="4b847-136">前の例では、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> エンドポイントが追加され、構成されます。</span><span class="sxs-lookup"><span data-stu-id="4b847-136">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="4b847-137"><`udpDiscoveryEndpoint`> 要素には `standardEndpoint` 、のプロパティを設定する <> が含まれてい <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ます。</span><span class="sxs-lookup"><span data-stu-id="4b847-137">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="4b847-138">.NET Framework に付属する標準エンドポイント</span><span class="sxs-lookup"><span data-stu-id="4b847-138">Standard Endpoints Shipped with the .NET Framework</span></span>  

 <span data-ttu-id="4b847-139">次の表は、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] に付属する標準エンドポイントを示しています。</span><span class="sxs-lookup"><span data-stu-id="4b847-139">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="4b847-140">サービス メタデータの公開に使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-140">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="4b847-141">サービスがアナウンス メッセージを送信するために使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-141">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="4b847-142">サービスが探索メッセージを送信するために使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-142">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="4b847-143">UDP マルチキャスト バインディング上での探索操作用に事前構成済みの標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-143">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="4b847-144">サービスが UDP バインディングでアナウンス メッセージを送信するために使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-144">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="4b847-145">実行時にエンドポイント アドレスを動的に検索するために WS-Discovery を使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-145">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="4b847-146">メタデータ交換用の標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-146">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="4b847-147"><xref:System.ServiceModel.WebHttpBinding> の動作を自動的に追加する <xref:System.ServiceModel.Description.WebHttpBehavior> バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="4b847-148"><xref:System.ServiceModel.WebHttpBinding> の動作を自動的に追加する <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="4b847-149"><xref:System.ServiceModel.WebHttpBinding> バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-149">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="4b847-150">ワークフロー インスタンスで管理操作を呼び出すことができる標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-150">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="4b847-151">ワークフローの作成とブックマークの再開をサポートする標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="4b847-151">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
