---
title: XmlReader にシリアル化する (XSLT の呼び出し) - LINQ to XML
description: CreateReader を使用すると、XML ツリーのノードを XSLT 変換に提供する XmlReader を作成できます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: e079627b5fe114438feabaa1a49f42a65afedf43
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412184"
---
# <a name="serialize-to-an-xmlreader-invoke-xslt-linq-to-xml"></a><span data-ttu-id="dff60-103">XmlReader にシリアル化する (XSLT の呼び出し) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="dff60-103">Serialize to an XmlReader (invoke XSLT) (LINQ to XML)</span></span>

<span data-ttu-id="dff60-104">LINQ to XML の <xref:System.Xml?displayProperty=nameWithType> 相互運用機能を使用する場合、<xref:System.Xml.Linq.XNode.CreateReader%2A> を使用して <xref:System.Xml.XmlReader> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="dff60-104">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of LINQ to XML, you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="dff60-105">この <xref:System.Xml.XmlReader> から読み取りを行うモジュールは、XML ツリーからノードを読み取って適宜処理します。</span><span class="sxs-lookup"><span data-stu-id="dff60-105">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>

## <a name="example-invoke-an-xslt-transformation"></a><span data-ttu-id="dff60-106">例: XSLT 変換を呼び出す</span><span class="sxs-lookup"><span data-stu-id="dff60-106">Example: Invoke an XSLT transformation</span></span>

<span data-ttu-id="dff60-107">このメソッドは、XSLT 変換を呼び出すときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="dff60-107">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="dff60-108">この例では、XML ツリーを作成し、この XML ツリーから <xref:System.Xml.XmlReader> を作成して、新しいドキュメントを作成します。次に、この新しいドキュメントに書き込むために <xref:System.Xml.XmlWriter> を作成します。</span><span class="sxs-lookup"><span data-stu-id="dff60-108">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="dff60-109">次に、XSLT 変換を呼び出して、<xref:System.Xml.XmlReader> と <xref:System.Xml.XmlWriter> を渡します。</span><span class="sxs-lookup"><span data-stu-id="dff60-109">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="dff60-110">変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="dff60-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>

```csharp
string xslMarkup = @"<?xml version='1.0'?>
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>
    <xsl:template match='/Parent'>
        <Root>
            <C1>
            <xsl:value-of select='Child1'/>
            </C1>
            <C2>
            <xsl:value-of select='Child2'/>
            </C2>
        </Root>
    </xsl:template>
</xsl:stylesheet>";

XDocument xmlTree = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

XDocument newTree = new XDocument();
using (XmlWriter writer = newTree.CreateWriter()) {
    // Load the style sheet.
    XslCompiledTransform xslt = new XslCompiledTransform();
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));

    // Execute the transformation and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer);
}

Console.WriteLine(newTree);
```

```vb
Dim xslMarkup As XDocument = _
    <?xml version='1.0'?>
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>
        <xsl:template match='/Parent'>
            <Root>
                <C1>
                    <xsl:value-of select='Child1'/>
                </C1>
                <C2>
                    <xsl:value-of select='Child2'/>
                </C2>
            </Root>
        </xsl:template>
    </xsl:stylesheet>

Dim xmlTree As XDocument = _
    <?xml version='1.0'?>
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()
Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transformation and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer)
End Using

Console.WriteLine(newTree)
```

<span data-ttu-id="dff60-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="dff60-111">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```
