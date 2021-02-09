---
description: '詳細情報: クエリ式の例 (LINQ to DataSet)'
title: クエリ式の例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
ms.openlocfilehash: 1d1571a851fae685942cbdbd557b275e86e8b0d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663691"
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="958a0-103">クエリ式の例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="958a0-103">Query Expression Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="958a0-104">このセクションでは、標準クエリ演算子を使用する LINQ to DataSet プログラミングの例を、クエリ式の構文を中心に説明します。</span><span class="sxs-lookup"><span data-stu-id="958a0-104">This section provides LINQ to DataSet programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="958a0-105">これらの例で使用されている <xref:System.Data.DataSet> は、`FillDataSet` メソッド (「[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)」を参照) を使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="958a0-105">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="958a0-106">詳しくは、「[標準クエリ演算子の概要 (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)」または「[標準クエリ演算子の概要 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958a0-106">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="958a0-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="958a0-107">In This Section</span></span>  

 [<span data-ttu-id="958a0-108">射影</span><span class="sxs-lookup"><span data-stu-id="958a0-108">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="958a0-109">このトピックでは、<xref:System.Linq.Enumerable.Select%2A> メソッドおよび <xref:System.Linq.Enumerable.SelectMany%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="958a0-109">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="958a0-110">制限</span><span class="sxs-lookup"><span data-stu-id="958a0-110">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="958a0-111">このトピックでは、<xref:System.Linq.Enumerable.Where%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="958a0-111">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="958a0-112">パーティション分割</span><span class="sxs-lookup"><span data-stu-id="958a0-112">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="958a0-113">このトピックでは、<xref:System.Linq.Enumerable.Skip%2A> メソッドおよび <xref:System.Linq.Enumerable.Take%2A> メソッドを使って <xref:System.Data.DataSet> を照会し、結果をパーティション分割する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="958a0-113">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="958a0-114">順序付け</span><span class="sxs-lookup"><span data-stu-id="958a0-114">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="958a0-115">このトピックでは、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A>、<xref:System.Linq.Enumerable.ThenByDescending%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、結果を並べ替える例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="958a0-115">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="958a0-116">要素演算子</span><span class="sxs-lookup"><span data-stu-id="958a0-116">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="958a0-117">このトピックでは、<xref:System.Linq.Enumerable.First%2A> メソッドおよび <xref:System.Linq.Enumerable.ElementAt%2A> メソッドを使用して <xref:System.Data.DataRow> から <xref:System.Data.DataSet> 要素を取得する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="958a0-117">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="958a0-118">集計演算子</span><span class="sxs-lookup"><span data-stu-id="958a0-118">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="958a0-119">このトピックでは、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Sum%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、データを集計する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="958a0-119">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="958a0-120">結合演算子</span><span class="sxs-lookup"><span data-stu-id="958a0-120">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="958a0-121">このトピックでは、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッドおよび <xref:System.Linq.Enumerable.Join%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="958a0-121">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958a0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="958a0-122">See also</span></span>

- [<span data-ttu-id="958a0-123">メソッド ベースのクエリ例</span><span class="sxs-lookup"><span data-stu-id="958a0-123">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)
- [<span data-ttu-id="958a0-124">DataSet 固有の演算子の例</span><span class="sxs-lookup"><span data-stu-id="958a0-124">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="958a0-125">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="958a0-125">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
