---
description: '詳細情報: Xor 演算子 (Visual Basic)'
title: Xor 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 313ff30ace91b1832c0d35df13294e570a8e410d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795223"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="a614f-103">Xor 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a614f-103">Xor Operator (Visual Basic)</span></span>

<span data-ttu-id="a614f-104">2 つの `Boolean` 式の場合は排他的論理和、2 つの数値式の場合はビットごとの排他を求めます。</span><span class="sxs-lookup"><span data-stu-id="a614f-104">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a614f-105">構文</span><span class="sxs-lookup"><span data-stu-id="a614f-105">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a614f-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="a614f-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="a614f-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="a614f-107">Required.</span></span> <span data-ttu-id="a614f-108">任意の `Boolean` または数値変数。</span><span class="sxs-lookup"><span data-stu-id="a614f-108">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="a614f-109">ブール値の比較の場合、`result` は 2 つの `Boolean` 値の排他的論理和 (排他的論理和演算) です。</span><span class="sxs-lookup"><span data-stu-id="a614f-109">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="a614f-110">ビットごとの演算の場合、`result` は 2 つの数値ビット パターンのビットごとの排他 (ビットごとの排他的論理和演算) を表す数値です。</span><span class="sxs-lookup"><span data-stu-id="a614f-110">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a614f-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="a614f-111">Required.</span></span> <span data-ttu-id="a614f-112">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="a614f-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a614f-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="a614f-113">Required.</span></span> <span data-ttu-id="a614f-114">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="a614f-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a614f-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="a614f-115">Remarks</span></span>  

 <span data-ttu-id="a614f-116">ブール値の比較では、`expression1` と `expression2` のうち 1 つだけが `True` に評価される場合にのみ、`result` は `True` になります。</span><span class="sxs-lookup"><span data-stu-id="a614f-116">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="a614f-117">つまり、`expression1` と `expression2` とが逆の `Boolean` 値に評価される場合、かつその場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="a614f-117">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="a614f-118">次の表は、`result` がどのように決定されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="a614f-118">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a614f-119">`expression1` が次の場合</span><span class="sxs-lookup"><span data-stu-id="a614f-119">If `expression1` is</span></span>|<span data-ttu-id="a614f-120">かつ、`expression2` が次の場合</span><span class="sxs-lookup"><span data-stu-id="a614f-120">And `expression2` is</span></span>|<span data-ttu-id="a614f-121">`result` の値は次のようになります</span><span class="sxs-lookup"><span data-stu-id="a614f-121">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="a614f-122">ブール値の比較では、`Xor` 演算子は常に両方の式を評価します。これには、プロシージャ呼び出しを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a614f-122">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="a614f-123">結果は常に両方のオペランドに依存するため、`Xor` に対応するショートサーキットはありません。</span><span class="sxs-lookup"><span data-stu-id="a614f-123">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="a614f-124">"*ショートサーキット*" 論理演算子については、「[AndAlso 演算子](andalso-operator.md)」、および「[OrElse 演算子](orelse-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a614f-124">For *short-circuiting* logical operators, see [AndAlso Operator](andalso-operator.md) and [OrElse Operator](orelse-operator.md).</span></span>  
  
 <span data-ttu-id="a614f-125">ビットごとの演算の場合、`Xor` 演算子は、2 つの数値式でまったく同じ位置にあるビットのビットごとの比較を実行し、次の表に従って `result` に対応するビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="a614f-125">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a614f-126">`expression1` 内のビットが次の場合</span><span class="sxs-lookup"><span data-stu-id="a614f-126">If bit in `expression1` is</span></span>|<span data-ttu-id="a614f-127">かつ、`expression2` 内のビットが次の場合</span><span class="sxs-lookup"><span data-stu-id="a614f-127">And bit in `expression2` is</span></span>|<span data-ttu-id="a614f-128">`result` 内のビットは次のようになります</span><span class="sxs-lookup"><span data-stu-id="a614f-128">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="a614f-129">1</span><span class="sxs-lookup"><span data-stu-id="a614f-129">1</span></span>|<span data-ttu-id="a614f-130">1</span><span class="sxs-lookup"><span data-stu-id="a614f-130">1</span></span>|<span data-ttu-id="a614f-131">0</span><span class="sxs-lookup"><span data-stu-id="a614f-131">0</span></span>|  
|<span data-ttu-id="a614f-132">1</span><span class="sxs-lookup"><span data-stu-id="a614f-132">1</span></span>|<span data-ttu-id="a614f-133">0</span><span class="sxs-lookup"><span data-stu-id="a614f-133">0</span></span>|<span data-ttu-id="a614f-134">1</span><span class="sxs-lookup"><span data-stu-id="a614f-134">1</span></span>|  
|<span data-ttu-id="a614f-135">0</span><span class="sxs-lookup"><span data-stu-id="a614f-135">0</span></span>|<span data-ttu-id="a614f-136">1</span><span class="sxs-lookup"><span data-stu-id="a614f-136">1</span></span>|<span data-ttu-id="a614f-137">1</span><span class="sxs-lookup"><span data-stu-id="a614f-137">1</span></span>|  
|<span data-ttu-id="a614f-138">0</span><span class="sxs-lookup"><span data-stu-id="a614f-138">0</span></span>|<span data-ttu-id="a614f-139">0</span><span class="sxs-lookup"><span data-stu-id="a614f-139">0</span></span>|<span data-ttu-id="a614f-140">0</span><span class="sxs-lookup"><span data-stu-id="a614f-140">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a614f-141">論理演算子とビット演算子は、他の算術演算子および関係演算子より優先順位が低いので、正確な実行を保証するために、ビットごとの演算はかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="a614f-141">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="a614f-142">たとえば、5 `Xor` 3 は 6 です。</span><span class="sxs-lookup"><span data-stu-id="a614f-142">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="a614f-143">なぜそのようになるのかを確認するには、5 と 3 をそれぞれのバイナリ表現 (101 および 011) に変換します。</span><span class="sxs-lookup"><span data-stu-id="a614f-143">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="a614f-144">次に、前の表を使用して、101 Xor 011 が 110 になることを確認します。これは 10 進数 6 のバイナリ表現です。</span><span class="sxs-lookup"><span data-stu-id="a614f-144">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a614f-145">データの種類</span><span class="sxs-lookup"><span data-stu-id="a614f-145">Data Types</span></span>  

 <span data-ttu-id="a614f-146">オペランドが 1 つの `Boolean` 式と 1 つの数値式で構成されている場合、Visual Basic では `Boolean` 式が数値に変換され (`True` の場合は –1、`False` の場合は 0)、ビットごとの演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a614f-146">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="a614f-147">`Boolean` の比較の場合、結果のデータ型は `Boolean` になります。</span><span class="sxs-lookup"><span data-stu-id="a614f-147">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a614f-148">ビットごとの比較の場合、結果のデータ型は `expression1` および `expression2` のデータ型に適した数値型になります。</span><span class="sxs-lookup"><span data-stu-id="a614f-148">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a614f-149">[演算子の結果のデータ型](data-types-of-operator-results.md)に関するページ内の表 "関係とビットごとの比較" を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a614f-149">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a614f-150">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="a614f-150">Overloading</span></span>  

 <span data-ttu-id="a614f-151">`Xor` 演算子を "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体で、演算子の動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="a614f-151">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a614f-152">コード内で、そのようなクラスまたは構造体に対してこの演算子が使用されている場合は、再定義されたその動作を必ず理解してください。</span><span class="sxs-lookup"><span data-stu-id="a614f-152">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="a614f-153">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a614f-153">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a614f-154">例</span><span class="sxs-lookup"><span data-stu-id="a614f-154">Example</span></span>  

 <span data-ttu-id="a614f-155">次の例では、`Xor` 演算子を使用して、2 つの式の排他的論理和 (排他的論理和演算) を実行します。</span><span class="sxs-lookup"><span data-stu-id="a614f-155">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="a614f-156">結果は、それらの式のうちの 1 つだけが `True` であるかどうかを表す `Boolean` 値となります。</span><span class="sxs-lookup"><span data-stu-id="a614f-156">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="a614f-157">前の例では、それぞれ `False`、`True`、および `False` の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a614f-157">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a614f-158">例</span><span class="sxs-lookup"><span data-stu-id="a614f-158">Example</span></span>  

 <span data-ttu-id="a614f-159">次の例では、`Xor` 演算子を使用して、2 つの数値式の個々のビットに対して排他的論理和 (排他的論理和演算) を実行します。</span><span class="sxs-lookup"><span data-stu-id="a614f-159">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="a614f-160">オペランド内の対応するビットのうちの 1 つだけが 1 に設定されている場合に、結果パターンのビットが設定されます。</span><span class="sxs-lookup"><span data-stu-id="a614f-160">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="a614f-161">前の例では、それぞれ 2、12、14 の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a614f-161">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a614f-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="a614f-162">See also</span></span>

- [<span data-ttu-id="a614f-163">論理演算子とビット処理演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a614f-163">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="a614f-164">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="a614f-164">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a614f-165">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="a614f-165">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a614f-166">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="a614f-166">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
