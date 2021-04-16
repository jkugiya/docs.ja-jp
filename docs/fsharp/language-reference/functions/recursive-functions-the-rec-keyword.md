---
title: '再帰関数: rec キーワード'
description: 再帰関数を定義するために F# 'let' キーワードと共に 'rec' キーワードを使用する方法について説明します。
ms.date: 08/12/2020
ms.openlocfilehash: 27f215f7b6f09646e847898c2618cfac10175e6e
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215713"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="de48e-103">再帰関数: rec キーワード</span><span class="sxs-lookup"><span data-stu-id="de48e-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="de48e-104">`rec` キーワードは、`let` キーワードと共に使用して、再帰関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="de48e-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="de48e-105">構文</span><span class="sxs-lookup"><span data-stu-id="de48e-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="de48e-106">解説</span><span class="sxs-lookup"><span data-stu-id="de48e-106">Remarks</span></span>

<span data-ttu-id="de48e-107">再帰関数 (それ自身を呼び出す関数) は、F# 言語では、`rec` キーワードを使用して明示的に識別します。</span><span class="sxs-lookup"><span data-stu-id="de48e-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="de48e-108">`rec` キーワードを使用すると、`let` バインドの名前をその本体で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="de48e-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="de48e-109">次の例は、数学的な定義を使用して *n*<sup> </sup>番目のフィボナッチ数を計算する再帰関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="de48e-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> n
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="de48e-110">実際には、前のサンプルのようなコードは、既に計算されている値を不必要に再計算しているため、理想的ではありません。</span><span class="sxs-lookup"><span data-stu-id="de48e-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="de48e-111">これは、この記事で詳しく説明されている末尾再帰ではないためです。</span><span class="sxs-lookup"><span data-stu-id="de48e-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="de48e-112">メソッドは、それが定義されている型内で暗黙的に再帰になるため、`rec` キーワードを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="de48e-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="de48e-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="de48e-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> n
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="de48e-114">ただし、クラス内の let バインドは暗黙的に再帰ではありません。</span><span class="sxs-lookup"><span data-stu-id="de48e-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="de48e-115">すべての `let` バインド関数には `rec` キーワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="de48e-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="de48e-116">末尾再帰</span><span class="sxs-lookup"><span data-stu-id="de48e-116">Tail recursion</span></span>

<span data-ttu-id="de48e-117">再帰関数によっては、より "純粋な" 定義を[末尾再帰](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)にリファクターする必要があります。</span><span class="sxs-lookup"><span data-stu-id="de48e-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="de48e-118">これにより、不必要な再計算が防止されます。</span><span class="sxs-lookup"><span data-stu-id="de48e-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="de48e-119">たとえば、前のフィボナッチ数ジェネレーターは、次のように書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="de48e-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

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

<span data-ttu-id="de48e-120">これは、より複雑な実装です。</span><span class="sxs-lookup"><span data-stu-id="de48e-120">This is a more complicated implementation.</span></span> <span data-ttu-id="de48e-121">フィボナッチ数の生成は、数学的には純粋であるものの実際には非効率である "単純な" アルゴリズムの好例です。</span><span class="sxs-lookup"><span data-stu-id="de48e-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="de48e-122">再帰的に定義されていることに変わりないものの、次のいくつかの側面によって、F# での効率が上がります。</span><span class="sxs-lookup"><span data-stu-id="de48e-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="de48e-123">`loop` という名前の再帰的な内部関数。これは F# の慣用的なパターンです。</span><span class="sxs-lookup"><span data-stu-id="de48e-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="de48e-124">2 つのアキュムレータ パラメーター。これらは累積値を再帰呼び出しに渡します。</span><span class="sxs-lookup"><span data-stu-id="de48e-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="de48e-125">`n` の値をチェックして、特定の累積値を返します。</span><span class="sxs-lookup"><span data-stu-id="de48e-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="de48e-126">ループを使用して反復的にこの例を記述したとすると、そのコードは、特定の条件が満たされるまで 2 つの異なる数値を累積していくものになります。</span><span class="sxs-lookup"><span data-stu-id="de48e-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="de48e-127">これが末尾再帰であると言えるのは、この再帰呼び出しでは、コール スタックに値を保存する必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="de48e-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="de48e-128">計算されるすべての中間値は、内部関数への入力によって累積されます。</span><span class="sxs-lookup"><span data-stu-id="de48e-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="de48e-129">こうすれば、`while` ループのようなものを記述した場合と同様に高速になるよう、F# コンパイラでコードを最適化することもできます。</span><span class="sxs-lookup"><span data-stu-id="de48e-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="de48e-130">前の例で示したように、内部および外部関数を使用して何かを再帰的に処理する F# コードを記述するのは、一般的なことです。</span><span class="sxs-lookup"><span data-stu-id="de48e-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="de48e-131">内部関数では末尾再帰を使用しますが、外部関数は呼び出し元に対してより適切なインターフェイスを備えています。</span><span class="sxs-lookup"><span data-stu-id="de48e-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="de48e-132">相互再帰関数</span><span class="sxs-lookup"><span data-stu-id="de48e-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="de48e-133">場合によっては、関数が "*相互再帰*" になることがあります。これは呼び出しが環状になって、最初に呼び出した別の関数から、今度は自分が呼び出されることです。両者の間の呼び出し回数は任意です。</span><span class="sxs-lookup"><span data-stu-id="de48e-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="de48e-134">このような関数は、1 つの `let` バインドの中で一緒に定義し、`and` キーワードを使用してそれらをリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="de48e-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="de48e-135">次の例は、2 つの相互再帰関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="de48e-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="de48e-136">再帰的な値</span><span class="sxs-lookup"><span data-stu-id="de48e-136">Recursive values</span></span>

<span data-ttu-id="de48e-137">`let` バインドの値が再帰的になるように定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="de48e-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="de48e-138">これは、ログ記録のために行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="de48e-138">This is sometimes done for logging.</span></span> <span data-ttu-id="de48e-139">F# 5 と `nameof` 関数を使用すると、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="de48e-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="de48e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="de48e-140">See also</span></span>

- [<span data-ttu-id="de48e-141">関数</span><span class="sxs-lookup"><span data-stu-id="de48e-141">Functions</span></span>](index.md)
