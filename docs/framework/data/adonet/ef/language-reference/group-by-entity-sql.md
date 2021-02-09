---
description: '詳細情報: GROUP BY (Entity SQL)'
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 16328b46a59a2a07622cda43dce30d8b4f1d3dde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696933"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="c3165-103">GROUP BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c3165-103">GROUP BY (Entity SQL)</span></span>

<span data-ttu-id="c3165-104">クエリ ([SELECT](select-entity-sql.md)) 式によって返されるオブジェクトをグループ化するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="c3165-104">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3165-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3165-105">Syntax</span></span>  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c3165-106">引数</span><span class="sxs-lookup"><span data-stu-id="c3165-106">Arguments</span></span>  

 `aliasedExpression`  
 <span data-ttu-id="c3165-107">グループ化の実行対象となる有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="c3165-107">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="c3165-108">`expression` には、プロパティを指定することも、FROM 句から返されたプロパティを参照する非集計式を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3165-108">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="c3165-109">GROUP BY 句内の各式は、等価かどうかを比較できる型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3165-109">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="c3165-110">通常、これらの型は数値、文字列、日付などのスカラー プリミティブです。</span><span class="sxs-lookup"><span data-stu-id="c3165-110">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="c3165-111">コレクション別にグループ化することはできません。</span><span class="sxs-lookup"><span data-stu-id="c3165-111">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3165-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c3165-112">Remarks</span></span>  

 <span data-ttu-id="c3165-113">SELECT 句の \<select list> に集計関数が含まれている場合は、GROUP BY によって各グループの集計値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="c3165-113">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="c3165-114">GROUP BY を指定する場合は、選択リスト内の非集計式内の各プロパティ名が GROUP BY リストに含まれるか、GROUP BY 式が選択リスト式に正確に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3165-114">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3165-115">ORDER BY 句を指定しない場合、GROUP BY 句でグループが返される順序には特に決まりはありません。</span><span class="sxs-lookup"><span data-stu-id="c3165-115">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="c3165-116">データの特定の順序を指定するには、常に ORDER BY 句を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c3165-116">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="c3165-117">GROUP BY 句を明示的または暗黙的に指定した場合 (たとえばクエリ内の HAVING 句)、現在のスコープは非表示になり、新しいスコープが導入されます。</span><span class="sxs-lookup"><span data-stu-id="c3165-117">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="c3165-118">SELECT 句、HAVING 句、および ORDER BY 句は、FROM 句で指定された要素名を参照することはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="c3165-118">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="c3165-119">ユーザーが参照できるのは、グループ化式自体だけです。</span><span class="sxs-lookup"><span data-stu-id="c3165-119">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="c3165-120">このためには、新しい名前 (別名) を各グループ化式に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c3165-120">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="c3165-121">グループ化式に別名が指定されていない場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、次の例に示すように別名生成規則を使用することによって別名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c3165-121">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="c3165-122">GROUP BY 句の式は、同じ GROUP BY 句で前に定義された名前を参照できません。</span><span class="sxs-lookup"><span data-stu-id="c3165-122">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="c3165-123">名前のグループ化に加え、SELECT 句、HAVING 句、および ORDER BY 句で集計を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3165-123">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="c3165-124">集計には、グループの各要素について評価される式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3165-124">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="c3165-125">集計演算子により、これらのすべての式の値の数が減少します (ただし、必ずしも単一の値になるとは限りません)。</span><span class="sxs-lookup"><span data-stu-id="c3165-125">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="c3165-126">集計式は、現在のスコープに表示される基の要素名、または GROUP BY 句自体によって導入された新しい任意の名前を参照できます。</span><span class="sxs-lookup"><span data-stu-id="c3165-126">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="c3165-127">集計は SELECT 句、HAVING 句、および ORDER BY 句に含まれますが、次の例で示すとおり、実際にはグループ化式と同じスコープで評価されます。</span><span class="sxs-lookup"><span data-stu-id="c3165-127">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="c3165-128">このクエリは GROUP BY 句を使用して、注文した全製品の価格のレポートを製品別に分類して生成します。</span><span class="sxs-lookup"><span data-stu-id="c3165-128">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="c3165-129">グループ化式の一部として、製品に `name` という名前を付け、SELECT リストでその名前を参照します。</span><span class="sxs-lookup"><span data-stu-id="c3165-129">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="c3165-130">さらに、注文明細の価格と数量を内部で参照する SELECT リスト内の集計 `sum` を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3165-130">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="c3165-131">各 GROUP By キー式には、入力スコープへの参照が少なくとも 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="c3165-131">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="c3165-132">GROUP BY を使用する場合の例については、「 [HAVING](having-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c3165-132">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3165-133">例</span><span class="sxs-lookup"><span data-stu-id="c3165-133">Example</span></span>  

 <span data-ttu-id="c3165-134">次の Entity SQL クエリでは、GROUP BY 演算子を使用して、クエリによって返されるオブジェクトをグループ化するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="c3165-134">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="c3165-135">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c3165-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c3165-136">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c3165-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c3165-137">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c3165-137">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="c3165-138">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c3165-138">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="c3165-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3165-139">See also</span></span>

- [<span data-ttu-id="c3165-140">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="c3165-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c3165-141">クエリ式</span><span class="sxs-lookup"><span data-stu-id="c3165-141">Query Expressions</span></span>](query-expressions-entity-sql.md)
