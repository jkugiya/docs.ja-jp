---
description: '詳細情報: 単精度浮動小数点型 (Single) (Visual Basic)'
title: 単精度浮動小数点型 (Single)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: f30e21d3b2d2960a040609a9422ec71cc029f5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792129"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="3157e-103">単精度浮動小数点型 (Single) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3157e-103">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="3157e-104">負の値の場合は -3.4028235E+38 から -1.401298E-45 まで、正の値の場合は 1.401298E-45 から 3.4028235E+38 までの値の範囲の符号付き IEEE 32 ビット (4 バイト) の単精度浮動小数点数を保持します。</span><span class="sxs-lookup"><span data-stu-id="3157e-104">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="3157e-105">単精度の数値は、実数の概数を格納します。</span><span class="sxs-lookup"><span data-stu-id="3157e-105">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3157e-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="3157e-106">Remarks</span></span>  

 <span data-ttu-id="3157e-107">`Double` の完全なデータ幅を必要としない浮動小数点値を格納するには、`Single` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="3157e-107">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="3157e-108">場合によっては、共通言語ランタイムで `Single` 変数を緊密にパックし、メモリ消費を節約できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3157e-108">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="3157e-109">`Single` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="3157e-109">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="3157e-110">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="3157e-110">Programming Tips</span></span>  
  
- <span data-ttu-id="3157e-111">**精度。**</span><span class="sxs-lookup"><span data-stu-id="3157e-111">**Precision.**</span></span> <span data-ttu-id="3157e-112">浮動小数点数を操作する場合、それらがメモリ内で常に正確な表現が使用されているとは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3157e-112">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="3157e-113">これにより、値の比較や `Mod` 演算子など、特定の操作によって、予期しない結果につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3157e-113">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="3157e-114">詳細については、「[データ型のトラブルシューティング](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3157e-114">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="3157e-115">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="3157e-115">**Widening.**</span></span> <span data-ttu-id="3157e-116">`Single` データ型は、`Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="3157e-116">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="3157e-117">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、`Single` を `Double` に変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3157e-117">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="3157e-118">**末尾のゼロ。**</span><span class="sxs-lookup"><span data-stu-id="3157e-118">**Trailing Zeros.**</span></span> <span data-ttu-id="3157e-119">浮動小数点データ型には、末尾がゼロの文字の内部表現はありません。</span><span class="sxs-lookup"><span data-stu-id="3157e-119">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="3157e-120">たとえば、4.2000 と 4.2 は区別されません。</span><span class="sxs-lookup"><span data-stu-id="3157e-120">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="3157e-121">そのため、浮動小数点値を表示または出力すると、末尾がゼロの文字は表示されません。</span><span class="sxs-lookup"><span data-stu-id="3157e-121">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="3157e-122">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="3157e-122">**Type Characters.**</span></span> <span data-ttu-id="3157e-123">あるリテラルにリテラルの型文字 `F` を付けると、そのリテラルは `Single` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="3157e-123">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="3157e-124">ある識別子に識別子の型文字 `!` を付けると、その識別子は整数型 (`Single`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="3157e-124">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="3157e-125">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="3157e-125">**Framework Type.**</span></span> <span data-ttu-id="3157e-126">.NET Framework において対応する型は、<xref:System.Single?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="3157e-126">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3157e-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="3157e-127">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="3157e-128">データの種類</span><span class="sxs-lookup"><span data-stu-id="3157e-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="3157e-129">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="3157e-129">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="3157e-130">Double 型</span><span class="sxs-lookup"><span data-stu-id="3157e-130">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="3157e-131">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="3157e-131">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="3157e-132">変換の概要</span><span class="sxs-lookup"><span data-stu-id="3157e-132">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="3157e-133">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="3157e-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="3157e-134">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="3157e-134">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
