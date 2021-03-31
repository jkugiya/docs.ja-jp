---
title: 標準クエリ演算子を連結する (C#) - LINQ to XML
description: クエリ演算子を連結する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: ed3ca44c853ebbeee690cb31232a13e35b383d1b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411950"
---
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a><span data-ttu-id="e2c8b-103">標準クエリ演算子を連結する (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e2c8b-103">Chain standard query operators together (C#) (LINQ to XML)</span></span>

<span data-ttu-id="e2c8b-104">標準クエリ演算子を連結できます。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-104">The standard query operators can be chained together.</span></span> <span data-ttu-id="e2c8b-105">たとえば、<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 演算子 (`where` 句によって呼び出される) を挿入すると、レイジー演算となります。つまり、中間的な成果が具体化されることがありません。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator (invoked by the `where` clause), and it operates in a lazy fashion; that is, no intermediate results are materialized by it.</span></span>

## <a name="example-interject-a-where-clause"></a><span data-ttu-id="e2c8b-106">例: where 句を挿入する</span><span class="sxs-lookup"><span data-stu-id="e2c8b-106">Example: Interject a where clause</span></span>

<span data-ttu-id="e2c8b-107">この例では、<xref:System.Linq.Enumerable.Where%2A> の前に `ConvertCollectionToUpperCase` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-107">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="e2c8b-108"><xref:System.Linq.Enumerable.Where%2A> メソッドは、このチュートリアルの前の例で使用したレイジー メソッド (`ConvertCollectionToUpperCase` および `AppendString`) とほぼ同様に動作しますが、この例では異なる点もあります。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-108">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>

<span data-ttu-id="e2c8b-109">異なる点とは、この場合の <xref:System.Linq.Enumerable.Where%2A> メソッドではソース コレクションを反復処理し、最初の項目を述語に渡さないことを決定してから、述語に渡す次の項目を取得します。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-109">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item doesn't pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="e2c8b-110">その後、2 番目の項目を生成します。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-110">It then yields the second item.</span></span>

<span data-ttu-id="e2c8b-111">ただし、基本的な考え方は同じです。つまり、中間コレクションは、必要がない限り具体化されません。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-111">However, the basic idea is the same: intermediate collections aren't materialized unless they have to be.</span></span>

<span data-ttu-id="e2c8b-112">クエリ式が使用されている場合、そのクエリ式は標準クエリ演算子への呼び出しに変換され、同じ原則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-112">When query expressions are used, they're converted to calls to the standard query operators, and the same principles apply.</span></span>

<span data-ttu-id="e2c8b-113">Office Open XML ドキュメントに対してクエリを実行するこのセクションの例はすべて、同じ原則を使用します。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-113">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="e2c8b-114">遅延実行およびレイジー評価は、LINQ (および LINQ to XML) を効果的に使用するために理解しておく必要がある基本的概念です。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-114">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand to use LINQ, and LINQ to XML, effectively.</span></span>

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source >{0}<", str);
            yield return str.ToUpper();
        }
    }

    public static IEnumerable<string>
      AppendString(this IEnumerable<string> source, string stringToAppend)
    {
        foreach (string str in source)
        {
            Console.WriteLine("AppendString: source >{0}<", str);
            yield return str + stringToAppend;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        IEnumerable<string> q1 =
            from s in stringArray.ConvertCollectionToUpperCase()
            where s.CompareTo("D") >= 0
            select s;

        IEnumerable<string> q2 =
            from s in q1.AppendString("!!!")
            select s;

        foreach (string str in q2)
        {
            Console.WriteLine("Main: str >{0}<", str);
            Console.WriteLine();
        }
    }
}
```

<span data-ttu-id="e2c8b-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-115">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="e2c8b-116">これは、「[チュートリアル: クエリを連結する (C#)](chain-queries-example.md)」の最後の記事です。</span><span class="sxs-lookup"><span data-stu-id="e2c8b-116">This is the final article in the [Tutorial: Chaining Queries Together (C#)](chain-queries-example.md) tutorial.</span></span>
