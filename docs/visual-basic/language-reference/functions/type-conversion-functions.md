---
description: '詳細情報: データ型変換関数 (Visual Basic)'
title: CString
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: c2e701b522bbeb32f4f6f448acd78e09b0616f46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731085"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="78fb1-103">データ型変換関数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78fb1-103">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="78fb1-104">これらの関数は、インラインでコンパイルされます。つまり、変換コードは、式を評価するコードに含まれます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-104">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="78fb1-105">変換を実行するためのプロシージャの呼び出しがないことがありますが、これにより、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-105">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="78fb1-106">各関数では、式を特定のデータ型に強制的に変換します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-106">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="78fb1-107">構文</span><span class="sxs-lookup"><span data-stu-id="78fb1-107">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="78fb1-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="78fb1-108">Part</span></span>

`expression`  
<span data-ttu-id="78fb1-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="78fb1-109">Required.</span></span> <span data-ttu-id="78fb1-110">ソース データ型の任意の式。</span><span class="sxs-lookup"><span data-stu-id="78fb1-110">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="78fb1-111">戻り値のデータ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-111">Return Value Data Type</span></span>

<span data-ttu-id="78fb1-112">次の表に示すように、関数名によって、それが返す値のデータ型が決まります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-112">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="78fb1-113">関数名</span><span class="sxs-lookup"><span data-stu-id="78fb1-113">Function name</span></span>|<span data-ttu-id="78fb1-114">戻り値のデータ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-114">Return data type</span></span>|<span data-ttu-id="78fb1-115">`expression` 引数の範囲</span><span class="sxs-lookup"><span data-stu-id="78fb1-115">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="78fb1-116">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-116">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="78fb1-117">任意の有効な `Char` または `String` または数値式。</span><span class="sxs-lookup"><span data-stu-id="78fb1-117">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="78fb1-118">Byte データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-118">Byte Data Type</span></span>](../data-types/byte-data-type.md)|<span data-ttu-id="78fb1-119"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) から <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (符号なし)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-119"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="78fb1-120">Visual Basic 15.8 以降、Visual Basic では、`CByte` 関数による浮動小数点からバイトへの変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-120">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-121">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-121">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="78fb1-122">Char データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-122">Char Data Type</span></span>](../data-types/char-data-type.md)|<span data-ttu-id="78fb1-123">任意の有効な `Char` または `String` 式。`String` の最初の文字のみが変換されます。値には 0 から 65535 (符号なし) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-123">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="78fb1-124">Date データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-124">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="78fb1-125">日付と時刻の任意の有効な表現。</span><span class="sxs-lookup"><span data-stu-id="78fb1-125">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="78fb1-126">Double 型</span><span class="sxs-lookup"><span data-stu-id="78fb1-126">Double Data Type</span></span>](../data-types/double-data-type.md)|<span data-ttu-id="78fb1-127">負の値の場合は -1.79769313486231570E+308 から -4.94065645841246544E-324 for negative values。正の値の場合は 4.94065645841246544E-324 から 1.79769313486231570E+308。</span><span class="sxs-lookup"><span data-stu-id="78fb1-127">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="78fb1-128">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-128">Decimal Data Type</span></span>](../data-types/decimal-data-type.md)|<span data-ttu-id="78fb1-129">ゼロスケールの数値 (つまり、小数点以下を含まない数値) の場合は +/-79,228,162,514,264,337,593,543,950,335。</span><span class="sxs-lookup"><span data-stu-id="78fb1-129">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="78fb1-130">小数点以下 28 桁の数値の場合の範囲は +/-7.9228162514264337593543950335 です。</span><span class="sxs-lookup"><span data-stu-id="78fb1-130">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="78fb1-131">0 以外の最小値は 0.0000000000000000000000000001 (+/-1E-28) です。</span><span class="sxs-lookup"><span data-stu-id="78fb1-131">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="78fb1-132">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-132">Integer Data Type</span></span>](../data-types/integer-data-type.md)|<span data-ttu-id="78fb1-133"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2147483648) から <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2147483647)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-133"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="78fb1-134">Visual Basic 15.8 以降、Visual Basic では、`CInt` 関数による浮動小数点から整数への変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-134">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-135">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-135">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="78fb1-136">Long データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-136">Long Data Type</span></span>](../data-types/long-data-type.md)|<span data-ttu-id="78fb1-137"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) から <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-137"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="78fb1-138">Visual Basic 15.8 以降、Visual Basic では、`CLng` 関数による浮動小数点から 64 ビット整数への変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-138">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-139">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-139">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="78fb1-140">Object 型</span><span class="sxs-lookup"><span data-stu-id="78fb1-140">Object Data Type</span></span>](../data-types/object-data-type.md)|<span data-ttu-id="78fb1-141">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="78fb1-141">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="78fb1-142">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-142">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)|<span data-ttu-id="78fb1-143"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) から <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-143"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="78fb1-144">Visual Basic 15.8 以降、Visual Basic では、`CSByte` 関数による浮動小数点から符号付きバイトへの変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-144">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-145">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-145">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="78fb1-146">Short データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-146">Short Data Type</span></span>](../data-types/short-data-type.md)|<span data-ttu-id="78fb1-147"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) から <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-147"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="78fb1-148">Visual Basic 15.8 以降、Visual Basic では、`CShort` 関数による浮動小数点から 16 ビット整数への変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-148">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-149">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-149">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="78fb1-150">Single データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-150">Single Data Type</span></span>](../data-types/single-data-type.md)|<span data-ttu-id="78fb1-151">負の値の場合は、-3.402823E+38 から -1.401298E-45。正の値の場合は、1.401298E-45 から 3.402823E+38。</span><span class="sxs-lookup"><span data-stu-id="78fb1-151">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="78fb1-152">String データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-152">String Data Type</span></span>](../data-types/string-data-type.md)|<span data-ttu-id="78fb1-153">`CStr` の戻り値は、`expression` 引数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-153">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="78fb1-154">「[CStr 関数の戻り値](return-values-for-the-cstr-function.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-154">See [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="78fb1-155">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-155">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)|<span data-ttu-id="78fb1-156"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) から <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-156"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="78fb1-157">Visual Basic 15.8 以降、Visual Basic では、`CUInt` 関数による浮動小数点から符号なし整数への変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-157">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-158">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-158">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="78fb1-159">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-159">ULong Data Type</span></span>](../data-types/ulong-data-type.md)|<span data-ttu-id="78fb1-160"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) から <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-160"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="78fb1-161">Visual Basic 15.8 以降、Visual Basic では、`CULng` 関数による浮動小数点から符号なし長整数への変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-161">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-162">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-162">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="78fb1-163">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="78fb1-163">UShort Data Type</span></span>](../data-types/ushort-data-type.md)|<span data-ttu-id="78fb1-164"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) から <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (符号なし)。小数部は丸められます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="78fb1-164"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="78fb1-165">Visual Basic 15.8 以降、Visual Basic では、`CUShort` 関数による浮動小数点から符号なし 16 ビット整数への変換のパフォーマンスが最適化されます。詳細については、「[解説](#remarks)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-165">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="78fb1-166">例については、「[CInt の例](#cint-example)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-166">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="78fb1-167"><sup>1</sup> 小数部は、*銀行型丸め* と呼ばれる特殊な種類の丸めの対象となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-167"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="78fb1-168">詳細については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-168">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="78fb1-169">Remarks</span><span class="sxs-lookup"><span data-stu-id="78fb1-169">Remarks</span></span>

<span data-ttu-id="78fb1-170">原則として、<xref:System.Convert> クラスで、または個々の型の構造体またはクラスで、`ToString()` などの .NET Framework メソッドに優先して、Visual Basic の型変換関数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-170">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="78fb1-171">Visual Basic 関数は、Visual Basic コードとの最適な相互作用のために設計されており、さらにそれらによって、ソースコードが短くなり、読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-171">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="78fb1-172">また、.NET Framework 変換メソッドでは、常に Visual Basic 関数と同じ結果が生成されるとは限りません。たとえば、`Boolean` を `Integer` に変換する場合などです。</span><span class="sxs-lookup"><span data-stu-id="78fb1-172">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="78fb1-173">詳細については、「[データ型のトラブルシューティング](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-173">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="78fb1-174">Visual Basic 15.8 以降、次のメソッドによって返される <xref:System.Single> または <xref:System.Double> 値を、整数変換関数 (`CByte`、`CShort`、`CInt`、`CLng`、`CSByte`、`CUShort`、`CUInt`、`CULng`) のいずれかに渡す場合に、浮動小数点から整数への変換のパフォーマンスが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-174">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="78fb1-175">この最適化によって、大量の整数変換を行うコードで、実行が最大 2 倍速くなります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-175">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="78fb1-176">次の例では、それらの最適化された浮動小数点から整数への変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-176">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="78fb1-177">動作</span><span class="sxs-lookup"><span data-stu-id="78fb1-177">Behavior</span></span>

- <span data-ttu-id="78fb1-178">**強制型変換。**</span><span class="sxs-lookup"><span data-stu-id="78fb1-178">**Coercion.**</span></span> <span data-ttu-id="78fb1-179">一般に、データ型変換関数を使用すると、操作の結果を、既定のデータ型ではなく、特定のデータ型に強制的に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-179">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="78fb1-180">たとえば、単精度、倍精度、または整数の算術演算が通常行われるところで、`CDec` を使用して、10 進数の算術演算を強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-180">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="78fb1-181">**変換の失敗。**</span><span class="sxs-lookup"><span data-stu-id="78fb1-181">**Failed Conversions.**</span></span> <span data-ttu-id="78fb1-182">関数に渡された `expression` が、変換先のデータ型の範囲外である場合、<xref:System.OverflowException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-182">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="78fb1-183">**小数部。**</span><span class="sxs-lookup"><span data-stu-id="78fb1-183">**Fractional Parts.**</span></span> <span data-ttu-id="78fb1-184">非整数値を整数型に変換する場合、整数変換関数 (`CByte`、`CInt`、`CLng`、`CSByte`、`CShort`、`CUInt`、`CULng`、および `CUShort`) で、小数部を削除し、値を最も近い整数に丸めます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-184">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="78fb1-185">小数部がちょうど 0.5 の場合、整数変換関数では、最も近い偶数の整数に丸められます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-185">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="78fb1-186">たとえば、0.5 は 0 に丸められ、1.5 と 2.5 は両方とも 2 に丸められます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-186">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="78fb1-187">これは、*銀行型丸め* と呼ばれることもあり、その目的は、そのような多数の数値を加算するときに累積する可能性があるバイアスを補正することです。</span><span class="sxs-lookup"><span data-stu-id="78fb1-187">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="78fb1-188">`CInt` と `CLng` は、<xref:Microsoft.VisualBasic.Conversion.Int%2A> 関数や <xref:Microsoft.VisualBasic.Conversion.Fix%2A> 関数とは異なり、数値の小数部を丸めるのではなく、切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-188">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="78fb1-189">さらに、`Fix` と `Int` は常に、渡された同じデータ型の値を返します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-189">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="78fb1-190">**日付/時刻の変換。**</span><span class="sxs-lookup"><span data-stu-id="78fb1-190">**Date/Time Conversions.**</span></span> <span data-ttu-id="78fb1-191"><xref:Microsoft.VisualBasic.Information.IsDate%2A> 関数を使用して、値を日付と時刻に変換できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-191">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="78fb1-192">`CDate` は、日付リテラルと時刻リテラルを認識しますが、数値は認識しません。</span><span class="sxs-lookup"><span data-stu-id="78fb1-192">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="78fb1-193">Visual Basic 6.0 の `Date` 値を Visual Basic 2005 以降のバージョンの `Date` 値に変換するには、<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-193">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="78fb1-194">**ニュートラル日付/時刻値。**</span><span class="sxs-lookup"><span data-stu-id="78fb1-194">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="78fb1-195">[Date データ型](../data-types/date-data-type.md)には、常に日付と時刻の両方の情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-195">The [Date Data Type](../data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="78fb1-196">型変換の目的で、Visual Basic では、1/1/0001 (1 年の 1 月 1 日) を日付の *ニュートラル値*、00:00:00 (午前 0 時) を時刻のニュートラル値と見なします。</span><span class="sxs-lookup"><span data-stu-id="78fb1-196">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="78fb1-197">`Date` 値を文字列に変換する場合、`CStr` では、結果の文字列にニュートラル値が含まれません。</span><span class="sxs-lookup"><span data-stu-id="78fb1-197">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="78fb1-198">たとえば、`#January 1, 0001 9:30:00#` を文字列に変換した場合、結果は "9:30:00 AM" になります。日付情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="78fb1-198">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="78fb1-199">ただし、日付情報は元の `Date` 値には引き続き存在しているため、<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 関数などの関数を使用して回復できます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-199">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="78fb1-200">**カルチャの感度。**</span><span class="sxs-lookup"><span data-stu-id="78fb1-200">**Culture Sensitivity.**</span></span> <span data-ttu-id="78fb1-201">文字列に関連する型変換関数では、アプリケーションの現在のカルチャ設定に基づいて変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-201">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="78fb1-202">たとえば、`CDate` では、システムのロケール設定に従って日付形式が認識されます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-202">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="78fb1-203">ロケールの正しい順序で日、月、年を指定する必要があります。そうしないと、日付が正しく解釈されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-203">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="78fb1-204">"Wednesday" など、曜日の文字列が含まれている場合、長い日付形式は認識されません。</span><span class="sxs-lookup"><span data-stu-id="78fb1-204">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="78fb1-205">ロケールによって指定された形式以外の形式で、値の文字列表現の変換を行う必要がある場合は、Visual Basic 型変換関数を使用できません。</span><span class="sxs-lookup"><span data-stu-id="78fb1-205">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="78fb1-206">これを行うには、その値の型の `ToString(IFormatProvider)` および `Parse(String, IFormatProvider)` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-206">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="78fb1-207">たとえば、文字列を `Double` に変換する場合は <xref:System.Double.Parse%2A?displayProperty=nameWithType> を使用し、`Double` 型の値を文字列に変換する場合は <xref:System.Double.ToString%2A?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-207">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="78fb1-208">CType Function</span><span class="sxs-lookup"><span data-stu-id="78fb1-208">CType Function</span></span>

<span data-ttu-id="78fb1-209">[CType 関数](ctype-function.md)は、2 つ目の引数 `typename` を受け取り、`expression` を `typename` に強制的に変換します。ここで `typename` は、それに対して有効な変換が存在する任意のデータ型、構造体、クラス、またはインターフェイスなどです。</span><span class="sxs-lookup"><span data-stu-id="78fb1-209">The [CType Function](ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="78fb1-210">`CType` と他の型変換キーワードとの比較については、「[DirectCast 演算子](../operators/directcast-operator.md)」と「[TryCast 演算子](../operators/trycast-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-210">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../operators/directcast-operator.md) and [TryCast Operator](../operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="78fb1-211">CBool の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-211">CBool Example</span></span>

<span data-ttu-id="78fb1-212">次の例では、`CBool` 関数を使用して、式を `Boolean` 値に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-212">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="78fb1-213">式が 0 以外の値に評価される場合、`CBool` では `True` が返されます。それ以外の場合は `False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-213">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="78fb1-214">CByte の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-214">CByte Example</span></span>

<span data-ttu-id="78fb1-215">次の例では、`CByte` 関数を使用して、式を `Byte` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-215">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="78fb1-216">CChar の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-216">CChar Example</span></span>

<span data-ttu-id="78fb1-217">次の例では、`CChar` 関数を使用して、`String` 式の最初の文字を `Char` 型に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-217">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="78fb1-218">`CChar` の入力引数は、`Char` または `String` データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="78fb1-218">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="78fb1-219">`CChar` を使用して数値を文字に変換することはできません。これは `CChar` では数値データ型を受け入れないためです。</span><span class="sxs-lookup"><span data-stu-id="78fb1-219">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="78fb1-220">次の例では、コード ポイント (文字コード) を表す数値を取得し、それを対応する文字に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-220">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="78fb1-221"><xref:Microsoft.VisualBasic.Interaction.InputBox%2A> 関数を使用して、数字の文字列を取得し、`CInt` を使用して、文字列を `Integer` 型に変換し、`ChrW` を使用して、数値を `Char` 型に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-221">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="78fb1-222">CDate の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-222">CDate Example</span></span>

<span data-ttu-id="78fb1-223">次の例では、`CDate` 関数を使用して、文字列を `Date` 値に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-223">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="78fb1-224">一般に、日付と時刻を文字列としてハードコーディングする (この例に示すように) ことは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="78fb1-224">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="78fb1-225">代わりに、#Feb 12、1969#、#4:45:23 PM# などの日付リテラルと時刻リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="78fb1-225">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="78fb1-226">CDbl の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-226">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="78fb1-227">CDec の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-227">CDec Example</span></span>

<span data-ttu-id="78fb1-228">次の例では、`CDec` 関数を使用して、数値を `Decimal` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-228">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="78fb1-229">CInt の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-229">CInt Example</span></span>

<span data-ttu-id="78fb1-230">次の例では、`CInt` 関数を使用して、値を `Integer` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-230">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="78fb1-231">CLng の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-231">CLng Example</span></span>

<span data-ttu-id="78fb1-232">次の例では、`CLng` 関数を使用して、値を `Long` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-232">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="78fb1-233">CObj の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-233">CObj Example</span></span>

<span data-ttu-id="78fb1-234">次の例では、`CObj` 関数を使用して、数値を `Object` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-234">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="78fb1-235">`Object` 変数自体には、それに代入される `Double` 値を指す 4 バイトのポインターのみが格納されます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-235">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="78fb1-236">CSByte の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-236">CSByte Example</span></span>

<span data-ttu-id="78fb1-237">次の例では、`CSByte` 関数を使用して、数値を `SByte` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-237">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="78fb1-238">CShort の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-238">CShort Example</span></span>

<span data-ttu-id="78fb1-239">次の例では、`CShort` 関数を使用して、数値を `Short` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-239">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="78fb1-240">CSng の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-240">CSng Example</span></span>

<span data-ttu-id="78fb1-241">次の例では、`CSng` 関数を使用して、値を `Single` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-241">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="78fb1-242">CStr の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-242">CStr Example</span></span>

<span data-ttu-id="78fb1-243">次の例では、`CStr` 関数を使用して、数値を `String` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-243">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="78fb1-244">次の例では、`CStr` 関数を使用して、 `Date` 値を `String` 値に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-244">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="78fb1-245">`CStr` では常に、現在のロケールの標準の短い形式 ("6/15/2003 4:35:47 PM" など) で `Date` 値がレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="78fb1-245">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="78fb1-246">ただし `CStr` では、日付の 1/1/0001 と時刻の 00:00:00 の *ニュートラル値* が含まれません。</span><span class="sxs-lookup"><span data-stu-id="78fb1-246">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="78fb1-247">`CStr` によって返される値の詳細については、「[CStr 関数の戻り値](return-values-for-the-cstr-function.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fb1-247">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="78fb1-248">CUInt の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-248">CUInt Example</span></span>

<span data-ttu-id="78fb1-249">次の例では、`CUInt` 関数を使用して、数値を `UInteger` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-249">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="78fb1-250">CULng の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-250">CULng Example</span></span>

<span data-ttu-id="78fb1-251">次の例では、`CULng` 関数を使用して、数値を `ULong` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-251">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="78fb1-252">CUShort の例</span><span class="sxs-lookup"><span data-stu-id="78fb1-252">CUShort Example</span></span>

<span data-ttu-id="78fb1-253">次の例では、`CUShort` 関数を使用して、数値を `UShort` に変換しています。</span><span class="sxs-lookup"><span data-stu-id="78fb1-253">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="78fb1-254">関連項目</span><span class="sxs-lookup"><span data-stu-id="78fb1-254">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="78fb1-255">変換関数</span><span class="sxs-lookup"><span data-stu-id="78fb1-255">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="78fb1-256">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="78fb1-256">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
