---
title: Dapr publish & subscribe ビルディングブロック
description: Dapr 発行 & サブスクライブのビルドブロックとその適用方法の説明
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 3d00c5a3171dd5a7287d07675f5a3742697e784b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102401483"
---
# <a name="the-dapr-publish--subscribe-building-block"></a>Dapr publish & subscribe ビルディングブロック

[パブリッシュ/サブスクライブパターン](/azure/architecture/patterns/publisher-subscriber)(多くの場合、"pub/sub" と呼ばれます) は、広く知られている、広く使用されているメッセージングパターンです。 通常、設計者は分散アプリケーションでこれを採用しています。 ただし、実装するのは複雑な場合があります。 多くの場合、さまざまなメッセージング製品での特徴の違いは微妙です。 Dapr は、pub/sub 機能の実装を大幅に簡略化するビルディングブロックを提供します。

## <a name="what-it-solves"></a>解決方法

Publish-Subscribe パターンの主な利点は疎 **結合** です。これは、 [一時的な分離](/azure/architecture/guide/technology-choices/messaging#decoupling)と呼ばれることもあります。 このパターンは、メッセージ ( **パブリッシャー**) を使用するサービス ( **サブスクライバー**) からメッセージを送信するサービスを分離します。 パブリッシャーとサブスクライバーはどちらも互いを認識していません。どちらも、メッセージを配信する集中 **メッセージブローカー** に依存しています。

図7-1 は、pub/sub パターンの高レベルアーキテクチャを示しています。

![Pub/sub パターン](./media/publish-subscribe/pub-sub-pattern.png)

**図 7-1**。 Pub/sub パターン。

前の図から、パターンの手順を確認します。

1. パブリッシャーはメッセージブローカーにメッセージを送信します。
1. サブスクライバーは、メッセージブローカーのサブスクリプションにバインドされます。
1. メッセージブローカーは、メッセージのコピーを関心のあるサブスクリプションに転送します。
1. サブスクライバーは、サブスクリプションからのメッセージを使用します。

ほとんどのメッセージブローカーは、受信後にメッセージを保持できるキューメカニズムをカプセル化します。 メッセージブローカーでは、メッセージを格納することで **持続性** が保証されます。 サブスクライバーは、パブリッシャーがメッセージを送信するときにすぐに使用できるようにしたり、オンラインにしたりする必要はありません。 サブスクライバーは、使用可能になると、メッセージを受信して処理します。  Dapr は、メッセージ配信に対して少なくとも **1 つ** のセマンティクスを保証します。 メッセージが公開されると、対象のサブスクライバーに少なくとも1回配信されます。

 > サービスがメッセージを1回だけ処理できる場合は、同じメッセージが複数回処理されないことを確認するために、 [べき等チェック](/azure/architecture/microservices/design/api-design#idempotent-operations) を行う必要があります。 このようなロジックはコーディングできますが、Azure Service Bus などの一部のメッセージブローカーには、組み込みの *重複検出* メッセージング機能が用意されています。

使用できるメッセージブローカー製品には、商用とオープンソースの両方があります。 それぞれに長所と短所があります。 ジョブは、システム要件を適切なブローカーに一致させることです。 選択したら、アプリケーションをメッセージブローカーの組み込みから切り離すことをお勧めします。 この機能を実現するには、 *抽象化* 内にブローカーをラップします。 抽象化は、メッセージの組み込みをカプセル化し、汎用の pub/sub 操作をコードに公開します。 コードは、実際のメッセージブローカーではなく、抽象化と通信します。 賢明な決定として、抽象化とその基盤となる実装を作成して維持する必要があります。 この方法では、複雑で反復的で、エラーが発生しやすいカスタムコードが必要です。

Dapr publish & subscribe ビルディングブロックは、メッセージングの抽象化と実装をすぐに使用できるようにします。 記述する必要があるカスタムコードは、事前に作成され、Dapr ビルディングブロック内にカプセル化されています。 それにバインドして使用します。 メッセージングプラミングコードを記述する代わりに、顧客に価値を追加するビジネス機能の作成に専念します。

## <a name="how-it-works"></a>しくみ

Dapr publish & subscribe ビルディングブロックは、メッセージを送受信するためのプラットフォームに依存しない API フレームワークを提供します。 サービスは、名前付き [トピック](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions)にメッセージを公開します。 サービスは、メッセージを使用するトピックをサブスクライブします。

サービスは、Dapr サイドカーで pub/sub API を呼び出します。 その後、サイドカーは、特定のメッセージブローカー製品をカプセル化する定義済みの dapr pub/sub コンポーネントを呼び出します。 図7-2 は、Dapr pub/sub messaging stack を示しています。

![Pub/sub スタック](./media/publish-subscribe/pub-sub-buildingblock.png)

**図 7-2**。 Dapr pub/sub スタック。

Dapr publish & subscribe ビルディングブロックは、さまざまな方法で呼び出すことができます。

最下位レベルでは、すべてのプログラミングプラットフォームは、 **Dapr ネイティブ API** を使用して HTTP または grpc 上でビルディングブロックを呼び出すことができます。 メッセージを公開するには、次の API 呼び出しを行います。

``` http
http://localhost:<dapr-port>/v1.0/publish/<pub-sub-name>/<topic>
```

上記の呼び出しには、いくつかの Dapr 特定の URL セグメントがあります。

- `<dapr-port>` dapr サイドカーがリッスンするポート番号を指定します。
- `<pub-sub-name>` 選択された Dapr pub/sub コンポーネントの名前を提供します。
- `<topic>` メッセージを公開するトピックの名前を指定します。

*Curl* コマンドラインツールを使用してメッセージを公開するには、次のようにします。

``` curl
curl -X POST http://localhost:3500/v1.0/publish/pubsub/newOrder \
  -H "Content-Type: application/json" \
  -d '{ "orderId": "1234", "productId": "5678", "amount": 2 }'
```

トピックをサブスクライブすることによってメッセージを受信します。 スタートアップ時に、Dapr ランタイムは既知のエンドポイントでアプリケーションを呼び出し、必要なサブスクリプションを特定して作成します。

``` http
http://localhost:<appPort>/dapr/subscribe
```

- `<appPort>` アプリケーションがリッスンしているポートの Dapr サイドカーを通知します。

このエンドポイントは自分で実装できます。 しかし、Dapr は、より直感的な実装方法を提供しています。 この機能については、この章で後ほど説明します。

呼び出しからの応答には、アプリケーションがサブスクライブするトピックの一覧が含まれています。 各には、トピックがメッセージを受信したときに呼び出すエンドポイントが含まれます。 応答の例を次に示します。

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

JSON 応答では、アプリケーションがトピックとにサブスクライブする必要があることがわかり `newOrder` `newProduct` ます。 それぞれにエンドポイントとが登録さ `/orders` `/productCatalog/products` れます。 どちらのサブスクリプションでも、アプリケーションはという名前の Dapr コンポーネントにバインド `pubsub` します。

図7-3 は、例のフローを示しています。

![Dapr を使用した pub/sub フローの例](media/publish-subscribe/pub-sub-flow.png)

**図 7-3**。 Dapr を使用した pub/sub フロー。

前の図から、フローに注意してください。

1. サービス b の dapr サイドカーは、 `/dapr/subscribe` サービス b (コンシューマー) からエンドポイントを呼び出します。 サービスは、作成するサブスクリプションを使用して応答します。
1. サービス B の dapr サイドカーは、要求されたサブスクリプションをメッセージブローカーに作成します。
1. サービス A は `/v1.0/publish/<pub-sub-name>/<topic>` 、Dapr サービスのエンドポイントでメッセージを公開します。
1. メッセージをメッセージブローカーに発行するサービス。
1. メッセージブローカーは、メッセージのコピーをサービス B に送信します。
1. サービス B は、サービス B のサブスクリプション (この場合は) に対応するエンドポイントを呼び出します `/orders` 。サービスは HTTP 状態コードで応答し `200 OK` ます。そのため、サイドカーは、メッセージが正常に処理されていると見なされます。

この例では、メッセージは正常に処理されます。 しかし、サービス B が要求を処理している間に問題が発生した場合は、応答を使用して、メッセージをどのように処理する必要があるかを指定できます。 HTTP 状態コードが返されると `404` 、エラーがログに記録され、メッセージが破棄されます。 または以外の状態コードで `200` は `404` 、警告がログに記録され、メッセージが再試行されます。 また、サービス B は、応答の本文に JSON ペイロードを含めることによって、メッセージに対してどのような処理が行われるかを明示的に指定できます。

```json
{
  "status": "<status>"
}
```

次の表に、使用可能な値を示し `status` ます。

| Status           | アクション                                                       |
| ---------------- | ------------------------------------------------------------ |
| SUCCESS          | メッセージは正常に処理され、削除されたと見なされます。 |
| 再試行            | メッセージは再試行されます。                                      |
| DROP             | 警告がログに記録され、メッセージが破棄されます。              |
| その他の状態 | メッセージは再試行されます。                                      |

### <a name="competing-consumers"></a>競合コンシューマー

トピックをサブスクライブするアプリケーションをスケールアウトする場合は、競合コンシューマーに対処する必要があります。 トピックに送信されたメッセージを処理するアプリケーションインスタンスは1つだけです。 さいわい、Dapr はその問題を処理します。 同じアプリケーション id を持つサービスの複数のインスタンスがトピックをサブスクライブしている場合、Dapr はそのうちの1つだけにメッセージを配信します。

### <a name="sdks"></a>SDK

ネイティブの Dapr Api に対する HTTP 呼び出しは、時間がかかり、抽象的なものです。 呼び出しは HTTP レベルで作成されるため、シリアル化や HTTP 応答コードなどの組み込みの問題を処理する必要があります。 幸いにも、直感的な方法があります。 Dapr には、一般的な開発プラットフォーム向けの言語固有の Sdk がいくつか用意されています。 このドキュメントの執筆時点では、Node.js、Python、.NET、Java、JavaScript を利用できます。

## <a name="use-the-dapr-net-sdk"></a>Dapr .NET SDK を使用する

.NET 開発者の場合、 [dapr .NET SDK](https://www.nuget.org/packages/Dapr.Client) を使用すると、dapr を操作するより生産的な方法が提供されます。 SDK は、 `DaprClient` Dapr 機能を直接呼び出すことができるクラスを公開します。 直感的で使いやすい方法です。

メッセージを公開するために、は `DaprClient` メソッドを公開し `PublishEventAsync` ます。

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

- 最初の引数 `pubsub` は、メッセージブローカーの実装を提供する Dapr コンポーネントの名前です。 コンポーネントについては、この章で後ほど説明します。
- 2番目の引数は、 `neworder` メッセージを送信するトピックの名前を指定します。
- 3番目の引数は、メッセージのペイロードです。
- メソッドのジェネリック型パラメーターを使用して、メッセージの .NET 型を指定できます。

メッセージを受信するには、登録されたトピックのサブスクリプションにエンドポイントをバインドします。 Dapr の AspNetCore ライブラリを使用すると、このようなことが簡単になります。 たとえば、既存の ASP.NET WebAPI action メソッドがあるとし `CreateOrder` ます。

```csharp
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

 > Dapr ASP.NET Core 統合を使用するには、プロジェクトの [dapr. AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) NuGet パッケージへの参照を追加する必要があります。

このアクションメソッドをトピックにバインドするには、属性を使用して修飾し `Topic` ます。

```csharp
[Topic("pubsub", "newOrder")]
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

この属性では、次の2つのキー要素を指定します。

- 対象となる Dapr pub/sub コンポーネント (この場合は `pubsub` )。
- サブスクライブするトピック (この場合は `newOrder` )。

その後、そのトピックのメッセージを受信すると、dapr はそのアクションメソッドを呼び出します。

また、Dapr を使用するには ASP.NET Core を有効にする必要があります。 Dapr .NET SDK には、クラスで呼び出すことができる拡張メソッドがいくつか用意されて `Startup` います。

メソッドでは、 `ConfigureServices` 次の拡張メソッドを追加する必要があります。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddControllers().AddDapr();
}
```

拡張メソッドを拡張メソッドに追加すると、 `AddDapr` `AddControllers` DAPR を MVC パイプラインに統合するために必要なサービスが登録されます。 また、インスタンスを `DaprClient` 依存関係挿入コンテナーに登録します。これにより、サービスに任意の場所に挿入できます。

メソッドでは、 `Configure` Dapr を有効にするために、次のミドルウェアコンポーネントを追加する必要があります。

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

への呼び出しは、 `UseCloudEvents` **CloudEvents** ミドルウェアを ASP.NET Core ミドルウェアパイプラインに追加します。 このミドルウェアは、CloudEvents 構造化形式を使用する要求をラップ解除します。これにより、受信側のメソッドはイベントペイロードを直接読み取ることができます。

> [CloudEvents](https://cloudevents.io/) は標準化されたメッセージング形式であり、プラットフォーム間でイベント情報を記述する一般的な方法を提供します。 Dapr は CloudEvents を採用しています。 CloudEvents の詳細については、 [CloudEvents 仕様](https://github.com/cloudevents/spec/tree/v1.0)を参照してください。

`MapSubscribeHandler`エンドポイントルーティング構成でを呼び出すと、Dapr サブスクライブエンドポイントがアプリケーションに追加されます。 このエンドポイントは、に対する要求に応答 `/dapr/subscribe` します。 このエンドポイントが呼び出されると、属性で修飾されたすべての WebAPI アクションメソッドが自動的に検出され、 `Topic` それらのサブスクリプションを作成するように Dapr に指示します。

## <a name="pubsub-components"></a>Pub/sub コンポーネント

Dapr [pub/sub コンポーネント](https://github.com/dapr/components-contrib/tree/master/pubsub) は、メッセージの実際の転送を処理します。 いくつかの使用方法があります。 各は、pub/sub 機能を実装するための特定のメッセージブローカー製品をカプセル化します。 書き込みの時点では、次の pub/sub コンポーネントを使用できました。

- Apache Kafka
- Azure Event Hubs
- Azure Service Bus
- AWS SNS/SQS
- GCP Pub/Sub
- Hazelcast
- MQTT
- NATS
- "プル"
- RabbitMQ
- Redis のストリーム

> [!NOTE]
> Azure クラウドスタックには、メッセージング機能 (Azure Service Bus) とイベントストリーミング (Azure イベントハブ) の可用性の両方があります。

これらのコンポーネントは、 [GitHub のコンポーネント contrib リポジトリ](https://github.com/dapr/components-contrib/tree/master/pubsub)のコミュニティによって作成されます。 まだサポートされていないメッセージブローカー用に独自の Dapr コンポーネントを作成することをお勧めします。

### <a name="configure-pubsub-components"></a>Pub/sub コンポーネントの構成

Dapr 構成ファイルを使用すると、使用する pub/sub コンポーネントを指定できます。 この構成にはいくつかのフィールドが含まれています。 フィールドは、 `name` 使用する pub/sub コンポーネントを指定します。 メッセージを送信または受信する場合は、この名前を指定する必要があります (メソッドシグネチャで前述したとおり `PublishEventAsync` )。

RabbitMQ message broker コンポーネントを構成するための Dapr 構成ファイルの例を以下に示します。

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

この例では、ブロックにメッセージブローカー固有の構成を指定できることを確認でき `metadata` ます。 この場合、RabbitMQ は永続的なキューを作成するように構成されています。 しかし、RabbitMQ コンポーネントには、より多くの構成オプションがあります。 各コンポーネントの構成には、使用可能なフィールドの独自のセットがあります。 各 [pub/sub コンポーネント](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/)のドキュメントで使用できるフィールドを確認できます。

コードからトピックをサブスクライブするプログラム的な方法の場合、Dapr pub/sub では、トピックをサブスクライブする宣言型の方法も提供されます。 この方法では、アプリケーションコードから Dapr 依存関係が削除されます。 したがって、既存のアプリケーションでコードを変更することなくトピックをサブスクライブすることもできます。 次の例は、サブスクリプションを構成するための Dapr 構成ファイルを示しています。

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

すべてのサブスクリプションで複数の要素を指定する必要があります。

- 使用する Dapr pub/sub コンポーネントの名前 (この場合は `pubsub` )。
- サブスクライブするトピックの名前 (この場合は `newOrder` )。
- このトピックに対して呼び出す必要がある API 操作 (この場合は `/orders` )。
- [スコープ](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/)では、トピックを発行およびサブスクライブできるサービスを指定できます。

## <a name="reference-application-eshopondapr"></a>参照アプリケーション: eShopOnDapr

付随する [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) アプリは、dapr を実装するマイクロサービスアプリケーションを構築するためのエンドツーエンドの参照アーキテクチャを提供します。 eShopOnDapr は、数年前に作成された、広く普及している [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainer) アプリの進化です。 どちらのバージョンも、マイクロサービス間の [統合イベント](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) の通信には、pub/sub パターンを使用します。 統合イベントには次のものがあります。

- ユーザーが買い物かごをチェックアウトしたとき。
- 注文の支払いが成功した場合。
- 購入の猶予期間が終了したとき。

EShopOnContainers のイベントは、次のインターフェイスに基づいてい `IEventBus` ます。

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent integrationEvent);

    void Subscribe<T, THandler>()
        where TEvent : IntegrationEvent
        where THandler : IIntegrationEventHandler<T>;
}
```

このインターフェイスの具象実装は、RabbitMQ と Azure Service Bus の両方の eShopOnContainers に存在します。 各実装には、理解が困難で保守が困難なカスタムプラミングコードが数多く含まれていました。

新しい eShopOnDapr は、Dapr を使用して公開/サブスクライブの動作を大幅に簡素化します。 たとえば、インターフェイスが `IEventBus` 1 つのメソッドに縮小されたとします。

```csharp
public interface IEventBus
{
    Task PublishAsync(IntegrationEvent integrationEvent);
}
```

### <a name="publish-events"></a>イベントの発行

更新された eShopOnDapr では、1つの実装で、 `DaprEventBus` 任意の Dapr でサポートされているメッセージブローカーをサポートできます。 次のコードブロックは、簡略化された発行メソッドを示しています。 `PublishAsync`メソッドが Dapr クライアントを使用してイベントを発行する方法に注意してください。

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

コードスニペットでわかるように、トピック名はイベントの種類の名前から派生します。 すべての eShop サービスで抽象化が使用されるため `IEventBus` 、改良 Dapr では、メインのアプリケーションコードをまったく変更する必要が *ありません* 。

> [!IMPORTANT]
> Dapr SDK は、を使用して `System.Text.Json` メッセージをシリアル化または逆シリアル化します。 ただし、では、 `System.Text.Json` 既定では派生クラスのプロパティはシリアル化されません。 EShop コードでは、イベントは、 `IntegrationEvent` 統合イベントの基底クラスであるとして明示的に宣言されることがあります。 これは、ビジネスロジックに基づいて、具象イベントの種類が実行時に動的に決定されるためです。 その結果、イベントは、派生クラスではなく、基本クラスの型情報を使用してシリアル化されます。 `System.Text.Json`この場合、が派生クラスのすべてのプロパティを強制的にシリアル化するには、コードが `object` ジェネリック型パラメーターとしてを使用します。 詳細については、 [.net のドキュメント](../../standard/serialization/system-text-json-polymorphism.md)を参照してください。

Dapr を使用すると、インフラストラクチャコードが **大幅に簡素化** されます。 異なるメッセージブローカーを区別する必要はありません。 Dapr は、このような抽象化を提供します。 また、必要に応じて、メッセージブローカーを簡単に交換したり、複数のメッセージブローカーコンポーネントを構成したりすることができます。

### <a name="subscribe-to-events"></a>イベントをサブスクライブする

以前の eShopOnContainers アプリには、各メッセージブローカーのサブスクリプションの実装を処理する *Subscriptionmanagers* が含まれています。 各マネージャーには、サブスクリプションイベントを処理するための、複雑なメッセージブローカー固有のコードが含まれています。 イベントを受け取るには、各サービスが各イベントの種類のハンドラーを明示的に登録する必要があります。

eShopOnDapr は、Dapr ASP.NET Core ライブラリを使用して、イベントサブスクリプションの組み込みを効率化します。 各イベントは、コントローラーのアクションメソッドによって処理されます。 `Topic`装飾属性は、アクションメソッドに、サブスクライブする対応するトピックの名前を指定します。 次に、から取得したコードスニペットを示し `PaymentService` ます。

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

属性で `Topic` は、イベントの .net 型の名前がトピック名として使用されます。 イベントを処理するために、以前の eShopOnContainers コードベースに既に存在していたイベントハンドラーが呼び出されます。 前の例では、トピックから受信したメッセージによっ `OrderStatusChangedToValidatedIntegrationEvent` て既存のイベントハンドラーが呼び出され `OrderStatusChangedToValidatedIntegrationEventHandler` ます。 Dapr はサブスクリプションとメッセージブローカーの基になるプラミングを実装しているため、大量の元のコードが廃止され、コードベースから削除されました。 このコードの多くは、理解しやすく、保守が困難でした。

### <a name="use-pubsub-components"></a>Pub/sub コンポーネントの使用

EShopOnDapr リポジトリ内のフォルダーには、 `deployment` さまざまな配置モード (および) を使用してアプリケーションを配置するためのファイルが含まれてい `Docker Compose` `Kubernetes` ます。 フォルダーは、フォルダー `dapr` を保持する各フォルダー内に存在し `components` ます。 このフォルダーには、 `eshop-pubsub.yaml` アプリケーションが pub/sub 動作に使用する Dapr pub/sub コンポーネントの構成を含むファイルが格納されます。 前のコードスニペットで見たように、使用される pub/sub コンポーネントの名前は `pubsub` です。 フォルダー内のファイルの内容を次に示し `eshop-pubsub.yaml` `deployment/compose/dapr/components` ます。

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

上記の構成では、この例で必要な [nat メッセージブローカー](https://nats.io/) を指定します。 メッセージブローカーを変更するには、RabbitMQ や Azure Service Bus などの別のメッセージブローカーを構成して、yaml ファイルを更新する必要があります。 Dapr では、メッセージブローカーを切り替えるときに、メインのサービスコードに変更はありません。

最後に、"アプリケーションに複数のメッセージブローカーが必要になるのはなぜですか。" という質問が表示される場合があります。 多くの場合、システムはさまざまな特性を持つワークロードを処理します。 1日に10回発生するイベントもありますが、別のイベントは1秒あたり5000回発生します。 メッセージングトラフィックを別のメッセージブローカーに分割することでメリットが得られる場合があります。 Dapr を使用すると、複数の pub/sub コンポーネント構成を追加できます。それぞれに異なる名前を付けることができます。

## <a name="summary"></a>まとめ

Pub/sub パターンは、分散アプリケーションでサービスを分離するのに役立ちます。 Dapr publish & subscribe ビルディングブロックを使用すると、アプリケーションにこの動作を簡単に実装できます。

Dapr pub/sub を使用すると、特定の *トピック* にメッセージを公開できます。 また、ビルディングブロックは、サブスクライブするトピックを決定するためにサービスにクエリを実行します。

Dapr pub/sub は、HTTP 経由でネイティブに使用することも、.NET SDK for Dapr などの言語固有の Sdk のいずれかを使用して使用することもできます。 .NET SDK は、ASP.NET core プラットフォームと緊密に統合されています。

Dapr を使用すると、サポートされているメッセージブローカー製品をアプリケーションに組み込むことができます。 次に、アプリケーションにコードの変更を必要とせずに、メッセージブローカーをスワップできます。

> [!div class="step-by-step"]
> [前へ](service-invocation.md)
> [次へ](bindings.md)
