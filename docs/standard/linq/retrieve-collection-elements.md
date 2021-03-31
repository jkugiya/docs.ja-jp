---
title: 要素のコレクションを取得する方法 - LINQ to XML
description: XContainer.Elements メソッドを使用し、要素の子要素のコレクションを取得する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: e73f608cff13f75f769f77372dc1c09949e00b0e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411963"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml"></a>要素のコレクションを取得する方法 (LINQ to XML)

この記事では、要素の子要素のコレクションを取得する <xref:System.Xml.Linq.XContainer.Elements%2A> メソッドについて説明します。

## <a name="example-iterate-through-the-child-elements-of-an-element"></a>例: 要素の子要素を反復処理する

この例では、`purchaseOrder` 要素の子要素を反復処理します。 XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」が使用されます。

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> childElements =
    from el in po.Elements()
    select el;
foreach (XElement el in childElements)
    Console.WriteLine("Name: " + el.Name);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim childElements As IEnumerable(Of XElement)
childElements = _
    From el In po.Elements() _
    Select el
For Each el As XElement In childElements
    Console.WriteLine("Name: " & el.Name.ToString())
Next
```

この例を実行すると、次の出力が生成されます。

```output
Name: Address
Name: Address
Name: DeliveryNotes
Name: Items
```

## <a name="see-also"></a>関連項目

- [LINQ to XML 軸の概要](linq-xml-axes-overview.md)
