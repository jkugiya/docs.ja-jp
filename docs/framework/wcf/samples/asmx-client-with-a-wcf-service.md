---
description: 詳細については、「WCF サービスを使用した ASMX クライアント」を参照してください。
title: WCF サービス付き ASMX クライアント
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: b9f561f6651c591556f821478c4c4bfd7d7da23d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778920"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="898d0-103">WCF サービス付き ASMX クライアント</span><span class="sxs-lookup"><span data-stu-id="898d0-103">ASMX Client with a WCF Service</span></span>

<span data-ttu-id="898d0-104">このサンプルでは、Windows Communication Foundation (WCF) を使用してサービスを作成し、ASMX クライアントなどの WCF 以外のクライアントからサービスにアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="898d0-104">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>

> [!NOTE]
> <span data-ttu-id="898d0-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="898d0-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="898d0-106">このサンプルは、クライアント コンソール プログラム (.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="898d0-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="898d0-107">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="898d0-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="898d0-108">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (`Add`、`Subtract`、`Multiply`、`Divide`) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="898d0-108">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="898d0-109">ASMX クライアントは算術演算を同期要求し、サービスは結果を添えて応答します。</span><span class="sxs-lookup"><span data-stu-id="898d0-109">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>

<span data-ttu-id="898d0-110">サービスは、次に示すコードで定義される `ICalculator` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="898d0-110">The service implements an `ICalculator` contract as defined in the following code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="898d0-111"><xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Xml.Serialization.XmlSerializer> は、CLR 型を XML 表現にマップします。</span><span class="sxs-lookup"><span data-stu-id="898d0-111">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="898d0-112"><xref:System.Runtime.Serialization.DataContractSerializer> は一部の XML 表現を、XmlSerializer とは異なる方法で解釈します。</span><span class="sxs-lookup"><span data-stu-id="898d0-112">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="898d0-113">Wsdl.exe などの WCF 以外のプロキシジェネレーターは、XmlSerializer が使用されている場合に、より使用可能なインターフェイスを生成します。</span><span class="sxs-lookup"><span data-stu-id="898d0-113">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="898d0-114">は、 <xref:System.ServiceModel.XmlSerializerFormatAttribute> `ICalculator` CLR 型を XML にマッピングするために XmlSerializer が使用されるように、インターフェイスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="898d0-114">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="898d0-115">このサービス実装は、計算を行い、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="898d0-115">The service implementation calculates and returns the appropriate result.</span></span>

<span data-ttu-id="898d0-116">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル (Web.config) で定義します。</span><span class="sxs-lookup"><span data-stu-id="898d0-116">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="898d0-117">エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="898d0-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="898d0-118">サービスは、インターネット インフォメーション サービス (IIS) ホストから提供されるベース アドレスで、エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="898d0-118">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="898d0-119">`binding` 属性は basicHttpBinding に設定されます。これにより、WS-I Basic Profile 1.1 に準拠した SOAP 1.1 を使用する HTTP 通信を実現します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="898d0-119">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>

```xml
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->
    <endpoint address=""
              binding="basicHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
</services>
```

<span data-ttu-id="898d0-120">ASMX クライアントは、Web サービス記述言語 (WSDL) ユーティリティ (Wsdl.exe) によって生成される型指定されたプロキシを使用して、WCF サービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="898d0-120">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="898d0-121">型指定のあるプロキシは、ファイル generatedClient.cs に含まれています。</span><span class="sxs-lookup"><span data-stu-id="898d0-121">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="898d0-122">WSDL ユーティリティは、指定されたサービスが使用するメタデータを取得し、クライアントが通信に使用する型指定のあるプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="898d0-122">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="898d0-123">既定では、フレームワークはメタデータを公開しません。</span><span class="sxs-lookup"><span data-stu-id="898d0-123">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="898d0-124">プロキシを生成するために必要なメタデータを公開するには、 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) `httpGetEnabled` 次の `True` 構成に示すように、を追加し、その属性をに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="898d0-124">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <!-- Setting httpGetEnabled to True on the serviceMetadata
           behavior exposes the service's wsdl at <base address>?wsdl :
           http://localhost/servicemodelsamples/service.svc?wsdl -->
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="898d0-125">次のコマンドをクライアント ディレクトリでコマンド プロンプトから実行して、型指定のあるプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="898d0-125">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

<span data-ttu-id="898d0-126">生成された型指定のあるプロキシを使用することにより、クライアントは適切なアドレスを構成して、指定のサービス エンドポイントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="898d0-126">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="898d0-127">クライアントは構成ファイル (App.config) を使用して、通信するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="898d0-127">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

<span data-ttu-id="898d0-128">クライアント実装は型指定のあるプロキシのインスタンスを構築し、サービスとの通信を開始します。</span><span class="sxs-lookup"><span data-stu-id="898d0-128">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>

```csharp
// Create a client to the CalculatorService.
using (CalculatorService client = new CalculatorService())
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

}

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="898d0-129">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="898d0-129">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="898d0-130">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="898d0-130">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="898d0-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="898d0-131">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="898d0-132">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="898d0-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="898d0-133">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="898d0-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="898d0-134">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="898d0-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="898d0-135">複合データ型を渡すと返す方法の詳細については、「 [Windows フォームクライアントでのデータバインディング](data-binding-in-a-windows-forms-client.md)」、「 [Windows Presentation Foundation クライアントでのデータバインディング](data-binding-in-a-wpf-client.md)」、および「 [ASP.NET クライアントでのデータ](data-binding-in-an-aspnet-client.md)バインディング」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="898d0-135">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](data-binding-in-an-aspnet-client.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="898d0-136">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="898d0-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="898d0-137">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="898d0-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="898d0-138">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="898d0-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="898d0-139">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="898d0-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
