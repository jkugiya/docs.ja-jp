---
description: '詳細情報: 数値データ型 (Visual Basic)'
title: 数値データ型
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 0e44301d953ab75378aabbec82fdb6dce00a02e2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430691"
---
# <a name="numeric-data-types-visual-basic"></a><span data-ttu-id="b6bdd-103">数値データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6bdd-103">Numeric Data Types (Visual Basic)</span></span>

<span data-ttu-id="b6bdd-104">Visual Basic には、さまざまな表現の数値を処理するためにいくつかの "*数値データ型*" が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-104">Visual Basic supplies several *numeric data types* for handling numbers in various representations.</span></span> <span data-ttu-id="b6bdd-105">"*整数*" 型は整数 (正、負、ゼロ) のみを表し、"*非整数*" 型は整数部と小数部の両方がある数値を表します。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-105">*Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="b6bdd-106">Visual Basic データ型を並べて比較している表を、[データ型](../../../language-reference/data-types/index.md)に関するページで参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-106">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="integral-numeric-types"></a><span data-ttu-id="b6bdd-107">整数数値型</span><span class="sxs-lookup"><span data-stu-id="b6bdd-107">Integral Numeric Types</span></span>  

 <span data-ttu-id="b6bdd-108">"*整数データ型*" は、小数部を含まない数値のみを表す型です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-108">*Integral data types* are those that represent only numbers without fractional parts.</span></span>  
  
 <span data-ttu-id="b6bdd-109">"*符号付き*" の整数データ型は、[SByte データ型](../../../language-reference/data-types/sbyte-data-type.md) (8 ビット)、[Short データ型](../../../language-reference/data-types/short-data-type.md) (16 ビット)、[Integer データ型](../../../language-reference/data-types/integer-data-type.md) (32 ビット)、および [Long データ型](../../../language-reference/data-types/long-data-type.md) (64 ビット) です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-109">The *signed* integral data types are [SByte Data Type](../../../language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../language-reference/data-types/long-data-type.md) (64-bit).</span></span> <span data-ttu-id="b6bdd-110">変数に小数ではなく整数が常に格納される場合は、これらのいずれかの型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-110">If a variable always stores integers rather than fractional numbers, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="b6bdd-111">"*符号なし*" の整数型は、[Byte データ型](../../../language-reference/data-types/byte-data-type.md) (8 ビット)、[UShort データ型](../../../language-reference/data-types/ushort-data-type.md) (16 ビット)、[UInteger データ型](../../../language-reference/data-types/uinteger-data-type.md) (32 ビット)、および [ULong データ型](../../../language-reference/data-types/ulong-data-type.md) (64 ビット) です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-111">The *unsigned* integral types are [Byte Data Type](../../../language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../language-reference/data-types/ulong-data-type.md) (64-bit).</span></span> <span data-ttu-id="b6bdd-112">変数にバイナリ データまたは不明な性質のデータが含まれる場合は、これらのいずれかの型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-112">If a variable contains binary data, or data of unknown nature, declare it as one of these types.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="b6bdd-113">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="b6bdd-113">Performance</span></span>  

 <span data-ttu-id="b6bdd-114">算術演算は、整数型を使用すると他のデータ型よりも高速です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-114">Arithmetic operations are faster with integral types than with other data types.</span></span> <span data-ttu-id="b6bdd-115">Visual Basic では `Integer` 型と `UInteger` 型が最も高速です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-115">They are fastest with the `Integer` and `UInteger` types in Visual Basic.</span></span>  
  
### <a name="large-integers"></a><span data-ttu-id="b6bdd-116">大きい整数</span><span class="sxs-lookup"><span data-stu-id="b6bdd-116">Large Integers</span></span>  

 <span data-ttu-id="b6bdd-117">`Integer` データ型よりも大きな整数を保持する必要がある場合は、代わりに `Long` データ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-117">If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead.</span></span> <span data-ttu-id="b6bdd-118">`Long` 変数は、-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807 までの数値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-118">`Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807.</span></span> <span data-ttu-id="b6bdd-119">`Long` を使用した演算は、`Integer` よりも少し遅くなります。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-119">Operations with `Long` are slightly slower than with `Integer`.</span></span>  
  
 <span data-ttu-id="b6bdd-120">さらに大きな値が必要な場合は、[Decimal データ型](../../../language-reference/data-types/decimal-data-type.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-120">If you need even larger values, you can use the [Decimal Data Type](../../../language-reference/data-types/decimal-data-type.md).</span></span> <span data-ttu-id="b6bdd-121">小数位を使用しない場合、`Decimal` 変数には -79,228,162,514,264,337,593,543,950,335 から 79,228,162,514,264,337,593,543,950,335 までの数値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-121">You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places.</span></span> <span data-ttu-id="b6bdd-122">ただし、`Decimal` 数値を使用した演算は、他の数値データ型を使用するよりもかなり遅くなります。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-122">However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.</span></span>  
  
### <a name="small-integers"></a><span data-ttu-id="b6bdd-123">小さい整数</span><span class="sxs-lookup"><span data-stu-id="b6bdd-123">Small Integers</span></span>  

 <span data-ttu-id="b6bdd-124">`Integer` データ型のすべての範囲が必要ない場合は、-32,768 から 32,767 までの整数を保持できる `Short` データ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-124">If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767.</span></span> <span data-ttu-id="b6bdd-125">最も小さい整数の範囲のためには、`SByte` データ型に -128 から 127 までの整数が保持されます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-125">For the smallest integer range, the `SByte` data type holds integers from -128 through 127.</span></span> <span data-ttu-id="b6bdd-126">小さい整数を保持する変数の数が非常に多い場合、共通言語ランタイムによって `Short` と `SByte` 変数がより効率的に格納され、メモリ消費が節約されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-126">If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption.</span></span> <span data-ttu-id="b6bdd-127">ただし、`Short` と `SByte` を使用した演算は、`Integer` よりも多少遅くなります。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-127">However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.</span></span>  
  
### <a name="unsigned-integers"></a><span data-ttu-id="b6bdd-128">符号なし整数</span><span class="sxs-lookup"><span data-stu-id="b6bdd-128">Unsigned Integers</span></span>  

 <span data-ttu-id="b6bdd-129">変数が負の数を保持する必要がないことがわかっている場合は、"*符号なしの型*" である `Byte`、`UShort`、`UInteger`、および `ULong` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-129">If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`.</span></span> <span data-ttu-id="b6bdd-130">これらのデータ型はそれぞれ、対応する符号付きの型 (`SByte`、`Short`、`Integer`、および `Long`) の 2 倍の正の整数を保持できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-130">Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`).</span></span> <span data-ttu-id="b6bdd-131">パフォーマンス面では、符号なしの各型の効率は、対応する符号付きの型とまったく同じです。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-131">In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type.</span></span> <span data-ttu-id="b6bdd-132">特に、`UInteger` が `Integer` と共通するのは、すべての基本数値データ型の中で最も効率的であるという特徴です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-132">In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.</span></span>  
  
## <a name="nonintegral-numeric-types"></a><span data-ttu-id="b6bdd-133">非整数数値型</span><span class="sxs-lookup"><span data-stu-id="b6bdd-133">Nonintegral Numeric Types</span></span>  

 <span data-ttu-id="b6bdd-134">"*非整数データ型*" は、整数部と小数部の両方を含む数値を表す型です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-134">*Nonintegral data types* are those that represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="b6bdd-135">非整数データ型は、`Decimal` (128 ビット固定小数点)、[Single データ型](../../../language-reference/data-types/single-data-type.md) (32 ビット浮動小数点)、および [Double データ型](../../../language-reference/data-types/double-data-type.md) (64 ビット浮動小数点) です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-135">The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../language-reference/data-types/double-data-type.md) (64-bit floating point).</span></span> <span data-ttu-id="b6bdd-136">これらはすべて符号付きの型です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-136">They are all signed types.</span></span> <span data-ttu-id="b6bdd-137">変数が小数を含む可能性がある場合は、これらのいずれかの型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-137">If a variable can contain a fraction, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="b6bdd-138">`Decimal` は浮動小数点データ型ではありません。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-138">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="b6bdd-139">`Decimal` 数は、2 進数の整数値と、値のどの部分が小数であるかを指定する整数のスケーリング ファクターを保持します。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-139">`Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span>  
  
 <span data-ttu-id="b6bdd-140">金額には `Decimal` 変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-140">You can use `Decimal` variables for money values.</span></span> <span data-ttu-id="b6bdd-141">利点は値の精度です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-141">The advantage is the precision of the values.</span></span> <span data-ttu-id="b6bdd-142">`Double` データ型の方が高速で、必要なメモリが少なくなりますが、丸めエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-142">The `Double` data type is faster and requires less memory, but it is subject to rounding errors.</span></span> <span data-ttu-id="b6bdd-143">`Decimal` データ型では、小数点以下 28 桁まで完全な精度が保持されます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-143">The `Decimal` data type retains complete accuracy to 28 decimal places.</span></span>  
  
 <span data-ttu-id="b6bdd-144">浮動小数点 (`Single` および `Double`) 数は、`Decimal` 数よりも広い範囲に対応しますが、丸めエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-144">Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors.</span></span> <span data-ttu-id="b6bdd-145">浮動小数点型は、`Decimal` よりも有効桁数は少ないものの、より大きい値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-145">Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.</span></span>  
  
 <span data-ttu-id="b6bdd-146">非整数の数値は mmmEeee として表すことができます。mmm は "*仮数*" (有効桁数)、eee は "*指数*" (10 の累乗) です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-146">Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10).</span></span> <span data-ttu-id="b6bdd-147">非整数型の最大の正の値は、7.9228162514264337593543950335E+28 (`Decimal`)、3.4028235E+38 (`Single`)、および 1.79769313486231570E+308 (`Double`) です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-147">The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="b6bdd-148">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="b6bdd-148">Performance</span></span>  

 <span data-ttu-id="b6bdd-149">`Double` は小数データ型の中で最も効率的です。現在のプラットフォームのプロセッサが、倍精度で浮動小数点演算を実行するためです。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-149">`Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="b6bdd-150">ただし、`Double` を使用した演算は、`Integer` などの整数型ほど高速ではありません。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-150">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
### <a name="small-magnitudes"></a><span data-ttu-id="b6bdd-151">大きさが小さい</span><span class="sxs-lookup"><span data-stu-id="b6bdd-151">Small Magnitudes</span></span>  

 <span data-ttu-id="b6bdd-152">大きさが最も小さくなる (0 に最も近くなる) 可能性がある数の場合、`Double` 変数は、負の値として -4.94065645841246544E-324、正の値として 4.94065645841246544E-324 を保持できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-152">For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.</span></span>  
  
### <a name="small-fractional-numbers"></a><span data-ttu-id="b6bdd-153">小さい小数</span><span class="sxs-lookup"><span data-stu-id="b6bdd-153">Small Fractional Numbers</span></span>  

 <span data-ttu-id="b6bdd-154">`Double` データ型のすべての範囲が必要ない場合は、-3.4028235E+38 から 3.4028235E+38 までの浮動小数点数を保持できる `Single` データ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-154">If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38.</span></span> <span data-ttu-id="b6bdd-155">`Single` 変数の最小の大きさは、負の値が -1.401298E-45、正の値が 1.401298E-45 です。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-155">The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values.</span></span> <span data-ttu-id="b6bdd-156">小さい浮動小数点数を保持する変数の数が非常に多い場合、共通言語ランタイムによって `Single` 変数がより効率的に格納され、メモリ消費が節約されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b6bdd-156">If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bdd-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6bdd-157">See also</span></span>

- [<span data-ttu-id="b6bdd-158">基本データ型</span><span class="sxs-lookup"><span data-stu-id="b6bdd-158">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="b6bdd-159">文字データ型</span><span class="sxs-lookup"><span data-stu-id="b6bdd-159">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="b6bdd-160">その他のデータ型</span><span class="sxs-lookup"><span data-stu-id="b6bdd-160">Miscellaneous Data Types</span></span>](miscellaneous-data-types.md)
- [<span data-ttu-id="b6bdd-161">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="b6bdd-161">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="b6bdd-162">方法: 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="b6bdd-162">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
