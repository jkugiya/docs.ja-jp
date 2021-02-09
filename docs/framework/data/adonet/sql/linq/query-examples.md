---
description: '詳細情報: クエリの例'
title: クエリの例
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: 77eb5c475a4f84930bd760b34f48d3954083c892
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695231"
---
# <a name="query-examples"></a><span data-ttu-id="e733e-103">クエリの例</span><span class="sxs-lookup"><span data-stu-id="e733e-103">Query Examples</span></span>

<span data-ttu-id="e733e-104">このセクションでは、Visual Basic および C# で一般的な [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-104">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="e733e-105">Visual Studio を使用している場合は、「サンプル」セクションに多数のサンプル ソリューションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e733e-105">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="e733e-106">詳細については、「[サンプル](samples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e733e-106">For more information, see [Samples](samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e733e-107">*db* は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ドキュメントのコード サンプルでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="e733e-107">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="e733e-108">*db* は、*Northwind* クラスのインスタンスであることが前提です。このクラスは、<xref:System.Data.Linq.DataContext> から継承されます。</span><span class="sxs-lookup"><span data-stu-id="e733e-108">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e733e-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e733e-109">In This Section</span></span>  

 [<span data-ttu-id="e733e-110">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="e733e-110">Aggregate Queries</span></span>](aggregate-queries.md)  
 <span data-ttu-id="e733e-111"><xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A> などの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-111">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="e733e-112">シーケンスの最初の要素の取得</span><span class="sxs-lookup"><span data-stu-id="e733e-112">Return the First Element in a Sequence</span></span>](return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="e733e-113"><xref:System.Linq.Enumerable.First%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-113">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-114">シーケンスの要素の取得またはスキップ</span><span class="sxs-lookup"><span data-stu-id="e733e-114">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="e733e-115"><xref:System.Linq.Enumerable.Take%2A> および <xref:System.Linq.Enumerable.Skip%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-115">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-116">シーケンスの要素の並べ替え</span><span class="sxs-lookup"><span data-stu-id="e733e-116">Sort Elements in a Sequence</span></span>](sort-elements-in-a-sequence.md)  
 <span data-ttu-id="e733e-117"><xref:System.Linq.Enumerable.OrderBy%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-117">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-118">シーケンスの要素のグループ化</span><span class="sxs-lookup"><span data-stu-id="e733e-118">Group Elements in a Sequence</span></span>](group-elements-in-a-sequence.md)  
 <span data-ttu-id="e733e-119"><xref:System.Linq.Enumerable.GroupBy%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-119">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-120">シーケンスからの重複する要素の削除</span><span class="sxs-lookup"><span data-stu-id="e733e-120">Eliminate Duplicate Elements from a Sequence</span></span>](eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="e733e-121"><xref:System.Linq.Enumerable.Distinct%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-121">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-122">シーケンスのすべての要素が条件を満たしているかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="e733e-122">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="e733e-123"><xref:System.Linq.Enumerable.All%2A> および <xref:System.Linq.Enumerable.Any%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-123">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-124">2 つのシーケンスの連結</span><span class="sxs-lookup"><span data-stu-id="e733e-124">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)  
 <span data-ttu-id="e733e-125"><xref:System.Linq.Enumerable.Concat%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-125">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-126">2 つのシーケンスの差集合の取得</span><span class="sxs-lookup"><span data-stu-id="e733e-126">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="e733e-127"><xref:System.Linq.Enumerable.Except%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-127">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-128">2 つのシーケンスの積集合の取得</span><span class="sxs-lookup"><span data-stu-id="e733e-128">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="e733e-129"><xref:System.Linq.Enumerable.Intersect%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-129">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-130">2 つのシーケンスの和集合の取得</span><span class="sxs-lookup"><span data-stu-id="e733e-130">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="e733e-131"><xref:System.Linq.Enumerable.Union%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-131">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-132">方法 : シーケンスを配列に変換する</span><span class="sxs-lookup"><span data-stu-id="e733e-132">Convert a Sequence to an Array</span></span>](convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="e733e-133"><xref:System.Linq.Enumerable.ToArray%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-133">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-134">ジェネリック リストへのシーケンスの変換</span><span class="sxs-lookup"><span data-stu-id="e733e-134">Convert a Sequence to a Generic List</span></span>](convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="e733e-135"><xref:System.Linq.Enumerable.ToList%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-135">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-136">汎用 IEnumerable への型の変換</span><span class="sxs-lookup"><span data-stu-id="e733e-136">Convert a Type to a Generic IEnumerable</span></span>](convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="e733e-137"><xref:System.Linq.Enumerable.AsEnumerable%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-137">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="e733e-138">結合およびクロス積クエリの作成</span><span class="sxs-lookup"><span data-stu-id="e733e-138">Formulate Joins and Cross-Product Queries</span></span>](formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="e733e-139">`from` 句、`where` 句、および `select` 句で外部キーを移動する方法の例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-139">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="e733e-140">射影の作成</span><span class="sxs-lookup"><span data-stu-id="e733e-140">Formulate Projections</span></span>](formulate-projections.md)  
 <span data-ttu-id="e733e-141">`select` と他の機能 (*匿名型* など) を組み合わせてクエリ射影を作成する方法の例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-141">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e733e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="e733e-142">Related Sections</span></span>  

 [<span data-ttu-id="e733e-143">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="e733e-143">Standard Query Operators Overview (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="e733e-144">C# を使用した標準クエリ演算子の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-144">Explains the concept of standard query operators using C#.</span></span>  
  
 [<span data-ttu-id="e733e-145">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e733e-145">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="e733e-146">Visual Basic を使用した標準クエリ演算子の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-146">Explains the concept of standard query operators using Visual Basic.</span></span>  
  
 [<span data-ttu-id="e733e-147">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="e733e-147">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="e733e-148">クエリに関する概念が [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でどのように使用されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="e733e-148">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="e733e-149">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e733e-149">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="e733e-150">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に関連するプログラミングの概念を説明するトピックへのポータルです。</span><span class="sxs-lookup"><span data-stu-id="e733e-150">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
