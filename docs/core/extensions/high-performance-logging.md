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
# <a name="high-performance-logging-in-net"></a><span data-ttu-id="c9c5d-103">.NET での高パフォーマンスのログ</span><span class="sxs-lookup"><span data-stu-id="c9c5d-103">High-performance logging in .NET</span></span>

<span data-ttu-id="c9c5d-104"><xref:Microsoft.Extensions.Logging.LoggerMessage> クラスには、<xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> や <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> のような[ロガー拡張メソッド](xref:Microsoft.Extensions.Logging.LoggerExtensions)と比較して、必要なオブジェクト割り当ての数が少なくコンピューティング オーバーヘッドが小さいキャッシュ可能なデリゲートを作成する機能があります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-104">The <xref:Microsoft.Extensions.Logging.LoggerMessage> class exposes functionality to create cacheable delegates that require fewer object allocations and reduced computational overhead compared to [logger extension methods](xref:Microsoft.Extensions.Logging.LoggerExtensions), such as <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> and <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>.</span></span> <span data-ttu-id="c9c5d-105">高パフォーマンスのログ記録シナリオの場合は、<xref:Microsoft.Extensions.Logging.LoggerMessage> パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-105">For high-performance logging scenarios, use the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

<span data-ttu-id="c9c5d-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> には、ロガー拡張メソッドに比べて次のようなパフォーマンス上の利点があります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> provides the following performance advantages over Logger extension methods:</span></span>

- <span data-ttu-id="c9c5d-107">ロガー拡張メソッドでは、`int` などの値の型を `object` に "ボックス化" (変換) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-107">Logger extension methods require "boxing" (converting) value types, such as `int`, into `object`.</span></span> <span data-ttu-id="c9c5d-108"><xref:Microsoft.Extensions.Logging.LoggerMessage> パターンでは、静的な <xref:System.Action> フィールドと、厳密に型指定されたパラメーターを持つ拡張メソッドを使用してボックス化を回避します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-108">The <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern avoids boxing by using static <xref:System.Action> fields and extension methods with strongly-typed parameters.</span></span>
- <span data-ttu-id="c9c5d-109">ロガー拡張メソッドでは、ログ メッセージが書き込まれるたびにメッセージ テンプレート (名前付きの書式文字列) を解析する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-109">Logger extension methods must parse the message template (named format string) every time a log message is written.</span></span> <span data-ttu-id="c9c5d-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> では、メッセージを定義するときに、一度テンプレートを解析する必要があるだけです。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> only requires parsing a template once when the message is defined.</span></span>

<span data-ttu-id="c9c5d-111">このサンプル アプリは、優先キュー処理 Worker サービスを使用した <xref:Microsoft.Extensions.Logging.LoggerMessage> 機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-111">The sample app demonstrates <xref:Microsoft.Extensions.Logging.LoggerMessage> features with a priority queue processing worker service.</span></span> <span data-ttu-id="c9c5d-112">このアプリを使用すると、作業項目が優先順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-112">The app processes work items in priority order.</span></span> <span data-ttu-id="c9c5d-113">これらの操作が実行されると、<xref:Microsoft.Extensions.Logging.LoggerMessage> パターンによってログ メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-113">As these operations occur, log messages are generated using the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

## <a name="define-a-logger-message"></a><span data-ttu-id="c9c5d-114">ロガー メッセージを定義する</span><span class="sxs-lookup"><span data-stu-id="c9c5d-114">Define a logger message</span></span>

<span data-ttu-id="c9c5d-115">[Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) を使用して、メッセージをログ記録するための <xref:System.Action> デリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-115">Use [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) to create an <xref:System.Action> delegate for logging a message.</span></span> <span data-ttu-id="c9c5d-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> オーバー ロードでは、名前付きの書式文字列 (テンプレート) に対して最大 6 個の型パラメーターを渡すことを許可します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> overloads permit passing up to six type parameters to a named format string (template).</span></span>

<span data-ttu-id="c9c5d-117"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> メソッドに指定された文字列はテンプレートであり、補間文字列ではありません。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-117">The string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="c9c5d-118">プレースホルダーは、型が指定された順に入力されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-118">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="c9c5d-119">テンプレート内のプレースホルダー名はわかりやすく、テンプレート間で一貫している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-119">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="c9c5d-120">それらは構造化されたログ データ内でプロパティ名としての役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-120">They serve as property names within structured log data.</span></span> <span data-ttu-id="c9c5d-121">プレースホルダー名には [Pascal 形式](../../standard/design-guidelines/capitalization-conventions.md)を推奨します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-121">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="c9c5d-122">たとえば、`{Item}`、`{DateTime}` のようになります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-122">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="c9c5d-123">各ログ メッセージは、[LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) によって作成された静的フィールドに保持される <xref:System.Action> です。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-123">Each log message is an <xref:System.Action> held in a static field created by [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span></span> <span data-ttu-id="c9c5d-124">たとえば、サンプル アプリにより、作業項目の処理に関するログ メッセージを記述するフィールドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-124">For example, the sample app creates a field to describe a log message for the processing of work items:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

<span data-ttu-id="c9c5d-125"><xref:System.Action> の場合は、次を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-125">For the <xref:System.Action>, specify:</span></span>

- <span data-ttu-id="c9c5d-126">ログ レベル。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-126">The log level.</span></span>
- <span data-ttu-id="c9c5d-127">静的な拡張メソッドの名前を持つ一意のイベント識別子です (<xref:Microsoft.Extensions.Logging.EventId>)。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-127">A unique event identifier (<xref:Microsoft.Extensions.Logging.EventId>) with the name of the static extension method.</span></span>
- <span data-ttu-id="c9c5d-128">メッセージ テンプレート (名前付き書式文字列)。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-128">The message template (named format string).</span></span>

<span data-ttu-id="c9c5d-129">Worker サービス アプリを処理するために作業項目がデキューされるので、次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-129">As work items are dequeued for processing the worker service app sets the:</span></span>

- <span data-ttu-id="c9c5d-130">ログ レベルを <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-130">Log level to <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="c9c5d-131">イベント ID を `FailedToProcessWorkItem` メソッドの名前を含む `13` に設定します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-131">Event id to `13` with the name of the `FailedToProcessWorkItem` method.</span></span>
- <span data-ttu-id="c9c5d-132">メッセージ テンプレート (名前付き書式文字列) を文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-132">Message template (named format string) to a string.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

<span data-ttu-id="c9c5d-133">構造化されたログ ストアは、イベント ID によって指定されているとき、ログ記録を強化するために、イベント名を使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-133">Structured logging stores may use the event name when it's supplied with the event id to enrich logging.</span></span> <span data-ttu-id="c9c5d-134">たとえば、[Serilog](https://github.com/serilog/serilog-extensions-logging) はイベント名を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-134">For example, [Serilog](https://github.com/serilog/serilog-extensions-logging) uses the event name.</span></span>

<span data-ttu-id="c9c5d-135"><xref:System.Action> は厳密に型指定された拡張メソッドによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-135">The <xref:System.Action> is invoked through a strongly-typed extension method.</span></span> <span data-ttu-id="c9c5d-136">`PriorityItemProcessed` メソッドを使用すると、作業項目が処理されるたびにメッセージがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-136">The `PriorityItemProcessed` method logs a message every time a work item is being processed.</span></span> <span data-ttu-id="c9c5d-137">一方、`FailedToProcessWorkItem` は、例外が発生したとき (場合) に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-137">Whereas, `FailedToProcessWorkItem` is called when (and if) an exception occurs:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

<span data-ttu-id="c9c5d-138">アプリのコンソール出力を検査する:</span><span class="sxs-lookup"><span data-stu-id="c9c5d-138">Inspect the app's console output:</span></span>

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

<span data-ttu-id="c9c5d-139">ログ メッセージにパラメーターを渡すには、静的フィールドを作成するときに最大 6 個の型を定義します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-139">To pass parameters to a log message, define up to six types when creating the static field.</span></span> <span data-ttu-id="c9c5d-140">このサンプル アプリには、<xref:System.Action> フィールドに `WorkItem` 型が定義されており、項目を処理するときに作業項目の詳細がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-140">The sample app logs the work item details when processing items by defining a `WorkItem` type for the <xref:System.Action> field:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

<span data-ttu-id="c9c5d-141">デリゲートのログ メッセージ テンプレートは、そのプレースホルダー値を指定された型で受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-141">The delegate's log message template receives its placeholder values from the types provided.</span></span> <span data-ttu-id="c9c5d-142">このサンプル アプリには、item パラメーターが `WorkItem` である作業項目を追加するためのデリゲートが定義されています。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-142">The sample app defines a delegate for adding a work item where the item parameter is a `WorkItem`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

<span data-ttu-id="c9c5d-143">作業項目が処理されていることをログに記録するための静的拡張メソッド `PriorityItemProcessed` を使用して、作業項目の引数値を受け取り、それを <xref:System.Action> デリゲートに渡します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-143">The static extension method for logging that a work item is being processed, `PriorityItemProcessed`, receives the work item argument value and passes it to the <xref:System.Action> delegate:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

<span data-ttu-id="c9c5d-144">Worker サービスの `ExecuteAsync` メソッドでは、メッセージをログに記録するために `PriorityItemProcessed` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-144">In the worker service's `ExecuteAsync` method, `PriorityItemProcessed` is called to log the message:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

<span data-ttu-id="c9c5d-145">アプリのコンソール出力を検査する:</span><span class="sxs-lookup"><span data-stu-id="c9c5d-145">Inspect the app's console output:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a><span data-ttu-id="c9c5d-146">ロガー メッセージ スコープを定義する</span><span class="sxs-lookup"><span data-stu-id="c9c5d-146">Define logger message scope</span></span>

<span data-ttu-id="c9c5d-147">[DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) メソッドにより、[ログ スコープ](logging.md#log-scopes)を定義するための <xref:System.Func%601> デリゲートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-147">The [DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) method creates a <xref:System.Func%601> delegate for defining a [log scope](logging.md#log-scopes).</span></span> <span data-ttu-id="c9c5d-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> オーバー ロードでは、名前付きの書式文字列 (テンプレート) に対して最大 3 個の型パラメーターを渡すことを許可します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> overloads permit passing up to three type parameters to a named format string (template).</span></span>

<span data-ttu-id="c9c5d-149"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> メソッドの場合と同様に、<xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> メソッドに指定された文字列はテンプレートであり、補間文字列ではありません。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-149">As is the case with the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method, the string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="c9c5d-150">プレースホルダーは、型が指定された順に入力されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-150">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="c9c5d-151">テンプレート内のプレースホルダー名はわかりやすく、テンプレート間で一貫している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-151">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="c9c5d-152">それらは構造化されたログ データ内でプロパティ名としての役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-152">They serve as property names within structured log data.</span></span> <span data-ttu-id="c9c5d-153">プレースホルダー名には [Pascal 形式](../../standard/design-guidelines/capitalization-conventions.md)を推奨します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-153">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="c9c5d-154">たとえば、`{Item}`、`{DateTime}` のようになります。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-154">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="c9c5d-155"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> メソッドを使用して、一連のログ メッセージに適用する[ログ スコープ](logging.md#log-scopes)を定義します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-155">Define a [log scope](logging.md#log-scopes) to apply to a series of log messages using the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method.</span></span> <span data-ttu-id="c9c5d-156">*appsettings.json* のコンソール ロガーのセクションで、`IncludeScopes` を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-156">Enable `IncludeScopes` in the console logger section of *appsettings.json*:</span></span>

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

<span data-ttu-id="c9c5d-157">ログ スコープを作成するには、スコープに対して <xref:System.Func%601> デリゲートを保持するフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-157">To create a log scope, add a field to hold a <xref:System.Func%601> delegate for the scope.</span></span> <span data-ttu-id="c9c5d-158">サンプル アプリでは、`_processingWorkScope` と呼ばれるフィールドを作成します (*Internal/LoggerExtensions.cs*)。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-158">The sample app creates a field called `_processingWorkScope` (*Internal/LoggerExtensions.cs*):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="c9c5d-159"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> を使用してデリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-159">Use <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> to create the delegate.</span></span> <span data-ttu-id="c9c5d-160">デリゲートを呼び出すとき、テンプレート引数として使用するように最大 3 つの型を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-160">Up to three types can be specified for use as template arguments when the delegate is invoked.</span></span> <span data-ttu-id="c9c5d-161">このサンプル アプリには、処理が開始された日時を含むメッセージ テンプレートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-161">The sample app uses a message template that includes the date time in which processing started:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="c9c5d-162">ログ メッセージ用の静的な拡張メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-162">Provide a static extension method for the log message.</span></span> <span data-ttu-id="c9c5d-163">メッセージ テンプレートに表示される名前付きプロパティの任意の型パラメーターを含めます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-163">Include any type parameters for named properties that appear in the message template.</span></span> <span data-ttu-id="c9c5d-164">サンプル アプリにより、ログに記録するカスタムのタイムスタンプの `DateTime` が取り込まれ、`_processingWorkScope` が返されます。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-164">The sample app takes in a `DateTime` for a custom time stamp to log and returns `_processingWorkScope`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="c9c5d-165">スコープは、[using](../../csharp/language-reference/keywords/using-statement.md) ブロックでログ拡張呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-165">The scope wraps the logging extension calls in a [using](../../csharp/language-reference/keywords/using-statement.md) block:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

<span data-ttu-id="c9c5d-166">アプリのコンソール出力のログ メッセージを検査します。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-166">Inspect the log messages in the app's console output.</span></span> <span data-ttu-id="c9c5d-167">次の結果は、ログ スコープ メッセージを含め、ログ メッセージの優先順位を示しています。</span><span class="sxs-lookup"><span data-stu-id="c9c5d-167">The following result shows priority ordering of log messages with the log scope message included:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c9c5d-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9c5d-168">See also</span></span>

- [<span data-ttu-id="c9c5d-169">.NET でのログの記録</span><span class="sxs-lookup"><span data-stu-id="c9c5d-169">Logging in .NET</span></span>](logging.md)
