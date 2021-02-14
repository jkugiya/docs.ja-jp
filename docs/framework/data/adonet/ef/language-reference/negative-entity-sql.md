---
description: '詳細情報: - (負符号) (Entity SQL)'
title: '- (負符号) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: f3d30ce36b95e44755d148dc06279f67f15b0664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712884"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="e801f-103">- (負符号) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e801f-103">- (Negative) (Entity SQL)</span></span>

<span data-ttu-id="e801f-104">数値式の負の値を返します。</span><span class="sxs-lookup"><span data-stu-id="e801f-104">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e801f-105">構文</span><span class="sxs-lookup"><span data-stu-id="e801f-105">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e801f-106">引数</span><span class="sxs-lookup"><span data-stu-id="e801f-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e801f-107">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="e801f-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e801f-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="e801f-108">Result Types</span></span>  

 <span data-ttu-id="e801f-109">`expression`のデータ型。</span><span class="sxs-lookup"><span data-stu-id="e801f-109">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e801f-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="e801f-110">Remarks</span></span>  

 <span data-ttu-id="e801f-111">符号なしの型を `expression` に指定した場合、戻り値の型は、 `expression`の型と最も関連性の高い符号付きの型になります。</span><span class="sxs-lookup"><span data-stu-id="e801f-111">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="e801f-112">たとえば、 `expression` に Byte 型を指定した場合、Int16 型の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="e801f-112">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e801f-113">例</span><span class="sxs-lookup"><span data-stu-id="e801f-113">Example</span></span>  

 <span data-ttu-id="e801f-114">次の Entity SQL クエリでは、- 算術演算子を使用して、数値式の負の値を返します。</span><span class="sxs-lookup"><span data-stu-id="e801f-114">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="e801f-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e801f-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e801f-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e801f-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e801f-117">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e801f-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e801f-118">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e801f-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="e801f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e801f-119">See also</span></span>

- [<span data-ttu-id="e801f-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="e801f-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
