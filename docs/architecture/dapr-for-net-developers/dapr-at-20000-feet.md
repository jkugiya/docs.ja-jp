---
title: 2 万フィートの Dapr
description: Dapr の概要、その機能、およびしくみについて説明します。
author: robvet
ms.date: 02/07/2021
ms.openlocfilehash: c6157d29274df73f6ea1fef44b8e5cd5d0239471
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401471"
---
# <a name="dapr-at-20000-feet"></a>2 万フィートの Dapr

第1章では、分散マイクロサービスアプリケーションの魅力を説明しました。 しかし、アーキテクチャや運用上の複雑さを劇的に向上させることも指摘しました。 そのことを念頭に置いて、"ケーキ" と "食べ" をどのようにして使用できるのでしょうか。 つまり、分散アーキテクチャの機敏性を活用し、複雑さを最小限に抑えるにはどうすればよいでしょうか。

Dapr ( *分散アプリケーションランタイム*) は、最新の分散アプリケーションを構築するための新しい方法です。

プロトタイプとして開始されたことが、優れたオープンソースプロジェクトに発展しました。 Microsoft のスポンサーであるスポンサーは、Dapr を設計および構築するために、お客様とオープンソースコミュニティと緊密に提携しています。 Dapr プロジェクトは、すべての背景から開発者を集めて、分散アプリケーションの開発に関する困難な課題をいくつか解決します。

この書籍では、.NET 開発者の視点から見た、Dapr について見ていきます。 この章では、Dapr とそのしくみの概念を理解します。 後で、アプリケーションで Dapr を使用する方法について、実践的な実践的な指示を提供します。

ジェットで2万フィートに飛ぶことを想像してください。 ウィンドウを見て、以下の横長を見てみましょう。 Dapr についても同様です。 Dapr を2万フィートで飛ぶことを視覚化します。 表示内容

## <a name="dapr-and-the-problem-it-solves"></a>Dapr とそれが解決する問題

Dapr は、最新の分散アプリケーションに固有の大きな課題に対処します。 **複雑さ**。

プラグ可能なコンポーネントのアーキテクチャを通じて、Dapr は分散アプリケーションの背後を大幅に簡略化します。 これは、アプリケーションを Dapr ランタイムからインフラストラクチャ機能にバインドする **動的接着** を提供します。 たとえば、アプリケーションで状態ストアが必要になる場合があります。 Redis Cache を対象とするカスタムコードを作成し、実行時にサービスに挿入することができます。 ただし、Dapr は、すぐに使用できる分散キャッシュ機能を提供することで、エクスペリエンスを簡略化します。 サービスは、Dapr **構成** を介して Redis Cache **コンポーネント** に動的にバインドする dapr **ビルディングブロック** を呼び出します。 このモデルでは、サービスによって Dapr への呼び出しが委任されます。この呼び出しは、お客様の代わりに Redis を呼び出します。 サービスには、Redis への SDK、ライブラリ、または直接参照がありません。 Redis Cache API ではなく、一般的な Dapr state management API に対してコードを記述します。

図2-1 は、2万フィートの Dapr を示しています。

![Dapr、2万フィートの ](./media/dapr-at-20000-feet/dapr-high-level.png)
 **図 2-1**。 Dapr は2万フィートです。

図の一番上の行で、Dapr が一般的な開発プラットフォーム向けの言語固有の Sdk を提供するしくみに注意してください。 Dapr v 1.0 には、ゴー、Node.js、Python、.NET、Java、および JavaScript がサポートされています。 この書籍では、Dapr .NET SDK に焦点を当てています。これにより、ASP.NET Core 統合も直接サポートされます。

言語固有の Sdk によって開発者のエクスペリエンスが向上しますが、Dapr はプラットフォームに依存しません。 内部的には、Dapr のプログラミングモデルは、標準の HTTP/gRPC 通信プロトコルを介して機能を公開します。 すべてのプログラミングプラットフォームは、ネイティブの HTTP および gRPC Api を介して Dapr を呼び出すことができます。  

図の中心にある青いボックスは、Dapr の構成要素を表します。 各は、アプリケーションが使用できる分散アプリケーション機能を公開します。

下の行は、Dapr と実行可能なさまざまな環境の移植性を強調しています。

## <a name="dapr-architecture"></a>Dapr アーキテクチャ

この時点で、ジェットは、Dapr に戻り、高度に下ります。 Dapr がどのように機能するかについて詳しく説明しています。

### <a name="building-blocks"></a>構成要素

新しいパースペクティブから、Dapr の **構成要素** の詳細なビューが表示されます。

ビルディングブロックは、分散インフラストラクチャ機能をカプセル化します。 この機能には、HTTP または gRPC Api を使用してアクセスできます。 図2-2 は、Dapr v 1.0 で使用可能なブロックを示しています。

![Dapr の構成要素](./media/dapr-at-20000-feet/building-blocks.png)

**図 2-2**. Dapr のビルディングブロック。

次の表では、各ブロックによって提供されるインフラストラクチャサービスについて説明します。

| 構成要素 | 説明 |
|----------------|-------------|
| [状態管理](state-management.md) | 長時間実行されるステートフルサービスのコンテキスト情報をサポートします。 |
| [サービスの呼び出し](service-invocation.md) | プラットフォームに依存しないプロトコルと既知のエンドポイントを使用して、直接、安全なサービス間呼び出しを呼び出します。 |
| [パブリッシュとサブスクライブ](publish-subscribe.md) | サービス間にセキュリティで保護されたスケーラブルな公開/サブメッセージングを実装します。 |
| [バインド](bindings.md) | 双方向通信で外部リソースによって発生したイベントからコードをトリガーします。 |
| [可観測性](observability.md) | ネットワークに接続されたサービス間でのメッセージ呼び出しを監視して測定します。 |
| [シークレット](secrets.md) | 外部シークレットストアに安全にアクセスします。 |
| アクター | 再利用可能なアクターオブジェクトでロジックとデータをカプセル化します。 |

構成要素は、サービスからの分散アプリケーション機能の実装を抽象化します。 図2-3 は、この相互作用を示しています。

![Dapr 構成ブロックの統合](./media/dapr-at-20000-feet/building-blocks-integration.png)

**図 2-3**. Dapr ビルディングブロック統合。

構成要素は、各リソースの具象実装を提供する Dapr コンポーネントを呼び出します。 サービスのコードは、ビルディングブロックだけを認識します。 外部 Sdk またはライブラリへの依存関係はありません。 Dapr は、組み込みを処理します。 各構成要素は独立しています。 アプリケーションでは、そのうちの1つ、一部、またはすべてを使用できます。 焼き付けるとして、Dapr は、包括的な可観測性を含む業界のベストプラクティスに従っています。

各 Dapr ビルディングブロックの詳細な説明とコードサンプルについては、今後の章で説明します。 この時点で、jet はさらに多くのことを降下します。 新しいパースペクティブから、Dapr コンポーネントレイヤーについて詳しく見ていきます。

### <a name="components"></a>Components

ビルドブロックは、分散アプリケーション機能を呼び出すための API を公開しますが、Dapr コンポーネントは、それを実現するための具象実装を提供します。

Dapr **状態ストア** コンポーネントを検討してください。 CRUD 操作の状態を管理するための一貫した方法を提供します。 サービスコードに変更を加えることなく、次のいずれかの Dapr 状態コンポーネントを切り替えることができます。

- AWS DynamoDB
- Aerospike
- Azure Blob Storage
- Azure CosmosDB
- Azure Table Storage
- Cassandra
- クラウド Firestore (データストアモード)
- CloudState
- Couchbase
- Etcd
- HashiCorp Consul
- Hazelcast
- Memcached
- MongoDB
- PostgreSQL
- Redis
- RethinkDB
- SQL Server
- Zookeeper

各コンポーネントは、共通の状態管理インターフェイスによって必要な実装を提供します。

```go
 type Store interface {
   Init(metadata Metadata) error
   Delete(req *DeleteRequest) error
   BulkDelete(req []DeleteRequest) error
   Get(req *GetRequest) (*GetResponse, error)
   Set(req *SetRequest) error
   BulkSet(req []SetRequest) error
}
```

> [!TIP]
> Dapr ランタイムとすべての Dapr コンポーネントは、Golang、またはゴー言語で記述されています。 外出先は、オープンソースコミュニティで広く普及している言語であり、Dapr のクロスプラットフォームコミットメントをはしています。

おそらく、状態ストアとして Azure Redis Cache から開始します。 次の構成で指定します。

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Component
 metadata:
   name: statestore
   namespace: default
 spec:
   type: state.redis
   version: v1
   metadata:
   - name: redisHost
     value: <HOST>
   - name: redisPassword
     value: <PASSWORD>
   - name: enableTLS
     value: <bool> # Optional. Allowed: true, false.
   - name: failover
     value: <bool> # Optional. Allowed: true, false.
 ```

[ **Spec** ] セクションでは、状態管理に Redis Cache を使用するように dapr を構成します。 このセクションには、コンポーネント固有のメタデータも含まれています。 この場合は、追加の Redis 設定を構成するために使用できます。

後で、アプリケーションを運用環境に移行する準備ができました。 運用環境では、状態管理を Azure Table Storage に変更することができます。 Azure Table Storage は、低価格で耐久性の高い状態管理機能を提供します。

このドキュメントの執筆時点では、Dapr によって次のコンポーネントの種類が提供されています。

| コンポーネント | 説明 |
|-----------|-------------|
| [サービスの検出](https://github.com/dapr/components-contrib/tree/master/nameresolution) | サービス呼び出しの構成要素によって使用され、ホスト環境と統合してサービス間検出を提供します。 |
| [State](https://github.com/dapr/components-contrib/tree/master/state) | さまざまな状態ストアの実装と対話するための、統一されたインターフェイスを提供します。 |
| [Pub/sub](https://github.com/dapr/components-contrib/tree/master/pubsub) | は、さまざまなメッセージバスの実装と対話するための、統一されたインターフェイスを提供します。 |
| [バインド](https://github.com/dapr/components-contrib/tree/master/bindings) | 外部システムからアプリケーションイベントをトリガーし、オプションのデータペイロードを使用して外部システムを呼び出すための、統一されたインターフェイスを提供します。 |
| [ミドルウェア](https://github.com/dapr/components-contrib/tree/master/middleware) | カスタムミドルウェアが要求処理パイプラインにプラグインし、要求または応答に対して追加のアクションを呼び出すことができるようにします。 |
| [シークレットストア](https://github.com/dapr/components-contrib/tree/master/secretstores) | クラウド、エッジ、商用、オープンソースサービスなど、外部シークレットストアと対話するための統一インターフェイスを提供します。 |
| [エクスポーターのトレース](https://github.com/dapr/components-contrib/tree/master/exporters) | テレメトリラッパーを開くための統一インターフェイスを提供します。 |

ジェットが Dapr に対して実行を完了すると、後でもう一度確認し、相互に接続する方法を確認できます。

### <a name="sidecar-architecture"></a>Sidecar アーキテクチャ

Dapr は、 [サイドカーアーキテクチャ](/azure/architecture/patterns/sidecar)を通じて、その構成要素とコンポーネントを公開します。 サイドカーを使用すると、Dapr を別のメモリプロセスで、またはサービスと共に個別のコンテナーで実行できます。 Sidecars、サービスの一部ではなく、接続されているため、分離とカプセル化を提供します。 この分離により、それぞれに独自のランタイム環境を持たせることができ、さまざまなプログラミングプラットフォームに基づいてビルドできます。 図2-4 は、サイドカーパターンを示しています。

![Sidecar アーキテクチャ](./media/dapr-at-20000-feet/sidecar-generic.png)

**図 2-4** Sidecar アーキテクチャ。

このパターンは、オートバイに取り付けられるサイドカーに似ているため、"サイドカー" と名付けられています。 前の図では、分散アプリケーション機能を提供するために、dapr サイドカーがサービスにどのようにアタッチされているかに注目してください。

### <a name="hosting-environments"></a>ホスティング環境

Dapr はクロスプラットフォームのサポートを備えており、さまざまな環境で実行できます。 これらの環境には、Kubernetes、Vm のグループ、Azure IoT Edge などのエッジ環境が含まれます。

ローカル開発の場合、開始する最も簡単な方法は、 [自己ホスト型モード](https://docs.dapr.io/concepts/overview/#self-hosted)を使用することです。 自己ホスト型モードでは、マイクロサービスと Dapr サイドカーは、Kubernetes などのコンテナー orchestrator を使用せずに個別のローカルプロセスで実行されます。 詳細については、「 [Dapr CLI のダウンロードとインストール](https://docs.dapr.io/getting-started/install-dapr/)」を参照してください。

図2-5 は、HTTP または gRPC を介して通信する2つの別個のメモリプロセスでホストされるアプリケーションと Dapr を示しています。

![自己ホスト型のサイドカーアーキテクチャ](./media/dapr-at-20000-feet/self-hosted-dapr-sidecar.png)

**図 2-5**. 自己ホスト型 Dapr sidecar。

既定では、Dapr は Redis および Zipkin 用の Docker コンテナーをインストールして、既定の状態管理と可観測性を提供します。 ローカルコンピューターに Docker をインストールしない場合は、 [docker コンテナーを使用せずに、自己ホスト型モードで Dapr を実行](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/)することもできます。 ただし、状態管理のための Redis、pub/sub などの既定のコンポーネントを手動でインストールする必要があります。

Dapr は、Kubernetes などのコンテナー化された [環境](https://docs.dapr.io/concepts/overview/#kubernetes-hosted)でも実行されます。 図2-6 は、同じ Kubernetes ポッド内のアプリケーションコンテナーと共に、別のサイドカーコンテナーで実行されている Dapr を示しています。

![Kubernetes-ホストされたサイドカーアーキテクチャ](./media/dapr-at-20000-feet/kubernetes-hosted-dapr-sidecar.png)

**図 2-6**. Kubernetes Dapr sidecar。

## <a name="dapr-performance-considerations"></a>Dapr のパフォーマンスに関する考慮事項

既に説明したように、Dapr は、アプリケーションを分散アプリケーションの機能から分離するためのサイドカーアーキテクチャを公開しています。 Dapr 操作を呼び出すには、少なくとも1つのプロセス外ネットワーク呼び出しが必要です。 図2-7 は、Dapr トラフィックパターンの例を示しています。

![Dapr トラフィックパターン](./media/dapr-at-20000-feet/dapr-traffic-patterns.png)

**図 2-7**. Dapr トラフィックパターン。

前の図を見ると、各呼び出しに発生した待機時間とオーバーヘッドを調べることができます。  

Dapr チームは、パフォーマンスに大きく投資してきました。 エンジニアリング作業の膨大な量が、Dapr の効率を高めることになりました。 Dapr サイドカーの間の呼び出しは、高いパフォーマンスと小さいバイナリペイロードを提供する gRPC で常に行われます。 ほとんどの場合、追加のオーバーヘッドは、ミリ秒単位にする必要があります。

パフォーマンスを向上させるために、開発者は gRPC を使用して Dapr ビルディングブロックを呼び出すことができます。

gRPC は、古い [リモートプロシージャコール (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) プロトコルを進化させる最新の高パフォーマンスフレームワークです。 gRPC は、トランスポートプロトコルとして HTTP/2 を使用します。これにより、次のような HTTP RESTFul サービスよりも大幅なパフォーマンスが向上します。

- 同一の接続で複数の並列要求を送信するための多重化サポート-HTTP 1.1 は、一度に1つの要求/応答メッセージに処理を制限します。
- クライアント要求とサーバー応答の両方を同時に送信するための双方向の全二重通信。
- 要求と応答を有効にして、大きなデータセットを非同期的にストリーム配信できる組み込みのストリーミング。

## <a name="dapr-and-service-meshes"></a>Dapr とサービスメッシュ

サービスメッシュは、分散アプリケーションのための、急速に進化するもう1つのテクノロジです。

サービスメッシュは、サービス間の通信、回復性、負荷分散、テレメトリのキャプチャを処理する組み込みの機能を備えた、構成可能なインフラストラクチャレイヤーです。 これらの問題に対する責任は、サービスとサービスメッシュレイヤーの間で分担されます。 Dapr と同様に、サービスメッシュもサイドカーアーキテクチャに従います。

図2-8 は、サービスメッシュテクノロジを実装するアプリケーションを示しています。

![サービスメッシュ](./media/dapr-at-20000-feet/service-mesh-with-side-car.png)

**図 2-8**. サイドカーを使用したサービスメッシュ。

前の図は、各サービスと共に実行されるプロキシによってメッセージが傍受される方法を示しています。 各プロキシは、サービスに固有のトラフィックルールを使用して構成できます。 メッセージを認識し、サービスや外部との間でルーティングできます。

この質問は、「サービスメッシュが Dapr であるか」となります。

どちらもサイドカーアーキテクチャを使用しますが、各テクノロジの目的は異なります。 Dapr は、分散アプリケーション機能を提供します。 サービスメッシュには、専用のネットワークインフラストラクチャレイヤーが用意されています。

それぞれが異なるレベルで動作するため、両方とも同じアプリケーションで連携できます。 たとえば、サービスメッシュは、サービス間のネットワーク通信を提供します。 Dapr は、状態管理やアクターサービスなどのアプリケーションサービスを提供できます。

図2-9 は、Dapr とサービスメッシュテクノロジの両方を実装するアプリケーションを示しています。

![Dapr とサービスメッシュの組み合わせ](./media/dapr-at-20000-feet/dapr-and-service-mesh.png)

**図 2-9**. Dapr とサービスメッシュの組み合わせ。

書籍「 [Learning Dapr](https://www.amazon.com/Learning-Dapr-Building-Distributed-Applications/dp/1492072427/ref=sr_1_1?dchild=1&keywords=dapr&qid=1604794794&sr=8-1), Authors Haishi Bai And Yaron Schneider」では、dapr とサービスメッシュの統合について説明しています。

## <a name="summary"></a>まとめ

この章では、分散アプリケーションランタイムである Dapr について紹介しました。

Dapr は、お客様とオープンソースコミュニティとの密接な共同作業により、Microsoft がスポンサーとするオープンソースプロジェクトです。

Dapr は、中核となる分散マイクロサービスアプリケーションの本質的な複雑さを軽減するのに役立ちます。 これは、ブロック Api の構築の概念に基づいて構築されています。 Dapr ビルディングブロックは、状態管理、サービス間の呼び出し、発行/サブスクライブメッセージングなどの一般的な分散アプリケーション機能を公開します。 Dapr コンポーネントは、構成要素の下に配置され、各機能の具象実装を提供します。 アプリケーションは、構成ファイルを介してさまざまなコンポーネントにバインドされます。

次の章では、アプリケーションでの Dapr の使用方法について、実践的な実践的な指示を提供しています。

### <a name="references"></a>関連項目

- [Dapr のドキュメント](https://dapr.io/)
- [Dapr の学習](https://www.amazon.com/Learning-Dapr-Building-Distributed-Applications/dp/1492072427/ref=sr_1_1?dchild=1&keywords=dapr&qid=1604794794&sr=8-1)
- [.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)
- [Azure 向け Cloud-Native .NET アプリの設計](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf)

> [!div class="step-by-step"]
> [前へ](the-world-is-distributed.md)
> [次へ](getting-started.md)
