---
title: ノードを使用したプログラミング - LINQ to XML
description: XML ツリーのノード レベルでコードを記述する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8f9d5c8656a06a9b40a3833aaf7e190b9ba3f0a6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412013"
---
# <a name="programming-with-nodes-linq-to-xml"></a>ノードを使用したプログラミング (LINQ to XML)

XML エディター、変換システム、レポート作成プログラムなどのプログラムを作成する LINQ to XML の開発者のコードは、通常、要素や属性よりも細かい細分性レベルで動作する必要があります。 しばしばノード レベルで、テキスト ノードを操作し、命令を処理し、コメントを処理する必要があります。 この記事では、ノード レベルでのプログラミングについて説明します。

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a>例: `null` に設定された XDocument の子ノードの `Parent` プロパティ値

<xref:System.Xml.Linq.XObject.Parent%2A> プロパティには、親ノードではなく親 <xref:System.Xml.Linq.XElement> が含まれています。 <xref:System.Xml.Linq.XDocument> の子ノードには、親 <xref:System.Xml.Linq.XElement> がありません。 これらの親はドキュメントであるため、それらのノードの <xref:System.Xml.Linq.XObject.Parent%2A> プロパティは `null` に設定されています。

この動作を次の例で示します。

```csharp
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);
Console.WriteLine(doc.Root.Parent == null);
```

```vb
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)
Console.WriteLine(doc.Root.Parent Is Nothing)
```

この例を実行すると、次の出力が生成されます。

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a>例: テキストを追加しても新しいテキスト ノードが作成される場合とされない場合がある

多くの XML プログラミング モデルでは、隣接するテキスト ノードが常に連結されます。 これは、テキスト ノードの正規化と呼ばれることがあります。 LINQ to XML ではテキスト ノードを正規化しません。 同じ要素に 2 つのテキスト ノードを追加すると、隣接するテキスト ノードになります。 ただし、<xref:System.Xml.Linq.XText> ノードではなく文字列として指定したコンテンツを追加すると、LINQ to XML はその文字列を隣接するテキスト ノードに連結します。 次に例を示します。

```csharp
XElement xmlTree = new XElement("Root", "Content");

Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this doesn't add a new text node
xmlTree.Add("new content");
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this does add a new, adjacent text node
xmlTree.Add(new XText("more text"));
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

' This doesn't add a new text node.
xmlTree.Add("new content")
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

'// This does add a new, adjacent text node.
xmlTree.Add(New XText("more text"))
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())
```

 この例を実行すると、次の出力が生成されます。

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a>例: テキスト ノードの値を空の文字列に設定しても、ノードは削除されない

一部の XML プログラミング モデルでは、テキスト ノードに空の文字列が含まれないことが保証されます。 その理由は、テキスト ノードに空の文字列が含まれていなければ、XML のシリアル化に対して影響が生じないためです。 ただし、隣接するテキスト ノードが生じるのと同じ理由で、テキスト ノードの値を空の文字列に設定してテキスト ノードからテキストを削除した場合、テキスト ノード自体は削除されません。

```csharp
XElement xmlTree = new XElement("Root", "Content");
XText textNode = xmlTree.Nodes().OfType<XText>().First();

// the following line doesn't cause the removal of the text node.
textNode.Value = "";

XText textNode2 = xmlTree.Nodes().OfType<XText>().First();
Console.WriteLine(">>{0}<<", textNode2);
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()

' The following line doesn't cause the removal of the text node.
textNode.Value = ""

Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()
Console.WriteLine(">>{0}<<", textNode2)
```

この例を実行すると、次の出力が生成されます。

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a>例: 空のテキスト ノードが 1 つある要素は、テキスト ノードのないものとは別にシリアル化される

要素に空の 1 つの子テキスト ノードのみが含まれている場合、その要素は長いタグ構文 `<Child></Child>` でシリアル化されます。 子ノードがまったく含まれていない要素は、短いタグ構文 `<Child />` でシリアル化されます。

```csharp
XElement child1 = new XElement("Child1",
    new XText("")
);
XElement child2 = new XElement("Child2");
Console.WriteLine(child1);
Console.WriteLine(child2);
```

```vb
Dim child1 As XElement = New XElement("Child1", _
    New XText("") _
)
Dim child2 As XElement = New XElement("Child2")
Console.WriteLine(child1)
Console.WriteLine(child2)
```

この例を実行すると、次の出力が生成されます。

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a>例: LINQ to XML ツリーでは名前空間が属性になる

名前空間宣言の構文は属性と同じですが、XSLT や XPath などの一部のプログラミング インターフェイスでは、名前空間宣言は属性と見なされません。 ただし LINQ to XML では、名前空間は <xref:System.Xml.Linq.XAttribute> オブジェクトとして XML ツリーに格納されます。 名前空間宣言を含む要素の属性を反復処理すると、名前空間宣言が、返されるコレクションの項目の 1 つになります。 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> プロパティによって、属性が名前空間宣言であるかどうかが示されます。

```csharp
XElement root = XElement.Parse(
@"<Root
    xmlns='http://www.adventure-works.com'
    xmlns:fc='www.fourthcoffee.com'
    AnAttribute='abc'/>");
foreach (XAttribute att in root.Attributes())
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);
```

```vb
Dim root As XElement = _
<Root
    xmlns='http://www.adventure-works.com'
    xmlns:fc='www.fourthcoffee.com'
    AnAttribute='abc'/>
For Each att As XAttribute In root.Attributes()
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _
                      att.IsNamespaceDeclaration)
Next
```

この例を実行すると、次の出力が生成されます。

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a>例: XPath 軸メソッドが XDocument の子テキスト ノードを返さない

LINQ to XML では、空白のみを含む <xref:System.Xml.Linq.XDocument> の子テキスト ノードを許可しています。 ただし、XPath オブジェクト モデルでは、空白がドキュメントの子ノードとして組み込まれないため、<xref:System.Xml.Linq.XContainer.Nodes%2A> 軸を使用して <xref:System.Xml.Linq.XDocument> の子を反復処理すると、空白のテキスト ノードが返されます。 一方、XPath 軸メソッドを使用して <xref:System.Xml.Linq.XDocument> の子を反復処理すると、空白のテキスト ノードは返されません。

```csharp
// Create a document with some white space child nodes of the document.
XDocument root = XDocument.Parse(
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<Root/>

<!--a comment-->
", LoadOptions.PreserveWhitespace);

// count the white space child nodes using LINQ to XML
Console.WriteLine(root.Nodes().OfType<XText>().Count());

// count the white space child nodes using XPathEvaluate
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```

```vb
' Create a document with some white space child nodes of the document.
Dim root As XDocument = XDocument.Parse( _
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _
LoadOptions.PreserveWhitespace)

' Count the white space child nodes using LINQ to XML.
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())

' Count the white space child nodes using XPathEvaluate.
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)
Console.WriteLine(nodes.OfType(Of XText)().Count())
```

この例を実行すると、次の出力が生成されます。

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a>XDocument の XML 宣言ノードはプロパティであり、子ノードではない

<xref:System.Xml.Linq.XDocument> の子ノードを反復処理しても、XML 宣言オブジェクトは生成されません。 これはドキュメントのプロパティであって、その子ノードではありません。

```csharp
XDocument doc = new XDocument(
    new XDeclaration("1.0", "utf-8", "yes"),
    new XElement("Root")
);
doc.Save("Temp.xml");
Console.WriteLine(File.ReadAllText("Temp.xml"));

// this shows that there is only one child node of the document
Console.WriteLine(doc.Nodes().Count());
```

```vb
Dim doc As XDocument = _
<?xml version='1.0' encoding='utf-8' standalone='yes'?>
<Root/>

doc.Save("Temp.xml")
Console.WriteLine(File.ReadAllText("Temp.xml"))

' This shows that there is only one child node of the document.
Console.WriteLine(doc.Nodes().Count())
```

この例を実行すると、次の出力が生成されます。

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
