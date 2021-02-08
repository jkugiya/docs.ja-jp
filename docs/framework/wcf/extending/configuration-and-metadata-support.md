---
description: '詳細情報: 構成とメタデータのサポート'
title: 構成とメタデータのサポート
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 725d6625e224ea3de5d8bd49fd06199e7c5d61be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802984"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="95a4a-103">構成とメタデータのサポート</span><span class="sxs-lookup"><span data-stu-id="95a4a-103">Configuration and Metadata Support</span></span>

<span data-ttu-id="95a4a-104">ここでは、バインディングおよびバインド要素用に構成とメタデータのサポートを有効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-104">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="95a4a-105">構成とメタデータの概要</span><span class="sxs-lookup"><span data-stu-id="95a4a-105">Overview of Configuration and Metadata</span></span>  

 <span data-ttu-id="95a4a-106">このトピックでは、次のタスクについて説明します。これらのタスクは、 [チャネルの開発](developing-channels.md) タスク一覧のオプションの項目1、2、および4です。</span><span class="sxs-lookup"><span data-stu-id="95a4a-106">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="95a4a-107">バインド要素の構成ファイル サポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="95a4a-107">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="95a4a-108">バインディングの構成ファイル サポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="95a4a-108">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="95a4a-109">バインド要素の WSDL とポリシー アサーションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="95a4a-109">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="95a4a-110">バインディングまたはバインド要素に挿入して構成する WSDL とポリシー アサーションを特定します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-110">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="95a4a-111">ユーザー定義バインディングとバインド要素の作成の詳細については、それぞれ「 [User-Defined バインディングの作成](creating-user-defined-bindings.md) 」と「 [BindingElement の作成](creating-a-bindingelement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95a4a-111">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="95a4a-112">構成サポートの追加</span><span class="sxs-lookup"><span data-stu-id="95a4a-112">Adding Configuration Support</span></span>  

 <span data-ttu-id="95a4a-113">チャネルに対する構成ファイルのサポートを有効にするには、2 つの構成セクションを実装する必要があります。1 つはバインド要素に対する構成のサポートを有効にする <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> で、もう 1 つはバインディングに対する構成のサポートを有効にする <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> と <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="95a4a-113">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="95a4a-114">これを行う簡単な方法は、 [Configurationcodegenerator](../samples/configurationcodegenerator.md) サンプルツールを使用して、バインドとバインド要素の構成コードを生成することです。</span><span class="sxs-lookup"><span data-stu-id="95a4a-114">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="95a4a-115">BindingElementExtensionElement の拡張</span><span class="sxs-lookup"><span data-stu-id="95a4a-115">Extending BindingElementExtensionElement</span></span>  

 <span data-ttu-id="95a4a-116">次のコード例は、 [Transport: UDP](../samples/transport-udp.md) サンプルから取得したものです。</span><span class="sxs-lookup"><span data-stu-id="95a4a-116">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="95a4a-117">`UdpTransportElement` は <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> を構成システムに公開する `UdpTransportBindingElement` です。</span><span class="sxs-lookup"><span data-stu-id="95a4a-117">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="95a4a-118">いくつかの基本的なオーバーライドを行うことで、サンプルでは構成セクション名、バインド要素の種類とバインド要素の作成方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-118">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="95a4a-119">その後、次のようにして拡張セクションを構成ファイルに登録できます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-119">Users can then register the extension section in a configuration file as follows.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="95a4a-120">この拡張は、UDP をトランスポートとして使用するためにカスタム バインドから参照されます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-120">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="95a4a-121">バインディングの構成の追加</span><span class="sxs-lookup"><span data-stu-id="95a4a-121">Adding Configuration for a Binding</span></span>  

 <span data-ttu-id="95a4a-122">セクション `SampleProfileUdpBindingCollectionElement` は <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> で、`SampleProfileUdpBinding` を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-122">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="95a4a-123">実装の大部分は `SampleProfileUdpBindingConfigurationElement` で代行されます。これは <xref:System.ServiceModel.Configuration.StandardBindingElement> の派生です。</span><span class="sxs-lookup"><span data-stu-id="95a4a-123">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="95a4a-124">`SampleProfileUdpBindingConfigurationElement`には、のプロパティに対応するプロパティ `SampleProfileUdpBinding` と、バインディングからマップする関数があり `ConfigurationElement` ます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-124">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="95a4a-125">次のサンプル コードで示すように、最後に、`OnApplyConfiguration` メソッドが `SampleProfileUdpBinding` 内でオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-125">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="95a4a-126">このハンドラーを構成システムに登録するには、次のセクションを関連する構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-126">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="95a4a-127">その後、構成セクションから参照でき [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-127">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="95a4a-128">バインド要素のメタデータ サポートの追加</span><span class="sxs-lookup"><span data-stu-id="95a4a-128">Adding Metadata Support for a Binding Element</span></span>  

 <span data-ttu-id="95a4a-129">チャネルをメタデータ システムに統合するには、ポリシーのインポートとエクスポートの両方がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a4a-129">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="95a4a-130">これにより、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) などのツールで、バインド要素のクライアントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-130">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="95a4a-131">WSDL サポートの追加</span><span class="sxs-lookup"><span data-stu-id="95a4a-131">Adding WSDL Support</span></span>  

 <span data-ttu-id="95a4a-132">バインディングのトランスポート バインド要素は、メタデータのアドレス指定情報のインポートとエクスポートを行います。</span><span class="sxs-lookup"><span data-stu-id="95a4a-132">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="95a4a-133">SOAP バインディングを使用する場合は、トランスポート バインド要素によっても、メタデータの正しいトランスポート URI がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-133">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="95a4a-134">次のコード例は、 [Transport: UDP](../samples/transport-udp.md) サンプルから取得したものです。</span><span class="sxs-lookup"><span data-stu-id="95a4a-134">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="95a4a-135">WSDL エクスポート</span><span class="sxs-lookup"><span data-stu-id="95a4a-135">WSDL Export</span></span>  

 <span data-ttu-id="95a4a-136">アドレス指定情報をエクスポートするために、は `UdpTransportBindingElement` インターフェイスを実装し <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-136">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="95a4a-137"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> メソッドにより、正しいアドレス指定情報が WSDL ポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-137">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="95a4a-138">エンドポイントが SOAP バインディングを使用する場合、`UdpTransportBindingElement` メソッドの <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> の実装でも、次のようにトランスポート URI がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-138">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="95a4a-139">WSDL インポート</span><span class="sxs-lookup"><span data-stu-id="95a4a-139">WSDL Import</span></span>  

 <span data-ttu-id="95a4a-140">WSDL インポート システムを拡張してアドレスのインポートを処理するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95a4a-140">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </wsdlImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="95a4a-141">Svcutil.exe を実行する場合、Svcutil.exe に WSDL インポートの拡張を読み込ませるために次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="95a4a-141">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="95a4a-142">/SvcutilConfig: を使用して、構成ファイル Svcutil.exe ポイントし \<file> ます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-142">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="95a4a-143">Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-143">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="95a4a-144">`UdpBindingElementImporter` 型は、<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-144">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="95a4a-145">`ImportEndpoint` メソッドは、次のようにして WSDL ポートからアドレスをインポートします。</span><span class="sxs-lookup"><span data-stu-id="95a4a-145">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="95a4a-146">ポリシー サポートの追加</span><span class="sxs-lookup"><span data-stu-id="95a4a-146">Adding Policy Support</span></span>  

 <span data-ttu-id="95a4a-147">カスタム バインド要素では、WSDL バインディング内のポリシー アサーションをエクスポートして、サービス エンドポイントでそのバインド要素の機能を表現します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-147">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="95a4a-148">次のコード例は、 [Transport: UDP](../samples/transport-udp.md) サンプルから取得したものです。</span><span class="sxs-lookup"><span data-stu-id="95a4a-148">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="95a4a-149">ポリシーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="95a4a-149">Policy Export</span></span>  

 <span data-ttu-id="95a4a-150">この `UdpTransportBindingElement` 型は、 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> ポリシーをエクスポートするためのサポートを追加するためにを実装します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-150">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="95a4a-151">その結果、<xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> には、これを含む任意のバインディングでのポリシーの生成時に `UdpTransportBindingElement` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-151">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="95a4a-152"><xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType> では、UDP のアサーションを追加します。チャネルがマルチキャスト モードである場合は、別のアサーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-152">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="95a4a-153">これは、マルチキャスト モードは通信スタックの構築方法に影響を与えるため、両方の側において調整される必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="95a4a-153">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="95a4a-154">カスタム トランスポート バインド要素はアドレス指定の処理を実行するため、<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> への `UdpTransportBindingElement` の実装でも、WS-Addressing ポリシー アサーションのエクスポートが処理されて、使用されている WS-Addressing のバージョンが示されます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-154">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="95a4a-155">ポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="95a4a-155">Policy Import</span></span>  

 <span data-ttu-id="95a4a-156">ポリシー インポート システムを拡張するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95a4a-156">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="95a4a-157">次に、登録されたクラス (<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType>) から `UdpBindingElementImporter` を実装します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-157">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="95a4a-158"><xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> で、適切な名前空間にあるアサーションを調べ、トランスポートを生成するためにそのアサーションを処理して、マルチキャストであるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="95a4a-158">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="95a4a-159">さらに、インポーターが処理するアサーションをバインディング アサーションの一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-159">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="95a4a-160">Svcutil.exe を実行する場合、ここでも、統合用に次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="95a4a-160">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="95a4a-161">/SvcutilConfig を使用して、構成ファイルに Svcutil.exe ポイントし \<file> ます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-161">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="95a4a-162">Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-162">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="95a4a-163">カスタムの標準バインディング インポーターの追加</span><span class="sxs-lookup"><span data-stu-id="95a4a-163">Adding a Custom Standard Binding Importer</span></span>  

 <span data-ttu-id="95a4a-164">Svcutil.exe と <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> 型は、既定でシステム指定のバインディングを識別してインポートします。</span><span class="sxs-lookup"><span data-stu-id="95a4a-164">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="95a4a-165">これ以外の場合、バインディングは、<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> インスタンスとしてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-165">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="95a4a-166">Svcutil.exe と <xref:System.ServiceModel.Description.WsdlImporter> を有効にして `SampleProfileUdpBinding` をインポートする場合、`UdpBindingElementImporter` もカスタムの標準バインディング インポーターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-166">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="95a4a-167">カスタムの標準バインディングインポーターは、インターフェイスのメソッドを実装して、 `ImportEndpoint` <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> メタデータからインポートされたインスタンスを調べて、特定の標準バインディングによって生成された可能性があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-167">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="95a4a-168">一般に、カスタムの標準バインディング インポーターを実装すると、インポートしたバインド要素のプロパティを調べて、標準バインディングによって設定されたプロパティのみが変更され、その他のすべてのプロパティは既定のままであることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="95a4a-168">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="95a4a-169">標準バインディング インポーターを実装する場合の基本的な方法は、標準バインディングのインスタンスを作成し、標準バインディングがサポートするバインド要素のプロパティを標準バインディング インスタンスに反映し、標準バインディングのバインド要素とインポートしたバインド要素とを比較します。</span><span class="sxs-lookup"><span data-stu-id="95a4a-169">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
