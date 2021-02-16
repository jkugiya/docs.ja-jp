---
description: '詳細情報: 条件判断構造 (Visual Basic)'
title: 条件判断構造
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 76b63d2cdc238ec5590d11a6a802f55866990a3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480688"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="c0b6f-103">条件判断構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0b6f-103">Decision Structures (Visual Basic)</span></span>

<span data-ttu-id="c0b6f-104">Visual Basic では、条件をテストし、そのテストの結果に応じてさまざまな操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-104">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="c0b6f-105">true または false の条件、式のさまざまな値、または一連のステートメントを実行するときに生成されるさまざまな例外に対して、テストを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-105">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="c0b6f-106">次の図は、条件が true であるかをテストし、true か false かに応じて異なるアクションを実行する決定構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-106">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![If...Then...Else コンストラクションのフロー チャート。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="c0b6f-108">If...Then...Else コンストラクション</span><span class="sxs-lookup"><span data-stu-id="c0b6f-108">If...Then...Else Construction</span></span>  

 <span data-ttu-id="c0b6f-109">`If...Then...Else` コンストラクションを使用すると、1 つ以上の条件をテストし、各条件に応じて 1 つ以上のステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="c0b6f-110">次の方法で、条件をテストし、アクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-110">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="c0b6f-111">条件が `True` の場合、1 つ以上のステートメントを実行する</span><span class="sxs-lookup"><span data-stu-id="c0b6f-111">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="c0b6f-112">条件が `False` の場合、1 つ以上のステートメントを実行する</span><span class="sxs-lookup"><span data-stu-id="c0b6f-112">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="c0b6f-113">条件が `True` 場合は、ステートメントをいくつか実行し、`False` の場合は、別のステートメントをいくつか実行する</span><span class="sxs-lookup"><span data-stu-id="c0b6f-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="c0b6f-114">前の条件が `False` の場合、追加の条件をテストする</span><span class="sxs-lookup"><span data-stu-id="c0b6f-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="c0b6f-115">これらのすべての可能性を提供する制御構造が [If...Then...Else ステートメント](../../../language-reference/statements/if-then-else-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="c0b6f-116">実行するテストとステートメントがそれぞれ 1 つしかない場合は、単一行バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="c0b6f-117">より複雑な条件とアクションのセットがある場合は、複数行バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="c0b6f-118">Select...Case コンストラクション</span><span class="sxs-lookup"><span data-stu-id="c0b6f-118">Select...Case Construction</span></span>  

 <span data-ttu-id="c0b6f-119">`Select...Case` コンストラクションを使用すると、式を 1 回評価し、使用できるさまざまな値に基づいてさまざまなステートメント セットを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="c0b6f-120">詳細については、「[Select...Case ステートメント](../../../language-reference/statements/select-case-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-120">For more information, see [Select...Case Statement](../../../language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="c0b6f-121">Try...Catch...Finally コンストラクション</span><span class="sxs-lookup"><span data-stu-id="c0b6f-121">Try...Catch...Finally Construction</span></span>  

 <span data-ttu-id="c0b6f-122">`Try...Catch...Finally` コンストラクションを使用すると、使っているステートメントのいずれかによって例外が引き起こされた場合に、コントロールが保持されている環境で一連のステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="c0b6f-123">さまざまな例外に対して、さまざまなアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="c0b6f-124">発生する事象を問わず、`Try...Catch...Finally` コンストラクション全体を終了する前に実行されるコード ブロックを、必要に応じて指定できます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="c0b6f-125">詳しくは、「[Try...Catch...Finally ステートメント](../../../language-reference/statements/try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-125">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0b6f-126">多くの制御構造で、キーワードの 1 つをクリックすると、構造内のすべてのキーワードが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="c0b6f-127">たとえば、`If...Then...Else` コンストラクションで `If` をクリックすると、コンストラクション内の `If`、`Then`、`ElseIf`、`Else`、および `End If` のすべてのインスタンスが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="c0b6f-128">次または前の強調表示されたキーワードに移動するには、Ctrl + Shift + ↓キーを押すか、Ctrl + Shift + ↑キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c0b6f-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b6f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0b6f-129">See also</span></span>

- [<span data-ttu-id="c0b6f-130">制御フロー</span><span class="sxs-lookup"><span data-stu-id="c0b6f-130">Control Flow</span></span>](index.md)
- [<span data-ttu-id="c0b6f-131">ループ構造</span><span class="sxs-lookup"><span data-stu-id="c0b6f-131">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="c0b6f-132">その他の制御構造</span><span class="sxs-lookup"><span data-stu-id="c0b6f-132">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="c0b6f-133">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="c0b6f-133">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="c0b6f-134">If 演算子</span><span class="sxs-lookup"><span data-stu-id="c0b6f-134">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
