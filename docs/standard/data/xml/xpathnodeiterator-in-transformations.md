---
description: '詳細情報: 変換における XPathNodeIterator'
title: 変換における XPathNodeIterator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: 5e27ff243e4ca0a609b4d5c28d941ea84ea5b10d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782560"
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="76679-103">変換における XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="76679-103">XPathNodeIterator in Transformations</span></span>

<span data-ttu-id="76679-104"><xref:System.Xml.XPath.XPathNodeIterator> は、XPath (XML Path Language) クエリの結果として作成されたノード セット、または node-set メソッドを使用して結果ツリー フラグメントから変換されたノード セットの反復処理を行うためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="76679-104">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="76679-105"><xref:System.Xml.XPath.XPathNodeIterator> を使用すれば、そのノード セット内のノードの反復処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="76679-105">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="76679-106">ノード セットが取得されると、<xref:System.Xml.XPath.XPathNodeIterator> クラスは、選択されたノード セットへの読み取り専用、前方参照専用のカーソルを提供します。</span><span class="sxs-lookup"><span data-stu-id="76679-106">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="76679-107">ノード セットはドキュメント順に作成されるため、このメソッドを呼び出すと、ドキュメント順で次のノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="76679-107">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="76679-108"><xref:System.Xml.XPath.XPathNodeIterator> は、セット内のすべてのノードのノード ツリーを構築するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="76679-108"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="76679-109">その代わりに、XPathNodeIterator は、データへの単一ノード ウィンドウを提供し、ツリー内での移動に合わせて、自身が指している基になるノードを公開します。</span><span class="sxs-lookup"><span data-stu-id="76679-109">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="76679-110"><xref:System.Xml.XPath.XPathNodeIterator> クラスで利用できるメソッドとプロパティを使用すると、現在のノードから情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="76679-110">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="76679-111">メソッドとプロパティの一覧については、「<xref:System.Windows.Forms.ToolBar>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76679-111">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="76679-112"><xref:System.Xml.XPath.XPathNodeIterator> は XPath クエリの結果作成されたノード セット内を前方にのみ移動するため、移動するときは <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="76679-112">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="76679-113">このメソッドの戻り値の型は `Boolean` であり、選択されている次のノードに移動すると `true` が返り、選択されているノードがそれ以上ないと `false` が返ります。</span><span class="sxs-lookup"><span data-stu-id="76679-113">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="76679-114">このメソッドが `true` を返した場合は、次のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="76679-114">If it returns `true`, the following list shows the properties available:</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="76679-115">ノード セットを初めて参照するときは、<xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> を呼び出して、選択されているセットの最初のノードに <xref:System.Xml.XPath.XPathNodeIterator> を移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76679-115">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="76679-116">これにより、while ループによる書き込みが可能になります。</span><span class="sxs-lookup"><span data-stu-id="76679-116">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="76679-117"><xref:System.Xml.XPath.XPathNodeIterator> を <xref:System.Xml.Xsl.XslTransform> に <xref:System.Xml.Xsl.XsltArgumentList> 内のパラメーターとして渡すコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="76679-117">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="76679-118">コードへの入力は **books.xml** で、スタイル シートは **text.xsl** です。</span><span class="sxs-lookup"><span data-stu-id="76679-118">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="76679-119">ファイル **test.xml** は、<xref:System.Xml.XPath.XPathDocument> です。</span><span class="sxs-lookup"><span data-stu-id="76679-119">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a><span data-ttu-id="76679-120">books.xml</span><span class="sxs-lookup"><span data-stu-id="76679-120">books.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a><span data-ttu-id="76679-121">test.xsl</span><span class="sxs-lookup"><span data-stu-id="76679-121">test.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a><span data-ttu-id="76679-122">test.xml</span><span class="sxs-lookup"><span data-stu-id="76679-122">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="76679-123">出力 (out.xml)</span><span class="sxs-lookup"><span data-stu-id="76679-123">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76679-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="76679-124">See also</span></span>

- [<span data-ttu-id="76679-125">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="76679-125">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
