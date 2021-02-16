---
title: IHttpClientFactory を使用して回復力の高い HTTP 要求を実装する
description: .NET Core 2.1 以降で使用できる IHttpClientFactory を使用して、`HttpClient` インスタンスを作成し、それをアプリケーションで簡単に使用できるようにする方法について説明します。
ms.date: 01/13/2021
ms.openlocfilehash: fc5da088b1ed7573532dff101aff03d39a02a6f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429313"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="87bf0-103">IHttpClientFactory を使用して回復力の高い HTTP 要求を実装する</span><span class="sxs-lookup"><span data-stu-id="87bf0-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="87bf0-104"><xref:System.Net.Http.IHttpClientFactory> はコントラクトであり、ご利用のアプリケーションで使用する <xref:System.Net.Http.HttpClient> インスタンスを作成するために .NET Core 2.1 以降で使用できる自己主張の強いファクトリ `DefaultHttpClientFactory` によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net"></a><span data-ttu-id="87bf0-105">.NET で使用可能な元の HttpClient クラスに関する問題</span><span class="sxs-lookup"><span data-stu-id="87bf0-105">Issues with the original HttpClient class available in .NET</span></span>

<span data-ttu-id="87bf0-106">よく知られている元の <xref:System.Net.Http.HttpClient> クラスは、簡単に使用できますが、場合によっては、多くの開発者が適切に使用していません。</span><span class="sxs-lookup"><span data-stu-id="87bf0-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="87bf0-107">このクラスでは `IDisposable` が実装されますが、これを `using` ステートメント内で宣言およびインスタンス化することはお勧めできません。その理由は、`HttpClient` オブジェクトが破棄されても、基になるソケットがすぐに解放されず、"_ソケットの枯渇_" の問題が発生する可能性があるということにあります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-107">Though this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="87bf0-108">この問題の詳細については、ブログ記事「[HttpClient の誤った使い方がソフトウェアを不安定にする](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87bf0-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="87bf0-109">そのため、`HttpClient` は一度インスタンス化されたら、アプリケーションの有効期間にわたって再利用されることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="87bf0-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="87bf0-110">すべての要求に対して `HttpClient` クラスをインスタンス化すると、高負荷の下で使用可能なソケットの数が枯渇してしまいます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="87bf0-111">この問題により、`SocketException` エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="87bf0-112">この問題を解決するために可能なアプローチは、HttpClient クライアントの使用に関するこの [Microsoft の記事](../../../csharp/tutorials/console-webapiclient.md)で説明されているように、`HttpClient` オブジェクトをシングルトンまたは静的として作成することに基づいています。</span><span class="sxs-lookup"><span data-stu-id="87bf0-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="87bf0-113">これは、1 日に数回実行される有効期間の短いコンソールアプリまたは類似のものに適したソリューションとなります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-113">This can be a good solution for short-lived console apps or similar, that run a few times a day.</span></span>

<span data-ttu-id="87bf0-114">開発者が遭遇するもう 1 つの問題は、長時間実行されるプロセスで `HttpClient` の共有インスタンスを使用するタイミングです。</span><span class="sxs-lookup"><span data-stu-id="87bf0-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long-running processes.</span></span> <span data-ttu-id="87bf0-115">HttpClient がシングルトンまたは静的オブジェクトとしてインスタンス化される状況では、dotnet/runtime GitHub リポジトリのこちらの[問題](https://github.com/dotnet/runtime/issues/18348)で説明されているように、DNS の変更を処理できません。</span><span class="sxs-lookup"><span data-stu-id="87bf0-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/runtime/issues/18348) of the dotnet/runtime GitHub repository.</span></span>

<span data-ttu-id="87bf0-116">ただし、この問題は実際には `HttpClient` にあるのではなく、[HttpClient の既定のコンストラクター](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)にあります。理由として、それによって、前述の "*ソケット枯渇*" および DNS 変更の問題を抱える、<xref:System.Net.Http.HttpMessageHandler> の新しい具象インスタンスが作成されるということが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="87bf0-117">上記の問題に対処し、`HttpClient` インスタンスを管理しやすくするために、.NET Core 2.1 では、<xref:System.Net.Http.IHttpClientFactory> インターフェイスが導入されました。これを使用すれば、依存関係の挿入 (DI) を介してアプリ内で `HttpClient` インスタンスを構成および作成することができます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="87bf0-118">HttpClient でのハンドラーのデリゲートを利用するために、Polly ベースのミドルウェアに対する拡張機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="87bf0-119">[Polly](https://thepollyproject.azurewebsites.net/) は、事前に定義されたポリシーを緩やかでスレッドセーフな方法で使用することにより、開発者がアプリケーションに回復性を追加できるようにするための一時的な障害処理ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="87bf0-119">[Polly](https://thepollyproject.azurewebsites.net/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="87bf0-120">IHttpClientFactory を使用する利点</span><span class="sxs-lookup"><span data-stu-id="87bf0-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="87bf0-121"><xref:System.Net.Http.IHttpClientFactory> の現在の実装 (これによって <xref:System.Net.Http.IHttpMessageHandlerFactory> も実装される) には、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="87bf0-122">論理 `HttpClient` オブジェクトの名前付けと構成を行うために、中央の場所が提供されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="87bf0-123">たとえば、特定のマイクロサービスにアクセスするために事前に構成されているクライアント (サービス エージェント) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="87bf0-124">`HttpClient` でのハンドラーのデリゲートにより送信ミドルウェアの概念を体系化し、Polly ベースのミドルウェアを実装して、回復性のための Polly のポリシーを利用します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="87bf0-125">`HttpClient` は既に、送信 HTTP 要求用にリンクできるハンドラーのデリゲートの概念を備えています。</span><span class="sxs-lookup"><span data-stu-id="87bf0-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="87bf0-126">ファクトリに HTTP クライアントを登録できるほか、Polly ハンドラーを使用して、再試行、サーキット ブレーカーなどに Polly ポリシーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="87bf0-127"><xref:System.Net.Http.HttpMessageHandler> の有効期間を管理して、`HttpClient` の有効期間を自分で管理する際に発生する可能性がある上記の問題を回避します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="87bf0-128">DI によって挿入された `HttpClient` インスタンスは、関連付けられた `HttpMessageHandler` がファクトリによって管理されるため、安全に破棄できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="87bf0-129">実際、挿入された `HttpClient` インスタンスは、DI パースペクティブから "*範囲指定*" されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="87bf0-130">`IHttpClientFactory` の実装 (`DefaultHttpClientFactory`) は、`Microsoft.Extensions.DependencyInjection` NuGet パッケージ内の DI の実装に緊密に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="87bf0-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="87bf0-131">その他の DI コンテナーの使用に関する詳細については、こちらの [GitHub のディスカッション](https://github.com/dotnet/extensions/issues/1345)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87bf0-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="87bf0-132">IHttpClientFactory を使用する複数の方法</span><span class="sxs-lookup"><span data-stu-id="87bf0-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="87bf0-133">アプリケーションで `IHttpClientFactory` を使用するには、複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="87bf0-134">基本的な使用方法</span><span class="sxs-lookup"><span data-stu-id="87bf0-134">Basic usage</span></span>
- <span data-ttu-id="87bf0-135">名前付きクライアントを使用する</span><span class="sxs-lookup"><span data-stu-id="87bf0-135">Use Named Clients</span></span>
- <span data-ttu-id="87bf0-136">型指定されたクライアントを使用する</span><span class="sxs-lookup"><span data-stu-id="87bf0-136">Use Typed Clients</span></span>
- <span data-ttu-id="87bf0-137">生成されたクライアントを使用する</span><span class="sxs-lookup"><span data-stu-id="87bf0-137">Use Generated Clients</span></span>

<span data-ttu-id="87bf0-138">簡潔にするために、このガイダンスでは、型指定されたクライアント (サービス エージェント パターン) を使用する、`IHttpClientFactory` を使用するための最も構造化された方法を示します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="87bf0-139">しかし、オプションはすべてドキュメント化されており、現在、[`IHttpClientFactory` の使用方法が記載されたこちらの記事](/aspnet/core/fundamentals/http-requests#consumption-patterns)で一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="87bf0-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="87bf0-140">IHttpClientFactory で型指定されたクライアントを使用する方法</span><span class="sxs-lookup"><span data-stu-id="87bf0-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="87bf0-141">それでは、"型指定されたクライアント" とは何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="87bf0-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="87bf0-142">これは、特定の用途に合わせて事前に構成された `HttpClient` にすぎません。</span><span class="sxs-lookup"><span data-stu-id="87bf0-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="87bf0-143">この構成には、ベース サーバー、HTTP ヘッダー、またはタイムアウトなどの特定の値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="87bf0-144">次の図は、`IHttpClientFactory` で型指定されたクライアントを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="87bf0-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![IHttpClientFactory で型指定されたクライアントを使用する方法を示している図。](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="87bf0-146">**図 8-4**</span><span class="sxs-lookup"><span data-stu-id="87bf0-146">**Figure 8-4**.</span></span> <span data-ttu-id="87bf0-147">型指定されたクライアント クラスで `IHttpClientFactory` を使用する</span><span class="sxs-lookup"><span data-stu-id="87bf0-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="87bf0-148">上の図では、(コントローラーまたはクライアント コードによって使用される) `ClientService` によって、登録済みの `IHttpClientFactory` によって作成された `HttpClient` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="87bf0-149">このファクトリでは、プールからの `HttpClient` が `HttpMessageHandler` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="87bf0-150">拡張メソッド <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> を使用して `IHttpClientFactory` を DI コンテナーに登録するときに、Polly のポリシーを使用して `HttpClient` を構成できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A>.</span></span>

<span data-ttu-id="87bf0-151">上の構造を構成するには、<xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> に対する <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> 拡張メソッドを含む `Microsoft.Extensions.Http` NuGet パッケージをインストールすることで、アプリケーションに <xref:System.Net.Http.IHttpClientFactory> を追加します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="87bf0-152">この拡張メソッドでは、インターフェイス `IHttpClientFactory` のシングルトンとして使用される内部 `DefaultHttpClientFactory` クラスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="87bf0-153">これは <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> の一時的な構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="87bf0-154">プールから取得されたこのメッセージ ハンドラー (<xref:System.Net.Http.HttpMessageHandler> オブジェクト) は、ファクトリから返された `HttpClient` によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="87bf0-155">次のコードで、`AddHttpClient()` を使用して、`HttpClient` を使用する必要がある型指定されたクライアント (エージェント サービス) を登録する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="87bf0-156">前のコードに示されているように、クライアント サービスを登録すると、`DefaultClientFactory` によって、サービスごとに標準の `HttpClient` が作成されるようになります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="87bf0-157">また、次のコードに示すように、登録にインスタンス固有の構成を追加し、ベース アドレスの構成や回復性ポリシーの追加などを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="87bf0-158">例として、次のコードで上記のポリシーの 1 つを確認できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="87bf0-159">[次の記事](implement-http-call-retries-exponential-backoff-polly.md)では、Polly の使用に関する詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="87bf0-160">HttpClient の有効期間</span><span class="sxs-lookup"><span data-stu-id="87bf0-160">HttpClient lifetimes</span></span>

<span data-ttu-id="87bf0-161">`IHttpClientFactory` から `HttpClient` オブジェクトを取得するたび、新しいインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="87bf0-162">ただし、各 `HttpClient` では、`HttpMessageHandler` の有効期間が切れていない限り、リソースの消費量を減らすために `IHttpClientFactory` によってプールおよび再利用されている `HttpMessageHandler` を使用します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="87bf0-163">通常各ハンドラーは基になる HTTP 接続を独自に管理しており、必要以上に多くのハンドラーを作成すると接続が遅延する可能性があるため、ハンドラーをプールするのは望ましい方法です。</span><span class="sxs-lookup"><span data-stu-id="87bf0-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="87bf0-164">また、一部のハンドラーは接続を無期限に開いており、DNS の変更にハンドラーが対応できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="87bf0-165">プール内の `HttpMessageHandler` オブジェクトには、有効期間があります。この有効期間は、プール内の `HttpMessageHandler` インスタンスを再利用できる期間です。</span><span class="sxs-lookup"><span data-stu-id="87bf0-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="87bf0-166">既定値は 2 分ですが、型指定されたクライアントごとにオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="87bf0-167">オーバーライドするには、次のコードに示すように、クライアント作成時に返された <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> で `SetHandlerLifetime()` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="87bf0-168">型指定された各クライアントには、独自の構成済みハンドラーの有効期間の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="87bf0-169">ハンドラーの有効期限を無効にするには、有効期間を `InfiniteTimeSpan` に設定します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="87bf0-170">挿入された構成済みの HttpClient を使用する、型指定されたクライアント クラスを実装する</span><span class="sxs-lookup"><span data-stu-id="87bf0-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="87bf0-171">前の手順では、型指定されたクライアント クラス (サンプル コードにある、'BasketService'、'CatalogService'、'OrderingService' のようなクラスなど) が定義されている必要がありました。型指定されたクライアントは、(そのコンストラクターを通じて挿入された) `HttpClient` オブジェクトを受け取り、それを使用していくつかのリモート HTTP サービスを呼び出すクラスです。</span><span class="sxs-lookup"><span data-stu-id="87bf0-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="87bf0-172">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-172">For example:</span></span>

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take,
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl,
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

<span data-ttu-id="87bf0-173">型指定されたクライアント (この例では `CatalogService`) は、依存関係の挿入 (DI) によってアクティブ化されます。つまり `HttpClient` だけでなく、そのコンストラクター内に登録されている任意のサービスを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), that means it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="87bf0-174">型指定されたクライアントは実質的に一時的なオブジェクトであるため、新しいインスタンスは必要になるたびに作成されます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-174">A Typed Client is effectively a transient object, that means a new instance is created each time one is needed.</span></span> <span data-ttu-id="87bf0-175">作成されるたびに、新しい `HttpClient` インスタンスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-175">It receives a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="87bf0-176">ただし、プール内の `HttpMessageHandler` オブジェクトは、複数の `HttpClient` 要求で再利用されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="87bf0-176">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="87bf0-177">型指定されたクライアント クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="87bf0-177">Use your Typed Client classes</span></span>

<span data-ttu-id="87bf0-178">最後に、型指定されたクラスを実装したら、`AddHttpClient()` に登録して構成できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-178">Finally, once you have your typed classes implemented, you can have them registered and configured with `AddHttpClient()`.</span></span> <span data-ttu-id="87bf0-179">その後、DI によってサービスが挿入される場所であればどこでもそれらを使用できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-179">After that you can use them wherever have services injected by DI.</span></span> <span data-ttu-id="87bf0-180">たとえば、次の eShopOnContainers のコードのように、Razor ページ コード、または MVC Web アプリのコントローラーなどがあります。</span><span class="sxs-lookup"><span data-stu-id="87bf0-180">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) =>
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied,
                                               int? TypesFilterApplied,
                                               int? page,
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0,
                                                            itemsPage,
                                                            BrandFilterApplied,
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

<span data-ttu-id="87bf0-181">この時点で、上記のコードスニペットには、通常の HTTP 要求を実行する例のみが示されています。</span><span class="sxs-lookup"><span data-stu-id="87bf0-181">Up to this point, the above code snippet has only shown the example of performing regular HTTP requests.</span></span> <span data-ttu-id="87bf0-182">ただし、この "魔法" は、`HttpClient` によって行われるすべての HTTP 要求に、エクスポネンシャル バックオフによる再試行、回路遮断器、認証トークンを使用したセキュリティ機能、さらにはその他のあらゆるカスタム機能など、回復性があるポリシーが与えられるしくみについて説明する後続のセクションで登場します。</span><span class="sxs-lookup"><span data-stu-id="87bf0-182">But the 'magic' comes in the following sections where it shows how all the HTTP requests made by `HttpClient`, can have resilient policies such as retries with exponential backoff, circuit breakers, security features using auth tokens, or even any other custom feature.</span></span> <span data-ttu-id="87bf0-183">いずれも、ポリシーを追加し、登録済みの型指定されたクライアントにハンドラーを委任するだけで完了できます。</span><span class="sxs-lookup"><span data-stu-id="87bf0-183">And all of these can be done just by adding policies and delegating handlers to your registered Typed Clients.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="87bf0-184">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="87bf0-184">Additional resources</span></span>

- <span data-ttu-id="87bf0-185">**.NET で HttpClientFactory を使用する**</span><span class="sxs-lookup"><span data-stu-id="87bf0-185">**Using HttpClientFactory in .NET**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="87bf0-186">**`dotnet/extensions` GitHub リポジトリ内の HttpClientFactory ソース コード**</span><span class="sxs-lookup"><span data-stu-id="87bf0-186">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/v3.1.8/src/HttpClientFactory>

- <span data-ttu-id="87bf0-187">**Polly (.NET の復元および一時的な障害処理ライブラリ)**</span><span class="sxs-lookup"><span data-stu-id="87bf0-187">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://thepollyproject.azurewebsites.net/>
  
- <span data-ttu-id="87bf0-188">**依存関係挿入なしで IHttpClientFactory を使用する (GitHub の問題)**</span><span class="sxs-lookup"><span data-stu-id="87bf0-188">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="87bf0-189">[前へ](implement-resilient-entity-framework-core-sql-connections.md)
>[次へ](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="87bf0-189">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
