---
description: '詳細情報: ページング (Entity SQL)'
title: ページング (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: c32474b772be359dbf2ffd46e5489cc0b4b2abb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791856"
---
# <a name="paging-entity-sql"></a><span data-ttu-id="871d5-103">ページング (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="871d5-103">Paging (Entity SQL)</span></span>

<span data-ttu-id="871d5-104">物理的なページングは、[ORDER BY](order-by-entity-sql.md) 句の [SKIP](skip-entity-sql.md) サブ句および [LIMIT](limit-entity-sql.md) サブ句を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="871d5-104">Physical paging can be performed by using the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="871d5-105">物理的ページングを決定的に実行するには、SKIP と LIMIT を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="871d5-105">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="871d5-106">非決定的な方法で結果の行の数を制限するには、[TOP](top-entity-sql.md) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="871d5-106">If you only want to restrict the number of rows in the result in a non-deterministic way, you should use [TOP](top-entity-sql.md).</span></span> <span data-ttu-id="871d5-107">TOP および SKIP/LIMIT は、同時には指定できません。</span><span class="sxs-lookup"><span data-stu-id="871d5-107">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="871d5-108">TOP の概要</span><span class="sxs-lookup"><span data-stu-id="871d5-108">TOP Overview</span></span>  

 <span data-ttu-id="871d5-109">SELECT 句には、オプションの ALL/DISTINCT 修飾子に続けてオプションの TOP サブ句を指定できます。</span><span class="sxs-lookup"><span data-stu-id="871d5-109">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="871d5-110">TOP サブ句は、クエリ結果の先頭から指定した行セットだけを返すよう指定します。</span><span class="sxs-lookup"><span data-stu-id="871d5-110">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="871d5-111">詳細については、「[TOP](top-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="871d5-111">For more information, see [TOP](top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="871d5-112">SKIP/LIMIT の概要</span><span class="sxs-lookup"><span data-stu-id="871d5-112">SKIP And LIMIT Overview</span></span>  

 <span data-ttu-id="871d5-113">SKIP と LIMIT は ORDER BY 句の一部です。</span><span class="sxs-lookup"><span data-stu-id="871d5-113">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="871d5-114">SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="871d5-114">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="871d5-115">たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。</span><span class="sxs-lookup"><span data-stu-id="871d5-115">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="871d5-116">LIMIT 式のサブ句が ORDER BY 句に存在する場合、クエリは並べ替え順序に従って並べ替えられ、結果の行数は LIMIT 式によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="871d5-116">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="871d5-117">たとえば、LIMIT 5 は、結果セットを 5 つのインスタンスまたは行に制限します。</span><span class="sxs-lookup"><span data-stu-id="871d5-117">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="871d5-118">SKIP と LIMIT を同時に使用することはできません。SKIP のみまたは LIMIT のみを ORDER BY 句と一緒に使用できます。</span><span class="sxs-lookup"><span data-stu-id="871d5-118">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="871d5-119">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="871d5-119">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="871d5-120">SKIP</span><span class="sxs-lookup"><span data-stu-id="871d5-120">SKIP</span></span>](skip-entity-sql.md)  
  
- [<span data-ttu-id="871d5-121">LIMIT</span><span class="sxs-lookup"><span data-stu-id="871d5-121">LIMIT</span></span>](limit-entity-sql.md)  
  
- [<span data-ttu-id="871d5-122">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="871d5-122">ORDER BY</span></span>](order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="871d5-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="871d5-123">See also</span></span>

- [<span data-ttu-id="871d5-124">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="871d5-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="871d5-125">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="871d5-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
- <span data-ttu-id="871d5-126">[方法: クエリの結果をページングする](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="871d5-126">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
