---
description: 詳細については、「WCF Discovery の概要」を参照してください。
title: WCF Discovery の概要
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: d6acfb86ce0961ea7fbfba7695bece067e3dcec2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779648"
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="58032-103">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="58032-103">WCF Discovery Overview</span></span>

<span data-ttu-id="58032-104">Discovery API は、WS-Discovery プロトコルを使用した Web サービスの動的公開と探索の統合プログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="58032-104">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="58032-105">これらの API は、サービスがサービス自体を公開し、クライアントが公開されたサービスを発見できるようにします。</span><span class="sxs-lookup"><span data-stu-id="58032-105">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="58032-106">サービスを探索可能にした後は、サービスでアナウンス メッセージを送信できるほか、探索要求のリッスンと応答もできるようになります。</span><span class="sxs-lookup"><span data-stu-id="58032-106">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="58032-107">探索可能なサービスは、ネットワークに接続されたことをアナウンスする Hello メッセージ、およびネットワークから切断されたことをアナウンスする Bye メッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="58032-107">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="58032-108">サービスを検索するために、クライアントは、サービス コントラクト型、キーワード、ネットワークのスコープなど、特定の条件が設定された `Probe` 要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="58032-108">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="58032-109">サービスはこの `Probe` 要求を受信し、条件に一致するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="58032-109">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="58032-110">サービスが条件に一致した場合は、サービスへの接続に必要な情報と併せて `ProbeMatch` メッセージをクライアントに送り返すことで応答します。</span><span class="sxs-lookup"><span data-stu-id="58032-110">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="58032-111">クライアントは `Resolve` 要求を送信することもできます。この要求では、エンドポイント アドレスが変更されている可能性があるサービスを発見できます。</span><span class="sxs-lookup"><span data-stu-id="58032-111">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="58032-112">条件に一致したサービスは、`Resolve` メッセージをクライアントに送り返すことで、`ResolveMatch` 要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="58032-112">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="58032-113">アドホック モードとマネージド モード</span><span class="sxs-lookup"><span data-stu-id="58032-113">Ad-Hoc and Managed Modes</span></span>  

 <span data-ttu-id="58032-114">Discovery API は、マネージドとアドホックという 2 種類のモードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="58032-114">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="58032-115">マネージド モードでは、使用可能なサービスについての情報を管理する探索プロキシと呼ばれる集中サーバーがあります。</span><span class="sxs-lookup"><span data-stu-id="58032-115">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="58032-116">探索プロキシには、さまざまな方法でサービスについての情報を設定できます。</span><span class="sxs-lookup"><span data-stu-id="58032-116">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="58032-117">たとえば、サービスから起動中にアナウンス メッセージを探索プロキシに送信することも、探索プロキシがデータベースや構成ファイルからデータを読み取って、使用可能なサービスを特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="58032-117">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="58032-118">探索プロキシへの情報の設定方法は、開発者が決定します。</span><span class="sxs-lookup"><span data-stu-id="58032-118">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="58032-119">クライアントは、探索プロキシを使用して、使用可能なサービスについての情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="58032-119">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="58032-120">クライアントは、サービスを検索するときに `Probe` メッセージを探索プロキシに送信します。探索プロキシは、認識しているサービスのうち、クライアントが検索しているサービスに一致するものがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="58032-120">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="58032-121">一致するものがあった場合、探索プロキシは `ProbeMatch` 応答をクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="58032-121">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="58032-122">クライアントは、プロキシから返されたサービスの情報を使用して、直接サービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="58032-122">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="58032-123">マネージド モードの基盤である最大の原則は、探索要求がユニキャストで 1 つの機構、つまり、探索プロキシに送信されることです。</span><span class="sxs-lookup"><span data-stu-id="58032-123">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="58032-124">.NET Framework には、開発者が独自のプロキシを作成できる主要コンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="58032-124">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="58032-125">クライアントとサービスは、次のような複数の方法でプロキシを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="58032-125">Clients and services can locate the proxy by multiple methods:</span></span>  
  
- <span data-ttu-id="58032-126">プロキシがアドホック メッセージに応答する。</span><span class="sxs-lookup"><span data-stu-id="58032-126">The proxy can respond to ad-hoc messages.</span></span>  
  
- <span data-ttu-id="58032-127">プロキシが起動中にアナウンス メッセージを送信する。</span><span class="sxs-lookup"><span data-stu-id="58032-127">The proxy can send an announcement message during start up.</span></span>  
  
- <span data-ttu-id="58032-128">特定の既知のエンドポイントを検索するように、クライアントとサービスを作成する。</span><span class="sxs-lookup"><span data-stu-id="58032-128">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="58032-129">アドホック モードには、集中サーバーはありません。</span><span class="sxs-lookup"><span data-stu-id="58032-129">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="58032-130">サービス アナウンスやクライアント要求など、すべての探索メッセージは、マルチキャストで送信されます。</span><span class="sxs-lookup"><span data-stu-id="58032-130">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="58032-131">既定では、.NET Framework に、UDP プロトコルを利用したアドホック探索のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58032-131">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="58032-132">たとえば、起動時に Hello アナウンスを送信するようにサービスが構成されている場合、サービスは、UDP プロトコルを使用して既知のマルチキャスト アドレスからアナウンスを送信します。</span><span class="sxs-lookup"><span data-stu-id="58032-132">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="58032-133">クライアントは、これらのアナウンスをアクティブにリッスンし、適宜処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-133">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="58032-134">クライアントが、ある特定のサービスを検索するための `Probe` メッセージを送信すると、このメッセージは、マルチキャスト プロトコルを使用してネットワーク上で送信されます。</span><span class="sxs-lookup"><span data-stu-id="58032-134">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="58032-135">要求を受信した各サービスは、`Probe` メッセージの条件に一致するかどうかを判断し、`ProbeMatch` メッセージに指定されている条件に一致する場合は、`Probe` メッセージを使用して直接クライアントに応答します。</span><span class="sxs-lookup"><span data-stu-id="58032-135">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="58032-136">WCF Discovery を使用する利点</span><span class="sxs-lookup"><span data-stu-id="58032-136">Benefits of Using WCF Discovery</span></span>  

 <span data-ttu-id="58032-137">WCF Discovery は WS-Discovery プロトコルを使用して実装されるため、WS-Discovery を実装するその他のクライアント、サービス、およびプロキシと相互運用可能です。</span><span class="sxs-lookup"><span data-stu-id="58032-137">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="58032-138">WCF Discovery は既存の WCF API を基盤にしているため、既存のサービスやクライアントに簡単に探索機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="58032-138">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="58032-139">サービスは、アプリケーション構成設定を使用して、簡単に探索可能にできます。</span><span class="sxs-lookup"><span data-stu-id="58032-139">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="58032-140">また、WCF Discovery では、ピア ネットワーク、名前付けオーバーレイ、HTTP など、その他のトランスポートでの探索プロトコルの使用もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="58032-140">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="58032-141">WCF Discovery は、探索プロキシが使用されるマネージド モードの運用をサポートします。</span><span class="sxs-lookup"><span data-stu-id="58032-141">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="58032-142">これにより、ネットワーク全体にマルチキャスト メッセージが送信されずに、探索プロキシに直接メッセージが送信されるため、ネットワーク トラフィックが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="58032-142">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="58032-143">WCF Discovery では、Web サービスをより柔軟に操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="58032-143">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="58032-144">たとえば、クライアントやサービスを再構成することなく、サービスのアドレスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="58032-144">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="58032-145">クライアントがサービスにアクセスする必要がある場合、`Probe` 要求により `Find` メッセージを発行すると、サービスの現在のアドレスがサービスから返されます。</span><span class="sxs-lookup"><span data-stu-id="58032-145">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="58032-146">WCF Discovery では、クライアントは、コントラクトの種類、バインド要素、名前空間、スコープ、キーワードやバージョン番号など、異なる条件を基に特定のサービスを検索できます。</span><span class="sxs-lookup"><span data-stu-id="58032-146">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="58032-147">WCF Discovery では、実行時および設計時にも探索が可能です。</span><span class="sxs-lookup"><span data-stu-id="58032-147">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="58032-148">アプリケーションに探索を追加することで、フォールト トレランスや自動構成など、その他のシナリオを実現することもできます。</span><span class="sxs-lookup"><span data-stu-id="58032-148">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="58032-149">サービスの公開</span><span class="sxs-lookup"><span data-stu-id="58032-149">Service Publication</span></span>  

 <span data-ttu-id="58032-150">サービスを探索可能にするには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> をサービス ホストに追加し、探索エンドポイントを追加して探索メッセージをリッスンする場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-150">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="58032-151">次のコード例は、自己ホスト型サービスを変更して探索可能にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="58032-151">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <span data-ttu-id="58032-152">サービスを探索可能にするには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> のインスタンスをサービスの説明に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-152">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="58032-153">探索要求をリッスンするサービスを指定するには、<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> のインスタンスをサービス ホストに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-153">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="58032-154">この例では、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> から派生した) を追加して、サービスが UDP マルチキャスト トランスポートを利用して探索要求をリッスンするように指定しています。</span><span class="sxs-lookup"><span data-stu-id="58032-154">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="58032-155">すべてのメッセージがマルチキャストで送信されるため、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を使用してアドホック探索が実行されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="58032-155">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="58032-156">告知</span><span class="sxs-lookup"><span data-stu-id="58032-156">Announcement</span></span>  

 <span data-ttu-id="58032-157">既定では、サービスを公開しても、アナウンス メッセージは送信されません。</span><span class="sxs-lookup"><span data-stu-id="58032-157">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="58032-158">アナウンス メッセージを送信するように、サービスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-158">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="58032-159">このため、探索メッセージのリッスンとは別に、サービスをアナウンスできるため、より柔軟にサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="58032-159">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="58032-160">サービス アナウンスは、探索プロキシまたはその他のサービス レジストリにサービスを登録するメカニズムとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="58032-160">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="58032-161">次のコード例は、UDP バインドを利用してアナウンス メッセージを送信するようにサービスを構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="58032-161">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a><span data-ttu-id="58032-162">サービス探索</span><span class="sxs-lookup"><span data-stu-id="58032-162">Service Discovery</span></span>  

 <span data-ttu-id="58032-163">クライアント アプリケーションは、<xref:System.ServiceModel.Discovery.DiscoveryClient> クラスを使用してサービスを検索できます。</span><span class="sxs-lookup"><span data-stu-id="58032-163">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="58032-164">開発者は、<xref:System.ServiceModel.Discovery.DiscoveryClient> メッセージまたは `Probe` メッセージの送信先を指定する探索エンドポイントに渡す `Resolve` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="58032-164">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="58032-165">クライアントは、次に、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> インスタンス内に検索条件を指定する <xref:System.ServiceModel.Discovery.FindCriteria> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="58032-165">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="58032-166">一致するサービスが見つかった場合、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> は <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="58032-166">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="58032-167">次のコードは、`Find` メソッドを呼び出して、検索されたサービスに接続する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="58032-167">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService())
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="58032-168">探索およびメッセージ レベルのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="58032-168">Discovery and Message Level Security</span></span>  

 <span data-ttu-id="58032-169">メッセージ レベルのセキュリティを使用する場合は、<xref:System.ServiceModel.EndpointIdentity> をサービスの探索エンドポイントに指定し、対応する <xref:System.ServiceModel.EndpointIdentity> をクライアントの探索エンドポイントに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-169">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> <span data-ttu-id="58032-170">メッセージレベルのセキュリティの詳細については、「 [メッセージセキュリティ](message-security-in-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58032-170">For more information about message level security, see [Message Security](message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="58032-171">探索および Web ホスト サービス</span><span class="sxs-lookup"><span data-stu-id="58032-171">Discovery and Web Hosted Services</span></span>  

 <span data-ttu-id="58032-172">WCF サービスが探索可能であるためには、このサービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-172">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="58032-173">IIS または WAS でホストされている WCF サービスは、IIS/WAS がサービスにバインドされているメッセージを受信するまで実行されないため、既定では探索できません。</span><span class="sxs-lookup"><span data-stu-id="58032-173">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="58032-174">Web ホスト サービスを探索可能にするには、次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="58032-174">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1. <span data-ttu-id="58032-175">Windows Server AppFabric の自動開始機能の使用</span><span class="sxs-lookup"><span data-stu-id="58032-175">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2. <span data-ttu-id="58032-176">サービスに代わって通信を行う探索プロキシの使用</span><span class="sxs-lookup"><span data-stu-id="58032-176">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="58032-177">Windows Server AppFabric には、メッセージを受信する前にサービスを開始できる自動開始機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="58032-177">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="58032-178">この自動開始セットで、IIS/WAS でホストされるサービスを探索できるように構成できます。</span><span class="sxs-lookup"><span data-stu-id="58032-178">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> <span data-ttu-id="58032-179">自動開始機能の詳細については、「 [Windows Server AppFabric 自動開始機能](/previous-versions/appfabric/ee677260(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58032-179">For more information about the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](/previous-versions/appfabric/ee677260(v=azure.10)).</span></span> <span data-ttu-id="58032-180">自動開始機能をオンにすると共に、探索サービスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-180">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> <span data-ttu-id="58032-181">詳細については、「[方法: プログラムによって検出機能を WCF サービスに追加](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)する」および「[構成ファイルで探索を構成](configuring-discovery-in-a-configuration-file.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58032-181">For more information, see [How to: Programmatically Add Discoverability to a WCF Service and Client](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="58032-182">探索プロキシはサービスが実行されていないときに WCF サービスの代わりに通信に使用できます。</span><span class="sxs-lookup"><span data-stu-id="58032-182">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="58032-183">このプロキシはプローブをリッスンするか、メッセージを解決して、クライアントに応答できます。</span><span class="sxs-lookup"><span data-stu-id="58032-183">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="58032-184">これで、クライアントはメッセージをサービスに直接送信できます。</span><span class="sxs-lookup"><span data-stu-id="58032-184">The client can then send messages directly to the service.</span></span> <span data-ttu-id="58032-185">クライアントがサービスにメッセージを送信する場合、インスタンス化されてメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="58032-185">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> <span data-ttu-id="58032-186">探索プロキシの実装の詳細については、「 [探索プロキシの実装](implementing-a-discovery-proxy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58032-186">For more information about implementing a discovery proxy see, [Implementing a Discovery Proxy](implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58032-187">WCF 検出を正常に機能させるには、すべての Nic (ネットワークインターフェイスコントローラー) に1つの IP アドレスのみを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58032-187">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
