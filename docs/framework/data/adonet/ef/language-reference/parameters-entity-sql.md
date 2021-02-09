---
description: '詳細情報: パラメーター (Entity SQL)'
title: パラメーター (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 77b1e6ee95b5d367fec8d99345bbb416c2b9787d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724532"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="474c9-103">パラメーター (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="474c9-103">Parameters (Entity SQL)</span></span>

<span data-ttu-id="474c9-104">パラメーターは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の外部で定義される変数です。通常は、ホスト言語で使用されるバインド API を通じて定義されます。</span><span class="sxs-lookup"><span data-stu-id="474c9-104">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="474c9-105">それぞれのパラメーターには、名前と型があります。</span><span class="sxs-lookup"><span data-stu-id="474c9-105">Each parameter has a name and a type.</span></span> <span data-ttu-id="474c9-106">パラメーター名は、クエリ式の中で、先頭に @ 記号を付けることによって定義します。</span><span class="sxs-lookup"><span data-stu-id="474c9-106">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="474c9-107">これにより、クエリ内で定義されている他の名前 (プロパティ名など) と明確に区別されます。</span><span class="sxs-lookup"><span data-stu-id="474c9-107">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="474c9-108">パラメーターをバインドするための API は、ホスト言語によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="474c9-108">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="474c9-109">例</span><span class="sxs-lookup"><span data-stu-id="474c9-109">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="474c9-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="474c9-110">See also</span></span>

- [<span data-ttu-id="474c9-111">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="474c9-111">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="474c9-112">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="474c9-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
