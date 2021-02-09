---
description: '詳細情報: EXCEPT (Entity SQL)'
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: fd66d8dc6e22a73afbfd27e6eb1fd6c8bb9d3475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786395"
---
# <a name="except-entity-sql"></a><span data-ttu-id="54eed-103">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="54eed-103">EXCEPT (Entity SQL)</span></span>

<span data-ttu-id="54eed-104">EXCEPT オペランドの左辺のクエリ式から返される結果のうち、右辺のクエリ式でも返される結果を除いた、重複しない値のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="54eed-104">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="54eed-105">すべての式は、 `expression`と同じ型であるか、共通の基本型または派生型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="54eed-105">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54eed-106">構文</span><span class="sxs-lookup"><span data-stu-id="54eed-106">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="54eed-107">引数</span><span class="sxs-lookup"><span data-stu-id="54eed-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="54eed-108">コレクションを返す任意の有効なクエリ式。もう一方のクエリ式から返されたコレクションと比較されます。</span><span class="sxs-lookup"><span data-stu-id="54eed-108">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54eed-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="54eed-109">Return Value</span></span>  

 <span data-ttu-id="54eed-110">`expression`と同じ型であるか、共通の基本データ型または派生型であるコレクション。</span><span class="sxs-lookup"><span data-stu-id="54eed-110">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54eed-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="54eed-111">Remarks</span></span>  

 <span data-ttu-id="54eed-112">EXCEPT は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="54eed-112">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="54eed-113">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="54eed-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="54eed-114">次の表に、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集合演算子の優先順位を示します。</span><span class="sxs-lookup"><span data-stu-id="54eed-114">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="54eed-115">優先順位</span><span class="sxs-lookup"><span data-stu-id="54eed-115">Precedence</span></span>|<span data-ttu-id="54eed-116">演算子</span><span class="sxs-lookup"><span data-stu-id="54eed-116">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="54eed-117">最高</span><span class="sxs-lookup"><span data-stu-id="54eed-117">Highest</span></span>|<span data-ttu-id="54eed-118">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="54eed-118">INTERSECT</span></span>|  
||<span data-ttu-id="54eed-119">UNION</span><span class="sxs-lookup"><span data-stu-id="54eed-119">UNION</span></span><br /><br /> <span data-ttu-id="54eed-120">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="54eed-120">UNION ALL</span></span>|  
||<span data-ttu-id="54eed-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="54eed-121">EXCEPT</span></span>|  
|<span data-ttu-id="54eed-122">最低</span><span class="sxs-lookup"><span data-stu-id="54eed-122">Lowest</span></span>|<span data-ttu-id="54eed-123">EXISTS</span><span class="sxs-lookup"><span data-stu-id="54eed-123">EXISTS</span></span><br /><br /> <span data-ttu-id="54eed-124">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="54eed-124">OVERLAPS</span></span><br /><br /> <span data-ttu-id="54eed-125">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="54eed-125">FLATTEN</span></span><br /><br /> <span data-ttu-id="54eed-126">SET</span><span class="sxs-lookup"><span data-stu-id="54eed-126">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54eed-127">例</span><span class="sxs-lookup"><span data-stu-id="54eed-127">Example</span></span>  

 <span data-ttu-id="54eed-128">次の Entity SQL クエリでは、EXCEPT 演算子を使用して、2 つのクエリ式から重複しない値のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="54eed-128">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="54eed-129">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="54eed-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="54eed-130">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="54eed-130">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="54eed-131">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="54eed-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="54eed-132">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="54eed-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="54eed-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="54eed-133">See also</span></span>

- [<span data-ttu-id="54eed-134">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="54eed-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
