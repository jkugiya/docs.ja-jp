---
description: '詳細情報: 方法:コマンド ライン コンパイラを起動する (Visual Basic)'
title: '方法: コマンド ライン コンパイラを起動する'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: aca8fe70e252ae9e7fb06f740ce5b7f3c8ca3d5d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470214"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="7d181-103">方法: コマンド ライン コンパイラを起動する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d181-103">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="7d181-104">コマンド ライン コンパイラを起動するには、実行可能ファイルの名前をコマンド ライン (MS-DOS プロンプトとも呼ばれます) に入力します。</span><span class="sxs-lookup"><span data-stu-id="7d181-104">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="7d181-105">既定の Windows コマンド プロンプトからコンパイルする場合は、実行可能ファイルへの完全修飾パスを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d181-105">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="7d181-106">この既定の動作をオーバーライドするには、Visual Studio の開発者コマンド プロンプトを使用するか、または PATH 環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="7d181-106">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="7d181-107">どちらの方法でも、コンパイラ名を入力するだけで、任意のディレクトリからコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="7d181-107">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="7d181-108">Visual Studio の開発者コマンド プロンプトを使用してコンパイラを起動するには</span><span class="sxs-lookup"><span data-stu-id="7d181-108">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="7d181-109">Microsoft Visual Studio プログラム グループ内の Visual Studio Tools プログラム フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7d181-109">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="7d181-110">Visual Studio がインストールされている場合は、Visual Studio の開発者コマンド プロンプトを使用して、ご使用のマシン上の任意のディレクトリからコンパイラにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7d181-110">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="7d181-111">Visual Studio の開発者コマンド プロンプトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7d181-111">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="7d181-112">コマンド ラインで「`vbc.exe` *sourceFileName*」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7d181-112">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="7d181-113">たとえば、ソース コードを `SourceFiles` という名前のディレクトリに保存した場合は、コマンド プロンプトを開き「`cd SourceFiles`」と入力して、そのディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="7d181-113">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="7d181-114">ディレクトリに `Source.vb` という名前のソース ファイルが含まれている場合は、「`vbc.exe Source.vb`」と入力してコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="7d181-114">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="7d181-115">Windows のコマンド プロンプト用のコンパイラに PATH 環境変数を設定するには</span><span class="sxs-lookup"><span data-stu-id="7d181-115">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="7d181-116">Windows 検索機能を使用して、ローカル ディスクで Vbc.exe を検索します。</span><span class="sxs-lookup"><span data-stu-id="7d181-116">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="7d181-117">コンパイラが配置されているディレクトリの正確な名前は、Windows ディレクトリの場所とインストールされている ".NET Framework" のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="7d181-117">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="7d181-118">".NET Framework" の複数のバージョンがインストールされている場合は、使用するバージョン (通常は最新バージョン) を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d181-118">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="7d181-119">**[スタート]** メニューから、 **[マイ コンピューター]** を右クリックし、ショートカット メニューから **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d181-119">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="7d181-120">**[詳細設定]** タブをクリックし、 **[環境変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d181-120">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="7d181-121">**[システム変数]** ペインで、一覧から **[パス]** を選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d181-121">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="7d181-122">**[システム変数の編集]** ダイアログ ボックスで、挿入ポイントを **[変数値]** フィールドの文字列の末尾に移動し、セミコロン (;) の後に手順 1 で見つかった完全なディレクトリ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d181-122">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="7d181-123">**[OK]** をクリックして、編集内容を確認し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d181-123">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="7d181-124">PATH 環境変数を変更すると、コンピューター上の任意のディレクトリから Windows コマンド プロンプトで Visual Basic コンパイラを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7d181-124">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="7d181-125">Windows のコマンド プロンプトを使用してコンパイラを起動するには</span><span class="sxs-lookup"><span data-stu-id="7d181-125">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="7d181-126">**[スタート]** メニューから、 **[アクセサリ]** フォルダーをクリックし、 **[Windows コマンドプロンプト]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="7d181-126">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="7d181-127">コマンド ラインで「`vbc.exe`*sourceFileName*」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7d181-127">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="7d181-128">たとえば、ソース コードを `SourceFiles` という名前のディレクトリに保存した場合は、コマンド プロンプトを開き「`cd SourceFiles`」と入力して、そのディレクトリに変更します。</span><span class="sxs-lookup"><span data-stu-id="7d181-128">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="7d181-129">ディレクトリに `Source.vb` という名前のソース ファイルが含まれている場合は、「`vbc.exe Source.vb`」と入力してコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="7d181-129">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d181-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d181-130">See also</span></span>

- [<span data-ttu-id="7d181-131">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="7d181-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7d181-132">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="7d181-132">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
