---
title: F# の関数型プログラミングの概要
description: F# での関数型プログラミングの基礎について説明し ます。
ms.date: 10/29/2018
ms.openlocfilehash: 44242a4319a331312a003a555d1483f2a3f1a90d
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110586"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="44695-103">F\# の関数型プログラミングの概要</span><span class="sxs-lookup"><span data-stu-id="44695-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="44695-104">関数型プログラミングは、関数と不変のデータの使用を重視するプログラミングのスタイルです。</span><span class="sxs-lookup"><span data-stu-id="44695-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="44695-105">F# を使用するなど、関数型プログラミングが静的な型と組み合わされる場合が、型指定される関数型プログラミングです。</span><span class="sxs-lookup"><span data-stu-id="44695-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="44695-106">関数型プログラミングでは、一般に、以下の概念が重視されています。</span><span class="sxs-lookup"><span data-stu-id="44695-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="44695-107">使用する主要コンストラクトとしての関数</span><span class="sxs-lookup"><span data-stu-id="44695-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="44695-108">ステートメントの代わりの式</span><span class="sxs-lookup"><span data-stu-id="44695-108">Expressions instead of statements</span></span>
* <span data-ttu-id="44695-109">変数よりも不変の値が優先</span><span class="sxs-lookup"><span data-stu-id="44695-109">Immutable values over variables</span></span>
* <span data-ttu-id="44695-110">命令型プログラミングよりも宣言型プログラミングが優先</span><span class="sxs-lookup"><span data-stu-id="44695-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="44695-111">このシリーズを通して、F# を使用する関数型プログラミングの概念とパターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="44695-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="44695-112">その間に、F# についても多少学習します。</span><span class="sxs-lookup"><span data-stu-id="44695-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="44695-113">用語</span><span class="sxs-lookup"><span data-stu-id="44695-113">Terminology</span></span>

<span data-ttu-id="44695-114">他のプログラミング パラダイムと同様に、関数型プログラミングには、いつかは学ぶ必要がある用語があります。</span><span class="sxs-lookup"><span data-stu-id="44695-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="44695-115">ここでは、頻繁に目にすることになる一般的用語の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="44695-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="44695-116">**関数** - 関数は、入力が与えられたときに出力を生成するコンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="44695-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="44695-117">より正式には、1 つのセットから別のセットに項目を _マッピング_ するものです。</span><span class="sxs-lookup"><span data-stu-id="44695-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="44695-118">こうした形式的な点は、データのコレクションに対する操作を行う関数の使用時には特に、いろいろな意味で具体的なものに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="44695-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="44695-119">これが、関数型プログラミングにおける最も基本的 (および重要) な概念です。</span><span class="sxs-lookup"><span data-stu-id="44695-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="44695-120">**式** - 式は、値を生成するコード内のコンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="44695-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="44695-121">F# では、この値は、バインドするか明示的に無視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44695-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="44695-122">式は、関数呼び出しで普通に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="44695-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="44695-123">**純粋性** - 純粋性は、同じ引数に対しては戻り値が常に同じであり、その評価に副作用がないような関数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="44695-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="44695-124">純粋関数は、その引数に完全に左右されます。</span><span class="sxs-lookup"><span data-stu-id="44695-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="44695-125">**参照の透過性** - 参照の透過性は、プログラムの動作に影響を与えずにその出力で置き換えることができるような、式のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="44695-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="44695-126">**不変性** - 不変性とは、その位置で値を変更できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="44695-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="44695-127">これは、その位置で変化することができる変数とは対照的です。</span><span class="sxs-lookup"><span data-stu-id="44695-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="44695-128">例</span><span class="sxs-lookup"><span data-stu-id="44695-128">Examples</span></span>

<span data-ttu-id="44695-129">これらの中心概念について、以下の例で具体的に説明します。</span><span class="sxs-lookup"><span data-stu-id="44695-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="44695-130">機能</span><span class="sxs-lookup"><span data-stu-id="44695-130">Functions</span></span>

<span data-ttu-id="44695-131">関数型プログラミングの最も一般的で基礎的なコンストラクトは関数です。</span><span class="sxs-lookup"><span data-stu-id="44695-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="44695-132">次に示すのは、整数に 1 を加算する単純な関数です。</span><span class="sxs-lookup"><span data-stu-id="44695-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="44695-133">その型のシグネチャは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="44695-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="44695-134">このシグネチャは、"`addOne` は `x` という名前の `int` を受け取り、`int` を生成する" と読むことができます。</span><span class="sxs-lookup"><span data-stu-id="44695-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="44695-135">より正式には、`addOne` は整数のセットからの値を、整数のセットに _マッピング_ しています。</span><span class="sxs-lookup"><span data-stu-id="44695-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="44695-136">`->` トークンが、このマッピングを意味します。</span><span class="sxs-lookup"><span data-stu-id="44695-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="44695-137">F# では、通常、関数シグネチャを調べると、それが何を行うかが何となくわかります。</span><span class="sxs-lookup"><span data-stu-id="44695-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="44695-138">では、なぜシグネチャが重要なのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="44695-138">So, why is the signature important?</span></span> <span data-ttu-id="44695-139">型指定される関数型プログラミングでは、多くの場合、関数の実装の重要度は、実際の型シグネチャよりも低くなります。</span><span class="sxs-lookup"><span data-stu-id="44695-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="44695-140">`addOne` によって整数に値 1 を追加するという事実は実行時には重要ですが、プログラムを構築しているときには、それが `int` を受け取って返すという事実が、この関数を実際にどう使用するかを伝えることになります。</span><span class="sxs-lookup"><span data-stu-id="44695-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="44695-141">さらに、この関数を (その型のシグネチャに関して) 正しく使用すれば、`addOne` 関数の本体内だけで、すべての問題の診断を行えます。</span><span class="sxs-lookup"><span data-stu-id="44695-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="44695-142">これが、型指定される関数型プログラミングを後押しする推進力となっています。</span><span class="sxs-lookup"><span data-stu-id="44695-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="44695-143">式</span><span class="sxs-lookup"><span data-stu-id="44695-143">Expressions</span></span>

<span data-ttu-id="44695-144">式は、1 つの値へと評価されるコンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="44695-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="44695-145">アクションを実行するステートメントとは対照的に、式は、値を返すアクションを実行すると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="44695-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="44695-146">関数型プログラミングでは、ステートメントではなく式がほとんど常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="44695-146">Expressions are almost always used in functional programming instead of statements.</span></span>

<span data-ttu-id="44695-147">前の関数 `addOne` について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="44695-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="44695-148">`addOne` の本体は式です。</span><span class="sxs-lookup"><span data-stu-id="44695-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="44695-149">これはこの式の結果であり、それが `addOne` 関数の結果の型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="44695-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="44695-150">たとえば、この関数を構成する式は、`string` などの異なる型に変更できます。</span><span class="sxs-lookup"><span data-stu-id="44695-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="44695-151">これで関数のシグネチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="44695-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="44695-152">F# のどの型でもそれに対して `ToString()` を呼び出せるため、`x` の型はジェネリック ([自動ジェネリック化](../language-reference/generics/automatic-generalization.md)と呼ばれます) になり、結果の型は `string` になります。</span><span class="sxs-lookup"><span data-stu-id="44695-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="44695-153">式は、関数の本体であるだけではありません。</span><span class="sxs-lookup"><span data-stu-id="44695-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="44695-154">他の場所で使用する値を生成する式を用意できます。</span><span class="sxs-lookup"><span data-stu-id="44695-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="44695-155">一般的なものは `if` です。</span><span class="sxs-lookup"><span data-stu-id="44695-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="44695-156">`if` 式では、`result` という名前の値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="44695-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="44695-157">`result` を完全に省略し、`if` 式を `addOneIfOdd` 関数の本体にできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="44695-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="44695-158">式について覚えておく必要がある重要なことは、式によって値が生成されるという点です。</span><span class="sxs-lookup"><span data-stu-id="44695-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="44695-159">特殊な型として `unit` があります。これは、返すものがない場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="44695-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="44695-160">たとえば、次の単純な関数について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="44695-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn $"String is: {str}"
```

<span data-ttu-id="44695-161">シグネチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="44695-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="44695-162">`unit` 型は、返される実際の値がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="44695-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="44695-163">これが便利なのは、その作業の結果として返す値がなくても "作業を行う" 必要のあるルーチンがある場合です。</span><span class="sxs-lookup"><span data-stu-id="44695-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="44695-164">これは、同等の `if` コンストラクトがステートメントであり、変化する変数を使用して値が生成される場合が多い命令型プログラミングとは著しい対照をなしています。</span><span class="sxs-lookup"><span data-stu-id="44695-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="44695-165">たとえば C# では、コードは次のように記述されることがあります。</span><span class="sxs-lookup"><span data-stu-id="44695-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="44695-166">C# やその他の C スタイルの言語では、式ベースの条件付きプログラミングを可能にする[三項式](../../csharp/language-reference/operators/conditional-operator.md)がサポートされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="44695-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="44695-167">関数型プログラミングでは、ステートメントを使用して値を変化させることはまれです。</span><span class="sxs-lookup"><span data-stu-id="44695-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="44695-168">一部の関数言語ではステートメントと変化がサポートされていますが、関数型プログラミングでこれらの概念を使用するのは一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="44695-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="44695-169">純粋関数</span><span class="sxs-lookup"><span data-stu-id="44695-169">Pure functions</span></span>

<span data-ttu-id="44695-170">前に触れたように、純粋関数は次のような関数です。</span><span class="sxs-lookup"><span data-stu-id="44695-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="44695-171">同じ入力に対しては、常に同じ値に評価されます。</span><span class="sxs-lookup"><span data-stu-id="44695-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="44695-172">副作用がありません。</span><span class="sxs-lookup"><span data-stu-id="44695-172">Have no side effects.</span></span>

<span data-ttu-id="44695-173">この文脈においては、数学関数のことを考えると参考になります。</span><span class="sxs-lookup"><span data-stu-id="44695-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="44695-174">数学では、関数は引数にのみ依存しており、副作用は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="44695-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="44695-175">数学関数 `f(x) = x + 1` では、`f(x)` の値は `x` の値にのみ左右されます。</span><span class="sxs-lookup"><span data-stu-id="44695-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="44695-176">関数型プログラミングの純粋関数も同様です。</span><span class="sxs-lookup"><span data-stu-id="44695-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="44695-177">純粋関数の記述時には、関数はその引数にのみ依存し、副作用が発生するアクションを実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="44695-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="44695-178">次は、グローバルで変更可能な状態に依存しているため、非純粋関数の例です。</span><span class="sxs-lookup"><span data-stu-id="44695-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="44695-179">`addOneToValue` 関数は明確に純粋ではありません。`value` は、いつでも 1 とは異なる値に変更できるためです。</span><span class="sxs-lookup"><span data-stu-id="44695-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="44695-180">グローバルな値に依存するこのパターンは、関数型プログラミングでは回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44695-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="44695-181">次は、副作用が実行されるため、非純粋関数の別の例となっています。</span><span class="sxs-lookup"><span data-stu-id="44695-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn $"x is %d{x}"
    x + 1
```

<span data-ttu-id="44695-182">この関数はグローバルな値に依存していませんが、`x` の値をプログラムの出力に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="44695-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="44695-183">これを行うことに本質的な問題はありませんが、関数は確かに純粋ではないことになります。</span><span class="sxs-lookup"><span data-stu-id="44695-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="44695-184">プログラムの別の部分が、出力バッファーなど、プログラム外部の何かに依存している場合は、この関数を呼び出すと、プログラムのそうした他の部分に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44695-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="44695-185">`printfn` ステートメントを削除すると、この関数は純粋になります。</span><span class="sxs-lookup"><span data-stu-id="44695-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="44695-186">この関数は、`printfn` ステートメントを含む前のバージョンよりも本質的に _優れている_ わけではありませんが、この関数で行うのは値を返すことがすべてであることが確かに保証されます。</span><span class="sxs-lookup"><span data-stu-id="44695-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="44695-187">この関数を何度呼び出しても同じ結果が生成されます。ただ値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="44695-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="44695-188">純粋性によって得られる予測可能性は、多くの関数プログラマが得ようと努めているものです。</span><span class="sxs-lookup"><span data-stu-id="44695-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="44695-189">不変性</span><span class="sxs-lookup"><span data-stu-id="44695-189">Immutability</span></span>

<span data-ttu-id="44695-190">最後に挙げる、型指定される関数型プログラミングの最も基本的な概念の 1 つは不変性です。</span><span class="sxs-lookup"><span data-stu-id="44695-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="44695-191">F# では、既定ですべての値が不変です。</span><span class="sxs-lookup"><span data-stu-id="44695-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="44695-192">つまり、明示的に変更可能とマークしない限り、これらをインプレースで変化させることはできません。</span><span class="sxs-lookup"><span data-stu-id="44695-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="44695-193">実際には、変更できない値を使用して作業することは、プログラミングに対するアプローチを、"私は何かを変更する必要があります" から、"私は新しい値を生成する必要があります" に変えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="44695-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="44695-194">たとえば、値に 1 を追加することは、既存の値を変更することではなく、新しい値を生成することを意味します。</span><span class="sxs-lookup"><span data-stu-id="44695-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="44695-195">F# では、次のコードで `value` 関数は変更され **ません**。代わりに、等価性チェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="44695-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="44695-196">一部の関数型プログラミング言語では、変化が一切サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="44695-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="44695-197">F# ではサポートされていますが、値についての既定の動作ではありません。</span><span class="sxs-lookup"><span data-stu-id="44695-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="44695-198">この概念はさらに、データ構造にさえ拡張されています。</span><span class="sxs-lookup"><span data-stu-id="44695-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="44695-199">関数型プログラミングでは、セット (やさらに多くのもの) などの変更できないデータ構造の実装は、最初に予期したのとは異なるものになります。</span><span class="sxs-lookup"><span data-stu-id="44695-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="44695-200">概念上、セットに項目を 1 つ追加するなどのことではセットは変更されません。追加された値を含む _新しい_ セットが生成されるのです。</span><span class="sxs-lookup"><span data-stu-id="44695-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="44695-201">内部的には、これは多くの場合、結果としてデータの適切な表現が得られるように、値の効率的な追跡を可能にする異なるデータ構造によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="44695-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="44695-202">このスタイルでの値とデータ構造の操作は、何かを変更するすべての操作を、それの新しいバージョンを作成するかのように扱うことが求められるため、非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="44695-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="44695-203">これで、プログラム内で等価性や比較可能性のようなことがらの一貫性を保てます。</span><span class="sxs-lookup"><span data-stu-id="44695-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="44695-204">次のステップ</span><span class="sxs-lookup"><span data-stu-id="44695-204">Next steps</span></span>

<span data-ttu-id="44695-205">次のセクションでは、関数型プログラミングで使用できるさまざまな方法を紹介しながら、関数について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="44695-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="44695-206">「[ファーストクラス関数](first-class-functions.md)」では、関数について深く掘り下げて、さまざまなコンテキストでそれらを使用できる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="44695-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="44695-207">参考資料</span><span class="sxs-lookup"><span data-stu-id="44695-207">Further reading</span></span>

<span data-ttu-id="44695-208">「[関数型での思考](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/)」シリーズは、F# を使用した関数型プログラミングについて学習するもう 1 つの優れたリソースです。</span><span class="sxs-lookup"><span data-stu-id="44695-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="44695-209">関数型プログラミングの基礎について、F# の機能を使用して概念を説明し、実用的で読みやすい方法で解説します。</span><span class="sxs-lookup"><span data-stu-id="44695-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
