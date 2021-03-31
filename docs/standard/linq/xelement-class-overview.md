---
title: XElement クラスの概要
description: XElement クラスは XML 要素を表します。 これを使用し、要素を作成または変更したり、属性と子を追加したり、シリアル化したりできます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411995"
---
# <a name="xelement-class-overview"></a>XElement クラスの概要

<xref:System.Xml.Linq.XElement> クラスは、LINQ to XML の基本的なクラスの 1 つです。 これは XML 要素を表します。 次の一覧は、このクラスでできることをまとめたものです。

- 要素を作成します。
- 要素のコンテンツを変更します。
- 子要素を追加、変更、削除します。
- 要素に属性を追加します。
- 要素のコンテンツをテキスト形式でシリアル化します。

<xref:System.Xml?displayProperty=nameWithType>、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> などの、<xref:System.Xml.Xsl.XslCompiledTransform> の他のクラスと相互運用することもできます。

この記事では、<xref:System.Xml.Linq.XElement> クラスによって提供される機能について説明します。

## <a name="construct-xml-trees"></a>XML ツリーの構築

次のようなさまざまな方法で XML ツリーを構築できます。

- コードで XML ツリーを構築できます。 詳細については、[XML ツリー](functional-construction.md)に関する記事を参照してください。
- <xref:System.IO.TextReader>、テキスト ファイル、Web アドレス (URL) など、さまざまなソースから XML を解析できます。 詳細については、[XML の解析](parse-string.md)に関するページを参照してください。
- <xref:System.Xml.XmlReader> を使用してツリーを設定できます。 詳細については、「<xref:System.Xml.Linq.XNode.ReadFrom%2A>」を参照してください。
- <xref:System.Xml.XmlWriter> にコンテンツを書き込むことができるモジュールがある場合は、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> メソッドを使用してライターを作成し、このライターをモジュールに渡し、<xref:System.Xml.XmlWriter> に書き込まれたコンテンツを使用して XML ツリーを設定できます。

ツリーを作成する例を次に示します。 C# バージョンでは、入れ子になった要素の作成が使用されます。 Visual Basic でも同じ手法を使用できますが、この例では XML リテラルを使用します。

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

また、次の例に示すように、LINQ to XML クエリを使用して XML ツリーを設定することもできます。

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a>XML ツリーをシリアル化する

XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。

詳しくは、[XML ツリーのシリアル化](preserve-white-space-serializing.md)に関するページをご覧ください。

## <a name="retrieve-xml-data-via-axis-methods"></a>軸メソッドによる XML データの取得

軸メソッドを使用すると、属性、子要素、子孫要素、および祖先要素を取得できます。 LINQ to XML クエリは、軸メソッドに対して機能し、XML ツリーを操作して処理するための、柔軟で強力な複数の機能を備えています。

詳しくは、「[LINQ to XML 軸の概要](linq-xml-axes-overview.md)」をご覧ください。

## <a name="query-xml-trees"></a>XML ツリーのクエリ

XML ツリーからデータを抽出する LINQ to XML クエリを記述できます。

詳しくは、「[XML ツリーのクエリの概要](query-xml-trees-overview.md)」をご覧ください。

## <a name="modify-xml-trees"></a>XML ツリーを変更する

要素を変更するには、そのコンテンツや属性を変更するなど、さまざまな方法があります。 要素を親から削除することもできます。

詳細については、[XML ツリーの変更](in-memory-xml-tree-modification-vs-functional-construction.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [LINQ to XML プログラミングの概要](functional-vs-procedural-programming.md)
