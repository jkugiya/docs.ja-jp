---
description: '詳細情報: ORDER BY (Entity SQL)'
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 092850e864ae95d50b615839265041a7e32b39a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696322"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="0e8d6-103">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0e8d6-103">ORDER BY (Entity SQL)</span></span>

<span data-ttu-id="0e8d6-104">SELECT ステートメントで返されるオブジェクトで使用される並べ替え順を指定します。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-104">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e8d6-105">構文</span><span class="sxs-lookup"><span data-stu-id="0e8d6-105">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e8d6-106">引数</span><span class="sxs-lookup"><span data-stu-id="0e8d6-106">Arguments</span></span>  

 `order_by_expression`  
 <span data-ttu-id="0e8d6-107">並べ替えるプロパティを指定する有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-107">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="0e8d6-108">並べ替えのキーとなる式を複数指定できます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-108">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="0e8d6-109">ORDER BY 句内に記述するキー式の並び順によって、並べ替えられた結果セットの構成が決まります。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-109">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="0e8d6-110">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="0e8d6-110">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="0e8d6-111">ORDER BY 操作が `collation_name`で指定された照合順序に従って実行されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-111">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="0e8d6-112">COLLATE は文字列式にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-112">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="0e8d6-113">ASC</span><span class="sxs-lookup"><span data-stu-id="0e8d6-113">ASC</span></span>  
 <span data-ttu-id="0e8d6-114">指定したプロパティの値が昇順、つまり小さい値から大きい値へと並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-114">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="0e8d6-115">既定値です。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-115">This is the default.</span></span>  
  
 <span data-ttu-id="0e8d6-116">DESC</span><span class="sxs-lookup"><span data-stu-id="0e8d6-116">DESC</span></span>  
 <span data-ttu-id="0e8d6-117">指定したプロパティの値が降順、つまり大きい値から小さい値へと並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-117">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="0e8d6-118">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="0e8d6-118">LIMIT `n`</span></span>  
 <span data-ttu-id="0e8d6-119">最初の `n` 個の項目のみが選択されます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-119">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="0e8d6-120">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="0e8d6-120">SKIP `n`</span></span>  
 <span data-ttu-id="0e8d6-121">最初の `n` 個の項目をスキップします。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-121">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e8d6-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="0e8d6-122">Remarks</span></span>  

 <span data-ttu-id="0e8d6-123">ORDER BY 句は、SELECT 句の結果に論理的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-123">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="0e8d6-124">ORDER BY 句では、別名を使用して選択リストの項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-124">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="0e8d6-125">ORDER BY 句は、現在スコープ内にあるその他の変数も参照できます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-125">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="0e8d6-126">ただし、SELECT 句が DISTINCT 修飾子で指定されている場合は、ORDER BY 句は SELECT 句の別名のみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-126">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="0e8d6-127">ORDER BY 句内の各式は、順序付けられた不等号 (より小さい、より大きいなど) について比較できる型として評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-127">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="0e8d6-128">通常、これらの型は数値、文字列、日付などのスカラー プリミティブです。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-128">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="0e8d6-129">比較できる型の RowType は順序も比較できます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-129">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="0e8d6-130">順序付けされたセットで、最上位の投影を除きコードが反復処理を行う場合、出力でその順序が維持されることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-130">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="0e8d6-131">次の例では、順序が維持されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-131">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="0e8d6-132">次のクエリでは、入れ子になったクエリの順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-132">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="0e8d6-133">UNION、UNION ALL、EXCEPT、または INTERSECT 操作を順序付けするには、次のパターンを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-133">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="0e8d6-134">制限付きのキーワード</span><span class="sxs-lookup"><span data-stu-id="0e8d6-134">Restricted keywords</span></span>  

 <span data-ttu-id="0e8d6-135">次のキーワードは `ORDER BY` 句で使用する場合には、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-135">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="0e8d6-136">CROSS</span><span class="sxs-lookup"><span data-stu-id="0e8d6-136">CROSS</span></span>  
  
- <span data-ttu-id="0e8d6-137">FULL</span><span class="sxs-lookup"><span data-stu-id="0e8d6-137">FULL</span></span>  
  
- <span data-ttu-id="0e8d6-138">KEY</span><span class="sxs-lookup"><span data-stu-id="0e8d6-138">KEY</span></span>  
  
- <span data-ttu-id="0e8d6-139">左方向 (←) キー</span><span class="sxs-lookup"><span data-stu-id="0e8d6-139">LEFT</span></span>  
  
- <span data-ttu-id="0e8d6-140">ORDER</span><span class="sxs-lookup"><span data-stu-id="0e8d6-140">ORDER</span></span>  
  
- <span data-ttu-id="0e8d6-141">OUTER</span><span class="sxs-lookup"><span data-stu-id="0e8d6-141">OUTER</span></span>  
  
- <span data-ttu-id="0e8d6-142">右方向 (→) キー</span><span class="sxs-lookup"><span data-stu-id="0e8d6-142">RIGHT</span></span>  
  
- <span data-ttu-id="0e8d6-143">ROW</span><span class="sxs-lookup"><span data-stu-id="0e8d6-143">ROW</span></span>  
  
- <span data-ttu-id="0e8d6-144">VALUE</span><span class="sxs-lookup"><span data-stu-id="0e8d6-144">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="0e8d6-145">入れ子になったクエリの順序</span><span class="sxs-lookup"><span data-stu-id="0e8d6-145">Ordering Nested Queries</span></span>  

 <span data-ttu-id="0e8d6-146">Entity Framework では、入れ子になった式をクエリ内の任意の場所に配置できるため、入れ子になったクエリの順序は維持されません。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-146">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="0e8d6-147">次のクエリでは、結果が姓の順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-147">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="0e8d6-148">次のクエリでは、入れ子になったクエリの順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-148">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="0e8d6-149">例</span><span class="sxs-lookup"><span data-stu-id="0e8d6-149">Example</span></span>  

 <span data-ttu-id="0e8d6-150">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-150">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="0e8d6-151">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-151">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0e8d6-152">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-152">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0e8d6-153">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-153">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0e8d6-154">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="0e8d6-154">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="0e8d6-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e8d6-155">See also</span></span>

- [<span data-ttu-id="0e8d6-156">クエリ式</span><span class="sxs-lookup"><span data-stu-id="0e8d6-156">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="0e8d6-157">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="0e8d6-157">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="0e8d6-158">SKIP</span><span class="sxs-lookup"><span data-stu-id="0e8d6-158">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="0e8d6-159">LIMIT</span><span class="sxs-lookup"><span data-stu-id="0e8d6-159">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="0e8d6-160">TOP</span><span class="sxs-lookup"><span data-stu-id="0e8d6-160">TOP</span></span>](top-entity-sql.md)
