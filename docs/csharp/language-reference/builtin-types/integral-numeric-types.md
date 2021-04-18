---
title: 整数数値型 - C# リファレンス
description: 各整数数値型の範囲、ストレージ サイズ、および使用方法について説明します。
ms.date: 04/10/2021
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
ms.openlocfilehash: 21e6595e477fd48d0e5f39f5b4f1f7c5893a8840
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369583"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="f6d12-103">整数数値型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f6d12-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="f6d12-104">"*整数数値型*" は、整数値を表します。</span><span class="sxs-lookup"><span data-stu-id="f6d12-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="f6d12-105">すべての整数数値型は、[値の型](value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="f6d12-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="f6d12-106">また、[単純型](value-types.md#built-in-value-types)でもあり、[リテラル](#integer-literals)を使用して初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="f6d12-107">すべての整数数値型では、[算術](../operators/arithmetic-operators.md)、[ビット論理](../operators/bitwise-and-shift-operators.md)、[比較](../operators/comparison-operators.md)、[等値](../operators/equality-operators.md)演算子がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f6d12-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="f6d12-108">整数型の特性</span><span class="sxs-lookup"><span data-stu-id="f6d12-108">Characteristics of the integral types</span></span>

<span data-ttu-id="f6d12-109">C# では、次の定義済みの整数型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f6d12-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="f6d12-110">C# 型/キーワード</span><span class="sxs-lookup"><span data-stu-id="f6d12-110">C# type/keyword</span></span>|<span data-ttu-id="f6d12-111">範囲</span><span class="sxs-lookup"><span data-stu-id="f6d12-111">Range</span></span>|<span data-ttu-id="f6d12-112">サイズ</span><span class="sxs-lookup"><span data-stu-id="f6d12-112">Size</span></span>|<span data-ttu-id="f6d12-113">.NET 型</span><span class="sxs-lookup"><span data-stu-id="f6d12-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="f6d12-114">-128 ～ 127</span><span class="sxs-lookup"><span data-stu-id="f6d12-114">-128 to 127</span></span>|<span data-ttu-id="f6d12-115">符号付き 8 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="f6d12-116">0 ～ 255</span><span class="sxs-lookup"><span data-stu-id="f6d12-116">0 to 255</span></span>|<span data-ttu-id="f6d12-117">符号なし 8 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="f6d12-118">-32,768 ～ 32,767</span><span class="sxs-lookup"><span data-stu-id="f6d12-118">-32,768 to 32,767</span></span>|<span data-ttu-id="f6d12-119">符号付き 16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="f6d12-120">0 ～ 65,535</span><span class="sxs-lookup"><span data-stu-id="f6d12-120">0 to 65,535</span></span>|<span data-ttu-id="f6d12-121">符号なし 16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="f6d12-122">-2,147,483,648 ～ 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="f6d12-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="f6d12-123">符号付き 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="f6d12-124">0 ～ 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="f6d12-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="f6d12-125">符号なし 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="f6d12-126">-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="f6d12-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="f6d12-127">符号付き 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="f6d12-128">0 ～ 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="f6d12-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="f6d12-129">符号なし 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|`nint`|<span data-ttu-id="f6d12-130">プラットフォームによって異なる</span><span class="sxs-lookup"><span data-stu-id="f6d12-130">Depends on platform</span></span>|<span data-ttu-id="f6d12-131">符号付き 32 ビットまたは 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-131">Signed 32-bit or 64-bit integer</span></span>|<xref:System.IntPtr?displayProperty=nameWithType>|
|`nuint`|<span data-ttu-id="f6d12-132">プラットフォームによって異なる</span><span class="sxs-lookup"><span data-stu-id="f6d12-132">Depends on platform</span></span>|<span data-ttu-id="f6d12-133">符号なし 32 ビットまたは 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f6d12-133">Unsigned 32-bit or 64-bit integer</span></span>|<xref:System.UIntPtr?displayProperty=nameWithType>|

<span data-ttu-id="f6d12-134">最後の 2 つを除くすべてのテーブル行で、左端の列の各 C# 型キーワードは、対応する .NET 型の別名です。</span><span class="sxs-lookup"><span data-stu-id="f6d12-134">In all of the table rows except the last two, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="f6d12-135">キーワードと .NET 型の名前は交換可能です。</span><span class="sxs-lookup"><span data-stu-id="f6d12-135">The keyword and .NET type name are interchangeable.</span></span> <span data-ttu-id="f6d12-136">たとえば、次の宣言では、同じ型の変数が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="f6d12-136">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="f6d12-137">テーブルの最後の 2 行の `nint` 型と `nuint` 型は、ネイティブサイズの整数です。</span><span class="sxs-lookup"><span data-stu-id="f6d12-137">The `nint` and `nuint` types in the last two rows of the table are native-sized integers.</span></span> <span data-ttu-id="f6d12-138">これらは、指定された .NET 型によって内部で表現されますが、いずれの場合もキーワードと .NET 型は交換できません。</span><span class="sxs-lookup"><span data-stu-id="f6d12-138">They are represented internally by the indicated .NET types, but in each case the keyword and the .NET type are not interchangeable.</span></span> <span data-ttu-id="f6d12-139">コンパイラによって、`nint` と `nuint` に対して、整数型としての演算と変換が提供されます。ポインター型 `System.IntPtr` と `System.UIntPtr` に対しては提供されません。</span><span class="sxs-lookup"><span data-stu-id="f6d12-139">The compiler provides operations and conversions for `nint` and `nuint` as integer types that it doesn't provide for the pointer types `System.IntPtr` and `System.UIntPtr`.</span></span> <span data-ttu-id="f6d12-140">詳細については、[`nint` 型と `nuint` 型](nint-nuint.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6d12-140">For more information, see [`nint` and `nuint` types](nint-nuint.md).</span></span>

<span data-ttu-id="f6d12-141">各整数型の既定値はゼロ (`0`) です。</span><span class="sxs-lookup"><span data-stu-id="f6d12-141">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="f6d12-142">ネイティブサイズの型を除く各整数型には、その型の最小値と最大値を指定する `MinValue` および `MaxValue` 定数があります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-142">Each of the integral types except the native-sized types has `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="f6d12-143"><xref:System.Numerics.BigInteger?displayProperty=nameWithType> 構造体を使用して、上限や下限のない符号付き整数を表します。</span><span class="sxs-lookup"><span data-stu-id="f6d12-143">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="f6d12-144">整数リテラル</span><span class="sxs-lookup"><span data-stu-id="f6d12-144">Integer literals</span></span>

<span data-ttu-id="f6d12-145">次の整数リテラルがあります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-145">Integer literals can be</span></span>

- <span data-ttu-id="f6d12-146">"*10 進*": プレフィックスなし</span><span class="sxs-lookup"><span data-stu-id="f6d12-146">*decimal*: without any prefix</span></span>
- <span data-ttu-id="f6d12-147">"*16 進*": `0x` または `0X` プレフィックスを使用します</span><span class="sxs-lookup"><span data-stu-id="f6d12-147">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="f6d12-148">"*バイナリ*": `0b` または `0B` プレフィックスを使用します (C# 7.0 以降で使用できます)</span><span class="sxs-lookup"><span data-stu-id="f6d12-148">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="f6d12-149">次のコードは、それぞれの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6d12-149">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="f6d12-150">前述の例は、C# 7.0 以降でサポートされている "*桁区切り記号*" としての `_` の使用法も示しています。</span><span class="sxs-lookup"><span data-stu-id="f6d12-150">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="f6d12-151">数字区切り記号は、あらゆる種類の数値リテラルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-151">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="f6d12-152">整数リテラルの型は、そのサフィックスによって次のように決まります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-152">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="f6d12-153">サフィックスがないリテラルの型は、`int`、`uint`、`long`、`ulong` の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-153">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f6d12-154">リテラルは正の値として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-154">Literals are interpreted as positive values.</span></span> <span data-ttu-id="f6d12-155">たとえば、リテラル `0xFF_FF_FF_FF` は、`uint` 型の数値 `4294967295` を表しますが、そのビット表現は `int` 型の数値 `-1` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-155">For example, the literal `0xFF_FF_FF_FF` represents the number `4294967295` of the `uint` type, though it has the same bit representation as the number `-1` of the `int` type.</span></span> <span data-ttu-id="f6d12-156">特定の型の値が必要な場合は、リテラルをその型にキャストしてください。</span><span class="sxs-lookup"><span data-stu-id="f6d12-156">If you need a value of a certain type, cast a literal to that type.</span></span> <span data-ttu-id="f6d12-157">リテラル値をターゲット型で表すことができない場合は、`unchecked` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6d12-157">Use the `unchecked` operator, if a literal value cannot be represented in the target type.</span></span> <span data-ttu-id="f6d12-158">たとえば、`unchecked((int)0xFF_FF_FF_FF)` を使用すると、`-1` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-158">For example, `unchecked((int)0xFF_FF_FF_FF)` produces `-1`.</span></span>

- <span data-ttu-id="f6d12-159">リテラルのサフィックスが `U` または `u` の場合、その型は、`uint`、`ulong` の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-159">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="f6d12-160">リテラルのサフィックスが `L` または `l` の場合、その型は、`long`、`ulong` の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-160">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f6d12-161">小文字の `l` はサフィックスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-161">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="f6d12-162">ただし、文字の `l` は数字の `1` と混同しやすいため、コンパイラから警告が出されます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-162">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="f6d12-163">わかりやすくするために `L` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="f6d12-163">Use `L` for clarity.</span></span>

- <span data-ttu-id="f6d12-164">リテラルのサフィックスが `UL`、`Ul`、`uL`、`ul`、`LU`、`Lu`、`lU`、または `lu` の場合、その型は `ulong` です。</span><span class="sxs-lookup"><span data-stu-id="f6d12-164">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="f6d12-165">整数リテラルで表される値が <xref:System.UInt64.MaxValue?displayProperty=nameWithType> を超えると、コンパイル エラー [CS1021](../../misc/cs1021.md) が発生します。</span><span class="sxs-lookup"><span data-stu-id="f6d12-165">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="f6d12-166">整数リテラルの決定された型が `int` で、リテラルで表される値が変換先の型の範囲内にある場合、値を暗黙的に `sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong`、`nint`、または `nuint` に変換できます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-166">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `nint` or `nuint`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="f6d12-167">前の例で示したように、リテラルの値が変換先の型の範囲内にない場合、コンパイラ エラー [CS0031](../../misc/cs0031.md) が発生します。</span><span class="sxs-lookup"><span data-stu-id="f6d12-167">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="f6d12-168">また、キャストを使用して、整数リテラルによって表される値を、指定された型のリテラル以外の型に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-168">You can also use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="f6d12-169">変換</span><span class="sxs-lookup"><span data-stu-id="f6d12-169">Conversions</span></span>

<span data-ttu-id="f6d12-170">任意の整数数値型を他の整数数値型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-170">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="f6d12-171">変換先の型に変換元の型のすべての値を格納できる場合、変換は暗黙的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="f6d12-171">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="f6d12-172">それ以外の場合は、[キャスト式](../operators/type-testing-and-cast.md#cast-expression)を使用して明示的な変換を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6d12-172">Otherwise, you need to use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span> <span data-ttu-id="f6d12-173">詳細については、「[組み込みの数値変換](numeric-conversions.md)」に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6d12-173">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f6d12-174">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f6d12-174">C# language specification</span></span>

<span data-ttu-id="f6d12-175">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6d12-175">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f6d12-176">整数型</span><span class="sxs-lookup"><span data-stu-id="f6d12-176">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="f6d12-177">整数リテラル</span><span class="sxs-lookup"><span data-stu-id="f6d12-177">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="f6d12-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6d12-178">See also</span></span>

- [<span data-ttu-id="f6d12-179">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f6d12-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f6d12-180">値型</span><span class="sxs-lookup"><span data-stu-id="f6d12-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="f6d12-181">浮動小数点型</span><span class="sxs-lookup"><span data-stu-id="f6d12-181">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="f6d12-182">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="f6d12-182">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="f6d12-183">.NET における数値</span><span class="sxs-lookup"><span data-stu-id="f6d12-183">Numerics in .NET</span></span>](../../../standard/numerics.md)
