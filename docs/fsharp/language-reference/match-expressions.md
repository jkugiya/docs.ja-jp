---
title: match 式
description: F# match 式により、式と一連のパターンとの比較に基づいて分岐がどのように制御されるかを説明します。
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627611"
---
# <a name="match-expressions"></a><span data-ttu-id="ef3b4-103">match 式</span><span class="sxs-lookup"><span data-stu-id="ef3b4-103">Match expressions</span></span>

<span data-ttu-id="ef3b4-104">`match` 式により、式と一連のパターンとの比較に基づいて分岐が制御されます。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef3b4-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef3b4-105">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="ef3b4-106">解説</span><span class="sxs-lookup"><span data-stu-id="ef3b4-106">Remarks</span></span>

<span data-ttu-id="ef3b4-107">パターン マッチング式を使用すると、テスト式と一連のパターンとの比較に基づいて、複雑な分岐が可能になります。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="ef3b4-108">`match` 式では、各パターンと *test-expression* が比較され、一致が見つかると、対応する *result-expression* が評価され、結果の値が match 式の値として返されます。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="ef3b4-109">前の構文で示されているパターン マッチング関数は、パターン マッチングが引数ですぐに実行されるラムダ式です。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="ef3b4-110">前の構文で示されているパターン マッチング関数は、以下と同じです。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="ef3b4-111">ラムダ式について詳しくは、「[ラムダ式: `fun` キーワード](./functions/lambda-expressions-the-fun-keyword.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="ef3b4-112">一連のパターン全体で、入力変数のすべての一致候補をカバーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="ef3b4-113">多くの場合、それより前で一致していない入力値と一致させるために、最後のパターンとしてワイルドカード パターン (`_`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="ef3b4-114">次のコードは、`match` 式が使用されるいくつかの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="ef3b4-115">使用可能なすべてのパターンの参照と例については、「[パターン マッチング](pattern-matching.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="ef3b4-116">パターンでのガード</span><span class="sxs-lookup"><span data-stu-id="ef3b4-116">Guards on patterns</span></span>

<span data-ttu-id="ef3b4-117">`when` 句を使用して、変数がパターンに一致するために満たす必要のある追加条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="ef3b4-118">このような句を *ガード* と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="ef3b4-119">`when` キーワードに続く式は、そのガードに関連付けられているパターンと一致しない限り評価されません。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="ef3b4-120">次の例は、変数パターンの数値範囲を指定するためのガードの使用例を示しています。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="ef3b4-121">複数の条件は、ブール演算子を使用することによって結合されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="ef3b4-122">リテラル以外の値はパターンで使用できないため、入力の一部を値と比較する必要がある場合は、`when` 句を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="ef3b4-123">これを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="ef3b4-124">和集合パターンがガードでカバーされている場合、ガードは、最後のものだけでなく、**すべて** のパターンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="ef3b4-125">たとえば、次のコードにおいて、ガード `when a > 12` は `A a` と `B a` の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ef3b4-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="ef3b4-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef3b4-126">See also</span></span>

- [<span data-ttu-id="ef3b4-127">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="ef3b4-127">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ef3b4-128">アクティブ パターン</span><span class="sxs-lookup"><span data-stu-id="ef3b4-128">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="ef3b4-129">パターン一致</span><span class="sxs-lookup"><span data-stu-id="ef3b4-129">Pattern Matching</span></span>](pattern-matching.md)
