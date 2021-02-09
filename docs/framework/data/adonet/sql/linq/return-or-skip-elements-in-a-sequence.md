---
description: '詳細情報: シーケンスの要素の取得またはスキップ'
title: シーケンスの要素の取得またはスキップ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 6eba93562d4c6a8ffa4150453deed88844d4e297
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695139"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="0764d-103">シーケンスの要素の取得またはスキップ</span><span class="sxs-lookup"><span data-stu-id="0764d-103">Return Or Skip Elements in a Sequence</span></span>

<span data-ttu-id="0764d-104"><xref:System.Linq.Queryable.Take%2A> 演算子を使用すると、シーケンス内の指定された数の要素を返し、残りをスキップできます。</span><span class="sxs-lookup"><span data-stu-id="0764d-104">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="0764d-105"><xref:System.Linq.Queryable.Skip%2A> 演算子を使用すると、シーケンス内の指定された数の要素をスキップし、残りを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="0764d-105">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0764d-106"><xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を SQL Server 2000 に対するクエリで使用する場合は、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="0764d-106"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="0764d-107">詳しくは、「[トラブルシューティング](troubleshooting.md)」の「SQL Server 2000 の Skip 例外と Take 例外」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0764d-107">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0764d-108">では、SQL の `NOT EXISTS` 句を含むサブクエリを使用して、<xref:System.Linq.Queryable.Skip%2A> が変換されます。</span><span class="sxs-lookup"><span data-stu-id="0764d-108">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="0764d-109">この変換には、次のような制限があります。</span><span class="sxs-lookup"><span data-stu-id="0764d-109">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="0764d-110">引数は、セットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0764d-110">The argument must be a set.</span></span> <span data-ttu-id="0764d-111">順序が指定されていてもマルチセットはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="0764d-111">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="0764d-112">生成されるクエリは、<xref:System.Linq.Queryable.Skip%2A> が適用される基本クエリに対して生成されるクエリより複雑な場合があります。</span><span class="sxs-lookup"><span data-stu-id="0764d-112">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="0764d-113">複雑なために、パフォーマンスが低下したり、タイムアウトが発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="0764d-113">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0764d-114">例</span><span class="sxs-lookup"><span data-stu-id="0764d-114">Example</span></span>  

 <span data-ttu-id="0764d-115">次の例では、`Take` を使用して、雇用された最初の 5 人の `Employees` を選択します。</span><span class="sxs-lookup"><span data-stu-id="0764d-115">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="0764d-116">コレクションは最初、`HireDate` 順に並べられます。</span><span class="sxs-lookup"><span data-stu-id="0764d-116">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="0764d-117">例</span><span class="sxs-lookup"><span data-stu-id="0764d-117">Example</span></span>  

 <span data-ttu-id="0764d-118">次の例では、<xref:System.Linq.Queryable.Skip%2A> を使用して、最も値段が高い 10 個の `Products` 以外のすべてを選択します。</span><span class="sxs-lookup"><span data-stu-id="0764d-118">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="0764d-119">例</span><span class="sxs-lookup"><span data-stu-id="0764d-119">Example</span></span>  

 <span data-ttu-id="0764d-120">次の例では、<xref:System.Linq.Queryable.Skip%2A> メソッドと <xref:System.Linq.Queryable.Take%2A> メソッドを組み合わせて、最初の 50 レコードをスキップし、次の 10 レコードを返します。</span><span class="sxs-lookup"><span data-stu-id="0764d-120">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="0764d-121"><xref:System.Linq.Queryable.Take%2A> 操作と <xref:System.Linq.Queryable.Skip%2A> 操作は、順序付けされたセットに対してのみ正しく定義されます。</span><span class="sxs-lookup"><span data-stu-id="0764d-121"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="0764d-122">順序付けされていないセットまたはマルチセットのセマンティクスは未定義です。</span><span class="sxs-lookup"><span data-stu-id="0764d-122">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="0764d-123">SQL での順序付けの制限により、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、<xref:System.Linq.Queryable.Take%2A> 演算子または <xref:System.Linq.Queryable.Skip%2A> 演算子の引数の順序を、演算子の結果に移動することを試みます。</span><span class="sxs-lookup"><span data-stu-id="0764d-123">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0764d-124">SQL Server 2000 と SQL Server 2005 では変換が異なります。</span><span class="sxs-lookup"><span data-stu-id="0764d-124">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="0764d-125">複雑さに関係なくクエリで <xref:System.Linq.Queryable.Skip%2A> を使用する場合は、SQL Server 2005 を使用します。</span><span class="sxs-lookup"><span data-stu-id="0764d-125">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="0764d-126">SQL Server 2000 の場合は次のような [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のクエリを検討します。</span><span class="sxs-lookup"><span data-stu-id="0764d-126">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0764d-127">は、次に示すように、順序付けを SQL コードの最後に移動します。</span><span class="sxs-lookup"><span data-stu-id="0764d-127">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="0764d-128"><xref:System.Linq.Queryable.Take%2A> と <xref:System.Linq.Queryable.Skip%2A> を連結する場合は、指定されているすべての順序が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0764d-128">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="0764d-129">それ以外の場合、結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="0764d-129">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="0764d-130">SQL の仕様に基づく負でない定数の整数引数に対して、<xref:System.Linq.Queryable.Take%2A> と <xref:System.Linq.Queryable.Skip%2A> の両方とも正しく定義されます。</span><span class="sxs-lookup"><span data-stu-id="0764d-130">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0764d-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0764d-131">See also</span></span>

- [<span data-ttu-id="0764d-132">クエリの例</span><span class="sxs-lookup"><span data-stu-id="0764d-132">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="0764d-133">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="0764d-133">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
