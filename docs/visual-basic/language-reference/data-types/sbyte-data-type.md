---
description: '詳細情報: SByte データ型 (Visual Basic)'
title: SByte 型
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e6e314a34469083433289c0fff9b404d4549824d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792168"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="98249-103">SByte データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98249-103">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="98249-104">-128 から 127 までの符号付き 8 ビット (1 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="98249-104">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="98249-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="98249-105">Remarks</span></span>

<span data-ttu-id="98249-106">完全なデータ幅の `Integer` や半分のデータ幅の `Short` も必要としない整数値を格納するには、`SByte` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="98249-106">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="98249-107">場合によっては、共通言語ランタイムで `SByte` 変数を緊密にパックし、メモリ消費を節約できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="98249-107">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="98249-108">`SByte` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="98249-108">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="98249-109">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="98249-109">Literal assignments</span></span>

<span data-ttu-id="98249-110">`SByte` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="98249-110">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="98249-111">次の例では、整数 -102 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`SByte` 値に代入されています。</span><span class="sxs-lookup"><span data-stu-id="98249-111">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="98249-112">この例では、`/removeintchecks` コンパイラ スイッチを使用してコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98249-112">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="98249-113">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="98249-113">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="98249-114">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="98249-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="98249-115">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="98249-115">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="98249-116">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="98249-116">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="98249-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="98249-117">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="98249-118">整数リテラルが `SByte` の範囲外にある場合 (つまり、<xref:System.SByte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.SByte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="98249-118">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="98249-119">整数リテラルにサフィックスがない場合は、[Integer](integer-data-type.md) が推定されます。</span><span class="sxs-lookup"><span data-stu-id="98249-119">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="98249-120">整数リテラルが `Integer` 型の範囲外の場合は、[Long](long-data-type.md) が推定されます。</span><span class="sxs-lookup"><span data-stu-id="98249-120">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="98249-121">つまり、前の例では、数値リテラル `0x9A` と `0b10011010` は値が 156 の 32 ビット符号付き整数として解釈され、これは <xref:System.SByte.MaxValue?displayProperty=nameWithType> を超えています。</span><span class="sxs-lookup"><span data-stu-id="98249-121">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="98249-122">`SByte` に 10 進数以外の整数を代入する次のようなコードを正常にコンパイルするには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="98249-122">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="98249-123">`/removeintchecks` コンパイラ スイッチを使用してコンパイルすることにより、整数境界のチェックを無効にします。</span><span class="sxs-lookup"><span data-stu-id="98249-123">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="98249-124">`SByte` に代入するリテラル値を明示的に定義するには、[型文字](../../programming-guide/language-features/data-types/type-characters.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="98249-124">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="98249-125">次の例では、負のリテラル `Short` 値を `SByte` に代入します。</span><span class="sxs-lookup"><span data-stu-id="98249-125">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="98249-126">負の数値の場合は、数値リテラルの上位ワードの上位ビットを設定する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="98249-126">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="98249-127">この例の場合、これはリテラル `Short` 値のビット 15 です。</span><span class="sxs-lookup"><span data-stu-id="98249-127">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="98249-128">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="98249-128">Programming tips</span></span>

- <span data-ttu-id="98249-129">**CLS 準拠。**</span><span class="sxs-lookup"><span data-stu-id="98249-129">**CLS Compliance.**</span></span> <span data-ttu-id="98249-130">`SByte` データ型は[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) に含まれないため、CLS に準拠しているコードではそれを使用するコンポーネントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="98249-130">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="98249-131">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="98249-131">**Widening.**</span></span> <span data-ttu-id="98249-132">`SByte` データ型は、`Short`、`Integer`、`Long`、`Decimal`、`Single`、および `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="98249-132">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="98249-133">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、これらの型のいずれかに `SByte` を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="98249-133">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="98249-134">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="98249-134">**Type Characters.**</span></span> <span data-ttu-id="98249-135">`SByte` には、リテラルの型文字も識別子の型文字も含まれません。</span><span class="sxs-lookup"><span data-stu-id="98249-135">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="98249-136">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="98249-136">**Framework Type.**</span></span> <span data-ttu-id="98249-137">.NET Framework において対応する型は、<xref:System.SByte?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="98249-137">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="98249-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="98249-138">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="98249-139">データの種類</span><span class="sxs-lookup"><span data-stu-id="98249-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="98249-140">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="98249-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="98249-141">変換の概要</span><span class="sxs-lookup"><span data-stu-id="98249-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="98249-142">Short データ型</span><span class="sxs-lookup"><span data-stu-id="98249-142">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="98249-143">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="98249-143">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="98249-144">Long データ型</span><span class="sxs-lookup"><span data-stu-id="98249-144">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="98249-145">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="98249-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
