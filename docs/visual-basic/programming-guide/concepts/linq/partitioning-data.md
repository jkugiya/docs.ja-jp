---
description: '詳細情報: データのパーティション分割 (Visual Basic)'
title: データのパーティション分割
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 264a81d1217c7f5034058761033171b9c232fae2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465614"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="f5cb5-103">データのパーティション分割 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5cb5-103">Partitioning Data (Visual Basic)</span></span>

<span data-ttu-id="f5cb5-104">LINQ におけるパーティション分割とは、要素を並べ替えずに入力シーケンスを 2 つのセクションに分割し、それらのセクションの 1 つを返す操作を指します。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-104">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="f5cb5-105">次の図は、文字のシーケンスに対して 3 つの異なるパーティション分割操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-105">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="f5cb5-106">最初の操作では、シーケンスの最初の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-106">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="f5cb5-107">2 番目の操作では、最初の 3 つの要素がスキップされ、残りの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-107">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="f5cb5-108">3 番目の操作では、シーケンスの最初の 2 つの要素がスキップされ、次の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-108">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![LINQ のパーティション操作を示す図。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="f5cb5-110">次のセクションに、シーケンスのパーティション分割を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-110">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="f5cb5-111">演算子</span><span class="sxs-lookup"><span data-stu-id="f5cb5-111">Operators</span></span>  
  
|<span data-ttu-id="f5cb5-112">演算子名</span><span class="sxs-lookup"><span data-stu-id="f5cb5-112">Operator Name</span></span>|<span data-ttu-id="f5cb5-113">説明</span><span class="sxs-lookup"><span data-stu-id="f5cb5-113">Description</span></span>|<span data-ttu-id="f5cb5-114">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="f5cb5-114">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f5cb5-115">説明</span><span class="sxs-lookup"><span data-stu-id="f5cb5-115">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="f5cb5-116">Skip</span><span class="sxs-lookup"><span data-stu-id="f5cb5-116">Skip</span></span>|<span data-ttu-id="f5cb5-117">シーケンス内の指定した位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-117">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5cb5-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="f5cb5-118">SkipWhile</span></span>|<span data-ttu-id="f5cb5-119">述語関数に基づき、条件を満たさない要素が出現する位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5cb5-120">Take</span><span class="sxs-lookup"><span data-stu-id="f5cb5-120">Take</span></span>|<span data-ttu-id="f5cb5-121">シーケンス内の指定した位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-121">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f5cb5-122">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="f5cb5-122">TakeWhile</span></span>|<span data-ttu-id="f5cb5-123">述語関数に基づき、条件を満たさない要素が出現する位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-123">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f5cb5-124">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="f5cb5-124">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="f5cb5-125">Skip</span><span class="sxs-lookup"><span data-stu-id="f5cb5-125">Skip</span></span>  

 <span data-ttu-id="f5cb5-126">次のコード例は、Visual Basic の `Skip` 句を使用し、文字列配列に格納されている最初の 4 つの文字列をスキップして残りの文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-126">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="f5cb5-127">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="f5cb5-127">SkipWhile</span></span>  

 <span data-ttu-id="f5cb5-128">次のコード例は、Visual Basic の `Skip While` 句を使用し、配列内の文字列のうち、先頭文字が "a" である文字列をスキップします。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-128">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="f5cb5-129">配列に格納されている残りの文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-129">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="f5cb5-130">Take</span><span class="sxs-lookup"><span data-stu-id="f5cb5-130">Take</span></span>  

 <span data-ttu-id="f5cb5-131">次のコード例は、Visual Basic の `Take` 句を使用して、文字列配列内の最初の 2 つの文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-131">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="f5cb5-132">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="f5cb5-132">TakeWhile</span></span>  

 <span data-ttu-id="f5cb5-133">次のコード例は、Visual Basic の `Take While` 句を使用し、配列から長さが 5 以下である文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="f5cb5-133">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f5cb5-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5cb5-134">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f5cb5-135">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5cb5-135">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="f5cb5-136">Skip 句</span><span class="sxs-lookup"><span data-stu-id="f5cb5-136">Skip Clause</span></span>](../../../language-reference/queries/skip-clause.md)
- [<span data-ttu-id="f5cb5-137">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="f5cb5-137">Skip While Clause</span></span>](../../../language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="f5cb5-138">Take 句</span><span class="sxs-lookup"><span data-stu-id="f5cb5-138">Take Clause</span></span>](../../../language-reference/queries/take-clause.md)
- [<span data-ttu-id="f5cb5-139">Take While 句</span><span class="sxs-lookup"><span data-stu-id="f5cb5-139">Take While Clause</span></span>](../../../language-reference/queries/take-while-clause.md)
