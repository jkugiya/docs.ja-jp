---
description: '詳細情報: HAVING (Entity SQL)'
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 70ace20d67e93aa051873d2b32a49f560902e63d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696881"
---
# <a name="having-entity-sql"></a><span data-ttu-id="c5209-103">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c5209-103">HAVING (Entity SQL)</span></span>

<span data-ttu-id="c5209-104">グループまたは集計の検索条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5209-104">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5209-105">構文</span><span class="sxs-lookup"><span data-stu-id="c5209-105">Syntax</span></span>  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5209-106">引数</span><span class="sxs-lookup"><span data-stu-id="c5209-106">Arguments</span></span>  

 `search_condition`  
 <span data-ttu-id="c5209-107">グループまたは集計の検索条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5209-107">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="c5209-108">HAVING 句を GROUP BY ALL と共に使用した場合、HAVING 句により ALL はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="c5209-108">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5209-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c5209-109">Remarks</span></span>  

 <span data-ttu-id="c5209-110">HAVING 句は、グループ化の結果について追加的なフィルター処理条件を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c5209-110">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="c5209-111">クエリ式で GROUP BY 句が指定されていないと、暗黙的な単独セットのグループになります。</span><span class="sxs-lookup"><span data-stu-id="c5209-111">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5209-112">HAVING は、[SELECT](select-entity-sql.md) ステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5209-112">HAVING can be used only with the [SELECT](select-entity-sql.md) statement.</span></span> <span data-ttu-id="c5209-113">[GROUP BY](group-by-entity-sql.md) が使われていない場合、HAVING は WHERE 句のように動作します。</span><span class="sxs-lookup"><span data-stu-id="c5209-113">When [GROUP BY](group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
<span data-ttu-id="c5209-114">GROUP BY 操作後に適用される場合を除いて、HAVING 句は WHERE 句と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="c5209-114">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="c5209-115">つまり、次の例のように、HAVING 句では別名および集計のグループ化のみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="c5209-115">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example:</span></span>
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="c5209-116">前述のグループは、複数の製品を含むグループのみに制限されています。</span><span class="sxs-lookup"><span data-stu-id="c5209-116">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5209-117">例</span><span class="sxs-lookup"><span data-stu-id="c5209-117">Example</span></span>  

 <span data-ttu-id="c5209-118">次の Entity SQL のクエリでは、HAVING および GROUP BY 操作を使用して、グループまたは集計の検索条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5209-118">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="c5209-119">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c5209-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c5209-120">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c5209-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c5209-121">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c5209-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="c5209-122">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c5209-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a><span data-ttu-id="c5209-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5209-123">See also</span></span>

- [<span data-ttu-id="c5209-124">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="c5209-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c5209-125">クエリ式</span><span class="sxs-lookup"><span data-stu-id="c5209-125">Query Expressions</span></span>](query-expressions-entity-sql.md)
