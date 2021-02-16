---
description: '詳細情報: チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)'
title: 'チュートリアル: Async と Await を使用した Web へのアクセス'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 08488d4909e4fbc40cc11213eb293c2693fdec71
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474162"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="d56ba-103">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56ba-103">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="d56ba-104">async/await 機能を使用することで、非同期プログラムをより簡単かつ直感的に記述できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-104">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="d56ba-105">同期コードに似た非同期コードを記述し、通常の非同期コードが必要とする難しいコールバック関数や継続の処理をコンパイラに任せます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-105">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="d56ba-106">非同期機能の詳細については、「[Async および Await を使用した非同期プログラミング (Visual Basic)](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-106">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="d56ba-107">このチュートリアルは、Web サイトの一覧でのバイト数の合計を計算する同期 Windows Presentation Foundation (WPF) アプリケーションから開始します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-107">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="d56ba-108">その後、新しい機能を使用して、アプリケーションを非同期ソリューションに変換します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-108">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="d56ba-109">自分でアプリケーションを作成しない場合は、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)のページから、"非同期サンプル: Web へのアクセスのチュートリアル (C# および Visual Basic)" をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-109">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="d56ba-110">このチュートリアルでは、次のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="d56ba-110">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="d56ba-111">WPF アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d56ba-111">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="d56ba-112">単純な WPF MainWindow をデザインする</span><span class="sxs-lookup"><span data-stu-id="d56ba-112">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="d56ba-113">参照を追加する</span><span class="sxs-lookup"><span data-stu-id="d56ba-113">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="d56ba-114">必要な Imports ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="d56ba-114">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="d56ba-115">同期アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d56ba-115">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="d56ba-116">同期ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="d56ba-116">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="d56ba-117">GetURLContents を非同期メソッドに変換する</span><span class="sxs-lookup"><span data-stu-id="d56ba-117">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="d56ba-118">SumPageSizes を非同期メソッドに変換する</span><span class="sxs-lookup"><span data-stu-id="d56ba-118">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="d56ba-119">startButton_Click を非同期メソッドに変換する</span><span class="sxs-lookup"><span data-stu-id="d56ba-119">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="d56ba-120">非同期ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="d56ba-120">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="d56ba-121">GetURLContentsAsync メソッドを .NET Framework メソッドに置き換える</span><span class="sxs-lookup"><span data-stu-id="d56ba-121">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="d56ba-122">非同期のコード例全体については、「[例](#example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-122">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d56ba-123">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d56ba-123">Prerequisites</span></span>

<span data-ttu-id="d56ba-124">お使いのコンピューターに、Visual Studio 2012 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d56ba-124">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="d56ba-125">詳細については、Visual Studio の[ダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-125">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="d56ba-126">WPF アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d56ba-126">Create a WPF application</span></span>

1. <span data-ttu-id="d56ba-127">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-127">Start Visual Studio.</span></span>

2. <span data-ttu-id="d56ba-128">メニュー バーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-128">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="d56ba-129">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-129">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="d56ba-130">**[インストールされたテンプレート]** ペインで、[Visual Basic] を選択し、プロジェクトの種類の一覧で **[WPF アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-130">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="d56ba-131">**[名前]** ボックスに「`AsyncExampleWPF`」と入力して、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-131">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="d56ba-132">**ソリューション エクスプローラー** に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-132">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="d56ba-133">単純な WPF MainWindow をデザインする</span><span class="sxs-lookup"><span data-stu-id="d56ba-133">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="d56ba-134">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-134">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="d56ba-135">**[ツールボックス]** ウィンドウが表示されていない場合は、 **[表示]** メニューを開き、 **[ツールボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-135">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="d56ba-136">**[Button]** コントロールと **[TextBox]** コントロールを **[MainWindow]** ウィンドウに追加します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-136">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="d56ba-137">**[TextBox]** コントロールを強調表示し、 **[プロパティ]** ウィンドウで次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-137">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="d56ba-138">**[Name]** プロパティを `resultsTextBox` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-138">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="d56ba-139">**[Height]** プロパティを 250 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-139">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="d56ba-140">**[Width]** プロパティを 500 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-140">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="d56ba-141">**[テキスト]** タブで、Lucida Console や Global Monospace などの等幅フォントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-141">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="d56ba-142">**[Button]** コントロールを強調表示し、 **[プロパティ]** ウィンドウで次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-142">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="d56ba-143">**[Name]** プロパティを `startButton` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-143">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="d56ba-144">**[Content]** プロパティの値を **[Button]** から **[Start]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-144">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="d56ba-145">テキスト ボックスとボタンの位置を調整し、両方が **[MainWindow]** ウィンドウ内に表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-145">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="d56ba-146">WPF XAML デザイナーについて詳しくは、「[XAML デザイナーを使用した UI の作成](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-146">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="d56ba-147">参照を追加する</span><span class="sxs-lookup"><span data-stu-id="d56ba-147">Add a reference</span></span>

1. <span data-ttu-id="d56ba-148">**ソリューション エクスプローラー** で、プロジェクトの名前を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-148">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="d56ba-149">メニュー バーで、 **[プロジェクト]** 、 **[参照の追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-149">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="d56ba-150">**[参照マネージャー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-150">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="d56ba-151">ダイアログ ボックスの上部で、プロジェクトのターゲットが .NET Framework 4.5 以上であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-151">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="d56ba-152">**[アセンブリ]** で、 **[フレームワーク]** を選択します (選択されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="d56ba-152">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="d56ba-153">名前の一覧で、 **[System.Net.Http]** のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-153">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="d56ba-154">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-154">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="d56ba-155">必要な Imports ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="d56ba-155">Add necessary Imports statements</span></span>

1. <span data-ttu-id="d56ba-156">**ソリューション エクスプローラー** で MainWindow.xaml.vb のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-156">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="d56ba-157">次の `Imports` ステートメントが存在しない場合は、コード ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-157">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="d56ba-158">同期アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d56ba-158">Create a synchronous application</span></span>

1. <span data-ttu-id="d56ba-159">デザイン ウィンドウの MainWindow.xaml で、 **[Start]** ボタンをダブルクリックして、MainWindow.xaml.vb に `startButton_Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-159">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="d56ba-160">MainWindow.xaml.vb で、次のコードを `startButton_Click` の本文にコピーします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-160">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="d56ba-161">このコードは、`SumPageSizes` アプリケーションを実行するメソッドを呼び出し、`startButton_Click` に制御が戻るとメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-161">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="d56ba-162">同期ソリューションのコードには、次の 4 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-162">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="d56ba-163">`SumPageSizes` は、`SetUpURLList` から Web ページ URL のリストを取得し、`GetURLContents` と `DisplayResults` を呼び出して各 URL を処理します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-163">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="d56ba-164">`SetUpURLList` は、Web アドレスのリストを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-164">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="d56ba-165">`GetURLContents` は、各 Web サイトのコンテンツをダウンロードし、バイト配列としてそのコンテンツを返します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-165">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="d56ba-166">`DisplayResults` は、各 URL のバイト配列内のバイト数を表示します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-166">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="d56ba-167">次の 4 つのメソッドをコピーし、それを MainWindow.xaml.vb の `startButton_Click` イベント ハンドラーの下に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-167">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="d56ba-168">同期ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="d56ba-168">Test the synchronous solution</span></span>

1. <span data-ttu-id="d56ba-169">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-169">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="d56ba-170">次の一覧のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-170">Output that resembles the following list should appear:</span></span>

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    <span data-ttu-id="d56ba-171">カウントの表示には数秒かかる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-171">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="d56ba-172">その間、要求されたリソースのダウンロードが完了するまで UI スレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-172">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="d56ba-173">このため、 **[Start]** ボタンのクリック後は、表示ウィンドウの移動、最大化、最小化のほか、閉じることさえできなくなります。</span><span class="sxs-lookup"><span data-stu-id="d56ba-173">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="d56ba-174">バイト カウントの表示が開始するまでは、これらの操作を実行しても失敗します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-174">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="d56ba-175">Web サイトが応答していない場合、どのサイトに問題があるのかを示す情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="d56ba-175">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="d56ba-176">待つのをやめて、プログラムを閉じることさえ難しい状態になります。</span><span class="sxs-lookup"><span data-stu-id="d56ba-176">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="d56ba-177">GetURLContents を非同期メソッドに変換する</span><span class="sxs-lookup"><span data-stu-id="d56ba-177">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="d56ba-178">同期ソリューションを非同期ソリューションに変換する際に、最初に取りかかるのに最適な場所は、`GetURLContents` 内です。その理由は、<xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> メソッドおよび <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> メソッドへの呼び出しで、アプリケーションが Web にアクセスするためです。</span><span class="sxs-lookup"><span data-stu-id="d56ba-178">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="d56ba-179">.NET Framework には両方のメソッドの非同期バージョンが用意されているため、変換は簡単です。</span><span class="sxs-lookup"><span data-stu-id="d56ba-179">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="d56ba-180">`GetURLContents` で使用されているメソッドの詳細については、「<xref:System.Net.WebRequest>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-180">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d56ba-181">このチュートリアルの手順に従っていると、いくつかのコンパイラ エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-181">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="d56ba-182">これらのエラーは無視することで、チュートリアルを続行できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-182">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="d56ba-183">`GetURLContents` の 3 行目で呼び出されるメソッドを、`GetResponse` から、非同期でタスク ベースの <xref:System.Net.WebRequest.GetResponseAsync%2A> メソッドに変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-183">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="d56ba-184">`GetResponseAsync` は、<xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-184">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d56ba-185">この場合、*タスク戻り変数* の `TResult` の型は <xref:System.Net.WebResponse> です。</span><span class="sxs-lookup"><span data-stu-id="d56ba-185">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="d56ba-186">このタスクは、要求されたデータのダウンロードが完了し、タスクが最後まで実行された後に、実際の `WebResponse` オブジェクトを生成するという約束です。</span><span class="sxs-lookup"><span data-stu-id="d56ba-186">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="d56ba-187">タスクから `WebResponse` 値を取得するには、次のコードに示すように、[Await](../../../language-reference/operators/await-operator.md) 演算子を `GetResponseAsync` への呼び出しに適用します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-187">To retrieve the `WebResponse` value from the task, apply an [Await](../../../language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="d56ba-188">`Await` 演算子は、現在のメソッド、`GetURLContents` の実行を、待機しているタスクが完了するまで中断します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-188">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="d56ba-189">その間、現在のメソッドの呼び出し元に制御が戻されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-189">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="d56ba-190">この例では、現在のメソッドが `GetURLContents` で、呼び出し元が `SumPageSizes` です。</span><span class="sxs-lookup"><span data-stu-id="d56ba-190">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="d56ba-191">タスクが完了すると、約束されていた `WebResponse` オブジェクトが完了したタスクの値として生成され、変数 `response` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-191">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="d56ba-192">上記のステートメントは、動作を明確にするため、次の 2 つのステートメントに分割できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-192">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="d56ba-193">`webReq.GetResponseAsync` への呼び出しによって、`Task(Of WebResponse)` または `Task<WebResponse>` が返されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-193">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="d56ba-194">その後、`WebResponse` 値を取得するため、タスクに `Await` 演算子が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-194">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="d56ba-195">非同期メソッドにタスクの完了に依存しない処理がある場合、メソッドはこれら 2 つのステートメントの間、つまり非同期メソッドへの呼び出しから、await 演算子の適用までの間にその処理を続行することができます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-195">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="d56ba-196">たとえば、「[方法:Async と Await を使用して複数の Web 要求を並列実行する (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)」および「[方法: Task.WhenAll を使用して非同期のチュートリアルを拡張する (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-196">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="d56ba-197">前の手順で `Await` 演算子を追加したため、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-197">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="d56ba-198">この演算子は、[Async](../../../language-reference/modifiers/async.md) 修飾子でマークされているメソッドでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-198">The operator can be used only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="d56ba-199">`CopyTo` への呼び出しを `CopyToAsync` への呼び出しに置き換える変換手順を繰り返す間は、エラーを無視してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-199">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="d56ba-200">呼び出されるメソッドの名前を <xref:System.IO.Stream.CopyToAsync%2A> に変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-200">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="d56ba-201">`CopyTo` または `CopyToAsync` メソッドは、その引数 `content` にバイトをコピーし、意味のある値は返しません。</span><span class="sxs-lookup"><span data-stu-id="d56ba-201">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="d56ba-202">同期バージョンでは、`CopyTo` への呼び出しは値を返さない単純なステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d56ba-202">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="d56ba-203">非同期バージョンでは、`CopyToAsync` は <xref:System.Threading.Tasks.Task> を返します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-203">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d56ba-204">タスクは "Task(void)" のように機能し、メソッドを待機できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-204">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="d56ba-205">次のコードに示すように、`Await` または `await` を、`CopyToAsync` への呼び出しに適用します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-205">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="d56ba-206">上記のステートメントでは、次の 2 行のコードを省略しています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-206">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="d56ba-207">`GetURLContents` 内で必要な作業として残っているのは、メソッド シグネチャの調整のみです。</span><span class="sxs-lookup"><span data-stu-id="d56ba-207">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="d56ba-208">`Await` 演算子は、[Async](../../../language-reference/modifiers/async.md) 修飾子でマークされているメソッドでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-208">You can use the `Await` operator only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="d56ba-209">次のコードに示すように、修飾子を追加し、メソッドを *非同期メソッド* としてマークします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-209">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="d56ba-210">非同期メソッドの戻り値の型は、<xref:System.Threading.Tasks.Task> と <xref:System.Threading.Tasks.Task%601> のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-210">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d56ba-211">Visual Basic でのメソッドは、`Task` または `Task(Of T)` を返す `Function` にするか、`Sub` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d56ba-211">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="d56ba-212">通常、`Sub` メソッドは、`Sub` を必要とする非同期イベント ハンドラーでのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-212">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="d56ba-213">それ以外のケースでは、完成したメソッドに、T 型の値を返す [Return](../../../language-reference/statements/return-statement.md) ステートメントが含まれる場合は `Task(T)` を使用し、完成したメソッドが意味のある値を返さない場合は `Task` を使用します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-213">In other cases, you use `Task(T)` if the completed method has a [Return](../../../language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="d56ba-214">詳細については、「[非同期の戻り値の型 (Visual Basic)](async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-214">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

    <span data-ttu-id="d56ba-215">メソッド `GetURLContents` には return ステートメントがあり、このステートメントはバイト配列を返します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-215">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="d56ba-216">そのため、非同期バージョンの戻り値の型は Task(T) であり、T はバイト配列です。</span><span class="sxs-lookup"><span data-stu-id="d56ba-216">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="d56ba-217">メソッド シグネチャに、次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-217">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="d56ba-218">戻り値の型を `Task(Of Byte())` に変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-218">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="d56ba-219">規則により、非同期メソッドは "Async" で終わる名前を持つことになっているため、メソッドの名前を `GetURLContentsAsync` に変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-219">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="d56ba-220">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-220">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="d56ba-221">このいくつかの変更によって、`GetURLContents` の非同期メソッドへの変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d56ba-221">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="d56ba-222">SumPageSizes を非同期メソッドに変換する</span><span class="sxs-lookup"><span data-stu-id="d56ba-222">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="d56ba-223">`SumPageSizes` に対して、前述した手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-223">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="d56ba-224">まずは、`GetURLContents` への呼び出しを非同期呼び出しに変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-224">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="d56ba-225">呼び出されるメソッドの名前を `GetURLContents` から `GetURLContentsAsync` に変更します (まだ変更していない場合)。</span><span class="sxs-lookup"><span data-stu-id="d56ba-225">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="d56ba-226">バイト配列値を取得するために、`Await` を、`GetURLContentsAsync` が返すタスクに適用します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-226">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="d56ba-227">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-227">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="d56ba-228">上記の割り当てでは、次の 2 行のコードを省略しています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-228">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="d56ba-229">メソッドのシグネチャに、次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-229">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="d56ba-230">メソッドを `Async` 修飾子でマークします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-230">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="d56ba-231">メソッド名に "Async" を追加します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-231">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="d56ba-232">今回、タスク戻り変数の T がない理由は、`SumPageSizesAsync` が T のための値を返さないからです (メソッドに `Return` ステートメントがありません)。ただし、メソッドは待機可能になるために `Task` を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d56ba-232">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="d56ba-233">そのため、メソッドの型を `Sub` から `Function` に変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-233">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="d56ba-234">関数の戻り値の型は、`Task` です。</span><span class="sxs-lookup"><span data-stu-id="d56ba-234">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="d56ba-235">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-235">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="d56ba-236">`SumPageSizes` から `SumPageSizesAsync` への変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d56ba-236">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="d56ba-237">startButton_Click を非同期メソッドに変換する</span><span class="sxs-lookup"><span data-stu-id="d56ba-237">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="d56ba-238">イベント ハンドラーで、呼び出されるメソッドの名前を `SumPageSizes` から `SumPageSizesAsync` に変更します (まだ変更していない場合)。</span><span class="sxs-lookup"><span data-stu-id="d56ba-238">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="d56ba-239">`SumPageSizesAsync` は非同期メソッドであるため、結果を待機するイベント ハンドラーのコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-239">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="d56ba-240">`SumPageSizesAsync` への呼び出しは、`GetURLContentsAsync` の `CopyToAsync` への呼び出しに似ています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-240">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="d56ba-241">この呼び出しによって、`Task(T)` ではなく `Task` が返されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-241">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="d56ba-242">前述した手順と同様に、1 つまたは 2 つのステートメントを使用して、呼び出しを変換できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-242">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="d56ba-243">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-243">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="d56ba-244">誤って操作が再入することを避けるために、次のステートメントを `startButton_Click` の先頭に追加して **[Start]** ボタンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-244">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="d56ba-245">イベント ハンドラーの末尾で、ボタンを再び有効にできます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-245">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="d56ba-246">再入の詳細については、「[非同期アプリにおける再入の処理 (Visual Basic)](handling-reentrancy-in-async-apps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-246">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="d56ba-247">最後に、`Async` 修飾子を宣言に追加し、イベント ハンドラーが `SumPagSizesAsync` を待機できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-247">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="d56ba-248">通常、イベント ハンドラーの名前は変更されません。</span><span class="sxs-lookup"><span data-stu-id="d56ba-248">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="d56ba-249">戻り値の型が `Task` に変更されていない理由は、イベント ハンドラーが、Visual Basic では `Sub` プロシージャになる必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="d56ba-249">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="d56ba-250">同期処理から非同期処理へのプロジェクトの変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d56ba-250">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="d56ba-251">非同期ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="d56ba-251">Test the asynchronous solution</span></span>

1. <span data-ttu-id="d56ba-252">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-252">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="d56ba-253">同期ソリューションの出力に似た出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-253">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="d56ba-254">ただし、次の相違点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d56ba-254">However, notice the following differences.</span></span>

    - <span data-ttu-id="d56ba-255">処理の完了後に、すべての結果が同時に表示されることはありません。</span><span class="sxs-lookup"><span data-stu-id="d56ba-255">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="d56ba-256">たとえば、両方のプログラムの `startButton_Click` には、テキスト ボックスをクリアする行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-256">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="d56ba-257">この目的は、実行ごとにテキスト ボックスをクリアすることです。1 つの結果セットが表示された後に、もう一度 **[Start]** ボタンをクリックすると、テキスト ボックスがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-257">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="d56ba-258">同期バージョンでは、2 回目のカウントが表示される直前、ダウンロードが完了して UI スレッドが他の処理を実行できる状態になったときにテキスト ボックスがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-258">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="d56ba-259">非同期バージョンでは、 **[Start]** ボタンをクリックした直後にテキスト ボックスがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-259">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="d56ba-260">最も重要な点は、ダウンロード中に UI スレッドがブロックされないことです。</span><span class="sxs-lookup"><span data-stu-id="d56ba-260">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="d56ba-261">Web リソースをダウンロード、カウント、および表示している間に、ウィンドウの移動やサイズ変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-261">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="d56ba-262">いずれかの Web サイトの処理が遅い、または応答しない場合、**閉じる** ボタン (右上隅の赤色のフィールドにある [x]) をクリックすることで、操作を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-262">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="d56ba-263">GetURLContentsAsync メソッドを .NET Framework メソッドに置き換える</span><span class="sxs-lookup"><span data-stu-id="d56ba-263">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="d56ba-264">.NET Framework では、使用できる非同期メソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-264">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="d56ba-265">その 1 つである、<xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> メソッドは、このチュートリアルに必要な処理だけを実行します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-265">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="d56ba-266">これを、前述の手順で作成した `GetURLContentsAsync` メソッドの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-266">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="d56ba-267">まずは、`SumPageSizesAsync` メソッドで <xref:System.Net.Http.HttpClient> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-267">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="d56ba-268">次の宣言をメソッドの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="d56ba-268">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="d56ba-269">`SumPageSizesAsync,` で、`GetURLContentsAsync` メソッドへの呼び出しを `HttpClient` メソッドへの呼び出しに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-269">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="d56ba-270">記述した `GetURLContentsAsync` メソッドを削除するかコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-270">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="d56ba-271">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="d56ba-271">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="d56ba-272">このバージョンのプロジェクトの動作は、「非同期ソリューションをテストするには」の手順で説明している動作と同じですが、さらに少ない手間で作成できます。</span><span class="sxs-lookup"><span data-stu-id="d56ba-272">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="d56ba-273">例</span><span class="sxs-lookup"><span data-stu-id="d56ba-273">Example</span></span>

<span data-ttu-id="d56ba-274">次に示したのは、非同期の `GetURLContentsAsync` メソッドを使用する変換後の非同期ソリューションのコード例全体です。</span><span class="sxs-lookup"><span data-stu-id="d56ba-274">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="d56ba-275">この例は、元の同期ソリューションと非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-275">Notice that it strongly resembles the original, synchronous solution.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
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

<span data-ttu-id="d56ba-276">次のコードには、`HttpClient` の `GetByteArrayAsync` メソッドを使用するソリューション例のすべてが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d56ba-276">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
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

## <a name="see-also"></a><span data-ttu-id="d56ba-277">関連項目</span><span class="sxs-lookup"><span data-stu-id="d56ba-277">See also</span></span>

- [<span data-ttu-id="d56ba-278">Async Sample:Web へのアクセスのチュートリアル (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56ba-278">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="d56ba-279">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="d56ba-279">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
- [<span data-ttu-id="d56ba-280">Async</span><span class="sxs-lookup"><span data-stu-id="d56ba-280">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="d56ba-281">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56ba-281">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="d56ba-282">非同期の戻り値の型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56ba-282">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="d56ba-283">タスク ベースの非同期プログラミング (TAP)</span><span class="sxs-lookup"><span data-stu-id="d56ba-283">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="d56ba-284">方法: Task.WhenAll を使用して非同期のチュートリアルを拡張する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56ba-284">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="d56ba-285">方法: Async と Await を使用して複数の Web 要求を並列実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d56ba-285">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
