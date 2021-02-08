---
description: 詳細については、「探索クライアントチャネルの使用」を参照してください。
title: 探索クライアント チャネルの使用
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: f83068c248ab8e2f1e2b3bfba3eb29fcf8aa20ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779661"
---
# <a name="using-the-discovery-client-channel"></a><span data-ttu-id="3e13e-103">探索クライアント チャネルの使用</span><span class="sxs-lookup"><span data-stu-id="3e13e-103">Using the Discovery Client Channel</span></span>

<span data-ttu-id="3e13e-104">WCF クライアント アプリケーションを記述するときには、呼び出すサービスのエンドポイント アドレスを知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e13e-104">When writing a WCF client application you need to know the endpoint address of the service you are calling.</span></span> <span data-ttu-id="3e13e-105">多くの場合、サービスのエンドポイント アドレスがわからなかったり、サービスのアドレスが時間の経過と共に変化したりします。</span><span class="sxs-lookup"><span data-stu-id="3e13e-105">In many situations the endpoint address of a service is not known in advance or the address of the service changes over time.</span></span> <span data-ttu-id="3e13e-106">探索クライアント チャネルでは、WCF クライアント アプリケーションを記述し、呼び出すサービスを示すと、クライアント チャネルが自動的にプローブ要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="3e13e-106">The Discovery Client Channel allows you to write a WCF client application, describe the service you want to call, and the client channel automatically sends a probe request.</span></span> <span data-ttu-id="3e13e-107">サービスが応答すると、探索クライアント チャネルは、プローブ応答からサービスのエンドポイント アドレスを受け取り、それを使用してサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3e13e-107">When a service responds, the discovery client channel retrieves the endpoint address for the service from the probe response and uses it to call the service.</span></span>  
  
## <a name="using-the-discovery-client-channel"></a><span data-ttu-id="3e13e-108">探索クライアント チャネルの使用</span><span class="sxs-lookup"><span data-stu-id="3e13e-108">Using the Discovery Client Channel</span></span>  

 <span data-ttu-id="3e13e-109">探索クライアント チャネルを使用するには、<xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> のインスタンスをクライアント チャネル スタックに追加します。</span><span class="sxs-lookup"><span data-stu-id="3e13e-109">To use the Discovery Client Channel, add an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your client channel stack.</span></span> <span data-ttu-id="3e13e-110">または、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を使用すると、まだ追加されていない場合は、<xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> が自動的にバインディングに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-110">Alternatively you can use the <xref:System.ServiceModel.Discovery.DynamicEndpoint> and a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is automatically added to your binding if not already present.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3e13e-111"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> は、クライアント チャネル スタックの最上位要素にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3e13e-111">It is recommended that the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is the top-most element on your client channel stack.</span></span> <span data-ttu-id="3e13e-112"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> の上に追加されたバインディング要素では、<xref:System.ServiceModel.ChannelFactory>、またはそれによって作成されるチャネルが、エンドポイント アドレスまたは `Via` アドレス (`CreateChannel` メソッドに渡されたアドレス) を使用しないようにする必要があります。これらには、正しいアドレスが格納されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3e13e-112">Any binding element that is added on top of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the <xref:System.ServiceModel.ChannelFactory> or channel it creates does not use the endpoint address or `Via` address (passed to the `CreateChannel` method) because they may not contain the correct address.</span></span>  
  
 <span data-ttu-id="3e13e-113"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> クラスには、2 つのパブリック プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3e13e-113">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> class contains two public properties:</span></span>  
  
1. <span data-ttu-id="3e13e-114">呼び出すサービスを示すのに使用する <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>。</span><span class="sxs-lookup"><span data-stu-id="3e13e-114"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, which is used to describe the service you want to call.</span></span>  
  
2. <span data-ttu-id="3e13e-115"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> 探索メッセージを送信する探索エンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e13e-115"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> which specifies the discovery endpoint to send discovery messages to.</span></span>  
  
 <span data-ttu-id="3e13e-116"><xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> プロパティでは、探しているサービス コントラクト、必要なスコープ URI、およびチャネルを開く最大試行回数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-116">The <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> property allows you to specify the service contract you are searching for, any required scope URIs, and the maximum number of time to attempt to open the channel.</span></span> <span data-ttu-id="3e13e-117">コントラクト型は、コンストラクターを呼び出すことによって指定され  <xref:System.ServiceModel.Discovery.FindCriteria> ます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-117">The contract type is specified by calling the constructor  <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span> <span data-ttu-id="3e13e-118">スコープ URI は <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> プロパティに追加できます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-118">Scope URIs can be added to the <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> property.</span></span> <span data-ttu-id="3e13e-119"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> プロパティでは、クライアントが接続を試行する結果の最大数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-119">The <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> property allows you to specify the maximum number of results to which the client tries to connect to.</span></span> <span data-ttu-id="3e13e-120">プローブ応答を受信すると、クライアントは、プローブ応答で取得したエンドポイント アドレスを使用してチャネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-120">When a probe response is received the client attempts to open the channel using the endpoint address from the probe response.</span></span> <span data-ttu-id="3e13e-121">例外が発生した場合、クライアントは次のプローブ応答に進み、必要に応じて、さらに応答の受信を待機します。</span><span class="sxs-lookup"><span data-stu-id="3e13e-121">If an exception occurs the client moves on to the next probe response, waiting for more responses to be received if necessary.</span></span> <span data-ttu-id="3e13e-122">チャネルが正常に開かれるか、または結果の最大数に達するまで、この処理が続行されます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-122">It continues to do this until the channel is successfully opened or the maximum number of results is reached.</span></span> <span data-ttu-id="3e13e-123">これらの設定の詳細については、「<xref:System.ServiceModel.Discovery.FindCriteria>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e13e-123">For more information about these settings, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>  
  
 <span data-ttu-id="3e13e-124"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> プロパティでは、使用する探索エンドポイントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-124">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> property allows you to specify the discovery endpoint to use.</span></span> <span data-ttu-id="3e13e-125">通常は <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ですが、任意の有効なエンドポイントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-125">Normally this is a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, but it can be any valid endpoint.</span></span>  
  
 <span data-ttu-id="3e13e-126">サービスとの通信に使用するバインディングを作成するときには、サービスとまったく同じバインディングを使用するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e13e-126">When you are creating the binding to use to communicate with the service, you must be careful to use the exact same binding as the service.</span></span> <span data-ttu-id="3e13e-127">唯一の相違点は、クライアント バインディングの場合は、<xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> がスタックの一番上にあることです。</span><span class="sxs-lookup"><span data-stu-id="3e13e-127">The only difference is the client binding has a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> on the top of the stack.</span></span> <span data-ttu-id="3e13e-128">サービスが、システムによって提供されるバインディングの 1 つを使用している場合は、新しい <xref:System.ServiceModel.Channels.CustomBinding> を作成し、システムによって提供されるバインディングを <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> コンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="3e13e-128">If service is using one of the system-provided bindings, create a new <xref:System.ServiceModel.Channels.CustomBinding> and pass in the system-provided binding to the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor.</span></span> <span data-ttu-id="3e13e-129">次に、<xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> を `Insert` プロパティで呼び出して、<xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> を追加できます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-129">Then you can add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> by calling `Insert` on the <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> property.</span></span>  
  
 <span data-ttu-id="3e13e-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> をバインディングに追加し、構成したら、WCF クライアント クラスのインスタンスを作成し、それを開いて、そのメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-130">Once you have added the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your binding and configured it, you can create an instance of the WCF client class, open it, and call its methods.</span></span> <span data-ttu-id="3e13e-131">次の例では、探索クライアント チャネルを使用して、`ICalculator` クラス (WCF の入門チュートリアルで使用するクラス) を実装し、その `Add` メソッドを呼び出す、WCF サービスを探索します。</span><span class="sxs-lookup"><span data-stu-id="3e13e-131">The following example uses the Discovery Client Channel to discover a WCF service that implements the `ICalculator` class (used in the Getting Started WCF tutorial) and calls its `Add` method.</span></span>  
  
```csharp
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a><span data-ttu-id="3e13e-132">セキュリティおよび探索クライアント チャネル</span><span class="sxs-lookup"><span data-stu-id="3e13e-132">Security and the Discovery Client Channel</span></span>  

 <span data-ttu-id="3e13e-133">探索クライアント チャネルの使用時には、2 つのエンドポイントが指定されます。</span><span class="sxs-lookup"><span data-stu-id="3e13e-133">When using the discovery client channel, two endpoints are being specified.</span></span> <span data-ttu-id="3e13e-134">1 つは探索メッセージ用に使用されるエンドポイント (通常は <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>) で、もう 1 つはアプリケーション エンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="3e13e-134">One is used for discovery messages, usually <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, and the other is the application endpoint.</span></span> <span data-ttu-id="3e13e-135">セキュリティで保護されたサービスを実装するときには、両方のエンドポイントを保護するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e13e-135">When implementing a secure service, care must be taken to secure both endpoints.</span></span> <span data-ttu-id="3e13e-136">セキュリティの詳細については、「 [サービスとクライアント](securing-services-and-clients.md)のセキュリティ保護」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e13e-136">For more information about security, see [Securing Services and Clients](securing-services-and-clients.md).</span></span>
