---
description: '詳細情報: * (乗算) (Entity SQL)'
title: '* (乗算) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 92606e5f9e4646ab651d0e07095e6f419401188f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696621"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="ac11c-103">\* (乗算) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ac11c-103">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="ac11c-104">2 つの式を乗算します。</span><span class="sxs-lookup"><span data-stu-id="ac11c-104">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac11c-105">構文</span><span class="sxs-lookup"><span data-stu-id="ac11c-105">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac11c-106">引数</span><span class="sxs-lookup"><span data-stu-id="ac11c-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ac11c-107">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="ac11c-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ac11c-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ac11c-108">Result Types</span></span>  

 <span data-ttu-id="ac11c-109">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="ac11c-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="ac11c-110">暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac11c-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac11c-111">例</span><span class="sxs-lookup"><span data-stu-id="ac11c-111">Example</span></span>  

 <span data-ttu-id="ac11c-112">次の Entity SQL クエリでは、\* 算術演算子を使用して 2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="ac11c-112">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="ac11c-113">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ac11c-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ac11c-114">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ac11c-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ac11c-115">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ac11c-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ac11c-116">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ac11c-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="ac11c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac11c-117">See also</span></span>

- [<span data-ttu-id="ac11c-118">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="ac11c-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
