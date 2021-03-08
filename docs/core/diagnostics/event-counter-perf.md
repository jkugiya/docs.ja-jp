---
title: .NET Core で EventCounters を使用してパフォーマンスを測定する
description: このチュートリアルでは、EventCounters を使用してパフォーマンスを測定する方法について説明します。
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: bde54ce1996b2f4e2a703c23384eadece06e66cb
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105311"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a>チュートリアル: .NET Core で EventCounters を使用してパフォーマンスを測定する

**この記事の対象: ✔️** .NET Core 3.0 SDK 以降のバージョン

このチュートリアルでは、<xref:System.Diagnostics.Tracing.EventCounter> を使用して、イベントの頻度が高い状態でパフォーマンスを測定する方法について説明します。 さまざまな公式 .NET Core パッケージまたはサードパーティ プロバイダーによって発行された[使用可能なカウンター](available-counters.md)を使用することも、監視用に独自のメトリックを作成することもできます。

このチュートリアルでは、次のことについて説明します。

> [!div class="checklist"]
>
> - <xref:System.Diagnostics.Tracing.EventSource> の実装。
> - [dotnet-counters](dotnet-counters.md) を使用したカウンターの監視。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは次のものを使用します。

- [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン。
- イベント カウンターを監視するための [dotnet-counters](dotnet-counters.md)。
- 診断する[サンプル デバッグ ターゲット](/samples/dotnet/samples/diagnostic-scenarios) アプリ。

## <a name="get-the-source"></a>ソースを入手する

監視のための基礎としてサンプル アプリケーションを使用します。 [サンプルの ASP.NET Core リポジトリ](/samples/dotnet/samples/diagnostic-scenarios)をサンプル ブラウザーから利用できます。 zip ファイルをダウンロードし、ダウンロード後に展開して、普段使用している IDE で開きます。 アプリケーションをビルドして実行し、正常に動作することを確実にしてから、アプリケーションを停止します。

## <a name="implement-an-eventsource"></a>EventSource を実装する

数ミリ秒ごとに発生するイベントの場合は、イベントごとのオーバーヘッドを低くする必要があります (ミリ秒未満)。 そうしないと、パフォーマンスへの影響が大きくなります。 イベントをログに記録すると、ディスクに何かが書き込まれることになります。 ディスクの速度が十分でない場合は、イベントが失われます。 イベント自体をログに記録する以外の解決策が必要です。

多数のイベントを処理する場合、イベントごとの測定値を知ることも役に立ちません。 ほとんどの場合、必要なのはそれから得られる統計情報だけです。 そのため、プロセス自体に含まれる統計情報を取得し、ときどきイベントを書き込んで統計情報を報告することができます。それが <xref:System.Diagnostics.Tracing.EventCounter> で行われることです。

<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> を実装する方法の例を次に示します。 *MinimalEventCounterSource.cs* という名前の新しいファイルを作成し、そのソースとして次のコード スニペットを使用します。

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> の行は <xref:System.Diagnostics.Tracing.EventSource> パーツであり、<xref:System.Diagnostics.Tracing.EventCounter> のパーツではありません。イベント カウンターと共にメッセージをログに記録できることを示すために記述されています。

## <a name="add-an-action-filter"></a>アクション フィルターを追加する

サンプルのソース コードは、ASP.NET Core プロジェクトです。 要求の合計時間をログに記録する[アクション フィルター](/aspnet/core/mvc/controllers/filters#action-filters)をグローバルに追加できます。 *LogRequestTimeFilterAttribute.cs* という名前の新しいファイルを作成し、次のコードを使用します。

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

アクション フィルターによって要求の開始時に <xref:System.Diagnostics.Stopwatch> を開始し、完了後に停止して、経過時間をキャプチャします。 合計時間 (ミリ秒) は `MinimalEventCounterSource` シングルトン インスタンスに記録されます。 このフィルターを適用するには、フィルター コレクションに追加する必要があります。 *Startup.cs* ファイルで、このフィルターを含めるように `ConfigureServices` メソッドを更新します。

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a>イベント カウンターを監視する

<xref:System.Diagnostics.Tracing.EventSource> の実装とカスタム アクション フィルターを使用して、アプリケーションをビルドして起動します。
<xref:System.Diagnostics.Tracing.EventCounter> にメトリックを記録しましたが、それから得られる統計情報にアクセスしない限り、それは役に立ちません。 統計を取得するには、イベントをキャプチャするリスナーだけでなく、必要な頻度で起動するタイマーを作成して、<xref:System.Diagnostics.Tracing.EventCounter> を有効にする必要があります。 これを行うために、[dotnet-counters](dotnet-counters.md) を使用できます。

[dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) コマンドを使用して、監視できる .NET プロセスの一覧を表示します。

```console
dotnet-counters ps
```

`dotnet-counters ps` コマンドの出力にあるプロセス識別子を使用し、次の `dotnet-counters monitor` コマンドを使ってイベント カウンターの監視を開始できます。

```console
dotnet-counters monitor --process-id 2196 --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

`dotnet-counters monitor` コマンドの実行中に、`https://localhost:5001/api/values` エンドポイントへの継続的な要求の発行を開始するために、ブラウザーで <kbd>F5</kbd> キーを押します。 数秒後に <kbd>q</kbd> キーを押して終了します。

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

`dotnet-counters monitor` コマンドは、アクティブな監視に適しています。 ただし、これらの診断メトリックを収集して、後処理や分析を行うこともできます。 そのためには、`dotnet-counters collect` コマンドを使用します。 `collect` スイッチ コマンドは、`monitor` コマンドに似ていますが、いくつかの追加パラメーターを受け取ります。 目的の出力ファイル名と形式を指定できます。 *diagnostics.json* という名前の JSON ファイルの場合、次のコマンドを使用します。

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

コマンドの実行中に再度ブラウザーで <kbd>F5</kbd> キーを押して、`https://localhost:5001/api/values` エンドポイントへの継続的な要求の発行を開始します。 数秒後に <kbd>q</kbd> キーを押します。 *diagnostics.json* ファイルが書き込まれます。 ただし、書き込まれた JSON ファイルはインデントされません。ここでは読みやすくするためにインデントしています。

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [EventCounters](event-counters.md)
