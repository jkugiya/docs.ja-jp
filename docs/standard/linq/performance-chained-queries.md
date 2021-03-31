---
title: 連結クエリのパフォーマンス - LINQ to XML
description: 複雑で大きな単一クエリと同様のパフォーマンスを発揮する連結クエリについて説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: c1dae1eaf008a1f17c6884ef6b8e67d042719ad9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411988"
---
# <a name="performance-of-chained-queries-linq-to-xml"></a><span data-ttu-id="a2640-103">連結クエリのパフォーマンス (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a2640-103">Performance of chained queries (LINQ to XML)</span></span>

<span data-ttu-id="a2640-104">LINQ (および LINQ to XML) の重要な利点の 1 つは、連結クエリがそれより大きく複雑な単一クエリと同様のパフォーマンスを発揮できるという点です。</span><span class="sxs-lookup"><span data-stu-id="a2640-104">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single query that is larger and more complicated than the chained queries.</span></span>

<span data-ttu-id="a2640-105">連結クエリとは、別のクエリをソースとして使用するクエリです。</span><span class="sxs-lookup"><span data-stu-id="a2640-105">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="a2640-106">たとえば、次の単純なコードでは、`query2` のソースとして `query1` があります。</span><span class="sxs-lookup"><span data-stu-id="a2640-106">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="a2640-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2640-107">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="a2640-108">この連結クエリは、リンク リストの反復と同じパフォーマンス プロファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="a2640-108">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="a2640-109"><xref:System.Xml.Linq.XContainer.Elements%2A> 軸のパフォーマンスは、基本的にリンク リストの反復と同じです。</span><span class="sxs-lookup"><span data-stu-id="a2640-109">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="a2640-110"><xref:System.Xml.Linq.XContainer.Elements%2A> は、遅延実行のある反復子として実装されます。</span><span class="sxs-lookup"><span data-stu-id="a2640-110"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="a2640-111">つまり、リンク リストの反復の他に、反復子オブジェクトの割り当てや実行状態の追跡などの作業をします。</span><span class="sxs-lookup"><span data-stu-id="a2640-111">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="a2640-112">この作業は、反復子の設定時に行われる作業と、各反復中に行われる作業の 2 つのカテゴリに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="a2640-112">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="a2640-113">設定作業は一定量の小さい作業であり、各反復中に行われる作業はソース コレクションの項目数に比例します。</span><span class="sxs-lookup"><span data-stu-id="a2640-113">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>
- <span data-ttu-id="a2640-114">`query1` では、`where` 句 (Visual Basic の場合は `Where`) によってクエリは <xref:System.Linq.Enumerable.Where%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a2640-114">In `query1`, the `where` clause (`Where` in Visual Basic) causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="a2640-115">このメソッドも反復子として実装されています。</span><span class="sxs-lookup"><span data-stu-id="a2640-115">This method is also implemented as an iterator.</span></span> <span data-ttu-id="a2640-116">設定作業は、ラムダ式を参照するデリゲートのインスタンス化と、反復子の通常の設定から成ります。</span><span class="sxs-lookup"><span data-stu-id="a2640-116">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="a2640-117">反復ごとに、デリゲートが呼び出されて述語を実行します。</span><span class="sxs-lookup"><span data-stu-id="a2640-117">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="a2640-118">設定作業と、各反復中に行われる作業は、軸の反復中に行われる作業に似ています。</span><span class="sxs-lookup"><span data-stu-id="a2640-118">The setup work and the work done during each iteration is similar to the work done while iterating through the axis.</span></span>
- <span data-ttu-id="a2640-119">`query1` では、SELECT 句によってクエリが <xref:System.Linq.Enumerable.Select%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a2640-119">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="a2640-120">このメソッドには <xref:System.Linq.Enumerable.Where%2A> メソッドと同じパフォーマンス プロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="a2640-120">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>
- <span data-ttu-id="a2640-121">`query2` では、`where` 句 (Visual Basic の場合は `Where`)と `select` 句の両方に `query1` と同じパフォーマンス プロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="a2640-121">In `query2`, both the `where` clause (`Where` in Visual Basic) and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="a2640-122">したがって、`query2` の反復は最初のクエリのソースにある項目数に直接比例します。つまり線形時間となります。</span><span class="sxs-lookup"><span data-stu-id="a2640-122">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

<span data-ttu-id="a2640-123">反復子の詳細については、「[yield](../../csharp/language-reference/keywords/yield.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2640-123">For more information on iterators, see [yield](../../csharp/language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="a2640-124">クエリの連結に関する詳細なチュートリアルについては、「[チュートリアル: クエリを連結する (C#)](chain-queries-example.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2640-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chain queries together (C#)](chain-queries-example.md).</span></span>
