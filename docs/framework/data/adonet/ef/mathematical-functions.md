---
description: '詳細情報: 数学関数'
title: 数学関数
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 6bf1f116d6d88a8a188dc31cab91fbf26bdaea36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795028"
---
# <a name="mathematical-functions"></a><span data-ttu-id="9962f-103">数学関数</span><span class="sxs-lookup"><span data-stu-id="9962f-103">Mathematical Functions</span></span>

<span data-ttu-id="9962f-104">.NET Framework Data Provider for SQL Server (SqlClient) には、引数として指定された入力値に対して計算を実行し、数値結果を返す数学関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9962f-104">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="9962f-105">これらの関数は、SqlClient の SqlServer 名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="9962f-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="9962f-106">Entity Framework は、プロバイダーの名前空間プロパティを使用することにより、型や関数など、特定のコンストラクターに対してこのプロバイダーによってどのプレフィックスが使用されているかを特定できます。</span><span class="sxs-lookup"><span data-stu-id="9962f-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="9962f-107">SqlClient の数学関数を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9962f-107">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="9962f-108">ABS(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-108">ABS(expression)</span></span>

<span data-ttu-id="9962f-109">絶対値を求める関数です。</span><span class="sxs-lookup"><span data-stu-id="9962f-109">Performs the absolute value function.</span></span>

<span data-ttu-id="9962f-110">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-110">**Arguments**</span></span>

<span data-ttu-id="9962f-111">`expression`:`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-111">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-112">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-112">**Return Value**</span></span>

<span data-ttu-id="9962f-113">指定された式の絶対値。</span><span class="sxs-lookup"><span data-stu-id="9962f-113">The absolute value of the specified expression.</span></span>

<span data-ttu-id="9962f-114">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-114">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="9962f-115">ACOS(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-115">ACOS(expression)</span></span>

<span data-ttu-id="9962f-116">指定された式のアークコサイン (逆余弦) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-116">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="9962f-117">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-117">**Arguments**</span></span>

<span data-ttu-id="9962f-118">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-118">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-119">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-119">**Return Value**</span></span>

<span data-ttu-id="9962f-120">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-120">A `Double`.</span></span>

<span data-ttu-id="9962f-121">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-121">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="9962f-122">ASIN(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-122">ASIN(expression)</span></span>

<span data-ttu-id="9962f-123">指定された式のアークサイン (逆正弦) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-123">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="9962f-124">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-124">**Arguments**</span></span>

<span data-ttu-id="9962f-125">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-125">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-126">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-126">**Return Value**</span></span>

<span data-ttu-id="9962f-127">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-127">A `Double`.</span></span>

<span data-ttu-id="9962f-128">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-128">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="9962f-129">ATAN(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-129">ATAN(expression)</span></span>

<span data-ttu-id="9962f-130">指定された数値式のアークタンジェント (逆正接) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-130">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="9962f-131">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-131">**Arguments**</span></span>

<span data-ttu-id="9962f-132">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-132">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-133">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-133">**Return Value**</span></span>

<span data-ttu-id="9962f-134">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-134">A `Double`.</span></span>

<span data-ttu-id="9962f-135">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-135">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="9962f-136">ATN2(expression, expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-136">ATN2(expression, expression)</span></span>

<span data-ttu-id="9962f-137">指定された 2 つの数値式の商がタンジェント (正接) となる角度をラジアンで返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-137">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="9962f-138">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-138">**Arguments**</span></span>

<span data-ttu-id="9962f-139">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-139">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-140">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-140">**Return Value**</span></span>

<span data-ttu-id="9962f-141">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-141">A `Double`.</span></span>

<span data-ttu-id="9962f-142">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-142">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="9962f-143">CEILING(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-143">CEILING(expression)</span></span>

<span data-ttu-id="9962f-144">指定された式をその式以上の最小整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="9962f-144">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="9962f-145">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-145">**Arguments**</span></span>

<span data-ttu-id="9962f-146">`expression`:`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-146">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-147">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-147">**Return Value**</span></span>

<span data-ttu-id="9962f-148">`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-148">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-149">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-149">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="9962f-150">COS(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-150">COS(expression)</span></span>

<span data-ttu-id="9962f-151">ラジアンで指定された角度のコサイン (余弦) を計算します。</span><span class="sxs-lookup"><span data-stu-id="9962f-151">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="9962f-152">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-152">**Arguments**</span></span>

<span data-ttu-id="9962f-153">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-153">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-154">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-154">**Return Value**</span></span>

<span data-ttu-id="9962f-155">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-155">A `Double`.</span></span>

<span data-ttu-id="9962f-156">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-156">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="9962f-157">COT(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-157">COT(expression)</span></span>

<span data-ttu-id="9962f-158">ラジアンで指定された角度のコタンジェント (余接) を計算します。</span><span class="sxs-lookup"><span data-stu-id="9962f-158">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="9962f-159">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-159">**Arguments**</span></span>

<span data-ttu-id="9962f-160">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-160">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-161">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-161">**Return Value**</span></span>

<span data-ttu-id="9962f-162">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-162">A `Double`.</span></span>

<span data-ttu-id="9962f-163">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-163">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="9962f-164">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="9962f-164">DEGREES(radians)</span></span>

<span data-ttu-id="9962f-165">対応する角度を度数で返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-165">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="9962f-166">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-166">**Arguments**</span></span>

<span data-ttu-id="9962f-167">`expression`:`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-167">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-168">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-168">**Return Value**</span></span>

<span data-ttu-id="9962f-169">`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-169">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-170">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-170">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="9962f-171">EXP(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-171">EXP(expression)</span></span>

<span data-ttu-id="9962f-172">指定された数値式の指数値を計算します。</span><span class="sxs-lookup"><span data-stu-id="9962f-172">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="9962f-173">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-173">**Arguments**</span></span>

<span data-ttu-id="9962f-174">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-174">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-175">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-175">**Return Value**</span></span>

<span data-ttu-id="9962f-176">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-176">A `Double`.</span></span>

<span data-ttu-id="9962f-177">**例** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="9962f-177">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="9962f-178">FLOOR(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-178">FLOOR(expression)</span></span>

<span data-ttu-id="9962f-179">指定された式をその式以下の最大整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="9962f-179">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="9962f-180">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-180">**Arguments**</span></span>

<span data-ttu-id="9962f-181">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-181">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-182">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-182">**Return Value**</span></span>

<span data-ttu-id="9962f-183">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-183">A `Double`.</span></span>

<span data-ttu-id="9962f-184">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-184">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="9962f-185">LOG(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-185">LOG(expression)</span></span>

<span data-ttu-id="9962f-186">指定された `float` 型の式の自然対数を計算します。</span><span class="sxs-lookup"><span data-stu-id="9962f-186">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="9962f-187">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-187">**Arguments**</span></span>

<span data-ttu-id="9962f-188">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-188">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-189">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-189">**Return Value**</span></span>

<span data-ttu-id="9962f-190">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-190">A `Double`.</span></span>

<span data-ttu-id="9962f-191">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-191">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="9962f-192">LOG10(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-192">LOG10(expression)</span></span>

<span data-ttu-id="9962f-193">指定された `Double` 型の式の 10 を底とした対数を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-193">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="9962f-194">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-194">**Arguments**</span></span>

<span data-ttu-id="9962f-195">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-195">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-196">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-196">**Return Value**</span></span>

<span data-ttu-id="9962f-197">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-197">A `Double`.</span></span>

<span data-ttu-id="9962f-198">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-198">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="9962f-199">PI()</span><span class="sxs-lookup"><span data-stu-id="9962f-199">PI()</span></span>

<span data-ttu-id="9962f-200">π の定数値を `Double` として返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-200">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="9962f-201">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-201">**Return Value**</span></span>

<span data-ttu-id="9962f-202">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-202">A `Double`.</span></span>

<span data-ttu-id="9962f-203">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-203">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="9962f-204">POWER(numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-204">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="9962f-205">指定された式の指定されたべき乗を計算します。</span><span class="sxs-lookup"><span data-stu-id="9962f-205">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="9962f-206">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-206">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="9962f-207">`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-207">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="9962f-208">`numeric_expression` のべき乗値を表す `Double` 型の値。</span><span class="sxs-lookup"><span data-stu-id="9962f-208">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="9962f-209">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-209">**Return Value**</span></span>

<span data-ttu-id="9962f-210">指定された `numeric_expression` を指定された `power_expression` でべき乗した値。</span><span class="sxs-lookup"><span data-stu-id="9962f-210">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="9962f-211">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-211">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="9962f-212">RADIANS(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-212">RADIANS(expression)</span></span>

<span data-ttu-id="9962f-213">角度をラジアンに変換します。</span><span class="sxs-lookup"><span data-stu-id="9962f-213">Converts degrees to radians.</span></span>

<span data-ttu-id="9962f-214">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-214">**Arguments**</span></span>

<span data-ttu-id="9962f-215">`expression`:`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-215">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-216">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-216">**Return Value**</span></span>

<span data-ttu-id="9962f-217">`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-217">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-218">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-218">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="9962f-219">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="9962f-219">RAND([seed])</span></span>

<span data-ttu-id="9962f-220">0 から 1 までの範囲の乱数を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-220">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="9962f-221">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-221">**Arguments**</span></span>

<span data-ttu-id="9962f-222">`Int32` としてのシード値。</span><span class="sxs-lookup"><span data-stu-id="9962f-222">The seed value as an `Int32`.</span></span> <span data-ttu-id="9962f-223">シードを指定しない場合は、SQL Server データベース エンジンによってシード値がランダムに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9962f-223">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="9962f-224">指定したシード値について、返される結果は常に同じです。</span><span class="sxs-lookup"><span data-stu-id="9962f-224">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="9962f-225">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-225">**Return Value**</span></span>

<span data-ttu-id="9962f-226">0 から 1 までの範囲の `Double` 型の乱数。</span><span class="sxs-lookup"><span data-stu-id="9962f-226">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="9962f-227">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-227">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="9962f-228">ROUND(numeric_expression, length[,function])</span><span class="sxs-lookup"><span data-stu-id="9962f-228">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="9962f-229">指定された長さまたは有効桁数に丸めた数値式を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-229">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="9962f-230">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-230">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="9962f-231">`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-231">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="9962f-232">`Int32` を丸めた後の有効桁数を表す `numeric_expression`。</span><span class="sxs-lookup"><span data-stu-id="9962f-232">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="9962f-233">`length` に正の値を指定した場合、`numeric_expression` は `length` で指定した小数点以下桁数に丸められます。</span><span class="sxs-lookup"><span data-stu-id="9962f-233">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="9962f-234">`length` に負の値を指定した場合、`numeric_expression` は `length` で指定した小数点の左側の位置で丸められます。</span><span class="sxs-lookup"><span data-stu-id="9962f-234">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="9962f-235">任意。</span><span class="sxs-lookup"><span data-stu-id="9962f-235">Optional.</span></span> <span data-ttu-id="9962f-236">実行する操作の種類を表す `Int32`。</span><span class="sxs-lookup"><span data-stu-id="9962f-236">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="9962f-237">function を省略した場合、または 0 (既定値) を指定した場合、`numeric_expression` は丸められます。</span><span class="sxs-lookup"><span data-stu-id="9962f-237">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="9962f-238">0 以外の値を指定した場合、`numeric_expression` は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="9962f-238">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="9962f-239">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-239">**Return Value**</span></span>

<span data-ttu-id="9962f-240">指定された `numeric_expression` を指定された `power_expression` でべき乗した値。</span><span class="sxs-lookup"><span data-stu-id="9962f-240">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="9962f-241">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-241">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="9962f-242">SIGN(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-242">SIGN(expression)</span></span>

<span data-ttu-id="9962f-243">指定した式の符号として、正 (+1)、負 (-1)、ゼロ (0) のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-243">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="9962f-244">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-244">**Arguments**</span></span>

<span data-ttu-id="9962f-245">`expression`: `Int32`、`Int64`、`Double`、または `Decimal`</span><span class="sxs-lookup"><span data-stu-id="9962f-245">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="9962f-246">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-246">**Return Value**</span></span>

<span data-ttu-id="9962f-247">`Int32`、`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9962f-247">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="9962f-248">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-248">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="9962f-249">SIN(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-249">SIN(expression)</span></span>

<span data-ttu-id="9962f-250">ラジアンで指定された角度のサイン (正弦) を計算し、`Double` 式を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-250">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="9962f-251">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-251">**Arguments**</span></span>

<span data-ttu-id="9962f-252">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-252">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-253">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-253">**Return Value**</span></span>

<span data-ttu-id="9962f-254">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-254">A `Double`.</span></span>

<span data-ttu-id="9962f-255">**例** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="9962f-255">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="9962f-256">SQRT(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-256">SQRT(expression)</span></span>

<span data-ttu-id="9962f-257">指定された式の平方根を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-257">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="9962f-258">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-258">**Arguments**</span></span>

<span data-ttu-id="9962f-259">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-259">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-260">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-260">**Return Value**</span></span>

<span data-ttu-id="9962f-261">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-261">A `Double`.</span></span>

<span data-ttu-id="9962f-262">**例** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="9962f-262">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="9962f-263">SQUARE(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-263">SQUARE(expression)</span></span>

<span data-ttu-id="9962f-264">指定された式の 2 乗値を返します。</span><span class="sxs-lookup"><span data-stu-id="9962f-264">Returns the square of the specified expression.</span></span>

<span data-ttu-id="9962f-265">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-265">**Arguments**</span></span>

<span data-ttu-id="9962f-266">`expression`:`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-266">`expression`: A `Double`.</span></span>

<span data-ttu-id="9962f-267">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-267">**Return Value**</span></span>

<span data-ttu-id="9962f-268">`Double`。</span><span class="sxs-lookup"><span data-stu-id="9962f-268">A `Double`.</span></span>

<span data-ttu-id="9962f-269">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-269">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="9962f-270">TAN(expression)</span><span class="sxs-lookup"><span data-stu-id="9962f-270">TAN(expression)</span></span>

<span data-ttu-id="9962f-271">指定された式のタンジェントを計算します。</span><span class="sxs-lookup"><span data-stu-id="9962f-271">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="9962f-272">**引数**</span><span class="sxs-lookup"><span data-stu-id="9962f-272">**Arguments**</span></span>

<span data-ttu-id="9962f-273">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="9962f-273">`expression`: `Double`</span></span>

<span data-ttu-id="9962f-274">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="9962f-274">**Return Value**</span></span>

`Double`

<span data-ttu-id="9962f-275">**例**</span><span class="sxs-lookup"><span data-stu-id="9962f-275">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="9962f-276">関連項目</span><span class="sxs-lookup"><span data-stu-id="9962f-276">See also</span></span>

- [<span data-ttu-id="9962f-277">数学関数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9962f-277">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="9962f-278">Entity Framework 用 SqlClient 関数</span><span class="sxs-lookup"><span data-stu-id="9962f-278">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
