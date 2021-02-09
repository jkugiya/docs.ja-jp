---
description: '詳細情報: Aggregate 句 (Visual Basic)'
title: Aggregate Clause
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 404cb4091bc11132450cf0d8d001ce426439ece7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700664"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="a22ea-103">Aggregate 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a22ea-103">Aggregate Clause (Visual Basic)</span></span>

<span data-ttu-id="a22ea-104">1 つ以上の集計関数をコレクションに適用します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-104">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22ea-105">構文</span><span class="sxs-lookup"><span data-stu-id="a22ea-105">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="a22ea-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="a22ea-106">Parts</span></span>  
  
|<span data-ttu-id="a22ea-107">用語</span><span class="sxs-lookup"><span data-stu-id="a22ea-107">Term</span></span>|<span data-ttu-id="a22ea-108">定義</span><span class="sxs-lookup"><span data-stu-id="a22ea-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="a22ea-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="a22ea-109">Required.</span></span> <span data-ttu-id="a22ea-110">コレクションの要素の反復処理に使用される変数。</span><span class="sxs-lookup"><span data-stu-id="a22ea-110">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="a22ea-111">任意。</span><span class="sxs-lookup"><span data-stu-id="a22ea-111">Optional.</span></span> <span data-ttu-id="a22ea-112">`element` の型。</span><span class="sxs-lookup"><span data-stu-id="a22ea-112">The type of `element`.</span></span> <span data-ttu-id="a22ea-113">型が指定されていない場合、`element` の型は `collection` から推論されます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-113">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="a22ea-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="a22ea-114">Required.</span></span> <span data-ttu-id="a22ea-115">操作対象のコレクションを参照します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-115">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="a22ea-116">任意。</span><span class="sxs-lookup"><span data-stu-id="a22ea-116">Optional.</span></span> <span data-ttu-id="a22ea-117">Aggregate 句を適用するクエリ結果を絞り込むための `Where` 句などの 1 つ以上のクエリ句。</span><span class="sxs-lookup"><span data-stu-id="a22ea-117">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="a22ea-118">必須です。</span><span class="sxs-lookup"><span data-stu-id="a22ea-118">Required.</span></span> <span data-ttu-id="a22ea-119">コレクションに適用する集計関数を識別する 1 つ以上のコンマ区切り式。</span><span class="sxs-lookup"><span data-stu-id="a22ea-119">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="a22ea-120">集計関数に別名を適用して、クエリ結果のメンバー名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-120">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="a22ea-121">別名が指定されていない場合、集計関数の名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-121">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="a22ea-122">例については、このトピックで後述する集計関数に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22ea-122">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a22ea-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="a22ea-123">Remarks</span></span>  

 <span data-ttu-id="a22ea-124">`Aggregate` 句を使用して、クエリに集計関数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-124">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="a22ea-125">集計関数は、値の集まりに対して、チェックと計算を実行し、1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-125">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="a22ea-126">クエリ結果の型のメンバーを使用して、計算された値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-126">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="a22ea-127">使用できる標準の集計関数は、`All`、`Any`、`Average`、`Count`、`LongCount`、`Max`、`Min`、`Sum` 関数です。</span><span class="sxs-lookup"><span data-stu-id="a22ea-127">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="a22ea-128">これらの関数は、SQL での集計に精通している開発者になじみがあります。</span><span class="sxs-lookup"><span data-stu-id="a22ea-128">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="a22ea-129">このトピックの以降のセクションで、それらについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-129">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="a22ea-130">集計関数の結果は、クエリ結果の型のフィールドとしてクエリ結果に含まれます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-130">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="a22ea-131">集計関数の結果に別名を指定して、集計値を保持するクエリ結果の型のメンバーの名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-131">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="a22ea-132">別名が指定されていない場合、集計関数の名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-132">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="a22ea-133">`Aggregate` 句は、クエリを開始したり、クエリの追加の句として含めたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-133">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="a22ea-134">`Aggregate` 句によってクエリが開始された場合、結果は、`Into` 句に指定された集計関数の結果である単一の値になります。</span><span class="sxs-lookup"><span data-stu-id="a22ea-134">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="a22ea-135">`Into` 句に複数の集計関数が指定されている場合、クエリでは、`Into` 句で各集計関数の結果を参照するための個別のプロパティを持つ単一の型が返されます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-135">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="a22ea-136">`Aggregate` 句がクエリに追加の句として含まれている場合、クエリ コレクションで返される型には、`Into` 句で各集計関数の結果を参照する個別のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a22ea-136">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="a22ea-137">集計関数</span><span class="sxs-lookup"><span data-stu-id="a22ea-137">Aggregate Functions</span></span>

<span data-ttu-id="a22ea-138">次に、`Aggregate` 句で使用できる標準の集計関数を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-138">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="a22ea-139">すべて</span><span class="sxs-lookup"><span data-stu-id="a22ea-139">All</span></span>

<span data-ttu-id="a22ea-140">コレクション内のすべての要素が指定された条件を満たす場合に `true` を返します。それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-140">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="a22ea-141">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-141">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="a22ea-142">どれでも可</span><span class="sxs-lookup"><span data-stu-id="a22ea-142">Any</span></span>

<span data-ttu-id="a22ea-143">コレクション内のいずれかの要素が指定された条件を満たす場合に `true` を返します。それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-143">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="a22ea-144">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-144">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="a22ea-145">平均</span><span class="sxs-lookup"><span data-stu-id="a22ea-145">Average</span></span>

<span data-ttu-id="a22ea-146">コレクション内のすべての要素の平均値を計算するか、コレクション内のすべての要素に対して指定された式を計算します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-146">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a22ea-147">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-147">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="a22ea-148">カウント</span><span class="sxs-lookup"><span data-stu-id="a22ea-148">Count</span></span>

<span data-ttu-id="a22ea-149">コレクション内の要素の数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="a22ea-149">Counts the number of elements in the collection.</span></span> <span data-ttu-id="a22ea-150">条件を満たすコレクション内の要素の数のみをカウントする省略可能な `Boolean` 式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-150">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="a22ea-151">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-151">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="a22ea-152">グループ化</span><span class="sxs-lookup"><span data-stu-id="a22ea-152">Group</span></span>

<span data-ttu-id="a22ea-153">`Group By` または `Group Join` 句の結果として、グループ化されたクエリ結果を参照します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-153">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="a22ea-154">`Group` 関数は、`Group By` または `Group Join` 句の `Into` 句でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="a22ea-154">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="a22ea-155">詳細と例については、「[Group By 句](group-by-clause.md)」と「[Group Join 句](group-join-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22ea-155">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="a22ea-156">LongCount</span><span class="sxs-lookup"><span data-stu-id="a22ea-156">LongCount</span></span>

<span data-ttu-id="a22ea-157">コレクション内の要素の数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="a22ea-157">Counts the number of elements in the collection.</span></span> <span data-ttu-id="a22ea-158">条件を満たすコレクション内の要素の数のみをカウントする省略可能な `Boolean` 式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-158">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="a22ea-159">結果を `Long` として返します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-159">Returns the result as a `Long`.</span></span> <span data-ttu-id="a22ea-160">例については、「`Count` 集計関数」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22ea-160">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="a22ea-161">最大</span><span class="sxs-lookup"><span data-stu-id="a22ea-161">Max</span></span>

<span data-ttu-id="a22ea-162">コレクションから最大値を計算するか、コレクション内のすべての要素に対して指定された式を計算します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-162">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a22ea-163">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-163">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="a22ea-164">最小</span><span class="sxs-lookup"><span data-stu-id="a22ea-164">Min</span></span>

<span data-ttu-id="a22ea-165">コレクションから最小値を計算するか、コレクション内のすべての要素に対して指定された式を計算します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-165">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a22ea-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-166">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="a22ea-167">Sum</span><span class="sxs-lookup"><span data-stu-id="a22ea-167">Sum</span></span>

<span data-ttu-id="a22ea-168">コレクション内のすべての要素の合計を計算するか、コレクション内のすべての要素に対して指定された式を計算します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-168">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="a22ea-169">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-169">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="a22ea-170">例</span><span class="sxs-lookup"><span data-stu-id="a22ea-170">Example</span></span>  

<span data-ttu-id="a22ea-171">次の例では、`Aggregate` 句を使用して、クエリ結果に集計関数を適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-171">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="a22ea-172">ユーザー定義集計関数の作成</span><span class="sxs-lookup"><span data-stu-id="a22ea-172">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="a22ea-173"><xref:System.Collections.Generic.IEnumerable%601> 型に拡張メソッドを追加することで、独自のカスタム集計関数をクエリ式に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-173">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="a22ea-174">カスタム メソッドが、集計関数を参照した列挙可能なコレクションに対して計算や操作を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a22ea-174">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="a22ea-175">拡張メソッドについて詳しくは、「[拡張メソッド](../../programming-guide/language-features/procedures/extension-methods.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a22ea-175">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="a22ea-176">たとえば、次の例では、数値のコレクションの中央値を計算するカスタム集計関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="a22ea-176">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="a22ea-177">`Median` 拡張メソッドには、2 つのオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="a22ea-177">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="a22ea-178">最初のオーバーロードでは、入力として `IEnumerable(Of Double)` 型のコレクションを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-178">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="a22ea-179">`Double` 型のクエリ フィールドに対して `Median` 集計関数が呼び出されると、このメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-179">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="a22ea-180">`Median` メソッドの 2 つ目のオーバーロードには、任意のジェネリック型を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a22ea-180">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="a22ea-181">`Median` メソッドのジェネリック オーバーロードは、`Func(Of T, Double)` ラムダ式を参照する 2 つ目のパラメーターを受け取ります。このパラメーターは、ある型 (コレクションからの) の値を `Double` 型の対応する値としてプロジェクションします。</span><span class="sxs-lookup"><span data-stu-id="a22ea-181">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="a22ea-182">次に、中央値の計算を `Median` メソッドの他のオーバーロードにデリゲートします。</span><span class="sxs-lookup"><span data-stu-id="a22ea-182">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="a22ea-183">ラムダ式について詳しくは、「[ラムダ式](../../programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a22ea-183">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="a22ea-184">次の例は、`Integer` 型のコレクションと `Double` 型のコレクションに対して `Median` 集計関数を呼び出すサンプル クエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="a22ea-184">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="a22ea-185">`Double` 型のコレクションに対して `Median` 集計関数を呼び出すクエリは、`Double` 型のコレクションを入力として受け入れる `Median` メソッドのオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-185">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="a22ea-186">`Integer` 型のコレクションに対して `Median` 集計関数を呼び出すクエリは、`Median` メソッドのジェネリック オーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a22ea-186">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="a22ea-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="a22ea-187">See also</span></span>

- [<span data-ttu-id="a22ea-188">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="a22ea-188">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="a22ea-189">クエリ</span><span class="sxs-lookup"><span data-stu-id="a22ea-189">Queries</span></span>](index.md)
- [<span data-ttu-id="a22ea-190">Select 句</span><span class="sxs-lookup"><span data-stu-id="a22ea-190">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="a22ea-191">From 句</span><span class="sxs-lookup"><span data-stu-id="a22ea-191">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="a22ea-192">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="a22ea-192">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="a22ea-193">Group By 句</span><span class="sxs-lookup"><span data-stu-id="a22ea-193">Group By Clause</span></span>](group-by-clause.md)
