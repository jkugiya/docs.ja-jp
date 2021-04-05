---
title: 分散トレースの概念 - .NET
description: .NET の分散トレースの概念
ms.date: 03/14/2021
ms.openlocfilehash: 368cb545b9928534766e3005992a7a55571b8dcc
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111514"
---
# <a name="net-distributed-tracing-concepts"></a>.NET の分散トレースの概念

分散トレースは、特に複数のコンピューターやプロセスに分散される可能性があるアプリケーション内のエラーとパフォーマンスの問題を、エンジニアがローカライズするのに役立つ診断手法です。 分散トレースが役立つ場所に関する一般的な情報と、作業を開始するためのコードの例については、「[分散トレースの概要](distributed-tracing.md)」を参照してください。

### <a name="traces-and-activities"></a>トレースとアクティビティ

アプリケーションによって新しい要求が受信されるたびに、トレースに関連付けることができます。 .NET で記述されたアプリケーション コンポーネントでは、トレース内の作業単位は <xref:System.Diagnostics.Activity?displayProperty=nameWithType> のインスタンスで表され、トレース全体で、多くの異なるプロセスにまたがっている可能性があるこれらのアクティビティのツリーが形成されます。 新しい要求に対して作成された最初のアクティビティにより、トレース ツリーのルートが形成され、要求の存続期間全体と成功/失敗処理が追跡されます。 必要に応じて、子アクティビティを作成し、個別に追跡できるさまざまなステップに作業を再分割することができます。
たとえば、Web サーバーで特定の受信 HTTP 要求を追跡したアクティビティの場合、子アクティビティを作成し、要求を完了するために必要だった各データベース クエリを追跡することができます。 これにより、各クエリの存続期間と成功を個別に記録することができます。
アクティビティでは、<xref:System.Diagnostics.Activity.OperationName>、<xref:System.Diagnostics.Activity.Tags> と呼ばれる名前と値のペア、および <xref:System.Diagnostics.Activity.Events> など、作業単位ごとに他の情報を記録することができます。 名前により、実行される作業の種類が特定され、タグでその作業の説明的なパラメーターを記録できます。イベントは、タイムスタンプが付いた診断メッセージを記録するためのシンプルなログ記録メカニズムです。

> [!NOTE]
> 分散トレースの作業単位に対するもう 1 つの一般的な業界名は、"スパン" です。
> .NET では、この概念に対して "スパン" という名前が定着する何年も前に "アクティビティ" という用語が採用されました。

### <a name="activity-ids"></a>活動 ID

分散トレース ツリー内のアクティビティ間における親と子の関係は、一意の ID を使用して確立されます。 分散トレースの .NET の実装では、2 つの ID スキームがサポートされています。これらは、.NET 5 の既定値である W3C 標準の [TraceContext](https://www.w3.org/TR/trace-context/) と、旧バージョンとの互換性のために使用できる "階層" と呼ばれる古い .NET 規約です。
<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> により、使用される ID スキームが制御されます。 W3C TraceContext 標準では、すべてのトレースにグローバルに一意の 16 バイト トレース ID (<xref:System.Diagnostics.Activity.TraceId?displayProperty=nameWithType>) が割り当てられ、トレース内のすべてのアクティビティには一意の 8 バイトのスパン ID (<xref:System.Diagnostics.Activity.SpanId?displayProperty=nameWithType>) が割り当てられます。 各アクティビティで、トレース ID、それ自体のスパン ID、およびその親のトレース ID (<xref:System.Diagnostics.Activity.ParentSpanId?displayProperty=nameWithType>) が記録されます。 分散トレースではプロセス境界を越えて作業を追跡できるため、親および子アクティビティが同じプロセスに存在しない場合があります。 トレース ID と親のスパン ID を組み合わせることで、親アクティビティが存在するプロセスに関係なく、グローバルに親アクティビティを一意に識別できます。

<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> によって、新しいトレースを開始するために使用される ID 形式が制御されますが、既定では、既存のトレースに新しいアクティビティを追加すると、親アクティビティで使われている任意の形式が使用されます。
<xref:System.Diagnostics.Activity.ForceDefaultIdFormat?displayProperty=nameWithType> を true に設定すると、この動作がオーバーライドされ、親で別の ID 形式が使用される場合でも、DefaultIdFormat ですべての新しいアクティビティが作成されます。

### <a name="starting-and-stopping-activities"></a>アクティビティの開始と停止

プロセス内の各スレッドには、対応するアクティビティ オブジェクトが含まれる場合があります。これにより、<xref:System.Diagnostics.Activity.Current?displayProperty=nameWithType> を介してアクセスできるそのスレッドで発生している作業が追跡されます。 現在のアクティビティは、スレッドのすべての同期呼び出しに加えて、異なるスレッドで処理される次の非同期呼び出しに沿って自動的に流れます。 アクティビティ A がスレッドの現在のアクティビティであり、コードで新しいアクティビティ B が開始された場合、B はそのスレッドの新しい現在のアクティビティになります。 また、既定では、アクティビティ B でアクティビティ A がその親として扱われます。 アクティビティ B が後で停止した場合、アクティビティ A は、スレッドの現在のアクティビティとして復元されます。 アクティビティが開始されると、現在の時刻が <xref:System.Diagnostics.Activity.StartTimeUtc?displayProperty=nameWithType> として取り込まれます。 停止すると、<xref:System.Diagnostics.Activity.Duration?displayProperty=nameWithType> が現在の時刻と開始時刻の差として計算されます。

### <a name="coordinating-across-process-boundaries"></a>プロセス境界を越えた調整

プロセス境界を越えて作業を追跡するためには、アクティビティの親 ID をネットワーク経由で転送し、受信側のプロセスでそれらを参照するアクティビティを作成できるようにする必要があります。 W3C TraceContext ID 形式を使用する場合、.NET では [標準](https://www.w3.org/TR/trace-context/)で推奨されている HTTP ヘッダーを使用して、この情報を転送することもできます。 <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID 形式を使用する場合、.NET ではカスタムの要求 ID HTTP ヘッダーを使って ID を転送します。 他の多くの言語ランタイムとは異なり、ASP.NET Web サーバーや System.Net.Http などの .NET のインボックス ライブラリでは、HTTP メッセージのアクティビティ ID をデコードおよびエンコードする方法がネイティブに認識されています。 ランタイムでは、同期および非同期呼び出しを介した ID のフロー方法も認識されています。 つまり、HTTP メッセージを受信して出力する .NET アプリケーションは、アプリ開発者やサード パーティ ライブラリの依存関係を使用する特殊なコーディングを行わずに、分散トレース ID の自動フローに関与します。 サード パーティ ライブラリでは、HTTP 以外のメッセージ プロトコルを介した ID の転送、または HTTP のカスタム エンコード規約のサポートが追加される場合があります。

### <a name="collecting-traces"></a>トレースの収集

インストルメント化されたコードでは、分散トレースの一部として <xref:System.Diagnostics.Activity> オブジェクトを作成できますが、これらのオブジェクトの情報は、後でトレース全体を有効に確認できるように、一元化された永続ストアで転送およびシリアル化する必要があります。 このタスクを実行できるテレメトリ コレクション ライブラリがいくつか ([Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing)、[OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md)、サード パーティ テレメトリまたは APM ベンダーによって提供されるライブラリなど) あります。 また、開発者は <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> または <xref:System.Diagnostics.DiagnosticListener?displayProperty=nameWithType> を使用して、独自のカスタム アクティビティ テレメトリ コレクションを作成できます。 ActivityListener では、開発者にそれについて予備知識があるかどうかに関係なく、アクティビティの監視がサポートされます。
これにより、ActivityListener はシンプルで柔軟な汎用ソリューションになります。 これに対して、DiagnosticListener の使用は、<xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> を呼び出すことによってインストルメント化されたコードをオプトインする必要があるより複雑なシナリオであり、コレクション ライブラリでは、開始時にインストルメント化されたコードで使用された正確な名前付け情報を認識している必要があります。 DiagnosticSource と DiagnosticListener を使用すると、作成者およびリスナーは任意の .NET オブジェクトを交換し、カスタマイズされた情報渡し規約を確立できます。

### <a name="sampling"></a>サンプリング

高スループット アプリケーションのパフォーマンスを向上させるために、.NET の分散トレースでは、トレースをすべて記録するのではなく、それらのサブセットのみのサンプリングがサポートされます。 推奨される <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> API を使用して作成されたアクティビティの場合、テレメトリ コレクション ライブラリでは、<xref:System.Diagnostics.ActivityListener.Sample%2A?displayProperty=nameWithType> コールバックによるサンプリングを制御できます。
ログ ライブラリでは、アクティビティをまったく作成しないか、分散トレース ID の伝達に必要な最小限の情報で作成するか、あるいは完全な診断情報を設定するかを選択できます。 このように選択できる代わりに、診断ユーティリティが増えるため、パフォーマンスのオーバーヘッドが増加します。 <xref:System.Diagnostics.Activity.%23ctor%2A?displayProperty=nameWithType> と <xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> を呼び出す古いパターンを使用して開始されたアクティビティでは、最初に <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A?displayProperty=nameWithType> を呼び出すことによって DiagnosticListener サンプリングがサポートされる場合もあります。
完全な診断情報を取り込む場合でも、.NET 実装は、最新のハードウェア上でアクティビティをわずかマイクロ秒で作成、設定、転送できる効率的なコレクターと高速結合されるように設計されています。 サンプリングでは、記録されていないアクティビティごとに 100 ナノ秒未満になるようにインストルメンテーション コストを減らすことができます。

## <a name="next-steps"></a>次のステップ

.NET アプリケーションで分散トレースの使用を開始するコード例については、「[分散トレースの概要](distributed-tracing.md)」を参照してください。
