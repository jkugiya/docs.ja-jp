---
title: 浮動小数点数値型 - C# リファレンス
description: 組み込みの C# 浮動小数点型 (float、double、decimal) について説明します
ms.date: 02/04/2021
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a086e8de60bbb63408c3f2cd557feb36c4baa0f8
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585755"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="0a803-103">浮動小数点数値型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0a803-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="0a803-104">"*浮動小数点数値型*" は実数を表します。</span><span class="sxs-lookup"><span data-stu-id="0a803-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="0a803-105">浮動小数点数値型は、[値の型](value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="0a803-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="0a803-106">また、[単純型](value-types.md#built-in-value-types)でもあり、[リテラル](#real-literals)を使用して初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="0a803-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="0a803-107">すべての浮動小数点数値型は、[算術](../operators/arithmetic-operators.md)、[比較](../operators/comparison-operators.md)、および[等値](../operators/equality-operators.md)演算子をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0a803-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="0a803-108">浮動小数点型の特性</span><span class="sxs-lookup"><span data-stu-id="0a803-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="0a803-109">C# では、次の定義済みの浮動小数点型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0a803-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="0a803-110">C# 型/キーワード</span><span class="sxs-lookup"><span data-stu-id="0a803-110">C# type/keyword</span></span>|<span data-ttu-id="0a803-111">おおよその範囲</span><span class="sxs-lookup"><span data-stu-id="0a803-111">Approximate range</span></span>|<span data-ttu-id="0a803-112">有効桁数</span><span class="sxs-lookup"><span data-stu-id="0a803-112">Precision</span></span>|<span data-ttu-id="0a803-113">サイズ</span><span class="sxs-lookup"><span data-stu-id="0a803-113">Size</span></span>|<span data-ttu-id="0a803-114">.NET 型</span><span class="sxs-lookup"><span data-stu-id="0a803-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="0a803-115">±1.5 x 10<sup>−45</sup> から ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="0a803-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="0a803-116">~6 ～9 桁</span><span class="sxs-lookup"><span data-stu-id="0a803-116">~6-9 digits</span></span>|<span data-ttu-id="0a803-117">4 バイト</span><span class="sxs-lookup"><span data-stu-id="0a803-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="0a803-118">±5.0 × 10<sup>−324</sup> - ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="0a803-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="0a803-119">~15-17 桁</span><span class="sxs-lookup"><span data-stu-id="0a803-119">~15-17 digits</span></span>|<span data-ttu-id="0a803-120">8 バイト</span><span class="sxs-lookup"><span data-stu-id="0a803-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="0a803-121">±1.0 x 10<sup>-28</sup> から ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="0a803-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="0a803-122">28 から 29 桁の数字</span><span class="sxs-lookup"><span data-stu-id="0a803-122">28-29 digits</span></span>|<span data-ttu-id="0a803-123">16 バイト</span><span class="sxs-lookup"><span data-stu-id="0a803-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="0a803-124">上の表の左端の列にある各 C# 型/キーワードは、対応する .NET 型の別名です。</span><span class="sxs-lookup"><span data-stu-id="0a803-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="0a803-125">これらは交換可能です。</span><span class="sxs-lookup"><span data-stu-id="0a803-125">They are interchangeable.</span></span> <span data-ttu-id="0a803-126">たとえば、次の宣言では、同じ型の変数が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="0a803-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="0a803-127">各浮動小数点型の既定値はゼロ `0` です。</span><span class="sxs-lookup"><span data-stu-id="0a803-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="0a803-128">各浮動小数点型には、その型の最小および最大有限値を指定する `MinValue` および `MaxValue` 定数があります。</span><span class="sxs-lookup"><span data-stu-id="0a803-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="0a803-129">`float` および `double` 型では、数字ではない値や無限値を表す定数も提供されています。</span><span class="sxs-lookup"><span data-stu-id="0a803-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="0a803-130">たとえば、`double` 型では、定数 <xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>、<xref:System.Double.PositiveInfinity?displayProperty=nameWithType> が提供されています。</span><span class="sxs-lookup"><span data-stu-id="0a803-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0a803-131">`decimal` 型は、必要な精度が小数点の右側の桁数によって決まる場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="0a803-131">The `decimal` type is appropriate when the required degree of precision is determined by the number of digits to the right of the decimal point.</span></span> <span data-ttu-id="0a803-132">このような数値は、財務アプリケーションで金額 ($1.00 など) や金利 (2.625% など) などによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a803-132">Such numbers are commonly used in financial applications, for currency amounts (for example, $1.00), interest rates (for example, 2.625%), and so forth.</span></span> <span data-ttu-id="0a803-133">1 つの 10 進数字だけで表される数値でさえも、`decimal` 型を使用するとより正確に処理されます。たとえば、0.1 は `decimal` インスタンスでは正確に表すことができますが、0.1 が正確に表される `double` または `float` のインスタンスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="0a803-133">Even numbers that are precise to only one decimal digit are handled more accurately by the `decimal` type: 0.1, for example, can be exactly represented by a `decimal` instance, while there's no `double` or `float` instance that exactly represents 0.1.</span></span> <span data-ttu-id="0a803-134">このような数値型の違いにより、10 進データに `double` または `float` を使用すると、算術計算で予期しない丸めエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a803-134">Because of this difference in numeric types, unexpected rounding errors can occur in arithmetic calculations when you use `double` or `float` for decimal data.</span></span> <span data-ttu-id="0a803-135">精度を保証するよりパフォーマンスを最適化する方が重要な場合は、`decimal` ではなく `double` を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0a803-135">You can use `double` instead of `decimal` when optimizing performance is more important than ensuring accuracy.</span></span> <span data-ttu-id="0a803-136">ただし、大量の計算処理が必要なアプリケーションでもない限り、パフォーマンスの違いに気付くことはありません。</span><span class="sxs-lookup"><span data-stu-id="0a803-136">However, any difference in performance would go unnoticed by all but the most calculation-intensive applications.</span></span> <span data-ttu-id="0a803-137">`decimal` を避ける理由としてもう 1 つ考えられるのは、必要な記憶域を最小限に抑えることです。</span><span class="sxs-lookup"><span data-stu-id="0a803-137">Another possible reason to avoid `decimal` is to minimize storage requirements.</span></span> <span data-ttu-id="0a803-138">たとえば、データ セットが非常に大きい場合は 4 バイトと 16 バイトの差が積み重なって意味を持つようになるため、[ML.NET](../../../machine-learning/how-does-mldotnet-work.md) では `float` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="0a803-138">For example, [ML.NET](../../../machine-learning/how-does-mldotnet-work.md) uses `float` because the difference between 4 bytes and 16 bytes adds up for very large data sets.</span></span> <span data-ttu-id="0a803-139">詳細については、「<xref:System.Decimal?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a803-139">For more information, see <xref:System.Decimal?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0a803-140">[整数](integral-numeric-types.md)型と `float` および `double` 型を 1 つの式の中で混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="0a803-140">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="0a803-141">この場合、整数型は、浮動小数点型の 1 つに暗黙的に変換されます。また、必要に応じて、`float` 型は `double` に暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="0a803-141">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="0a803-142">この式は、次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="0a803-142">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="0a803-143">式に `double` 型がある場合、リレーショナル比較と等価比較で、式は `double`、または [`bool`](bool.md) に評価されます。</span><span class="sxs-lookup"><span data-stu-id="0a803-143">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="0a803-144">式に `double` 型がない場合、リレーショナル比較と等価比較で、式は `float`、または `bool` に評価されます。</span><span class="sxs-lookup"><span data-stu-id="0a803-144">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="0a803-145">また、整数型と `decimal` 型を 1 つの式の中で混在させることもできます。</span><span class="sxs-lookup"><span data-stu-id="0a803-145">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="0a803-146">この場合、整数型は `decimal` 型に暗黙的に変換され、リレーショナル比較と等価比較で、式は `decimal`、または `bool` に評価されます。</span><span class="sxs-lookup"><span data-stu-id="0a803-146">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="0a803-147">`decimal` 型と `float` および `double` 型を 1 つの式の中で混在させることはできません。</span><span class="sxs-lookup"><span data-stu-id="0a803-147">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="0a803-148">この場合、算術演算、比較演算、または等値演算を実行するには、次の例に示すように、`decimal` 型との間でオペランドを明示的に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a803-148">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="0a803-149">浮動小数点値の書式指定には、[標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md)または[カスタムの数値書式指定文字列](../../../standard/base-types/custom-numeric-format-strings.md)のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a803-149">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="0a803-150">実数リテラル</span><span class="sxs-lookup"><span data-stu-id="0a803-150">Real literals</span></span>

<span data-ttu-id="0a803-151">実数リテラルの型は、サフィックスによって次のように決まります。</span><span class="sxs-lookup"><span data-stu-id="0a803-151">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="0a803-152">サフィックスがない、または `d` または `D` のリテラルは `double` 型です</span><span class="sxs-lookup"><span data-stu-id="0a803-152">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="0a803-153">サフィックスが `f` または `F` のリテラルは `float` 型です</span><span class="sxs-lookup"><span data-stu-id="0a803-153">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="0a803-154">サフィックスが `m` または `M` のリテラルは `decimal` 型です</span><span class="sxs-lookup"><span data-stu-id="0a803-154">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="0a803-155">次のコードは、それぞれの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="0a803-155">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="0a803-156">前述の例は、C# 7.0 以降でサポートされている "*桁区切り記号*" としての `_` の使用法も示しています。</span><span class="sxs-lookup"><span data-stu-id="0a803-156">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="0a803-157">数字区切り記号は、あらゆる種類の数値リテラルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a803-157">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="0a803-158">次の例に示すように、指数表記を使用して、実数リテラルの指数部を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="0a803-158">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="0a803-159">変換</span><span class="sxs-lookup"><span data-stu-id="0a803-159">Conversions</span></span>

<span data-ttu-id="0a803-160">浮動小数点数値型の間には、`float` から `double` に対する暗黙的な変換が 1 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="0a803-160">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="0a803-161">ただし、[明示的なキャスト](../operators/type-testing-and-cast.md#cast-expression)を使用して、任意の浮動小数点型を他の浮動小数点型に変換することはできます。</span><span class="sxs-lookup"><span data-stu-id="0a803-161">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="0a803-162">詳細については、「[組み込みの数値変換](numeric-conversions.md)」に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a803-162">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0a803-163">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0a803-163">C# language specification</span></span>

<span data-ttu-id="0a803-164">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a803-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0a803-165">浮動小数点型</span><span class="sxs-lookup"><span data-stu-id="0a803-165">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="0a803-166">decimal 型</span><span class="sxs-lookup"><span data-stu-id="0a803-166">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="0a803-167">実数リテラル</span><span class="sxs-lookup"><span data-stu-id="0a803-167">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="0a803-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a803-168">See also</span></span>

- [<span data-ttu-id="0a803-169">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="0a803-169">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0a803-170">値型</span><span class="sxs-lookup"><span data-stu-id="0a803-170">Value types</span></span>](value-types.md)
- [<span data-ttu-id="0a803-171">整数型</span><span class="sxs-lookup"><span data-stu-id="0a803-171">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="0a803-172">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="0a803-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="0a803-173">.NET における数値</span><span class="sxs-lookup"><span data-stu-id="0a803-173">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
