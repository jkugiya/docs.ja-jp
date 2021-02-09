---
description: '詳細情報: 集計クエリ'
title: 集計クエリ
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 2b9b71440c804740e2f04d5b2dc8c2cd111634b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712832"
---
# <a name="aggregate-queries"></a><span data-ttu-id="75764-103">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="75764-103">Aggregate Queries</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="75764-104">は、`Average`、`Count`、`Max`、`Min`、および `Sum` の各集計演算子をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="75764-104">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="75764-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の集計演算子には、次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="75764-105">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="75764-106">集計クエリは直ちに実行されます。</span><span class="sxs-lookup"><span data-stu-id="75764-106">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="75764-107">詳細については、「[LINQ クエリの概要 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75764-107">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="75764-108">通常、集計クエリはコレクションではなく 1 つの数値を返します。</span><span class="sxs-lookup"><span data-stu-id="75764-108">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="75764-109">詳しくは、「[集計操作](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75764-109">For more information, see [Aggregation Operations](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="75764-110">匿名型に対して集計を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="75764-110">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="75764-111">以下のトピックの例は、Northwind サンプル データベースから派生しています。</span><span class="sxs-lookup"><span data-stu-id="75764-111">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="75764-112">詳細については、「[サンプル データベースのダウンロード](downloading-sample-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75764-112">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75764-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="75764-113">In This Section</span></span>  

 [<span data-ttu-id="75764-114">一連の数値の平均値の取得</span><span class="sxs-lookup"><span data-stu-id="75764-114">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="75764-115"><xref:System.Linq.Enumerable.Average%2A> 演算子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75764-115">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="75764-116">シーケンス内の要素数のカウント</span><span class="sxs-lookup"><span data-stu-id="75764-116">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="75764-117"><xref:System.Linq.Enumerable.Count%2A> 演算子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75764-117">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="75764-118">一連の数値の中の最大値の検出</span><span class="sxs-lookup"><span data-stu-id="75764-118">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="75764-119"><xref:System.Linq.Enumerable.Max%2A> 演算子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75764-119">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="75764-120">一連の数値の中の最小値の検出</span><span class="sxs-lookup"><span data-stu-id="75764-120">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="75764-121"><xref:System.Linq.Enumerable.Min%2A> 演算子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75764-121">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="75764-122">数値のシーケンスの合計の計算</span><span class="sxs-lookup"><span data-stu-id="75764-122">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="75764-123"><xref:System.Linq.Enumerable.Sum%2A> 演算子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75764-123">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="75764-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="75764-124">Related Sections</span></span>  

 [<span data-ttu-id="75764-125">クエリの例</span><span class="sxs-lookup"><span data-stu-id="75764-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="75764-126">Visual Basic および C# の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリに関するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="75764-126">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="75764-127">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="75764-127">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="75764-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での LINQ クエリの設計に関する概念について説明するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="75764-128">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="75764-129">LINQ クエリの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="75764-129">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="75764-130">LINQ でクエリが動作するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="75764-130">Explains how queries work in LINQ.</span></span>
