---
description: '詳細情報: Visual Basic の論理演算子とビット処理演算子'
title: 論理演算子とビット処理演算子
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 55d9567813a9114573e1e3f70fe181cb8621b350
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472723"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="9ba41-103">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="9ba41-103">Logical and Bitwise Operators in Visual Basic</span></span>

<span data-ttu-id="9ba41-104">論理演算子を使用すると、`Boolean` 式を比較し、`Boolean` の結果を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-104">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="9ba41-105">`And`、`Or`、`AndAlso`、`OrElse`、および `Xor` の各演算子は、2 つのオペランドを受け取るため、"*二項*" です。`Not` 演算子は、1 つのオペランドを受け取るため、"*単項*" です。</span><span class="sxs-lookup"><span data-stu-id="9ba41-105">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="9ba41-106">これらの演算子の一部を使用して、整数値に対してビットごとの論理演算を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-106">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="9ba41-107">単項論理演算子</span><span class="sxs-lookup"><span data-stu-id="9ba41-107">Unary Logical Operator</span></span>  

 <span data-ttu-id="9ba41-108">[Not 演算子](../../../language-reference/operators/not-operator.md)を使用すると、`Boolean` 式に対して論理的な "*否定*" を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-108">The [Not Operator](../../../language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="9ba41-109">これにより、そのオペランドの反対の論理値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-109">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="9ba41-110">式が `True` に評価される場合、`Not` からは `False` が返されます。式が `False` に評価される場合、`Not` からは `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-110">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="9ba41-111">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="9ba41-111">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="9ba41-112">二項論理演算子</span><span class="sxs-lookup"><span data-stu-id="9ba41-112">Binary Logical Operators</span></span>  

 <span data-ttu-id="9ba41-113">[And 演算子](../../../language-reference/operators/and-operator.md)を使用すると、2 つの `Boolean` 式に対して "*論理積*" を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-113">The [And Operator](../../../language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="9ba41-114">両方の式が `True` に評価される場合、`And` からは `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-114">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="9ba41-115">式の少なくとも 1 つが `False` に評価される場合、`And` からは `False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-115">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="9ba41-116">[Or 演算子](../../../language-reference/operators/or-operator.md)を使用すると、2 つの `Boolean` 式に対して "*論理和*" または "*論理包含*" を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-116">The [Or Operator](../../../language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="9ba41-117">いずれかの式が `True` に評価されるか、または両方が `True` に評価される場合、`Or` からは `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-117">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="9ba41-118">どちらの式も `True` に評価されない場合、`Or` からは `False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-118">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="9ba41-119">[Xor 演算子](../../../language-reference/operators/xor-operator.md)を使用すると、2 つの `Boolean` 式に対して "*排他的論理和*" を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-119">The [Xor Operator](../../../language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="9ba41-120">両方ではなく 1 つの式のみが `True` に評価される場合、`Xor` からは `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-120">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="9ba41-121">両方の式が `True` に評価されるか、両方が `False` に評価される場合、`Xor` からは `False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-121">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="9ba41-122">次の例は、`And`、`Or`、および `Xor` の各演算子を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ba41-122">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="9ba41-123">短絡論理演算</span><span class="sxs-lookup"><span data-stu-id="9ba41-123">Short-Circuiting Logical Operations</span></span>  

 <span data-ttu-id="9ba41-124">[AndAlso 演算子](../../../language-reference/operators/andalso-operator.md)を使用すると、2 つの `Boolean` 式に対して論理積も実行されるという点で、`And` 演算子とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="9ba41-124">The [AndAlso Operator](../../../language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="9ba41-125">この 2 つの主な違いは、`AndAlso` が "*短絡*" 動作を示すことです。</span><span class="sxs-lookup"><span data-stu-id="9ba41-125">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="9ba41-126">`AndAlso` 式の 1 つ目の式が `False` に評価される場合、最終結果を変更できないため、2 つ目の式は評価されず、`AndAlso` からは `False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-126">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="9ba41-127">同様に、[OrElse 演算子](../../../language-reference/operators/orelse-operator.md)を使用すると、2 つの `Boolean` 式に対して短絡論理和を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-127">Similarly, the [OrElse Operator](../../../language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="9ba41-128">`OrElse` 式の 1 つ目の式が `True` に評価される場合、最終結果を変更できないため、2 つ目の式は評価されず、`OrElse` からは `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-128">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="9ba41-129">短絡のトレードオフ</span><span class="sxs-lookup"><span data-stu-id="9ba41-129">Short-Circuiting Trade-Offs</span></span>  

 <span data-ttu-id="9ba41-130">短絡を使用すると、論理演算の結果を変更できない式が評価されないため、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-130">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="9ba41-131">ただし、その式で追加のアクションが実行される場合、短絡によってそれらのアクションはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-131">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="9ba41-132">たとえば、式に `Function` プロシージャへの呼び出しが含まれている場合、式が短絡されると、そのプロシージャは呼び出されず、`Function` に含まれる追加のコードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="9ba41-132">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="9ba41-133">そのため、この関数はたまにしか実行されず、正しくテストされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9ba41-133">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="9ba41-134">また、プログラム ロジックは `Function` のコードに依存する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ba41-134">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="9ba41-135">次の例は、`And`、`Or`、およびそれらに対応する短絡演算の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ba41-135">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 <span data-ttu-id="9ba41-136">前の例では、呼び出しが短絡されると、`checkIfValid()` 内の一部の重要なコードが実行されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9ba41-136">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="9ba41-137">`12 > 45` から `False` が返される場合でも、1 つ目の `If` ステートメントでは `checkIfValid()` が呼び出されます。これは、`And` では短絡が実行されないためです。</span><span class="sxs-lookup"><span data-stu-id="9ba41-137">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="9ba41-138">2 つ目の `If` ステートメントでは `checkIfValid()` が呼び出されません。これは、`12 > 45` から `False` が返されると、`AndAlso` によって 2 つ目の式が短絡されるためです。</span><span class="sxs-lookup"><span data-stu-id="9ba41-138">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="9ba41-139">`12 < 45` から `True` が返される場合でも、3 つ目の `If` ステートメントでは `checkIfValid()` が呼び出されます。これは、`Or` では短絡が実行されないためです。</span><span class="sxs-lookup"><span data-stu-id="9ba41-139">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="9ba41-140">4 つ目の `If` ステートメントでは `checkIfValid()` が呼び出されません。これは、`12 < 45` から `True` が返されると、`OrElse` によって 2 つ目の式が短絡されるためです。</span><span class="sxs-lookup"><span data-stu-id="9ba41-140">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="9ba41-141">ビットごとの演算</span><span class="sxs-lookup"><span data-stu-id="9ba41-141">Bitwise Operations</span></span>  

 <span data-ttu-id="9ba41-142">ビットごとの演算では、2 つの整数値がバイナリ (base 2) 形式で評価されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-142">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="9ba41-143">対応する位置にあるビットが比較され、比較に基づいて値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-143">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="9ba41-144">`And` 演算子の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9ba41-144">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 <span data-ttu-id="9ba41-145">前の例では、`x` の値を 1 に設定しています。</span><span class="sxs-lookup"><span data-stu-id="9ba41-145">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="9ba41-146">これは次の理由によるものです。</span><span class="sxs-lookup"><span data-stu-id="9ba41-146">This happens for the following reasons:</span></span>  
  
- <span data-ttu-id="9ba41-147">値はバイナリとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-147">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="9ba41-148">バイナリ形式の 3 = 011</span><span class="sxs-lookup"><span data-stu-id="9ba41-148">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="9ba41-149">バイナリ形式の 5 = 101</span><span class="sxs-lookup"><span data-stu-id="9ba41-149">5 in binary form = 101</span></span>  
  
- <span data-ttu-id="9ba41-150">`And` 演算子を使用すると、バイナリ表現を一度に 1 つのバイナリ位置 (ビット) ずつ比較できます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-150">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="9ba41-151">特定の位置の両方のビットが 1 の場合、結果のその位置に 1 が配置されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-151">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="9ba41-152">いずれかのビットが 0 の場合、結果のその位置に 0 が配置されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-152">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="9ba41-153">前の例では、これは次のように機能します。</span><span class="sxs-lookup"><span data-stu-id="9ba41-153">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="9ba41-154">011 (バイナリ形式の 3)</span><span class="sxs-lookup"><span data-stu-id="9ba41-154">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="9ba41-155">101 (バイナリ形式の 5)</span><span class="sxs-lookup"><span data-stu-id="9ba41-155">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="9ba41-156">001 (バイナリ形式の結果)</span><span class="sxs-lookup"><span data-stu-id="9ba41-156">001 (The result, in binary form)</span></span>  
  
- <span data-ttu-id="9ba41-157">結果は 10 進として扱われます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-157">The result is treated as decimal.</span></span> <span data-ttu-id="9ba41-158">値 001 は 1 のバイナリ表現であるため、`x` = 1 です。</span><span class="sxs-lookup"><span data-stu-id="9ba41-158">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="9ba41-159">ビットごとの `Or` 演算は似ていますが、比較されるビットのいずれか、または両方が 1 の場合、結果ビットに 1 が割り当てられる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="9ba41-159">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="9ba41-160">`Xor` を使用すると、比較されたビットの (両方ではなく) いずれかが 1 の場合、結果ビットに 1 が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-160">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="9ba41-161">`Not` を使用すると、1 つのオペランドを受け取り、符号ビットを含むすべてのビットが反転され、その値が結果に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-161">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="9ba41-162">つまり、符号付き正数の場合、`Not` からは常に負の値が返され、負数の場合、`Not` からは常に正または 0 の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-162">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="9ba41-163">`AndAlso` 演算子と `OrElse` 演算子はビットごとの演算をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9ba41-163">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ba41-164">ビットごとの演算は、整数型に対してのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ba41-164">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="9ba41-165">ビットごとの演算を進める前に、浮動小数点値を整数型に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ba41-165">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba41-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ba41-166">See also</span></span>

- [<span data-ttu-id="9ba41-167">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ba41-167">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="9ba41-168">ブール式</span><span class="sxs-lookup"><span data-stu-id="9ba41-168">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="9ba41-169">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="9ba41-169">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="9ba41-170">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="9ba41-170">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="9ba41-171">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="9ba41-171">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="9ba41-172">演算子の効率のよい組み合わせ</span><span class="sxs-lookup"><span data-stu-id="9ba41-172">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
