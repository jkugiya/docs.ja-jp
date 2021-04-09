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
# <a name="net-distributed-tracing-concepts"></a><span data-ttu-id="f5989-103">.NET の分散トレースの概念</span><span class="sxs-lookup"><span data-stu-id="f5989-103">.NET Distributed Tracing Concepts</span></span>

<span data-ttu-id="f5989-104">分散トレースは、特に複数のコンピューターやプロセスに分散される可能性があるアプリケーション内のエラーとパフォーマンスの問題を、エンジニアがローカライズするのに役立つ診断手法です。</span><span class="sxs-lookup"><span data-stu-id="f5989-104">Distributed tracing is a diagnostic technique that helps engineers localize failures and performance issues within applications, especially those that may be distributed across multiple machines or processes.</span></span> <span data-ttu-id="f5989-105">分散トレースが役立つ場所に関する一般的な情報と、作業を開始するためのコードの例については、「[分散トレースの概要](distributed-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5989-105">See the [Distributed Tracing Overview](distributed-tracing.md) for general information about where distributed tracing is useful and example code to get started.</span></span>

### <a name="traces-and-activities"></a><span data-ttu-id="f5989-106">トレースとアクティビティ</span><span class="sxs-lookup"><span data-stu-id="f5989-106">Traces and Activities</span></span>

<span data-ttu-id="f5989-107">アプリケーションによって新しい要求が受信されるたびに、トレースに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="f5989-107">Each time a new request is received by an application it can be associated with a trace.</span></span> <span data-ttu-id="f5989-108">.NET で記述されたアプリケーション コンポーネントでは、トレース内の作業単位は <xref:System.Diagnostics.Activity?displayProperty=nameWithType> のインスタンスで表され、トレース全体で、多くの異なるプロセスにまたがっている可能性があるこれらのアクティビティのツリーが形成されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-108">In application components written in .NET, units of work in a trace are represented by instances of <xref:System.Diagnostics.Activity?displayProperty=nameWithType> and the trace as a whole forms a tree of these Activities, potentially spanning across many distinct processes.</span></span> <span data-ttu-id="f5989-109">新しい要求に対して作成された最初のアクティビティにより、トレース ツリーのルートが形成され、要求の存続期間全体と成功/失敗処理が追跡されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-109">The first Activity created for a new request forms the root of the trace tree and it tracks the overall duration and success/failure handling the request.</span></span> <span data-ttu-id="f5989-110">必要に応じて、子アクティビティを作成し、個別に追跡できるさまざまなステップに作業を再分割することができます。</span><span class="sxs-lookup"><span data-stu-id="f5989-110">Child activities can be optionally created to sub-divide the work into different steps that can be tracked individually.</span></span>
<span data-ttu-id="f5989-111">たとえば、Web サーバーで特定の受信 HTTP 要求を追跡したアクティビティの場合、子アクティビティを作成し、要求を完了するために必要だった各データベース クエリを追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="f5989-111">For example given an Activity that tracked a specific inbound HTTP request in a web server, child activites could be created to track each of the database queries that were necessary to complete the request.</span></span> <span data-ttu-id="f5989-112">これにより、各クエリの存続期間と成功を個別に記録することができます。</span><span class="sxs-lookup"><span data-stu-id="f5989-112">This allows the duration and success for each query to be recorded independently.</span></span>
<span data-ttu-id="f5989-113">アクティビティでは、<xref:System.Diagnostics.Activity.OperationName>、<xref:System.Diagnostics.Activity.Tags> と呼ばれる名前と値のペア、および <xref:System.Diagnostics.Activity.Events> など、作業単位ごとに他の情報を記録することができます。</span><span class="sxs-lookup"><span data-stu-id="f5989-113">Activities can record other information for each unit of work such as <xref:System.Diagnostics.Activity.OperationName>, name-value pairs called <xref:System.Diagnostics.Activity.Tags>, and <xref:System.Diagnostics.Activity.Events>.</span></span> <span data-ttu-id="f5989-114">名前により、実行される作業の種類が特定され、タグでその作業の説明的なパラメーターを記録できます。イベントは、タイムスタンプが付いた診断メッセージを記録するためのシンプルなログ記録メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="f5989-114">The name identifies the type of work being performed, tags can record descriptive parameters of the work, and events are a simple logging mechanism to record timestamped diagnostic messages.</span></span>

> [!NOTE]
> <span data-ttu-id="f5989-115">分散トレースの作業単位に対するもう 1 つの一般的な業界名は、"スパン" です。</span><span class="sxs-lookup"><span data-stu-id="f5989-115">Another common industry name for units of work in a distributed trace are 'Spans'.</span></span>
> <span data-ttu-id="f5989-116">.NET では、この概念に対して "スパン" という名前が定着する何年も前に "アクティビティ" という用語が採用されました。</span><span class="sxs-lookup"><span data-stu-id="f5989-116">.NET adopted the term 'Activity' many years ago, before the name 'Span' was well established for this concept.</span></span>

### <a name="activity-ids"></a><span data-ttu-id="f5989-117">活動 ID</span><span class="sxs-lookup"><span data-stu-id="f5989-117">Activity IDs</span></span>

<span data-ttu-id="f5989-118">分散トレース ツリー内のアクティビティ間における親と子の関係は、一意の ID を使用して確立されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-118">Parent-Child relationships between Activities in the distributed trace tree are established using unique IDs.</span></span> <span data-ttu-id="f5989-119">分散トレースの .NET の実装では、2 つの ID スキームがサポートされています。これらは、.NET 5 の既定値である W3C 標準の [TraceContext](https://www.w3.org/TR/trace-context/) と、旧バージョンとの互換性のために使用できる "階層" と呼ばれる古い .NET 規約です。</span><span class="sxs-lookup"><span data-stu-id="f5989-119">.NET's implementation of distributed tracing supports two ID schemes, the W3C standard [TraceContext](https://www.w3.org/TR/trace-context/) which is the default in .NET 5 and an older .NET convention called 'Hierarchical' that is available for backwards compatibility.</span></span>
<span data-ttu-id="f5989-120"><xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> により、使用される ID スキームが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-120"><xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> controls which ID scheme is used.</span></span> <span data-ttu-id="f5989-121">W3C TraceContext 標準では、すべてのトレースにグローバルに一意の 16 バイト トレース ID (<xref:System.Diagnostics.Activity.TraceId?displayProperty=nameWithType>) が割り当てられ、トレース内のすべてのアクティビティには一意の 8 バイトのスパン ID (<xref:System.Diagnostics.Activity.SpanId?displayProperty=nameWithType>) が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f5989-121">In the W3C TraceContext standard every trace is assigned a globally unique 16 byte trace-id (<xref:System.Diagnostics.Activity.TraceId?displayProperty=nameWithType>) and every Activity within the trace is assigned a unique 8 byte span-id (<xref:System.Diagnostics.Activity.SpanId?displayProperty=nameWithType>).</span></span> <span data-ttu-id="f5989-122">各アクティビティで、トレース ID、それ自体のスパン ID、およびその親のトレース ID (<xref:System.Diagnostics.Activity.ParentSpanId?displayProperty=nameWithType>) が記録されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-122">Each Activity records the trace-id, its own span-id, and the span-id of its parent (<xref:System.Diagnostics.Activity.ParentSpanId?displayProperty=nameWithType>).</span></span> <span data-ttu-id="f5989-123">分散トレースではプロセス境界を越えて作業を追跡できるため、親および子アクティビティが同じプロセスに存在しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5989-123">Because distributed traces can track work across process boundaries parent and child Activities may not be in the same process.</span></span> <span data-ttu-id="f5989-124">トレース ID と親のスパン ID を組み合わせることで、親アクティビティが存在するプロセスに関係なく、グローバルに親アクティビティを一意に識別できます。</span><span class="sxs-lookup"><span data-stu-id="f5989-124">The combination of a trace-id and parent span-id can uniquely identify the parent Activity globally, regardless of what process it resides in.</span></span>

<span data-ttu-id="f5989-125"><xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> によって、新しいトレースを開始するために使用される ID 形式が制御されますが、既定では、既存のトレースに新しいアクティビティを追加すると、親アクティビティで使われている任意の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-125"><xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> controls which ID format is used for starting new traces, but by default adding a new Activity to an existing trace uses whatever format the parent Activity is using.</span></span>
<span data-ttu-id="f5989-126"><xref:System.Diagnostics.Activity.ForceDefaultIdFormat?displayProperty=nameWithType> を true に設定すると、この動作がオーバーライドされ、親で別の ID 形式が使用される場合でも、DefaultIdFormat ですべての新しいアクティビティが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-126">Setting <xref:System.Diagnostics.Activity.ForceDefaultIdFormat?displayProperty=nameWithType> to true overrides this behavior and creates all new Activities with the DefaultIdFormat, even when the parent uses a different ID format.</span></span>

### <a name="starting-and-stopping-activities"></a><span data-ttu-id="f5989-127">アクティビティの開始と停止</span><span class="sxs-lookup"><span data-stu-id="f5989-127">Starting and stopping Activities</span></span>

<span data-ttu-id="f5989-128">プロセス内の各スレッドには、対応するアクティビティ オブジェクトが含まれる場合があります。これにより、<xref:System.Diagnostics.Activity.Current?displayProperty=nameWithType> を介してアクセスできるそのスレッドで発生している作業が追跡されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-128">Each thread in a process may have a corresponding Activity object that is tracking the work occuring on that thread, accessible via <xref:System.Diagnostics.Activity.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5989-129">現在のアクティビティは、スレッドのすべての同期呼び出しに加えて、異なるスレッドで処理される次の非同期呼び出しに沿って自動的に流れます。</span><span class="sxs-lookup"><span data-stu-id="f5989-129">The current activity automatically flows along all synchronous calls on a thread as well as following async calls that are processed on different threads.</span></span> <span data-ttu-id="f5989-130">アクティビティ A がスレッドの現在のアクティビティであり、コードで新しいアクティビティ B が開始された場合、B はそのスレッドの新しい現在のアクティビティになります。</span><span class="sxs-lookup"><span data-stu-id="f5989-130">If Activity A is the current activity on a thread and code starts a new Activity B then B becomes the new current activity on that thread.</span></span> <span data-ttu-id="f5989-131">また、既定では、アクティビティ B でアクティビティ A がその親として扱われます。</span><span class="sxs-lookup"><span data-stu-id="f5989-131">By default activity B will also treat Activity A as its parent.</span></span> <span data-ttu-id="f5989-132">アクティビティ B が後で停止した場合、アクティビティ A は、スレッドの現在のアクティビティとして復元されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-132">When Activity B is later stopped activity A will be restored as the current Activity on the thread.</span></span> <span data-ttu-id="f5989-133">アクティビティが開始されると、現在の時刻が <xref:System.Diagnostics.Activity.StartTimeUtc?displayProperty=nameWithType> として取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="f5989-133">When an Activity is started it captures the current time as the <xref:System.Diagnostics.Activity.StartTimeUtc?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5989-134">停止すると、<xref:System.Diagnostics.Activity.Duration?displayProperty=nameWithType> が現在の時刻と開始時刻の差として計算されます。</span><span class="sxs-lookup"><span data-stu-id="f5989-134">When it stops <xref:System.Diagnostics.Activity.Duration?displayProperty=nameWithType> is calculated as the difference between the current time and the start time.</span></span>

### <a name="coordinating-across-process-boundaries"></a><span data-ttu-id="f5989-135">プロセス境界を越えた調整</span><span class="sxs-lookup"><span data-stu-id="f5989-135">Coordinating across process boundaries</span></span>

<span data-ttu-id="f5989-136">プロセス境界を越えて作業を追跡するためには、アクティビティの親 ID をネットワーク経由で転送し、受信側のプロセスでそれらを参照するアクティビティを作成できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5989-136">In order to track work across process boundaries Activity parent IDs need to be transmitted across the network so that the receiving process can create Activities that refer to them.</span></span> <span data-ttu-id="f5989-137">W3C TraceContext ID 形式を使用する場合、.NET では [標準](https://www.w3.org/TR/trace-context/)で推奨されている HTTP ヘッダーを使用して、この情報を転送することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5989-137">When using W3C TraceContext ID format .NET will also use the HTTP headers recommended by [the standard](https://www.w3.org/TR/trace-context/) to transmit this information.</span></span> <span data-ttu-id="f5989-138"><xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID 形式を使用する場合、.NET ではカスタムの要求 ID HTTP ヘッダーを使って ID を転送します。</span><span class="sxs-lookup"><span data-stu-id="f5989-138">When using the <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID format .NET uses a custom request-id HTTP header to transmit the ID.</span></span> <span data-ttu-id="f5989-139">他の多くの言語ランタイムとは異なり、ASP.NET Web サーバーや System.Net.Http などの .NET のインボックス ライブラリでは、HTTP メッセージのアクティビティ ID をデコードおよびエンコードする方法がネイティブに認識されています。</span><span class="sxs-lookup"><span data-stu-id="f5989-139">Unlike many other language runtimes .NET in-box libraries such as the ASP.NET web server and System.Net.Http natively understand how to decode and encode Activity IDs on HTTP messages.</span></span> <span data-ttu-id="f5989-140">ランタイムでは、同期および非同期呼び出しを介した ID のフロー方法も認識されています。</span><span class="sxs-lookup"><span data-stu-id="f5989-140">The runtime also understands how to flow the ID through sychronous and asynchronous calls.</span></span> <span data-ttu-id="f5989-141">つまり、HTTP メッセージを受信して出力する .NET アプリケーションは、アプリ開発者やサード パーティ ライブラリの依存関係を使用する特殊なコーディングを行わずに、分散トレース ID の自動フローに関与します。</span><span class="sxs-lookup"><span data-stu-id="f5989-141">This means that .NET applications that receive and emit HTTP messages participate in flowing distributed trace IDs automatically, with no special coding by the app developer nor 3rd party library dependencies.</span></span> <span data-ttu-id="f5989-142">サード パーティ ライブラリでは、HTTP 以外のメッセージ プロトコルを介した ID の転送、または HTTP のカスタム エンコード規約のサポートが追加される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5989-142">3rd party libraries may add support for transmitting IDs over non-HTTP message protocols or supporting custom encoding conventions for HTTP.</span></span>

### <a name="collecting-traces"></a><span data-ttu-id="f5989-143">トレースの収集</span><span class="sxs-lookup"><span data-stu-id="f5989-143">Collecting traces</span></span>

<span data-ttu-id="f5989-144">インストルメント化されたコードでは、分散トレースの一部として <xref:System.Diagnostics.Activity> オブジェクトを作成できますが、これらのオブジェクトの情報は、後でトレース全体を有効に確認できるように、一元化された永続ストアで転送およびシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5989-144">Instrumented code can create <xref:System.Diagnostics.Activity> objects as part of a distributed trace, but the information in these objects needs to be transmitted and serialized in a centralized persistant store so that the entire trace can be usefully reviewed later.</span></span> <span data-ttu-id="f5989-145">このタスクを実行できるテレメトリ コレクション ライブラリがいくつか ([Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing)、[OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md)、サード パーティ テレメトリまたは APM ベンダーによって提供されるライブラリなど) あります。</span><span class="sxs-lookup"><span data-stu-id="f5989-145">There are several telemetry collection libraries that can do this task such as [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing), [OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md), or a library provided by a 3rd party telemetry or APM vendor.</span></span> <span data-ttu-id="f5989-146">また、開発者は <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> または <xref:System.Diagnostics.DiagnosticListener?displayProperty=nameWithType> を使用して、独自のカスタム アクティビティ テレメトリ コレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f5989-146">Alternately developers can author their own custom Activity telemetry collection by using <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> or <xref:System.Diagnostics.DiagnosticListener?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f5989-147">ActivityListener では、開発者にそれについて予備知識があるかどうかに関係なく、アクティビティの監視がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5989-147">ActivityListener supports observing any Activity regardless whether the developer has any a-priori knowledge about it.</span></span>
<span data-ttu-id="f5989-148">これにより、ActivityListener はシンプルで柔軟な汎用ソリューションになります。</span><span class="sxs-lookup"><span data-stu-id="f5989-148">This makes ActivityListener a simple and flexible general purpose solution.</span></span> <span data-ttu-id="f5989-149">これに対して、DiagnosticListener の使用は、<xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> を呼び出すことによってインストルメント化されたコードをオプトインする必要があるより複雑なシナリオであり、コレクション ライブラリでは、開始時にインストルメント化されたコードで使用された正確な名前付け情報を認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5989-149">By contrast using DiagnosticListener is a more complex scenario that requires the instrumented code to opt-in by invoking <xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> and the collection library needs to know the exact naming information that the instrumented code used when starting it.</span></span> <span data-ttu-id="f5989-150">DiagnosticSource と DiagnosticListener を使用すると、作成者およびリスナーは任意の .NET オブジェクトを交換し、カスタマイズされた情報渡し規約を確立できます。</span><span class="sxs-lookup"><span data-stu-id="f5989-150">Using DiagnosticSource and DiagnosticListener allows the creator and listener to exchange arbitrary .NET objects and establish customized information passing conventions.</span></span>

### <a name="sampling"></a><span data-ttu-id="f5989-151">サンプリング</span><span class="sxs-lookup"><span data-stu-id="f5989-151">Sampling</span></span>

<span data-ttu-id="f5989-152">高スループット アプリケーションのパフォーマンスを向上させるために、.NET の分散トレースでは、トレースをすべて記録するのではなく、それらのサブセットのみのサンプリングがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f5989-152">For improved performance in high throughput applications, distributed tracing on .NET supports sampling only a subset of traces rather than recording all of them.</span></span> <span data-ttu-id="f5989-153">推奨される <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> API を使用して作成されたアクティビティの場合、テレメトリ コレクション ライブラリでは、<xref:System.Diagnostics.ActivityListener.Sample%2A?displayProperty=nameWithType> コールバックによるサンプリングを制御できます。</span><span class="sxs-lookup"><span data-stu-id="f5989-153">For activites created with the recommended <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> API, telemetry collection libraries can control sampling with the <xref:System.Diagnostics.ActivityListener.Sample%2A?displayProperty=nameWithType> callback.</span></span>
<span data-ttu-id="f5989-154">ログ ライブラリでは、アクティビティをまったく作成しないか、分散トレース ID の伝達に必要な最小限の情報で作成するか、あるいは完全な診断情報を設定するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f5989-154">The logging library can elect not to create the Activity at all, to create it with minimal information necessary to propagate distributing tracing IDs, or to populate it with complete diagnostic information.</span></span> <span data-ttu-id="f5989-155">このように選択できる代わりに、診断ユーティリティが増えるため、パフォーマンスのオーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="f5989-155">These choices trade-off increasing performance overhead for increasing diagnostic utility.</span></span> <span data-ttu-id="f5989-156"><xref:System.Diagnostics.Activity.%23ctor%2A?displayProperty=nameWithType> と <xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> を呼び出す古いパターンを使用して開始されたアクティビティでは、最初に <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A?displayProperty=nameWithType> を呼び出すことによって DiagnosticListener サンプリングがサポートされる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f5989-156">Activities that are started using the older pattern of invoking <xref:System.Diagnostics.Activity.%23ctor%2A?displayProperty=nameWithType> and <xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> may also support DiagnosticListener sampling by first calling <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="f5989-157">完全な診断情報を取り込む場合でも、.NET 実装は、最新のハードウェア上でアクティビティをわずかマイクロ秒で作成、設定、転送できる効率的なコレクターと高速結合されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="f5989-157">Even when capturing full diagnostic information the .NET implementation is designed to be fast - coupled with an efficient collector an Activity can be created, populated, and transmitted in about a microsecond on modern hardware.</span></span> <span data-ttu-id="f5989-158">サンプリングでは、記録されていないアクティビティごとに 100 ナノ秒未満になるようにインストルメンテーション コストを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="f5989-158">Sampling can reduce the instrumentation cost to less than 100 nanoseconds for each Activity that isn't recorded.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f5989-159">次のステップ</span><span class="sxs-lookup"><span data-stu-id="f5989-159">Next steps</span></span>

<span data-ttu-id="f5989-160">.NET アプリケーションで分散トレースの使用を開始するコード例については、「[分散トレースの概要](distributed-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5989-160">See the [Distributed Tracing Overview](distributed-tracing.md) for example code to get started using distributed tracing in .NET applications.</span></span>