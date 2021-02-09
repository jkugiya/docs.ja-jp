---
description: '詳細情報: EXISTS (Entity SQL)'
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: c6c5b86616d63b9cc3389365a96c382101463732
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786382"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="0921c-103">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0921c-103">EXISTS (Entity SQL)</span></span>

<span data-ttu-id="0921c-104">コレクションが空かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="0921c-104">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0921c-105">構文</span><span class="sxs-lookup"><span data-stu-id="0921c-105">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0921c-106">引数</span><span class="sxs-lookup"><span data-stu-id="0921c-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="0921c-107">コレクションを返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="0921c-107">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="0921c-108">NOT</span><span class="sxs-lookup"><span data-stu-id="0921c-108">NOT</span></span>  
 <span data-ttu-id="0921c-109">EXISTS の結果を否定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="0921c-109">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0921c-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="0921c-110">Return Value</span></span>  

 <span data-ttu-id="0921c-111">コレクションが空でない場合は `true`、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="0921c-111">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0921c-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="0921c-112">Remarks</span></span>  

 <span data-ttu-id="0921c-113">EXISTS は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="0921c-113">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="0921c-114">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="0921c-114">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="0921c-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の優先順位に関する情報については、「[EXCEPT](except-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0921c-115">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0921c-116">例</span><span class="sxs-lookup"><span data-stu-id="0921c-116">Example</span></span>  

 <span data-ttu-id="0921c-117">次の Entity SQL クエリでは、EXISTS 演算子を使用して、コレクションが空かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="0921c-117">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="0921c-118">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="0921c-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0921c-119">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0921c-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0921c-120">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0921c-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0921c-121">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="0921c-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="0921c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0921c-122">See also</span></span>

- [<span data-ttu-id="0921c-123">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="0921c-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
