---
title: 2 つのロケーション パスの和集合を検索する方法 - LINQ to XML
description: 2 つの XPath ロケーション パスの結果の和集合を検索できます。 2 つの方法を紹介します。1 つは XPathSelectElements を使用し、もう 1 つは Concat 標準クエリ演算子を使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 13d1a22d933d789f28efa2d196fc0106986caa90
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412140"
---
# <a name="how-to-find-a-union-of-two-location-paths-linq-to-xml"></a><span data-ttu-id="b9eca-104">2 つのロケーション パスの和集合を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b9eca-104">How to find a union of two location paths (LINQ to XML)</span></span>

<span data-ttu-id="b9eca-105">この記事では、<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用して 2 つの XPath ロケーション パスの結果の和集合を検索する方法と、<xref:System.Linq.Enumerable.Concat%2A> 標準クエリ演算子を使用して同じことをする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="b9eca-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find the union of the results of two XPath location paths, and how to use the <xref:System.Linq.Enumerable.Concat%2A> standard query operator to do the same thing.</span></span>

## <a name="example-find-all-category-and-price-elements-and-concatenate-them"></a><span data-ttu-id="b9eca-106">例: `Category` 要素と `Price` 要素をすべて見つけ、それらを連結する</span><span class="sxs-lookup"><span data-stu-id="b9eca-106">Example: Find all `Category` and `Price` elements and concatenate them</span></span>

<span data-ttu-id="b9eca-107">この例では、XML ドキュメント「[サンプル XML ファイル: 数値データ](sample-xml-file-numerical-data.md)」に含まれる `Category` 要素と `Price` 要素をすべて見つけ、連結して 1 つのコレクションを生成します。</span><span class="sxs-lookup"><span data-stu-id="b9eca-107">This example finds all of the `Category` elements and all of the `Price` elements in XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md), and concatenates them into a single collection.</span></span> <span data-ttu-id="b9eca-108">XPath 式は `//Category|//Price` です。</span><span class="sxs-lookup"><span data-stu-id="b9eca-108">The XPath expression is `//Category|//Price`.</span></span>

> [!NOTE]
> <span data-ttu-id="b9eca-109">LINQ to XML クエリでは <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> が呼び出され、結果がドキュメント順に配置されます。</span><span class="sxs-lookup"><span data-stu-id="b9eca-109">The LINQ to XML query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to put the results in document order.</span></span> <span data-ttu-id="b9eca-110">XPath 式の結果もドキュメント順になります。</span><span class="sxs-lookup"><span data-stu-id="b9eca-110">The XPath expression results are also in document order.</span></span>

```csharp
XDocument data = XDocument.Load("Data.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    data
    .Descendants("Category")
    .Concat(
        data
        .Descendants("Price")
    )
    .InDocumentOrder();

// XPath expression
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim data As XDocument = XDocument.Load("Data.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    data...<Category>.Concat(data...<Price>).InDocumentOrder()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = _
    data.XPathSelectElements("//Category|//Price")

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

<span data-ttu-id="b9eca-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b9eca-111">This example produces the following output:</span></span>

```output
Results are identical
<Category>A</Category>
<Price>24.50</Price>
<Category>B</Category>
<Price>89.99</Price>
<Category>A</Category>
<Price>4.95</Price>
<Category>A</Category>
<Price>66.00</Price>
<Category>B</Category>
<Price>.99</Price>
<Category>A</Category>
<Price>29.00</Price>
<Category>B</Category>
<Price>6.99</Price>
```

## <a name="see-also"></a><span data-ttu-id="b9eca-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9eca-112">See also</span></span>

- [<span data-ttu-id="b9eca-113">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9eca-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
