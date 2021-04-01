---
title: 単一の子要素を取得する方法 - LINQ to XML
description: 指定された名前を持つ最初の子要素を取得します。 C# では XContainer.Element を使用し、Visual Basic では配列インデクサー表記を使用できます。
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412196"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a>単一の子要素を取得する方法 (LINQ to XML)

この記事では、指定された名前を持つ最初の子要素である単一の子要素を取得する方法について説明します。 C# では、<xref:System.Xml.Linq.XContainer.Element%2A> メソッドを使用してこれを行います。 Visual Basic は、配列インデクサー表記を使用してこれを行います。

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a>例: 指定された名前を持つ最初の要素を取得する

次の例では、「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」の XML ドキュメントから最初の `DeliveryNotes` 要素を取得します。

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

この例を実行すると、次の出力が生成されます。

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a>例: 名前空間にある XML から取得する

次の例は、1 つ上と同じ内容を行いますが、名前空間にある XML が対象になっています。 XML ドキュメントの[サンプル XML ファイル: 名前空間内の一般的な購買発注書](sample-xml-file-typical-purchase-order-namespace.md)が使用されています。 名前空間の詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim e As XElement = po.<aw:DeliveryNotes>(0)
        Console.WriteLine(e)
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a>関連項目

- [LINQ to XML 軸の概要](linq-xml-axes-overview.md)
