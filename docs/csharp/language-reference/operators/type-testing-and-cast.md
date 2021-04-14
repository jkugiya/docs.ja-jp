---
title: 型のテスト演算子とキャスト式 - C# リファレンス
description: 式の結果の型を確認し、必要に応じて別の型に変換することができる、C# の演算子について説明します。
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
- as
- typeof
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: f47074fda20c1bc2eda75184dd26c9de1c0e3701
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075317"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="553c9-103">型のテスト演算子とキャスト式 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="553c9-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="553c9-104">次の演算子と式を使用して、型のチェックまたは型の変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="553c9-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="553c9-105">[is 演算子](#is-operator): 式のランタイム型と指定された型の間に互換性があるかどうかを確認します</span><span class="sxs-lookup"><span data-stu-id="553c9-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="553c9-106">[as 演算子](#as-operator): 式のランタイム型と指定された型の間に互換性がある場合、式を指定された型に明示的に変換します</span><span class="sxs-lookup"><span data-stu-id="553c9-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="553c9-107">[キャスト式](#cast-expression): 明示的な変換を実行します</span><span class="sxs-lookup"><span data-stu-id="553c9-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="553c9-108">[typeof 演算子](#typeof-operator): 型の <xref:System.Type?displayProperty=nameWithType> インスタンスを取得します</span><span class="sxs-lookup"><span data-stu-id="553c9-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="553c9-109">is 演算子</span><span class="sxs-lookup"><span data-stu-id="553c9-109">is operator</span></span>

<span data-ttu-id="553c9-110">`is` 演算子では、式の結果のランタイム型と指定された型の間に互換性があるかどうかが調べられます。</span><span class="sxs-lookup"><span data-stu-id="553c9-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="553c9-111">C# 7.0 以降の `is` 演算子では、パターンに対する式の結果のテストも行われます。</span><span class="sxs-lookup"><span data-stu-id="553c9-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="553c9-112">`is` 型テスト演算子を使用する式の形式は次のとおりです</span><span class="sxs-lookup"><span data-stu-id="553c9-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="553c9-113">`E` は値を返す式であり、`T` は型または型パラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="553c9-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="553c9-114">`E` を匿名メソッドまたはラムダ式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="553c9-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="553c9-115">式 `E is T` では、`E` の結果が null ではなく、参照変換、ボックス化変換、またはボックス化解除変換によって型 `T` に変換できる場合は `true` が返され、それ以外の場合は `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="553c9-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="553c9-116">`is` 演算子では、ユーザー定義変換は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="553c9-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="553c9-117">次の例で示す `is` 演算子では、式の結果のランタイム型が指定された型から派生する場合、つまり型の間に参照変換が存在する場合は、`true` が返されます。</span><span class="sxs-lookup"><span data-stu-id="553c9-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="553c9-118">次の例で示す `is` 演算子では、ボックス化変換とボックス化解除変換は考慮されますが、[数値変換](../builtin-types/numeric-conversions.md)は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="553c9-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="553c9-119">C# の変換については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[Conversions (変換)](~/_csharplang/spec/conversions.md)」の章をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="553c9-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="553c9-120">パターン マッチングを使用する型テスト</span><span class="sxs-lookup"><span data-stu-id="553c9-120">Type testing with pattern matching</span></span>

<span data-ttu-id="553c9-121">C# 7.0 以降の `is` 演算子では、パターンに対する式の結果のテストも行われます。</span><span class="sxs-lookup"><span data-stu-id="553c9-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="553c9-122">次の例は、[宣言パターン](patterns.md#declaration-and-type-patterns)を使用して、式のランタイム型を確認する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="553c9-122">The following example shows how to use a [declaration pattern](patterns.md#declaration-and-type-patterns) to check the runtime type of an expression:</span></span>

[!code-csharp-interactive[is with declaration pattern](snippets/shared/TypeTestingAndConversionOperators.cs#IsDeclarationPattern)]

<span data-ttu-id="553c9-123">サポートされているパターンの詳細については、「[パターン](patterns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="553c9-123">For information about the supported patterns, see [Patterns](patterns.md).</span></span>

## <a name="as-operator"></a><span data-ttu-id="553c9-124">as 演算子</span><span class="sxs-lookup"><span data-stu-id="553c9-124">as operator</span></span>

<span data-ttu-id="553c9-125">`as` 演算子では、式の結果が、指定された参照型または null 許容値型に明示的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="553c9-125">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="553c9-126">変換できない場合、`as` 演算子からは `null` が返されます。</span><span class="sxs-lookup"><span data-stu-id="553c9-126">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="553c9-127">[キャスト式](#cast-expression)とは異なり、`as` 演算子では例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="553c9-127">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="553c9-128">式の形式は次のとおりです</span><span class="sxs-lookup"><span data-stu-id="553c9-128">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="553c9-129">`E` は値を返す式であり、`T` は型または型パラメーターの名前です。次の式と同じ結果が生成されます</span><span class="sxs-lookup"><span data-stu-id="553c9-129">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="553c9-130">ただし、`E` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="553c9-130">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="553c9-131">`as` 演算子では、参照、null 許容、ボックス化、およびボックス化解除の各変換だけが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="553c9-131">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="553c9-132">`as` 演算子を使って、ユーザー定義の変換を実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="553c9-132">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="553c9-133">これを行うには、[キャスト式](#cast-expression)を使用します。</span><span class="sxs-lookup"><span data-stu-id="553c9-133">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="553c9-134">`as` 演算子の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="553c9-134">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/shared/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="553c9-135">上の例のように、変換が成功したかどうかを確認するには、`as` 式の結果を `null` と比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="553c9-135">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="553c9-136">C# 7.0 以降では、変換が成功するかどうかのテストと、成功する場合の新しい変数への結果の代入の両方を、[is 演算子](#type-testing-with-pattern-matching)を使って行うことができます。</span><span class="sxs-lookup"><span data-stu-id="553c9-136">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="553c9-137">キャスト式</span><span class="sxs-lookup"><span data-stu-id="553c9-137">Cast expression</span></span>

<span data-ttu-id="553c9-138">`(T)E` という形式のキャスト式では、式 `E` の結果が、型 `T` に明示的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="553c9-138">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="553c9-139">型 `E` から型 `T` への明示的な変換が存在しない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="553c9-139">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="553c9-140">実行時に、明示的な変換が成功せず、キャスト式で例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="553c9-140">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="553c9-141">次の例では、数値と参照の明示的な変換を示します。</span><span class="sxs-lookup"><span data-stu-id="553c9-141">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/shared/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="553c9-142">サポートされる明示的な変換については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[Explicit conversions (明示的な変換)](~/_csharplang/spec/conversions.md#explicit-conversions)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="553c9-142">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="553c9-143">カスタムの明示的または暗黙的な型変換を定義する方法については、「[User-defined conversion operators](user-defined-conversion-operators.md)」(ユーザー定義の変換演算子) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="553c9-143">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="553c9-144">() の他の使用方法</span><span class="sxs-lookup"><span data-stu-id="553c9-144">Other usages of ()</span></span>

<span data-ttu-id="553c9-145">かっこは、[メソッドまたはデリゲートを呼び出すとき](member-access-operators.md#invocation-expression-)にも使います。</span><span class="sxs-lookup"><span data-stu-id="553c9-145">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="553c9-146">他には、式に含まれる演算を評価する順序を調整する場合にもかっこを使います。</span><span class="sxs-lookup"><span data-stu-id="553c9-146">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="553c9-147">詳細については、[C# 演算子](index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="553c9-147">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="553c9-148">typeof 演算子</span><span class="sxs-lookup"><span data-stu-id="553c9-148">typeof operator</span></span>

<span data-ttu-id="553c9-149">`typeof` 演算子では、型の <xref:System.Type?displayProperty=nameWithType> インスタンスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="553c9-149">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="553c9-150">`typeof` 演算子への引数では、次の例で示すように、型または型パラメーターの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="553c9-150">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="553c9-151">バインドされていないジェネリック型で `typeof` 演算子を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="553c9-151">You can also use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="553c9-152">バインドされていないジェネリック型の名前には、適切な数のコンマが含まれる必要があります。これは、型パラメーターの数より 1 だけ少ない数です。</span><span class="sxs-lookup"><span data-stu-id="553c9-152">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="553c9-153">次の例では、バインドされていないジェネリック型での `typeof` 演算子の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="553c9-153">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="553c9-154">式を `typeof` 演算子の引数にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="553c9-154">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="553c9-155">式の結果のランタイム型に対する <xref:System.Type?displayProperty=nameWithType> インスタンスを取得するには、<xref:System.Object.GetType%2A?displayProperty=nameWithType> メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="553c9-155">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="553c9-156">`typeof` 演算子での型テスト</span><span class="sxs-lookup"><span data-stu-id="553c9-156">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="553c9-157">`typeof` 演算子を使って、式の結果のランタイム型が指定された型と完全に一致するかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="553c9-157">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="553c9-158">次の例では、`typeof` 演算子と [is 演算子](#is-operator)で実行される型チェックの違いを示します。</span><span class="sxs-lookup"><span data-stu-id="553c9-158">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/shared/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="553c9-159">演算子のオーバーロード可/不可</span><span class="sxs-lookup"><span data-stu-id="553c9-159">Operator overloadability</span></span>

<span data-ttu-id="553c9-160">`is`、`as`、および `typeof` の各演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="553c9-160">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="553c9-161">ユーザー定義型で `()` 演算子をオーバーロードすることはできませんが、キャスト式で実行できるカスタム型変換を定義することはできます。</span><span class="sxs-lookup"><span data-stu-id="553c9-161">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="553c9-162">詳細については、「[ユーザー定義の変換演算子](user-defined-conversion-operators.md)」 に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="553c9-162">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="553c9-163">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="553c9-163">C# language specification</span></span>

<span data-ttu-id="553c9-164">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="553c9-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="553c9-165">is 演算子</span><span class="sxs-lookup"><span data-stu-id="553c9-165">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="553c9-166">as 演算子</span><span class="sxs-lookup"><span data-stu-id="553c9-166">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="553c9-167">キャスト式</span><span class="sxs-lookup"><span data-stu-id="553c9-167">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="553c9-168">typeof 演算子</span><span class="sxs-lookup"><span data-stu-id="553c9-168">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="553c9-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="553c9-169">See also</span></span>

- [<span data-ttu-id="553c9-170">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="553c9-170">C# reference</span></span>](../index.md)
- [<span data-ttu-id="553c9-171">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="553c9-171">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="553c9-172">パターン マッチング、is 演算子、as 演算子を使用して安全にキャストする方法</span><span class="sxs-lookup"><span data-stu-id="553c9-172">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="553c9-173">.NET のジェネリック</span><span class="sxs-lookup"><span data-stu-id="553c9-173">Generics in .NET</span></span>](../../../standard/generics/index.md)
