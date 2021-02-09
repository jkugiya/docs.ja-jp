---
description: '詳細情報: サポートされていない式'
title: サポートされていない式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: ceb57dc78f9685a79de987d15f7fd57a583b75a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673298"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="f8c94-103">サポートされていない式</span><span class="sxs-lookup"><span data-stu-id="f8c94-103">Unsupported expressions</span></span>

<span data-ttu-id="f8c94-104">このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていない Transact-SQL 式について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8c94-104">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="f8c94-105">詳細については、「[Entity SQL と Transact-SQL の相違点](how-entity-sql-differs-from-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8c94-105">For more information, see [How Entity SQL Differs from Transact-SQL](how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="f8c94-106">定量化された述語</span><span class="sxs-lookup"><span data-stu-id="f8c94-106">Quantified predicates</span></span>

<span data-ttu-id="f8c94-107">Transact-SQL では、次の形式のコンストラクターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f8c94-107">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="f8c94-108">ただし、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、このようなコンストラクターがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f8c94-108">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="f8c94-109">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、これに相当する式を次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="f8c94-109">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="f8c94-110">\* 演算子</span><span class="sxs-lookup"><span data-stu-id="f8c94-110">\* operator</span></span>

<span data-ttu-id="f8c94-111">Transact-SQL では、すべての列を投影する必要があることを示すために、SELECT 句で \* 演算子を使用できます。これは [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f8c94-111">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="f8c94-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8c94-112">See also</span></span>

- [<span data-ttu-id="f8c94-113">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="f8c94-113">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="f8c94-114">Entity SQL と Transact-SQL の相違点</span><span class="sxs-lookup"><span data-stu-id="f8c94-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)
