---
title: 特定の属性を持つ要素を検索する方法 - LINQ to XML
description: 属性に特定の値が含まれる要素を検索する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: a1569f8a91e980f12ecc1801e00d6414711833d0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412120"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a>特定の属性を持つ要素を検索する方法 (LINQ to XML)

この記事では、属性に特定の値が含まれる要素を検索する方法の例を提供します。

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a>例: 属性に特定の値が含まれる要素を検索する

次の例では、"Billing" の値を含む `Type` 属性を持つ `Address` 要素を検索する方法を示します。 この例では、XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」を使用します。

```csharp
XElement root = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> address =
    from el in root.Elements("Address")
    where (string)el.Attribute("Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrder.xml")
Dim address As IEnumerable(Of XElement) = _
    From el In root.<Address> _
    Where el.@Type = "Billing" _
    Select el
For Each el As XElement In address
    Console.WriteLine(el)
Next
```

この例を実行すると、次の出力が生成されます。

```xml
<Address Type="Billing">
  <Name>Tai Yee</Name>
  <Street>8 Oak Avenue</Street>
  <City>Old Town</City>
  <State>PA</State>
  <Zip>95819</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a>例: ある名前空間にある XML 内の要素を検索する

次の例では同じクエリを確認できますが、ある名前空間にある XML が対象になっています。 XML ドキュメント「[サンプル XML ファイル: 名前空間内の一般的な購買発注書](sample-xml-file-typical-purchase-order-namespace.md)」が使用されています。

名前空間の詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。

```csharp
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> address =
    from el in root.Elements(aw + "Address")
    where (string)el.Attribute(aw + "Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim address As IEnumerable(Of XElement) = _
            From el In root.<aw:Address> _
            Where el.@aw:Type = "Billing" _
            Select el
        For Each el As XElement In address
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">
  <aw:Name>Tai Yee</aw:Name>
  <aw:Street>8 Oak Avenue</aw:Street>
  <aw:City>Old Town</aw:City>
  <aw:State>PA</aw:State>
  <aw:Zip>95819</aw:Zip>
  <aw:Country>USA</aw:Country>
</aw:Address>
```

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [標準クエリ演算子の概要 (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [射影操作 (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [基本的なクエリ (LINQ to XML) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)
- [標準クエリ演算子の概要 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [射影操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
