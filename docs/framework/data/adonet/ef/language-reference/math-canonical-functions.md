---
description: '詳細情報: 数値演算正規関数'
title: 数値演算正規関数
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 55072099f5766d48ea3067a2e9eaa187a8b3f111
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739366"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="b917a-103">数値演算正規関数</span><span class="sxs-lookup"><span data-stu-id="b917a-103">Math Canonical Functions</span></span>

<span data-ttu-id="b917a-104">Entity SQL には、次の数値演算正規関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b917a-104">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="b917a-105">Abs(value)</span><span class="sxs-lookup"><span data-stu-id="b917a-105">Abs(value)</span></span>

<span data-ttu-id="b917a-106">`value` の絶対値を返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-106">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="b917a-107">**引数**</span><span class="sxs-lookup"><span data-stu-id="b917a-107">**Arguments**</span></span>

<span data-ttu-id="b917a-108">`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、および `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-108">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="b917a-109">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="b917a-109">**Return Value**</span></span>

<span data-ttu-id="b917a-110">`value` の型。</span><span class="sxs-lookup"><span data-stu-id="b917a-110">The type of `value`.</span></span>

<span data-ttu-id="b917a-111">**例**</span><span class="sxs-lookup"><span data-stu-id="b917a-111">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="b917a-112">Ceiling(value)</span><span class="sxs-lookup"><span data-stu-id="b917a-112">Ceiling(value)</span></span>

<span data-ttu-id="b917a-113">`value` 以上で最小の整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-113">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="b917a-114">**引数**</span><span class="sxs-lookup"><span data-stu-id="b917a-114">**Arguments**</span></span>

<span data-ttu-id="b917a-115">`Single`、`Double`、および `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-115">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="b917a-116">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="b917a-116">**Return Value**</span></span>

<span data-ttu-id="b917a-117">`value` の型。</span><span class="sxs-lookup"><span data-stu-id="b917a-117">The type of `value`.</span></span>

<span data-ttu-id="b917a-118">**例**</span><span class="sxs-lookup"><span data-stu-id="b917a-118">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="b917a-119">Floor(value)</span><span class="sxs-lookup"><span data-stu-id="b917a-119">Floor(value)</span></span>

<span data-ttu-id="b917a-120">`value` 以下で最大の整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-120">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="b917a-121">**引数**</span><span class="sxs-lookup"><span data-stu-id="b917a-121">**Arguments**</span></span>

<span data-ttu-id="b917a-122">`Single`、`Double`、および `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-122">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="b917a-123">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="b917a-123">**Return Value**</span></span>

<span data-ttu-id="b917a-124">`value` の型。</span><span class="sxs-lookup"><span data-stu-id="b917a-124">The type of `value`.</span></span>

<span data-ttu-id="b917a-125">**例**</span><span class="sxs-lookup"><span data-stu-id="b917a-125">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="b917a-126">Power(value, exponent)</span><span class="sxs-lookup"><span data-stu-id="b917a-126">Power(value, exponent)</span></span>

<span data-ttu-id="b917a-127">指定された `value` を指定された `exponent` でべき乗した結果を返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-127">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="b917a-128">**引数**</span><span class="sxs-lookup"><span data-stu-id="b917a-128">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="b917a-129">`Int32, Int64, Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-129">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="b917a-130">`Int64`、`Double`、または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-130">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="b917a-131">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="b917a-131">**Return Value**</span></span>

<span data-ttu-id="b917a-132">`value` の型。</span><span class="sxs-lookup"><span data-stu-id="b917a-132">The type of `value`.</span></span>

<span data-ttu-id="b917a-133">**例**</span><span class="sxs-lookup"><span data-stu-id="b917a-133">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="b917a-134">Round(value)</span><span class="sxs-lookup"><span data-stu-id="b917a-134">Round(value)</span></span>

<span data-ttu-id="b917a-135">最も近い整数に丸められた `value` の整数部分を返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-135">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="b917a-136">**引数**</span><span class="sxs-lookup"><span data-stu-id="b917a-136">**Arguments**</span></span>

<span data-ttu-id="b917a-137">`Single`、`Double`、および `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-137">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="b917a-138">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="b917a-138">**Return Value**</span></span>

<span data-ttu-id="b917a-139">`value` の型。</span><span class="sxs-lookup"><span data-stu-id="b917a-139">The type of `value`.</span></span>

<span data-ttu-id="b917a-140">**例**</span><span class="sxs-lookup"><span data-stu-id="b917a-140">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="b917a-141">Round(value, digits)</span><span class="sxs-lookup"><span data-stu-id="b917a-141">Round(value, digits)</span></span>

<span data-ttu-id="b917a-142">`value` を指定された最も近い `digits` に丸めて返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-142">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="b917a-143">**引数**</span><span class="sxs-lookup"><span data-stu-id="b917a-143">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="b917a-144">`Double` または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-144">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="b917a-145">`Int16` または `Int32`。</span><span class="sxs-lookup"><span data-stu-id="b917a-145">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="b917a-146">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="b917a-146">**Return Value**</span></span>

<span data-ttu-id="b917a-147">`value` の型。</span><span class="sxs-lookup"><span data-stu-id="b917a-147">The type of `value`.</span></span>

<span data-ttu-id="b917a-148">**例**</span><span class="sxs-lookup"><span data-stu-id="b917a-148">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="b917a-149">Truncate(value, digits)</span><span class="sxs-lookup"><span data-stu-id="b917a-149">Truncate(value, digits)</span></span>

<span data-ttu-id="b917a-150">`value` を指定された最も近い `digits` に切り詰めて返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-150">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="b917a-151">**引数**</span><span class="sxs-lookup"><span data-stu-id="b917a-151">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="b917a-152">`Double` または `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="b917a-152">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="b917a-153">`Int16` または `Int32`。</span><span class="sxs-lookup"><span data-stu-id="b917a-153">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="b917a-154">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="b917a-154">**Return Value**</span></span>

<span data-ttu-id="b917a-155">`value` の型。</span><span class="sxs-lookup"><span data-stu-id="b917a-155">The type of `value`.</span></span>

<span data-ttu-id="b917a-156">**例**</span><span class="sxs-lookup"><span data-stu-id="b917a-156">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="b917a-157">`null` が入力された場合、これらの関数は `null` を返します。</span><span class="sxs-lookup"><span data-stu-id="b917a-157">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="b917a-158">同等の機能は、Microsoft SQL クライアント マネージド プロバイダーでも利用できます。</span><span class="sxs-lookup"><span data-stu-id="b917a-158">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="b917a-159">詳細については、「[Entity Framework 用 SqlClient 関数](../sqlclient-for-ef-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b917a-159">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b917a-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="b917a-160">See also</span></span>

- [<span data-ttu-id="b917a-161">正規関数</span><span class="sxs-lookup"><span data-stu-id="b917a-161">Canonical Functions</span></span>](canonical-functions.md)
