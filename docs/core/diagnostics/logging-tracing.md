---
title: ログとトレース - .NET Core
description: .NET Core のログとトレースの概要について説明します。
ms.date: 10/12/2020
ms.openlocfilehash: dfecdad4518c79b605eb4fbe991af07fcba7db1c
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111089"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core のログとトレース

ログとトレースは、実際には同じ手法の 2 つの名前です。 コンピューターの初期の頃から、単純な手法が使用されています。 アプリケーションをインストルメント化して、後で使用するために出力を書き込みます。

## <a name="reasons-to-use-logging-and-tracing"></a>ログとトレースを使用する理由

この単純な手法は、驚くほど強力です。 これは、次のようなデバッガーでは対応できない場合に使用できます。

- 長期間にわたって発生する問題は、従来のデバッガーでデバッグするのが困難な場合があります。 ログを使用すると、長期間にわたる詳細な事後分析を行うことができます。 これに対し、デバッガーはリアルタイム分析に制約されます。
- 多くの場合、マルチスレッド アプリケーションと分散アプリケーションはデバッグが困難です。  デバッガーをアタッチすると、動作が変更される傾向があります。 必要に応じて詳細ログを分析することで、複雑なシステムを理解できます。
- 分散アプリケーションの問題は、多くのコンポーネント間の複雑な相互作用によって生じる可能性があり、デバッガーをシステムのすべての部分に接続するのは合理的でない場合があります。
- 多くのサービスは停止することができません。 デバッガーをアタッチすると、多くの場合、タイムアウト エラーが発生します。
- 問題は常に予測できるとは限りません。 ログとトレースは、問題が発生した場合に備えてプログラムで常に記録できるように、オーバーヘッドが低くなるように設計されています。

## <a name="net-core-apis"></a>.NET Core API

### <a name="print-style-apis"></a>出力スタイルの API

<xref:System.Console?displayProperty=nameWithType>、<xref:System.Diagnostics.Trace?displayProperty=nameWithType>、および <xref:System.Diagnostics.Debug?displayProperty=nameWithType> クラスはそれぞれ、ログ記録に便利な出力スタイルの API を備えています。

どの出力スタイル API を使用するかは、ユーザーが決定します。 主な違いを次に示します。

- <xref:System.Console?displayProperty=nameWithType>
  - 常に有効であり、常にコンソールに書き込みます。
  - 顧客がリリースで参照する必要のある情報の場合に便利です。
  - 最も簡単な方法であるため、アドホックな一時デバッグによく使用されます。 このデバッグ コードは、多くの場合、ソース管理にチェックインされません。
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - ソースに `#define TRACE` を追加するか、コンパイル時、オプション `/d:TRACE` を指定することで `TRACE` が定義されたときにのみ有効です。
  - アタッチされている <xref:System.Diagnostics.Trace.Listeners> (既定では <xref:System.Diagnostics.DefaultTraceListener>) に書き込みます。
  - ほとんどのビルドで有効になるログを作成するときに、この API を使用します。
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - ソースに `#define DEBUG` を追加するか、コンパイル時、オプション `/d:DEBUG` を指定することで `DEBUG` が定義されたときにのみ有効です。
  - アタッチされたデバッガーに書き込みます。
  - `*nix` では、`COMPlus_DebugWriteToStdErr` が設定されている場合は stderr に書き込みます。
  - デバッグ ビルドでのみ有効になるログを作成するときに、この API を使用します。

### <a name="logging-events"></a>イベントのログ記録

次の API は、よりイベント指向です。 単純な文字列をログに記録するのではなく、イベント オブジェクトをログに記録します。

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource は、プライマリ ルートの .NET Core トレース API です。
  - すべての .NET Standard バージョンで使用できます。
  - シリアル化可能なオブジェクトのみをトレースできます。
  - EventSource を使用するように構成されている [EventListener](xref:System.Diagnostics.Tracing.EventListener) インスタンスを介してインプロセスで使用できます。
  - 次を介してアウトプロセスで使用できます。
    - すべてのプラットフォームでの [.NET Core の EventPipe](./eventpipe.md)
    - [Windows イベント トレーシング (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Linux 用 LTTng トレース フレームワーク](https://lttng.org/)
      - チュートリアル: [PerfCollect を使用して LTTng トレースを収集する](trace-perfcollect-lttng.md)。

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - .NET Core に含まれており、.NET Framework の [NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource)として提供されています。
  - シリアル化できないオブジェクトのインプロセス トレースを可能にします。
  - ログ対象オブジェクトの選択したフィールドを <xref:System.Diagnostics.Tracing.EventSource> に書き込むことができるようにするブリッジが含まれています。

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Windows のみ。
  - Windows イベント ログにメッセージを書き込みます。
  - システム管理者は、致命的なアプリケーション エラー メッセージが Windows イベントログに記録されることを想定しています。

## <a name="distributed-tracing"></a>分散トレース

[分散トレース](./distributed-tracing.md)は、特に複数のコンピューターやプロセスに分散される可能性があるアプリケーション内のエラーとパフォーマンスの問題を、エンジニアがローカライズするのに役立つ診断手法です。 この手法は、アプリケーションを介して要求を追跡し、さまざまなアプリケーション コンポーネントによって実行される作業を相互に関連付けて、アプリケーションが同時要求に対して実行する可能性がある他の作業から分離します。

## <a name="ilogger-and-logging-frameworks"></a>ILogger とログ記録フレームワーク

低レベルの API は、ログ記録のニーズに適しているとは限りません。 ログ記録フレームワークを検討することもできます。

<xref:Microsoft.Extensions.Logging.ILogger> インターフェイスは、依存関係の挿入を通じてロガーを挿入できる共通のログ インターフェイスを作成するために使用されています。

たとえば、アプリケーションに最適な選択を可能にするために、.NET では、組み込みおよびサード パーティのフレームワークのサポートが提供されています。

- [.NET の組み込みのログ プロバイダー](../extensions/logging-providers.md#built-in-logging-providers)
- [.NET のサード パーティ製のログ プロバイダー](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a>ログ関連の参照

- [方法 : トレースとデバッグを指定して条件付きコンパイルを実行する](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [方法 : アプリケーション コードにトレース ステートメントを追加する](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- 「[.NET のログ記録](../extensions/logging.md)」では、サポートしているログ記録技法の概要を示しています。

- [C# の文字列補間](../../csharp/language-reference/tokens/interpolated.md)を使用すると、ログ記録コードを簡単に記述できます。

- [ランタイム プロバイダー イベント一覧](../../fundamentals/diagnostics/runtime-events.md)

- [.NET の既知のイベント プロバイダー](well-known-event-providers.md)

- <xref:System.Exception.Message?displayProperty=nameWithType> プロパティは、例外をログに記録する場合に便利です。

- <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> クラスは、ログにスタック情報を提供するのに役立ちます。

## <a name="performance-considerations"></a>パフォーマンスに関する考慮事項

文字列を書式設定すると、CPU 処理時間が著しく長くなる可能性があります。

パフォーマンス クリティカルなアプリケーションでは、次のことをお勧めします。

- リッスンしているものがない場合は、大量のログを記録しないようにします。 最初にログ記録が有効かどうかを確認することで、負荷の高いログ メッセージを作成しないようにします。
- 役に立つものだけをログに記録します。
- 凝ったフォーマット設定は分析ステージで行います。
