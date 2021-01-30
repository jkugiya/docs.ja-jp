---
title: '再帰関数: rec キーワード'
description: "再帰関数を定義するために、' let ' キーワードと共に F # ' rec ' キーワードを使用する方法について説明します。"
ms.date: 08/12/2020
ms.openlocfilehash: 27f215f7b6f09646e847898c2618cfac10175e6e
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215713"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="b39d4-103">再帰関数: rec キーワード</span><span class="sxs-lookup"><span data-stu-id="b39d4-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="b39d4-104">キーワードは、 `rec` `let` 再帰関数を定義するためにキーワードと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="b39d4-105">構文</span><span class="sxs-lookup"><span data-stu-id="b39d4-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
    function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
    function1-body

and function2-nameparameter-list =
    function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="b39d4-106">解説</span><span class="sxs-lookup"><span data-stu-id="b39d4-106">Remarks</span></span>

<span data-ttu-id="b39d4-107">再帰関数-自身を呼び出す関数は、F # 言語でキーワードを使用して明示的に識別され `rec` ます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="b39d4-108">キーワードを使用すると、 `rec` バインディングの名前を `let` 本体で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b39d4-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="b39d4-109">次の例は、数学的定義を使用して *n*<sup>番目</sup> のフィボナッチ数を計算する再帰関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="b39d4-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> n
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="b39d4-110">実際には、前のサンプルのようなコードは、既に計算されている値を unecessarily しているため、理想的ではありません。</span><span class="sxs-lookup"><span data-stu-id="b39d4-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="b39d4-111">これは、この記事で詳しく説明されている末尾の再帰ではないためです。</span><span class="sxs-lookup"><span data-stu-id="b39d4-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="b39d4-112">メソッドは、定義されている型内で暗黙的に再帰的に行われます。つまり、キーワードを追加する必要はありません `rec` 。</span><span class="sxs-lookup"><span data-stu-id="b39d4-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="b39d4-113">例:</span><span class="sxs-lookup"><span data-stu-id="b39d4-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> n
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="b39d4-114">ただし、クラス内のバインディングは暗黙的に再帰的ではありません。</span><span class="sxs-lookup"><span data-stu-id="b39d4-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="b39d4-115">すべて `let` のバインドされた関数にはキーワードが必要 `rec` です。</span><span class="sxs-lookup"><span data-stu-id="b39d4-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="b39d4-116">Tail 再帰</span><span class="sxs-lookup"><span data-stu-id="b39d4-116">Tail recursion</span></span>

<span data-ttu-id="b39d4-117">再帰関数によっては、より "純粋な" 定義を [末尾の再帰](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)型にリファクタリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b39d4-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="b39d4-118">これにより、不要な再計算が防止されます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="b39d4-119">たとえば、前のフィボナッチ数ジェネレーターは次のように書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="b39d4-120">これはより複雑な実装です。</span><span class="sxs-lookup"><span data-stu-id="b39d4-120">This is a more complicated implementation.</span></span> <span data-ttu-id="b39d4-121">フィボナッチ数を生成することは、数学的に純粋だが実用的ではない "単純な" アルゴリズムの好例です。</span><span class="sxs-lookup"><span data-stu-id="b39d4-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="b39d4-122">いくつかの側面では、F # で効率的に実行できますが、再帰的に定義されています。</span><span class="sxs-lookup"><span data-stu-id="b39d4-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="b39d4-123">という名前の再帰的な内部関数 `loop` (慣用的な F # パターン)。</span><span class="sxs-lookup"><span data-stu-id="b39d4-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="b39d4-124">2つのアキュムレータパラメーター。累積値を再帰呼び出しに渡します。</span><span class="sxs-lookup"><span data-stu-id="b39d4-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="b39d4-125">の値をチェックして、特定の累積値を `n` 返します。</span><span class="sxs-lookup"><span data-stu-id="b39d4-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="b39d4-126">この例がループで繰り返し記述されている場合、コードは、特定の条件が満たされるまで、2つの異なる値を累積したものと似ています。</span><span class="sxs-lookup"><span data-stu-id="b39d4-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="b39d4-127">再帰呼び出しでは、呼び出し履歴に値を保存する必要がないため、これが末尾再帰の原因です。</span><span class="sxs-lookup"><span data-stu-id="b39d4-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="b39d4-128">計算されるすべての中間値は、内部関数への入力によって累積されます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="b39d4-129">これにより、F # コンパイラは、ループのようなものを記述した場合と同じように、コードを最適化することもでき `while` ます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="b39d4-130">前の例で示したように、内部関数と外部関数を使用して何かを再帰的に処理する F # コードを記述するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="b39d4-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="b39d4-131">内部関数は、末尾の再帰を使用します。一方、外側の関数は、呼び出し元に対してより適切なインターフェイスを備えています。</span><span class="sxs-lookup"><span data-stu-id="b39d4-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="b39d4-132">相互再帰関数</span><span class="sxs-lookup"><span data-stu-id="b39d4-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="b39d4-133">場合によっては、関数が *相互に再帰的* であることを意味します。これは、呼び出しが円を形成することを意味します。この場合、1つ目の関数はを呼び出し、その間に任意の数の呼び出しを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b39d4-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="b39d4-134">このような関数は、1つのバインディングで定義し `let` 、キーワードを使用してそれらをリンクする必要があり `and` ます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="b39d4-135">次の例は、2つの相互再帰関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="b39d4-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="b39d4-136">再帰的な値</span><span class="sxs-lookup"><span data-stu-id="b39d4-136">Recursive values</span></span>

<span data-ttu-id="b39d4-137">また、 `let` 再帰的になるように、バインドされた値を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="b39d4-138">これは、ログ記録のために行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="b39d4-138">This is sometimes done for logging.</span></span> <span data-ttu-id="b39d4-139">F # 5 と関数を使用 `nameof` すると、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b39d4-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="b39d4-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b39d4-140">See also</span></span>

- [<span data-ttu-id="b39d4-141">関数</span><span class="sxs-lookup"><span data-stu-id="b39d4-141">Functions</span></span>](index.md)
