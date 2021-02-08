---
description: '詳細情報: 探索のアナウンスとアナウンスクライアント'
title: 探索アナウンスとアナウンス クライアント
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 2076b4dbdc57bd3de47fccdb4a51ef9e6fc48366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802971"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="dc8b2-103">探索アナウンスとアナウンス クライアント</span><span class="sxs-lookup"><span data-stu-id="dc8b2-103">Discovery Announcements and Announcement Client</span></span>

<span data-ttu-id="dc8b2-104">WCF 検出機能を使用すると、コンポーネントはその可用性をアナウンスできます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-104">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="dc8b2-105">そのように構成されている場合、サービスは Hello アナウンスと Bye アナウンスを送信します。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-105">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="dc8b2-106">クライアントまたはその他のコンポーネントは、それらのアナウンス メッセージをリッスンして、対応します。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-106">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="dc8b2-107">これにより、クライアントは別の手段でサービスを認識します。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-107">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="dc8b2-108">アナウンス機能にはいくつかの用途があります。たとえば、サービスがネットワークに頻繁に出入りする場合は、サービスを検索するよりも、アナウンスを利用する方が効果的です。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-108">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="dc8b2-109">この方法を使用すると、ネットワーク トラフィックが減少し、クライアントは、アナウンスを受信するとすぐに、そのサービスが存在するかどうかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-109">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>

## <a name="discovery-announcements"></a><span data-ttu-id="dc8b2-110">探索アナウンス</span><span class="sxs-lookup"><span data-stu-id="dc8b2-110">Discovery Announcements</span></span>

<span data-ttu-id="dc8b2-111">アナウンスが構成されたサービスがネットワークに参加し、探索可能になると、そのサービスは、リッスンしているクライアントにそのサービスの可用性をアナウンスする Hello メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-111">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="dc8b2-112">このメッセージには、サービスのコントラクト、エンドポイント アドレス、および関連付けられたスコープなど、探索関連の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-112">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="dc8b2-113">アナウンス メッセージを送信する先を <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> クラスで指定できます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-113">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="dc8b2-114">アナウンス エンドポイントが <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> の場合、Hello および Bye はマルチキャストです。また、アナウンス エンドポイントがユニキャストの場合、メッセージは指定されたエンドポイントに直接送信されます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-114">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="dc8b2-115">アナウンスは、サービス ホストが開いたときと閉じたときに送信されます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-115">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="dc8b2-116">これらの呼び出しが正常に完了しない場合は、アナウンスメッセージが送信されない可能性があります。たとえば、サービスでエラーが生じた場合、Bye アナウンスメッセージは送信されません。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-116">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>

> [!TIP]
> <span data-ttu-id="dc8b2-117">アナウンス機能をカスタマイズして、選択したタイミングでアナウンスを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-117">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="dc8b2-118">では、<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> および <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> が標準エンドポイントとして定義されているため、サービスとクライアントが簡単に Hello アナウンスと Bye アナウンスを送信できます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-118">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>

### <a name="announcements-on-the-service"></a><span data-ttu-id="dc8b2-119">サービスのアナウンス</span><span class="sxs-lookup"><span data-stu-id="dc8b2-119">Announcements on the Service</span></span>

<span data-ttu-id="dc8b2-120">アナウンスを送信するようにサービスを構成するには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> をアナウンス エンドポイントと共に追加します。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-120">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="dc8b2-121">次の例は、この動作をプログラムでサービス ホストに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-121">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="dc8b2-122">この例では、アナウンスが、その標準エンドポイントで指定される場所へのマルチキャストであることを暗黙で示す `UdpAnnouncementEndpoint` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-122">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

<span data-ttu-id="dc8b2-123">この動作は、次の例に示すように、構成ファイルで構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-123">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>

```xml
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="dc8b2-124">前の例では、サービスが自動的にアナウンス メッセージを送信するように構成します。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-124">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="dc8b2-125"><xref:System.ServiceModel.Discovery.AnnouncementClient> クラスを使用して、アナウンス メッセージを明示的に送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-125">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>

### <a name="announcements-on-the-client"></a><span data-ttu-id="dc8b2-126">クライアントのアナウンス</span><span class="sxs-lookup"><span data-stu-id="dc8b2-126">Announcements on the Client</span></span>

<span data-ttu-id="dc8b2-127">クライアント アプリケーションは、アナウンス サービスをホストして Hello メッセージと Bye メッセージに応答し、<xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> イベントと <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> イベントを定期受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-127">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="dc8b2-128">次の例は、その方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-128">The following example shows how to do this.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;

// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();

    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}
```

<span data-ttu-id="dc8b2-129">Hello メッセージまたは Bye メッセージを受信したら、次の例に示すように、<xref:System.ServiceModel.Discovery.AnnouncementEventArgs> を介してエンドポイント探索メタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="dc8b2-129">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}
```
