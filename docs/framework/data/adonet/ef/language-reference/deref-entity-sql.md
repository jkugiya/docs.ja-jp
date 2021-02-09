---
description: '詳細情報: DEREF (Entity SQL)'
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 9d0f29123c1459c6eab21ea9cd860b5c9e77f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724727"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="ddbdc-103">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ddbdc-103">DEREF (Entity SQL)</span></span>

<span data-ttu-id="ddbdc-104">参照値を逆参照し、その逆参照の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-104">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbdc-105">構文</span><span class="sxs-lookup"><span data-stu-id="ddbdc-105">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="ddbdc-106">引数</span><span class="sxs-lookup"><span data-stu-id="ddbdc-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ddbdc-107">コレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddbdc-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ddbdc-108">Return Value</span></span>  

 <span data-ttu-id="ddbdc-109">参照されるエンティティの値。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-109">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddbdc-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ddbdc-110">Remarks</span></span>  

 <span data-ttu-id="ddbdc-111">DEREF 演算子は参照値を逆参照し、その逆参照の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-111">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="ddbdc-112">たとえば、`r` が ref\<T> 型の参照である場合、`Deref(r)` は `r` によって参照されるエンティティを生成する `T` 型の式です。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-112">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="ddbdc-113">参照値が null または未解決 (つまり、参照先が存在しない) の場合、DEREF 演算子の結果は null になります。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-113">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddbdc-114">例</span><span class="sxs-lookup"><span data-stu-id="ddbdc-114">Example</span></span>  

 <span data-ttu-id="ddbdc-115">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、DEREF 演算子を使用して参照値を逆参照し、その逆参照の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-115">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="ddbdc-116">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ddbdc-117">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ddbdc-118">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-118">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="ddbdc-119">次のクエリを引数として ExecutePrimitiveTypeQuery メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ddbdc-119">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="ddbdc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddbdc-120">See also</span></span>

- [<span data-ttu-id="ddbdc-121">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="ddbdc-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ddbdc-122">REF</span><span class="sxs-lookup"><span data-stu-id="ddbdc-122">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="ddbdc-123">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="ddbdc-123">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="ddbdc-124">KEY</span><span class="sxs-lookup"><span data-stu-id="ddbdc-124">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="ddbdc-125">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="ddbdc-125">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
