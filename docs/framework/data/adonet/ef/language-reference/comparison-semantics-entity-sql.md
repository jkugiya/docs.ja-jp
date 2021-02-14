---
description: '詳細情報: 比較セマンティクス (Entity SQL)'
title: 比較セマンティクス (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: b1c832cb6f2903073b1c6be806c73823b1f4a220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786434"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="c4c0b-103">比較セマンティクス (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c4c0b-103">Comparison Semantics (Entity SQL)</span></span>

<span data-ttu-id="c4c0b-104">次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-104">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="c4c0b-105">明示的な比較</span><span class="sxs-lookup"><span data-stu-id="c4c0b-105">Explicit comparison</span></span>  

 <span data-ttu-id="c4c0b-106">等価演算</span><span class="sxs-lookup"><span data-stu-id="c4c0b-106">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="c4c0b-107">!=</span><span class="sxs-lookup"><span data-stu-id="c4c0b-107">!=</span></span>  
  
 <span data-ttu-id="c4c0b-108">順序付け操作</span><span class="sxs-lookup"><span data-stu-id="c4c0b-108">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="c4c0b-109">NULL 値が許容される操作</span><span class="sxs-lookup"><span data-stu-id="c4c0b-109">Nullability operations:</span></span>  
  
- <span data-ttu-id="c4c0b-110">IS_NULL</span><span class="sxs-lookup"><span data-stu-id="c4c0b-110">IS NULL</span></span>  
  
- <span data-ttu-id="c4c0b-111">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="c4c0b-111">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="c4c0b-112">明示的な区別</span><span class="sxs-lookup"><span data-stu-id="c4c0b-112">Explicit distinction</span></span>  

 <span data-ttu-id="c4c0b-113">等価区別</span><span class="sxs-lookup"><span data-stu-id="c4c0b-113">Equality distinction:</span></span>  
  
- <span data-ttu-id="c4c0b-114">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="c4c0b-114">DISTINCT</span></span>  
  
- <span data-ttu-id="c4c0b-115">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="c4c0b-115">GROUP BY</span></span>  
  
 <span data-ttu-id="c4c0b-116">順序付け区別</span><span class="sxs-lookup"><span data-stu-id="c4c0b-116">Ordering distinction:</span></span>  
  
- <span data-ttu-id="c4c0b-117">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="c4c0b-117">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="c4c0b-118">暗黙的な区別</span><span class="sxs-lookup"><span data-stu-id="c4c0b-118">Implicit distinction</span></span>  

 <span data-ttu-id="c4c0b-119">設定操作および述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="c4c0b-119">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="c4c0b-120">UNION</span><span class="sxs-lookup"><span data-stu-id="c4c0b-120">UNION</span></span>  
  
- <span data-ttu-id="c4c0b-121">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="c4c0b-121">INTERSECT</span></span>  
  
- <span data-ttu-id="c4c0b-122">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="c4c0b-122">EXCEPT</span></span>  
  
- <span data-ttu-id="c4c0b-123">SET</span><span class="sxs-lookup"><span data-stu-id="c4c0b-123">SET</span></span>  
  
- <span data-ttu-id="c4c0b-124">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="c4c0b-124">OVERLAPS</span></span>  
  
 <span data-ttu-id="c4c0b-125">項目述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="c4c0b-125">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="c4c0b-126">IN</span><span class="sxs-lookup"><span data-stu-id="c4c0b-126">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="c4c0b-127">サポートされている組み合わせ</span><span class="sxs-lookup"><span data-stu-id="c4c0b-127">Supported Combinations</span></span>  

 <span data-ttu-id="c4c0b-128">次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-128">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="c4c0b-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-129">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="c4c0b-130">**!=**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-130">**!=**</span></span>|<span data-ttu-id="c4c0b-131">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-131">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="c4c0b-132">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-132">**DISTINCT**</span></span>|<span data-ttu-id="c4c0b-133">**UNION**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-133">**UNION**</span></span><br /><br /> <span data-ttu-id="c4c0b-134">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-134">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="c4c0b-135">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-135">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="c4c0b-136">**SET**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-136">**SET**</span></span><br /><br /> <span data-ttu-id="c4c0b-137">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-137">**OVERLAPS**</span></span>|<span data-ttu-id="c4c0b-138">**IN**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-138">**IN**</span></span>|<span data-ttu-id="c4c0b-139">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-139">**<   <=**</span></span><br /><br /> <span data-ttu-id="c4c0b-140">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-140">**>   >=**</span></span>|<span data-ttu-id="c4c0b-141">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-141">**ORDER BY**</span></span>|<span data-ttu-id="c4c0b-142">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-142">**IS NULL**</span></span><br /><br /> <span data-ttu-id="c4c0b-143">**IS NOT NULL**</span><span class="sxs-lookup"><span data-stu-id="c4c0b-143">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="c4c0b-144">エンティティ型</span><span class="sxs-lookup"><span data-stu-id="c4c0b-144">Entity type</span></span>|<span data-ttu-id="c4c0b-145">参照<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-145">Ref<sup>1</sup></span></span>|<span data-ttu-id="c4c0b-146">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="c4c0b-147">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="c4c0b-148">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-148">All properties<sup>2</sup></span></span>|<span data-ttu-id="c4c0b-149">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-150">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-150">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-151">参照<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-151">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="c4c0b-152">複合型</span><span class="sxs-lookup"><span data-stu-id="c4c0b-152">Complex type</span></span>|<span data-ttu-id="c4c0b-153">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-154">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-155">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-156">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-157">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-158">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-158">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-159">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-159">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="c4c0b-160">行</span><span class="sxs-lookup"><span data-stu-id="c4c0b-160">Row</span></span>|<span data-ttu-id="c4c0b-161">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="c4c0b-162">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="c4c0b-163">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-163">All properties<sup>4</sup></span></span>|<span data-ttu-id="c4c0b-164">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-165">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-165">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-166">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-166">All properties<sup>4</sup></span></span>|<span data-ttu-id="c4c0b-167">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-167">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="c4c0b-168">プリミティブ型</span><span class="sxs-lookup"><span data-stu-id="c4c0b-168">Primitive type</span></span>|<span data-ttu-id="c4c0b-169">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="c4c0b-169">Provider-specific</span></span>|<span data-ttu-id="c4c0b-170">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="c4c0b-170">Provider-specific</span></span>|<span data-ttu-id="c4c0b-171">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="c4c0b-171">Provider-specific</span></span>|<span data-ttu-id="c4c0b-172">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="c4c0b-172">Provider-specific</span></span>|<span data-ttu-id="c4c0b-173">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="c4c0b-173">Provider-specific</span></span>|<span data-ttu-id="c4c0b-174">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="c4c0b-174">Provider-specific</span></span>|<span data-ttu-id="c4c0b-175">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="c4c0b-175">Provider-specific</span></span>|  
|<span data-ttu-id="c4c0b-176">マルチセット</span><span class="sxs-lookup"><span data-stu-id="c4c0b-176">Multiset</span></span>|<span data-ttu-id="c4c0b-177">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-178">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-179">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-180">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-181">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-182">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-182">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-183">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-183">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="c4c0b-184">参照</span><span class="sxs-lookup"><span data-stu-id="c4c0b-184">Ref</span></span>|<span data-ttu-id="c4c0b-185">○<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="c4c0b-186">○<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="c4c0b-187">○<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="c4c0b-188">○<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-188">Yes<sup>5</sup></span></span>|<span data-ttu-id="c4c0b-189">Throw</span><span class="sxs-lookup"><span data-stu-id="c4c0b-189">Throw</span></span>|<span data-ttu-id="c4c0b-190">Throw</span><span class="sxs-lookup"><span data-stu-id="c4c0b-190">Throw</span></span>|<span data-ttu-id="c4c0b-191">○<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-191">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="c4c0b-192">関連付け</span><span class="sxs-lookup"><span data-stu-id="c4c0b-192">Association</span></span><br /><br /> <span data-ttu-id="c4c0b-193">型</span><span class="sxs-lookup"><span data-stu-id="c4c0b-193">type</span></span>|<span data-ttu-id="c4c0b-194">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-194">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-195">Throw</span><span class="sxs-lookup"><span data-stu-id="c4c0b-195">Throw</span></span>|<span data-ttu-id="c4c0b-196">Throw</span><span class="sxs-lookup"><span data-stu-id="c4c0b-196">Throw</span></span>|<span data-ttu-id="c4c0b-197">Throw</span><span class="sxs-lookup"><span data-stu-id="c4c0b-197">Throw</span></span>|<span data-ttu-id="c4c0b-198">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-199">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-199">Throw<sup>3</sup></span></span>|<span data-ttu-id="c4c0b-200">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c4c0b-200">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="c4c0b-201"><sup>1</sup> 次の例に示すように、エンティティ型インスタンスの参照は暗黙的に比較されます。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-201"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="c4c0b-202">エンティティ インスタンスは、明示的な参照に対して比較できません。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-202">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="c4c0b-203">明示的な参照に対する比較を行った場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-203">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="c4c0b-204">たとえば、次のクエリを実行すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-204">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="c4c0b-205"><sup>2</sup> 複合型のプロパティは、ストアに送信される前にフラット化されるので、比較が可能になります (すべてのプロパティが比較可能である場合)。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-205"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="c4c0b-206"><sup>4</sup> も参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-206">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="c4c0b-207"><sup>3</sup> Entity Framework ランタイムでは、サポートされていないケースが検出され、プロバイダー/ストアは呼び出されずに、意味のある例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-207"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="c4c0b-208"><sup>4</sup> すべてのプロパティの比較が試行されます。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-208"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="c4c0b-209">比較不能な型のプロパティ (text、ntext、image など) がある場合、サーバー例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-209">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="c4c0b-210"><sup>5</sup> 参照のすべての個々の要素 (エンティティ セット名およびエンティティ型のすべてのキー プロパティを含む) が比較されます。</span><span class="sxs-lookup"><span data-stu-id="c4c0b-210"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c0b-211">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4c0b-211">See also</span></span>

- [<span data-ttu-id="c4c0b-212">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="c4c0b-212">Entity SQL Overview</span></span>](entity-sql-overview.md)
