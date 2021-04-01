---
title: 遅延実行の例 - LINQ to XML
description: 遅延実行とレイジー評価が LINQ to XML クエリの実行にどのように影響するかについて説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 59784db895211aecbd263b5ee050734ecd16fa4b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366005"
---
# <a name="deferred-execution-example-linq-to-xml"></a><span data-ttu-id="53c97-103">遅延実行の例 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="53c97-103">Deferred execution example (LINQ to XML)</span></span>

<span data-ttu-id="53c97-104">この記事では、遅延実行とレイジー評価が LINQ to XML クエリの実行にどのように影響するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="53c97-104">This article shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example-use-the-yield-return-construct-in-an-extension-method-to-defer-execution"></a><span data-ttu-id="53c97-105">例: 拡張メソッドで `yield return` コンストラクトを使用して実行を遅延する</span><span class="sxs-lookup"><span data-stu-id="53c97-105">Example: Use the `yield return` construct in an extension method to defer execution</span></span>

<span data-ttu-id="53c97-106">遅延実行を利用する拡張メソッドの使用時における実行順序の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="53c97-106">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="53c97-107">この例では、3 つの文字列の配列を宣言します。</span><span class="sxs-lookup"><span data-stu-id="53c97-107">The example declares an array of three strings.</span></span> <span data-ttu-id="53c97-108">次に、`ConvertCollectionToUpperCase` によって返されるコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="53c97-108">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source {0}", str);
            yield return str.ToUpper();
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        var q = from str in stringArray.ConvertCollectionToUpperCase()
                select str;

        foreach (string str in q)
            Console.WriteLine("Main: str {0}", str);
    }
}
```

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

<span data-ttu-id="53c97-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="53c97-109">This example produces the following output:</span></span>

```output
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="53c97-110">`ConvertCollectionToUpperCase` によって返されるコレクションの反復処理時、各アイテムはソース文字列の配列から取得され、次のアイテムがソース文字列の配列から取得される前に大文字に変換されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="53c97-110">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="53c97-111">返されるコレクションの各アイテムが `foreach` の `Main` ループで処理されるまで、文字列の配列全体は大文字に変換されないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="53c97-111">You can see that the entire array of strings isn't converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="53c97-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="53c97-112">See also</span></span>

- [<span data-ttu-id="53c97-113">遅延実行とレイジー評価</span><span class="sxs-lookup"><span data-stu-id="53c97-113">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
- [<span data-ttu-id="53c97-114">チュートリアル: クエリを連結する (C#)</span><span class="sxs-lookup"><span data-stu-id="53c97-114">Tutorial: Chain queries together (C#)</span></span>](chain-queries-example.md)
