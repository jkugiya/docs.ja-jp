---
title: コンピュテーション式
description: 制御フローのコンストラクトとバインドを使用してシーケンス化および結合できる F# の計算を記述するための便利な構文の作成方法について説明します。
ms.date: 08/15/2020
f1_keywords:
- let!_FS
ms.openlocfilehash: a0a71533ea1bc87b75f028ad0d416326f627672a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739305"
---
# <a name="computation-expressions"></a><span data-ttu-id="b13c0-103">コンピュテーション式</span><span class="sxs-lookup"><span data-stu-id="b13c0-103">Computation Expressions</span></span>

<span data-ttu-id="b13c0-104">F# のコンピュテーション式には、制御フローのコンストラクトとバインドを使用してシーケンス化および結合できる計算を記述するための便利な構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b13c0-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="b13c0-105">コンピュテーション式は、その種類に応じて、モナド、モノイド、モナド変換子、およびアプリカティブ ファンクターを表現する方法と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="b13c0-106">ただし、他の言語 (Haskell の *do-notation* など) とは異なり、それらは 1 つの抽象化に関連付けられておらず、便利な状況依存の構文を実現するためにマクロやその他の形式のメタプログラミングに依存しません。</span><span class="sxs-lookup"><span data-stu-id="b13c0-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="b13c0-107">概要</span><span class="sxs-lookup"><span data-stu-id="b13c0-107">Overview</span></span>

<span data-ttu-id="b13c0-108">計算にはさまざまな形式があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-108">Computations can take many forms.</span></span> <span data-ttu-id="b13c0-109">計算の最も一般的な形式は、理解と変更が簡単なシングルスレッド実行です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="b13c0-110">ただし、すべての形式の計算がシングルスレッド実行ほど単純であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b13c0-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="b13c0-111">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-111">Some examples include:</span></span>

- <span data-ttu-id="b13c0-112">非決定的な計算</span><span class="sxs-lookup"><span data-stu-id="b13c0-112">Non-deterministic computations</span></span>
- <span data-ttu-id="b13c0-113">非同期計算</span><span class="sxs-lookup"><span data-stu-id="b13c0-113">Asynchronous computations</span></span>
- <span data-ttu-id="b13c0-114">有効計算</span><span class="sxs-lookup"><span data-stu-id="b13c0-114">Effectful computations</span></span>
- <span data-ttu-id="b13c0-115">生成的計算</span><span class="sxs-lookup"><span data-stu-id="b13c0-115">Generative computations</span></span>

<span data-ttu-id="b13c0-116">より一般には、アプリケーションの特定の部分で実行する必要がある "*状況依存*" の計算があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="b13c0-117">状況依存のコードを記述することは難しい場合があります。これは、抽象化によって回避しないと特定のコンテキストの外部に計算が "リーク" しやすいからです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="b13c0-118">多くの場合、これらの抽象化は自分で記述することが困難です。そのため、F# には **コンピュテーション式** と呼ばれる汎用的な方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b13c0-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="b13c0-119">コンピュテーション式により、状況依存の計算をエンコードするための統一された構文と抽象化モデルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="b13c0-120">すべてのコンピュテーション式は、"*ビルダー*" 型によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="b13c0-121">ビルダー型により、コンピュテーション式で使用できる操作が定義されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="b13c0-122">カスタム コンピュテーション式の作成方法を示している「[コンピュテーション式の新しい型の作成](computation-expressions.md#creating-a-new-type-of-computation-expression)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b13c0-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="b13c0-123">構文の概要</span><span class="sxs-lookup"><span data-stu-id="b13c0-123">Syntax overview</span></span>

<span data-ttu-id="b13c0-124">すべてのコンピュテーション式の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="b13c0-125">ここで、`builder-expr` はコンピュテーション式を定義するビルダー型の名前、`cexper` はコンピュテーション式の式本体です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="b13c0-126">たとえば、`async` コンピュテーション式のコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="b13c0-127">前の例で示したように、コンピュテーション式内で使用できる特殊な追加の構文があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="b13c0-128">コンピュテーション式では、次の形式の式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="b13c0-129">これらの各キーワードおよびその他の標準 F# キーワードは、バッキング ビルダー型で定義されている場合にのみ、コンピュテーション式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="b13c0-130">これに対する唯一の例外は `match!` です。これ自体は、`let!` に続いて結果に対するパターン マッチを使用するための糖衣構文です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="b13c0-131">ビルダー型は、コンピュテーション式のフラグメントの結合方法を制御する特殊なメソッドを定義するオブジェクトです。つまり、そのメソッドによって、コンピュテーション式の動作が制御されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="b13c0-132">ビルダー クラスは、ループやバインドなど、多くの F# コンストラクトの操作をカスタマイズできるようにするものとして説明することもできます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="b13c0-133">`let!` キーワードにより、別のコンピュテーション式の呼び出し結果が名前にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="b13c0-134">`let` を使用してコンピュテーション式の呼び出しをバインドすると、コンピュテーション式の結果は得られません。</span><span class="sxs-lookup"><span data-stu-id="b13c0-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="b13c0-135">代わりに、そのコンピュテーション式に対する "*実現されていない*" 呼び出しの値がバインドされます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="b13c0-136">`let!` を使用して結果にバインドします。</span><span class="sxs-lookup"><span data-stu-id="b13c0-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="b13c0-137">`let!` は、ビルダー型の `Bind(x, f)` メンバーによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="b13c0-138">`do!` キーワードは、`unit` のような型 (ビルダーで `Zero` メンバーによって定義される) を返すコンピュテーション式を呼び出すためのものです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="b13c0-139">[非同期ワークフロー](asynchronous-workflows.md)の場合、この型は `Async<unit>` です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="b13c0-140">その他のコンピュテーション式の場合、型は `CExpType<unit>` になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="b13c0-141">`do!` は、ビルダー型の `Bind(x, f)` メンバーによって定義されます。ここで、`f` によって `unit` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="b13c0-142">`yield` キーワードは、コンピュテーション式から値を返して、<xref:System.Collections.Generic.IEnumerable%601> として使用できるようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn $"%d{sq}"
```

<span data-ttu-id="b13c0-143">ほとんどの場合、呼び出し元では省略できます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="b13c0-144">`yield` を省略する最も一般的な方法は、`->` 演算子を使用することです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn $"%d{sq}"
```

<span data-ttu-id="b13c0-145">多くの異なる値を生成する可能性がある複雑な式の場合、場合によってはキーワードを省略するだけで、次のことが可能です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

<span data-ttu-id="b13c0-146">[C# の yield キーワード](../../csharp/language-reference/keywords/yield.md)の場合と同様に、コンピュテーション式の各要素は反復処理されるときに返されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="b13c0-147">`yield` は、ビルダー型の `Yield(x)` メンバーによって定義されます。ここで、`x` は返す項目です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="b13c0-148">`yield!` キーワードは、コンピュテーション式からの値のコレクションをフラット化するためのものです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn $"{squaresAndCubes}"  // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="b13c0-149">評価されると、`yield!` によって呼び出されるコンピュテーション式の項目が 1 つずつ返され、結果がフラット化されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="b13c0-150">`yield!` は、ビルダー型の `YieldFrom(x)` メンバーによって定義されます。ここで、`x` は値のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="b13c0-151">`yield` とは異なり、`yield!` は明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="b13c0-152">コンピュテーション式では、その動作は暗黙的ではありません。</span><span class="sxs-lookup"><span data-stu-id="b13c0-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="b13c0-153">`return` キーワードにより、コンピュテーション式に対応する型に値がラップされます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="b13c0-154">`yield` を使用したコンピュテーション式とは別に、コンピュテーション式を "完了" するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="b13c0-155">`return` は、ビルダー型の `Return(x)` メンバーによって定義されます。ここで、`x` はラップする項目です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="b13c0-156">`return!` キーワードにより、コンピュテーション式の値が認識され、その結果がコンピュテーション式に対応する型にラップされます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="b13c0-157">`return!` は、ビルダー型の `ReturnFrom(x)` メンバーによって定義されます。ここで、`x` は別のコンピュテーション式です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="b13c0-158">`match!` キーワードを使用すると、呼び出しを別のコンピュテーション式にインライン化し、結果のパターン マッチを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="b13c0-159">`match!` を使用してコンピュテーション式を呼び出すと、`let!` のような呼び出しの結果が認識されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="b13c0-160">通常、これは、結果が[省略可能](options.md)であるコンピュテーション式を呼び出すときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="b13c0-161">組み込みのコンピュテーション式</span><span class="sxs-lookup"><span data-stu-id="b13c0-161">Built-in computation expressions</span></span>

<span data-ttu-id="b13c0-162">F# コア ライブラリには、[シーケンス式](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、[クエリ式](query-expressions.md)という 3 つの組み込みのコンピュテーション式が定義されています。</span><span class="sxs-lookup"><span data-stu-id="b13c0-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="b13c0-163">新しい種類のコンピュテーション式の作成</span><span class="sxs-lookup"><span data-stu-id="b13c0-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="b13c0-164">ビルダー クラスを作成し、そのクラスに特定の特殊なメソッドを定義することで、独自のコンピュテーション式の特性を定義できます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="b13c0-165">ビルダー クラスでは、次の表に示すように、必要に応じてメソッドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="b13c0-166">次の表では、ワークフロー ビルダー クラスで使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="b13c0-167">**方法**</span><span class="sxs-lookup"><span data-stu-id="b13c0-167">**Method**</span></span>|<span data-ttu-id="b13c0-168">**一般的なシグネチャ**</span><span class="sxs-lookup"><span data-stu-id="b13c0-168">**Typical signature(s)**</span></span>|<span data-ttu-id="b13c0-169">**説明**</span><span class="sxs-lookup"><span data-stu-id="b13c0-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="b13c0-170">コンピュテーション式で `let!` および `do!` に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="b13c0-171">コンピュテーション式を関数としてラップします。</span><span class="sxs-lookup"><span data-stu-id="b13c0-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="b13c0-172">コンピュテーション式で `return` に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="b13c0-173">コンピュテーション式で `return!` に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="b13c0-174">`M<'T> -> M<'T>` または</span><span class="sxs-lookup"><span data-stu-id="b13c0-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="b13c0-175">コンピュテーション式を実行します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="b13c0-176">`M<'T> * M<'T> -> M<'T>` または</span><span class="sxs-lookup"><span data-stu-id="b13c0-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="b13c0-177">コンピュテーション式でシーケンス処理を行うために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="b13c0-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` または</span><span class="sxs-lookup"><span data-stu-id="b13c0-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="b13c0-179">コンピュテーション式の `for...do` 式に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="b13c0-180">コンピュテーション式の `try...finally` 式に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="b13c0-181">コンピュテーション式の `try...with` 式に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="b13c0-182">コンピュテーション式の `use` バインディングに対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="b13c0-183">コンピュテーション式の `while...do` 式に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="b13c0-184">コンピュテーション式の `yield` 式に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="b13c0-185">コンピュテーション式の `yield!` 式に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="b13c0-186">コンピュテーション式の `if...then` 式の空の `else` 分岐に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="b13c0-187">コンピュテーション式が `Run` メンバーに引用符として渡されることを示します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="b13c0-188">計算のすべてのインスタンスを引用符に変換します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="b13c0-189">ビルダー クラスのメソッドの多くは、`M<'T>` コンストラクトを使用して返します。通常、これは非同期ワークフローに対する `Async<'T>` やシーケンス ワークフローに対する `Seq<'T>` など、結合される計算の種類を特徴付ける個別に定義された型です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="b13c0-190">これらのメソッドのシグネチャを使用すると、1 つのコンストラクトから返されるワークフロー オブジェクトを次のものに渡すことができるように、それらを組み合わせて入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="b13c0-191">コンパイラでは、コンピュテーション式を解析するときに、前の表のメソッドとコンピュテーション式内のコードを使用して、式が一連の入れ子になった関数呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="b13c0-192">入れ子になった式の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b13c0-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="b13c0-193">上記のコードで、`Run` と `Delay` は、コンピュテーション式ビルダー クラス内で定義されていない場合に省略されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="b13c0-194">ここでは `{| cexpr |}` と示されているコンピュテーション式の本体は、次の表で説明する変換によって、ビルダー クラスのメソッドを含む呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="b13c0-195">コンピュテーション式 `{| cexpr |}` は、これらの変換に従って再帰的に定義されます。ここで、`expr` は F# の式で、`cexpr` はコンピュテーション式です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="b13c0-196">式</span><span class="sxs-lookup"><span data-stu-id="b13c0-196">Expression</span></span>|<span data-ttu-id="b13c0-197">翻訳</span><span class="sxs-lookup"><span data-stu-id="b13c0-197">Translation</span></span>|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

<span data-ttu-id="b13c0-198">前の表では、`other-expr` は表に記載されていない式について説明しています。</span><span class="sxs-lookup"><span data-stu-id="b13c0-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="b13c0-199">ビルダー クラスでは、必ずしもすべてのメソッドを実装する必要はなく、前の表に一覧表示されているすべての変換がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="b13c0-200">実装されていないコンストラクトは、その型のコンピュテーション式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="b13c0-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="b13c0-201">たとえば、コンピュテーション式内で `use` キーワードをサポートしない場合は、ビルダー クラス内で `Use` の定義を省略できます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="b13c0-202">次のコード例は、一度に 1 ステップずつ評価できる一連のステップとして計算をカプセル化するコンピュテーション式を示しています。</span><span class="sxs-lookup"><span data-stu-id="b13c0-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="b13c0-203">判別共用体型である `OkOrException` により、これまでに評価された式のエラー状態がエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="b13c0-204">このコードは、一部のビルダー メソッドの定型実装など、コンピュテーション式内で使用できるいくつかの一般的なパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="b13c0-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn $" x = %d{x}"
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

<span data-ttu-id="b13c0-205">コンピュテーション式には、式によって返される基になる型があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="b13c0-206">基になる型では、計算された結果または実行可能な遅延計算を表すことができます。また、一部のコレクション型を反復処理する方法が提供される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="b13c0-207">前の例では、基になる型は **Eventually** でした。</span><span class="sxs-lookup"><span data-stu-id="b13c0-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="b13c0-208">シーケンス式の場合、基になる型は <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b13c0-209">クエリ式の場合、基になる型は <xref:System.Linq.IQueryable?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b13c0-210">非同期ワークフローの場合、基になる型は [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html) です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-210">For an asynchronous workflow, the underlying type is [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html).</span></span> <span data-ttu-id="b13c0-211">`Async` オブジェクトは、結果を計算するために実行する作業を表します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="b13c0-212">たとえば、[`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) を呼び出して計算を実行し、その結果を返します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-212">For example, you call [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="b13c0-213">カスタム操作</span><span class="sxs-lookup"><span data-stu-id="b13c0-213">Custom Operations</span></span>

<span data-ttu-id="b13c0-214">コンピュテーション式に対してカスタム操作を定義し、コンピュテーション式内でカスタム操作を演算子として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="b13c0-215">たとえば、クエリ式にクエリ演算子を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="b13c0-216">カスタム操作を定義する場合は、コンピュテーション式で Yield および For メソッドを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="b13c0-217">カスタム操作を定義するには、それをコンピュテーション式のビルダー クラスに配置し、[`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html) を適用します。</span><span class="sxs-lookup"><span data-stu-id="b13c0-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html).</span></span> <span data-ttu-id="b13c0-218">この属性は、文字列を引数として受け取ります。これはカスタム操作で使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="b13c0-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="b13c0-219">この名前は、コンピュテーション式の左中かっこの先頭にあるスコープに含まれます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="b13c0-220">したがって、このブロック内ではカスタム操作と同じ名前を持つ識別子は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b13c0-220">Therefore, you shouldn't use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="b13c0-221">たとえば、クエリ式で `all` や `last` などの識別子を使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="b13c0-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="b13c0-222">新しいカスタム操作を使用した既存のビルダーの拡張</span><span class="sxs-lookup"><span data-stu-id="b13c0-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="b13c0-223">既にビルダー クラスがある場合は、そのカスタム操作をこのビルダー クラスの外部から拡張できます。</span><span class="sxs-lookup"><span data-stu-id="b13c0-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="b13c0-224">拡張はモジュール内で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b13c0-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="b13c0-225">名前空間には、同じファイルと、型が定義されている同じ名前空間宣言グループを除き、拡張メンバーを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="b13c0-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="b13c0-226">次の例は、既存の `FSharp.Linq.QueryBuilder` クラスの拡張を示しています。</span><span class="sxs-lookup"><span data-stu-id="b13c0-226">The following example shows the extension of the existing `FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="b13c0-227">関連項目</span><span class="sxs-lookup"><span data-stu-id="b13c0-227">See also</span></span>

- [<span data-ttu-id="b13c0-228">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="b13c0-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b13c0-229">非同期ワークフロー</span><span class="sxs-lookup"><span data-stu-id="b13c0-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="b13c0-230">シーケンス</span><span class="sxs-lookup"><span data-stu-id="b13c0-230">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="b13c0-231">クエリ式</span><span class="sxs-lookup"><span data-stu-id="b13c0-231">Query Expressions</span></span>](query-expressions.md)
