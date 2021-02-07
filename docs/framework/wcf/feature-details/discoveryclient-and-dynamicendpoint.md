---
description: 詳細については、DiscoveryClient と DynamicEndpoint に関するページを参照してください。
title: DiscoveryClient と DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 34f6c5d7d8958f4a28a6bff950f3f6dad81871ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743175"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="8af0d-103">DiscoveryClient と DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="8af0d-103">DiscoveryClient and DynamicEndpoint</span></span>

<span data-ttu-id="8af0d-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> および <xref:System.ServiceModel.Discovery.DynamicEndpoint> の 2 つは、サービスの検索にクライアント側で使用されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="8af0d-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="8af0d-105"><xref:System.ServiceModel.Discovery.DiscoveryClient> は、特定の条件に一致するサービスの一覧を表示し、サービスに接続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8af0d-105"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="8af0d-106"><xref:System.ServiceModel.Discovery.DynamicEndpoint> は同じ操作を実行するだけでなく、見つかったサービスの 1 つに自動的に接続します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-106"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="8af0d-107"><xref:System.ServiceModel.Discovery.DynamicEndpoint> には任意のエンドポイントを指定でき、構成に検索条件も追加できます。このため、ソリューションに探索機能が必要だが、クライアント ロジックを変更したくないという場合は、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を使用すると、エンドポイントを変更するだけで済み、便利です。</span><span class="sxs-lookup"><span data-stu-id="8af0d-107">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="8af0d-108">これに対して、<xref:System.ServiceModel.Discovery.DiscoveryClient> は、検索操作を詳細に制御する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-108"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="8af0d-109">次に、それぞれのクラスの用途と利点について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-109">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="8af0d-110">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="8af0d-110">DiscoveryClient</span></span>  

 <span data-ttu-id="8af0d-111"><xref:System.ServiceModel.Discovery.DiscoveryClient> は、同期および非同期の Find メソッド、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベント、および <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-111">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="8af0d-112">さらに、同期および非同期の Resolve メソッド、および <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> イベントも定義します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-112">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="8af0d-113"><xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドまたは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> メソッドを使用して、サービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-113">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="8af0d-114">これらのメソッドは両方とも <xref:System.ServiceModel.Discovery.FindCriteria> インスタンスを受け取ります。このインスタンスにより、コントラクト型名、スコープ、要求した結果の最大数、およびスコープ一致規則の指定が可能になります。</span><span class="sxs-lookup"><span data-stu-id="8af0d-114">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="8af0d-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> メソッドを呼び出す際には、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントおよび <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> イベントが使用できます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-115">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="8af0d-116"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> がサービスからの応答を受け取るたびに、<xref:System.ServiceModel.Discovery.DiscoveryClient> が発生します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-116"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="8af0d-117">これを使用して、検索操作の進捗状況を示すプログレス バーを表示できます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-117">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="8af0d-118">また、受け取った検索応答を処理するのにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-118">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="8af0d-119">検索操作が完了すると、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-119">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="8af0d-120">最大数の応答を受信した場合、または <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> が経過した場合に、これが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="8af0d-120">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="8af0d-121">検索操作が完了すると、結果が <xref:System.ServiceModel.Discovery.FindResponse> インスタンスで返されます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-121">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="8af0d-122"><xref:System.ServiceModel.Discovery.FindResponse> には <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のコレクションが含まれており、これには、一致するサービスのアドレス、コントラクト型名、拡張子、リッスン URI、およびスコープが格納されています。</span><span class="sxs-lookup"><span data-stu-id="8af0d-122">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="8af0d-123">この情報を使用して、一致するいずれかのサービスに接続し、呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-123">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="8af0d-124">次の例は、DiscoveryClient (system.servicemodel) メソッドを呼び出し、返されたメタデータを使用して検出されたサービスを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8af0d-124">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="8af0d-125">を使用する利点 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> は、見つかったエンドポイントのリストをキャッシュし、後で使用できることです。</span><span class="sxs-lookup"><span data-stu-id="8af0d-125">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="8af0d-126">このキャッシュを使用して、さまざまなエラー状況を処理するカスタム ロジックを構築できます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-126">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```csharp
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="8af0d-127">次の例は、検索操作を非同期で実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8af0d-127">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```csharp
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));
}
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 <span data-ttu-id="8af0d-128">エンドポイント アドレスに基づいてサービスを検索するには、<xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> メソッドおよび <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-128">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="8af0d-129">エンドポイント アドレスをネットワーク アドレスで指定できないアドレスの場合は、これが便利です。</span><span class="sxs-lookup"><span data-stu-id="8af0d-129">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="8af0d-130">Resolve メソッドは、<xref:System.ServiceModel.Discovery.ResolveCriteria> のインスタンスを受け取ります。このインスタンスは、解決するサービスのエンドポイント アドレス、解決操作の最大期間、および拡張のセットを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8af0d-130">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="8af0d-131">次の例は、<xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> メソッドを使用してサービスを解決する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8af0d-131">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="8af0d-132">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="8af0d-132">DynamicEndpoint</span></span>  

 <span data-ttu-id="8af0d-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> は標準エンドポイントです (詳細については、「 [標準エンドポイント](standard-endpoints.md)」を参照してください)。検出を実行し、一致するサービスを自動的に選択します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="8af0d-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> を作成して、検索するコントラクトおよび使用するバインディングを渡し、<xref:System.ServiceModel.Discovery.DynamicEndpoint> インスタンスを WCF クライアントに渡します。</span><span class="sxs-lookup"><span data-stu-id="8af0d-134">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="8af0d-135">次の例は、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を作成および使用して電卓サービスを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8af0d-135">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="8af0d-136">クライアントが開かれるたびに、探索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-136">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="8af0d-137">構成で定義されているエンドポイントは、 <xref:System.ServiceModel.Discovery.DynamicEndpoint> `kind ="dynamicEndpoint"` エンドポイント構成要素に属性を追加することによってにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8af0d-137">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="8af0d-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="8af0d-138">See also</span></span>

- [<span data-ttu-id="8af0d-139">スコープを使用した探索</span><span class="sxs-lookup"><span data-stu-id="8af0d-139">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="8af0d-140">Basic</span><span class="sxs-lookup"><span data-stu-id="8af0d-140">Basic</span></span>](../samples/basic-sample.md)
