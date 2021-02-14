---
title: 分散トレース - .NET
description: .NET の分散トレースの概要です。
ms.date: 02/02/2021
ms.openlocfilehash: d21d2a978cfe58d89db689dec07107f089363912
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640122"
---
# <a name="net-distributed-tracing"></a><span data-ttu-id="637be-103">.NET の分散トレース</span><span class="sxs-lookup"><span data-stu-id="637be-103">.NET Distributed Tracing</span></span>

<span data-ttu-id="637be-104">分散トレースは、分散システムでトレース データを発行して監視する方法です。</span><span class="sxs-lookup"><span data-stu-id="637be-104">Distributed tracing is the way to publish and observe tracing data in a distributed system.</span></span>
<span data-ttu-id="637be-105">.NET Framework と .NET Core では、<xref:System.Diagnostics> API によりトレースがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="637be-105">.NET Framework and .NET Core has been supporting tracing through the <xref:System.Diagnostics> APIs.</span></span>

- <span data-ttu-id="637be-106"><xref:System.Diagnostics.Activity?displayProperty=nameWithType> クラスを使用すると、診断コンテキストを格納してアクセスし、ログ システムでそれを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="637be-106"><xref:System.Diagnostics.Activity?displayProperty=nameWithType> class which allows storing and accessing diagnostics context and consuming it with logging system.</span></span>
- <span data-ttu-id="637be-107"><xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> を使用すると、インストルメント化されたプロセス内での使用に関する、リッチ データ ペイロードの運用時のログ記録のため、コードをインストルメント化することができます。</span><span class="sxs-lookup"><span data-stu-id="637be-107"><xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> that allows code to be instrumented for production-time logging of rich data payloads for consumption within the process that was instrumented.</span></span>

<span data-ttu-id="637be-108">HTTP 受信要求からトレース データを発行する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="637be-108">Here is an example that shows how to publish tracing data from the HTTP incoming requests:</span></span>

```csharp
   public void OnIncomingRequest(DiagnosticListener httpListener, HttpContext context)
   {
       if (httpListener.IsEnabled("Http_In"))
       {
           var activity = new Activity("Http_In");

           //add tags, baggage, etc.
           activity.SetParentId(context.Request.headers["Request-id"])
           foreach (var pair in context.Request.Headers["Correlation-Context"])
           {
               var baggageItem = NameValueHeaderValue.Parse(pair);
               activity.AddBaggage(baggageItem.Key, baggageItem.Value);
           }
           httpListener.StartActivity(activity, new { context });
           try
           {
               //process request ...
           }
           finally
           {
               //stop activity
               httpListener.StopActivity(activity, new {context} );
           }
       }
   }
```

<span data-ttu-id="637be-109">アクティビティ イベントをリッスンする方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="637be-109">Here is example for how to listen to the Activity events:</span></span>

```csharp
    DiagnosticListener.AllListeners.Subscribe(delegate (DiagnosticListener listener)
    {
        if (listener.Name == "MyActivitySource")
        {
            listener.Subscribe(delegate (KeyValuePair<string, object> value)
            {
                if (value.Key.EndsWith("Start", StringComparison.Ordinal))
                    LogActivityStart();
                else if (value.Key.EndsWith("Stop", StringComparison.Ordinal))
                    LogActivityStop();
            });
        }
    }
```

<span data-ttu-id="637be-110">.NET 5.0 では、[OpenTelemetry](https://opentelemetry.io/) トレース シナリオに対応するように分散トレースの機能が拡張され、サンプリング機能が追加され、トレースのコーディング パターンが簡素化され、アクティビティ イベントのリッスンが簡単かつ柔軟になっています。</span><span class="sxs-lookup"><span data-stu-id="637be-110">.NET 5.0 has extended the capability of the distributed tracing to allow the [OpenTelemetry](https://opentelemetry.io/) tracing scenarios, added Sampling capabilities, simplified the tracing coding pattern, and made listening to the Activity events easier and flexible.</span></span>

> [!NOTE]
> <span data-ttu-id="637be-111">追加されたすべての .NET 5.0 機能にアクセスするには、プロジェクトで [System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet パッケージバージョン5.0 以降を参照します。</span><span class="sxs-lookup"><span data-stu-id="637be-111">To access all added .NET 5.0 capabilities, ensure your project references the [System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet package version 5.0 or later.</span></span> <span data-ttu-id="637be-112">このパッケージは、サポートされている任意のバージョンの .NET Framework、.NET Core、.NET Standard を対象とするライブラリおよびアプリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="637be-112">This package can be used in libraries and apps targeting any supported version of the .NET Framework, .NET Core, and .NET Standard.</span></span> <span data-ttu-id="637be-113">.NET 5.0 以降を対象とする場合は、.NET ランタイムと共にインストールされる共有ライブラリに含まれているため、手動でパッケージを参照する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="637be-113">If targeting .NET 5.0 or later, there is no need to manually reference the package as it is included in the shared library installed with the .NET Runtime.</span></span>

## <a name="getting-started-with-tracing"></a><span data-ttu-id="637be-114">トレースの概要</span><span class="sxs-lookup"><span data-stu-id="637be-114">Getting Started With Tracing</span></span>

<span data-ttu-id="637be-115"><xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> と <xref:System.Diagnostics.Activity?displayProperty=nameWithType> クラスを使用するだけで、アプリケーションやライブラリから簡単にトレース データを発行できます。</span><span class="sxs-lookup"><span data-stu-id="637be-115">Applications and libraries can easily publish tracing data by simply using the <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> and the <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes.</span></span>

### <a name="activitysource"></a><span data-ttu-id="637be-116">ActivitySource</span><span class="sxs-lookup"><span data-stu-id="637be-116">ActivitySource</span></span>

<span data-ttu-id="637be-117">トレース データを発行するための最初のステップは、ActivitySource クラスのインスタンスを作成することです。</span><span class="sxs-lookup"><span data-stu-id="637be-117">The first step to publish tracing data is to create an instance of the ActivitySource class.</span></span> <span data-ttu-id="637be-118">ActivitySource クラスによって提供されている API を使用すると、Activity オブジェクトを作成して開始し、ActivityListener オブジェクトを登録してアクティビティ イベントをリッスンすることができます。</span><span class="sxs-lookup"><span data-stu-id="637be-118">The ActivitySource is the class that provides APIs to create and start Activity objects and to register ActivityListener objects to listen to the Activity events.</span></span>

```csharp
    internal static ActivitySource source = new ActivitySource("MyCompany.MyComponent.SourceName", "v1");
```

#### <a name="best-practices"></a><span data-ttu-id="637be-119">推奨する運用方法</span><span class="sxs-lookup"><span data-stu-id="637be-119">Best Practices</span></span>

- <span data-ttu-id="637be-120">ActivitySource を一度作成して静的変数に格納し、必要に応じてそのインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="637be-120">Create the ActivitySource once and store it in a static variable and use that instance as long as needed.</span></span>

- <span data-ttu-id="637be-121">コンストラクターに渡されるソース名は、他のソースと競合しないように一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="637be-121">The source name passed to the constructor has to be unique to avoid the conflicts with any other sources.</span></span> <span data-ttu-id="637be-122">会社名、コンポーネント名、ソース名が含まれる階層的な名前を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="637be-122">It is recommended to use a hierarchical name contains the company name, the component name, and the source name.</span></span> <span data-ttu-id="637be-123">たとえば、`Microsoft.System.HttpClient.HttpInOutRequests` のようにします。</span><span class="sxs-lookup"><span data-stu-id="637be-123">For example, `Microsoft.System.HttpClient.HttpInOutRequests`.</span></span>

- <span data-ttu-id="637be-124">バージョン パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="637be-124">The version parameter is optional.</span></span> <span data-ttu-id="637be-125">複数のバージョンのライブラリまたはアプリケーションをリリースする予定があり、異なるバージョンのソースを区別したい場合は、バージョンを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="637be-125">It is recommended to provide the version in case you plan to release multiple versions of the library or the application and want to distinguish between the sources of different versions.</span></span>

### <a name="activity-creation"></a><span data-ttu-id="637be-126">Activity の作成</span><span class="sxs-lookup"><span data-stu-id="637be-126">Activity Creation</span></span>

<span data-ttu-id="637be-127">これで、作成された ActivitySource オブジェクトを使用して、Activity オブジェクトを作成して開始し、コード内の任意の場所でトレース データをログすることができます。</span><span class="sxs-lookup"><span data-stu-id="637be-127">Now the created ActivitySource object can be used to create and start Activity objects which are used to log any tracing data in any desired places in the code.</span></span>

```csharp
        using (Activity activity = source.StartActivity("OperationName"))
        {
            // Do something

            activity?.AddTag("key", "value"); // log the tracing
        }
```

<span data-ttu-id="637be-128">このサンプル コードでは、Activity オブジェクトを作成してから、トレース タグ `key` と `value` をログします。</span><span class="sxs-lookup"><span data-stu-id="637be-128">This sample code tries to create the Activity object and then logs some tracing tag `key` and `value`.</span></span>

#### <a name="notes"></a><span data-ttu-id="637be-129">ノート</span><span class="sxs-lookup"><span data-stu-id="637be-129">Notes</span></span>

- <span data-ttu-id="637be-130">`ActivitySource.StartActivity` により、アクティビティの作成と開始が同時に試みられます。</span><span class="sxs-lookup"><span data-stu-id="637be-130">`ActivitySource.StartActivity` tries to create and start the activity at the same time.</span></span> <span data-ttu-id="637be-131">リストのコード パターンで使用されている `using` ブロックにより、作成された Activity オブジェクトはブロックの実行後に自動的に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="637be-131">The listed code pattern is using the `using` block which automatically disposes the created Activity object after executing the block.</span></span> <span data-ttu-id="637be-132">Activity オブジェクトを破棄すると、この開始されたアクティビティが停止するので、コードでアクティビティを明示的に停止する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="637be-132">Disposing the Activity object will stop this started activity and the code doesn't have to explicitly stop the activity.</span></span> <span data-ttu-id="637be-133">それにより、コーディング パターンが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="637be-133">That simplifies the coding pattern.</span></span>

- <span data-ttu-id="637be-134">`ActivitySource.StartActivity` により、そのようなイベントに対するリスナーがあるかどうかが内部的に調べられます。</span><span class="sxs-lookup"><span data-stu-id="637be-134">`ActivitySource.StartActivity` internally figures out if there are any listeners to such events.</span></span> <span data-ttu-id="637be-135">登録済みのリスナーが存在しない場合、またはリスナーが存在してもそのようなイベントが対象になっていない場合、`ActivitySource.StartActivity` からは単に `null` が返され、Activity オブジェクトは作成されません。</span><span class="sxs-lookup"><span data-stu-id="637be-135">If there are no registered listeners or there are listeners which are not interested in such an event, `ActivitySource.StartActivity` simply will return `null` and avoid creating the Activity object.</span></span> <span data-ttu-id="637be-136">そのため、コードの `activity?.AddTag` ステートメントで null 許容演算子 `?` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="637be-136">That is why the code used the nullable operator `?`  in the statement `activity?.AddTag`.</span></span> <span data-ttu-id="637be-137">一般に、`using` ブロック内では、常に、アクティビティ オブジェクト名の後で null 許容演算子 `?` を使用します。</span><span class="sxs-lookup"><span data-stu-id="637be-137">In general, inside the `using` block, always use the nullable operator `?` after the activity object name.</span></span>

## <a name="listening-to-the-activity-events"></a><span data-ttu-id="637be-138">アクティビティ イベントのリッスン</span><span class="sxs-lookup"><span data-stu-id="637be-138">Listening to the Activity Events</span></span>

<span data-ttu-id="637be-139">.NET で提供されている <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> クラスを使用すると、1 つまたは複数の ActivitySource からトリガーされたアクティビティ イベントをリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="637be-139">.NET provides the class <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> which can be used to listen to the Activity events triggered from one or more ActivitySources.</span></span>
<span data-ttu-id="637be-140">リスナーを使用して、トレース データの収集、サンプリング、または Activity オブジェクトの作成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="637be-140">The listener can be used to collect tracing data, sample, or force creating the Activity object.</span></span>

<span data-ttu-id="637be-141">`ActivityListener` クラスにより、さまざまなイベントを処理するためのさまざまなコールバックが提供されています。</span><span class="sxs-lookup"><span data-stu-id="637be-141">The `ActivityListener` class provides a different callbacks to handle different events.</span></span>

```csharp

ActivityListener listener = new ActivityListener()

ShouldListenTo = (activitySource) => object.ReferenceEquals(source, activitySource),
ActivityStarted = activity => /* Handle the Activity start event here */ DoSomething(),
ActivityStopped = activity => /* Handle the Activity stop event here */ DoSomething(),
SampleUsingParentId = (ref ActivityCreationOptions<string> activityOptions) => ActivitySamplingResult.AllData,
Sample = (ref ActivityCreationOptions<ActivityContext> activityOptions) => ActivitySamplingResult.AllData

// Enable the listener
ActivitySource.AddActivityListener(listener);
```

- <span data-ttu-id="637be-142">`ShouldListenTo` を使用して、特定の `ActivitySource` オブジェクトをリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="637be-142">`ShouldListenTo` enables listening to specific `ActivitySource` objects.</span></span> <span data-ttu-id="637be-143">この例では、前に作成した `ActivitySource` オブジェクトをリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="637be-143">In the example, it enables listening to the `ActivitySource` object we have previously created.</span></span> <span data-ttu-id="637be-144">入力された `ActivitySource` の `Name` と `Version` をチェックすることにより、他の `ActivitySource` オブジェクトをいっそう柔軟にリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="637be-144">There is more flexibility to listen to any other `ActivitySource` objects by checking the `Name` and `Version` of the input `ActivitySource`.</span></span>

- <span data-ttu-id="637be-145">`ActivityStarted` と `ActivityStopped` により、`ShouldListenTo` コールバックで有効にされた `ActivitySource` オブジェクトによって作成されたすべての `Activity` オブジェクトについて、`Activity` の開始イベントと停止イベントを取得できます。</span><span class="sxs-lookup"><span data-stu-id="637be-145">`ActivityStarted` and `ActivityStopped` enable getting the `Activity` Start and Stop events for all `Activity` objects created by the `ActivitySource` objects which were enabled by the `ShouldListenTo` callback.</span></span>

- <span data-ttu-id="637be-146">`Sample` と `SampleUsingParentId` は、サンプリングを目的とする主要なコールバックです。</span><span class="sxs-lookup"><span data-stu-id="637be-146">`Sample` and `SampleUsingParentId` are the main callbacks which intended for sampling.</span></span> <span data-ttu-id="637be-147">これら 2 つのコールバックから返される `ActivitySamplingResult` 列挙値により、現在の `Activity` 作成要求がサンプリングされるかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="637be-147">These two callbacks return the `ActivitySamplingResult` enum value which can tell either to sample in or out the current `Activity` creation request.</span></span> <span data-ttu-id="637be-148">コールバックから `ActivitySamplingResult.None` が返され、他の有効なリスナーにより別の値が返されない場合、Activity は作成されず、`ActivitySource.StartActivity` からは `null` が返されます。</span><span class="sxs-lookup"><span data-stu-id="637be-148">If the callback returns `ActivitySamplingResult.None` and no other enabled listeners return different value, then the Activity will not get created and `ActivitySource.StartActivity` will return `null`.</span></span> <span data-ttu-id="637be-149">それ以外の場合は、`Activity` オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="637be-149">Otherwise, the `Activity` object will get created.</span></span>

## <a name="net-50-new-features"></a><span data-ttu-id="637be-150">.NET 5.0 の新機能</span><span class="sxs-lookup"><span data-stu-id="637be-150">.NET 5.0 New Features</span></span>

<span data-ttu-id="637be-151">しばらく前から、`Activity` クラスでトレース シナリオがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="637be-151">For awhile the `Activity` class has been supporting tracing scenarios.</span></span> <span data-ttu-id="637be-152">それにより、トレース データのキーと値のペアであるタグを追加できました。</span><span class="sxs-lookup"><span data-stu-id="637be-152">It allowed adding tags which are key-value pairs of tracing data.</span></span> <span data-ttu-id="637be-153">それでは、ネットワーク経由で伝達されることが意図されたキーと値のペアである Baggage がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="637be-153">It has been supporting Baggage which is are key-value pairs intended to be propagated across the wire.</span></span>

<span data-ttu-id="637be-154">.NET 5.0 では、主に OpenTelemetry シナリオを実現するために、さらに多くの機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="637be-154">.NET 5.0 supports more features mainly to enable OpenTelemetry scenarios.</span></span>

### <a name="activitycontext"></a><span data-ttu-id="637be-155">ActivityContext</span><span class="sxs-lookup"><span data-stu-id="637be-155">ActivityContext</span></span>

<span data-ttu-id="637be-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> は、トレース操作のコンテキストを保持する構造体です (トレース ID、スパン ID、トレース フラグ、トレース状態など)。</span><span class="sxs-lookup"><span data-stu-id="637be-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> is the struct carrying the context of the tracing operations (e.g. the trace Id, Span Id, trace flags, and trace state).</span></span> <span data-ttu-id="637be-157">親トレース コンテキストを提供して、新しい `Activity` を作成できます。</span><span class="sxs-lookup"><span data-stu-id="637be-157">Now it is possible to create a new `Activity` providing the parent tracing context.</span></span> <span data-ttu-id="637be-158">また、`Activity.Context` プロパティを呼び出すことにより、任意の `Activity` オブジェクトからトレース コンテキストを簡単に抽出できます。</span><span class="sxs-lookup"><span data-stu-id="637be-158">Also, it is easy to extract the tracing context from any `Activity` object by calling `Activity.Context` property.</span></span>

### <a name="activitylink"></a><span data-ttu-id="637be-159">ActivityLink</span><span class="sxs-lookup"><span data-stu-id="637be-159">ActivityLink</span></span>

<span data-ttu-id="637be-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> は、一時的に関連付けられた `Activity` オブジェクトにリンクできるトレース コンテキスト インスタンスが格納される構造体です。</span><span class="sxs-lookup"><span data-stu-id="637be-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> is the struct containing the tracing context instance which can be linked to casually related `Activity` objects.</span></span> <span data-ttu-id="637be-161">`Activity` を作成するときにリンク リストを `ActivitySource.StartActivity` メソッドに渡すことによって、`Activity` オブジェクトにリンクを追加できます。</span><span class="sxs-lookup"><span data-stu-id="637be-161">Links can be added to the `Activity` object by passing the links list to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="637be-162">リンクをアタッチされた `Activity` オブジェクトは、`Activity.Links` プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="637be-162">The `Activity` object attached links can be retrieved using the property `Activity.Links`.</span></span>

### <a name="activityevent"></a><span data-ttu-id="637be-163">ActivityEvent</span><span class="sxs-lookup"><span data-stu-id="637be-163">ActivityEvent</span></span>

<span data-ttu-id="637be-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> は、名前とタイムスタンプおよび必要に応じてタグのリストが含まれる、イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="637be-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> represents an event containing a name and a timestamp, as well as an optional list of tags.</span></span> <span data-ttu-id="637be-165">`Activity.AddEvent` メソッドを呼び出すことによって、イベントを `Activity` オブジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="637be-165">Events can be added to the `Activity` object by calling `Activity.AddEvent` method.</span></span> <span data-ttu-id="637be-166">`Activity` オブジェクト イベントのリスト全体は、`Activity.Events` プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="637be-166">The whole list of the `Activity` object Events can be retrieved using the property `Activity.Events`.</span></span>

### <a name="activitykind"></a><span data-ttu-id="637be-167">ActivityKind</span><span class="sxs-lookup"><span data-stu-id="637be-167">ActivityKind</span></span>

<span data-ttu-id="637be-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> には、トレースでのアクティビティ、その親、その子の間の関係が記述されています。</span><span class="sxs-lookup"><span data-stu-id="637be-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> describes the relationship between the activity, its parents and its children in a trace.</span></span> <span data-ttu-id="637be-169">`Activity` を作成するときに種類の値を `ActivitySource.StartActivity` メソッドに渡すことによって、`Activity` オブジェクトに種類を設定できます。</span><span class="sxs-lookup"><span data-stu-id="637be-169">Kind can be set to the `Activity` object by passing the kind value to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="637be-170">`Activity` オブジェクトの種類は、`Activity.Kind` プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="637be-170">The `Activity` object kind can be retrieved using the property `Activity.Kind`.</span></span>

### <a name="isalldatarequested"></a><span data-ttu-id="637be-171">IsAllDataRequested</span><span class="sxs-lookup"><span data-stu-id="637be-171">IsAllDataRequested</span></span>

<span data-ttu-id="637be-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> は、すべての伝達情報に加えて、リンク、タグ、イベントなどの他のすべてのプロパティをこのアクティビティに設定する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="637be-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> indicates whether this activity should be populated with all the propagation information, as well as all the other properties, such as links, tags, and events.</span></span> <span data-ttu-id="637be-173">`IsAllDataRequested` の値は、すべてのリスナーの `Sample` および `SampleUsingParentId` コールバックから返される結果から決定されます。</span><span class="sxs-lookup"><span data-stu-id="637be-173">The value of `IsAllDataRequested` is determined from the result returned from all listeners `Sample` and `SampleUsingParentId` callbacks.</span></span> <span data-ttu-id="637be-174">その値は、`Activity.IsAllDataRequested` プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="637be-174">The value can be retrieved using `Activity.IsAllDataRequested` property.</span></span>

### <a name="activitysource"></a><span data-ttu-id="637be-175">Activity.Source</span><span class="sxs-lookup"><span data-stu-id="637be-175">Activity.Source</span></span>

<span data-ttu-id="637be-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> を使用すると、このアクティビティに関連付けられているアクティビティ ソースが取得されます。</span><span class="sxs-lookup"><span data-stu-id="637be-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> gets the activity source associated with this activity.</span></span>

### <a name="activitydisplayname"></a><span data-ttu-id="637be-177">Activity.DisplayName</span><span class="sxs-lookup"><span data-stu-id="637be-177">Activity.DisplayName</span></span>

<span data-ttu-id="637be-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> を使用すると、アクティビティの表示名を取得または設定できます。</span><span class="sxs-lookup"><span data-stu-id="637be-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> allows getting or setting a display name for the activity.</span></span>

### <a name="activitytagobjects"></a><span data-ttu-id="637be-179">Activity.TagObjects</span><span class="sxs-lookup"><span data-stu-id="637be-179">Activity.TagObjects</span></span>

<span data-ttu-id="637be-180">`Activity` クラスの `Activity.Tags` プロパティからは、キーと値に対する文字列型のタグのキーと値のペアのリストが返されます。</span><span class="sxs-lookup"><span data-stu-id="637be-180">`Activity` class has the property `Activity.Tags` which return the a key-value pair list of the tags of type string for the key and value.</span></span> <span data-ttu-id="637be-181">`AddTag(string, string)` メソッドを使用して、その Tags を `Activity` に追加できます。</span><span class="sxs-lookup"><span data-stu-id="637be-181">Such Tags can be added to the `Activity` using the method `AddTag(string, string)`.</span></span> <span data-ttu-id="637be-182">`Activity` によるタグのサポートは、任意の型の値を許可するオーバーロードされた `AddTag(string, object)` メソッドを提供することによって拡張されています。</span><span class="sxs-lookup"><span data-stu-id="637be-182">`Activity` has extended the support of tags by providing the overloaded method `AddTag(string, object)` allowing values of any type.</span></span>  <span data-ttu-id="637be-183">そのようなタグの完全なリストは、<xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType> を使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="637be-183">The complete list of such tags can be retrieved using <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType>.</span></span>

## <a name="sampling"></a><span data-ttu-id="637be-184">サンプリング</span><span class="sxs-lookup"><span data-stu-id="637be-184">Sampling</span></span>

<span data-ttu-id="637be-185">サンプリングは、収集されてバックエンドに送信されるトレースのサンプル数を減らすことによって、ノイズとオーバーヘッドを制御するメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="637be-185">Sampling is a mechanism to control the noise and overhead by reducing the number of samples of traces collected and sent to the backend.</span></span> <span data-ttu-id="637be-186">サンプリングは、重要な OpenTelemetry シナリオです。</span><span class="sxs-lookup"><span data-stu-id="637be-186">Sampling is an important OpenTelemetry scenario.</span></span> <span data-ttu-id="637be-187">.NET 5.0 では、サンプリングを簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="637be-187">In .NET 5.0 it is easy to allow sampling.</span></span> <span data-ttu-id="637be-188">よい方法は、`ActivitySource.StartActivity` を使用して新しい `Activity` オブジェクトを作成し、このメソッドを呼び出すときに使用可能なすべてのデータ (タグ、種類、リンクなど) を指定することです。</span><span class="sxs-lookup"><span data-stu-id="637be-188">A good practice is to create the new `Activity` objects using `ActivitySource.StartActivity` and try to provide all possible available data (e.g. tags, kind, links, ...etc.) when calling this method.</span></span> <span data-ttu-id="637be-189">データを指定すると、`ActivityListener` を使用して実装されたサンプラーで、サンプリングを適切に決定できます。</span><span class="sxs-lookup"><span data-stu-id="637be-189">Providing the data will allow the samplers implemented using the `ActivityListener` to have a proper sampling decision.</span></span> <span data-ttu-id="637be-190">`Activity` オブジェクトが作成される前にデータが作成されないようにするため、パフォーマンスが重要な場合は、`ActivitySource.HasListeners` プロパティを使用して、必要なデータを作成する前にリスナーがあるかどうかを簡単にチェックできます。</span><span class="sxs-lookup"><span data-stu-id="637be-190">If the performance is critical to avoid creating the data before creating the `Activity` object, the property `ActivitySource.HasListeners` comes in handy to check if there are any listeners before creating the needed data.</span></span>

## <a name="opentelemetry"></a><span data-ttu-id="637be-191">OpenTelemetry</span><span class="sxs-lookup"><span data-stu-id="637be-191">OpenTelemetry</span></span>

<span data-ttu-id="637be-192">OpenTelemetry SDK には、エンド ツー エンドの分散トレース シナリオをサポートする多くの機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="637be-192">OpenTelemetry SDK comes with many features that support end-to-end distributed tracing scenarios.</span></span> <span data-ttu-id="637be-193">複数のサンプラーとエクスポーターが用意されており、そこから選択できます。</span><span class="sxs-lookup"><span data-stu-id="637be-193">It provides multiple samplers and exporters which you can choose from.</span></span> <span data-ttu-id="637be-194">これにより、カスタム サンプラーとエクスポーターを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="637be-194">It allows creating a custom samplers and exporters too.</span></span>

<span data-ttu-id="637be-195">OpenTelemetry では、収集されたトレース データの異なるバックエンド (Jaeger、Zipkin、New Relic など) へのエクスポートがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="637be-195">OpenTelemetry supports exporting the collected tracing data to different backends (e.g. Jaeger, Zipkin, New Relic,...etc.).</span></span> <span data-ttu-id="637be-196">詳細については、「[OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/)」 を参照してください。また、エクスポーターのパッケージの一覧を取得するには、`OpenTelemetry.Exporter.` で始まるパッケージを Nuget.org で検索してください。</span><span class="sxs-lookup"><span data-stu-id="637be-196">Refer to [OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/) for more details and search Nuget.org for packages starting with `OpenTelemetry.Exporter.` to get the exporter packages list.</span></span>

<span data-ttu-id="637be-197">次に示すのは [OpenTelemetry-dotnet の概要](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started)から移植されたサンプル コードであり、トレース データを簡単にサンプリングしてコンソールにエクスポートする方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="637be-197">Here is sample code ported from [OpenTelemetry-dotnet getting started](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) showing how easy it is to sample and export tracing data to the console.</span></span>

```csharp
// <copyright file="Program.cs" company="OpenTelemetry Authors">
// Copyright The OpenTelemetry Authors
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
// </copyright>

using System.Diagnostics;
using OpenTelemetry;
using OpenTelemetry.Trace;

public class Program
{
    private static readonly ActivitySource MyActivitySource = new ActivitySource(
        "MyCompany.MyProduct.MyLibrary");

    public static void Main()
    {
        using var tracerProvider = Sdk.CreateTracerProviderBuilder()
            .SetSampler(new AlwaysOnSampler())
            .AddSource("MyCompany.MyProduct.MyLibrary")
            .AddConsoleExporter()
            .Build();

        using (var activity = MyActivitySource.StartActivity("SayHello"))
        {
            activity?.SetTag("foo", 1);
            activity?.SetTag("bar", "Hello, World!");
            activity?.SetTag("baz", new int[] { 1, 2, 3 });
        }
    }
}
```

<span data-ttu-id="637be-198">このサンプルでは、[OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2) パッケージを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="637be-198">The sample needs to reference the package [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2).</span></span>
