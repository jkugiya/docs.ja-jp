---
description: '詳細情報: SET (Entity SQL)'
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 80be5b76e654c39776d97413c4ece5a8f3df8d2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768026"
---
# <a name="set-entity-sql"></a><span data-ttu-id="dce08-103">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dce08-103">SET (Entity SQL)</span></span>

<span data-ttu-id="dce08-104">SET 式は、重複する要素をすべて除外した新しいコレクションを生成することによって、オブジェクトのコレクションを 1 つの集合に変換します。</span><span class="sxs-lookup"><span data-stu-id="dce08-104">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce08-105">構文</span><span class="sxs-lookup"><span data-stu-id="dce08-105">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="dce08-106">引数</span><span class="sxs-lookup"><span data-stu-id="dce08-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="dce08-107">コレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="dce08-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dce08-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="dce08-108">Remarks</span></span>  

 <span data-ttu-id="dce08-109">集合式 `SET(c)` は、論理上、次の select ステートメントと等価です。</span><span class="sxs-lookup"><span data-stu-id="dce08-109">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="dce08-110">`SET` は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="dce08-110">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="dce08-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="dce08-111">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="dce08-112">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の優先順位に関する情報については、「[EXCEPT](except-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dce08-112">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dce08-113">例</span><span class="sxs-lookup"><span data-stu-id="dce08-113">Example</span></span>  

 <span data-ttu-id="dce08-114">次の Entity SQL クエリでは、SET 式を使用して、オブジェクトのコレクションを 1 つの集合に変換します。</span><span class="sxs-lookup"><span data-stu-id="dce08-114">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="dce08-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="dce08-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dce08-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="dce08-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dce08-117">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="dce08-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="dce08-118">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="dce08-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="dce08-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="dce08-119">See also</span></span>

- [<span data-ttu-id="dce08-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="dce08-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
