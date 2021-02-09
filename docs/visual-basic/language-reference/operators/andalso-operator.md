---
description: '詳細情報: AndAlso 演算子 (Visual Basic)'
title: AndAlso 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: dcf6c2685bf8f9ffee27b00543786cd3b315b327
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774266"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="b7253-103">AndAlso 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7253-103">AndAlso Operator (Visual Basic)</span></span>

<span data-ttu-id="b7253-104">2 つの式の短絡論理積を求めます。</span><span class="sxs-lookup"><span data-stu-id="b7253-104">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7253-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7253-105">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b7253-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="b7253-106">Parts</span></span>  
  
|<span data-ttu-id="b7253-107">用語</span><span class="sxs-lookup"><span data-stu-id="b7253-107">Term</span></span>|<span data-ttu-id="b7253-108">定義</span><span class="sxs-lookup"><span data-stu-id="b7253-108">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="b7253-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="b7253-109">Required.</span></span> <span data-ttu-id="b7253-110">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7253-110">Any `Boolean` expression.</span></span> <span data-ttu-id="b7253-111">結果は、2 つの式の比較の `Boolean` 結果です。</span><span class="sxs-lookup"><span data-stu-id="b7253-111">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="b7253-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="b7253-112">Required.</span></span> <span data-ttu-id="b7253-113">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7253-113">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="b7253-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="b7253-114">Required.</span></span> <span data-ttu-id="b7253-115">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7253-115">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7253-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="b7253-116">Remarks</span></span>  

 <span data-ttu-id="b7253-117">コンパイルされたコードが、ある式の評価を別の式の結果に応じてバイパスできる場合、論理演算は "*短絡*" であると言われます。</span><span class="sxs-lookup"><span data-stu-id="b7253-117">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="b7253-118">最初に評価された式の結果によって演算の最終結果が決まる場合、最終結果を変更できないため、2 番目の式を評価する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b7253-118">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="b7253-119">バイパスされた式が複雑な場合や、プロシージャ呼び出しが関係している場合に、短絡によってパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="b7253-119">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="b7253-120">両方の式が `True` に評価される場合、`result` は `True` です。</span><span class="sxs-lookup"><span data-stu-id="b7253-120">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="b7253-121">次の表は、`result` の判定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b7253-121">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="b7253-122">`expression1` が次の場合</span><span class="sxs-lookup"><span data-stu-id="b7253-122">If `expression1` is</span></span>|<span data-ttu-id="b7253-123">かつ、`expression2` が次の場合</span><span class="sxs-lookup"><span data-stu-id="b7253-123">And `expression2` is</span></span>|<span data-ttu-id="b7253-124">`result` の値は次のようになります</span><span class="sxs-lookup"><span data-stu-id="b7253-124">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="b7253-125">(評価されていない)</span><span class="sxs-lookup"><span data-stu-id="b7253-125">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="b7253-126">データの種類</span><span class="sxs-lookup"><span data-stu-id="b7253-126">Data Types</span></span>  

 <span data-ttu-id="b7253-127">`AndAlso` 演算子は [Boolean データ型](../data-types/boolean-data-type.md)に対してのみ定義されます。</span><span class="sxs-lookup"><span data-stu-id="b7253-127">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="b7253-128">Visual Basic は、式を評価する前に、必要に応じて各オペランドを `Boolean` に変換します。</span><span class="sxs-lookup"><span data-stu-id="b7253-128">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="b7253-129">結果を数値型に代入すると、Visual Basic によって `Boolean` からその型への変換が行われ、`False` が `0` になり、`True` が `-1` になります。</span><span class="sxs-lookup"><span data-stu-id="b7253-129">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="b7253-130">詳細については、[ブール型変換](../data-types/boolean-data-type.md#type-conversions)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b7253-130">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="b7253-131">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="b7253-131">Overloading</span></span>  

 <span data-ttu-id="b7253-132">[And 演算子](and-operator.md)と [IsFalse 演算子](isfalse-operator.md)は "*オーバーロード*" できます。つまり、オペランドがあるクラスまたは構造体の型を持っているときに、そのクラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="b7253-132">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b7253-133">`And` と `IsFalse` の演算子をオーバーロードすると、`AndAlso` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="b7253-133">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="b7253-134">コードで、`And` と `IsFalse` をオーバーロードするクラスまたは構造体で `AndAlso` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b7253-134">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="b7253-135">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7253-135">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7253-136">例</span><span class="sxs-lookup"><span data-stu-id="b7253-136">Example</span></span>  

 <span data-ttu-id="b7253-137">次の例では、`AndAlso` 演算子を使用して、2 つの式の論理積を求めます。</span><span class="sxs-lookup"><span data-stu-id="b7253-137">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="b7253-138">結果は、結合した式全体が真かどうかを表す `Boolean` 値です。</span><span class="sxs-lookup"><span data-stu-id="b7253-138">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="b7253-139">最初の式が `False` の場合、2 番目の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="b7253-139">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="b7253-140">前の例では、それぞれ `True`、`False`、`False` の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b7253-140">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="b7253-141">`secondCheck` の計算では、最初の式が既に `False` であるため、2 番目の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="b7253-141">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="b7253-142">ただし、2 番目の式は `thirdCheck` の計算で評価されます。</span><span class="sxs-lookup"><span data-stu-id="b7253-142">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7253-143">例</span><span class="sxs-lookup"><span data-stu-id="b7253-143">Example</span></span>  

 <span data-ttu-id="b7253-144">次の例は、配列の要素の中から特定の値を検索する `Function` プロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="b7253-144">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="b7253-145">配列が空の場合、または配列の長さが超過した場合、`While` ステートメントは、検索値に対する配列要素のテストを行いません。</span><span class="sxs-lookup"><span data-stu-id="b7253-145">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="b7253-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7253-146">See also</span></span>

- [<span data-ttu-id="b7253-147">論理演算子とビット処理演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7253-147">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="b7253-148">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="b7253-148">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b7253-149">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="b7253-149">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b7253-150">And 演算子</span><span class="sxs-lookup"><span data-stu-id="b7253-150">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="b7253-151">IsFalse 演算子</span><span class="sxs-lookup"><span data-stu-id="b7253-151">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="b7253-152">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="b7253-152">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
