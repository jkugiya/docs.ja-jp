---
description: '詳細情報: セット操作 (Visual Basic)'
title: セット操作
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 9c75c9e029ba260917f59c7d2ea0341c157bf406
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471670"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="c8d57-103">セット操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8d57-103">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="c8d57-104">LINQ のセット操作は、同一または別個のコレクション (またはセット) に等しい要素があるかどうかに基づいて、結果を生成するクエリ操作です。</span><span class="sxs-lookup"><span data-stu-id="c8d57-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="c8d57-105">次のセクションでは、セット操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="c8d57-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c8d57-106">Methods</span></span>

|<span data-ttu-id="c8d57-107">メソッド名</span><span class="sxs-lookup"><span data-stu-id="c8d57-107">Method Name</span></span>|<span data-ttu-id="c8d57-108">説明</span><span class="sxs-lookup"><span data-stu-id="c8d57-108">Description</span></span>|<span data-ttu-id="c8d57-109">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="c8d57-109">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c8d57-110">説明</span><span class="sxs-lookup"><span data-stu-id="c8d57-110">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="c8d57-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="c8d57-111">Distinct</span></span>|<span data-ttu-id="c8d57-112">コレクションから重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-112">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c8d57-113">除く</span><span class="sxs-lookup"><span data-stu-id="c8d57-113">Except</span></span>|<span data-ttu-id="c8d57-114">差集合 (一方のコレクションにだけ存在し、もう一方のコレクションには出現しない要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="c8d57-115">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c8d57-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c8d57-116">交差</span><span class="sxs-lookup"><span data-stu-id="c8d57-116">Intersect</span></span>|<span data-ttu-id="c8d57-117">積集合 (2 つのコレクションのそれぞれに出現する要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="c8d57-118">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c8d57-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c8d57-119">和集合</span><span class="sxs-lookup"><span data-stu-id="c8d57-119">Union</span></span>|<span data-ttu-id="c8d57-120">和集合 (2 つのコレクションのどちらかに出現する一意の要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="c8d57-121">該当なし。</span><span class="sxs-lookup"><span data-stu-id="c8d57-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="c8d57-122">セット操作の比較</span><span class="sxs-lookup"><span data-stu-id="c8d57-122">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="c8d57-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="c8d57-123">Distinct</span></span>

<span data-ttu-id="c8d57-124">次の図は、文字のシーケンスに対する <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> メソッドの動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8d57-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="c8d57-125">返されたシーケンスには、入力シーケンスからの一意の要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="c8d57-125">The returned sequence contains the unique elements from the input sequence.</span></span>

![Distinct&#40;&#41; の動作を示すグラフィック。](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="c8d57-127">除く</span><span class="sxs-lookup"><span data-stu-id="c8d57-127">Except</span></span>

<span data-ttu-id="c8d57-128"><xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> の動作を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c8d57-129">返されたシーケンスには、1 つ目の入力シーケンスのうち、2 つ目の入力シーケンスには存在しない要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="c8d57-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="c8d57-130">![Except&#40;&#41; のアクションを示すグラフィック。](./media/set-operations/except-behavior-graphic.png "Except の動作を示します。")</span><span class="sxs-lookup"><span data-stu-id="c8d57-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="c8d57-131">交差</span><span class="sxs-lookup"><span data-stu-id="c8d57-131">Intersect</span></span>

<span data-ttu-id="c8d57-132"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> の動作を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c8d57-133">返されたシーケンスには、両方の入力シーケンスに共通する要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="c8d57-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![2 つのシーケンスの交差部分を示すグラフィック。](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="c8d57-135">和集合</span><span class="sxs-lookup"><span data-stu-id="c8d57-135">Union</span></span>

<span data-ttu-id="c8d57-136">次の図は、2 つの文字シーケンスに対する和集合演算を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8d57-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="c8d57-137">返されたシーケンスには、両方の入力シーケンスからの一意の要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="c8d57-137">The returned sequence contains the unique elements from both input sequences.</span></span>

![2 つのシーケンスの結合を示すグラフィック。](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="c8d57-139">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="c8d57-139">Query Expression Syntax Example</span></span>

<span data-ttu-id="c8d57-140">次の例では、LINQ クエリで `Distinct` 句を使用して、整数のリストから一意の数値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c8d57-140">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="c8d57-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8d57-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c8d57-142">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8d57-142">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="c8d57-143">Distinct 句</span><span class="sxs-lookup"><span data-stu-id="c8d57-143">Distinct Clause</span></span>](../../../language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="c8d57-144">方法: 文字列コレクションを結合および比較する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8d57-144">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="c8d57-145">方法: 2 つのリストの差集合を見つける (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8d57-145">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)
