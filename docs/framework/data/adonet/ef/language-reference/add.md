---
description: '詳細情報: + (加算)'
title: + (追加)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b8ec9f50b349fe971513f399b7e9984e9044cf58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697310"
---
# <a name="-add"></a><span data-ttu-id="e3bf5-103">+ (加算)</span><span class="sxs-lookup"><span data-stu-id="e3bf5-103">+ (Add)</span></span>

<span data-ttu-id="e3bf5-104">2 つの値を加算します。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-104">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3bf5-105">構文</span><span class="sxs-lookup"><span data-stu-id="e3bf5-105">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e3bf5-106">引数</span><span class="sxs-lookup"><span data-stu-id="e3bf5-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e3bf5-107">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e3bf5-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="e3bf5-108">Result Types</span></span>  

 <span data-ttu-id="e3bf5-109">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="e3bf5-110">暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3bf5-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3bf5-111">Remarks</span></span>  

 <span data-ttu-id="e3bf5-112">EDM.String 型の場合は、値が連結されます。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-112">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3bf5-113">例</span><span class="sxs-lookup"><span data-stu-id="e3bf5-113">Example</span></span>  

 <span data-ttu-id="e3bf5-114">次の Entity SQL クエリでは、+ 算術演算子を使用して 2 つの数値を加算します。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-114">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="e3bf5-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e3bf5-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e3bf5-117">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e3bf5-118">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e3bf5-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="e3bf5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3bf5-119">See also</span></span>

- [<span data-ttu-id="e3bf5-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="e3bf5-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e3bf5-121">概念モデルの型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="e3bf5-121">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
