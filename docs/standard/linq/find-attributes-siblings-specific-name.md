---
title: 特定の名前を持つ兄弟の属性を検索する方法 - LINQ to XML
description: 特定の名前を持ち、かつ、コンテキスト ノードの兄弟にも属するあらゆる属性を検索する方法について説明します。 2 つの方法を紹介します。1 つは XPathEvaluate を使用し、もう 1 つは LINQ to XML クエリを使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 869c63f26c14bedc8d9911915b8974aa530685fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412149"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-linq-to-xml"></a>特定の名前を持つ兄弟の属性を検索する方法 (LINQ to XML)

この記事では、<xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> を使用することで、特定の名前を持ち、かつ、コンテキスト ノードの兄弟にも属するあらゆる属性を検索する方法を紹介します。 この記事ではまた、LINQ to XML クエリを使用して同じことを行う方法を紹介します。

## <a name="example-find-all-sibling-elements-named-book-and-then-find-all-attributes-named-id"></a>例: `Book` という名前の兄弟要素をすべて検索し、`id` という名前の属性をすべて検索する

この例では、XML ドキュメント「[サンプル XML ファイル: 書籍](sample-xml-file-books.md)」で `Book` 要素を検索します。 その後、`Book` という名前の兄弟要素をすべて検索し、それらの要素から `id` という名前の属性をすべて検索します。 結果は属性のコレクションです。

XPath 式は `../Book/@id` です。

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Element("Book");

// LINQ to XML query
IEnumerable<XAttribute> list1 =
    from el in book.Parent.Elements("Book")
    select el.Attribute("id");

// XPath expression
IEnumerable<XAttribute> list2 =
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XAttribute el in list1)
    Console.WriteLine(el);
```

```vb
Dim books as XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>(0)

' LINQ to XML query
Dim list1 As IEnumerable(Of XAttribute) = _
    From el In book.Parent.<Book> _
    Select el.Attribute("id")

' XPath expression
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()

If list1.Count() = list2.Count() And _
        (list1.Intersect(list2)).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XAttribute In list1
    Console.WriteLine(el)
Next
```

この例を実行すると、次の出力が生成されます。

```output
Results are identical
id="bk101"
id="bk102"
```

## <a name="see-also"></a>関連項目

- [XPath ユーザー向けの LINQ to XML (Visual Basic)](./comparison-xpath-linq-xml.md)
