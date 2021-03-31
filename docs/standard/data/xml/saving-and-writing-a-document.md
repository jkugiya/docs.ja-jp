---
description: '詳細情報: ドキュメントの保存と書き込み'
title: ドキュメントの保存と書き込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: c5d91a2ec057272db87d7d3fd8146be34ec2b76e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783002"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="cfc62-103">ドキュメントの保存と書き込み</span><span class="sxs-lookup"><span data-stu-id="cfc62-103">Saving and Writing a Document</span></span>

<span data-ttu-id="cfc62-104"><xref:System.Xml.XmlDocument> を読み込んで保存した場合、保存されたドキュメントは、元のドキュメントとは次のように異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cfc62-104">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="cfc62-105"><xref:System.Xml.XmlDocument.PreserveWhitespace%2A> メソッドを呼び出す前に `true` プロパティが <xref:System.Xml.XmlDocument.Save%2A> に設定されている場合は、ドキュメント内の空白が出力でも保持されますが、`false` に設定されている場合は、<xref:System.Xml.XmlDocument> が出力を自動的にインデントします。</span><span class="sxs-lookup"><span data-stu-id="cfc62-105">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="cfc62-106">属性間のすべての空白は 1 つの空白文字になります。</span><span class="sxs-lookup"><span data-stu-id="cfc62-106">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="cfc62-107">要素間の空白が変更されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-107">The white space between elements is changed.</span></span> <span data-ttu-id="cfc62-108">有意の空白は保持され、意味のない空白は保持されません。</span><span class="sxs-lookup"><span data-stu-id="cfc62-108">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="cfc62-109">しかしながら、ドキュメントの保存時には、出力が読みやすくなるように、既定で <xref:System.Xml.XmlTextWriter> の **インデント** モードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-109">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="cfc62-110">属性値を囲む引用符は、既定で二重引用符に変更されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-110">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="cfc62-111"><xref:System.Xml.XmlTextReader.QuoteChar%2A> の <xref:System.Xml.XmlTextWriter> プロパティを使用すると、引用符を二重引用符または一重引用符のいずれかに設定できます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-111">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="cfc62-112">既定では、`{` のような数値エンティティは展開されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-112">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="cfc62-113">入力ドキュメントのバイト順マークは保持されません。</span><span class="sxs-lookup"><span data-stu-id="cfc62-113">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="cfc62-114">別のエンコーディングを指定する XML 宣言を明示的に作成しない限り、UCS-2 は UTF-8 として保存されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-114">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="cfc62-115"><xref:System.Xml.XmlDocument> をファイルまたはストリームに書き出す場合、書き出される出力はドキュメントのコンテンツと同じになります。</span><span class="sxs-lookup"><span data-stu-id="cfc62-115">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="cfc62-116">つまり、<xref:System.Xml.XmlDeclaration> が書き出されるのは、ドキュメントに  が 1 つ含まれていて、ドキュメントの出力時に使われるエンコーディングが宣言ノードで指定されたエンコーディングと同じ場合だけです。</span><span class="sxs-lookup"><span data-stu-id="cfc62-116">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="cfc62-117">XmlDeclaration の書き込み</span><span class="sxs-lookup"><span data-stu-id="cfc62-117">Writing an XmlDeclaration</span></span>  

 <span data-ttu-id="cfc62-118"><xref:System.Xml.XmlDocument> および <xref:System.Xml.XmlDeclaration> の <xref:System.Xml.XmlNode.OuterXml%2A> メソッドに加えて、<xref:System.Xml.XmlNode.InnerXml%2A>、<xref:System.Xml.XmlNode.WriteTo%2A>、および <xref:System.Xml.XmlDocument> の <xref:System.Xml.XmlDocument.Save%2A> および <xref:System.Xml.XmlDocument.WriteContentTo%2A> メンバーは XML 宣言を作成します。</span><span class="sxs-lookup"><span data-stu-id="cfc62-118">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="cfc62-119"><xref:System.Xml.XmlDocument>、<xref:System.Xml.XmlNode.OuterXml%2A> の <xref:System.Xml.XmlDocument.InnerXml%2A> プロパティ、<xref:System.Xml.XmlDocument.Save%2A>、<xref:System.Xml.XmlDocument.WriteTo%2A> メソッド、および <xref:System.Xml.XmlDocument.WriteContentTo%2A> メソッドについて、XML 宣言に書き出されるエンコーディングは <xref:System.Xml.XmlDeclaration> ノードから取り出されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-119">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="cfc62-120"><xref:System.Xml.XmlDeclaration> ノードが存在しない場合、<xref:System.Xml.XmlDeclaration> は書き出されません。<xref:System.Xml.XmlDeclaration> ノードにエンコーディングが含まれていない場合、エンコーディングは XML 宣言に書き出されません。</span><span class="sxs-lookup"><span data-stu-id="cfc62-120">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="cfc62-121"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> および <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> メソッドは、常に <xref:System.Xml.XmlDeclaration> を書き出します。</span><span class="sxs-lookup"><span data-stu-id="cfc62-121">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="cfc62-122">これらのメソッドは、書き込みを行っているライターからエンコーディングを取得します。</span><span class="sxs-lookup"><span data-stu-id="cfc62-122">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="cfc62-123">つまり、ライターのエンコーディングの値によって、ドキュメントと <xref:System.Xml.XmlDeclaration> オブジェクトのエンコーディングがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-123">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="cfc62-124">たとえば、次のコードでは、出力ファイル `out.xml` の XML 宣言にはエンコーディングは書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="cfc62-124">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="cfc62-125"><xref:System.Xml.XmlDocument.Save%2A> メソッドでは、<xref:System.Xml.XmlWriter.WriteStartDocument%2A> クラスの <xref:System.Xml.XmlWriter> メソッドを使用して XML 宣言が書き出されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-125">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="cfc62-126">そのため、<xref:System.Xml.XmlWriter.WriteStartDocument%2A> メソッドをオーバーライドすると、ドキュメントの先頭部分の出力方法が変わります。</span><span class="sxs-lookup"><span data-stu-id="cfc62-126">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="cfc62-127"><xref:System.Xml.XmlDeclaration>、<xref:System.Xml.XmlNode.OuterXml%2A>、および <xref:System.Xml.XmlDeclaration.WriteTo%2A> の <xref:System.Xml.XmlNode.InnerXml%2A> メンバーについて、<xref:System.Xml.XmlDeclaration.Encoding%2A> プロパティが設定されていないと、エンコーディングは書き出されません。それ以外の場合は、<xref:System.Xml.XmlDeclaration.Encoding%2A> プロパティ内に見られるエンコーディングと同じエンコーディングが XML 宣言に書き出されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-127">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="cfc62-128">OuterXml プロパティを使用したドキュメント内容の書き込み</span><span class="sxs-lookup"><span data-stu-id="cfc62-128">Writing Document Content Using the OuterXml Property</span></span>  

 <span data-ttu-id="cfc62-129"><xref:System.Xml.XmlNode.OuterXml%2A> プロパティは、W3C XML ドキュメント オブジェクト モデル (DOM) 標準に対するマイクロソフトの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="cfc62-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="cfc62-130"><xref:System.Xml.XmlNode.OuterXml%2A> プロパティは、XML ドキュメント全体のマークアップ、または 1 つのノードとその子ノードのマークアップだけを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cfc62-130">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="cfc62-131"><xref:System.Xml.XmlNode.OuterXml%2A> は、指定されたノードとそのすべての子ノードを表すマークアップを返します。</span><span class="sxs-lookup"><span data-stu-id="cfc62-131"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="cfc62-132">ドキュメント全体を文字列として保存するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cfc62-132">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="cfc62-133">ドキュメント要素だけを保存するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cfc62-133">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="cfc62-134">一方、子ノードの内容が必要な場合は、<xref:System.Xml.XmlNode.InnerText%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="cfc62-134">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc62-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfc62-135">See also</span></span>

- [<span data-ttu-id="cfc62-136">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="cfc62-136">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
