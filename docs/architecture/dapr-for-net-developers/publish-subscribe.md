---
title: Dapr publish & subscribe ビルディングブロック
description: Dapr 発行 & サブスクライブのビルドブロックとその適用方法の説明
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 4cb249bafc8241eb54153be2605c33d0a3adb619
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604685"
---
# <a name="the-dapr-publish--subscribe-building-block"></a><span data-ttu-id="bd273-103">Dapr publish & subscribe ビルディングブロック</span><span class="sxs-lookup"><span data-stu-id="bd273-103">The Dapr publish & subscribe building block</span></span>

<span data-ttu-id="bd273-104">[パブリッシュ/サブスクライブパターン](/azure/architecture/patterns/publisher-subscriber)(多くの場合、"pub/sub" と呼ばれます) は、広く知られている、広く使用されているメッセージングパターンです。</span><span class="sxs-lookup"><span data-stu-id="bd273-104">The [Publish-Subscribe pattern](/azure/architecture/patterns/publisher-subscriber) (often referred to as "pub/sub") is a well-known and widely used messaging pattern.</span></span> <span data-ttu-id="bd273-105">通常、設計者は分散アプリケーションでこれを採用しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-105">Architects commonly embrace it in distributed applications.</span></span> <span data-ttu-id="bd273-106">ただし、実装するのは複雑な場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-106">However, the plumbing to implement it can be complex.</span></span> <span data-ttu-id="bd273-107">多くの場合、さまざまなメッセージング製品での特徴の違いは微妙です。</span><span class="sxs-lookup"><span data-stu-id="bd273-107">There are often subtle feature differences across different messaging products.</span></span> <span data-ttu-id="bd273-108">Dapr は、pub/sub 機能の実装を大幅に簡略化するビルディングブロックを提供します。</span><span class="sxs-lookup"><span data-stu-id="bd273-108">Dapr offers a building block that significantly simplifies implementing pub/sub functionality.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="bd273-109">解決方法</span><span class="sxs-lookup"><span data-stu-id="bd273-109">What it solves</span></span>

<span data-ttu-id="bd273-110">Publish-Subscribe パターンの主な利点は疎 **結合** です。これは、 [一時的な分離](/azure/architecture/guide/technology-choices/messaging#decoupling)と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="bd273-110">The primary advantage of the Publish-Subscribe pattern is **loose coupling**, sometimes referred to as [temporal decoupling](/azure/architecture/guide/technology-choices/messaging#decoupling).</span></span> <span data-ttu-id="bd273-111">このパターンは、メッセージ ( **パブリッシャー**) を使用するサービス ( **サブスクライバー**) からメッセージを送信するサービスを分離します。</span><span class="sxs-lookup"><span data-stu-id="bd273-111">The pattern decouples services that send messages (the **publishers**) from services that consume messages (the **subscribers**).</span></span> <span data-ttu-id="bd273-112">パブリッシャーとサブスクライバーはどちらも互いを認識していません。どちらも、メッセージを配信する集中 **メッセージブローカー** に依存しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-112">Both publishers and subscribers are unaware of each other - both are dependent on a centralized **message broker** that distributes the messages.</span></span>

<span data-ttu-id="bd273-113">図7-1 は、pub/sub パターンの高レベルアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-113">Figure 7-1 shows the high-level architecture of the pub/sub pattern.</span></span>

![Pub/sub パターン](./media/publish-subscribe/pub-sub-pattern.png)

<span data-ttu-id="bd273-115">**図 7-1**。</span><span class="sxs-lookup"><span data-stu-id="bd273-115">**Figure 7-1**.</span></span> <span data-ttu-id="bd273-116">Pub/sub パターン。</span><span class="sxs-lookup"><span data-stu-id="bd273-116">The pub/sub pattern.</span></span>

<span data-ttu-id="bd273-117">前の図から、パターンの手順を確認します。</span><span class="sxs-lookup"><span data-stu-id="bd273-117">From the previous figure, note the steps of the pattern:</span></span>

1. <span data-ttu-id="bd273-118">パブリッシャーはメッセージブローカーにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="bd273-118">Publishers send messages to the message broker.</span></span>
1. <span data-ttu-id="bd273-119">サブスクライバーは、メッセージブローカーのサブスクリプションにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="bd273-119">Subscribers bind to a subscription on the message broker.</span></span>
1. <span data-ttu-id="bd273-120">メッセージブローカーは、メッセージのコピーを関心のあるサブスクリプションに転送します。</span><span class="sxs-lookup"><span data-stu-id="bd273-120">The message broker forwards a copy of the message to interested subscriptions.</span></span>
1. <span data-ttu-id="bd273-121">サブスクライバーは、サブスクリプションからのメッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd273-121">Subscribers consume messages from their subscriptions.</span></span>

<span data-ttu-id="bd273-122">ほとんどのメッセージブローカーは、受信後にメッセージを保持できるキューメカニズムをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="bd273-122">Most message brokers encapsulate a queueing mechanism that can persist messages once received.</span></span> <span data-ttu-id="bd273-123">メッセージブローカーでは、メッセージを格納することで **持続性** が保証されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-123">With it, the message broker guarantees **durability** by storing the message.</span></span> <span data-ttu-id="bd273-124">サブスクライバーは、パブリッシャーがメッセージを送信するときにすぐに使用できるようにしたり、オンラインにしたりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bd273-124">Subscribers don't need to be immediately available or even online when a publisher sends a message.</span></span> <span data-ttu-id="bd273-125">サブスクライバーは、使用可能になると、メッセージを受信して処理します。</span><span class="sxs-lookup"><span data-stu-id="bd273-125">Once available, the subscriber receives and processes the message.</span></span>  <span data-ttu-id="bd273-126">Dapr は、メッセージ配信に対して少なくとも **1 つ** のセマンティクスを保証します。</span><span class="sxs-lookup"><span data-stu-id="bd273-126">Dapr guarantees **At-Least-Once** semantics for message delivery.</span></span> <span data-ttu-id="bd273-127">メッセージが公開されると、対象のサブスクライバーに少なくとも1回配信されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-127">Once a message is published, it will be delivered at least once to any interested subscriber.</span></span>

 > <span data-ttu-id="bd273-128">サービスがメッセージを1回だけ処理できる場合は、同じメッセージが複数回処理されないことを確認するために、 [べき等チェック](/azure/architecture/microservices/design/api-design#idempotent-operations) を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-128">If your service can only process a message once, you'll need to provide an [idempotency check](/azure/architecture/microservices/design/api-design#idempotent-operations) to ensure that the same message is not processed multiple times.</span></span> <span data-ttu-id="bd273-129">このようなロジックはコーディングできますが、Azure Service Bus などの一部のメッセージブローカーには、組み込みの *重複検出* メッセージング機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="bd273-129">While such logic can be coded, some message brokers, such as Azure Service Bus, provide built-in *duplicate detection* messaging capabilities.</span></span>

<span data-ttu-id="bd273-130">使用できるメッセージブローカー製品には、商用とオープンソースの両方があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-130">There are several message broker products available - both commercially and open-source.</span></span> <span data-ttu-id="bd273-131">それぞれに長所と短所があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-131">Each has advantages and drawbacks.</span></span> <span data-ttu-id="bd273-132">ジョブは、システム要件を適切なブローカーに一致させることです。</span><span class="sxs-lookup"><span data-stu-id="bd273-132">Your job is to match your system requirements to the appropriate broker.</span></span> <span data-ttu-id="bd273-133">選択したら、アプリケーションをメッセージブローカーの組み込みから切り離すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bd273-133">Once selected, it's a best practice to decouple your application from message broker plumbing.</span></span> <span data-ttu-id="bd273-134">この機能を実現するには、 *抽象化* 内にブローカーをラップします。</span><span class="sxs-lookup"><span data-stu-id="bd273-134">You achieve this functionality by wrapping the broker inside an *abstraction*.</span></span> <span data-ttu-id="bd273-135">抽象化は、メッセージの組み込みをカプセル化し、汎用の pub/sub 操作をコードに公開します。</span><span class="sxs-lookup"><span data-stu-id="bd273-135">The abstraction encapsulates the message plumbing and exposes generic pub/sub operations to your code.</span></span> <span data-ttu-id="bd273-136">コードは、実際のメッセージブローカーではなく、抽象化と通信します。</span><span class="sxs-lookup"><span data-stu-id="bd273-136">Your code communicates with the abstraction, not the actual message broker.</span></span> <span data-ttu-id="bd273-137">賢明な決定として、抽象化とその基盤となる実装を作成して維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-137">While a wise decision, you'll have to write and maintain the abstraction and its underlying implementation.</span></span> <span data-ttu-id="bd273-138">この方法では、複雑で反復的で、エラーが発生しやすいカスタムコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="bd273-138">This approach requires custom code that can be complex, repetitive, and error-prone.</span></span>

<span data-ttu-id="bd273-139">Dapr publish & subscribe ビルディングブロックは、メッセージングの抽象化と実装をすぐに使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bd273-139">The Dapr publish & subscribe building block provides the messaging abstraction and implementation out-of-the-box.</span></span> <span data-ttu-id="bd273-140">記述する必要があるカスタムコードは、事前に作成され、Dapr ビルディングブロック内にカプセル化されています。</span><span class="sxs-lookup"><span data-stu-id="bd273-140">The custom code you would have had to write is prebuilt and encapsulated inside the Dapr building block.</span></span> <span data-ttu-id="bd273-141">それにバインドして使用します。</span><span class="sxs-lookup"><span data-stu-id="bd273-141">You bind to it and consume it.</span></span> <span data-ttu-id="bd273-142">メッセージングプラミングコードを記述する代わりに、顧客に価値を追加するビジネス機能の作成に専念します。</span><span class="sxs-lookup"><span data-stu-id="bd273-142">Instead of writing messaging plumbing code, you and your team focus on creating business functionality that adds value to your customers.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="bd273-143">しくみ</span><span class="sxs-lookup"><span data-stu-id="bd273-143">How it works</span></span>

<span data-ttu-id="bd273-144">Dapr publish & subscribe ビルディングブロックは、メッセージを送受信するためのプラットフォームに依存しない API フレームワークを提供します。</span><span class="sxs-lookup"><span data-stu-id="bd273-144">The Dapr publish & subscribe building block provides a platform-agnostic API framework to send and receive messages.</span></span> <span data-ttu-id="bd273-145">サービスは、名前付き [トピック](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions)にメッセージを公開します。</span><span class="sxs-lookup"><span data-stu-id="bd273-145">Your services publish messages to a named [topic](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions).</span></span> <span data-ttu-id="bd273-146">サービスは、メッセージを使用するトピックをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="bd273-146">Your services subscribe to a topic to consume messages.</span></span>

<span data-ttu-id="bd273-147">サービスは、Dapr サイドカーで pub/sub API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bd273-147">The service calls the pub/sub API on the Dapr sidecar.</span></span> <span data-ttu-id="bd273-148">その後、サイドカーは、特定のメッセージブローカー製品をカプセル化する定義済みの dapr pub/sub コンポーネントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bd273-148">The sidecar then makes calls into a pre-defined Dapr pub/sub component that encapsulates a specific message broker product.</span></span> <span data-ttu-id="bd273-149">図7-2 は、Dapr pub/sub messaging stack を示しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-149">Figure 7-2 shows the Dapr pub/sub messaging stack.</span></span>

![Pub/sub スタック](./media/publish-subscribe/pub-sub-buildingblock.png)

<span data-ttu-id="bd273-151">**図 7-2**。</span><span class="sxs-lookup"><span data-stu-id="bd273-151">**Figure 7-2**.</span></span> <span data-ttu-id="bd273-152">Dapr pub/sub スタック。</span><span class="sxs-lookup"><span data-stu-id="bd273-152">The Dapr pub/sub stack.</span></span>

<span data-ttu-id="bd273-153">Dapr publish & subscribe ビルディングブロックは、さまざまな方法で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bd273-153">The Dapr publish & subscribe building block can be invoked in many ways.</span></span>

<span data-ttu-id="bd273-154">最下位レベルでは、すべてのプログラミングプラットフォームは、 **Dapr ネイティブ API** を使用して HTTP または grpc 上でビルディングブロックを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bd273-154">At the lowest level, any programming platform can invoke the building block over HTTP or gRPC using the **Dapr native API**.</span></span> <span data-ttu-id="bd273-155">メッセージを公開するには、次の API 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="bd273-155">To publish a message, you make the following API call:</span></span>

``` http
http://localhost:<dapr-port>/v1.0/publish/<pub-sub-name>/<topic>
```

<span data-ttu-id="bd273-156">上記の呼び出しには、いくつかの Dapr 特定の URL セグメントがあります。</span><span class="sxs-lookup"><span data-stu-id="bd273-156">There are several Dapr specific URL segments in the above call:</span></span>

- <span data-ttu-id="bd273-157">`<dapr-port>` dapr サイドカーがリッスンするポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd273-157">`<dapr-port>` provides the port number upon which the Dapr sidecar is listening.</span></span>
- <span data-ttu-id="bd273-158">`<pub-sub-name>` 選択された Dapr pub/sub コンポーネントの名前を提供します。</span><span class="sxs-lookup"><span data-stu-id="bd273-158">`<pub-sub-name>` provides the name of the selected Dapr pub/sub component.</span></span>
- <span data-ttu-id="bd273-159">`<topic>` メッセージを公開するトピックの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd273-159">`<topic>` provides the name of the topic to which the message is published.</span></span>

<span data-ttu-id="bd273-160">*Curl* コマンドラインツールを使用してメッセージを公開するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bd273-160">Using the *curl* command-line tool to publish a message, you can try it out:</span></span>

``` curl
curl -X POST http://localhost:3500/v1.0/publish/pubsub/newOrder \
  -H "Content-Type: application/json" \
  -d '{ "orderId": "1234", "productId": "5678", "amount": 2 }'
```

<span data-ttu-id="bd273-161">トピックをサブスクライブすることによってメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="bd273-161">You receive messages by subscribing to a topic.</span></span> <span data-ttu-id="bd273-162">スタートアップ時に、Dapr ランタイムは既知のエンドポイントでアプリケーションを呼び出し、必要なサブスクリプションを特定して作成します。</span><span class="sxs-lookup"><span data-stu-id="bd273-162">At startup, the Dapr runtime will call the application on a well-known endpoint to identify and create the required subscriptions:</span></span>

``` http
http://localhost:<appPort>/dapr/subscribe
```

- <span data-ttu-id="bd273-163">`<appPort>` アプリケーションがリッスンしているポートの Dapr サイドカーを通知します。</span><span class="sxs-lookup"><span data-stu-id="bd273-163">`<appPort>` informs the Dapr sidecar of the port upon which the application is listening.</span></span>

<span data-ttu-id="bd273-164">このエンドポイントは自分で実装できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-164">You can implement this endpoint yourself.</span></span> <span data-ttu-id="bd273-165">しかし、Dapr は、より直感的な実装方法を提供しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-165">But Dapr provides more intuitive ways of implementing it.</span></span> <span data-ttu-id="bd273-166">この機能については、この章で後ほど説明します。</span><span class="sxs-lookup"><span data-stu-id="bd273-166">We'll address this functionality later in this chapter.</span></span>

<span data-ttu-id="bd273-167">呼び出しからの応答には、アプリケーションがサブスクライブするトピックの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd273-167">The response from the call contains a list of topics to which the applications will subscribe.</span></span> <span data-ttu-id="bd273-168">各には、トピックがメッセージを受信したときに呼び出すエンドポイントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd273-168">Each includes an endpoint to call when the topic receives a message.</span></span> <span data-ttu-id="bd273-169">応答の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd273-169">Here's an example of a response:</span></span>

```json
[
  {
    "pubsubname": "pubsub",
    "topic": "newOrder",
    "route": "/orders"
  },
  {
    "pubsubname": "pubsub",
    "topic": "newProduct",
    "route": "/productCatalog/products"
  }
]
```

<span data-ttu-id="bd273-170">JSON 応答では、アプリケーションがトピックとにサブスクライブする必要があることがわかり `newOrder` `newProduct` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-170">In the JSON response, you can see the application wants to subscribe to topics `newOrder` and `newProduct`.</span></span> <span data-ttu-id="bd273-171">それぞれにエンドポイントとが登録さ `/orders` `/productCatalog/products` れます。</span><span class="sxs-lookup"><span data-stu-id="bd273-171">It registers the endpoints `/orders` and `/productCatalog/products` for each, respectively.</span></span> <span data-ttu-id="bd273-172">どちらのサブスクリプションでも、アプリケーションはという名前の Dapr コンポーネントにバインド `pubsub` します。</span><span class="sxs-lookup"><span data-stu-id="bd273-172">For both subscriptions, the application is binding to the Dapr component named `pubsub`.</span></span>

<span data-ttu-id="bd273-173">図7-3 は、例のフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-173">Figure 7-3 presents the flow of the example.</span></span>

![Dapr を使用した pub/sub フローの例](media/publish-subscribe/pub-sub-flow.png)

<span data-ttu-id="bd273-175">**図 7-3**。</span><span class="sxs-lookup"><span data-stu-id="bd273-175">**Figure 7-3**.</span></span> <span data-ttu-id="bd273-176">Dapr を使用した pub/sub フロー。</span><span class="sxs-lookup"><span data-stu-id="bd273-176">pub/sub flow with Dapr.</span></span>

<span data-ttu-id="bd273-177">前の図から、フローに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd273-177">From the previous figure, note the flow:</span></span>

1. <span data-ttu-id="bd273-178">サービス b の dapr サイドカーは、 `/dapr/subscribe` サービス b (コンシューマー) からエンドポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bd273-178">The Dapr sidecar for Service B calls the `/dapr/subscribe` endpoint from Service B (the consumer).</span></span> <span data-ttu-id="bd273-179">サービスは、作成するサブスクリプションを使用して応答します。</span><span class="sxs-lookup"><span data-stu-id="bd273-179">The service responds with the subscriptions it wants to create.</span></span>
1. <span data-ttu-id="bd273-180">サービス B の dapr サイドカーは、要求されたサブスクリプションをメッセージブローカーに作成します。</span><span class="sxs-lookup"><span data-stu-id="bd273-180">The Dapr sidecar for Service B creates the requested subscriptions on the message broker.</span></span>
1. <span data-ttu-id="bd273-181">サービス A は `/v1.0/publish/<pub-sub-name>/<topic>` 、Dapr サービスのエンドポイントでメッセージを公開します。</span><span class="sxs-lookup"><span data-stu-id="bd273-181">Service A publishes a message at the `/v1.0/publish/<pub-sub-name>/<topic>` endpoint on the Dapr Service A sidecar.</span></span>
1. <span data-ttu-id="bd273-182">メッセージをメッセージブローカーに発行するサービス。</span><span class="sxs-lookup"><span data-stu-id="bd273-182">The Service A sidecar publishes the message to the message broker.</span></span>
1. <span data-ttu-id="bd273-183">メッセージブローカーは、メッセージのコピーをサービス B に送信します。</span><span class="sxs-lookup"><span data-stu-id="bd273-183">The message broker sends a copy of the message to the Service B sidecar.</span></span>
1. <span data-ttu-id="bd273-184">サービス B は、サービス B のサブスクリプション (この場合は) に対応するエンドポイントを呼び出します `/orders` 。サービスは HTTP 状態コードで応答し `200 OK` ます。そのため、サイドカーは、メッセージが正常に処理されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="bd273-184">The Service B sidecar calls the endpoint corresponding to the subscription (in this case `/orders`) on Service B. The service responds with an HTTP status-code `200 OK` so the sidecar will consider the message as being handled successfully.</span></span>

<span data-ttu-id="bd273-185">この例では、メッセージは正常に処理されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-185">In the example, the message is handled successfully.</span></span> <span data-ttu-id="bd273-186">しかし、サービス B が要求を処理している間に問題が発生した場合は、応答を使用して、メッセージをどのように処理する必要があるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-186">But if something goes wrong while Service B is handling the request, it can use the response to specify what needs to happen with the message.</span></span> <span data-ttu-id="bd273-187">HTTP 状態コードが返されると `404` 、エラーがログに記録され、メッセージが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-187">When it returns an HTTP status-code `404`, an error is logged and the message is dropped.</span></span> <span data-ttu-id="bd273-188">または以外の状態コードで `200` は `404` 、警告がログに記録され、メッセージが再試行されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-188">With any other status-code than `200` or `404`, a warning is logged and the message is retried.</span></span> <span data-ttu-id="bd273-189">また、サービス B は、応答の本文に JSON ペイロードを含めることによって、メッセージに対してどのような処理が行われるかを明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-189">Alternatively, Service B can explicitly specify what needs to happen with the message by including a JSON payload in the body of the response:</span></span>

```json
{
  "status": "<status>"
}
```

<span data-ttu-id="bd273-190">次の表に、使用可能な値を示し `status` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-190">The following table shows the available `status` values:</span></span>

| <span data-ttu-id="bd273-191">状態</span><span class="sxs-lookup"><span data-stu-id="bd273-191">Status</span></span>           | <span data-ttu-id="bd273-192">アクション</span><span class="sxs-lookup"><span data-stu-id="bd273-192">Action</span></span>                                                       |
| ---------------- | ------------------------------------------------------------ |
| <span data-ttu-id="bd273-193">SUCCESS</span><span class="sxs-lookup"><span data-stu-id="bd273-193">SUCCESS</span></span>          | <span data-ttu-id="bd273-194">メッセージは正常に処理され、削除されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="bd273-194">The message is considered as processed successfully and dropped.</span></span> |
| <span data-ttu-id="bd273-195">再試行</span><span class="sxs-lookup"><span data-stu-id="bd273-195">RETRY</span></span>            | <span data-ttu-id="bd273-196">メッセージは再試行されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-196">The message is retried.</span></span>                                      |
| <span data-ttu-id="bd273-197">DROP</span><span class="sxs-lookup"><span data-stu-id="bd273-197">DROP</span></span>             | <span data-ttu-id="bd273-198">警告がログに記録され、メッセージが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-198">A warning is logged and the message is dropped.</span></span>              |
| <span data-ttu-id="bd273-199">その他の状態</span><span class="sxs-lookup"><span data-stu-id="bd273-199">Any other status</span></span> | <span data-ttu-id="bd273-200">メッセージは再試行されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-200">The message is retried.</span></span>                                      |

### <a name="competing-consumers"></a><span data-ttu-id="bd273-201">競合コンシューマー</span><span class="sxs-lookup"><span data-stu-id="bd273-201">Competing consumers</span></span>

<span data-ttu-id="bd273-202">トピックをサブスクライブするアプリケーションをスケールアウトする場合は、競合コンシューマーに対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-202">When scaling out an application that subscribes to a topic, you have to deal with competing consumers.</span></span> <span data-ttu-id="bd273-203">トピックに送信されたメッセージを処理するアプリケーションインスタンスは1つだけです。</span><span class="sxs-lookup"><span data-stu-id="bd273-203">Only one application instance should handle a message sent to the topic.</span></span> <span data-ttu-id="bd273-204">さいわい、Dapr はその問題を処理します。</span><span class="sxs-lookup"><span data-stu-id="bd273-204">Luckily, Dapr handles that problem.</span></span> <span data-ttu-id="bd273-205">同じアプリケーション id を持つサービスの複数のインスタンスがトピックをサブスクライブしている場合、Dapr はそのうちの1つだけにメッセージを配信します。</span><span class="sxs-lookup"><span data-stu-id="bd273-205">When multiple instances of a service with the same application-id subscribe to a topic, Dapr delivers each message to only one of them.</span></span>

### <a name="sdks"></a><span data-ttu-id="bd273-206">SDK</span><span class="sxs-lookup"><span data-stu-id="bd273-206">SDKs</span></span>

<span data-ttu-id="bd273-207">ネイティブの Dapr Api に対する HTTP 呼び出しは、時間がかかり、抽象的なものです。</span><span class="sxs-lookup"><span data-stu-id="bd273-207">Making HTTP calls to the native Dapr APIs is time-consuming and abstract.</span></span> <span data-ttu-id="bd273-208">呼び出しは HTTP レベルで作成されるため、シリアル化や HTTP 応答コードなどの組み込みの問題を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-208">Your calls are crafted at the HTTP level, and you'll need to handle plumbing concerns such as serialization and HTTP response codes.</span></span> <span data-ttu-id="bd273-209">幸いにも、直感的な方法があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-209">Fortunately, there's a more intuitive way.</span></span> <span data-ttu-id="bd273-210">Dapr には、一般的な開発プラットフォーム向けの言語固有の Sdk がいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="bd273-210">Dapr provides several language-specific SDKs for popular development platforms.</span></span> <span data-ttu-id="bd273-211">このドキュメントの執筆時点では、Node.js、Python、.NET、Java、JavaScript を利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-211">At the time of this writing, Go, Node.js, Python, .NET, Java, and JavaScript are available.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="bd273-212">Dapr .NET SDK を使用する</span><span class="sxs-lookup"><span data-stu-id="bd273-212">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="bd273-213">.NET 開発者の場合、 [dapr .NET SDK](https://www.nuget.org/packages/Dapr.Client) を使用すると、dapr を操作するより生産的な方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-213">For .NET Developers, the [Dapr .NET SDK](https://www.nuget.org/packages/Dapr.Client) provides a more productive way of working with Dapr.</span></span> <span data-ttu-id="bd273-214">SDK は、 `DaprClient` Dapr 機能を直接呼び出すことができるクラスを公開します。</span><span class="sxs-lookup"><span data-stu-id="bd273-214">The SDK exposes a `DaprClient` class through which you can directly invoke Dapr functionality.</span></span> <span data-ttu-id="bd273-215">直感的で使いやすい方法です。</span><span class="sxs-lookup"><span data-stu-id="bd273-215">It's intuitive and easy to use.</span></span>

<span data-ttu-id="bd273-216">メッセージを公開するために、は `DaprClient` メソッドを公開し `PublishEventAsync` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-216">To publish a message, the `DaprClient` exposes a `PublishEventAsync` method.</span></span>

```csharp
var data = new OrderData
{
  orderId = "123456",
  productId = "67890",
  amount = 2
};

var daprClient = new DaprClientBuilder().Build();

await daprClient.PublishEventAsync<OrderData>("pubsub", "newOrder", data);
```

- <span data-ttu-id="bd273-217">最初の引数 `pubsub` は、メッセージブローカーの実装を提供する Dapr コンポーネントの名前です。</span><span class="sxs-lookup"><span data-stu-id="bd273-217">The first argument `pubsub` is the name of the Dapr component that provides the message broker implementation.</span></span> <span data-ttu-id="bd273-218">コンポーネントについては、この章で後ほど説明します。</span><span class="sxs-lookup"><span data-stu-id="bd273-218">We'll address components later in this chapter.</span></span>
- <span data-ttu-id="bd273-219">2番目の引数は、 `neworder` メッセージを送信するトピックの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd273-219">The second argument `neworder` provides the name of the topic to send the message to.</span></span>
- <span data-ttu-id="bd273-220">3番目の引数は、メッセージのペイロードです。</span><span class="sxs-lookup"><span data-stu-id="bd273-220">The third argument is the payload of the message.</span></span>
- <span data-ttu-id="bd273-221">メソッドのジェネリック型パラメーターを使用して、メッセージの .NET 型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-221">You can specify the .NET type of the message using the generic type parameter of the method.</span></span>

<span data-ttu-id="bd273-222">メッセージを受信するには、登録されたトピックのサブスクリプションにエンドポイントをバインドします。</span><span class="sxs-lookup"><span data-stu-id="bd273-222">To receive messages, you bind an endpoint to a subscription for a registered topic.</span></span> <span data-ttu-id="bd273-223">Dapr の AspNetCore ライブラリを使用すると、このようなことが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="bd273-223">The AspNetCore library for Dapr makes this trivial.</span></span> <span data-ttu-id="bd273-224">たとえば、既存の ASP.NET WebAPI action メソッドがあるとし `CreateOrder` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-224">Assume, for example, that you have an existing ASP.NET WebAPI action method entitled `CreateOrder`:</span></span>

```csharp
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

 > <span data-ttu-id="bd273-225">Dapr ASP.NET Core 統合を使用するには、プロジェクトの [dapr. AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) NuGet パッケージへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-225">You must add a reference to the [Dapr.AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) NuGet package in your project to consume the Dapr ASP.NET Core integration.</span></span>

<span data-ttu-id="bd273-226">このアクションメソッドをトピックにバインドするには、属性を使用して修飾し `Topic` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-226">To bind this action method to a topic, you decorate it with the `Topic` attribute:</span></span>

```csharp
[Topic("pubsub", "newOrder")]
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

<span data-ttu-id="bd273-227">この属性では、次の2つのキー要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd273-227">You specify two key elements with this attribute:</span></span>

- <span data-ttu-id="bd273-228">対象となる Dapr pub/sub コンポーネント (この場合は `pubsub` )。</span><span class="sxs-lookup"><span data-stu-id="bd273-228">The Dapr pub/sub component to target (in this case `pubsub`).</span></span>
- <span data-ttu-id="bd273-229">サブスクライブするトピック (この場合は `newOrder` )。</span><span class="sxs-lookup"><span data-stu-id="bd273-229">The topic to subscribe to (in this case `newOrder`).</span></span>

<span data-ttu-id="bd273-230">その後、そのトピックのメッセージを受信すると、dapr はそのアクションメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bd273-230">Dapr then invokes that action method as it receives messages for that topic.</span></span>

<span data-ttu-id="bd273-231">また、Dapr を使用するには ASP.NET Core を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-231">You'll also need to enable ASP.NET Core to use Dapr.</span></span> <span data-ttu-id="bd273-232">Dapr .NET SDK には、クラスで呼び出すことができる拡張メソッドがいくつか用意されて `Startup` います。</span><span class="sxs-lookup"><span data-stu-id="bd273-232">The Dapr .NET SDK provides several extension methods that can be invoked in the `Startup` class.</span></span>

<span data-ttu-id="bd273-233">メソッドでは、 `ConfigureServices` 次の拡張メソッドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-233">In the `ConfigureServices` method, you must add the following extension method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddControllers().AddDapr();
}
```

<span data-ttu-id="bd273-234">拡張メソッドを拡張メソッドに追加すると、 `AddDapr` `AddControllers` DAPR を MVC パイプラインに統合するために必要なサービスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-234">Appending the `AddDapr` extension-method to the `AddControllers` extension-method registers the necessary services to integrate Dapr into the MVC pipeline.</span></span> <span data-ttu-id="bd273-235">また、インスタンスを `DaprClient` 依存関係挿入コンテナーに登録します。これにより、サービスに任意の場所に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-235">It also registers a `DaprClient` instance into the dependency injection container, which then can be injected anywhere into your service.</span></span>

<span data-ttu-id="bd273-236">メソッドでは、 `Configure` Dapr を有効にするために、次のミドルウェアコンポーネントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-236">In the `Configure` method, you must add the following middleware components to enable Dapr:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // ...
    app.UseCloudEvents();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapSubscribeHandler();
        // ...
    });
}
```

<span data-ttu-id="bd273-237">への呼び出しは、 `UseCloudEvents` **CloudEvents** ミドルウェアを ASP.NET Core ミドルウェアパイプラインに追加します。</span><span class="sxs-lookup"><span data-stu-id="bd273-237">The call to `UseCloudEvents` adds **CloudEvents** middleware into to the ASP.NET Core middleware pipeline.</span></span> <span data-ttu-id="bd273-238">このミドルウェアは、CloudEvents 構造化形式を使用する要求をラップ解除します。これにより、受信側のメソッドはイベントペイロードを直接読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="bd273-238">This middleware will unwrap requests that use the CloudEvents structured format, so the receiving method can read the event payload directly.</span></span>

> <span data-ttu-id="bd273-239">[CloudEvents](https://cloudevents.io/) は標準化されたメッセージング形式であり、プラットフォーム間でイベント情報を記述する一般的な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="bd273-239">[CloudEvents](https://cloudevents.io/) is a standardized messaging format, providing a common way to describe event information across platforms.</span></span> <span data-ttu-id="bd273-240">Dapr は CloudEvents を採用しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-240">Dapr embraces CloudEvents.</span></span> <span data-ttu-id="bd273-241">CloudEvents の詳細については、 [CloudEvents 仕様](https://github.com/cloudevents/spec/tree/v1.0)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd273-241">For more information about CloudEvents, see the [cloudevents specification](https://github.com/cloudevents/spec/tree/v1.0).</span></span>

<span data-ttu-id="bd273-242">`MapSubscribeHandler`エンドポイントルーティング構成でを呼び出すと、Dapr サブスクライブエンドポイントがアプリケーションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-242">The call to `MapSubscribeHandler` in the endpoint routing configuration will add a Dapr subscribe endpoint to the application.</span></span> <span data-ttu-id="bd273-243">このエンドポイントは、に対する要求に応答 `/dapr/subscribe` します。</span><span class="sxs-lookup"><span data-stu-id="bd273-243">This endpoint will respond to requests on `/dapr/subscribe`.</span></span> <span data-ttu-id="bd273-244">このエンドポイントが呼び出されると、属性で修飾されたすべての WebAPI アクションメソッドが自動的に検出され、 `Topic` それらのサブスクリプションを作成するように Dapr に指示します。</span><span class="sxs-lookup"><span data-stu-id="bd273-244">When this endpoint is called, it will automatically find all WebAPI action methods decorated with the `Topic` attribute and instruct Dapr to create subscriptions for them.</span></span>

## <a name="pubsub-components"></a><span data-ttu-id="bd273-245">Pub/sub コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bd273-245">Pub/sub components</span></span>

<span data-ttu-id="bd273-246">Dapr [pub/sub コンポーネント](https://github.com/dapr/components-contrib/tree/master/pubsub) は、メッセージの実際の転送を処理します。</span><span class="sxs-lookup"><span data-stu-id="bd273-246">Dapr [pub/sub components](https://github.com/dapr/components-contrib/tree/master/pubsub) handle the actual transport of the messages.</span></span> <span data-ttu-id="bd273-247">いくつかの使用方法があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-247">Several are available.</span></span> <span data-ttu-id="bd273-248">各は、pub/sub 機能を実装するための特定のメッセージブローカー製品をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="bd273-248">Each encapsulates a specific message broker product to implement the pub/sub functionality.</span></span> <span data-ttu-id="bd273-249">書き込みの時点では、次の pub/sub コンポーネントを使用できました。</span><span class="sxs-lookup"><span data-stu-id="bd273-249">At the time of writing, the following pub/sub components were available:</span></span>

- <span data-ttu-id="bd273-250">Apache Kafka</span><span class="sxs-lookup"><span data-stu-id="bd273-250">Apache Kafka</span></span>
- <span data-ttu-id="bd273-251">Azure Event Hubs</span><span class="sxs-lookup"><span data-stu-id="bd273-251">Azure Event Hubs</span></span>
- <span data-ttu-id="bd273-252">Azure Service Bus</span><span class="sxs-lookup"><span data-stu-id="bd273-252">Azure Service Bus</span></span>
- <span data-ttu-id="bd273-253">AWS SNS/SQS</span><span class="sxs-lookup"><span data-stu-id="bd273-253">AWS SNS/SQS</span></span>
- <span data-ttu-id="bd273-254">GCP Pub/Sub</span><span class="sxs-lookup"><span data-stu-id="bd273-254">GCP Pub/Sub</span></span>
- <span data-ttu-id="bd273-255">Hazelcast</span><span class="sxs-lookup"><span data-stu-id="bd273-255">Hazelcast</span></span>
- <span data-ttu-id="bd273-256">MQTT</span><span class="sxs-lookup"><span data-stu-id="bd273-256">MQTT</span></span>
- <span data-ttu-id="bd273-257">NATS</span><span class="sxs-lookup"><span data-stu-id="bd273-257">NATS</span></span>
- <span data-ttu-id="bd273-258">"プル"</span><span class="sxs-lookup"><span data-stu-id="bd273-258">Pulsar</span></span>
- <span data-ttu-id="bd273-259">RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="bd273-259">RabbitMQ</span></span>
- <span data-ttu-id="bd273-260">Redis のストリーム</span><span class="sxs-lookup"><span data-stu-id="bd273-260">Redis Streams</span></span>

> [!NOTE]
> <span data-ttu-id="bd273-261">Azure クラウドスタックには、メッセージング機能 (Azure Service Bus) とイベントストリーミング (Azure イベントハブ) の可用性の両方があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-261">The Azure cloud stack has both messaging functionality (Azure Service Bus) and event streaming (Azure Event Hub) availability.</span></span>

<span data-ttu-id="bd273-262">これらのコンポーネントは、 [GitHub のコンポーネント contrib リポジトリ](https://github.com/dapr/components-contrib/tree/master/pubsub)のコミュニティによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-262">These components are created by the community in a [component-contrib repository on GitHub](https://github.com/dapr/components-contrib/tree/master/pubsub).</span></span> <span data-ttu-id="bd273-263">まだサポートされていないメッセージブローカー用に独自の Dapr コンポーネントを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bd273-263">You're encouraged to write your own Dapr component for a message broker that isn't yet supported.</span></span>

### <a name="configure-pubsub-components"></a><span data-ttu-id="bd273-264">Pub/sub コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="bd273-264">Configure pub/sub components</span></span>

<span data-ttu-id="bd273-265">Dapr 構成ファイルを使用すると、使用する pub/sub コンポーネントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-265">Using a Dapr configuration file, you can specify the pub/sub component(s) to use.</span></span> <span data-ttu-id="bd273-266">この構成にはいくつかのフィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd273-266">This configuration contains several fields.</span></span> <span data-ttu-id="bd273-267">フィールドは、 `name` 使用する pub/sub コンポーネントを指定します。</span><span class="sxs-lookup"><span data-stu-id="bd273-267">The `name` field specifies the pub/sub component that you want to use.</span></span> <span data-ttu-id="bd273-268">メッセージを送信または受信する場合は、この名前を指定する必要があります (メソッドシグネチャで前述したとおり `PublishEventAsync` )。</span><span class="sxs-lookup"><span data-stu-id="bd273-268">When sending or receiving a message, you need to specify this name (as you saw earlier in the `PublishEventAsync` method signature).</span></span>

<span data-ttu-id="bd273-269">RabbitMQ message broker コンポーネントを構成するための Dapr 構成ファイルの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="bd273-269">Below you see an example of a Dapr configuration file for configuring a RabbitMQ message broker component:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub-rq
spec:
  type: pubsub.rabbitmq
  version: v1
  metadata:
  - name: host
    value: "amqp://localhost:5672"
  - name: durable
    value: true
```

<span data-ttu-id="bd273-270">この例では、ブロックにメッセージブローカー固有の構成を指定できることを確認でき `metadata` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-270">In this example, you can see that you can specify any message broker-specific configuration in the `metadata` block.</span></span> <span data-ttu-id="bd273-271">この場合、RabbitMQ は永続的なキューを作成するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="bd273-271">In this case, RabbitMQ is configured to create durable queues.</span></span> <span data-ttu-id="bd273-272">しかし、RabbitMQ コンポーネントには、より多くの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="bd273-272">But the RabbitMQ component has more configuration options.</span></span> <span data-ttu-id="bd273-273">各コンポーネントの構成には、使用可能なフィールドの独自のセットがあります。</span><span class="sxs-lookup"><span data-stu-id="bd273-273">Each of the components' configuration will have its own set of possible fields.</span></span> <span data-ttu-id="bd273-274">各 [pub/sub コンポーネント](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/)のドキュメントで使用できるフィールドを確認できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-274">You can read which fields are available in the documentation of each [pub/sub component](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/).</span></span>

<span data-ttu-id="bd273-275">コードからトピックをサブスクライブするプログラム的な方法の場合、Dapr pub/sub では、トピックをサブスクライブする宣言型の方法も提供されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-275">Next to the programmatic way of subscribing to a topic from code, Dapr pub/sub also provides a declarative way of subscribing to a topic.</span></span> <span data-ttu-id="bd273-276">この方法では、アプリケーションコードから Dapr 依存関係が削除されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-276">This approach removes the Dapr dependency from the application code.</span></span> <span data-ttu-id="bd273-277">したがって、既存のアプリケーションでコードを変更することなくトピックをサブスクライブすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bd273-277">Therefore, it also enables an existing application to subscribe to topics without any changes to the code.</span></span> <span data-ttu-id="bd273-278">次の例は、サブスクリプションを構成するための Dapr 構成ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-278">The following example shows a Dapr configuration file for configuring a subscription:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Subscription
metadata:
  name: newOrder-subscription
spec:
  pubsubname: pubsub
  topic: newOrder
  route: /orders
scopes:
- ServiceB
- ServiceC
```

<span data-ttu-id="bd273-279">すべてのサブスクリプションで複数の要素を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-279">You have to specify several elements with every subscription:</span></span>

- <span data-ttu-id="bd273-280">使用する Dapr pub/sub コンポーネントの名前 (この場合は `pubsub` )。</span><span class="sxs-lookup"><span data-stu-id="bd273-280">The name of the Dapr pub/sub component you want to use (in this case `pubsub`).</span></span>
- <span data-ttu-id="bd273-281">サブスクライブするトピックの名前 (この場合は `newOrder` )。</span><span class="sxs-lookup"><span data-stu-id="bd273-281">The name of the topic to subscribe to (in this case `newOrder`).</span></span>
- <span data-ttu-id="bd273-282">このトピックに対して呼び出す必要がある API 操作 (この場合は `/orders` )。</span><span class="sxs-lookup"><span data-stu-id="bd273-282">The API operation that needs to be called for this topic (in this case `/orders`).</span></span>
- <span data-ttu-id="bd273-283">[スコープ](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/)では、トピックを発行およびサブスクライブできるサービスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-283">The [scope](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/) can specify which services can publish and subscribe to a topic.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="bd273-284">参照アプリケーション: eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="bd273-284">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="bd273-285">付随する [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) アプリは、dapr を実装するマイクロサービスアプリケーションを構築するためのエンドツーエンドの参照アーキテクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="bd273-285">The accompanying [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) app provides an end-to-end reference architecture for constructing a microservices application implementing Dapr.</span></span> <span data-ttu-id="bd273-286">eShopOnDapr は、数年前に作成された、広く普及している [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) アプリの進化です。</span><span class="sxs-lookup"><span data-stu-id="bd273-286">eShopOnDapr is an evolution of the widely popular [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) app, created several years ago.</span></span> <span data-ttu-id="bd273-287">どちらのバージョンも、マイクロサービス間の [統合イベント](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) の通信には、pub/sub パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd273-287">Both versions use the pub/sub pattern for communicating [integration events](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) across microservices.</span></span> <span data-ttu-id="bd273-288">統合イベントには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="bd273-288">Integration events include:</span></span>

- <span data-ttu-id="bd273-289">ユーザーが買い物かごをチェックアウトしたとき。</span><span class="sxs-lookup"><span data-stu-id="bd273-289">When a user checks-out a shopping basket.</span></span>
- <span data-ttu-id="bd273-290">注文の支払いが成功した場合。</span><span class="sxs-lookup"><span data-stu-id="bd273-290">When a payment for an order has succeeded.</span></span>
- <span data-ttu-id="bd273-291">購入の猶予期間が終了したとき。</span><span class="sxs-lookup"><span data-stu-id="bd273-291">When the grace-period of a purchase has expired.</span></span>

<span data-ttu-id="bd273-292">EShopOnContainers のイベントは、次のインターフェイスに基づいてい `IEventBus` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-292">Eventing in eShopOnContainers is based on the following `IEventBus` interface:</span></span>

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent integrationEvent);

    void Subscribe<T, THandler>()
        where TEvent : IntegrationEvent
        where THandler : IIntegrationEventHandler<T>;
}
```

<span data-ttu-id="bd273-293">このインターフェイスの具象実装は、RabbitMQ と Azure Service Bus の両方の eShopOnContainers に存在します。</span><span class="sxs-lookup"><span data-stu-id="bd273-293">Concrete implementations of this interface exist in eShopOnContainers for both RabbitMQ and Azure Service Bus.</span></span> <span data-ttu-id="bd273-294">各実装には、理解が困難で保守が困難なカスタムプラミングコードが数多く含まれていました。</span><span class="sxs-lookup"><span data-stu-id="bd273-294">Each implementation included a great deal of custom plumbing code that was complex to understand and difficult to maintain.</span></span>

<span data-ttu-id="bd273-295">新しい eShopOnDapr は、Dapr を使用して公開/サブスクライブの動作を大幅に簡素化します。</span><span class="sxs-lookup"><span data-stu-id="bd273-295">The newer eShopOnDapr significantly simplifies pub/sub behavior by using Dapr.</span></span> <span data-ttu-id="bd273-296">たとえば、インターフェイスが `IEventBus` 1 つのメソッドに縮小されたとします。</span><span class="sxs-lookup"><span data-stu-id="bd273-296">For example, the `IEventBus` interface was reduced to a single method:</span></span>

```csharp
public interface IEventBus
{
    Task PublishAsync(IntegrationEvent integrationEvent);
}
```

### <a name="publish-events"></a><span data-ttu-id="bd273-297">イベントの発行</span><span class="sxs-lookup"><span data-stu-id="bd273-297">Publish events</span></span>

<span data-ttu-id="bd273-298">更新された eShopOnDapr では、1つの実装で、 `DaprEventBus` 任意の Dapr でサポートされているメッセージブローカーをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="bd273-298">In the updated eShopOnDapr, a single `DaprEventBus` implementation can support any Dapr-supported message broker.</span></span> <span data-ttu-id="bd273-299">次のコードブロックは、簡略化された発行メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd273-299">The following code block shows the simplified Publish method.</span></span> <span data-ttu-id="bd273-300">`PublishAsync`メソッドが Dapr クライアントを使用してイベントを発行する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd273-300">Note how the `PublishAsync` method uses the Dapr client to publish an event:</span></span>

```csharp
public class DaprEventBus : IEventBus
{
    private const string PubSubName = "pubsub";

    private readonly DaprClient _daprClient;
    private readonly ILogger<DaprEventBus> _logger;

    public DaprEventBus(DaprClient daprClient, ILogger<DaprEventBus> logger)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task PublishAsync(IntegrationEvent integrationEvent)
    {
        var topicName = integrationEvent.GetType().Name;

        // Dapr uses System.Text.Json which does not support serialization of a
        // polymorphic type hierarchy by default. Using object as the type
        // parameter causes all properties to be serialized.
        await _daprClient.PublishEventAsync<object>(PubSubName, topicName, integrationEvent);
    }
}
```

<span data-ttu-id="bd273-301">コードスニペットでわかるように、トピック名はイベントの種類の名前から派生します。</span><span class="sxs-lookup"><span data-stu-id="bd273-301">As you can see in the code snippet, the topic name is derived from event type's name.</span></span> <span data-ttu-id="bd273-302">すべての eShop サービスで抽象化が使用されるため `IEventBus` 、改良 Dapr では、メインのアプリケーションコードをまったく変更する必要が *ありません* 。</span><span class="sxs-lookup"><span data-stu-id="bd273-302">Because all eShop services use the `IEventBus` abstraction, retrofitting Dapr required *absolutely no change* to the mainline application code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd273-303">Dapr SDK は、を使用して `System.Text.Json` メッセージをシリアル化または逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="bd273-303">The Dapr SDK uses `System.Text.Json` to serialize/deserialize messages.</span></span> <span data-ttu-id="bd273-304">ただし、では、 `System.Text.Json` 既定では派生クラスのプロパティはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="bd273-304">However, `System.Text.Json` doesn't serialize properties of derived classes by default.</span></span> <span data-ttu-id="bd273-305">EShop コードでは、イベントは、 `IntegrationEvent` 統合イベントの基底クラスであるとして明示的に宣言されることがあります。</span><span class="sxs-lookup"><span data-stu-id="bd273-305">In the eShop code, an event is sometimes explicitly declared as an `IntegrationEvent`, the base class for integration events.</span></span> <span data-ttu-id="bd273-306">これは、ビジネスロジックに基づいて、具象イベントの種類が実行時に動的に決定されるためです。</span><span class="sxs-lookup"><span data-stu-id="bd273-306">This is done because the concrete event type is determined dynamically at run time based on business logic.</span></span> <span data-ttu-id="bd273-307">その結果、イベントは、派生クラスではなく、基本クラスの型情報を使用してシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-307">As a result, the event is serialized using the type information of the base class and not the derived class.</span></span> <span data-ttu-id="bd273-308">`System.Text.Json`この場合、が派生クラスのすべてのプロパティを強制的にシリアル化するには、コードが `object` ジェネリック型パラメーターとしてを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd273-308">To force `System.Text.Json` to serialize all properties of the derived class in this case, the code uses `object` as the generic type parameter.</span></span> <span data-ttu-id="bd273-309">詳細については、 [.net のドキュメント](../../standard/serialization/system-text-json-polymorphism.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd273-309">For more information, see the [.NET documentation](../../standard/serialization/system-text-json-polymorphism.md).</span></span>

<span data-ttu-id="bd273-310">Dapr を使用すると、インフラストラクチャコードが **大幅に簡素化** されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-310">With Dapr, the infrastructure code is **dramatically simplified**.</span></span> <span data-ttu-id="bd273-311">異なるメッセージブローカーを区別する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bd273-311">It doesn't need to distinguish between the different message brokers.</span></span> <span data-ttu-id="bd273-312">Dapr は、このような抽象化を提供します。</span><span class="sxs-lookup"><span data-stu-id="bd273-312">Dapr provides this abstraction for you.</span></span> <span data-ttu-id="bd273-313">また、必要に応じて、メッセージブローカーを簡単に交換したり、複数のメッセージブローカーコンポーネントを構成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="bd273-313">And if needed, you can easily swap out message brokers or configure multiple message broker components.</span></span>

### <a name="subscribe-to-events"></a><span data-ttu-id="bd273-314">イベントをサブスクライブする</span><span class="sxs-lookup"><span data-stu-id="bd273-314">Subscribe to events</span></span>

<span data-ttu-id="bd273-315">以前の eShopOnContainers アプリには、各メッセージブローカーのサブスクリプションの実装を処理する *Subscriptionmanagers* が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd273-315">The earlier eShopOnContainers app contains *SubscriptionManagers* to handle the subscription implementation for each message broker.</span></span> <span data-ttu-id="bd273-316">各マネージャーには、サブスクリプションイベントを処理するための、複雑なメッセージブローカー固有のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd273-316">Each manager contains complex message broker-specific code for handling subscription events.</span></span> <span data-ttu-id="bd273-317">イベントを受け取るには、各サービスが各イベントの種類のハンドラーを明示的に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-317">To receive events, each service has to explicitly register a handler for each event-type.</span></span>

<span data-ttu-id="bd273-318">eShopOnDapr は、Dapr ASP.NET Core ライブラリを使用して、イベントサブスクリプションの組み込みを効率化します。</span><span class="sxs-lookup"><span data-stu-id="bd273-318">eShopOnDapr streamlines the plumbing for event subscriptions by using Dapr ASP.NET Core libraries.</span></span> <span data-ttu-id="bd273-319">各イベントは、コントローラーのアクションメソッドによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-319">Each event is handled by an action method in the controller.</span></span> <span data-ttu-id="bd273-320">`Topic`装飾属性は、アクションメソッドに、サブスクライブする対応するトピックの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd273-320">A `Topic` attribute decorates the action method with the name of the corresponding topic to subscribe to.</span></span> <span data-ttu-id="bd273-321">次に、から取得したコードスニペットを示し `PaymentService` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-321">Here's a code snippet taken from the `PaymentService`:</span></span>

```csharp
[Route("api/v1/[controller]")]
[ApiController]
public class IntegrationEventController : ControllerBase
{
    private const string DAPR_PUBSUB_NAME = "pubsub";

    private readonly IServiceProvider _serviceProvider;

    public IntegrationEventController(IServiceProvider serviceProvider)
    {
        _serviceProvider = serviceProvider;
    }

    [HttpPost("OrderStatusChangedToValidated")]
    [Topic(DAPR_PUBSUB_NAME, "OrderStatusChangedToValidatedIntegrationEvent")]
    public async Task OrderStarted(OrderStatusChangedToValidatedIntegrationEvent integrationEvent)
    {
        var handler = _serviceProvider.GetRequiredService<OrderStatusChangedToValidatedIntegrationEventHandler>();
        await handler.Handle(integrationEvent);
    }
}
```

<span data-ttu-id="bd273-322">属性で `Topic` は、イベントの .net 型の名前がトピック名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-322">In the `Topic` attribute, the name of the .NET type of the event is used as the topic name.</span></span> <span data-ttu-id="bd273-323">イベントを処理するために、以前の eShopOnContainers コードベースに既に存在していたイベントハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-323">For handling the event, an event handler that already existed in the earlier eShopOnContainers code base is invoked.</span></span> <span data-ttu-id="bd273-324">前の例では、トピックから受信したメッセージによっ `OrderStatusChangedToValidatedIntegrationEvent` て既存のイベントハンドラーが呼び出され `OrderStatusChangedToValidatedIntegrationEventHandler` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-324">In the previous example, messages received from the `OrderStatusChangedToValidatedIntegrationEvent` topic invoke the existing `OrderStatusChangedToValidatedIntegrationEventHandler` event-handler.</span></span> <span data-ttu-id="bd273-325">Dapr はサブスクリプションとメッセージブローカーの基になるプラミングを実装しているため、大量の元のコードが廃止され、コードベースから削除されました。</span><span class="sxs-lookup"><span data-stu-id="bd273-325">Because Dapr implements the underlying plumbing for subscriptions and message brokers, a large amount of original code became obsolete and was removed from the code-base.</span></span> <span data-ttu-id="bd273-326">このコードの多くは、理解しやすく、保守が困難でした。</span><span class="sxs-lookup"><span data-stu-id="bd273-326">Much of this code was complex to understand and challenging to maintain.</span></span>

### <a name="use-pubsub-components"></a><span data-ttu-id="bd273-327">Pub/sub コンポーネントの使用</span><span class="sxs-lookup"><span data-stu-id="bd273-327">Use pub/sub components</span></span>

<span data-ttu-id="bd273-328">EShopOnDapr リポジトリ内のフォルダーには、 `deployment` さまざまな配置モード (および) を使用してアプリケーションを配置するためのファイルが含まれてい `Docker Compose` `Kubernetes` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-328">Within the eShopOnDapr repository, a `deployment` folder contains files for deploying the application using different deployment modes: `Docker Compose` and `Kubernetes`.</span></span> <span data-ttu-id="bd273-329">フォルダーは、フォルダー `dapr` を保持する各フォルダー内に存在し `components` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-329">A `dapr` folder exists within each of these folders that holds a `components` folder.</span></span> <span data-ttu-id="bd273-330">このフォルダーには、 `eshop-pubsub.yaml` アプリケーションが pub/sub 動作に使用する Dapr pub/sub コンポーネントの構成を含むファイルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="bd273-330">This folder holds a file `eshop-pubsub.yaml` containing the configuration of the Dapr pub/sub component that the application will use for pub/sub behavior.</span></span> <span data-ttu-id="bd273-331">前のコードスニペットで見たように、使用される pub/sub コンポーネントの名前は `pubsub` です。</span><span class="sxs-lookup"><span data-stu-id="bd273-331">As you saw in the earlier code snippets, the name of the pub/sub component used is `pubsub`.</span></span> <span data-ttu-id="bd273-332">フォルダー内のファイルの内容を次に示し `eshop-pubsub.yaml` `deployment/compose/dapr/components` ます。</span><span class="sxs-lookup"><span data-stu-id="bd273-332">Here's the content of the `eshop-pubsub.yaml` file in the `deployment/compose/dapr/components` folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: default
spec:
  type: pubsub.nats
  version: v1
  metadata:
  - name: natsURL
    value: nats://demo.nats.io:4222
```

<span data-ttu-id="bd273-333">上記の構成では、この例で必要な [nat メッセージブローカー](https://nats.io/) を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd273-333">The preceding configuration specifies the desired [NATS message broker](https://nats.io/) for this example.</span></span> <span data-ttu-id="bd273-334">メッセージブローカーを変更するには、RabbitMQ や Azure Service Bus などの別のメッセージブローカーを構成して、yaml ファイルを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-334">To change message brokers, you need only to configure a different message broker, such as RabbitMQ or Azure Service Bus and update the yaml file.</span></span> <span data-ttu-id="bd273-335">Dapr では、メッセージブローカーを切り替えるときに、メインのサービスコードに変更はありません。</span><span class="sxs-lookup"><span data-stu-id="bd273-335">With Dapr, there are no changes to your mainline service code when switching message brokers.</span></span>

<span data-ttu-id="bd273-336">最後に、"アプリケーションに複数のメッセージブローカーが必要になるのはなぜですか。" という質問が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-336">Finally, you might ask, "Why would I need multiple message brokers in an application?".</span></span> <span data-ttu-id="bd273-337">多くの場合、システムはさまざまな特性を持つワークロードを処理します。</span><span class="sxs-lookup"><span data-stu-id="bd273-337">Many times a system will handle workloads with different characteristics.</span></span> <span data-ttu-id="bd273-338">1日に10回発生するイベントもありますが、別のイベントは1秒あたり5000回発生します。</span><span class="sxs-lookup"><span data-stu-id="bd273-338">One event may occur 10 times a day, but another event occurs 5,000 times per second.</span></span> <span data-ttu-id="bd273-339">メッセージングトラフィックを別のメッセージブローカーに分割することでメリットが得られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd273-339">You may benefit by partitioning messaging traffic to different message brokers.</span></span> <span data-ttu-id="bd273-340">Dapr を使用すると、複数の pub/sub コンポーネント構成を追加できます。それぞれに異なる名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="bd273-340">With Dapr, you can add multiple pub/sub component configurations, each with a different name.</span></span>

## <a name="summary"></a><span data-ttu-id="bd273-341">まとめ</span><span class="sxs-lookup"><span data-stu-id="bd273-341">Summary</span></span>

<span data-ttu-id="bd273-342">Pub/sub パターンは、分散アプリケーションでサービスを分離するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bd273-342">The pub/sub pattern helps you decouple services in a distributed application.</span></span> <span data-ttu-id="bd273-343">Dapr publish & subscribe ビルディングブロックを使用すると、アプリケーションにこの動作を簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-343">The Dapr publish & subscribe building block simplifies implementing this behavior in your application.</span></span>

<span data-ttu-id="bd273-344">Dapr pub/sub を使用すると、特定の *トピック* にメッセージを公開できます。</span><span class="sxs-lookup"><span data-stu-id="bd273-344">Through Dapr pub/sub, you can publish messages to a specific *topic*.</span></span> <span data-ttu-id="bd273-345">また、ビルディングブロックは、サブスクライブするトピックを決定するためにサービスにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="bd273-345">As well, the building block will query your service to determine which topic(s) to subscribe to.</span></span>

<span data-ttu-id="bd273-346">Dapr pub/sub は、HTTP 経由でネイティブに使用することも、.NET SDK for Dapr などの言語固有の Sdk のいずれかを使用して使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd273-346">You can use Dapr pub/sub natively over HTTP or by using one of the language-specific SDKs, such as the .NET SDK for Dapr.</span></span> <span data-ttu-id="bd273-347">.NET SDK は、ASP.NET core プラットフォームと緊密に統合されています。</span><span class="sxs-lookup"><span data-stu-id="bd273-347">The .NET SDK tightly integrates with the ASP.NET core platform.</span></span>

<span data-ttu-id="bd273-348">Dapr を使用すると、サポートされているメッセージブローカー製品をアプリケーションに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bd273-348">With Dapr, you can plug a supported message broker product into your application.</span></span> <span data-ttu-id="bd273-349">次に、アプリケーションにコードの変更を必要とせずに、メッセージブローカーをスワップできます。</span><span class="sxs-lookup"><span data-stu-id="bd273-349">You can then swap message brokers without requiring code changes to your application.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="bd273-350">[前へ](service-invocation.md)
> [次へ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bd273-350">[Previous](service-invocation.md)
[Next](bindings.md)</span></span>
