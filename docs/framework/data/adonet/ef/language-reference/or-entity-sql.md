---
description: '詳細情報: || (OR) (Entity SQL)'
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 83af0211de1dd86b057237c36312e3ce33a3512a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696335"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="c2996-103">|| (OR) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c2996-103">|| (OR) (Entity SQL)</span></span>

<span data-ttu-id="c2996-104">2 つの `Boolean` 式を結合します。</span><span class="sxs-lookup"><span data-stu-id="c2996-104">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2996-105">構文</span><span class="sxs-lookup"><span data-stu-id="c2996-105">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c2996-106">引数</span><span class="sxs-lookup"><span data-stu-id="c2996-106">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="c2996-107">`Boolean`値を返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="c2996-107">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2996-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="c2996-108">Return Value</span></span>  

 <span data-ttu-id="c2996-109">いずれかの条件が`true` の場合は `true`、それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="c2996-109">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2996-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c2996-110">Remarks</span></span>  

 <span data-ttu-id="c2996-111">OR は [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の論理演算子です。</span><span class="sxs-lookup"><span data-stu-id="c2996-111">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="c2996-112">2 つの条件を結合する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c2996-112">It is used to combine two conditions.</span></span> <span data-ttu-id="c2996-113">1 つのステートメント内に複数の論理演算子が使われている場合、OR 演算子は AND 演算子の次に評価されます。</span><span class="sxs-lookup"><span data-stu-id="c2996-113">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="c2996-114">ただし、かっこを使うと、演算の順序を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="c2996-114">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="c2996-115">二重の縦棒 (&#124;&#124;) は、OR 演算子と同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="c2996-115">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="c2996-116">使用可能な入力値と戻り値の型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c2996-116">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="c2996-117">true</span><span class="sxs-lookup"><span data-stu-id="c2996-117">TRUE</span></span>|<span data-ttu-id="c2996-118">true</span><span class="sxs-lookup"><span data-stu-id="c2996-118">TRUE</span></span>|<span data-ttu-id="c2996-119">true</span><span class="sxs-lookup"><span data-stu-id="c2996-119">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="c2996-120">true</span><span class="sxs-lookup"><span data-stu-id="c2996-120">TRUE</span></span>|<span data-ttu-id="c2996-121">false</span><span class="sxs-lookup"><span data-stu-id="c2996-121">FALSE</span></span>|<span data-ttu-id="c2996-122">NULL</span><span class="sxs-lookup"><span data-stu-id="c2996-122">NULL</span></span>|  
|`NULL`|<span data-ttu-id="c2996-123">true</span><span class="sxs-lookup"><span data-stu-id="c2996-123">TRUE</span></span>|<span data-ttu-id="c2996-124">NULL</span><span class="sxs-lookup"><span data-stu-id="c2996-124">NULL</span></span>|<span data-ttu-id="c2996-125">NULL</span><span class="sxs-lookup"><span data-stu-id="c2996-125">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2996-126">例</span><span class="sxs-lookup"><span data-stu-id="c2996-126">Example</span></span>  

 <span data-ttu-id="c2996-127">次の Entity SQL クエリでは、OR 演算子を使用して 2 つの `Boolean` 式を結合します。</span><span class="sxs-lookup"><span data-stu-id="c2996-127">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="c2996-128">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c2996-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c2996-129">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c2996-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c2996-130">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c2996-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c2996-131">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c2996-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="c2996-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2996-132">See also</span></span>

- [<span data-ttu-id="c2996-133">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="c2996-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
