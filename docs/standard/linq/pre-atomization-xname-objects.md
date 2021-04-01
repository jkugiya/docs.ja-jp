---
title: XName オブジェクトの事前アトミック化 - LINQ to XML
description: 同じ名前で大量の要素を作成するとき、事前アトミック化でパフォーマンスを改善する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 97da1e09e246491d8427c7a69953e006c80475a4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411986"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml"></a>XName オブジェクトの事前アトミック化 (LINQ to XML)

LINQ to XML でパフォーマンスを向上させる方法の 1 つは、<xref:System.Xml.Linq.XName> オブジェクトの事前アトミック化です。 事前アトミック化とは、<xref:System.Xml.Linq.XName> クラスと <xref:System.Xml.Linq.XElement> クラスのコンストラクターを使用して XML ツリーを作成する前に、文字列を <xref:System.Xml.Linq.XAttribute> オブジェクトに割り当てる操作です。 次に、(文字列から <xref:System.Xml.Linq.XName> への暗黙的な変換を使用する) コンストラクターに文字列を渡す代わりに、初期化された <xref:System.Xml.Linq.XName> オブジェクトを渡します。

これによって、名前が繰り返される大きい XML ツリーを作成するときにパフォーマンスが向上します。 これを行うには、XML ツリーを構築する前に、<xref:System.Xml.Linq.XName> オブジェクトを宣言して初期化し、次に要素名と属性名に文字列を指定する代わりに <xref:System.Xml.Linq.XName> オブジェクトを使用します。 この手法では、同じ名前の多数の要素や属性を作成する場合に、パフォーマンスが大幅に向上します。

各自のシナリオで事前アトミック化をテストし、使用すべきかどうかを判断してください。

## <a name="example-create-elements-in-various-ways-with-and-without-pre-atomization"></a>例: 事前アトミック化の有無を含め、さまざまな方法で要素を作成する

次の例では、事前アトミック化が示されています。

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

次の例は同じ手法ですが、ある名前空間に属する XML ドキュメントが対象になっています。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XName Root = aw + "Root";
XName Data = aw + "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XAttribute(XNamespace.Xmlns + "aw", aw),
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

```vb
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim root1 As XName = aw + "Root"
Dim data As XName = aw + "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XAttribute(XNamespace.Xmlns + "aw", aw),
                          New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

次に示すのは、より実働環境に近い例です。 この例では、要素の内容がクエリによって提供されます。

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

DateTime t1 = DateTime.Now;
XElement root = new XElement(Root,
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement(Data,
        new XAttribute(ID, i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root2 As New XElement(root1, From i In Enumerable.Range(1, 100000)
                                 Select New XElement(data, New XAttribute(ID, i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

前の例では、名前が事前アトミック化されていない次の例に比べて良いパフォーマンスが得られます。

```csharp
DateTime t1 = DateTime.Now;
XElement root = new XElement("Root",
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement("Data",
        new XAttribute("ID", i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a>関連項目

- [アトミック化された XName および XNamespace オブジェクト](atomized-xname-xnamespace-objects.md)
