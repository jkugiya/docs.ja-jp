---
description: '詳細情報: Long データ型 (Visual Basic)'
title: Long 型
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: cb4a22fa3b9d1440f755c8a3412aa3a918b7f261
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792181"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="92327-103">Long データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92327-103">Long data type (Visual Basic)</span></span>

<span data-ttu-id="92327-104">-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807 (9.2...E+18) までの値の範囲の符号付き 64 ビット (8 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="92327-104">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="92327-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="92327-105">Remarks</span></span>

<span data-ttu-id="92327-106">`Long` データ型を使用して、`Integer` データ型には大きすぎて収まらない整数値を格納します。</span><span class="sxs-lookup"><span data-stu-id="92327-106">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="92327-107">`Long` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="92327-107">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="92327-108">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="92327-108">Literal assignments</span></span>

<span data-ttu-id="92327-109">`Long` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="92327-109">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="92327-110">整数リテラルが `Long` の範囲外にある場合 (つまり、<xref:System.Int64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="92327-110">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="92327-111">次の例では、整数 4,294,967,296 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Long` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="92327-111">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="92327-112">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="92327-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="92327-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="92327-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="92327-114">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="92327-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="92327-115">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="92327-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="92327-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="92327-116">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="92327-117">数値リテラルには、次の例に示すように、`L` [型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めて、`Long` データ型を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="92327-117">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="92327-118">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="92327-118">Programming tips</span></span>

- <span data-ttu-id="92327-119">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="92327-119">**Interop Considerations.**</span></span> <span data-ttu-id="92327-120">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、他の環境では整数型 (`Long`) のデータ幅 (32 ビット) が異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="92327-120">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="92327-121">そのようなコンポーネントに 32 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 (`Long`) ではなく短整数型 (`Integer`) として宣言します。</span><span class="sxs-lookup"><span data-stu-id="92327-121">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="92327-122">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="92327-122">**Widening.**</span></span> <span data-ttu-id="92327-123">`Long` データ型は、`Decimal`、`Single`、または `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="92327-123">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="92327-124">これは、`Long` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="92327-124">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="92327-125">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="92327-125">**Type Characters.**</span></span> <span data-ttu-id="92327-126">あるリテラルにリテラルの型文字 `L` を付けると、そのリテラルは `Long` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="92327-126">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="92327-127">ある識別子に識別子の型文字 `&` を付けると、その識別子は整数型 (`Long`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="92327-127">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="92327-128">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="92327-128">**Framework Type.**</span></span> <span data-ttu-id="92327-129">.NET Framework において対応する型は、<xref:System.Int64?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="92327-129">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="92327-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="92327-130">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="92327-131">データの種類</span><span class="sxs-lookup"><span data-stu-id="92327-131">Data Types</span></span>](index.md)
- [<span data-ttu-id="92327-132">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="92327-132">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="92327-133">Short データ型</span><span class="sxs-lookup"><span data-stu-id="92327-133">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="92327-134">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="92327-134">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="92327-135">変換の概要</span><span class="sxs-lookup"><span data-stu-id="92327-135">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="92327-136">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="92327-136">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
