---
description: '詳細情報: 変換におけるノード セット'
title: 変換におけるノード セット
ms.date: 03/30/2017
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
ms.openlocfilehash: 7a19445548109cd2c649b975974d5233818d0d02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675911"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="a00ad-103">変換におけるノード セット</span><span class="sxs-lookup"><span data-stu-id="a00ad-103">Node Sets in Transformations</span></span>

<span data-ttu-id="a00ad-104">ノード セットは、XPath (XML Path Language) 式が返す 4 つの基本データ型のうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a00ad-104">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="a00ad-105">ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="a00ad-105">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a00ad-106">.NET Framework 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="a00ad-106">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="a00ad-107"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a00ad-107">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a00ad-108">詳しくは、「[XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](migrating-from-the-xsltransform-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a00ad-108">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="a00ad-109">ノード セットは、XPath 式が返す 4 つの基本データ型のうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a00ad-109">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="a00ad-110">ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="a00ad-110">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="a00ad-111">変換の `select` 属性で使用される XPath 式の結果であるこのノード セットは、XML ドキュメント オブジェクト モデル (DOM) のノード セットと同じ動作をします。</span><span class="sxs-lookup"><span data-stu-id="a00ad-111">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="a00ad-112">移動に <xref:System.Xml.XPath.XPathNodeIterator> を使用する結果ツリー フラグメントと異なり、ノード セットの場合は「[Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md)」で説明している各種のメソッドを使用してノード セット間を移動します。</span><span class="sxs-lookup"><span data-stu-id="a00ad-112">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="a00ad-113">スタイル シートの `variable` 要素または `parameter` 要素がノード セットとして評価される場合のノード セットに対する反復処理を、次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="a00ad-113">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="a00ad-114">スタイル シート</span><span class="sxs-lookup"><span data-stu-id="a00ad-114">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="a00ad-115">入力</span><span class="sxs-lookup"><span data-stu-id="a00ad-115">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="a00ad-116">出力</span><span class="sxs-lookup"><span data-stu-id="a00ad-116">Output</span></span>  
  
```output  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="a00ad-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a00ad-117">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="a00ad-118">XslTransform クラスを使用した XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="a00ad-118">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="a00ad-119">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="a00ad-119">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
