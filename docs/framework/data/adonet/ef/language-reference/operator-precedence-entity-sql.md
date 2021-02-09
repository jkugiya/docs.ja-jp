---
description: '詳細情報: 演算子の優先順位 (Entity SQL)'
title: 演算子の優先順位 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 72cfdecf7dfe4ce590d99e866429e771f9ede231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739327"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="e3a68-103">演算子の優先順位 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e3a68-103">Operator Precedence (Entity SQL)</span></span>

<span data-ttu-id="e3a68-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリに複数の演算子がある場合は、演算子の優先順位によって、操作の実行順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="e3a68-104">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="e3a68-105">実行される順序により、クエリ結果の値は大きく変わります。</span><span class="sxs-lookup"><span data-stu-id="e3a68-105">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="e3a68-106">演算子には、次の表に示す優先順位レベルが定義されています。</span><span class="sxs-lookup"><span data-stu-id="e3a68-106">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="e3a68-107">優先順位が高い演算子は、優先順位が低い演算子よりも前に評価されます。</span><span class="sxs-lookup"><span data-stu-id="e3a68-107">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="e3a68-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e3a68-108">Level</span></span>|<span data-ttu-id="e3a68-109">演算の種類</span><span class="sxs-lookup"><span data-stu-id="e3a68-109">Operation type</span></span>|<span data-ttu-id="e3a68-110">演算子</span><span class="sxs-lookup"><span data-stu-id="e3a68-110">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="e3a68-111">1</span><span class="sxs-lookup"><span data-stu-id="e3a68-111">1</span></span>|<span data-ttu-id="e3a68-112">1 次式</span><span class="sxs-lookup"><span data-stu-id="e3a68-112">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="e3a68-113">2</span><span class="sxs-lookup"><span data-stu-id="e3a68-113">2</span></span>|<span data-ttu-id="e3a68-114">単項</span><span class="sxs-lookup"><span data-stu-id="e3a68-114">Unary</span></span>|`! not`|  
|<span data-ttu-id="e3a68-115">3</span><span class="sxs-lookup"><span data-stu-id="e3a68-115">3</span></span>|<span data-ttu-id="e3a68-116">乗法</span><span class="sxs-lookup"><span data-stu-id="e3a68-116">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="e3a68-117">4</span><span class="sxs-lookup"><span data-stu-id="e3a68-117">4</span></span>|<span data-ttu-id="e3a68-118">加法</span><span class="sxs-lookup"><span data-stu-id="e3a68-118">Additive</span></span>|`+ -`|  
|<span data-ttu-id="e3a68-119">5</span><span class="sxs-lookup"><span data-stu-id="e3a68-119">5</span></span>|<span data-ttu-id="e3a68-120">順序</span><span class="sxs-lookup"><span data-stu-id="e3a68-120">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="e3a68-121">6</span><span class="sxs-lookup"><span data-stu-id="e3a68-121">6</span></span>|<span data-ttu-id="e3a68-122">等価比較</span><span class="sxs-lookup"><span data-stu-id="e3a68-122">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="e3a68-123">7</span><span class="sxs-lookup"><span data-stu-id="e3a68-123">7</span></span>|<span data-ttu-id="e3a68-124">条件 AND</span><span class="sxs-lookup"><span data-stu-id="e3a68-124">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="e3a68-125">8</span><span class="sxs-lookup"><span data-stu-id="e3a68-125">8</span></span>|<span data-ttu-id="e3a68-126">条件 OR</span><span class="sxs-lookup"><span data-stu-id="e3a68-126">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="e3a68-127">式の中の 2 つの演算子が同じ優先順位レベルである場合は、クエリの中での位置に従って演算子は左から右へと評価されます。</span><span class="sxs-lookup"><span data-stu-id="e3a68-127">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="e3a68-128">たとえば、`x+y-z` は `(x+y)-z` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="e3a68-128">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="e3a68-129">クエリの中で演算子の定義済みの優先順位をオーバーライドするには、かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="e3a68-129">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="e3a68-130">この場合、かっこ内のすべての演算が評価され、1 つの結果が作成されてから、かっこ外の演算子でこの結果が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e3a68-130">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="e3a68-131">たとえば、`x+y*z` の場合、`y` と `z` の積に `x` が加算されますが、`(x+y)*z` の場合は、`x` と `y` の和に `z` が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="e3a68-131">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a68-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3a68-132">See also</span></span>

- [<span data-ttu-id="e3a68-133">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="e3a68-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
