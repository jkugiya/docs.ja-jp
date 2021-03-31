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
# <a name="use-xslt-to-transform-an-xml-tree-linq-to-xml"></a>XSLT を使用して XML ツリーを変換する (LINQ to XML)

XSLT を使用して XML ツリーを変換できます。読み取りには <xref:System.Xml.XmlReader> を、書き込みには <xref:System.Xml.XmlWriter> を使用します。

## <a name="example-use-xslt-to-transform-an-xml-tree-using-xmlreader-to-read-and-xmlwriter-to-write"></a>例: XSLT を使用して XML ツリーを変換する。読み取りには `XMLReader` を、書き込みには `XMLWriter` を使用する。

この例では XML ツリーを作成し、XSLT を使用してそれを変換します。 <xref:System.Xml.XmlReader> を使用して元のツリーを読み取り、変換後のバージョンを <xref:System.Xml.XmlWriter> を使用して書き込みます。

まず、以下が作成されます。

- XML ツリー。
- XML ツリーの <xref:System.Xml.XmlReader>。
- XSLT 出力を保持する新しいドキュメント。
- 変換後のツリーを新しいドキュメントに書き込むための <xref:System.Xml.XmlWriter>。

次に、<xref:System.Xml.XmlReader> を使用して元の XML ツリーを読み取り、変換後のツリーを <xref:System.Xml.XmlWriter> を使用して新しいドキュメントに書き込む XSLT 変換が呼び出されます。

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

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
