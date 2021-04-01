---
title: Descendants メソッドを使用して単一の子孫を検索する方法 - LINQ to XML
description: XContainer.Descendants 軸メソッドを使用し、一意の名前が付いた子孫要素を 1 つ検索します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 9065309822bfb7c46da556fcf9b3a3b48df16302
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411999"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-linq-to-xml"></a><span data-ttu-id="ed853-103">Descendants メソッドを使用して単一の子孫を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ed853-103">How to find a single descendant using the Descendants method (LINQ to XML)</span></span>

<span data-ttu-id="ed853-104"><xref:System.Xml.Linq.XContainer.Descendants%2A> 軸メソッドを使用し、一意の名前が付いた子孫要素を 1 つ検索できます。</span><span class="sxs-lookup"><span data-stu-id="ed853-104">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to find a single uniquely-named descendant element.</span></span> <span data-ttu-id="ed853-105">この手法は特に、特定の名前が付いた特定の子孫を見つけるときに役立ちます。XML ツリー内をあちこち移動するよりも検索が速く、簡単になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed853-105">This technique is especially useful when you want to find a particular descendant with a specific name, and may be faster and easier to use than navigating the XML tree.</span></span>

## <a name="example-use-xcontainerdescendants-to-find-a-single-uniquely-named-descendant-element"></a><span data-ttu-id="ed853-106">例: XContainer.Descendants 軸メソッドを使用し、一意の名前が付いた子孫要素を 1 つ検索する</span><span class="sxs-lookup"><span data-stu-id="ed853-106">Example: Use XContainer.Descendants to find a single uniquely-named descendant element</span></span>

<span data-ttu-id="ed853-107">この例では、<xref:System.Linq.Enumerable.First%2A> 標準クエリ演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="ed853-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <GrandChild1>GC1 Value</GrandChild1>
  </Child1>
  <Child2>
    <GrandChild2>GC2 Value</GrandChild2>
  </Child2>
  <Child3>
    <GrandChild3>GC3 Value</GrandChild3>
  </Child3>
  <Child4>
    <GrandChild4>GC4 Value</GrandChild4>
  </Child4>
</Root>");
string grandChild3 = (string)
    (from el in root.Descendants("GrandChild3")
    select el).First();
Console.WriteLine(grandChild3);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1>GC1 Value</GrandChild1>
        </Child1>
        <Child2>
            <GrandChild2>GC2 Value</GrandChild2>
        </Child2>
        <Child3>
            <GrandChild3>GC3 Value</GrandChild3>
        </Child3>
        <Child4>
            <GrandChild4>GC4 Value</GrandChild4>
        </Child4>
    </Root>
Dim grandChild3 As String = _
    (From el In root...<GrandChild3> _
    Select el).First()
Console.WriteLine(grandChild3)
```

<span data-ttu-id="ed853-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ed853-108">This example produces the following output:</span></span>

```output
GC3 Value
```

## <a name="example-find-when-the-xml-is-in-a-namespace"></a><span data-ttu-id="ed853-109">例: ある名前空間に XML が属する場合に検索する</span><span class="sxs-lookup"><span data-stu-id="ed853-109">Example: Find when the XML is in a namespace</span></span>

<span data-ttu-id="ed853-110">次の例のクエリは前のものと同じですが、ある名前空間に属する XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="ed853-110">The following example does the same as the previous one, but for XML that's  in a namespace.</span></span> <span data-ttu-id="ed853-111">詳細については、[名前空間の概要](namespaces-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed853-111">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
  <aw:Child1>
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
  </aw:Child1>
  <aw:Child2>
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
  </aw:Child2>
  <aw:Child3>
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
  </aw:Child3>
  <aw:Child4>
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
  </aw:Child4>
</aw:Root>");
XNamespace aw = "http://www.adventure-works.com";
string grandChild3 = (string)
    (from el in root.Descendants(aw + "GrandChild3")
     select el).First();
Console.WriteLine(grandChild3);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child1>
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>
                </aw:Child1>
                <aw:Child2>
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>
                </aw:Child2>
                <aw:Child3>
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>
                </aw:Child3>
                <aw:Child4>
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>
                </aw:Child4>
            </aw:Root>
        Dim grandChild3 As String = _
            (From el In root...<aw:GrandChild3> _
            Select el).First()
        Console.WriteLine(grandChild3)
    End Sub
End Module
```

<span data-ttu-id="ed853-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ed853-112">This example produces the following output:</span></span>

```output
GC3 Value
```
