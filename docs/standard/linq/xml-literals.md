---
title: Visual Basic の XML リテラル - LINQ to XML
description: XML リテラルと組み込み式を使用し、Visual Basic で XML ツリーを作成できます。 組み込み式を使用すると、式を評価してその式の結果を XML ツリーに挿入できます。
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412003"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a>Visual Basic の XML リテラル (LINQ to XML)

この記事では、XML リテラルと組み込み式を使用し、Visual Basic で XML ツリーを作成する方法について説明します。

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a>例: XML リテラルを使用して XML ツリーを作成する

次の例では、XML リテラルを使用して <xref:System.Xml.Linq.XElement> (ここでは `contacts`) を作成する方法を示しています。

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

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a>例: XML リテラルを使用し、簡単なコンテンツで XElement を作成する

次のように、単純コンテンツを含む <xref:System.Xml.Linq.XElement> を作成できます。

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

この例を実行すると、次の出力が生成されます。

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a>例: XML リテラルを使用し、空の要素を作成する

次のように、空の <xref:System.Xml.Linq.XElement> を作成できます。

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

この例を実行すると、次の出力が生成されます。

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a>組み込み式を使用してコンテンツを作成する

XML リテラルの重要な機能は、組み込み式を利用できることです。 組み込み式を使用すると、式を評価してその式の結果を XML ツリーに挿入できます。 式が <xref:System.Xml.Linq.XElement> の型に評価される場合、要素がツリーに挿入されます。 式が <xref:System.Xml.Linq.XAttribute> の型に評価される場合は、属性がツリーに挿入されます。 要素や属性は、それが有効となるツリーにのみ挿入できます。

組み込み式に含めることができるのは 1 つの式だけであることに注意することが重要です。 複数のステートメントを組み込むことはできません。 式が複数の行にまたがる場合は、行連結文字を使用する必要があります。

組み込み式を使用して既存のノード (要素を含む) や属性を新しい XML ツリーに追加する場合に、その既存のノードに既に親があるときは、ノードが複製されます。 新しく複製されたノードは、新しい XML ツリーにアタッチされます。 既存のノードに親がない場合は、単にノードが新しい XML ツリーにアタッチされます。 この記事の最後の例では、この動作について説明します。

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a>例: 組み込み式を使用し、要素を挿入する

次の例では、組み込み式を使用して要素をツリーに挿入します。

```vb
xmlTree1 As XElement = _
    <Root>
        <Child>Contents</Child>
    </Root>
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child> %>
    </Root>
Console.WriteLine(xmlTree2)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a>例: コンテンツの組み込み式を使用する

組み込み式を使用して要素のコンテンツを指定できます。

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a>例: 組み込み式で LINQ クエリを使用する

LINQ クエリの結果を使用し、ある要素のコンテンツを指定できます。

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a>例: 組み込み式を使用し、ノード名を指定する

組み込み式を使用して、属性名、属性値、要素名、要素値を計算することもできます。

```vb
Dim eleName As String = "ele"
Dim attName As String = "att"
Dim attValue As String = "aValue"
Dim eleValue As String = "eValue"
Dim n As XElement = _
    <Root <%= attName %>=<%= attValue %>>
        <<%= eleName %>>
            <%= eleValue %>
        </>
    </Root>
Console.WriteLine(n)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a>例: 組み込み式を使用し、ノードを複製し、アタッチする

既に説明したとおり、組み込み式を使用して既存のノード (要素を含む) や属性を新しい XML ツリーに追加するとき、追加されるノードに既に親があるとき、ノードが複製され、複製が新しい XML ツリーにアタッチされます。 既存のノードに親がない場合は、そのままノードが新しい XML ツリーにアタッチされます。

次のコードでは、親を持つ要素をツリーに追加する場合と親を持たない要素をツリーに追加する場合の動作を示します。

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
Dim child2 As XElement = <Child2>2</Child2>

' Create a tree and add Child1 and Child2 to it.
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child1>(0) %>
        <%= child2 %>
    </Root>

' Compare Child1 identity.
Console.WriteLine("Child1 was {0}", _
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _
    "attached", "cloned"))

' Compare Child2 identity.
Console.WriteLine("Child2 was {0}", _
    IIf(child2 Is xmlTree2.Element("Child2"), _
    "attached", "cloned"))
```

この例を実行すると、次の出力が生成されます。

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a>関連項目

- [関数型構築](functional-construction.md)
