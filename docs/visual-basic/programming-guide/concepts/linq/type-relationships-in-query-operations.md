---
description: '詳細情報: クエリ操作での型の関係 (Visual Basic)'
title: クエリ操作での型の関係
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: b6a59308e76afdcf1aaf7084904b9925cd5bef14
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428221"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="48982-103">クエリ操作での型の関係 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48982-103">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="48982-104">統合言語クエリ (LINQ) のクエリ操作で使用される変数は厳密に型指定されており、互いに互換性がなければなりません。</span><span class="sxs-lookup"><span data-stu-id="48982-104">Variables used in Language-Integrated Query (LINQ) query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="48982-105">厳密な型指定は、データ ソースで使用されるほか、クエリそのものや、クエリの実行でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="48982-105">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="48982-106">次の図は、LINQ クエリの説明で用いられる用語を示したものです。</span><span class="sxs-lookup"><span data-stu-id="48982-106">The following illustration identifies terms used to describe a LINQ query.</span></span> <span data-ttu-id="48982-107">クエリの構成要素について詳しくは、「[基本的なクエリ操作 (Visual Basic)](basic-query-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48982-107">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span>

![要素が強調表示された擬似コード クエリを示すスクリーンショット](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="48982-109">クエリの範囲変数の型には、データ ソース内の要素の型との互換性が必要です。</span><span class="sxs-lookup"><span data-stu-id="48982-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="48982-110">クエリ変数の型は、`Select` 句で定義されているシーケンス要素と互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="48982-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="48982-111">最後に、シーケンス要素の型も、クエリを実行する `For Each` ステートメントで使用されるループ制御変数の型と互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="48982-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="48982-112">この厳密な型指定によって、コンパイル時に発生する型エラーが特定しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="48982-112">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="48982-113">Visual Basic は、ローカル型推論 ("*暗黙の型指定*" とも呼ばれます) を実装することで、厳密な型指定の利便性を高めています。</span><span class="sxs-lookup"><span data-stu-id="48982-113">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="48982-114">その機能は、前の例で使用されているほか、LINQ のサンプルやドキュメントの至る所で目にすることができます。</span><span class="sxs-lookup"><span data-stu-id="48982-114">That feature is used in the previous example, and you will see it used throughout the LINQ samples and documentation.</span></span> <span data-ttu-id="48982-115">Visual Basic では、単に `As` 句のない `Dim` ステートメントを使用すれば、ローカル型推論が行われます。</span><span class="sxs-lookup"><span data-stu-id="48982-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="48982-116">次の例の `city` は、文字列として厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="48982-116">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="48982-117">ローカル型推論が機能するのは、`Option Infer` が `On` に設定されているときだけです。</span><span class="sxs-lookup"><span data-stu-id="48982-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="48982-118">詳細については、「[Option Infer ステートメント](../../../language-reference/statements/option-infer-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48982-118">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="48982-119">ただし、クエリでローカル型推論を使用した場合でも、データ ソース内の変数、クエリ変数、クエリの実行ループの間に存在する型の関係は同じです。</span><span class="sxs-lookup"><span data-stu-id="48982-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="48982-120">こうした型の関係についての基本的な知識は、LINQ クエリを記述するときや、ドキュメント内のサンプルまたはコード例を扱うときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="48982-120">It is useful to have a basic understanding of these type relationships when you are writing LINQ queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="48982-121">データ ソースから返された型と一致しない範囲変数には、明示的な型の指定が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="48982-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="48982-122">範囲変数の型は、`As` 句を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="48982-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="48982-123">ただし、変換が[縮小変換](../../language-features/data-types/widening-and-narrowing-conversions.md)で、なおかつ `Option Strict` が `On` に設定されているとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="48982-123">However, this results in an error if the conversion is a [narrowing conversion](../../language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="48982-124">したがって変換は、データ ソースから取得された値に対して実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="48982-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="48982-125"><xref:System.Linq.Enumerable.Cast%2A> メソッドを使用すると、データ ソースから取得された値を、明示的な範囲変数の型に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="48982-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="48982-126">また、`Select` 句で選択した値を、範囲変数の型とは異なる明示的な型にキャストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="48982-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="48982-127">以上の点については、次のコードで説明しています。</span><span class="sxs-lookup"><span data-stu-id="48982-127">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="48982-128">ソース データの要素全体を返すクエリ</span><span class="sxs-lookup"><span data-stu-id="48982-128">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="48982-129">次の例は、ソース データから選択された要素のシーケンスを返す LINQ クエリ操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="48982-129">The following example shows a LINQ query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="48982-130">ソース (`names`) には、文字列の配列が格納されます。アルファベットの M で始まる文字列を含んだシーケンスがクエリの出力となります。</span><span class="sxs-lookup"><span data-stu-id="48982-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="48982-131">次のコードに相当しますが、こちらの方がはるかに短く、記述しやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="48982-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="48982-132">Visual Basic では、クエリにローカル型推論を使うのが、推奨されるスタイルです。</span><span class="sxs-lookup"><span data-stu-id="48982-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="48982-133">型の指定が暗黙的であれ明示的であれ、前出のコード例には、どちらも次の関係が存在します。</span><span class="sxs-lookup"><span data-stu-id="48982-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="48982-134">データ ソース (`names`) に含まれる要素の型は、クエリの範囲変数 (`name`) の型です。</span><span class="sxs-lookup"><span data-stu-id="48982-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="48982-135">選択したオブジェクト (`name`) の型によって、クエリ変数 (`mNames`) の型が決まります。</span><span class="sxs-lookup"><span data-stu-id="48982-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="48982-136">ここでは `name` が文字列であるため、クエリ変数は Visual Basic の IEnumerable(Of String) となります。</span><span class="sxs-lookup"><span data-stu-id="48982-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="48982-137">`mNames` で定義されたクエリは、`For Each` ループで実行されます。</span><span class="sxs-lookup"><span data-stu-id="48982-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="48982-138">このループによって、クエリの実行結果が反復処理されます。</span><span class="sxs-lookup"><span data-stu-id="48982-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="48982-139">`mNames` は、実行されたときに文字列のシーケンスを返すため、ループの反復変数 (`nm`) も文字列になります。</span><span class="sxs-lookup"><span data-stu-id="48982-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="48982-140">選択された要素から 1 つのフィールドを返すクエリ</span><span class="sxs-lookup"><span data-stu-id="48982-140">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="48982-141">次の例は、データ ソースから選択された各要素の一部分のみを含んだシーケンスを返す [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] クエリ操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="48982-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="48982-142">このクエリは、`Customer` オブジェクトのコレクションをそのデータ ソースとして受け取って、`Name` プロパティのみを結果に投影します。</span><span class="sxs-lookup"><span data-stu-id="48982-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="48982-143">顧客名は文字列なので、クエリは出力として文字列のシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="48982-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="48982-144">単純な方の例と同様、変数間の関係は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="48982-144">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="48982-145">データ ソース (`customers`) に含まれる要素の型は、クエリの範囲変数 (`cust`) の型です。</span><span class="sxs-lookup"><span data-stu-id="48982-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="48982-146">この例では、`Customer` 型が該当します。</span><span class="sxs-lookup"><span data-stu-id="48982-146">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="48982-147">`Select` ステートメントから返されるのは、オブジェクト全体ではなく、各 `Customer` オブジェクトの `Name` プロパティです。</span><span class="sxs-lookup"><span data-stu-id="48982-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="48982-148">`Name` は文字列であるため、この場合もクエリ変数 (`custNames`) は IEnumerable(Of String) であって、`Customer` ではありません。</span><span class="sxs-lookup"><span data-stu-id="48982-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="48982-149">`custNames` は文字列のシーケンスを表すので、`For Each` ループの反復変数 (`custName`) も文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="48982-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="48982-150">ローカル型推論がなければ、前出の例は、もっと書きづらく、また理解しにくいものになるでしょう。その例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="48982-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="48982-151">匿名型を必要とするクエリ</span><span class="sxs-lookup"><span data-stu-id="48982-151">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="48982-152">次に示したのは、より複雑な状況の例です。</span><span class="sxs-lookup"><span data-stu-id="48982-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="48982-153">前の例では、すべての変数に対して明示的に型を指定するのは、容易ではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="48982-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="48982-154">この例では、それが不可能となります。</span><span class="sxs-lookup"><span data-stu-id="48982-154">In this example, it is impossible.</span></span> <span data-ttu-id="48982-155">このクエリの `Select` 句は、データ ソースから `Customer` 要素全体を選択したり、各要素から 1 つのフィールドだけを選択したりするのではなく、元の `Customer` オブジェクトから `Name` と `City` の 2 つのプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="48982-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="48982-156">`Select` 句に対する応答として、それら 2 つのプロパティを含んだ匿名型がコンパイラによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="48982-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="48982-157">`For Each` ループで `nameCityQuery` を実行した結果は、新しい匿名型のインスタンスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="48982-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="48982-158">匿名型には有効な名前がないため、`nameCityQuery` と `custInfo` の型を明示的に指定することができません。</span><span class="sxs-lookup"><span data-stu-id="48982-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="48982-159">つまり、匿名型では、`IEnumerable(Of String)` の `String` の代わりに使用できる型名がないのです。</span><span class="sxs-lookup"><span data-stu-id="48982-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="48982-160">詳細については、「[匿名型](../../language-features/objects-and-classes/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48982-160">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="48982-161">前の例のすべての変数に型を指定することはできませんが、その関係は変わりません。</span><span class="sxs-lookup"><span data-stu-id="48982-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="48982-162">この場合も、データ ソースに含まれる要素の型は、クエリの範囲変数の型です。</span><span class="sxs-lookup"><span data-stu-id="48982-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="48982-163">この例の `cust` は、`Customer` のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="48982-163">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="48982-164">`Select` ステートメントによって匿名型が生成されるため、クエリ変数 (`nameCityQuery`) は、匿名型として暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48982-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="48982-165">匿名型は、有効な名前を持たないため、明示的に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="48982-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="48982-166">`For Each` ループにおける反復変数の型は、手順 2. で作成した匿名型です。</span><span class="sxs-lookup"><span data-stu-id="48982-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="48982-167">この型には有効な名前がないため、ループの反復変数の型は、必然的に暗黙的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="48982-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="48982-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="48982-168">See also</span></span>

- [<span data-ttu-id="48982-169">Visual Basic の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="48982-169">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="48982-170">匿名型</span><span class="sxs-lookup"><span data-stu-id="48982-170">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="48982-171">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="48982-171">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="48982-172">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="48982-172">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="48982-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="48982-173">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="48982-174">クエリ</span><span class="sxs-lookup"><span data-stu-id="48982-174">Queries</span></span>](../../../language-reference/queries/index.md)
