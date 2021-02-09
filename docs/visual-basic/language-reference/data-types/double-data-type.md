---
description: '詳細情報: 倍精度浮動小数点数型 (Double) (Visual Basic)'
title: 倍精度浮動小数点数型 (Double)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: ae7b87b392038c67ba47e09d7ca995562bf06c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792220"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="c62d7-103">倍精度浮動小数点数型 (Double) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c62d7-103">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="c62d7-104">-1.79769313486231570 E + 308 から -4.94065645841246544 E-324 (負の値の場合) および 4.94065645841246544 E-324 から 1.79769313486231570 E + 308 (正の値の場合) までの値の範囲の、符号付き IEEE 64 ビット (8 バイト) の倍精度浮動小数点数を保持します。</span><span class="sxs-lookup"><span data-stu-id="c62d7-104">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="c62d7-105">倍精度の数値は、実数の概数を格納します。</span><span class="sxs-lookup"><span data-stu-id="c62d7-105">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="c62d7-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="c62d7-106">Remarks</span></span>

<span data-ttu-id="c62d7-107">`Double` データ型は、数値に対して可能な最大と最小の絶対値を提供します。</span><span class="sxs-lookup"><span data-stu-id="c62d7-107">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="c62d7-108">`Double` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="c62d7-108">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="c62d7-109">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="c62d7-109">Programming Tips</span></span>

- <span data-ttu-id="c62d7-110">**精度。**</span><span class="sxs-lookup"><span data-stu-id="c62d7-110">**Precision.**</span></span> <span data-ttu-id="c62d7-111">浮動小数点数を操作する場合、それらがメモリ内で常に正確な表現が使用されているとは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c62d7-111">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="c62d7-112">これにより、値の比較や `Mod` 演算子など、特定の操作によって、予期しない結果につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c62d7-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="c62d7-113">詳細については、「[データ型のトラブルシューティング](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c62d7-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="c62d7-114">**末尾のゼロ。**</span><span class="sxs-lookup"><span data-stu-id="c62d7-114">**Trailing Zeros.**</span></span> <span data-ttu-id="c62d7-115">浮動小数点データ型には、末尾がゼロの文字の内部表現はありません。</span><span class="sxs-lookup"><span data-stu-id="c62d7-115">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="c62d7-116">たとえば、4.2000 と 4.2 は区別されません。</span><span class="sxs-lookup"><span data-stu-id="c62d7-116">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="c62d7-117">そのため、浮動小数点値を表示または出力すると、末尾がゼロの文字は表示されません。</span><span class="sxs-lookup"><span data-stu-id="c62d7-117">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="c62d7-118">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="c62d7-118">**Type Characters.**</span></span> <span data-ttu-id="c62d7-119">あるリテラルにリテラルの型文字 `R` を付けると、そのリテラルは `Double` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c62d7-119">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="c62d7-120">たとえば、整数値の後に `R` が続く場合、値は `Double` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="c62d7-120">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="c62d7-121">ある識別子に識別子の型文字 `#` を付けると、その識別子は整数型 (`Double`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c62d7-121">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="c62d7-122">次の例では、変数 `num` は `Double` として型指定されます。</span><span class="sxs-lookup"><span data-stu-id="c62d7-122">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="c62d7-123">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="c62d7-123">**Framework Type.**</span></span> <span data-ttu-id="c62d7-124">.NET Framework において対応する型は、<xref:System.Double?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="c62d7-124">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c62d7-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="c62d7-125">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="c62d7-126">データの種類</span><span class="sxs-lookup"><span data-stu-id="c62d7-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="c62d7-127">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="c62d7-127">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="c62d7-128">Single データ型</span><span class="sxs-lookup"><span data-stu-id="c62d7-128">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="c62d7-129">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="c62d7-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="c62d7-130">変換の概要</span><span class="sxs-lookup"><span data-stu-id="c62d7-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="c62d7-131">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="c62d7-131">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="c62d7-132">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="c62d7-132">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="c62d7-133">型文字</span><span class="sxs-lookup"><span data-stu-id="c62d7-133">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
