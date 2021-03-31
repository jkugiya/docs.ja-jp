---
title: 直前の兄弟を検索する方法 - LINQ to XML
description: あるノードの直前に存在する兄弟を検索する方法について説明します。 2 つの方法を紹介します。1 つは XPathEvaluate を使用し、もう 1 つは LINQ to XML クエリを使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 9be39c20a99920482899efa934003957ffc696b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412122"
---
# <a name="how-to-find-the-immediate-preceding-sibling-linq-to-xml"></a><span data-ttu-id="c022c-104">直前の兄弟を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c022c-104">How to find the immediate preceding sibling (LINQ to XML)</span></span>

<span data-ttu-id="c022c-105">この記事では、<xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> を使用し、あるノードの直前に存在する兄弟を検索する方法と、LINQ to XML クエリを使用して同じことをする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c022c-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the sibling that immediately precedes a node, and how to use LINQ to XML query to do the same thing.</span></span> <span data-ttu-id="c022c-106">LINQ to XML とは対照的に、XPath では先行する兄弟軸の位置述語にはセマンティクス上の違いがあります。この相違点は、注目すべき特徴と言えます。</span><span class="sxs-lookup"><span data-stu-id="c022c-106">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to LINQ to XML, this is one of the more interesting comparisons.</span></span>

## <a name="example-find-the-next-to-last-element"></a><span data-ttu-id="c022c-107">例: 最終要素の 1 つ手前を検索する</span><span class="sxs-lookup"><span data-stu-id="c022c-107">Example: Find the next to last element</span></span>

<span data-ttu-id="c022c-108">この例では、LINQ to XML クエリは、<xref:System.Linq.Enumerable.Last%2A> 演算子を使用し、<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> から返されるコレクション内の最後のノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="c022c-108">In this example, the LINQ to XML query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="c022c-109">一方、XPath 式は、値が 1 の述語を使用して直前の要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="c022c-109">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

```csharp
XElement root = XElement.Parse(
    @"<Root>
    <Child1/>
    <Child2/>
    <Child3/>
    <Child4/>
</Root>");
XElement child4 = root.Element("Child4");

// LINQ to XML query
XElement el1 =
    child4
    .ElementsBeforeSelf()
    .Last();

// XPath expression
XElement el2 =
    ((IEnumerable)child4
                 .XPathEvaluate("preceding-sibling::*[1]"))
                 .Cast<XElement>()
                 .First();

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1/>
        <Child2/>
        <Child3/>
        <Child4/>
    </Root>
Dim child4 As XElement = root.Element("Child4")

' LINQ to XML query
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()

' XPath expression
Dim el2 As XElement = _
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _
    IEnumerable).Cast(Of XElement)().First()

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

<span data-ttu-id="c022c-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c022c-110">This example produces the following output:</span></span>

```output
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="c022c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c022c-111">See also</span></span>

- [<span data-ttu-id="c022c-112">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c022c-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
