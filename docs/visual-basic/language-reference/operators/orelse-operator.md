---
description: '詳細情報: OrElse 演算子 (Visual Basic)'
title: OrElse 演算子
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 48ccbda1e0cb4f655b28e902b22fbfe0c3e66ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795327"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="a7e4a-103">OrElse 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7e4a-103">OrElse Operator (Visual Basic)</span></span>

<span data-ttu-id="a7e4a-104">2 つの式の短絡包含的論理和を求めます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-104">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e4a-105">構文</span><span class="sxs-lookup"><span data-stu-id="a7e4a-105">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a7e4a-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="a7e4a-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="a7e4a-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-107">Required.</span></span> <span data-ttu-id="a7e4a-108">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-108">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a7e4a-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-109">Required.</span></span> <span data-ttu-id="a7e4a-110">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-110">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a7e4a-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-111">Required.</span></span> <span data-ttu-id="a7e4a-112">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-112">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7e4a-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="a7e4a-113">Remarks</span></span>  

 <span data-ttu-id="a7e4a-114">コンパイルされたコードが、ある式の評価を別の式の結果に応じてバイパスできる場合、論理演算は "*短絡*" であると言われます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-114">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="a7e4a-115">最初に評価された式の結果によって演算の最終結果が決まる場合、最終結果を変更できないため、2 番目の式を評価する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-115">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="a7e4a-116">バイパスされた式が複雑な場合や、プロシージャ呼び出しが関係している場合に、短絡によってパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-116">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="a7e4a-117">いずれかまたは両方の式が `True` に評価される場合、`result` は `True` です。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-117">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="a7e4a-118">次の表は、`result` がどのように決定されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-118">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a7e4a-119">`expression1` が次の場合</span><span class="sxs-lookup"><span data-stu-id="a7e4a-119">If `expression1` is</span></span>|<span data-ttu-id="a7e4a-120">かつ、`expression2` が次の場合</span><span class="sxs-lookup"><span data-stu-id="a7e4a-120">And `expression2` is</span></span>|<span data-ttu-id="a7e4a-121">`result` の値は次のようになります</span><span class="sxs-lookup"><span data-stu-id="a7e4a-121">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="a7e4a-122">(評価されていない)</span><span class="sxs-lookup"><span data-stu-id="a7e4a-122">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="a7e4a-123">データの種類</span><span class="sxs-lookup"><span data-stu-id="a7e4a-123">Data Types</span></span>  

 <span data-ttu-id="a7e4a-124">`OrElse` 演算子は [Boolean データ型](../data-types/boolean-data-type.md)に対してのみ定義されます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-124">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="a7e4a-125">Visual Basic は、式を評価する前に、必要に応じて各オペランドを `Boolean` に変換します。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-125">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="a7e4a-126">結果を数値型に代入すると、Visual Basic によって `Boolean` からその型への変換が行われ、`False` が `0` になり、`True` が `-1` になります。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-126">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="a7e4a-127">詳細については、[ブール型変換](../data-types/boolean-data-type.md#type-conversions)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-127">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="a7e4a-128">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="a7e4a-128">Overloading</span></span>  

 <span data-ttu-id="a7e4a-129">[Or 演算子](or-operator.md)と [IsTrue 演算子](istrue-operator.md)は "*オーバーロード*" できます。つまり、オペランドがクラスまたは構造体の型を持っているときに、このクラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-129">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a7e4a-130">`Or` と `IsTrue` の演算子をオーバーロードすると、`OrElse` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="a7e4a-131">コードで、`Or` と `IsTrue` をオーバーロードするクラスまたは構造体で `OrElse` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="a7e4a-132">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-132">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7e4a-133">例</span><span class="sxs-lookup"><span data-stu-id="a7e4a-133">Example</span></span>  

 <span data-ttu-id="a7e4a-134">次の例では、`OrElse` 演算子を使用して、2 つの式の論理和を求めます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="a7e4a-135">結果は、2 つの式のいずれかが true かどうかを表す `Boolean` 値です。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="a7e4a-136">最初の式が `True` 場合、2 番目の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="a7e4a-137">前の例では、それぞれ `True`、`True`、`False` の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="a7e4a-138">`firstCheck` の計算では、最初の式が既に `True` であるため、2 番目の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="a7e4a-139">ただし、2 番目の式は `secondCheck` の計算で評価されます。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7e4a-140">例</span><span class="sxs-lookup"><span data-stu-id="a7e4a-140">Example</span></span>  

 <span data-ttu-id="a7e4a-141">次の例は、2 つのプロシージャ呼び出しを含む `If`...`Then` ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="a7e4a-142">最初の呼び出しで `True` が返された場合、2 番目のプロシージャは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="a7e4a-143">コードのこのセクションの実行時に常に実行する必要がある重要なタスクを 2 番目のプロシージャが実行すると場合、予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a7e4a-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="a7e4a-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7e4a-144">See also</span></span>

- [<span data-ttu-id="a7e4a-145">論理演算子とビット処理演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7e4a-145">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="a7e4a-146">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="a7e4a-146">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a7e4a-147">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="a7e4a-147">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a7e4a-148">Or 演算子</span><span class="sxs-lookup"><span data-stu-id="a7e4a-148">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="a7e4a-149">IsTrue 演算子</span><span class="sxs-lookup"><span data-stu-id="a7e4a-149">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="a7e4a-150">Visual Basic の論理演算子とビット演算子</span><span class="sxs-lookup"><span data-stu-id="a7e4a-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
