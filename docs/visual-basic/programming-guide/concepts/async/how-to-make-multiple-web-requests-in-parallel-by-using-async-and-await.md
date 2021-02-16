---
description: '詳細情報: 方法:Async と Await を使用して複数の Web 要求を並列実行する (Visual Basic)'
title: '方法: Async と Await を使用して複数の Web 要求を並列実行する'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: e1137424911b77ba94a760a4b4b034e45ef83462
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474344"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="0585d-103">方法: Async と Await を使用して複数の Web 要求を並列実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0585d-103">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="0585d-104">非同期メソッドでは、タスクは作成されると開始されます。</span><span class="sxs-lookup"><span data-stu-id="0585d-104">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="0585d-105">[Await](../../../language-reference/operators/await-operator.md) 演算子は、メソッド内でタスクが終了するまで処理が続行できなくなった時点で、タスクに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0585d-105">The [Await](../../../language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="0585d-106">次の例に示すように、タスクは多くの場合、作成されるとすぐに待機します。</span><span class="sxs-lookup"><span data-stu-id="0585d-106">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

<span data-ttu-id="0585d-107">ただし、プログラムにタスクの完了に依存せずに実行する別の処理がある場合、タスクの作成とタスクの待機を分けることもできます。</span><span class="sxs-lookup"><span data-stu-id="0585d-107">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>

```vb
' The following line creates and starts the task.
Dim myTask = someWebAccessMethodAsync(url)

' While the task is running, you can do other work that does not depend
' on the results of the task.
' . . . . .

' The application of Await suspends the rest of this method until the task is
' complete.
Dim result = Await myTask
```

<span data-ttu-id="0585d-108">タスクを開始して待機する間に、他のタスクを開始できます。</span><span class="sxs-lookup"><span data-stu-id="0585d-108">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="0585d-109">追加のタスクは暗黙的に並列で実行されますが、追加のスレッドは作成されません。</span><span class="sxs-lookup"><span data-stu-id="0585d-109">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>

<span data-ttu-id="0585d-110">次のプログラムは 3 つの非同期的な Web ダウンロードを開始し、次に呼び出した順にそれを待機します。</span><span class="sxs-lookup"><span data-stu-id="0585d-110">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="0585d-111">プログラムを実行する場合、タスクは必ずしも作成して待機した順には終了しないことに注意します。</span><span class="sxs-lookup"><span data-stu-id="0585d-111">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="0585d-112">タスクは作成されると実行され、メソッドが await 式に到達する前に 1 つまたは複数のタスクが終了する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0585d-112">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="0585d-113">このプロジェクトを完成させるには、Visual Studio 2012 以降および .NET Framework 4.5 以降がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0585d-113">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>

<span data-ttu-id="0585d-114">複数のタスクを同時に開始する別の例については、「[方法: Task.whenall を使用して非同期のチュートリアルを拡張する (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0585d-114">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

<span data-ttu-id="0585d-115">この例のコードは、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)のページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="0585d-115">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>

### <a name="to-set-up-the-project"></a><span data-ttu-id="0585d-116">プロジェクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="0585d-116">To set up the project</span></span>

1. <span data-ttu-id="0585d-117">WPF アプリケーションを設定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0585d-117">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="0585d-118">これらの手順の詳細については、「[チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0585d-118">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="0585d-119">テキスト ボックスとボタンを含む WPF アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="0585d-119">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="0585d-120">ボタンに `startButton` という名前を付け、テキスト ボックスに `resultsTextBox` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="0585d-120">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>

    - <span data-ttu-id="0585d-121"><xref:System.Net.Http> への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0585d-121">Add a reference for <xref:System.Net.Http>.</span></span>

    - <span data-ttu-id="0585d-122">MainWindow.xaml.vb ファイルで、`System.Net.Http` の `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="0585d-122">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>

### <a name="to-add-the-code"></a><span data-ttu-id="0585d-123">コードを追加するには</span><span class="sxs-lookup"><span data-stu-id="0585d-123">To add the code</span></span>

1. <span data-ttu-id="0585d-124">デザイン ウィンドウの MainWindow.xaml で、ボタンをダブルクリックして、MainWindow.xaml.vb に `startButton_Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0585d-124">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="0585d-125">次のコードをコピーし、MainWindow.xaml.vb の `startButton_Click` の本体に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0585d-125">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     <span data-ttu-id="0585d-126">このコードは、アプリケーションを呼び出す非同期メソッドである `CreateMultipleTasksAsync` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0585d-126">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>

3. <span data-ttu-id="0585d-127">プロジェクトに次のサポート メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0585d-127">Add the following support methods to the project:</span></span>

    - <span data-ttu-id="0585d-128">`ProcessURLAsync` は <xref:System.Net.Http.HttpClient> メソッドを使用して、Web サイトのコンテンツをバイト配列としてダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="0585d-128">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="0585d-129">次に `ProcessURLAsync` サポート メソッドは、配列の長さを表示して返します。</span><span class="sxs-lookup"><span data-stu-id="0585d-129">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>

    - <span data-ttu-id="0585d-130">`DisplayResults` は各 URL のバイト配列内のバイトの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="0585d-130">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="0585d-131">この表示は、各タスクがいつダウンロードを完了したかを示します。</span><span class="sxs-lookup"><span data-stu-id="0585d-131">This display shows when each task has finished downloading.</span></span>

     <span data-ttu-id="0585d-132">次のメソッドをコピーし、MainWindow.xaml.vb の `startButton_Click` イベント ハンドラーの後に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0585d-132">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

4. <span data-ttu-id="0585d-133">最後に、次の手順を実行するメソッド `CreateMultipleTasksAsync` を定義します。</span><span class="sxs-lookup"><span data-stu-id="0585d-133">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>

    - <span data-ttu-id="0585d-134">このメソッドは、`HttpClient` の <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> メソッドにアクセスするために必要な `ProcessURLAsync` オブジェクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="0585d-134">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>

    - <span data-ttu-id="0585d-135">このメソッドは <xref:System.Threading.Tasks.Task%601> が整数である `TResult` 型の 3 つのタスクを作成して開始します。</span><span class="sxs-lookup"><span data-stu-id="0585d-135">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="0585d-136">各タスクが終了すると、`DisplayResults` はタスクの URL とダウンロードしたコンテンツの長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="0585d-136">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="0585d-137">タスクは非同期的に実行されるため、結果が表示される順序は、宣言された順序と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0585d-137">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>

    - <span data-ttu-id="0585d-138">メソッドは、各タスクの完了を待機します。</span><span class="sxs-lookup"><span data-stu-id="0585d-138">The method awaits the completion of each task.</span></span> <span data-ttu-id="0585d-139">各 `Await` 演算子は、待機したタスクが終了するまで `CreateMultipleTasksAsync` の実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="0585d-139">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="0585d-140">さらに演算子は、完了した各タスクから `ProcessURLAsync` への呼び出しからの戻り値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0585d-140">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>

    - <span data-ttu-id="0585d-141">タスクが完了して整数値が取得されると、メソッドは Web サイトの長さの合計し、その結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="0585d-141">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>

     <span data-ttu-id="0585d-142">次のメソッドをコピーしてソリューションに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0585d-142">Copy the following method, and paste it into your solution.</span></span>

    ```vb
    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function
    ```

5. <span data-ttu-id="0585d-143">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="0585d-143">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="0585d-144">プログラムを複数回実行して、3 つのタスクが必ずしも同じ順序では完了しないこと、また完了の順序は必ずしも作成され待機した順序と同じではないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0585d-144">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>

## <a name="example"></a><span data-ttu-id="0585d-145">例</span><span class="sxs-lookup"><span data-stu-id="0585d-145">Example</span></span>

<span data-ttu-id="0585d-146">ここまでの例をすべて含んだコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0585d-146">The following code contains the full example.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
        resultsTextBox.Clear()
        Await CreateMultipleTasksAsync()
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function CreateMultipleTasksAsync() As Task

        ' Declare an HttpClient object, and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Create and start the tasks. As each task finishes, DisplayResults
        ' displays its length.
        Dim download1 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com", client)
        Dim download2 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)
        Dim download3 As Task(Of Integer) =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)

        ' Await each task.
        Dim length1 As Integer = Await download1
        Dim length2 As Integer = Await download2
        Dim length3 As Integer = Await download3

        Dim total As Integer = length1 + length2 + length3

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="0585d-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="0585d-147">See also</span></span>

- [<span data-ttu-id="0585d-148">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0585d-148">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="0585d-149">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0585d-149">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="0585d-150">方法: Task.WhenAll を使用して非同期のチュートリアルを拡張する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0585d-150">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
