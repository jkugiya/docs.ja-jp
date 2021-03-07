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
# <a name="the-dapr-service-invocation-building-block"></a>Dapr サービス呼び出しのビルドブロック

分散システム全体で、1つのサービスが別のサービスと通信してビジネス操作を完了する必要があります。 [Dapr サービスの呼び出しの構成ブロック](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)は、サービス間の通信を効率化するのに役立ちます。

## <a name="what-it-solves"></a>解決方法

分散アプリケーションでサービス間の呼び出しを行うのは簡単ですが、多くの課題が関係しています。 次に例を示します。

- 他のサービスが配置されている場所。
- サービスアドレスを指定してサービスを安全に呼び出す方法。
- 短時間の [一時的なエラー](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) が発生した場合の再試行の処理方法。

最後に、分散アプリケーションではさまざまなサービスが構成されるため、サービス呼び出しグラフ間で分析情報をキャプチャすることは、運用上の問題を診断するうえで非常に重要です。

サービス呼び出しの構成要素では、サービスの [リバースプロキシ](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) として dapr サイドカーを使用することによって、これらの課題に対処します。

## <a name="how-it-works"></a>しくみ

まず例を見てみましょう。 "サービス A" と "サービス B" という2つのサービスを考えてみましょう。 サービス A は、サービス B で API を呼び出す必要があり `catalog/items` ます。サービス A はサービス B への依存関係を取得し、それに直接呼び出しを行うことができますが、サービス a は代わりに Dapr sidecar でサービス呼び出し API を呼び出します。 図6-1 に、この操作を示します。

![Dapr サービスの呼び出しのしくみ](./media/service-invocation/service-invocation-flow.png)

**図 6-1**。 Dapr サービスの呼び出しのしくみ。

前の図の手順を確認します。

1. サービス A はサービス B のエンドポイントを呼び出します。サービスでサービス `catalog/items` 呼び出し API を呼び出します。

    > [!NOTE]
    > サイドカーは、プラグ可能な名前解決メカニズムを使用して、サービス B のアドレスを解決します。自己ホスト型モードでは、Dapr は [mdn](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) を使用して検索します。 Kubernetes モードで実行すると、Kubernetes DNS サービスによってアドレスが決定されます。  

1. サービスは、サービス B に要求を転送します。

1. サービス b はサービス `catalog/items` b API に対して実際の要求を行います。

1. サービス B は要求を実行し、応答を sidecar に返します。

1. サービス B サイドカーは、サービスに応答を転送します。

1. サービスは、サービス A に応答を返します。

呼び出しはサイドカーを通じてフローするので、Dapr は便利なクロスカット動作を挿入できます。

- 失敗したときに、自動的に呼び出しを再試行します。
- 証明書の自動ロールオーバーなど、相互 (mTLS) 認証を使用して、サービス間の呼び出しを行います。
- クライアントがアクセス制御ポリシーを使用して実行できる操作を制御します。
- サービス間のすべての呼び出しのトレースとメトリックをキャプチャして、洞察と診断を提供します。

すべてのアプリケーションは、dapr に組み込まれているネイティブ **呼び出し** API を使用して dapr サイドカーを呼び出すことができます。 API は、HTTP または gRPC を使用して呼び出すことができます。 次の URL を使用して HTTP API を呼び出します。

``` http
http://localhost:<dapr-port>/v1.0/invoke/<application-id>/method/<method-name>
```

- `<dapr-port>` Dapr がリッスンしている HTTP ポート。
- `<application-id>` 呼び出すサービスのアプリケーション ID。
- `<method-name>` リモートサービスで呼び出すメソッドの名前。

次の例では、  `catalog/items` の "GET" エンドポイントに対して curl 呼び出しが行われ `Service B` ます。

```console
curl http://localhost:3500/v1.0/invoke/serviceb/method/catalog/items
```

> [!NOTE]
> Dapr Api は、HTTP または gRPC をサポートするすべてのアプリケーションスタックで、Dapr 構成ブロックを使用できるようにします。 したがって、サービス呼び出しの構成ブロックは、プロトコル間のブリッジとして機能することができます。 サービスは、HTTP、gRPC、またはその両方の組み合わせを使用して相互に通信できます。

次のセクションでは、.NET SDK を使用してサービス呼び出しを簡略化する方法について説明します。

## <a name="use-the-dapr-net-sdk"></a>Dapr .NET SDK を使用する

Dapr [.NET SDK](https://github.com/dapr/dotnet-sdk) は、.net 開発者に、dapr と対話するための直感的で言語固有の方法を提供します。 SDK は、リモートサービス呼び出しを行うための3つの方法を開発者に提供します。

1. HttpClient を使用して HTTP サービスを呼び出す
1. DaprClient を使用して HTTP サービスを呼び出す
1. DaprClient を使用して gRPC サービスを呼び出す

### <a name="invoke-http-services-using-httpclient"></a>HttpClient を使用して HTTP サービスを呼び出す

HTTP エンドポイントを呼び出す方法としては、Dapr との豊富な統合を使用することをお勧めし `HttpClient` ます。 次の例では、アプリケーションのメソッドを呼び出して注文を送信し `submit` `orderservice` ます。

```csharp
var httpClient = DaprClient.CreateHttpClient();
await httpClient.PostAsJsonAsync("http://orderservice/submit", order);
```

この例では、は `DaprClient.CreateHttpClient` `HttpClient` dapr サービスの呼び出しを実行するために使用されるインスタンスを返します。 返されるは、 `HttpClient` 送信要求の uri を書き換える特別な Dapr メッセージハンドラーを使用します。 ホスト名は、呼び出すサービスのアプリケーション ID として解釈されます。 実際に呼び出される書き換えられた要求は次のとおりです。

```http
http://127.0.0.1:3500/v1/invoke/orderservice/method/submit
```

この例では、Dapr HTTP エンドポイントの既定値であるを使用し `http://127.0.0.1:<dapr-http-port>/` ます。 の値 `dapr-http-port` は、環境変数から取得され `DAPR_HTTP_PORT` ます。 設定されていない場合は、既定のポート番号 `3500` が使用されます。

または、の呼び出しでカスタムエンドポイントを構成することもでき `DaprClient.CreateHttpClient` ます。

```csharp
var httpClient = DaprClient.CreateHttpClient(daprEndpoint = "localhost:4000");
```

アプリケーション ID を指定して、ベースアドレスを直接設定することもできます。 これにより、呼び出しを行うときに、相対 Uri を使用できるようになります。

```csharp
var httpClient = DaprClient.CreateHttpClient("orderservice");
await httpClient.PostAsJsonAsync("/submit");
```

`HttpClient`オブジェクトは、有効期間が長いことを意図しています。 `HttpClient`アプリケーションの有効期間中、1つのインスタンスを再利用することができます。 次のシナリオでは、 `OrderServiceClient` クラスが Dapr インスタンスを再利用する方法について説明し `HttpClient` ます。  

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddSingleton<IOrderServiceClient, OrderServiceClient>(
        _ => new OrderServiceClient(DaprClient.CreateInvokeHttpClient("orderservice")));
}
```

上記のスニペットでは、は `OrderServiceClient` ASP.NET Core 依存関係の注入システムを使用してシングルトンとして登録されています。 実装ファクトリは、を `HttpClient` 呼び出すことによって新しいインスタンスを作成し `DaprClient.CreateInvokeHttpClient` ます。 次に、新しく作成されたを使用して `HttpClient` オブジェクトをインスタンス化し `OrderServiceClient` ます。 を `OrderServiceClient` シングルトンとして登録すると、アプリケーションの有効期間に再利用されます。

自体には、 `OrderServiceClient` Dapr 固有のコードがありません。 Dapr サービスの呼び出しが内部で使用されていても、他の HttpClient と同様に Dapr HttpClient を扱うことができます。

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

HttpClient クラスと Dapr サービスの呼び出しには、次のような多くの利点があります。

- HttpClient は、多くの開発者がコードで既に使用している、よく知られたクラスです。 Dapr サービスの呼び出しに HttpClient を使用すると、開発者は既存のスキルを再利用できます。
- HttpClient は、カスタムヘッダーなどの高度なシナリオや、要求メッセージと応答メッセージを完全に制御する機能をサポートしています。
- .NET 5 では、HttpClient は System.Text.Jsを使用した自動シリアル化とシリアル化解除をサポートしています。
- HttpClient は、多くの既存のフレームワークやライブラリ (たとえば、"RestSharp ["、"](https://github.com/reactiveui/refit) [](https://restsharp.dev/getting-started/getting-started.html#basic-usage)"、" [polly](https://github.com/App-vNext/Polly)など) と統合されています。

### <a name="invoke-http-services-using-daprclient"></a>DaprClient を使用して HTTP サービスを呼び出す

HTTP セマンティクスを使用してサービスを呼び出すには、HttpClient を使用することをお勧めしますが、メソッドのファミリを使用することもでき `DaprClient.InvokeMethodAsync` ます。 次の例では、アプリケーションのメソッドを呼び出して注文を送信し `submit` `orderservice` ます。

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

3番目の引数であるオブジェクトは、 `order` 内部で (を使用して) シリアル化され、 `System.Text.JsonSerializer` 要求ペイロードとして送信されます。 .NET SDK は、sidecar の呼び出しを処理します。 また、オブジェクトへの応答を逆シリアル化し `OrderConfirmation` ます。 HTTP メソッドが指定されていないため、要求は HTTP POST として実行されます。

次の例では、を指定して HTTP GET 要求を行う方法を示し `HttpMethod` ます。

```csharp
var catalogItems = await daprClient.InvokeMethodAsync<IEnumerable<CatalogItem>>(HttpMethod.Get, "catalogservice", "items");
```

シナリオによっては、要求メッセージをより詳細に制御する必要がある場合があります。 たとえば、要求ヘッダーを指定する必要がある場合、またはペイロードにカスタムシリアライザーを使用する場合などです。 `DaprClient.CreateInvokeMethodRequest` を作成 `HttpRequestMessage` します。 次の例は、HTTP authorization ヘッダーを要求メッセージに追加する方法を示しています。

```csharp
var request = daprClient.CreateInvokeMethodRequest("orderservice", "submit", order);
request.Headers.Authorization = new AuthenticationHeaderValue("bearer", token);
```

では、 `HttpRequestMessage` 次のプロパティが設定されました。

- Url = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`
- HttpMethod = 投稿
- Content =  `JsonContent` JSON でシリアル化されたオブジェクトを含むオブジェクト `order`
- ヘッダー. Authorization = "ベアラー \<token> "

要求が希望どおりに設定されたら、を使用し `DaprClient.InvokeMethodAsync` て送信します。

```csharp
var orderConfirmation = await daprClient.InvokeMethodAsync<OrderConfirmation>(request);
```

`DaprClient.InvokeMethodAsync` 要求が成功した場合は、オブジェクトへの応答を逆シリアル化し `OrderConfirmation` ます。 または、を使用し `DaprClient.InvokeMethodWithResponseAsync` て、基になるへのフルアクセスを取得することもでき `HttpResponseMessage` ます。

```csharp
var response = await daprClient.InvokeMethodWithResponseAsync(request);
response.EnsureSuccessStatusCode();

var orderConfirmation = response.Content.ReadFromJsonAsync<OrderConfirmation>();
```

> [!NOTE]
> HTTP を使用したサービス呼び出しでは、前のセクションで説明した Dapr HttpClient 統合を使用することを検討してください。 HttpClient を使用すると、既存のフレームワークやライブラリとの統合などの追加の利点が得られます。

### <a name="invoke-grpc-services-using-daprclient"></a>DaprClient を使用して gRPC サービスを呼び出す

DaprClient には、 `InvokeMethodGrpcAsync` gRPC エンドポイントを呼び出すための一連のメソッドが用意されています。 HTTP メソッドとの主な違いは、JSON ではなく Protobuf serializer を使用することです。 次の例で `submitOrder` は、 `orderservice` grpc 上でのメソッドを呼び出します。

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

上の例では、DaprClient は Protobuf を使用して指定されたオブジェクトをシリアル化 `order` し、その結果を gRPC 要求本文として使用します。 [](https://developers.google.com/protocol-buffers) 同様に、応答本文は Protobuf 逆シリアル化され、呼び出し元に返されます。 Protobuf は、通常、HTTP サービスの呼び出しで使用される JSON ペイロードより優れたパフォーマンスを提供します。

## <a name="reference-application-eshopondapr"></a>参照アプリケーション: eShopOnDapr

Microsoft の元の [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) マイクロサービス参照アーキテクチャでは、HTTP/REST と grpc サービスの組み合わせが使用されていました。 GRPC の使用は、 [アグリゲーターサービス](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) とコアバックエンドサービス間の通信に限定されていました。 図6-2 は、アーキテクチャを示しています。

![eShopOnContainers での gRPC と HTTP/REST 呼び出し](./media/service-invocation/eshop-on-containers.png)

**図 6-2**。 eShopOnContainers で gRPC と HTTP/REST を呼び出します。

前の図の手順を確認します。

1. フロントエンドは、HTTP/REST を使用して [API ゲートウェイ](/azure/architecture/microservices/design/gateway) を呼び出します。

1. API ゲートウェイは、HTTP/REST を使用して単純な [CRUD](https://www.sumologic.com/glossary/crud/) (作成、読み取り、更新、削除) 要求を直接コアバックエンドサービスに転送します。

1. API ゲートウェイは、複数のバックエンドサービスへの連携呼び出しを伴う複雑な要求を web ショッピングアグリゲーターサービスに転送します。

1. アグリゲーターサービスは gRPC を使用して、コアバックエンドサービスを呼び出します。

最近更新された eShopOnDapr 実装では、Dapr sidecars サービスと API ゲートウェイに追加されます。 図6-3 は、更新されたアーキテクチャを示しています。

![eShopOnContainers での gRPC と HTTP/REST 呼び出し](./media/service-invocation/eshop-on-dapr.png)

**図 6-3**。 Dapr を使用して eShop アーキテクチャを更新しました。

前の図の更新された手順に注意してください。

1. フロントエンドは引き続き HTTP/REST を使用して API ゲートウェイを呼び出します。

1. API ゲートウェイは、HTTP 要求を Dapr サイドカーに転送します。

1. API ゲートウェイのサイドカーは、アグリゲーターまたはバックエンドサービスのサイドカーに要求を送信します。

1. アグリゲーターサービスは dapr .net SDK を使用して、サイドカーアーキテクチャを通じてバックエンドサービスを呼び出します。

Dapr は、gRPC との間の呼び出しを実装します。 したがって、HTTP/REST セマンティクスを使用してリモートサービスを起動している場合でも、トランスポートの一部は gRPC を使用して実装されます。

EShopOnDapr 参照アプリケーションは、Dapr サービス呼び出しの構成要素の恩恵を得ます。 サービスの検出、自動 mTLS、可観測性などの利点があります。

### <a name="forward-http-requests-using-envoy-and-dapr"></a>エンボイと Dapr を使用した HTTP 要求の転送

元と更新された eShop アプリケーションはどちらも、API ゲートウェイとして [エンボイプロキシ](https://www.envoyproxy.io/) を利用します。 エンボイは、オープンソースのプロキシと通信バスで、最新の分散アプリケーションで広く使われています。 これから、エンボイは [クラウドネイティブコンピューティングファンデーション](https://www.cncf.io/)によって所有および管理されます。

元の eShopOnContainers 実装では、エンボイ API ゲートウェイは、受信 HTTP 要求をアグリゲーターまたはバックエンドサービスに直接転送します。 新しい eShopOnDapr では、エンボイプロキシが Dapr sidecar に要求を転送します。 サイドカーは、サービスの呼び出し、mTLS、可観測性を提供します。

エンボイは、プロキシの動作を制御するために YAML 定義ファイルを使用して構成されます。 エンボイが HTTP 要求を dapr サイドカーコンテナーに転送できるようにするには、 `dapr` 構成にクラスターを追加します。 クラスター構成には、dapr サイドカーがリッスンしている HTTP ポートを指すホストが含まれています。

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

次のように、エンボイルートの構成が更新され、受信要求が dapr サイドカーの呼び出しとして書き換えられます (キーと値のペアに注意して `prefix_rewrite` ください)。

``` yaml
- name: "c-short"
  match:
    prefix: "/c/"
  route:
    auto_host_rewrite: true
    prefix_rewrite: "/v1.0/invoke/catalog-api/method/"
    cluster: dapr
```

フロントエンドクライアントがカタログ項目の一覧を取得するシナリオについて考えてみます。 Catalog API は、カタログアイテムを取得するためのエンドポイントを提供します。

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

まず、フロントエンドは、エンボイ API ゲートウェイに直接 HTTP 呼び出しを行います。

```
GET http://<api-gateway>/c/api/v1/catalog/items?pageSize=20
```

エンボイプロキシはルートに一致し、HTTP 要求を書き換えて、 `invoke` Dapr sidecar の API に転送します。

```
GET http://127.0.0.1:3500/v1.0/invoke/catalog-api/method/api/v1/catalog/items?pageSize=20
```

サイドカーはサービス検出を処理し、カタログ API サイドカーに要求をルーティングします。 最後に、サイドカーは catalog API を呼び出して要求を実行し、カタログ項目をフェッチして、応答を返します。

```
GET http://localhost/api/v1/catalog/items?pageSize=20
```

### <a name="make-aggregated-service-calls-using-the-net-sdk"></a>.NET SDK を使用して集計されたサービスの呼び出しを行う

EShop フロントエンドからのほとんどの呼び出しは単純な CRUD 呼び出しです。 API ゲートウェイは、処理のためにそれらを1つのサービスに転送します。 ただし、一部のシナリオでは、要求を完了するために複数のバックエンドサービスを連携させる必要があります。 これらのより複雑な呼び出しでは、web ショッピングアグリゲーターサービスを使用して、複数のサービスにわたってワークフローを仲介します。 図6-4 は、買い物かごに商品を追加する処理シーケンスを示しています。

![バスケットのシーケンス図を更新する](./media/service-invocation/complex-call.png)

**図 6-4**。 買い物かごのシーケンスを更新します。

アグリゲーターサービスは、最初に catalog API からカタログアイテムを取得します。 次に、アイテムの可用性と価格を検証します。 最後に、アグリゲーターサービスは、バスケット API を呼び出すことによって、更新された買い物かごを保存します。

アグリゲーターサービスには、 `BasketController` 買い物かごを更新するためのエンドポイントを提供するが含まれています。

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

メソッドは、 `UpdateAllBasketAsync` 属性を使用して受信要求の *承認* ヘッダーを取得し `FromHeader` ます。 *Authorization* ヘッダーには、保護されたバックエンドサービスを呼び出すために必要なアクセストークンが含まれています。

バスケットを更新する要求を受信すると、アグリゲーターサービスはカタログ API を呼び出して項目の詳細を取得します。 バスケットコントローラーは、挿入されたオブジェクトを使用して `ICatalogService` その呼び出しを行い、カタログ API と通信します。 インターフェイスの元の実装で gRPC を使用して呼び出しを行います。 更新された実装では、HttpClient サポートで Dapr サービスの呼び出しを使用します。

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

サービス呼び出しを行うために、Dapr 固有のコードが必要ないことに注目してください。 すべての通信は、標準の HttpClient オブジェクトを使用して行われます。

Dapr HttpClient は、メソッドのクラスに挿入され `CatalogService` `Startup.ConfigureServices` ます。

```csharp
services.AddSingleton<ICatalogService, CatalogService>(
    _ => new CatalogService(DaprClient.CreateInvokeHttpClient("catalog-api")));
```

アグリゲーターサービスによって実行されるもう1つの呼び出しは、バスケット API に対して行われます。 承認された要求のみを許可します。 アクセストークンは *承認* 要求ヘッダーと共に渡され、呼び出しが成功するようにします。

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

この例でも、サービスを呼び出すために使用されるのは、標準の HttpClient 機能だけです。 これにより、既に HttpClient を使い慣れている開発者は、既存のスキルを再利用できます。 また、既存の HttpClient コードでは、変更を加えずに Dapr サービスの呼び出しを使用できます。

## <a name="summary"></a>まとめ

この章では、サービス呼び出しのビルドブロックについて学習しました。 ここでは、Dapr sidecar に対して直接 HTTP 呼び出しを行うことと、Dapr .NET SDK を使用して、リモートメソッドを呼び出す方法について説明しました。

Dapr .NET SDK には、リモートメソッドを呼び出すための複数の方法が用意されています。 HttpClient のサポートは、既存のスキルを再利用する開発者にとって優れており、既存の多くのフレームワークやライブラリと互換性があります。 DaprClient は、HTTP または gRPC セマンティクスを使用して Dapr サービス呼び出し API を直接使用するためのサポートを提供します。

EShopOnDapr 参照アーキテクチャは、Dapr サービスの呼び出しを使用して、元の eShopOnContainers ソリューションが最新である方法を示しています。 EShop に Dapr を追加すると、自動再試行、mTLS を使用したメッセージの暗号化、改善された可観測性などの利点が得られます。

### <a name="references"></a>関連項目

- [Dapr サービス呼び出しの構成ブロック](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/)

- [分散型クラウドネイティブアプリケーションの監視](../cloud-native/observability-patterns.md)

> [!div class="step-by-step"]
> [前へ](state-management.md)
> [次へ](publish-subscribe.md)
