---
description: '詳細情報: > (より大きい) (Entity SQL)'
title: '> (より大きい) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: e14470d477336fd719bb419657af3fdadcd54d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786291"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="4c97e-103">> (より大きい) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4c97e-103">> (Greater Than) (Entity SQL)</span></span>

<span data-ttu-id="4c97e-104">2 つの式を比較して、左の式の値が右の式の値よりも大きいかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="4c97e-104">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c97e-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c97e-105">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4c97e-106">引数</span><span class="sxs-lookup"><span data-stu-id="4c97e-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="4c97e-107">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="4c97e-107">Any valid expression.</span></span> <span data-ttu-id="4c97e-108">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="4c97e-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4c97e-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="4c97e-109">Result Types</span></span>  

 <span data-ttu-id="4c97e-110">左の式の値が右の式の値よりも大きい場合は`true` 、そうでない場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="4c97e-110">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c97e-111">例</span><span class="sxs-lookup"><span data-stu-id="4c97e-111">Example</span></span>  

 <span data-ttu-id="4c97e-112">次の Entity SQL クエリは「>」比較演算子を使用して 2 つの式を比較し、左の式の値が右の式の値よりも大きいかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="4c97e-112">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="4c97e-113">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4c97e-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4c97e-114">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4c97e-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4c97e-115">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4c97e-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4c97e-116">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="4c97e-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="4c97e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c97e-117">See also</span></span>

- [<span data-ttu-id="4c97e-118">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="4c97e-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
