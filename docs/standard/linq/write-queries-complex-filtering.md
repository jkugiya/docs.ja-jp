---
title: 複雑なフィルターを使用してクエリを記述する方法 - LINQ to XML
description: 複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。 たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412110"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a>複雑なフィルターを使用してクエリを記述する方法 (LINQ to XML)

複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。 たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。 この記事では、複雑なフィルターを使用してクエリを記述する例について説明します。

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a>例: `Where` 句で入れ子になったクエリを使用して検索する

この例では、次を持つ `PurchaseOrder` 要素を検索する方法を示します。

- `Type` 属性が "Shipping" の `Address` 子要素。
- "NY" と等しい `State` 子要素。

この例では、入れ子になったクエリを `Where` 句で使用しています。コレクションに要素が含まれる場合、`Any` 演算子は `true` を返します。 この例では、「[サンプル XML ファイル: 複数の購買発注書](sample-xml-file-multiple-purchase-orders.md)」の XML ドキュメントを使用します。

`Any` 演算子の詳細については、「[量指定子操作 (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md)」および「[量指定子操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)」を参照してください。

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrders.xml")
Dim purchaseOrders As IEnumerable(Of XElement) = _
    From el In root.<PurchaseOrder> _
    Where _
        (From add In el.<Address> _
        Where _
             add.@Type = "Shipping" And _
             add.<State>.Value = "NY" _
        Select add) _
    .Any() _
    Select el
For Each el As XElement In purchaseOrders
    Console.WriteLine(el.@PurchaseOrderNumber)
Next
```

この例を実行すると、次の出力が生成されます。

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a>例: 名前空間にある XML で検索する

次の例のクエリは上のものと同じですが、ある名前空間にある XML が対象になっています。 詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。

この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](sample-xml-file-multiple-purchase-orders-namespace.md)」の XML ドキュメントを使用します。

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim purchaseOrders As IEnumerable(Of XElement) = _
            From el In root.<aw:PurchaseOrder> _
            Where _
                (From add In el.<aw:Address> _
                Where _
                     add.@aw:Type = "Shipping" And _
                     add.<aw:State>.Value = "NY" _
                Select add) _
            .Any() _
            Select el
        For Each el As XElement In purchaseOrders
            Console.WriteLine(el.@aw:PurchaseOrderNumber)
        Next
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
99505
```

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [射影操作 (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [量指定子操作 (C#)](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [XML 子軸プロパティ (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 属性軸プロパティ (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML Value プロパティ (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [射影操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [量指定子操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
