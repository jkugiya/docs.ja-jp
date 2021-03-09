---
description: '詳細情報: UInteger データ型'
title: UInteger 型
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: c3c04f746f0e2cf15bc1881544b93a538dbdc04e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104836"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="81c66-103">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="81c66-103">UInteger data type</span></span>

<span data-ttu-id="81c66-104">0 から 4,294,967,295 までの値の範囲の符号なし 32 ビット (4 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="81c66-104">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="81c66-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="81c66-105">Remarks</span></span>

<span data-ttu-id="81c66-106">`UInteger` データ型は、最も効率的なデータ幅で最も大きな符号なしの値を提供します。</span><span class="sxs-lookup"><span data-stu-id="81c66-106">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="81c66-107">`UInteger` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="81c66-107">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="81c66-108">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="81c66-108">Literal assignments</span></span>

<span data-ttu-id="81c66-109">`UInteger` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="81c66-109">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="81c66-110">整数リテラルが `UInteger` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="81c66-110">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="81c66-111">次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`UInteger` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="81c66-111">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="81c66-112">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="81c66-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="81c66-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="81c66-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="81c66-114">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="81c66-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="81c66-115">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="81c66-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="81c66-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="81c66-116">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="81c66-117">数値リテラルには、次の例に示すように、`UI` または `ui` [型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めて、`UInteger` データ型を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="81c66-117">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="81c66-118">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="81c66-118">Programming tips</span></span>

<span data-ttu-id="81c66-119">`UInteger` データ型および `Integer` データ型は、32 ビット プロセッサで最適なパフォーマンスを発揮します。これは、より小さい整数型 (`UShort`、`Short`、`Byte`、`SByte`) では、使用するビット数が少なくても、読み込み、格納、およびフェッチにかかる時間が長くなるためです。</span><span class="sxs-lookup"><span data-stu-id="81c66-119">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="81c66-120">**負の数値。**</span><span class="sxs-lookup"><span data-stu-id="81c66-120">**Negative Numbers.**</span></span> <span data-ttu-id="81c66-121">`UInteger` は符号なしの型であるため、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="81c66-121">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="81c66-122">`UInteger` 型に評価される式で、単項マイナス (`-`) 演算子を使用すると、Visual Basic で式が最初に `Long` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="81c66-122">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="81c66-123">**CLS 準拠。**</span><span class="sxs-lookup"><span data-stu-id="81c66-123">**CLS Compliance.**</span></span> <span data-ttu-id="81c66-124">`UInteger` データ型は[共通言語仕様](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS) に含まれないため、CLS に準拠しているコードではそれを使用するコンポーネントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="81c66-124">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="81c66-125">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="81c66-125">**Interop Considerations.**</span></span> <span data-ttu-id="81c66-126">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、`uint` などの型は、他の環境ではデータ幅 (16 ビット) が異なる可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="81c66-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="81c66-127">そのようなコンポーネントに 16 ビットの引数を渡す場合は、Visual Basic のマネージド コードで、`UInteger` ではなく `UShort` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="81c66-127">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="81c66-128">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="81c66-128">**Widening.**</span></span> <span data-ttu-id="81c66-129">`UInteger` データ型は、`Long`、`ULong`、`Decimal`、`Single`、および `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="81c66-129">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="81c66-130">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、これらの型のいずれかに `UInteger` を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="81c66-130">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="81c66-131">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="81c66-131">**Type Characters.**</span></span> <span data-ttu-id="81c66-132">あるリテラルにリテラルの型文字 `UI` を付けると、そのリテラルは `UInteger` データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="81c66-132">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="81c66-133">`UInteger` には識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="81c66-133">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="81c66-134">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="81c66-134">**Framework Type.**</span></span> <span data-ttu-id="81c66-135">.NET Framework において対応する型は、<xref:System.UInt32?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="81c66-135">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="81c66-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="81c66-136">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="81c66-137">データの種類</span><span class="sxs-lookup"><span data-stu-id="81c66-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="81c66-138">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="81c66-138">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="81c66-139">変換の概要</span><span class="sxs-lookup"><span data-stu-id="81c66-139">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="81c66-140">方法: 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="81c66-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="81c66-141">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="81c66-141">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
