---
description: '! (null 免除) 演算子 - C# リファレンス'
title: '! (null 免除) 演算子 - C# リファレンス'
ms.date: 11/13/2020
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 14bc4501dfed515e162a6e30137c9def89bb3651
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111076"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="320ab-105">!</span><span class="sxs-lookup"><span data-stu-id="320ab-105">!</span></span> <span data-ttu-id="320ab-106">(null 免除) 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="320ab-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="320ab-107">C# 8.0 以降では、単項の接尾辞 `!` 演算子は null 免除 (または null 抑制) 演算子です。</span><span class="sxs-lookup"><span data-stu-id="320ab-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving, or null-suppression, operator.</span></span> <span data-ttu-id="320ab-108">有効な [null 許容注釈コンテキスト](../../nullable-references.md#nullable-annotation-context)では、null 免除演算子を使用して、参照型の式 `x` が `null`: `x!` ではないことを宣言します。</span><span class="sxs-lookup"><span data-stu-id="320ab-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="320ab-109">単項の接頭辞 `!` 演算子は、[論理否定演算子](boolean-logical-operators.md#logical-negation-operator-)です。</span><span class="sxs-lookup"><span data-stu-id="320ab-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="320ab-110">null 免除演算子は実行時には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="320ab-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="320ab-111">式の null 状態を変更することによって、コンパイラの静的フロー分析にのみ影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="320ab-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="320ab-112">実行時に、式 `x!` は基になる式 `x` の結果に評価されます。</span><span class="sxs-lookup"><span data-stu-id="320ab-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="320ab-113">null 許容参照型の機能の詳細については、「[null 許容参照型](../builtin-types/nullable-reference-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="320ab-113">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="320ab-114">使用例</span><span class="sxs-lookup"><span data-stu-id="320ab-114">Examples</span></span>

<span data-ttu-id="320ab-115">null 免除演算子のユース ケースの 1 つは、引数検証ロジックをテストすることです。</span><span class="sxs-lookup"><span data-stu-id="320ab-115">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="320ab-116">たとえば、次のクラスを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="320ab-116">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="320ab-117">[MSTest テスト フレームワーク](../../../core/testing/unit-testing-with-mstest.md) を使用して、コンストラクターの検証ロジックに対して次のテストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="320ab-117">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="320ab-118">null 免除演算子を使用しない場合は、コンパイラによって上のコードに対して次の警告が生成されます: `Warning CS8625: Cannot convert null literal to non-nullable reference type`。</span><span class="sxs-lookup"><span data-stu-id="320ab-118">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="320ab-119">null 免除演算子を使用すると、`null` を渡すことが予測されており、警告を生成しないことがコンパイラに通知されます。</span><span class="sxs-lookup"><span data-stu-id="320ab-119">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="320ab-120">また、式を `null` にできないことが明確にわかっているが、コンパイラでそのことを認識できない場合にも、null 免除演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="320ab-120">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="320ab-121">次の例では、`IsValid` メソッドによって `true` が返された場合、その引数は `null` ではなく、安全に逆参照できます。</span><span class="sxs-lookup"><span data-stu-id="320ab-121">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="320ab-122">null 免除演算子を使用しない場合は、コンパイラによって `p.Name` コードに対して次の警告が生成されます: `Warning CS8602: Dereference of a possibly null reference`。</span><span class="sxs-lookup"><span data-stu-id="320ab-122">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="320ab-123">`IsValid` メソッドを変更できる場合は、[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) 属性を使用して、メソッドによって `true` が返されたときに `IsValid` メソッドの引数を `null` にできないことをコンパイラに通知することができます。</span><span class="sxs-lookup"><span data-stu-id="320ab-123">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="320ab-124">前の例では、null 免除演算子を使用する必要はありません。これは、`if` ステートメント内で `p` を `null` にできないことを把握するのに十分な情報がコンパイラに含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="320ab-124">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="320ab-125">変数の null 状態に関する追加情報を提供するための属性の詳細については、[null 予測を定義する属性を使用した API のアップグレード](../attributes/nullable-analysis.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="320ab-125">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="320ab-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="320ab-126">C# language specification</span></span>

<span data-ttu-id="320ab-127">詳細については、[null 許容参照型仕様の下書き](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)の「[null 免除演算子](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="320ab-127">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="320ab-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="320ab-128">See also</span></span>

- [<span data-ttu-id="320ab-129">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="320ab-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="320ab-130">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="320ab-130">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="320ab-131">チュートリアル: null 許容参照型を使用して設計する</span><span class="sxs-lookup"><span data-stu-id="320ab-131">Tutorial: Design with nullable reference types</span></span>](../../whats-new/tutorials/nullable-reference-types.md)
