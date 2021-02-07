---
description: 詳細については、「ルーティングサービス」を参照してください。
title: ルーティング サービス
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 29fec780e6bc9266a8fe17d779ff0998e13e5c68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733256"
---
# <a name="routing-service"></a><span data-ttu-id="327c6-103">ルーティング サービス</span><span class="sxs-lookup"><span data-stu-id="327c6-103">Routing Service</span></span>

<span data-ttu-id="327c6-104">ルーティング サービスは、メッセージ ルーターとして機能する、汎用の SOAP 中継局です。</span><span class="sxs-lookup"><span data-stu-id="327c6-104">The Routing Service is a generic SOAP intermediary that acts as a message router.</span></span> <span data-ttu-id="327c6-105">ルーティング サービスの主要な機能は、メッセージのコンテンツに基づいてメッセージをルーティングする機能です。これにより、メッセージのヘッダーまたはメッセージ本文内に含まれる値に基づいて、メッセージをクライアント エンドポイントに転送できます。</span><span class="sxs-lookup"><span data-stu-id="327c6-105">The core functionality of the Routing Service is the ability to route messages based on message content, which allows a message to be forwarded to a client endpoint based on a value within the message itself, in either the header or the message body.</span></span>

<span data-ttu-id="327c6-106">は、 <xref:System.ServiceModel.Routing.RoutingService> 名前空間に Windows Communication Foundation (WCF) サービスとして実装され <xref:System.ServiceModel.Routing> ます。</span><span class="sxs-lookup"><span data-stu-id="327c6-106">The <xref:System.ServiceModel.Routing.RoutingService> is implemented as a Windows Communication Foundation (WCF) service in the <xref:System.ServiceModel.Routing> namespace.</span></span> <span data-ttu-id="327c6-107">ルーティング サービスは、メッセージを受信し、その内容に基づいて各メッセージを 1 つ以上のクライアント エンドポイントにルーティングする、1 つ以上のサービス エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="327c6-107">The Routing Service exposes one or more service endpoints that receive messages and then routes each message to one or more client endpoints based on the message content.</span></span> <span data-ttu-id="327c6-108">このサービスには、次の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="327c6-108">The service provides the following features:</span></span>

- <span data-ttu-id="327c6-109">コンテンツ ベースのルーティング</span><span class="sxs-lookup"><span data-stu-id="327c6-109">Content-based routing</span></span>

  - <span data-ttu-id="327c6-110">サービスの集計</span><span class="sxs-lookup"><span data-stu-id="327c6-110">Service aggregation</span></span>

  - <span data-ttu-id="327c6-111">サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="327c6-111">Service versioning</span></span>

  - <span data-ttu-id="327c6-112">優先順位によるルーティング</span><span class="sxs-lookup"><span data-stu-id="327c6-112">Priority routing</span></span>

  - <span data-ttu-id="327c6-113">動的構成</span><span class="sxs-lookup"><span data-stu-id="327c6-113">Dynamic configuration</span></span>

- <span data-ttu-id="327c6-114">プロトコル ブリッジ</span><span class="sxs-lookup"><span data-stu-id="327c6-114">Protocol bridging</span></span>

- <span data-ttu-id="327c6-115">SOAP 処理</span><span class="sxs-lookup"><span data-stu-id="327c6-115">SOAP processing</span></span>

- <span data-ttu-id="327c6-116">高度なエラー処理</span><span class="sxs-lookup"><span data-stu-id="327c6-116">Advanced error handling</span></span>

- <span data-ttu-id="327c6-117">バックアップ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="327c6-117">Backup endpoints</span></span>

<span data-ttu-id="327c6-118">上記の機能の 1 つ以上を実現する中間サービスを作成することもできますが、このような実装では、特定のシナリオまたはソリューションに制限され、新しいアプリケーションにすぐに適用できません。</span><span class="sxs-lookup"><span data-stu-id="327c6-118">While it is possible to create an intermediary service that accomplishes one or more of these goals, often such an implementation is tied to a specific scenario or solution and cannot be readily applied to new applications.</span></span>

<span data-ttu-id="327c6-119">ルーティングサービスは、WCF サービスおよびチャネルモデルと互換性があり、SOAP ベースのメッセージのコンテンツベースのルーティングを実行できる、動的に構成可能な汎用のプラグ可能な SOAP 中継局を提供します。</span><span class="sxs-lookup"><span data-stu-id="327c6-119">The Routing Service provides a generic, dynamically configurable, pluggable SOAP intermediary that is compatible with the WCF Service and Channel models and allows you to perform content-based routing of SOAP-based messages.</span></span>

> [!NOTE]
> <span data-ttu-id="327c6-120">ルーティング サービスは、現在 WCF REST サービスのルーティングをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="327c6-120">The Routing Service does not currently support routing of WCF REST services.</span></span>  <span data-ttu-id="327c6-121">REST 呼び出しをルーティングするに <xref:System.Web.Routing> は、または [アプリケーション要求ルーティング](https://go.microsoft.com/fwlink/?LinkId=164589)を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="327c6-121">To route REST calls, consider using <xref:System.Web.Routing> or [Application Request Routing](https://go.microsoft.com/fwlink/?LinkId=164589).</span></span>

## <a name="content-based-routing"></a><span data-ttu-id="327c6-122">コンテンツ ベースのルーティング</span><span class="sxs-lookup"><span data-stu-id="327c6-122">Content-Based Routing</span></span>

<span data-ttu-id="327c6-123">コンテンツ ベースのルーティングは、メッセージに含まれている 1 つ以上の値に基づいて、メッセージをルーティングする機能です。</span><span class="sxs-lookup"><span data-stu-id="327c6-123">Content-based routing is the ability to route a message based on one or more values contained within the message.</span></span> <span data-ttu-id="327c6-124">ルーティング サービスでは、各メッセージを確認し、メッセージの内容と開発者が作成したルーティング ロジックに基づいて、送信先エンドポイントにメッセージをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="327c6-124">The Routing Service inspects each message and routes it to the destination endpoint based on the message contents and the routing logic you create.</span></span> <span data-ttu-id="327c6-125">コンテンツ ベースのルーティングは、サービス集計、サービスのバージョン管理、および優先度ルーティングの基礎になります。</span><span class="sxs-lookup"><span data-stu-id="327c6-125">Content-based routing provides the basis for service aggregation, service versioning, and priority routing.</span></span>

<span data-ttu-id="327c6-126">コンテンツ ベースのルーティングを実装するために、ルーティング サービスは <xref:System.ServiceModel.Dispatcher.MessageFilter> 実装に依存しています。これらの実装は、ルーティングするメッセージ内の特定の値を照合するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="327c6-126">To implement content-based routing, the Routing Service relies on <xref:System.ServiceModel.Dispatcher.MessageFilter> implementations that are used to match specific values within the messages to be routed.</span></span> <span data-ttu-id="327c6-127">**Messagefilter** がメッセージに一致する場合、メッセージは **messagefilter** に関連付けられている送信先エンドポイントにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="327c6-127">If a **MessageFilter** matches a message, the message is routed to the destination endpoint associated with the **MessageFilter**.</span></span>  <span data-ttu-id="327c6-128">メッセージ フィルターはフィルター テーブル (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) にグループ化されて、複雑なルーティング ロジックを構築します。</span><span class="sxs-lookup"><span data-stu-id="327c6-128">Message filters are grouped together into filter tables (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) to construct complex routing logic.</span></span> <span data-ttu-id="327c6-129">たとえば、フィルター テーブルに 5 つの相互に排他的なメッセージ フィルターが含まれ、それによって、5 つの送信先エンドポイントのうちの 1 つだけにメッセージがルーティングされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="327c6-129">For example, a filter table might contain five mutually exclusive message filters that cause messages to be routed to only one of the five destination endpoints.</span></span>

<span data-ttu-id="327c6-130">ルーティング サービスを使用すると、コンテンツ ベースのルーティングの実行に使用するロジックを構成できるほか、ルーティング ロジックを実行時に動的に更新できます。</span><span class="sxs-lookup"><span data-stu-id="327c6-130">The Routing Service allows you to configure the logic that is used to perform content-based routing, as well as dynamically update the routing logic at run time.</span></span>

<span data-ttu-id="327c6-131">メッセージ フィルターをフィルター テーブルにグループ化することで、ルーティング ロジックを構築し、次のような複数のルーティング シナリオを処理できます。</span><span class="sxs-lookup"><span data-stu-id="327c6-131">Through the grouping of message filters into filter tables, routing logic can be constructed that allows you to handle multiple routing scenarios such as:</span></span>

- <span data-ttu-id="327c6-132">サービスの集計</span><span class="sxs-lookup"><span data-stu-id="327c6-132">Service aggregation</span></span>

- <span data-ttu-id="327c6-133">サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="327c6-133">Service versioning</span></span>

- <span data-ttu-id="327c6-134">優先順位によるルーティング</span><span class="sxs-lookup"><span data-stu-id="327c6-134">Priority routing</span></span>

- <span data-ttu-id="327c6-135">動的構成</span><span class="sxs-lookup"><span data-stu-id="327c6-135">Dynamic configuration</span></span>

<span data-ttu-id="327c6-136">メッセージフィルターとフィルターテーブルの詳細については、「 [ルーティングの概要](routing-introduction.md) 」と「 [メッセージフィルター](message-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="327c6-136">For more information about message filters and filter tables, see [Routing Introduction](routing-introduction.md) and [Message Filters](message-filters.md).</span></span>

### <a name="service-aggregation"></a><span data-ttu-id="327c6-137">サービスの集計</span><span class="sxs-lookup"><span data-stu-id="327c6-137">Service Aggregation</span></span>

<span data-ttu-id="327c6-138">コンテンツ ベースのルーティングを使用することで、外部のクライアント アプリケーションからメッセージを受信する 1 つのエンドポイントを公開し、メッセージ内の値に基づいて、各メッセージを適切な内部エンドポイントにルーティングできます。</span><span class="sxs-lookup"><span data-stu-id="327c6-138">By using content-based routing, you can expose one endpoint that receives messages from external client applications and then routes each message to the appropriate internal endpoint based on a value within the message.</span></span> <span data-ttu-id="327c6-139">これは、さまざまなバックエンド アプリケーションに対して単一のエンドポイントを提供する場合だけでなく、アプリケーションをさまざまなサービスにファクタリングしているときに単一のアプリケーション エンドポイントを顧客に提供する場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="327c6-139">This is useful to offer one specific endpoint for a variety of back-end applications, and also to present one application endpoint to customers while factoring your application into a variety of services.</span></span>

### <a name="service-versioning"></a><span data-ttu-id="327c6-140">サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="327c6-140">Service Versioning</span></span>

<span data-ttu-id="327c6-141">ソリューションを新しいバージョンに移行するときに、既存の顧客に対応するために、古いバージョンを同時に維持する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="327c6-141">When migrating to a new version of your solution, you may have to maintain the old version in parallel to serve existing customers.</span></span> <span data-ttu-id="327c6-142">このような場合の多くでは、新しいバージョンに接続するクライアントが、ソリューションとの通信時に別のアドレスを使用することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="327c6-142">Often this requires that clients connecting to the newer version must use a different address when communicating with the solution.</span></span> <span data-ttu-id="327c6-143">ルーティング サービスを使用すると、メッセージに含まれるバージョン固有の情報に基づいて、適切なソリューションにメッセージをルーティングすることで、ソリューションの両方のバージョンに対応する単一のサービス エンドポイントを公開できます。</span><span class="sxs-lookup"><span data-stu-id="327c6-143">The Routing Service allows you to expose one service endpoint that serves both versions of your solution by routing messages to the appropriate solution based on version-specific information contained in the message.</span></span> <span data-ttu-id="327c6-144">このような実装の例については、「 [方法: サービスのバージョン管理](how-to-service-versioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="327c6-144">For an example of such an implementation see [How To: Service Versioning](how-to-service-versioning.md).</span></span>

### <a name="priority-routing"></a><span data-ttu-id="327c6-145">優先度ルーティング</span><span class="sxs-lookup"><span data-stu-id="327c6-145">Priority Routing</span></span>

<span data-ttu-id="327c6-146">サービスを複数のクライアントに提供するときに、パートナーとサービス レベル アグリーメント (SLA) を結び、それらのパートナーのデータをすべて、その他のクライアントのデータとは別に処理するように規定している場合があります。</span><span class="sxs-lookup"><span data-stu-id="327c6-146">When providing a service for multiple clients, you may have a service level agreement (SLA) with some partners that requires all data from these partners to be processed separately from that of other clients.</span></span> <span data-ttu-id="327c6-147">メッセージに含まれる顧客固有の情報を検索するフィルターを使用すると、特定のパートナーから送られたメッセージを、各パートナーの SLA 要件に合わせて作成されたエンドポイントに容易にルーティングできます。</span><span class="sxs-lookup"><span data-stu-id="327c6-147">By using a filter that looks for customer-specific information contained in the message, you can easily route messages from specific partners to an endpoint that has been created to meet their SLA requirements.</span></span>

## <a name="dynamic-configuration"></a><span data-ttu-id="327c6-148">動的構成</span><span class="sxs-lookup"><span data-stu-id="327c6-148">Dynamic Configuration</span></span>

<span data-ttu-id="327c6-149">サービスを中断させずにメッセージを処理する必要があるミッション クリティカルなシステムをサポートするには、システム内のコンポーネントの構成を実行時に変更できることが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="327c6-149">To support mission-critical systems, where messages must be processed without any service interruptions, it is vital that you be able to modify the configuration of components within the system at run time.</span></span> <span data-ttu-id="327c6-150">このニーズを満たすために、ルーティング サービスでは <xref:System.ServiceModel.IExtension%601> 実装が提供されています。これは、実行時にルーティング サービス構成を動的に更新できるようにする <xref:System.ServiceModel.Routing.RoutingExtension> です。</span><span class="sxs-lookup"><span data-stu-id="327c6-150">To support this need, the Routing Service provides an <xref:System.ServiceModel.IExtension%601> implementation, the <xref:System.ServiceModel.Routing.RoutingExtension>, which allows dynamic updating of the Routing Service configuration at run time.</span></span>

<span data-ttu-id="327c6-151">ルーティングサービスの動的構成の詳細については、「 [ルーティングの概要](routing-introduction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="327c6-151">For more information about dynamic configuration of the Routing Service, see [Routing Introduction](routing-introduction.md).</span></span>

## <a name="protocol-bridging"></a><span data-ttu-id="327c6-152">プロトコル ブリッジ</span><span class="sxs-lookup"><span data-stu-id="327c6-152">Protocol Bridging</span></span>

<span data-ttu-id="327c6-153">中継局シナリオの課題の 1 つは、内部エンドポイントとメッセージの送信先エンドポイントのトランスポートまたは SOAP バージョンの要件が異なる場合があることです。</span><span class="sxs-lookup"><span data-stu-id="327c6-153">One of the challenges in intermediary scenarios is that the internal endpoints may have different transport or SOAP version requirements than the endpoint that messages are received on.</span></span> <span data-ttu-id="327c6-154">このシナリオをサポートするために、ルーティング サービスでは、SOAP メッセージを送信先エンドポイントが必要とする <xref:System.ServiceModel.Channels.MessageVersion> に合わせて処理するなど、プロトコル間をブリッジできます。</span><span class="sxs-lookup"><span data-stu-id="327c6-154">To support this scenario, the Routing Service can bridge protocols, including processing the SOAP message to the <xref:System.ServiceModel.Channels.MessageVersion> required by the destination endpoint(s).</span></span> <span data-ttu-id="327c6-155">これを利用して、内部の通信と外部の通信に別々のプロトコルを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="327c6-155">In this way, one protocol can be used for internal communication, while another can be used for external communication.</span></span>

<span data-ttu-id="327c6-156">異なるトランスポートを持つエンドポイント間でのメッセージのルーティングをサポートするために、ルーティング サービスでは、サービスが複数の異なるプロトコルをブリッジできるようにする、システム指定のバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="327c6-156">To support the routing of messages between endpoints with different transports, the Routing Service uses system-provided bindings that enable the service to bridge dissimilar protocols.</span></span> <span data-ttu-id="327c6-157">この処理は、ルーティング サービスが公開するサービス エンドポイントで、メッセージのルーティング先のクライアント エンドポイントとは異なるプロトコルが使用されると、自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="327c6-157">This occurs automatically when the service endpoint exposed by the Routing Service uses a different protocol than the client endpoints that messages are routed to.</span></span>

## <a name="soap-processing"></a><span data-ttu-id="327c6-158">SOAP 処理</span><span class="sxs-lookup"><span data-stu-id="327c6-158">SOAP Processing</span></span>

<span data-ttu-id="327c6-159">一般的なルーティング要件は、異なる SOAP 要件を持つエンドポイント間でメッセージをルーティングできることです。</span><span class="sxs-lookup"><span data-stu-id="327c6-159">A common routing requirement is the ability to route messages between endpoints with differing SOAP requirements.</span></span> <span data-ttu-id="327c6-160">この要件をサポートするために、ルーティングサービスは、 <xref:System.ServiceModel.Routing.SoapProcessingBehavior> メッセージがルーティングされる前に、送信先エンドポイントの要件を満たす新しい **MessageVersion** を自動的に作成するを提供します。</span><span class="sxs-lookup"><span data-stu-id="327c6-160">To support this requirement, the Routing Service provides a <xref:System.ServiceModel.Routing.SoapProcessingBehavior> that automatically creates a new **MessageVersion** that meets the requirements of the destination endpoint before the message is routed to it.</span></span> <span data-ttu-id="327c6-161">また、この動作により、応答メッセージを要求元のクライアントアプリケーションに返す前に、応答メッセージの新しい **MessageVersion** が作成され、応答の **MessageVersion** が元の要求のものと一致するようになります。</span><span class="sxs-lookup"><span data-stu-id="327c6-161">This behavior also creates a new **MessageVersion** for any response message before returning it to the requesting client application, to ensure that the **MessageVersion** of the response matches that of the original request.</span></span>

<span data-ttu-id="327c6-162">SOAP 処理の詳細については、「 [ルーティングの概要](routing-introduction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="327c6-162">For more information about SOAP processing, see [Routing Introduction](routing-introduction.md).</span></span>

## <a name="error-handling"></a><span data-ttu-id="327c6-163">エラー処理</span><span class="sxs-lookup"><span data-stu-id="327c6-163">Error Handling</span></span>

<span data-ttu-id="327c6-164">システムを構成する分散サービスがネットワーク通信に依存する場合は、システム内の通信が、一時的なネットワーク障害に対応可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="327c6-164">In a system composed of distributed services that rely on network communications, it is important to ensure that communications within your system are resistant to transient network failures.</span></span>  <span data-ttu-id="327c6-165">ルーティング サービスはエラー処理を実装しており、これによって、サービスの停止を招く可能性がある多くの通信障害を処理できます。</span><span class="sxs-lookup"><span data-stu-id="327c6-165">The Routing Service implements error handling that allows you to handle many communication failure scenarios that might otherwise result in a service outage.</span></span>

<span data-ttu-id="327c6-166">ルーティング サービスがメッセージを送信している間に <xref:System.ServiceModel.CommunicationException> が発生した場合は、エラー処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="327c6-166">If the Routing Service encounters a <xref:System.ServiceModel.CommunicationException> while attempting to send a message, error handling will take place.</span></span>  <span data-ttu-id="327c6-167">これらの例外は、一般的に、<xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException>、<xref:System.ServiceModel.CommunicationObjectFaultedException> など、定義されているクライアント エンドポイントとの通信を試みている間に問題が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="327c6-167">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span>  <span data-ttu-id="327c6-168">また、エラー処理コードは、 **TimeoutException** が発生したときに送信を試行します。これは、 **CommunicationException** から派生していないもう1つの一般的な例外です。</span><span class="sxs-lookup"><span data-stu-id="327c6-168">The error-handling code will also catch and attempt to retry sending when a **TimeoutException** occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="327c6-169">エラー処理の詳細については、「 [ルーティングの概要](routing-introduction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="327c6-169">For more information about error handling, see [Routing Introduction](routing-introduction.md).</span></span>

## <a name="backup-endpoints"></a><span data-ttu-id="327c6-170">バックアップ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="327c6-170">Backup Endpoints</span></span>

<span data-ttu-id="327c6-171">フィルター テーブル内の各フィルター定義と関連付けられる送信先クライアント エンドポイントに加えて、転送エラーが発生した場合にメッセージをルーティングする、バックアップ エンドポイントのリストも作成できます。</span><span class="sxs-lookup"><span data-stu-id="327c6-171">In addition to the destination client endpoints associated with each filter definition in the filter table, you can also create a list of backup endpoints that the message will be routed to in the event of a transmission failure.</span></span> <span data-ttu-id="327c6-172">エラーが発生した場合に、フィルター エントリのバックアップ リストが定義されていると、ルーティング サービスにより、そのリストに定義されている最初のエンドポイントにメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="327c6-172">If an error occurs and a backup list is defined for the filter entry, the Routing Service will attempt to send the message to the first endpoint defined in the list.</span></span> <span data-ttu-id="327c6-173">この送信に失敗した場合は、送信に成功する、送信失敗に関連しないエラーが返される、またはバックアップ リスト内のすべてのエンドポイントで送信エラーが返されるまで、次のエンドポイントへの送信が試みられます。</span><span class="sxs-lookup"><span data-stu-id="327c6-173">If this transmission attempt fails, the service will try the next endpoint, and continue this process until the transmission attempt succeeds, returns a non-transmission related error, or all endpoints in the backup list have returned a transmission error.</span></span>

<span data-ttu-id="327c6-174">バックアップエンドポイントの詳細については、「 [ルーティングの概要](routing-introduction.md) 」と「 [メッセージフィルター](message-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="327c6-174">For more information about backup endpoints, see [Routing Introduction](routing-introduction.md) and [Message Filters](message-filters.md).</span></span>

## <a name="streaming"></a><span data-ttu-id="327c6-175">ストリーミング</span><span class="sxs-lookup"><span data-stu-id="327c6-175">Streaming</span></span>

<span data-ttu-id="327c6-176">バインディングがストリーミングをサポートするように設定すると、ルーティング サービスはメッセージを正常にストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="327c6-176">The routing service can successfully stream messages if you set the binding to support streaming.</span></span>  <span data-ttu-id="327c6-177">ただし、メッセージのバッファーが必要となる可能性のある条件がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="327c6-177">However, there are some conditions under which messages may need to buffered:</span></span>

- <span data-ttu-id="327c6-178">マルチキャスト (追加のメッセージ コピーを作成するためのバッファー)</span><span class="sxs-lookup"><span data-stu-id="327c6-178">Multicast (buffer to create additional message copies)</span></span>

- <span data-ttu-id="327c6-179">フェールオーバー (メッセージがバックアップに送信される必要がある場合のバッファー)</span><span class="sxs-lookup"><span data-stu-id="327c6-179">Failover (buffer in case the message needs to be sent to a backup)</span></span>

- <span data-ttu-id="327c6-180">System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly は false です (フィルターが本文を検査できるように MessageBuffer と共に MessageFilterTable を示すバッファー)</span><span class="sxs-lookup"><span data-stu-id="327c6-180">System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly is false (buffer to present the MessageFilterTable with a MessageBuffer so that filters can inspect the body)</span></span>

- <span data-ttu-id="327c6-181">動的構成</span><span class="sxs-lookup"><span data-stu-id="327c6-181">Dynamic configuration</span></span>

## <a name="see-also"></a><span data-ttu-id="327c6-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="327c6-182">See also</span></span>

- [<span data-ttu-id="327c6-183">ルーティングの概要</span><span class="sxs-lookup"><span data-stu-id="327c6-183">Routing Introduction</span></span>](routing-introduction.md)
- [<span data-ttu-id="327c6-184">ルーティング コントラクト</span><span class="sxs-lookup"><span data-stu-id="327c6-184">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="327c6-185">メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="327c6-185">Message Filters</span></span>](message-filters.md)
