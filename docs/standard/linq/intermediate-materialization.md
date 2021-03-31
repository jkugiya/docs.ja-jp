---
title: 中間結果の具体化 (C#)
description: 一部の標準的クエリ演算子を使用すると、クエリ内でコレクションが具体化し、アプリケーションのメモリとパフォーマンス プロファイルが大幅に変更される可能性について説明します。
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 8dca4bb29886973762351049d06bcf5d3ba352db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411964"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="f900c-103">中間結果の具体化 (C#)</span><span class="sxs-lookup"><span data-stu-id="f900c-103">Intermediate materialization (C#)</span></span>

<span data-ttu-id="f900c-104">不注意なユーザーは、クエリ内でコレクションを早期に具体化して、アプリケーションのメモリおよびパフォーマンスのプロファイルを大幅に変更してしまうことがあります。</span><span class="sxs-lookup"><span data-stu-id="f900c-104">If you're not careful you can, in some situations, drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="f900c-105">一部の標準クエリ演算子では、単一の要素を生成する前に、ソース コレクションを具体化する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f900c-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="f900c-106">たとえば、<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> は最初にソース コレクション全体を反復処理し、次にすべての項目を並べ替えて、最後に最初の項目を生成します。</span><span class="sxs-lookup"><span data-stu-id="f900c-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="f900c-107">これは、順序付けられたコレクションの最初の項目の取得が高コストであることを意味しています。これ以降の各項目の取得は高コストではありません。</span><span class="sxs-lookup"><span data-stu-id="f900c-107">This means that it's expensive to get the first item of an ordered collection; each item thereafter isn't expensive.</span></span> <span data-ttu-id="f900c-108">このクエリ演算子は他の方法では処理を実行できないため、これは処理方法として適切なものです。</span><span class="sxs-lookup"><span data-stu-id="f900c-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>

## <a name="example-add-a-method-that-calls-tolist-causing-materialization"></a><span data-ttu-id="f900c-109">例: `ToList` を呼び出すメソッドを追加し、具体化を発生させる</span><span class="sxs-lookup"><span data-stu-id="f900c-109">Example: Add a method that calls `ToList`, causing materialization</span></span>

<span data-ttu-id="f900c-110">この例は、[クエリの連結の例 (C#)](chain-queries-example.md) に含まれる例を改変したものです。ソースを反復処理する前に <xref:System.Linq.Enumerable.ToList%2A> を呼び出すように `AppendString` メソッドが変更されています。それにより具体化が引き起こされます。</span><span class="sxs-lookup"><span data-stu-id="f900c-110">This example alters the example in [Chain queries example (C#)](chain-queries-example.md): the `AppendString` method is changed to call <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source, which causes materialization.</span></span>

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
        // the following statement materializes the source collection in a List<T>
        // before iterating through it
        foreach (string str in source.ToList())
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

 <span data-ttu-id="f900c-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f900c-111">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
ToUpper: source >ghi<
AppendString: source >ABC<
Main: str >ABC!!!<

AppendString: source >DEF<
Main: str >DEF!!!<

AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="f900c-112">この例では、<xref:System.Linq.Enumerable.ToList%2A> の呼び出しにより、`AppendString` が、最初の項目を生成する前にソース全体を列挙することがわかります。</span><span class="sxs-lookup"><span data-stu-id="f900c-112">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="f900c-113">ソースが大きな配列である場合は、これによってアプリケーションのメモリ プロファイルが大幅に変更されます。</span><span class="sxs-lookup"><span data-stu-id="f900c-113">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>

<span data-ttu-id="f900c-114">標準クエリ演算子は、このチュートリアルの最終記事で示されているように、連結することもできます。</span><span class="sxs-lookup"><span data-stu-id="f900c-114">Standard query operators can also be chained together as shown in the final article in this tutorial:</span></span>

- [<span data-ttu-id="f900c-115">標準クエリ演算子を連結する (C#)</span><span class="sxs-lookup"><span data-stu-id="f900c-115">Chain standard query operators together (C#)</span></span>](chain-standard-query-operators-together.md)

## <a name="see-also"></a><span data-ttu-id="f900c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f900c-116">See also</span></span>

- [<span data-ttu-id="f900c-117">遅延実行とレイジー評価</span><span class="sxs-lookup"><span data-stu-id="f900c-117">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
