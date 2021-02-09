---
description: '詳細情報: And 演算子 (Visual Basic)'
title: And 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 238ef0b2f14f2014da6e65684bfac183e03d963e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774279"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="ef043-103">And 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef043-103">And Operator (Visual Basic)</span></span>

<span data-ttu-id="ef043-104">2 つの `Boolean` 式の場合は論理積、2 つの数値式の場合はビットごとの積を求めます。</span><span class="sxs-lookup"><span data-stu-id="ef043-104">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef043-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef043-105">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="ef043-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="ef043-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="ef043-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="ef043-107">Required.</span></span> <span data-ttu-id="ef043-108">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="ef043-108">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="ef043-109">ブール型の比較の場合、`result` は 2 つの `Boolean` 値の論理積となります。</span><span class="sxs-lookup"><span data-stu-id="ef043-109">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="ef043-110">ビットごとの演算の場合、`result` は 2 つの数値ビット パターンのビットごとの積を表す数値です。</span><span class="sxs-lookup"><span data-stu-id="ef043-110">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="ef043-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="ef043-111">Required.</span></span> <span data-ttu-id="ef043-112">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="ef043-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="ef043-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="ef043-113">Required.</span></span> <span data-ttu-id="ef043-114">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="ef043-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef043-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="ef043-115">Remarks</span></span>  

 <span data-ttu-id="ef043-116">ブール値の比較では、`expression1` と `expression2` の両方が `True` に評価される場合にのみ、`result` は `True` になります。</span><span class="sxs-lookup"><span data-stu-id="ef043-116">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="ef043-117">次の表は、`result` がどのように決定されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="ef043-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="ef043-118">`expression1` が次の場合</span><span class="sxs-lookup"><span data-stu-id="ef043-118">If `expression1` is</span></span>|<span data-ttu-id="ef043-119">かつ、`expression2` が次の場合</span><span class="sxs-lookup"><span data-stu-id="ef043-119">And `expression2` is</span></span>|<span data-ttu-id="ef043-120">`result` の値は次のようになります</span><span class="sxs-lookup"><span data-stu-id="ef043-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="ef043-121">ブール値の比較では、`And` 演算子は常に両方の式を評価します。これには、プロシージャ呼び出しを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ef043-121">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="ef043-122">[AndAlso 演算子](andalso-operator.md)は "*ショートサーキット*" を実行します。つまり、`expression1` が `False` の場合、`expression2` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="ef043-122">The [AndAlso Operator](andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="ef043-123">`And` 演算子は、数値に適用される場合、2 つの数値式でまったく同じ位置にあるビットのビットごとの比較を実行し、次の表に従って `result` に対応するビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="ef043-123">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="ef043-124">`expression1` 内のビットが次の場合</span><span class="sxs-lookup"><span data-stu-id="ef043-124">If bit in `expression1` is</span></span>|<span data-ttu-id="ef043-125">かつ、`expression2` 内のビットが次の場合</span><span class="sxs-lookup"><span data-stu-id="ef043-125">And bit in `expression2` is</span></span>|<span data-ttu-id="ef043-126">`result` 内のビットは次のようになります</span><span class="sxs-lookup"><span data-stu-id="ef043-126">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="ef043-127">1</span><span class="sxs-lookup"><span data-stu-id="ef043-127">1</span></span>|<span data-ttu-id="ef043-128">1</span><span class="sxs-lookup"><span data-stu-id="ef043-128">1</span></span>|<span data-ttu-id="ef043-129">1</span><span class="sxs-lookup"><span data-stu-id="ef043-129">1</span></span>|  
|<span data-ttu-id="ef043-130">1</span><span class="sxs-lookup"><span data-stu-id="ef043-130">1</span></span>|<span data-ttu-id="ef043-131">0</span><span class="sxs-lookup"><span data-stu-id="ef043-131">0</span></span>|<span data-ttu-id="ef043-132">0</span><span class="sxs-lookup"><span data-stu-id="ef043-132">0</span></span>|  
|<span data-ttu-id="ef043-133">0</span><span class="sxs-lookup"><span data-stu-id="ef043-133">0</span></span>|<span data-ttu-id="ef043-134">1</span><span class="sxs-lookup"><span data-stu-id="ef043-134">1</span></span>|<span data-ttu-id="ef043-135">0</span><span class="sxs-lookup"><span data-stu-id="ef043-135">0</span></span>|  
|<span data-ttu-id="ef043-136">0</span><span class="sxs-lookup"><span data-stu-id="ef043-136">0</span></span>|<span data-ttu-id="ef043-137">0</span><span class="sxs-lookup"><span data-stu-id="ef043-137">0</span></span>|<span data-ttu-id="ef043-138">0</span><span class="sxs-lookup"><span data-stu-id="ef043-138">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ef043-139">論理演算子とビット処理演算子は、他の算術演算子および関係演算子より優先順位が低いので、正確な結果を確実に得るために、ビットごとの演算はかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef043-139">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="ef043-140">データの種類</span><span class="sxs-lookup"><span data-stu-id="ef043-140">Data Types</span></span>  

 <span data-ttu-id="ef043-141">オペランドが 1 つの `Boolean` 式と 1 つの数値式で構成されている場合、Visual Basic は `Boolean` 式を数値に変換し (`True` の場合は 1、`False` の場合は 0)、ビットごとの演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="ef043-141">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="ef043-142">ブール値の比較の場合、結果のデータ型は `Boolean` になります。</span><span class="sxs-lookup"><span data-stu-id="ef043-142">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="ef043-143">ビットごとの比較の場合、結果のデータ型は `expression1` および `expression2` のデータ型に適した数値型になります。</span><span class="sxs-lookup"><span data-stu-id="ef043-143">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="ef043-144">「[演算子の結果のデータ型](data-types-of-operator-results.md)」の「関係とビットごとの比較」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef043-144">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef043-145">`And` 演算子は "*オーバーロード*" できます。つまり、オペランドがクラスまたは構造体の型を持っているときに、クラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="ef043-145">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ef043-146">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ef043-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ef043-147">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef043-147">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef043-148">例</span><span class="sxs-lookup"><span data-stu-id="ef043-148">Example</span></span>  

 <span data-ttu-id="ef043-149">次の例では、`And` 演算子を使用して、2 つの式の論理積を実行します。</span><span class="sxs-lookup"><span data-stu-id="ef043-149">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="ef043-150">結果は、両方の式が `True` かどうかを表す `Boolean` 値です。</span><span class="sxs-lookup"><span data-stu-id="ef043-150">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="ef043-151">前の例では、それぞれ `True` と `False` の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef043-151">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef043-152">例</span><span class="sxs-lookup"><span data-stu-id="ef043-152">Example</span></span>  

 <span data-ttu-id="ef043-153">次の例では、`And` 演算子を使用して、2 つの数値式の個々のビットに対して論理積を実行します。</span><span class="sxs-lookup"><span data-stu-id="ef043-153">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="ef043-154">オペランドの対応するビットが両方とも 1 に設定されている場合、結果パターンのビットが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ef043-154">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="ef043-155">前の例では、それぞれ 8、2、および 0 の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef043-155">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef043-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef043-156">See also</span></span>

- [<span data-ttu-id="ef043-157">論理演算子とビット処理演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef043-157">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="ef043-158">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="ef043-158">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ef043-159">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="ef043-159">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ef043-160">AndAlso 演算子</span><span class="sxs-lookup"><span data-stu-id="ef043-160">AndAlso Operator</span></span>](andalso-operator.md)
- [<span data-ttu-id="ef043-161">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="ef043-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
