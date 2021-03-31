---
title: XSLT を使用して XML ツリーを変換する - LINQ to XML
description: XSLT を使用して XML ツリーを変換する方法について説明します。読み取りには XmlReader を、書き込みには XmlWriter を使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 9a8f85b4f563d177d00d41feeac6fd8cd61375a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411997"
---
# <a name="use-xslt-to-transform-an-xml-tree-linq-to-xml"></a><span data-ttu-id="ac9e5-103">XSLT を使用して XML ツリーを変換する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ac9e5-103">Use XSLT to transform an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="ac9e5-104">XSLT を使用して XML ツリーを変換できます。読み取りには <xref:System.Xml.XmlReader> を、書き込みには <xref:System.Xml.XmlWriter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-104">You can use XSLT to transform an XML tree, using <xref:System.Xml.XmlReader> to read and <xref:System.Xml.XmlWriter> to write.</span></span>

## <a name="example-use-xslt-to-transform-an-xml-tree-using-xmlreader-to-read-and-xmlwriter-to-write"></a><span data-ttu-id="ac9e5-105">例: XSLT を使用して XML ツリーを変換する。読み取りには `XMLReader` を、書き込みには `XMLWriter` を使用する。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-105">Example: Use XSLT to transform an XML tree, using `XMLReader` to read and `XMLWriter` to write</span></span>

<span data-ttu-id="ac9e5-106">この例では XML ツリーを作成し、XSLT を使用してそれを変換します。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-106">This example creates an XML tree and uses XSLT to transform it.</span></span> <span data-ttu-id="ac9e5-107"><xref:System.Xml.XmlReader> を使用して元のツリーを読み取り、変換後のバージョンを <xref:System.Xml.XmlWriter> を使用して書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-107">It makes use of an <xref:System.Xml.XmlReader> to read the original tree, and an <xref:System.Xml.XmlWriter> to write the transformed version.</span></span>

<span data-ttu-id="ac9e5-108">まず、以下が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-108">It starts by creating:</span></span>

- <span data-ttu-id="ac9e5-109">XML ツリー。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-109">An XML tree.</span></span>
- <span data-ttu-id="ac9e5-110">XML ツリーの <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-110">An <xref:System.Xml.XmlReader> of the XML tree.</span></span>
- <span data-ttu-id="ac9e5-111">XSLT 出力を保持する新しいドキュメント。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-111">A new document to hold the XSLT output.</span></span>
- <span data-ttu-id="ac9e5-112">変換後のツリーを新しいドキュメントに書き込むための <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-112">An <xref:System.Xml.XmlWriter> to write the transformed tree to the new document.</span></span>

<span data-ttu-id="ac9e5-113">次に、<xref:System.Xml.XmlReader> を使用して元の XML ツリーを読み取り、変換後のツリーを <xref:System.Xml.XmlWriter> を使用して新しいドキュメントに書き込む XSLT 変換が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-113">It then invokes an XSLT transformation that uses the <xref:System.Xml.XmlReader> to read the original XML tree, and the <xref:System.Xml.XmlWriter> to write the transformed tree to the new document.</span></span>

```csharp
string xslt = @"<?xml version='1.0'?>
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

var oldDocument = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

var newDocument = new XDocument();

using (var stringReader = new StringReader(xslt))
{
    using (XmlReader xsltReader = XmlReader.Create(stringReader))
    {
        var transformer = new XslCompiledTransform();
        transformer.Load(xsltReader);
        using (XmlReader oldDocumentReader = oldDocument.CreateReader())
        {
            using (XmlWriter newDocumentWriter = newDocument.CreateWriter())
            {
                transformer.Transform(oldDocumentReader, newDocumentWriter);
            }
        }
    }
}

string result = newDocument.ToString();
Console.WriteLine(result);
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

Dim xmlTree As XElement = _
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()

Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = _
        New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transform and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer)
End Using

Console.WriteLine(newTree)
```

<span data-ttu-id="ac9e5-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ac9e5-114">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="ac9e5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac9e5-115">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
