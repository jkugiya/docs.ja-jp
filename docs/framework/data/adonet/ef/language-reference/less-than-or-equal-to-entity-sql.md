---
description: '詳細情報: <= (以下) (Entity SQL)'
title: <= (以下) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: f720c4ef87cdd0cceea175b1ea70caf5ac6e1deb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748259"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="90620-103">\<= (以下) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="90620-103">\<= (Less Than or Equal To) (Entity SQL)</span></span>

<span data-ttu-id="90620-104">2 つの式を比較して、左の式の値が右の式の値以下であるかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="90620-104">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90620-105">構文</span><span class="sxs-lookup"><span data-stu-id="90620-105">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="90620-106">引数</span><span class="sxs-lookup"><span data-stu-id="90620-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="90620-107">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="90620-107">Any valid expression.</span></span> <span data-ttu-id="90620-108">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="90620-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="90620-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="90620-109">Result Types</span></span>  

 <span data-ttu-id="90620-110">左の式の値が右の式の値以下である場合は`true` 、そうでない場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="90620-110">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90620-111">例</span><span class="sxs-lookup"><span data-stu-id="90620-111">Example</span></span>  

 <span data-ttu-id="90620-112">次の Entity SQL クエリは「<=」比較演算子を使用して 2 つの式を比較し、左の式の値が右の式の値以下であるかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="90620-112">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="90620-113">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="90620-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="90620-114">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="90620-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="90620-115">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="90620-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="90620-116">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="90620-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="90620-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="90620-117">See also</span></span>

- [<span data-ttu-id="90620-118">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="90620-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
