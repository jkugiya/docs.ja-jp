---
description: '詳細情報: XslTransform への XPathDocument の入力'
title: XslTransform への XPathDocument の入力
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
ms.openlocfilehash: 5778a359cd4bfa748318533c9be6a1def97b5be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782586"
---
# <a name="xpathdocument-input-to-xsltransform"></a><span data-ttu-id="1844e-103">XslTransform への XPathDocument の入力</span><span class="sxs-lookup"><span data-stu-id="1844e-103">XPathDocument Input to XslTransform</span></span>

<span data-ttu-id="1844e-104"><xref:System.Xml.XPath.XPathDocument> は、<xref:System.Xml.Xsl.XslTransform> でドキュメントを処理するための読み取り専用キャッシュです。</span><span class="sxs-lookup"><span data-stu-id="1844e-104">The <xref:System.Xml.XPath.XPathDocument> is a read-only cache, for processing documents with <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="1844e-105"><xref:System.Xml.XPath.XPathNavigator> は、構造的には XML ドキュメント オブジェクト モデル (DOM) に似ていますが、 で XPath 最適化関数を使用することで、XSLT (Extensible Stylesheet Language for Transformations) による処理と XPath (XML Path Language) データ モデルに高度に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="1844e-105">It is structurally similar to the XML Document Object Model (DOM), but it is highly optimized for Extensible Stylesheet Language for Transformations (XSLT) processing and the XML Path Language (XPath) data model using the XPath optimization functions on the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1844e-106">.NET Framework 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="1844e-106">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="1844e-107"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="1844e-107">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="1844e-108">詳しくは、「[XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](migrating-from-the-xsltransform-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1844e-108">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="1844e-109">変換への入力として <xref:System.Xml.XPath.XPathDocument> を作成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1844e-109">The following code sample creates an <xref:System.Xml.XPath.XPathDocument> as input to a transform.</span></span>  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## <a name="see-also"></a><span data-ttu-id="1844e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1844e-110">See also</span></span>

- [<span data-ttu-id="1844e-111">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="1844e-111">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
