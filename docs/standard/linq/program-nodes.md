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
# <a name="programming-with-nodes-linq-to-xml"></a><span data-ttu-id="cd3a4-103">ノードを使用したプログラミング (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cd3a4-103">Programming with nodes (LINQ to XML)</span></span>

<span data-ttu-id="cd3a4-104">XML エディター、変換システム、レポート作成プログラムなどのプログラムを作成する LINQ to XML の開発者のコードは、通常、要素や属性よりも細かい細分性レベルで動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-104">LINQ to XML developers who need to write programs such as an XML editor, a transform system, or a report writer often need code that works at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="cd3a4-105">しばしばノード レベルで、テキスト ノードを操作し、命令を処理し、コメントを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-105">They often need to work at the node level, manipulating text nodes, processing instructions, and processing comments.</span></span> <span data-ttu-id="cd3a4-106">この記事では、ノード レベルでのプログラミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-106">This article provides information about programming at the node level.</span></span>

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a><span data-ttu-id="cd3a4-107">例: `null` に設定された XDocument の子ノードの `Parent` プロパティ値</span><span class="sxs-lookup"><span data-stu-id="cd3a4-107">Example: The `Parent` property values of the child nodes of XDocument are set to `null`</span></span>

<span data-ttu-id="cd3a4-108"><xref:System.Xml.Linq.XObject.Parent%2A> プロパティには、親ノードではなく親 <xref:System.Xml.Linq.XElement> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-108">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="cd3a4-109"><xref:System.Xml.Linq.XDocument> の子ノードには、親 <xref:System.Xml.Linq.XElement> がありません。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-109">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="cd3a4-110">これらの親はドキュメントであるため、それらのノードの <xref:System.Xml.Linq.XObject.Parent%2A> プロパティは `null` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-110">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to `null`.</span></span>

<span data-ttu-id="cd3a4-111">この動作を次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-111">The following example demonstrates this:</span></span>

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

<span data-ttu-id="cd3a4-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-112">This example produces the following output:</span></span>

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a><span data-ttu-id="cd3a4-113">例: テキストを追加しても新しいテキスト ノードが作成される場合とされない場合がある</span><span class="sxs-lookup"><span data-stu-id="cd3a4-113">Example: Adding text may or may not create a new text node</span></span>

<span data-ttu-id="cd3a4-114">多くの XML プログラミング モデルでは、隣接するテキスト ノードが常に連結されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-114">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="cd3a4-115">これは、テキスト ノードの正規化と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-115">This is sometimes called normalization of text nodes.</span></span> <span data-ttu-id="cd3a4-116">LINQ to XML ではテキスト ノードを正規化しません。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-116">LINQ to XML doesn't normalize text nodes.</span></span> <span data-ttu-id="cd3a4-117">同じ要素に 2 つのテキスト ノードを追加すると、隣接するテキスト ノードになります。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-117">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="cd3a4-118">ただし、<xref:System.Xml.Linq.XText> ノードではなく文字列として指定したコンテンツを追加すると、LINQ to XML はその文字列を隣接するテキスト ノードに連結します。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-118">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, LINQ to XML might merge the string with an adjacent text node.</span></span> <span data-ttu-id="cd3a4-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-119">The following example demonstrates this.</span></span>

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

 <span data-ttu-id="cd3a4-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-120">This example produces the following output:</span></span>

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a><span data-ttu-id="cd3a4-121">例: テキスト ノードの値を空の文字列に設定しても、ノードは削除されない</span><span class="sxs-lookup"><span data-stu-id="cd3a4-121">Example: Setting a text node value to the empty string doesn't delete the node</span></span>

<span data-ttu-id="cd3a4-122">一部の XML プログラミング モデルでは、テキスト ノードに空の文字列が含まれないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-122">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="cd3a4-123">その理由は、テキスト ノードに空の文字列が含まれていなければ、XML のシリアル化に対して影響が生じないためです。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-123">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="cd3a4-124">ただし、隣接するテキスト ノードが生じるのと同じ理由で、テキスト ノードの値を空の文字列に設定してテキスト ノードからテキストを削除した場合、テキスト ノード自体は削除されません。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-124">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself won't be deleted.</span></span>

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

<span data-ttu-id="cd3a4-125">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-125">This example produces the following output:</span></span>

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a><span data-ttu-id="cd3a4-126">例: 空のテキスト ノードが 1 つある要素は、テキスト ノードのないものとは別にシリアル化される</span><span class="sxs-lookup"><span data-stu-id="cd3a4-126">Example: An element with one empty text node is serialized differently from one with no text node</span></span>

<span data-ttu-id="cd3a4-127">要素に空の 1 つの子テキスト ノードのみが含まれている場合、その要素は長いタグ構文 `<Child></Child>` でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-127">If an element contains only a child text node that's empty, it's serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="cd3a4-128">子ノードがまったく含まれていない要素は、短いタグ構文 `<Child />` でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-128">If an element contains no child nodes whatsoever, it's serialized with the short tag syntax: `<Child />`.</span></span>

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

<span data-ttu-id="cd3a4-129">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-129">This example produces the following output:</span></span>

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="cd3a4-130">例: LINQ to XML ツリーでは名前空間が属性になる</span><span class="sxs-lookup"><span data-stu-id="cd3a4-130">Example: Namespaces are attributes in the LINQ to XML tree</span></span>

<span data-ttu-id="cd3a4-131">名前空間宣言の構文は属性と同じですが、XSLT や XPath などの一部のプログラミング インターフェイスでは、名前空間宣言は属性と見なされません。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-131">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations aren't considered to be attributes.</span></span> <span data-ttu-id="cd3a4-132">ただし LINQ to XML では、名前空間は <xref:System.Xml.Linq.XAttribute> オブジェクトとして XML ツリーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-132">However, in LINQ to XML, namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="cd3a4-133">名前空間宣言を含む要素の属性を反復処理すると、名前空間宣言が、返されるコレクションの項目の 1 つになります。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-133">If you iterate through the attributes of an element that contains a namespace declaration, the namespace declaration is one of the items in the returned collection.</span></span> <span data-ttu-id="cd3a4-134"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> プロパティによって、属性が名前空間宣言であるかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-134">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>

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

<span data-ttu-id="cd3a4-135">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-135">This example produces the following output:</span></span>

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a><span data-ttu-id="cd3a4-136">例: XPath 軸メソッドが XDocument の子テキスト ノードを返さない</span><span class="sxs-lookup"><span data-stu-id="cd3a4-136">Example: XPath axis methods don't return the child text nodes of XDocument</span></span>

<span data-ttu-id="cd3a4-137">LINQ to XML では、空白のみを含む <xref:System.Xml.Linq.XDocument> の子テキスト ノードを許可しています。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-137">LINQ to XML allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="cd3a4-138">ただし、XPath オブジェクト モデルでは、空白がドキュメントの子ノードとして組み込まれないため、<xref:System.Xml.Linq.XContainer.Nodes%2A> 軸を使用して <xref:System.Xml.Linq.XDocument> の子を反復処理すると、空白のテキスト ノードが返されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-138">However, the XPath object model doesn't include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="cd3a4-139">一方、XPath 軸メソッドを使用して <xref:System.Xml.Linq.XDocument> の子を反復処理すると、空白のテキスト ノードは返されません。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-139">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes won't be returned.</span></span>

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

<span data-ttu-id="cd3a4-140">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-140">This example produces the following output:</span></span>

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a><span data-ttu-id="cd3a4-141">XDocument の XML 宣言ノードはプロパティであり、子ノードではない</span><span class="sxs-lookup"><span data-stu-id="cd3a4-141">The XML declaration node of an XDocument is a property, not a child node</span></span>

<span data-ttu-id="cd3a4-142"><xref:System.Xml.Linq.XDocument> の子ノードを反復処理しても、XML 宣言オブジェクトは生成されません。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-142">When you iterate through the child nodes of an <xref:System.Xml.Linq.XDocument>, you won't see the XML declaration object.</span></span> <span data-ttu-id="cd3a4-143">これはドキュメントのプロパティであって、その子ノードではありません。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-143">It's a property of the document, not a child node of it.</span></span>

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

<span data-ttu-id="cd3a4-144">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd3a4-144">This example produces the following output:</span></span>

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
