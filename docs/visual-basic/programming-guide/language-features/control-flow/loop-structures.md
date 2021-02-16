---
description: '詳細情報: ループ構造 (Visual Basic)'
title: ループ構造
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 82ff36d8f5c05501fcff0f1d564e2613c9b78953
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480649"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="33494-103">ループ構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33494-103">Loop Structures (Visual Basic)</span></span>

<span data-ttu-id="33494-104">Visual Basic ループ構造を使用すると、1 行または複数行のコードを繰り返し実行できます。</span><span class="sxs-lookup"><span data-stu-id="33494-104">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="33494-105">ループ構造では、条件が `True` または `False` になるまで、指定された回数だけ、またはコレクション内の要素ごとに 1 回、ステートメントを繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="33494-105">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="33494-106">次の図は、条件が true になるまで、一連のステートメントを実行するループ構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="33494-106">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Do...Until ループを示すフロー チャート。](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="33494-108">While ループ</span><span class="sxs-lookup"><span data-stu-id="33494-108">While Loops</span></span>  

 <span data-ttu-id="33494-109">`While`...`End While` コンストラクションでは、`While` ステートメントで指定された条件が `True` である限り、一連のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="33494-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="33494-110">詳細については、「[While...End While ステートメント](../../../language-reference/statements/while-end-while-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33494-110">For more information, see [While...End While Statement](../../../language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="33494-111">Do ループ</span><span class="sxs-lookup"><span data-stu-id="33494-111">Do Loops</span></span>  

 <span data-ttu-id="33494-112">`Do`...`Loop` コンストラクションを使用すると、ループ構造の最初または最後で条件をテストできます。</span><span class="sxs-lookup"><span data-stu-id="33494-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="33494-113">また、条件が `True` の間、または `True` になるまで、ループを繰り返すかどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="33494-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="33494-114">詳細については、「[Do...Loop ステートメント](../../../language-reference/statements/do-loop-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33494-114">For more information, see [Do...Loop Statement](../../../language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="33494-115">For ループ</span><span class="sxs-lookup"><span data-stu-id="33494-115">For Loops</span></span>  

 <span data-ttu-id="33494-116">`For`...`Next` コンストラクションでは、設定された回数だけループが実行されます。</span><span class="sxs-lookup"><span data-stu-id="33494-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="33494-117">繰り返しの追跡には、"*カウンター*" とも呼ばれるループ制御変数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="33494-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="33494-118">このカウンターの開始値と終了値を指定し、必要に応じて、ある繰り返しから次の繰り返しまでの増加量を指定できます。</span><span class="sxs-lookup"><span data-stu-id="33494-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="33494-119">詳細については、「[For...Next ステートメント](../../../language-reference/statements/for-next-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33494-119">For more information, see [For...Next Statement](../../../language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="33494-120">For Each ループ</span><span class="sxs-lookup"><span data-stu-id="33494-120">For Each Loops</span></span>  

 <span data-ttu-id="33494-121">`For Each`...`Next` コンストラクションでは、コレクション内の要素ごとに 1 回、一連のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="33494-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="33494-122">ループ制御変数を指定しますが、その開始値と終了値を決める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="33494-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="33494-123">詳細については、[For Each...Next ステートメント](../../../language-reference/statements/for-each-next-statement.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33494-123">For more information, see [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33494-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="33494-124">See also</span></span>

- [<span data-ttu-id="33494-125">制御フロー</span><span class="sxs-lookup"><span data-stu-id="33494-125">Control Flow</span></span>](index.md)
- [<span data-ttu-id="33494-126">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="33494-126">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="33494-127">その他の制御構造</span><span class="sxs-lookup"><span data-stu-id="33494-127">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="33494-128">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="33494-128">Nested Control Structures</span></span>](nested-control-structures.md)
