---
title: 親の属性を検索する方法 - LINQ to XML
description: ある要素に移動し、その親の属性を検索する方法について説明します。 2 つの方法を紹介します。1 つは XPathEvaluate を使用し、もう 1 つは LINQ to XML クエリを使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6d5d1ce768f91aa6e32bf09668bad66f3c4f2334
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412144"
---
# <a name="how-to-find-an-attribute-of-the-parent-linq-to-xml"></a><span data-ttu-id="d5d3f-104">親の属性を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d5d3f-104">How to find an attribute of the parent (LINQ to XML)</span></span>

<span data-ttu-id="d5d3f-105">この記事では、<xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> を使用して親要素の属性を検索する方法と、LINQ to XML クエリを使用して同じことをする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="d5d3f-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find an attribute of a parent element, and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-the-author-element-and-then-find-the-id-attribute-of-its-parent"></a><span data-ttu-id="d5d3f-106">例: `Author` 要素を検索し、その親の `id` 属性を検索します。</span><span class="sxs-lookup"><span data-stu-id="d5d3f-106">Example: Find the `Author` element, and then find the `id` attribute of its parent</span></span>

<span data-ttu-id="d5d3f-107">この例ではまず、XML ドキュメント「[サンプル XML ファイル : 書籍](sample-xml-file-books.md)」に含まれる `Author` 要素を検索し、それからその親要素の `id` 属性を検索します。</span><span class="sxs-lookup"><span data-stu-id="d5d3f-107">This example first finds an `Author` element in XML document [Sample XML file: Books](sample-xml-file-books.md), and then finds the `id` attribute of its parent element.</span></span>

<span data-ttu-id="d5d3f-108">XPath 式は `../@id` です。</span><span class="sxs-lookup"><span data-stu-id="d5d3f-108">The XPath expression is `../@id`.</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()

' LINQ to XML query
Dim att1 As XAttribute = author.Parent.Attribute("id")

' XPath expression
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _
    IEnumerable).Cast(Of XAttribute)().First()

If att1 Is att2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(att1)
```

<span data-ttu-id="d5d3f-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d5d3f-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```

## <a name="see-also"></a><span data-ttu-id="d5d3f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5d3f-110">See also</span></span>

- [<span data-ttu-id="d5d3f-111">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5d3f-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
