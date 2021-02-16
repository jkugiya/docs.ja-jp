---
description: '詳細情報: 集計操作 (Visual Basic)'
title: 集計操作
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 2ef41faf03100814e062ec98afb8fe17b1ef64bc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462166"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="70faf-103">集計操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70faf-103">Aggregation Operations (Visual Basic)</span></span>

<span data-ttu-id="70faf-104">集計の操作では、値の集合体から単一の値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="70faf-104">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="70faf-105">たとえば、1 か月分の毎日の気温値から 1 日あたりの平均の気温値を計算することが集計操作です。</span><span class="sxs-lookup"><span data-stu-id="70faf-105">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="70faf-106">次の図は、数値のシーケンスに対する 2 つの集計処理の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="70faf-106">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="70faf-107">最初の処理で数値が合計されます。</span><span class="sxs-lookup"><span data-stu-id="70faf-107">The first operation sums the numbers.</span></span> <span data-ttu-id="70faf-108">2 つ目の処理でシーケンスの最大値が返されます。</span><span class="sxs-lookup"><span data-stu-id="70faf-108">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![LINQ 集計操作を示す図。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="70faf-110">次のセクションでは、集計処理を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="70faf-110">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70faf-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="70faf-111">Methods</span></span>  
  
|<span data-ttu-id="70faf-112">メソッド名</span><span class="sxs-lookup"><span data-stu-id="70faf-112">Method Name</span></span>|<span data-ttu-id="70faf-113">説明</span><span class="sxs-lookup"><span data-stu-id="70faf-113">Description</span></span>|<span data-ttu-id="70faf-114">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="70faf-114">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="70faf-115">説明</span><span class="sxs-lookup"><span data-stu-id="70faf-115">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="70faf-116">Aggregate</span><span class="sxs-lookup"><span data-stu-id="70faf-116">Aggregate</span></span>|<span data-ttu-id="70faf-117">コレクションの値に対してカスタム集計処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="70faf-117">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="70faf-118">該当なし。</span><span class="sxs-lookup"><span data-stu-id="70faf-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="70faf-119">平均</span><span class="sxs-lookup"><span data-stu-id="70faf-119">Average</span></span>|<span data-ttu-id="70faf-120">値のコレクションの平均値を計算します。</span><span class="sxs-lookup"><span data-stu-id="70faf-120">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="70faf-121">カウント</span><span class="sxs-lookup"><span data-stu-id="70faf-121">Count</span></span>|<span data-ttu-id="70faf-122">コレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。</span><span class="sxs-lookup"><span data-stu-id="70faf-122">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="70faf-123">LongCount</span><span class="sxs-lookup"><span data-stu-id="70faf-123">LongCount</span></span>|<span data-ttu-id="70faf-124">大規模なコレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。</span><span class="sxs-lookup"><span data-stu-id="70faf-124">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="70faf-125">最大</span><span class="sxs-lookup"><span data-stu-id="70faf-125">Max</span></span>|<span data-ttu-id="70faf-126">コレクション内の最大値を決定します。</span><span class="sxs-lookup"><span data-stu-id="70faf-126">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="70faf-127">最小</span><span class="sxs-lookup"><span data-stu-id="70faf-127">Min</span></span>|<span data-ttu-id="70faf-128">コレクション内の最小値を決定します。</span><span class="sxs-lookup"><span data-stu-id="70faf-128">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="70faf-129">Sum</span><span class="sxs-lookup"><span data-stu-id="70faf-129">Sum</span></span>|<span data-ttu-id="70faf-130">コレクション内にある値の合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="70faf-130">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="70faf-131">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="70faf-131">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="70faf-132">平均</span><span class="sxs-lookup"><span data-stu-id="70faf-132">Average</span></span>  

 <span data-ttu-id="70faf-133">次のコード例では、Visual Basic の `Aggregate Into Average` 句を使用して、温度を表す数値配列の平均温度を計算します。</span><span class="sxs-lookup"><span data-stu-id="70faf-133">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="70faf-134">カウント</span><span class="sxs-lookup"><span data-stu-id="70faf-134">Count</span></span>  

 <span data-ttu-id="70faf-135">次のコード例は、Visual Basic の `Aggregate Into Count` 句を使用して、80 以上の値が配列に何個含まれるかをカウントします。</span><span class="sxs-lookup"><span data-stu-id="70faf-135">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="70faf-136">LongCount</span><span class="sxs-lookup"><span data-stu-id="70faf-136">LongCount</span></span>  

 <span data-ttu-id="70faf-137">次のコード例は、`Aggregate Into LongCount` 句を使用して、配列に含まれる値の数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="70faf-137">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="70faf-138">最大</span><span class="sxs-lookup"><span data-stu-id="70faf-138">Max</span></span>  

 <span data-ttu-id="70faf-139">次のコード例では、`Aggregate Into Max` 句を使用して、温度を表す数値配列の最高温度を計算します。</span><span class="sxs-lookup"><span data-stu-id="70faf-139">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="70faf-140">最小</span><span class="sxs-lookup"><span data-stu-id="70faf-140">Min</span></span>  

 <span data-ttu-id="70faf-141">次のコード例では、`Aggregate Into Min` 句を使用して、温度を表す数値配列の最低温度を計算します。</span><span class="sxs-lookup"><span data-stu-id="70faf-141">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="70faf-142">Sum</span><span class="sxs-lookup"><span data-stu-id="70faf-142">Sum</span></span>  

 <span data-ttu-id="70faf-143">次のコード例では、`Aggregate Into Sum` 句を使用して、経費を表す値の配列から経費の総額を計算します。</span><span class="sxs-lookup"><span data-stu-id="70faf-143">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="70faf-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="70faf-144">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="70faf-145">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70faf-145">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="70faf-146">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="70faf-146">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="70faf-147">方法: CSV テキスト ファイルの列値を計算する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70faf-147">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="70faf-148">方法: データの数、合計、または平均の算出</span><span class="sxs-lookup"><span data-stu-id="70faf-148">How to: Count, Sum, or Average Data</span></span>](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="70faf-149">方法: クエリ結果内の最小値と最大値の検索</span><span class="sxs-lookup"><span data-stu-id="70faf-149">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="70faf-150">方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70faf-150">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="70faf-151">方法: 一連のフォルダーの合計バイト数を照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70faf-151">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
