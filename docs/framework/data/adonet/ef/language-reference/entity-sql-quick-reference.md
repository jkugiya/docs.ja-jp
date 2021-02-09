---
description: '詳細情報: Entity SQL クイック リファレンス'
title: Entity SQL クイック リファレンス
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: ddac48bece1f0e9df737db295d4d028529ea290f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724558"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="01162-103">Entity SQL クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="01162-103">Entity SQL Quick Reference</span></span>

<span data-ttu-id="01162-104">このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリのクイック リファレンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="01162-104">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="01162-105">このトピックのクエリでは、AdventureWorks Sales Model が使用されています。</span><span class="sxs-lookup"><span data-stu-id="01162-105">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="01162-106">リテラル</span><span class="sxs-lookup"><span data-stu-id="01162-106">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="01162-107">String</span><span class="sxs-lookup"><span data-stu-id="01162-107">String</span></span>  

 <span data-ttu-id="01162-108">Unicode と非 Unicode の文字列リテラルがあります。</span><span class="sxs-lookup"><span data-stu-id="01162-108">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="01162-109">Unicode 文字列は先頭に N が付きます。たとえば、`N'hello'` のようになります。</span><span class="sxs-lookup"><span data-stu-id="01162-109">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="01162-110">非 Unicode 文字列リテラルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="01162-110">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="01162-111">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-111">Output:</span></span>  
  
|<span data-ttu-id="01162-112">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-112">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-113">hello</span><span class="sxs-lookup"><span data-stu-id="01162-113">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="01162-114">DateTime</span><span class="sxs-lookup"><span data-stu-id="01162-114">DateTime</span></span>  

 <span data-ttu-id="01162-115">DateTime リテラルでは、日付部分と時刻部分の両方が必須です。</span><span class="sxs-lookup"><span data-stu-id="01162-115">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="01162-116">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="01162-116">There are no default values.</span></span>  
  
 <span data-ttu-id="01162-117">例:</span><span class="sxs-lookup"><span data-stu-id="01162-117">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="01162-118">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-118">Output:</span></span>  
  
|<span data-ttu-id="01162-119">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-119">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-120">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="01162-120">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="01162-121">整数型</span><span class="sxs-lookup"><span data-stu-id="01162-121">Integer</span></span>  

 <span data-ttu-id="01162-122">整数リテラルには Int32 (123) 型、UInt32 (123U) 型、Int64 (123L) 型、および UInt64 (123UL) 型があります。</span><span class="sxs-lookup"><span data-stu-id="01162-122">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="01162-123">例:</span><span class="sxs-lookup"><span data-stu-id="01162-123">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="01162-124">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-124">Output:</span></span>  
  
|<span data-ttu-id="01162-125">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-125">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-126">1</span><span class="sxs-lookup"><span data-stu-id="01162-126">1</span></span>|  
|<span data-ttu-id="01162-127">2</span><span class="sxs-lookup"><span data-stu-id="01162-127">2</span></span>|  
|<span data-ttu-id="01162-128">3</span><span class="sxs-lookup"><span data-stu-id="01162-128">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="01162-129">その他</span><span class="sxs-lookup"><span data-stu-id="01162-129">Other</span></span>  

 <span data-ttu-id="01162-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされているその他のリテラルは、Guid、Binary、Float/Double、Decimal、および `null` です。</span><span class="sxs-lookup"><span data-stu-id="01162-130">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="01162-131">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の NULL リテラルは、概念モデルのその他すべての型と互換性があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="01162-131">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="01162-132">型コンストラクター</span><span class="sxs-lookup"><span data-stu-id="01162-132">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="01162-133">ROW</span><span class="sxs-lookup"><span data-stu-id="01162-133">ROW</span></span>  

 <span data-ttu-id="01162-134">[ROW](row-entity-sql.md) では、`ROW(1 AS myNumber, ‘Name’ AS myName).` のように、構造的に型付けされた匿名のレコード値が作成されます。</span><span class="sxs-lookup"><span data-stu-id="01162-134">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="01162-135">例:</span><span class="sxs-lookup"><span data-stu-id="01162-135">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="01162-136">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-136">Output:</span></span>  
  
|<span data-ttu-id="01162-137">ProductID</span><span class="sxs-lookup"><span data-stu-id="01162-137">ProductID</span></span>|<span data-ttu-id="01162-138">名前</span><span class="sxs-lookup"><span data-stu-id="01162-138">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="01162-139">1</span><span class="sxs-lookup"><span data-stu-id="01162-139">1</span></span>|<span data-ttu-id="01162-140">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="01162-140">Adjustable Race</span></span>|  
|<span data-ttu-id="01162-141">879</span><span class="sxs-lookup"><span data-stu-id="01162-141">879</span></span>|<span data-ttu-id="01162-142">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="01162-142">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="01162-143">712</span><span class="sxs-lookup"><span data-stu-id="01162-143">712</span></span>|<span data-ttu-id="01162-144">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="01162-144">AWC Logo Cap</span></span>|  
|<span data-ttu-id="01162-145">...</span><span class="sxs-lookup"><span data-stu-id="01162-145">...</span></span>|<span data-ttu-id="01162-146">...</span><span class="sxs-lookup"><span data-stu-id="01162-146">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="01162-147">MULTISET</span><span class="sxs-lookup"><span data-stu-id="01162-147">MULTISET</span></span>  

 <span data-ttu-id="01162-148">[MULTISET](multiset-entity-sql.md) では、次のようなコレクションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="01162-148">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="01162-149">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="01162-149">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="01162-150">例:</span><span class="sxs-lookup"><span data-stu-id="01162-150">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="01162-151">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-151">Output:</span></span>  
  
|<span data-ttu-id="01162-152">ProductID</span><span class="sxs-lookup"><span data-stu-id="01162-152">ProductID</span></span>|<span data-ttu-id="01162-153">名前</span><span class="sxs-lookup"><span data-stu-id="01162-153">Name</span></span>|<span data-ttu-id="01162-154">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="01162-154">ProductNumber</span></span>|<span data-ttu-id="01162-155">…</span><span class="sxs-lookup"><span data-stu-id="01162-155">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="01162-156">842</span><span class="sxs-lookup"><span data-stu-id="01162-156">842</span></span>|<span data-ttu-id="01162-157">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="01162-157">Touring-Panniers, Large</span></span>|<span data-ttu-id="01162-158">PA-T100</span><span class="sxs-lookup"><span data-stu-id="01162-158">PA-T100</span></span>|<span data-ttu-id="01162-159">…</span><span class="sxs-lookup"><span data-stu-id="01162-159">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="01162-160">Object</span><span class="sxs-lookup"><span data-stu-id="01162-160">Object</span></span>  

 <span data-ttu-id="01162-161">[名前付きの型コンストラクター](named-type-constructor-entity-sql.md)では、`person("abc", 12)` のように、名前付きのユーザー定義オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="01162-161">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="01162-162">例:</span><span class="sxs-lookup"><span data-stu-id="01162-162">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="01162-163">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-163">Output:</span></span>  
  
|<span data-ttu-id="01162-164">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="01162-164">SalesOrderDetailID</span></span>|<span data-ttu-id="01162-165">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="01162-165">CarrierTrackingNumber</span></span>|<span data-ttu-id="01162-166">OrderQty</span><span class="sxs-lookup"><span data-stu-id="01162-166">OrderQty</span></span>|<span data-ttu-id="01162-167">ProductID</span><span class="sxs-lookup"><span data-stu-id="01162-167">ProductID</span></span>|<span data-ttu-id="01162-168">...</span><span class="sxs-lookup"><span data-stu-id="01162-168">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="01162-169">1</span><span class="sxs-lookup"><span data-stu-id="01162-169">1</span></span>|<span data-ttu-id="01162-170">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="01162-170">4911-403C-98</span></span>|<span data-ttu-id="01162-171">1</span><span class="sxs-lookup"><span data-stu-id="01162-171">1</span></span>|<span data-ttu-id="01162-172">776</span><span class="sxs-lookup"><span data-stu-id="01162-172">776</span></span>|<span data-ttu-id="01162-173">...</span><span class="sxs-lookup"><span data-stu-id="01162-173">...</span></span>|  
|<span data-ttu-id="01162-174">2</span><span class="sxs-lookup"><span data-stu-id="01162-174">2</span></span>|<span data-ttu-id="01162-175">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="01162-175">4911-403C-98</span></span>|<span data-ttu-id="01162-176">3</span><span class="sxs-lookup"><span data-stu-id="01162-176">3</span></span>|<span data-ttu-id="01162-177">777</span><span class="sxs-lookup"><span data-stu-id="01162-177">777</span></span>|<span data-ttu-id="01162-178">...</span><span class="sxs-lookup"><span data-stu-id="01162-178">...</span></span>|  
|<span data-ttu-id="01162-179">...</span><span class="sxs-lookup"><span data-stu-id="01162-179">...</span></span>|<span data-ttu-id="01162-180">...</span><span class="sxs-lookup"><span data-stu-id="01162-180">...</span></span>|<span data-ttu-id="01162-181">...</span><span class="sxs-lookup"><span data-stu-id="01162-181">...</span></span>|<span data-ttu-id="01162-182">...</span><span class="sxs-lookup"><span data-stu-id="01162-182">...</span></span>|<span data-ttu-id="01162-183">...</span><span class="sxs-lookup"><span data-stu-id="01162-183">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="01162-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="01162-184">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="01162-185">REF</span><span class="sxs-lookup"><span data-stu-id="01162-185">REF</span></span>  

 <span data-ttu-id="01162-186">[REF](ref-entity-sql.md) では、エンティティ型のインスタンスへの参照が作成されます。</span><span class="sxs-lookup"><span data-stu-id="01162-186">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="01162-187">たとえば、次のクエリは、Orders エンティティ セットの各 Order エンティティへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="01162-187">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="01162-188">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-188">Output:</span></span>  
  
|<span data-ttu-id="01162-189">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-189">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-190">1</span><span class="sxs-lookup"><span data-stu-id="01162-190">1</span></span>|  
|<span data-ttu-id="01162-191">2</span><span class="sxs-lookup"><span data-stu-id="01162-191">2</span></span>|  
|<span data-ttu-id="01162-192">3</span><span class="sxs-lookup"><span data-stu-id="01162-192">3</span></span>|  
|<span data-ttu-id="01162-193">...</span><span class="sxs-lookup"><span data-stu-id="01162-193">...</span></span>|  
  
 <span data-ttu-id="01162-194">次の例では、プロパティ抽出演算子 (.) を使用して、エンティティのプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="01162-194">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="01162-195">プロパティ抽出演算子を使用すると、参照は自動的に逆参照されます。</span><span class="sxs-lookup"><span data-stu-id="01162-195">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="01162-196">例:</span><span class="sxs-lookup"><span data-stu-id="01162-196">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="01162-197">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-197">Output:</span></span>  
  
|<span data-ttu-id="01162-198">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-198">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-199">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="01162-199">Adjustable Race</span></span>|  
|<span data-ttu-id="01162-200">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="01162-200">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="01162-201">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="01162-201">AWC Logo Cap</span></span>|  
|<span data-ttu-id="01162-202">...</span><span class="sxs-lookup"><span data-stu-id="01162-202">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="01162-203">DEREF</span><span class="sxs-lookup"><span data-stu-id="01162-203">DEREF</span></span>  

 <span data-ttu-id="01162-204">[DEREF](deref-entity-sql.md) では、参照値が逆参照されて、その逆参照の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="01162-204">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="01162-205">たとえば、次のクエリは、`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2` のように、Orders エンティティ セットの各 Order について Order エンティティを生成します。</span><span class="sxs-lookup"><span data-stu-id="01162-205">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="01162-206">例:</span><span class="sxs-lookup"><span data-stu-id="01162-206">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="01162-207">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-207">Output:</span></span>  
  
|<span data-ttu-id="01162-208">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-208">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-209">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="01162-209">Adjustable Race</span></span>|  
|<span data-ttu-id="01162-210">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="01162-210">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="01162-211">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="01162-211">AWC Logo Cap</span></span>|  
|<span data-ttu-id="01162-212">...</span><span class="sxs-lookup"><span data-stu-id="01162-212">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="01162-213">CREATEREF と KEY</span><span class="sxs-lookup"><span data-stu-id="01162-213">CREATEREF AND KEY</span></span>  

 <span data-ttu-id="01162-214">[CREATEREF](createref-entity-sql.md) では、キーを渡す参照が作成されます。</span><span class="sxs-lookup"><span data-stu-id="01162-214">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="01162-215">[KEY](key-entity-sql.md) では、型参照を持つ式のキー部分が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="01162-215">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="01162-216">例:</span><span class="sxs-lookup"><span data-stu-id="01162-216">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="01162-217">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-217">Output:</span></span>  
  
|<span data-ttu-id="01162-218">ProductID</span><span class="sxs-lookup"><span data-stu-id="01162-218">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="01162-219">980</span><span class="sxs-lookup"><span data-stu-id="01162-219">980</span></span>|  
|<span data-ttu-id="01162-220">365</span><span class="sxs-lookup"><span data-stu-id="01162-220">365</span></span>|  
|<span data-ttu-id="01162-221">771</span><span class="sxs-lookup"><span data-stu-id="01162-221">771</span></span>|  
|<span data-ttu-id="01162-222">...</span><span class="sxs-lookup"><span data-stu-id="01162-222">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="01162-223">関数</span><span class="sxs-lookup"><span data-stu-id="01162-223">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="01162-224">正規</span><span class="sxs-lookup"><span data-stu-id="01162-224">Canonical</span></span>  

 <span data-ttu-id="01162-225">[正規関数](canonical-functions.md)の名前空間は Edm で、`Edm.Length("string")` のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="01162-225">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="01162-226">正規関数と同じ名前の関数を含んでいる別の名前空間がインポートされない限り、名前空間を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="01162-226">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="01162-227">2 つの名前空間に同じ関数が存在する場合は、完全な名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01162-227">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="01162-228">例:</span><span class="sxs-lookup"><span data-stu-id="01162-228">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="01162-229">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-229">Output:</span></span>  
  
|<span data-ttu-id="01162-230">NameLen</span><span class="sxs-lookup"><span data-stu-id="01162-230">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="01162-231">6</span><span class="sxs-lookup"><span data-stu-id="01162-231">6</span></span>|  
|<span data-ttu-id="01162-232">6</span><span class="sxs-lookup"><span data-stu-id="01162-232">6</span></span>|  
|<span data-ttu-id="01162-233">5</span><span class="sxs-lookup"><span data-stu-id="01162-233">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="01162-234">Microsoft プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="01162-234">Microsoft Provider-Specific</span></span>  

 <span data-ttu-id="01162-235">[Microsoft プロバイダー固有の関数](../sqlclient-for-ef-functions.md)は、`SqlServer` 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="01162-235">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="01162-236">例:</span><span class="sxs-lookup"><span data-stu-id="01162-236">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="01162-237">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-237">Output:</span></span>  
  
|<span data-ttu-id="01162-238">EmailLen</span><span class="sxs-lookup"><span data-stu-id="01162-238">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="01162-239">27</span><span class="sxs-lookup"><span data-stu-id="01162-239">27</span></span>|  
|<span data-ttu-id="01162-240">27</span><span class="sxs-lookup"><span data-stu-id="01162-240">27</span></span>|  
|<span data-ttu-id="01162-241">26</span><span class="sxs-lookup"><span data-stu-id="01162-241">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="01162-242">名前空間</span><span class="sxs-lookup"><span data-stu-id="01162-242">Namespaces</span></span>  

 <span data-ttu-id="01162-243">[USING](using-entity-sql.md) では、クエリ式で使用する名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="01162-243">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="01162-244">例:</span><span class="sxs-lookup"><span data-stu-id="01162-244">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="01162-245">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-245">Output:</span></span>  
  
|<span data-ttu-id="01162-246">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-246">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-247">aa</span><span class="sxs-lookup"><span data-stu-id="01162-247">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="01162-248">ページング</span><span class="sxs-lookup"><span data-stu-id="01162-248">Paging</span></span>  

 <span data-ttu-id="01162-249">ページングは、[ORDER BY](order-by-entity-sql.md) 句に対して [SKIP](skip-entity-sql.md) および [LIMIT](limit-entity-sql.md) サブ句を宣言することによって表すことができます。</span><span class="sxs-lookup"><span data-stu-id="01162-249">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="01162-250">例:</span><span class="sxs-lookup"><span data-stu-id="01162-250">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="01162-251">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-251">Output:</span></span>  
  
|<span data-ttu-id="01162-252">ID</span><span class="sxs-lookup"><span data-stu-id="01162-252">ID</span></span>|<span data-ttu-id="01162-253">名前</span><span class="sxs-lookup"><span data-stu-id="01162-253">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="01162-254">10</span><span class="sxs-lookup"><span data-stu-id="01162-254">10</span></span>|<span data-ttu-id="01162-255">Adina</span><span class="sxs-lookup"><span data-stu-id="01162-255">Adina</span></span>|  
|<span data-ttu-id="01162-256">11</span><span class="sxs-lookup"><span data-stu-id="01162-256">11</span></span>|<span data-ttu-id="01162-257">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="01162-257">Agcaoili</span></span>|  
|<span data-ttu-id="01162-258">12</span><span class="sxs-lookup"><span data-stu-id="01162-258">12</span></span>|<span data-ttu-id="01162-259">Aguilar</span><span class="sxs-lookup"><span data-stu-id="01162-259">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="01162-260">グループ化</span><span class="sxs-lookup"><span data-stu-id="01162-260">Grouping</span></span>  

 <span data-ttu-id="01162-261">[GROUPING BY](group-by-entity-sql.md) では、クエリ ([SELECT](select-entity-sql.md)) 式によって返されるオブジェクトをグループ化するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="01162-261">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="01162-262">例:</span><span class="sxs-lookup"><span data-stu-id="01162-262">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="01162-263">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-263">Output:</span></span>  
  
|<span data-ttu-id="01162-264">name</span><span class="sxs-lookup"><span data-stu-id="01162-264">name</span></span>|  
|----------|  
|<span data-ttu-id="01162-265">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="01162-265">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="01162-266">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="01162-266">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="01162-267">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="01162-267">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="01162-268">...</span><span class="sxs-lookup"><span data-stu-id="01162-268">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="01162-269">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="01162-269">Navigation</span></span>  

 <span data-ttu-id="01162-270">リレーションシップ ナビゲーション操作を使用すると、開始側のエンティティと終了側のエンティティ間のリレーションシップをナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="01162-270">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="01162-271">[NAVIGATE](navigate-entity-sql.md) は、\<namespace>.\<relationship type name> のように修飾されたリレーションシップ型を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="01162-271">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="01162-272">終了側のカーディナリティが 1 の場合、NAVIGATE から Ref\<T> が返されます。</span><span class="sxs-lookup"><span data-stu-id="01162-272">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="01162-273">終了側のカーディナリティが n の場合、Collection<Ref\<T>> が返されます。</span><span class="sxs-lookup"><span data-stu-id="01162-273">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="01162-274">例:</span><span class="sxs-lookup"><span data-stu-id="01162-274">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="01162-275">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-275">Output:</span></span>  
  
|<span data-ttu-id="01162-276">AddressID</span><span class="sxs-lookup"><span data-stu-id="01162-276">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="01162-277">1</span><span class="sxs-lookup"><span data-stu-id="01162-277">1</span></span>|  
|<span data-ttu-id="01162-278">2</span><span class="sxs-lookup"><span data-stu-id="01162-278">2</span></span>|  
|<span data-ttu-id="01162-279">3</span><span class="sxs-lookup"><span data-stu-id="01162-279">3</span></span>|  
|<span data-ttu-id="01162-280">...</span><span class="sxs-lookup"><span data-stu-id="01162-280">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="01162-281">SELECT VALUE AND SELECT</span><span class="sxs-lookup"><span data-stu-id="01162-281">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="01162-282">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="01162-282">SELECT VALUE</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="01162-283">には、暗黙の行の構築をスキップする SELECT VALUE 句が用意されています。</span><span class="sxs-lookup"><span data-stu-id="01162-283">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="01162-284">SELECT VALUE 句には 1 つの項目のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="01162-284">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="01162-285">このような句を使用した場合、SELECT 句内の項目には row ラッパーは構築されず、`SELECT VALUE a` などの目的の構造を持つコレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="01162-285">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="01162-286">例:</span><span class="sxs-lookup"><span data-stu-id="01162-286">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="01162-287">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-287">Output:</span></span>  
  
|<span data-ttu-id="01162-288">名前</span><span class="sxs-lookup"><span data-stu-id="01162-288">Name</span></span>|  
|----------|  
|<span data-ttu-id="01162-289">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="01162-289">Adjustable Race</span></span>|  
|<span data-ttu-id="01162-290">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="01162-290">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="01162-291">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="01162-291">AWC Logo Cap</span></span>|  
|<span data-ttu-id="01162-292">...</span><span class="sxs-lookup"><span data-stu-id="01162-292">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="01162-293">SELECT</span><span class="sxs-lookup"><span data-stu-id="01162-293">SELECT</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="01162-294">には、任意の行を構築するための行コンストラクターも用意されています。</span><span class="sxs-lookup"><span data-stu-id="01162-294">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="01162-295">SELECT は、投影内の 1 つまたは複数の要素、および `SELECT a, b, c` などのフィールドを持つデータ レコードの結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="01162-295">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="01162-296">例:</span><span class="sxs-lookup"><span data-stu-id="01162-296">Example:</span></span>  
  
 <span data-ttu-id="01162-297">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="01162-297">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="01162-298">名前</span><span class="sxs-lookup"><span data-stu-id="01162-298">Name</span></span>|<span data-ttu-id="01162-299">ProductID</span><span class="sxs-lookup"><span data-stu-id="01162-299">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="01162-300">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="01162-300">Adjustable Race</span></span>|<span data-ttu-id="01162-301">1</span><span class="sxs-lookup"><span data-stu-id="01162-301">1</span></span>|  
|<span data-ttu-id="01162-302">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="01162-302">All-Purpose Bike Stand</span></span>|<span data-ttu-id="01162-303">879</span><span class="sxs-lookup"><span data-stu-id="01162-303">879</span></span>|  
|<span data-ttu-id="01162-304">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="01162-304">AWC Logo Cap</span></span>|<span data-ttu-id="01162-305">712</span><span class="sxs-lookup"><span data-stu-id="01162-305">712</span></span>|  
|<span data-ttu-id="01162-306">...</span><span class="sxs-lookup"><span data-stu-id="01162-306">...</span></span>|<span data-ttu-id="01162-307">...</span><span class="sxs-lookup"><span data-stu-id="01162-307">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="01162-308">CASE 式</span><span class="sxs-lookup"><span data-stu-id="01162-308">CASE EXPRESSION</span></span>  

 <span data-ttu-id="01162-309">[CASE 式](case-entity-sql.md)では、一連のブール式が評価されて結果が判定されます。</span><span class="sxs-lookup"><span data-stu-id="01162-309">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="01162-310">例:</span><span class="sxs-lookup"><span data-stu-id="01162-310">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="01162-311">Output:</span><span class="sxs-lookup"><span data-stu-id="01162-311">Output:</span></span>  
  
|<span data-ttu-id="01162-312">[値]</span><span class="sxs-lookup"><span data-stu-id="01162-312">Value</span></span>|  
|-----------|  
|<span data-ttu-id="01162-313">true</span><span class="sxs-lookup"><span data-stu-id="01162-313">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01162-314">関連項目</span><span class="sxs-lookup"><span data-stu-id="01162-314">See also</span></span>

- [<span data-ttu-id="01162-315">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="01162-315">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="01162-316">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="01162-316">Entity SQL Overview</span></span>](entity-sql-overview.md)
