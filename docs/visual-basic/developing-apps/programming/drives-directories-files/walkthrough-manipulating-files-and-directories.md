---
description: '詳細情報: チュートリアル: Visual Basic によるファイルとディレクトリの操作'
title: ファイルとディレクトリの操作
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 315635ee43ee4d4956fc35b7f9bc635b374646f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775384"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="d94d5-103">チュートリアル : Visual Basic によるファイルとディレクトリの操作</span><span class="sxs-lookup"><span data-stu-id="d94d5-103">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>

<span data-ttu-id="d94d5-104">このチュートリアルでは、Visual Basic でのファイル I/O の基礎について概説します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-104">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="d94d5-105">具体的には、ディレクトリ内のテキスト ファイルをリストして調査する小さなアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-105">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="d94d5-106">このアプリケーションは、選択された各テキスト ファイルについて、ファイルの属性とコンテンツの最初の行を取得します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-106">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="d94d5-107">ログ ファイルに情報を書き込むオプションもあります。</span><span class="sxs-lookup"><span data-stu-id="d94d5-107">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="d94d5-108">このチュートリアルでは、Visual Basic で利用可能な、`My.Computer.FileSystem Object` のメンバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-108">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="d94d5-109">詳細については、「 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d94d5-109">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="d94d5-110">チュートリアルの最後では、<xref:System.IO> 名前空間のクラスを使用する同等の例を示します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-110">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="d94d5-111">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="d94d5-111">To create the project</span></span>  
  
1. <span data-ttu-id="d94d5-112">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-112">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="d94d5-113">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-113">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="d94d5-114">**[インストールされたテンプレート]** ペインで、**[Visual Basic]** を展開し、**[Windows]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-114">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="d94d5-115">中央の **[テンプレート]** ペインで、**[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-115">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="d94d5-116">**[名前]** ボックスに「`FileExplorer`」と入力してプロジェクト名を設定し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-116">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d94d5-117">Visual Studio の **ソリューション エクスプローラー** にプロジェクトが追加され、Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-117">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="d94d5-118">次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-118">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="d94d5-119">コントロール</span><span class="sxs-lookup"><span data-stu-id="d94d5-119">Control</span></span>|<span data-ttu-id="d94d5-120">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d94d5-120">Property</span></span>|<span data-ttu-id="d94d5-121">値</span><span class="sxs-lookup"><span data-stu-id="d94d5-121">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="d94d5-122">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="d94d5-122">**ListBox**</span></span>|<span data-ttu-id="d94d5-123">**名前**</span><span class="sxs-lookup"><span data-stu-id="d94d5-123">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="d94d5-124">**Button**</span><span class="sxs-lookup"><span data-stu-id="d94d5-124">**Button**</span></span>|<span data-ttu-id="d94d5-125">**名前**</span><span class="sxs-lookup"><span data-stu-id="d94d5-125">**Name**</span></span><br /><br /> <span data-ttu-id="d94d5-126">**Text**</span><span class="sxs-lookup"><span data-stu-id="d94d5-126">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="d94d5-127">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="d94d5-127">**Browse**</span></span>|  
    |<span data-ttu-id="d94d5-128">**Button**</span><span class="sxs-lookup"><span data-stu-id="d94d5-128">**Button**</span></span>|<span data-ttu-id="d94d5-129">**名前**</span><span class="sxs-lookup"><span data-stu-id="d94d5-129">**Name**</span></span><br /><br /> <span data-ttu-id="d94d5-130">**Text**</span><span class="sxs-lookup"><span data-stu-id="d94d5-130">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="d94d5-131">**調査**</span><span class="sxs-lookup"><span data-stu-id="d94d5-131">**Examine**</span></span>|  
    |<span data-ttu-id="d94d5-132">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="d94d5-132">**CheckBox**</span></span>|<span data-ttu-id="d94d5-133">**名前**</span><span class="sxs-lookup"><span data-stu-id="d94d5-133">**Name**</span></span><br /><br /> <span data-ttu-id="d94d5-134">**Text**</span><span class="sxs-lookup"><span data-stu-id="d94d5-134">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="d94d5-135">**結果の保存**</span><span class="sxs-lookup"><span data-stu-id="d94d5-135">**Save Results**</span></span>|  
    |<span data-ttu-id="d94d5-136">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="d94d5-136">**FolderBrowserDialog**</span></span>|<span data-ttu-id="d94d5-137">**名前**</span><span class="sxs-lookup"><span data-stu-id="d94d5-137">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="d94d5-138">フォルダーを選択し、フォルダー内のファイルをリストするには</span><span class="sxs-lookup"><span data-stu-id="d94d5-138">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="d94d5-139">フォーム上のコントロールをダブルクリックして、`browseButton` の `Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-139">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="d94d5-140">コード エディターが開きます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-140">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="d94d5-141">`Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-141">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="d94d5-142">`FolderBrowserDialog1.ShowDialog` 呼び出しにより、**[フォルダーの参照]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-142">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="d94d5-143">ユーザーが **[OK]** をクリックすると、次の手順で追加する `ListFiles` メソッドに <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> プロパティが引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-143">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="d94d5-144">次の `ListFiles` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-144">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="d94d5-145">このコードでは、まず最初に **ListBox** をクリアします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-145">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="d94d5-146">次に、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> メソッドによって、ディレクトリ内の各ファイルを表す文字列のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-146">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="d94d5-147">`GetFiles` メソッドは、検索パターンの引数を受け取り、特定のパターンに一致するファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-147">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="d94d5-148">この例では、拡張子 .txt が付いているファイルのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-148">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="d94d5-149">その後、`GetFiles` メソッドによって返された文字列が、**ListBox** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-149">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="d94d5-150">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-150">Run the application.</span></span> <span data-ttu-id="d94d5-151">**[参照]** をクリックし、</span><span class="sxs-lookup"><span data-stu-id="d94d5-151">Click the **Browse** button.</span></span> <span data-ttu-id="d94d5-152">**[フォルダーの参照]** ダイアログ ボックスで、.txt ファイルが含まれているフォルダーを参照し、そのフォルダーを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-152">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="d94d5-153">`ListBox` に、選択したフォルダー内のファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-153">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="d94d5-154">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-154">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="d94d5-155">テキスト ファイルからファイルの属性とコンテンツを取得するには</span><span class="sxs-lookup"><span data-stu-id="d94d5-155">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="d94d5-156">フォーム上のコントロールをダブルクリックして、`examineButton` の `Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-156">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="d94d5-157">`Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-157">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="d94d5-158">このコードは、`ListBox` で選択された項目を検証します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-158">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="d94d5-159">その後、`ListBox` からファイル パスのエントリを取得します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-159">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="d94d5-160"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> メソッドを使用して、ファイルがまだ存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-160">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="d94d5-161">ファイル パスは引数として `GetTextForOutput` メソッドに送られます (このメソッドは次の手順で追加します)。</span><span class="sxs-lookup"><span data-stu-id="d94d5-161">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="d94d5-162">このメソッドは、ファイル情報を含んだ文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-162">This method returns a string that contains file information.</span></span> <span data-ttu-id="d94d5-163">ファイル情報は、**MessageBox** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-163">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="d94d5-164">次の `GetTextForOutput` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-164">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="d94d5-165">このコードでは、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドを使用してファイル パラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-165">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="d94d5-166">ファイル パラメーターは、<xref:System.Text.StringBuilder> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-166">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="d94d5-167"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> メソッドは、ファイルの内容を <xref:System.IO.StreamReader> に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-167">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="d94d5-168">コンテンツの最初の行が `StreamReader` から取得され、`StringBuilder` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-168">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="d94d5-169">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-169">Run the application.</span></span> <span data-ttu-id="d94d5-170">**[参照]** をクリックし、.txt ファイルが含まれているフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-170">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="d94d5-171">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-171">Click **OK**.</span></span>  
  
     <span data-ttu-id="d94d5-172">`ListBox` でファイルを選択し、**[調査]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-172">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="d94d5-173">`MessageBox` にファイル情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-173">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="d94d5-174">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-174">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="d94d5-175">ログ エントリを追加するには</span><span class="sxs-lookup"><span data-stu-id="d94d5-175">To add a log entry</span></span>  
  
1. <span data-ttu-id="d94d5-176">`examineButton_Click` イベント ハンドラーの末尾に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-176">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="d94d5-177">このコードは、ログ ファイルのパスを設定して、選択したファイルと同じディレクトリにログ ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-177">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="d94d5-178">ログ エントリのテキストは現在の日付と時刻に設定され、その後にファイル情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-178">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="d94d5-179">`append` 引数を `True` に設定した <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使用して、ログ エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-179">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="d94d5-180">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-180">Run the application.</span></span> <span data-ttu-id="d94d5-181">テキスト ファイルを参照し、`ListBox` でファイルを選択して、**[結果の保存]** チェック ボックスをオンにした後、**[調査]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-181">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="d94d5-182">ログ エントリが `log.txt` ファイルに書き込まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-182">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="d94d5-183">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-183">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="d94d5-184">現在のディレクトリを使用するには</span><span class="sxs-lookup"><span data-stu-id="d94d5-184">To use the current directory</span></span>  
  
1. <span data-ttu-id="d94d5-185">フォームをダブルクリックして、`Form1_Load` のイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-185">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="d94d5-186">イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-186">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="d94d5-187">このコードは、フォルダー ブラウザーの既定のディレクトリを現在のディレクトリに設定します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-187">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="d94d5-188">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-188">Run the application.</span></span> <span data-ttu-id="d94d5-189">**[参照]** を最初にクリックすると、**[フォルダーの参照]** ダイアログ ボックスが開き、現在のディレクトリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d94d5-189">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="d94d5-190">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-190">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="d94d5-191">コントロールを選択的に有効化するには</span><span class="sxs-lookup"><span data-stu-id="d94d5-191">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="d94d5-192">次の `SetEnabled` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-192">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="d94d5-193">`SetEnabled` メソッドは、`ListBox` で項目が選択されているかどうかに応じて、コントロールを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="d94d5-193">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="d94d5-194">フォーム上の `ListBox` コントロールをダブルクリックして、`filesListBox` の `SelectedIndexChanged` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-194">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="d94d5-195">新しい `filesListBox_SelectedIndexChanged` イベント ハンドラーで、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-195">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="d94d5-196">`browseButton_Click` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-196">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="d94d5-197">`Form1_Load` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-197">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="d94d5-198">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-198">Run the application.</span></span> <span data-ttu-id="d94d5-199">`ListBox` で項目が選択されていない場合は、**[結果の保存**] チェック ボックスと **[調査]** ボタンが無効になります。</span><span class="sxs-lookup"><span data-stu-id="d94d5-199">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="d94d5-200">My.Computer.FileSystem を使用した完全な例</span><span class="sxs-lookup"><span data-stu-id="d94d5-200">Full example using My.Computer.FileSystem</span></span>  

 <span data-ttu-id="d94d5-201">完全な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d94d5-201">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="d94d5-202">System.IO を使用した完全な例</span><span class="sxs-lookup"><span data-stu-id="d94d5-202">Full example using System.IO</span></span>  

 <span data-ttu-id="d94d5-203">次に示す同等の例では、`My.Computer.FileSystem` オブジェクトではなく、<xref:System.IO> 名前空間のクラスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="d94d5-203">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="d94d5-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="d94d5-204">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="d94d5-205">チュートリアル: .NET Framework のメソッドによるファイル操作</span><span class="sxs-lookup"><span data-stu-id="d94d5-205">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](walkthrough-manipulating-files-by-using-net-framework-methods.md)
