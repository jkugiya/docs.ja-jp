---
description: '詳細情報: If...Then...Else ステートメント (Visual Basic)'
title: If...Then...Else ステートメント
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: 83850771354b95f0e2d9c1bf1360a61d5264fe2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769014"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="4b12c-103">If...Then...Else ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b12c-103">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="4b12c-104">式の値に応じてステートメント グループを条件付きで実行します。</span><span class="sxs-lookup"><span data-stu-id="4b12c-104">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b12c-105">構文</span><span class="sxs-lookup"><span data-stu-id="4b12c-105">Syntax</span></span>

```vb
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a><span data-ttu-id="4b12c-106">コード例へのクイック リンク</span><span class="sxs-lookup"><span data-stu-id="4b12c-106">Quick links to example code</span></span>

<span data-ttu-id="4b12c-107">この記事には、`If`...`Then`...`Else` ステートメントの使用方法を示す例がいくつか含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b12c-107">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="4b12c-108">複数行構文の例</span><span class="sxs-lookup"><span data-stu-id="4b12c-108">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="4b12c-109">入れ子になった構文の例</span><span class="sxs-lookup"><span data-stu-id="4b12c-109">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="4b12c-110">単一行構文の例</span><span class="sxs-lookup"><span data-stu-id="4b12c-110">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="4b12c-111">指定項目</span><span class="sxs-lookup"><span data-stu-id="4b12c-111">Parts</span></span>

`condition` \
<span data-ttu-id="4b12c-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="4b12c-112">Required.</span></span> <span data-ttu-id="4b12c-113">式。</span><span class="sxs-lookup"><span data-stu-id="4b12c-113">Expression.</span></span> <span data-ttu-id="4b12c-114">`True` または `False`、または `Boolean` に暗黙的に変換できるデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b12c-114">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="4b12c-115">式が [Nothing](../nothing.md) に評価される [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) の `Boolean` 変数の場合、条件は、式が `False` であるかのように処理され、`ElseIf` ブロックが存在する場合は評価されます。存在しない場合は、`Else` ブロックが実行されます (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="4b12c-115">If the expression is a [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="4b12c-116">単一行の構文では必須です。複数行の構文では省略可能です。</span><span class="sxs-lookup"><span data-stu-id="4b12c-116">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="4b12c-117">任意。</span><span class="sxs-lookup"><span data-stu-id="4b12c-117">Optional.</span></span> <span data-ttu-id="4b12c-118">`condition` が `True` に評価された場合に実行される `If`...`Then` の後に続く 1 つ以上のステートメント。</span><span class="sxs-lookup"><span data-stu-id="4b12c-118">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="4b12c-119">`ElseIf` が存在する場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="4b12c-119">Required if `ElseIf` is present.</span></span> <span data-ttu-id="4b12c-120">式。</span><span class="sxs-lookup"><span data-stu-id="4b12c-120">Expression.</span></span> <span data-ttu-id="4b12c-121">`True` または `False`、または `Boolean` に暗黙的に変換できるデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b12c-121">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="4b12c-122">任意。</span><span class="sxs-lookup"><span data-stu-id="4b12c-122">Optional.</span></span> <span data-ttu-id="4b12c-123">`elseifcondition` が `True` に評価された場合に実行される `ElseIf`...`Then` の後に続く 1 つ以上のステートメント。</span><span class="sxs-lookup"><span data-stu-id="4b12c-123">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="4b12c-124">任意。</span><span class="sxs-lookup"><span data-stu-id="4b12c-124">Optional.</span></span> <span data-ttu-id="4b12c-125">前の `condition` または `elseifcondition` 式が `True` に評価されなかった場合に実行される 1 つ以上のステートメント。</span><span class="sxs-lookup"><span data-stu-id="4b12c-125">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="4b12c-126">複数行バージョンの `If`...`Then`...`Else` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="4b12c-126">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b12c-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="4b12c-127">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="4b12c-128">複数行の構文</span><span class="sxs-lookup"><span data-stu-id="4b12c-128">Multiline syntax</span></span>

<span data-ttu-id="4b12c-129">`If`...`Then`...`Else` ステートメントが検出されると、`condition` がテストされます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-129">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="4b12c-130">`condition` が `True` の場合、`Then` に続くステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-130">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="4b12c-131">`condition` が `False` の場合は、各 `ElseIf` ステートメント (存在する場合) が順番に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-131">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="4b12c-132">`True` になる `elseifcondition` が見つかると、関連付けられた `ElseIf` の直後にあるステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-132">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="4b12c-133">`True` に評価される `elseifcondition` がない場合、または `ElseIf` ステートメントが存在しない場合は、`Else` に続くステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-133">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="4b12c-134">`Then`、`ElseIf`、または `Else` の後に続くステートメントが実行されると、`End If` に続くステートメントが引き続き実行されます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-134">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="4b12c-135">`ElseIf` と `Else` の句は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="4b12c-135">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="4b12c-136">`If`...`Then`...`Else` ステートメントには、必要な数の `ElseIf` 句を指定できますが、`Else` 句の後に `ElseIf` 句を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="4b12c-136">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="4b12c-137">`If`...`Then`...`Else` ステートメントは、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-137">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="4b12c-138">複数行の構文では、`If` ステートメントが 1 行目の唯一のステートメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b12c-138">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="4b12c-139">`ElseIf`、`Else`、および `End If` ステートメントの前には、行ラベルのみを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-139">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="4b12c-140">`If`...`Then`...`Else` ブロックは、`End If` ステートメントで終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b12c-140">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="4b12c-141">[Select...Case ステートメント](select-case-statement.md)は、複数の値が結果として得られる可能性がある単一の式を評価する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="4b12c-141">The [Select...Case Statement](select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="4b12c-142">単一行の構文</span><span class="sxs-lookup"><span data-stu-id="4b12c-142">Single-Line syntax</span></span>

<span data-ttu-id="4b12c-143">単一行の構文は、単一の条件の場合に使用することができ、True の場合に実行するコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b12c-143">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="4b12c-144">ただし、複数行の構文では、より多くの構造と柔軟性が提供され、読み取り、保守、デバッグが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="4b12c-144">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="4b12c-145">ステートメントが単一行の `If` であるかどうかを判別するために、`Then` キーワードの後に続くものが検査されます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-145">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="4b12c-146">同じ行の `Then` の後にコメント以外のものがある場合、そのステートメントは単一行の `If` ステートメントとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-146">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="4b12c-147">`Then` がない場合は、複数行の `If`...`Then`...`Else` が開始されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-147">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="4b12c-148">単一行の構文では、`If`...`Then` の判断の結果として複数のステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4b12c-148">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="4b12c-149">すべてのステートメントは、同じ行にあり、コロンで区切られている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b12c-149">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="4b12c-150">複数行構文の例</span><span class="sxs-lookup"><span data-stu-id="4b12c-150">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="4b12c-151">次の例では、`If`...`Then`...`Else` ステートメントの複数行構文の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4b12c-151">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="4b12c-152">入れ子になった構文の例</span><span class="sxs-lookup"><span data-stu-id="4b12c-152">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="4b12c-153">次の例には、入れ子になった `If`...`Then`...`Else` ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b12c-153">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="4b12c-154">単一行構文の例</span><span class="sxs-lookup"><span data-stu-id="4b12c-154">Single-Line syntax example</span></span>

<a name="single-line"></a> <span data-ttu-id="4b12c-155">単一行構文の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4b12c-155">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="4b12c-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b12c-156">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="4b12c-157">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="4b12c-157">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
- [<span data-ttu-id="4b12c-158">Select...Case ステートメント</span><span class="sxs-lookup"><span data-stu-id="4b12c-158">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="4b12c-159">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="4b12c-159">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="4b12c-160">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="4b12c-160">Decision Structures</span></span>](../../programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="4b12c-161">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="4b12c-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="4b12c-162">If 演算子</span><span class="sxs-lookup"><span data-stu-id="4b12c-162">If Operator</span></span>](../operators/if-operator.md)
