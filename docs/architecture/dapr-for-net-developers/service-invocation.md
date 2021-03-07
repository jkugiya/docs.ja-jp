---
title: Dapr サービス呼び出しのビルドブロック
description: サービス呼び出しの構成要素の説明、機能、利点、適用方法
author: amolenk
ms.date: 02/07/2021
ms.openlocfilehash: 2b64aa1e9b079a3fefe120e687cd6d395981c633
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401431"
---
# <a name="the-dapr-service-invocation-building-block"></a><span data-ttu-id="7046d-103">Dapr サービス呼び出しのビルドブロック</span><span class="sxs-lookup"><span data-stu-id="7046d-103">The Dapr service invocation building block</span></span>

<span data-ttu-id="7046d-104">分散システム全体で、1つのサービスが別のサービスと通信してビジネス操作を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7046d-104">Across a distributed system, one service often needs to communicate with another to complete a business operation.</span></span> <span data-ttu-id="7046d-105">[Dapr サービスの呼び出しの構成ブロック](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)は、サービス間の通信を効率化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7046d-105">The [Dapr service invocation building block](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/) can help streamline the communication between services.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="7046d-106">解決方法</span><span class="sxs-lookup"><span data-stu-id="7046d-106">What it solves</span></span>

<span data-ttu-id="7046d-107">分散アプリケーションでサービス間の呼び出しを行うのは簡単ですが、多くの課題が関係しています。</span><span class="sxs-lookup"><span data-stu-id="7046d-107">Making calls between services in a distributed application may appear easy, but there are many challenges involved.</span></span> <span data-ttu-id="7046d-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7046d-108">For example:</span></span>

- <span data-ttu-id="7046d-109">他のサービスが配置されている場所。</span><span class="sxs-lookup"><span data-stu-id="7046d-109">Where the other services are located.</span></span>
- <span data-ttu-id="7046d-110">サービスアドレスを指定してサービスを安全に呼び出す方法。</span><span class="sxs-lookup"><span data-stu-id="7046d-110">How to call a service securely, given the service address.</span></span>
- <span data-ttu-id="7046d-111">短時間の [一時的なエラー](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) が発生した場合の再試行の処理方法。</span><span class="sxs-lookup"><span data-stu-id="7046d-111">How to handle retries when short-lived [transient errors](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) occur.</span></span>

<span data-ttu-id="7046d-112">最後に、分散アプリケーションではさまざまなサービスが構成されるため、サービス呼び出しグラフ間で分析情報をキャプチャすることは、運用上の問題を診断するうえで非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="7046d-112">Lastly, as distributed applications compose many different services, capturing insights across service call graphs are critical to diagnosing production issues.</span></span>

<span data-ttu-id="7046d-113">サービス呼び出しの構成要素では、サービスの [リバースプロキシ](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) として dapr サイドカーを使用することによって、これらの課題に対処します。</span><span class="sxs-lookup"><span data-stu-id="7046d-113">The service invocation building block addresses these challenges by using a Dapr sidecar as a [reverse proxy](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) for your service.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="7046d-114">しくみ</span><span class="sxs-lookup"><span data-stu-id="7046d-114">How it works</span></span>

<span data-ttu-id="7046d-115">まず例を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="7046d-115">Let's start with an example.</span></span> <span data-ttu-id="7046d-116">"サービス A" と "サービス B" という2つのサービスを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="7046d-116">Consider two services, "Service A" and "Service B".</span></span> <span data-ttu-id="7046d-117">サービス A は、サービス B で API を呼び出す必要があり `catalog/items` ます。サービス A はサービス B への依存関係を取得し、それに直接呼び出しを行うことができますが、サービス a は代わりに Dapr sidecar でサービス呼び出し API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-117">Service A needs to call the `catalog/items` API on Service B. While Service A could take a dependency on Service B and make a direct call to it, Service A instead invokes the service invocation API on the Dapr sidecar.</span></span> <span data-ttu-id="7046d-118">図6-1 に、この操作を示します。</span><span class="sxs-lookup"><span data-stu-id="7046d-118">Figure 6-1 shows the operation.</span></span>

![Dapr サービスの呼び出しのしくみ](./media/service-invocation/service-invocation-flow.png)

<span data-ttu-id="7046d-120">**図 6-1**。</span><span class="sxs-lookup"><span data-stu-id="7046d-120">**Figure 6-1**.</span></span> <span data-ttu-id="7046d-121">Dapr サービスの呼び出しのしくみ。</span><span class="sxs-lookup"><span data-stu-id="7046d-121">How Dapr service invocation works.</span></span>

<span data-ttu-id="7046d-122">前の図の手順を確認します。</span><span class="sxs-lookup"><span data-stu-id="7046d-122">Note the steps from the previous figure:</span></span>

1. <span data-ttu-id="7046d-123">サービス A はサービス B のエンドポイントを呼び出します。サービスでサービス `catalog/items` 呼び出し API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-123">Service A makes a call to the `catalog/items` endpoint in Service B by invoking the service invocation API on the Service A sidecar.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7046d-124">サイドカーは、プラグ可能な名前解決メカニズムを使用して、サービス B のアドレスを解決します。自己ホスト型モードでは、Dapr は [mdn](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) を使用して検索します。</span><span class="sxs-lookup"><span data-stu-id="7046d-124">The sidecar uses a pluggable name resolution mechanism to resolve the address of Service B. In self-hosted mode, Dapr uses [mDNS](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) to find it.</span></span> <span data-ttu-id="7046d-125">Kubernetes モードで実行すると、Kubernetes DNS サービスによってアドレスが決定されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-125">When running in Kubernetes mode, the Kubernetes DNS service determines the address.</span></span>  

1. <span data-ttu-id="7046d-126">サービスは、サービス B に要求を転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-126">The Service A sidecar forwards the request to the Service B sidecar.</span></span>

1. <span data-ttu-id="7046d-127">サービス b はサービス `catalog/items` b API に対して実際の要求を行います。</span><span class="sxs-lookup"><span data-stu-id="7046d-127">The Service B sidecar makes the actual `catalog/items` request against the Service B API.</span></span>

1. <span data-ttu-id="7046d-128">サービス B は要求を実行し、応答を sidecar に返します。</span><span class="sxs-lookup"><span data-stu-id="7046d-128">Service B executes the request and returns a response back to its sidecar.</span></span>

1. <span data-ttu-id="7046d-129">サービス B サイドカーは、サービスに応答を転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-129">The Service B sidecar forwards the response back to the Service A sidecar.</span></span>

1. <span data-ttu-id="7046d-130">サービスは、サービス A に応答を返します。</span><span class="sxs-lookup"><span data-stu-id="7046d-130">The Service A sidecar returns the response back to Service A.</span></span>

<span data-ttu-id="7046d-131">呼び出しはサイドカーを通じてフローするので、Dapr は便利なクロスカット動作を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="7046d-131">Because the calls flow through sidecars, Dapr can inject some useful cross-cutting behaviors:</span></span>

- <span data-ttu-id="7046d-132">失敗したときに、自動的に呼び出しを再試行します。</span><span class="sxs-lookup"><span data-stu-id="7046d-132">Automatically retry calls upon failure.</span></span>
- <span data-ttu-id="7046d-133">証明書の自動ロールオーバーなど、相互 (mTLS) 認証を使用して、サービス間の呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="7046d-133">Make calls between services secure with mutual (mTLS) authentication, including automatic certificate rollover.</span></span>
- <span data-ttu-id="7046d-134">クライアントがアクセス制御ポリシーを使用して実行できる操作を制御します。</span><span class="sxs-lookup"><span data-stu-id="7046d-134">Control what operations clients can do using access control policies.</span></span>
- <span data-ttu-id="7046d-135">サービス間のすべての呼び出しのトレースとメトリックをキャプチャして、洞察と診断を提供します。</span><span class="sxs-lookup"><span data-stu-id="7046d-135">Capture traces and metrics for all calls between services to provide insights and diagnostics.</span></span>

<span data-ttu-id="7046d-136">すべてのアプリケーションは、dapr に組み込まれているネイティブ **呼び出し** API を使用して dapr サイドカーを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7046d-136">Any application can invoke a Dapr sidecar by using the native **invoke** API built into Dapr.</span></span> <span data-ttu-id="7046d-137">API は、HTTP または gRPC を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7046d-137">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="7046d-138">次の URL を使用して HTTP API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-138">Use the following URL to call the HTTP API:</span></span>

``` http
http://localhost:<dapr-port>/v1.0/invoke/<application-id>/method/<method-name>
```

- <span data-ttu-id="7046d-139">`<dapr-port>` Dapr がリッスンしている HTTP ポート。</span><span class="sxs-lookup"><span data-stu-id="7046d-139">`<dapr-port>` the HTTP port that Dapr is listening on.</span></span>
- <span data-ttu-id="7046d-140">`<application-id>` 呼び出すサービスのアプリケーション ID。</span><span class="sxs-lookup"><span data-stu-id="7046d-140">`<application-id>` application ID of the service to call.</span></span>
- <span data-ttu-id="7046d-141">`<method-name>` リモートサービスで呼び出すメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="7046d-141">`<method-name>` name of the method to invoke on the remote service.</span></span>

<span data-ttu-id="7046d-142">次の例では、  `catalog/items` の "GET" エンドポイントに対して curl 呼び出しが行われ `Service B` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-142">In the following example, a *curl* call is made to the `catalog/items` 'GET' endpoint of `Service B`:</span></span>

```console
curl http://localhost:3500/v1.0/invoke/serviceb/method/catalog/items
```

> [!NOTE]
> <span data-ttu-id="7046d-143">Dapr Api は、HTTP または gRPC をサポートするすべてのアプリケーションスタックで、Dapr 構成ブロックを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7046d-143">The Dapr APIs enable any application stack that supports HTTP or gRPC to use Dapr building blocks.</span></span> <span data-ttu-id="7046d-144">したがって、サービス呼び出しの構成ブロックは、プロトコル間のブリッジとして機能することができます。</span><span class="sxs-lookup"><span data-stu-id="7046d-144">Therefore, the service invocation building block can act as a bridge between protocols.</span></span> <span data-ttu-id="7046d-145">サービスは、HTTP、gRPC、またはその両方の組み合わせを使用して相互に通信できます。</span><span class="sxs-lookup"><span data-stu-id="7046d-145">Services can communicate with each other using HTTP, gRPC or a combination of both.</span></span>

<span data-ttu-id="7046d-146">次のセクションでは、.NET SDK を使用してサービス呼び出しを簡略化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7046d-146">In the next section, you'll learn how to use the .NET SDK to simplify service invocation calls.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="7046d-147">Dapr .NET SDK を使用する</span><span class="sxs-lookup"><span data-stu-id="7046d-147">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="7046d-148">Dapr [.NET SDK](https://github.com/dapr/dotnet-sdk) は、.net 開発者に、dapr と対話するための直感的で言語固有の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="7046d-148">The Dapr [.NET SDK](https://github.com/dapr/dotnet-sdk) provides .NET developers with an intuitive and language-specific way to interact with Dapr.</span></span> <span data-ttu-id="7046d-149">SDK は、リモートサービス呼び出しを行うための3つの方法を開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="7046d-149">The SDK offers developers three ways of making remote service invocation calls:</span></span>

1. <span data-ttu-id="7046d-150">HttpClient を使用して HTTP サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7046d-150">Invoke HTTP services using HttpClient</span></span>
1. <span data-ttu-id="7046d-151">DaprClient を使用して HTTP サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7046d-151">Invoke HTTP services using DaprClient</span></span>
1. <span data-ttu-id="7046d-152">DaprClient を使用して gRPC サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7046d-152">Invoke gRPC services using DaprClient</span></span>

### <a name="invoke-http-services-using-httpclient"></a><span data-ttu-id="7046d-153">HttpClient を使用して HTTP サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7046d-153">Invoke HTTP services using HttpClient</span></span>

<span data-ttu-id="7046d-154">HTTP エンドポイントを呼び出す方法としては、Dapr との豊富な統合を使用することをお勧めし `HttpClient` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-154">The preferred way to call an HTTP endpoint is to use Dapr's rich integration with `HttpClient`.</span></span> <span data-ttu-id="7046d-155">次の例では、アプリケーションのメソッドを呼び出して注文を送信し `submit` `orderservice` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-155">The following example submits an order by calling the `submit` method of the `orderservice` application:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient();
await httpClient.PostAsJsonAsync("http://orderservice/submit", order);
```

<span data-ttu-id="7046d-156">この例では、は `DaprClient.CreateHttpClient` `HttpClient` dapr サービスの呼び出しを実行するために使用されるインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="7046d-156">In the example, `DaprClient.CreateHttpClient` returns an `HttpClient` instance that is used to perform Dapr service invocation.</span></span> <span data-ttu-id="7046d-157">返されるは、 `HttpClient` 送信要求の uri を書き換える特別な Dapr メッセージハンドラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="7046d-157">The returned `HttpClient` uses a special Dapr message handler that rewrites URIs of outgoing requests.</span></span> <span data-ttu-id="7046d-158">ホスト名は、呼び出すサービスのアプリケーション ID として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-158">The host name is interpreted as the application ID of the service to call.</span></span> <span data-ttu-id="7046d-159">実際に呼び出される書き換えられた要求は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7046d-159">The rewritten request that's actually being called is:</span></span>

```http
http://127.0.0.1:3500/v1/invoke/orderservice/method/submit
```

<span data-ttu-id="7046d-160">この例では、Dapr HTTP エンドポイントの既定値であるを使用し `http://127.0.0.1:<dapr-http-port>/` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-160">This example uses the default value for the Dapr HTTP endpoint, which is `http://127.0.0.1:<dapr-http-port>/`.</span></span> <span data-ttu-id="7046d-161">の値 `dapr-http-port` は、環境変数から取得され `DAPR_HTTP_PORT` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-161">The value of `dapr-http-port` is taken from the `DAPR_HTTP_PORT` environment variable.</span></span> <span data-ttu-id="7046d-162">設定されていない場合は、既定のポート番号 `3500` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-162">If it's not set, the default port number `3500` is used.</span></span>

<span data-ttu-id="7046d-163">または、の呼び出しでカスタムエンドポイントを構成することもでき `DaprClient.CreateHttpClient` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-163">Alternatively, you can configure a custom endpoint in the call to `DaprClient.CreateHttpClient`:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient(daprEndpoint = "localhost:4000");
```

<span data-ttu-id="7046d-164">アプリケーション ID を指定して、ベースアドレスを直接設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7046d-164">You can also directly set the base address by specifying the application ID.</span></span> <span data-ttu-id="7046d-165">これにより、呼び出しを行うときに、相対 Uri を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7046d-165">This makes it possible to use relative URIs when making a call:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient("orderservice");
await httpClient.PostAsJsonAsync("/submit");
```

<span data-ttu-id="7046d-166">`HttpClient`オブジェクトは、有効期間が長いことを意図しています。</span><span class="sxs-lookup"><span data-stu-id="7046d-166">The `HttpClient` object is intended to be long-lived.</span></span> <span data-ttu-id="7046d-167">`HttpClient`アプリケーションの有効期間中、1つのインスタンスを再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="7046d-167">A single `HttpClient` instance can be reused for the lifetime of the application.</span></span> <span data-ttu-id="7046d-168">次のシナリオでは、 `OrderServiceClient` クラスが Dapr インスタンスを再利用する方法について説明し `HttpClient` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-168">The next scenario demonstrates how an `OrderServiceClient` class reuses a Dapr `HttpClient` instance:</span></span>  

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddSingleton<IOrderServiceClient, OrderServiceClient>(
        _ => new OrderServiceClient(DaprClient.CreateInvokeHttpClient("orderservice")));
}
```

<span data-ttu-id="7046d-169">上記のスニペットでは、は `OrderServiceClient` ASP.NET Core 依存関係の注入システムを使用してシングルトンとして登録されています。</span><span class="sxs-lookup"><span data-stu-id="7046d-169">In the snippet above, the `OrderServiceClient` is registered as a singleton with the ASP.NET Core dependency injection system.</span></span> <span data-ttu-id="7046d-170">実装ファクトリは、を `HttpClient` 呼び出すことによって新しいインスタンスを作成し `DaprClient.CreateInvokeHttpClient` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-170">An implementation factory creates a new `HttpClient` instance by calling `DaprClient.CreateInvokeHttpClient`.</span></span> <span data-ttu-id="7046d-171">次に、新しく作成されたを使用して `HttpClient` オブジェクトをインスタンス化し `OrderServiceClient` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-171">It then uses the newly created `HttpClient` to instantiate the `OrderServiceClient` object.</span></span> <span data-ttu-id="7046d-172">を `OrderServiceClient` シングルトンとして登録すると、アプリケーションの有効期間に再利用されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-172">By registering the `OrderServiceClient` as a singleton, it will be reused for the lifetime of the application.</span></span>

<span data-ttu-id="7046d-173">自体には、 `OrderServiceClient` Dapr 固有のコードがありません。</span><span class="sxs-lookup"><span data-stu-id="7046d-173">The `OrderServiceClient` itself has no Dapr-specific code.</span></span> <span data-ttu-id="7046d-174">Dapr サービスの呼び出しが内部で使用されていても、他の HttpClient と同様に Dapr HttpClient を扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="7046d-174">Even though Dapr service invocation is used under the hood, you can treat the Dapr HttpClient like any other HttpClient:</span></span>

```csharp
public class OrderServiceClient : IOrderServiceClient
{
    private readonly HttpClient _httpClient;

    public OrderServiceClient(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public async Task SubmitOrder(Order order)
    {
        var response = await _httpClient.PostAsJsonAsync("submit", order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="7046d-175">HttpClient クラスと Dapr サービスの呼び出しには、次のような多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="7046d-175">Using the HttpClient class with Dapr service invocation has many benefits:</span></span>

- <span data-ttu-id="7046d-176">HttpClient は、多くの開発者がコードで既に使用している、よく知られたクラスです。</span><span class="sxs-lookup"><span data-stu-id="7046d-176">HttpClient is a well-known class that many developers already use in their code.</span></span> <span data-ttu-id="7046d-177">Dapr サービスの呼び出しに HttpClient を使用すると、開発者は既存のスキルを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="7046d-177">Using HttpClient for Dapr service invocation allows developers to reuse their existing skills.</span></span>
- <span data-ttu-id="7046d-178">HttpClient は、カスタムヘッダーなどの高度なシナリオや、要求メッセージと応答メッセージを完全に制御する機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7046d-178">HttpClient supports advanced scenarios, such as custom headers, and full control over request and response messages.</span></span>
- <span data-ttu-id="7046d-179">.NET 5 では、HttpClient は System.Text.Jsを使用した自動シリアル化とシリアル化解除をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7046d-179">In .NET 5, HttpClient supports automatic serialization and deserialization using System.Text.Json.</span></span>
- <span data-ttu-id="7046d-180">HttpClient は、多くの既存のフレームワークやライブラリ (たとえば、"RestSharp ["、"](https://github.com/reactiveui/refit) [](https://restsharp.dev/getting-started/getting-started.html#basic-usage)"、" [polly](https://github.com/App-vNext/Polly)など) と統合されています。</span><span class="sxs-lookup"><span data-stu-id="7046d-180">HttpClient integrates with many existing frameworks and libraries, such as [Refit](https://github.com/reactiveui/refit), [RestSharp](https://restsharp.dev/getting-started/getting-started.html#basic-usage), and [Polly](https://github.com/App-vNext/Polly).</span></span>

### <a name="invoke-http-services-using-daprclient"></a><span data-ttu-id="7046d-181">DaprClient を使用して HTTP サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7046d-181">Invoke HTTP services using DaprClient</span></span>

<span data-ttu-id="7046d-182">HTTP セマンティクスを使用してサービスを呼び出すには、HttpClient を使用することをお勧めしますが、メソッドのファミリを使用することもでき `DaprClient.InvokeMethodAsync` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-182">While HttpClient is the preferred way to invoke services using HTTP semantics, you can also use the `DaprClient.InvokeMethodAsync` family of methods.</span></span> <span data-ttu-id="7046d-183">次の例では、アプリケーションのメソッドを呼び出して注文を送信し `submit` `orderservice` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-183">The following example submits an order by calling the `submit` method of the `orderservice` application:</span></span>

``` csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation =
        await daprClient.InvokeMethodAsync<Order, OrderConfirmation>(
            "orderservice", "submit", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

<span data-ttu-id="7046d-184">3番目の引数であるオブジェクトは、 `order` 内部で (を使用して) シリアル化され、 `System.Text.JsonSerializer` 要求ペイロードとして送信されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-184">The third argument, an `order` object, is serialized internally (with `System.Text.JsonSerializer`) and sent as the request payload.</span></span> <span data-ttu-id="7046d-185">.NET SDK は、sidecar の呼び出しを処理します。</span><span class="sxs-lookup"><span data-stu-id="7046d-185">The .NET SDK takes care of the call to the sidecar.</span></span> <span data-ttu-id="7046d-186">また、オブジェクトへの応答を逆シリアル化し `OrderConfirmation` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-186">It also deserializes the response to an `OrderConfirmation` object.</span></span> <span data-ttu-id="7046d-187">HTTP メソッドが指定されていないため、要求は HTTP POST として実行されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-187">Because no HTTP method is specified, the request is executed as an HTTP POST.</span></span>

<span data-ttu-id="7046d-188">次の例では、を指定して HTTP GET 要求を行う方法を示し `HttpMethod` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-188">The next example demonstrates how you can make an HTTP GET request by specifying the `HttpMethod`:</span></span>

```csharp
var catalogItems = await daprClient.InvokeMethodAsync<IEnumerable<CatalogItem>>(HttpMethod.Get, "catalogservice", "items");
```

<span data-ttu-id="7046d-189">シナリオによっては、要求メッセージをより詳細に制御する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="7046d-189">For some scenarios, you may require more control over the request message.</span></span> <span data-ttu-id="7046d-190">たとえば、要求ヘッダーを指定する必要がある場合、またはペイロードにカスタムシリアライザーを使用する場合などです。</span><span class="sxs-lookup"><span data-stu-id="7046d-190">For example, when you need to specify request headers, or you want to use a custom serializer for the payload.</span></span> <span data-ttu-id="7046d-191">`DaprClient.CreateInvokeMethodRequest` を作成 `HttpRequestMessage` します。</span><span class="sxs-lookup"><span data-stu-id="7046d-191">`DaprClient.CreateInvokeMethodRequest` creates an `HttpRequestMessage`.</span></span> <span data-ttu-id="7046d-192">次の例は、HTTP authorization ヘッダーを要求メッセージに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7046d-192">The following example demonstrates how to add an HTTP authorization header to a request message:</span></span>

```csharp
var request = daprClient.CreateInvokeMethodRequest("orderservice", "submit", order);
request.Headers.Authorization = new AuthenticationHeaderValue("bearer", token);
```

<span data-ttu-id="7046d-193">では、 `HttpRequestMessage` 次のプロパティが設定されました。</span><span class="sxs-lookup"><span data-stu-id="7046d-193">The `HttpRequestMessage` now has the following properties set:</span></span>

- <span data-ttu-id="7046d-194">Url = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`</span><span class="sxs-lookup"><span data-stu-id="7046d-194">Url = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`</span></span>
- <span data-ttu-id="7046d-195">HttpMethod = 投稿</span><span class="sxs-lookup"><span data-stu-id="7046d-195">HttpMethod = POST</span></span>
- <span data-ttu-id="7046d-196">Content =  `JsonContent` JSON でシリアル化されたオブジェクトを含むオブジェクト `order`</span><span class="sxs-lookup"><span data-stu-id="7046d-196">Content =  `JsonContent` object containing the JSON-serialized `order`</span></span>
- <span data-ttu-id="7046d-197">ヘッダー. Authorization = "ベアラー \<token> "</span><span class="sxs-lookup"><span data-stu-id="7046d-197">Headers.Authorization = "bearer \<token>"</span></span>

<span data-ttu-id="7046d-198">要求が希望どおりに設定されたら、を使用し `DaprClient.InvokeMethodAsync` て送信します。</span><span class="sxs-lookup"><span data-stu-id="7046d-198">Once you've got the request set up the way you want, use `DaprClient.InvokeMethodAsync` to send it:</span></span>

```csharp
var orderConfirmation = await daprClient.InvokeMethodAsync<OrderConfirmation>(request);
```

<span data-ttu-id="7046d-199">`DaprClient.InvokeMethodAsync` 要求が成功した場合は、オブジェクトへの応答を逆シリアル化し `OrderConfirmation` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-199">`DaprClient.InvokeMethodAsync` deserializes the response to an `OrderConfirmation` object if the request is successful.</span></span> <span data-ttu-id="7046d-200">または、を使用し `DaprClient.InvokeMethodWithResponseAsync` て、基になるへのフルアクセスを取得することもでき `HttpResponseMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-200">Alternatively, you can use `DaprClient.InvokeMethodWithResponseAsync` to get full access to the underlying `HttpResponseMessage`:</span></span>

```csharp
var response = await daprClient.InvokeMethodWithResponseAsync(request);
response.EnsureSuccessStatusCode();

var orderConfirmation = response.Content.ReadFromJsonAsync<OrderConfirmation>();
```

> [!NOTE]
> <span data-ttu-id="7046d-201">HTTP を使用したサービス呼び出しでは、前のセクションで説明した Dapr HttpClient 統合を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7046d-201">For service invocation calls using HTTP, it's worth considering using the Dapr HttpClient integration presented in the previous section.</span></span> <span data-ttu-id="7046d-202">HttpClient を使用すると、既存のフレームワークやライブラリとの統合などの追加の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="7046d-202">Using HttpClient gives you additional benefits such as integration with existing frameworks and libraries.</span></span>

### <a name="invoke-grpc-services-using-daprclient"></a><span data-ttu-id="7046d-203">DaprClient を使用して gRPC サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7046d-203">Invoke gRPC services using DaprClient</span></span>

<span data-ttu-id="7046d-204">DaprClient には、 `InvokeMethodGrpcAsync` gRPC エンドポイントを呼び出すための一連のメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7046d-204">DaprClient provides a family of `InvokeMethodGrpcAsync` methods for calling gRPC endpoints.</span></span> <span data-ttu-id="7046d-205">HTTP メソッドとの主な違いは、JSON ではなく Protobuf serializer を使用することです。</span><span class="sxs-lookup"><span data-stu-id="7046d-205">The main difference with the HTTP methods is the use of a Protobuf serializer instead of JSON.</span></span> <span data-ttu-id="7046d-206">次の例で `submitOrder` は、 `orderservice` grpc 上でのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-206">The following example invokes the `submitOrder` method of the `orderservice` over gRPC.</span></span>

```csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation = await daprClient.InvokeMethodGrpcAsync<Order, OrderConfirmation>("orderservice", "submitOrder", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

<span data-ttu-id="7046d-207">上の例では、DaprClient は Protobuf を使用して指定されたオブジェクトをシリアル化 `order` し、その結果を gRPC 要求本文として使用します。 [](https://developers.google.com/protocol-buffers)</span><span class="sxs-lookup"><span data-stu-id="7046d-207">In the example above, DaprClient serializes the given `order` object using [Protobuf](https://developers.google.com/protocol-buffers) and uses the result as the gRPC request body.</span></span> <span data-ttu-id="7046d-208">同様に、応答本文は Protobuf 逆シリアル化され、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-208">Likewise, the response body is Protobuf deserialized and returned to the caller.</span></span> <span data-ttu-id="7046d-209">Protobuf は、通常、HTTP サービスの呼び出しで使用される JSON ペイロードより優れたパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="7046d-209">Protobuf typically provides better performance than the JSON payloads used in HTTP service invocation.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="7046d-210">参照アプリケーション: eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="7046d-210">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="7046d-211">Microsoft の元の [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) マイクロサービス参照アーキテクチャでは、HTTP/REST と grpc サービスの組み合わせが使用されていました。</span><span class="sxs-lookup"><span data-stu-id="7046d-211">The original [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) microservice reference architecture from Microsoft used a mix of HTTP/REST and gRPC services.</span></span> <span data-ttu-id="7046d-212">GRPC の使用は、 [アグリゲーターサービス](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) とコアバックエンドサービス間の通信に限定されていました。</span><span class="sxs-lookup"><span data-stu-id="7046d-212">The use of gRPC was limited to communication between an [aggregator service](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) and core back-end services.</span></span> <span data-ttu-id="7046d-213">図6-2 は、アーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="7046d-213">Figure 6-2 show the architecture:</span></span>

![eShopOnContainers での gRPC と HTTP/REST 呼び出し](./media/service-invocation/eshop-on-containers.png)

<span data-ttu-id="7046d-215">**図 6-2**。</span><span class="sxs-lookup"><span data-stu-id="7046d-215">**Figure 6-2**.</span></span> <span data-ttu-id="7046d-216">eShopOnContainers で gRPC と HTTP/REST を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-216">gRPC and HTTP/REST calls in eShopOnContainers.</span></span>

<span data-ttu-id="7046d-217">前の図の手順を確認します。</span><span class="sxs-lookup"><span data-stu-id="7046d-217">Note the steps from the previous figure:</span></span>

1. <span data-ttu-id="7046d-218">フロントエンドは、HTTP/REST を使用して [API ゲートウェイ](/azure/architecture/microservices/design/gateway) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-218">The front end calls the [API gateway](/azure/architecture/microservices/design/gateway) using HTTP/REST.</span></span>

1. <span data-ttu-id="7046d-219">API ゲートウェイは、HTTP/REST を使用して単純な [CRUD](https://www.sumologic.com/glossary/crud/) (作成、読み取り、更新、削除) 要求を直接コアバックエンドサービスに転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-219">The API gateway forwards simple [CRUD](https://www.sumologic.com/glossary/crud/) (Create, Read, Update, Delete) requests directly to a core back-end service using HTTP/REST.</span></span>

1. <span data-ttu-id="7046d-220">API ゲートウェイは、複数のバックエンドサービスへの連携呼び出しを伴う複雑な要求を web ショッピングアグリゲーターサービスに転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-220">The API gateway forwards complex requests that involve coordinated calls to multiple back-end services to the web shopping aggregator service.</span></span>

1. <span data-ttu-id="7046d-221">アグリゲーターサービスは gRPC を使用して、コアバックエンドサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-221">The aggregator service uses gRPC to call core back-end services.</span></span>

<span data-ttu-id="7046d-222">最近更新された eShopOnDapr 実装では、Dapr sidecars サービスと API ゲートウェイに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-222">In the recently updated eShopOnDapr implementation, Dapr sidecars are added to the services and API gateway.</span></span> <span data-ttu-id="7046d-223">図6-3 は、更新されたアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="7046d-223">Figure 6-3 show the updated architecture:</span></span>

![eShopOnContainers での gRPC と HTTP/REST 呼び出し](./media/service-invocation/eshop-on-dapr.png)

<span data-ttu-id="7046d-225">**図 6-3**。</span><span class="sxs-lookup"><span data-stu-id="7046d-225">**Figure 6-3**.</span></span> <span data-ttu-id="7046d-226">Dapr を使用して eShop アーキテクチャを更新しました。</span><span class="sxs-lookup"><span data-stu-id="7046d-226">Updated eShop architecture using Dapr.</span></span>

<span data-ttu-id="7046d-227">前の図の更新された手順に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7046d-227">Note the updated steps from the previous figure:</span></span>

1. <span data-ttu-id="7046d-228">フロントエンドは引き続き HTTP/REST を使用して API ゲートウェイを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-228">The front end still uses HTTP/REST to call the API gateway.</span></span>

1. <span data-ttu-id="7046d-229">API ゲートウェイは、HTTP 要求を Dapr サイドカーに転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-229">The API gateway forwards HTTP requests to its Dapr sidecar.</span></span>

1. <span data-ttu-id="7046d-230">API ゲートウェイのサイドカーは、アグリゲーターまたはバックエンドサービスのサイドカーに要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="7046d-230">The API gateway sidecar sends the request to the sidecar of the aggregator or back-end service.</span></span>

1. <span data-ttu-id="7046d-231">アグリゲーターサービスは dapr .net SDK を使用して、サイドカーアーキテクチャを通じてバックエンドサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7046d-231">The aggregator service uses the Dapr .NET SDK to call back-end services through their sidecar architecture.</span></span>

<span data-ttu-id="7046d-232">Dapr は、gRPC との間の呼び出しを実装します。</span><span class="sxs-lookup"><span data-stu-id="7046d-232">Dapr implements calls between sidecars with gRPC.</span></span> <span data-ttu-id="7046d-233">したがって、HTTP/REST セマンティクスを使用してリモートサービスを起動している場合でも、トランスポートの一部は gRPC を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-233">So even if you're invoking a remote service with HTTP/REST semantics, a part of the transport is still implemented using gRPC.</span></span>

<span data-ttu-id="7046d-234">EShopOnDapr 参照アプリケーションは、Dapr サービス呼び出しの構成要素の恩恵を得ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-234">The eShopOnDapr reference application benefits from the Dapr service invocation building block.</span></span> <span data-ttu-id="7046d-235">サービスの検出、自動 mTLS、可観測性などの利点があります。</span><span class="sxs-lookup"><span data-stu-id="7046d-235">The benefits include service discovery, automatic mTLS, and observability.</span></span>

### <a name="forward-http-requests-using-envoy-and-dapr"></a><span data-ttu-id="7046d-236">エンボイと Dapr を使用した HTTP 要求の転送</span><span class="sxs-lookup"><span data-stu-id="7046d-236">Forward HTTP requests using Envoy and Dapr</span></span>

<span data-ttu-id="7046d-237">元と更新された eShop アプリケーションはどちらも、API ゲートウェイとして [エンボイプロキシ](https://www.envoyproxy.io/) を利用します。</span><span class="sxs-lookup"><span data-stu-id="7046d-237">Both the original and updated eShop application leverage the [Envoy proxy](https://www.envoyproxy.io/) as an API gateway.</span></span> <span data-ttu-id="7046d-238">エンボイは、オープンソースのプロキシと通信バスで、最新の分散アプリケーションで広く使われています。</span><span class="sxs-lookup"><span data-stu-id="7046d-238">Envoy is an open-source proxy and communication bus that is popular across modern distributed applications.</span></span> <span data-ttu-id="7046d-239">これから、エンボイは [クラウドネイティブコンピューティングファンデーション](https://www.cncf.io/)によって所有および管理されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-239">Originating from Lyft, Envoy is owned and maintained by the [Cloud-Native Computing Foundation](https://www.cncf.io/).</span></span>

<span data-ttu-id="7046d-240">元の eShopOnContainers 実装では、エンボイ API ゲートウェイは、受信 HTTP 要求をアグリゲーターまたはバックエンドサービスに直接転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-240">In the original eShopOnContainers implementation, the Envoy API gateway forwarded incoming HTTP requests directly to aggregator or back-end services.</span></span> <span data-ttu-id="7046d-241">新しい eShopOnDapr では、エンボイプロキシが Dapr sidecar に要求を転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-241">In the new eShopOnDapr, the Envoy proxy forwards the request to a Dapr sidecar.</span></span> <span data-ttu-id="7046d-242">サイドカーは、サービスの呼び出し、mTLS、可観測性を提供します。</span><span class="sxs-lookup"><span data-stu-id="7046d-242">The sidecar provides service invocation, mTLS, and observability.</span></span>

<span data-ttu-id="7046d-243">エンボイは、プロキシの動作を制御するために YAML 定義ファイルを使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="7046d-243">Envoy is configured using a YAML definition file to control the proxy's behavior.</span></span> <span data-ttu-id="7046d-244">エンボイが HTTP 要求を dapr サイドカーコンテナーに転送できるようにするには、 `dapr` 構成にクラスターを追加します。</span><span class="sxs-lookup"><span data-stu-id="7046d-244">To enable Envoy to forward HTTP requests to a Dapr sidecar container, a `dapr` cluster is added to the configuration.</span></span> <span data-ttu-id="7046d-245">クラスター構成には、dapr サイドカーがリッスンしている HTTP ポートを指すホストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7046d-245">The cluster configuration contains a host that points to the HTTP port on which the Dapr sidecar is listening:</span></span>

``` yaml
clusters:
- name: dapr
  connect_timeout: 0.25s
  type: strict_dns
  hosts:
  - socket_address:
    address: 127.0.0.1
    port_value: 3500
```

<span data-ttu-id="7046d-246">次のように、エンボイルートの構成が更新され、受信要求が dapr サイドカーの呼び出しとして書き換えられます (キーと値のペアに注意して `prefix_rewrite` ください)。</span><span class="sxs-lookup"><span data-stu-id="7046d-246">The Envoy routes configuration is updated to rewrite incoming requests as calls to the Dapr sidecar (pay close attention to the `prefix_rewrite` key/value pair):</span></span>

``` yaml
- name: "c-short"
  match:
    prefix: "/c/"
  route:
    auto_host_rewrite: true
    prefix_rewrite: "/v1.0/invoke/catalog-api/method/"
    cluster: dapr
```

<span data-ttu-id="7046d-247">フロントエンドクライアントがカタログ項目の一覧を取得するシナリオについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="7046d-247">Consider a scenario where the front-end client wants to retrieve a list of catalog items.</span></span> <span data-ttu-id="7046d-248">Catalog API は、カタログアイテムを取得するためのエンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="7046d-248">The Catalog API provides an endpoint for getting the catalog items:</span></span>

``` csharp
[Route("api/v1/[controller]")]
[ApiController]
public class CatalogController : ControllerBase
{
    [HttpGet("items")]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery] int pageSize = 10,
        [FromQuery] int pageIndex = 0)
    {
        // ...
    }
```

<span data-ttu-id="7046d-249">まず、フロントエンドは、エンボイ API ゲートウェイに直接 HTTP 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="7046d-249">First, the front end makes a direct HTTP call to the Envoy API gateway.</span></span>

```
GET http://<api-gateway>/c/api/v1/catalog/items?pageSize=20
```

<span data-ttu-id="7046d-250">エンボイプロキシはルートに一致し、HTTP 要求を書き換えて、 `invoke` Dapr sidecar の API に転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-250">The Envoy proxy matches the route, rewrites the HTTP request, and forwards it to the `invoke` API of its Dapr sidecar:</span></span>

```
GET http://127.0.0.1:3500/v1.0/invoke/catalog-api/method/api/v1/catalog/items?pageSize=20
```

<span data-ttu-id="7046d-251">サイドカーはサービス検出を処理し、カタログ API サイドカーに要求をルーティングします。</span><span class="sxs-lookup"><span data-stu-id="7046d-251">The sidecar handles service discovery and routes the request to the Catalog API sidecar.</span></span> <span data-ttu-id="7046d-252">最後に、サイドカーは catalog API を呼び出して要求を実行し、カタログ項目をフェッチして、応答を返します。</span><span class="sxs-lookup"><span data-stu-id="7046d-252">Finally, the sidecar calls the Catalog API to execute the request, fetch catalog items, and return a response:</span></span>

```
GET http://localhost/api/v1/catalog/items?pageSize=20
```

### <a name="make-aggregated-service-calls-using-the-net-sdk"></a><span data-ttu-id="7046d-253">.NET SDK を使用して集計されたサービスの呼び出しを行う</span><span class="sxs-lookup"><span data-stu-id="7046d-253">Make aggregated service calls using the .NET SDK</span></span>

<span data-ttu-id="7046d-254">EShop フロントエンドからのほとんどの呼び出しは単純な CRUD 呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="7046d-254">Most calls from the eShop front end are simple CRUD calls.</span></span> <span data-ttu-id="7046d-255">API ゲートウェイは、処理のためにそれらを1つのサービスに転送します。</span><span class="sxs-lookup"><span data-stu-id="7046d-255">The API gateway forwards them to a single service for processing.</span></span> <span data-ttu-id="7046d-256">ただし、一部のシナリオでは、要求を完了するために複数のバックエンドサービスを連携させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7046d-256">Some scenarios, however, require multiple back-end services to work together to complete a request.</span></span> <span data-ttu-id="7046d-257">これらのより複雑な呼び出しでは、web ショッピングアグリゲーターサービスを使用して、複数のサービスにわたってワークフローを仲介します。</span><span class="sxs-lookup"><span data-stu-id="7046d-257">For these more complex calls, eShop uses the web shopping aggregator service to mediate the workflow across multiple services.</span></span> <span data-ttu-id="7046d-258">図6-4 は、買い物かごに商品を追加する処理シーケンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="7046d-258">Figure 6-4 show the processing sequence of adding an item to your shopping basket:</span></span>

![バスケットのシーケンス図を更新する](./media/service-invocation/complex-call.png)

<span data-ttu-id="7046d-260">**図 6-4**。</span><span class="sxs-lookup"><span data-stu-id="7046d-260">**Figure 6-4**.</span></span> <span data-ttu-id="7046d-261">買い物かごのシーケンスを更新します。</span><span class="sxs-lookup"><span data-stu-id="7046d-261">Update shopping basket sequence.</span></span>

<span data-ttu-id="7046d-262">アグリゲーターサービスは、最初に catalog API からカタログアイテムを取得します。</span><span class="sxs-lookup"><span data-stu-id="7046d-262">The aggregator service first retrieves catalog items from the Catalog API.</span></span> <span data-ttu-id="7046d-263">次に、アイテムの可用性と価格を検証します。</span><span class="sxs-lookup"><span data-stu-id="7046d-263">It then validates item availability and pricing.</span></span> <span data-ttu-id="7046d-264">最後に、アグリゲーターサービスは、バスケット API を呼び出すことによって、更新された買い物かごを保存します。</span><span class="sxs-lookup"><span data-stu-id="7046d-264">Finally, the aggregator service saves the updated shopping basket by calling the Basket API.</span></span>

<span data-ttu-id="7046d-265">アグリゲーターサービスには、 `BasketController` 買い物かごを更新するためのエンドポイントを提供するが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7046d-265">The aggregator service contains a `BasketController` that provides an endpoint for updating the shopping basket:</span></span>

``` csharp
[Route("api/v1/[controller]")]
[Authorize]
[ApiController]
public class BasketController : ControllerBase
{
    private readonly ICatalogService _catalog;
    private readonly IBasketService _basket;

    [HttpPost]
    [HttpPut]
    public async Task<ActionResult<BasketData>> UpdateAllBasketAsync(
        [FromBody] UpdateBasketRequest data, [FromHeader] string authorization)
    {
        // Get the item details from the catalog API.
        var catalogItems = await _catalog.GetCatalogItemsAsync(
            data.Items.Select(x => x.ProductId));

        // Check item availability and prices; store results in basket object.
        var basket = CreateValidatedBasket(data, catalogItems);

        // Save the shopping basket.
        await _basket.UpdateAsync(basket, authorization);

        return basket;
    }

    // ...
}
```

<span data-ttu-id="7046d-266">メソッドは、 `UpdateAllBasketAsync` 属性を使用して受信要求の *承認* ヘッダーを取得し `FromHeader` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-266">The `UpdateAllBasketAsync` method gets the *Authorization* header of the incoming request using a `FromHeader` attribute.</span></span> <span data-ttu-id="7046d-267">*Authorization* ヘッダーには、保護されたバックエンドサービスを呼び出すために必要なアクセストークンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7046d-267">The *Authorization* header contains the access token that is needed to call protected back-end services.</span></span>

<span data-ttu-id="7046d-268">バスケットを更新する要求を受信すると、アグリゲーターサービスはカタログ API を呼び出して項目の詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="7046d-268">After receiving a request to update the basket, the aggregator service calls the Catalog API to get the item details.</span></span> <span data-ttu-id="7046d-269">バスケットコントローラーは、挿入されたオブジェクトを使用して `ICatalogService` その呼び出しを行い、カタログ API と通信します。</span><span class="sxs-lookup"><span data-stu-id="7046d-269">The Basket controller uses an injected `ICatalogService` object to make that call and communicate with the Catalog API.</span></span> <span data-ttu-id="7046d-270">インターフェイスの元の実装で gRPC を使用して呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="7046d-270">The original implementation of the interface used gRPC to make the call.</span></span> <span data-ttu-id="7046d-271">更新された実装では、HttpClient サポートで Dapr サービスの呼び出しを使用します。</span><span class="sxs-lookup"><span data-stu-id="7046d-271">The updated implementation uses Dapr service invocation with HttpClient support:</span></span>

``` csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public Task<IEnumerable<CatalogItem>> GetCatalogItemsAsync(IEnumerable<int> ids)
    {
        var requestUri = $"api/v1/catalog/items?ids={string.Join(",", ids)}";

        return _httpClient.GetFromJsonAsync<IEnumerable<CatalogItem>>(requestUri);
    }

    // ...
}
```

<span data-ttu-id="7046d-272">サービス呼び出しを行うために、Dapr 固有のコードが必要ないことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="7046d-272">Notice how no Dapr specific code is required to make the service invocation call.</span></span> <span data-ttu-id="7046d-273">すべての通信は、標準の HttpClient オブジェクトを使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="7046d-273">All communication is done using the standard HttpClient object.</span></span>

<span data-ttu-id="7046d-274">Dapr HttpClient は、メソッドのクラスに挿入され `CatalogService` `Startup.ConfigureServices` ます。</span><span class="sxs-lookup"><span data-stu-id="7046d-274">The Dapr HttpClient is injected into the `CatalogService` class in the `Startup.ConfigureServices` method:</span></span>

```csharp
services.AddSingleton<ICatalogService, CatalogService>(
    _ => new CatalogService(DaprClient.CreateInvokeHttpClient("catalog-api")));
```

<span data-ttu-id="7046d-275">アグリゲーターサービスによって実行されるもう1つの呼び出しは、バスケット API に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="7046d-275">The other call made by the aggregator service is to the Basket API.</span></span> <span data-ttu-id="7046d-276">承認された要求のみを許可します。</span><span class="sxs-lookup"><span data-stu-id="7046d-276">It only allows authorized requests.</span></span> <span data-ttu-id="7046d-277">アクセストークンは *承認* 要求ヘッダーと共に渡され、呼び出しが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="7046d-277">The access token is passed along in an *Authorization* request header to ensure the call succeeds:</span></span>

``` csharp
public class BasketService : IBasketService
{
    public Task UpdateAsync(BasketData currentBasket, string accessToken)
    {
        var request = new HttpRequestMessage(HttpMethod.Post, "api/v1/basket")
        {
            Content = JsonContent.Create(currentBasket)
        };
        request.Headers.Authorization = new AuthenticationHeaderValue(accessToken);

        var response = await _httpClient.SendAsync(request);
        response.EnsureSuccessStatusCode();
    }

    // ...
}
```

<span data-ttu-id="7046d-278">この例でも、サービスを呼び出すために使用されるのは、標準の HttpClient 機能だけです。</span><span class="sxs-lookup"><span data-stu-id="7046d-278">In this example too, only standard HttpClient functionality is used to call the service.</span></span> <span data-ttu-id="7046d-279">これにより、既に HttpClient を使い慣れている開発者は、既存のスキルを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="7046d-279">This allows developers who are already familiar with HttpClient to reuse their existing skills.</span></span> <span data-ttu-id="7046d-280">また、既存の HttpClient コードでは、変更を加えずに Dapr サービスの呼び出しを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7046d-280">It even enables existing HttpClient code to use Dapr service invocation without making any changes.</span></span>

## <a name="summary"></a><span data-ttu-id="7046d-281">まとめ</span><span class="sxs-lookup"><span data-stu-id="7046d-281">Summary</span></span>

<span data-ttu-id="7046d-282">この章では、サービス呼び出しのビルドブロックについて学習しました。</span><span class="sxs-lookup"><span data-stu-id="7046d-282">In this chapter, you learned about the service invocation building block.</span></span> <span data-ttu-id="7046d-283">ここでは、Dapr sidecar に対して直接 HTTP 呼び出しを行うことと、Dapr .NET SDK を使用して、リモートメソッドを呼び出す方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="7046d-283">You saw how to invoke remote methods both by making direct HTTP calls to the Dapr sidecar, and by using the Dapr .NET SDK.</span></span>

<span data-ttu-id="7046d-284">Dapr .NET SDK には、リモートメソッドを呼び出すための複数の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7046d-284">The Dapr .NET SDK provides multiple ways to invoke remote methods.</span></span> <span data-ttu-id="7046d-285">HttpClient のサポートは、既存のスキルを再利用する開発者にとって優れており、既存の多くのフレームワークやライブラリと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="7046d-285">HttpClient support is great for developers wanting to reuse existing skills and is compatible with many existing frameworks and libraries.</span></span> <span data-ttu-id="7046d-286">DaprClient は、HTTP または gRPC セマンティクスを使用して Dapr サービス呼び出し API を直接使用するためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="7046d-286">DaprClient offers support for directly using the Dapr service invocation API using either HTTP or gRPC semantics.</span></span>

<span data-ttu-id="7046d-287">EShopOnDapr 参照アーキテクチャは、Dapr サービスの呼び出しを使用して、元の eShopOnContainers ソリューションが最新である方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7046d-287">The eShopOnDapr reference architecture shows how the original eShopOnContainers solution is modernized by using Dapr service invocation.</span></span> <span data-ttu-id="7046d-288">EShop に Dapr を追加すると、自動再試行、mTLS を使用したメッセージの暗号化、改善された可観測性などの利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="7046d-288">Adding Dapr to eShop provides benefits such as automatic retries, message encryption using mTLS, and improved observability.</span></span>

### <a name="references"></a><span data-ttu-id="7046d-289">関連項目</span><span class="sxs-lookup"><span data-stu-id="7046d-289">References</span></span>

- [<span data-ttu-id="7046d-290">Dapr サービス呼び出しの構成ブロック</span><span class="sxs-lookup"><span data-stu-id="7046d-290">Dapr service invocation building block</span></span>](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/)

- [<span data-ttu-id="7046d-291">分散型クラウドネイティブアプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="7046d-291">Monitoring distributed cloud-native applications</span></span>](../cloud-native/observability-patterns.md)

> [!div class="step-by-step"]
> <span data-ttu-id="7046d-292">[前へ](state-management.md)
> [次へ](publish-subscribe.md)</span><span class="sxs-lookup"><span data-stu-id="7046d-292">[Previous](state-management.md)
[Next](publish-subscribe.md)</span></span>
