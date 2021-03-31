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
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a>先行する兄弟を検索する方法 (LINQ to XML)

この記事では、先行する兄弟軸に沿って <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用し、特定の要素の前にある兄弟要素を検索する方法と、<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> を使用して同じ要素を検索する方法を紹介します。

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a>例: ある要素の前に存在する兄弟要素を 2 とおりの方法で検索する

次の例では、XML ドキュメント「[サンプル XML ファイル: 顧客と注文](sample-xml-file-customers-orders.md)」で `FullAddress` 要素を検索し、先行する兄弟要素を 2 とおりの方法で取得します。 その後、結果を比較し、同じであることを確認します。

> [!NOTE]
> いずれの方法でも、結果はドキュメント順になります。

使用される XPath 式は `preceding-sibling::*` です。

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

この例を実行すると、次の出力が生成されます。

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a>関連項目

- [XPath ユーザー向けの LINQ to XML (Visual Basic)](./comparison-xpath-linq-xml.md)
