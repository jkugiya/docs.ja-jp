---
description: '詳細情報: コード内のコメント (Visual Basic)'
title: コード内のコメント
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 66e12a18c2532bb5b694affccb84153f01bcddd5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461932"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="dc725-103">コード内のコメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc725-103">Comments in Code (Visual Basic)</span></span>

<span data-ttu-id="dc725-104">コード例にはコメント記号 (`'`) がしばしば見られます。</span><span class="sxs-lookup"><span data-stu-id="dc725-104">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="dc725-105">この記号は、後続のテキスト ("*コメント*") を無視するように Visual Basic コンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="dc725-105">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="dc725-106">コメントは、コードを読むユーザーに役立つように追加される簡単な説明です。</span><span class="sxs-lookup"><span data-stu-id="dc725-106">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="dc725-107">プロシージャの先頭に、そのプロシージャの機能の特性 (何を実行するか) について説明する簡単なコメントを常に配置するのは、推奨されるプログラミング方法です。</span><span class="sxs-lookup"><span data-stu-id="dc725-107">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="dc725-108">コードを作成した本人にとっても、コードを調べる他人にとっても、この説明は役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="dc725-108">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="dc725-109">実装の詳細 (プロシージャの実行手順) は、機能の特性を説明するコメントとは別に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc725-109">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="dc725-110">実装の詳細を記述に入れる場合は、関数を更新するときにその説明も更新してください。</span><span class="sxs-lookup"><span data-stu-id="dc725-110">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="dc725-111">同じ行のステートメントの後にコメントを入れたり、1 行全体をコメントにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="dc725-111">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="dc725-112">両方の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="dc725-112">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="dc725-113">コメントを複数行に記述する必要がある場合は、以下に例を示すとおりに、各行にコメント記号を記述します。</span><span class="sxs-lookup"><span data-stu-id="dc725-113">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="dc725-114">コメントのガイドライン</span><span class="sxs-lookup"><span data-stu-id="dc725-114">Commenting Guidelines</span></span>  

 <span data-ttu-id="dc725-115">次の表は、どの種類のコメントをコードのセクションの前に配置できるかに関する一般的なガイドラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="dc725-115">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="dc725-116">これらは推奨事項です。Visual Basic にはコメントの追加に関する規則はありません。</span><span class="sxs-lookup"><span data-stu-id="dc725-116">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="dc725-117">コードの作成者自身およびコードを読む他のユーザーに最適な内容を記述してください。</span><span class="sxs-lookup"><span data-stu-id="dc725-117">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="dc725-118">コメント タイプ</span><span class="sxs-lookup"><span data-stu-id="dc725-118">Comment type</span></span>|<span data-ttu-id="dc725-119">コメントの説明</span><span class="sxs-lookup"><span data-stu-id="dc725-119">Comment description</span></span>|  
|<span data-ttu-id="dc725-120">目的</span><span class="sxs-lookup"><span data-stu-id="dc725-120">Purpose</span></span>|<span data-ttu-id="dc725-121">プロシージャが行う内容 (手順ではありません) を説明します。</span><span class="sxs-lookup"><span data-stu-id="dc725-121">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="dc725-122">外部からの影響</span><span class="sxs-lookup"><span data-stu-id="dc725-122">Assumptions</span></span>|<span data-ttu-id="dc725-123">各外部変数、コントロール、開いているファイル、またはプロシージャからアクセスされるその他の要素の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="dc725-123">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="dc725-124">エフェクト</span><span class="sxs-lookup"><span data-stu-id="dc725-124">Effects</span></span>|<span data-ttu-id="dc725-125">影響を受ける外部変数、コントロール、またはファイル、およびその効果 (明白でない場合のみ) の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="dc725-125">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="dc725-126">受け取る値</span><span class="sxs-lookup"><span data-stu-id="dc725-126">Inputs</span></span>|<span data-ttu-id="dc725-127">引数の目的を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc725-127">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="dc725-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="dc725-128">Returns</span></span>|<span data-ttu-id="dc725-129">プロシージャから返される値について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc725-129">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="dc725-130">次のことに留意してください。</span><span class="sxs-lookup"><span data-stu-id="dc725-130">Remember the following points:</span></span>  
  
- <span data-ttu-id="dc725-131">重要な変数を宣言する場合は、宣言した変数の用途を説明するためのインライン コメントを必ず前に配置します。</span><span class="sxs-lookup"><span data-stu-id="dc725-131">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="dc725-132">コメントには複雑な実装の詳細だけを記述して済むように、変数、コントロール、およびプロシージャにはわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="dc725-132">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="dc725-133">同じ行の行連結シーケンスの後にコメントを付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="dc725-133">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="dc725-134">コード ブロックのコメント記号を追加または削除するには、1 行以上のコードを選択し、 **[編集]** ツールバーの **[コメント]** (![Visual Studio の Visual Basic の [コメント] ボタン](./media/comments-in-code/visual-basic-comment-button.gif)) および **[コメント解除]** (![Visual Studio の Visual Basic の [コメント解除] ボタン](./media/comments-in-code/visual-basic-uncomment-button.gif)) ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc725-134">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc725-135">テキストの前に `REM` キーワードを付けて、コードにコメントを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc725-135">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="dc725-136">ただし、`'` 記号および **[コメント]** / **[コメント解除]** ボタンの方が使いやすく、必要なスペースとメモリが少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="dc725-136">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc725-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc725-137">See also</span></span>

- [<span data-ttu-id="dc725-138">基本的な機能 - XML コメントによるコードの文書化</span><span class="sxs-lookup"><span data-stu-id="dc725-138">Basic Instincts - Documenting Your Code With XML Comments</span></span>](/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="dc725-139">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="dc725-139">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
- [<span data-ttu-id="dc725-140">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="dc725-140">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="dc725-141">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="dc725-141">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="dc725-142">REM ステートメント</span><span class="sxs-lookup"><span data-stu-id="dc725-142">REM Statement</span></span>](../../language-reference/statements/rem-statement.md)
