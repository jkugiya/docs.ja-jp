---
title: .NET での高パフォーマンスのログ
author: IEvangelist
description: 高パフォーマンスのログ記録シナリオにおいて、必要とするオブジェクト割り当ての数が少ない、キャッシュ可能なデリゲートを LoggerMessage を使用して作成する方法について説明します。
ms.author: dapine
ms.date: 01/04/2021
ms.openlocfilehash: 0031ff7a9f70cb0cf724fdf6dfa4fbe0a44af7c1
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "102402136"
---
# <a name="high-performance-logging-in-net"></a>.NET での高パフォーマンスのログ

<xref:Microsoft.Extensions.Logging.LoggerMessage> クラスには、<xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> や <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> のような[ロガー拡張メソッド](xref:Microsoft.Extensions.Logging.LoggerExtensions)と比較して、必要なオブジェクト割り当ての数が少なくコンピューティング オーバーヘッドが小さいキャッシュ可能なデリゲートを作成する機能があります。 高パフォーマンスのログ記録シナリオの場合は、<xref:Microsoft.Extensions.Logging.LoggerMessage> パターンを使用します。

<xref:Microsoft.Extensions.Logging.LoggerMessage> には、ロガー拡張メソッドに比べて次のようなパフォーマンス上の利点があります。

- ロガー拡張メソッドでは、`int` などの値の型を `object` に "ボックス化" (変換) する必要があります。 <xref:Microsoft.Extensions.Logging.LoggerMessage> パターンでは、静的な <xref:System.Action> フィールドと、厳密に型指定されたパラメーターを持つ拡張メソッドを使用してボックス化を回避します。
- ロガー拡張メソッドでは、ログ メッセージが書き込まれるたびにメッセージ テンプレート (名前付きの書式文字列) を解析する必要があります。 <xref:Microsoft.Extensions.Logging.LoggerMessage> では、メッセージを定義するときに、一度テンプレートを解析する必要があるだけです。

このサンプル アプリは、優先キュー処理 Worker サービスを使用した <xref:Microsoft.Extensions.Logging.LoggerMessage> 機能を示しています。 このアプリを使用すると、作業項目が優先順に処理されます。 これらの操作が実行されると、<xref:Microsoft.Extensions.Logging.LoggerMessage> パターンによってログ メッセージが生成されます。

## <a name="define-a-logger-message"></a>ロガー メッセージを定義する

[Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) を使用して、メッセージをログ記録するための <xref:System.Action> デリゲートを作成します。 <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> オーバー ロードでは、名前付きの書式文字列 (テンプレート) に対して最大 6 個の型パラメーターを渡すことを許可します。

<xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> メソッドに指定された文字列はテンプレートであり、補間文字列ではありません。 プレースホルダーは、型が指定された順に入力されます。 テンプレート内のプレースホルダー名はわかりやすく、テンプレート間で一貫している必要があります。 それらは構造化されたログ データ内でプロパティ名としての役割を果たします。 プレースホルダー名には [Pascal 形式](../../standard/design-guidelines/capitalization-conventions.md)を推奨します。 たとえば、`{Item}`、`{DateTime}` のようになります。

各ログ メッセージは、[LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) によって作成された静的フィールドに保持される <xref:System.Action> です。 たとえば、サンプル アプリにより、作業項目の処理に関するログ メッセージを記述するフィールドが作成されます。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

<xref:System.Action> の場合は、次を指定します。

- ログ レベル。
- 静的な拡張メソッドの名前を持つ一意のイベント識別子です (<xref:Microsoft.Extensions.Logging.EventId>)。
- メッセージ テンプレート (名前付き書式文字列)。

Worker サービス アプリを処理するために作業項目がデキューされるので、次のように設定します。

- ログ レベルを <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType> に設定します。
- イベント ID を `FailedToProcessWorkItem` メソッドの名前を含む `13` に設定します。
- メッセージ テンプレート (名前付き書式文字列) を文字列に設定します。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

構造化されたログ ストアは、イベント ID によって指定されているとき、ログ記録を強化するために、イベント名を使用する場合があります。 たとえば、[Serilog](https://github.com/serilog/serilog-extensions-logging) はイベント名を使用します。

<xref:System.Action> は厳密に型指定された拡張メソッドによって呼び出されます。 `PriorityItemProcessed` メソッドを使用すると、作業項目が処理されるたびにメッセージがログに記録されます。 一方、`FailedToProcessWorkItem` は、例外が発生したとき (場合) に呼び出されます。

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

アプリのコンソール出力を検査する:

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

ログ メッセージにパラメーターを渡すには、静的フィールドを作成するときに最大 6 個の型を定義します。 このサンプル アプリには、<xref:System.Action> フィールドに `WorkItem` 型が定義されており、項目を処理するときに作業項目の詳細がログに記録されます。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

デリゲートのログ メッセージ テンプレートは、そのプレースホルダー値を指定された型で受け取ります。 このサンプル アプリには、item パラメーターが `WorkItem` である作業項目を追加するためのデリゲートが定義されています。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

作業項目が処理されていることをログに記録するための静的拡張メソッド `PriorityItemProcessed` を使用して、作業項目の引数値を受け取り、それを <xref:System.Action> デリゲートに渡します。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

Worker サービスの `ExecuteAsync` メソッドでは、メッセージをログに記録するために `PriorityItemProcessed` が呼び出されます。

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

アプリのコンソール出力を検査する:

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a>ロガー メッセージ スコープを定義する

[DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) メソッドにより、[ログ スコープ](logging.md#log-scopes)を定義するための <xref:System.Func%601> デリゲートが作成されます。 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> オーバー ロードでは、名前付きの書式文字列 (テンプレート) に対して最大 3 個の型パラメーターを渡すことを許可します。

<xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> メソッドの場合と同様に、<xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> メソッドに指定された文字列はテンプレートであり、補間文字列ではありません。 プレースホルダーは、型が指定された順に入力されます。 テンプレート内のプレースホルダー名はわかりやすく、テンプレート間で一貫している必要があります。 それらは構造化されたログ データ内でプロパティ名としての役割を果たします。 プレースホルダー名には [Pascal 形式](../../standard/design-guidelines/capitalization-conventions.md)を推奨します。 たとえば、`{Item}`、`{DateTime}` のようになります。

<xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> メソッドを使用して、一連のログ メッセージに適用する[ログ スコープ](logging.md#log-scopes)を定義します。 *appsettings.json* のコンソール ロガーのセクションで、`IncludeScopes` を有効にします。

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

ログ スコープを作成するには、スコープに対して <xref:System.Func%601> デリゲートを保持するフィールドを追加します。 サンプル アプリでは、`_processingWorkScope` と呼ばれるフィールドを作成します (*Internal/LoggerExtensions.cs*)。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> を使用してデリゲートを作成します。 デリゲートを呼び出すとき、テンプレート引数として使用するように最大 3 つの型を指定することができます。 このサンプル アプリには、処理が開始された日時を含むメッセージ テンプレートが使用されます。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

ログ メッセージ用の静的な拡張メソッドを指定します。 メッセージ テンプレートに表示される名前付きプロパティの任意の型パラメーターを含めます。 サンプル アプリにより、ログに記録するカスタムのタイムスタンプの `DateTime` が取り込まれ、`_processingWorkScope` が返されます。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

スコープは、[using](../../csharp/language-reference/keywords/using-statement.md) ブロックでログ拡張呼び出しをラップします。

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

アプリのコンソール出力のログ メッセージを検査します。 次の結果は、ログ スコープ メッセージを含め、ログ メッセージの優先順位を示しています。

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a>関連項目

- [.NET でのログの記録](logging.md)
