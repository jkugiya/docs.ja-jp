---
description: '詳細情報: バイト (Byte) データ型 (Visual Basic)'
title: バイト型 (Byte)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 983af36d8340b5df7ac44782bf56349901460c20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731228"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="0bbef-103">バイト (Byte) データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bbef-103">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="0bbef-104">0 から 255 までの値の範囲の符号なし 8 ビット (1 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="0bbef-104">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="0bbef-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="0bbef-105">Remarks</span></span>

<span data-ttu-id="0bbef-106">バイナリ データを格納するには、`Byte` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bbef-106">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="0bbef-107">`Byte` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="0bbef-107">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="0bbef-108">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="0bbef-108">Literal assignments</span></span>

<span data-ttu-id="0bbef-109">`Byte` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="0bbef-109">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0bbef-110">整数リテラルが `Byte` の範囲外にある場合 (つまり、<xref:System.Byte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Byte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="0bbef-110">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="0bbef-111">次の例では、整数 201 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[Integer](integer-data-type.md) から `byte` 値に暗黙的に変換されています。</span><span class="sxs-lookup"><span data-stu-id="0bbef-111">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="0bbef-112">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="0bbef-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0bbef-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="0bbef-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0bbef-114">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0bbef-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="0bbef-115">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0bbef-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0bbef-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0bbef-116">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="0bbef-117">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="0bbef-117">Programming tips</span></span>

- <span data-ttu-id="0bbef-118">**負の数値。**</span><span class="sxs-lookup"><span data-stu-id="0bbef-118">**Negative Numbers.**</span></span> <span data-ttu-id="0bbef-119">`Byte` は符号なしの型であるため、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="0bbef-119">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="0bbef-120">`Byte` 型に評価される式で、単項マイナス (`-`) 演算子を使用すると、Visual Basic で式が最初に `Short` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="0bbef-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="0bbef-121">**形式変換。**</span><span class="sxs-lookup"><span data-stu-id="0bbef-121">**Format Conversions.**</span></span> <span data-ttu-id="0bbef-122">Visual Basic でファイルの読み取りまたは書き込みを行うとき、または DLL、メソッド、およびプロパティを呼び出すときに、データ形式を自動的に変換させることができます。</span><span class="sxs-lookup"><span data-stu-id="0bbef-122">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="0bbef-123">`Byte` 変数および配列に格納されているバイナリ データは、そのような形式の変換時に保持されます。</span><span class="sxs-lookup"><span data-stu-id="0bbef-123">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="0bbef-124">バイナリ データには `String` 変数を使用しないでください。ANSI 形式と Unicode 形式間の変換時に、その内容が破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0bbef-124">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="0bbef-125">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="0bbef-125">**Widening.**</span></span> <span data-ttu-id="0bbef-126">`Byte` データ型は、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、または `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="0bbef-126">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="0bbef-127">これは、<xref:System.OverflowException?displayProperty=nameWithType> エラーを発生させることなく、これらの型のいずれかに `Byte` を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0bbef-127">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="0bbef-128">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="0bbef-128">**Type Characters.**</span></span> <span data-ttu-id="0bbef-129">`Byte` には、リテラルの型文字も識別子の型文字も含まれません。</span><span class="sxs-lookup"><span data-stu-id="0bbef-129">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="0bbef-130">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="0bbef-130">**Framework Type.**</span></span> <span data-ttu-id="0bbef-131">.NET Framework において対応する型は、<xref:System.Byte?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="0bbef-131">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="0bbef-132">例</span><span class="sxs-lookup"><span data-stu-id="0bbef-132">Example</span></span>

 <span data-ttu-id="0bbef-133">次の例では、`b` は `Byte` 変数です。</span><span class="sxs-lookup"><span data-stu-id="0bbef-133">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="0bbef-134">このステートメントでは、変数の範囲と、それに対するビットシフト演算子の適用を示しています。</span><span class="sxs-lookup"><span data-stu-id="0bbef-134">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="0bbef-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bbef-135">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="0bbef-136">データの種類</span><span class="sxs-lookup"><span data-stu-id="0bbef-136">Data Types</span></span>](index.md)
- [<span data-ttu-id="0bbef-137">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="0bbef-137">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="0bbef-138">変換の概要</span><span class="sxs-lookup"><span data-stu-id="0bbef-138">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="0bbef-139">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="0bbef-139">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
