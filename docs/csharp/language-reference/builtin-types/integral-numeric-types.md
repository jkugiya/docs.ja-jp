---
title: 整数数値型 - C# リファレンス
description: 各整数数値型の範囲、ストレージ サイズ、および使用方法について説明します。
ms.date: 03/17/2021
f1_keywords:
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- short_CSharpKeyword
- ushort_CSharpKeyword
- int_CSharpKeyword
- uint_CSharpKeyword
- long_CSharpKeyword
- ulong_CSharpKeyword
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 02b1451dc3aa22dfe27181b0e9160d198349107c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760172"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="b738b-103">整数数値型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b738b-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="b738b-104">"*整数数値型*" は、整数値を表します。</span><span class="sxs-lookup"><span data-stu-id="b738b-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="b738b-105">すべての整数数値型は、[値の型](value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="b738b-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="b738b-106">また、[単純型](value-types.md#built-in-value-types)でもあり、[リテラル](#integer-literals)を使用して初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="b738b-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="b738b-107">すべての整数数値型では、[算術](../operators/arithmetic-operators.md)、[ビット論理](../operators/bitwise-and-shift-operators.md)、[比較](../operators/comparison-operators.md)、[等値](../operators/equality-operators.md)演算子がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b738b-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="b738b-108">整数型の特性</span><span class="sxs-lookup"><span data-stu-id="b738b-108">Characteristics of the integral types</span></span>

<span data-ttu-id="b738b-109">C# では、次の定義済みの整数型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b738b-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="b738b-110">C# 型/キーワード</span><span class="sxs-lookup"><span data-stu-id="b738b-110">C# type/keyword</span></span>|<span data-ttu-id="b738b-111">範囲</span><span class="sxs-lookup"><span data-stu-id="b738b-111">Range</span></span>|<span data-ttu-id="b738b-112">サイズ</span><span class="sxs-lookup"><span data-stu-id="b738b-112">Size</span></span>|<span data-ttu-id="b738b-113">.NET 型</span><span class="sxs-lookup"><span data-stu-id="b738b-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="b738b-114">-128 ～ 127</span><span class="sxs-lookup"><span data-stu-id="b738b-114">-128 to 127</span></span>|<span data-ttu-id="b738b-115">符号付き 8 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="b738b-116">0 ～ 255</span><span class="sxs-lookup"><span data-stu-id="b738b-116">0 to 255</span></span>|<span data-ttu-id="b738b-117">符号なし 8 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="b738b-118">-32,768 ～ 32,767</span><span class="sxs-lookup"><span data-stu-id="b738b-118">-32,768 to 32,767</span></span>|<span data-ttu-id="b738b-119">符号付き 16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="b738b-120">0 ～ 65,535</span><span class="sxs-lookup"><span data-stu-id="b738b-120">0 to 65,535</span></span>|<span data-ttu-id="b738b-121">符号なし 16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="b738b-122">-2,147,483,648 ～ 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="b738b-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="b738b-123">符号付き 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="b738b-124">0 ～ 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="b738b-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="b738b-125">符号なし 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="b738b-126">-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="b738b-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="b738b-127">符号付き 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="b738b-128">0 ～ 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="b738b-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="b738b-129">符号なし 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|`nint`|<span data-ttu-id="b738b-130">プラットフォームによって異なる</span><span class="sxs-lookup"><span data-stu-id="b738b-130">Depends on platform</span></span>|<span data-ttu-id="b738b-131">符号付き 32 ビットまたは 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-131">Signed 32-bit or 64-bit integer</span></span>|<xref:System.IntPtr?displayProperty=nameWithType>|
|`nuint`|<span data-ttu-id="b738b-132">プラットフォームによって異なる</span><span class="sxs-lookup"><span data-stu-id="b738b-132">Depends on platform</span></span>|<span data-ttu-id="b738b-133">符号なし 32 ビットまたは 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="b738b-133">Unsigned 32-bit or 64-bit integer</span></span>|<xref:System.UIntPtr?displayProperty=nameWithType>|

<span data-ttu-id="b738b-134">最後の 2 つを除くすべてのテーブル行で、左端の列の各 C# 型キーワードは、対応する .NET 型の別名です。</span><span class="sxs-lookup"><span data-stu-id="b738b-134">In all of the table rows except the last two, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="b738b-135">キーワードと .NET 型の名前は交換可能です。</span><span class="sxs-lookup"><span data-stu-id="b738b-135">The keyword and .NET type name are interchangeable.</span></span> <span data-ttu-id="b738b-136">たとえば、次の宣言では、同じ型の変数が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="b738b-136">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="b738b-137">テーブルの最後の 2 行の `nint` 型と `nuint` 型は、ネイティブサイズの整数です。</span><span class="sxs-lookup"><span data-stu-id="b738b-137">The `nint` and `nuint` types in the last two rows of the table are native-sized integers.</span></span> <span data-ttu-id="b738b-138">これらは、指定された .NET 型によって内部で表現されますが、いずれの場合もキーワードと .NET 型は交換できません。</span><span class="sxs-lookup"><span data-stu-id="b738b-138">They are represented internally by the indicated .NET types, but in each case the keyword and the .NET type are not interchangeable.</span></span> <span data-ttu-id="b738b-139">コンパイラによって、`nint` と `nuint` に対して、整数型としての演算と変換が提供されます。ポインター型 `System.IntPtr` と `System.UIntPtr` に対しては提供されません。</span><span class="sxs-lookup"><span data-stu-id="b738b-139">The compiler provides operations and conversions for `nint` and `nuint` as integer types that it doesn't provide for the pointer types `System.IntPtr` and `System.UIntPtr`.</span></span> <span data-ttu-id="b738b-140">詳細については、[`nint` 型と `nuint` 型](nint-nuint.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b738b-140">For more information, see [`nint` and `nuint` types](nint-nuint.md).</span></span>

<span data-ttu-id="b738b-141">ネイティブサイズの整数型の詳細については、[`nint` と `nuint`](nint-nuint.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b738b-141">For information about the native-sized integer types, see [`nint` and `nuint`](nint-nuint.md).</span></span>

<span data-ttu-id="b738b-142">各整数型の既定値はゼロ (`0`) です。</span><span class="sxs-lookup"><span data-stu-id="b738b-142">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="b738b-143">ネイティブサイズの型を除く各整数型には、その型の最小値と最大値を指定する `MinValue` および `MaxValue` 定数があります。</span><span class="sxs-lookup"><span data-stu-id="b738b-143">Each of the integral types except the native-sized types has `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="b738b-144"><xref:System.Numerics.BigInteger?displayProperty=nameWithType> 構造体を使用して、上限や下限のない符号付き整数を表します。</span><span class="sxs-lookup"><span data-stu-id="b738b-144">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="b738b-145">整数リテラル</span><span class="sxs-lookup"><span data-stu-id="b738b-145">Integer literals</span></span>

<span data-ttu-id="b738b-146">次の整数リテラルがあります。</span><span class="sxs-lookup"><span data-stu-id="b738b-146">Integer literals can be</span></span>

- <span data-ttu-id="b738b-147">"*10 進*": プレフィックスなし</span><span class="sxs-lookup"><span data-stu-id="b738b-147">*decimal*: without any prefix</span></span>
- <span data-ttu-id="b738b-148">"*16 進*": `0x` または `0X` プレフィックスを使用します</span><span class="sxs-lookup"><span data-stu-id="b738b-148">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="b738b-149">"*バイナリ*": `0b` または `0B` プレフィックスを使用します (C# 7.0 以降で使用できます)</span><span class="sxs-lookup"><span data-stu-id="b738b-149">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="b738b-150">次のコードは、それぞれの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="b738b-150">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="b738b-151">前述の例は、C# 7.0 以降でサポートされている "*桁区切り記号*" としての `_` の使用法も示しています。</span><span class="sxs-lookup"><span data-stu-id="b738b-151">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="b738b-152">数字区切り記号は、あらゆる種類の数値リテラルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b738b-152">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="b738b-153">整数リテラルの型は、そのサフィックスによって次のように決まります。</span><span class="sxs-lookup"><span data-stu-id="b738b-153">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="b738b-154">サフィックスがないリテラルの型は、`int`、`uint`、`long`、`ulong` の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="b738b-154">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="b738b-155">リテラルのサフィックスが `U` または `u` の場合、その型は、`uint`、`ulong` の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="b738b-155">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="b738b-156">リテラルのサフィックスが `L` または `l` の場合、その型は、`long`、`ulong` の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="b738b-156">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b738b-157">小文字の `l` はサフィックスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="b738b-157">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="b738b-158">ただし、文字の `l` は数字の `1` と混同しやすいため、コンパイラから警告が出されます。</span><span class="sxs-lookup"><span data-stu-id="b738b-158">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="b738b-159">わかりやすくするために `L` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="b738b-159">Use `L` for clarity.</span></span>

- <span data-ttu-id="b738b-160">リテラルのサフィックスが `UL`、`Ul`、`uL`、`ul`、`LU`、`Lu`、`lU`、または `lu` の場合、その型は `ulong` です。</span><span class="sxs-lookup"><span data-stu-id="b738b-160">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="b738b-161">整数リテラルで表される値が <xref:System.UInt64.MaxValue?displayProperty=nameWithType> を超えると、コンパイル エラー [CS1021](../../misc/cs1021.md) が発生します。</span><span class="sxs-lookup"><span data-stu-id="b738b-161">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="b738b-162">整数リテラルの決定された型が `int` で、リテラルで表される値が変換先の型の範囲内にある場合、値を暗黙的に `sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong`、`nint`、または `nuint` に変換できます。</span><span class="sxs-lookup"><span data-stu-id="b738b-162">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `nint` or `nuint`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="b738b-163">前の例で示したように、リテラルの値が変換先の型の範囲内にない場合、コンパイラ エラー [CS0031](../../misc/cs0031.md) が発生します。</span><span class="sxs-lookup"><span data-stu-id="b738b-163">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="b738b-164">また、キャストを使用して、整数リテラルによって表される値を、指定された型のリテラル以外の型に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="b738b-164">You can also use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="b738b-165">変換</span><span class="sxs-lookup"><span data-stu-id="b738b-165">Conversions</span></span>

<span data-ttu-id="b738b-166">任意の整数数値型を他の整数数値型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="b738b-166">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="b738b-167">変換先の型に変換元の型のすべての値を格納できる場合、変換は暗黙的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="b738b-167">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="b738b-168">それ以外の場合は、[キャスト式](../operators/type-testing-and-cast.md#cast-expression)を使用して明示的な変換を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b738b-168">Otherwise, you need to use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span> <span data-ttu-id="b738b-169">詳細については、「[組み込みの数値変換](numeric-conversions.md)」に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b738b-169">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b738b-170">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="b738b-170">C# language specification</span></span>

<span data-ttu-id="b738b-171">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b738b-171">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b738b-172">整数型</span><span class="sxs-lookup"><span data-stu-id="b738b-172">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="b738b-173">整数リテラル</span><span class="sxs-lookup"><span data-stu-id="b738b-173">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="b738b-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="b738b-174">See also</span></span>

- [<span data-ttu-id="b738b-175">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b738b-175">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b738b-176">値型</span><span class="sxs-lookup"><span data-stu-id="b738b-176">Value types</span></span>](value-types.md)
- [<span data-ttu-id="b738b-177">浮動小数点型</span><span class="sxs-lookup"><span data-stu-id="b738b-177">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="b738b-178">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="b738b-178">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="b738b-179">.NET における数値</span><span class="sxs-lookup"><span data-stu-id="b738b-179">Numerics in .NET</span></span>](../../../standard/numerics.md)
