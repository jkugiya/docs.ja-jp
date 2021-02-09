---
description: '詳細情報: UNION (Entity SQL)'
title: UNION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: f02b3d76d8c21848b7a1b7ef5e7bbf749aea5c0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673311"
---
# <a name="union-entity-sql"></a><span data-ttu-id="3987a-103">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3987a-103">UNION (Entity SQL)</span></span>

<span data-ttu-id="3987a-104">複数のクエリの結果を 1 つのコレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="3987a-104">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3987a-105">構文</span><span class="sxs-lookup"><span data-stu-id="3987a-105">Syntax</span></span>  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3987a-106">引数</span><span class="sxs-lookup"><span data-stu-id="3987a-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="3987a-107">コレクションと結合するコレクションを返す任意の有効なクエリ式。すべての式は、 `expression`と同じ型であるか、共通の基本データ型または派生型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3987a-107">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="3987a-108">UNION</span><span class="sxs-lookup"><span data-stu-id="3987a-108">UNION</span></span>  
 <span data-ttu-id="3987a-109">複数のコレクションを結合し、1 つのコレクションとして返すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="3987a-109">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="3987a-110">ALL</span><span class="sxs-lookup"><span data-stu-id="3987a-110">ALL</span></span>  
 <span data-ttu-id="3987a-111">複数のコレクションを結合し、重複も含めて 1 つのコレクションとして返すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="3987a-111">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="3987a-112">指定しない場合、重複は結果コレクションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="3987a-112">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3987a-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="3987a-113">Return Value</span></span>  

 <span data-ttu-id="3987a-114">`expression`と同じ型であるか、共通の基本データ型または派生型であるコレクション。</span><span class="sxs-lookup"><span data-stu-id="3987a-114">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3987a-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="3987a-115">Remarks</span></span>  

 <span data-ttu-id="3987a-116">UNION は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="3987a-116">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="3987a-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="3987a-117">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="3987a-118">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の優先順位に関する情報については、「[EXCEPT](except-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3987a-118">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3987a-119">例</span><span class="sxs-lookup"><span data-stu-id="3987a-119">Example</span></span>  

 <span data-ttu-id="3987a-120">次の Entity SQL クエリでは、UNION ALL 演算子を使用して、2 つのクエリの結果を 1 つのコレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="3987a-120">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="3987a-121">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="3987a-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3987a-122">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3987a-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3987a-123">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3987a-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3987a-124">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="3987a-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a><span data-ttu-id="3987a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3987a-125">See also</span></span>

- [<span data-ttu-id="3987a-126">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="3987a-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
