---
title: 子要素の一覧を検索する方法 - LINQ to XML
description: この記事では、XPath の子要素軸と LINQ to XML の XContainer.Elements 軸を比較します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: c575df2e8caa2125091265c00557b91a24601e48
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412132"
---
# <a name="how-to-find-a-list-of-child-elements-linq-to-xml"></a><span data-ttu-id="ab994-103">子要素の一覧を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ab994-103">How to find a list of child elements (LINQ to XML)</span></span>

<span data-ttu-id="ab994-104">この記事では、XPath の子要素軸と LINQ to XML の <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を比較します。</span><span class="sxs-lookup"><span data-stu-id="ab994-104">This article compares the XPath child elements axis to the LINQ to XML <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>

## <a name="example-find-all-child-elements-of-an-element"></a><span data-ttu-id="ab994-105">例: ある要素のすべての子要素を検索する</span><span class="sxs-lookup"><span data-stu-id="ab994-105">Example: Find all child elements of an element</span></span>

<span data-ttu-id="ab994-106">この例では、XML ドキュメント「[サンプル XML ファイル: 複数の購買発注書](sample-xml-file-multiple-purchase-orders.md)」に含まれる `Address` 要素の子要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="ab994-106">This example finds all of the child elements of the `Address` element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="ab994-107">XPath 式は `./*` です。</span><span class="sxs-lookup"><span data-stu-id="ab994-107">The XPath expression is: `./*`</span></span>

```csharp
XDocument cpo = XDocument.Load("PurchaseOrders.xml");
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");

// LINQ to XML query
IEnumerable<XElement> list1 = po.Elements();

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = po.Elements()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")

If (list1.Count() = list2.Count()) AndAlso _
    (list1.Intersect(list2).Count() = list1.Count()) Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="ab994-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ab994-108">This example produces the following output:</span></span>

```output
Results are identical
<Name>Ellen Adams</Name>
<Street>123 Maple Street</Street>
<City>Mill Valley</City>
<State>CA</State>
<Zip>10999</Zip>
<Country>USA</Country>
```

## <a name="see-also"></a><span data-ttu-id="ab994-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab994-109">See also</span></span>

- [<span data-ttu-id="ab994-110">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab994-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
