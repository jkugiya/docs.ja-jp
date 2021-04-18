---
description: '?: 演算子 - C# リファレンス'
title: '?: 演算子 - C# リファレンス'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 84a740f3afeca94a706b4120b8cd8f191f49a048
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369570"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="48ef5-103">?: 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="48ef5-103">?: operator (C# reference)</span></span>

<span data-ttu-id="48ef5-104">条件演算子 `?:` は、三項条件演算子とも呼ばれ、ブール式を評価し、ブール式の評価結果 (`true` または `false`) に応じて、2 つの式のいずれかの結果を返します。次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48ef5-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`, as the following example shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="snippets/shared/ConditionalOperator.cs" id="BasicExample":::

<span data-ttu-id="48ef5-105">前の例で示したように、条件演算子の構文は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-105">As the preceding example shows, the syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="48ef5-106">`condition` 式は `true` または `false` と評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="48ef5-107">`condition` が `true` と評価された場合は、`consequent` 式が評価され、その結果が演算の結果になります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="48ef5-108">`condition` が `false` と評価された場合は、`alternative` 式が評価され、その結果が演算の結果になります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="48ef5-109">`consequent` または `alternative` のみが評価されます。</span><span class="sxs-lookup"><span data-stu-id="48ef5-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="48ef5-110">C# 9.0 以降、条件式はターゲット型になっています。</span><span class="sxs-lookup"><span data-stu-id="48ef5-110">Beginning with C# 9.0, conditional expressions are target-typed.</span></span> <span data-ttu-id="48ef5-111">つまり、条件式のターゲット型がわかっている場合、次の例に示すように、`consequent` と `alternative` の型は、暗黙的にターゲット型に変換できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-111">That is, if a target type of a conditional expression is known, the types of `consequent` and `alternative` must be implicitly convertible to the target type, as the following example shows:</span></span>

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

<span data-ttu-id="48ef5-112">条件式のターゲット型が不明な場合 (たとえば、[`var`](../keywords/var.md) キーワードを使用する場合) または C# 8.0 以前の場合、`consequent` と `alternative` の型は同じであるか、またはある型から別の型に暗黙的に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-112">If a target type of a conditional expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword) or in C# 8.0 and earlier, the type of `consequent` and `alternative` must be the same or there must be an implicit conversion from one type to the other:</span></span>

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

<span data-ttu-id="48ef5-113">条件演算子は右結合です。つまり、次の形式の式があるとします。</span><span class="sxs-lookup"><span data-stu-id="48ef5-113">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="48ef5-114">これが次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="48ef5-114">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="48ef5-115">次のニーモニック デバイスを使用して、条件演算子の評価方法を思い出すことができます。</span><span class="sxs-lookup"><span data-stu-id="48ef5-115">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

## <a name="conditional-ref-expression"></a><span data-ttu-id="48ef5-116">ref 条件式</span><span class="sxs-lookup"><span data-stu-id="48ef5-116">Conditional ref expression</span></span>

<span data-ttu-id="48ef5-117">C# 7.2 以降、ref 条件式は、[ref ローカル](../keywords/ref.md#ref-locals)または [ref readonly ローカル](../keywords/ref.md#ref-readonly-locals)変数を使用して条件付きで割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="48ef5-117">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with a conditional ref expression.</span></span> <span data-ttu-id="48ef5-118">ref 条件式を[参照戻り値](../keywords/ref.md#reference-return-values)または [`ref` メソッドの引数](../keywords/ref.md#passing-an-argument-by-reference)として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="48ef5-118">You can also use a conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="48ef5-119">ref 条件式の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="48ef5-119">The syntax for a conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="48ef5-120">ref 条件式では、元の条件演算子と同じように、2 つの式 (`consequent` または `alternative`) のいずれかのみが評価されます。</span><span class="sxs-lookup"><span data-stu-id="48ef5-120">Like the original conditional operator, a conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="48ef5-121">ref 条件式の場合、`consequent` と `alternative` の型は同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-121">In the case of a conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span> <span data-ttu-id="48ef5-122">ref 条件式は、ターゲット型ではありません。</span><span class="sxs-lookup"><span data-stu-id="48ef5-122">Conditional ref expressions are not target-typed.</span></span>

<span data-ttu-id="48ef5-123">ref 条件演算子の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="48ef5-123">The following example demonstrates the usage of a conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="48ef5-124">条件演算子と `if..else` ステートメント</span><span class="sxs-lookup"><span data-stu-id="48ef5-124">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="48ef5-125">[if-else](../keywords/if-else.md) ステートメントではなく条件演算子を使用すると、値の計算を条件付きで実行する必要がある場合に、コードをもっと簡潔にできる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="48ef5-125">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="48ef5-126">次の例では、整数を負の値または負以外の値に分類するための 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="48ef5-126">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="48ef5-127">演算子のオーバーロード可/不可</span><span class="sxs-lookup"><span data-stu-id="48ef5-127">Operator overloadability</span></span>

<span data-ttu-id="48ef5-128">ユーザー定義型は条件演算子をオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="48ef5-128">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="48ef5-129">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="48ef5-129">C# language specification</span></span>

<span data-ttu-id="48ef5-130">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の「[条件演算子](~/_csharplang/spec/expressions.md#conditional-operator)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48ef5-130">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="48ef5-131">C# 7.2 以降に追加された機能の詳細については、機能の提案に関する次の記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48ef5-131">For more information about features added in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="48ef5-132">ref 条件式 (C# 7.2)</span><span class="sxs-lookup"><span data-stu-id="48ef5-132">Conditional ref expressions (C# 7.2)</span></span>](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [<span data-ttu-id="48ef5-133">ターゲット型の条件式 (C# 9.0)</span><span class="sxs-lookup"><span data-stu-id="48ef5-133">Target-typed conditional expression (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a><span data-ttu-id="48ef5-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="48ef5-134">See also</span></span>

- [<span data-ttu-id="48ef5-135">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="48ef5-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="48ef5-136">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="48ef5-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="48ef5-137">if-else ステートメント</span><span class="sxs-lookup"><span data-stu-id="48ef5-137">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="48ef5-138">[?. および ?[] 演算子](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="48ef5-138">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="48ef5-139">?? および ??= 演算子</span><span class="sxs-lookup"><span data-stu-id="48ef5-139">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="48ef5-140">ref キーワード</span><span class="sxs-lookup"><span data-stu-id="48ef5-140">ref keyword</span></span>](../keywords/ref.md)
