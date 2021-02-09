---
description: '詳細情報: 変数 (Entity SQL)'
title: 変数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 134fee8f61c8e87a18520e6622f6a6a5cceb0076
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795041"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="d35d4-103">変数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d35d4-103">Variables (Entity SQL)</span></span>

## <a name="variable"></a><span data-ttu-id="d35d4-104">変数</span><span class="sxs-lookup"><span data-stu-id="d35d4-104">Variable</span></span>  

 <span data-ttu-id="d35d4-105">変数式は、現在のスコープで定義されている名前付きの式への参照です。</span><span class="sxs-lookup"><span data-stu-id="d35d4-105">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="d35d4-106">変数参照は、[識別子](identifiers-entity-sql.md)で定義された有効な [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d35d4-106">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="d35d4-107">次の例は、式における変数の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d35d4-107">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="d35d4-108">FROM 句の `c` は変数の定義です。</span><span class="sxs-lookup"><span data-stu-id="d35d4-108">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="d35d4-109">SELECT 句内で使用された `c` は、変数参照を表します。</span><span class="sxs-lookup"><span data-stu-id="d35d4-109">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="d35d4-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d35d4-110">See also</span></span>

- [<span data-ttu-id="d35d4-111">識別子</span><span class="sxs-lookup"><span data-stu-id="d35d4-111">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="d35d4-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d35d4-112">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="d35d4-113">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="d35d4-113">Entity SQL Overview</span></span>](entity-sql-overview.md)
