---
description: 詳細については、ルーティングサービスを使用した Hello World に関するページを参照してください。
title: ルーティング サービスを使用した Hello World
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 1741c7d1f1e474864d66220fd160633997744876
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631971"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="1995c-103">ルーティング サービスを使用した Hello World</span><span class="sxs-lookup"><span data-stu-id="1995c-103">Hello World with the Routing Service</span></span>

<span data-ttu-id="1995c-104">このサンプルでは、Windows Communication Foundation (WCF) ルーティングサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="1995c-104">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="1995c-105">ルーティングサービスは、コンテンツベースのルーターをアプリケーションに簡単に含めることができる WCF コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1995c-105">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="1995c-106">このサンプルでは、ルーティングサービスを使用して通信するように、標準の WCF Calculator サンプルを適応させます。</span><span class="sxs-lookup"><span data-stu-id="1995c-106">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="1995c-107">このサンプルの電卓クライアントは、ルーターによって公開されるエンドポイントにメッセージを送信するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="1995c-107">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="1995c-108">ルーティング サービスは、送信されてきたすべてのメッセージを受け入れ、電卓サービスに対応するエンドポイントに転送するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="1995c-108">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="1995c-109">したがって、クライアントから送信されたメッセージはルーターで受信され、実際の電卓サービスに再ルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="1995c-109">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="1995c-110">電卓サービスからのメッセージはルーターに送り返され、ルーターから電卓クライアントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="1995c-110">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="1995c-111">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="1995c-111">To use this sample</span></span>

1. <span data-ttu-id="1995c-112">Visual Studio 2012 を使用して、HelloRoutingService を開きます。</span><span class="sxs-lookup"><span data-stu-id="1995c-112">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="1995c-113">F5 キーを押すか、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1995c-113">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1995c-114">F5 キーを押した場合は、電卓クライアントが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="1995c-114">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="1995c-115">Ctrl キーと Shift キーを押しながら B キーを押した (ビルドする) 場合は、次のアプリケーションを手動で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1995c-115">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="1995c-116">電卓クライアント (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="1995c-116">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="1995c-117">電卓サービス (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="1995c-117">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="1995c-118">ルーティング サービス (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="1995c-118">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="1995c-119">Enter キーを押してクライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="1995c-119">Press ENTER to start the client.</span></span>

     <span data-ttu-id="1995c-120">次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1995c-120">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="1995c-121">コードまたは App.Config で構成可能</span><span class="sxs-lookup"><span data-stu-id="1995c-121">Configurable via Code or App.Config</span></span>

 <span data-ttu-id="1995c-122">サンプルは、提供された時点では、App.config ファイルを使用してルーターの動作を定義するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="1995c-122">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="1995c-123">App.config ファイルの名前を別の名前に変更して認識されないようにし、ConfigureRouterViaCode() に対するメソッド呼び出しのコメントを解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="1995c-123">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="1995c-124">どちらの方法でも、ルーターの動作は同じになります。</span><span class="sxs-lookup"><span data-stu-id="1995c-124">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="1995c-125">シナリオ</span><span class="sxs-lookup"><span data-stu-id="1995c-125">Scenario</span></span>

 <span data-ttu-id="1995c-126">このサンプルでは、基本的なメッセージ ポンプとして機能するルーターを示します。</span><span class="sxs-lookup"><span data-stu-id="1995c-126">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="1995c-127">ルーティング サービスは、構成済みの一連の送信先エンドポイントに直接メッセージを渡すように構成された透過的なプロキシ ノードとして機能します。</span><span class="sxs-lookup"><span data-stu-id="1995c-127">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="1995c-128">実際のシナリオ</span><span class="sxs-lookup"><span data-stu-id="1995c-128">Real World Scenario</span></span>

 <span data-ttu-id="1995c-129">Contoso では、サービスの名前指定、アドレス指定、構成、およびセキュリティに関する柔軟性を高めるために、</span><span class="sxs-lookup"><span data-stu-id="1995c-129">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="1995c-130">基本的なメッセージ ポンプをサービスの前に配置して、それをエンドポイントとして公開しています。</span><span class="sxs-lookup"><span data-stu-id="1995c-130">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="1995c-131">これにより、実際のサービスの前にセキュリティが追加され、スケールアウトされたソリューションやサービスのバージョン管理を後で簡単に実装できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1995c-131">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1995c-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1995c-132">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1995c-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1995c-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1995c-134">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="1995c-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1995c-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1995c-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="1995c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="1995c-136">See also</span></span>

- <span data-ttu-id="1995c-137">[AppFabric のホストおよび永続化のサンプル](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1995c-137">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
