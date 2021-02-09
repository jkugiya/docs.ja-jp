---
description: '詳細情報: USING (Entity SQL)'
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 084ab56f25041377dd6a0a35dd743122f482eeba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795054"
---
# <a name="using-entity-sql"></a><span data-ttu-id="bb051-103">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bb051-103">USING (Entity SQL)</span></span>

<span data-ttu-id="bb051-104">クエリ式で使用する名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb051-104">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb051-105">構文</span><span class="sxs-lookup"><span data-stu-id="bb051-105">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb051-106">引数</span><span class="sxs-lookup"><span data-stu-id="bb051-106">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="bb051-107">名前空間を修飾する短い別名。</span><span class="sxs-lookup"><span data-stu-id="bb051-107">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="bb051-108">任意の有効な名前空間。</span><span class="sxs-lookup"><span data-stu-id="bb051-108">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb051-109">例</span><span class="sxs-lookup"><span data-stu-id="bb051-109">Example</span></span>  

 <span data-ttu-id="bb051-110">次の Entity SQL クエリでは、USING 演算子を使用して、クエリ式に使用する名前空間が指定されています。</span><span class="sxs-lookup"><span data-stu-id="bb051-110">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="bb051-111">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="bb051-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bb051-112">「[方法: PrimitiveType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="bb051-112">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="bb051-113">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="bb051-113">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb051-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb051-114">See also</span></span>

- [<span data-ttu-id="bb051-115">名前空間</span><span class="sxs-lookup"><span data-stu-id="bb051-115">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="bb051-116">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="bb051-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
