---
description: '詳細情報: 完了時での複数の同期タスクとプロセスの実行 (Visual Basic)'
title: 完了時での複数の同期タスクとプロセスの実行
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: 5053bb55acaa058c551ad5f4169ef93c773fc1ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474266"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="1beae-103">完了時での複数の同期タスクとプロセスの実行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1beae-103">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>

<span data-ttu-id="1beae-104"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> を使用すると、複数のタスクを、開始された順番に処理するのでなく、同時に開始して完了するごとに 1 つずつ処理できます。</span><span class="sxs-lookup"><span data-stu-id="1beae-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="1beae-105">クエリを使用して、タスクのコレクションを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1beae-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="1beae-106">各タスクは、指定された Web サイトのコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1beae-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="1beae-107">while ループの各反復で、待機されている `WhenAny` への呼び出しは、最初にダウンロードを終了するタスクのコレクションにあるタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="1beae-107">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="1beae-108">タスクはコレクションから削除され、処理されます。</span><span class="sxs-lookup"><span data-stu-id="1beae-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="1beae-109">ループは、コレクションのタスクがなくなるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="1beae-109">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1beae-110">この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1beae-110">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="1beae-111">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="1beae-111">Downloading the Example</span></span>  

 <span data-ttu-id="1beae-112">完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」(非同期のサンプル: アプリケーションの微調整) からダウンロードできます。その後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1beae-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="1beae-113">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="1beae-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="1beae-114">メニュー バーで **[ファイル]** 、 **[開く]** 、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1beae-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="1beae-115">**[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningVB 用のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1beae-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="1beae-116">**ソリューション エクスプローラー** で、**ProcessTasksAsTheyFinish** プロジェクトのショートカット メニューを開き、 **[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1beae-116">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="1beae-117">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="1beae-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="1beae-118">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="1beae-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="1beae-119">ダウンロードの長さが常に同じ順序では表示されないことを確認するために、プロジェクトを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="1beae-119">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="1beae-120">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.vb ファイルをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="1beae-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="1beae-121">例のビルド</span><span class="sxs-lookup"><span data-stu-id="1beae-121">Building the Example</span></span>  

 <span data-ttu-id="1beae-122">この例では、「[完了後の残りの非同期タスクのキャンセル (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)」で開発したコードを追加し、同じ UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="1beae-122">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="1beae-123">この例を自分でビルドするには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、 **[スタートアップ プロジェクト]** では **CancelAfterOneTask** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1beae-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="1beae-124">そのプロジェクトの `AccessTheWebAsync` メソッドに、このトピックでの変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="1beae-124">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="1beae-125">変更部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="1beae-125">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="1beae-126">**CancelAfterOneTask** プロジェクトには、実行時にタスクのコレクションを作成するクエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1beae-126">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="1beae-127">次のコードの `ProcessURLAsync` への各呼び出しは、<xref:System.Threading.Tasks.Task%601> が整数である `TResult` を返します。</span><span class="sxs-lookup"><span data-stu-id="1beae-127">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 <span data-ttu-id="1beae-128">プロジェクトの MainWindow.xaml.vb ファイルで、`AccessTheWebAsync` メソッドに次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="1beae-128">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
- <span data-ttu-id="1beae-129"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> の代わりに <xref:System.Linq.Enumerable.ToArray%2A> を適用して、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1beae-129">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- <span data-ttu-id="1beae-130">コレクションの各タスクで次の手順を実行する while ループを追加します。</span><span class="sxs-lookup"><span data-stu-id="1beae-130">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1. <span data-ttu-id="1beae-131">`WhenAny` への呼び出しを待機し、ダウンロードを終了する、コレクションの最初のタスクを識別します。</span><span class="sxs-lookup"><span data-stu-id="1beae-131">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```vb  
        Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. <span data-ttu-id="1beae-132">コレクションからそのタスクを削除します。</span><span class="sxs-lookup"><span data-stu-id="1beae-132">Removes that task from the collection.</span></span>  
  
        ```vb  
        downloadTasks.Remove(finishedTask)  
        ```  
  
    3. <span data-ttu-id="1beae-133">`finishedTask` への呼び出しから返される、`ProcessURLAsync` を待機します。</span><span class="sxs-lookup"><span data-stu-id="1beae-133">Awaits `finishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="1beae-134">`finishedTask` 変数は <xref:System.Threading.Tasks.Task%601> が整数である `TReturn` です。</span><span class="sxs-lookup"><span data-stu-id="1beae-134">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="1beae-135">次の例に示すように、タスクは既に完了していますが、ダウンロードした Web サイトの長さの取得を待機します。</span><span class="sxs-lookup"><span data-stu-id="1beae-135">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await finishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="1beae-136">ダウンロードの長さが常に同じ順序では表示されないことを確認するために、プロジェクトを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="1beae-136">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1beae-137">ループで `WhenAny` を使って、例に示すように、いくつかのタスクを格納する問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="1beae-137">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="1beae-138">ただし、多数のタスクが処理する場合、他のアプローチがより効率的です。</span><span class="sxs-lookup"><span data-stu-id="1beae-138">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="1beae-139">使用例を含む詳細については、「[Processing Tasks as they complete (完了したタスクを処理する)](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1beae-139">For more information and examples, see [Processing Tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="1beae-140">コード例全体</span><span class="sxs-lookup"><span data-stu-id="1beae-140">Complete Example</span></span>  

 <span data-ttu-id="1beae-141">次のコードは、この例の MainWindow.xaml.vb ファイルのテキスト全体です。</span><span class="sxs-lookup"><span data-stu-id="1beae-141">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="1beae-142">アスタリスクはこの例のために追加された要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="1beae-142">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="1beae-143"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1beae-143">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="1beae-144">プロジェクトは、「[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」(非同期のサンプル: アプリケーションの微調整) からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1beae-144">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(finishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await finishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        Return urlContents.Length  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1beae-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="1beae-145">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="1beae-146">非同期アプリケーションの微調整 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1beae-146">Fine-Tuning Your Async Application (Visual Basic)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="1beae-147">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1beae-147">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="1beae-148">Async Sample:Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)</span><span class="sxs-lookup"><span data-stu-id="1beae-148">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
