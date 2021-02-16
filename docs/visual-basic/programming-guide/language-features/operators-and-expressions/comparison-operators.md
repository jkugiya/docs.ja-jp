---
description: '詳細情報: Visual Basic における比較演算子'
title: 比較演算子
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: f16b30ca3a0cd5aa4bd5c0b2673a51205714a00c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476411"
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="5bb8c-103">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="5bb8c-103">Comparison Operators in Visual Basic</span></span>

<span data-ttu-id="5bb8c-104">比較演算子は、2 つの式を比較し、それらの値の関係を表す `Boolean` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-104">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="5bb8c-105">数値を比較するための演算子、文字列を比較するための演算子、およびオブジェクトを比較するための演算子があります。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-105">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="5bb8c-106">ここでは、3 種類のすべての演算子について説明します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-106">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="5bb8c-107">数値の比較</span><span class="sxs-lookup"><span data-stu-id="5bb8c-107">Comparing Numeric Values</span></span>  

 <span data-ttu-id="5bb8c-108">Visual Basic は、6 つの数値比較演算子を使用して数値を比較します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-108">Visual Basic compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="5bb8c-109">各演算子は、数値として評価される 2 つの式をオペランドとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-109">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="5bb8c-110">次の表に、演算子の一覧とそれぞれの例を示します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-110">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="5bb8c-111">演算子</span><span class="sxs-lookup"><span data-stu-id="5bb8c-111">Operator</span></span>|<span data-ttu-id="5bb8c-112">テストされた条件</span><span class="sxs-lookup"><span data-stu-id="5bb8c-112">Condition tested</span></span>|<span data-ttu-id="5bb8c-113">使用例</span><span class="sxs-lookup"><span data-stu-id="5bb8c-113">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="5bb8c-114">`=` (等値)</span><span class="sxs-lookup"><span data-stu-id="5bb8c-114">`=` (Equality)</span></span>|<span data-ttu-id="5bb8c-115">最初の式の値が 2 番目の式の値と等しいかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-115">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="5bb8c-116">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-116">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="5bb8c-117">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-117">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="5bb8c-118">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-118">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="5bb8c-119">`<>` (非等値)</span><span class="sxs-lookup"><span data-stu-id="5bb8c-119">`<>` (Inequality)</span></span>|<span data-ttu-id="5bb8c-120">最初の式の値が 2 番目の式の値と等しくないかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-120">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="5bb8c-121">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-121">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="5bb8c-122">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-122">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="5bb8c-123">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-123">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="5bb8c-124">`<` (より小さい)</span><span class="sxs-lookup"><span data-stu-id="5bb8c-124">`<` (Less than)</span></span>|<span data-ttu-id="5bb8c-125">最初の式の値が 2 番目の式の値より小さいかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-125">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="5bb8c-126">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-126">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="5bb8c-127">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-127">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="5bb8c-128">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-128">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="5bb8c-129">`>` (より大きい)</span><span class="sxs-lookup"><span data-stu-id="5bb8c-129">`>` (Greater than)</span></span>|<span data-ttu-id="5bb8c-130">最初の式の値が 2 番目の式の値より大きいかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-130">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="5bb8c-131">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-131">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="5bb8c-132">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-132">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="5bb8c-133">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-133">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="5bb8c-134">`<=` (以下)</span><span class="sxs-lookup"><span data-stu-id="5bb8c-134">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="5bb8c-135">最初の式の値が 2 番目の式の値以下であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-135">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="5bb8c-136">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-136">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="5bb8c-137">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-137">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="5bb8c-138">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-138">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="5bb8c-139">`>=` (以上)</span><span class="sxs-lookup"><span data-stu-id="5bb8c-139">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="5bb8c-140">最初の式の値が 2 番目の式の値以上であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-140">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="5bb8c-141">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-141">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="5bb8c-142">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-142">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="5bb8c-143">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="5bb8c-143">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="5bb8c-144">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="5bb8c-144">Comparing Strings</span></span>  

 <span data-ttu-id="5bb8c-145">Visual Basic は、[Like 演算子](../../../language-reference/operators/like-operator.md)および数値比較演算子を使用して文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-145">Visual Basic compares strings using the [Like Operator](../../../language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="5bb8c-146">`Like` 演算子を使用すると、パターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-146">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="5bb8c-147">その後、文字列がパターンと比較され、一致する場合、結果は `True` です。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-147">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="5bb8c-148">それ以外の場合、結果は `False` です。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-148">Otherwise, the result is `False`.</span></span> <span data-ttu-id="5bb8c-149">数値演算子を使用すると、次の例に示すように、並べ替え順序に基づいて `String` 値を比較できます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-149">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="5bb8c-150">前の例の結果は、最初の文字列の最初の文字が 2 番目の文字列の最初の文字の前にあるため、`True` です。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-150">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="5bb8c-151">最初の文字が等しい場合、比較は両方の文字列の次の文字に続き、以下同様に続きます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-151">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="5bb8c-152">次の例に示すように、等値演算子を使用して文字列の等価性をテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-152">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="5bb8c-153">"aa" や "aaa" のように、ある文字列が別の文字列のプレフィックスである場合、長い文字列は短い文字列よりも大きいと見なされます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-153">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="5bb8c-154">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-154">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="5bb8c-155">並べ替え順序は、`Option Compare` の設定に応じて、バイナリ比較またはテキスト比較のいずれかに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-155">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="5bb8c-156">詳細については、「[Option Compare ステートメント](../../../language-reference/statements/option-compare-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-156">For more information see [Option Compare Statement](../../../language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="5bb8c-157">オブジェクトの比較</span><span class="sxs-lookup"><span data-stu-id="5bb8c-157">Comparing Objects</span></span>  

 <span data-ttu-id="5bb8c-158">Visual Basic は、[Is 演算子](../../../language-reference/operators/is-operator.md)および [IsNot 演算子](../../../language-reference/operators/isnot-operator.md)を使用して 2 つのオブジェクト参照変数を比較します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-158">Visual Basic compares two object reference variables with the [Is Operator](../../../language-reference/operators/is-operator.md) and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="5bb8c-159">これらの演算子のいずれかを使用して、2 つの参照変数が同じオブジェクト インスタンスを参照しているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-159">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="5bb8c-160">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-160">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 <span data-ttu-id="5bb8c-161">前の例では、両方の変数が同じインスタンスを参照しているため、`x Is y` は `True` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-161">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="5bb8c-162">この結果を次の例と比較してください。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-162">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 <span data-ttu-id="5bb8c-163">前の例では、`x Is y` は `False` と評価されます。これは、変数が同じ型のオブジェクトを参照しているにもかかわらず、その型の異なるインスタンスを参照しているためです。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-163">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="5bb8c-164">同じインスタンスを指していない 2 つのオブジェクトをテストする場合は、`IsNot` 演算子を使用すると、`Not` と `Is` の文法的にぎこちない組み合わせを回避できます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-164">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="5bb8c-165">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-165">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 <span data-ttu-id="5bb8c-166">前の例では、`If a IsNot b` は `If Not a Is b` に相当します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-166">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="5bb8c-167">オブジェクトの種類の比較</span><span class="sxs-lookup"><span data-stu-id="5bb8c-167">Comparing Object Type</span></span>  

 <span data-ttu-id="5bb8c-168">`TypeOf`...`Is` 式を使用して、オブジェクトが特定の型であるかどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-168">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="5bb8c-169">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-169">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="5bb8c-170">`typename` がインターフェイス型を指定するとき、オブジェクトがインターフェイス型を実装している場合、`TypeOf`...`Is` 式は `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-170">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="5bb8c-171">`typename` がクラス型の場合、オブジェクトが指定されたクラスのインスタンスであるか、または指定されたクラスから派生したクラスのインスタンスである場合、式は `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-171">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="5bb8c-172">次の例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-172">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 <span data-ttu-id="5bb8c-173">前の例では、`TypeOf x Is Control` 式は `True` と評価されます。これは、`x` の型が `Button` であり、`Control` から継承されているためです。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-173">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="5bb8c-174">詳細については、「[TypeOf 演算子](../../../language-reference/operators/typeof-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bb8c-174">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb8c-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bb8c-175">See also</span></span>

- [<span data-ttu-id="5bb8c-176">値の比較</span><span class="sxs-lookup"><span data-stu-id="5bb8c-176">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="5bb8c-177">比較演算子</span><span class="sxs-lookup"><span data-stu-id="5bb8c-177">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="5bb8c-178">演算子</span><span class="sxs-lookup"><span data-stu-id="5bb8c-178">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="5bb8c-179">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="5bb8c-179">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="5bb8c-180">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="5bb8c-180">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="5bb8c-181">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="5bb8c-181">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
