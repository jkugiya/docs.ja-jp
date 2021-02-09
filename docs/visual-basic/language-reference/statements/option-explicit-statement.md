---
description: '詳細情報: Option Explicit ステートメント (Visual Basic)'
title: Option Explicit ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 11f59508125167fde98b4fc359dde7fd7c539b75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741615"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="b9112-103">Option Explicit ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9112-103">Option Explicit Statement (Visual Basic)</span></span>

<span data-ttu-id="b9112-104">ファイル内のすべての変数の明示的な宣言を強制させるか、変数の暗黙的な宣言を許可します。</span><span class="sxs-lookup"><span data-stu-id="b9112-104">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9112-105">構文</span><span class="sxs-lookup"><span data-stu-id="b9112-105">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="b9112-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="b9112-106">Parts</span></span>  

 `On`  
 <span data-ttu-id="b9112-107">任意。</span><span class="sxs-lookup"><span data-stu-id="b9112-107">Optional.</span></span> <span data-ttu-id="b9112-108">`Option Explicit` チェックを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b9112-108">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="b9112-109">`On` または `Off` が指定されていない場合、既定値は `On` になります。</span><span class="sxs-lookup"><span data-stu-id="b9112-109">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="b9112-110">任意。</span><span class="sxs-lookup"><span data-stu-id="b9112-110">Optional.</span></span> <span data-ttu-id="b9112-111">`Option Explicit` チェックを無効にします。</span><span class="sxs-lookup"><span data-stu-id="b9112-111">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9112-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9112-112">Remarks</span></span>  

 <span data-ttu-id="b9112-113">`Option Explicit On` または `Option Explicit` がファイルに含まれている場合、`Dim` または `ReDim` ステートメントを使用して、すべての変数を明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9112-113">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="b9112-114">宣言されていない変数名を使用しようとすると、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b9112-114">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="b9112-115">`Option Explicit Off` ステートメントを使用すると、変数の暗黙的な宣言を許可します。</span><span class="sxs-lookup"><span data-stu-id="b9112-115">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="b9112-116">使用した場合、`Option Explicit` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9112-116">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9112-117">`Option Explicit` を `Off` に設定することは、通常お勧めできません。</span><span class="sxs-lookup"><span data-stu-id="b9112-117">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="b9112-118">変数名のスペルを 1 か所以上間違えると、プログラムの実行時に予期しない結果を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9112-118">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="b9112-119">Option Explicit ステートメントが指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="b9112-119">When an Option Explicit Statement Is Not Present</span></span>  

 <span data-ttu-id="b9112-120">ソース コードに `Option Explicit` ステートメントが含まれていない場合は、[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) の **[Option Explicit]** 設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9112-120">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="b9112-121">コマンドライン コンパイラを使用している場合は、[-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9112-121">If the command-line compiler is used, the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="b9112-122">IDE の Option Explicit を設定するには</span><span class="sxs-lookup"><span data-stu-id="b9112-122">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="b9112-123">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="b9112-123">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="b9112-124">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9112-124">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="b9112-125">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9112-125">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="b9112-126">**[Option Explicit]** ボックスに値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b9112-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="b9112-127">新しいプロジェクトを作成すると、 **[コンパイル]** タブの **[Option Explicit]** 設定が **[VISUAL BASIC の既定値]** ダイアログ ボックスの **[Option Explicit]** 設定に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b9112-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="b9112-128">**[VISUAL BASIC の既定値]** ダイアログ ボックスにアクセスするには、 **[ツール]** メニューで **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9112-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="b9112-129">**[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9112-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="b9112-130">**[VISUAL BASIC の既定値]** の初期の既定値は `On` です。</span><span class="sxs-lookup"><span data-stu-id="b9112-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="b9112-131">コマンド ラインで Option Explicit を設定するには</span><span class="sxs-lookup"><span data-stu-id="b9112-131">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="b9112-132">**vbc** コマンドに [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) コンパイラ オプションを含めます。</span><span class="sxs-lookup"><span data-stu-id="b9112-132">Include the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9112-133">例</span><span class="sxs-lookup"><span data-stu-id="b9112-133">Example</span></span>  

 <span data-ttu-id="b9112-134">次の例では、`Option Explicit` ステートメントを使用して、すべての変数の明示的な宣言を強制しています。</span><span class="sxs-lookup"><span data-stu-id="b9112-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="b9112-135">宣言されていない変数を使用しようとすると、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b9112-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="b9112-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9112-136">See also</span></span>

- [<span data-ttu-id="b9112-137">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9112-137">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="b9112-138">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9112-138">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="b9112-139">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9112-139">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="b9112-140">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9112-140">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="b9112-141">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="b9112-141">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="b9112-142">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="b9112-142">-optionexplicit</span></span>](../../reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="b9112-143">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="b9112-143">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- <span data-ttu-id="b9112-144">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="b9112-144">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
