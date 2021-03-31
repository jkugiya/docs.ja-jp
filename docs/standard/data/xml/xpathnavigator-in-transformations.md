---
description: '詳細情報: 変換における XPathNavigator'
title: 変換における XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
ms.openlocfilehash: 0f939dca7ef941a444ca90d7afc5edfe6ce7ba8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782573"
---
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="a84a3-103">変換における XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a84a3-103">XPathNavigator in Transformations</span></span>

<span data-ttu-id="a84a3-104"><xref:System.Xml.XPath.XPathNavigator> クラスは、データへの読み取り専用のランダム アクセスを提供し、XSLT (Extensible Stylesheet Language for Transformations) への入力として使用することを目的に設計されています。</span><span class="sxs-lookup"><span data-stu-id="a84a3-104">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="a84a3-105">このクラスは、<xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDataDocument>、および <xref:System.Xml.XmlDocument> に実装されます。</span><span class="sxs-lookup"><span data-stu-id="a84a3-105">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="a84a3-106"><xref:System.Xml.XPath.XPathNavigator> は、『XML Path Language (XPath)』勧告のセクション 5 で規定されている W3C (World Wide Web Consortium) データ モデルに準拠しています。</span><span class="sxs-lookup"><span data-stu-id="a84a3-106">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="a84a3-107"><xref:System.Xml.XPath.XPathNavigator> は、任意のストアに対するカーソル モデルを定義し、任意のデータ ストアに対する高速で読み取り専用の XPath クエリを提供します。</span><span class="sxs-lookup"><span data-stu-id="a84a3-107">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="a84a3-108"><xref:System.Xml.XPath.XPathNavigator> クラスは、結果ツリー フラグメントの反復処理でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="a84a3-108">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="a84a3-109">この API を使用すると、ストア内の現在のノードから情報を取得し、接続されているノードに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="a84a3-109">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="a84a3-110"><xref:System.Xml.XPath.XPathNavigator> は、一連の **Move** メソッドを使用してストアの走査を実行するカーソル スタイルのモデルです。</span><span class="sxs-lookup"><span data-stu-id="a84a3-110">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="a84a3-111"><xref:System.Xml.XPath.XPathNavigator> は、常にノード上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="a84a3-111">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="a84a3-112">**Move** メソッドが失敗した場合、<xref:System.Xml.XPath.XPathNavigator> は変更されません。</span><span class="sxs-lookup"><span data-stu-id="a84a3-112">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="a84a3-113"><xref:System.Xml.XPath.XPathNavigator> クラスは、結果ツリー フラグメントの反復処理で使用されます。</span><span class="sxs-lookup"><span data-stu-id="a84a3-113">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="a84a3-114">XML を含む `fragment` パラメーターを指定して関数を呼び出すことにより、スタイル シート内で結果ツリー フラグメントを作成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a84a3-114">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="a84a3-115">test.xsl</span><span class="sxs-lookup"><span data-stu-id="a84a3-115">test.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl ="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
  
<xsl:variable name="fragment">  
    <authorlist>  
       <author>Joe</author>  
    </authorlist>  
</xsl:variable>  
  
<msxsl:script language="C#" implements-prefix="user">  
<![CDATA[  
   string NodeFragment(XPathNavigator nav)  
   {  
      if (nav.HasChildren)  
        return nav.Value;  
      else  
        return "";  
   }  
]]>  
</msxsl:script>  
  
<xsl:template match="/">  
     <xsl:value-of select="user:NodeFragment($fragment)"/>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a><span data-ttu-id="a84a3-116">test.xml</span><span class="sxs-lookup"><span data-stu-id="a84a3-116">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="a84a3-117">次の例では、**test.xsl** スタイル シートと **test.xml** 入力データを使用しています。</span><span class="sxs-lookup"><span data-stu-id="a84a3-117">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
Public Class sample  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load("test.xsl")  
  
        Dim xd As New XPathDocument("test.xml")  
  
        Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
        xslt.Transform(xd, Nothing, strmTemp, Nothing)  
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
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, null, strmTemp, null);  
    }  
}  
```  
  
## <a name="output"></a><span data-ttu-id="a84a3-118">Output</span><span class="sxs-lookup"><span data-stu-id="a84a3-118">Output</span></span>  

 <span data-ttu-id="a84a3-119">変換結果はファイル **out.xml** に出力されます。</span><span class="sxs-lookup"><span data-stu-id="a84a3-119">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="a84a3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a84a3-120">See also</span></span>

- [<span data-ttu-id="a84a3-121">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="a84a3-121">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
