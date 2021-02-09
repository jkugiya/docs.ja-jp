---
description: '詳細情報: Select...Case ステートメント (Visual Basic)'
title: Select...Case ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 4f8edecd0a0b1afd59e182a372e308c3829a9b93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741134"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="e89a5-103">Select...Case ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e89a5-103">Select...Case Statement (Visual Basic)</span></span>

<span data-ttu-id="e89a5-104">式の値に応じて、いくつかのステートメント グループのいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-104">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89a5-105">構文</span><span class="sxs-lookup"><span data-stu-id="e89a5-105">Syntax</span></span>  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="e89a5-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="e89a5-106">Parts</span></span>  
  
|<span data-ttu-id="e89a5-107">用語</span><span class="sxs-lookup"><span data-stu-id="e89a5-107">Term</span></span>|<span data-ttu-id="e89a5-108">定義</span><span class="sxs-lookup"><span data-stu-id="e89a5-108">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="e89a5-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="e89a5-109">Required.</span></span> <span data-ttu-id="e89a5-110">式。</span><span class="sxs-lookup"><span data-stu-id="e89a5-110">Expression.</span></span> <span data-ttu-id="e89a5-111">基本データ型 (`Boolean`、`Byte`、`Char`、`Date`、`Double`、`Decimal`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong`、および `UShort`) のいずれかとして評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="e89a5-111">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="e89a5-112">`Case` ステートメントには必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-112">Required in a `Case` statement.</span></span> <span data-ttu-id="e89a5-113">`testexpression` の一致する値を表す式の句の一覧。</span><span class="sxs-lookup"><span data-stu-id="e89a5-113">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="e89a5-114">複数の式の句を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="e89a5-114">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="e89a5-115">各句には、次のいずれかの形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-115">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="e89a5-116">-   *expression1* `To` *expression2*</span><span class="sxs-lookup"><span data-stu-id="e89a5-116">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="e89a5-117">-   [ `Is` ] *comparisonoperator* *expression*</span><span class="sxs-lookup"><span data-stu-id="e89a5-117">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="e89a5-118">-   *式*</span><span class="sxs-lookup"><span data-stu-id="e89a5-118">-   *expression*</span></span><br /><br /> <span data-ttu-id="e89a5-119">`To` キーワードを使用して、`testexpression` の一致する値の範囲の境界を指定します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-119">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="e89a5-120">`expression1` の値は `expression2` の値以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e89a5-120">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="e89a5-121">比較演算子 (`=`、`<>`、`<`、`<=`、`>`、または `>=`) と共に `Is` キーワードを使用して、`testexpression` の一致する値に対する制限を指定します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-121">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="e89a5-122">`Is` キーワードが指定されていない場合は、自動的に *comparisonoperator* の前に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-122">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="e89a5-123">`expression` のみを指定する形式は、`Is` 形式の特殊なケースとして扱われます。ここで、*comparisonoperator* は等号 (`=`) です。</span><span class="sxs-lookup"><span data-stu-id="e89a5-123">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="e89a5-124">この形式は `testexpression` = `expression` として評価されます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-124">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="e89a5-125">`expressionlist` の式は、`testexpression` の型に暗黙的に変換可能であり、一緒に使用される 2 つの型に対して適切な `comparisonoperator` が有効であれば、任意のデータ型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-125">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="e89a5-126">任意。</span><span class="sxs-lookup"><span data-stu-id="e89a5-126">Optional.</span></span> <span data-ttu-id="e89a5-127">`testexpression` が `expressionlist` 内のいずれかの句と一致する場合に実行される、`Case` の後の 1 つ以上のステートメント。</span><span class="sxs-lookup"><span data-stu-id="e89a5-127">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="e89a5-128">任意。</span><span class="sxs-lookup"><span data-stu-id="e89a5-128">Optional.</span></span> <span data-ttu-id="e89a5-129">`testexpression` が どの `Case` ステートメントの `expressionlist` 内のどの句とも一致しない場合に実行される、`Case Else` の後の 1 つ以上のステートメント。</span><span class="sxs-lookup"><span data-stu-id="e89a5-129">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="e89a5-130">`Select`...`Case` コンストラクションの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-130">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e89a5-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="e89a5-131">Remarks</span></span>  

 <span data-ttu-id="e89a5-132">`testexpression` が `Case` `expressionlist` 句と一致する場合、その `Case` ステートメントの後のステートメントは、次の `Case`、`Case Else`、または `End Select` ステートメントまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-132">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="e89a5-133">その後、制御は `End Select` の後のステートメントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-133">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="e89a5-134">`testexpression` が複数の `Case` 句の `expressionlist` 句と一致する場合は、最初の一致の後のステートメントのみが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-134">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="e89a5-135">`Case Else` ステートメントを使用して、他のいずれかの `Case` ステートメントで `testexpression` 句と `expressionlist` 句の間に一致が検出されなかった場合に実行する `elsestatements` を導入します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-135">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="e89a5-136">必須ではありませんが、予期しない `testexpression` 値を処理するために、`Select Case` コンストラクションに `Case Else` ステートメントを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e89a5-136">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="e89a5-137">`Case` `expressionlist` 句が `testexpression` に一致せず、`Case Else` ステートメントが存在しない場合、制御は `End Select` の後のステートメントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-137">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="e89a5-138">各 `Case` 句では、複数の式または範囲を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-138">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="e89a5-139">たとえば、次の行は有効です。</span><span class="sxs-lookup"><span data-stu-id="e89a5-139">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> <span data-ttu-id="e89a5-140">`Case` および `Case Else` ステートメントで使用される `Is` キーワードは、オブジェクト参照の比較に使用される [Is Operator](../operators/is-operator.md) と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="e89a5-140">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="e89a5-141">文字列の範囲と複数の式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-141">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="e89a5-142">次の例では、`Case` は、"apples" と完全に等しいか、アルファベット順の "nuts" と "soup" の間の値を持つか、`testItem` の現在の値とまったく同じ値が含まれている任意の文字列に一致します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-142">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="e89a5-143">`Option Compare` の設定は、文字列比較に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e89a5-143">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="e89a5-144">`Option Compare Text` では、文字列 "Apples" と "apples" は等しいものとして比較されますが、`Option Compare Binary` ではこれらは等しくありません。</span><span class="sxs-lookup"><span data-stu-id="e89a5-144">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e89a5-145">複数の句を持つ `Case` ステートメントでは、*ショートサーキット* と呼ばれる動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e89a5-145">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="e89a5-146">Visual Basic では句が左から右に評価され、いずれかが `testexpression` と一致する場合、残りの句は評価されません。</span><span class="sxs-lookup"><span data-stu-id="e89a5-146">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="e89a5-147">ショートサーキットはパフォーマンスを向上させることができますが、`expressionlist` 内のすべての式を評価する必要がある場合は、予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e89a5-147">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="e89a5-148">ショートサーキットの詳細については、[ブール式](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e89a5-148">For more information on short-circuiting, see [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="e89a5-149">`Case` または `Case Else` ステートメント ブロック内のコードがブロック内のステートメントをこれ以上実行する必要がない場合は、`Exit Select` ステートメントを使用してブロックを終了できます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-149">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="e89a5-150">これは `End Select` の次のステートメントに制御を直ちに渡します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-150">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="e89a5-151">`Select Case` コンストラクションは入れ子にできます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-151">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="e89a5-152">入れ子になった `Select Case` コンストラクションのそれぞれには、一致する `End Select` ステートメントが必要です。また、入れ子になっている外側の `Select Case` コンストラクションの 1 つの `Case` または `Case Else` ステートメント ブロック内に完全に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e89a5-152">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e89a5-153">例</span><span class="sxs-lookup"><span data-stu-id="e89a5-153">Example</span></span>  

 <span data-ttu-id="e89a5-154">次の例では、`Select Case` コンストラクションを使用して、変数 `number` の値に対応する行を記述します。</span><span class="sxs-lookup"><span data-stu-id="e89a5-154">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="e89a5-155">2 番目の `Case` ステートメントには、`number` の現在の値と一致する値が含まれています。そのため、"Between 6 and 8, inclusive" を記述するステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e89a5-155">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a><span data-ttu-id="e89a5-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="e89a5-156">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [<span data-ttu-id="e89a5-157">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="e89a5-157">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="e89a5-158">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="e89a5-158">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="e89a5-159">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e89a5-159">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="e89a5-160">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="e89a5-160">Exit Statement</span></span>](exit-statement.md)
