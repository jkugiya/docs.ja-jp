---
description: '詳細情報: 指定した時間の経過後の非同期タスクのキャンセル (Visual Basic)'
title: 指定した時間の経過後の非同期タスクのキャンセル
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: fa1711017128dd32f29adfd87a540676371d02cf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431634"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="58cd0-103">指定した時間の経過後の非同期タスクのキャンセル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58cd0-103">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>

<span data-ttu-id="58cd0-104"><xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> メソッドを使用すると、一定の時間が過ぎた後に非同期操作が完了するまで待たない場合に、その操作を取り消しできます。</span><span class="sxs-lookup"><span data-stu-id="58cd0-104">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="58cd0-105">このメソッドは、`CancelAfter` 式によって指定された時間内に完了しない、関連付けられたタスクの取り消しをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="58cd0-105">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="58cd0-106">この例では、「[非同期タスクまたはタスクの一覧のキャンセル (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md)」で開発したコードに追加して、Web サイトの一覧をダウンロードして各サイトのコンテンツの長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-106">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="58cd0-107">この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="58cd0-107">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="58cd0-108">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="58cd0-108">Downloading the Example</span></span>

<span data-ttu-id="58cd0-109">完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」(非同期のサンプル: アプリケーションの微調整) からダウンロードできます。その後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="58cd0-109">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="58cd0-110">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-110">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="58cd0-111">メニュー バーで **[ファイル]** 、 **[開く]** 、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-111">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="58cd0-112">**[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningVB 用のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="58cd0-112">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="58cd0-113">**ソリューション エクスプローラー** で、**CancelAfterTime** プロジェクトのショートカット メニューを開き、 **[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58cd0-113">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="58cd0-114">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-114">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="58cd0-115">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-115">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="58cd0-116">プログラムを複数回実行して、出力がすべての Web サイトの出力を示したり、どの Web サイトの出力も示さなかったり、一部の Web サイトの出力を示したりすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-116">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

 <span data-ttu-id="58cd0-117">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.vb ファイルをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="58cd0-117">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="58cd0-118">例のビルド</span><span class="sxs-lookup"><span data-stu-id="58cd0-118">Building the Example</span></span>

<span data-ttu-id="58cd0-119">このトピックの例では、「[非同期タスクまたはタスクの一覧のキャンセル (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md)」で開発したプロジェクトに追加して、タスクのリストをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="58cd0-119">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="58cd0-120">この例では、 **[キャンセル]** ボタンは明示的に使用していませんが、同じ UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-120">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="58cd0-121">この例を自分で 1 つずつビルドするには、"例をダウンロードする" セクションの手順に従います。ただし、 **[スタートアップ プロジェクト]** として **CancelAListOfTasks** を選択します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-121">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="58cd0-122">そのプロジェクトに、このトピックでの変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-122">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="58cd0-123">次の例に示すように、タスクが取り消し済みとマークされるまでの最大時間を指定するには、`CancelAfter` に `startButton_Click` への呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-123">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="58cd0-124">追加部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="58cd0-124">The addition is marked with asterisks.</span></span>

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

        Await AccessTheWebAsync(cts.Token)
        resultsTextBox.Text &= vbCrLf & "Downloads complete."

    Catch ex As OperationCanceledException
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

    Catch ex As Exception
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
    End Try

    ' Set the CancellationTokenSource to Nothing when the download is complete.
    cts = Nothing
End Sub
```

<span data-ttu-id="58cd0-125">プログラムを複数回実行して、出力がすべての Web サイトの出力を示したり、どの Web サイトの出力も示さなかったり、一部の Web サイトの出力を示したりすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-125">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="58cd0-126">出力例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="58cd0-126">The following output is a sample:</span></span>

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="58cd0-127">コード例全体</span><span class="sxs-lookup"><span data-stu-id="58cd0-127">Complete Example</span></span>

<span data-ttu-id="58cd0-128">次のコードは、この例の MainWindow.xaml.vb ファイルのテキスト全体です。</span><span class="sxs-lookup"><span data-stu-id="58cd0-128">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="58cd0-129">アスタリスクはこの例のために追加された要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="58cd0-129">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="58cd0-130"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58cd0-130">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="58cd0-131">プロジェクトは、「[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」(非同期のサンプル: アプリケーションの微調整) からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="58cd0-131">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="58cd0-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="58cd0-132">See also</span></span>

- [<span data-ttu-id="58cd0-133">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58cd0-133">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="58cd0-134">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58cd0-134">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="58cd0-135">非同期タスクまたはタスクの一覧のキャンセル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58cd0-135">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="58cd0-136">非同期アプリケーションの微調整 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58cd0-136">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="58cd0-137">Async Sample:Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)</span><span class="sxs-lookup"><span data-stu-id="58cd0-137">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
