---
description: '詳細情報: 標準クエリ演算子の変換'
title: 標準クエリ演算子の変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: e7e45e8f27f1e7d3c572f00ea014b4edb288b2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681527"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="ffaf3-103">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="ffaf3-103">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-104">では、標準クエリ演算子から SQL コマンドへの変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-104">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="ffaf3-105">SQL 変換の実行のセマンティクスは、データベースのクエリ プロセッサによって決まります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-105">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="ffaf3-106">標準クエリ演算子は "*シーケンス*" に対して定義されています。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-106">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="ffaf3-107">シーケンスは "*順序付き*" で、シーケンスの各要素の参照 ID に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-107">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="ffaf3-108">詳しくは、「[標準クエリ演算子の概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)」または「[標準クエリ演算子の概要 (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-108">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="ffaf3-109">SQL で扱われるのは主に、"*順序なしの値のセット*" です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-109">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="ffaf3-110">通常、順序付けは、明示的な後処理の操作として、クエリの中間結果ではなく最終結果に対して適用されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-110">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="ffaf3-111">ID は値で定義されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-111">Identity is defined by values.</span></span> <span data-ttu-id="ffaf3-112">このため、SQL クエリは、"*セット*" ではなくマルチセット ("*バッグ*") を扱うものとして理解されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-112">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="ffaf3-113">以下、標準クエリ演算子とその SQL 変換との違いを、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 用 SQL Server プロバイダーの場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-113">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="ffaf3-114">演算子のサポート</span><span class="sxs-lookup"><span data-stu-id="ffaf3-114">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="ffaf3-115">Concat</span><span class="sxs-lookup"><span data-stu-id="ffaf3-115">Concat</span></span>

<span data-ttu-id="ffaf3-116"><xref:System.Linq.Enumerable.Concat%2A> メソッドは、受信側と引数の順序が同じである、順序付けされたマルチセットに対して定義されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-116">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="ffaf3-117"><xref:System.Linq.Enumerable.Concat%2A> は、共通の順序に従ったマルチセットに対する `UNION ALL` として機能します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-117"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="ffaf3-118">最後の手順は、結果を生成する前の SQL での順序付けです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-118">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="ffaf3-119"><xref:System.Linq.Enumerable.Concat%2A> は、引数の順序を維持しません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-119"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="ffaf3-120">適切な順序にするには、<xref:System.Linq.Enumerable.Concat%2A> の結果を明示的に順序付けする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-120">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="ffaf3-121">Intersect、Except、Union</span><span class="sxs-lookup"><span data-stu-id="ffaf3-121">Intersect, Except, Union</span></span>

<span data-ttu-id="ffaf3-122"><xref:System.Linq.Enumerable.Intersect%2A> メソッドと <xref:System.Linq.Enumerable.Except%2A> メソッドは、セットに対してのみ正しく定義されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-122">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="ffaf3-123">マルチセットのセマンティクスは未定義です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-123">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="ffaf3-124"><xref:System.Linq.Enumerable.Union%2A> メソッドは、マルチセットの順序なし連結メソッドとして、マルチセットに対して定義されます (事実上、SQL の UNION ALL 句の結果)。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-124">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="ffaf3-125">Take、Skip</span><span class="sxs-lookup"><span data-stu-id="ffaf3-125">Take, Skip</span></span>

<span data-ttu-id="ffaf3-126"><xref:System.Linq.Enumerable.Take%2A> メソッドと <xref:System.Linq.Enumerable.Skip%2A> メソッドは、"*順序付けされたセット*" に対してのみ正しく定義されています。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-126"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="ffaf3-127">順序付けされていないセットまたはマルチセットのセマンティクスは未定義です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-127">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="ffaf3-128"><xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を SQL Server 2000 に対するクエリで使用する場合は、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-128"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="ffaf3-129">詳しくは、「[トラブルシューティング](troubleshooting.md)」の「SQL Server 2000 の Skip 例外と Take 例外」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-129">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

<span data-ttu-id="ffaf3-130">SQL での順序付けに対する制限のため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、これらのメソッドの引数の順序を、メソッドの結果に移動することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-130">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="ffaf3-131">たとえば、次のような [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-131">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="ffaf3-132">このコードに対して生成される SQL では、順序が次のように末尾に移動されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-132">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="ffaf3-133"><xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を連結する場合は、指定されているすべての順序が一致することが当然必要です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-133">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="ffaf3-134">それ以外の場合、結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-134">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="ffaf3-135"><xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> はいずれも、標準クエリ演算子の仕様に基づく、負でない定数の整数引数に対して正しく定義されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-135">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="ffaf3-136">変換されない演算子</span><span class="sxs-lookup"><span data-stu-id="ffaf3-136">Operators with No Translation</span></span>

<span data-ttu-id="ffaf3-137">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって変換されないメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-137">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="ffaf3-138">最も一般的な理由は、順序なしのマルチセットとシーケンスの違いにあります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-138">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="ffaf3-139">演算子</span><span class="sxs-lookup"><span data-stu-id="ffaf3-139">Operators</span></span>|<span data-ttu-id="ffaf3-140">理由</span><span class="sxs-lookup"><span data-stu-id="ffaf3-140">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="ffaf3-141"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="ffaf3-141"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="ffaf3-142">SQL クエリの操作の対象は、シーケンスではなく、マルチセットです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-142">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="ffaf3-143">結果に対して適用する最後の句が `ORDER BY` であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-143">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="ffaf3-144">このため、これら 2 つのメソッドには、汎用的な変換がありません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-144">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="ffaf3-145">順序付けされたセットに対しては、このメソッドの変換が可能ですが、現在の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では変換されません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-145">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="ffaf3-146"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="ffaf3-146"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="ffaf3-147">順序付けされたセットに対しては、これらのメソッドの変換が可能ですが、現在の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では変換されません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-147">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="ffaf3-148"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="ffaf3-148"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="ffaf3-149">SQL クエリの操作の対象は、インデックス可能なシーケンスではなくマルチセットです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-149">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="ffaf3-150"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (既定の引数のオーバーロード)</span><span class="sxs-lookup"><span data-stu-id="ffaf3-150"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="ffaf3-151">一般に、任意のタプルに対して既定値を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-151">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="ffaf3-152">場合によっては、外部結合を通じて、タプルに対する null 値の使用が可能です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-152">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="ffaf3-153">式の変換</span><span class="sxs-lookup"><span data-stu-id="ffaf3-153">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="ffaf3-154">null セマンティクス</span><span class="sxs-lookup"><span data-stu-id="ffaf3-154">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-155">は、null 比較セマンティクスを SQL に強制しません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-155">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="ffaf3-156">比較演算子は、対応する SQL の演算子に構文上は変換されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-156">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="ffaf3-157">このため、セマンティクスには、サーバーまたは接続の設定で定義された SQL セマンティクスが反映されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-157">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="ffaf3-158">たとえば、SQL Server の既定の設定では、2 つの null 値は一致しないと見なされますが、この設定を変更することでセマンティクスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-158">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-159">は、クエリを変換するときにサーバーの設定を考慮しません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-159">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="ffaf3-160">リテラルの null による比較は適切な SQL 形式 (`is null` または `is not null`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-160">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="ffaf3-161">`null` の値の照合順序は SQL Server で定義されます</span><span class="sxs-lookup"><span data-stu-id="ffaf3-161">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-162">では変更されません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-162">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="ffaf3-163">集計</span><span class="sxs-lookup"><span data-stu-id="ffaf3-163">Aggregates</span></span>

<span data-ttu-id="ffaf3-164">標準クエリ演算子の集計メソッド <xref:System.Linq.Enumerable.Sum%2A> では、空のシーケンスや null のみを含むシーケンスはゼロに評価されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-164">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="ffaf3-165">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、SQL のセマンティクスは変更されず、空のシーケンスまたは null のみを含むシーケンスに対する <xref:System.Linq.Enumerable.Sum%2A> による評価は、ゼロではなく `null` になります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-165">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="ffaf3-166">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での集計には、中間結果に対する SQL の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-166">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="ffaf3-167">32 ビットの整数の <xref:System.Linq.Enumerable.Sum%2A> の計算では、64 ビットの結果は使用されません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-167">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="ffaf3-168">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による <xref:System.Linq.Enumerable.Sum%2A> の変換では、オーバーフローが発生することがあります。これには、標準クエリ演算子の実装で、対応するメモリ内シーケンスでオーバーフローが発生しないケースも含まれます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-168">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="ffaf3-169">同様に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が整数値の <xref:System.Linq.Enumerable.Average%2A> を変換するときには、`integer` ではなく `double` として計算されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-169">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="ffaf3-170">エンティティ引数</span><span class="sxs-lookup"><span data-stu-id="ffaf3-170">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-171">では、<xref:System.Linq.Enumerable.GroupBy%2A> メソッドおよび <xref:System.Linq.Enumerable.OrderBy%2A> メソッドでエンティティ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-171">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="ffaf3-172">これらの演算子の変換では、型の引数を使用している場合、その型のすべてのメンバーを指定しているのと同等と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-172">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="ffaf3-173">たとえば、次のコードは同じ意味です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-173">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="ffaf3-174">引数の等値性/比較</span><span class="sxs-lookup"><span data-stu-id="ffaf3-174">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="ffaf3-175">以下のメソッドの実装では、引数が等値であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-175">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-176">では、"*フラット*" な引数に対して、等値性と比較がサポートされていますが、シーケンスの引数またはシーケンスを含む引数に対してはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-176">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="ffaf3-177">フラットな引数とは、SQL の行に対応付けられる型のものです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-177">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="ffaf3-178">シーケンスを含まないと静的に決定できる 1 つまたは複数のエンティティ型の射影は、フラットな引数と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-178">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="ffaf3-179">フラットな引数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-179">The following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="ffaf3-180">フラットでない (階層構造の) 引数の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-180">The following are examples of non-flat (hierarchical) arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="ffaf3-181">Visual Basic の関数の変換</span><span class="sxs-lookup"><span data-stu-id="ffaf3-181">Visual Basic Function Translation</span></span>

<span data-ttu-id="ffaf3-182">Visual Basic のコンパイラが使用する以下のヘルパー関数は、対応する SQL 演算子および関数に変換されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-182">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="ffaf3-183">変換メソッド :</span><span class="sxs-lookup"><span data-stu-id="ffaf3-183">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="ffaf3-184">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="ffaf3-184">ToBoolean</span></span>|<span data-ttu-id="ffaf3-185">ToSByte</span><span class="sxs-lookup"><span data-stu-id="ffaf3-185">ToSByte</span></span>|<span data-ttu-id="ffaf3-186">ToByte</span><span class="sxs-lookup"><span data-stu-id="ffaf3-186">ToByte</span></span>|<span data-ttu-id="ffaf3-187">ToChar</span><span class="sxs-lookup"><span data-stu-id="ffaf3-187">ToChar</span></span>|
|<span data-ttu-id="ffaf3-188">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="ffaf3-188">ToCharArrayRankOne</span></span>|<span data-ttu-id="ffaf3-189">ToDate</span><span class="sxs-lookup"><span data-stu-id="ffaf3-189">ToDate</span></span>|<span data-ttu-id="ffaf3-190">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="ffaf3-190">ToDecimal</span></span>|<span data-ttu-id="ffaf3-191">ToDouble</span><span class="sxs-lookup"><span data-stu-id="ffaf3-191">ToDouble</span></span>|
|<span data-ttu-id="ffaf3-192">ToInteger</span><span class="sxs-lookup"><span data-stu-id="ffaf3-192">ToInteger</span></span>|<span data-ttu-id="ffaf3-193">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="ffaf3-193">ToUInteger</span></span>|<span data-ttu-id="ffaf3-194">ToLong</span><span class="sxs-lookup"><span data-stu-id="ffaf3-194">ToLong</span></span>|<span data-ttu-id="ffaf3-195">ToULong</span><span class="sxs-lookup"><span data-stu-id="ffaf3-195">ToULong</span></span>|
|<span data-ttu-id="ffaf3-196">ToShort</span><span class="sxs-lookup"><span data-stu-id="ffaf3-196">ToShort</span></span>|<span data-ttu-id="ffaf3-197">ToUShort</span><span class="sxs-lookup"><span data-stu-id="ffaf3-197">ToUShort</span></span>|<span data-ttu-id="ffaf3-198">ToSingle</span><span class="sxs-lookup"><span data-stu-id="ffaf3-198">ToSingle</span></span>|<span data-ttu-id="ffaf3-199">ToString</span><span class="sxs-lookup"><span data-stu-id="ffaf3-199">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="ffaf3-200">継承のサポート</span><span class="sxs-lookup"><span data-stu-id="ffaf3-200">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="ffaf3-201">継承の対応付けの制限</span><span class="sxs-lookup"><span data-stu-id="ffaf3-201">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="ffaf3-202">詳細については、「[方法: 継承階層を割り当てる](how-to-map-inheritance-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-202">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="ffaf3-203">クエリでの継承</span><span class="sxs-lookup"><span data-stu-id="ffaf3-203">Inheritance in Queries</span></span>

<span data-ttu-id="ffaf3-204">C# のキャストは射影でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-204">C# casts are supported only in projection.</span></span> <span data-ttu-id="ffaf3-205">他の場所で使用したキャストは変換されず、無視されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-205">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="ffaf3-206">SQL 関数名を除き、SQL が実行するのは、共通言語ランタイム (CLR: Common Language Runtime) の <xref:System.Convert> に相当する処理のみです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-206">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="ffaf3-207">つまり、SQL は、ある型の値を別の型に変更することはできます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-207">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="ffaf3-208">CLR のキャストに相当するものはありません。同じビット列を別の型として再解釈するという概念がないためです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-208">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="ffaf3-209">したがって、C# のキャストはローカルでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-209">That is why a C# cast works only locally.</span></span> <span data-ttu-id="ffaf3-210">リモート処理はされません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-210">It is not remoted.</span></span>

<span data-ttu-id="ffaf3-211">演算子 `is` と `as`、および `GetType` メソッドは、`Select` 演算子に限定されません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-211">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="ffaf3-212">他のクエリ演算子でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-212">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="ffaf3-213">SQL Server 2008 のサポート</span><span class="sxs-lookup"><span data-stu-id="ffaf3-213">SQL Server 2008 Support</span></span>

<span data-ttu-id="ffaf3-214">.NET Framework 3.5 SP1 以降、LINQ to SQL は SQL Server 2008 で導入された新しい日付/時刻型へのマッピングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-214">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="ffaf3-215">ただし、これらの新しい型にマッピングされた値を操作するときに使用できる LINQ to SQL のクエリ演算子にはいくつか制限があります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-215">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="ffaf3-216">サポートされていないクエリ演算子</span><span class="sxs-lookup"><span data-stu-id="ffaf3-216">Unsupported Query Operators</span></span>

<span data-ttu-id="ffaf3-217">`DATETIME2`、`DATE`、`TIME`、および `DATETIMEOFFSET` は、SQL Server の新しい日付/時刻型にマッピングされた値ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-217">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="ffaf3-218">SQL Server の日付/時刻型へのマッピングについて詳しくは、「[SQL と CLR の型マッピング](sql-clr-type-mapping.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-218">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="ffaf3-219">SQL Server 2005 のサポート</span><span class="sxs-lookup"><span data-stu-id="ffaf3-219">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-220">は、SQL Server 2005 の以下の機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-220">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="ffaf3-221">SQL CLR 用に作成されたストアド プロシージャ。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-221">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="ffaf3-222">ユーザー定義型。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-222">User-defined type.</span></span>

- <span data-ttu-id="ffaf3-223">XML クエリ機能。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-223">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="ffaf3-224">SQL Server 2000 のサポート</span><span class="sxs-lookup"><span data-stu-id="ffaf3-224">SQL Server 2000 Support</span></span>

<span data-ttu-id="ffaf3-225">(Microsoft SQL Server 2005 と比較した) SQL Server 2000 での以下の制限事項は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のサポートに影響します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-225">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="ffaf3-226">Cross Apply 演算子および Outer Apply 演算子</span><span class="sxs-lookup"><span data-stu-id="ffaf3-226">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="ffaf3-227">これらの演算子は SQL Server 2000 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-227">These operators are not available in SQL Server 2000.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ffaf3-228">は、一連の書き換えを行って、これらの演算子を適切な結合に置換します。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-228">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="ffaf3-229">`Cross Apply` および `Outer Apply` は、リレーションシップ ナビゲーションに対してのみ生成されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-229">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="ffaf3-230">どのようなクエリのセットに対してこのような書き換えが可能かは、正しく定義されていません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-230">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="ffaf3-231">このため、SQL Server 2000 でサポートされている最小限のクエリのセットは、リレーションシップ ナビゲーションを含まないクエリのセットです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-231">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="ffaf3-232">text / ntext</span><span class="sxs-lookup"><span data-stu-id="ffaf3-232">text / ntext</span></span>

<span data-ttu-id="ffaf3-233">データ型 `text` および `ntext` は、Microsoft SQL Server 2005 でサポートされている、`varchar(max)` および `nvarchar(max)` に対する特定のクエリ操作では使用できません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-233">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="ffaf3-234">この制限事項には、対処方法はありません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-234">No resolution is available for this limitation.</span></span> <span data-ttu-id="ffaf3-235">具体的には、`Distinct()` 列または `text` 列に割り当てられているメンバーを含む結果に対して、`ntext` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-235">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="ffaf3-236">入れ子になったクエリによってトリガーされる動作</span><span class="sxs-lookup"><span data-stu-id="ffaf3-236">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="ffaf3-237">SQL Server 2000 (SP4 まで) のバインダーには、入れ子になったクエリによってトリガーされる特異な動作があります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-237">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="ffaf3-238">この特異動作をトリガーする SQL クエリのセットは、正しく定義されていません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-238">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="ffaf3-239">このため、SQL Server の例外を発生させる可能性がある [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリのセットは定義することができません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-239">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="ffaf3-240">Skip 演算子および Take 演算子</span><span class="sxs-lookup"><span data-stu-id="ffaf3-240">Skip and Take Operators</span></span>

<span data-ttu-id="ffaf3-241"><xref:System.Linq.Enumerable.Take%2A> と <xref:System.Linq.Enumerable.Skip%2A> を SQL Server 2000 に対するクエリで使用する場合は、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-241"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="ffaf3-242">詳しくは、「[トラブルシューティング](troubleshooting.md)」の「SQL Server 2000 の Skip 例外と Take 例外」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-242">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="ffaf3-243">オブジェクトの具体化</span><span class="sxs-lookup"><span data-stu-id="ffaf3-243">Object Materialization</span></span>

<span data-ttu-id="ffaf3-244">実体化とは、1 つまたは複数の SQL クエリで返された行から CLR オブジェクトを作成することです。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-244">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="ffaf3-245">以下の呼び出しは、実体化の一部として "*ローカルで実行*" されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-245">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="ffaf3-246">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ffaf3-246">Constructors</span></span>

  - <span data-ttu-id="ffaf3-247">射影での `ToString` メソッド</span><span class="sxs-lookup"><span data-stu-id="ffaf3-247">`ToString` methods in projections</span></span>

  - <span data-ttu-id="ffaf3-248">射影での型キャスト</span><span class="sxs-lookup"><span data-stu-id="ffaf3-248">Type casts in projections</span></span>

- <span data-ttu-id="ffaf3-249"><xref:System.Linq.Enumerable.AsEnumerable%2A> メソッドに続くメソッドは "*ローカルで実行*" されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-249">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="ffaf3-250">このメソッドでは即時実行は行われません。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-250">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="ffaf3-251">`struct` は、クエリ結果の戻り値の型として、または結果の型のメンバーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-251">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="ffaf3-252">エンティティはクラスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-252">Entities are required to be classes.</span></span> <span data-ttu-id="ffaf3-253">匿名型はクラス インスタンスとして実体化されますが、射影では名前付き構造体 (エンティティ以外) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-253">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="ffaf3-254">クエリ結果の戻り値の型のメンバーには、<xref:System.Linq.IQueryable%601> 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-254">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="ffaf3-255">これはローカル コレクションとして実体化されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-255">It is materialized as a local collection.</span></span>

- <span data-ttu-id="ffaf3-256">以下のメソッドでは、メソッドが適用されるシーケンスが "*すぐに実体化*" されます。</span><span class="sxs-lookup"><span data-stu-id="ffaf3-256">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="ffaf3-257">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffaf3-257">See also</span></span>

- [<span data-ttu-id="ffaf3-258">参照</span><span class="sxs-lookup"><span data-stu-id="ffaf3-258">Reference</span></span>](reference.md)
- [<span data-ttu-id="ffaf3-259">シーケンスの要素の取得またはスキップ</span><span class="sxs-lookup"><span data-stu-id="ffaf3-259">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="ffaf3-260">2 つのシーケンスの連結</span><span class="sxs-lookup"><span data-stu-id="ffaf3-260">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)
- [<span data-ttu-id="ffaf3-261">2 つのシーケンスの差集合の取得</span><span class="sxs-lookup"><span data-stu-id="ffaf3-261">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="ffaf3-262">2 つのシーケンスの積集合の取得</span><span class="sxs-lookup"><span data-stu-id="ffaf3-262">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="ffaf3-263">2 つのシーケンスの和集合の取得</span><span class="sxs-lookup"><span data-stu-id="ffaf3-263">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)
