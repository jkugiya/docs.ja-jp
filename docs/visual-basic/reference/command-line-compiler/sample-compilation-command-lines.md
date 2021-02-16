---
description: '詳細情報: コンパイル コマンド ラインのサンプル (Visual Basic)'
title: コンパイル コマンド ラインのサンプル
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: fbd35b7f12b3bee9690698a24dcb70d850081f95
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474006"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="c87d1-103">コンパイル コマンド ラインのサンプル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c87d1-103">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="c87d1-104">Visual Studio 内から Visual Basic プログラムをコンパイルする代わりに、コマンド ラインからコンパイルして、実行可能 (.exe) ファイルまたはダイナミックリンク ライブラリ (.dll) ファイルを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="c87d1-104">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="c87d1-105">Visual Basic のコマンドライン コンパイラでは、入力および出力ファイル、アセンブリ、デバッグおよびプリプロセッサ オプションを制御するオプションの完全なセットがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c87d1-105">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="c87d1-106">各オプションは、`-option` と `/option` の 2 つの交換可能な形式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c87d1-106">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="c87d1-107">このドキュメントでは、`-option` 形式のみを示します。</span><span class="sxs-lookup"><span data-stu-id="c87d1-107">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="c87d1-108">次の表に、自分で使用するために変更できるコマンド ラインのサンプルをいくつか一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c87d1-108">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="c87d1-109">終了</span><span class="sxs-lookup"><span data-stu-id="c87d1-109">To</span></span>|<span data-ttu-id="c87d1-110">使用</span><span class="sxs-lookup"><span data-stu-id="c87d1-110">Use</span></span>|
|--------|---------|
|<span data-ttu-id="c87d1-111">File.vb をコンパイルし、File.exe を作成する</span><span class="sxs-lookup"><span data-stu-id="c87d1-111">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="c87d1-112">File.vb をコンパイルし、File.dll を作成する</span><span class="sxs-lookup"><span data-stu-id="c87d1-112">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="c87d1-113">File.vb をコンパイルし、My.exe を作成する</span><span class="sxs-lookup"><span data-stu-id="c87d1-113">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="c87d1-114">File.vb をコンパイルし、ライブラリ、および File.dll という名前の参照アセンブリの両方を作成する</span><span class="sxs-lookup"><span data-stu-id="c87d1-114">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="c87d1-115">最適化を有効にし、`DEBUG` シンボルを定義して、現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルし、File2.exe を生成する</span><span class="sxs-lookup"><span data-stu-id="c87d1-115">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="c87d1-116">現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルし、ロゴや警告を表示せずに、File2.dll のデバッグ バージョンを生成する</span><span class="sxs-lookup"><span data-stu-id="c87d1-116">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="c87d1-117">現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルし、Something.dll に出力する</span><span class="sxs-lookup"><span data-stu-id="c87d1-117">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="c87d1-118">Visual Studio IDE を使用してプロジェクトをビルドする場合、関連する **vbc** コマンドに関する情報をそのコンパイラ オプションと共に出力ウィンドウに表示できます。</span><span class="sxs-lookup"><span data-stu-id="c87d1-118">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="c87d1-119">この情報を表示するには、[[オプション] ダイアログ ボックス、[プロジェクトおよびソリューション]、[ビルド/実行]](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run) の順に開き、 **[MSBuild プロジェクト ビルドの出力の詳細]** を **[通常]** またはそれ以上の詳細レベルに設定します。</span><span class="sxs-lookup"><span data-stu-id="c87d1-119">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="c87d1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c87d1-120">See also</span></span>

- [<span data-ttu-id="c87d1-121">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c87d1-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c87d1-122">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="c87d1-122">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
