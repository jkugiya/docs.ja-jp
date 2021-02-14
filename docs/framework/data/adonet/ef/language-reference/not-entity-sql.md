---
description: '詳細情報: ! (NOT) (Entity SQL)'
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 648cc4ff73769ae280570b2d42934b2001fa5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696452"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="a27ab-105">!</span><span class="sxs-lookup"><span data-stu-id="a27ab-105">!</span></span> <span data-ttu-id="a27ab-106">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a27ab-106">(NOT) (Entity SQL)</span></span>

<span data-ttu-id="a27ab-107">`Boolean` 型の式を否定します。</span><span class="sxs-lookup"><span data-stu-id="a27ab-107">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27ab-108">構文</span><span class="sxs-lookup"><span data-stu-id="a27ab-108">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="a27ab-109">引数</span><span class="sxs-lookup"><span data-stu-id="a27ab-109">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="a27ab-110">ブール値を返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="a27ab-110">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a27ab-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a27ab-111">Remarks</span></span>  

 <span data-ttu-id="a27ab-112">感嘆符 (!) には、NOT 演算子と同じ機能があります。</span><span class="sxs-lookup"><span data-stu-id="a27ab-112">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a27ab-113">例</span><span class="sxs-lookup"><span data-stu-id="a27ab-113">Example</span></span>  

 <span data-ttu-id="a27ab-114">次の Entity SQL クエリでは、NOT 演算子を使用して `Boolean` 型の式を否定します。</span><span class="sxs-lookup"><span data-stu-id="a27ab-114">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="a27ab-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a27ab-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a27ab-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a27ab-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a27ab-117">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a27ab-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a27ab-118">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="a27ab-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="a27ab-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a27ab-119">See also</span></span>

- [<span data-ttu-id="a27ab-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="a27ab-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
