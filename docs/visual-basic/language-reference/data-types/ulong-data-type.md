---
description: '詳細情報: ULong データ型 (Visual Basic)'
title: ULong 型
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 107100b4992be75dab574cbf274b53f506e267f3
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494598"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="1b213-103">ULong データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b213-103">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="1b213-104">0 から 18,446,744,073,709,551,615 (1.84 x 10 ^ 19 以上) までの値の範囲の符号なし 64 ビット (8 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="1b213-104">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="1b213-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="1b213-105">Remarks</span></span>

<span data-ttu-id="1b213-106">`ULong` データ型は、`UInteger` には大きすぎるバイナリ データや、可能な限り最大の符号なし整数値を格納する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="1b213-106">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="1b213-107">`ULong` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="1b213-107">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="1b213-108">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="1b213-108">Literal assignments</span></span>

<span data-ttu-id="1b213-109">`ULong` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="1b213-109">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="1b213-110">整数リテラルが `ULong` の範囲外にある場合 (つまり、<xref:System.UInt64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1b213-110">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="1b213-111">次の例では、整数 7,934,076,125 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`ULong` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="1b213-111">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="1b213-112">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="1b213-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="1b213-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="1b213-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1b213-114">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1b213-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="1b213-115">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b213-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="1b213-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1b213-116">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="1b213-117">数値リテラルには、次の例に示すように、`UL` または `ul` [型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めて、`ULong` データ型を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="1b213-117">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="1b213-118">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="1b213-118">Programming tips</span></span>

- <span data-ttu-id="1b213-119">**負の数値。**</span><span class="sxs-lookup"><span data-stu-id="1b213-119">**Negative Numbers.**</span></span> <span data-ttu-id="1b213-120">`ULong` は符号なしの型であるため、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="1b213-120">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="1b213-121">`ULong` 型に評価される式で、単項マイナス (`-`) 演算子を使用すると、Visual Basic で式が最初に `Decimal` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="1b213-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="1b213-122">**CLS 準拠。**</span><span class="sxs-lookup"><span data-stu-id="1b213-122">**CLS Compliance.**</span></span> <span data-ttu-id="1b213-123">`ULong` データ型は[共通言語仕様](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS) に含まれないため、CLS に準拠しているコードではそれを使用するコンポーネントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="1b213-123">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="1b213-124">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="1b213-124">**Interop Considerations.**</span></span> <span data-ttu-id="1b213-125">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、`ulong` などの型は、他の環境ではデータ幅 (32 ビット) が異なる可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1b213-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="1b213-126">そのようなコンポーネントに 32 ビットの引数を渡す場合は、Visual Basic のマネージド コードで、`ULong` ではなく `UInteger` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="1b213-126">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="1b213-127">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="1b213-127">**Widening.**</span></span> <span data-ttu-id="1b213-128">`ULong` データ型は、`Decimal`、`Single`、および `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="1b213-128">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="1b213-129">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、これらの型のいずれかに `ULong` を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1b213-129">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="1b213-130">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="1b213-130">**Type Characters.**</span></span> <span data-ttu-id="1b213-131">あるリテラルにリテラルの型文字 `UL` を付けると、そのリテラルは `ULong` データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="1b213-131">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="1b213-132">`ULong` には識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="1b213-132">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="1b213-133">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="1b213-133">**Framework Type.**</span></span> <span data-ttu-id="1b213-134">.NET Framework において対応する型は、<xref:System.UInt64?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="1b213-134">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b213-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b213-135">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="1b213-136">データの種類</span><span class="sxs-lookup"><span data-stu-id="1b213-136">Data Types</span></span>](index.md)
- [<span data-ttu-id="1b213-137">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="1b213-137">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="1b213-138">変換の概要</span><span class="sxs-lookup"><span data-stu-id="1b213-138">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="1b213-139">方法: 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="1b213-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="1b213-140">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="1b213-140">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
