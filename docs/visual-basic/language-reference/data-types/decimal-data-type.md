---
description: '詳細情報: 10 進型 (Decimal) (Visual Basic)'
title: 10 進型 (Decimal)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 5806041e7737b8fe0f1c7ffa63f6cbadcbf92e42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792233"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="6da71-103">10 進型 (Decimal) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6da71-103">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="6da71-104">可変の 10 の累乗によってスケーリングされた 96 ビット (12 バイト) 整数値を表す符号付き 128 ビット (16 バイト) 値を保持します。</span><span class="sxs-lookup"><span data-stu-id="6da71-104">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="6da71-105">スケール ファクターは小数点以下の桁数を指定し、0 から 28 の範囲になります。</span><span class="sxs-lookup"><span data-stu-id="6da71-105">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="6da71-106">0 のスケール (小数点以下の桁数なし) では、有効な最大値は +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28) です。</span><span class="sxs-lookup"><span data-stu-id="6da71-106">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="6da71-107">28 桁の小数点以下の桁数では、最大値は +/-7.9228162514264337593543950335 で、0 以外の最小値は +/-0.0000000000000000000000000001 (+/-1E-28) になります。</span><span class="sxs-lookup"><span data-stu-id="6da71-107">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="6da71-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="6da71-108">Remarks</span></span>

<span data-ttu-id="6da71-109">`Decimal` データ型は、数値の最大有効桁数を提供します。</span><span class="sxs-lookup"><span data-stu-id="6da71-109">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="6da71-110">最大 29 桁の有効桁数をサポートし、7.9228 x 10^28 を超える値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="6da71-110">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="6da71-111">これは、多くの桁数を必要とするが丸め誤差を許容できない財務などの計算に特に適しています。</span><span class="sxs-lookup"><span data-stu-id="6da71-111">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="6da71-112">`Decimal` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="6da71-112">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="6da71-113">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="6da71-113">Programming Tips</span></span>

- <span data-ttu-id="6da71-114">**精度。**</span><span class="sxs-lookup"><span data-stu-id="6da71-114">**Precision.**</span></span> <span data-ttu-id="6da71-115">`Decimal` は浮動小数点データ型ではありません。</span><span class="sxs-lookup"><span data-stu-id="6da71-115">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="6da71-116">`Decimal` 構造体は、2 進数の整数値を保持します。符号ビットと、値のどの部分が小数であるかを指定する整数のスケーリング ファクターです。</span><span class="sxs-lookup"><span data-stu-id="6da71-116">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="6da71-117">このため、`Decimal` の数値は、浮動小数点型 (`Single` と `Double`) よりもメモリ内でより正確に表現されます。</span><span class="sxs-lookup"><span data-stu-id="6da71-117">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="6da71-118">**パフォーマンス。**</span><span class="sxs-lookup"><span data-stu-id="6da71-118">**Performance.**</span></span> <span data-ttu-id="6da71-119">`Decimal` データ型は、すべての数値型の中で最も低速です。</span><span class="sxs-lookup"><span data-stu-id="6da71-119">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="6da71-120">データ型を選択する前に、精度の重要性をパフォーマンスに照らして検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6da71-120">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="6da71-121">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="6da71-121">**Widening.**</span></span> <span data-ttu-id="6da71-122">`Decimal` データ型は、`Single` または `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="6da71-122">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="6da71-123">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、これらの型のいずれかに `Decimal` を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6da71-123">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="6da71-124">**末尾のゼロ。**</span><span class="sxs-lookup"><span data-stu-id="6da71-124">**Trailing Zeros.**</span></span> <span data-ttu-id="6da71-125">Visual Basic では、末尾のゼロが `Decimal` リテラルに格納されません。</span><span class="sxs-lookup"><span data-stu-id="6da71-125">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="6da71-126">ただし、`Decimal` 変数では、計算によって取得されたすべての末尾のゼロが保持されます。</span><span class="sxs-lookup"><span data-stu-id="6da71-126">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="6da71-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6da71-127">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="6da71-128">前の例の `MsgBox` の出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6da71-128">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="6da71-129">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="6da71-129">**Type Characters.**</span></span> <span data-ttu-id="6da71-130">あるリテラルにリテラルの型文字 `D` を付けると、そのリテラルは `Decimal` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="6da71-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="6da71-131">ある識別子に識別子の型文字 `@` を付けると、その識別子は整数型 (`Decimal`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="6da71-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="6da71-132">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="6da71-132">**Framework Type.**</span></span> <span data-ttu-id="6da71-133">.NET Framework において対応する型は、<xref:System.Decimal?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="6da71-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="6da71-134">範囲</span><span class="sxs-lookup"><span data-stu-id="6da71-134">Range</span></span>

 <span data-ttu-id="6da71-135">`Decimal` 変数または定数に大きな値を代入するために、`D` 型文字を使用する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="6da71-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="6da71-136">この要件は、次の例に示すように、リテラルの型文字がリテラルの後に続く場合を除いて、コンパイラではリテラルが `Long` として解釈されるためです。</span><span class="sxs-lookup"><span data-stu-id="6da71-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="6da71-137">それに代入される値は `Long` の範囲に収まるため、`bigDec1` の宣言でオーバーフローが発生しません。</span><span class="sxs-lookup"><span data-stu-id="6da71-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="6da71-138">`Long` 値は `Decimal` 変数に代入することができます。</span><span class="sxs-lookup"><span data-stu-id="6da71-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="6da71-139">`bigDec2` の宣言で、オーバーフロー エラーが発生するのは、それに代入された値が `Long` に対して大きすぎるためです。</span><span class="sxs-lookup"><span data-stu-id="6da71-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="6da71-140">数値リテラルは最初に `Long` として解釈できないため、`Decimal` 変数に代入できません。</span><span class="sxs-lookup"><span data-stu-id="6da71-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="6da71-141">`bigDec3` の場合、リテラルの型文字 `D` で、コンパイラにリテラルを `Long` ではなく `Decimal` として強制的に解釈させることによって、問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="6da71-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6da71-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="6da71-142">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6da71-143">データの種類</span><span class="sxs-lookup"><span data-stu-id="6da71-143">Data Types</span></span>](index.md)
- [<span data-ttu-id="6da71-144">Single データ型</span><span class="sxs-lookup"><span data-stu-id="6da71-144">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="6da71-145">Double 型</span><span class="sxs-lookup"><span data-stu-id="6da71-145">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="6da71-146">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="6da71-146">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="6da71-147">変換の概要</span><span class="sxs-lookup"><span data-stu-id="6da71-147">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="6da71-148">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="6da71-148">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
