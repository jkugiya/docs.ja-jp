---
title: ルート要素を検索する方法 - LINQ to XML
description: C# および Visual Basic で XPath と LINQ to XML を使用して、XML ドキュメントのルート要素を検索する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 89247c19fc31add4e95f11742772cef1bdd2ce63
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "103412204"
---
# <a name="how-to-find-the-root-element-linq-to-xml"></a>ルート要素を検索する方法 (LINQ to XML)

この記事では、C# および Visual Basic で XPath と LINQ to XML を使用して、XML ドキュメントのルート要素を検索する方法を示す例を提供します。

## <a name="example-find-the-root-element"></a>例: ルート要素を検索する

この例では、LINQ to XML クエリと XPath を使用して、XML ドキュメントの「[サンプル XML ファイル: 複数の購買発注書](sample-xml-file-multiple-purchase-orders.md)」のルート要素を検索します。 XPath 式は `/PurchaseOrders` です。

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
XElement el1 = po.Root;

// XPath expression
XElement el2 = po.XPathSelectElement("/PurchaseOrders");

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1.Name);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim el1 As XElement = po.Root

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1.Name)
```

この例を実行すると、次の出力が生成されます。

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a>関連項目

- [XPath と LINQ to XML の比較](comparison-xpath-linq-xml.md)
