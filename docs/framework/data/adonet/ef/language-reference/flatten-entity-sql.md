---
description: '詳細情報: FLATTEN (Entity SQL)'
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 3701fbdf481024c799b4cdc6f109bae9fc226609
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786356"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="61bfb-103">FLATTEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="61bfb-103">FLATTEN (Entity SQL)</span></span>

<span data-ttu-id="61bfb-104">コレクションのコレクションをフラット化して単一のコレクションに変換します。</span><span class="sxs-lookup"><span data-stu-id="61bfb-104">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="61bfb-105">変換後のコレクションは、入れ子構造が失われるだけで、変換前のコレクションとまったく同じ要素を格納します。</span><span class="sxs-lookup"><span data-stu-id="61bfb-105">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61bfb-106">構文</span><span class="sxs-lookup"><span data-stu-id="61bfb-106">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="61bfb-107">引数</span><span class="sxs-lookup"><span data-stu-id="61bfb-107">Arguments</span></span>  

 `collection`  
 <span data-ttu-id="61bfb-108">値のコレクションのコレクションをフラット化して単一のコレクションとして返す有効な任意の式。</span><span class="sxs-lookup"><span data-stu-id="61bfb-108">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61bfb-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="61bfb-109">Remarks</span></span>  

 <span data-ttu-id="61bfb-110">`FLATTEN` は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="61bfb-110">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="61bfb-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="61bfb-111">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="61bfb-112">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の優先順位に関する情報については、「[EXCEPT](except-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="61bfb-112">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61bfb-113">例</span><span class="sxs-lookup"><span data-stu-id="61bfb-113">Example</span></span>  

 <span data-ttu-id="61bfb-114">次の Entity SQL クエリでは、 `FLATTEN` 演算子を使用して、コレクションのコレクションをフラット化されたコレクションに変換します。</span><span class="sxs-lookup"><span data-stu-id="61bfb-114">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="61bfb-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="61bfb-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="61bfb-116">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="61bfb-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="61bfb-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="61bfb-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="61bfb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="61bfb-118">See also</span></span>

- [<span data-ttu-id="61bfb-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="61bfb-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
