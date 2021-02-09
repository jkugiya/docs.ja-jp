---
description: '詳細情報: Await 演算子 (Visual Basic)'
title: Await 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 04e32f31de970b389ae38fc3a4cdc6ab3f873f3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774136"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="39310-103">Await 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39310-103">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="39310-104">`Await` 演算子は、非同期のメソッドまたはラムダ式のオペランドに適用されて、待機中のタスクが完了するまでメソッドの実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="39310-104">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="39310-105">このタスクは、進行中の作業を表します。</span><span class="sxs-lookup"><span data-stu-id="39310-105">The task represents ongoing work.</span></span>

<span data-ttu-id="39310-106">`Await` が使用されるメソッドには [Async](../modifiers/async.md) 修飾子が必要です。</span><span class="sxs-lookup"><span data-stu-id="39310-106">The method in which `Await` is used must have an [Async](../modifiers/async.md) modifier.</span></span> <span data-ttu-id="39310-107">このようなメソッド (`Async` 修飾子を使用して定義され、通常 1 つ以上の `Await` 式を含むメソッド) を "*非同期メソッド*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="39310-107">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="39310-108">`Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="39310-108">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="39310-109">非同期プログラミングの概要については、「[Async および Await を使用した非同期プログラミング](../../programming-guide/concepts/async/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39310-109">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="39310-110">`Await` 演算子を適用するタスクは、通常、[タスク ベースの非同期パターン](https://www.microsoft.com/download/details.aspx?id=19957) (<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601>) を実装するメソッド呼び出しの戻り値です。</span><span class="sxs-lookup"><span data-stu-id="39310-110">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="39310-111">次のコードでは、<xref:System.Net.Http.HttpClient> メソッドの <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> が `getContentsTask` (`Task(Of Byte())`) を返します。</span><span class="sxs-lookup"><span data-stu-id="39310-111">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="39310-112">これにより、操作が完了したときに実際のバイト配列が生成されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="39310-112">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="39310-113">`Await` 演算子が `getContentsTask` に適用されているため、`SumPageSizesAsync` が完了するまで `getContentsTask` の実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="39310-113">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="39310-114">その間、コントロールは `SumPageSizesAsync` の呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="39310-114">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="39310-115">`getContentsTask` が終了すると、`Await` 式がバイト配列に評価されます。</span><span class="sxs-lookup"><span data-stu-id="39310-115">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> <span data-ttu-id="39310-116">完全な例については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39310-116">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="39310-117">Microsoft Web サイトの[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)からサンプルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="39310-117">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="39310-118">この例は AsyncWalkthrough_HttpClient プロジェクトにあります。</span><span class="sxs-lookup"><span data-stu-id="39310-118">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="39310-119">`Await` を返すメソッド呼び出しの結果に `Task(Of TResult)` が適用されている場合、`Await` 式の型は TResult になります。</span><span class="sxs-lookup"><span data-stu-id="39310-119">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="39310-120">`Await` を返すメソッド呼び出しの結果に `Task` が適用されている場合、`Await` 式は値を返しません。</span><span class="sxs-lookup"><span data-stu-id="39310-120">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="39310-121">この違いを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="39310-121">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="39310-122">`Await` 式またはステートメントは、自身が実行されているスレッドをブロックするのではなく、</span><span class="sxs-lookup"><span data-stu-id="39310-122">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="39310-123">非同期メソッドの残りの部分が待機中のタスクの継続として `Await` 式の後に登録されるようにします。</span><span class="sxs-lookup"><span data-stu-id="39310-123">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="39310-124">これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="39310-124">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="39310-125">タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="39310-125">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="39310-126">`Await` 式は、`Async` 修飾子で修飾されたすぐ外側のメソッドまたはラムダ式の本体でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="39310-126">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="39310-127">*Await* という用語がキーワードとして機能するのはこのコンテキストだけです。</span><span class="sxs-lookup"><span data-stu-id="39310-127">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="39310-128">他の場所では、識別子として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="39310-128">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="39310-129">`Async` メソッドまたはラムダ式内では、クエリ式、[Try…Catch…Finally ステートメント](../statements/try-catch-finally-statement.md)の `Catch` ブロックまたは `Finally` ブロック、`For` ループまたは `For Each` ループのループ コントロール変数式、または [SyncLock](../statements/synclock-statement.md) ステートメントの本体で `Await` 式を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="39310-129">Within the `Async` method or lambda expression, an `Await` expression cannot occur in a query expression, in the `Catch` or `Finally` block of a [Try…Catch…Finally statement](../statements/try-catch-finally-statement.md), in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="39310-130">例外</span><span class="sxs-lookup"><span data-stu-id="39310-130">Exceptions</span></span>

<span data-ttu-id="39310-131">大半の非同期メソッドは、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="39310-131">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="39310-132">返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39310-132">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="39310-133">`Await` 演算子は、これらのプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="39310-133">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="39310-134">タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`Await` 演算子はその例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="39310-134">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="39310-135">タスクを返す非同期メソッドを待機しているときにそのメソッドがキャンセルされた場合、`Await` 演算子は <xref:System.OperationCanceledException> を再スローします。</span><span class="sxs-lookup"><span data-stu-id="39310-135">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="39310-136">障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。</span><span class="sxs-lookup"><span data-stu-id="39310-136">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="39310-137">たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> の呼び出しの結果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="39310-137">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39310-138">このようなタスクを待機すると、await 操作によって 1 つの例外のみが再スローされます。</span><span class="sxs-lookup"><span data-stu-id="39310-138">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="39310-139">ただし、どの例外が再スローされるかを予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="39310-139">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="39310-140">非同期メソッドのエラー処理の例については、「[Try...Catch...Finally ステートメント](../statements/try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39310-140">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="39310-141">例</span><span class="sxs-lookup"><span data-stu-id="39310-141">Example</span></span>

<span data-ttu-id="39310-142">次に示す Windows フォームの例では、`Await` という非同期メソッドで `WaitAsynchronouslyAsync` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="39310-142">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="39310-143">このメソッドの動作と `WaitSynchronously` の動作の違いを確認します。</span><span class="sxs-lookup"><span data-stu-id="39310-143">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="39310-144">`WaitSynchronously` には `Await` 演算子がないため、定義で `Async` 修飾子が使用されていて、本体で <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> が呼び出されているにもかかわらず、同期的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="39310-144">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a><span data-ttu-id="39310-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="39310-145">See also</span></span>

- [<span data-ttu-id="39310-146">Async および Await を使用した非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="39310-146">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="39310-147">チュートリアル: Async と Await を使用した Web へのアクセス</span><span class="sxs-lookup"><span data-stu-id="39310-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="39310-148">Async</span><span class="sxs-lookup"><span data-stu-id="39310-148">Async</span></span>](../modifiers/async.md)
