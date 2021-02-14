---
description: '詳細情報: + (文字列連結) (Entity SQL)'
title: + (文字列連結) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 7b6aac5b865e2127bb23446248e20d83ea3c7ea3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791843"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="2bde5-103">+ (文字列連結) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2bde5-103">+ (String Concatenation) (Entity SQL)</span></span>

<span data-ttu-id="2bde5-104">2 つの文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="2bde5-104">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bde5-105">構文</span><span class="sxs-lookup"><span data-stu-id="2bde5-105">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2bde5-106">引数</span><span class="sxs-lookup"><span data-stu-id="2bde5-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="2bde5-107">EDM.String データ型の任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="2bde5-107">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="2bde5-108">両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bde5-108">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2bde5-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="2bde5-109">Result Types</span></span>  

 <span data-ttu-id="2bde5-110">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="2bde5-110">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="2bde5-111">暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2bde5-111">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bde5-112">例</span><span class="sxs-lookup"><span data-stu-id="2bde5-112">Example</span></span>  

 <span data-ttu-id="2bde5-113">次の Entity SQL クエリでは、+ 演算子を使用して、2 つの文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="2bde5-113">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="2bde5-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="2bde5-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2bde5-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2bde5-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2bde5-116">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2bde5-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2bde5-117">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="2bde5-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="2bde5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bde5-118">See also</span></span>

- [<span data-ttu-id="2bde5-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="2bde5-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2bde5-120">概念モデルの型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="2bde5-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
