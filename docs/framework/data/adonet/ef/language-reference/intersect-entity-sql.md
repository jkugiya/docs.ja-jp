---
description: '詳細情報: INTERSECT (Entity SQL)'
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 45c0434f6fc0ed6c110162d7e34d76c336635b0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748512"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="9ca5f-103">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9ca5f-103">INTERSECT (Entity SQL)</span></span>

<span data-ttu-id="9ca5f-104">INTERSECT オペランドの左右両方のクエリ式によって返される個別の値のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-104">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="9ca5f-105">すべての式は、 `expression`と同じ型であるか、共通の基本型または派生型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-105">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca5f-106">構文</span><span class="sxs-lookup"><span data-stu-id="9ca5f-106">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9ca5f-107">引数</span><span class="sxs-lookup"><span data-stu-id="9ca5f-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9ca5f-108">コレクションを返す任意の有効なクエリ式。もう一方のクエリ式から返されたコレクションと比較されます。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-108">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ca5f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ca5f-109">Return Value</span></span>  

 <span data-ttu-id="9ca5f-110">`expression`と同じ型であるか、共通の基本データ型または派生型であるコレクション。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-110">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ca5f-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="9ca5f-111">Remarks</span></span>  

 <span data-ttu-id="9ca5f-112">INTERSECT は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-112">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="9ca5f-113">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="9ca5f-114">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の優先順位に関する情報については、「[EXCEPT](except-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ca5f-115">例</span><span class="sxs-lookup"><span data-stu-id="9ca5f-115">Example</span></span>  

 <span data-ttu-id="9ca5f-116">次の Entity SQL クエリでは、INTERSECT 演算子を使用して、INTERSECT オペランドの左右両方のクエリ式によって返される個別の値のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-116">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="9ca5f-117">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9ca5f-118">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9ca5f-119">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9ca5f-120">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="9ca5f-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="9ca5f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ca5f-121">See also</span></span>

- [<span data-ttu-id="9ca5f-122">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="9ca5f-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
