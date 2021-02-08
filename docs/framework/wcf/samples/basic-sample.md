---
description: 詳細については、基本的なサンプルを参照してください。
title: 基本的なサンプル
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 064c3d616a911f789050ccd5da433ed10fcfb596
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778842"
---
# <a name="basic-sample"></a><span data-ttu-id="f6c9c-103">基本的なサンプル</span><span class="sxs-lookup"><span data-stu-id="f6c9c-103">Basic Sample</span></span>

<span data-ttu-id="f6c9c-104">このサンプルでは、サービスを探索可能にする方法と、探索可能なサービスの検索方法および呼び出し方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-104">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="f6c9c-105">このサンプルは、2 つのプロジェクト (サービスとクライアント) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-105">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="f6c9c-106">このサンプルでは、探索をコードで実装しています。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-106">This sample implements discovery in code.</span></span>  <span data-ttu-id="f6c9c-107">構成で探索を実装するサンプルについては、「 [構成](configuration-sample.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-107">For a sample that implements discovery in configuration, see [Configuration](configuration-sample.md).</span></span>

## <a name="service"></a><span data-ttu-id="f6c9c-108">サービス</span><span class="sxs-lookup"><span data-stu-id="f6c9c-108">Service</span></span>

<span data-ttu-id="f6c9c-109">これは簡単な電卓サービスの実装です。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-109">This is a simple calculator service implementation.</span></span> <span data-ttu-id="f6c9c-110">探索関連のコードは `Main` にあります。ここでは、次のコードに示すように、 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> がサービス ホストに追加され、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-110">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new
      WSHttpBinding(), String.Empty);

    // Make the service discoverable over UDP multicast
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="f6c9c-111">クライアント</span><span class="sxs-lookup"><span data-stu-id="f6c9c-111">Client</span></span>

<span data-ttu-id="f6c9c-112">クライアントは、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を使用してサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-112">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="f6c9c-113"><xref:System.ServiceModel.Discovery.DynamicEndpoint> は標準エンドポイントで、クライアントが開いたときにサービスのエンドポイントを解決します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-113">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="f6c9c-114">この場合、<xref:System.ServiceModel.Discovery.DynamicEndpoint> は、サービス コントラクトに基づいてサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-114">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="f6c9c-115"><xref:System.ServiceModel.Discovery.DynamicEndpoint> は、既定で <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を検索します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-115">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="f6c9c-116">サービス エンドポイントが見つかると、クライアントは指定されたバインディングを介してそのサービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-116">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

<span data-ttu-id="f6c9c-117">クライアントは、`InvokeCalculatorService` クラスを使用してサービスを検索する <xref:System.ServiceModel.Discovery.DiscoveryClient> という名前のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-117">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="f6c9c-118"><xref:System.ServiceModel.Discovery.DynamicEndpoint> は <xref:System.ServiceModel.Description.ServiceEndpoint> を継承しているため、`InvokeCalculatorService` メソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-118">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="f6c9c-119">この例では、次に <xref:System.ServiceModel.Discovery.DynamicEndpoint> を使用して `CalculatorServiceClient` インスタンスを作成し、電卓サービスのさまざまな操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-119">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>

```csharp
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)
{
   // Create a client
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);

   Console.WriteLine("Invoking CalculatorService");
   Console.WriteLine();

   double value1 = 100.00D;
   double value2 = 15.99D;

   // Call the Add service operation.
   double result = client.Add(value1, value2);
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

   // Call the Subtract service operation.
   result = client.Subtract(value1, value2);
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

   // Call the Multiply service operation.
   result = client.Multiply(value1, value2);
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

   // Call the Divide service operation.
   result = client.Divide(value1, value2);
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
   Console.WriteLine();

   //Closing the client gracefully closes the connection and cleans up resources
   client.Close();
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="f6c9c-120">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="f6c9c-120">To use this sample</span></span>

1. <span data-ttu-id="f6c9c-121">このサンプルでは HTTP エンドポイントを使用します。このサンプルを実行するには、適切な URL ACL を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="f6c9c-122">詳細については、「 [HTTP および HTTPS の構成](../feature-details/configuring-http-and-https.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-122">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="f6c9c-123">管理特権で次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-123">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="f6c9c-124">そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-124">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="f6c9c-125">Visual Studio 2012 を使用して、基本的な .sln を開き、サンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-125">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>

3. <span data-ttu-id="f6c9c-126">service.exe アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-126">Run the service.exe application.</span></span>

4. <span data-ttu-id="f6c9c-127">サービスが開始したら、client.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-127">After the service has started, run the client.exe.</span></span>

5. <span data-ttu-id="f6c9c-128">クライアントがサービスのアドレスを知ることなくサービスを検索できたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-128">Observe that the client was able to find the service without knowing its address.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6c9c-129">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6c9c-130">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-130">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f6c9c-131">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6c9c-132">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f6c9c-132">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
