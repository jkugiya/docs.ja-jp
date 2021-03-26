---
title: 非同期の戻り値の型 (C#)
description: 各型およびその他のリソースのコード例と共に非同期メソッドが C# で持つことのできる戻り値の型について説明します。
ms.date: 08/19/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 53eb3bedebb99cd829101eee4c2e190c0fb952bf
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653453"
---
# <a name="async-return-types-c"></a>非同期の戻り値の型 (C#)

非同期メソッドには、次の戻り値の型があります。

- <xref:System.Threading.Tasks.Task>: 操作を実行し、値を返さない非同期メソッドの場合。
- <xref:System.Threading.Tasks.Task%601>: 値を返す非同期メソッドの場合。
- `void`: イベント ハンドラーの場合。
- C# 7.0 以降、アクセス可能な `GetAwaiter` を持つ任意の型です。 <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> メソッドによって返されるオブジェクトは、`GetAwaiter` インターフェイスを実装する必要があります。
- C# 8.0 以降、"*非同期ストリーム*" を返す非同期メソッドの場合は <xref:System.Collections.Generic.IAsyncEnumerable%601>。

非同期メソッドの詳細については、「[Async および Await を使用した非同期プログラミング (C#)](./index.md)」を参照してください。

他にも、Windows ワークロードに固有の型がいくつか存在します。

- <xref:System.Windows.Threading.DispatcherOperation>: Windows に限定された非同期操作。
- <xref:Windows.Foundation.IAsyncAction>: 値を返さない UWP の非同期アクション。
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>: 進行状況は報告するが値を返さない UWP の非同期アクション。
- <xref:Windows.Foundation.IAsyncOperation%601>: 値を返す UWP の非同期操作。
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>: 進行状況を報告し値を返す UWP の非同期操作。

## <a name="task-return-type"></a>Task の戻り値の型

`return` ステートメントを含まない非同期メソッド、またはオペランドを返さない `return` ステートメントを含む非同期メソッドは、通常は <xref:System.Threading.Tasks.Task> の戻り値の型を指定します。 こうしたメソッドは、同期的に実行するように作成されている場合に `void` を返します。 非同期メソッドに戻り値の型 <xref:System.Threading.Tasks.Task> を使用した場合、呼び出し元のメソッドは `await` 演算子を使って、呼び出された async のメソッドが終了するまで、呼び出し元の完了を中断します。

次の例では、`WaitAndApologizeAsync` メソッドに `return` ステートメントが含まれていないため、メソッドからは <xref:System.Threading.Tasks.Task> オブジェクトが返されます。 `Task` を返すことで、`WaitAndApologizeAsync` を待機できるようになります。 <xref:System.Threading.Tasks.Task> 型には戻り値がないため、`Result` プロパティを含みません。

:::code language="csharp" source="snippets/async-return-types/async-returns2.cs" id="TaskReturn":::

`WaitAndApologizeAsync` を待機するには、void を返す同期メソッドを呼び出す場合と同様に、await 式でなく、await ステートメントを使用します。 この場合、await 演算子の適用によって値は生成されません。 `await` の右オペランドが <xref:System.Threading.Tasks.Task%601> の場合、`await` 式によって、`T` の結果が生成されます。 `await` の右オペランドが、<xref:System.Threading.Tasks.Task> の場合、`await` とそのオペランドはステートメントです。

次のコードを見るとわかるように、`WaitAndApologizeAsync` の呼び出しを await 演算子の適用から分離することができます。 ただし `Task` は `Result` プロパティを持たないこと、また await 演算子が `Task` に適用されるときに値は生成されないことに注意します。

次のコードは、`WaitAndApologizeAsync` メソッドの呼び出しを、そのメソッドが返すタスクの待機から分離します。

:::code language="csharp" source="snippets/async-return-types/async-returns2a.cs" id="AwaitTask":::

## <a name="tasktresult-return-type"></a>Task\<TResult\> の戻り値の型

戻り値の型 <xref:System.Threading.Tasks.Task%601> は、オペランドが `TResult` である [return](../../../language-reference/keywords/return.md) ステートメントを含む非同期メソッドに使用されます。

次の例の `GetLeisureHoursAsync` メソッドには、整数を返す `return` ステートメントが含まれています。 そのため、メソッド宣言では、戻り値の型を `Task<int>` と指定する必要があります。 非同期メソッド <xref:System.Threading.Tasks.Task.FromResult%2A> は、<xref:System.DateTime.DayOfWeek> を返す操作に対するプレースホルダーです。

:::code language="csharp" source="snippets/async-return-types/async-returns1.cs" id="LeisureHours":::

`GetLeisureHoursAsync` が `ShowTodaysInfo` メソッドの await 式の中から呼び出されると、await 式は `GetLeisureHours` メソッドから返されるタスクに格納されている整数値 (`leisureHours` の値) を取得します。 await 式の詳細については、「[await](../../../language-reference/operators/await.md)」を参照してください。

次のコードが示すように、`GetLeisureHoursAsync` への呼び出しを `await` のアプリケーションから分離すると、`await` で `Task<T>` から結果を取得する方法をよりよく理解できます。 メソッドの宣言から予想されるように、直ちに待機しない `GetLeisureHoursAsync` メソッドの呼び出しは、`Task<int>` を返します。 タスクは、この例の `getLeisureHoursTask` 変数に割り当てられます。 `getLeisureHoursTask` は <xref:System.Threading.Tasks.Task%601> であるため、<xref:System.Threading.Tasks.Task%601.Result> 型の `TResult` プロパティが含まれています。 この場合、`TResult` は整数型を表します。 `await` が `getLeisureHoursTask` に適用されると、`getLeisureHoursTask` の <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティの内容が await 式の評価となります。 この値は `ret` 変数に割り当てられます。

> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティは Blocking プロパティです。 タスクが終了する前にアクセスしようとすると、現在アクティブなスレッドは、タスクが完了して値が使用可能になるまで、ブロックされます。 多くの場合、プロパティに直接アクセスする代わりに、`await` を使用して値にアクセスする必要があります。
>
> 前の例では、アプリケーションが終了する前に `Main` メソッドで `message` を出力できるように、<xref:System.Threading.Tasks.Task%601.Result%2A> プロパティの値を取得してメイン スレッドをブロックしました。

:::code language="csharp" source="snippets/async-return-types/async-returns1a.cs" id="StoreTask":::

## <a name="void-return-type"></a>Void の戻り値の型

`void` 戻り値の型は、`void` 戻り値の型が必要な非同期イベント ハンドラーで使用します。 値を返さないイベント ハンドラー以外のメソッドについては、<xref:System.Threading.Tasks.Task> を返す必要があります。これは、`void` を返す非同期メソッドを待機できないためです。 このようなメソッドの呼び出し元は、呼び出された非同期メソッドが完了するまで待機せずに、完了するまで続行する必要があります。 呼び出し元は、非同期メソッドによって生成される値や例外から独立している必要があります。

void を返す非同期メソッドの呼び出し元は、メソッドからスローされる例外をキャッチすることはできません。そのようなハンドルされない例外によって、アプリケーションが失敗する可能性が高くなります。 <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返すメソッドから例外がスローされた場合、例外は返されたタスクに格納されます。 タスクを待機しているときは、例外が再スローされます。 したがって、例外を生成する場合がある非同期メソッドは <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> の戻り値の型を持つこと、またメソッドの呼び出しが待機することを確認します。

非同期メソッドで例外をキャッチする方法の詳細については、「[try-catch](../../../language-reference/keywords/try-catch.md)」の記事の「[非同期メソッドの例外](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods)」セクションを参照してください。

次の例では、非同期イベント ハンドラーの動作を示します。 コード例では、非同期イベント ハンドラーが終了したとき、その非同期イベント ハンドラーからメイン スレッドに通知が送られる必要があります。 このため、メイン スレッドでは、非同期イベント ハンドラーの終了を待ってから、プログラムを終了することができます。

:::code language="csharp" source="snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>一般化された async の戻り値の型と ValueTask\<TResult\>

C# 7.0 以降、非同期メソッドでは、*awaiter 型* のインスタンスを返すアクセス可能な `GetAwaiter` メソッドがある任意の型を返すことができます。 さらに、`GetAwaiter` メソッドから返される型には <xref:System.Runtime.CompilerServices.AsyncMethodBuilderAttribute?displayProperty=nameWithType> 属性が必要です。 詳細については、[task に似た戻り値の型](../../../../../_csharplang/proposals/csharp-7.0/task-types.md)の機能仕様を参照してください。

この機能は、`await` のオペランドの要件を記述する[待機可能な式](../../../../../_csharplang/spec/expressions.md#awaitable-expressions)を補完するものです。 一般化された非同期の戻り値の型により、コンパイラではさまざまな型を返す `async` メソッドを生成できます。 一般化された非同期の戻り値の型により、.NET ライブラリのパフォーマンスの向上が可能になりました。 <xref:System.Threading.Tasks.Task> および <xref:System.Threading.Tasks.Task%601> は参照型であるため、特に厳密なループ処理で割り当てが発生すると、パフォーマンスが重要なパスのメモリ割り当てが、パフォーマンスに悪影響を及ぼすことがあります。 一般化された戻り値の型のサポートにより、参照型ではなく、軽量な値の型を返すことができ、追加のメモリ割り当てを回避することが可能です。

.NET には、一般化されたタスク戻り値の軽量な実装として、<xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 構造が用意されています。 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 型を使用するには、`System.Threading.Tasks.Extensions` NuGet パッケージをプロジェクトに追加する必要があります。 次の例では、<xref:System.Threading.Tasks.ValueTask%601> 構造を使用して、2 つのさいころを転がしたときの値を取得します。

:::code language="csharp" source="snippets/async-return-types/async-valuetask.cs":::

一般化された非同期の戻り値の型を記述することは高度なシナリオであり、きわめて特殊な環境での使用を対象としています。 代わりに、非同期コードのほとんどのシナリオに対応する `Task`、`Task<T>`、`ValueTask<T>` 型の使用を検討してください。

## <a name="async-streams-with-iasyncenumerablet"></a>IAsyncEnumerable\<T\> を使用する非同期ストリーム

C# 8.0 以降は、非同期メソッドから <xref:System.Collections.Generic.IAsyncEnumerable%601> で表される *非同期ストリーム* が返される場合があります。 非同期ストリームを使用すると、非同期呼び出しが繰り返される要素がチャンクで生成されるときに、ストリームから読み取られた項目を列挙できます。 次の例は、非同期ストリームを生成する非同期メソッドを示しています。

:::code language="csharp" source="snippets/async-return-types/AsyncStreams.cs" id="GenerateAsyncStream":::

前の例では、文字列から非同期に行を読み取ります。 各行が読み取られると、コードによって文字列内の各単語が列挙されます。 呼び出し元では、`await foreach` ステートメントを使用して各単語を列挙します。 このメソッドを使用すると、ソース文字列から次の行を非同期的に読み取る必要があるときに待機できます。

## <a name="see-also"></a>関連項目

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [完了時の非同期タスクの処理](start-multiple-async-tasks-and-process-them-as-they-complete.md)
- [Async および Await を使用した非同期プログラミング (C#)](index.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
