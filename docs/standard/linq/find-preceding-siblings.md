---
title: 先行する兄弟を検索する方法 - LINQ to XML
description: 特定の要素の前にある兄弟要素を検索する方法について説明します。 2 つの方法を紹介します。1 つは先行する兄弟軸に沿って XPath を使用し、もう 1 つは XNode.ElementsBeforeSelf を使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 0cfd516f274eaf2940a7b944d34c6ea494e7eaa1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412126"
---
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a><span data-ttu-id="98bd4-104">先行する兄弟を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="98bd4-104">How to find preceding siblings (LINQ to XML)</span></span>

<span data-ttu-id="98bd4-105">この記事では、先行する兄弟軸に沿って <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用し、特定の要素の前にある兄弟要素を検索する方法と、<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> を使用して同じ要素を検索する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="98bd4-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> along the preceding-sibling axis to find sibling elements that precede a given element, and how to use <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> to find the same elements.</span></span>

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a><span data-ttu-id="98bd4-106">例: ある要素の前に存在する兄弟要素を 2 とおりの方法で検索する</span><span class="sxs-lookup"><span data-stu-id="98bd4-106">Example: Use two methods to find sibling elements that precede an element</span></span>

<span data-ttu-id="98bd4-107">次の例では、XML ドキュメント「[サンプル XML ファイル: 顧客と注文](sample-xml-file-customers-orders.md)」で `FullAddress` 要素を検索し、先行する兄弟要素を 2 とおりの方法で取得します。</span><span class="sxs-lookup"><span data-stu-id="98bd4-107">The following example finds the `FullAddress` element in XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), and retrieves the preceding sibling elements in two different ways.</span></span> <span data-ttu-id="98bd4-108">その後、結果を比較し、同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="98bd4-108">It then compares the results and finds them identical.</span></span>

> [!NOTE]
> <span data-ttu-id="98bd4-109">いずれの方法でも、結果はドキュメント順になります。</span><span class="sxs-lookup"><span data-stu-id="98bd4-109">Both methods provide results that are in document order.</span></span>

<span data-ttu-id="98bd4-110">使用される XPath 式は `preceding-sibling::*` です。</span><span class="sxs-lookup"><span data-stu-id="98bd4-110">The XPath expression used is `preceding-sibling::*`.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");

XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");

// LINQ to XML query
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();

// XPath expression
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim add As XElement = co.<Customers>.<Customer>. _
        <FullAddress>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list2
    Console.WriteLine(el)
Next
```

<span data-ttu-id="98bd4-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="98bd4-111">This example produces the following output:</span></span>

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a><span data-ttu-id="98bd4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="98bd4-112">See also</span></span>

- [<span data-ttu-id="98bd4-113">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98bd4-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
