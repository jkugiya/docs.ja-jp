---
description: '詳細情報: UShort データ型 (Visual Basic)'
title: UShort 型
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 9c709e2110aef4281c348f697408044a191314c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774981"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="69f8e-103">UShort データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69f8e-103">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="69f8e-104">0 から 65,535 までの値の範囲の符号なし 16 ビット (2 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="69f8e-104">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69f8e-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="69f8e-105">Remarks</span></span>

 <span data-ttu-id="69f8e-106">`Byte` には大きすぎるバイナリ データを格納する場合に、`UShort` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="69f8e-106">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="69f8e-107">`UShort` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="69f8e-107">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="69f8e-108">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="69f8e-108">Literal assignments</span></span>

<span data-ttu-id="69f8e-109">`UShort` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="69f8e-109">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="69f8e-110">整数リテラルが `UShort` の範囲外にある場合 (つまり、<xref:System.UInt16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="69f8e-110">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="69f8e-111">次の例では、整数 65,034 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`UShort` 値に代入されています。</span><span class="sxs-lookup"><span data-stu-id="69f8e-111">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="69f8e-112">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="69f8e-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="69f8e-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="69f8e-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="69f8e-114">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="69f8e-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="69f8e-115">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="69f8e-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="69f8e-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="69f8e-116">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="69f8e-117">数値リテラルには、次の例に示すように、`US` または `us` [型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めて、`UShort` データ型を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="69f8e-117">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="69f8e-118">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="69f8e-118">Programming tips</span></span>
  
- <span data-ttu-id="69f8e-119">**負の数値。**</span><span class="sxs-lookup"><span data-stu-id="69f8e-119">**Negative Numbers.**</span></span> <span data-ttu-id="69f8e-120">`UShort` は符号なしの型であるため、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="69f8e-120">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="69f8e-121">`UShort` 型に評価される式で、単項マイナス (`-`) 演算子を使用すると、Visual Basic で式が最初に `Integer` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="69f8e-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="69f8e-122">**CLS 準拠。**</span><span class="sxs-lookup"><span data-stu-id="69f8e-122">**CLS Compliance.**</span></span> <span data-ttu-id="69f8e-123">`UShort` データ型は[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS) に含まれないため、CLS に準拠しているコードではそれを使用するコンポーネントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="69f8e-123">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="69f8e-124">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="69f8e-124">**Widening.**</span></span> <span data-ttu-id="69f8e-125">`UShort` データ型は、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、および `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="69f8e-125">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="69f8e-126">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、これらの型のいずれかに `UShort` を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="69f8e-126">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="69f8e-127">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="69f8e-127">**Type Characters.**</span></span> <span data-ttu-id="69f8e-128">あるリテラルにリテラルの型文字 `US` を付けると、そのリテラルは `UShort` データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="69f8e-128">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="69f8e-129">`UShort` には識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="69f8e-129">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="69f8e-130">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="69f8e-130">**Framework Type.**</span></span> <span data-ttu-id="69f8e-131">.NET Framework において対応する型は、<xref:System.UInt16?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="69f8e-131">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f8e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="69f8e-132">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="69f8e-133">データの種類</span><span class="sxs-lookup"><span data-stu-id="69f8e-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="69f8e-134">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="69f8e-134">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="69f8e-135">変換の概要</span><span class="sxs-lookup"><span data-stu-id="69f8e-135">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="69f8e-136">方法: 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="69f8e-136">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="69f8e-137">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="69f8e-137">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
