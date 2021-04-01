---
description: '詳細情報: XPathNavigator を使用した XML データの抽出'
title: XpathNavigator を使用した XML データの抽出
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: f7a908a419bee9dcc9e4b2d384bb46c4794ef80b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713872"
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="bcd7a-103">XpathNavigator を使用した XML データの抽出</span><span class="sxs-lookup"><span data-stu-id="bcd7a-103">Extract XML Data Using XPathNavigator</span></span>

<span data-ttu-id="bcd7a-104">Microsoft .NET Framework において XML ドキュメントを表現する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-104">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="bcd7a-105">これには、<xref:System.String> を使用する方法、または <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、<xref:System.Xml.XmlDocument>、<xref:System.Xml.XPath.XPathDocument> クラスを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-105">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="bcd7a-106">XML ドキュメントの異なる表現の間での移行を容易にするため、<xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.String>, <xref:System.Xml.XmlReader> オブジェクトまたは <xref:System.Xml.XmlWriter> オブジェクトとして XML を抽出するためのメソッドおよびプロパティを多数提供しています。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-106">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="bcd7a-107">XPathNavigator から文字列への変換</span><span class="sxs-lookup"><span data-stu-id="bcd7a-107">Convert an XPathNavigator to a String</span></span>  

 <span data-ttu-id="bcd7a-108"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> プロパティは、XML ドキュメント全体のマークアップ、または 1 つのノードとその子ノードのマークアップだけを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-108">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcd7a-109"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティは、ノードの子ノードのマークアップだけを取得します。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-109">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="bcd7a-110">以下は、1 つのノードとその子ノードを保存する方法と、<xref:System.Xml.XPath.XPathNavigator> オブジェクトに含まれる XML ドキュメント全体を <xref:System.String> として保存する方法について説明するサンプル コードです。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-110">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="bcd7a-111">XPathNavigator から XmlReader への変換</span><span class="sxs-lookup"><span data-stu-id="bcd7a-111">Convert an XPathNavigator to an XmlReader</span></span>  

 <span data-ttu-id="bcd7a-112"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> メソッドは、XML ドキュメントのコンテンツ全体、または 1 つのノードとその子ノードを <xref:System.Xml.XmlReader> オブジェクトにストリーム出力するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-112">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="bcd7a-113"><xref:System.Xml.XmlReader> オブジェクトが現在のノードとその子で作成されている場合、<xref:System.Xml.XmlReader> オブジェクトの <xref:System.Xml.XmlReader.ReadState%2A> プロパティは <xref:System.Xml.ReadState.Initial> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-113">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="bcd7a-114"><xref:System.Xml.XmlReader> オブジェクトの <xref:System.Xml.XmlReader.Read%2A> メソッドが初めて呼び出されたときに、<xref:System.Xml.XmlReader> が <xref:System.Xml.XPath.XPathNavigator> の現在のノードに移動されます。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-114">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="bcd7a-115">新しい <xref:System.Xml.XmlReader> オブジェクトは、XML ツリーの末尾に到達するまで読み取りを継続します。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-115">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="bcd7a-116">この時点で、<xref:System.Xml.XmlReader.Read%2A> メソッドは `false` を返し、<xref:System.Xml.XmlReader> オブジェクトの <xref:System.Xml.XmlReader.ReadState%2A> プロパティは <xref:System.Xml.ReadState.EndOfFile> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-116">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="bcd7a-117"><xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置は、<xref:System.Xml.XmlReader> オブジェクトの作成または移動によって変更されことはありません。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-117">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="bcd7a-118"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> メソッドは、要素ノードまたはルート ノードに位置している場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-118">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="bcd7a-119">1 つのノードとその子ノードを取得する方法と、<xref:System.Xml.XmlReader> オブジェクト内の XML ドキュメント全体を含む <xref:System.Xml.XPath.XPathDocument> オブジェクトを取得する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-119">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 <span data-ttu-id="bcd7a-120">この例は、`books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-120">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="bcd7a-121">XPathNavigator から XmlWriter への変換</span><span class="sxs-lookup"><span data-stu-id="bcd7a-121">Converting an XPathNavigator to an XmlWriter</span></span>  

 <span data-ttu-id="bcd7a-122"><xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> メソッドは、XML ドキュメントのコンテンツ全体、または 1 つのノードとその子ノードを <xref:System.Xml.XmlWriter> オブジェクトにストリーム出力するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-122">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="bcd7a-123"><xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置は、<xref:System.Xml.XmlWriter> オブジェクトの作成によって変更されことはありません。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-123">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="bcd7a-124">1 つのノードとその子ノードを取得する方法と、<xref:System.Xml.XmlWriter> オブジェクト内の XML ドキュメント全体を含む <xref:System.Xml.XPath.XPathDocument> オブジェクトを取得する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-124">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 <span data-ttu-id="bcd7a-125">この例は、このトピックの前の方にある `books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd7a-125">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd7a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcd7a-126">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="bcd7a-127">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="bcd7a-127">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="bcd7a-128">XPathNavigator を使用するノード セットのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="bcd7a-128">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="bcd7a-129">XPathNavigator を使用する属性と名前空間のナビゲーション</span><span class="sxs-lookup"><span data-stu-id="bcd7a-129">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="bcd7a-130">厳密に型指定された XML データへの XPathNavigator を使用したアクセス</span><span class="sxs-lookup"><span data-stu-id="bcd7a-130">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
