---
description: '詳細情報: Skip 句 (Visual Basic)'
title: Skip 句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 6af702f65a724ea8c3d5a6122fb5f7a0ed5f6755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653551"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="3d24b-103">Skip 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d24b-103">Skip Clause (Visual Basic)</span></span>

<span data-ttu-id="3d24b-104">コレクション内の指定された数の要素をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="3d24b-104">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d24b-105">構文</span><span class="sxs-lookup"><span data-stu-id="3d24b-105">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="3d24b-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="3d24b-106">Parts</span></span>  

 `count`  
 <span data-ttu-id="3d24b-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="3d24b-107">Required.</span></span> <span data-ttu-id="3d24b-108">スキップするシーケンスの要素数に評価される値または式。</span><span class="sxs-lookup"><span data-stu-id="3d24b-108">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d24b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="3d24b-109">Remarks</span></span>  

 <span data-ttu-id="3d24b-110">`Skip` 句を使用すると、クエリは結果リストの先頭の要素をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="3d24b-110">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="3d24b-111">スキップする要素の数は `count` パラメーターによって識別されます。</span><span class="sxs-lookup"><span data-stu-id="3d24b-111">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="3d24b-112">`Take` 句と共に `Skip` 句を使用すると、クエリの任意のセグメントからのデータの範囲を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d24b-112">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="3d24b-113">これを行うには、範囲の最初の要素のインデックスを `Skip` 句に渡し、範囲のサイズを `Take` 句に渡します。</span><span class="sxs-lookup"><span data-stu-id="3d24b-113">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="3d24b-114">クエリで `Skip` 句を使用する場合は、`Skip` 句で目的の結果がバイパスされるような順番で、結果が返されるようにする必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="3d24b-114">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="3d24b-115">クエリ結果の順序付けの詳細については、「[Order By 句](order-by-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d24b-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="3d24b-116">指定した条件に応じて、特定の要素のみが無視されるように指定するには、`SkipWhile` 句を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3d24b-116">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d24b-117">例</span><span class="sxs-lookup"><span data-stu-id="3d24b-117">Example</span></span>  

 <span data-ttu-id="3d24b-118">次のコード例では、`Take` 句と共に `Skip` 句を使用して、ページ内のクエリからのデータを返しています。</span><span class="sxs-lookup"><span data-stu-id="3d24b-118">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="3d24b-119">`GetCustomers` 関数は、`Skip` 句を使用して、指定した開始インデックス値までリスト内の顧客をバイパスし、`Take` 句を使用して、そのインデックス値から始まる顧客のページを返します。</span><span class="sxs-lookup"><span data-stu-id="3d24b-119">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3d24b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d24b-120">See also</span></span>

- [<span data-ttu-id="3d24b-121">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="3d24b-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3d24b-122">クエリ</span><span class="sxs-lookup"><span data-stu-id="3d24b-122">Queries</span></span>](index.md)
- [<span data-ttu-id="3d24b-123">Select 句</span><span class="sxs-lookup"><span data-stu-id="3d24b-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="3d24b-124">From 句</span><span class="sxs-lookup"><span data-stu-id="3d24b-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="3d24b-125">Order By 句</span><span class="sxs-lookup"><span data-stu-id="3d24b-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="3d24b-126">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="3d24b-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="3d24b-127">Take 句</span><span class="sxs-lookup"><span data-stu-id="3d24b-127">Take Clause</span></span>](take-clause.md)
