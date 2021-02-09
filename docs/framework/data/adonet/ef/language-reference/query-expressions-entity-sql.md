---
description: '詳細情報: クエリ式 (Entity SQL)'
title: クエリ式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 218e7db0e812bd43a92d3145bc4bf96244ef6a3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696036"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="9c7a1-103">クエリ式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9c7a1-103">Query Expressions (Entity SQL)</span></span>

<span data-ttu-id="9c7a1-104">クエリ式とは、さまざまなクエリ演算子を組み合わせて 1 つの構文にしたものです。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-104">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="9c7a1-105">には、[リテラル](literals-entity-sql.md)、[パラメーター](parameters-entity-sql.md)、[変数](variables-entity-sql.md)、演算子、[関数](functions-entity-sql.md)、集合演算子などのさまざまな種類の式が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-105">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="9c7a1-106">詳細については、「[Entity SQL リファレンス](entity-sql-reference.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-106">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="9c7a1-107">句</span><span class="sxs-lookup"><span data-stu-id="9c7a1-107">Clauses</span></span>  

 <span data-ttu-id="9c7a1-108">クエリ式は、オブジェクトのコレクションに連続した操作を適用する一連の句で構成されます。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-108">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="9c7a1-109">これらは、標準の SQL select ステートメントと同じ句に基づいています:[SELECT](select-entity-sql.md)、[FROM](from-entity-sql.md)、[WHERE](where-entity-sql.md)、[GROUP BY](group-by-entity-sql.md)、[HAVING](having-entity-sql.md)、および [ORDER BY](order-by-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-109">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="9c7a1-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="9c7a1-110">Scope</span></span>  

 <span data-ttu-id="9c7a1-111">FROM 句で定義された名前は、出現順 (左から右の順) に FROM スコープに導入されます。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-111">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="9c7a1-112">JOIN リストでは、式は既にリストで定義されている名前を参照できます。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-112">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="9c7a1-113">FROM 句で指定された要素のパブリック プロパティは FROM スコープに追加されません。それらは常に、別名で修飾された名前を使用して参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-113">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="9c7a1-114">通常は、SELECT 式のすべての部分が FROM スコープに含まれると見なされます。</span><span class="sxs-lookup"><span data-stu-id="9c7a1-114">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c7a1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c7a1-115">See also</span></span>

- [<span data-ttu-id="9c7a1-116">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="9c7a1-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
