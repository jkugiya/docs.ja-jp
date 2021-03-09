---
title: 分散トレース - .NET
description: .NET の分散トレースの概要です。
ms.date: 02/02/2021
ms.openlocfilehash: 44022232d4451f8d8a255a352206d7bdc9cb4e5c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105572"
---
# <a name="net-distributed-tracing"></a>.NET の分散トレース

分散トレースは、分散システムでトレース データを発行して監視する方法です。
.NET Framework と .NET Core では、<xref:System.Diagnostics> API によりトレースがサポートされています。

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType> クラスを使用すると、診断コンテキストを格納してアクセスし、ログ システムでそれを使用することができます。
- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> を使用すると、インストルメント化されたプロセス内での使用に関する、リッチ データ ペイロードの運用時のログ記録のため、コードをインストルメント化することができます。

HTTP 受信要求からトレース データを発行する方法の例を次に示します。

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

アクティビティ イベントをリッスンする方法の例を次に示します。

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

.NET 5.0 では、[OpenTelemetry](https://opentelemetry.io/) トレース シナリオに対応するように分散トレースの機能が拡張され、サンプリング機能が追加され、トレースのコーディング パターンが簡素化され、アクティビティ イベントのリッスンが簡単かつ柔軟になっています。

> [!NOTE]
> 追加されたすべての .NET 5.0 機能にアクセスするには、プロジェクトで [System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet パッケージバージョン5.0 以降を参照します。 このパッケージは、サポートされている任意のバージョンの .NET Framework、.NET Core、.NET Standard を対象とするライブラリおよびアプリで使用できます。 .NET 5.0 以降を対象とする場合は、.NET ランタイムと共にインストールされる共有ライブラリに含まれているため、手動でパッケージを参照する必要はありません。

## <a name="getting-started-with-tracing"></a>トレースの概要

<xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> と <xref:System.Diagnostics.Activity?displayProperty=nameWithType> クラスを使用するだけで、アプリケーションやライブラリから簡単にトレース データを発行できます。

### <a name="activitysource"></a>ActivitySource

トレース データを発行するための最初のステップは、ActivitySource クラスのインスタンスを作成することです。 ActivitySource クラスによって提供されている API を使用すると、Activity オブジェクトを作成して開始し、ActivityListener オブジェクトを登録してアクティビティ イベントをリッスンすることができます。

```csharp
    private static ActivitySource source = new ActivitySource("MyCompany.MyComponent.SourceName", "v1");
```

#### <a name="best-practices"></a>推奨する運用方法

- ActivitySource を一度作成して静的変数に格納し、必要に応じてそのインスタンスを使用します。

- コンストラクターに渡されるソース名は、他のソースと競合しないように一意である必要があります。 会社名、コンポーネント名、ソース名が含まれる階層的な名前を使用することをお勧めします。 たとえば、`Microsoft.System.HttpClient.HttpInOutRequests` のようにします。

- バージョン パラメーターは省略可能です。 複数のバージョンのライブラリまたはアプリケーションをリリースする予定があり、異なるバージョンのソースを区別したい場合は、バージョンを指定することをお勧めします。

### <a name="activity-creation"></a>Activity の作成

これで、作成された ActivitySource オブジェクトを使用して、Activity オブジェクトを作成して開始し、コード内の任意の場所でトレース データをログすることができます。

```csharp
        using (Activity activity = source.StartActivity("OperationName"))
        {
            // Do something

            activity?.AddTag("key", "value"); // log the tracing
        }
```

このサンプル コードでは、Activity オブジェクトを作成してから、トレース タグ `key` と `value` をログします。

#### <a name="notes"></a>ノート

- `ActivitySource.StartActivity` により、アクティビティの作成と開始が同時に試みられます。 リストのコード パターンで使用されている `using` ブロックにより、作成された Activity オブジェクトはブロックの実行後に自動的に破棄されます。 Activity オブジェクトを破棄すると、この開始されたアクティビティが停止するので、コードでアクティビティを明示的に停止する必要はありません。 それにより、コーディング パターンが簡単になります。

- `ActivitySource.StartActivity` により、そのようなイベントに対するリスナーがあるかどうかが内部的に調べられます。 登録済みのリスナーが存在しない場合、またはリスナーが存在してもそのようなイベントが対象になっていない場合、`ActivitySource.StartActivity` からは単に `null` が返され、Activity オブジェクトは作成されません。 そのため、コードの `activity?.AddTag` ステートメントで null 許容演算子 `?` が使用されています。 一般に、`using` ブロック内では、常に、アクティビティ オブジェクト名の後で null 許容演算子 `?` を使用します。

## <a name="listening-to-the-activity-events"></a>アクティビティ イベントのリッスン

.NET で提供されている <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> クラスを使用すると、1 つまたは複数の ActivitySource からトリガーされたアクティビティ イベントをリッスンできます。
リスナーを使用して、トレース データの収集、サンプリング、または Activity オブジェクトの作成を行うことができます。

`ActivityListener` クラスにより、さまざまなイベントを処理するためのさまざまなコールバックが提供されています。

```csharp
var listener = new ActivityListener
{
    ShouldListenTo = (activitySource) => object.ReferenceEquals(source, activitySource),
    ActivityStarted = activity => /* Handle the Activity start event here */ DoSomething(),
    ActivityStopped = activity => /* Handle the Activity stop event here */ DoSomething(),
    SampleUsingParentId = (ref ActivityCreationOptions<string> activityOptions) => ActivitySamplingResult.AllData,
    Sample = (ref ActivityCreationOptions<ActivityContext> activityOptions) => ActivitySamplingResult.AllData
};

// Enable the listener
ActivitySource.AddActivityListener(listener);
```

- `ShouldListenTo` を使用して、特定の `ActivitySource` オブジェクトをリッスンできます。 この例では、前に作成した `ActivitySource` オブジェクトをリッスンできます。 入力された `ActivitySource` の `Name` と `Version` をチェックすることにより、他の `ActivitySource` オブジェクトをいっそう柔軟にリッスンできます。

- `ActivityStarted` と `ActivityStopped` により、`ShouldListenTo` コールバックで有効にされた `ActivitySource` オブジェクトによって作成されたすべての `Activity` オブジェクトについて、`Activity` の開始イベントと停止イベントを取得できます。

- `Sample` と `SampleUsingParentId` は、サンプリングを目的とする主要なコールバックです。 これら 2 つのコールバックから返される `ActivitySamplingResult` 列挙値により、現在の `Activity` 作成要求がサンプリングされるかどうかがわかります。 コールバックから `ActivitySamplingResult.None` が返され、他の有効なリスナーにより別の値が返されない場合、Activity は作成されず、`ActivitySource.StartActivity` からは `null` が返されます。 それ以外の場合は、`Activity` オブジェクトが作成されます。

## <a name="net-50-new-features"></a>.NET 5.0 の新機能

しばらく前から、`Activity` クラスでトレース シナリオがサポートされています。 それにより、トレース データのキーと値のペアであるタグを追加できました。 それでは、ネットワーク経由で伝達されることが意図されたキーと値のペアである Baggage がサポートされています。

.NET 5.0 では、主に OpenTelemetry シナリオを実現するために、さらに多くの機能がサポートされています。

### <a name="activitycontext"></a>ActivityContext

<xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> は、トレース操作のコンテキストを保持する構造体です (トレース ID、スパン ID、トレース フラグ、トレース状態など)。 親トレース コンテキストを提供して、新しい `Activity` を作成できます。 また、`Activity.Context` プロパティを呼び出すことにより、任意の `Activity` オブジェクトからトレース コンテキストを簡単に抽出できます。

### <a name="activitylink"></a>ActivityLink

<xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> は、一時的に関連付けられた `Activity` オブジェクトにリンクできるトレース コンテキスト インスタンスが格納される構造体です。 `Activity` を作成するときにリンク リストを `ActivitySource.StartActivity` メソッドに渡すことによって、`Activity` オブジェクトにリンクを追加できます。 リンクをアタッチされた `Activity` オブジェクトは、`Activity.Links` プロパティを使用して取得できます。

### <a name="activityevent"></a>ActivityEvent

<xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> は、名前とタイムスタンプおよび必要に応じてタグのリストが含まれる、イベントを表します。 `Activity.AddEvent` メソッドを呼び出すことによって、イベントを `Activity` オブジェクトに追加できます。 `Activity` オブジェクト イベントのリスト全体は、`Activity.Events` プロパティを使用して取得できます。

### <a name="activitykind"></a>ActivityKind

<xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> には、トレースでのアクティビティ、その親、その子の間の関係が記述されています。 `Activity` を作成するときに種類の値を `ActivitySource.StartActivity` メソッドに渡すことによって、`Activity` オブジェクトに種類を設定できます。 `Activity` オブジェクトの種類は、`Activity.Kind` プロパティを使用して取得できます。

### <a name="isalldatarequested"></a>IsAllDataRequested

<xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> は、すべての伝達情報に加えて、リンク、タグ、イベントなどの他のすべてのプロパティをこのアクティビティに設定する必要があるかどうかを示します。 `IsAllDataRequested` の値は、すべてのリスナーの `Sample` および `SampleUsingParentId` コールバックから返される結果から決定されます。 その値は、`Activity.IsAllDataRequested` プロパティを使用して取得できます。

### <a name="activitysource"></a>Activity.Source

<xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> を使用すると、このアクティビティに関連付けられているアクティビティ ソースが取得されます。

### <a name="activitydisplayname"></a>Activity.DisplayName

<xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> を使用すると、アクティビティの表示名を取得または設定できます。

### <a name="activitytagobjects"></a>Activity.TagObjects

`Activity` クラスの `Activity.Tags` プロパティからは、キーと値に対する文字列型のタグのキーと値のペアのリストが返されます。 `AddTag(string, string)` メソッドを使用して、その Tags を `Activity` に追加できます。 `Activity` によるタグのサポートは、任意の型の値を許可するオーバーロードされた `AddTag(string, object)` メソッドを提供することによって拡張されています。  そのようなタグの完全なリストは、<xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType> を使用して取得できます。

## <a name="sampling"></a>サンプリング

サンプリングは、収集されてバックエンドに送信されるトレースのサンプル数を減らすことによって、ノイズとオーバーヘッドを制御するメカニズムです。 サンプリングは、重要な OpenTelemetry シナリオです。 .NET 5.0 では、サンプリングを簡単に行うことができます。 よい方法は、`ActivitySource.StartActivity` を使用して新しい `Activity` オブジェクトを作成し、このメソッドを呼び出すときに使用可能なすべてのデータ (タグ、種類、リンクなど) を指定することです。 データを指定すると、`ActivityListener` を使用して実装されたサンプラーで、サンプリングを適切に決定できます。 `Activity` オブジェクトが作成される前にデータが作成されないようにするため、パフォーマンスが重要な場合は、`ActivitySource.HasListeners` プロパティを使用して、必要なデータを作成する前にリスナーがあるかどうかを簡単にチェックできます。

## <a name="opentelemetry"></a>OpenTelemetry

OpenTelemetry SDK には、エンド ツー エンドの分散トレース シナリオをサポートする多くの機能が用意されています。 複数のサンプラーとエクスポーターが用意されており、そこから選択できます。 これにより、カスタム サンプラーとエクスポーターを作成することもできます。

OpenTelemetry では、収集されたトレース データの異なるバックエンド (Jaeger、Zipkin、New Relic など) へのエクスポートがサポートされています。 詳細については、「[OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/)」 を参照してください。また、エクスポーターのパッケージの一覧を取得するには、`OpenTelemetry.Exporter.` で始まるパッケージを Nuget.org で検索してください。

次に示すのは [OpenTelemetry-dotnet の概要](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started)から移植されたサンプル コードであり、トレース データを簡単にサンプリングしてコンソールにエクスポートする方法がわかります。

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

このサンプルでは、[OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2) パッケージを参照する必要があります。
