---
title: パターン - C# リファレンス
description: C# のパターン マッチング式およびステートメントでサポートされるパターンについての説明 - C# リファレンス
ms.date: 04/05/2021
f1_keywords:
- and_CSharpKeyword
- or_CSharpKeyword
- not_CSharpKeyword
helpviewer_keywords:
- pattern matching [C#]
- and keyword [C#]
- or keyword [C#]
- not keyword [C#]
ms.openlocfilehash: cac2208d41bca2c6befecffbe4bb0b8ca43042bc
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498577"
---
# <a name="patterns-c-reference"></a><span data-ttu-id="c23e1-103">パターン (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c23e1-103">Patterns (C# reference)</span></span>

<span data-ttu-id="c23e1-104">C# では、C# 7.0 でパターン マッチングが導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-104">C# introduced pattern matching in C# 7.0.</span></span> <span data-ttu-id="c23e1-105">その後、C# の各メジャー バージョンで、パターン マッチング機能が拡張されています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-105">Since then, each major C# version extends pattern matching capabilities.</span></span> <span data-ttu-id="c23e1-106">次の C# 式およびステートメントでは、パターン マッチングがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-106">The following C# expressions and statements support pattern matching:</span></span>

- [<span data-ttu-id="c23e1-107">`is` 式</span><span class="sxs-lookup"><span data-stu-id="c23e1-107">`is` expression</span></span>](../keywords/is.md)
- <span data-ttu-id="c23e1-108">`switch` [ステートメント](../keywords/switch.md)</span><span class="sxs-lookup"><span data-stu-id="c23e1-108">`switch` [statement](../keywords/switch.md)</span></span>
- <span data-ttu-id="c23e1-109">`switch` [式](switch-expression.md) (C# 8.0 で導入)</span><span class="sxs-lookup"><span data-stu-id="c23e1-109">`switch` [expression](switch-expression.md) (introduced in C# 8.0)</span></span>

<span data-ttu-id="c23e1-110">それらの構造体では、入力式を次の任意のパターンと一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-110">In those constructs, you can match an input expression against any of the following patterns:</span></span>

- <span data-ttu-id="c23e1-111">[宣言パターン](#declaration-and-type-patterns): 式のランタイム型をチェックし、一致が成功した場合は、宣言された変数に式の結果を代入します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-111">[Declaration pattern](#declaration-and-type-patterns): to check the runtime type of an expression and, if a match succeeds, assign an expression result to a declared variable.</span></span> <span data-ttu-id="c23e1-112">C# 7.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-112">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="c23e1-113">[型パターン](#declaration-and-type-patterns): 式のランタイム型をチェックします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-113">[Type pattern](#declaration-and-type-patterns): to check the runtime type of an expression.</span></span> <span data-ttu-id="c23e1-114">C# 9.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-114">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="c23e1-115">[定数パターン](#constant-pattern): 式の結果が指定された定数と等しいかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-115">[Constant pattern](#constant-pattern): to test if an expression result equals a specified constant.</span></span> <span data-ttu-id="c23e1-116">C# 7.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-116">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="c23e1-117">[リレーショナル パターン](#relational-patterns): 式の結果と指定された定数を比較します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-117">[Relational patterns](#relational-patterns): to compare an expression result with a specified constant.</span></span> <span data-ttu-id="c23e1-118">C# 9.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-118">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="c23e1-119">[論理パターン](#logical-patterns): 式がパターンの論理的な組み合わせと一致するかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-119">[Logical patterns](#logical-patterns): to test if an expression matches a logical combination of patterns.</span></span> <span data-ttu-id="c23e1-120">C# 9.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-120">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="c23e1-121">[プロパティ パターン](#property-pattern): 式のプロパティまたはフィールドが入れ子になったパターンに一致するかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-121">[Property pattern](#property-pattern): to test if an expression's properties or fields match nested patterns.</span></span> <span data-ttu-id="c23e1-122">C# 8.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-122">Introduced in C# 8.0.</span></span>
- <span data-ttu-id="c23e1-123">[位置指定パターン](#positional-pattern): 式の結果を分解し、結果の値が入れ子になったパターンに一致するかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-123">[Positional pattern](#positional-pattern): to deconstruct an expression result and test if the resulting values match nested patterns.</span></span> <span data-ttu-id="c23e1-124">C# 8.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-124">Introduced in C# 8.0.</span></span>
- <span data-ttu-id="c23e1-125">[`var` パターン](#var-pattern): 任意の式に一致させ、その結果を宣言された変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-125">[`var` pattern](#var-pattern): to match any expression and assign its result to a declared variable.</span></span> <span data-ttu-id="c23e1-126">C# 7.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-126">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="c23e1-127">[破棄パターン](#discard-pattern): 任意の式に一致させます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-127">[Discard pattern](#discard-pattern): to match any expression.</span></span> <span data-ttu-id="c23e1-128">C# 8.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="c23e1-128">Introduced in C# 8.0.</span></span>

<span data-ttu-id="c23e1-129">[論理](#logical-patterns)、[プロパティ](#property-pattern)、および [位置指定](#positional-pattern)パターンは *再帰的* パターンです。</span><span class="sxs-lookup"><span data-stu-id="c23e1-129">[Logical](#logical-patterns), [property](#property-pattern), and [positional](#positional-pattern) patterns are *recursive* patterns.</span></span> <span data-ttu-id="c23e1-130">つまり、それらには *入れ子になった* パターンを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-130">That is, they can contain *nested* patterns.</span></span>

<span data-ttu-id="c23e1-131">これらのパターンを使用してデータ ドリブン アルゴリズムを構築する方法の例については、「[チュートリアル: パターン マッチングを使用して、型ドリブンおよびデータ ドリブンのアルゴリズムを構築する](../../tutorials/pattern-matching.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-131">For the example of how to use those patterns to build a data-driven algorithm, see [Tutorial: Use pattern matching to build type-driven and data-driven algorithms](../../tutorials/pattern-matching.md).</span></span>

## <a name="declaration-and-type-patterns"></a><span data-ttu-id="c23e1-132">宣言パターンと型パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-132">Declaration and type patterns</span></span>

<span data-ttu-id="c23e1-133">宣言パターンと型パターンを使用して、式のランタイム型が指定された型と互換性があるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-133">You use declaration and type patterns to check if the runtime type of an expression is compatible with a given type.</span></span> <span data-ttu-id="c23e1-134">宣言パターンでは、新しいローカル変数を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-134">With a declaration pattern, you can also declare a new local variable.</span></span> <span data-ttu-id="c23e1-135">宣言パターンが式に一致すると、次の例に示すように、その変数に変換された式の結果が代入されます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-135">When a declaration pattern matches an expression, that variable is assigned a converted expression result, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="BasicExample":::

<span data-ttu-id="c23e1-136">C# 7.0 以降、式の結果が null 以外で、次のいずれかの条件が満たされている場合に、`T` 型の *宣言パターン* が式に一致します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-136">Beginning with C# 7.0, a *declaration pattern* with type `T` matches an expression when an expression result is non-null and any of the following conditions are true:</span></span>

- <span data-ttu-id="c23e1-137">式の結果のランタイム型は `T` です。</span><span class="sxs-lookup"><span data-stu-id="c23e1-137">The runtime type of an expression result is `T`.</span></span>

- <span data-ttu-id="c23e1-138">式の結果のランタイム型は、`T` 型から派生するか、インターフェイス `T` を実装するか、または、それから `T` への[暗黙的な参照変換](~/_csharplang/spec/conversions.md#implicit-reference-conversions)が存在します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-138">The runtime type of an expression result derives from type `T` or implements interface `T` or another [implicit reference conversion](~/_csharplang/spec/conversions.md#implicit-reference-conversions) exists from it to `T`.</span></span> <span data-ttu-id="c23e1-139">次の例は、この条件が満たされている場合の 2 つのケースを示しています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-139">The following example demonstrates two cases when this condition is true:</span></span>

  :::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="ReferenceConversion":::

  <span data-ttu-id="c23e1-140">前の例では、`GetSourceLabel` メソッドへの最初の呼び出しで、引数 のランタイム型 `int[]` が <xref:System.Array> 型から派生しているため、最初のパターンが引数値と一致し ます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-140">In the preceding example, at the first call to the `GetSourceLabel` method, the first pattern matches an argument value because the argument's runtime type `int[]` derives from the <xref:System.Array> type.</span></span> <span data-ttu-id="c23e1-141">`GetSourceLabel` メソッドへの 2 つ目の呼び出しでは、引数のランタイム型 <xref:System.Collections.Generic.List%601> は、<xref:System.Array> 型から派生していませんが、<xref:System.Collections.Generic.ICollection%601> インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-141">At the second call to the `GetSourceLabel` method, the argument's runtime type <xref:System.Collections.Generic.List%601> doesn't derive from the <xref:System.Array> type but implements the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

- <span data-ttu-id="c23e1-142">式の結果のランタイム型は、基になる型 `T` を持つ [Null 許容値型](../builtin-types/nullable-value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="c23e1-142">The runtime type of an expression result is a [nullable value type](../builtin-types/nullable-value-types.md) with the underlying type `T`.</span></span>

- <span data-ttu-id="c23e1-143">式の結果のランタイム型から `T` 型までに、[ボックス化](../../programming-guide/types/boxing-and-unboxing.md#boxing)変換または[ボックス化解除](../../programming-guide/types/boxing-and-unboxing.md#unboxing)変換が存在します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-143">A [boxing](../../programming-guide/types/boxing-and-unboxing.md#boxing) or [unboxing](../../programming-guide/types/boxing-and-unboxing.md#unboxing) conversion exists from the runtime type of an expression result to type `T`.</span></span>

<span data-ttu-id="c23e1-144">次の例は、最後の 2 つの条件を示しています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-144">The following example demonstrates the last two conditions:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="NullableAndUnboxing":::

<span data-ttu-id="c23e1-145">式の型のみをチェックする場合は、次の例に示すように、変数名の代わりに破棄 `_` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-145">If you want to check only the type of an expression, you can use a discard `_` in place of a variable's name, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="DiscardVariable":::

<span data-ttu-id="c23e1-146">C# 9.0 以降、その目的のために、次の例に示すように *型パターン* を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-146">Beginning with C# 9.0, for that purpose you can use a *type pattern*, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="TypePattern":::

<span data-ttu-id="c23e1-147">宣言パターンと同様に、式の結果が null 以外で、そのランタイム型が上記のいずれかの条件を満たす場合に、型パターンは式に一致します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-147">Like a declaration pattern, a type pattern matches an expression when an expression result is non-null and its runtime type satisfies any of the conditions listed above.</span></span>

<span data-ttu-id="c23e1-148">詳細については、機能提案ノートの「[宣言パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern)」と「[型パターン](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-148">For more information, see the [Declaration pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern) and [Type pattern](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns) sections of the feature proposal notes.</span></span>

## <a name="constant-pattern"></a><span data-ttu-id="c23e1-149">定数パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-149">Constant pattern</span></span>

<span data-ttu-id="c23e1-150">C# 7.0 以降、次の例に示すように、*定数パターン* を使用して、式の結果が指定された定数と等しいかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-150">Beginning with C# 7.0, you use a *constant pattern* to test if an expression result equals a specified constant, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="BasicExample":::

<span data-ttu-id="c23e1-151">定数パターンでは、次のような任意の定数式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-151">In a constant pattern, you can use any constant expression, such as:</span></span>

- <span data-ttu-id="c23e1-152">[整数](../builtin-types/integral-numeric-types.md)または[浮動小数点](../builtin-types/floating-point-numeric-types.md)数値リテラル</span><span class="sxs-lookup"><span data-stu-id="c23e1-152">an [integer](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numerical literal</span></span>
- <span data-ttu-id="c23e1-153">[char](../builtin-types/char.md) または[文字列](../builtin-types/reference-types.md#the-string-type)リテラル</span><span class="sxs-lookup"><span data-stu-id="c23e1-153">a [char](../builtin-types/char.md) or a [string](../builtin-types/reference-types.md#the-string-type) literal</span></span>
- <span data-ttu-id="c23e1-154">ブール値 `true` または `false`</span><span class="sxs-lookup"><span data-stu-id="c23e1-154">a Boolean value `true` or `false`</span></span>
- <span data-ttu-id="c23e1-155">[列挙型](../builtin-types/enum.md)値</span><span class="sxs-lookup"><span data-stu-id="c23e1-155">an [enum](../builtin-types/enum.md) value</span></span>
- <span data-ttu-id="c23e1-156">宣言された[定数](../keywords/const.md)フィールドまたはローカルの名前</span><span class="sxs-lookup"><span data-stu-id="c23e1-156">the name of a declared [const](../keywords/const.md) field or local</span></span>
- `null`

<span data-ttu-id="c23e1-157">次の例に示すように、定数パターンを使用して `null` をチェックします。</span><span class="sxs-lookup"><span data-stu-id="c23e1-157">Use a constant pattern to check for `null`, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NullCheck":::

<span data-ttu-id="c23e1-158">コンパイラにより、式 `x is null` が評価されるときに、ユーザーがオーバーロードした等値演算子 `==` が呼び出されないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-158">The compiler guarantees that no user-overloaded equality operator `==` is invoked when expression `x is null` is evaluated.</span></span>

<span data-ttu-id="c23e1-159">C# 9.0 以降、次の例に示すように、[否定された](#logical-patterns) `null` 定数パターンを使用して null 以外であるかをチェックできます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-159">Beginning with C# 9.0, you can use a [negated](#logical-patterns) `null` constant pattern to check for non-null, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NonNullCheck":::

<span data-ttu-id="c23e1-160">詳細については、機能提案ノートの「[定数パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-160">For more information, see the [Constant pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern) section of the feature proposal note.</span></span>

## <a name="relational-patterns"></a><span data-ttu-id="c23e1-161">リレーショナル パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-161">Relational patterns</span></span>

<span data-ttu-id="c23e1-162">C# 9.0 以降、次の例に示すように、*リレーショナル パターン* を使用して、式の結果を定数と比較します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-162">Beginning with C# 9.0, you use a *relational pattern* to compare an expression result with a constant, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="BasicExample":::

<span data-ttu-id="c23e1-163">リレーショナル パターンでは、[関係演算子](comparison-operators.md) `<`、`>`、`<=`、または `>=` のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-163">In a relational pattern, you can use any of the [relational operators](comparison-operators.md) `<`, `>`, `<=`, or `>=`.</span></span> <span data-ttu-id="c23e1-164">リレーショナル パターンの右側の部分は、定数式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c23e1-164">The right-hand part of a relational pattern must be a constant expression.</span></span> <span data-ttu-id="c23e1-165">定数式には、[整数](../builtin-types/integral-numeric-types.md)、[浮動小数点](../builtin-types/floating-point-numeric-types.md)、[char](../builtin-types/char.md)、または[列挙](../builtin-types/enum.md)型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-165">The constant expression can be of an [integer](../builtin-types/integral-numeric-types.md), [floating-point](../builtin-types/floating-point-numeric-types.md), [char](../builtin-types/char.md), or [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="c23e1-166">式の結果が特定の範囲内にあるかどうかをチェックするには、次の例に示すように、[接続的`and`パターン](#logical-patterns)に対して、それを一致させます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-166">To check if an expression result is in a certain range, match it against a [conjunctive `and` pattern](#logical-patterns), as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="WithCombinators":::

<span data-ttu-id="c23e1-167">式の結果が `null` であるか、null 許容変換またはボックス化解除変換によって定数の型に変換できない場合、リレーショナル パターンは式に一致しません。</span><span class="sxs-lookup"><span data-stu-id="c23e1-167">If an expression result is `null` or fails to convert to the type of a constant by a nullable or unboxing conversion, a relational pattern doesn't match an expression.</span></span>

<span data-ttu-id="c23e1-168">詳細については、機能提案ノートの「[リレーショナル パターン](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-168">For more information, see the [Relational patterns](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns) section of the feature proposal note.</span></span>

## <a name="logical-patterns"></a><span data-ttu-id="c23e1-169">論理パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-169">Logical patterns</span></span>

<span data-ttu-id="c23e1-170">C# 9.0 以降、`not`、`and`、および `or` パターン連結子を使用して、次の *論理パターン* を作成します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-170">Beginning with C# 9.0, you use the `not`, `and`, and `or` pattern combinators to create the following *logical patterns*:</span></span>

- <span data-ttu-id="c23e1-171">否定されたパターンが式に一致しない場合に、式に一致する *否定*`not`パターン。</span><span class="sxs-lookup"><span data-stu-id="c23e1-171">*Negation* `not` pattern that matches an expression when the negated pattern doesn't match the expression.</span></span> <span data-ttu-id="c23e1-172">次の例に、[定数](#constant-pattern) `null` パターンを否定して、式が null でないかどうかを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-172">The following example shows how you can negate a [constant](#constant-pattern) `null` pattern to check if an expression is non-null:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="NotPattern":::

- <span data-ttu-id="c23e1-173">両方のパターンが式に一致する場合に、式に一致する *接続的*`and` パターン。</span><span class="sxs-lookup"><span data-stu-id="c23e1-173">*Conjunctive* `and` pattern that matches an expression when both patterns match the expression.</span></span> <span data-ttu-id="c23e1-174">次の例に、[リレーショナル パターン](#relational-patterns)を組み合わせて、値が特定の範囲内にあるかどうかをチェックする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-174">The following example shows how you can combine [relational patterns](#relational-patterns) to check if a value is in a certain range:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="AndPattern":::

- <span data-ttu-id="c23e1-175">次の例に示すように、いずれかのパターンが式に一致する場合に、式に一致する *離接的* `or` パターン。</span><span class="sxs-lookup"><span data-stu-id="c23e1-175">*Disjunctive* `or` pattern that matches an expression when either of patterns matches the expression, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="OrPattern":::

<span data-ttu-id="c23e1-176">前の例に示すように、パターンでパターンの連結子を繰り返し使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-176">As the preceding example shows, you can repeatedly use the pattern combinators in a pattern.</span></span>

<span data-ttu-id="c23e1-177">`and` パターン連結子は、`or` よりも優先順位が高くなります。</span><span class="sxs-lookup"><span data-stu-id="c23e1-177">The `and` pattern combinator has higher precedence than `or`.</span></span> <span data-ttu-id="c23e1-178">次の例に示すように、優先順位を明示的に指定するには、かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-178">To explicitly specify the precedence, use parentheses, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="WithParentheses":::

> [!NOTE]
> <span data-ttu-id="c23e1-179">パターンがチェックされる順序は定義されていません。</span><span class="sxs-lookup"><span data-stu-id="c23e1-179">The order in which patterns are checked is undefined.</span></span> <span data-ttu-id="c23e1-180">実行時に、`or` および `and` パターンの右側の入れ子になったパターンを最初にチェックできます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-180">At run time, the right-hand nested patterns of `or` and `and` patterns can be checked first.</span></span>

<span data-ttu-id="c23e1-181">詳細については、機能提案ノートの「[パターン連結子](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-181">For more information, see the [Pattern combinators](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators) section of the feature proposal note.</span></span>

## <a name="property-pattern"></a><span data-ttu-id="c23e1-182">プロパティ パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-182">Property pattern</span></span>

<span data-ttu-id="c23e1-183">C# 8.0 以降、次の例に示すように、*プロパティ パターン* を使用して、入れ子になったパターンに対して、式のプロパティまたはフィールドを一致させます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-183">Beginning with C# 8.0, you use a *property pattern* to match an expression's properties or fields against nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="BasicExample":::

<span data-ttu-id="c23e1-184">式の結果が null 以外で、すべての入れ子になったパターンが、式の結果の対応するプロパティまたはフィールドと一致する場合、プロパティ パターンは式に一致します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-184">A property pattern matches an expression when an expression result is non-null and every nested pattern matches the corresponding property or field of the expression result.</span></span>

<span data-ttu-id="c23e1-185">次の例に示すように、ランタイム型チェックと変数宣言をプロパティ パターンに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-185">You can also add a runtime type check and a variable declaration to a property pattern, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="WithTypeCheck":::

<span data-ttu-id="c23e1-186">プロパティ パターンは、再帰的パターンです。</span><span class="sxs-lookup"><span data-stu-id="c23e1-186">A property pattern is a recursive pattern.</span></span> <span data-ttu-id="c23e1-187">つまり、入れ子になったパターンとして任意のパターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-187">That is, you can use any pattern as a nested pattern.</span></span> <span data-ttu-id="c23e1-188">次の例に示すように、入れ子になったパターンに対して、データの一部を一致させるには、プロパティ パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-188">Use a property pattern to match parts of data against nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="RecursivePropertyPattern":::

<span data-ttu-id="c23e1-189">前の例では、C# 9.0 以降で使用できる 2 つの機能 (`or`[パターン連結子](#logical-patterns)と[レコード型](../builtin-types/record.md)) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-189">The preceding example uses two features available in C# 9.0 and later: `or` [pattern combinator](#logical-patterns) and [record types](../builtin-types/record.md).</span></span>

<span data-ttu-id="c23e1-190">詳細については、機能提案ノートの「[プロパティ パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-190">For more information, see the [Property pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern) section of the feature proposal note.</span></span>

## <a name="positional-pattern"></a><span data-ttu-id="c23e1-191">位置指定パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-191">Positional pattern</span></span>

<span data-ttu-id="c23e1-192">C# 8.0 以降、次の例に示すように、*位置指定パターン* を使用して、式の結果を分解し、結果の値を、対応する入れ子になったパターンに対して一致させます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-192">Beginning with C# 8.0, you use a *positional pattern* to deconstruct an expression result and match the resulting values against the corresponding nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="BasicExample":::

<span data-ttu-id="c23e1-193">前の例では、式の型に [Deconstruct](../../deconstruct.md) メソッドが含まれており、これは、式の結果を分解するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-193">At the preceding example, the type of an expression contains the [Deconstruct](../../deconstruct.md) method, which is used to deconstruct an expression result.</span></span> <span data-ttu-id="c23e1-194">また、位置指定パターンに対して[タプル型](../builtin-types/value-tuples.md)の式を一致させることもできます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-194">You can also match expressions of [tuple types](../builtin-types/value-tuples.md) against positional patterns.</span></span> <span data-ttu-id="c23e1-195">このようにして、次の例に示すように、複数の入力をさまざまなパターンに一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-195">In that way, you can match multiple inputs against various patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="MatchTuple":::

<span data-ttu-id="c23e1-196">前の例では、C# 9.0 以降で使用できる[リレーショナル](#relational-patterns) パターンと[論理](#logical-patterns)パターンを使用しています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-196">The preceding example uses [relational](#relational-patterns) and [logical](#logical-patterns) patterns, which are available in C# 9.0 and later.</span></span>

<span data-ttu-id="c23e1-197">次の例に示すように、位置指定パターンでタプル要素と `Deconstruct` パラメーターの名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-197">You can use the names of tuple elements and `Deconstruct` parameters in a positional pattern, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="UseIdentifiers":::

<span data-ttu-id="c23e1-198">また、次のいずれかの方法で位置指定パターンを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-198">You can also extend a positional pattern in any of the following ways:</span></span>

- <span data-ttu-id="c23e1-199">次の例に示すように、ランタイム型チェックと変数宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-199">Add a runtime type check and a variable declaration, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithTypeCheck":::

  <span data-ttu-id="c23e1-200">前の例では、`Deconstruct` メソッドを暗黙的に提供する[位置指定レコード](../builtin-types/record.md#positional-syntax-for-property-definition)を使用しています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-200">The preceding example uses [positional records](../builtin-types/record.md#positional-syntax-for-property-definition) that implicitly provide the `Deconstruct` method.</span></span>

- <span data-ttu-id="c23e1-201">次の例に示すように、位置指定パターン内で[プロパティ パターン](#property-pattern)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-201">Use a [property pattern](#property-pattern) within a positional pattern, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithPropertyPattern":::

- <span data-ttu-id="c23e1-202">次の例に示すように、前の 2 つの使用方法を組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-202">Combine two preceding usages, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="CompletePositionalPattern":::

<span data-ttu-id="c23e1-203">位置指定パターンは、再帰的パターンです。</span><span class="sxs-lookup"><span data-stu-id="c23e1-203">A positional pattern is a recursive pattern.</span></span> <span data-ttu-id="c23e1-204">つまり、入れ子になったパターンとして任意のパターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-204">That is, you can use any pattern as a nested pattern.</span></span>

<span data-ttu-id="c23e1-205">詳細については、機能提案ノートの「[位置指定パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-205">For more information, see the [Positional pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern) section of the feature proposal note.</span></span>

## <a name="var-pattern"></a><span data-ttu-id="c23e1-206">`var` パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-206">`var` pattern</span></span>

<span data-ttu-id="c23e1-207">C# 7.0 以降、次の例に示すように、 *`var` パターン* を使用して、`null` を含む任意の式に一致させ、その結果を新しいローカル変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-207">Beginning with C# 7.0, you use a *`var` pattern* to match any expression, including `null`, and assign its result to a new local variable, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="KeepInterimResult":::

<span data-ttu-id="c23e1-208">`var` パターンは、中間計算の結果を保持するためにブール式内に一時変数が必要な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c23e1-208">A `var` pattern is useful when you need a temporary variable within a Boolean expression to hold the result of intermediate calculations.</span></span> <span data-ttu-id="c23e1-209">さらに、次の例に示すように、`switch` 式またはステートメントの `when` case guard で追加のチェックを実行する必要がある場合は、`var` パターンを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-209">You can also use a `var` pattern when you need to perform additional checks in `when` case guards of a `switch` expression or statement, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="WithCaseGuards":::

<span data-ttu-id="c23e1-210">前の例で、パターン `var (x, y)` は [位置指定パターン](#positional-pattern) `(var x, var y)` と同じです。</span><span class="sxs-lookup"><span data-stu-id="c23e1-210">In the preceding example, pattern `var (x, y)` is equivalent to a [positional pattern](#positional-pattern) `(var x, var y)`.</span></span>

<span data-ttu-id="c23e1-211">`var` パターンでは、宣言された変数の型は、パターンに一致する式のコンパイル時の型になります。</span><span class="sxs-lookup"><span data-stu-id="c23e1-211">In a `var` pattern, the type of a declared variable is the compile-time type of the expression that is matched against the pattern.</span></span>

<span data-ttu-id="c23e1-212">詳細については、機能提案ノートの「[Var パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-212">For more information, see the [Var pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern) section of the feature proposal note.</span></span>

## <a name="discard-pattern"></a><span data-ttu-id="c23e1-213">破棄パターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-213">Discard pattern</span></span>

<span data-ttu-id="c23e1-214">C# 8.0 以降、次の例に示すように、*破棄パターン* `_` を使用して、`null` を含む任意の式に一致させます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-214">Beginning with C# 8.0, you use a *discard pattern* `_` to match any expression, including `null`, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DiscardPattern.cs" id="BasicExample":::

<span data-ttu-id="c23e1-215">前の例では、破棄パターンを使用して、`null` と、<xref:System.DayOfWeek> 列挙型の対応するメンバーを持たない任意の整数値を処理しています。</span><span class="sxs-lookup"><span data-stu-id="c23e1-215">In the preceding example, a discard pattern is used to handle `null` and any integer value that doesn't have the corresponding member of the <xref:System.DayOfWeek> enumeration.</span></span> <span data-ttu-id="c23e1-216">これにより、例の `switch` 式ですべての可能な入力値が処理されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-216">That guarantees that a `switch` expression in the example handles all possible input values.</span></span> <span data-ttu-id="c23e1-217">`switch` 式で破棄パターンを使用せず、式のパターンが入力に一致しない場合、ランタイムによって、[例外がスロー](switch-expression.md#non-exhaustive-switch-expressions)されます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-217">If you don't use a discard pattern in a `switch` expression and none of the expression's patterns matches an input, the runtime [throws an exception](switch-expression.md#non-exhaustive-switch-expressions).</span></span> <span data-ttu-id="c23e1-218">`switch` 式ですべての可能な入力値が処理されない場合、コンパイラで警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-218">The compiler generates a warning if a `switch` expression doesn't handle all possible input values.</span></span>

<span data-ttu-id="c23e1-219">破棄パターンを、`is` 式または `switch` ステートメントでパターンにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c23e1-219">A discard pattern cannot be a pattern in an `is` expression or a `switch` statement.</span></span> <span data-ttu-id="c23e1-220">そのような場合、任意の式に一致させるには、破棄を含む [`var` パターン](#var-pattern) `var _` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c23e1-220">In those cases, to match any expression, use a [`var` pattern](#var-pattern) with a discard: `var _`.</span></span>

<span data-ttu-id="c23e1-221">詳細については、機能提案ノートの「[破棄パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-221">For more information, see the [Discard pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern) section of the feature proposal note.</span></span>

## <a name="parenthesized-pattern"></a><span data-ttu-id="c23e1-222">かっこで囲まれたパターン</span><span class="sxs-lookup"><span data-stu-id="c23e1-222">Parenthesized pattern</span></span>

<span data-ttu-id="c23e1-223">C# 9.0 以降、任意のパターンをかっこで囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="c23e1-223">Beginning with C# 9.0, you can put parentheses around any pattern.</span></span> <span data-ttu-id="c23e1-224">一般にそれを行うのは、次の例に示すように、[論理パターン](#logical-patterns)の優先順位を強調または変更するためです。</span><span class="sxs-lookup"><span data-stu-id="c23e1-224">Typically, you do that to emphasize or change the precedence in [logical patterns](#logical-patterns), as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="ChangedPrecedence":::

## <a name="c-language-specification"></a><span data-ttu-id="c23e1-225">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c23e1-225">C# language specification</span></span>

<span data-ttu-id="c23e1-226">詳しくは、次の機能提案メモをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c23e1-226">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="c23e1-227">C# 7.0 のパターン マッチング</span><span class="sxs-lookup"><span data-stu-id="c23e1-227">Pattern matching for C# 7.0</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="c23e1-228">再帰的なパターンマッチング (C# 8.0 で導入)</span><span class="sxs-lookup"><span data-stu-id="c23e1-228">Recursive pattern matching (introduced in C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/patterns.md)
- [<span data-ttu-id="c23e1-229">C# 9.0 のパターン マッチングの変更</span><span class="sxs-lookup"><span data-stu-id="c23e1-229">Pattern-matching changes for C# 9.0</span></span>](~/_csharplang/proposals/csharp-9.0/patterns3.md)

## <a name="see-also"></a><span data-ttu-id="c23e1-230">関連項目</span><span class="sxs-lookup"><span data-stu-id="c23e1-230">See also</span></span>

- [<span data-ttu-id="c23e1-231">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="c23e1-231">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c23e1-232">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="c23e1-232">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="c23e1-233">チュートリアル: パターン マッチングを使用して、型ドリブンおよびデータ ドリブンのアルゴリズムを構築する</span><span class="sxs-lookup"><span data-stu-id="c23e1-233">Tutorial: Use pattern matching to build type-driven and data-driven algorithms</span></span>](../../tutorials/pattern-matching.md)
