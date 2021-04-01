---
title: 兄弟ノードを検索する方法 - LINQ to XML
description: 特定の名前を持つノードのすべての兄弟を検索する方法について説明します。 2 つの方法を紹介します。1 つは XPathSelectElements を使用し、もう 1 つは LINQ to XML クエリを使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 56833ef3758a6d8af1eb6f0a103b85ad967c9aad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412142"
---
# <a name="how-to-find-sibling-nodes-linq-to-xml"></a><span data-ttu-id="fc8ed-104">兄弟ノードを検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fc8ed-104">How to find sibling nodes (LINQ to XML)</span></span>

<span data-ttu-id="fc8ed-105">この記事では、<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用し、特定の名前を持つノードの兄弟をすべて検索する方法と、LINQ to XML クエリを使用して同じことをする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find all siblings of a node that have a specific name, and how to use LINQ to XML query to do the same thing.</span></span>

> [!NOTE]
> <span data-ttu-id="fc8ed-106">コンテキスト ノードにも特定の名前が含まれる場合、結果的に生成されるコレクションにはコンテキスト ノードも含まれます。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-106">The resulting collection includes the context node if it also has the specific name.</span></span>

## <a name="example-find-an-element-named-book-and-all-sibling-elements-named-book"></a><span data-ttu-id="fc8ed-107">例: `Book` という名前の要素と `Book` という名前のすべての兄弟要素を検索する</span><span class="sxs-lookup"><span data-stu-id="fc8ed-107">Example: Find an element named `Book`, and all sibling elements named `Book`</span></span>

<span data-ttu-id="fc8ed-108">この例ではまず、XML ドキュメント「[サンプル XML ファイル : 書籍](sample-xml-file-books.md)」に含まれる `Book` 要素を検索し、それから `Book` という名前の兄弟要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-108">This example first finds a `Book` element in XML document [Sample XML file: Books](sample-xml-file-books.md), and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="fc8ed-109">結果のコレクションにはコンテキスト ノードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-109">The resulting collection includes the context node.</span></span>

<span data-ttu-id="fc8ed-110">XPath 式は `../Book` です。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-110">The XPath expression is `../Book`</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Elements("Book")
    .Skip(1)
    .First();

// LINQ to XML query
IEnumerable<XElement> list1 =
    book
    .Parent
    .Elements("Book");

// XPath expression
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>.Skip(1).First()

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")

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

<span data-ttu-id="fc8ed-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc8ed-111">This example produces the following output:</span></span>

```output
Results are identical
<Book id="bk101">
  <Author>Garghentini, Davide</Author>
  <Title>XML Developer's Guide</Title>
  <Genre>Computer</Genre>
  <Price>44.95</Price>
  <PublishDate>2000-10-01</PublishDate>
  <Description>An in-depth look at creating applications
      with XML.</Description>
</Book>
<Book id="bk102">
  <Author>Garcia, Debra</Author>
  <Title>Midnight Rain</Title>
  <Genre>Fantasy</Genre>
  <Price>5.95</Price>
  <PublishDate>2000-12-16</PublishDate>
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
</Book>
```

## <a name="see-also"></a><span data-ttu-id="fc8ed-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc8ed-112">See also</span></span>

- [<span data-ttu-id="fc8ed-113">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc8ed-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
