---
description: '詳細情報: 基本的なクエリ操作 (Visual Basic)'
title: クエリの基本操作
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 1f8fbda83c21fe9032415d96ff2d7e184083a839
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428689"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="7e339-103">基本的なクエリ操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e339-103">Basic Query Operations (Visual Basic)</span></span>

<span data-ttu-id="7e339-104">このトピックでは、Visual Basic における統合言語クエリ (LINQ) 式と、クエリで実行されるいくつかの一般的な操作について簡単に紹介します。</span><span class="sxs-lookup"><span data-stu-id="7e339-104">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="7e339-105">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-105">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="7e339-106">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="7e339-106">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="7e339-107">クエリ</span><span class="sxs-lookup"><span data-stu-id="7e339-107">Queries</span></span>](../../../language-reference/queries/index.md)  
  
 [<span data-ttu-id="7e339-108">チュートリアル: Visual Basic でのクエリの作成</span><span class="sxs-lookup"><span data-stu-id="7e339-108">Walkthrough: Writing Queries in Visual Basic</span></span>](walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="7e339-109">データ ソースを指定する (From)</span><span class="sxs-lookup"><span data-stu-id="7e339-109">Specifying the Data Source (From)</span></span>  

 <span data-ttu-id="7e339-110">LINQ クエリで最初に行う手順は、照会するデータ ソースの指定です。</span><span class="sxs-lookup"><span data-stu-id="7e339-110">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="7e339-111">そのためクエリでは、`From` 句が必ず先頭に来ます。</span><span class="sxs-lookup"><span data-stu-id="7e339-111">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="7e339-112">クエリ演算子は、ソースの種類に基づいて結果を選択し、整形します。</span><span class="sxs-lookup"><span data-stu-id="7e339-112">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="7e339-113">`From` 句は、データ ソース (`customers`) と "*範囲変数*" (`cust`) を指定するものです。</span><span class="sxs-lookup"><span data-stu-id="7e339-113">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="7e339-114">範囲変数はループの反復変数に似ていますが、クエリ式では実際の反復処理が実行されない点は除きます。</span><span class="sxs-lookup"><span data-stu-id="7e339-114">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="7e339-115">クエリは多くの場合、`For Each` ループを使用して実行され、範囲変数は、クエリが実行されたとき、`customers` に含まれる連続する各要素への参照として機能します。</span><span class="sxs-lookup"><span data-stu-id="7e339-115">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="7e339-116">`cust` の型はコンパイラで推論できるため、明示的に指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7e339-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="7e339-117">明示的な型指定を使用して記述されたクエリと使用せずに記述されたクエリの例については、「[クエリ操作での型の関係 (Visual Basic)](type-relationships-in-query-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-117">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="7e339-118">Visual Basic での `From` 句の使い方について詳しくは、「[From 句](../../../language-reference/queries/from-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-118">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="7e339-119">データをフィルター処理する (Where)</span><span class="sxs-lookup"><span data-stu-id="7e339-119">Filtering Data (Where)</span></span>  

 <span data-ttu-id="7e339-120">最も一般的なクエリ操作は、ブール式の形式でフィルターを適用することです。</span><span class="sxs-lookup"><span data-stu-id="7e339-120">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="7e339-121">その場合、クエリからは、式が true となる要素のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="7e339-121">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="7e339-122">フィルター処理は、`Where` 句を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="7e339-122">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="7e339-123">データ ソース内のどの要素を結果のシーケンスに含めるかをフィルターで指定します。</span><span class="sxs-lookup"><span data-stu-id="7e339-123">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="7e339-124">次の例では、住所がロンドンにある顧客だけが結果に含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e339-124">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="7e339-125">`Where` 句では、`And` や `Or` といった論理演算子を使用して、複数のフィルター式を結合することができます。</span><span class="sxs-lookup"><span data-stu-id="7e339-125">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="7e339-126">たとえばロンドン在住で、なおかつ名前が Devon である顧客のみを取得するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e339-126">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="7e339-127">ロンドンまたはパリ在住の顧客を取得するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e339-127">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="7e339-128">Visual Basic での `Where` 句の使い方について詳しくは、「[Where 句](../../../language-reference/queries/where-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-128">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="7e339-129">データを並べ替える (Order By)</span><span class="sxs-lookup"><span data-stu-id="7e339-129">Ordering Data (Order By)</span></span>  

 <span data-ttu-id="7e339-130">返されたデータを特定の順序で並べ替えると都合がよい場合は少なくありません。</span><span class="sxs-lookup"><span data-stu-id="7e339-130">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="7e339-131">`Order By` 句を使用すると、返されたシーケンス内の要素が、指定された 1 つまたは複数のフィールドを基準に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="7e339-131">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="7e339-132">たとえば、次のクエリは `Name` プロパティに基づいて結果を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="7e339-132">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="7e339-133">`Name` は文字列であるため、返されるデータはアルファベット順 (A から Z) に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="7e339-133">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="7e339-134">結果を逆の順序 (Z から A) で並び替えるには、`Order By...Descending` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e339-134">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="7e339-135">`Ascending` も `Descending` も指定されなかった場合は、既定で `Ascending` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e339-135">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="7e339-136">Visual Basic での `Order By` 句の使い方について詳しくは、「[Order By 句](../../../language-reference/queries/order-by-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-136">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="7e339-137">データを選択する (Select)</span><span class="sxs-lookup"><span data-stu-id="7e339-137">Selecting Data (Select)</span></span>  

 <span data-ttu-id="7e339-138">`Select` 句は、返された要素の形式と内容を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e339-138">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="7e339-139">たとえば、`Customer` オブジェクト全体、1 つの `Customer` プロパティのみ、プロパティのサブセット、各種データ ソースのプロパティの組み合わせ、計算に基づくなんらかの新しい結果型のいずれで結果が構成されるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e339-139">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="7e339-140">`Select` 句でソース要素のコピー以外のものを生成する場合、その操作は *投影* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7e339-140">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="7e339-141">`Customer` オブジェクト全体から成るコレクションを取得するには、範囲変数自体を選択します。</span><span class="sxs-lookup"><span data-stu-id="7e339-141">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="7e339-142">`Customer` インスタンスがフィールドを多数含んだ大きなオブジェクトで、取得したいのはその名前だけである場合は、次の例のように `cust.Name` を選択できます。</span><span class="sxs-lookup"><span data-stu-id="7e339-142">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="7e339-143">それに伴い、結果の型が `Customer` オブジェクトのコレクションから文字列のコレクションに変化したことは、ローカル型推論によって認識されます。</span><span class="sxs-lookup"><span data-stu-id="7e339-143">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="7e339-144">データ ソースから複数のフィールドを選択したい場合、次の 2 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="7e339-144">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="7e339-145">`Select` 句で、結果に含めたいフィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e339-145">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="7e339-146">それらのフィールドをプロパティとして持つ匿名型がコンパイラによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="7e339-146">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="7e339-147">詳細については、「[匿名型](../../language-features/objects-and-classes/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-147">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="7e339-148">以下の例で返される要素は匿名型のインスタンスであるため、コード内の他の場所では、型を名前で参照することができません。</span><span class="sxs-lookup"><span data-stu-id="7e339-148">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="7e339-149">コンパイラによって指定された型名には、通常の Visual Basic コードでは無効な文字が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e339-149">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="7e339-150">次の例で、`londonCusts4` としてクエリから返されるコレクション内の要素は匿名型のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="7e339-150">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="7e339-151">\- または -</span><span class="sxs-lookup"><span data-stu-id="7e339-151">-or-</span></span>  
  
- <span data-ttu-id="7e339-152">結果に含めたい特定のフィールドを含む名前付きの型を定義し、その型のインスタンスを `Select` 句で作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="7e339-152">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="7e339-153">この方法を使用するのは、結果が返されるコレクションの外で個々の結果を使用しなければならない場合や、それらをパラメーターとしてメソッド呼び出しに渡す必要がある場合のみです。</span><span class="sxs-lookup"><span data-stu-id="7e339-153">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="7e339-154">次の例では、`londonCusts5` の型が IEnumerable(Of NamePhone) になります。</span><span class="sxs-lookup"><span data-stu-id="7e339-154">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="7e339-155">Visual Basic での `Select` 句の使い方について詳しくは、「[Select 句](../../../language-reference/queries/select-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-155">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="7e339-156">データを結合する (Join と Group Join)</span><span class="sxs-lookup"><span data-stu-id="7e339-156">Joining Data (Join and Group Join)</span></span>  

 <span data-ttu-id="7e339-157">`From` 句では、いくつかの方法で複数のデータ ソースを結合することができます。</span><span class="sxs-lookup"><span data-stu-id="7e339-157">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="7e339-158">たとえば次のコードでは、2 つのデータ ソースを使用し、その両方のプロパティを結果の中で暗黙的に結合しています。</span><span class="sxs-lookup"><span data-stu-id="7e339-158">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="7e339-159">このクエリでは、姓が母音で始まる学生が選択されます。</span><span class="sxs-lookup"><span data-stu-id="7e339-159">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="7e339-160">このコードは、「[方法: 項目のリストを作成する](how-to-create-a-list-of-items.md)」で作成した学生のリストを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="7e339-160">You can run this code with the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="7e339-161">`Join` キーワードは、SQL の `INNER JOIN` に相当します。</span><span class="sxs-lookup"><span data-stu-id="7e339-161">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="7e339-162">2 つのコレクションの要素間の一致するキーの値に基づいて 2 つのコレクションを結合します。</span><span class="sxs-lookup"><span data-stu-id="7e339-162">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="7e339-163">このクエリは、一致するキー値を持つコレクション要素の全部または一部を返します。</span><span class="sxs-lookup"><span data-stu-id="7e339-163">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="7e339-164">たとえば、前の暗黙的結合のアクションを再現するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7e339-164">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="7e339-165">SQL の `LEFT JOIN` のように、複数のコレクションを結合して 1 つの階層コレクションにするには、`Group Join` を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e339-165">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="7e339-166">詳細については、「[Join 句](../../../language-reference/queries/join-clause.md)」および「[Group Join 句](../../../language-reference/queries/group-join-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-166">For more information, see [Join Clause](../../../language-reference/queries/join-clause.md) and [Group Join Clause](../../../language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="7e339-167">データをグループ化する (Group By)</span><span class="sxs-lookup"><span data-stu-id="7e339-167">Grouping Data (Group By)</span></span>  

 <span data-ttu-id="7e339-168">`Group By` 句を追加すれば、クエリの結果に含まれる要素を、その要素の 1 つ以上のフィールドに従ってグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="7e339-168">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="7e339-169">たとえば、次のコードは、学生を学年ごとにグループ化するものです。</span><span class="sxs-lookup"><span data-stu-id="7e339-169">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="7e339-170">「[方法: 項目のリストを作成する](how-to-create-a-list-of-items.md)」で作成した学生のリストを使用してこのコードを実行した場合、`For Each` ステートメントから次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="7e339-170">If you run this code using the list of students created in [How to: Create a List of Items](how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="7e339-171">年:Junior</span><span class="sxs-lookup"><span data-stu-id="7e339-171">Year: Junior</span></span>  
  
 <span data-ttu-id="7e339-172">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="7e339-172">Tucker, Michael</span></span>  
  
 <span data-ttu-id="7e339-173">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="7e339-173">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="7e339-174">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="7e339-174">Garcia, Debra</span></span>  
  
 <span data-ttu-id="7e339-175">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="7e339-175">Tucker, Lance</span></span>  
  
 <span data-ttu-id="7e339-176">年:Senior</span><span class="sxs-lookup"><span data-stu-id="7e339-176">Year: Senior</span></span>  
  
 <span data-ttu-id="7e339-177">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="7e339-177">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="7e339-178">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="7e339-178">Osada, Michiko</span></span>  
  
 <span data-ttu-id="7e339-179">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="7e339-179">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="7e339-180">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="7e339-180">Feng, Hanying</span></span>  
  
 <span data-ttu-id="7e339-181">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="7e339-181">Adams, Terry</span></span>  
  
 <span data-ttu-id="7e339-182">年:Freshman</span><span class="sxs-lookup"><span data-stu-id="7e339-182">Year: Freshman</span></span>  
  
 <span data-ttu-id="7e339-183">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="7e339-183">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="7e339-184">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="7e339-184">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="7e339-185">次のコードでは、先ほどの例を応用し、学生をまず学年で並べ替えた後、各学年の学生を姓で並べ替えています。</span><span class="sxs-lookup"><span data-stu-id="7e339-185">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="7e339-186">`Group By` の詳細については、「[Group By 句](../../../language-reference/queries/group-by-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e339-186">For more information about `Group By`, see [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e339-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e339-187">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="7e339-188">Visual Basic の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="7e339-188">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="7e339-189">クエリ</span><span class="sxs-lookup"><span data-stu-id="7e339-189">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="7e339-190">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e339-190">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="7e339-191">LINQ</span><span class="sxs-lookup"><span data-stu-id="7e339-191">LINQ</span></span>](../../language-features/linq/index.md)
