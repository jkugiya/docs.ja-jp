---
description: '詳細情報: 集計正規関数'
title: 集計正規関数
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: e26888ac15553a592f7d2cb9b1a0941161115615
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697297"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="4fe0a-103">集計正規関数</span><span class="sxs-lookup"><span data-stu-id="4fe0a-103">Aggregate Canonical Functions</span></span>

<span data-ttu-id="4fe0a-104">集計とは、一連の入力値をまとまった値 (単一の値など) に変換する式を指します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-104">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="4fe0a-105">集計は SELECT 式の GROUP BY 句と組み合わせて使用されるのが一般的であり、どこで使用できるかについては制約があります。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-105">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="4fe0a-106">集計 Entity SQL 正規関数</span><span class="sxs-lookup"><span data-stu-id="4fe0a-106">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="4fe0a-107">集計 Entity SQL 正規関数を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-107">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="4fe0a-108">Avg(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-108">Avg(expression)</span></span>

<span data-ttu-id="4fe0a-109">NULL 以外の値の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-109">Returns the average of the non-null values.</span></span>

<span data-ttu-id="4fe0a-110">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-110">**Arguments**</span></span>

<span data-ttu-id="4fe0a-111">`Int32`、`Int64`、`Double`、および `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-111">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4fe0a-112">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-112">**Return Value**</span></span>

<span data-ttu-id="4fe0a-113">`expression` の型、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-113">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-114">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-114">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="4fe0a-115">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-115">BigCount(expression)</span></span>

<span data-ttu-id="4fe0a-116">NULL 値および重複値を含む集計のサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-116">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="4fe0a-117">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-117">**Arguments**</span></span>

<span data-ttu-id="4fe0a-118">任意の型。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-118">Any type.</span></span>

<span data-ttu-id="4fe0a-119">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-119">**Return Value**</span></span>

<span data-ttu-id="4fe0a-120">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-120">An `Int64`.</span></span>

<span data-ttu-id="4fe0a-121">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-121">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="4fe0a-122">Count(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-122">Count(expression)</span></span>

<span data-ttu-id="4fe0a-123">NULL 値および重複値を含む集計のサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-123">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="4fe0a-124">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-124">**Arguments**</span></span>

<span data-ttu-id="4fe0a-125">任意の型。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-125">Any type.</span></span>

<span data-ttu-id="4fe0a-126">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-126">**Return Value**</span></span>

<span data-ttu-id="4fe0a-127">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-127">An `Int32`.</span></span>

<span data-ttu-id="4fe0a-128">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-128">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="4fe0a-129">Max(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-129">Max(expression)</span></span>

<span data-ttu-id="4fe0a-130">NULL 以外の値の最大値を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-130">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="4fe0a-131">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-131">**Arguments**</span></span>

<span data-ttu-id="4fe0a-132">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-132">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="4fe0a-133">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-133">**Return Value**</span></span>

<span data-ttu-id="4fe0a-134">`expression` の型、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-134">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-135">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-135">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="4fe0a-136">Min(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-136">Min(expression)</span></span>

<span data-ttu-id="4fe0a-137">NULL 以外の値の最小値を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-137">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="4fe0a-138">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-138">**Arguments**</span></span>

<span data-ttu-id="4fe0a-139">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-139">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="4fe0a-140">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-140">**Return Value**</span></span>

<span data-ttu-id="4fe0a-141">`expression` の型、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-141">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-142">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-142">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="4fe0a-143">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-143">StDev(expression)</span></span>

<span data-ttu-id="4fe0a-144">NULL 以外の値の標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-144">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="4fe0a-145">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-145">**Arguments**</span></span>

<span data-ttu-id="4fe0a-146">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-146">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4fe0a-147">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-147">**Return Value**</span></span>

<span data-ttu-id="4fe0a-148">`Double`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-148">A `Double`.</span></span> <span data-ttu-id="4fe0a-149">すべての入力値が `Null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-149">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-150">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-150">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="4fe0a-151">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-151">StDevP(expression)</span></span>

<span data-ttu-id="4fe0a-152">すべての値の母集団の標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-152">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="4fe0a-153">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-153">**Arguments**</span></span>

<span data-ttu-id="4fe0a-154">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-154">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4fe0a-155">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-155">**Return Value**</span></span>

<span data-ttu-id="4fe0a-156">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-156">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-157">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-157">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="4fe0a-158">Sum(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-158">Sum(expression)</span></span>

<span data-ttu-id="4fe0a-159">NULL 以外の値の合計を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-159">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="4fe0a-160">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-160">**Arguments**</span></span>

<span data-ttu-id="4fe0a-161">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-161">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4fe0a-162">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-162">**Return Value**</span></span>

<span data-ttu-id="4fe0a-163">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-163">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-164">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-164">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="4fe0a-165">Var(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-165">Var(expression)</span></span>

<span data-ttu-id="4fe0a-166">すべての null 以外の値の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-166">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="4fe0a-167">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-167">**Arguments**</span></span>

<span data-ttu-id="4fe0a-168">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-168">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4fe0a-169">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-169">**Return Value**</span></span>

<span data-ttu-id="4fe0a-170">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-170">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-171">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-171">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="4fe0a-172">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="4fe0a-172">VarP(expression)</span></span>

<span data-ttu-id="4fe0a-173">すべての null 以外の値の母集団の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-173">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="4fe0a-174">**引数**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-174">**Arguments**</span></span>

<span data-ttu-id="4fe0a-175">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-175">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4fe0a-176">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-176">**Return Value**</span></span>

<span data-ttu-id="4fe0a-177">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-177">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4fe0a-178">**例**</span><span class="sxs-lookup"><span data-stu-id="4fe0a-178">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="4fe0a-179">同等の機能は、Microsoft SQL クライアント マネージド プロバイダーでも利用できます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-179">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="4fe0a-180">詳細については、「[Entity Framework 用 SqlClient 関数](../sqlclient-for-ef-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-180">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="4fe0a-181">コレクションベースの集計</span><span class="sxs-lookup"><span data-stu-id="4fe0a-181">Collection-based aggregates</span></span>

<span data-ttu-id="4fe0a-182">コレクションベースの集計 (コレクション関数) は、コレクションに対して演算を実行して、値を返します。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-182">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="4fe0a-183">たとえば、ORDERS がすべての注文のコレクションである場合、次の式を使って、最も早い出荷日を計算できます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-183">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="4fe0a-184">コレクションベースの集計では、現在の周囲の名前解決スコープ内で式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-184">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="4fe0a-185">グループベースの集計</span><span class="sxs-lookup"><span data-stu-id="4fe0a-185">Group-based aggregates</span></span>

<span data-ttu-id="4fe0a-186">グループベースの集計では、GROUP BY 句によって定義されたグループごとに計算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-186">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="4fe0a-187">その結果の各グループについて、それぞれのグループ内の要素を、集計計算の入力として使って別個の集計が計算されます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-187">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="4fe0a-188">select 式で group by 句を使用した場合、投影または order by 句で使用できるのは、グループ化式の名前、集計式、または定数式だけです。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-188">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="4fe0a-189">次の例では、製品ごとの平均発注数量を計算しています。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-189">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="4fe0a-190">SELECT 式に明示的な group by 句を指定せずに、グループベースの集計を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-190">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="4fe0a-191">この場合、すべての要素が単一のグループとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-191">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="4fe0a-192">これは、定数に基づくグループ化の指定と同等です。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-192">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="4fe0a-193">たとえば、次のような式があったとします。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-193">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="4fe0a-194">これは、次の指定と同じです。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-194">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="4fe0a-195">グループベースの集計内の式は、WHERE 句式から可視である名前解決スコープ内で評価されます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-195">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="4fe0a-196">Transact-SQL の場合と同様、グループベースの集計には、ALL または DISTINCT の修飾子を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-196">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="4fe0a-197">DISTINCT 修飾子が指定された場合、集計を計算する前に、集計の入力コレクションから重複が除外されます。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-197">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="4fe0a-198">ALL 修飾子が指定された場合 (または修飾子が指定されなかった場合)、重複は除外されません。</span><span class="sxs-lookup"><span data-stu-id="4fe0a-198">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fe0a-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fe0a-199">See also</span></span>

- [<span data-ttu-id="4fe0a-200">正規関数</span><span class="sxs-lookup"><span data-stu-id="4fe0a-200">Canonical Functions</span></span>](canonical-functions.md)
