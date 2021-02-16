---
description: '詳細情報: 方法:コード内でステートメントを分割および連結する (Visual Basic)'
title: '方法: コード内でステートメントを分割および連結する'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 33a8b87171c4ee14e73ada564cff406637e96783
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475995"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="2294e-103">方法: コード内でステートメントを分割および連結する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2294e-103">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="2294e-104">コードを記述するときに、コード エディターで水平スクロールを必要とする長いステートメントを作成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2294e-104">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="2294e-105">これはコードの実行方法には影響しませんが、モニターに表示されたコードを読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="2294e-105">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="2294e-106">このような場合は、1 つの長いステートメントを複数の行に分割することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2294e-106">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="2294e-107">1 つのステートメントを複数の行に分割するには</span><span class="sxs-lookup"><span data-stu-id="2294e-107">To break a single statement into multiple lines</span></span>

<span data-ttu-id="2294e-108">行を分割する位置で行連結文字 (アンダースコア (`_`)) を使用します。</span><span class="sxs-lookup"><span data-stu-id="2294e-108">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="2294e-109">アンダースコアの直前にスペースを入力し、直後に行終端記号 (キャリッジ リターン) を入力するか、(バージョン 16.0 以降では) 直後にコメントを入力し、その後にキャリッジ リターンを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2294e-109">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2294e-110">場合によっては、行連結文字を省略すると、Visual Basic コンパイラはステートメントを暗黙的に次のコード行に継続します。</span><span class="sxs-lookup"><span data-stu-id="2294e-110">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="2294e-111">行連結文字を省略できる構文要素の一覧については、[ステートメント](../language-features/statements.md)に関する記事の「暗黙的な行連結」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2294e-111">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../language-features/statements.md).</span></span>

  <span data-ttu-id="2294e-112">次の例では、最後の行を除くすべての行を行連結文字で終了して、ステートメントが 4 行に分割されています。</span><span class="sxs-lookup"><span data-stu-id="2294e-112">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="2294e-113">このシーケンスを使用すると、オンラインでも印刷された場合でもコードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="2294e-113">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="2294e-114">行連結文字は、行の最後の文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2294e-114">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="2294e-115">同じ行でその後に何かを続けることはできません。</span><span class="sxs-lookup"><span data-stu-id="2294e-115">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="2294e-116">行連結文字を使用できる場所については、いくつかの制限があります。たとえば、引数名の途中で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2294e-116">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="2294e-117">引数リストを行連結文字で分割することはできますが、引数の個々の名前はそのままにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2294e-117">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="2294e-118">行連結文字を使用してコメントを継続することはできません。</span><span class="sxs-lookup"><span data-stu-id="2294e-118">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="2294e-119">コンパイラは、コメント内の文字に特別な意味があるかどうかを調べるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2294e-119">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="2294e-120">複数行のコメントでは、各行でコメント記号 (`'`) を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="2294e-120">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="2294e-121">各ステートメントを別々の行に配置するのが推奨される方法ですが、Visual Basic では同じ行に複数のステートメントを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="2294e-121">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="2294e-122">同じ行に複数のステートメントを配置するには</span><span class="sxs-lookup"><span data-stu-id="2294e-122">To place multiple statements on the same line</span></span>

<span data-ttu-id="2294e-123">次の例のように、ステートメントをコロン (`:`) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="2294e-123">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="2294e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2294e-124">See also</span></span>

- [<span data-ttu-id="2294e-125">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="2294e-125">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="2294e-126">ステートメント</span><span class="sxs-lookup"><span data-stu-id="2294e-126">Statements</span></span>](../language-features/statements.md)
