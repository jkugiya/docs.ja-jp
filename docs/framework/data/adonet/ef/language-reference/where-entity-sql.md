---
description: '詳細情報: WHERE (Entity SQL)'
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: e094a93927f6ac77aef772654f1d8d4fcf999cbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712871"
---
# <a name="where-entity-sql"></a><span data-ttu-id="553f4-103">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="553f4-103">WHERE (Entity SQL)</span></span>

<span data-ttu-id="553f4-104">WHERE 句は、[FROM](from-entity-sql.md) 句の直後に適用されます。</span><span class="sxs-lookup"><span data-stu-id="553f4-104">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="553f4-105">構文</span><span class="sxs-lookup"><span data-stu-id="553f4-105">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="553f4-106">引数</span><span class="sxs-lookup"><span data-stu-id="553f4-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="553f4-107">ブール型です。</span><span class="sxs-lookup"><span data-stu-id="553f4-107">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="553f4-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="553f4-108">Remarks</span></span>  

 <span data-ttu-id="553f4-109">WHERE 句のセマンティクスは、Transact-SQL で記述する場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="553f4-109">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="553f4-110">ソース コレクションの要素を条件を満たすものに制限することで、クエリ式によって生成されるオブジェクトを制限します。</span><span class="sxs-lookup"><span data-stu-id="553f4-110">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="553f4-111">式 `e` には Boolean 型が含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="553f4-111">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="553f4-112">WHERE 句は、FROM 句の直後、およびグループ化、順序付け、または投影が実行される前に適用されます。</span><span class="sxs-lookup"><span data-stu-id="553f4-112">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="553f4-113">FROM 句で定義されたすべての要素名は、WHERE 句の式に対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="553f4-113">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="553f4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="553f4-114">See also</span></span>

- [<span data-ttu-id="553f4-115">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="553f4-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="553f4-116">クエリ式</span><span class="sxs-lookup"><span data-stu-id="553f4-116">Query Expressions</span></span>](query-expressions-entity-sql.md)
