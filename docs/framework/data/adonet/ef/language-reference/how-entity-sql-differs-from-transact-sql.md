---
description: '詳細情報: Entity SQL と Transact-SQL の相違点'
title: Entity SQL と Transact-SQL の相違点
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 349dd64cc0e548ab0dc8d0e66e8bb14b58912d09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696868"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="fbd6a-103">Entity SQL と Transact-SQL の相違点</span><span class="sxs-lookup"><span data-stu-id="fbd6a-103">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="fbd6a-104">この記事では、Entity SQL と Transact-SQL の相違点について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-104">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="fbd6a-105">継承とリレーションシップのサポート</span><span class="sxs-lookup"><span data-stu-id="fbd6a-105">Inheritance and Relationships Support</span></span>  

 <span data-ttu-id="fbd6a-106">Entity SQL では、エンティティの概念スキーマが直接操作され、継承やリレーションシップなどの概念モデル機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-106">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="fbd6a-107">継承を操作するときは、スーパータイプ インスタンスのコレクションからサブタイプのインスタンスを選択すると便利である場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-107">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="fbd6a-108">Entity SQL 内の [oftype](oftype-entity-sql.md) 演算子 (C# シーケンスの `oftype` に相当) によってこの機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-108">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="fbd6a-109">コレクションのサポート</span><span class="sxs-lookup"><span data-stu-id="fbd6a-109">Support for Collections</span></span>  

 <span data-ttu-id="fbd6a-110">Entity SQL では、コレクションがファーストクラスのエンティティとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-110">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="fbd6a-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-111">For example:</span></span>  
  
- <span data-ttu-id="fbd6a-112">コレクションの式は、`from` 句内で有効です。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-112">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="fbd6a-113">`in` サブクエリと `exists` サブクエリは任意のコレクションを使用できるように一般化されています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-113">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="fbd6a-114">サブクエリは一種のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-114">A subquery is one kind of collection.</span></span> <span data-ttu-id="fbd6a-115">`e1 in e2` および `exists(e)` は、これらの演算を実行する Entity SQL 構造です。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-115">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="fbd6a-116">`union`、`intersect`、`except` などの集合演算は、現在ではコレクションに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-116">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="fbd6a-117">結合はコレクションに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-117">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="fbd6a-118">式のサポート</span><span class="sxs-lookup"><span data-stu-id="fbd6a-118">Support for Expressions</span></span>  

 <span data-ttu-id="fbd6a-119">Transact-SQL にはサブクエリ (テーブル) と式 (行と列) があります。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-119">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="fbd6a-120">コレクションおよび入れ子になったコレクションをサポートするために、Entity SQL ではすべてが式として扱われます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-120">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="fbd6a-121">Entity SQL は Transact-SQL よりコンポーザブルであり、すべての式をどこにでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-121">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="fbd6a-122">クエリ式は常に投射型のコレクションとなり、コレクション式が許可されている任意の場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-122">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="fbd6a-123">Entity SQL でサポートされていない Transact-SQL の式について詳しくは、「[サポートされていない式](unsupported-expressions-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-123">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="fbd6a-124">次の Entity SQL クエリはすべて有効です。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-124">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="fbd6a-125">サブクエリの一貫した処理</span><span class="sxs-lookup"><span data-stu-id="fbd6a-125">Uniform Treatment of Subqueries</span></span>  

 <span data-ttu-id="fbd6a-126">Transact-SQL では、テーブルに重点を置いてサブクエリのコンテキストが解釈されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-126">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="fbd6a-127">たとえば、`from` 句内のサブクエリは、マルチセット (テーブル) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-127">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="fbd6a-128">ただし、`select` 句で使用される同じサブクエリは、スカラー サブクエリと見なされます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-128">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="fbd6a-129">同様に、`in` 演算子の左側で使用されるサブクエリはスカラー サブクエリと見なされますが、右側で使用されるサブクエリはマルチセット サブクエリと見なされます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-129">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="fbd6a-130">Entity SQL ではこれらの違いが排除されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-130">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="fbd6a-131">式は、使用するコンテキストに依存しない、一貫した方法で解釈されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-131">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="fbd6a-132">Entity SQL では、すべてのサブクエリがマルチセット サブクエリと見なされます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-132">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="fbd6a-133">サブクエリでスカラー値が必要な場合のために、Entity SQL には `anyelement` 演算子が用意されています。この演算子はコレクション (この場合はサブクエリ) に対して演算を行い、コレクションからシングルトン値を抽出します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-133">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="fbd6a-134">サブクエリの暗黙の強制型変換の回避</span><span class="sxs-lookup"><span data-stu-id="fbd6a-134">Avoiding Implicit Coercions for Subqueries</span></span>  

 <span data-ttu-id="fbd6a-135">サブクエリの一貫した処理に伴う二次的作用として、スカラー値へのサブクエリの暗黙的な変換があります。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-135">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="fbd6a-136">具体的には、Transact-SQL では、単一フィールドの行のマルチセットはそのフィールドのデータ型を持つスカラー値に暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-136">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="fbd6a-137">Entity SQL では、この暗黙の強制型変換をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-137">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="fbd6a-138">Entity SQL では、コレクションからシングルトン値を抽出するための `ANYELEMENT` 演算子と、クエリ式の実行中に row ラッパーの作成を回避するための `select value` 句が提供されています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-138">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="fbd6a-139">SELECT VALUE: 暗黙の row ラッパーの回避</span><span class="sxs-lookup"><span data-stu-id="fbd6a-139">Select Value: Avoiding the Implicit Row Wrapper</span></span>  

 <span data-ttu-id="fbd6a-140">Transact-SQL サブクエリ内の SELECT 句では、句内の項目に row ラッパーが暗黙的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-140">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="fbd6a-141">これは、スカラーやオブジェクトのコレクションを作成できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-141">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="fbd6a-142">Transact-SQL では、1 つのフィールドの `rowtype` と、同じデータ型のシングルトン値との間の暗黙の強制型変換が許可されています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-142">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="fbd6a-143">Entity SQL には、暗黙の行の構築をスキップする `select value` 句が用意されています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-143">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="fbd6a-144">`select value` 句には 1 つの項目のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-144">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="fbd6a-145">このような句を使用した場合、`select` 句内の項目には row ラッパーは構築されず、目的の構造を持つコレクションを作成できます (例: `select value a`)。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-145">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="fbd6a-146">Entity SQL には、任意の行を構築するための行コンストラクターも用意されています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-146">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="fbd6a-147">`select` は、プロジェクションの 1 つ以上の要素を受け取り、フィールドを持つデータ レコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-147">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="fbd6a-148">左の相関関係と別名定義</span><span class="sxs-lookup"><span data-stu-id="fbd6a-148">Left Correlation and Aliasing</span></span>  

 <span data-ttu-id="fbd6a-149">Transact-SQL では、1 つのスコープ内の式 (`select` や `from` のような単一句) は同じスコープ内で先に定義された式を参照できません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-149">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="fbd6a-150">一部の SQL 言語仕様 (Transact-SQL を含む) では、`from` 句でこれらが制限付きでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-150">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="fbd6a-151">Entity SQL では `from` 句における左の相関関係が一般化され、一貫した方法でこれらが扱われます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-151">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="fbd6a-152">`from` 句内の式は、追加の構文を使用せずに、同じ句内で先に作成された定義 (左側の定義) を参照できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-152">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="fbd6a-153">Entity SQL では、`group by` 句を伴うクエリにも追加の制限が課されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-153">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="fbd6a-154">このようなクエリの `select` 句および `having` 句内の式では、別名を使用した場合にのみ `group by` キーを参照できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-154">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="fbd6a-155">次の構造は Transact-SQL では有効ですが、Entity SQL では無効です。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-155">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="fbd6a-156">Entity SQL でこれを行うには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-156">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="fbd6a-157">テーブル (コレクション) の列 (プロパティ) の参照</span><span class="sxs-lookup"><span data-stu-id="fbd6a-157">Referencing Columns (Properties) of Tables (Collections)</span></span>  

 <span data-ttu-id="fbd6a-158">Entity SQL 内の列の参照は、すべてテーブルの別名を使用して修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-158">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="fbd6a-159">次のコンストラクトは Transact-SQL では有効ですが、Entity SQL では無効です (`a` がテーブル `T` の有効な列である場合)。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-159">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="fbd6a-160">Entity SQL の形式は次のようになります</span><span class="sxs-lookup"><span data-stu-id="fbd6a-160">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="fbd6a-161">テーブルの別名は `from` 句では省略できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-161">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="fbd6a-162">テーブル名は暗黙的な別名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-162">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="fbd6a-163">Entity SQL では次の形式も使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-163">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="fbd6a-164">オブジェクト間の移動</span><span class="sxs-lookup"><span data-stu-id="fbd6a-164">Navigation Through Objects</span></span>  

 <span data-ttu-id="fbd6a-165">Transact-SQL では、テーブルの列または行の参照に "." 表記が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-165">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="fbd6a-166">Entity SQL では (プログラミング言語に由来する) この表記が拡張され、オブジェクトのプロパティ間の移動がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-166">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="fbd6a-167">たとえば、`p` が Person 型の式である場合、この人の住所の市区町村を参照するには次の Entity SQL 構文が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-167">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="fbd6a-168">\* のサポートなし</span><span class="sxs-lookup"><span data-stu-id="fbd6a-168">No Support for \*</span></span>  

 <span data-ttu-id="fbd6a-169">Transact-SQL では、修飾されていない \* 構文は行全体の別名としてサポートされており、修飾された \* 構文 (t.\*) はそのテーブルのフィールドのショートカットとしてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-169">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="fbd6a-170">また、Transact-SQL では NULL を含む特殊な count(\*) 集計も使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-170">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="fbd6a-171">Entity SQL では、\* 構造がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-171">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="fbd6a-172">`select * from T` および `select T1.* from T1, T2...` の形式の Transact-SQL クエリは、Entity SQL ではそれぞれ `select value t from T as t` および `select value t1 from T1 as t1, T2 as t2...` として表すことができます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-172">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="fbd6a-173">また、これらの構造は継承 (値の置換可能性) に対応していますが、`select *` Variant 型では宣言された型の最上位レベルのプロパティに限定されています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-173">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="fbd6a-174">Entity SQL では、`count(*)` 集約がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-174">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="fbd6a-175">代わりに、`count(0)` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-175">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="fbd6a-176">Group By への変更</span><span class="sxs-lookup"><span data-stu-id="fbd6a-176">Changes to Group By</span></span>  

 <span data-ttu-id="fbd6a-177">Entity SQL では `group by` キーの別名定義がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-177">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="fbd6a-178">`select` 句および `having` 句内の式では、これらの別名を使用して `group by` キーを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-178">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="fbd6a-179">たとえば、次の Entity SQL 構文です。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-179">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="fbd6a-180">これは、次の Transact-SQL と同じです。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-180">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="fbd6a-181">コレクションベースの集計</span><span class="sxs-lookup"><span data-stu-id="fbd6a-181">Collection-Based Aggregates</span></span>  

 <span data-ttu-id="fbd6a-182">Entity SQL では、2 種類の集約がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-182">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="fbd6a-183">コレクションベースの集計は、コレクションに対して演算を行い、集計結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-183">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="fbd6a-184">これらはクエリ内の任意の場所で使用でき、`group by` 句を必要としません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-184">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="fbd6a-185">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-185">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="fbd6a-186">Entity SQL では、SQL スタイルの集約もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-186">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="fbd6a-187">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-187">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="fbd6a-188">ORDER BY 句の使用法</span><span class="sxs-lookup"><span data-stu-id="fbd6a-188">ORDER BY Clause Usage</span></span>  

<span data-ttu-id="fbd6a-189">Transact-SQL では、`ORDER BY` 句は最上位の `SELECT .. FROM .. WHERE` ブロック内でのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-189">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="fbd6a-190">Entity SQL では、入れ子になった `ORDER BY` 式を使用でき、それをクエリ内の任意の場所に配置できますが、入れ子になったクエリ内の順序は保持されません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-190">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="fbd6a-191">識別子</span><span class="sxs-lookup"><span data-stu-id="fbd6a-191">Identifiers</span></span>  

 <span data-ttu-id="fbd6a-192">Transact-SQL では、識別子の比較は現在のデータベースの照合順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-192">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="fbd6a-193">Entity SQL の識別子では、常に大文字と小文字は区別されず、アクセントは区別されます (つまり、Entity SQL ではアクセントのある文字とアクセントのない文字が区別されます。たとえば、'a' と 'ấ' は等しくありません)。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-193">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="fbd6a-194">Entity SQL では、外観が同じでも別のコード ページに由来している複数の文字のバージョンが別々の文字として扱われます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-194">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="fbd6a-195">詳しくは、「[入力文字セット](input-character-set-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-195">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="fbd6a-196">Entity SQL では使用できない Transact-SQL 機能</span><span class="sxs-lookup"><span data-stu-id="fbd6a-196">Transact-SQL Functionality Not Available in Entity SQL</span></span>  

 <span data-ttu-id="fbd6a-197">Transact-SQL の次の機能は、Entity SQL では使用できません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-197">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="fbd6a-198">DML</span><span class="sxs-lookup"><span data-stu-id="fbd6a-198">DML</span></span>  
 <span data-ttu-id="fbd6a-199">Entity SQL では現在、DML ステートメント (insert、update、delete) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-199">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="fbd6a-200">DDL</span><span class="sxs-lookup"><span data-stu-id="fbd6a-200">DDL</span></span>  
 <span data-ttu-id="fbd6a-201">Entity SQL の現在のバージョンでは DDL はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-201">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="fbd6a-202">命令型プログラミング</span><span class="sxs-lookup"><span data-stu-id="fbd6a-202">Imperative Programming</span></span>  
 <span data-ttu-id="fbd6a-203">Transact-SQL とは異なり、Entity SQL では、命令型プログラミングはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-203">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="fbd6a-204">代わりにプログラミング言語を使用します。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-204">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="fbd6a-205">グループ化関数</span><span class="sxs-lookup"><span data-stu-id="fbd6a-205">Grouping Functions</span></span>  
 <span data-ttu-id="fbd6a-206">Entity SQL では、グループ化関数 (CUBE、ROLLUP、GROUPING_SET など) はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-206">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="fbd6a-207">分析関数</span><span class="sxs-lookup"><span data-stu-id="fbd6a-207">Analytic Functions</span></span>  
 <span data-ttu-id="fbd6a-208">Entity SQL では、分析関数は (まだ) サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-208">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="fbd6a-209">組み込み関数、演算子</span><span class="sxs-lookup"><span data-stu-id="fbd6a-209">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="fbd6a-210">Entity SQL では、Transact-SQL の組み込み関数と演算子のサブセットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-210">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="fbd6a-211">これらの演算子と関数の多くは、主要なストア プロバイダーによりサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-211">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="fbd6a-212">Entity SQL では、プロバイダー マニフェストで宣言されたストア固有の関数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-212">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="fbd6a-213">また、Entity Framework では、Entity SQL で使用される既存の組み込みストア関数とユーザー定義ストア関数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-213">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="fbd6a-214">ヒント</span><span class="sxs-lookup"><span data-stu-id="fbd6a-214">Hints</span></span>  
 <span data-ttu-id="fbd6a-215">Entity SQL には、クエリ ヒントのメカニズムが用意されていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-215">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="fbd6a-216">クエリ結果のバッチ処理</span><span class="sxs-lookup"><span data-stu-id="fbd6a-216">Batching Query Results</span></span>  
 <span data-ttu-id="fbd6a-217">Entity SQL では、クエリ結果のバッチ処理がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-217">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="fbd6a-218">たとえば、次の Transact-SQL は有効です (バッチとして送信)。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-218">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="fbd6a-219">ただし、同等の Entity SQL はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-219">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="fbd6a-220">Entity SQL では、コマンドごとに 1 つの結果生成クエリ ステートメントのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="fbd6a-220">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd6a-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbd6a-221">See also</span></span>

- [<span data-ttu-id="fbd6a-222">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="fbd6a-222">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="fbd6a-223">サポートされていない式</span><span class="sxs-lookup"><span data-stu-id="fbd6a-223">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
