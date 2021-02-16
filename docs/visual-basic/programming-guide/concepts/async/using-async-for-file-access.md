---
description: '詳細情報: ファイル アクセスにおける非同期の使用 (Visual Basic)'
title: ファイル アクセスにおける非同期の使用
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: f065ef8d8672569921e1652e62d24c10a506f828
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474214"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="cf638-103">ファイル アクセスにおける非同期の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf638-103">Using Async for File Access (Visual Basic)</span></span>

<span data-ttu-id="cf638-104">ファイルにアクセスする際に非同期機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf638-104">You can use the Async feature to access files.</span></span> <span data-ttu-id="cf638-105">非同期機能を使用すると、コールバックの使用や複数のメソッドまたはラムダ式へのコードの分割を行わずに、非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="cf638-105">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="cf638-106">同期コードを非同期コードにするには、同期メソッドの代わりに非同期メソッドを呼び出して、コードにいくつかのキーワードを追加するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="cf638-106">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="cf638-107">ファイル アクセスの呼び出しに非同期性を適用する利点には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="cf638-107">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="cf638-108">非同期性により、UI アプリケーションの応答性が向上します。非同期処理を開始した UI スレッドが他の処理を実行できるためです。</span><span class="sxs-lookup"><span data-stu-id="cf638-108">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="cf638-109">UI スレッドが、時間のかかるコード、たとえば 50 ミリ秒を超えるコードを実行する必要がある場合、I/O が完了して、UI スレッドがキーボードやマウス入力などのイベントを再度処理できるようになるまで、UI が停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="cf638-109">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="cf638-110">非同期性を適用すると、スレッドの必要性が軽減され、ASP.NET などのサーバー ベースのアプリケーションのスケーラビリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="cf638-110">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="cf638-111">アプリケーションが応答ごとに専用スレッドを使用している場合、1,000 個の要求を同時に処理するには、1,000 個のスレッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="cf638-111">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="cf638-112">非同期処理では、待機中にスレッドを使用する必要がほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="cf638-112">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="cf638-113">既存の I/O 完了スレッドが最後に少しだけ使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf638-113">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="cf638-114">現状ではファイル アクセス操作の待機時間が非常に短くても、将来に大幅に長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf638-114">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="cf638-115">たとえば、地球の裏側にあるサーバーにファイルが移動される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cf638-115">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="cf638-116">非同期機能の使用に伴うオーバーヘッドはわずかです。</span><span class="sxs-lookup"><span data-stu-id="cf638-116">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="cf638-117">非同期タスクは簡単に並列実行できます。</span><span class="sxs-lookup"><span data-stu-id="cf638-117">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="cf638-118">例の実行</span><span class="sxs-lookup"><span data-stu-id="cf638-118">Running the Examples</span></span>  

 <span data-ttu-id="cf638-119">このトピックの例を実行するには、**WPF アプリケーション** または **Windows フォーム アプリケーション** を作成し、**ボタン** を追加します。</span><span class="sxs-lookup"><span data-stu-id="cf638-119">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="cf638-120">ボタンの `Click` イベントに、それぞれの例で最初のメソッドの呼び出しを追加してください。</span><span class="sxs-lookup"><span data-stu-id="cf638-120">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="cf638-121">以降の例には、次の `Imports` ステートメントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="cf638-121">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="cf638-122">FileStream クラスの使用</span><span class="sxs-lookup"><span data-stu-id="cf638-122">Use of the FileStream Class</span></span>  

 <span data-ttu-id="cf638-123">このトピックの例では、<xref:System.IO.FileStream> クラスを使用します。このクラスには、非同期 I/O をオペレーティング システム レベルで発生させるオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="cf638-123">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="cf638-124">このオプションを使用すると、多くのケースで ThreadPool スレッドがブロックされるのを回避できます。</span><span class="sxs-lookup"><span data-stu-id="cf638-124">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="cf638-125">このオプションを有効にするには、コンストラクター呼び出しで `useAsync=true` または `options=FileOptions.Asynchronous` 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf638-125">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="cf638-126">ファイル パスを指定して <xref:System.IO.StreamReader> と <xref:System.IO.StreamWriter> を直接開いた場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="cf638-126">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="cf638-127">一方、<xref:System.IO.FileStream> クラスによって開かれた <xref:System.IO.Stream> を使用する場合は、このオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf638-127">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="cf638-128">UI アプリでは、ThreadPool スレッドがブロックされた場合でも、非同期呼び出しのほうが高速です。これは、UI スレッドは待機中にブロックされないためです。</span><span class="sxs-lookup"><span data-stu-id="cf638-128">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="cf638-129">テキストの書き込み</span><span class="sxs-lookup"><span data-stu-id="cf638-129">Writing Text</span></span>  

 <span data-ttu-id="cf638-130">次の例では、ファイルにテキストを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="cf638-130">The following example writes text to a file.</span></span> <span data-ttu-id="cf638-131">各 await ステートメントに達すると、メソッドは直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="cf638-131">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="cf638-132">ファイル I/O が完了すると、メソッドは await ステートメントの後のステートメントから再開します。</span><span class="sxs-lookup"><span data-stu-id="cf638-132">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="cf638-133">await ステートメントを使用するメソッドの定義に async 修飾子が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cf638-133">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 <span data-ttu-id="cf638-134">元の例には `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)` ステートメントがあります。これは、次の 2 つのステートメントの省略形です。</span><span class="sxs-lookup"><span data-stu-id="cf638-134">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="cf638-135">最初のステートメントはタスクを返し、ファイル処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="cf638-135">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="cf638-136">await が含まれた 2 番目のステートメントによって、メソッドが直ちに終了し、別のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="cf638-136">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="cf638-137">ファイル処理が完了すると、await の後のステートメントに実行が戻ります。</span><span class="sxs-lookup"><span data-stu-id="cf638-137">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="cf638-138">詳細については、「[非同期プログラムにおける制御フロー (Visual Basic)](control-flow-in-async-programs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf638-138">For more information, see  [Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="cf638-139">テキストの読み取り</span><span class="sxs-lookup"><span data-stu-id="cf638-139">Reading Text</span></span>  

 <span data-ttu-id="cf638-140">次の例では、ファイルからテキストを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="cf638-140">The following example reads text from a file.</span></span> <span data-ttu-id="cf638-141">テキストはバッファーに格納されます。この例では <xref:System.Text.StringBuilder> に配置されます。</span><span class="sxs-lookup"><span data-stu-id="cf638-141">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="cf638-142">前の例と異なり、await の評価で値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cf638-142">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="cf638-143"><xref:System.IO.Stream.ReadAsync%2A> メソッドによって <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>> が返されます。処理の完了後、await の評価によって `Int32` 値 (`numRead`) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cf638-143">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="cf638-144">詳細については、「[非同期の戻り値の型 (Visual Basic)](async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf638-144">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="cf638-145">並列非同期 I/O</span><span class="sxs-lookup"><span data-stu-id="cf638-145">Parallel Asynchronous I/O</span></span>  

 <span data-ttu-id="cf638-146">次の例では、10 個のテキスト ファイルを記述する並列処理を示します。</span><span class="sxs-lookup"><span data-stu-id="cf638-146">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="cf638-147"><xref:System.IO.Stream.WriteAsync%2A> メソッドは、ファイルごとにタスクを返します。タスクはタスクの一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="cf638-147">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="cf638-148">`Await Task.WhenAll(tasks)` ステートメントはメソッドを終了し、すべてのタスクのファイル処理が完了すると、メソッド内で再開します。</span><span class="sxs-lookup"><span data-stu-id="cf638-148">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="cf638-149">この例では、タスクの完了後、`Finally` ブロックのすべての <xref:System.IO.FileStream> インスタンスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="cf638-149">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="cf638-150">`Imports` ステートメントで `FileStream` が作成された場合は、タスクが完了する前に `FileStream` が破棄されることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf638-150">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="cf638-151">パフォーマンスの向上のほとんどが、非同期処理ではなく並列処理によって実現していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cf638-151">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="cf638-152">非同期性の利点は、複数のスレッドやユーザー インターフェイス スレッドが拘束されなくなる点にあります。</span><span class="sxs-lookup"><span data-stu-id="cf638-152">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="cf638-153"><xref:System.IO.Stream.WriteAsync%2A> メソッドと <xref:System.IO.Stream.ReadAsync%2A> メソッドを使用すると、<xref:System.Threading.CancellationToken> を指定して、途中で処理をキャンセルすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf638-153">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="cf638-154">詳細については、「[非同期アプリケーションの微調整 (Visual Basic)](fine-tuning-your-async-application.md)」および「[マネージド スレッドのキャンセル](../../../../standard/threading/cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf638-154">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf638-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf638-155">See also</span></span>

- [<span data-ttu-id="cf638-156">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf638-156">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="cf638-157">非同期の戻り値の型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf638-157">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="cf638-158">非同期プログラムにおける制御フロー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf638-158">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
