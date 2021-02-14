---
description: '詳細情報: / (除算) (Entity SQL)'
title: '- (除算) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 4ac487c636c460401eeb147dc7ce1a8d8ba7f7ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724636"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="d7f0a-103">/ (除算) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7f0a-103">/ (Divide) (Entity SQL)</span></span>

<span data-ttu-id="d7f0a-104">1 つの値を別の値で除算します。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-104">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7f0a-105">構文</span><span class="sxs-lookup"><span data-stu-id="d7f0a-105">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7f0a-106">引数</span><span class="sxs-lookup"><span data-stu-id="d7f0a-106">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="d7f0a-107">除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-107">The numeric expression to divide.</span></span> <span data-ttu-id="d7f0a-108">`dividend` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-108">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="d7f0a-109">被除数を除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-109">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="d7f0a-110">`divisor` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-110">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d7f0a-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="d7f0a-111">Result Types</span></span>  

 <span data-ttu-id="d7f0a-112">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-112">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d7f0a-113">暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-113">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7f0a-114">例</span><span class="sxs-lookup"><span data-stu-id="d7f0a-114">Example</span></span>  

 <span data-ttu-id="d7f0a-115">次の Entity SQL クエリでは、/ 算術演算子を使用して 2 つの数値の間で除算をします。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-115">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="d7f0a-116">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7f0a-117">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d7f0a-118">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d7f0a-119">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="d7f0a-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="d7f0a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7f0a-120">See also</span></span>

- [<span data-ttu-id="d7f0a-121">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="d7f0a-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
