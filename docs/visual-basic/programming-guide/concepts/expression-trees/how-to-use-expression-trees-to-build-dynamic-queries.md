---
title: 実行時の状態に基づくクエリの実行 (Visual Basic)
description: LINQ メソッドの呼び出し、またはこれらのメソッドに渡される式ツリーを変更することにより、コードで実行時の状態に応じて動的にクエリを実行するために使用できるさまざまな手法について説明します。
ms.date: 02/14/2021
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: c9f57950b2c26c0cca798ab632da90bf9f6c519a
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584844"
---
# <a name="querying-based-on-runtime-state-visual-basic"></a><span data-ttu-id="c49e1-103">実行時の状態に基づくクエリの実行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c49e1-103">Querying based on runtime state (Visual Basic)</span></span>

<span data-ttu-id="c49e1-104">データ ソースに対して <xref:System.Linq.IQueryable> または [IQueryable(Of T)](<xref:System.Linq.IQueryable%601>) が定義されているコードについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-104">Consider code that defines an <xref:System.Linq.IQueryable> or an [IQueryable(Of T)](<xref:System.Linq.IQueryable%601>) against a data source:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Initialize":::

<span data-ttu-id="c49e1-105">このコードを実行するたびに、同じクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-105">Every time you run this code, the same exact query will be executed.</span></span> <span data-ttu-id="c49e1-106">実行時の状態に応じてさまざまなクエリを実行するコードが必要になる可能性があるため、これは多くの場合、あまり役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="c49e1-106">This is frequently not very useful, as you may want your code to execute different queries depending on conditions at runtime.</span></span> <span data-ttu-id="c49e1-107">この記事では、実行時の状態に基づいて別のクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c49e1-107">This article describes how you can execute a different query based on runtime state.</span></span>

## <a name="iqueryable--iqueryableof-t-and-expression-trees"></a><span data-ttu-id="c49e1-108">IQueryable または IQueryable(Of T) と式ツリー</span><span class="sxs-lookup"><span data-stu-id="c49e1-108">IQueryable / IQueryable(Of T) and expression trees</span></span>

<span data-ttu-id="c49e1-109">基本的に、<xref:System.Linq.IQueryable> には次の 2 つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-109">Fundamentally, an <xref:System.Linq.IQueryable> has two components:</span></span>

* <span data-ttu-id="c49e1-110"><xref:System.Linq.IQueryable.Expression> &mdash; 式ツリーの形式である、現在のクエリのコンポーネントの言語およびデータソースに依存しない表現。</span><span class="sxs-lookup"><span data-stu-id="c49e1-110"><xref:System.Linq.IQueryable.Expression>&mdash;a language- and datasource-agnostic representation of the current query's components, in the form of an expression tree.</span></span>
* <span data-ttu-id="c49e1-111"><xref:System.Linq.IQueryable.Provider> &mdash; 現在のクエリを値または値のセットに具体化する方法を認識している LINQ プロバイダーのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="c49e1-111"><xref:System.Linq.IQueryable.Provider>&mdash;an instance of a LINQ provider, which knows how to materialize the current query into a value or set of values.</span></span>

<span data-ttu-id="c49e1-112">動的なクエリのコンテキストでは、通常、プロバイダーは同じままとなります。クエリの式ツリーはクエリによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-112">In the context of dynamic querying, the provider will usually remain the same; the expression tree of the query will differ from query to query.</span></span>

<span data-ttu-id="c49e1-113">式ツリーは変更できません。別の式ツリー &mdash; したがって、別のクエリ &mdash; が必要な場合は、既存の式ツリーを新しいもの (したがって、新しい <xref:System.Linq.IQueryable>) に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-113">Expression trees are immutable; if you want a different expression tree&mdash;and thus a different query&mdash;you'll need to translate the existing expression tree to a new one, and thus to a new <xref:System.Linq.IQueryable>.</span></span>

<span data-ttu-id="c49e1-114">次のセクションでは、実行時の状態に応じて異なる方法でクエリを実行する特定の手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c49e1-114">The following sections describe specific techniques for querying differently in response to runtime state:</span></span>

- <span data-ttu-id="c49e1-115">式ツリー内から実行時の状態を使用する</span><span class="sxs-lookup"><span data-stu-id="c49e1-115">Use runtime state from within the expression tree</span></span>
- <span data-ttu-id="c49e1-116">追加の LINQ メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="c49e1-116">Call additional LINQ methods</span></span>
- <span data-ttu-id="c49e1-117">LINQ メソッドに渡される式ツリーを変更する</span><span class="sxs-lookup"><span data-stu-id="c49e1-117">Vary the expression tree passed into the LINQ methods</span></span>
- <span data-ttu-id="c49e1-118"><xref:System.Linq.Expressions.Expression> でファクトリ メソッドを使用して、[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) 式ツリー式を作成する</span><span class="sxs-lookup"><span data-stu-id="c49e1-118">Construct an [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) expression tree using the factory methods at <xref:System.Linq.Expressions.Expression></span></span>
- <span data-ttu-id="c49e1-119"><xref:System.Linq.IQueryable> の式ツリーにメソッド呼び出しノードを追加する</span><span class="sxs-lookup"><span data-stu-id="c49e1-119">Add method call nodes to an <xref:System.Linq.IQueryable>'s expression tree</span></span>
- <span data-ttu-id="c49e1-120">文字列を構築し、[動的 LINQ ライブラリ](https://dynamic-linq.net/)を使用する</span><span class="sxs-lookup"><span data-stu-id="c49e1-120">Construct strings, and use the [Dynamic LINQ library](https://dynamic-linq.net/)</span></span>

## <a name="use-runtime-state-from-within-the-expression-tree"></a><span data-ttu-id="c49e1-121">式ツリー内から実行時の状態を使用する</span><span class="sxs-lookup"><span data-stu-id="c49e1-121">Use runtime state from within the expression tree</span></span>

<span data-ttu-id="c49e1-122">LINQ プロバイダーでサポートされていると仮定した場合にクエリを動的に実行する最も簡単な方法は、次のコード例の `length` など、閉じ込められた変数を使用して、クエリ内の実行時の状態を直接参照することです。</span><span class="sxs-lookup"><span data-stu-id="c49e1-122">Assuming the LINQ provider supports it, the simplest way to query dynamically is to reference the runtime state directly in the query via a closed-over variable, such as `length` in the following code example:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Runtime_state_from_within_expression_tree":::

<span data-ttu-id="c49e1-123">内部式ツリー &mdash;したがって、クエリ&mdash; は変更されていません。このクエリの場合は、`length` の値が変更されているため、異なる値が返されます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-123">The internal expression tree&mdash;and thus the query&mdash;haven't been modified; the query returns different values only because the value of `length` has been changed.</span></span>

## <a name="call-additional-linq-methods"></a><span data-ttu-id="c49e1-124">追加の LINQ メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="c49e1-124">Call additional LINQ methods</span></span>

<span data-ttu-id="c49e1-125">一般に、<xref:System.Linq.Queryable> の[組み込みの LINQ メソッド](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs)では、次の 2 つの手順を行います。</span><span class="sxs-lookup"><span data-stu-id="c49e1-125">Generally, the [built-in LINQ methods](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Linq.Queryable/src/System/Linq/Queryable.cs) at <xref:System.Linq.Queryable> perform two steps:</span></span>

* <span data-ttu-id="c49e1-126">メソッド呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> で現在の式ツリーをラップする。</span><span class="sxs-lookup"><span data-stu-id="c49e1-126">Wrap the current expression tree in a <xref:System.Linq.Expressions.MethodCallExpression> representing the method call.</span></span>
* <span data-ttu-id="c49e1-127">ラップされた式ツリーをプロバイダーに戻し、プロバイダーの <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> メソッドを使用して値を返すか、<xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> メソッドを使用して変換されたクエリ オブジェクトを返す。</span><span class="sxs-lookup"><span data-stu-id="c49e1-127">Pass the wrapped expression tree back to the provider, either to return a value via the provider's <xref:System.Linq.IQueryProvider.Execute%2A?displayProperty=nameWithType> method; or to return a translated query object via the <xref:System.Linq.IQueryProvider.CreateQuery%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c49e1-128">元のクエリを、[IQueryable(Of T)](xref:System.Linq.IQueryable%601) を返すメソッドの結果に置き換えて、新しいクエリを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-128">You can replace the original query with the result of an [IQueryable(Of T)](xref:System.Linq.IQueryable%601)-returning method, to get a new query.</span></span> <span data-ttu-id="c49e1-129">次の例のように、実行時の状態に基づいて条件付きでこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-129">You can do this conditionally based on runtime state, as in the following example:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Added_method_calls":::

## <a name="vary-the-expression-tree-passed-into-the-linq-methods"></a><span data-ttu-id="c49e1-130">LINQ メソッドに渡される式ツリーを変更する</span><span class="sxs-lookup"><span data-stu-id="c49e1-130">Vary the expression tree passed into the LINQ methods</span></span>

<span data-ttu-id="c49e1-131">実行時の状態に応じて、LINQ メソッドに異なる式を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-131">You can pass in different expressions to the LINQ methods, depending on runtime state:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Varying_expressions":::

<span data-ttu-id="c49e1-132">[LinqKit](http://www.albahari.com/nutshell/linqkit.aspx) の [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx) などのサードパーティ製ライブラリを使用して、さまざまなサブ式を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-132">You might also want to compose the various sub-expressions using a third-party library such as [LinqKit](http://www.albahari.com/nutshell/linqkit.aspx)'s [PredicateBuilder](http://www.albahari.com/nutshell/predicatebuilder.aspx):</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Compose_expression":::

## <a name="construct-expression-trees-and-queries-using-factory-methods"></a><span data-ttu-id="c49e1-133">ファクトリ メソッドを使用して式ツリーとクエリを構築する</span><span class="sxs-lookup"><span data-stu-id="c49e1-133">Construct expression trees and queries using factory methods</span></span>

<span data-ttu-id="c49e1-134">この時点までのすべての例では、コンパイル時に要素型 &mdash;`String`&mdash; (したがって、クエリの型 &mdash;`IQueryable(Of String)`) がわかっています。</span><span class="sxs-lookup"><span data-stu-id="c49e1-134">In all the examples up to this point, we've known the element type at compile time&mdash;`String`&mdash;and thus the type of the query&mdash;`IQueryable(Of String)`.</span></span> <span data-ttu-id="c49e1-135">要素型に関係なくクエリにコンポーネントを追加したり、要素型に応じて異なるコンポーネントを追加したりすることが、必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-135">You may need to add components to a query of any element type, or to add different components depending on the element type.</span></span> <span data-ttu-id="c49e1-136"><xref:System.Linq.Expressions.Expression?displayProperty=fullName> でファクトリ メソッドを使用して、最初から式ツリーを作成し、実行時に特定の要素型に合わせて式を調整することができます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-136">You can create expression trees from the ground up, using the factory methods at <xref:System.Linq.Expressions.Expression?displayProperty=fullName>, and thus tailor the expression at runtime to a specific element type.</span></span>

### <a name="constructing-an-expressionof-tdelegate"></a><span data-ttu-id="c49e1-137">[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) の構築</span><span class="sxs-lookup"><span data-stu-id="c49e1-137">Constructing an [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601)</span></span>

<span data-ttu-id="c49e1-138">LINQ メソッドのいずれかに渡す式を構築する場合、実際には [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) のインスタンスを構築します。`TDelegate` は、`Func(Of String, Boolean)`、`Action`、カスタム デリゲート型などの、何らかのデリゲート型です。</span><span class="sxs-lookup"><span data-stu-id="c49e1-138">When you construct an expression to pass into one of the LINQ methods, you're actually constructing an instance of [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601), where `TDelegate` is some delegate type such as `Func(Of String, Boolean)`, `Action`, or a custom delegate type.</span></span>

<span data-ttu-id="c49e1-139">[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) は、次のような完全なラムダ式を表す <xref:System.Linq.Expressions.LambdaExpression> から継承されます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-139">[Expression(Of TDelegate))](xref:System.Linq.Expressions.Expression%601) inherits from <xref:System.Linq.Expressions.LambdaExpression>, which represents a complete lambda expression like the following:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Compiler_generated":::

<span data-ttu-id="c49e1-140"><xref:System.Linq.Expressions.LambdaExpression> には次の 2 つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-140">A <xref:System.Linq.Expressions.LambdaExpression> has two components:</span></span>

* <span data-ttu-id="c49e1-141">パラメーター リスト &mdash;`(x As String)`&mdash; <xref:System.Linq.Expressions.LambdaExpression.Parameters> プロパティによって表されます</span><span class="sxs-lookup"><span data-stu-id="c49e1-141">a parameter list&mdash;`(x As String)`&mdash;represented by the <xref:System.Linq.Expressions.LambdaExpression.Parameters> property</span></span>
* <span data-ttu-id="c49e1-142">本文 &mdash;`x.StartsWith("a")`&mdash; <xref:System.Linq.Expressions.LambdaExpression.Body> プロパティによって表されます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-142">a body&mdash;`x.StartsWith("a")`&mdash;represented by the <xref:System.Linq.Expressions.LambdaExpression.Body> property.</span></span>

<span data-ttu-id="c49e1-143">[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) を構築する基本的な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c49e1-143">The basic steps in constructing an [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) are as follows:</span></span>

* <span data-ttu-id="c49e1-144"><xref:System.Linq.Expressions.Expression.Parameter%2A> ファクトリ メソッドを使用して、ラムダ式内の各パラメーター (存在する場合) に <xref:System.Linq.Expressions.ParameterExpression> オブジェクトを定義する。</span><span class="sxs-lookup"><span data-stu-id="c49e1-144">Define <xref:System.Linq.Expressions.ParameterExpression> objects for each of the parameters (if any) in the lambda expression, using the <xref:System.Linq.Expressions.Expression.Parameter%2A> factory method.</span></span>

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_parameter":::

* <span data-ttu-id="c49e1-145">定義した <xref:System.Linq.Expressions.ParameterExpression> と、<xref:System.Linq.Expressions.Expression> のファクトリ メソッドを使用して、<xref:System.Linq.Expressions.LambdaExpression> の本体を作成します。</span><span class="sxs-lookup"><span data-stu-id="c49e1-145">Construct the body of your <xref:System.Linq.Expressions.LambdaExpression>, using the <xref:System.Linq.Expressions.ParameterExpression>(s) you've defined, and the factory methods at <xref:System.Linq.Expressions.Expression>.</span></span> <span data-ttu-id="c49e1-146">たとえば、`x.StartsWith("a")` を表す式はこのように構築できます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-146">For instance, an expression representing `x.StartsWith("a")` could be constructed like this:</span></span>

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_body":::

* <span data-ttu-id="c49e1-147">適切な <xref:System.Linq.Expressions.Expression.Lambda%2A> ファクトリ メソッドのオーバーロードを使用して、コンパイル時に型指定される [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) にパラメーターと本文をラップします。</span><span class="sxs-lookup"><span data-stu-id="c49e1-147">Wrap the parameters and body in a compile-time-typed [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601), using the appropriate <xref:System.Linq.Expressions.Expression.Lambda%2A> factory method overload:</span></span>

    :::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_method_lambda":::

<span data-ttu-id="c49e1-148">次のセクションでは、LINQ メソッドに渡す [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) を構築することが望ましいシナリオについて説明し、ファクトリ メソッドを使用してそれを行う方法の完全な例を示します。</span><span class="sxs-lookup"><span data-stu-id="c49e1-148">The following sections describe a scenario in which you might want to construct an [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) to pass into a LINQ method, and provide a complete example of how to do so using the factory methods.</span></span>

### <a name="scenario"></a><span data-ttu-id="c49e1-149">シナリオ</span><span class="sxs-lookup"><span data-stu-id="c49e1-149">Scenario</span></span>

<span data-ttu-id="c49e1-150">たとえば、複数のエンティティ型があるとします。</span><span class="sxs-lookup"><span data-stu-id="c49e1-150">Let's say you have multiple entity types:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Entities.vb":::

<span data-ttu-id="c49e1-151">これらのいずれかのエンティティ型については、`string` フィールドの 1 つに特定のテキストが含まれているエンティティのみをフィルター処理して返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-151">For any of these entity types, you want to filter and return only those entities that have a given text inside one of their `string` fields.</span></span> <span data-ttu-id="c49e1-152">`Person` については、`FirstName` と `LastName` のプロパティを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-152">For `Person`, you'd want to search the `FirstName` and `LastName` properties:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="PersonsQry":::

<span data-ttu-id="c49e1-153">しかし、`Car` については、`Model` プロパティのみを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c49e1-153">but for `Car`, you'd want to search only the `Model` property:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="CarsQry":::

<span data-ttu-id="c49e1-154">`IQueryable(Of Person)` 用にカスタム関数を 1 つと、`IQueryable(Of Car)` 用にもう 1 つを記述することもできますが、次の関数では、特定の要素型に関係なく、このフィルターを既存のすべてのクエリに追加します。</span><span class="sxs-lookup"><span data-stu-id="c49e1-154">While you could write one custom function for `IQueryable(Of Person)` and another for `IQueryable(Of Car)`, the following function adds this filtering to any existing query, irrespective of the specific element type.</span></span>

### <a name="example"></a><span data-ttu-id="c49e1-155">例</span><span class="sxs-lookup"><span data-stu-id="c49e1-155">Example</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_expression_of_tdelegate":::

<span data-ttu-id="c49e1-156">`TextFilter` 関数は [IQueryable(Of T)](xref:System.Linq.IQueryable%601) (<xref:System.Linq.IQueryable> だけでなく) を受け取って返すため、コンパイル時に型指定されるクエリ要素をテキスト フィルターの後にさらに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-156">Because the `TextFilter` function takes and returns an [IQueryable(Of T)](xref:System.Linq.IQueryable%601) (and not just an <xref:System.Linq.IQueryable>), you can add further compile-time-typed query elements after the text filter.</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_expression_of_tdelegate_usage":::

## <a name="add-method-call-nodes-to-the-xrefsystemlinqiqueryables-expression-tree"></a><span data-ttu-id="c49e1-157"><xref:System.Linq.IQueryable> の式ツリーにメソッド呼び出しノードを追加する</span><span class="sxs-lookup"><span data-stu-id="c49e1-157">Add method call nodes to the <xref:System.Linq.IQueryable>'s expression tree</span></span>

<span data-ttu-id="c49e1-158">[IQueryable(Of T)](xref:System.Linq.IQueryable%601) の代わりに <xref:System.Linq.IQueryable> を使用する場合は、汎用 LINQ メソッドを直接呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c49e1-158">If you have an <xref:System.Linq.IQueryable> instead of an [IQueryable(Of T)](xref:System.Linq.IQueryable%601), you can't directly call the generic LINQ methods.</span></span> <span data-ttu-id="c49e1-159">代替手段の 1 つは、上記のように内部式ツリーをビルドし、リフレクションを使用して、式ツリーに渡すときに適切な LINQ メソッドを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="c49e1-159">One alternative is to build the inner expression tree as above, and use reflection to invoke the appropriate LINQ method while passing in the expression tree.</span></span>

<span data-ttu-id="c49e1-160">LINQ メソッドの呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> でツリー全体をラップすることにより、LINQ メソッドの機能を複製することもできます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-160">You could also duplicate the LINQ method's functionality, by wrapping the entire tree in a <xref:System.Linq.Expressions.MethodCallExpression> which represents a call to the LINQ method:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Factory_methods_lambdaexpression":::

<span data-ttu-id="c49e1-161">この場合、コンパイル時の `T` 汎用プレースホルダーがないため、コンパイル時に型情報が必要なく、[Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601) の代わりに <xref:System.Linq.Expressions.LambdaExpression> が生成される、<xref:System.Linq.Expressions.Expression.Lambda%2A> のオーバーロードを使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c49e1-161">Note that in this case you don't have a compile-time `T` generic placeholder, so you'll use the <xref:System.Linq.Expressions.Expression.Lambda%2A> overload which doesn't require compile-time type information, and which produces a <xref:System.Linq.Expressions.LambdaExpression> instead of an an [Expression(Of TDelegate)](xref:System.Linq.Expressions.Expression%601).</span></span>

## <a name="the-dynamic-linq-library"></a><span data-ttu-id="c49e1-162">動的 LINQ ライブラリ</span><span class="sxs-lookup"><span data-stu-id="c49e1-162">The Dynamic LINQ library</span></span>

<span data-ttu-id="c49e1-163">ファクトリ メソッドを使用した式ツリーの構築は比較的複雑です。文字列を作成する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="c49e1-163">Constructing expression trees using factory methods is relatively complex; it is easier to compose strings.</span></span> <span data-ttu-id="c49e1-164">[動的 LINQ ライブラリ](https://dynamic-linq.net/)では、<xref:System.Linq.Queryable>で標準 LINQ メソッドに対応する <xref:System.Linq.IQueryable> の拡張メソッドのセットを公開し、式ツリーではなく[特殊な構文](https://dynamic-linq.net/expression-language)で文字列を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-164">The [Dynamic LINQ library](https://dynamic-linq.net/) exposes a set of extension methods on <xref:System.Linq.IQueryable> corresponding to the standard LINQ methods at <xref:System.Linq.Queryable>, and which accept strings in a [special syntax](https://dynamic-linq.net/expression-language) instead of expression trees.</span></span> <span data-ttu-id="c49e1-165">ライブラリで文字列から適切な式ツリーが生成され、結果として変換された <xref:System.Linq.IQueryable> を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-165">The library generates the appropriate expression tree from the string, and can return the resultant translated <xref:System.Linq.IQueryable>.</span></span>

<span data-ttu-id="c49e1-166">たとえば、前の例 (式ツリーの構築を含む) は次のように書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="c49e1-166">For instance, the previous example (including the expression tree construction) could be rewritten as follows:</span></span>

:::code language="vb" source="../../../../../samples/snippets/visualbasic/programming-guide/dynamic-linq-expression-trees/Program.vb" id="Dynamic_linq":::

## <a name="see-also"></a><span data-ttu-id="c49e1-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="c49e1-167">See also</span></span>

- [<span data-ttu-id="c49e1-168">式ツリー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c49e1-168">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="c49e1-169">方法: 式ツリーを実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c49e1-169">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
