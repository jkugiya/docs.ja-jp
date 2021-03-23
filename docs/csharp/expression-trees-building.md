---
title: 式ツリーの構築
description: 式ツリーを構築するためのテクニックについて説明します。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: f6752879dc01080e056221b00ca5377a6abc20db
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875812"
---
# <a name="building-expression-trees"></a><span data-ttu-id="6443a-103">式ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="6443a-103">Building Expression Trees</span></span>

[<span data-ttu-id="6443a-104">前回 -- 式の解釈</span><span class="sxs-lookup"><span data-stu-id="6443a-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="6443a-105">これまでに説明した式ツリーは、いずれも C# コンパイラで作成したものです。</span><span class="sxs-lookup"><span data-stu-id="6443a-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="6443a-106">`Expression<Func<T>>` や他の同様の型として型指定された変数に割り当てるラムダ式を作成するだけの手順でしたが、</span><span class="sxs-lookup"><span data-stu-id="6443a-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="6443a-107">式ツリーを作成する方法は他にもあります。</span><span class="sxs-lookup"><span data-stu-id="6443a-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="6443a-108">実行時にメモリ内で式を構築する必要があるというシナリオはよくあります。</span><span class="sxs-lookup"><span data-stu-id="6443a-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="6443a-109">式ツリーは不変なので、式ツリーの構築は複雑です。</span><span class="sxs-lookup"><span data-stu-id="6443a-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="6443a-110">不変とは、リーフからルートにいたるまでツリーを構築する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6443a-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="6443a-111">式ツリーの構築に使用する API がこれを反映しています。ノードの構築に使用するメソッドは、そのすべての子を引数として取得します。</span><span class="sxs-lookup"><span data-stu-id="6443a-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="6443a-112">いくつかの例を挙げながら手法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6443a-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="6443a-113">ノードの作成</span><span class="sxs-lookup"><span data-stu-id="6443a-113">Creating Nodes</span></span>

<span data-ttu-id="6443a-114">比較的単純な例から始めましょう。</span><span class="sxs-lookup"><span data-stu-id="6443a-114">Let's start relatively simply again.</span></span> <span data-ttu-id="6443a-115">これまでに使用してきた加算式を使用します。</span><span class="sxs-lookup"><span data-stu-id="6443a-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="6443a-116">式ツリーを構築するには、リーフ ノードを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6443a-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="6443a-117">リーフ ノードは定数なので、`Expression.Constant` メソッドを使用してノードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6443a-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="6443a-118">次に、加算式を構築します。</span><span class="sxs-lookup"><span data-stu-id="6443a-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="6443a-119">加算式を構築したら、ラムダ式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6443a-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="6443a-120">引数がないので、これはとても単純なラムダ式です。</span><span class="sxs-lookup"><span data-stu-id="6443a-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="6443a-121">このセクションの後半では、引数をパラメーターにマップし、より複雑な式を構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6443a-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="6443a-122">この例のように単純な式の場合、すべての呼び出しを 1 つのステートメントにまとめることもできます。</span><span class="sxs-lookup"><span data-stu-id="6443a-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="6443a-123">ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="6443a-123">Building a Tree</span></span>

<span data-ttu-id="6443a-124">メモリ内に式ツリーを構築する基本的な方法です。</span><span class="sxs-lookup"><span data-stu-id="6443a-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="6443a-125">一般的に、複雑なツリーの場合はノードの種類が多く、ツリー内のノード数も多くなります。</span><span class="sxs-lookup"><span data-stu-id="6443a-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="6443a-126">もう 1 つの例を使って、式ツリーを作成するときに一般的に構築する 2 つのノードについて説明します。引数ノードとメソッド呼び出しノードです。</span><span class="sxs-lookup"><span data-stu-id="6443a-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="6443a-127">式ツリーを構築して次の式を作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="6443a-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="6443a-128">まず `x` と `y` のパラメーター式を作成します。</span><span class="sxs-lookup"><span data-stu-id="6443a-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="6443a-129">乗算式と加算式の作成方法は、これまでに説明したパターンどおりです。</span><span class="sxs-lookup"><span data-stu-id="6443a-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="6443a-130">次に、`Math.Sqrt` の呼び出しのために、メソッド呼び出し式を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6443a-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="6443a-131">最後に、メソッド呼び出しをラムダ式に組み込み、忘れずにラムダ式の引数を定義します。</span><span class="sxs-lookup"><span data-stu-id="6443a-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="6443a-132">このやや複雑な例では、式ツリーの作成に必要になることが多い手法がいくつか見られます。</span><span class="sxs-lookup"><span data-stu-id="6443a-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="6443a-133">まず、パラメーターまたはローカル変数を表すオブジェクトは、使用前に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="6443a-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="6443a-134">オブジェクトの作成後は、式ツリーのどこでも必要な場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6443a-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="6443a-135">次に、`MethodInfo` オブジェクトを作成するには、リフレクション API の一部を使用する必要があります。これは、そのメソッドにアクセスする式ツリーを作成できるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="6443a-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="6443a-136">使用するリフレクション API は、.NET Core プラットフォームで使用できるものに限定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6443a-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="6443a-137">繰り返しになりますが、こうした手法は他の式ツリーにも応用されます。</span><span class="sxs-lookup"><span data-stu-id="6443a-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="6443a-138">コードの構築の詳細</span><span class="sxs-lookup"><span data-stu-id="6443a-138">Building Code In Depth</span></span>

<span data-ttu-id="6443a-139">このような API を使用して構築できるものに制限はありませんが、</span><span class="sxs-lookup"><span data-stu-id="6443a-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="6443a-140">構築する式ツリーが複雑になるほど、コードの管理と読み取りが困難になります。</span><span class="sxs-lookup"><span data-stu-id="6443a-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="6443a-141">このコードと同じ式ツリーを構築してみましょう。</span><span class="sxs-lookup"><span data-stu-id="6443a-141">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="6443a-142">上の例では、式ツリーを構築せず、デリゲートのみを構築しました。</span><span class="sxs-lookup"><span data-stu-id="6443a-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="6443a-143">`Expression` クラスを使用して、ステートメント形式のラムダを構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="6443a-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="6443a-144">同じ機能を構築するために必要なコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6443a-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="6443a-145">この例が複雑なのは、`while` ループを構築する API がなく、条件テストを含むループと、ループを抜けるためのラベル ターゲットを構築する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="6443a-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="6443a-146">階乗関数の式ツリーを構築するコードは、かなり長く複雑になります。また、通常のコーディング作業では避けたいラベルや break ステートメントなどの要素が多くなってしまいます。</span><span class="sxs-lookup"><span data-stu-id="6443a-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="6443a-147">このセクションでは、この式ツリーのすべてのノードにアクセスするビジター コードも更新し、このサンプルで作成したノードに関する情報を書き出しました。</span><span class="sxs-lookup"><span data-stu-id="6443a-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="6443a-148">GitHub の dotnet/docs レポジトリで、[サンプル コードを表示またはダウンロード](https://github.com/dotnet/samples/tree/main/csharp/expression-trees)することができます。</span><span class="sxs-lookup"><span data-stu-id="6443a-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/main/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="6443a-149">自分でサンプルをビルドし、実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="6443a-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="6443a-150">ダウンロード方法については、「[サンプルおよびチュートリアル](../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6443a-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="6443a-151">API の確認</span><span class="sxs-lookup"><span data-stu-id="6443a-151">Examining the APIs</span></span>

<span data-ttu-id="6443a-152">.NET Core では、式ツリーの API をたどることがやや難しくはありますが、問題ありません。</span><span class="sxs-lookup"><span data-stu-id="6443a-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="6443a-153">その目的は、実行時にコードを生成するコードを作成するという、かなり複雑な作業だからです。</span><span class="sxs-lookup"><span data-stu-id="6443a-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="6443a-154">C# 言語で使用できるすべてのコントロール構造体をサポートしながら、API のアクセス領域をできるだけ少なくするバランスを取るため、必然的に複雑な作業になります。</span><span class="sxs-lookup"><span data-stu-id="6443a-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="6443a-155">このバランスとは、多くのコントロール構造体は、C# コンストラクトではなく、上位のコンストラクトからコンパイラが生成する基のロジックを示すコンストラクトで表されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6443a-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="6443a-156">また、現時点では、`Expression` クラス メソッドを使用して直接構築できない C# 式があります。</span><span class="sxs-lookup"><span data-stu-id="6443a-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="6443a-157">一般的に、C# 5 と C# 6 で追加された最新の演算子と式です</span><span class="sxs-lookup"><span data-stu-id="6443a-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="6443a-158">(たとえば、`async` は構築できず、新しい `?.` 演算子は直接作成できません)。</span><span class="sxs-lookup"><span data-stu-id="6443a-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="6443a-159">次回 -- 式の変換</span><span class="sxs-lookup"><span data-stu-id="6443a-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
