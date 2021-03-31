---
title: 遅延実行とレイジー評価 - LINQ to XML
description: 遅延実行の長所と要件、およびクエリと軸を操作してそれを実装する方法について説明します。
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 21b1c7b7d54e7f787919f1e1601fc36bc8c1caff
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411953"
---
# <a name="deferred-execution-and-lazy-evaluation-linq-to-xml"></a><span data-ttu-id="c1d57-103">遅延実行とレイジー評価 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c1d57-103">Deferred execution and lazy evaluation (LINQ to XML)</span></span>

<span data-ttu-id="c1d57-104">クエリと軸の操作は、多くの場合、遅延実行を使用するように実装されています。</span><span class="sxs-lookup"><span data-stu-id="c1d57-104">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="c1d57-105">この記事では、遅延実行の要件と利点、および実装に関する注意点について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1d57-105">This article explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>

## <a name="deferred-execution"></a><span data-ttu-id="c1d57-106">遅延実行</span><span class="sxs-lookup"><span data-stu-id="c1d57-106">Deferred execution</span></span>

<span data-ttu-id="c1d57-107">遅延実行とは、"*具体*" 値が実際に必要となるまで、式の評価を遅らせることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c1d57-107">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="c1d57-108">大きなデータ コレクションの操作が必要な場合、特に連結されたクエリや操作が含まれているプログラムでは、遅延実行によってパフォーマンスが大幅に向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="c1d57-108">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="c1d57-109">最も効果的なケースでは、遅延実行を使用することによって、ソース コレクションの繰り返し処理を 1 度行うだけで済むようになります。</span><span class="sxs-lookup"><span data-stu-id="c1d57-109">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>

<span data-ttu-id="c1d57-110">LINQ テクノロジでは、コア <xref:System.Linq?displayProperty=nameWithType> クラスのメンバーにおいても、<xref:System.Xml.Linq.Extensions?displayProperty=nameWithType> などのさまざまな LINQ 名前空間の拡張メソッドにおいても、遅延実行が広く利用されています。</span><span class="sxs-lookup"><span data-stu-id="c1d57-110">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c1d57-111">C# 言語では、反復子ブロック内で [yield (C# リファレンス)](../../csharp/language-reference/keywords/yield.md) キーワード (`yield-return` ステートメントの形式) を使用することにより、遅延実行が直接サポートされます。</span><span class="sxs-lookup"><span data-stu-id="c1d57-111">Deferred execution is supported directly in the C# language by the [yield (C# Reference)](../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="c1d57-112">このような反復子は <xref:System.Collections.IEnumerator> 型または <xref:System.Collections.Generic.IEnumerator%601> 型 (または派生型) のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="c1d57-112">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>

## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="c1d57-113">集中評価とレイジー評価</span><span class="sxs-lookup"><span data-stu-id="c1d57-113">Eager vs. lazy evaluation</span></span>

<span data-ttu-id="c1d57-114">遅延実行を実装するメソッドを記述するときは、レイジー評価と集中評価のどちらを使用してメソッドを実装するかについても決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1d57-114">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>

- <span data-ttu-id="c1d57-115">"*レイジー評価*" では、反復子を呼び出すたびに、ソース コレクションの 1 つの要素が処理されます。</span><span class="sxs-lookup"><span data-stu-id="c1d57-115">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="c1d57-116">これが、一般的な反復子の実装方法です。</span><span class="sxs-lookup"><span data-stu-id="c1d57-116">This is the typical way in which iterators are implemented.</span></span>
- <span data-ttu-id="c1d57-117">"*集中評価*" では、反復子への最初の呼び出しの結果として、コレクション全体が処理されます。</span><span class="sxs-lookup"><span data-stu-id="c1d57-117">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="c1d57-118">ソース コレクションの一時的なコピーが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c1d57-118">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="c1d57-119">たとえば <xref:System.Linq.Enumerable.OrderBy%2A> メソッドでは、最初の要素を返す前に、コレクション全体を並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1d57-119">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>

<span data-ttu-id="c1d57-120">通常は、レイジー評価を使用するとパフォーマンスが向上します。コレクション評価時のオーバーヘッド処理が均等に分散され、一時データの使用が最小限に抑えられるためです。</span><span class="sxs-lookup"><span data-stu-id="c1d57-120">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="c1d57-121">もちろん、操作によっては、中間結果を具体化するより他に方法がない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c1d57-121">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>

<span data-ttu-id="c1d57-122">C# と Visual Basic で遅延実行をプログラミングする例については、「[遅延実行の例](deferred-execution-example.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1d57-122">See [Deferred execution example](deferred-execution-example.md) for an example of programming deferred execution in C# and Visual Basic.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1d57-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1d57-123">See also</span></span>

- [<span data-ttu-id="c1d57-124">チュートリアル: C# のクエリの連結</span><span class="sxs-lookup"><span data-stu-id="c1d57-124">Tutorial: Chain Queries Together in C#</span></span>](chain-queries-example.md)
- [<span data-ttu-id="c1d57-125">概念と用語 (関数型変換)</span><span class="sxs-lookup"><span data-stu-id="c1d57-125">Concepts and terminology (functional transformation)</span></span>](concepts-terminology-functional-transformation.md)
- [<span data-ttu-id="c1d57-126">集計操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="c1d57-126">Aggregation Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [<span data-ttu-id="c1d57-127">集計操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1d57-127">Aggregation Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
- [<span data-ttu-id="c1d57-128">yield (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c1d57-128">yield (C# Reference)</span></span>](../../csharp/language-reference/keywords/yield.md)
