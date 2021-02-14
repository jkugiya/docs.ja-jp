---
description: '詳細情報: = (等しい) (Entity SQL)'
title: = (等しい) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 500c3fdde2377b3b5160436f23d051c2bcd0ee62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786408"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="69e07-103">= (等しい) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="69e07-103">= (Equals) (Entity SQL)</span></span>

<span data-ttu-id="69e07-104">2 つの式の等価性を比較します。</span><span class="sxs-lookup"><span data-stu-id="69e07-104">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e07-105">構文</span><span class="sxs-lookup"><span data-stu-id="69e07-105">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="69e07-106">引数</span><span class="sxs-lookup"><span data-stu-id="69e07-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="69e07-107">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="69e07-107">Any valid expression.</span></span> <span data-ttu-id="69e07-108">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="69e07-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="69e07-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="69e07-109">Result Types</span></span>  

 <span data-ttu-id="69e07-110">左の式が右の式と等しい場合は`true` 、等しくない場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="69e07-110">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69e07-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="69e07-111">Remarks</span></span>  

 <span data-ttu-id="69e07-112">== 演算子は = 演算子と同じです。</span><span class="sxs-lookup"><span data-stu-id="69e07-112">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e07-113">例</span><span class="sxs-lookup"><span data-stu-id="69e07-113">Example</span></span>  

 <span data-ttu-id="69e07-114">次の Entity SQL クエリでは、= 比較演算子を使用して 2 つの式の等価性を比較します。</span><span class="sxs-lookup"><span data-stu-id="69e07-114">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="69e07-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="69e07-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="69e07-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="69e07-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="69e07-117">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="69e07-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="69e07-118">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="69e07-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="69e07-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="69e07-119">See also</span></span>

- [<span data-ttu-id="69e07-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="69e07-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
