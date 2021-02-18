---
description: '詳細情報: -optioninfer'
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: d45761914612a28788cc5c1a848d92238f05c162
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475917"
---
# <a name="-optioninfer"></a><span data-ttu-id="2258f-103">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="2258f-103">-optioninfer</span></span>

<span data-ttu-id="2258f-104">変数宣言でローカル型推論を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2258f-104">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2258f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2258f-105">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2258f-106">引数</span><span class="sxs-lookup"><span data-stu-id="2258f-106">Arguments</span></span>  
  
|<span data-ttu-id="2258f-107">用語</span><span class="sxs-lookup"><span data-stu-id="2258f-107">Term</span></span>|<span data-ttu-id="2258f-108">定義</span><span class="sxs-lookup"><span data-stu-id="2258f-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="2258f-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2258f-109">`+` &#124; `-`</span></span>|<span data-ttu-id="2258f-110">任意。</span><span class="sxs-lookup"><span data-stu-id="2258f-110">Optional.</span></span> <span data-ttu-id="2258f-111">`-optioninfer+` を指定してローカル型推論を有効にするか、または `-optioninfer-` を指定してローカル型推論をブロックします。</span><span class="sxs-lookup"><span data-stu-id="2258f-111">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="2258f-112">`-optioninfer` オプションは、何も値を指定しない場合、`-optioninfer+` と同じです。</span><span class="sxs-lookup"><span data-stu-id="2258f-112">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="2258f-113">`-optioninfer` スイッチが存在しない場合の既定値も `-optioninfer+` です。</span><span class="sxs-lookup"><span data-stu-id="2258f-113">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="2258f-114">既定値は、Vbc.rsp 応答ファイル内に設定されています。</span><span class="sxs-lookup"><span data-stu-id="2258f-114">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2258f-115">`-noconfig` オプションを使用すると、vbc.rsp に指定するのではなく、コンパイラの内部既定値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="2258f-115">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="2258f-116">このオプションのコンパイラの既定値は `-optioninfer-` です。</span><span class="sxs-lookup"><span data-stu-id="2258f-116">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2258f-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="2258f-117">Remarks</span></span>  

 <span data-ttu-id="2258f-118">ソース コード ファイルに [Option Infer](../../language-reference/statements/option-infer-statement.md) ステートメントが含まれている場合、そのステートメントによって `-optioninfer` コマンド ライン コンパイラ設定がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="2258f-118">If the source code file contains an [Option Infer Statement](../../language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="2258f-119">Visual Studio IDE で -optioninfer を設定するには</span><span class="sxs-lookup"><span data-stu-id="2258f-119">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="2258f-120">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="2258f-120">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="2258f-121">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2258f-121">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="2258f-122">**[コンパイル]** タブで、 **[Option infer]** ボックスの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="2258f-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2258f-123">例</span><span class="sxs-lookup"><span data-stu-id="2258f-123">Example</span></span>  

 <span data-ttu-id="2258f-124">次のコードは、ローカル型推論を有効にした状態で `test.vb` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2258f-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2258f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="2258f-125">See also</span></span>

- [<span data-ttu-id="2258f-126">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="2258f-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2258f-127">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="2258f-127">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="2258f-128">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="2258f-128">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="2258f-129">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="2258f-129">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="2258f-130">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="2258f-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="2258f-131">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="2258f-131">Option Infer Statement</span></span>](../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="2258f-132">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="2258f-132">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- <span data-ttu-id="2258f-133">[[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="2258f-133">[Visual Basic Defaults, Projects, Options Dialog Box](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
- <span data-ttu-id="2258f-134">[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="2258f-134">[Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span></span>
- [<span data-ttu-id="2258f-135">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2258f-135">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="2258f-136">コマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="2258f-136">Building from the Command Line</span></span>](building-from-the-command-line.md)
