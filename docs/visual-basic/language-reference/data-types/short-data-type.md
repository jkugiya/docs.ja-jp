---
description: '詳細情報: Short データ型 (Visual Basic)'
title: Short 型
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8c6bee45355548b3a32d74d059159918b4009fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792142"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="9cef9-103">Short データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cef9-103">Short data type (Visual Basic)</span></span>

<span data-ttu-id="9cef9-104">-32,768 から 32,767 までの符号付き 16 ビット (2 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="9cef9-104">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cef9-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="9cef9-105">Remarks</span></span>  

 <span data-ttu-id="9cef9-106">`Integer` の完全なデータ幅を必要としない整数値を格納するには、`Short` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="9cef9-106">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="9cef9-107">場合によっては、共通言語ランタイムで `Short` 変数を緊密にパックし、メモリ消費を節約できます。</span><span class="sxs-lookup"><span data-stu-id="9cef9-107">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="9cef9-108">`Short` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="9cef9-108">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="9cef9-109">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="9cef9-109">Literal assignments</span></span>

<span data-ttu-id="9cef9-110">`Short` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="9cef9-110">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="9cef9-111">整数リテラルが `Short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9cef9-111">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="9cef9-112">次の例では、整数 1,034 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[Integer](integer-data-type.md) から `Short` 値に暗黙的に変換されています。</span><span class="sxs-lookup"><span data-stu-id="9cef9-112">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="9cef9-113">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="9cef9-113">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="9cef9-114">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="9cef9-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9cef9-115">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9cef9-115">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="9cef9-116">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9cef9-116">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="9cef9-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9cef9-117">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="9cef9-118">数値リテラルには、次の例に示すように、`S` [型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めて、`Short` データ型を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9cef9-118">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="9cef9-119">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="9cef9-119">Programming tips</span></span>

- <span data-ttu-id="9cef9-120">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="9cef9-120">**Widening.**</span></span> <span data-ttu-id="9cef9-121">`Short` データ型は、`Integer`、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="9cef9-121">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="9cef9-122">これは、`Short` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9cef9-122">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="9cef9-123">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="9cef9-123">**Type Characters.**</span></span> <span data-ttu-id="9cef9-124">あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="9cef9-124">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="9cef9-125">`Short` には識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="9cef9-125">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="9cef9-126">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="9cef9-126">**Framework Type.**</span></span> <span data-ttu-id="9cef9-127">.NET Framework において対応する型は、<xref:System.Int16?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="9cef9-127">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cef9-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cef9-128">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="9cef9-129">データの種類</span><span class="sxs-lookup"><span data-stu-id="9cef9-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="9cef9-130">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="9cef9-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="9cef9-131">変換の概要</span><span class="sxs-lookup"><span data-stu-id="9cef9-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="9cef9-132">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="9cef9-132">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="9cef9-133">Long データ型</span><span class="sxs-lookup"><span data-stu-id="9cef9-133">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="9cef9-134">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="9cef9-134">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
