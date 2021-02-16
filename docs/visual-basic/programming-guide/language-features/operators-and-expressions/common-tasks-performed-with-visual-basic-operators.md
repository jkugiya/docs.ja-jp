---
description: '詳細情報: Visual Basic の演算子で実行される一般的な演算'
title: Visual Basic の演算子で実行される一般的な演算
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], logical
- operators [Visual Basic], string concatenation
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- operators [Visual Basic], arithmetic
- operators [Visual Basic], string comparison
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- operators [Visual Basic], comparison
- operators [Visual Basic], short-circuiting logical
ms.assetid: d181afe5-fafa-460f-a13b-81203f6f4587
ms.openlocfilehash: 5103241c7c92ffe7264178e9abb6a56ba03d4b52
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465263"
---
# <a name="common-tasks-performed-with-visual-basic-operators"></a><span data-ttu-id="6835e-103">Visual Basic の演算子で実行される一般的な演算</span><span class="sxs-lookup"><span data-stu-id="6835e-103">Common Tasks Performed with Visual Basic Operators</span></span>

<span data-ttu-id="6835e-104">演算子によって、"*オペランド*" と呼ばれる 1 つ以上の式を含む多くの一般的なタスクが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6835e-104">Operators perform many common tasks involving one or more expressions called *operands*.</span></span>  
  
## <a name="arithmetic-and-bit-shift-tasks"></a><span data-ttu-id="6835e-105">算術とビットシフト タスク</span><span class="sxs-lookup"><span data-stu-id="6835e-105">Arithmetic and Bit-shift Tasks</span></span>  

 <span data-ttu-id="6835e-106">次の表は、使用できる算術演算とビットシフト演算をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6835e-106">The following table summarizes the available arithmetic and bit-shift operations.</span></span>  
  
|<span data-ttu-id="6835e-107">終了</span><span class="sxs-lookup"><span data-stu-id="6835e-107">To</span></span>|<span data-ttu-id="6835e-108">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="6835e-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="6835e-109">ある数値をもう 1 つの数値に加算します</span><span class="sxs-lookup"><span data-stu-id="6835e-109">Add one numeric value to another</span></span>|[<span data-ttu-id="6835e-110">+ 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-110">+ Operator</span></span>](../../../language-reference/operators/addition-operator.md)|  
|<span data-ttu-id="6835e-111">ある数値からもう 1 つの数値を減算します</span><span class="sxs-lookup"><span data-stu-id="6835e-111">Subtract one numeric value from another</span></span>|[<span data-ttu-id="6835e-112">- 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6835e-112">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="6835e-113">ある数値の符号を反転します</span><span class="sxs-lookup"><span data-stu-id="6835e-113">Reverse the sign of a numeric value</span></span>|[<span data-ttu-id="6835e-114">- 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6835e-114">- Operator (Visual Basic)</span></span>](../../../language-reference/operators/subtraction-operator.md)|  
|<span data-ttu-id="6835e-115">ある数値にもう 1 つの数値を乗算します</span><span class="sxs-lookup"><span data-stu-id="6835e-115">Multiply one numeric value by another</span></span>|[<span data-ttu-id="6835e-116">\* 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-116">\* Operator</span></span>](../../../language-reference/operators/multiplication-operator.md)|  
|<span data-ttu-id="6835e-117">ある数値をもう 1 つの数値に除算します</span><span class="sxs-lookup"><span data-stu-id="6835e-117">Divide one numeric value into another</span></span>|[<span data-ttu-id="6835e-118">/ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6835e-118">/ Operator (Visual Basic)</span></span>](../../../language-reference/operators/floating-point-division-operator.md)|  
|<span data-ttu-id="6835e-119">ある数値をもう 1 つの数値で除算した商を求めます (剰余なし)</span><span class="sxs-lookup"><span data-stu-id="6835e-119">Find the quotient of one numeric value divided by another (without the remainder)</span></span>|[<span data-ttu-id="6835e-120">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6835e-120">\ Operator (Visual Basic)</span></span>](../../../language-reference/operators/integer-division-operator.md)|  
|<span data-ttu-id="6835e-121">ある数値をもう 1 つの数値で除算した剰余を求めます (商なし)</span><span class="sxs-lookup"><span data-stu-id="6835e-121">Find the remainder of one numeric value divided by another (without the quotient)</span></span>|[<span data-ttu-id="6835e-122">Mod 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-122">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)|  
|<span data-ttu-id="6835e-123">ある数値をもう 1 つの数値のべき乗にします</span><span class="sxs-lookup"><span data-stu-id="6835e-123">Raise one numeric value to the power of another</span></span>|[<span data-ttu-id="6835e-124">^ 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-124">^ Operator</span></span>](../../../language-reference/operators/exponentiation-operator.md)|  
|<span data-ttu-id="6835e-125">数値のビット パターンを左にシフトします</span><span class="sxs-lookup"><span data-stu-id="6835e-125">Shift the bit pattern of a numeric value to the left</span></span>|[<span data-ttu-id="6835e-126"><\< 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-126"><\< Operator</span></span>](../../../language-reference/operators/left-shift-operator.md)|  
|<span data-ttu-id="6835e-127">数値のビット パターンを右にシフトします</span><span class="sxs-lookup"><span data-stu-id="6835e-127">Shift the bit pattern of a numeric value to the right</span></span>|[<span data-ttu-id="6835e-128">>> 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-128">>> Operator</span></span>](../../../language-reference/operators/right-shift-operator.md)|  
  
## <a name="comparison-tasks"></a><span data-ttu-id="6835e-129">比較タスク</span><span class="sxs-lookup"><span data-stu-id="6835e-129">Comparison Tasks</span></span>  

 <span data-ttu-id="6835e-130">次の表は、使用できる比較演算をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6835e-130">The following table summarizes the available comparison operations.</span></span>  
  
|<span data-ttu-id="6835e-131">終了</span><span class="sxs-lookup"><span data-stu-id="6835e-131">To</span></span>|<span data-ttu-id="6835e-132">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="6835e-132">See</span></span>|  
|---|---|  
|<span data-ttu-id="6835e-133">2 つの値が等しいかどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-133">Determine whether two values are equal</span></span>|<span data-ttu-id="6835e-134">`=` 演算子 ([Visual Basic の比較演算子](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-134">`=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="6835e-135">2 つの値が等しくないかどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-135">Determine whether two values are unequal</span></span>|<span data-ttu-id="6835e-136">`<>` 演算子 ([Visual Basic の比較演算子](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-136">`<>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="6835e-137">ある値がもう 1 つの値より小さいかどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-137">Determine whether one value is less than another</span></span>|<span data-ttu-id="6835e-138">`<` 演算子 ([Visual Basic の比較演算子](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-138">`<` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="6835e-139">ある値がもう 1 つの値より大きいかどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-139">Determine whether one value is greater than another</span></span>|<span data-ttu-id="6835e-140">`>` 演算子 ([Visual Basic の比較演算子](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-140">`>` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="6835e-141">ある値がもう 1 つの値以下かどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-141">Determine whether one value is less than or equal to another</span></span>|<span data-ttu-id="6835e-142">`<=` 演算子 ([Visual Basic の比較演算子](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-142">`<=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="6835e-143">ある値がもう 1 つの値以上かどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-143">Determine whether one value is greater than or equal to another</span></span>|<span data-ttu-id="6835e-144">`>=` 演算子 ([Visual Basic の比較演算子](comparison-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-144">`>=` Operator ([Comparison Operators in Visual Basic](comparison-operators.md))</span></span>|  
|<span data-ttu-id="6835e-145">2 つのオブジェクト変数が同じオブジェクト インスタンスを参照しているかどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-145">Determine whether two object variables refer to the same object instance</span></span>|[<span data-ttu-id="6835e-146">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-146">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)|  
|<span data-ttu-id="6835e-147">2 つのオブジェクト変数が異なるオブジェクト インスタンスを参照しているかどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-147">Determine whether two object variables refer to different object instances</span></span>|[<span data-ttu-id="6835e-148">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-148">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)|  
|<span data-ttu-id="6835e-149">オブジェクトが特定の型であるかどうかを判断します</span><span class="sxs-lookup"><span data-stu-id="6835e-149">Determine whether an object is of a specific type</span></span>|[<span data-ttu-id="6835e-150">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-150">TypeOf Operator</span></span>](../../../language-reference/operators/typeof-operator.md)|  
  
## <a name="concatenation-tasks"></a><span data-ttu-id="6835e-151">連結タスク</span><span class="sxs-lookup"><span data-stu-id="6835e-151">Concatenation Tasks</span></span>  

 <span data-ttu-id="6835e-152">次の表は、使用できる連結演算をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6835e-152">The following table summarizes the available concatenation operations.</span></span>  
  
|<span data-ttu-id="6835e-153">終了</span><span class="sxs-lookup"><span data-stu-id="6835e-153">To</span></span>|<span data-ttu-id="6835e-154">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="6835e-154">See</span></span>|  
|---|---|  
|<span data-ttu-id="6835e-155">複数の文字列を 1 つの文字列に結合します</span><span class="sxs-lookup"><span data-stu-id="6835e-155">Join multiple strings into a single string</span></span>|<span data-ttu-id="6835e-156">`&` 演算子 ([Visual Basic の連結演算子](concatenation-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-156">`&` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
|<span data-ttu-id="6835e-157">数値と文字列値を結合します</span><span class="sxs-lookup"><span data-stu-id="6835e-157">Join numeric values with string values</span></span>|<span data-ttu-id="6835e-158">`+` 演算子 ([Visual Basic の連結演算子](concatenation-operators.md))</span><span class="sxs-lookup"><span data-stu-id="6835e-158">`+` Operator ([Concatenation Operators in Visual Basic](concatenation-operators.md))</span></span>|  
  
## <a name="logical-and-bitwise-tasks"></a><span data-ttu-id="6835e-159">論理タスクとビットごとのタスク</span><span class="sxs-lookup"><span data-stu-id="6835e-159">Logical and Bitwise Tasks</span></span>  

 <span data-ttu-id="6835e-160">次の表は、使用できる論理演算とビットごとの演算をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6835e-160">The following table summarizes the available logical and bitwise operations.</span></span>  
  
|<span data-ttu-id="6835e-161">終了</span><span class="sxs-lookup"><span data-stu-id="6835e-161">To</span></span>|<span data-ttu-id="6835e-162">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="6835e-162">See</span></span>|  
|---|---|  
|<span data-ttu-id="6835e-163">ブール値に対して論理否定を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-163">Perform logical negation on a Boolean value</span></span>|[<span data-ttu-id="6835e-164">Not 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-164">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
|<span data-ttu-id="6835e-165">2 つのブール値に対して論理積を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-165">Perform logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="6835e-166">And 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-166">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="6835e-167">2 つのブール値に対して包括的論理和演算を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-167">Perform inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="6835e-168">Or 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-168">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="6835e-169">2 つのブール値に対して排他的論理和演算を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-169">Perform exclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="6835e-170">Xor 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-170">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="6835e-171">2 つのブール値に対して短絡論理積を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-171">Perform short-circuited logical conjunction on two Boolean values</span></span>|[<span data-ttu-id="6835e-172">AndAlso 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-172">AndAlso Operator</span></span>](../../../language-reference/operators/andalso-operator.md)|  
|<span data-ttu-id="6835e-173">2 つのブール値に対して短絡包括的論理和演算を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-173">Perform short-circuited inclusive logical disjunction on two Boolean values</span></span>|[<span data-ttu-id="6835e-174">OrElse 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-174">OrElse Operator</span></span>](../../../language-reference/operators/orelse-operator.md)|  
|<span data-ttu-id="6835e-175">2 つの整数値に対してビット単位の論理積を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-175">Perform bit-by-bit logical conjunction on two integral values</span></span>|[<span data-ttu-id="6835e-176">And 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-176">And Operator</span></span>](../../../language-reference/operators/and-operator.md)|  
|<span data-ttu-id="6835e-177">2 つの整数値に対してビット単位の包括的論理和演算を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-177">Perform bit-by-bit inclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="6835e-178">Or 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-178">Or Operator</span></span>](../../../language-reference/operators/or-operator.md)|  
|<span data-ttu-id="6835e-179">2 つの整数値に対してビット単位の排他的論理和演算を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-179">Perform bit-by-bit exclusive logical disjunction on two integral values</span></span>|[<span data-ttu-id="6835e-180">Xor 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-180">Xor Operator</span></span>](../../../language-reference/operators/xor-operator.md)|  
|<span data-ttu-id="6835e-181">整数値に対してビット単位の論理否定を実行します</span><span class="sxs-lookup"><span data-stu-id="6835e-181">Perform bit-by-bit logical negation on an integral value</span></span>|[<span data-ttu-id="6835e-182">Not 演算子</span><span class="sxs-lookup"><span data-stu-id="6835e-182">Not Operator</span></span>](../../../language-reference/operators/not-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="6835e-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="6835e-183">See also</span></span>

- [<span data-ttu-id="6835e-184">演算子および式</span><span class="sxs-lookup"><span data-stu-id="6835e-184">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="6835e-185">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="6835e-185">Operators Listed by Functionality</span></span>](../../../language-reference/operators/operators-listed-by-functionality.md)
