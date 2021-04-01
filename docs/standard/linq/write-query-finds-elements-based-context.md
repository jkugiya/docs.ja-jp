---
title: コンテキストに基づいて要素を検索するクエリを記述する方法 - LINQ to XML
description: コンテキストに基づいて要素を選択するクエリを記述します。たとえば、先行または後続の兄弟要素に基づいて結果をフィルタリングします。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 2c51a790a2a8adef565f186992a6a3faa5f102ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103366026"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-linq-to-xml"></a><span data-ttu-id="7426a-103">コンテキストに基づいて要素を検索するクエリを記述する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7426a-103">How to write a query that finds elements based on context (LINQ to XML)</span></span>

<span data-ttu-id="7426a-104">コンテキストに基づいて要素を選択するクエリの記述が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7426a-104">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="7426a-105">たとえば、先行または後続の兄弟要素、子要素、先祖要素に基づいて結果をフィルタリングすると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7426a-105">For example, you might want to filter based on preceding or following sibling elements, or on child or ancestor elements.</span></span>

<span data-ttu-id="7426a-106">これを実現するには、クエリを記述し、そのクエリの結果を `where` 句で使用します。</span><span class="sxs-lookup"><span data-stu-id="7426a-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="7426a-107">最初に NULL に対してテストし、次に値をテストする必要がある場合は、`let` 句でクエリを実行し、次にその結果を `where` 句で使用する方が便利です。</span><span class="sxs-lookup"><span data-stu-id="7426a-107">If you have to first test against null, and then test the value, it's more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>

## <a name="example-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a><span data-ttu-id="7426a-108">例: 直後に `ul` 要素が続く `p` 要素を選択する</span><span class="sxs-lookup"><span data-stu-id="7426a-108">Example: Select `p` elements that are immediately followed by a `ul` element</span></span>

<span data-ttu-id="7426a-109">次の例では、`p` 要素の直前の `ul` 要素をすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="7426a-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>

```csharp
XElement doc = XElement.Parse(@"<Root>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

IEnumerable<XElement> items =
    from e in doc.Descendants("p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name.LocalName == "ul"
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Dim doc As XElement = _
    <Root>
        <p id='1'/>
        <ul>abc</ul>
        <Child>
            <p id='2'/>
            <notul/>
            <p id='3'/>
            <ul>def</ul>
            <p id='4'/>
        </Child>
        <Child>
            <p id='5'/>
            <notul/>
            <p id='6'/>
            <ul>abc</ul>
            <p id='7'/>
        </Child>
    </Root>

Dim items As IEnumerable(Of XElement) = _
    From e In doc...<p> _
    Let z = e.ElementsAfterSelf().FirstOrDefault() _
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _
    Select e

For Each e As XElement In items
    Console.WriteLine("id = {0}", e.@<id>)
Next
```

<span data-ttu-id="7426a-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7426a-110">This example produces the following output:</span></span>

```output
id = 1
id = 3
id = 6
```

## <a name="example-in-a-namespace-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a><span data-ttu-id="7426a-111">例: ある名前空間で、直後に `ul` 要素が続く `p` 要素を選択する</span><span class="sxs-lookup"><span data-stu-id="7426a-111">Example: In a namespace select `p` elements that are immediately followed by a `ul` element</span></span>

<span data-ttu-id="7426a-112">次の例のクエリは上のものと同じですが、ある名前空間に属する XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="7426a-112">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="7426a-113">詳細については、[名前空間の概要](namespaces-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7426a-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

XNamespace ad = "http://www.adatum.com";

IEnumerable<XElement> items =
    from e in doc.Descendants(ad + "p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name == ad.GetName("ul")
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim doc As XElement = _
            <Root>
                <p id='1'/>
                <ul>abc</ul>
                <Child>
                    <p id='2'/>
                    <notul/>
                    <p id='3'/>
                    <ul>def</ul>
                    <p id='4'/>
                </Child>
                <Child>
                    <p id='5'/>
                    <notul/>
                    <p id='6'/>
                    <ul>abc</ul>
                    <p id='7'/>
                </Child>
            </Root>

        Dim items As IEnumerable(Of XElement) = _
            From e In doc...<p> _
            Let z = e.ElementsAfterSelf().FirstOrDefault() _
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _
            Select e

        For Each e As XElement In items
            Console.WriteLine("id = {0}", e.@<id>)
        Next
    End Sub
End Module
```

<span data-ttu-id="7426a-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7426a-114">This example produces the following output:</span></span>

```output
id = 1
id = 3
id = 6
```

## <a name="see-also"></a><span data-ttu-id="7426a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7426a-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="7426a-116">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7426a-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
