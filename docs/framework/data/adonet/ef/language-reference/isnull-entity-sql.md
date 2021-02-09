---
description: '詳細情報: ISNULL (Entity SQL)'
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 1dbaf964facf089ab6714ebd58baf8b040288cff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748493"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="da8cc-103">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="da8cc-103">ISNULL (Entity SQL)</span></span>

<span data-ttu-id="da8cc-104">クエリ式が NULL かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="da8cc-104">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8cc-105">構文</span><span class="sxs-lookup"><span data-stu-id="da8cc-105">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="da8cc-106">引数</span><span class="sxs-lookup"><span data-stu-id="da8cc-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="da8cc-107">任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="da8cc-107">Any valid query expression.</span></span> <span data-ttu-id="da8cc-108">コレクションにすることはできません。また、コレクション メンバーや、コレクション型のプロパティを持つレコード型を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="da8cc-108">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="da8cc-109">NOT</span><span class="sxs-lookup"><span data-stu-id="da8cc-109">NOT</span></span>  
 <span data-ttu-id="da8cc-110">IS NULL の EDM.Boolean の結果を否定します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-110">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da8cc-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="da8cc-111">Return Value</span></span>  

 <span data-ttu-id="da8cc-112">`true` によって NULL が返される場合は `expression`、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="da8cc-112">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da8cc-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="da8cc-113">Remarks</span></span>  

 <span data-ttu-id="da8cc-114">外部結合の要素が NULL かどうかを確認するには、`IS NULL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-114">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="da8cc-115">メンバーに実際の値が含まれているかどうかを確認するには、`IS NULL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-115">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="da8cc-116">次の表は、いくつかのパターンにおける `IS NULL` の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="da8cc-116">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="da8cc-117">すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="da8cc-117">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="da8cc-118">パターン</span><span class="sxs-lookup"><span data-stu-id="da8cc-118">Pattern</span></span>|<span data-ttu-id="da8cc-119">動作</span><span class="sxs-lookup"><span data-stu-id="da8cc-119">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="da8cc-120">null IS NULL</span><span class="sxs-lookup"><span data-stu-id="da8cc-120">null IS NULL</span></span>|<span data-ttu-id="da8cc-121">`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-121">Returns `true`.</span></span>|  
|<span data-ttu-id="da8cc-122">TREAT (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="da8cc-122">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="da8cc-123">`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-123">Returns `true`.</span></span>|  
|<span data-ttu-id="da8cc-124">TREAT (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="da8cc-124">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="da8cc-125">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="da8cc-125">Throws an error.</span></span>|  
|<span data-ttu-id="da8cc-126">TREAT (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="da8cc-126">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="da8cc-127">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="da8cc-127">Throws an error.</span></span>|  
|<span data-ttu-id="da8cc-128">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="da8cc-128">EntityType IS NULL</span></span>|<span data-ttu-id="da8cc-129">`true` または `false`を返します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-129">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="da8cc-130">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="da8cc-130">ComplexType IS NULL</span></span>|<span data-ttu-id="da8cc-131">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="da8cc-131">Throws an error.</span></span>|  
|<span data-ttu-id="da8cc-132">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="da8cc-132">RowType IS NULL</span></span>|<span data-ttu-id="da8cc-133">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="da8cc-133">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="da8cc-134">例</span><span class="sxs-lookup"><span data-stu-id="da8cc-134">Example</span></span>  

 <span data-ttu-id="da8cc-135">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、IS NOT NULL 演算子を使用して、クエリ式が NULL でないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-135">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="da8cc-136">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="da8cc-136">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="da8cc-137">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-137">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="da8cc-138">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="da8cc-138">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="da8cc-139">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="da8cc-139">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="da8cc-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="da8cc-140">See also</span></span>

- [<span data-ttu-id="da8cc-141">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="da8cc-141">Entity SQL Reference</span></span>](entity-sql-reference.md)
