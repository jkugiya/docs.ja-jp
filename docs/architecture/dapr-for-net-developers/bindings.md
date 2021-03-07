---
title: Dapr バインド構成ブロック
description: バインド構成要素の説明、その機能、利点、適用方法
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 757d2560016407119fe9244c100a971977852cc5
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401463"
---
# <a name="the-dapr-bindings-building-block"></a><span data-ttu-id="0a4f6-103">Dapr バインド構成ブロック</span><span class="sxs-lookup"><span data-stu-id="0a4f6-103">The Dapr bindings building block</span></span>

<span data-ttu-id="0a4f6-104">Azure Functions や AWS などのクラウドベースの *サーバーレス* サービスでは、分散アーキテクチャ領域全体で広く普及しています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-104">Cloud-based *serverless* offerings, such as Azure Functions and AWS Lambda, have gained wide adoption across the distributed architecture space.</span></span> <span data-ttu-id="0a4f6-105">多くの利点の中で、マイクロサービスが外部システム *のイベント\*\*のイベントを処理* したり、イベントを呼び出したりできるようにします。これにより、基盤となる複雑さやプラミングの問題を解消できます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-105">Among many benefits, they enable a microservice to *handle events from* or *invoke events in* an external system - abstracting away the underlying complexity and plumbing concerns.</span></span> <span data-ttu-id="0a4f6-106">外部リソースは多数あります。これには、さまざまなプラットフォームやベンダーにわたるデータストア、メッセージシステム、web リソースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-106">External resources are many: They include datastores, message systems, and web resources, across different platforms and vendors.</span></span> <span data-ttu-id="0a4f6-107">[Dapr binding ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/)は、dapr アプリケーションの doorstep に同じリソースバインド機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-107">The [Dapr bindings building block](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/) brings these same resource binding capabilities to the doorstep of your Dapr applications.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="0a4f6-108">解決方法</span><span class="sxs-lookup"><span data-stu-id="0a4f6-108">What it solves</span></span>

<span data-ttu-id="0a4f6-109">Dapr リソースバインドを使用すると、サービスは、直接アプリケーションの外部にある外部リソースに対してビジネス操作を統合できます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-109">Dapr resource bindings enable your services to integrate business operations across external resources outside of the immediate application.</span></span> <span data-ttu-id="0a4f6-110">外部システムからのイベントにより、サービスでコンテキスト情報を渡す操作がトリガーされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-110">An event from an external system could trigger an operation in your service passing in contextual information.</span></span> <span data-ttu-id="0a4f6-111">サービスは、別の外部システムでイベントをトリガーすることによって操作を拡張し、コンテキストペイロード情報を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-111">Your service could then expand the operation by triggering an event in another external system, passing in contextual payload information.</span></span> <span data-ttu-id="0a4f6-112">サービスは、外部リソースを結合または認識しなくても通信します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-112">Your service communicates without coupling or awareness of the external resource.</span></span> <span data-ttu-id="0a4f6-113">組み込みは、事前に定義された Dapr コンポーネント内にカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-113">The plumbing is encapsulated inside pre-defined Dapr components.</span></span> <span data-ttu-id="0a4f6-114">使用する Dapr コンポーネントは、コードを変更せずに実行時に簡単に入れ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-114">The Dapr component to use can be easily swapped at runtime without code changes.</span></span>

<span data-ttu-id="0a4f6-115">たとえば、ユーザーがキーワードをツイートたびにイベントをトリガーする Twitter アカウントなどを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-115">Consider, for example, a Twitter account that triggers an event whenever a user tweets a keyword.</span></span> <span data-ttu-id="0a4f6-116">サービスは、ツイートを受信して処理するイベントハンドラーを公開します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-116">Your service exposes an event handler that receives and processes the tweet.</span></span> <span data-ttu-id="0a4f6-117">完了すると、サービスによって、外部の Twilio サービスを呼び出すイベントがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-117">Once complete, your service triggers an event that invokes an external Twilio service.</span></span> <span data-ttu-id="0a4f6-118">Twilio は、ツイートを含む SMS メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-118">Twilio sends an SMS message that includes the tweet.</span></span> <span data-ttu-id="0a4f6-119">図8-1 は、この操作の概念アーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-119">Figure 8-1 show the conceptual architecture of this operation.</span></span>

![入力バインド](media/bindings/bindings-architecture.png)

<span data-ttu-id="0a4f6-121">**図 8-1**。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-121">**Figure 8-1**.</span></span> <span data-ttu-id="0a4f6-122">Dapr リソースバインドの概念アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-122">Conceptual architecture of a Dapr resource binding.</span></span>

<span data-ttu-id="0a4f6-123">一見すると、リソースバインドの動作は、このブックで前に説明した [Publish/Subscribe パターン](publish-subscribe.md) と同様に表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-123">At first glance, resource binding behavior may appear similar to the [Publish/Subscribe pattern](publish-subscribe.md) described earlier in this book.</span></span> <span data-ttu-id="0a4f6-124">両者は類似性を共有していますが、違いがあります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-124">While they share similarities, there are differences.</span></span> <span data-ttu-id="0a4f6-125">パブリッシュ/サブスクライブは、Dapr サービス間の非同期通信に重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-125">Publish/subscribe focuses on asynchronous communication between Dapr services.</span></span> <span data-ttu-id="0a4f6-126">リソースバインドのスコープはかなり広くなります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-126">Resource binding has a much wider scope.</span></span> <span data-ttu-id="0a4f6-127">ソフトウェアプラットフォーム間のシステムの相互運用性に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-127">It focuses on system interoperability across software platforms.</span></span> <span data-ttu-id="0a4f6-128">マイクロサービスアプリケーション外の異なるアプリケーション、データストア、およびサービス間で情報を交換する。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-128">Exchanging information between disparate applications, datastores, and services outside your microservice application.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="0a4f6-129">しくみ</span><span class="sxs-lookup"><span data-stu-id="0a4f6-129">How it works</span></span>

<span data-ttu-id="0a4f6-130">Dapr リソースバインドは、コンポーネント構成ファイルで開始されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-130">Dapr resource binding starts with a component configuration file.</span></span> <span data-ttu-id="0a4f6-131">この YAML ファイルは、構成設定と共にバインドするリソースの種類を記述します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-131">This YAML file describes the type of resource to which you'll bind along with its configuration settings.</span></span> <span data-ttu-id="0a4f6-132">構成が完了すると、サービスはリソースからイベントを受信したり、イベントをトリガーしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-132">Once configured, your service can receive events from the resource or trigger events on it.</span></span>

> [!NOTE]
> <span data-ttu-id="0a4f6-133">バインディングの構成については、後の「 *コンポーネント* 」セクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-133">Binding configurations are presented in detail later in the *Components* section.</span></span>

### <a name="input-bindings"></a><span data-ttu-id="0a4f6-134">入力バインディング</span><span class="sxs-lookup"><span data-stu-id="0a4f6-134">Input bindings</span></span>

<span data-ttu-id="0a4f6-135">入力バインディングは、外部リソースからの受信イベントでコードをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-135">Input bindings trigger your code with incoming events from external resources.</span></span> <span data-ttu-id="0a4f6-136">イベントとデータを受信するには、サービスから *イベントハンドラー* になるパブリックエンドポイントを登録します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-136">To receive events and data, you register a public endpoint from your service that becomes the *event handler*.</span></span> <span data-ttu-id="0a4f6-137">図8-2 にフローを示します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-137">Figure 8-2 shows the flow:</span></span>

![Dapr 入力バインドフロー](media/bindings/input-binding-flow.png)

<span data-ttu-id="0a4f6-139">**図 8-2**。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-139">**Figure 8-2**.</span></span> <span data-ttu-id="0a4f6-140">Dapr 入力バインドフロー。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-140">Dapr input binding flow.</span></span>

<span data-ttu-id="0a4f6-141">図8.2 では、外部の Twitter アカウントからイベントを受信する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-141">Figure 8.2 describes the steps for receiving events from an external Twitter account:</span></span>

1. <span data-ttu-id="0a4f6-142">Dapr サイドカーは、バインド構成ファイルを読み取り、外部リソースに対して指定されたイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-142">The Dapr sidecar reads the binding configuration file and subscribes to the event specified for the external resource.</span></span> <span data-ttu-id="0a4f6-143">この例では、イベントソースは Twitter アカウントです。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-143">In the example, the event source is a Twitter account.</span></span>
1. <span data-ttu-id="0a4f6-144">一致するツイートが Twitter で公開されると、Dapr サイドカーで実行されているバインドコンポーネントがそれを取得し、イベントをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-144">When a matching Tweet is published on Twitter, the binding component running in the Dapr sidecar picks it up and triggers an event.</span></span>
1. <span data-ttu-id="0a4f6-145">Dapr サイドカーは、バインディング用に構成されたエンドポイント (つまり、イベントハンドラー) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-145">The Dapr sidecar invokes the endpoint (that is, event handler) configured for the binding.</span></span> <span data-ttu-id="0a4f6-146">この例では、サービスは、 `/tweet` ポート6000でエンドポイントの HTTP POST をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-146">In the example, the service listens for an HTTP POST on the `/tweet` endpoint on port 6000.</span></span> <span data-ttu-id="0a4f6-147">HTTP POST 操作であるため、イベントの JSON ペイロードが要求本文で渡されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-147">Because it's an HTTP POST operation, the JSON payload for the event is passed in the request body.</span></span>
1. <span data-ttu-id="0a4f6-148">イベントを処理した後、サービスは HTTP 状態コードを返し `200 OK` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-148">After handling the event, the service returns an HTTP status code `200 OK`.</span></span>

<span data-ttu-id="0a4f6-149">次の ASP.NET Core コントローラーは、Twitter のバインドによってトリガーされるイベントを処理する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-149">The following ASP.NET Core controller provides an example of handling an event triggered by the Twitter binding:</span></span>

```csharp
[ApiController]
public class SomeController : ControllerBase
{
    public class TwitterTweet
    {
        [JsonPropertyName("id_str")]
        public string ID {get; set; }

        [JsonPropertyName("text")]
        public string Text {get; set; }
    }

    [HttpPost("/tweet")]
    public ActionResult Post(TwitterTweet tweet)
    {
        // Handle tweet
        Console.WriteLine("Tweet received: {0}: {1}", tweet.ID, tweet.Text);

        // ...

        // Acknowledge message
        return Ok();
    }
}
```

<span data-ttu-id="0a4f6-150">操作がエラーになる場合は、適切な400または500レベルの HTTP 状態コードを返します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-150">If the operation should error, you would return the appropriate 400 or 500 level HTTP status code.</span></span> <span data-ttu-id="0a4f6-151">少なくとも *1 回の配信* が保証される場合は、dapr サイドカーによってトリガーが再試行されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-151">For bindings that feature *at-least-once-delivery* guarantees, the Dapr sidecar will retry the trigger.</span></span> <span data-ttu-id="0a4f6-152">[リソースバインドの Dapr ドキュメント] [1] をチェックアウトして、少なくとも 1 *回* または 1 *回* の配信保証を提供するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-152">Check out [Dapr documentation for resource bindings][1] to see whether they offer *at-least-once* or *exactly-once* delivery guarantees.</span></span>

### <a name="output-bindings"></a><span data-ttu-id="0a4f6-153">出力バインディング</span><span class="sxs-lookup"><span data-stu-id="0a4f6-153">Output bindings</span></span>

<span data-ttu-id="0a4f6-154">Dapr には、 *出力バインディング* 機能も含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-154">Dapr also includes *output binding* capabilities.</span></span> <span data-ttu-id="0a4f6-155">これにより、サービスが外部リソースを呼び出すイベントをトリガーできるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-155">They enable your service to trigger an event that invokes an external resource.</span></span> <span data-ttu-id="0a4f6-156">ここでも、まず、出力バインディングを記述するバインド構成 YAML ファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-156">Again, you start by configuring a binding configuration YAML file that describes the output binding.</span></span> <span data-ttu-id="0a4f6-157">その後、アプリケーションの dapr サイドカーで bindings API を呼び出すイベントをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-157">Once in place, you trigger an event that invokes the bindings API on the Dapr sidecar of your application.</span></span> <span data-ttu-id="0a4f6-158">図8-3 は、出力バインドのフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-158">Figure 8-3 shows the flow of an output binding:</span></span>

![Dapr 出力バインドフロー](media/bindings/output-binding-flow.png)

<span data-ttu-id="0a4f6-160">**図 8-3**。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-160">**Figure 8-3**.</span></span> <span data-ttu-id="0a4f6-161">Dapr の出力バインドフロー。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-161">Dapr output binding flow.</span></span>

1. <span data-ttu-id="0a4f6-162">Dapr サイドカーは、外部リソースへの接続方法に関する情報を使用して、バインド構成ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-162">The Dapr sidecar reads the binding configuration file with the information on how to connect to the external resource.</span></span> <span data-ttu-id="0a4f6-163">この例では、外部リソースは Twilio SMS アカウントです。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-163">In the example, the external resource is a Twilio SMS account.</span></span>
1. <span data-ttu-id="0a4f6-164">アプリケーションは `/v1.0/bindings/sms` Dapr サイドカーでエンドポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-164">Your application invokes the `/v1.0/bindings/sms` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="0a4f6-165">この場合は、HTTP POST を使用して API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-165">In this case, it uses an HTTP POST to invoke the API.</span></span> <span data-ttu-id="0a4f6-166">GRPC を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-166">It's also possible to use gRPC.</span></span>
1. <span data-ttu-id="0a4f6-167">Dapr サイドカーで実行されているバインディングコンポーネントは、メッセージを送信するために外部メッセージングシステムを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-167">The binding component running in the Dapr sidecar calls the external messaging system to send the message.</span></span> <span data-ttu-id="0a4f6-168">メッセージには、POST 要求で渡されたペイロードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-168">The message will contain the payload passed in the POST request.</span></span>

<span data-ttu-id="0a4f6-169">例として、curl を使用して Dapr API を呼び出すことにより、出力バインディングを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-169">As an example, you can invoke an output binding by invoking the Dapr API using curl:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/bindings/sms \
  -H "Content-Type: application/json" \
  -d '{
        "data": "Welcome to this awesome service",
        "metadata": {
          "toNumber": "555-3277"
        },
        "operation": "create"
      }'
```

<span data-ttu-id="0a4f6-170">HTTP ポートは、dapr サイドカー (この場合は既定の dapr HTTP ポート) で使用されているものと同じであることに注意して `3500` ください。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-170">Note that the HTTP port is the same as used by the Dapr sidecar (in this case, the default Dapr HTTP port `3500`).</span></span>

<span data-ttu-id="0a4f6-171">ペイロードの構造 (つまり、送信されたメッセージ) はバインドごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-171">The structure of the payload (that is, message sent) will vary per binding.</span></span> <span data-ttu-id="0a4f6-172">上記の例では、ペイロードにメッセージを含む要素が含まれてい `data` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-172">In the example above, the payload contains a `data` element with a message.</span></span> <span data-ttu-id="0a4f6-173">他の種類の外部リソースへのバインドは、特に送信されるメタデータに対して異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-173">Bindings to other types of external resources can be different, especially for the metadata that is sent.</span></span> <span data-ttu-id="0a4f6-174">各ペイロードには、バインディングが実行する操作を定義するフィールドも含まれている必要があり `operation` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-174">Each payload must also contain an `operation` field, that defines the operation the binding will execute.</span></span> <span data-ttu-id="0a4f6-175">上の例では、 `create` SMS メッセージを作成する操作を指定しています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-175">The above example specifies a `create` operation that creates the SMS message.</span></span> <span data-ttu-id="0a4f6-176">一般的な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-176">Common operations include:</span></span>

- <span data-ttu-id="0a4f6-177">create</span><span class="sxs-lookup"><span data-stu-id="0a4f6-177">create</span></span>
- <span data-ttu-id="0a4f6-178">get</span><span class="sxs-lookup"><span data-stu-id="0a4f6-178">get</span></span>
- <span data-ttu-id="0a4f6-179">delete</span><span class="sxs-lookup"><span data-stu-id="0a4f6-179">delete</span></span>
- <span data-ttu-id="0a4f6-180">list</span><span class="sxs-lookup"><span data-stu-id="0a4f6-180">list</span></span>

<span data-ttu-id="0a4f6-181">バインディングがサポートする操作をバインドの作成者が決定します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-181">It's up to the author of the binding which operations the binding supports.</span></span> <span data-ttu-id="0a4f6-182">各バインドのドキュメントでは、使用可能な操作とそれらを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-182">The documentation for each binding describes the available operations and how to invoke them.</span></span>

## <a name="using-the-dapr-net-sdk"></a><span data-ttu-id="0a4f6-183">Dapr .NET SDK の使用</span><span class="sxs-lookup"><span data-stu-id="0a4f6-183">Using the Dapr .NET SDK</span></span>

<span data-ttu-id="0a4f6-184">Dapr .NET SDK は、.NET Core 開発者向けの言語固有のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-184">The Dapr .NET SDK provides language-specific support for .NET Core developers.</span></span> <span data-ttu-id="0a4f6-185">次の例では、への呼び出し `HttpClient.PostAsync()` がメソッドに置き換えられてい `DaprClient.InvokeBindingAsync()` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-185">In the following example, the call to the `HttpClient.PostAsync()` is replaced with the `DaprClient.InvokeBindingAsync()` method.</span></span> <span data-ttu-id="0a4f6-186">この特殊なメソッドは、構成済みの出力バインディングの呼び出しを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-186">This specialized method simplifies invoking a configured output binding:</span></span>

```csharp
private async Task SendSMSAsync([FromServices] DaprClient daprClient)
{
    var message = "Welcome to this awesome service";
    var metadata = new Dictionary<string, string>
    {
      { "toNumber", "555-3277" }
    };
    await daprClient.InvokeBindingAsync("sms", "create", message, metadata);
}
```

<span data-ttu-id="0a4f6-187">メソッドは、との値を受け取り `metadata` `message` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-187">The method expects the `metadata` and `message` values.</span></span>

<span data-ttu-id="0a4f6-188">バインディングを呼び出すために使用する場合、は `DaprClient` gRPC を使用して dapr sidecar の DAPR API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-188">When used to invoke a binding, the `DaprClient` uses gRPC to call the Dapr API on the Dapr sidecar.</span></span>

## <a name="binding-components"></a><span data-ttu-id="0a4f6-189">バインド (コンポーネントを)</span><span class="sxs-lookup"><span data-stu-id="0a4f6-189">Binding components</span></span>

<span data-ttu-id="0a4f6-190">内部的には、リソースバインドは Dapr バインドコンポーネントと共に実装されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-190">Under the hood, resource bindings are implemented with Dapr binding components.</span></span> <span data-ttu-id="0a4f6-191">これらはコミュニティによって提供され、外出先で書かれています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-191">They're contributed by the community and written in Go.</span></span> <span data-ttu-id="0a4f6-192">Dapr バインドがまだ存在しない外部リソースと統合する必要がある場合は、自分で作成できます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-192">If you need to integrate with an external resource for which no Dapr binding exists yet, you can create it yourself.</span></span> <span data-ttu-id="0a4f6-193">「 [Dapr contrib リポジトリ](https://github.com/dapr/components-contrib) 」を参照して、バインドを投稿する方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-193">Check out the [Dapr components-contrib repo](https://github.com/dapr/components-contrib) to see how you can contribute a binding.</span></span>

> [!NOTE]
> <span data-ttu-id="0a4f6-194">Dapr とそのすべてのコンポーネントは、 [Golang](https://golang.org/) (ゴー) 言語で記述されています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-194">Dapr and all of its components are written in the [Golang](https://golang.org/) (Go) language.</span></span> <span data-ttu-id="0a4f6-195">ゴーは、最新のクラウドネイティブプログラミングプラットフォームと見なされます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-195">Go is considered a modern, cloud-native programming platform.</span></span>

<span data-ttu-id="0a4f6-196">バインドは、YAML 構成ファイルを使用して構成します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-196">You configure bindings using a YAML configuration file.</span></span> <span data-ttu-id="0a4f6-197">Twitter バインドの構成例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-197">Here's an example configuration for the Twitter binding:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: twitter-mention
  namespace: default
spec:
  type: bindings.twitter
  version: v1
  metadata:
  - name: consumerKey
    value: "****" # twitter api consumer key, required
  - name: consumerSecret
    value: "****" # twitter api consumer secret, required
  - name: accessToken
    value: "****" # twitter api access token, required
  - name: accessSecret
    value: "****" # twitter api access secret, required
  - name: query
    value: "dapr" # your search query, required
```

<span data-ttu-id="0a4f6-198">各バインド構成には、フィールドとフィールドを持つ一般的な要素が含まれてい `metadata` `name` `namespace` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-198">Each binding configuration contains a general `metadata` element with a `name` and `namespace` field.</span></span> <span data-ttu-id="0a4f6-199">Dapr は、構成されたフィールドに基づいて、サービスを呼び出すエンドポイントを決定し `name` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-199">Dapr will determine the endpoint to invoke your service based upon the configured `name` field.</span></span> <span data-ttu-id="0a4f6-200">上の例では、イベントが発生したときに、Dapr がサービスで注釈が付けられたメソッドを呼び出し `/twitter-mention` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-200">In the above example, Dapr will invoke the method annotated with `/twitter-mention` in your service when an event occurs.</span></span>

<span data-ttu-id="0a4f6-201">要素では、バインディング `spec` のとバインディング固有のを指定し `type` `metadata` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-201">In the `spec` element, you specify the `type` of the binding along with binding specific `metadata`.</span></span> <span data-ttu-id="0a4f6-202">この例では、API を使用して、Twitter アカウントにアクセスするための資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-202">The example specifies credentials for accessing a Twitter account using its API.</span></span> <span data-ttu-id="0a4f6-203">メタデータは、入力バインディングと出力バインドで異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-203">The metadata can differ between input and output bindings.</span></span> <span data-ttu-id="0a4f6-204">たとえば、Twitter を入力バインドとして使用するには、フィールドを使用してツイートで検索するテキストを指定する必要があり `query` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-204">For example, to use Twitter as an input binding, you need to specify the text to search for in tweets using the `query` field.</span></span> <span data-ttu-id="0a4f6-205">一致するツイートが送信されるたびに、dapr サイドカーは `/twitter-mention` サービスのエンドポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-205">Every time a matching tweet is sent, the Dapr sidecar will invoke the `/twitter-mention` endpoint on the service.</span></span> <span data-ttu-id="0a4f6-206">また、ツイートの内容も配信されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-206">It will also deliver the contents of the tweet.</span></span>

<span data-ttu-id="0a4f6-207">バインディングは、入力、出力、またはその両方に対して構成できます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-207">A binding can be configured for input, output, or both.</span></span> <span data-ttu-id="0a4f6-208">興味深いことに、バインドでは入力または出力の構成が明示的に指定されていません。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-208">Interestingly, the binding doesn't explicitly specify input or output configuration.</span></span> <span data-ttu-id="0a4f6-209">代わりに、バインドを構成値と共に使用して、方向が推論されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-209">Instead, the direction is inferred by the usage of the binding along with configuration values.</span></span>

<span data-ttu-id="0a4f6-210">[リソースバインドの Dapr ドキュメント] [1] には、使用可能なバインドとその特定の構成設定の完全な一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-210">The [Dapr documentation for resource bindings][1] provides a complete list of the available bindings and their specific configuration settings.</span></span>

### <a name="cron-binding"></a><span data-ttu-id="0a4f6-211">Cron バインド</span><span class="sxs-lookup"><span data-stu-id="0a4f6-211">Cron binding</span></span>

<span data-ttu-id="0a4f6-212">Dapr の Cron バインドに細心の注意を払ってください。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-212">Pay close attention to Dapr's Cron binding.</span></span> <span data-ttu-id="0a4f6-213">外部システムからのイベントをサブスクライブしません。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-213">It doesn't subscribe to events from an external system.</span></span> <span data-ttu-id="0a4f6-214">代わりに、このバインディングでは、構成可能な間隔スケジュールを使用してアプリケーションをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-214">Instead, this binding uses a configurable interval schedule to trigger your application.</span></span> <span data-ttu-id="0a4f6-215">バインディングを使用すると、バックグラウンドワーカーを実装して、一定の間隔で何らかの処理を実行するための簡単な方法を提供できます。これにより、構成可能な遅延で無限ループを実装する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-215">The binding provides a simple way to implement a background worker to wake up and do some work at a regular interval, without the need to implement an endless loop with a configurable delay.</span></span> <span data-ttu-id="0a4f6-216">Cron バインド構成の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-216">Here's an example of a Cron binding configuration:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: checkOrderBacklog
  namespace: default
spec:
  type: bindings.cron
  version: v1
  metadata:
  - name: schedule
    value: "@every 30m"
```

<span data-ttu-id="0a4f6-217">この例では、Dapr は、30分ごとにエンドポイントを呼び出すことによってサービスをトリガーし `/checkOrderBacklog` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-217">In this example, Dapr triggers a service by invoking the `/checkOrderBacklog` endpoint every 30 minutes.</span></span> <span data-ttu-id="0a4f6-218">値を指定するために使用できるパターンがいくつかあり `schedule` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-218">There are several patterns available for specifying the `schedule` value.</span></span> <span data-ttu-id="0a4f6-219">詳細については、 [Cron バインドのドキュメント](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-219">For more information, see the [Cron binding documentation](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/).</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="0a4f6-220">参照アプリケーション: eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="0a4f6-220">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="0a4f6-221">付随する eShopOnDapr reference アプリケーションは、出力バインディングの例を実装します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-221">The accompanying eShopOnDapr reference application implements an output binding example.</span></span> <span data-ttu-id="0a4f6-222">Dapr [Sendgrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) バインドをトリガーして、新しい注文が配置されたときにユーザーに電子メールを送信します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-222">It triggers the Dapr [SendGrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) binding to send a user an email when a new order is placed.</span></span> <span data-ttu-id="0a4f6-223">このバインドは、次のように、 `eshop-email.yaml` components フォルダー内のファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-223">You can find this binding in the `eshop-email.yaml` file in the components folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: sendmail
  namespace: eshop
spec:
  type: bindings.twilio.sendgrid
  version: v1
  metadata:
  - name: apiKey
    secretKeyRef:
      name: sendGridAPIKey
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="0a4f6-224">この構成では、 [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) バインドコンポーネントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-224">This configuration uses the [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) binding component.</span></span> <span data-ttu-id="0a4f6-225">サービスに接続するための API キーは、Dapr シークレットの参照を使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-225">Note how the API key for connecting to the service consumes a Dapr secret reference.</span></span> <span data-ttu-id="0a4f6-226">この方法では、シークレットが構成ファイルの外部に保持されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-226">This approach keeps secrets outside of the configuration file.</span></span> <span data-ttu-id="0a4f6-227">Dapr シークレットの詳細については、 [シークレットの構成ブロック](secrets.md) に関する章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-227">Read the [secrets building block chapter](secrets.md) to learn more about Dapr secrets.</span></span>

<span data-ttu-id="0a4f6-228">バインディング構成は、Dapr サイドカーのエンドポイントを使用して呼び出すことができるバインドコンポーネントを指定し `/sendmail` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-228">The binding configuration specifies a binding component that can be invoked using the `/sendmail` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="0a4f6-229">次のコードスニペットでは、注文が開始されるたびに電子メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-229">Here's a code snippet in which an email is sent whenever an order is started:</span></span>

```csharp
public Task Handle(OrderStartedDomainEvent notification, CancellationToken cancellationToken)
{
    var string message = CreateEmailBody(notification);
    var metadata = new Dictionary<string, string>
    {
        {"emailFrom", "eShopOn@dapr.io"},
        {"emailTo", notification.UserName},
        {"subject", $"Your eShopOnDapr order #{notification.Order.Id}"}
    };
    return _daprClient.InvokeBindingAsync("sendmail", "create", message, metadata, cancellationToken);
}
```

<span data-ttu-id="0a4f6-230">この例でわかるように、には `message` メッセージ本文が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-230">As you can see in this example, `message` contains the message body.</span></span> <span data-ttu-id="0a4f6-231">メソッドは、 `CreateEmailBody` 文字列の書式を、本文のテキストで単純にします。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-231">The `CreateEmailBody` method simply formats a string with the body text.</span></span> <span data-ttu-id="0a4f6-232">は、電子メール `metadata` メッセージの送信者、受信者、件名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-232">The `metadata` specifies the email sender, recipient, and the subject for the email message.</span></span> <span data-ttu-id="0a4f6-233">これらの値が静的である場合は、構成ファイルのメタデータフィールドにも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-233">If these values are static, they can also be included in the metadata fields in the configuration file.</span></span> <span data-ttu-id="0a4f6-234">呼び出すバインディングの名前はであり、 `sendmail` 操作は `create` です。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-234">The name of the binding to invoke is `sendmail` and the operation is `create`.</span></span>

## <a name="summary"></a><span data-ttu-id="0a4f6-235">まとめ</span><span class="sxs-lookup"><span data-stu-id="0a4f6-235">Summary</span></span>

<span data-ttu-id="0a4f6-236">Dapr リソースバインドを使用すると、ライブラリや Sdk に依存することなく、さまざまな外部リソースやシステムと統合できます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-236">Dapr resource bindings enable you to integrate with different external resources and systems without taking dependencies on their libraries or SDKs.</span></span> <span data-ttu-id="0a4f6-237">これらの外部システムは、必ずしも service bus やメッセージブローカーなどのメッセージングシステムである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-237">These external systems don't necessarily have to be messaging systems like a service bus or message broker.</span></span> <span data-ttu-id="0a4f6-238">また、データストアや web リソース (Twitter や SendGrid など) のバインドも存在します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-238">Bindings also exist for datastores and web resources like Twitter or SendGrid.</span></span>

<span data-ttu-id="0a4f6-239">入力バインド (トリガー) は、外部システムで発生するイベントに反応します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-239">Input bindings (or triggers) react to events occurring in an external system.</span></span> <span data-ttu-id="0a4f6-240">アプリケーションで事前に構成されているパブリック HTTP エンドポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-240">They invoke the public HTTP endpoints pre-configured in your application.</span></span> <span data-ttu-id="0a4f6-241">Dapr は、構成内のバインディングの名前を使用して、アプリケーションで呼び出すエンドポイントを決定します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-241">Dapr uses the name of the binding in the configuration to determine the endpoint to call in your application.</span></span>

<span data-ttu-id="0a4f6-242">出力バインドは、外部システムにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-242">Output bindings will send messages to an external system.</span></span> <span data-ttu-id="0a4f6-243">出力バインドをトリガーするには、Dapr サイドカーのエンドポイントで HTTP POST を実行し `/v1.0/bindings/<binding-name>` ます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-243">You trigger an output binding by doing an HTTP POST on the `/v1.0/bindings/<binding-name>` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="0a4f6-244">GRPC を使用してバインディングを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-244">You can also use gRPC to invoke the binding.</span></span> <span data-ttu-id="0a4f6-245">.NET SDK には、 `InvokeBindingAsync` gRPC を使用して Dapr バインドを呼び出すためのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-245">The .NET SDK offers a `InvokeBindingAsync` method to invoke Dapr bindings using gRPC.</span></span>

<span data-ttu-id="0a4f6-246">Dapr コンポーネントでバインドを実装します。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-246">You implement a binding with a Dapr component.</span></span> <span data-ttu-id="0a4f6-247">これらのコンポーネントは、コミュニティによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-247">These components are contributed by the community.</span></span> <span data-ttu-id="0a4f6-248">各バインドコンポーネントの構成には、抽象化する外部システムに固有のメタデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-248">Each binding component's configuration has metadata that is specific for the external system it abstracts.</span></span> <span data-ttu-id="0a4f6-249">また、サポートするコマンドとペイロードの構造は、バインドコンポーネントごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="0a4f6-249">Also, the commands it supports and the structure of the payload will differ per binding component.</span></span>

### <a name="references"></a><span data-ttu-id="0a4f6-250">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a4f6-250">References</span></span>

- [<span data-ttu-id="0a4f6-251">リソースバインドに関する dapr ドキュメント</span><span class="sxs-lookup"><span data-stu-id="0a4f6-251">Dapr documentation for resource bindings</span></span>](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/)

>[!div class="step-by-step"]
><span data-ttu-id="0a4f6-252">[前へ](publish-subscribe.md)
>[次へ](observability.md)</span><span class="sxs-lookup"><span data-stu-id="0a4f6-252">[Previous](publish-subscribe.md)
[Next](observability.md)</span></span>
