---
title: 特定の属性を持つ要素を検索する方法 - LINQ to XML
description: (値に関係なく) 特定の属性を持つすべての要素を検索する方法について説明します。 2 つの方法を紹介します。1 つは XPathEvaluate を使用し、もう 1 つは LINQ to XML クエリを使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: 2a747e7609e2b130249a7635d8448577d035f939
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412123"
---
# <a name="how-to-find-elements-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="ae941-104">特定の属性を持つ要素を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ae941-104">How to find elements with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="ae941-105">この記事では、<xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> を使用して (値に関係なく) 特定の属性を持つすべての要素を検索する方法と、LINQ to XML クエリを使用して同じことを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae941-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find all elements that have a specific attribute (regardless of value), and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-all-elements-that-have-the-select-attribute"></a><span data-ttu-id="ae941-106">例: `Select` 属性を持つすべての要素を検索する</span><span class="sxs-lookup"><span data-stu-id="ae941-106">Example: Find all elements that have the `Select` attribute</span></span>

<span data-ttu-id="ae941-107">次の例では、XML ツリーを作成し、`Select` 属性を持つ要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="ae941-107">The following example creates an XML tree and then finds the elements that have the `Select` attribute.</span></span>

<span data-ttu-id="ae941-108">XPath 式は `./*[@Select]` です。</span><span class="sxs-lookup"><span data-stu-id="ae941-108">The XPath expression is `./*[@Select]`.</span></span>

```csharp
XElement doc = XElement.Parse(
@"<Root>
    <Child1>1</Child1>
    <Child2 Select='true'>2</Child2>
    <Child3>3</Child3>
    <Child4 Select='true'>4</Child4>
    <Child5>5</Child5>
</Root>");

// LINQ to XML query
IEnumerable<XElement> list1 =
    from el in doc.Elements()
    where el.Attribute("Select") != null
    select el;

// XPath expression
IEnumerable<XElement> list2 =
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim doc As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child2 Select='true'>2</Child2>
        <Child3>3</Child3>
        <Child4 Select='true'>4</Child4>
        <Child5>5</Child5>
    </Root>

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    From el In doc.Elements() _
    Where el.@Select <> Nothing _
    Select el

' XPath expression
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()

If list1.Count() = list2.Count() And _
    list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="ae941-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ae941-109">This example produces the following output:</span></span>

```output
Results are identical
<Child2 Select="true">2</Child2>
<Child4 Select="true">4</Child4>
```

## <a name="see-also"></a><span data-ttu-id="ae941-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae941-110">See also</span></span>

- [<span data-ttu-id="ae941-111">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae941-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
