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
# <a name="the-dapr-bindings-building-block"></a>Dapr バインド構成ブロック

Azure Functions や AWS などのクラウドベースの *サーバーレス* サービスでは、分散アーキテクチャ領域全体で広く普及しています。 多くの利点の中で、マイクロサービスが外部システム *のイベント**のイベントを処理* したり、イベントを呼び出したりできるようにします。これにより、基盤となる複雑さやプラミングの問題を解消できます。 外部リソースは多数あります。これには、さまざまなプラットフォームやベンダーにわたるデータストア、メッセージシステム、web リソースが含まれます。 [Dapr binding ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/)は、dapr アプリケーションの doorstep に同じリソースバインド機能を提供します。

## <a name="what-it-solves"></a>解決方法

Dapr リソースバインドを使用すると、サービスは、直接アプリケーションの外部にある外部リソースに対してビジネス操作を統合できます。 外部システムからのイベントにより、サービスでコンテキスト情報を渡す操作がトリガーされる可能性があります。 サービスは、別の外部システムでイベントをトリガーすることによって操作を拡張し、コンテキストペイロード情報を渡すことができます。 サービスは、外部リソースを結合または認識しなくても通信します。 組み込みは、事前に定義された Dapr コンポーネント内にカプセル化されます。 使用する Dapr コンポーネントは、コードを変更せずに実行時に簡単に入れ替えることができます。

たとえば、ユーザーがキーワードをツイートたびにイベントをトリガーする Twitter アカウントなどを考えてみましょう。 サービスは、ツイートを受信して処理するイベントハンドラーを公開します。 完了すると、サービスによって、外部の Twilio サービスを呼び出すイベントがトリガーされます。 Twilio は、ツイートを含む SMS メッセージを送信します。 図8-1 は、この操作の概念アーキテクチャを示しています。

![入力バインド](media/bindings/bindings-architecture.png)

**図 8-1**。 Dapr リソースバインドの概念アーキテクチャ。

一見すると、リソースバインドの動作は、このブックで前に説明した [Publish/Subscribe パターン](publish-subscribe.md) と同様に表示されることがあります。 両者は類似性を共有していますが、違いがあります。 パブリッシュ/サブスクライブは、Dapr サービス間の非同期通信に重点を置いています。 リソースバインドのスコープはかなり広くなります。 ソフトウェアプラットフォーム間のシステムの相互運用性に焦点を当てています。 マイクロサービスアプリケーション外の異なるアプリケーション、データストア、およびサービス間で情報を交換する。

## <a name="how-it-works"></a>しくみ

Dapr リソースバインドは、コンポーネント構成ファイルで開始されます。 この YAML ファイルは、構成設定と共にバインドするリソースの種類を記述します。 構成が完了すると、サービスはリソースからイベントを受信したり、イベントをトリガーしたりすることができます。

> [!NOTE]
> バインディングの構成については、後の「 *コンポーネント* 」セクションで詳しく説明します。

### <a name="input-bindings"></a>入力バインディング

入力バインディングは、外部リソースからの受信イベントでコードをトリガーします。 イベントとデータを受信するには、サービスから *イベントハンドラー* になるパブリックエンドポイントを登録します。 図8-2 にフローを示します。

![Dapr 入力バインドフロー](media/bindings/input-binding-flow.png)

**図 8-2**。 Dapr 入力バインドフロー。

図8.2 では、外部の Twitter アカウントからイベントを受信する手順について説明します。

1. Dapr サイドカーは、バインド構成ファイルを読み取り、外部リソースに対して指定されたイベントをサブスクライブします。 この例では、イベントソースは Twitter アカウントです。
1. 一致するツイートが Twitter で公開されると、Dapr サイドカーで実行されているバインドコンポーネントがそれを取得し、イベントをトリガーします。
1. Dapr サイドカーは、バインディング用に構成されたエンドポイント (つまり、イベントハンドラー) を呼び出します。 この例では、サービスは、 `/tweet` ポート6000でエンドポイントの HTTP POST をリッスンします。 HTTP POST 操作であるため、イベントの JSON ペイロードが要求本文で渡されます。
1. イベントを処理した後、サービスは HTTP 状態コードを返し `200 OK` ます。

次の ASP.NET Core コントローラーは、Twitter のバインドによってトリガーされるイベントを処理する例を示しています。

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

操作がエラーになる場合は、適切な400または500レベルの HTTP 状態コードを返します。 少なくとも *1 回の配信* が保証される場合は、dapr サイドカーによってトリガーが再試行されます。 [リソースバインドの Dapr ドキュメント] [1] をチェックアウトして、少なくとも 1 *回* または 1 *回* の配信保証を提供するかどうかを確認します。

### <a name="output-bindings"></a>出力バインディング

Dapr には、 *出力バインディング* 機能も含まれています。 これにより、サービスが外部リソースを呼び出すイベントをトリガーできるようになります。 ここでも、まず、出力バインディングを記述するバインド構成 YAML ファイルを構成します。 その後、アプリケーションの dapr サイドカーで bindings API を呼び出すイベントをトリガーします。 図8-3 は、出力バインドのフローを示しています。

![Dapr 出力バインドフロー](media/bindings/output-binding-flow.png)

**図 8-3**。 Dapr の出力バインドフロー。

1. Dapr サイドカーは、外部リソースへの接続方法に関する情報を使用して、バインド構成ファイルを読み取ります。 この例では、外部リソースは Twilio SMS アカウントです。
1. アプリケーションは `/v1.0/bindings/sms` Dapr サイドカーでエンドポイントを呼び出します。 この場合は、HTTP POST を使用して API を呼び出します。 GRPC を使用することもできます。
1. Dapr サイドカーで実行されているバインディングコンポーネントは、メッセージを送信するために外部メッセージングシステムを呼び出します。 メッセージには、POST 要求で渡されたペイロードが含まれます。

例として、curl を使用して Dapr API を呼び出すことにより、出力バインディングを呼び出すことができます。

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

HTTP ポートは、dapr サイドカー (この場合は既定の dapr HTTP ポート) で使用されているものと同じであることに注意して `3500` ください。

ペイロードの構造 (つまり、送信されたメッセージ) はバインドごとに異なります。 上記の例では、ペイロードにメッセージを含む要素が含まれてい `data` ます。 他の種類の外部リソースへのバインドは、特に送信されるメタデータに対して異なる場合があります。 各ペイロードには、バインディングが実行する操作を定義するフィールドも含まれている必要があり `operation` ます。 上の例では、 `create` SMS メッセージを作成する操作を指定しています。 一般的な操作は次のとおりです。

- create
- get
- delete
- list

バインディングがサポートする操作をバインドの作成者が決定します。 各バインドのドキュメントでは、使用可能な操作とそれらを呼び出す方法について説明します。

## <a name="using-the-dapr-net-sdk"></a>Dapr .NET SDK の使用

Dapr .NET SDK は、.NET Core 開発者向けの言語固有のサポートを提供します。 次の例では、への呼び出し `HttpClient.PostAsync()` がメソッドに置き換えられてい `DaprClient.InvokeBindingAsync()` ます。 この特殊なメソッドは、構成済みの出力バインディングの呼び出しを簡略化します。

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

メソッドは、との値を受け取り `metadata` `message` ます。

バインディングを呼び出すために使用する場合、は `DaprClient` gRPC を使用して dapr sidecar の DAPR API を呼び出します。

## <a name="binding-components"></a>バインド (コンポーネントを)

内部的には、リソースバインドは Dapr バインドコンポーネントと共に実装されます。 これらはコミュニティによって提供され、外出先で書かれています。 Dapr バインドがまだ存在しない外部リソースと統合する必要がある場合は、自分で作成できます。 「 [Dapr contrib リポジトリ](https://github.com/dapr/components-contrib) 」を参照して、バインドを投稿する方法を確認してください。

> [!NOTE]
> Dapr とそのすべてのコンポーネントは、 [Golang](https://golang.org/) (ゴー) 言語で記述されています。 ゴーは、最新のクラウドネイティブプログラミングプラットフォームと見なされます。

バインドは、YAML 構成ファイルを使用して構成します。 Twitter バインドの構成例を次に示します。

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

各バインド構成には、フィールドとフィールドを持つ一般的な要素が含まれてい `metadata` `name` `namespace` ます。 Dapr は、構成されたフィールドに基づいて、サービスを呼び出すエンドポイントを決定し `name` ます。 上の例では、イベントが発生したときに、Dapr がサービスで注釈が付けられたメソッドを呼び出し `/twitter-mention` ます。

要素では、バインディング `spec` のとバインディング固有のを指定し `type` `metadata` ます。 この例では、API を使用して、Twitter アカウントにアクセスするための資格情報を指定します。 メタデータは、入力バインディングと出力バインドで異なる場合があります。 たとえば、Twitter を入力バインドとして使用するには、フィールドを使用してツイートで検索するテキストを指定する必要があり `query` ます。 一致するツイートが送信されるたびに、dapr サイドカーは `/twitter-mention` サービスのエンドポイントを呼び出します。 また、ツイートの内容も配信されます。

バインディングは、入力、出力、またはその両方に対して構成できます。 興味深いことに、バインドでは入力または出力の構成が明示的に指定されていません。 代わりに、バインドを構成値と共に使用して、方向が推論されます。

[リソースバインドの Dapr ドキュメント] [1] には、使用可能なバインドとその特定の構成設定の完全な一覧が表示されます。

### <a name="cron-binding"></a>Cron バインド

Dapr の Cron バインドに細心の注意を払ってください。 外部システムからのイベントをサブスクライブしません。 代わりに、このバインディングでは、構成可能な間隔スケジュールを使用してアプリケーションをトリガーします。 バインディングを使用すると、バックグラウンドワーカーを実装して、一定の間隔で何らかの処理を実行するための簡単な方法を提供できます。これにより、構成可能な遅延で無限ループを実装する必要がなくなります。 Cron バインド構成の例を次に示します。

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

この例では、Dapr は、30分ごとにエンドポイントを呼び出すことによってサービスをトリガーし `/checkOrderBacklog` ます。 値を指定するために使用できるパターンがいくつかあり `schedule` ます。 詳細については、 [Cron バインドのドキュメント](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/)を参照してください。

## <a name="reference-application-eshopondapr"></a>参照アプリケーション: eShopOnDapr

付随する eShopOnDapr reference アプリケーションは、出力バインディングの例を実装します。 Dapr [Sendgrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) バインドをトリガーして、新しい注文が配置されたときにユーザーに電子メールを送信します。 このバインドは、次のように、 `eshop-email.yaml` components フォルダー内のファイルにあります。

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

この構成では、 [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) バインドコンポーネントが使用されます。 サービスに接続するための API キーは、Dapr シークレットの参照を使用することに注意してください。 この方法では、シークレットが構成ファイルの外部に保持されます。 Dapr シークレットの詳細については、 [シークレットの構成ブロック](secrets.md) に関する章を参照してください。

バインディング構成は、Dapr サイドカーのエンドポイントを使用して呼び出すことができるバインドコンポーネントを指定し `/sendmail` ます。 次のコードスニペットでは、注文が開始されるたびに電子メールが送信されます。

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

この例でわかるように、には `message` メッセージ本文が含まれています。 メソッドは、 `CreateEmailBody` 文字列の書式を、本文のテキストで単純にします。 は、電子メール `metadata` メッセージの送信者、受信者、件名を指定します。 これらの値が静的である場合は、構成ファイルのメタデータフィールドにも含めることができます。 呼び出すバインディングの名前はであり、 `sendmail` 操作は `create` です。

## <a name="summary"></a>まとめ

Dapr リソースバインドを使用すると、ライブラリや Sdk に依存することなく、さまざまな外部リソースやシステムと統合できます。 これらの外部システムは、必ずしも service bus やメッセージブローカーなどのメッセージングシステムである必要はありません。 また、データストアや web リソース (Twitter や SendGrid など) のバインドも存在します。

入力バインド (トリガー) は、外部システムで発生するイベントに反応します。 アプリケーションで事前に構成されているパブリック HTTP エンドポイントを呼び出します。 Dapr は、構成内のバインディングの名前を使用して、アプリケーションで呼び出すエンドポイントを決定します。

出力バインドは、外部システムにメッセージを送信します。 出力バインドをトリガーするには、Dapr サイドカーのエンドポイントで HTTP POST を実行し `/v1.0/bindings/<binding-name>` ます。 GRPC を使用してバインディングを呼び出すこともできます。 .NET SDK には、 `InvokeBindingAsync` gRPC を使用して Dapr バインドを呼び出すためのメソッドが用意されています。

Dapr コンポーネントでバインドを実装します。 これらのコンポーネントは、コミュニティによって提供されます。 各バインドコンポーネントの構成には、抽象化する外部システムに固有のメタデータが含まれています。 また、サポートするコマンドとペイロードの構造は、バインドコンポーネントごとに異なります。

### <a name="references"></a>関連項目

- [リソースバインドに関する dapr ドキュメント](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/)

>[!div class="step-by-step"]
>[前へ](publish-subscribe.md)
>[次へ](observability.md)
