---
description: '詳細情報: 集計関数 (Entity Framework 用 SqlClient)'
title: 集計関数 (Entity Framework 用 SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: b9f1ff8c75fc09de7532b459090b0b5cd1d47262
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651081"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="2a861-103">集計関数 (Entity Framework 用 SqlClient)</span><span class="sxs-lookup"><span data-stu-id="2a861-103">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="2a861-104">.NET Framework Data Provider for SQL Server (SqlClient) には、集計関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2a861-104">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="2a861-105">集計関数は、一連の入力値に対して計算を実行し、値を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-105">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="2a861-106">これらの関数は、SqlClient の SqlServer 名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="2a861-106">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="2a861-107">Entity Framework は、プロバイダーの名前空間プロパティを使用することにより、型や関数など、特定のコンストラクターに対してこのプロバイダーによってどのプレフィックスが使用されているかを特定できます。</span><span class="sxs-lookup"><span data-stu-id="2a861-107">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="2a861-108">以下は、SqlClient の集計関数です。</span><span class="sxs-lookup"><span data-stu-id="2a861-108">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="2a861-109">AVG(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-109">AVG(expression)</span></span>

<span data-ttu-id="2a861-110">コレクション内の値の平均値を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-110">Returns the average of the values in a collection.</span></span> <span data-ttu-id="2a861-111">NULL 値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="2a861-111">Null values are ignored.</span></span>

<span data-ttu-id="2a861-112">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-112">**Arguments**</span></span>

<span data-ttu-id="2a861-113">`Int32`、`Int64`、`Double`、および `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="2a861-113">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="2a861-114">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-114">**Return Value**</span></span>

<span data-ttu-id="2a861-115">`expression` の型。</span><span class="sxs-lookup"><span data-stu-id="2a861-115">The type of `expression`.</span></span>

<span data-ttu-id="2a861-116">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-116">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="2a861-117">CHECKSUM_AGG(collection)</span><span class="sxs-lookup"><span data-stu-id="2a861-117">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="2a861-118">コレクション内にある値のチェックサムを返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-118">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="2a861-119">NULL 値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="2a861-119">Null values are ignored.</span></span>

 <span data-ttu-id="2a861-120">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-120">**Arguments**</span></span>

 <span data-ttu-id="2a861-121">Collection(`Int32`)。</span><span class="sxs-lookup"><span data-stu-id="2a861-121">A Collection(`Int32`).</span></span>

 <span data-ttu-id="2a861-122">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-122">**Return Value**</span></span>

 <span data-ttu-id="2a861-123">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="2a861-123">An `Int32`.</span></span>

 <span data-ttu-id="2a861-124">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-124">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="2a861-125">COUNT(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-125">COUNT(expression)</span></span>

<span data-ttu-id="2a861-126">コレクション内のアイテムの数を `Int32` 型の値として返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-126">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="2a861-127">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-127">**Arguments**</span></span>

<span data-ttu-id="2a861-128">Collection\<T>。T は次のいずれかの型です:</span><span class="sxs-lookup"><span data-stu-id="2a861-128">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="2a861-129">`Guid` (SQL Server 2000 では返されません)</span><span class="sxs-lookup"><span data-stu-id="2a861-129">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="2a861-130">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-130">**Return Value**</span></span>

<span data-ttu-id="2a861-131">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="2a861-131">An `Int32`.</span></span>

<span data-ttu-id="2a861-132">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-132">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="2a861-133">COUNT_BIG(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-133">COUNT_BIG(expression)</span></span>

<span data-ttu-id="2a861-134">コレクション内のアイテムの数を `bigint` 型の値として返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-134">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="2a861-135">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-135">**Arguments**</span></span>

 <span data-ttu-id="2a861-136">Collection(T)。T は次のいずれかの型です。</span><span class="sxs-lookup"><span data-stu-id="2a861-136">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="2a861-137">`Guid` (SQL Server 2000 では返されません)</span><span class="sxs-lookup"><span data-stu-id="2a861-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="2a861-138">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-138">**Return Value**</span></span>

<span data-ttu-id="2a861-139">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="2a861-139">An `Int64`.</span></span>

<span data-ttu-id="2a861-140">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-140">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="2a861-141">MAX(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-141">MAX(expression)</span></span>

<span data-ttu-id="2a861-142">コレクション内の最大値を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="2a861-143">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-143">**Arguments**</span></span>

<span data-ttu-id="2a861-144">Collection(T)。T は次のいずれかの型です。</span><span class="sxs-lookup"><span data-stu-id="2a861-144">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="2a861-145">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-145">**Return Value**</span></span>

<span data-ttu-id="2a861-146">`expression` の型。</span><span class="sxs-lookup"><span data-stu-id="2a861-146">The type of `expression`.</span></span>

<span data-ttu-id="2a861-147">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-147">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="2a861-148">MIN(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-148">MIN(expression)</span></span>

<span data-ttu-id="2a861-149">コレクション内の最小値を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="2a861-150">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-150">**Arguments**</span></span>

<span data-ttu-id="2a861-151">Collection(T)。T は次のいずれかの型です。</span><span class="sxs-lookup"><span data-stu-id="2a861-151">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="2a861-152">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-152">**Return Value**</span></span>

<span data-ttu-id="2a861-153">`expression` の型。</span><span class="sxs-lookup"><span data-stu-id="2a861-153">The type of `expression`.</span></span>

<span data-ttu-id="2a861-154">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-154">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="2a861-155">STDEV(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-155">STDEV(expression)</span></span>

<span data-ttu-id="2a861-156">指定された式のすべての値の統計的標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="2a861-157">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-157">**Arguments**</span></span>

<span data-ttu-id="2a861-158">Collection(`Double`)。</span><span class="sxs-lookup"><span data-stu-id="2a861-158">A Collection(`Double`).</span></span>

<span data-ttu-id="2a861-159">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-159">**Return Value**</span></span>

<span data-ttu-id="2a861-160">`Double`。</span><span class="sxs-lookup"><span data-stu-id="2a861-160">A `Double`.</span></span>

<span data-ttu-id="2a861-161">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-161">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="2a861-162">STDEVP(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-162">STDEVP(expression)</span></span>

<span data-ttu-id="2a861-163">指定された式のすべての値を母集団として統計的標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="2a861-164">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-164">**Arguments**</span></span>

<span data-ttu-id="2a861-165">Collection(`Double`)。</span><span class="sxs-lookup"><span data-stu-id="2a861-165">A Collection(`Double`).</span></span>

<span data-ttu-id="2a861-166">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-166">**Return Value**</span></span>

<span data-ttu-id="2a861-167">`Double`。</span><span class="sxs-lookup"><span data-stu-id="2a861-167">A `Double`.</span></span>

<span data-ttu-id="2a861-168">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-168">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="2a861-169">SUM(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-169">SUM(expression)</span></span>

<span data-ttu-id="2a861-170">コレクション内のすべての値の合計を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="2a861-171">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-171">**Arguments**</span></span>

<span data-ttu-id="2a861-172">Collection(T)。T は次のいずれかの型です: `Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="2a861-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="2a861-173">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-173">**Return Value**</span></span>

<span data-ttu-id="2a861-174">`expression` の型。</span><span class="sxs-lookup"><span data-stu-id="2a861-174">The type of `expression`.</span></span>

<span data-ttu-id="2a861-175">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-175">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="2a861-176">VAR(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-176">VAR(expression)</span></span>

<span data-ttu-id="2a861-177">指定された式のすべての値の統計的分散を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="2a861-178">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-178">**Arguments**</span></span>

<span data-ttu-id="2a861-179">Collection(`Double`)。</span><span class="sxs-lookup"><span data-stu-id="2a861-179">A Collection(`Double`).</span></span>

<span data-ttu-id="2a861-180">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-180">**Return Value**</span></span>

<span data-ttu-id="2a861-181">`Double`。</span><span class="sxs-lookup"><span data-stu-id="2a861-181">A `Double`.</span></span>

<span data-ttu-id="2a861-182">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-182">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="2a861-183">VARP(expression)</span><span class="sxs-lookup"><span data-stu-id="2a861-183">VARP(expression)</span></span>

<span data-ttu-id="2a861-184">指定した式のすべての値について、母集団に対する統計的変位を返します。</span><span class="sxs-lookup"><span data-stu-id="2a861-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="2a861-185">**引数**</span><span class="sxs-lookup"><span data-stu-id="2a861-185">**Arguments**</span></span>

<span data-ttu-id="2a861-186">Collection(`Double`)。</span><span class="sxs-lookup"><span data-stu-id="2a861-186">A Collection(`Double`).</span></span>

<span data-ttu-id="2a861-187">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="2a861-187">**Return Value**</span></span>

<span data-ttu-id="2a861-188">`Double`。</span><span class="sxs-lookup"><span data-stu-id="2a861-188">A `Double`.</span></span>

<span data-ttu-id="2a861-189">**例**</span><span class="sxs-lookup"><span data-stu-id="2a861-189">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="2a861-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a861-190">See also</span></span>

- [<span data-ttu-id="2a861-191">集計関数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a861-191">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="2a861-192">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="2a861-192">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="2a861-193">集計正規関数</span><span class="sxs-lookup"><span data-stu-id="2a861-193">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
