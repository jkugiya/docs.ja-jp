---
description: '詳細情報: != (等しくない) (Entity SQL)'
title: '!= (等しくない) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: a7a96606fb1834b757253948c3a0d2cde11893dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696400"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="85fe1-103">!= (等しくない) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="85fe1-103">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="85fe1-104">2 つの式を比較して、左の式の値が右の式の値と等しくないかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="85fe1-104">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="85fe1-105">!= (等しくない) 演算子は、機能的には <> 演算子と同じです。</span><span class="sxs-lookup"><span data-stu-id="85fe1-105">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fe1-106">構文</span><span class="sxs-lookup"><span data-stu-id="85fe1-106">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="85fe1-107">引数</span><span class="sxs-lookup"><span data-stu-id="85fe1-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="85fe1-108">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="85fe1-108">Any valid expression.</span></span> <span data-ttu-id="85fe1-109">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="85fe1-109">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="85fe1-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="85fe1-110">Result Types</span></span>  

 <span data-ttu-id="85fe1-111">左の式が右の式と等しくない場合は`true` 、等しい場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="85fe1-111">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85fe1-112">例</span><span class="sxs-lookup"><span data-stu-id="85fe1-112">Example</span></span>  

 <span data-ttu-id="85fe1-113">次の Entity SQL クエリは != 演算子を使用して 2 つの式を比較し、左の式が右の式と等しくないかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="85fe1-113">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="85fe1-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="85fe1-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="85fe1-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="85fe1-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="85fe1-116">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="85fe1-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="85fe1-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="85fe1-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="85fe1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="85fe1-118">See also</span></span>

- [<span data-ttu-id="85fe1-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="85fe1-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
