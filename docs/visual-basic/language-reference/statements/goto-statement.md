---
description: '詳細情報: GoTo ステートメント'
title: GoTo ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 804baec130111562225b09cbdc7b5fb2d73adba5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769053"
---
# <a name="goto-statement"></a><span data-ttu-id="d5394-103">GoTo ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-103">GoTo Statement</span></span>

<span data-ttu-id="d5394-104">プロシージャ内の指定した行に無条件に分岐します。</span><span class="sxs-lookup"><span data-stu-id="d5394-104">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5394-105">構文</span><span class="sxs-lookup"><span data-stu-id="d5394-105">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="d5394-106">パーツ</span><span class="sxs-lookup"><span data-stu-id="d5394-106">Part</span></span>  

 `line`  
 <span data-ttu-id="d5394-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="d5394-107">Required.</span></span> <span data-ttu-id="d5394-108">任意の行ラベル。</span><span class="sxs-lookup"><span data-stu-id="d5394-108">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5394-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d5394-109">Remarks</span></span>  

 <span data-ttu-id="d5394-110">`GoTo` ステートメントでは、それが存在するプロシージャ内の行にのみ分岐できます。</span><span class="sxs-lookup"><span data-stu-id="d5394-110">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="d5394-111">行には、`GoTo` で参照できる行ラベルが必要です。</span><span class="sxs-lookup"><span data-stu-id="d5394-111">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="d5394-112">詳細については、「[方法:ステートメントへのラベル付け](../../programming-guide/program-structure/how-to-label-statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5394-112">For more information, see [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5394-113">`GoTo` ステートメントによって、コードの読み取りと保守が困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5394-113">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="d5394-114">可能な限り、代わりに制御構造を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d5394-114">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="d5394-115">詳細については、「 [Control Flow](../../programming-guide/language-features/control-flow/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5394-115">For more information, see [Control Flow](../../programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="d5394-116">`GoTo` ステートメントを使用して、`For`...`Next`、`For Each`...`Next`、`SyncLock`...`End SyncLock`、`Try`...`Catch`...`Finally`、`With`...`End With`、または `Using`...`End Using` コンストラクションの外部から、内部のラベルに分岐することはできません。</span><span class="sxs-lookup"><span data-stu-id="d5394-116">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="d5394-117">分岐と Try コンストラクション</span><span class="sxs-lookup"><span data-stu-id="d5394-117">Branching and Try Constructions</span></span>  

 <span data-ttu-id="d5394-118">`Try`...`Catch``Finally` コンストラクション内では、`GoTo` ステートメントによる分岐に、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="d5394-118">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="d5394-119">ブロックまたは領域</span><span class="sxs-lookup"><span data-stu-id="d5394-119">Block or region</span></span>|<span data-ttu-id="d5394-120">外部からの分岐</span><span class="sxs-lookup"><span data-stu-id="d5394-120">Branching in from outside</span></span>|<span data-ttu-id="d5394-121">内部からの分岐</span><span class="sxs-lookup"><span data-stu-id="d5394-121">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="d5394-122">`Try` ブロック</span><span class="sxs-lookup"><span data-stu-id="d5394-122">`Try` block</span></span>|<span data-ttu-id="d5394-123">同じコンストラクションの `Catch` ブロックからのみ <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d5394-123">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="d5394-124">コンストラクション全体の外部へのみ</span><span class="sxs-lookup"><span data-stu-id="d5394-124">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="d5394-125">`Catch` ブロック</span><span class="sxs-lookup"><span data-stu-id="d5394-125">`Catch` block</span></span>|<span data-ttu-id="d5394-126">許可されない</span><span class="sxs-lookup"><span data-stu-id="d5394-126">Never allowed</span></span>|<span data-ttu-id="d5394-127">コンストラクション全体の外部、または同じコンストラクションの `Try` ブロックへのみ <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d5394-127">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="d5394-128">`Finally` ブロック</span><span class="sxs-lookup"><span data-stu-id="d5394-128">`Finally` block</span></span>|<span data-ttu-id="d5394-129">許可されない</span><span class="sxs-lookup"><span data-stu-id="d5394-129">Never allowed</span></span>|<span data-ttu-id="d5394-130">許可されない</span><span class="sxs-lookup"><span data-stu-id="d5394-130">Never allowed</span></span>|  
  
 <span data-ttu-id="d5394-131"><sup>1</sup> 1 つの `Try`...`Catch`...`Finally` コンストラクションが別のコンストラクション内に入れ子になっている場合、`Catch` ブロックは自身の入れ子レベルにある `Try` ブロックに分岐できますが、他の `Try` ブロックには分岐できません。</span><span class="sxs-lookup"><span data-stu-id="d5394-131"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="d5394-132">入れ子になった `Try`...`Catch`...`Finally` コンストラクションは、それが中で入れ子になっているコンストラクションの `Try` または `Catch` ブロックに完全に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5394-132">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="d5394-133">次の図は、別のコンストラクション内に入れ子になっている `Try` コンストラクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="d5394-133">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="d5394-134">2 つのコンストラクションのブロック間のさまざまな分岐は、有効または無効として示されます。</span><span class="sxs-lookup"><span data-stu-id="d5394-134">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Try 構造内の分岐のグラフィック ダイアグラム](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="d5394-136">例</span><span class="sxs-lookup"><span data-stu-id="d5394-136">Example</span></span>  

 <span data-ttu-id="d5394-137">次の例では、`GoTo` ステートメントを使用して、プロシージャ内の行ラベルに分岐します。</span><span class="sxs-lookup"><span data-stu-id="d5394-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="d5394-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5394-138">See also</span></span>

- [<span data-ttu-id="d5394-139">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-139">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="d5394-140">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-140">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="d5394-141">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-141">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="d5394-142">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-142">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="d5394-143">Select...Case ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-143">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="d5394-144">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-144">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="d5394-145">While...End While ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-145">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="d5394-146">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="d5394-146">With...End With Statement</span></span>](with-end-with-statement.md)
