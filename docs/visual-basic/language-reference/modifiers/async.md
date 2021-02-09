---
description: '詳細情報: Async (Visual Basic)'
title: Async
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: a20c80ace06e386e7c106acc2b7e6258abca13b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701158"
---
# <a name="async-visual-basic"></a><span data-ttu-id="79b82-103">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79b82-103">Async (Visual Basic)</span></span>

<span data-ttu-id="79b82-104">`Async` 修飾子は、修飾するメソッドまたは[ラムダ式](../../programming-guide/language-features/procedures/lambda-expressions.md)が非同期であることを示します。</span><span class="sxs-lookup"><span data-stu-id="79b82-104">The `Async` modifier indicates that the method or [lambda expression](../../programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="79b82-105">このようなメソッドは、*非同期メソッド* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="79b82-105">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="79b82-106">非同期メソッドは、呼び出し元のスレッドをブロックすることなく、実行に時間のかかる可能性のある処理を行うことができる、便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="79b82-106">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="79b82-107">非同期メソッドの呼び出し元は、非同期メソッドの完了を待たずに作業を再開できます。</span><span class="sxs-lookup"><span data-stu-id="79b82-107">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="79b82-108">`Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="79b82-108">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="79b82-109">非同期プログラミングの概要については、「[Async および Await を使用した非同期プログラミング](../../programming-guide/concepts/async/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79b82-109">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="79b82-110">次の例は、非同期メソッドの構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="79b82-110">The following example shows the structure of an async method.</span></span> <span data-ttu-id="79b82-111">規則により、非同期メソッドの名前の末尾は "Async" になります。</span><span class="sxs-lookup"><span data-stu-id="79b82-111">By convention, async method names end in "Async."</span></span>

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

<span data-ttu-id="79b82-112">通常、`Async` キーワードで修飾されているメソッドには、1 つ以上の [Await](async.md) 式またはステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="79b82-112">Typically, a method modified by the `Async` keyword contains at least one [Await](async.md) expression or statement.</span></span> <span data-ttu-id="79b82-113">メソッドは、最初の `Await` に到達するまで同期的に実行されますが、この時点で、待機していたタスクが完了するまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="79b82-113">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="79b82-114">その間、コントロールはメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="79b82-114">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="79b82-115">メソッドに `Await` 式またはステートメントが含まれていない場合、メソッドは中断されず、同期メソッドのように実行されます。</span><span class="sxs-lookup"><span data-stu-id="79b82-115">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="79b82-116">`Await` が含まれていない非同期メソッドが存在する場合は、その状態がエラーを示す可能性があるため、コンパイラによって警告が通知されます。</span><span class="sxs-lookup"><span data-stu-id="79b82-116">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="79b82-117">詳細については、[コンパイラ エラー](../error-messages/bc42358.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="79b82-117">For more information, see the [compiler error](../error-messages/bc42358.md).</span></span>

<span data-ttu-id="79b82-118">`Async` キーワードは、予約されていないキーワードです。</span><span class="sxs-lookup"><span data-stu-id="79b82-118">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="79b82-119">メソッドまたはラムダ式を修飾する場合にキーワードとなります。</span><span class="sxs-lookup"><span data-stu-id="79b82-119">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="79b82-120">それ以外の場合は、識別子として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="79b82-120">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="79b82-121">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="79b82-121">Return Types</span></span>

<span data-ttu-id="79b82-122">非同期メソッドは、[Sub](../../programming-guide/language-features/procedures/sub-procedures.md) プロシージャか、戻り値の型が <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> の [Function](../../programming-guide/language-features/procedures/function-procedures.md) プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="79b82-122">An async method is either a [Sub](../../programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="79b82-123">メソッドで、[ByRef](byref.md) パラメーターを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="79b82-123">The method cannot declare any [ByRef](byref.md) parameters.</span></span>

<span data-ttu-id="79b82-124">メソッドの [Return](../statements/return-statement.md) ステートメントに TResult 型のオペランドがある場合、非同期メソッドの戻り値の型として `Task(Of TResult)` を指定します。</span><span class="sxs-lookup"><span data-stu-id="79b82-124">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="79b82-125">メソッドの完了時に意味のある値を返さない場合は、`Task` を使用します。</span><span class="sxs-lookup"><span data-stu-id="79b82-125">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="79b82-126">これにより、メソッドの呼び出しでは `Task` が返されますが、`Task` の完了時に、`Await` を待機している `Task` ステートメントは結果値を生成しません。</span><span class="sxs-lookup"><span data-stu-id="79b82-126">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="79b82-127">非同期サブルーチンは主として、`Sub` プロシージャが必要なイベント ハンドラーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="79b82-127">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="79b82-128">非同期サブルーチンの呼び出し元は、このサブルーチンを待機できず、このメソッドがスローする例外をキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="79b82-128">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="79b82-129">使用例を含む詳細については、「[非同期の戻り値の型](../../programming-guide/concepts/async/async-return-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79b82-129">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="79b82-130">例</span><span class="sxs-lookup"><span data-stu-id="79b82-130">Example</span></span>

<span data-ttu-id="79b82-131">次の例は、非同期のイベント ハンドラー、非同期ラムダ式、および非同期メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="79b82-131">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="79b82-132">これらの要素を使用する例の完全版については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79b82-132">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="79b82-133">チュートリアル コードは、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)のページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="79b82-133">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a><span data-ttu-id="79b82-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="79b82-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="79b82-135">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="79b82-135">Await Operator</span></span>](../operators/await-operator.md)
- [<span data-ttu-id="79b82-136">Async および Await を使用した非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="79b82-136">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="79b82-137">チュートリアル: Async と Await を使用した Web へのアクセス</span><span class="sxs-lookup"><span data-stu-id="79b82-137">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
