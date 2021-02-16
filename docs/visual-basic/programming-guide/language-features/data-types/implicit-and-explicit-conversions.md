---
description: '詳細情報: 暗黙の型変換と明示的な型変換 (Visual Basic)'
title: 暗黙の型変換と明示的な型変換
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 6a53c0998025cc8c19274c67d9dfe1c50a4f1373
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483951"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="d9e94-103">暗黙の型変換と明示的な型変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9e94-103">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="d9e94-104">"*暗黙の変換*" では、ソース コードに特別な構文は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d9e94-104">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="d9e94-105">次の例で、Visual Basic は、`k` の値を単精度浮動小数点値に暗黙的に変換してから、`q` に代入します。</span><span class="sxs-lookup"><span data-stu-id="d9e94-105">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="d9e94-106">"*明示的な変換*" では、型変換キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d9e94-106">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="d9e94-107">Visual Basic には、このようなキーワードがいくつか用意されており、これらを使用すると、かっこ内の式が目的のデータ型に強制的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-107">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="d9e94-108">これらのキーワードは関数と同様に機能しますが、コンパイラによってインラインでコードが生成されるため、関数呼び出しに比べて実行速度が若干速くなります。</span><span class="sxs-lookup"><span data-stu-id="d9e94-108">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="d9e94-109">次に示すのは前の例を拡張したものですが、`CInt` キーワードによって `q` の値が整数に変換された後で `k` に代入されます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-109">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="d9e94-110">変換キーワード</span><span class="sxs-lookup"><span data-stu-id="d9e94-110">Conversion Keywords</span></span>

<span data-ttu-id="d9e94-111">次の表に、使用可能な変換キーワードを示します。</span><span class="sxs-lookup"><span data-stu-id="d9e94-111">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="d9e94-112">型変換キーワード</span><span class="sxs-lookup"><span data-stu-id="d9e94-112">Type conversion keyword</span></span>|<span data-ttu-id="d9e94-113">式の変換先のデータ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-113">Converts an expression to data type</span></span>|<span data-ttu-id="d9e94-114">変換可能な式のデータ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-114">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="d9e94-115">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-115">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="d9e94-116">任意の数値型 (`Byte`、`SByte`、列挙型など)、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-116">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="d9e94-117">Byte データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-117">Byte Data Type</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="d9e94-118">任意の数値型 (`SByte` や列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-118">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="d9e94-119">Char データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-119">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="d9e94-120">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-120">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="d9e94-121">Date データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-121">Date Data Type</span></span>](../../../language-reference/data-types/date-data-type.md)|<span data-ttu-id="d9e94-122">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-122">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="d9e94-123">Double 型</span><span class="sxs-lookup"><span data-stu-id="d9e94-123">Double Data Type</span></span>](../../../language-reference/data-types/double-data-type.md)|<span data-ttu-id="d9e94-124">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-124">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="d9e94-125">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-125">Decimal Data Type</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="d9e94-126">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-126">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="d9e94-127">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-127">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="d9e94-128">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-128">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="d9e94-129">Long データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-129">Long Data Type</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="d9e94-130">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-130">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="d9e94-131">Object 型</span><span class="sxs-lookup"><span data-stu-id="d9e94-131">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)|<span data-ttu-id="d9e94-132">任意の型</span><span class="sxs-lookup"><span data-stu-id="d9e94-132">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="d9e94-133">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-133">SByte Data Type</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="d9e94-134">任意の数値型 (`Byte` や列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-134">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="d9e94-135">Short データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-135">Short Data Type</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="d9e94-136">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-136">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="d9e94-137">Single データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-137">Single Data Type</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="d9e94-138">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-138">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="d9e94-139">String データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-139">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)|<span data-ttu-id="d9e94-140">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`Char`、`Char` 配列、`Date`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-140">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="d9e94-141">コンマ (`,`) の後に指定される型</span><span class="sxs-lookup"><span data-stu-id="d9e94-141">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="d9e94-142">"*基本データ型*" (基本型の配列を含む) に変換するときは、対応する変換キーワードと同じ型が許可されます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-142">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="d9e94-143">"*複合データ型*" に変換するときは、実装するインターフェイスと継承するクラス</span><span class="sxs-lookup"><span data-stu-id="d9e94-143">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="d9e94-144">`CType` をオーバーロードしたクラスまたは構造体に変換するときは、そのクラスまたは構造体</span><span class="sxs-lookup"><span data-stu-id="d9e94-144">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="d9e94-145">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-145">UInteger Data Type</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="d9e94-146">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-146">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="d9e94-147">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-147">ULong Data Type</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="d9e94-148">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-148">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="d9e94-149">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="d9e94-149">UShort Data Type</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="d9e94-150">任意の数値型 (`Byte`、`SByte`、列挙型など)、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="d9e94-150">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="d9e94-151">CType 関数</span><span class="sxs-lookup"><span data-stu-id="d9e94-151">The CType Function</span></span>

<span data-ttu-id="d9e94-152">[CType 関数](../../../language-reference/functions/ctype-function.md)は、2 つの引数に対して動作します。</span><span class="sxs-lookup"><span data-stu-id="d9e94-152">The [CType Function](../../../language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="d9e94-153">1 つ目は変換される式、2 つ目は変換先のデータ型またはオブジェクト クラスです。</span><span class="sxs-lookup"><span data-stu-id="d9e94-153">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="d9e94-154">1 つ目の引数は型ではなく式である必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d9e94-154">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="d9e94-155">`CType` は "*インライン関数*" です。つまり、多くの場合、関数呼び出しを生成せず、コンパイルされたコードが変換を行います。</span><span class="sxs-lookup"><span data-stu-id="d9e94-155">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="d9e94-156">これによってパフォーマンスも向上します。</span><span class="sxs-lookup"><span data-stu-id="d9e94-156">This improves performance.</span></span>

<span data-ttu-id="d9e94-157">`CType` と他の型変換キーワードとの比較については、「[DirectCast 演算子](../../../language-reference/operators/directcast-operator.md)」と「[TryCast 演算子](../../../language-reference/operators/trycast-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9e94-157">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="d9e94-158">基本型</span><span class="sxs-lookup"><span data-stu-id="d9e94-158">Elementary Types</span></span>

<span data-ttu-id="d9e94-159">次の例は、`CType` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="d9e94-159">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="d9e94-160">複合型</span><span class="sxs-lookup"><span data-stu-id="d9e94-160">Composite Types</span></span>

<span data-ttu-id="d9e94-161">`CType` を使用すると、値を基本型だけでなく複合データ型にも変換できます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-161">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="d9e94-162">また、これを使用して、次の例のように、オブジェクト クラスをそのインターフェイスの型の 1 つに強制的に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-162">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="d9e94-163">配列型</span><span class="sxs-lookup"><span data-stu-id="d9e94-163">Array Types</span></span>

<span data-ttu-id="d9e94-164">`CType` では、次の例のように配列データ型を変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-164">`CType` can also convert array data types, as in the following example.</span></span>

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

<span data-ttu-id="d9e94-165">詳細および例については、「[配列の変換](array-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9e94-165">For more information and an example, see [Array Conversions](array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="d9e94-166">CType を定義する型</span><span class="sxs-lookup"><span data-stu-id="d9e94-166">Types Defining CType</span></span>

<span data-ttu-id="d9e94-167">定義したクラスまたは構造体で `CType` を定義できます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-167">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="d9e94-168">これにより、クラスまたは構造体の型との間で値を変換できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d9e94-168">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="d9e94-169">詳細および使用例については、「[方法:変換演算子を定義する](../procedures/how-to-define-a-conversion-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9e94-169">For more information and an example, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d9e94-170">変換キーワードと共に使用する値は、変換先のデータ型で有効でなければなりません。そうでない場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d9e94-170">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="d9e94-171">たとえば、`Long` を `Integer` に変換しようとする場合、`Long` の値は `Integer` データ型の有効範囲内である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9e94-171">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="d9e94-172">`CType` を指定した、あるクラス型から別のクラス型への変換が実行時に失敗するのは、変換元の型が変換先の型から派生されない場合です。</span><span class="sxs-lookup"><span data-stu-id="d9e94-172">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="d9e94-173">このような失敗では、<xref:System.InvalidCastException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-173">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="d9e94-174">ただし、型のいずれかが定義した構造体またはクラスであり、その構造体またはクラスに `CType` を定義している場合、それが `CType` の要件を満たすと変換が成功する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d9e94-174">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="d9e94-175">「[方法:変換演算子を定義する](../procedures/how-to-define-a-conversion-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9e94-175">See [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="d9e94-176">明示的な変換の実行は、指定のデータ型またはオブジェクト クラスへの式の "*キャスト*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d9e94-176">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9e94-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9e94-177">See also</span></span>

- [<span data-ttu-id="d9e94-178">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="d9e94-178">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="d9e94-179">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="d9e94-179">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="d9e94-180">方法: Visual Basic でオブジェクトを別の型に変換する</span><span class="sxs-lookup"><span data-stu-id="d9e94-180">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="d9e94-181">構造体</span><span class="sxs-lookup"><span data-stu-id="d9e94-181">Structures</span></span>](structures.md)
- [<span data-ttu-id="d9e94-182">データの種類</span><span class="sxs-lookup"><span data-stu-id="d9e94-182">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="d9e94-183">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="d9e94-183">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d9e94-184">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="d9e94-184">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
