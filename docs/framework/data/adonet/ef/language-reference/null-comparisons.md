---
description: '詳細情報: NULL 比較'
title: NULL 比較
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 3f2165cae56b6987330612cd2c9e21dfe8606fb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696361"
---
# <a name="null-comparisons"></a><span data-ttu-id="50c1b-103">NULL 比較</span><span class="sxs-lookup"><span data-stu-id="50c1b-103">Null Comparisons</span></span>

<span data-ttu-id="50c1b-104">データ ソースの `null` 値は不明な値を表します。</span><span class="sxs-lookup"><span data-stu-id="50c1b-104">A `null` value in the data source indicates that the value is unknown.</span></span> <span data-ttu-id="50c1b-105">LINQ to Entities クエリでは、null 値をチェックして、必ず null でない有効なデータを持つ行に特定の計算または比較を行うようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-105">In LINQ to Entities queries, you can check for null values so that certain calculations or comparisons are only performed on rows that have valid, or non-null, data.</span></span> <span data-ttu-id="50c1b-106">ただし、CLR の NULL セマンティクスは、データ ソースの NULL セマンティクスとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="50c1b-106">CLR null semantics, however, may differ from the null semantics of the data source.</span></span> <span data-ttu-id="50c1b-107">ほとんどのデータベースでは、3 値論理を使用して NULL 比較を処理します。</span><span class="sxs-lookup"><span data-stu-id="50c1b-107">Most databases use a version of three-valued logic to handle null comparisons.</span></span> <span data-ttu-id="50c1b-108">つまり、null 値との比較は `true` にも `false` にも評価されず、`unknown` に評価されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-108">That is, a comparison against a null value does not evaluate to `true` or `false`, it evaluates to `unknown`.</span></span> <span data-ttu-id="50c1b-109">これは、多くの場合は ANSI NULL の実装ですが、そうでない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="50c1b-109">Often this is an implementation of ANSI nulls, but this is not always the case.</span></span>  
  
 <span data-ttu-id="50c1b-110">SQL Server の既定では、NULL = NULL の比較は NULL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="50c1b-110">By default in SQL Server, the null-equals-null comparison returns a null value.</span></span> <span data-ttu-id="50c1b-111">次の例では、`ShipDate` が null である行が結果セットから除外され、Transact-SQL ステートメントからは 0 行が返されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-111">In the following example, the rows where `ShipDate` is null are excluded from the result set, and the Transact-SQL statement would return 0 rows.</span></span>  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 <span data-ttu-id="50c1b-112">これは、NULL = NULL の比較が true を返す CLR の NULL セマンティクスとは大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="50c1b-112">This is very different from the CLR null semantics, where the null-equals-null comparison returns true.</span></span>  
  
 <span data-ttu-id="50c1b-113">次の LINQ クエリは CLR で表されますが、データ ソースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-113">The following LINQ query is expressed in the CLR, but it is executed in the data source.</span></span> <span data-ttu-id="50c1b-114">CLR セマンティクスがデータ ソースで使用される保証はないため、動作は予測できません。</span><span class="sxs-lookup"><span data-stu-id="50c1b-114">Because there is no guarantee that CLR semantics will be honored at the data source, the expected behavior is indeterminate.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a><span data-ttu-id="50c1b-115">キー セレクター</span><span class="sxs-lookup"><span data-stu-id="50c1b-115">Key Selectors</span></span>  

 <span data-ttu-id="50c1b-116">"*キー セレクター*" とは、要素からキーを抽出するために標準クエリ演算子で使用される関数です。</span><span class="sxs-lookup"><span data-stu-id="50c1b-116">A *key selector* is a function used in the standard query operators to extract a key from an element.</span></span> <span data-ttu-id="50c1b-117">キー セレクター関数では、式を定数と比較できます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-117">In the key selector function, an expression can be compared with a constant.</span></span> <span data-ttu-id="50c1b-118">式が NULL 定数と比較される場合、または 2 つの NULL 定数が比較される場合、CLR の NULL セマンティクスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-118">CLR null semantics are exhibited if an expression is compared to a null constant or if two null constants are compared.</span></span> <span data-ttu-id="50c1b-119">データ ソースの NULL 値を持つ 2 つの列が比較される場合は、ストア NULL セマンティクスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-119">Store null semantics are exhibited if two columns with null values in the data source are compared.</span></span> <span data-ttu-id="50c1b-120">キー セレクターは、<xref:System.Linq.Queryable.GroupBy%2A> など、グループ化や並べ替えの標準クエリ演算子で使用される場合が多く、クエリ結果の並べ替えやグループ化に使用するキーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-120">Key selectors are found in many of the grouping and ordering standard query operators, such as <xref:System.Linq.Queryable.GroupBy%2A>, and are used to select keys by which to order or group the query results.</span></span>  
  
## <a name="null-property-on-a-null-object"></a><span data-ttu-id="50c1b-121">NULL オブジェクトの NULL プロパティ</span><span class="sxs-lookup"><span data-stu-id="50c1b-121">Null Property on a Null Object</span></span>  

 <span data-ttu-id="50c1b-122">Entity Framework では、null オブジェクトのプロパティは null です。</span><span class="sxs-lookup"><span data-stu-id="50c1b-122">In the Entity Framework, the properties of a null object are null.</span></span> <span data-ttu-id="50c1b-123">CLR で NULL オブジェクトのプロパティを参照しようとすると、<xref:System.NullReferenceException> が返されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-123">When you attempt to reference a property of a null object in the CLR, you will receive a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="50c1b-124">LINQ クエリに NULL オブジェクトのプロパティが含まれている場合、動作の一貫性が失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="50c1b-124">When a LINQ query involves a property of a null object, this can result in inconsistent behavior.</span></span>  
  
 <span data-ttu-id="50c1b-125">たとえば、次のクエリでは、`NewProduct` へのキャストはコマンド ツリー レイヤーで行われ、`Introduced` プロパティが NULL になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50c1b-125">For example, in the following query, the cast to `NewProduct` is done in the command tree layer, which might result in the `Introduced` property being null.</span></span> <span data-ttu-id="50c1b-126"><xref:System.DateTime> の比較が true に評価されるように NULL 比較がデータベースで定義されている場合に、その行が含められます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-126">If the database defined null comparisons such that the <xref:System.DateTime> comparison evaluates to true, the row will be included.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a><span data-ttu-id="50c1b-127">集計関数に NULL コレクションを渡す</span><span class="sxs-lookup"><span data-stu-id="50c1b-127">Passing Null Collections to Aggregate Functions</span></span>  

 <span data-ttu-id="50c1b-128">LINQ to Entities では、`IQueryable` をサポートするコレクションを集計関数に渡すと、データベースで集計演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-128">In LINQ to Entities, when you pass a collection that supports `IQueryable` to an aggregate function, aggregate operations are performed at the database.</span></span> <span data-ttu-id="50c1b-129">メモリで実行されたクエリとデータベースで実行されたクエリの結果は、異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50c1b-129">There might be differences in the results of a query that was performed in-memory and a query that was performed at the database.</span></span> <span data-ttu-id="50c1b-130">メモリ内のクエリでは、一致するものがなければ 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-130">With an in-memory query, if there are no matches, the query returns zero.</span></span> <span data-ttu-id="50c1b-131">データベースでは、これと同じクエリから `null` が返されます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-131">At the database, the same query returns `null`.</span></span> <span data-ttu-id="50c1b-132">`null` 値が LINQ 集計関数に渡されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="50c1b-132">If a `null` value is passed to a LINQ aggregate function, an exception will be thrown.</span></span> <span data-ttu-id="50c1b-133">`null` 値を受け入れるには、型、およびクエリ結果を受け取るその型のプロパティを Null 許容値型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="50c1b-133">To accept possible `null` values, cast the types and the properties of the types that receive query results to nullable value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c1b-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="50c1b-134">See also</span></span>

- [<span data-ttu-id="50c1b-135">LINQ to Entities クエリ内の式</span><span class="sxs-lookup"><span data-stu-id="50c1b-135">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
