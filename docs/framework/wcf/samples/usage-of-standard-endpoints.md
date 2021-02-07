---
description: 詳細については、標準エンドポイントの使用に関するページを参照してください。
title: 標準エンドポイントの使用
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 804fdd84d3f6ff6f961aed81e8bd14cf8c43063c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685414"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="cb45d-103">標準エンドポイントの使用</span><span class="sxs-lookup"><span data-stu-id="cb45d-103">Usage of Standard Endpoints</span></span>

<span data-ttu-id="cb45d-104">このサンプルでは、サービスの構成ファイルでの標準エンドポイントの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-104">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="cb45d-105">標準エンドポイントでは、単一のプロパティを使用してアドレス、バインディング、およびコントラクトの組み合わせをそのエンドポイントに関連付けられている追加のプロパティで記述することで、エンドポイントの定義を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-105">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="cb45d-106">このサンプルでは、カスタムの標準エンドポイントを定義して実装する方法、およびエンドポイントの特定のプロパティを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-106">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="cb45d-107">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="cb45d-107">Sample Details</span></span>

<span data-ttu-id="cb45d-108">サービス エンドポイントは、アドレス、バインディング、およびコントラクトの 3 つのパラメーターを指定して指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-108">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="cb45d-109">指定できるその他のパラメーターには、動作構成、ヘッダー、リッスン URI などがあります。</span><span class="sxs-lookup"><span data-stu-id="cb45d-109">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="cb45d-110">アドレス、バインディング、およびコントラクトのいずれかまたはすべてに、変更できない値が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb45d-110">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="cb45d-111">このような理由から、標準エンドポイントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-111">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="cb45d-112">このようなエンドポイントの例として、メタデータ交換エンドポイントや探索エンドポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="cb45d-112">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="cb45d-113">また、標準エンドポイントでは、固定された性質の情報を提供したり、独自の標準エンドポイントを作成したりしなくても、サービス エンドポイントを構成できるため、ユーザビリティが向上します。たとえば、適切な既定の値のセットを指定し、構成ファイルの詳細を削減してユーザビリティを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-113">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="cb45d-114">このサンプルは、2 つの標準エンドポイントを定義するサービスおよびサービスと通信するクライアントの 2 つのプロジェクトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="cb45d-114">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="cb45d-115">構成ファイルでサービスの標準エンドポイントを定義する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-115">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="cb45d-116">サービスに定義されている最初のエンドポイントは、`customEndpoint` の一種で、その定義については、`<standardEndpoints>` セクションで確認できます。このセクションでは、プロパティ `property` に `true` の値が指定されています。</span><span class="sxs-lookup"><span data-stu-id="cb45d-116">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="cb45d-117">これは、新しいプロパティでカスタマイズされたエンドポイントの例です。</span><span class="sxs-lookup"><span data-stu-id="cb45d-117">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="cb45d-118">2 つ目のエンドポイントはメタデータ エンドポイントを表します。このエンドポイントでは、アドレス、バインディング、およびコントラクトの値が固定されています。</span><span class="sxs-lookup"><span data-stu-id="cb45d-118">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="cb45d-119">標準エンドポイント要素を定義するには、`StandardEndpointElement` から派生するクラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb45d-119">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="cb45d-120">このサンプルでは、`CustomEndpointElement` クラスは、次の例のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="cb45d-120">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

<span data-ttu-id="cb45d-121">`CreateServiceEndpoint` 関数で、`CustomEndpoint` オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-121">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="cb45d-122">その定義を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-122">Its definition is shown in the following example:</span></span>

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 <span data-ttu-id="cb45d-123">サービスとクライアントとの間で通信を実行するために、クライアントでサービスに対するサービス参照が作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-123">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="cb45d-124">このサンプルをビルドして実行した場合、サービスが実行されて、クライアントはそのサービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-124">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="cb45d-125">サービスが変更されるたびに、サービス参照を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb45d-125">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="cb45d-126">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="cb45d-126">To use this sample</span></span>

1. <span data-ttu-id="cb45d-127">Visual Studio 2012 を使用して、StandardEndpoints .sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-127">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="cb45d-128">複数のプロジェクトを起動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="cb45d-128">Enable multiple projects to start up.</span></span>

    1. <span data-ttu-id="cb45d-129">**ソリューションエクスプローラー** で、標準エンドポイントソリューションを右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-129">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2. <span data-ttu-id="cb45d-130">[ **共通プロパティ**] で、[ **スタートアッププロジェクト**] を選択し、[ **マルチスタートアッププロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45d-130">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3. <span data-ttu-id="cb45d-131">サービスプロジェクトを一覧の先頭に移動し、 **アクション** を [ **開始**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-131">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4. <span data-ttu-id="cb45d-132">サービスプロジェクトの後に、 **アクション** が [ **開始**] に設定されているクライアントプロジェクトを移動します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-132">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="cb45d-133">これで、Client プロジェクトは Service プロジェクトの後に実行されます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-133">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="cb45d-134">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-134">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="cb45d-135">これらの手順が機能しない場合は、次の手順に従って、環境が適切に設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cb45d-135">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="cb45d-136">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb45d-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="cb45d-137">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="cb45d-137">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="cb45d-138">1つまたは複数のコンピューター構成でサンプルを実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="cb45d-138">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb45d-139">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb45d-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb45d-140">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cb45d-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cb45d-141">このディレクトリが存在しない場合は、 [.NET Framework 4 の Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプル](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="cb45d-141">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb45d-142">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cb45d-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
