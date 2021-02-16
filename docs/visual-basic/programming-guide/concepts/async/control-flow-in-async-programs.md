---
description: '詳細情報: 非同期プログラムにおける制御フロー (Visual Basic)'
title: 非同期プログラムにおける制御フロー
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: bf0ca6a083971cb02cfb6dff2dfcaaabd5405b36
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428247"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="22930-103">非同期プログラムにおける制御フロー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22930-103">Control Flow in Async Programs (Visual Basic)</span></span>

<span data-ttu-id="22930-104">`Async` キーワードと `Await` キーワードを使用すると、非同期のプログラムの作成と保守をより簡単に行えます。</span><span class="sxs-lookup"><span data-stu-id="22930-104">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="22930-105">ただし、プログラムがどのように動作するかを理解しないと、その結果は予想に反するものになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="22930-105">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="22930-106">このトピックでは、簡単な非同期プログラムによる制御フローをトレースして、制御があるメソッドから別のメソッドに移るタイミングと、その都度転送される情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="22930-106">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

> [!NOTE]
> <span data-ttu-id="22930-107">`Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="22930-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>

<span data-ttu-id="22930-108">一般に、[Async](../../../language-reference/modifiers/async.md) 修飾子を使用した非同期コードを含むメソッドをマークします。</span><span class="sxs-lookup"><span data-stu-id="22930-108">In general, you mark methods that contain asynchronous code with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="22930-109">async 修飾子でマークされたメソッドでは、[Await (Visual Basic)](../../../language-reference/operators/await-operator.md) 演算子を使用して、呼び出される非同期処理の終了をメソッドが待機する場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="22930-109">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="22930-110">詳細については、「[Async および Await を使用した非同期プログラミング (Visual Basic)](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22930-110">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="22930-111">次の例では、非同期メソッドを使用して、指定した Web サイトのコンテンツを文字列としてダウンロードし、その文字列の長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="22930-111">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="22930-112">この例には、次の 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="22930-112">The example contains the following two methods.</span></span>

- <span data-ttu-id="22930-113">`startButton_Click` を呼び出して結果を表示する `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="22930-113">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="22930-114">Web サイトのコンテンツを文字列としてダウンロードして、その文字列の長さを返す `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="22930-114">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="22930-115">`AccessTheWebAsync` は、非同期 <xref:System.Net.Http.HttpClient> メソッドである <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> を使用してコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="22930-115">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="22930-116">番号付き表示行はプログラム全体で重要なポイントを示し、プログラムがどのように実行され、マークされている各ポイントで何が発生するかを理解するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="22930-116">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="22930-117">表示行には「1」から「6」までのラベルが付けられています。</span><span class="sxs-lookup"><span data-stu-id="22930-117">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="22930-118">このラベルは、プログラムがこれらのコード行に到達する順序を表します。</span><span class="sxs-lookup"><span data-stu-id="22930-118">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="22930-119">次のコードは、プログラムの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="22930-119">The following code shows an outline of the program.</span></span>

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

<span data-ttu-id="22930-120">「1」から「6」までのそれぞれのラベルの位置は、プログラムの現在の状態に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="22930-120">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="22930-121">次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="22930-121">The following output is produced:</span></span>

```console
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="22930-122">プログラムをセットアップする</span><span class="sxs-lookup"><span data-stu-id="22930-122">Set Up the Program</span></span>

<span data-ttu-id="22930-123">このトピックで使用するコードは、MSDN からダウンロードするか、または自分でビルドできます。</span><span class="sxs-lookup"><span data-stu-id="22930-123">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="22930-124">この例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="22930-124">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="22930-125">プログラムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="22930-125">Download the Program</span></span>

<span data-ttu-id="22930-126">このトピックのアプリケーションは、「[非同期のサンプル:非同期プログラムにおける制御フロー](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="22930-126">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="22930-127">次の手順でプログラムを開いて実行します。</span><span class="sxs-lookup"><span data-stu-id="22930-127">The following steps open and run the program.</span></span>

1. <span data-ttu-id="22930-128">ダウンロードしたファイルを解凍し、Visual Studio を開始します。</span><span class="sxs-lookup"><span data-stu-id="22930-128">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="22930-129">メニュー バーで **[ファイル]** 、 **[開く]** 、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="22930-129">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="22930-130">解凍したサンプル コードが含まれるフォルダーに移動し、ソリューション (.sln) ファイルを開き、F5 キーを押してプロジェクトをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="22930-130">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>

### <a name="build-the-program-yourself"></a><span data-ttu-id="22930-131">プログラムを手動でビルドする</span><span class="sxs-lookup"><span data-stu-id="22930-131">Build the Program Yourself</span></span>

<span data-ttu-id="22930-132">次の Windows Presentation Foundation (WPF) プロジェクトには、このトピックのコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="22930-132">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="22930-133">このプロジェクトを実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="22930-133">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="22930-134">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="22930-134">Start Visual Studio.</span></span>

2. <span data-ttu-id="22930-135">メニュー バーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="22930-135">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="22930-136">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="22930-136">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="22930-137">**[インストールされたテンプレート]** ペインで、 **[Visual Basic]** を選択し、プロジェクトの種類の一覧で **[WPF アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="22930-137">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="22930-138">プロジェクトの名前として「`AsyncTracer`」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="22930-138">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

    <span data-ttu-id="22930-139">**ソリューション エクスプローラー** に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="22930-139">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="22930-140">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="22930-140">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

    <span data-ttu-id="22930-141">タブが表示されない場合は、**ソリューション エクスプローラー** で MainWindow.xaml のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="22930-141">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="22930-142">MainWindow.xaml の **XAML** ビューで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="22930-142">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    <span data-ttu-id="22930-143">テキスト ボックスとボタンを含む簡単なウィンドウが、MainWindow.xaml の **デザイン** ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="22930-143">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="22930-144"><xref:System.Net.Http> への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="22930-144">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="22930-145">**ソリューション エクスプローラー** で MainWindow.xaml.vb のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="22930-145">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

9. <span data-ttu-id="22930-146">MainWindow.xaml.vb のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="22930-146">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. <span data-ttu-id="22930-147">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="22930-147">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="22930-148">次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="22930-148">The following output should appear:</span></span>

    ```console
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="22930-149">プログラムのトレース</span><span class="sxs-lookup"><span data-stu-id="22930-149">Trace the Program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="22930-150">手順 1. および 2.</span><span class="sxs-lookup"><span data-stu-id="22930-150">Steps ONE and TWO</span></span>

<span data-ttu-id="22930-151">`startButton_Click` が `AccessTheWebAsync` を呼び出し、`AccessTheWebAsync` が非同期 <xref:System.Net.Http.HttpClient> メソッド <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> を呼び出すと、最初の 2 行の表示行がパスをトレースします。</span><span class="sxs-lookup"><span data-stu-id="22930-151">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="22930-152">次の図は、メソッドからメソッドへの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="22930-152">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="22930-153">![手順 1. および 2.](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="22930-153">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="22930-154">`AccessTheWebAsync` と `client.GetStringAsync` の戻り値の型はどちらも <xref:System.Threading.Tasks.Task%601> です。</span><span class="sxs-lookup"><span data-stu-id="22930-154">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="22930-155">`AccessTheWebAsync` では、TResult は整数です。</span><span class="sxs-lookup"><span data-stu-id="22930-155">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="22930-156">`GetStringAsync` では、TResult は文字列です。</span><span class="sxs-lookup"><span data-stu-id="22930-156">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="22930-157">非同期メソッドの戻り値の型について詳しくは、「[非同期の戻り値の型 (Visual Basic)](async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22930-157">For more information about async method return types, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

<span data-ttu-id="22930-158">タスクを返す非同期のメソッドは、制御が呼び出し元に戻ると、タスク インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="22930-158">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="22930-159">`Await` 演算子が呼び出されたメソッドで実行されるか、または呼び出されたメソッドが終了すると、非同期メソッドから呼び出し元に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="22930-159">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="22930-160">「3」から「6」のラベルの付いた表示行はこのプロセスの部分をトレースします。</span><span class="sxs-lookup"><span data-stu-id="22930-160">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="22930-161">手順 3.</span><span class="sxs-lookup"><span data-stu-id="22930-161">Step THREE</span></span>

<span data-ttu-id="22930-162">`AccessTheWebAsync` で非同期メソッド <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> が呼び出され、ターゲットの Web ページのコンテンツがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="22930-162">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="22930-163">`client.GetStringAsync` が制御を返すと、`AccessTheWebAsync` から `client.GetStringAsync` に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="22930-163">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

<span data-ttu-id="22930-164">`client.GetStringAsync` メソッドは、`getStringTask` の `AccessTheWebAsync` 変数に割り当てる文字列のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="22930-164">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="22930-165">プログラム例の次の行は、`client.GetStringAsync` の呼び出しと割り当てを示しています。</span><span class="sxs-lookup"><span data-stu-id="22930-165">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

<span data-ttu-id="22930-166">このタスクは `client.GetStringAsync` により実際の文字列が最終的に生成される約束と見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="22930-166">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="22930-167">`AccessTheWebAsync` には `client.GetStringAsync` から約束された文字列に依存しない処理がある場合、その処理は `client.GetStringAsync` を待機している間は、続行できます。</span><span class="sxs-lookup"><span data-stu-id="22930-167">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="22930-168">この例では、"THREE" のラベルの付いた行の出力は、独立した処理を行う機会を表します。</span><span class="sxs-lookup"><span data-stu-id="22930-168">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="22930-169">次のステートメントは `AccessTheWebAsync` が待機中の場合 `getStringTask` の進行を中断します。</span><span class="sxs-lookup"><span data-stu-id="22930-169">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```vb
Dim urlContents As String = Await getStringTask
```

<span data-ttu-id="22930-170">次の図は `client.GetStringAsync` から `getStringTask` への割り当てへの制御フロー、および `getStringTask` の作成から Await 演算子のアプリケーションへの制御フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="22930-170">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>

<span data-ttu-id="22930-171">![手順 3.](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span><span class="sxs-lookup"><span data-stu-id="22930-171">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

<span data-ttu-id="22930-172">await 式は `AccessTheWebAsync` が制御を返すまで `client.GetStringAsync` を中断します。</span><span class="sxs-lookup"><span data-stu-id="22930-172">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="22930-173">その間、コントロールは `AccessTheWebAsync` の呼び出し元である `startButton_Click` に戻されます。</span><span class="sxs-lookup"><span data-stu-id="22930-173">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="22930-174">通常、直ちに非同期メソッドへの呼び出しの待機状態となります。</span><span class="sxs-lookup"><span data-stu-id="22930-174">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="22930-175">たとえば、次の割り当てで、`getStringTask` を作成してそれを待機する前のコードを置き換えることができます: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="22930-175">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>
>
> <span data-ttu-id="22930-176">このトピックでは、await 演算子が後で適用され、プログラムでの制御フローを示す出力行を格納します。</span><span class="sxs-lookup"><span data-stu-id="22930-176">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="22930-177">手順 4.</span><span class="sxs-lookup"><span data-stu-id="22930-177">Step FOUR</span></span>

<span data-ttu-id="22930-178">`AccessTheWebAsync` の宣言された戻り値の型は、`Task(Of Integer)` です。</span><span class="sxs-lookup"><span data-stu-id="22930-178">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="22930-179">したがって、`AccessTheWebAsync` が中断されると、`startButton_Click` に整数のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="22930-179">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="22930-180">返されたタスクは `getStringTask` ではないことに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22930-180">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="22930-181">返されたタスクは、中断されたメソッド `AccessTheWebAsync` での未処理を表す、整数の新しいタスクです。</span><span class="sxs-lookup"><span data-stu-id="22930-181">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="22930-182">これにより、タスクが完了したときに `AccessTheWebAsync` が整数を生成することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="22930-182">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="22930-183">次のステートメントはこのタスクを `getLengthTask` 変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="22930-183">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

<span data-ttu-id="22930-184">`AccessTheWebAsync` と同様に、`startButton_Click` は、非同期タスク (`getLengthTask`) の結果に依存しない処理を、タスクが待機するまで続行できます。</span><span class="sxs-lookup"><span data-stu-id="22930-184">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="22930-185">次の出力行はその処理を表します。</span><span class="sxs-lookup"><span data-stu-id="22930-185">The following output lines represent that work:</span></span>

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

<span data-ttu-id="22930-186">`startButton_Click` が待機すると、`getLengthTask` の進行は中断します。</span><span class="sxs-lookup"><span data-stu-id="22930-186">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="22930-187">次の代入ステートメントは、`startButton_Click` が完了するまで `AccessTheWebAsync` を中断します。</span><span class="sxs-lookup"><span data-stu-id="22930-187">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="22930-188">次の図で、矢印は `AccessTheWebAsync` の await 式から `getLengthTask` への値の割り当てへの制御のフロー、および `startButton_Click` が待機するまでの `getLengthTask` の通常の処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="22930-188">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

<span data-ttu-id="22930-189">![手順 4.](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="22930-189">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="22930-190">手順 5.</span><span class="sxs-lookup"><span data-stu-id="22930-190">Step FIVE</span></span>

<span data-ttu-id="22930-191">`client.GetStringAsync` が終了を通知すると、`AccessTheWebAsync` の処理は中断から解放され、await ステートメントを越えて続行できます。</span><span class="sxs-lookup"><span data-stu-id="22930-191">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="22930-192">次の出力行は、処理の再開を表します。</span><span class="sxs-lookup"><span data-stu-id="22930-192">The following lines of output represent the resumption of processing:</span></span>

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

<span data-ttu-id="22930-193">return ステートメントのオペランド `urlContents.Length` は `AccessTheWebAsync` が返すタスクに格納されます。</span><span class="sxs-lookup"><span data-stu-id="22930-193">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="22930-194">await 式はその値を `getLengthTask` の `startButton_Click` から取得します。</span><span class="sxs-lookup"><span data-stu-id="22930-194">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

<span data-ttu-id="22930-195">次の図は、`client.GetStringAsync` (および `getStringTask`) が完了した後の制御の移動を示します。</span><span class="sxs-lookup"><span data-stu-id="22930-195">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

<span data-ttu-id="22930-196">![手順 5.](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="22930-196">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

<span data-ttu-id="22930-197">`AccessTheWebAsync` は完了するまで実行され、完了を待機していた `startButton_Click` に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="22930-197">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="22930-198">手順 6.</span><span class="sxs-lookup"><span data-stu-id="22930-198">Step SIX</span></span>

<span data-ttu-id="22930-199">`AccessTheWebAsync` が終了を通知すると、処理は `startButton_Async` の await ステートメントを越えて続行できます。</span><span class="sxs-lookup"><span data-stu-id="22930-199">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="22930-200">実際、プログラムはそれ以上行うことがありません。</span><span class="sxs-lookup"><span data-stu-id="22930-200">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="22930-201">次の出力行は、`startButton_Async` の処理の再開を表します。</span><span class="sxs-lookup"><span data-stu-id="22930-201">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

<span data-ttu-id="22930-202">await 式は `getLengthTask` から `AccessTheWebAsync` の return ステートメントのオペランドである整数値を取得します。</span><span class="sxs-lookup"><span data-stu-id="22930-202">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="22930-203">次のステートメントはその値を `contentLength` 変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="22930-203">The following statement assigns that value to the `contentLength` variable.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="22930-204">次の図は `AccessTheWebAsync` から `startButton_Click` に制御が戻ることを示しています。</span><span class="sxs-lookup"><span data-stu-id="22930-204">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

<span data-ttu-id="22930-205">![手順 6.](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="22930-205">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="22930-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="22930-206">See also</span></span>

- [<span data-ttu-id="22930-207">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22930-207">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="22930-208">非同期の戻り値の型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22930-208">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="22930-209">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22930-209">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="22930-210">Async Sample:非同期プログラムにおける制御フロー (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22930-210">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
