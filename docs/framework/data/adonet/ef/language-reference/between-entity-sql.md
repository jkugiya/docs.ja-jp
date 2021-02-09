---
description: '詳細情報: BETWEEN (Entity SQL)'
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 35ac16e94f2e55f6a0f76591daf0f91f9708aa53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697115"
---
# <a name="between-entity-sql"></a><span data-ttu-id="f7f16-103">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f7f16-103">BETWEEN (Entity SQL)</span></span>

<span data-ttu-id="f7f16-104">式の結果が指定の範囲内の値になるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="f7f16-104">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="f7f16-105">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の BETWEEN 式は、Transact-SQL の BETWEEN 式と同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="f7f16-105">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7f16-106">構文</span><span class="sxs-lookup"><span data-stu-id="f7f16-106">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="f7f16-107">引数</span><span class="sxs-lookup"><span data-stu-id="f7f16-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="f7f16-108">`begin_expression` と `end_expression` で定義される範囲についてテストするための任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="f7f16-108">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="f7f16-109">`expression` は、`begin_expression` と `end_expression` の両方と同じ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7f16-109">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="f7f16-110">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="f7f16-110">Any valid expression.</span></span> <span data-ttu-id="f7f16-111">`begin_expression` は、`expression` と `end_expression` の両方と同じ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7f16-111">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="f7f16-112">`begin_expression` は、`end_expression` 未満でなければなりません。それ以外の場合、戻り値は否定されます。</span><span class="sxs-lookup"><span data-stu-id="f7f16-112">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="f7f16-113">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="f7f16-113">Any valid expression.</span></span> <span data-ttu-id="f7f16-114">`end_expression` は、`expression` と `begin_expression` の両方と同じ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7f16-114">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="f7f16-115">NOT</span><span class="sxs-lookup"><span data-stu-id="f7f16-115">NOT</span></span>  
 <span data-ttu-id="f7f16-116">BETWEEN の結果を否定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7f16-116">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="f7f16-117">AND</span><span class="sxs-lookup"><span data-stu-id="f7f16-117">AND</span></span>  
 <span data-ttu-id="f7f16-118">`expression` と `begin_expression` で表される範囲内で `end_expression` をテストする必要があることを示すプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="f7f16-118">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7f16-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="f7f16-119">Return Value</span></span>  

 <span data-ttu-id="f7f16-120">`true` が、`expression` と `begin_expression` で指定される範囲内にある場合は `end_expression`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="f7f16-120">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="f7f16-121">`null` が `expression` であるか、`null` または `begin_expression` が `end_expression` である場合は、`null` が返されます。</span><span class="sxs-lookup"><span data-stu-id="f7f16-121">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7f16-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="f7f16-122">Remarks</span></span>  

 <span data-ttu-id="f7f16-123">両端を除いた範囲を指定するには、BETWEEN の代わりに、より大きい (>) とより小さい (<) を意味する演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7f16-123">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7f16-124">例</span><span class="sxs-lookup"><span data-stu-id="f7f16-124">Example</span></span>  

 <span data-ttu-id="f7f16-125">次の Entity SQL クエリでは、BETWEEN 演算子を使用して、式の結果が指定の範囲内の値になるかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="f7f16-125">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="f7f16-126">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f7f16-126">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f7f16-127">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f7f16-127">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f7f16-128">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f7f16-128">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f7f16-129">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f7f16-129">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="f7f16-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7f16-130">See also</span></span>

- [<span data-ttu-id="f7f16-131">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="f7f16-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
