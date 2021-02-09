---
description: '詳細情報: Take 句 (Visual Basic)'
title: Take 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 6542d262490d9d4acff893b2a99ffb60dd1446a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653538"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="ebe3d-103">Take 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebe3d-103">Take Clause (Visual Basic)</span></span>

<span data-ttu-id="ebe3d-104">コレクションの先頭から、指定された数の連続する要素を返します。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-104">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe3d-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebe3d-105">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="ebe3d-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="ebe3d-106">Parts</span></span>  

 `count`  
 <span data-ttu-id="ebe3d-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-107">Required.</span></span> <span data-ttu-id="ebe3d-108">返されるシーケンスの要素数に評価される値または式。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-108">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebe3d-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ebe3d-109">Remarks</span></span>  

 <span data-ttu-id="ebe3d-110">`Take` 句を指定すると、結果リストの先頭から指定した数の連続した要素がクエリに含まれます。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-110">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="ebe3d-111">含まれる要素の数は `count` パラメーターによって指定します。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-111">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="ebe3d-112">`Skip` 句と共に `Take` 句を使用すると、クエリの任意のセグメントからのデータの範囲を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-112">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="ebe3d-113">これを行うには、範囲の最初の要素のインデックスを `Skip` 句に渡し、範囲のサイズを `Take` 句に渡します。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-113">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="ebe3d-114">この場合、`Take` 句を `Skip` 句の後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-114">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="ebe3d-115">クエリで `Take` 句を使用する場合は、`Take` 句に目的の結果が含まれるようにする順番で、結果が返されるようにする必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-115">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="ebe3d-116">クエリ結果の順序付けの詳細については、「[Order By 句](order-by-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-116">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="ebe3d-117">指定した条件に応じて、特定の要素のみが返されるように指定するには、`TakeWhile` 句を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-117">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebe3d-118">例</span><span class="sxs-lookup"><span data-stu-id="ebe3d-118">Example</span></span>  

 <span data-ttu-id="ebe3d-119">次のコード例では、`Skip` 句と共に `Take` 句を使用して、ページ内のクエリからのデータを返しています。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-119">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="ebe3d-120">GetCustomers 関数では、`Skip` 句を使用して、指定した開始インデックス値までリスト内の顧客をバイパスし、`Take` 句を使用して、そのインデックス値から始まる顧客のページを返します。</span><span class="sxs-lookup"><span data-stu-id="ebe3d-120">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ebe3d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebe3d-121">See also</span></span>

- [<span data-ttu-id="ebe3d-122">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="ebe3d-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ebe3d-123">クエリ</span><span class="sxs-lookup"><span data-stu-id="ebe3d-123">Queries</span></span>](index.md)
- [<span data-ttu-id="ebe3d-124">Select 句</span><span class="sxs-lookup"><span data-stu-id="ebe3d-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="ebe3d-125">From 句</span><span class="sxs-lookup"><span data-stu-id="ebe3d-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="ebe3d-126">Order By 句</span><span class="sxs-lookup"><span data-stu-id="ebe3d-126">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="ebe3d-127">Take While 句</span><span class="sxs-lookup"><span data-stu-id="ebe3d-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="ebe3d-128">Skip 句</span><span class="sxs-lookup"><span data-stu-id="ebe3d-128">Skip Clause</span></span>](skip-clause.md)
