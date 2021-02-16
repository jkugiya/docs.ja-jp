---
description: '詳細情報: 型文字 (Visual Basic)'
title: 型文字
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: d1afccb821d2ffb4dfabe3c38e0db4a7f902c164
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454548"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="22cd3-103">型文字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22cd3-103">Type characters (Visual Basic)</span></span>

<span data-ttu-id="22cd3-104">宣言ステートメントでデータ型を指定するだけでなく、"*型文字*" を使用して一部のプログラミング要素のデータ型を強制的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-104">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="22cd3-105">型文字は、要素の直後に指定する必要があります。その間にはどのような種類の文字も指定できません。</span><span class="sxs-lookup"><span data-stu-id="22cd3-105">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="22cd3-106">型文字は、要素の名前の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="22cd3-106">The type character is not part of the name of the element.</span></span> <span data-ttu-id="22cd3-107">型文字で定義された要素は、型文字を使用せずに参照できます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-107">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="22cd3-108">識別子の型文字</span><span class="sxs-lookup"><span data-stu-id="22cd3-108">Identifier type characters</span></span>

<span data-ttu-id="22cd3-109">Visual Basic には、変数または定数のデータ型を指定するために宣言で使用できる、一連の "*識別子の型文字*" が用意されています。</span><span class="sxs-lookup"><span data-stu-id="22cd3-109">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="22cd3-110">使用できる識別子の型文字と使用例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-110">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="22cd3-111">識別子の型文字</span><span class="sxs-lookup"><span data-stu-id="22cd3-111">Identifier type character</span></span>|<span data-ttu-id="22cd3-112">データの種類</span><span class="sxs-lookup"><span data-stu-id="22cd3-112">Data type</span></span>|<span data-ttu-id="22cd3-113">例</span><span class="sxs-lookup"><span data-stu-id="22cd3-113">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="22cd3-114">`Boolean`、`Byte`、`Char`、`Date`、`Object`、`SByte`、`Short`、`UInteger`、`ULong`、または `UShort` データ型、あるいは配列や構造体などの複合データ型には、識別子の型文字はありません。</span><span class="sxs-lookup"><span data-stu-id="22cd3-114">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="22cd3-115">場合によっては、`$` 文字を Visual Basic 関数に追加して (`Left` ではなく `Left$` など)、`String` 型の戻り値を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-115">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="22cd3-116">すべての場合で、識別子の型文字は識別子名の直後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22cd3-116">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="22cd3-117">リテラルの型文字</span><span class="sxs-lookup"><span data-stu-id="22cd3-117">Literal type characters</span></span>

<span data-ttu-id="22cd3-118">"*リテラル*" は、あるデータ型の特定の値のテキスト表現です。</span><span class="sxs-lookup"><span data-stu-id="22cd3-118">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="22cd3-119">既定のリテラル型</span><span class="sxs-lookup"><span data-stu-id="22cd3-119">Default literal types</span></span>

<span data-ttu-id="22cd3-120">通常は、コードに表示されるリテラルの形式によって、そのデータ型が決まります。</span><span class="sxs-lookup"><span data-stu-id="22cd3-120">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="22cd3-121">次の表に既定の型を示します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-121">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="22cd3-122">テキスト形式のリテラル</span><span class="sxs-lookup"><span data-stu-id="22cd3-122">Textual form of literal</span></span>|<span data-ttu-id="22cd3-123">既定のデータ型</span><span class="sxs-lookup"><span data-stu-id="22cd3-123">Default data type</span></span>|<span data-ttu-id="22cd3-124">例</span><span class="sxs-lookup"><span data-stu-id="22cd3-124">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="22cd3-125">数値、小数部なし</span><span class="sxs-lookup"><span data-stu-id="22cd3-125">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="22cd3-126">数値、小数部なし、`Integer` には大きすぎる</span><span class="sxs-lookup"><span data-stu-id="22cd3-126">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="22cd3-127">数値、小数部あり</span><span class="sxs-lookup"><span data-stu-id="22cd3-127">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="22cd3-128">二重引用符で囲まれている</span><span class="sxs-lookup"><span data-stu-id="22cd3-128">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="22cd3-129">シャープ記号で囲まれている</span><span class="sxs-lookup"><span data-stu-id="22cd3-129">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="22cd3-130">強制リテラル型</span><span class="sxs-lookup"><span data-stu-id="22cd3-130">Forced literal types</span></span>

<span data-ttu-id="22cd3-131">Visual Basic には一連の "*リテラルの型文字*" が用意されています。これらを使用して、リテラルの形式が示すデータ型以外のデータ型に強制的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-131">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="22cd3-132">これを行うには、リテラルの末尾に文字を追加します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-132">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="22cd3-133">使用できるリテラルの型文字と使用例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-133">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="22cd3-134">リテラルの型文字</span><span class="sxs-lookup"><span data-stu-id="22cd3-134">Literal type character</span></span>|<span data-ttu-id="22cd3-135">データの種類</span><span class="sxs-lookup"><span data-stu-id="22cd3-135">Data type</span></span>|<span data-ttu-id="22cd3-136">例</span><span class="sxs-lookup"><span data-stu-id="22cd3-136">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="22cd3-137">`Boolean`、`Byte`、`Date`、`Object`、`SByte`、または `String` データ型、あるいは配列や構造体などの複合データ型には、リテラルの型文字はありません。</span><span class="sxs-lookup"><span data-stu-id="22cd3-137">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="22cd3-138">リテラルは、変数、定数、および式と同様に、識別子の型文字(`%`、`&`、`@`、`!`、`#`、`$`) も使用できます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-138">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="22cd3-139">ただし、リテラルの型文字 (`S`、`I`、`L`、`D`、`F`、`R`、`C`) はリテラルでしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="22cd3-139">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="22cd3-140">すべての場合で、リテラルの型文字はリテラル値の直後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22cd3-140">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="22cd3-141">16 進数、2 進数、および 8 進数のリテラル</span><span class="sxs-lookup"><span data-stu-id="22cd3-141">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="22cd3-142">通常、コンパイラは、整数リテラルを 10 進法 (基数 10) で解釈します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-142">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="22cd3-143">整数リテラルは、`&H` プレフィックスを使用して 16 進法 (基数 16) として、`&B` プレフィックスを使用して 2 進法 (基数 2) として、また `&O` プレフィックスを使用して 8 進法 (基数 8) として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-143">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="22cd3-144">プレフィックスの後の数字は、その記数法に適している必要があります。</span><span class="sxs-lookup"><span data-stu-id="22cd3-144">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="22cd3-145">次の表に例を示します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-145">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="22cd3-146">基数</span><span class="sxs-lookup"><span data-stu-id="22cd3-146">Number base</span></span>|<span data-ttu-id="22cd3-147">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="22cd3-147">Prefix</span></span>|<span data-ttu-id="22cd3-148">有効な数値</span><span class="sxs-lookup"><span data-stu-id="22cd3-148">Valid digit values</span></span>|<span data-ttu-id="22cd3-149">例</span><span class="sxs-lookup"><span data-stu-id="22cd3-149">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="22cd3-150">16 進数 (基数 16)。</span><span class="sxs-lookup"><span data-stu-id="22cd3-150">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="22cd3-151">0 - 9 および A - F</span><span class="sxs-lookup"><span data-stu-id="22cd3-151">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="22cd3-152">2 進数 (基数 2)</span><span class="sxs-lookup"><span data-stu-id="22cd3-152">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="22cd3-153">0-1</span><span class="sxs-lookup"><span data-stu-id="22cd3-153">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="22cd3-154">8 進数 (基数 8)。</span><span class="sxs-lookup"><span data-stu-id="22cd3-154">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="22cd3-155">0-7</span><span class="sxs-lookup"><span data-stu-id="22cd3-155">0-7</span></span>|`&O77`|

<span data-ttu-id="22cd3-156">Visual Basic 2017 以降では、アンダースコア文字 (`_`) をグループ区切り記号として使用して、整数リテラルを読みやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-156">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="22cd3-157">次の例では、`_` 文字を使用して、2 進数リテラルを 8 ビットずつのグループにグループ化しています。</span><span class="sxs-lookup"><span data-stu-id="22cd3-157">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="22cd3-158">プレフィックス付きリテラルの後にリテラルの型文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-158">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="22cd3-159">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-159">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="22cd3-160">前の例では、`counter` は 10 進値 -32768、`flags` は 10 進値 +32768 を含みます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-160">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="22cd3-161">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="22cd3-161">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="22cd3-162">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="22cd3-162">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="22cd3-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="22cd3-163">See also</span></span>

- [<span data-ttu-id="22cd3-164">データの種類</span><span class="sxs-lookup"><span data-stu-id="22cd3-164">Data Types</span></span>](index.md)
- [<span data-ttu-id="22cd3-165">基本データ型</span><span class="sxs-lookup"><span data-stu-id="22cd3-165">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="22cd3-166">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="22cd3-166">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="22cd3-167">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="22cd3-167">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="22cd3-168">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="22cd3-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="22cd3-169">変数宣言</span><span class="sxs-lookup"><span data-stu-id="22cd3-169">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="22cd3-170">データの種類</span><span class="sxs-lookup"><span data-stu-id="22cd3-170">Data Types</span></span>](../../../language-reference/data-types/index.md)
