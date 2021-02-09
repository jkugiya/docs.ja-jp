---
description: '詳細情報: FROM (Entity SQL)'
title: FROM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: e8f7906669b3ea9ee5c3be307bd31a2043b2650e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786343"
---
# <a name="from-entity-sql"></a><span data-ttu-id="19134-103">FROM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="19134-103">FROM (Entity SQL)</span></span>

<span data-ttu-id="19134-104">[SELECT](select-entity-sql.md) ステートメントで使用するコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="19134-104">Specifies the collection used in [SELECT](select-entity-sql.md) statements.</span></span>

## <a name="syntax"></a><span data-ttu-id="19134-105">構文</span><span class="sxs-lookup"><span data-stu-id="19134-105">Syntax</span></span>

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a><span data-ttu-id="19134-106">引数</span><span class="sxs-lookup"><span data-stu-id="19134-106">Arguments</span></span>

`expression` \
<span data-ttu-id="19134-107">`SELECT` ステートメントのソースとして使用するコレクションを生成する任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="19134-107">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="19134-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="19134-108">Remarks</span></span>

<span data-ttu-id="19134-109">`FROM` 句は、1 つ以上の `FROM` 句の項目をコンマで区切ったリストです。</span><span class="sxs-lookup"><span data-stu-id="19134-109">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="19134-110">`FROM` 句を使用して、`SELECT` ステートメントのソースを 1 つ以上指定できます。</span><span class="sxs-lookup"><span data-stu-id="19134-110">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="19134-111">`FROM` 句の最も単純な形式は、次の例に示すように、`SELECT` ステートメントのソースとして使用する 1 つのコレクションと 1 つの別名を識別する単一のクエリ式です。</span><span class="sxs-lookup"><span data-stu-id="19134-111">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>

`FROM C as c`

## <a name="from-clause-items"></a><span data-ttu-id="19134-112">FROM 句の項目</span><span class="sxs-lookup"><span data-stu-id="19134-112">FROM Clause Items</span></span>

<span data-ttu-id="19134-113">各 `FROM` 句項目は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリ内のソース コレクションを参照します。</span><span class="sxs-lookup"><span data-stu-id="19134-113">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="19134-114">は、`FROM` 句項目のクラスとして、単純 `FROM` 句項目、`JOIN FROM` 句項目、および `APPLY FROM` 句項目をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="19134-114">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="19134-115">これらの `FROM` 句の各項目については、以下のセクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="19134-115">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>

### <a name="simple-from-clause-item"></a><span data-ttu-id="19134-116">単純な FROM 句の項目</span><span class="sxs-lookup"><span data-stu-id="19134-116">Simple FROM Clause Item</span></span>

<span data-ttu-id="19134-117">最も単純な `FROM` 句の項目は、1 つのコレクションと 1 つの別名を識別する単一の式です。</span><span class="sxs-lookup"><span data-stu-id="19134-117">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="19134-118">式には、エンティティ セット、サブクエリ、またはコレクション型のその他の任意の式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="19134-118">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="19134-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="19134-119">The following is an example:</span></span>

```sql
LOB.Customers as c
```

<span data-ttu-id="19134-120">別名の指定は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19134-120">The alias specification is optional.</span></span> <span data-ttu-id="19134-121">上記のように FROM 句の項目を指定する代わりに、次のように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="19134-121">An alternate specification of the above from clause item could be the following:</span></span>

```sql
LOB.Customers
```

<span data-ttu-id="19134-122">別名を指定しない場合、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] はコレクション式に基づいて別名の生成を試みます。</span><span class="sxs-lookup"><span data-stu-id="19134-122">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>

### <a name="join-from-clause-item"></a><span data-ttu-id="19134-123">JOIN FROM 句の項目</span><span class="sxs-lookup"><span data-stu-id="19134-123">JOIN FROM Clause Item</span></span>

<span data-ttu-id="19134-124">`JOIN FROM` 句項目は、2 つの `FROM` 句項目の間の結合を表します。</span><span class="sxs-lookup"><span data-stu-id="19134-124">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="19134-125">では、クロス結合、内部結合、左外部結合、右外部結合、および完全外部結合をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="19134-125">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="19134-126">これらの結合はすべて、Transact-SQL でのサポートと同様にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="19134-126">All these joins are supported similar to the way that they are supported in Transact-SQL.</span></span> <span data-ttu-id="19134-127">Transact-SQL の場合と同様に、`JOIN` に含まれる 2 つの `FROM` 句の項目は独立している必要があります。</span><span class="sxs-lookup"><span data-stu-id="19134-127">As in Transact-SQL, the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="19134-128">つまり、相互に関連付けられた項目は使用できません。</span><span class="sxs-lookup"><span data-stu-id="19134-128">That is, they cannot be correlated.</span></span> <span data-ttu-id="19134-129">このような場合には、`CROSS APPLY` または `OUTER APPLY` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="19134-129">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>

#### <a name="cross-joins"></a><span data-ttu-id="19134-130">クロス結合</span><span class="sxs-lookup"><span data-stu-id="19134-130">Cross Joins</span></span>

<span data-ttu-id="19134-131">次の例に示すように、`CROSS JOIN` クエリ式は 2 つのコレクションのデカルト積を生成します。</span><span class="sxs-lookup"><span data-stu-id="19134-131">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a><span data-ttu-id="19134-132">内部結合</span><span class="sxs-lookup"><span data-stu-id="19134-132">Inner Joins</span></span>

<span data-ttu-id="19134-133">次の例に示すように、`INNER JOIN` は 2 つのコレクションの制約付きデカルト積を生成します。</span><span class="sxs-lookup"><span data-stu-id="19134-133">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c [INNER] JOIN D AS d ON e`

<span data-ttu-id="19134-134">上記のクエリ式では、`ON` 条件が指定されており、右のコレクションの各要素と対になっている左のコレクションの各要素を結合して処理します。</span><span class="sxs-lookup"><span data-stu-id="19134-134">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="19134-135">`ON` 条件を指定しない場合、`INNER JOIN` の動作は `CROSS JOIN` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="19134-135">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>

#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="19134-136">左外部結合と右外部結合</span><span class="sxs-lookup"><span data-stu-id="19134-136">Left Outer Joins and Right Outer Joins</span></span>

<span data-ttu-id="19134-137">次の例に示すように、`OUTER JOIN` クエリ式は 2 つのコレクションの制約付きデカルト積を生成します。</span><span class="sxs-lookup"><span data-stu-id="19134-137">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

<span data-ttu-id="19134-138">上記のクエリ式では、`ON` 条件が指定されており、右のコレクションの各要素と対になっている左のコレクションの各要素を結合して処理します。</span><span class="sxs-lookup"><span data-stu-id="19134-138">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="19134-139">`ON` 条件が指定されていない場合、式は、NULL 値を使用して、右の要素と対になっている左の要素の単一のインスタンスを処理します。</span><span class="sxs-lookup"><span data-stu-id="19134-139">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>

<span data-ttu-id="19134-140">`RIGHT OUTER JOIN` についても同様です。</span><span class="sxs-lookup"><span data-stu-id="19134-140">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>

#### <a name="full-outer-joins"></a><span data-ttu-id="19134-141">完全外部結合</span><span class="sxs-lookup"><span data-stu-id="19134-141">Full Outer Joins</span></span>

<span data-ttu-id="19134-142">次の例に示すように、明示的な `FULL OUTER JOIN` は 2 つのコレクションの制約付きデカルト積を生成します。</span><span class="sxs-lookup"><span data-stu-id="19134-142">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>

`FROM C AS c FULL OUTER JOIN D AS d ON e`

<span data-ttu-id="19134-143">上記のクエリ式では、`ON` 条件が指定されており、右のコレクションの各要素と対になっている左のコレクションの各要素を結合して処理します。</span><span class="sxs-lookup"><span data-stu-id="19134-143">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="19134-144">`ON` 条件が指定されていない場合、式は、NULL 値を使用して、右の要素と対になっている左の要素のインスタンスを 1 つ処理します。</span><span class="sxs-lookup"><span data-stu-id="19134-144">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="19134-145">また、NULL 値を使用して、左の要素と対になっている右の要素のインスタンスも 1 つ処理します。</span><span class="sxs-lookup"><span data-stu-id="19134-145">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>

> [!NOTE]
> <span data-ttu-id="19134-146">SQL-92 との互換性を保つため、Transact-SQL では、OUTER キーワードは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19134-146">To preserve compatibility with SQL-92, in Transact-SQL the OUTER keyword is optional.</span></span> <span data-ttu-id="19134-147">したがって、`LEFT JOIN`、`RIGHT JOIN`、および `FULL JOIN` は、`LEFT OUTER JOIN`、`RIGHT OUTER JOIN`、および `FULL OUTER JOIN` のシノニムです。</span><span class="sxs-lookup"><span data-stu-id="19134-147">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>

### <a name="apply-clause-item"></a><span data-ttu-id="19134-148">APPLY 句の項目</span><span class="sxs-lookup"><span data-stu-id="19134-148">APPLY Clause Item</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="19134-149">は、`APPLY` と `CROSS APPLY` という 2 種類の `OUTER APPLY` をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="19134-149">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>

<span data-ttu-id="19134-150">`CROSS APPLY` は、左のコレクションの各要素と右の式の評価によって生成されたコレクションの要素との一意の組み合わせを生成します。</span><span class="sxs-lookup"><span data-stu-id="19134-150">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="19134-151">`CROSS APPLY` では、右の式は左の要素に機能的に依存します。このような関連付けられたコレクションの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19134-151">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

<span data-ttu-id="19134-152">`CROSS APPLY` の動作は結合リストに似ています。</span><span class="sxs-lookup"><span data-stu-id="19134-152">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="19134-153">右の式が空のコレクションとして評価される場合、`CROSS APPLY` は、左の要素のそのインスタンスの組み合わせを生成しません。</span><span class="sxs-lookup"><span data-stu-id="19134-153">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>

<span data-ttu-id="19134-154">`OUTER APPLY` は、右の式が空のコレクションとして評価される場合でも組み合わせを生成する以外は、`CROSS APPLY` と同様です。</span><span class="sxs-lookup"><span data-stu-id="19134-154">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="19134-155">`OUTER APPLY` の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19134-155">The following is an example of an `OUTER APPLY`:</span></span>

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> <span data-ttu-id="19134-156">Transact-SQL とは異なり、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、明示的なネスト解除の手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="19134-156">Unlike in Transact-SQL, there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="19134-157">`CROSS` 演算子および `OUTER APPLY` 演算子は SQL Server 2005 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="19134-157">`CROSS` and `OUTER APPLY` operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="19134-158">場合によっては、クエリ パイプラインにより、`CROSS APPLY` 演算子または `OUTER APPLY` 演算子を含む Transact-SQL が生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="19134-158">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="19134-159">一部のバックエンド プロバイダー (SQL Server 2005 より古いバージョンの SQL Server など) では、これらの演算子がサポートされていません。したがって、このようなクエリをこれらのバックエンド プロバイダーで実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="19134-159">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>
>
> <span data-ttu-id="19134-160">`CROSS APPLY` 演算子または `OUTER APPLY` 演算子を含むクエリの生成につながる可能性がある一般的なシナリオとしては、ページングを使用した相関サブクエリ、相関サブクエリ全体またはナビゲーションによって生成されたコレクション全体を対象とした AnyElement、要素セレクターを受け取るグループ化メソッドを使用した LINQ クエリ、`CROSS APPLY` 演算子または `OUTER APPLY` 演算子が明示的に指定されたクエリ、`DEREF` コンストラクターを引数に取る `REF` コンストラクターを含むクエリなどがあります。</span><span class="sxs-lookup"><span data-stu-id="19134-160">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>

## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="19134-161">FROM 句での複数のコレクション</span><span class="sxs-lookup"><span data-stu-id="19134-161">Multiple Collections in the FROM Clause</span></span>

<span data-ttu-id="19134-162">`FROM` 句には、複数のコレクションをコンマで区切って含めることができます。</span><span class="sxs-lookup"><span data-stu-id="19134-162">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="19134-163">この場合、これらのコレクションは 1 つに結合されるものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="19134-163">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="19134-164">これは、n 方向の CROSS JOIN と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="19134-164">Think of these as an n-way CROSS JOIN.</span></span>

<span data-ttu-id="19134-165">次の例では、`C` と `D` は独立したコレクションですが、`c.Names` は `C` に依存しています。</span><span class="sxs-lookup"><span data-stu-id="19134-165">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>

```sql
FROM C AS c, D AS d, c.Names AS e
```

<span data-ttu-id="19134-166">上記の例は、次の例と論理的に等価です。</span><span class="sxs-lookup"><span data-stu-id="19134-166">The previous example is logically equivalent to the following example:</span></span>

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a><span data-ttu-id="19134-167">左の相関関係</span><span class="sxs-lookup"><span data-stu-id="19134-167">Left Correlation</span></span>

 <span data-ttu-id="19134-168">`FROM` 句の項目は、前の句で指定された項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="19134-168">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="19134-169">次の例で、`C` と `D` は独立したコレクションですが、`c.Names` は `C` に依存しています。</span><span class="sxs-lookup"><span data-stu-id="19134-169">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>

```sql
from C as c, D as d, c.Names as e
```

<span data-ttu-id="19134-170">上記の例は、次の例と論理的に等価です。</span><span class="sxs-lookup"><span data-stu-id="19134-170">This is logically equivalent to:</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a><span data-ttu-id="19134-171">Semantics</span><span class="sxs-lookup"><span data-stu-id="19134-171">Semantics</span></span>

<span data-ttu-id="19134-172">論理上、`FROM` 句のコレクションは `n` 方向のクロス結合の一部になると見なされます (1 方向のクロス結合の場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="19134-172">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="19134-173">`FROM` 句内の別名は、左から右へと処理され、後で参照できるように現在のスコープに追加されます。</span><span class="sxs-lookup"><span data-stu-id="19134-173">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="19134-174">`FROM` 句は、行のマルチセットを生成すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="19134-174">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="19134-175">`FROM` 句の項目ごとに 1 つのフィールドが生成され、そのコレクションの項目の 1 つの要素を表します。</span><span class="sxs-lookup"><span data-stu-id="19134-175">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>

<span data-ttu-id="19134-176">`FROM` 句は、c、d、e の各フィールドが `C`、`D`、`c.Names` の要素型になると見なされる Row(c, d, e) 型の行のマルチセットを論理的に生成します。</span><span class="sxs-lookup"><span data-stu-id="19134-176">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="19134-177">では、単純な `FROM` 句の項目ごとの別名がスコープに導入されます。</span><span class="sxs-lookup"><span data-stu-id="19134-177">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="19134-178">たとえば、次の FROM 句の例では、スコープに導入される名前は c、d、e です。</span><span class="sxs-lookup"><span data-stu-id="19134-178">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

<span data-ttu-id="19134-179">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では Transact-SQL と異なり、`FROM` 句では別名のみがスコープに導入されます。</span><span class="sxs-lookup"><span data-stu-id="19134-179">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike Transact-SQL), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="19134-180">これらのコレクションの列 (プロパティ) への参照は、別名を使用して修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19134-180">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>

## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="19134-181">入れ子になったクエリからのキーの抽出</span><span class="sxs-lookup"><span data-stu-id="19134-181">Pulling Up Keys from Nested Queries</span></span>

<span data-ttu-id="19134-182">入れ子になったクエリからのキーの抽出を必要とする特定の種類のクエリはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="19134-182">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="19134-183">たとえば、次のクエリは有効です。</span><span class="sxs-lookup"><span data-stu-id="19134-183">For example, the following query is valid:</span></span>

```sql
select c.Orders from Customers as c
```

<span data-ttu-id="19134-184">しかし、次のクエリは、入れ子になったクエリにキーがないため無効です。</span><span class="sxs-lookup"><span data-stu-id="19134-184">However, the following query is not valid, because the nested query does not have any keys:</span></span>

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a><span data-ttu-id="19134-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="19134-185">See also</span></span>

- [<span data-ttu-id="19134-186">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="19134-186">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="19134-187">クエリ式</span><span class="sxs-lookup"><span data-stu-id="19134-187">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="19134-188">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="19134-188">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
