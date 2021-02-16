---
description: '詳細情報: データ型のトラブルシューティング (Visual Basic)'
title: データ型のトラブルシューティング
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 417a71e88dcd0bfb0c6582ee6304a64871640255
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463846"
---
# <a name="troubleshooting-data-types-visual-basic"></a><span data-ttu-id="78ea3-103">データ型のトラブルシューティング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78ea3-103">Troubleshooting Data Types (Visual Basic)</span></span>

<span data-ttu-id="78ea3-104">このページでは、組み込みデータ型に対して操作を実行するときに発生する可能性がある一般的な問題をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-104">This page lists some common problems that can occur when you perform operations on intrinsic data types.</span></span>

## <a name="floating-point-expressions-do-not-compare-as-equal"></a><span data-ttu-id="78ea3-105">浮動小数点式を比較したときに等しくならない</span><span class="sxs-lookup"><span data-stu-id="78ea3-105">Floating-Point Expressions Do Not Compare as Equal</span></span>

<span data-ttu-id="78ea3-106">浮動小数点数 ([Single データ型](../../../language-reference/data-types/single-data-type.md)および [Double データ型](../../../language-reference/data-types/double-data-type.md)) を扱うときは、それらがバイナリの分数として格納されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-106">When you work with floating-point numbers ([Single Data Type](../../../language-reference/data-types/single-data-type.md) and [Double Data Type](../../../language-reference/data-types/double-data-type.md)), remember that they are stored as binary fractions.</span></span> <span data-ttu-id="78ea3-107">つまり、これらは、バイナリの分数 (形式は k / (2 ^ n)、k と n は整数) ではない数量表現を保持できません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-107">This means they cannot hold an exact representation of any quantity that is not a binary fraction (of the form k / (2 ^ n) where k and n are integers).</span></span> <span data-ttu-id="78ea3-108">たとえば、0.5 (= 1/2) と 0.3125 (= 5/16) は正確な値を保持できますが、0.2 (= 1/5) と 0.3 (= 3/10) は概算値しか保持できません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-108">For example, 0.5 (= 1/2) and 0.3125 (= 5/16) can be held as precise values, whereas 0.2 (= 1/5) and 0.3 (= 3/10) can be only approximations.</span></span>

<span data-ttu-id="78ea3-109">この誤差のため、浮動小数点値の演算では、正確な結果かどうか信頼できません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-109">Because of this imprecision, you cannot rely on exact results when you operate on floating-point values.</span></span> <span data-ttu-id="78ea3-110">特に、理論的には等しい 2 つの値の表現が多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-110">In particular, two values that are theoretically equal might have slightly different representations.</span></span>

| <span data-ttu-id="78ea3-111">浮動小数点数の数量を比較するには</span><span class="sxs-lookup"><span data-stu-id="78ea3-111">To compare floating-point quantities</span></span> |
|---|
|<span data-ttu-id="78ea3-112">1.<xref:System> 名前空間の <xref:System.Math> クラスの <xref:System.Math.Abs%2A> メソッドを使用して、差の絶対値を計算します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-112">1.  Calculate the absolute value of their difference by using the <xref:System.Math.Abs%2A> method of the <xref:System.Math> class in the <xref:System> namespace.</span></span><br /><span data-ttu-id="78ea3-113">2.最大の許容差を決めて、差がそれよりも小さい場合には、実際に 2 つの数量を等価と見なすようにします。</span><span class="sxs-lookup"><span data-stu-id="78ea3-113">2.  Determine an acceptable maximum difference, such that you can consider the two quantities to be equal for practical purposes if their difference is no larger.</span></span><br /><span data-ttu-id="78ea3-114">3.差の絶対値と許容差を比較します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-114">3.  Compare the absolute value of the difference to the acceptable difference.</span></span>|

<span data-ttu-id="78ea3-115">次の例は、2 つの `Double` 値の誤った比較と正しい比較を示しています。</span><span class="sxs-lookup"><span data-stu-id="78ea3-115">The following example demonstrates both incorrect and correct comparison of two `Double` values.</span></span>

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

<span data-ttu-id="78ea3-116">前の例では、<xref:System.Double> 構造体の <xref:System.Double.ToString%2A> メソッドを使用して、`CStr` キーワードで使用されるよりも高い精度を指定できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="78ea3-116">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better  precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="78ea3-117">既定値は 15 桁ですが、"G17" 形式によって 17 桁に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-117">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>

## <a name="mod-operator-does-not-return-accurate-result"></a><span data-ttu-id="78ea3-118">Mod 演算子が正確な結果を返さない</span><span class="sxs-lookup"><span data-stu-id="78ea3-118">Mod Operator Does Not Return Accurate Result</span></span>

<span data-ttu-id="78ea3-119">浮動小数点数の格納が正確でないため、少なくとも 1 つのオペランドが浮動小数点数である場合、[Mod 演算子](../../../language-reference/operators/mod-operator.md)は予期しない結果を返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-119">Because of the imprecision of floating-point storage, the [Mod Operator](../../../language-reference/operators/mod-operator.md) can return an unexpected result when at least one of the operands is floating-point.</span></span>

<span data-ttu-id="78ea3-120">[Decimal データ型](../../../language-reference/data-types/decimal-data-type.md)では、浮動小数点表現は使用されません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-120">The [Decimal Data Type](../../../language-reference/data-types/decimal-data-type.md) does not use floating-point representation.</span></span> <span data-ttu-id="78ea3-121">`Single` と `Double` で正確ではない多くの数値は、`Decimal` では正確です (0.2 や 0.3 など)。</span><span class="sxs-lookup"><span data-stu-id="78ea3-121">Many numbers that are inexact in `Single` and `Double` are exact in `Decimal` (for example 0.2 and 0.3).</span></span> <span data-ttu-id="78ea3-122">浮動小数点型より `Decimal` では算術が遅くなりますが、パフォーマンスが低下しても精度が高まる値打ちがあります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-122">Although arithmetic is slower in `Decimal` than in floating-point, it might be worth the performance decrease to achieve better precision.</span></span>

|<span data-ttu-id="78ea3-123">浮動小数点数の整数の剰余を求めるには</span><span class="sxs-lookup"><span data-stu-id="78ea3-123">To find the integer remainder of floating-point quantities</span></span>|
|---|
|<span data-ttu-id="78ea3-124">1.変数を `Decimal` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-124">1.  Declare variables as `Decimal`.</span></span><br /><span data-ttu-id="78ea3-125">2.リテラルの型文字 `D` を使用して、リテラルを強制的に `Decimal` にします (値が `Long` データ型に対して大きすぎる場合)。</span><span class="sxs-lookup"><span data-stu-id="78ea3-125">2.  Use the literal type character `D` to force literals to `Decimal`, in case their values are too large for the `Long` data type.</span></span>|

<span data-ttu-id="78ea3-126">次の例は、浮動小数点オペランドにおける誤差の可能性を示しています。</span><span class="sxs-lookup"><span data-stu-id="78ea3-126">The following example demonstrates the potential imprecision of floating-point operands.</span></span>

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

<span data-ttu-id="78ea3-127">前の例では、<xref:System.Double> 構造体の <xref:System.Double.ToString%2A> メソッドを使用して、`CStr` キーワードで使用されるよりも高い精度を指定できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="78ea3-127">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="78ea3-128">既定値は 15 桁ですが、"G17" 形式によって 17 桁に拡張されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-128">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>

<span data-ttu-id="78ea3-129">`zeroPointTwo` は `Double` であるため、0.2 に対する値は、無限に連続するバイナリ分数値で、値 0.20000000000000001 が格納されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-129">Because `zeroPointTwo` is `Double`, its value for 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="78ea3-130">2\.0 をこの数で割ると 9.9999999999999995 になり、剰余が 0.19999999999999991 になります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-130">Dividing 2.0 by this quantity yields 9.9999999999999995 with a remainder of 0.19999999999999991.</span></span>

<span data-ttu-id="78ea3-131">`decimalRemainder` の式では、リテラルの型文字 `D` によって両方のオペランドが強制的に `Decimal` になり、0.2 の表現は正確です。</span><span class="sxs-lookup"><span data-stu-id="78ea3-131">In the expression for `decimalRemainder`, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span> <span data-ttu-id="78ea3-132">したがって、`Mod` 演算子では、0.0 という予期される剰余が得られます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-132">Therefore the `Mod` operator yields the expected remainder of 0.0.</span></span>

<span data-ttu-id="78ea3-133">`decimalRemainder` を `Decimal` として宣言するだけでは十分ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-133">Note that it is not sufficient to declare `decimalRemainder` as `Decimal`.</span></span> <span data-ttu-id="78ea3-134">また、リテラルを強制的に `Decimal` にする必要があります。そうしないと、`Double` が既定で使用され、`decimalRemainder` は `doubleRemainder` と同じ不正確な値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-134">You must also force the literals to `Decimal`, or they use `Double` by default and `decimalRemainder` receives the same inaccurate value as `doubleRemainder`.</span></span>

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a><span data-ttu-id="78ea3-135">Boolean 型が数値型に正確に変換されない</span><span class="sxs-lookup"><span data-stu-id="78ea3-135">Boolean Type Does Not Convert to Numeric Type Accurately</span></span>

<span data-ttu-id="78ea3-136">[Boolean データ型](../../../language-reference/data-types/boolean-data-type.md)の値は数値として格納されず、格納された値は数値と等価であると見なされません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-136">[Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="78ea3-137">以前のバージョンとの互換性のために、Visual Basic は変換キーワード ([CType 関数](../../../language-reference/functions/ctype-function.md)、`CBool`、`CInt` など) を使用して、`Boolean` と数値型の間で変換を行います。</span><span class="sxs-lookup"><span data-stu-id="78ea3-137">For compatibility with earlier versions, Visual Basic provides conversion keywords ([CType Function](../../../language-reference/functions/ctype-function.md), `CBool`, `CInt`, and so on) to convert between `Boolean` and numeric types.</span></span> <span data-ttu-id="78ea3-138">ただし、その他の言語では、.NET Framework メソッドと同様に、これらの変換が異なる方法で実行されることがあります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-138">However, other languages sometimes perform these conversions differently, as do the .NET Framework methods.</span></span>

<span data-ttu-id="78ea3-139">`True` と `False` に対して等価の数値に依存するコードを記述することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-139">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="78ea3-140">可能な限り、`Boolean` 変数には、仕様で定められている論理値以外の値を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-140">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span> <span data-ttu-id="78ea3-141">`Boolean` 値と数値を混在させる必要がある場合は、選択する変換方法をよく理解してください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-141">If you must mix `Boolean` and numeric values, make sure that you understand the conversion method that you select.</span></span>

### <a name="conversion-in-visual-basic"></a><span data-ttu-id="78ea3-142">Visual Basic での変換</span><span class="sxs-lookup"><span data-stu-id="78ea3-142">Conversion in Visual Basic</span></span>

<span data-ttu-id="78ea3-143">`CType` または `CBool` の変換キーワードを使用して数値データ型を `Boolean` に変換するとき、0 が `False` になり、その他のすべての値が `True` になります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-143">When you use the `CType` or `CBool` conversion keywords to convert numeric data types to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="78ea3-144">変換キーワードを使用して `Boolean` 値を数値型に変換するとき、`False` は 0 になり、`True` は -1 になります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-144">When you convert `Boolean` values to numeric types by using the conversion keywords, `False` becomes 0 and `True` becomes -1.</span></span>

### <a name="conversion-in-the-framework"></a><span data-ttu-id="78ea3-145">フレームワークでの変換</span><span class="sxs-lookup"><span data-stu-id="78ea3-145">Conversion in the Framework</span></span>

<span data-ttu-id="78ea3-146"><xref:System> 名前空間の <xref:System.Convert> クラスの <xref:System.Convert.ToInt32%2A> メソッドによって、`True` が +1 に変換されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-146">The <xref:System.Convert.ToInt32%2A> method of the <xref:System.Convert> class in the <xref:System> namespace converts `True` to +1.</span></span>

<span data-ttu-id="78ea3-147">`Boolean` 値を数値データ型に変換する必要がある場合は、使用する変換方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-147">If you must convert a `Boolean` value to a numeric data type, be careful about which conversion method you use.</span></span>

## <a name="character-literal-generates-compiler-error"></a><span data-ttu-id="78ea3-148">文字リテラルによってコンパイラ エラーが生成される</span><span class="sxs-lookup"><span data-stu-id="78ea3-148">Character Literal Generates Compiler Error</span></span>

<span data-ttu-id="78ea3-149">型文字が存在しない場合、Visual Basic によってリテラルの既定データ型と見なされます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-149">In the absence of any type characters, Visual Basic assumes default data types for literals.</span></span> <span data-ttu-id="78ea3-150">二重引用符 (`" "`) で囲まれた文字リテラルの既定型は `String` です。</span><span class="sxs-lookup"><span data-stu-id="78ea3-150">The default type for a character literal — enclosed in quotation marks (`" "`) — is `String`.</span></span>

<span data-ttu-id="78ea3-151">`String` データ型は [Char データ型](../../../language-reference/data-types/char-data-type.md)に拡大変換されません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-151">The `String` data type does not widen to the [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span> <span data-ttu-id="78ea3-152">つまり、`Char` 変数にリテラルを代入する場合は、縮小変換を行うか、リテラルを強制的に `Char` 型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-152">This means that if you want to assign a literal to a `Char` variable, you must either make a narrowing conversion or force the literal to the `Char` type.</span></span>

|<span data-ttu-id="78ea3-153">変数または定数に代入する Char リテラルを作成するには</span><span class="sxs-lookup"><span data-stu-id="78ea3-153">To create a Char literal to assign to a variable or constant</span></span>|
|---|
|<span data-ttu-id="78ea3-154">1.変数または定数を `Char` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-154">1.  Declare the variable or constant as `Char`.</span></span><br /><span data-ttu-id="78ea3-155">2.文字値を二重引用符 `" "` で囲みます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-155">2.  Enclose the character value in quotation marks (`" "`).</span></span><br /><span data-ttu-id="78ea3-156">3.終わりの二重引用符の後にリテラルの型文字 `C` を指定して、リテラルを強制的に `Char` にします。</span><span class="sxs-lookup"><span data-stu-id="78ea3-156">3.  Follow the closing double quotation mark with the literal type character `C` to force the literal to `Char`.</span></span> <span data-ttu-id="78ea3-157">これは型チェック スイッチ ([Option Strict ステートメント](../../../language-reference/statements/option-strict-statement.md)) が `On` の場合に必須ですが、どのような場合でもお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78ea3-157">This is necessary if the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On`, and it is desirable in any case.</span></span>|

<span data-ttu-id="78ea3-158">次の例では、`Char` 変数へのリテラルの代入の失敗と成功の両方を示します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-158">The following example demonstrates both unsuccessful and successful assignments of a literal to a `Char` variable.</span></span>

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

<span data-ttu-id="78ea3-159">縮小変換は実行時に失敗する可能性があるため、使用には常にリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="78ea3-159">There is always a risk in using narrowing conversions, because they can fail at run time.</span></span> <span data-ttu-id="78ea3-160">たとえば、`String` から `Char` への変換が失敗する可能性があるのは、`String` 値に複数の文字が含まれている場合です。</span><span class="sxs-lookup"><span data-stu-id="78ea3-160">For example, a conversion from `String` to `Char` can fail if the `String` value contains more than one character.</span></span> <span data-ttu-id="78ea3-161">そのため、`C` 型文字を使用する方が適切なプログラミングです。</span><span class="sxs-lookup"><span data-stu-id="78ea3-161">Therefore, it is better programming to use the `C` type character.</span></span>

## <a name="string-conversion-fails-at-run-time"></a><span data-ttu-id="78ea3-162">実行時に文字列変換が失敗する</span><span class="sxs-lookup"><span data-stu-id="78ea3-162">String Conversion Fails at Run Time</span></span>

<span data-ttu-id="78ea3-163">[String データ型](../../../language-reference/data-types/string-data-type.md)は、非常に多くの拡大変換に関連します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-163">The [String Data Type](../../../language-reference/data-types/string-data-type.md) participates in very few widening conversions.</span></span> <span data-ttu-id="78ea3-164">`String` はそれ自体と `Object` に拡大変換され、`Char` と `Char()` (`Char` 配列) のみが `String` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-164">`String` widens only to itself and `Object`, and only `Char` and `Char()` (a `Char` array) widen to `String`.</span></span> <span data-ttu-id="78ea3-165">これは、`String` の変数と定数には、他のデータ型に含めることができない値が含まれている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="78ea3-165">This is because `String` variables and constants can contain values that other data types cannot contain.</span></span>

<span data-ttu-id="78ea3-166">型チェック スイッチ ([Option Strict ステートメント](../../../language-reference/statements/option-strict-statement.md)) が `On` のとき、コンパイラによって暗黙の縮小変換がすべて禁止されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-166">When the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On`, the compiler disallows all implicit narrowing conversions.</span></span> <span data-ttu-id="78ea3-167">これには、`String` に関係するものも含まれます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-167">This includes those involving `String`.</span></span> <span data-ttu-id="78ea3-168">.NET Framework が変換を試行するように指示する変換キーワード (`CStr` や [CType 関数](../../../language-reference/functions/ctype-function.md)など) をコードで引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-168">Your code can still use conversion keywords such as `CStr` and [CType Function](../../../language-reference/functions/ctype-function.md), which direct the .NET Framework to attempt the conversion.</span></span>

> [!NOTE]
> <span data-ttu-id="78ea3-169">`For Each…Next` コレクション内の要素からループ制御変数への変換では、縮小変換エラーが抑制されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-169">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="78ea3-170">詳細と例については、「[For Each...Next ステートメント](../../../language-reference/statements/for-each-next-statement.md)」の縮小変換に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-170">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>

### <a name="narrowing-conversion-protection"></a><span data-ttu-id="78ea3-171">縮小変換の保護</span><span class="sxs-lookup"><span data-stu-id="78ea3-171">Narrowing Conversion Protection</span></span>

<span data-ttu-id="78ea3-172">縮小変換の欠点は、実行時にエラーが発生する可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="78ea3-172">The disadvantage of narrowing conversions is that they can fail at run time.</span></span> <span data-ttu-id="78ea3-173">たとえば、`String` 変数に "True" または "False" 以外が含まれる場合は、`Boolean` に変換できません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-173">For example, if a `String` variable contains anything other than "True" or "False," it cannot be converted to `Boolean`.</span></span> <span data-ttu-id="78ea3-174">区切り文字が含まれている場合は、どの数値型への変換も失敗します。</span><span class="sxs-lookup"><span data-stu-id="78ea3-174">If it contains punctuation characters, conversion to any numeric type fails.</span></span> <span data-ttu-id="78ea3-175">`String` 変数が、変換先の型で受け入れ可能な値を常に保持していることがわかっている場合を除き、変換を試行しないでください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-175">Unless you know that your `String` variable always holds values that the destination type can accept, you should not try a conversion.</span></span>

<span data-ttu-id="78ea3-176">`String` から別のデータ型に変換する必要がある場合、最も安全な手順は、[Try...Catch...Finally ステートメント](../../../language-reference/statements/try-catch-finally-statement.md)に変換の試行を含めることです。</span><span class="sxs-lookup"><span data-stu-id="78ea3-176">If you must convert from `String` to another data type, the safest procedure is to enclose the attempted conversion in the [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="78ea3-177">これにより、実行時エラーに対処できます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-177">This lets you deal with a run-time failure.</span></span>

### <a name="character-arrays"></a><span data-ttu-id="78ea3-178">文字配列</span><span class="sxs-lookup"><span data-stu-id="78ea3-178">Character Arrays</span></span>

<span data-ttu-id="78ea3-179">1 つの `Char` および `Char` 要素の配列 1 つは、どちらも `String` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-179">A single `Char` and an array of `Char` elements both widen to `String`.</span></span> <span data-ttu-id="78ea3-180">ただし、`String` は `Char()` に拡大変換されません。</span><span class="sxs-lookup"><span data-stu-id="78ea3-180">However, `String` does not widen to `Char()`.</span></span> <span data-ttu-id="78ea3-181">`String` 値を `Char` 配列に変換するには、<xref:System.String?displayProperty=nameWithType> クラスの <xref:System.String.ToCharArray%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78ea3-181">To convert a `String` value to a `Char` array, you can use the <xref:System.String.ToCharArray%2A> method of the <xref:System.String?displayProperty=nameWithType> class.</span></span>

### <a name="meaningless-values"></a><span data-ttu-id="78ea3-182">意味のない値</span><span class="sxs-lookup"><span data-stu-id="78ea3-182">Meaningless Values</span></span>

<span data-ttu-id="78ea3-183">一般に、`String` の値は他のデータ型では意味がなく、変換は非常に人為的で危険です。</span><span class="sxs-lookup"><span data-stu-id="78ea3-183">In general, `String` values are not meaningful in other data types, and conversion is highly artificial and dangerous.</span></span> <span data-ttu-id="78ea3-184">可能な限り、`String` 変数には、仕様で定められている文字シーケンス以外の値を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-184">Whenever possible, you should restrict usage of `String` variables to the character sequences for which they are designed.</span></span> <span data-ttu-id="78ea3-185">他の型の等価の値に依存するコードを記述することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="78ea3-185">You should never write code that relies on equivalent values in other types.</span></span>

## <a name="see-also"></a><span data-ttu-id="78ea3-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="78ea3-186">See also</span></span>

- [<span data-ttu-id="78ea3-187">データの種類</span><span class="sxs-lookup"><span data-stu-id="78ea3-187">Data Types</span></span>](index.md)
- [<span data-ttu-id="78ea3-188">型文字</span><span class="sxs-lookup"><span data-stu-id="78ea3-188">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="78ea3-189">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="78ea3-189">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="78ea3-190">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="78ea3-190">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="78ea3-191">データの種類</span><span class="sxs-lookup"><span data-stu-id="78ea3-191">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="78ea3-192">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="78ea3-192">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="78ea3-193">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="78ea3-193">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
