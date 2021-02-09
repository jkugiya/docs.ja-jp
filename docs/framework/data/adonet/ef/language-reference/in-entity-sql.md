---
description: '詳細情報: IN (Entity SQL)'
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 234ed15430e44d12d4ca7c98fcb4a7bc03d117f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748597"
---
# <a name="in-entity-sql"></a><span data-ttu-id="5feca-103">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5feca-103">IN (Entity SQL)</span></span>

<span data-ttu-id="5feca-104">コレクション内に一致する値があるかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="5feca-104">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5feca-105">構文</span><span class="sxs-lookup"><span data-stu-id="5feca-105">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5feca-106">引数</span><span class="sxs-lookup"><span data-stu-id="5feca-106">Arguments</span></span>  

 `value`  
 <span data-ttu-id="5feca-107">照合する値を返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="5feca-107">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="5feca-108">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="5feca-108">[ NOT ]</span></span>  
 <span data-ttu-id="5feca-109">IN の `Boolean` 型の結果を否定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5feca-109">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="5feca-110">一致の判定対象のコレクションを返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="5feca-110">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="5feca-111">すべての式は、 `value`と同じ型であるか、共通の基本型または派生型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5feca-111">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5feca-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5feca-112">Return Value</span></span>  

 <span data-ttu-id="5feca-113">コレクションに値が見つかった場合は `true`、値が null またはコレクションが null の場合は null、それ以外の場合は `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="5feca-113">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="5feca-114">NOT IN を使用すると、IN の結果が否定されます。</span><span class="sxs-lookup"><span data-stu-id="5feca-114">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5feca-115">例</span><span class="sxs-lookup"><span data-stu-id="5feca-115">Example</span></span>  

 <span data-ttu-id="5feca-116">次の Entity SQL クエリでは、IN 演算子を使用して、コレクション内に一致する値があるかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="5feca-116">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="5feca-117">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5feca-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5feca-118">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5feca-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5feca-119">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5feca-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5feca-120">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="5feca-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="5feca-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="5feca-121">See also</span></span>

- [<span data-ttu-id="5feca-122">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="5feca-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
