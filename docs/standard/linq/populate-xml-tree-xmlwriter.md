---
title: XmlWriter を使用して XML ツリーを設定する方法 - LINQ to XML
description: C# と Visual Basic で XML ツリーを設定するには、CreateWriter を使用して XMLWriter を作成し、XmlWriter に書き込みます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 3f8005eca009ae5f2102444a5494336d2caa2450
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366004"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml"></a><span data-ttu-id="576a4-103">XmlWriter を使用して XML ツリーを設定する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="576a4-103">How to populate an XML tree with an XmlWriter (LINQ to XML)</span></span>

<span data-ttu-id="576a4-104">XML ツリーを設定する方法の 1 つは、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> を使用して <xref:System.Xml.XmlWriter> を作成し、この <xref:System.Xml.XmlWriter> に書き込みを行うことです。</span><span class="sxs-lookup"><span data-stu-id="576a4-104">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="576a4-105">XML ツリーには、<xref:System.Xml.XmlWriter> に書き込まれたすべてのノードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="576a4-105">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="576a4-106">通常、この方法は、LINQ to XML と、<xref:System.Xml.XmlWriter> への書き込みを必要とする別のクラス (<xref:System.Xml.Xsl.XslCompiledTransform> など) を併用する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="576a4-106">You'd typically use this method when you use LINQ to XML with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

## <a name="example-create-an-xmlwriter-to-accept-the-output-of-an-xslt-transformation"></a><span data-ttu-id="576a4-107">例: XmlWriter を作成し、XSLT 変換の出力を受け取る</span><span class="sxs-lookup"><span data-stu-id="576a4-107">Example: Create an XmlWriter to accept the output of an XSLT transformation</span></span>

<span data-ttu-id="576a4-108"><xref:System.Xml.Linq.XContainer.CreateWriter%2A> を使用することで、XSLT 変換の出力を受け取る <xref:System.Xml.XmlWriter> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="576a4-108">You can use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter> to accept the output of an XSLT transformation.</span></span> <span data-ttu-id="576a4-109">これは次の例で示されています。例では次が行われています。</span><span class="sxs-lookup"><span data-stu-id="576a4-109">This is shown in the following example, which does the following:</span></span>

- <span data-ttu-id="576a4-110">XML ツリーとそれから読み取るための <xref:System.Xml.XmlReader> を作成します。</span><span class="sxs-lookup"><span data-stu-id="576a4-110">Creates an XML tree and an <xref:System.Xml.XmlReader> to read from it.</span></span>
- <span data-ttu-id="576a4-111">新しいツリーとそれに書き込むための <xref:System.Xml.XmlWriter> を作成します。</span><span class="sxs-lookup"><span data-stu-id="576a4-111">Creates a new tree and an <xref:System.Xml.XmlWriter> to write to it.</span></span>
- <span data-ttu-id="576a4-112">XSLT 変換を呼び出し、それに <xref:System.Xml.XmlReader> と <xref:System.Xml.XmlWriter> を指定します。</span><span class="sxs-lookup"><span data-stu-id="576a4-112">Invokes the XSLT transformation, providing it with the  <xref:System.Xml.XmlReader> and the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="576a4-113">変換によって新しいツリーが設定されます。</span><span class="sxs-lookup"><span data-stu-id="576a4-113">The transformation then populates the new tree.</span></span>

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
using (XmlWriter writer = newTree.CreateWriter())
{
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

<span data-ttu-id="576a4-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="576a4-114">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="576a4-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="576a4-115">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="576a4-116">XML ツリー</span><span class="sxs-lookup"><span data-stu-id="576a4-116">XML trees</span></span>](functional-construction.md)
