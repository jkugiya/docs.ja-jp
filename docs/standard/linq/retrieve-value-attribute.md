---
title: 属性の値を取得する方法 - LINQ to XML
description: 属性の値を取得します。 XAttribute を目的の型にキャストすることも、XAttribute.Value プロパティを使用することもできます。
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412195"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a>属性の値を取得する方法 (LINQ to XML)

この記事では、属性の値を取得する方法について示します。 主に 2 つの方法があります。1 つは、<xref:System.Xml.Linq.XAttribute> を目的の型にキャストする方法です。その後、明示的な変換演算子によって、要素または属性のコンテンツが指定した型に変換されます。 もう 1 つは、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを使用する方法です。 ただし、通常はキャストがより適切な方法です。 属性を null 許容の値の型にキャストすると、存在しているかどうかが不明確な属性の値を取得する場合にコードをより簡単に記述できます。 この手法の例については、「[要素の値を取得する方法](retrieve-value-element.md)」を参照してください。

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a>例: 属性の値を取得するためにキャストを使用する

C# で属性の値を取得するには、<xref:System.Xml.Linq.XAttribute> オブジェクトを目的の型にキャストします。 Visual Basic では、統合属性プロパティを使用して値を取得できます。

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

この例を実行すると、次の出力が生成されます。

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a>例: 名前空間にある XML からの取得にキャストを使用する

属性が名前空間内にある場合にその属性の値を取得する方法を次の例に示します。 詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>
        Dim str As String = root.@aw:Attr
        Console.WriteLine(str)
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
abcde
```

## <a name="see-also"></a>関連項目

- [LINQ to XML 軸の概要](linq-xml-axes-overview.md)
