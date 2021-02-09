---
description: '詳細情報: (剰余) (Entity SQL)'
title: (剰余) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 8ac9bf2fa9dbee843215dcfeed13fefc7bd54796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696634"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="28baf-103">(剰余) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="28baf-103">(Modulo) (Entity SQL)</span></span>

<span data-ttu-id="28baf-104">ある式を別の式で除算した結果の余りを返します。</span><span class="sxs-lookup"><span data-stu-id="28baf-104">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28baf-105">構文</span><span class="sxs-lookup"><span data-stu-id="28baf-105">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="28baf-106">引数</span><span class="sxs-lookup"><span data-stu-id="28baf-106">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="28baf-107">除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="28baf-107">The numeric expression to divide.</span></span> <span data-ttu-id="28baf-108">`dividend` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="28baf-108">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="28baf-109">被除数を除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="28baf-109">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="28baf-110">`divisor` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="28baf-110">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="28baf-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="28baf-111">Result Types</span></span>  

 <span data-ttu-id="28baf-112">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="28baf-112">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="28baf-113">例</span><span class="sxs-lookup"><span data-stu-id="28baf-113">Example</span></span>  

 <span data-ttu-id="28baf-114">次の Entity SQL クエリでは、% 算術演算子を使用して、特定の式を別の式で除算した結果の余りを返します。</span><span class="sxs-lookup"><span data-stu-id="28baf-114">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="28baf-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="28baf-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="28baf-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="28baf-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="28baf-117">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="28baf-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="28baf-118">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="28baf-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="28baf-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="28baf-119">See also</span></span>

- [<span data-ttu-id="28baf-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="28baf-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
