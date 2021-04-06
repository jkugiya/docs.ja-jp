---
title: 分散トレース インストルメンテーションを追加する - .NET
description: .NET アプリケーションで分散トレースをインストルメント化するためのチュートリアル
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: 4eb791499855a1479393ef2e00d86316a81409a1
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231154"
---
# <a name="adding-distributed-tracing-instrumentation"></a>分散トレース インストルメンテーションの追加

**この記事の対象: ✔️** .NET Core 2.1 以降のバージョン **および** .NET Framework 4.5 以降のバージョン

.NET アプリケーションを <xref:System.Diagnostics.Activity?displayProperty=nameWithType> API を使用してインストルメント化し、分散トレース テレメトリを生成することができます。 一部のインストルメンテーションは標準の .NET ライブラリに組み込まれていますが、さらに追加してコードをより簡単に診断できるようにすることができます。 このチュートリアルでは、新しいカスタム分散トレース インストルメンテーションを追加します。 このインストルメンテーションによって生成されるテレメトリの記録の詳細については、[コレクションのチュートリアル](distributed-tracing-instrumentation-walkthroughs.md)を参照してください。

## <a name="prerequisites"></a>前提条件

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン

## <a name="an-initial-app"></a>最初のアプリ

最初に、OpenTelemetry を使用してテレメトリを収集するサンプル アプリを作成しますが、インストルメンテーションはまだありません。

```dotnetcli
dotnet new console
```

.NET 5 以降をターゲットとするアプリケーションには、必要な分散トレース API が既に含まれています。 以前のバージョンの .NET をターゲットとするアプリの場合は、[System.Diagnostics.DiagnosticSource NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) バージョン 5 以降を追加します。

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

テレメトリを収集するために使用される [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry/) および [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet パッケージを追加します。

```dotnetcli
dotnet add package OpenTelemetry
dotnet add package OpenTelemetry.Exporter.Console
```

生成された Program.cs の内容を次のソース例に置き換えます。

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static async Task Main(string[] args)
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork("banana", 8);
            Console.WriteLine("Example work done");
        }

        // All the functions below simulate doing some arbitrary work
        static async Task DoSomeWork(string foo, int bar)
        {
            await StepOne();
            await StepTwo();
        }

        static async Task StepOne()
        {
            await Task.Delay(500);
        }

        static async Task StepTwo()
        {
            await Task.Delay(1000);
        }
    }
}
```

アプリにはまだインストルメンテーションがないため、表示されるトレース情報はありません。

```dotnetcli
> dotnet run
Example work done
```

#### <a name="best-practices"></a>推奨する運用方法

この例の OpenTelemetry など、分散トレース テレメトリを収集するためにオプションのサード パーティ ライブラリを参照する必要があるのは、アプリ開発者のみです。 .NET ライブラリの作成者は、.NET ランタイムの一部である System.Diagnostics.DiagnosticSource 内の API にのみ依存できます。 これにより、テレメトリの収集に使用するライブラリまたはベンダーに関するアプリ開発者の設定に関係なく、さまざまな .NET アプリでライブラリが確実に実行されるようになります。

## <a name="adding-basic-instrumentation"></a>基本インストルメンテーションの追加

アプリケーションとライブラリでは、<xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> および <xref:System.Diagnostics.Activity?displayProperty=nameWithType> クラスを使用して分散トレース インストルメンテーションが追加されます。

### <a name="activitysource"></a>ActivitySource

まず ActivitySource のインスタンスを作成します。 ActivitySource により、アクティビティ オブジェクトを作成および開始するための API が提供されます。 Main() および `using System.Diagnostics;` の上の静的 ActivitySource 変数を using ステートメントに追加します。

```csharp
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        private static ActivitySource source = new ActivitySource("Sample.DistributedTracing", "1.0.0");

        static async Task Main(string[] args)
        {
            ...
```

#### <a name="best-practices"></a>推奨する運用方法

- ActivitySource を一度作成し、静的変数に格納し、必要に応じてそのインスタンスを使用します。
各ライブラリまたはライブラリのサブコンポーネントでは、独自のソースを作成することができます (多くの場合、そうする必要があります)。 アプリ開発者がソース内のアクティビティ テレメトリを個別に有効または無効にできることが予想される場合は、既存のソースを再利用するのではなく、新しいものを作成することを検討してください。

- コンストラクターに渡されるソース名は、他のソースと競合しないように一意である必要があります。
同じアセンブリ内に複数のソースが存在する場合は、アセンブリ名を含む階層名と、必要に応じてコンポーネント名を使用することをお勧めします。 たとえば、「 `Microsoft.AspNetCore.Hosting` 」のように入力します。 アセンブリで 2 番目の独立したアセンブリにコードのインストルメンテーションを追加する場合、その名前は、コードがインストルメント化されるアセンブリではなく、ActivitySource を定義するアセンブリに基づいている必要があります。

- バージョン パラメーターは省略可能です。 複数のバージョンのライブラリをリリースし、インストルメント化されたテレメトリに変更を加える場合は、バージョンを指定することをお勧めします。

> [!NOTE]
> OpenTelemetry では、代替用語である "トレーサー" と "スパン" を使用します。 .NET では、"ActivitySource" はトレーサーの実装であり、アクティビティは "スパン" の実装です。 .NET の long 型のアクティビティは OpenTelemetry 仕様より前のものであり、.NET エコシステム内の一貫性および .NET アプリケーションの互換性のために元の .NET の名前付けが保持されています。

### <a name="activity-creation"></a>Activity の作成

ActivitySource オブジェクトを使用し、意味のある作業単位に基づいてアクティビティ オブジェクトを開始および停止します。 ここに示すコードで DoSomeWork() を更新します。

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }
```

これで、アプリを実行すると、ログに記録される新しいアクティビティが表示されるようになりました。

```dotnetcli
> dotnet run
Activity.Id:          00-f443e487a4998c41a6fd6fe88bae644e-5b7253de08ed474f-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:36:51.4720202Z
Activity.Duration:    00:00:01.5025842
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 067f4bb5-a5a8-4898-a288-dec569d6dbef
```

#### <a name="notes"></a>Notes

- <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> では、アクティビティを同時に作成して開始します。 リストのコード パターンで使用されている `using` ブロックにより、作成された Activity オブジェクトはブロックの実行後に自動的に破棄されます。 アクティビティ オブジェクトを破棄すると停止し、コードで明示的に <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType> を呼び出す必要がなくなります。
それにより、コーディング パターンが簡単になります。

- <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> では、アクティビティを記録しているリスナーが存在するかどうかを内部で判断します。 登録済みのリスナーが存在しない場合、または対象ではないリスナーが存在する場合、StartActivity() によって `null` が返され、アクティビティ オブジェクトは作成されません。 これでパフォーマンスが最適化されるため、非常に頻繁に呼び出される関数でもコード パターンを使用できます。

## <a name="optional-populate-tags"></a>省略可能: タグを設定する

アクティビティではタグと呼ばれるキー値データがサポートされます。これらは一般的に、診断に役立つ可能性のある作業のパラメーターを格納するために使用されます。 DoSomeWork() を更新してそれらが含まれるようにします。

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                await StepTwo();
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-2b56072db8cb5a4496a4bfb69f46aa06-7bc4acda3b9cce4d-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:37:31.4949570Z
Activity.Duration:    00:00:01.5417719
Activity.TagObjects:
    foo: banana
    bar: 8
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 25bbc1c3-2de5-48d9-9333-062377fea49c

Example work done
```

#### <a name="best-practices"></a>推奨する運用方法

- 前述のように、`activity` によって返される <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> は null である可能性があります。 null 合体演算子 ? (C#) は、アクティビティが null でない場合に <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> のみを呼び出すのに短くて便利なものです。 この動作は書き込みと同じです。

```csharp
if(activity != null)
{
    activity.SetTag("foo", foo);
}
```

- OpenTelemetry では、一般的な種類のアプリケーション作業を表すアクティビティにタグを設定するために推奨される一連の[規約](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions)が提供されます。

- ハイ パフォーマンスが求められる関数をインストルメント化する場合、<xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> は、アクティビティをリッスンしているいずれかのコードでタグなどの補助情報を読み取ることを目的としているかどうかを示すヒントとなります。 リスナーがそれを読み取らない場合、インストルメント化されたコードでそれを設定する CPU サイクルを消費する必要はありません。 わかりやすくするために、このサンプルではその最適化を適用しません。

## <a name="optional-adding-events"></a>省略可能: イベントの追加

イベントは、追加の診断データの任意のストリームをアクティビティにアタッチできるタイムスタンプが付いたメッセージです。 アクティビティにいくつかのイベントを追加します。

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-82cf6ea92661b84d9fd881731741d04e-33fff2835a03c041-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:39:10.6902609Z
Activity.Duration:    00:00:01.5147582
Activity.TagObjects:
    foo: banana
    bar: 8
Activity.Events:
    Part way there [3/18/2021 10:39:11 AM +00:00]
    Done now [3/18/2021 10:39:12 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: ea7f0fcb-3673-48e0-b6ce-e4af5a86ce4f

Example work done
```

#### <a name="best-practices"></a>推奨する運用方法

- イベントは、転送できるようになるまでメモリ内の一覧に格納されます。これにより、このメカニズムが、適度な数のイベントの記録にのみ適したものとなります。 大容量または無制限の量のイベントの場合、[ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) など、このタスクに重点を置いたログ API を使用することをお勧めします。 また、ILogger を使えば、アプリ開発者が分散トレースを使用することを選択したかどうかに関係なく、ログ情報を確実に利用できるようになります。
ILogger ではアクティブなアクティビティ ID の自動取り込みがサポートされるため、その API を介してログに記録されたメッセージは、引き続き分散トレースに関連付けることができます。

## <a name="optional-adding-status"></a>省略可能: 状態の追加

OpenTelemetry を使用すると、各アクティビティで、作業の成功/失敗の結果を表す[状態](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status)を報告することができます。 そのため、現在、.NET には厳密に型指定された API がありませんが、タグを使用して確立された規約があります。

- `otel.status_code` は、`StatusCode` を格納するために使用されるタグ名です。 StatusCode タグの値は、文字列 "UNSET"、"OK"、"ERROR" のいずれかである必要があります。これらはそれぞれ StatusCode からの列挙型 `Unset`、`Ok`、`Error` に対応しています。
- `otel.status_description` は、省略可能な `Description` を格納するために使用されるタグ名です

DoSomeWork() を更新して状態を設定します。

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));

                // Pretend something went wrong
                activity?.SetTag("otel.status_code", "ERROR");
                activity?.SetTag("otel.status_description", "Use this text give more information about the error");
            }
        }
```

## <a name="optional-add-additional-activities"></a>省略可能: アクティビティをさらに追加する

アクティビティを入れ子にして、より大きな作業単位の部分を記述できます。 これは、短時間で実行されないおそれがあるコードの部分に関して、あるいは特定の外部依存関係からのエラーをより適切にローカライズするために特に役立ちます。 このサンプルでは、すべての方法でアクティビティを使用していますが、それは追加のコードが最小化されているだけの理由によるものです。 すべての方法でアクティビティを使用するより大規模で現実的なプロジェクトでは、非常に詳細なトレースが生成されるため、推奨されません。

StepOne と StepTwo を更新して、これらの個々のステップに関するトレースをさらに追加します。

```csharp
        static async Task StepOne()
        {
            using (Activity activity = source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity activity = source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-39cac574e8fda44b-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4278822Z
Activity.Duration:    00:00:00.5051364
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-4ccccb6efdc59546-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.9441095Z
Activity.Duration:    00:00:01.0052729
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4256627Z
Activity.Duration:    00:00:01.5286408
Activity.TagObjects:
    foo: banana
    bar: 8
    otel.status_code: ERROR
    otel.status_description: Use this text give more information about the error
Activity.Events:
    Part way there [3/18/2021 10:40:51 AM +00:00]
    Done now [3/18/2021 10:40:52 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Example work done
```

StepOne と StepTwo の両方に、SomeWork を参照する ParentId が含まれていることに注目してください。 コンソールは、入れ子になった作業ツリーを視覚化するのに最適ではありませんが、[Zipkin](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md) などの多くの GUI ビューアーでは、これをガント チャートとして表示できます。

[![Zipkin ガント チャート](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)

### <a name="optional-activitykind"></a>省略可能: ActivityKind

アクティビティには、アクティビティ、その親およびその子の間の関係を記述する <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType> プロパティがあります。 既定では、すべての新しいアクティビティが <xref:System.Diagnostics.ActivityKind.Internal> に設定されます。これは、リモートの親や子がないアプリケーション内の内部操作であるアクティビティに適しています。 その他の種類は、<xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> で kind パラメーターを使用して設定することができます。 その他のオプションについては、<xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> を参照してください。

### <a name="optional-links"></a>省略可能: リンク

バッチ処理システムで作業が行われると、1 つのアクティビティにより、多くの異なる要求に代わって同時に作業が表される可能性があり、それぞれに独自のトレース ID があります。アクティビティは 1 つの親を持つように制限されていますが、<xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> を使用して追加のトレース ID にリンクすることができます。 各 ActivityLink には、リンクされているアクティビティに関する ID 情報を格納する <xref:System.Diagnostics.ActivityContext> が設定されます。 ActivityContext は、<xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> を使用してインプロセス アクティビティ オブジェクトから取得することも、<xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType> を使用してシリアル化された ID 情報から解析することもできます。

```csharp
void DoBatchWork(ActivityContext[] requestContexts)
{
    // Assume each context in requestContexts encodes the trace-id that was sent with a request
    using(Activity activity = s_source.StartActivity(name: "BigBatchOfWork",
                                                     kind: ActivityKind.Internal,
                                                     parentContext: null,
                                                     links: requestContexts.Select(ctx => new ActivityLink(ctx))
    {
        // do the batch of work here
    }
}
```

オンデマンドで追加できるイベントやタグとは異なり、リンクは StartActivity() 中に追加する必要があり、その後は変更できません。
