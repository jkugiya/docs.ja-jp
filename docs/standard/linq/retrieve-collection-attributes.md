---
title: 属性のコレクションを取得する方法 - LINQ to XML
description: XElement.Attributes メソッドを使用し、要素の属性を取得する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: a15375ffd6b3af7fb9119e3321495cffa00268e4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411983"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml"></a>属性のコレクションを取得する方法 (LINQ to XML)

この記事では、<xref:System.Xml.Linq.XElement.Attributes%2A> メソッドを使用し、要素の属性を取得します。

## <a name="example-iterate-through-the-attributes-of-an-element"></a>例: 要素の属性を反復処理する

次の例では、要素の属性のコレクションを反復処理する方法を示します。

```csharp
XElement val = new XElement("Value",
    new XAttribute("ID", "1243"),
    new XAttribute("Type", "int"),
    new XAttribute("ConvertableTo", "double"),
    "100");
IEnumerable<XAttribute> listOfAttributes =
    from att in val.Attributes()
    select att;
foreach (XAttribute a in listOfAttributes)
    Console.WriteLine(a);
```

```vb
Dim val = _
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>
Dim listOfAttributes As IEnumerable(Of XAttribute) = _
    From att In val.Attributes() _
    Select att
For Each att As XAttribute In listOfAttributes
    Console.WriteLine(att)
Next
```

この例を実行すると、次の出力が生成されます。

```output
ID="1243"
Type="int"
ConvertableTo="double"
```

## <a name="see-also"></a>関連項目

- [LINQ to XML 軸の概要](linq-xml-axes-overview.md)
