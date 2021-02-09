---
description: '詳細情報: SELECT (Entity SQL)'
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 7feaf1d9a5101cb745e67afeba8d608104430e7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791869"
---
# <a name="select-entity-sql"></a><span data-ttu-id="1bdbc-103">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1bdbc-103">SELECT (Entity SQL)</span></span>

<span data-ttu-id="1bdbc-104">クエリで返される要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-104">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdbc-105">構文</span><span class="sxs-lookup"><span data-stu-id="1bdbc-105">Syntax</span></span>  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="1bdbc-106">引数</span><span class="sxs-lookup"><span data-stu-id="1bdbc-106">Arguments</span></span>  

 <span data-ttu-id="1bdbc-107">ALL</span><span class="sxs-lookup"><span data-stu-id="1bdbc-107">ALL</span></span>  
 <span data-ttu-id="1bdbc-108">結果セットに重複を含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-108">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="1bdbc-109">ALL は既定値です。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-109">ALL is the default.</span></span>  
  
 <span data-ttu-id="1bdbc-110">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="1bdbc-110">DISTINCT</span></span>  
 <span data-ttu-id="1bdbc-111">結果セットに一意な結果のみを含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-111">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="1bdbc-112">VALUE</span><span class="sxs-lookup"><span data-stu-id="1bdbc-112">VALUE</span></span>  
 <span data-ttu-id="1bdbc-113">1 つの項目のみを指定でき、row ラッパーを追加しません。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-113">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="1bdbc-114">`top(expr)`の形式で、クエリから返す最初の結果数を指定する有効な式。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-114">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="1bdbc-115">[ORDER BY](order-by-entity-sql.md) 演算子の LIMIT パラメーターにより、結果セットの最初の n 項目を選ぶこともできます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-115">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="1bdbc-116">次の形式の式。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-116">An expression of the form:</span></span>  
  
 <span data-ttu-id="1bdbc-117">`expr` as `identifier` &#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="1bdbc-117">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="1bdbc-118">リテラルまたは式。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-118">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bdbc-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="1bdbc-119">Remarks</span></span>  

 <span data-ttu-id="1bdbc-120">[FROM](from-entity-sql.md)、[GROUP BY](group-by-entity-sql.md)、[HAVING](having-entity-sql.md) 句が評価された後で、SELECT 句が評価されます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-120">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="1bdbc-121">SELECT 句は、FROM 句または外側のスコープから現在スコープ内にある項目のみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-121">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="1bdbc-122">GROUP BY 句を指定した場合、SELECT 句は GROUP BY キーの別名のみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-122">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="1bdbc-123">FROM 句の項目への参照は、集計関数でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-123">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="1bdbc-124">SELECT キーワードの後に続く 1 つまたは複数のクエリ式の一覧は、選択リスト (旧称、投影) と呼びます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-124">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="1bdbc-125">投影のより一般的な形式は、単一クエリ式です。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-125">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="1bdbc-126">次の例に示すように、コレクション `member1` からメンバー `collection1`を選択すると、 `member1` の各オブジェクトに対応するすべての `collection1`値の新しいコレクションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-126">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="1bdbc-127">たとえば、 `customers` が、タイプ `Customer` のコレクションで、このコレクションに、タイプ `Name` であるプロパティ `string`が含まれる場合、 `Name` から `customers` を選択すると、文字列のコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-127">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="1bdbc-128">JOIN 構文 (FULL、INNER、LEFT、OUTER、ON、および RIGHT) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-128">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="1bdbc-129">内部結合に対しては ON が必要ですが、クロス結合に対しては ON を使用できません。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-129">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="1bdbc-130">ROW 句および VALUE SELECT 句</span><span class="sxs-lookup"><span data-stu-id="1bdbc-130">Row and Value Select Clauses</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1bdbc-131">は、SELECT 句の 2 つのバリアントをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-131">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="1bdbc-132">最初のバリアント、row select は、SELECT キーワードによって識別され、このバリアントを使用して、投影する必要がある 1 つまたは複数の値を指定できます。row ラッパーは、返された値の前後に暗黙的に追加されるため、クエリ式の結果は常に、行のマルチセットになります。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-132">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="1bdbc-133">row select の各クエリ式は、別名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-133">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="1bdbc-134">別名を指定しないと、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は別名生成規則を使用して別名の生成を試みます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-134">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="1bdbc-135">SELECT 句のもう 1 つのバリアント、value select は SELECT VALUE キーワードによって識別されます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-135">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="1bdbc-136">このバリアントは、1 つの値のみを指定でき、row ラッパーを追加しません。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-136">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="1bdbc-137">次の例に示すように、row select は常に VALUE SELECT として表現できます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-137">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="1bdbc-138">ALL 修飾子および DISTINCT 修飾子</span><span class="sxs-lookup"><span data-stu-id="1bdbc-138">All and Distinct Modifiers</span></span>  

 <span data-ttu-id="1bdbc-139">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の SELECT のどちらのバリアントも ALL 修飾子または DISTINCT 修飾子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-139">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="1bdbc-140">DISTINCT 修飾子を指定した場合、SELECT 句まで (SELECT 句を含めて) のクエリ式によって生成されたコレクションから重複が除外されます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-140">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="1bdbc-141">ALL 修飾子が指定された場合、重複は除外されません。ALL 修飾子は既定値です。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-141">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="1bdbc-142">Transact-SQL との違い</span><span class="sxs-lookup"><span data-stu-id="1bdbc-142">Differences from Transact-SQL</span></span>  

 <span data-ttu-id="1bdbc-143">Transact-SQL とは異なり、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では SELECT 句で \* 引数を使用できません。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-143">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="1bdbc-144">代わりに、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、次の例に示すように、FROM 句からコレクションの別名を参照して、レコード全体にクエリを投影できます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-144">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="1bdbc-145">上の Transact-SQL クエリ式は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では次のように表されます。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-145">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="1bdbc-146">例</span><span class="sxs-lookup"><span data-stu-id="1bdbc-146">Example</span></span>  

 <span data-ttu-id="1bdbc-147">次の Entity SQL クエリは、SELECT 演算子を使用して、クエリによって返される要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-147">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="1bdbc-148">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-148">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1bdbc-149">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-149">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1bdbc-150">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-150">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1bdbc-151">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="1bdbc-151">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="1bdbc-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bdbc-152">See also</span></span>

- [<span data-ttu-id="1bdbc-153">クエリ式</span><span class="sxs-lookup"><span data-stu-id="1bdbc-153">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="1bdbc-154">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="1bdbc-154">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="1bdbc-155">TOP</span><span class="sxs-lookup"><span data-stu-id="1bdbc-155">TOP</span></span>](top-entity-sql.md)
