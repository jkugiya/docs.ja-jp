---
description: '詳細情報: If 演算子 (Visual Basic)'
title: If 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 3b25ab4b6c5f0d2608644adb6e35ff4ad5128f42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665875"
---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="3d6c2-103">If 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d6c2-103">If Operator (Visual Basic)</span></span>

<span data-ttu-id="3d6c2-104">ショートサーキット評価を使用して、条件に応じて 2 つの値のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-104">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="3d6c2-105">`If` 演算子は、3 つの引数または 2 つの引数を指定して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-105">The `If` operator can be called with three arguments or with two arguments.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d6c2-106">構文</span><span class="sxs-lookup"><span data-stu-id="3d6c2-106">Syntax</span></span>

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="3d6c2-107">3 つの引数を指定して If 演算子を呼び出す場合</span><span class="sxs-lookup"><span data-stu-id="3d6c2-107">If operator called with three arguments</span></span>

<span data-ttu-id="3d6c2-108">3 つの引数を使用して `If` を呼び出す場合、最初の引数は `Boolean` としてキャストできる値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-108">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="3d6c2-109">この `Boolean` 値によって、他の 2 つの引数のうち、どちらが評価されて返されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-109">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="3d6c2-110">次の一覧は、3 つの引数を使用して `If` 演算子を呼び出す場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-110">The following list applies only when the `If` operator is called by using three arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="3d6c2-111">指定項目</span><span class="sxs-lookup"><span data-stu-id="3d6c2-111">Parts</span></span>

|<span data-ttu-id="3d6c2-112">用語</span><span class="sxs-lookup"><span data-stu-id="3d6c2-112">Term</span></span>|<span data-ttu-id="3d6c2-113">定義</span><span class="sxs-lookup"><span data-stu-id="3d6c2-113">Definition</span></span>|
|---|---|
|`argument1`|<span data-ttu-id="3d6c2-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-114">Required.</span></span> <span data-ttu-id="3d6c2-115">`Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-115">`Boolean`.</span></span> <span data-ttu-id="3d6c2-116">他のどの引数を評価して返すかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-116">Determines which of the other arguments to evaluate and return.</span></span>|
|`argument2`|<span data-ttu-id="3d6c2-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-117">Required.</span></span> <span data-ttu-id="3d6c2-118">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-118">`Object`.</span></span> <span data-ttu-id="3d6c2-119">`argument1` が `True` に評価された場合に、評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-119">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|
|`argument3`|<span data-ttu-id="3d6c2-120">必須です。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-120">Required.</span></span> <span data-ttu-id="3d6c2-121">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-121">`Object`.</span></span> <span data-ttu-id="3d6c2-122">`argument1` が `False` に評価された場合、または `argument1` が [Nothing](../nothing.md) に評価された [null 許容](../../programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` 変数である場合に、評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-122">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../nothing.md).</span></span>|

<span data-ttu-id="3d6c2-123">3 つの引数を指定して呼び出される `If` 演算子は、ショートサーキット評価を使用する点を除き、`IIf` 関数と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-123">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="3d6c2-124">`IIf` 関数では常に、その 3 つの引数がすべて評価されます。それに対し、3 つの引数を持つ `If` 演算子では、そのうちの 2 つだけが評価されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-124">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="3d6c2-125">最初の `If` 引数が評価され、結果が `Boolean` 値 (`True` または `False`) としてキャストされます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-125">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="3d6c2-126">値が `True` の場合、`argument2` が評価され、その値が返されますが、`argument3` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-126">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="3d6c2-127">`Boolean` 式の値が `False` の場合、`argument3` が評価され、その値が返されますが、`argument2` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-127">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="3d6c2-128">次の例では、3 つの引数が使用されている場合の `If` の使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-128">The following examples illustrate the use of `If` when three arguments are used:</span></span>

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

<span data-ttu-id="3d6c2-129">次の例は、ショートサーキット評価の値を示しています。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-129">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="3d6c2-130">この例では、変数 `divisor` による変数 `number` の除算が 2 回試行されていることを示しています。これは `divisor` がゼロの場合以外に行われます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-130">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="3d6c2-131">該当する場合は 0 が返されます。また、実行時エラーが発生するため、除算を実行しようとしないでください。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-131">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="3d6c2-132">`If` 式ではショートサーキット評価が使用されるため、最初の引数の値に応じて、2 番目または 3 番目の引数のいずれかが評価されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-132">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="3d6c2-133">最初の引数が true の場合、除数はゼロではなく、2 番目の引数を評価して除算を実行しても問題はありません。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-133">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="3d6c2-134">最初の引数が false の場合、3 番目の引数のみが評価され、0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-134">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="3d6c2-135">したがって、除数が 0 の場合、除算の実行は試みられず、エラーも発生しません。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-135">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="3d6c2-136">ただし、`IIf` ではショートサーキット評価が使用されないため、最初の引数が false の場合でも 2 番目の引数が評価されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-136">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="3d6c2-137">これにより、実行時の 0 除算エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-137">This causes a run-time divide-by-zero error.</span></span>

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="3d6c2-138">2 つの引数を指定して If 演算子を呼び出す場合</span><span class="sxs-lookup"><span data-stu-id="3d6c2-138">If operator called with two arguments</span></span>

<span data-ttu-id="3d6c2-139">`If` の最初の引数は省略できます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-139">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="3d6c2-140">これにより、2 つの引数のみを使用してこの演算子を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-140">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="3d6c2-141">次の一覧は、2 つの引数を使用して `If` 演算子を呼び出す場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-141">The following list applies only when the `If` operator is called with two arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="3d6c2-142">指定項目</span><span class="sxs-lookup"><span data-stu-id="3d6c2-142">Parts</span></span>

|<span data-ttu-id="3d6c2-143">用語</span><span class="sxs-lookup"><span data-stu-id="3d6c2-143">Term</span></span>|<span data-ttu-id="3d6c2-144">定義</span><span class="sxs-lookup"><span data-stu-id="3d6c2-144">Definition</span></span>|
|---|---|
|`argument2`|<span data-ttu-id="3d6c2-145">必須です。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-145">Required.</span></span> <span data-ttu-id="3d6c2-146">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-146">`Object`.</span></span> <span data-ttu-id="3d6c2-147">参照または null 許容値型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-147">Must be a reference or nullable value type.</span></span> <span data-ttu-id="3d6c2-148">`Nothing` 以外に評価される場合、評価され、返されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-148">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|
|`argument3`|<span data-ttu-id="3d6c2-149">必須です。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-149">Required.</span></span> <span data-ttu-id="3d6c2-150">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d6c2-150">`Object`.</span></span> <span data-ttu-id="3d6c2-151">`argument2` が `Nothing` に評価された場合に、評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-151">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|

<span data-ttu-id="3d6c2-152">`Boolean` 引数が省略された場合、最初の引数は参照または null 許容値型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-152">When the `Boolean` argument is omitted, the first argument must be a reference or nullable value type.</span></span> <span data-ttu-id="3d6c2-153">最初の引数が `Nothing` に評価された場合は、2 番目の引数の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-153">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="3d6c2-154">その他すべての場合、最初の引数の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-154">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="3d6c2-155">次の例は、この評価のしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="3d6c2-155">The following example illustrates how this evaluation works:</span></span>

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a><span data-ttu-id="3d6c2-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d6c2-156">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [<span data-ttu-id="3d6c2-157">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="3d6c2-157">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="3d6c2-158">Nothing</span><span class="sxs-lookup"><span data-stu-id="3d6c2-158">Nothing</span></span>](../nothing.md)
