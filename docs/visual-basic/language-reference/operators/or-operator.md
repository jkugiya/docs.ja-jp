---
description: '詳細情報: Or 演算子 (Visual Basic)'
title: Or 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: dfc50af2298c162707976e4b2eda9e9536aa64bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730331"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="3312c-103">Or 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3312c-103">Or Operator (Visual Basic)</span></span>

<span data-ttu-id="3312c-104">2 つの `Boolean` 式の場合は論理和演算、2 つの数値式の場合はビットごとの論理和演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="3312c-104">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3312c-105">構文</span><span class="sxs-lookup"><span data-stu-id="3312c-105">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="3312c-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="3312c-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="3312c-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="3312c-107">Required.</span></span> <span data-ttu-id="3312c-108">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="3312c-108">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="3312c-109">`Boolean` の比較の場合、`result` は 2 つの `Boolean` 値の包含論理和演算となります。</span><span class="sxs-lookup"><span data-stu-id="3312c-109">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="3312c-110">ビットごとの演算の場合、`result` は 2 つの数値ビット パターンのビットごとの包含論理和演算を表す数値です。</span><span class="sxs-lookup"><span data-stu-id="3312c-110">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="3312c-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="3312c-111">Required.</span></span> <span data-ttu-id="3312c-112">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="3312c-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="3312c-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="3312c-113">Required.</span></span> <span data-ttu-id="3312c-114">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="3312c-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3312c-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="3312c-115">Remarks</span></span>  

 <span data-ttu-id="3312c-116">`Boolean` の比較では、`expression1` と `expression2` の両方が `False` に評価された場合にのみ、`result` は `False` になります。</span><span class="sxs-lookup"><span data-stu-id="3312c-116">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="3312c-117">次の表は、`result` がどのように決定されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="3312c-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="3312c-118">`expression1` が次の場合</span><span class="sxs-lookup"><span data-stu-id="3312c-118">If `expression1` is</span></span>|<span data-ttu-id="3312c-119">かつ、`expression2` が次の場合</span><span class="sxs-lookup"><span data-stu-id="3312c-119">And `expression2` is</span></span>|<span data-ttu-id="3312c-120">`result` の値は次のようになります</span><span class="sxs-lookup"><span data-stu-id="3312c-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="3312c-121">`Boolean` の比較では、`Or` 演算子は常に両方の式を評価します。これには、プロシージャ呼び出しの実行を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3312c-121">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="3312c-122">[OrElse 演算子](orelse-operator.md)は "*ショートサーキット*" を実行します。つまり、`expression1` が `True` の場合、`expression2` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="3312c-122">The [OrElse Operator](orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="3312c-123">ビットごとの演算の場合、`Or` 演算子は、2 つの数値式でまったく同じ位置にあるビットのビットごとの比較を実行し、次の表に従って `result` に対応するビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="3312c-123">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="3312c-124">`expression1` 内のビットが次の場合</span><span class="sxs-lookup"><span data-stu-id="3312c-124">If bit in `expression1` is</span></span>|<span data-ttu-id="3312c-125">かつ、`expression2` 内のビットが次の場合</span><span class="sxs-lookup"><span data-stu-id="3312c-125">And bit in `expression2` is</span></span>|<span data-ttu-id="3312c-126">`result` 内のビットは次のようになります</span><span class="sxs-lookup"><span data-stu-id="3312c-126">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="3312c-127">1</span><span class="sxs-lookup"><span data-stu-id="3312c-127">1</span></span>|<span data-ttu-id="3312c-128">1</span><span class="sxs-lookup"><span data-stu-id="3312c-128">1</span></span>|<span data-ttu-id="3312c-129">1</span><span class="sxs-lookup"><span data-stu-id="3312c-129">1</span></span>|  
|<span data-ttu-id="3312c-130">1</span><span class="sxs-lookup"><span data-stu-id="3312c-130">1</span></span>|<span data-ttu-id="3312c-131">0</span><span class="sxs-lookup"><span data-stu-id="3312c-131">0</span></span>|<span data-ttu-id="3312c-132">1</span><span class="sxs-lookup"><span data-stu-id="3312c-132">1</span></span>|  
|<span data-ttu-id="3312c-133">0</span><span class="sxs-lookup"><span data-stu-id="3312c-133">0</span></span>|<span data-ttu-id="3312c-134">1</span><span class="sxs-lookup"><span data-stu-id="3312c-134">1</span></span>|<span data-ttu-id="3312c-135">1</span><span class="sxs-lookup"><span data-stu-id="3312c-135">1</span></span>|  
|<span data-ttu-id="3312c-136">0</span><span class="sxs-lookup"><span data-stu-id="3312c-136">0</span></span>|<span data-ttu-id="3312c-137">0</span><span class="sxs-lookup"><span data-stu-id="3312c-137">0</span></span>|<span data-ttu-id="3312c-138">0</span><span class="sxs-lookup"><span data-stu-id="3312c-138">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3312c-139">論理およびビット処理演算子は、他の算術演算子および関係演算子より優先順位が低いので、正確に実行するために、ビットごとの演算はかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="3312c-139">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="3312c-140">データの種類</span><span class="sxs-lookup"><span data-stu-id="3312c-140">Data Types</span></span>  

 <span data-ttu-id="3312c-141">オペランドが 1 つの `Boolean` 式と 1 つの数値式で構成されている場合、Visual Basic では `Boolean` 式が数値に変換され (`True` の場合は –1、`False` の場合は 0)、ビットごとの演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3312c-141">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="3312c-142">`Boolean` の比較の場合、結果のデータ型は `Boolean` になります。</span><span class="sxs-lookup"><span data-stu-id="3312c-142">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="3312c-143">ビットごとの比較の場合、結果のデータ型は `expression1` および `expression2` のデータ型に適した数値型になります。</span><span class="sxs-lookup"><span data-stu-id="3312c-143">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="3312c-144">[演算子の結果のデータ型](data-types-of-operator-results.md)に関するページ内の表 "関係とビットごとの比較" を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3312c-144">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3312c-145">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="3312c-145">Overloading</span></span>  

 <span data-ttu-id="3312c-146">`Or` 演算子は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体で、演算子の動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="3312c-146">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3312c-147">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3312c-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3312c-148">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3312c-148">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3312c-149">例</span><span class="sxs-lookup"><span data-stu-id="3312c-149">Example</span></span>  

 <span data-ttu-id="3312c-150">次の例では、`Or` 演算子を使用して、2 つの式の包含論理和演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="3312c-150">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="3312c-151">結果は、2 つの式のいずれかが `True` かどうかを表す `Boolean` 値です。</span><span class="sxs-lookup"><span data-stu-id="3312c-151">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="3312c-152">前の例では、それぞれ `True`、`True`、`False` の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3312c-152">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3312c-153">例</span><span class="sxs-lookup"><span data-stu-id="3312c-153">Example</span></span>  

 <span data-ttu-id="3312c-154">次の例では、`Or` 演算子を使用して、2 つの数値式の個々のビットに対して包含論理和演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="3312c-154">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="3312c-155">オペランドの対応するビットのいずれかが 1 に設定されている場合、結果パターンのビットが設定されます。</span><span class="sxs-lookup"><span data-stu-id="3312c-155">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="3312c-156">前の例では、それぞれ 10、14、14 の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3312c-156">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3312c-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="3312c-157">See also</span></span>

- [<span data-ttu-id="3312c-158">論理演算子とビット処理演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3312c-158">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="3312c-159">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="3312c-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="3312c-160">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="3312c-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="3312c-161">OrElse 演算子</span><span class="sxs-lookup"><span data-stu-id="3312c-161">OrElse Operator</span></span>](orelse-operator.md)
- [<span data-ttu-id="3312c-162">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="3312c-162">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
