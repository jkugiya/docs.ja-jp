---
description: '詳細情報: データの並べ替え (Visual Basic)'
title: データの並べ替え
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: 83e05b2af1b3421d004a87630cd5df43f2a21ae4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468552"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="a1d09-103">データの並べ替え (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1d09-103">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="a1d09-104">並べ替え操作では、1 つ以上の属性に基づいてシーケンスの要素を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="a1d09-105">並べ替えの第 1 条件で、要素に対して一回目の並べ替えが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="a1d09-106">第 2 条件を指定すると、第 1 条件で並べ替えられた各グループ内の要素を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="a1d09-107">次の図は、文字のシーケンスに対してアルファベット順の並べ替え操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1d09-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![アルファベット順の並べ替え操作を示している図。](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="a1d09-109">次のセクションでは、データの並べ替えを実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a1d09-109">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="a1d09-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="a1d09-110">Methods</span></span>

|<span data-ttu-id="a1d09-111">メソッド名</span><span class="sxs-lookup"><span data-stu-id="a1d09-111">Method Name</span></span>|<span data-ttu-id="a1d09-112">説明</span><span class="sxs-lookup"><span data-stu-id="a1d09-112">Description</span></span>|<span data-ttu-id="a1d09-113">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="a1d09-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="a1d09-114">説明</span><span class="sxs-lookup"><span data-stu-id="a1d09-114">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="a1d09-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="a1d09-115">OrderBy</span></span>|<span data-ttu-id="a1d09-116">値を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-116">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="a1d09-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="a1d09-117">OrderByDescending</span></span>|<span data-ttu-id="a1d09-118">値を降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-118">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="a1d09-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="a1d09-119">ThenBy</span></span>|<span data-ttu-id="a1d09-120">2 番目の並べ替えを昇順で実行します。</span><span class="sxs-lookup"><span data-stu-id="a1d09-120">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="a1d09-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="a1d09-121">ThenByDescending</span></span>|<span data-ttu-id="a1d09-122">2 番目の並べ替えを降順で実行します。</span><span class="sxs-lookup"><span data-stu-id="a1d09-122">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="a1d09-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="a1d09-123">Reverse</span></span>|<span data-ttu-id="a1d09-124">コレクションの要素の順序を反転させます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="a1d09-125">該当なし。</span><span class="sxs-lookup"><span data-stu-id="a1d09-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="a1d09-126">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="a1d09-126">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="a1d09-127">1 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="a1d09-127">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="a1d09-128">1 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="a1d09-128">Primary Ascending Sort</span></span>

<span data-ttu-id="a1d09-129">次の例は、LINQ クエリで `Order By` 句を使用して、配列内の文字列を文字列長に従って昇順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1d09-129">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a><span data-ttu-id="a1d09-130">1 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="a1d09-130">Primary Descending Sort</span></span>

<span data-ttu-id="a1d09-131">次の例は、LINQ クエリで `Order By Descending` 句を使用して、文字列を最初の文字に従って降順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1d09-131">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a><span data-ttu-id="a1d09-132">2 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="a1d09-132">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="a1d09-133">2 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="a1d09-133">Secondary Ascending Sort</span></span>

<span data-ttu-id="a1d09-134">次の例は、LINQ クエリで `Order By` 句を使用して、配列内の文字列に対して 1 番目および 2 番目の並べ替えを実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1d09-134">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="a1d09-135">文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として、どちらも昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a><span data-ttu-id="a1d09-136">2 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="a1d09-136">Secondary Descending Sort</span></span>

<span data-ttu-id="a1d09-137">次の例は、LINQ クエリで `Order By Descending` 句を使用して、1 番目の並べ替えを昇順で実行し、2 番目の並べ替えを降順で実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1d09-137">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="a1d09-138">各文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="a1d09-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a><span data-ttu-id="a1d09-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1d09-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a1d09-140">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1d09-140">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="a1d09-141">Order By 句</span><span class="sxs-lookup"><span data-stu-id="a1d09-141">Order By Clause</span></span>](../../../language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="a1d09-142">方法: クエリ結果を並べ替える</span><span class="sxs-lookup"><span data-stu-id="a1d09-142">How to: Sort Query Results</span></span>](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="a1d09-143">方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1d09-143">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
