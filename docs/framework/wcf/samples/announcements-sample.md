---
description: '詳細情報: アナウンスのサンプル'
title: アナウンスのサンプル
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 076efed31f862f6de68e924446528d682a62824a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778946"
---
# <a name="announcements-sample"></a><span data-ttu-id="17c4b-103">アナウンスのサンプル</span><span class="sxs-lookup"><span data-stu-id="17c4b-103">Announcements Sample</span></span>

<span data-ttu-id="17c4b-104">このサンプルでは、探索機能のアナウンス機能を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-104">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="17c4b-105">アナウンス機能を使用すると、サービスに関するメタデータを含むアナウンス メッセージをサービスから送信できます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-105">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="17c4b-106">既定では、サービスが開始されたときに Hello アナウンスが送信され、サービスがシャットダウンされたときに Bye アナウンスが送信されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-106">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="17c4b-107">これらのアナウンスは、マルチキャストすることも、Point-to-Point 送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-107">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="17c4b-108">このサンプルは、2 つのプロジェクト (サービスとクライアント) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-108">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="17c4b-109">サービス</span><span class="sxs-lookup"><span data-stu-id="17c4b-109">Service</span></span>

<span data-ttu-id="17c4b-110">このプロジェクトには、自己ホスト型の電卓サービスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="17c4b-110">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="17c4b-111">`Main` メソッドでは、サービス ホストが作成され、それにサービス エンドポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-111">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="17c4b-112">次に、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-112">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="17c4b-113">アナウンスを有効にする場合は、アナウンス エンドポイントを <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17c4b-113">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="17c4b-114">この場合、UDP マルチキャストを使用して、標準エンドポイントをアナウンス エンドポイントとして追加します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-114">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="17c4b-115">これにより、既知の UDP アドレスからアナウンスがブロードキャストされます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-115">This broadcasts the announcements over a well-known UDP address.</span></span>

```csharp
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);

     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();

     // Announce the availability of the service over UDP multicast
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());

    // Make the service discoverable over UDP multicast.
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());
    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="17c4b-116">クライアント</span><span class="sxs-lookup"><span data-stu-id="17c4b-116">Client</span></span>

<span data-ttu-id="17c4b-117">このプロジェクトでは、クライアントが <xref:System.ServiceModel.Discovery.AnnouncementService> をホストすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="17c4b-117">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="17c4b-118">また、2 つのデリゲートがイベントに登録されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-118">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="17c4b-119">これらのイベントにより、オンラインおよびオフラインのアナウンスを受信したときのクライアントの処理が決定されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-119">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="17c4b-120">`OnOnlineEvent` メソッドと `OnOfflineEvent` メソッドはそれぞれ、Hello アナウンス メッセージと Bye アナウンス メッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-120">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="17c4b-121">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="17c4b-121">To use this sample</span></span>

1. <span data-ttu-id="17c4b-122">このサンプルでは HTTP エンドポイントを使用します。このサンプルを実行するには、適切な URL ACL を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17c4b-122">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="17c4b-123">詳細については、「 [HTTP および HTTPS の構成](../feature-details/configuring-http-and-https.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17c4b-123">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="17c4b-124">管理特権で次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-124">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="17c4b-125">そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="17c4b-125">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="17c4b-126">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="17c4b-126">Build the solution.</span></span>

3. <span data-ttu-id="17c4b-127">client.exe アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-127">Run the client.exe application.</span></span>

4. <span data-ttu-id="17c4b-128">service.exe アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-128">Run the service.exe application.</span></span> <span data-ttu-id="17c4b-129">クライアントは、オンライン アナウンスを受信します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-129">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="17c4b-130">service.exe アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-130">Close the service.exe application.</span></span> <span data-ttu-id="17c4b-131">クライアントは、オフライン アナウンスを受信します。</span><span class="sxs-lookup"><span data-stu-id="17c4b-131">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17c4b-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="17c4b-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="17c4b-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="17c4b-133">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="17c4b-134">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="17c4b-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="17c4b-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="17c4b-135">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
