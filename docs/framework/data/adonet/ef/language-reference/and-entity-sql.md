---
description: '詳細情報: &amp;&amp; (AND) (Entity SQL)'
title: '&amp;&amp; (AND) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 14fc6bc3f58ac78cb9806a7f421db87bbad048ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697180"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="a5c4b-103">&amp;&amp; (AND) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a5c4b-103">&amp;&amp; (AND) (Entity SQL)</span></span>

<span data-ttu-id="a5c4b-104">両方の式が `true` の場合は `true`を返します。それ以外の場合は `false` または `NULL`を返します。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-104">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c4b-105">構文</span><span class="sxs-lookup"><span data-stu-id="a5c4b-105">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="a5c4b-106">or</span><span class="sxs-lookup"><span data-stu-id="a5c4b-106">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5c4b-107">引数</span><span class="sxs-lookup"><span data-stu-id="a5c4b-107">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="a5c4b-108">ブール値を返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c4b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a5c4b-109">Remarks</span></span>  

 <span data-ttu-id="a5c4b-110">二重のアンパサンド (&&) は、AND 演算子と同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-110">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="a5c4b-111">使用可能な入力値と戻り値の型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-111">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="a5c4b-112">true</span><span class="sxs-lookup"><span data-stu-id="a5c4b-112">TRUE</span></span>|<span data-ttu-id="a5c4b-113">false</span><span class="sxs-lookup"><span data-stu-id="a5c4b-113">FALSE</span></span>|<span data-ttu-id="a5c4b-114">NULL</span><span class="sxs-lookup"><span data-stu-id="a5c4b-114">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="a5c4b-115">false</span><span class="sxs-lookup"><span data-stu-id="a5c4b-115">FALSE</span></span>|<span data-ttu-id="a5c4b-116">false</span><span class="sxs-lookup"><span data-stu-id="a5c4b-116">FALSE</span></span>|<span data-ttu-id="a5c4b-117">false</span><span class="sxs-lookup"><span data-stu-id="a5c4b-117">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="a5c4b-118">NULL</span><span class="sxs-lookup"><span data-stu-id="a5c4b-118">NULL</span></span>|<span data-ttu-id="a5c4b-119">false</span><span class="sxs-lookup"><span data-stu-id="a5c4b-119">FALSE</span></span>|<span data-ttu-id="a5c4b-120">NULL</span><span class="sxs-lookup"><span data-stu-id="a5c4b-120">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a5c4b-121">例</span><span class="sxs-lookup"><span data-stu-id="a5c4b-121">Example</span></span>  

 <span data-ttu-id="a5c4b-122">次の Entity SQL クエリは、AND 演算子の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-122">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="a5c4b-123">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a5c4b-124">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a5c4b-125">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a5c4b-126">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="a5c4b-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="a5c4b-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5c4b-127">See also</span></span>

- [<span data-ttu-id="a5c4b-128">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="a5c4b-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
