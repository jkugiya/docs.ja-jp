---
title: Dapr 可観測性ビルディングブロック
description: 可観測性ビルディングブロックの説明、その機能、利点、適用方法
author: edwinvw
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: c7c941625f5867ad58eee602bfc42183bee87183
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401451"
---
# <a name="the-dapr-observability-building-block"></a>Dapr 可観測性ビルディングブロック

最新の分散システムは複雑です。 小規模で疎結合のデプロイ可能なサービスから始めることができます。 これらのサービスは、プロセスとサーバーの境界を越えています。 次に、さまざまな種類のインフラストラクチャバッキングサービス (データベース、メッセージブローカー、キーコンテナー) を使用します。 最後に、これらの異なる部分は、アプリケーションを形成するためにまとめられています。

複数の独立した部品を使用して、何が起こっているのかをどのように理解しているのでしょうか。 残念ながら、従来の監視アプローチは十分ではありません。 代わりに、システムをエンドツー **エンドで監視可能に** する必要があります。 最新の [可観測性](../cloud-native/observability-patterns.md) プラクティスでは、アプリケーションの正常性を常に把握し、洞察を得ることができます。 これにより、出力を観察することによって内部状態を推論できます。 可観測性は、分散アプリケーションの監視とトラブルシューティングに必須です。

可観測性を取得するために使用されるシステム情報を **テレメトリ** と呼びます。 これは、次の4つの広範なカテゴリに分けることができます。

1. **分散トレース** は、分散トランザクションに関係するサービスとサービス間のトラフィックに関する洞察を提供します。
1. **メトリック** により、サービスのパフォーマンスとそのリソース消費量を把握できます。
1. **ログ記録** を使用すると、コードの実行状況やエラーが発生したかどうかを把握できます。
1. **正常性** エンドポイントは、サービスの可用性に関する洞察を提供します。

テレメトリの深さは、アプリケーションプラットフォームの可観測性機能によって決まります。 Azure クラウドを考えてみましょう。 すべてのテレメトリカテゴリを含む豊富なテレメトリエクスペリエンスが提供されます。 構成がない場合、ほとんどの Azure IaaS および PaaS サービスは、テレメトリを [Azure アプリケーション Insights](/azure/azure-monitor/app/app-insights-overview) サービスに伝達して公開します。 Application Insights には、高度に視覚化されたダッシュボードでシステムログ、トレース、問題領域が示されます。 また、通信に基づいてサービス間の依存関係を示す図を表示することもできます。

ただし、アプリケーションで Azure PaaS と IaaS リソースを使用できない場合はどうすればよいでしょうか。 Application Insights の豊富なテレメトリエクスペリエンスを利用できますか。 答えは [はい] です。 Azure 以外のアプリケーションでは、ライブラリをインポートし、構成を追加し、コードをインストルメント化してテレメトリを Azure アプリケーション Insights に出力できます。 ただし、この方法では、アプリケーションが Application Insights に **密** に結合されます。 別の監視プラットフォームにアプリを移動すると、負荷の高いリファクタリングが必要になる可能性があります。 密結合を回避し、コード外で可観測性を使用するのはすばらしいことではないでしょうか。

Dapr を使用すると、できます。 Dapr が可観測性を分散アプリケーションに追加する方法を見てみましょう。

## <a name="what-it-solves"></a>解決方法

Dapr 可観測性ビルディングブロックは、アプリケーションから可観測性を分離します。 Dapr のシステムサービスによって生成されたトラフィックを自動的にキャプチャし、dapr コントロールプレーンを構成します。 ブロックは、複数のサービスにまたがる1つの操作からのトラフィックを関連付けます。 また、パフォーマンスメトリック、リソース使用率、システムの正常性も公開します。 テレメトリはオープン標準形式で公開されており、選択した監視バックエンドに情報を取り込むことができます。 ここで、情報を視覚化、照会、および分析することができます。

Dapr がプラミングを抽象化するため、アプリケーションは可観測性がどのように実装されているかを認識しません。 ライブラリを参照したり、カスタムインストルメンテーションコードを実装したりする必要はありません。 Dapr を使用すると、開発者はビジネスロジックの構築に集中することができ、可観測性することはできません。 可観測性は Dapr レベルで構成され、さまざまなチームによって作成され、さまざまなテクノロジスタックを使用して構築された場合でも、サービス間で一貫しています。

## <a name="how-it-works"></a>しくみ

Dapr の [サイドカーアーキテクチャ](dapr-at-20000-feet.md#sidecar-architecture) は、組み込みの可観測性機能を有効にします。 サービスが通信する際、Dapr はトラフィックをインターセプトし、トレース、メトリック、およびログ情報を抽出します。 テレメトリはオープン標準形式で公開されます。 既定では、Dapr は [OpenTelemetry](https://opentelemetry.io/) と [Zipkin](https://zipkin.io/)をサポートしています。

Dapr には、さまざまなバックエンド監視ツールにテレメトリを発行できる [コレクター](https://docs.dapr.io/operations/monitoring/open-telemetry-collector/) が用意されています。 これらのツールは、分析とクエリのために Dapr テレメトリを提示します。 図9-1 は、Dapr 可観測性アーキテクチャを示しています。

![Dapr 可観測性アーキテクチャ](media/observability/observability-architecture.png)

**図 9-1** Dapr 可観測性アーキテクチャ。

1. サービス A がサービス B に対して操作を呼び出します。この呼び出しは、サービス a の dapr サイドカーからサービス B のサイドカーにルーティングされます。
1. サービス B が操作を完了すると、応答が Dapr フォールバックを通じてサービス A に返されます。 すべての要求と応答に対して利用可能なすべてのテレメトリを収集して公開します。
1. 構成されたコレクターはテレメトリを取り込みし、それを監視バックエンドに送信します。  

開発者として、可観測性の追加は、pub/sub や state management など、他の Dapr 構成要素の構成とは異なることに注意してください。 ビルディングブロックを参照する代わりに、コレクターと監視バックエンドを追加します。 図9-1 は、さまざまな監視バックエンドと統合する複数のコレクターを構成できることを示しています。

この章の最初に、4つのカテゴリのテレメトリが識別されました。 次のセクションでは、各カテゴリの詳細について説明します。 一般的な監視バックエンドと統合するコレクターを構成する方法についての指示が含まれます。

### <a name="distributed-tracing"></a>分散トレース

分散トレースを使用すると、分散アプリケーション内のサービス間を流れるトラフィックについての洞察を得ることができます。 交換された要求メッセージと応答メッセージのログは、問題のトラブルシューティングを行うための非常に重要な情報源です。 ハードパートは、同じ操作から送信されるメッセージを相互に *関連付け* ます。

Dapr は、 [W3C トレースコンテキスト](https://www.w3.org/TR/trace-context) を使用して関連メッセージを関連付けます。 同じコンテキスト情報を要求と応答に挿入して、一意の操作を形成します。 図9-2 は、相関関係のしくみを示しています。

![W3C トレースコンテキストの例](media/observability/w3c-trace-context.png)

**図 9-2** W3C トレースコンテキストの例。

1. サービス A がサービス B に対して操作を呼び出します。サービス A が呼び出しを開始すると、Dapr は一意のトレースコンテキストを作成し、要求に挿入します。
1. サービス B は要求を受信し、サービス C に対して操作を呼び出します。 Dapr は、受信要求にトレースコンテキストが含まれていることを検出し、それをサービス C に送信する要求に挿入することによって伝達します。  
1. サービス C は、要求を受信して処理します。 Dapr は、受信要求にトレースコンテキストが含まれていることを検出し、それをサービス B への送信応答に挿入することによって伝達します。
1. サービス B は応答を受信して処理します。 次に、新しい応答を作成し、それをサービス A に送信する応答に挿入して、トレースコンテキストを伝達します。

まとめて属する一連の要求と応答は、 *トレース* と呼ばれます。 図9-3 にトレースを示します。

![トレースとスパン](media/observability/traces-spans.png)

**図 9-3** トレースとスパン。

図では、トレースが、多くのサービスに対して実行される一意のアプリケーショントランザクションを表していることに注意してください。 トレースは、 *範囲* のコレクションです。 各スパンは、トレース内で実行された1つの操作または作業単位を表します。 範囲は、一意のトランザクションを実装するサービス間で送信される要求と応答です。

次のセクションでは、トレーステレメトリを監視バックエンドに公開して、そのテレメトリを検査する方法について説明します。

#### <a name="use-a-zipkin-monitoring-back-end"></a>Zipkin monitoring バックエンドを使用する

[Zipkin](https://zipkin.io/) は、オープンソースの分散トレースシステムです。 テレメトリデータを取り込み、視覚化することができます。 Dapr は、Zipkin の既定のサポートを提供します。 次の例は、Dapr テレメトリを視覚化するように Zipkin を構成する方法を示しています。

##### <a name="enable-and-configure-tracing"></a>トレースの有効化と構成

開始するには、dapr 構成ファイルを使用して Dapr ランタイムに対してトレースを有効にする必要があります。 次に、という名前の構成ファイルの例を示し `tracing-config.yaml` ます。  

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: tracing-config
  namespace: default
spec:
  tracing:
    samplingRate: "1"
    zipkin:
      endpointAddress: "http://zipkin.default.svc.cluster.local:9411/api/v2/spans"
```

属性は、 `samplingRate` トレースの発行に使用する間隔を指定します。 値は `0` (トレースが無効) と `1` (すべてのトレースが公開されている) の間である必要があります。 たとえば、という値を指定すると、 `0.5` 他のすべてのトレースが公開され、パブリッシュされたトラフィックが大幅に減少します。 は、 `endpointAddress` Kubernetes クラスターで実行されている Zipkin サーバー上のエンドポイントを指します。 Zipkin の既定のポートは `9411` です。 構成は、Kubernetes CLI を使用して Kubernetes クラスターに適用する必要があります。

```console
kubectl apply -f tracing-config.yaml
```

##### <a name="install-the-zipkin-server"></a>Zipkin サーバーをインストールする

Dapr を自己ホスト型のモードでインストールすると、Zipkin サーバーが自動的にインストールされ、または Windows 上の既定の構成ファイルでトレースが有効になり `$HOME/.dapr/config.yaml` `%USERPROFILE%\.dapr\config.yaml` ます。

ただし、Dapr を Kubernetes クラスターにインストールする場合、Zipkin は既定では追加されません。 という名前の次の Kubernetes マニフェストファイルは `zipkin.yaml` 、標準の Zipkin サーバーをクラスターにデプロイします。

```yaml
kind: Deployment
apiVersion: apps/v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  replicas: 1
  selector:
    matchLabels:
      service: zipkin
  template:
    metadata:
      labels:
        service: zipkin
    spec:
      containers:
        - name: zipkin
          image: openzipkin/zipkin-slim
          imagePullPolicy: IfNotPresent
          ports:
            - name: http
              containerPort: 9411
              protocol: TCP

---

kind: Service
apiVersion: v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  type: NodePort
  ports:
    - port: 9411
      targetPort: 9411
      nodePort: 32411
      protocol: TCP
      name: zipkin
  selector:
    service: zipkin

```

デプロイでは、標準のコンテナーイメージを使用し `openzipkin/zipkin-slim` ます。 Zipkin サービスは、ポートでテレメトリを表示するために使用できる Zipkin web フロントエンドを公開し `32411` ます。 Kubernetes CLI を使用して、Zipkin マニフェストファイルを Kubernetes クラスターに適用し、Zipkin サーバーをデプロイします。

```console
kubectl apply -f zipkin.yaml
```

##### <a name="configure-the-services-to-use-the-tracing-configuration"></a>トレース構成を使用するようにサービスを構成する

これで、テレメトリの発行を開始するためのすべてが正しく設定されました。 アプリケーションの一部としてデプロイされているすべての Dapr サイドカーは、開始時にテレメトリを出力するように指示する必要があります。 これを行うには、 `dapr.io/config` `tracing-config` 各サービスの配置に構成を参照する注釈を追加します。 次に、注釈を含む、eShop 注文 API サービスのマニフェストファイルの例を示します。

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ordering-api
  namespace: eshop
  labels:
    app: eshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: eshop
  template:
    metadata:
      labels:
        app: simulation
      annotations:
        dapr.io/enabled: "true"
        dapr.io/app-id: "ordering-api"
        dapr.io/config: "tracing-config"
    spec:
      containers:
      - name: simulation
        image: eshop/ordering.api:linux-latest
```

##### <a name="inspect-the-telemetry-in-zipkin"></a>Zipkin でテレメトリを検査する

アプリケーションが起動すると、Dapr サイドカーが Zipkin サーバーにテレメトリを出力します。 このテレメトリを検査するには、web ブラウザーでをポイント <http://localhost:32411> します。 Zipkin web フロントエンドが表示されます。

![Zipkin スタートページ](media/observability/zipkin.png)

[ *トレースの検索* ] タブで、トレースを照会できます。 制限を指定せずに [ *クエリの実行* ] ボタンを押すと、すべての取り込まれた *トレース* が表示されます。

![トレースの一覧](media/observability/zipkin-traces-overview.png)

特定のトレースの横にある [ *表示* ] ボタンをクリックすると、そのトレースの詳細が表示されます。

![トレースの詳細](media/observability/zipkin-trace-details.png)

[詳細] ページの各項目は、選択したトレースの一部である要求を表すスパンです。

##### <a name="inspect-the-dependencies-between-services"></a>サービス間の依存関係を検査する

Dapr sidecars はサービス間のトラフィックを処理するので、トレース情報を使用してサービス間の依存関係を判断できます。 実際の動作を確認するには、Zipkin web ページの [ *依存関係* ] タブにアクセスし、虫眼鏡付きのボタンを選択します。 Zipkin には、サービスとその依存関係の概要が表示されます。

![Zipkin の依存関係グラフ](media/observability/zipkin-dependencies.png)

サービス間の線のアニメーション化されたドットは、要求を表し、転送元から送信先に移動します。 赤い点は、要求が失敗したことを示します。

#### <a name="use-a-jaeger-or-new-relic-monitoring-back-end"></a>Jaeger または新しい聖を監視するバックエンドを使用する

Zipkin 自体以外の監視バックエンドソフトウェアでは、Zipkin 形式を使用した取り込みテレメトリもサポートされています。 [Jaeger](https://www.jaegertracing.io/) は、Uber テクノロジによって作成されたオープンソースのトレースシステムです。 これは、分散サービス間のトランザクションをトレースし、複雑なマイクロサービス環境のトラブルシューティングを行うために使用されます。 [新しい聖箱](https://newrelic.com/) は、 *フルスタック* の可観測性プラットフォームです。 分散アプリケーションから関連するデータをリンクして、システムの全体像を提供します。 これを試すには、 `endpointAddress` Dapr 構成ファイルで Jaeger または新しい聖剣サーバーをポイントするを指定します。 Jaeger サーバーにテレメトリを送信するように Dapr を構成する構成ファイルの例を次に示します。 Jaeger の URL は、Zipkin の URL と同じです。 唯一の違いは、サーバーが実行されているポートです。

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "http://localhost:9415/api/v2/spans"
 ```

新しい聖箱をお試しになるには、新しい聖数点の API のエンドポイントを指定します。 新しい聖箱の構成ファイルの例を次に示します。

 ```yaml
apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "https://trace-api.newrelic.com/trace/v1?Api-Key=<NR-API-KEY>&Data-Format=zipkin&Data-Format-Version=2"
 ```

使用方法の詳細については、Jaeger と新しい聖数の web サイトをご覧ください。

### <a name="metrics"></a>メトリック

メトリックを使用すると、パフォーマンスとリソース消費に関する洞察を得ることができます。 内部的には、Dapr はシステムとランタイムのさまざまなメトリックのコレクションを生成します。 Dapr は、 [Prometheus](https://prometheus.io/) をメトリック標準として使用します。 Dapr サイドカーとシステムサービスは、ポートでメトリックエンドポイントを公開し `9090` ます。 *Prometheus よう* は、メトリックを収集するために、事前に定義された間隔でこのエンドポイントを呼び出します。 ようは、メトリック値を監視バックエンドに送信します。 図9-4 は、スクラッププロセスを示しています。

![スクラップ Prometheus メトリック](media/observability/prometheus-scraper.png)

**図 9-4**. スクラップ Prometheus メトリック。

上の図では、各サイドカーとシステムサービスが、ポート9090でリッスンするメトリックエンドポイントを公開しています。 Prometheus メトリック Scrapper は、各エンドポイントからメトリックをキャプチャし、その情報を監視バックエンドに発行します。  

#### <a name="service-discovery"></a>サービス検出

メトリックを収集する場所をメトリックようが認識していることを不思議に思うかもしれません。 Prometheus は、ターゲットデプロイ環境に組み込まれている検出メカニズムと統合できます。 たとえば、Kubernetes で実行すると、Prometheus は Kubernetes API と統合して、環境で実行されている使用可能なすべての Kubernetes リソースを見つけることができます。

#### <a name="metrics-list"></a>メトリックの一覧

Dapr は、Dapr システムサービスとそのランタイムに対して多数のメトリックを生成します。 次に例をいくつか示します。

| メトリック                                         | source | 説明                                                  |
| ---------------------------------------------- | :----: | ------------------------------------------------------------ |
| dapr_operator_service_created_total            | システム | Dapr オペレーターサービスによって作成された Dapr サービスの合計数。 |
| dapr_injector_sidecar_injection/requests_total | システム | Dapr Sidecar-Injector サービスによって受信されたサイドカーインジェクション要求の合計数。 |
| dapr_placement_runtimes_total                  | システム | Dapr 配置サービスに報告されたホストの合計数。 |
| dapr_sentry_cert_sign_request_received_total   | システム | Dapr Sentry サービスによって受信された証明書署名要求 (CRSs) の数。 |
| dapr_runtime_component_loaded      | ランタイム | 正常に読み込まれた Dapr コンポーネントの数。           |
| dapr_grpc_io_server_completed_rpcs | ランタイム | メソッドとステータスによる gRPC 呼び出しの数。                    |
| dapr_http_server_request_count     | ランタイム | HTTP サーバーで開始された HTTP 要求の数。           |
| dapr_http/クライアント/sent_bytes        | ランタイム | HTTP クライアントによって要求本文で送信された合計バイト数 (ヘッダーは含まれません)。 |

使用可能なメトリックの詳細については、 [Dapr メトリックのドキュメント](https://docs.dapr.io/developing-applications/building-blocks/observability/metrics)を参照してください。

#### <a name="configure-dapr-metrics"></a>Dapr メトリックを構成する

実行時に、Dapr コマンドに引数を含めることで、メトリックコレクションエンドポイントを無効にでき `--enable-metrics=false` ます。 または、引数を使用して、エンドポイントの既定のポートを変更することもでき `--metrics-port 9090` ます。

また、Dapr 構成ファイルを使用して、ランタイムメトリックコレクションを静的に有効または無効にすることもできます。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  metric:
    enabled: false
```

#### <a name="visualize-dapr-metrics"></a>Dapr メトリックを視覚化する

Prometheus ようが監視バックエンドにメトリックを収集して公開することにより、生データをどのように意味するのでしょうか。 メトリックを分析するための一般的な視覚化ツールは [Grafana](https://grafana.com/grafana/)です。 Grafana を使用すると、利用可能なメトリックからダッシュボードを作成できます。 次に、Dapr システムサービスのメトリックを表示するダッシュボードの例を示します。

![Dapr システムサービスのメトリックを表示する Grafana ダッシュボード](media/observability/grafana-sample.png)

Dapr のドキュメントには、 [Prometheus と Grafana をインストールするためのチュートリアル](https://docs.dapr.io/operations/monitoring/grafana/)が含まれています。

### <a name="logging"></a>ログの記録

ログ記録を使用すると、実行時にサービスに何が起こっているかを把握できます。 アプリケーションを実行すると、dapr は Dapr システムサービスと Dapr システムサービスからログエントリを自動的に生成します。 ただし、アプリケーションコードでインストルメント化されたログエントリは、自動的には含まれ **ません** 。 アプリケーションコードからログを出力するには、 [OPENTELEMETRY sdk for .net](https://opentelemetry.io/docs/net/)などの特定の sdk をインポートします。 アプリケーションコードのログ記録については、この章の「 *Dapr .NET SDK の使用*」セクションを参照してください。  

#### <a name="log-entry-structure"></a>ログ エントリの構造

Dapr は構造化ログを出力します。 各ログエントリの形式は次のとおりです。

| フィールド    | 説明                                          | 例                             |
| -------- | ---------------------------------------------------- | ----------------------------------- |
| time     | 全形式で書式設定されたタイムスタンプ                          | `2021-01-10T14:19:31.000Z`          |
| level    | エントリのレベル ( `debug` \| `info` \| `warn` \| `error` )   | `info`                              |
| type     | ログの種類                                             | `log`                               |
| msg      | ログメッセージ                                          | `metrics server started on :62408/` |
| scope    | ログのスコープ                                        | `dapr.runtime`                      |
| instance | Dapr が実行されるホスト名                             | TSTSRV01                            |
| app_id   | Dapr アプリ ID                                          | ordering-api                        |
| ver      | Dapr ランタイムバージョン                                 | `1.0.0`-rc. 2                        |

トラブルシューティングのシナリオでログエントリを検索する場合は、 `time` `level` フィールドとフィールドが特に役立ちます。 時刻フィールドは、特定の期間を特定できるようにログエントリを順序付けます。 トラブルシューティングの際には、 *デバッグレベル* のログエントリによって、コードの動作に関する詳細情報が提供されます。

#### <a name="plain-text-versus-json-format"></a>プレーンテキストと JSON 形式

既定では、Dapr は構造化されたログをプレーンテキスト形式で出力します。 すべてのログエントリは、キーと値のペアを含む文字列として書式設定されます。 プレーンテキストでのログ記録の例を次に示します。

```text
== DAPR == time="2021-01-12T16:11:39.4669323+01:00" level=info msg="starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="log level set to: info" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="metrics server started on :62408/" app_id=ordering-api instance=TSTSRV03 scope=dapr.metrics type=log ver=1.0.0-rc.2
```

単純に、この形式は解析が困難です。 監視ツールでログエントリを表示する場合は、JSON 形式のログ記録を有効にすることをお勧めします。 JSON エントリを使用すると、監視ツールは個々のフィールドにインデックスを作成し、クエリを実行できます。 JSON 形式のログエントリは次のようになります。

```json
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d", "scope": "dapr.runtime", "time": "2021-01-12T16:11:39.4669323+01:00", "type": "log", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "log level set to: info", "scope": "dapr.runtime", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "metrics server started on :62408/", "scope": "dapr.metrics", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
```

JSON の書式設定を有効にするには、各 Dapr sidecar を構成する必要があります。 自己ホスト型モードでは、コマンドラインでフラグを指定でき `--log-as-json` ます。

```console
dapr run --app-id ordering-api --log-level info --log-as-json dotnet run
```

Kubernetes では、 `dapr.io/log-as-json` アプリケーションの各デプロイに注釈を追加できます。

```yaml
annotations:
   dapr.io/enabled: "true"
   dapr.io/app-id: "ordering-api"
   dapr.io/app-port: "80"
   dapr.io/config: "dapr-config"
   dapr.io/log-as-json: "true"
```

Kubernetes クラスターに、ヘルムを使用して Dapr をインストールすると、すべての Dapr システムサービスで JSON 形式のログ記録を有効にすることができます。

```console
helm repo add dapr https://dapr.github.io/helm-charts/
helm repo update
kubectl create namespace dapr-system
helm install dapr dapr/dapr --namespace dapr-system --set global.logAsJson=true
```

#### <a name="collect-logs"></a>ログの収集

Dapr によって出力されたログは、分析のために監視バックエンドに渡すことができます。 ログコレクターは、システムからログを収集して監視バックエンドに送信するコンポーネントです。 一般的なログコレクターは [Fluentd](https://www.fluentd.org/)です。 「 [How to: Set Up Fluentd, エラスティック search And Kibana In Kubernetes in](https://docs.dapr.io/operations/monitoring/fluentd/) The dapr documentation」をご覧ください。 この記事では、Fluentd を log collector として設定し、 [ELK Stack](https://www.elastic.co/elastic-stack) (エラスティック検索と Kibana) を監視バックエンドとして設定する手順について説明します。

### <a name="health-status"></a>正常性状態

サービスの正常性状態は、その可用性に関する洞察を提供します。 各 dapr サイドカーは、ホスト環境でサイドカーの正常性を判断するために使用できる正常性 API を公開します。 API には、次の1つの操作があります。

```console
GET http://localhost:3500/v1.0/healthz
```

この操作では、次の2つの HTTP 状態コードが返されます。

- 204: サイドカーが正常な状態である場合
- 500: サイドカーが正常でない場合

自己ホスト型モードで実行している場合、正常性 API は自動的には呼び出されません。 アプリケーションコードまたは正常性監視ツールから API を呼び出すことができます。

Kubernetes で実行されている場合、Dapr sidecar は、自動的に Kubernetes を構成して、 *ライブプローブ* および *準備プローブ* を実行するための正常性 API を使用するようにを構成します。

Kubernetes は、ライブプローブを使用して、コンテナーが起動して実行されているかどうかを判断します。 Liveness probe がエラーコードを返した場合、Kubernetes はコンテナーが停止していると見なし、自動的に再起動します。 この機能により、アプリケーションの全体的な可用性が向上します。

Kubernetes は、準備プローブを使用して、コンテナーがトラフィックの受け入れを開始する準備ができているかどうかを判断します。 すべてのコンテナーの準備が整ったら、ポッドは準備完了と見なされます。 準備とは、Kubernetes サービスが負荷分散シナリオでポッドにトラフィックを送信できるかどうかを決定します。 準備ができていないポッドは、ロードバランサーから自動的に削除されます。

ライブおよび準備プローブには、いくつかの構成可能なパラメーターがあります。 どちらも、ポッドのマニフェストファイルのコンテナー仕様セクションで構成されています。 既定では、Dapr は各サイドカーコンテナーに対して次の構成を使用します。

```yaml
livenessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold : 3
readinessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold: 3
```

 プローブでは、次のパラメーターを使用できます。

- は、 `path` Dapr HEALTH API エンドポイントを指定します。
- は、 `port` Dapr HEALTH API ポートを指定します。
- は、 `initialDelaySeconds` 最初にコンテナーのプローブを開始する前に Kubernetes が待機する秒数を指定します。
- は、 `periodSeconds` 各プローブ間で Kubernetes が待機する秒数を指定します。
- は、 `timeoutSeconds` タイムアウトするまでに Kubernetes が API からの応答を待機する秒数を指定します。タイムアウトはエラーとして解釈されます。
- は、コンテナーが動作して `failureThreshold` いないか準備されていないと見なす前に、Kubernetes が受け入れる失敗状態コードの数を指定します。

### <a name="dapr-dashboard"></a>Dapr ダッシュボード

Dapr は、Dapr アプリケーション、コンポーネント、および構成に関するステータス情報を示すダッシュボードを提供します。 Dapr CLI を使用して、ポート8080でローカルコンピューター上の web アプリケーションとしてダッシュボードを開始します。

```console
dapr dashboard
```

Kubernetes で実行されている Dapr アプリケーションの場合は、次のコマンドを使用します。

```console
dapr dashboard -k
```

ダッシュボードが開き、アプリケーション内のすべてのサービスの概要が表示されます。これには、Dapr sidecar があります。 次のスクリーンショットは、Kubernetes で実行されている eShopOnDapr アプリケーションの Dapr ダッシュボードを示しています。

![Dapr ダッシュボードの [概要] ページ](media/observability/dapr-dashboard-overview.png)

Dapr ダッシュボードは、Dapr アプリケーションのトラブルシューティングを行うときに非常に役立ちます。 Dapr とシステムサービスに関する情報を提供します。 ログエントリなど、各サービスの構成をドリルダウンすることができます。

ダッシュボードには、アプリケーションの構成済みのコンポーネント (およびその構成) も表示されます。

![[Dapr ダッシュボードコンポーネント] ページ](media/observability/dapr-dashboard-components.png)

ダッシュボードでは、大量の情報が提供されています。 これを検出するには、Dapr アプリケーションを実行し、ダッシュボードを参照します。 付属の eShopOnDapr アプリケーションを使用してを開始できます。

Dapr ダッシュボードコマンドの詳細については、dapr ドキュメントの「 [dapr DASHBOARD CLI コマンドリファレンス](https://docs.dapr.io/reference/cli/dapr-dashboard/) 」を参照してください。

## <a name="use-the-dapr-net-sdk"></a>Dapr .NET SDK を使用する

Dapr .NET SDK には、特定の可観測性機能が含まれていません。 可観測性のすべての機能は、Dapr レベルで提供されます。

.NET アプリケーションコードからテレメトリを生成する場合は、 [OPENTELEMETRY SDK for .net](https://opentelemetry.io/docs/net/)を検討する必要があります。 オープンテレメトリプロジェクトは、クロスプラットフォーム、オープンソース、およびベンダーに依存しないプロジェクトです。 テレメトリデータを生成、出力、収集、処理、およびエクスポートするためのエンドツーエンドの実装を提供します。 自動および手動のインストルメンテーションをサポートする言語ごとに1つのインストルメンテーションライブラリがあります。 テレメトリはオープンテレメトリ標準を使用して公開されます。 このプロジェクトには、クラウドプロバイダー、ベンダー、およびエンドユーザーからの幅広い業界サポートと導入が含まれています。

## <a name="reference-application-eshopondapr"></a>参照アプリケーション: eShopOnDapr

付随する eShopOnDapr reference アプリケーションの可観測性は、いくつかの部分で構成されています。 すべてのサイドカーのテレメトリがキャプチャされます。 また、以前の eShopOnContainers サンプルから継承された他の可観測性機能もあります。

### <a name="custom-health-dashboard"></a>カスタム正常性ダッシュボード

EShopOnDapr の **Webstatus** プロジェクトは、eShop サービスの正常性に関する洞察を提供するカスタム正常性ダッシュボードです。 このダッシュボードは Dapr health API を使用しませんが、ASP.NET Core の組み込みの [正常性チェックメカニズム](/aspnet/core/host-and-deploy/health-checks) を使用します。 ダッシュボードは、サービスの正常性状態だけでなく、サービスの依存関係の正常性状態も提供します。 たとえば、データベースを使用するサービスは、次のスクリーンショットに示すように、このデータベースの正常性状態も提供します。

![eShopOnDapr カスタム正常性ダッシュボード](media/observability/eshop-health-dashboard.png)

### <a name="seq-log-aggregator"></a>Seq ログアグリゲーター

[Seq](https://datalust.co/seq) は、ログを集計するために eShopOnDapr で使用される一般的なログアグリゲーターサーバーです。 Seq 取り込みは、Dapr システムサービスやサイドカーからではなく、アプリケーションサービスからのログ記録を行います。 Seq インデックスはアプリケーションログを記録し、ログを分析してクエリを実行するための web フロントエンドを提供します。 また、監視ダッシュボードを構築するための機能も用意されています。

EShopOnDapr アプリケーションサービスは、 [Serilog](https://serilog.net/) ログライブラリを使用して構造化ログを出力します。 Serilog は、 **シンク** と呼ばれる構成要素にログイベントを発行します。 シンクは、Serilog がログイベントを書き込むターゲットプラットフォームです。 Seq 用に1つなど、[多数の Serilog シンクを使用でき](https://github.com/serilog/serilog/wiki/Provided-Sinks)ます。 Seq は、eShopOnDapr で使用される Serilog シンクです。

### <a name="application-insights"></a>Application Insights

また、eShopOnDapr services は、Microsoft Application Insights SDK for .NET Core を使用して Azure アプリケーションインサイトに直接テレメトリを送信します。 詳細については、Microsoft docs の「 [ASP.NET Core アプリケーションの Azure アプリケーションインサイト](/azure/azure-monitor/app/asp-net-core) 」を参照してください。

## <a name="summary"></a>まとめ

運用環境で分散システムを実行する場合は、優れた可観測性が不可欠です。

Dapr は、分散トレース、ログ記録、メトリック、正常性状態など、さまざまな種類のテレメトリを提供します。

Dapr は、Dapr システムサービスと sidecars のテレメトリのみを生成します。 アプリケーションコードからのテレメトリは自動的に含まれません。 ただし、OpenTelemetry SDK for .NET などの特定の SDK を使用して、アプリケーションコードからテレメトリを生成することができます。

Dapr テレメトリはオープン標準ベースの形式で生成されるため、使用可能な多数の監視ツールによって取り込まれたできます。 例として、Zipkin、Azure アプリケーション Insights、ELK Stack、New 聖箱、Grafana などがあります。 特定の監視バックエンドを使用して Dapr アプリケーションを監視する方法については、dapr のドキュメントで「 [dapr を使用したアプリケーションの監視](https://docs.dapr.io/operations/monitoring/) 」を参照してください。

テレメトリを取り込みして監視バックエンドに公開するテレメトリようが必要です。

Dapr は、構造化されたログを出力するように構成できます。 構造化ログは、バックエンド監視ツールでインデックスを作成できるため、優先されます。 インデックス付きログを使用すると、ログの検索時にリッチクエリを実行できます。

Dapr は、Dapr サービスと構成に関する情報を提示するダッシュボードを提供します。

## <a name="references"></a>関連項目

- [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview/)
- [テレメトリを開く](https://opentelemetry.io/)
- [Zipkin](https://zipkin.io/)
- [W3C トレースコンテキスト](https://www.w3.org/TR/trace-context/)
- [Jaeger](https://www.jaegertracing.io/)
- [New Relic](https://newrelic.com/)
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/grafana/)
- [.NET 用テレメトリ SDK を開く](https://opentelemetry.io/docs/net/)
- [Fluentd](https://www.fluentd.org/)
- [ELK スタック](https://www.elastic.co/elastic-stack)
- [Seq](https://datalust.co/seq)
- [Serilog](https://serilog.net/)

> [!div class="step-by-step"]
> [前へ](bindings.md)
> [次へ](secrets.md)
