---
title: 単一の属性を取得する方法 - LINQ to XML
description: 属性名を指定して要素の単一の属性を取得します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: a8a56ec62275f2376d19d7fc9090414b74fc77ad
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412073"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml"></a>単一の属性を取得する方法 (LINQ to XML)

この記事では、属性名を指定して要素の単一の属性を取得する方法について説明します。 これは、特定の属性を持つ要素を検索するクエリ式を記述する場合に便利です。

<xref:System.Xml.Linq.XElement.Attribute%2A> クラスの <xref:System.Xml.Linq.XElement> メソッドは、指定された名前を持つ <xref:System.Xml.Linq.XAttribute> を返します。

## <a name="example-retrieve-attribute-values-given-the-element-and-attribute-names"></a>例: 要素名と属性名を指定して属性値を取得する

次の例では、<xref:System.Xml.Linq.XElement> メソッドを使用して、`PhoneNumbers` という名前の要素を作成します。 次に、`Phone` という名前の子孫要素をすべて検索し、それぞれに対して、<xref:System.Xml.Linq.XElement.Attribute%2A> メソッドを使用して `type` という名前の属性の値を取得して出力します。

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList = From el In cust...<Phone>
For Each e As XElement In elList
    Console.WriteLine(e.@type)
Next
```

この例を実行すると、次の出力が生成されます。

```output
home
work
```

## <a name="example-retrieve-an-attribute-value-with-a-cast"></a>例: キャストを使用して属性値を取得する

<xref:System.Xml.Linq.XElement> オブジェクトの場合と同じように、キャストすることで属性の値を取得することができます。 この動作を次の例で示します。

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList As IEnumerable(Of XElement) = _
    From el In cust...<Phone> _
    Select el
For Each el As XElement In elList
    Console.WriteLine(el.@type)
Next
```

この例を実行すると、次の出力が生成されます。

```output
home
work
```

LINQ to XML には、`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID`、`GUID?` に対する <xref:System.Xml.Linq.XAttribute> クラスのための明示的なキャスト演算子が用意されています。

## <a name="example-cast-for-an-attribute-in-a-namespace"></a>例: 名前空間内の属性にキャストする

上記と同じコードを使用して、名前空間内の属性を取得する例を次に示します。 詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement cust = new XElement(aw + "PhoneNumbers",
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "home"),
        "555-555-5555"),
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants(aw + "Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute(aw + "type"));
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cust As XElement = _
            <aw:PhoneNumbers>
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>
            </aw:PhoneNumbers>
        Dim elList As IEnumerable(Of XElement) = _
            From el In cust...<aw:Phone> _
            Select el
        For Each el As XElement In elList
            Console.WriteLine(el.@aw:type)
        Next
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
home
work
```

## <a name="see-also"></a>関連項目

- [LINQ to XML 軸の概要](linq-xml-axes-overview.md)
