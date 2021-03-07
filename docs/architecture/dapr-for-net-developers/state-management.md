---
title: Dapr 状態管理構成ブロック
description: 状態管理のビルディングブロック、その機能、利点、およびその適用方法の説明。
author: amolenk
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: 05daf18ece1da377f3d5d6a91c4839f196f14f80
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401427"
---
# <a name="the-dapr-state-management-building-block"></a>Dapr 状態管理構成ブロック

分散アプリケーションは、独立したサービスで構成されます。 各サービスはステートレスである必要がありますが、一部のサービスでは、ビジネス操作を完了するために状態を追跡する必要があります。 E コマースサイトのショッピングバスケットサービスについて考えてみましょう。 サービスが状態を追跡できない場合、顧客は web サイトを離れることによって買い物かごのコンテンツを無駄にする可能性があり、その結果、販売が失われ、カスタマーエクスペリエンスが低下する可能性があります。 これらのシナリオでは、状態を分散状態ストアに永続化する必要があります。 [Dapr state management ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/state-management/)は、状態の追跡を簡略化し、さまざまなデータストア間で高度な機能を提供します。

State management ビルディングブロックを試すには、 [第3章のカウンタアプリケーションサンプル](getting-started.md)を参照してください。

## <a name="what-it-solves"></a>解決方法

分散アプリケーションの状態を追跡することは困難な場合があります。 次に例を示します。

- アプリケーションによっては、さまざまな種類のデータストアが必要になる場合があります。
- データへのアクセスやデータの更新には、異なる一貫性レベルが必要になる場合があります。
- 複数のユーザーが同時にデータを更新して、競合の解決が必要になる場合があります。
- サービスは、データストアとの対話中に発生する [一時的なエラー](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) をすべて再試行する必要があります。

Dapr state management ビルディングブロックは、これらの課題に対処します。 依存関係がない追跡状態や、サードパーティのストレージ Sdk の学習曲線を合理化します。

> [!IMPORTANT]
> Dapr 状態管理には、 [キー/値](/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) API が用意されています。 この機能は、リレーショナルデータストレージまたはグラフデータストレージをサポートしていません。

## <a name="how-it-works"></a>しくみ

アプリケーションは Dapr サイドカーとやり取りして、キー/値データを格納および取得します。 内部的には、サイドカー API はデータを永続化するために、構成可能な状態ストアコンポーネントを使用します。 開発者は、Azure Cosmos DB、SQL Server、Cassandra など、 [サポートされている状態ストア](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) のコレクションから選択できます。

API は、HTTP または gRPC を使用して呼び出すことができます。 次の URL を使用して HTTP API を呼び出します。

```http
http://localhost:<dapr-port>/v1.0/state/<store-name>/
```

- `<dapr-port>`: Dapr がリッスンする HTTP ポート。
- `<store-name>`: 使用する状態ストアコンポーネントの名前。

図5-1 は、Dapr が有効なショッピングバスケットサービスが、という名前の Dapr 状態ストアコンポーネントを使用してキーと値のペアを格納する方法を示して `statestore` います。

![Dapr 状態ストアにキーと値のペアを格納する図。](media/state-management/state-management-flow.png)

**図 5-1**. Dapr 状態ストアにキーと値のペアを格納する。

前の図の手順を確認してください。

1. バスケットサービスは、Dapr サイドカーで状態管理 API を呼び出します。 要求の本文は、複数のキーと値のペアを含むことができる JSON 配列を囲みます。
1. Dapr サイドカーは、コンポーネント構成ファイルに基づいて状態ストアを決定します。 この例では、Redis cache の状態ストアです。
1. サイドカーは、Redis cache にデータを永続化します。

格納されたデータの取得は、同様の API 呼び出しです。 次の例では、 *curl* コマンドは dapr サイドカー API を呼び出してデータを取得します。

```console
curl http://localhost:3500/v1.0/state/statestore/basket1
```

コマンドは、次のように、格納されている状態を応答の本文に返します。

```json
{
  "items": [
    {
      "itemId": "DaprHoodie",
      "quantity": 1
    }
  ],
  "customerId": 1
}
```

以下のセクションでは、state management ビルディングブロックの高度な機能を使用する方法について説明します。

### <a name="consistency"></a>一貫性

[CAP 定理](https://en.wikipedia.org/wiki/CAP_theorem)は、状態を格納する分散システムに適用される一連の原則です。 図5-2 は、キャップ定理の3つのプロパティを示しています。

![キャップ定理。](media/state-management/cap-theorem.png)

**図 5-2** キャップ定理。

定理は、分散データシステムが整合性、可用性、およびパーティションの許容範囲のトレードオフを提供していることを示しています。 また、すべてのデータストアは、次 *の3つのプロパティのうち2つ* だけを保証できます。

- *整合性* (**C**)。 すべてのレプリカが更新されるまで、システムが要求をブロックする必要がある場合でも、クラスター内のすべてのノードが最新のデータで応答します。 現在更新中の項目に対して "一貫性のあるシステム" を照会した場合、すべてのレプリカが正常に更新されるまで応答は返されません。 ただし、常に最新のデータを受け取ることになります。

- *可用性* (**A**)。 すべてのノードは、応答が最新のデータではない場合でも、直ちに応答を返します。 更新中の項目に対して "使用可能なシステム" を照会すると、その時点でサービスが提供できる最適な回答が得られます。

- *パーティションの許容範囲* (**P**)。 レプリケートされたデータノードで障害が発生した場合や、他のレプリケートされたデータノードとの接続が失われた場合でも、システムの動作が保証されます。

分散アプリケーションは、 **P** プロパティを処理する必要があります。 サービスがネットワーク呼び出しを使用して相互に通信するため、ネットワークの中断 (**P**) が発生します。 この点を念頭に置いて、分散アプリケーションは **AP** または **CP** である必要があります。

**AP** アプリケーションは、整合性を超える可用性を選択します。 Dapr は、 **最終的な整合性** 戦略でこの選択をサポートしています。 複数のレプリカに冗長データを格納する Azure CosmosDB など、基になるデータストアについて考えてみましょう。 最終的な整合性を確保するために、状態ストアは更新を1つのレプリカに書き込み、クライアントとの書き込み要求を完了します。 この時間が経過すると、ストアはレプリカを非同期的に更新します。 読み取り要求では、最新の更新を受信していないレプリカも含め、任意のレプリカからデータを返すことができます。

**CP** アプリケーションは、可用性よりも整合性を選択します。 Dapr は、 **強力な整合性** 戦略でこの選択をサポートしています。 このシナリオでは、書き込み要求を完了 *する前に*、必要なレプリカ *を (場合* によっては *クォーラム* として) 同期的に更新します。 読み取り操作では、レプリカ間で常に最新のデータが返されます。

状態操作の一貫性レベルは、操作に *整合性ヒント* をアタッチすることによって指定されます。 次の *curl* コマンドは、 `Hello=World` 厳密な整合性ヒントを使用して、キーと値のペアを状態ストアに書き込みます。

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        {
          "key": "Hello",
          "value": "World",
          "options": {
            "consistency": "strong"
          }
        }
      ]'
```

> [!IMPORTANT]
> 操作にアタッチされている整合性ヒントを満たすには、Dapr 状態ストアコンポーネントが必要です。 すべてのデータストアが両方の整合性レベルをサポートしているわけではありません。 整合性ヒントが設定されていない場合、既定の動作は **最終的** にはになります。

### <a name="concurrency"></a>コンカレンシー

マルチユーザーアプリケーションでは、複数のユーザーが同時に (同時に) 同じデータを更新する可能性があります。 Dapr は、オプティミスティック同時実行制御 (OCC) をサポートして競合を管理します。 OCC は、ユーザーがデータのさまざまな部分を操作するため、更新の競合が発生することがないという前提に基づいています。 更新が成功し、そうでない場合は再試行する方が効率的です。 別の方法として、ペシミスティックロックを実装すると、実行時間の長いロックによってパフォーマンスが低下し、データ競合が発生する可能性があります。

Dapr は、Etag を使用したオプティミスティック同時実行制御 (OCC) をサポートしています。 ETag は、格納されているキーと値のペアの特定のバージョンに関連付けられた値です。 キーと値のペアが更新されるたびに、ETag 値も更新されます。 クライアントがキーと値のペアを取得すると、応答には現在の ETag の値が含まれます。 クライアントは、キーと値のペアを更新または削除するときに、その ETag 値を要求本文に戻す必要があります。 別のクライアントがその間にデータを更新した場合、Etag は一致せず、要求は失敗します。 この時点で、クライアントは更新されたデータを取得し、再度変更を加えて、更新を再送信する必要があります。 この方法は **、最初の書き込み-優先** と呼ばれます。

Dapr は、 **最終書き込み優先** 戦略もサポートしています。 この方法では、クライアントは ETag を書き込み要求にアタッチしません。 セッション中に基になる値が変更された場合でも、状態ストアコンポーネントは常に更新を許可します。 最後の書き込み-wins は、データの競合が少ない高スループットの書き込みシナリオに役立ちます。 また、ユーザーの不定期な更新を上書きすることもできます。

### <a name="transactions"></a>トランザクション

Dapr は、トランザクションとして実装された単一の操作として、データストアに *複数項目の変更* を書き込むことができます。 この機能は、 [ACID](https://en.wikipedia.org/wiki/ACID) トランザクションをサポートするデータストアに対してのみ使用できます。 このドキュメントの執筆時点では、Redis、MongoDB、PostgreSQL、SQL Server、Azure CosmosDB が含まれています。

次の例では、複数項目の操作が1つのトランザクションの状態ストアに送信されます。 トランザクションをコミットするには、すべての操作を成功させる必要があります。 1つ以上の操作が失敗した場合、トランザクション全体がロールバックされます。

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name>/transaction \
  -H "Content-Type: application/json" \
  -d '{
        "operations": [
          {
            "operation": "upsert",
            "request": { "key": "Key1", "value": "Value1"
            }
          },
          {
            "operation": "delete",
            "request": { "key": "Key2" }
          }
        ]
      }'
```

トランザクションをサポートしていないデータストアの場合、複数のキーを1つの要求として送信できます。 次の例は、 **一括** 書き込み操作を示しています。

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        { "key": "Key1", "value": "Value1" },
        { "key": "Key2", "value": "Value2" }
      ]'
```

一括操作の場合、Dapr は各キー/値ペアの更新をデータストアに個別の要求として送信します。

## <a name="use-the-dapr-net-sdk"></a>Dapr .NET SDK を使用する

Dapr .NET SDK は、.NET Core プラットフォームの言語固有のサポートを提供します。 開発者は、 `DaprClient` [第3章](getting-started.md) で導入されたクラスを使用して、データの読み取りと書き込みを行うことができます。 次の例は、メソッドを使用して `DaprClient.GetStateAsync<TValue>` 状態ストアからデータを読み取る方法を示しています。 メソッドでは、 `statestore` パラメーターとして、ストア名、、およびキーが必要 `AMS` です。

```csharp
var weatherForecast = await daprClient.GetStateAsync<WeatherForecast>("statestore", "AMS");
```

状態ストアにキーのデータが含まれていない場合、結果はになり `AMS` `default(WeatherForecast)` ます。

データをデータストアに書き込むには、メソッドを使用し `DaprClient.SaveStateAsync<TValue>` ます。

```csharp
daprClient.SaveStateAsync("statestore", "AMS", weatherForecast);
```

この例では、ETag 値が状態ストアコンポーネントに渡されないため、 **最後の書き込み優先** の方法を使用します。 **最初の書き込み優先** 戦略でオプティミスティック同時実行制御 (occ) を使用するには、最初にメソッドを使用して現在の ETag を取得し `DaprClient.GetStateAndETagAsync` ます。 次に、更新された値を書き込み、メソッドを使用して取得した ETag に沿って渡し `DaprClient.TrySaveStateAsync` ます。

```csharp
var (weatherForecast, etag) = await daprClient.GetStateAndETagAsync<WeatherForecast>("statestore", city);

// ... make some changes to the retrieved weather forecast

var result = await daprClient.TrySaveStateAsync("statestore", city, weatherForecast, etag);
```

データが取得され `DaprClient.TrySaveStateAsync` た後、状態ストアでデータ (および関連する ETag) が変更されている場合、メソッドは失敗します。 メソッドは、呼び出しが成功したかどうかを示すブール値を返します。 障害を処理するには、単に状態ストアから更新されたデータを再読み込みし、変更を加えてから更新を再送信します。

データに対するその他の変更に関係なく書き込みが常に成功するようにするには、 **最終書き込み優先** 戦略を使用します。

SDK には、データを一括で取得したり、データを削除したり、トランザクションを実行したりする他の方法が用意されています。 詳細については、 [Dapr .NET SDK リポジトリ](https://github.com/dapr/dotnet-sdk)を参照してください。

### <a name="aspnet-core-integration"></a>ASP.NET Core の統合

Dapr は、最新のクラウドベースの web アプリケーションを構築するためのクロスプラットフォームフレームワークである ASP.NET Core もサポートしています。 Dapr SDK は、状態管理機能を [ASP.NET Core モデルバインディング](/aspnet/core/mvc/models/model-binding) 機能に直接統合します。 構成は簡単です。 次の `IMVCBuilder.AddDapr` `.AddDapr` 例に示すように、クラスに拡張メソッドを追加してを追加し `Startup.cs` ます。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers().AddDapr();
}
```

構成が完了すると、Dapr は、ASP.NET Core 属性を使用して、キーと値のペアをコントローラーアクションに直接挿入でき `FromState` ます。 オブジェクトを参照する `DaprClient` 必要はなくなりました。 次の例は、特定の都市の天気予報を返す Web API を示しています。

```csharp
[HttpGet("{city}")]
public ActionResult<WeatherForecast> Get([FromState("statestore", "city")] StateEntry<WeatherForecast> forecast)
{
    if (forecast.Value == null)
    {
      return NotFound();
    }

    return forecast.Value;
}
```

この例では、コントローラーは属性を使用して天気予報を読み込み `FromState` ます。 最初の属性パラメーターは、状態ストア () です `statestore` 。 2番目の属性パラメーターは、 `city` 状態キーを取得する [ルートテンプレート](/aspnet/core/mvc/controllers/routing#route-templates) 変数の名前です。 2番目のパラメーターを省略した場合は、バインドされたメソッドパラメーター () の名前を使用して `forecast` ルートテンプレート変数が検索されます。

クラスには `StateEntry` 、1つのキーと値のペアに対して取得されるすべての情報 (、、、および) のプロパティが含まれてい `StoreName` `Key` `Value` `ETag` ます。 ETag は、オプティミスティック同時実行制御 (OCC) 戦略を実装する場合に便利です。 クラスには、インスタンスを必要とせずに取得したキー/値データを削除または更新するメソッドも用意されて `DaprClient` います。 次の例では、 `TrySaveAsync` メソッドを使用して、OCC を使用して取得された気象予測を更新します。

```csharp
[HttpPut("{city}")]
public async Task Put(WeatherForecast updatedForecast, [FromState("statestore", "city")] StateEntry<WeatherForecast> currentForecast)
{
    // update cached current forecast with updated forecast passed into service endpoint
    currentForecast.Value = updatedForecast;

    // update state store
    var success = await currentForecast.TrySaveAsync();

    // ... check result
}
```

## <a name="state-store-components"></a>状態ストアのコンポーネント

このドキュメントの執筆時点では、Dapr は次のトランザクション状態ストアをサポートしています。

- Azure CosmosDB
- Azure SQL Server
- MongoDB
- PostgreSQL
- Redis

Dapr には、CRUD 操作をサポートするがトランザクション機能ではない状態ストアのサポートも含まれています。

- Aerospike
- Azure Blob Storage
- Azure Table Storage
- Cassandra
- Cloudstate
- Couchbase
- etcd
- Google Cloud Firestore
- Hashicorp Consul
- Hazelcast
- Memcached
- Zookeeper

### <a name="configuration"></a>構成

自己ホスト型のローカル開発用に初期化された場合、Dapr は Redis を既定の状態ストアとして登録します。 既定の状態ストア構成の例を次に示します。 既定の名前に注意して `statestore` ください。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

 > [!NOTE]
 > 多くの状態ストアは、別々の名前を持つ1つのアプリケーションに登録できます。

Redis 状態ストアには `redisHost` 、 `redisPassword` redis インスタンスに接続するためのメタデータとメタデータが必要です。 上の例では、Redis パスワード (既定では空の文字列) がプレーン文字列として格納されます。 ベストプラクティスとしては、クリアテキスト文字列を避け、常にシークレット参照を使用することをお勧めします。 シークレット管理の詳細については、 [第10章](secrets.md)を参照してください。

もう1つのメタデータフィールドは、 `actorStateStore` 状態ストアをアクター構成ブロックで使用できるかどうかを示します。

### <a name="key-prefix-strategies"></a>キープレフィックス戦略

状態ストアコンポーネントを使用すると、キーと値のペアを基になるストアに格納するさまざまな方法が有効になります。 顧客が購入する品目を格納するショッピングバスケットサービスの例を思い出してください。

```console
curl -X POST http://localhost:3500/v1.0/state/statestore \
  -H "Content-Type: application/json" \
  -d '[{
        "key": "basket1",
        "value": {
          "customerId": 1,
          "items": [
            { "itemId": "DaprHoodie", "quantity": 1 }
          ]
        }
     }]'
```

Redis コンソールツールを使用して、redis cache の内部を調べて、Redis 状態ストアコンポーネントがどのようにデータを永続化したかを確認します。

```
127.0.0.1:6379> KEYS *
1) "basketservice||basket1"

127.0.0.1:6379> HGETALL basketservice||basket1
1) "data"
2) "{\"items\":[{\"itemId\":\"DaprHoodie\",\"quantity\":1}],\"customerId\":1}"
3) "version"
4) "1"
```

出力には、データの完全な Redis **キー** がとして表示され `basketservice||basket1` ます。 既定では、Dapr は、 `application id` dapr インスタンス () のを `basketservice` キーのプレフィックスとして使用します。 この名前付け規則を使用すると、複数の Dapr インスタンスで、キー名の競合を発生させずに同じデータストアを共有できます。 開発者にとっては、 `application id` Dapr でアプリケーションを実行するときは常に同じを指定することが重要です。 省略した場合、Dapr は一意のアプリケーション ID を生成します。 が変更されると、 `application id` アプリケーションは前のキープレフィックスで格納された状態にアクセスできなくなります。

とは言うものの、状態ストアのコンポーネントファイルのメタデータフィールドで、キープレフィックスの *定数値* を構成することができ `keyPrefix` ます。 次の例を確認してください。

```yaml
spec:
  metadata:
  - name: keyPrefix
  - value: MyPrefix
```

定数キープレフィックスを使用すると、複数の Dapr アプリケーション間で状態ストアにアクセスできます。 さらに、を設定して、 `keyPrefix` `none` プレフィックスを完全に省略します。

## <a name="reference-application-eshopondapr"></a>参照アプリケーション: eShopOnDapr

この書籍には、資格のある参照アプリケーションが含まれてい `eShopOnDapr` ます。 これは、以前の Microsoft マイクロサービス参照アプリケーションからモデル化さ `eShopOnContainers` れています。

元の [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) アーキテクチャは、インターフェイスを使用して `IBasketRepository` バスケットサービスのデータの読み取りと書き込みを行います。 クラスは、 `RedisBasketRepository` 基になるデータストアとして Redis を使用して実装を提供しました。

```csharp
public class RedisBasketRepository : IBasketRepository
{
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _database;

    public RedisBasketRepository(ConnectionMultiplexer redis)
    {
        _redis = redis;
        _database = redis.GetDatabase();
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        var data = await _database.StringGetAsync(customerId);

        if (data.IsNullOrEmpty)
        {
            return null;
        }

        return JsonConvert.DeserializeObject<CustomerBasket>(data);
    }

    // ...
}
```

このコードでは、サードパーティの NuGet パッケージを使用し `StackExchange.Redis` ます。 特定の顧客に対して買い物かごを読み込むには、次の手順を実行する必要があります。

1. を `ConnectionMultiplexer` コンストラクターに挿入します。 は、 `ConnectionMultiplexer` ファイルの依存関係挿入フレームワークに登録され `Startup.cs` ます。

   ```csharp
   services.AddSingleton<ConnectionMultiplexer>(sp =>
   {
       var settings = sp.GetRequiredService<IOptions<BasketSettings>>().Value;
       var configuration = ConfigurationOptions.Parse(settings.ConnectionString, true);
       configuration.ResolveDns = true;
       return ConnectionMultiplexer.Connect(configuration);
   });
   ```

1. 使用 `ConnectionMultiplexer` する各クラスにインスタンスを作成するには、を使用し `IDatabase` ます。

1. `IDatabase`キーとして指定されたを使用して Redis StringGet 呼び出しを実行するには、インスタンスを使用し `customerId` ます。

1. データが Redis から読み込まれているかどうかを確認します。それ以外の場合は、を返し `null` ます。

1. Redis からオブジェクトにデータを逆シリアル化し、その `CustomerBasket` 結果を返します。

更新された [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) 参照アプリケーションでは、クラスを新しい `DaprBasketRepository` クラスで置き換え `RedisBasketRepository` ます。

```csharp
public class DaprBasketRepository : IBasketRepository
{
    private const string StoreName = "eshop-basket-statestore";

    private readonly DaprClient _daprClient;

    public DaprBasketRepository(DaprClient daprClient)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));;
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        return await _daprClient.GetStateAsync<CustomerBasket>(StoreName, customerId);
    }

    // ...
}
```

更新されたコードでは、Dapr .NET SDK を使用して、state management ビルディングブロックを使用してデータの読み取りと書き込みを行います。 顧客向けにバスケットを読み込む新しい手順は、大幅に簡素化されています。

1. を `DaprClient` コンストラクターに挿入します。 は、 `DaprClient` ファイルの依存関係挿入フレームワークに登録され `Startup.cs` ます。
1. メソッドを使用し `DaprClient.GetStateAsync` て、構成済みの状態ストアから顧客の買い物かご項目を読み込み、結果を返します。

更新された実装では、引き続き Redis が基になるデータストアとして使用されます。 しかし、Dapr は、 `StackExchange.Redis` アプリケーションから参照と複雑さを抽象化します。 Dapr 構成ファイルが必要です。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

Dapr の実装により、基になるデータストアの変更も簡略化されます。 たとえば、Azure Table Storage に切り替えるには、構成ファイルの内容のみを変更する必要があります。 コードに変更を加える必要はありません。

## <a name="summary"></a>まとめ

Dapr state management ビルディングブロックは、さまざまなデータストア間でキー/値データを格納するための API を提供します。 API では、次の機能がサポートされています。

- 一括操作
- 強力で最終的な整合性
- オプティミスティック コンカレンシー
- 複数項目のトランザクション

.NET SDK は、.NET Core と ASP.NET Core の言語固有のサポートを提供します。 モデルバインディングの統合により、ASP.NET Core コントローラーアクションメソッドからの状態へのアクセスと更新が簡単になります。

EShopOnDapr reference アプリケーションでは、Dapr 状態管理に移行する利点は明らかです。

1. 新しい実装では、より少数のコード行が使用されます。
1. これにより、サードパーティの API の複雑さが解消され `StackExchange.Redis` ます。
1. 基になる Redis キャッシュを別の種類のデータストアに置き換えるには、状態ストアの構成ファイルの変更のみが必要になりました。

### <a name="references"></a>関連項目

- [Dapr がサポートする状態ストア](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/)

> [!div class="step-by-step"]
> [前へ](reference-application.md)
> [次へ](service-invocation.md)
