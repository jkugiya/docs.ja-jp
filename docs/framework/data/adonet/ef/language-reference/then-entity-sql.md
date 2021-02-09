---
description: '詳細情報: THEN (Entity SQL)'
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: e1f0657cfef3786832f489434fd8fc0342e8687b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673467"
---
# <a name="then-entity-sql"></a><span data-ttu-id="04262-103">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="04262-103">THEN (Entity SQL)</span></span>

<span data-ttu-id="04262-104">WHEN 句が `true`として評価された場合の結果です。</span><span class="sxs-lookup"><span data-stu-id="04262-104">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04262-105">構文</span><span class="sxs-lookup"><span data-stu-id="04262-105">Syntax</span></span>  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="04262-106">引数</span><span class="sxs-lookup"><span data-stu-id="04262-106">Arguments</span></span>  

 `when_expression`  
 <span data-ttu-id="04262-107">任意の有効なブール式。</span><span class="sxs-lookup"><span data-stu-id="04262-107">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="04262-108">コレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="04262-108">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04262-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="04262-109">Remarks</span></span>  

 <span data-ttu-id="04262-110">`when_expression` が `true`として評価された場合、対応する `then-expression`が評価されます。</span><span class="sxs-lookup"><span data-stu-id="04262-110">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="04262-111">WHEN の条件が満たされなかった場合は、 `else-expression` が評価されます。</span><span class="sxs-lookup"><span data-stu-id="04262-111">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="04262-112">ただし、 `else-expression`が存在しない場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="04262-112">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="04262-113">例については、「[CASE](case-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04262-113">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04262-114">例</span><span class="sxs-lookup"><span data-stu-id="04262-114">Example</span></span>  

 <span data-ttu-id="04262-115">次の Entity SQL クエリでは、CASE 式を使用して、一連の `Boolean` 式を評価します。</span><span class="sxs-lookup"><span data-stu-id="04262-115">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="04262-116">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="04262-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="04262-117">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="04262-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="04262-118">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="04262-118">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="04262-119">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="04262-119">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="04262-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="04262-120">See also</span></span>

- [<span data-ttu-id="04262-121">CASE</span><span class="sxs-lookup"><span data-stu-id="04262-121">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="04262-122">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="04262-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
