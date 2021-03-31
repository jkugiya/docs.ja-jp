---
title: 異なる構造の XML を射影する - LINQ to XML
description: ソース XML とは異なる構造の XML を射影する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4cb6b14a-32dc-4a2a-813e-bf9368fa8d86
ms.openlocfilehash: 512e8f754c0e7b6c84d7265a676a0f69beb1baa1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412084"
---
# <a name="project-xml-in-a-different-shape-linq-to-xml"></a><span data-ttu-id="a217c-103">異なる構造の XML を射影する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a217c-103">Project XML in a different shape (LINQ to XML)</span></span>

<span data-ttu-id="a217c-104">この記事では、ソース XML とは異なる構造の XML を射影する例を示します。</span><span class="sxs-lookup"><span data-stu-id="a217c-104">This article shows an example of projecting XML in a shape that differs from the source XML.</span></span>

<span data-ttu-id="a217c-105">一般的な XML 変換の多くは、この例のように連結されたクエリで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a217c-105">Many typical XML transformations consist of chained queries, as in this example.</span></span> <span data-ttu-id="a217c-106">通常、ある形式の XML から開始して、中間結果を匿名型または名前付き型のコレクションとして射影してから、その結果をソース XML とはまったく異なる構造の XML に射影します。</span><span class="sxs-lookup"><span data-stu-id="a217c-106">It's common to start with some form of XML, project intermediate results as collections of anonymous types or named types, and then project the results back into XML of an entirely different shape from the source XML.</span></span>

## <a name="example-retrieve-paragraph-nodes-and-identify-the-style-and-text-of-each-paragraph"></a><span data-ttu-id="a217c-107">例: 段落ノードを取得し、各段落のスタイルとテキストを識別する</span><span class="sxs-lookup"><span data-stu-id="a217c-107">Example: Retrieve paragraph nodes and identify the style and text of each paragraph</span></span>

<span data-ttu-id="a217c-108">この例では、WordprocessingML ドキュメントから段落ノードを取得し、各段落のスタイルとテキストを識別します。</span><span class="sxs-lookup"><span data-stu-id="a217c-108">This example retrieves the paragraph nodes from a WordprocessingML document and identifies the style and text of each paragraph.</span></span> <span data-ttu-id="a217c-109">次に、異なる構造の XML を射影します。</span><span class="sxs-lookup"><span data-stu-id="a217c-109">Then it projects XML of a different shape.</span></span> <span data-ttu-id="a217c-110">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a217c-110">The example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="a217c-111">射影を実行するために追加されたステートメントは、コード内のコメントによって指摘されます。</span><span class="sxs-lookup"><span data-stu-id="a217c-111">The statement that was added to do the projection is pointed out by comments in the code.</span></span>

<span data-ttu-id="a217c-112">この例のソース ドキュメントを作成する方法の手順については、「[ソースとなる Office Open XML ドキュメントを作成する](create-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a217c-112">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="a217c-113">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a217c-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="a217c-114">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="a217c-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
public static class LocalExtensions
{
    public static string StringConcatenate(this IEnumerable<string> source)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item));
        return sb.ToString();
    }

    public static string StringConcatenate(this IEnumerable<string> source, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s).Append(separator);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item)).Append(separator);
        return sb.ToString();
    }
}

class Program
{
    public static string ParagraphText(XElement e)
    {
        XNamespace w = e.Name.Namespace;
        return e
               .Elements(w + "r")
               .Elements(w + "t")
               .StringConcatenate(element => (string)element);
    }

    static void Main(string[] args)
    {
        const string fileName = "SampleDoc.docx";

        const string documentRelationshipType =
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
        const string stylesRelationshipType =
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
        const string wordmlNamespace =
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
        XNamespace w = wordmlNamespace;

        XDocument xDoc = null;
        XDocument styleDoc = null;

        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
        {
            PackageRelationship docPackageRelationship =
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
            if (docPackageRelationship != null)
            {
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),
                  docPackageRelationship.TargetUri);
                PackagePart documentPart = wdPackage.GetPart(documentUri);

                //  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

                //  Find the styles part. There will only be one.
                PackageRelationship styleRelation =
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
                if (styleRelation != null)
                {
                    Uri styleUri =
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
                    PackagePart stylePart = wdPackage.GetPart(styleUri);

                    //  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
                }
            }
        }

        string defaultStyle =
            (string)(
                from style in styleDoc.Root.Elements(w + "style")
                where (string)style.Attribute(w + "type") == "paragraph" &&
                      (string)style.Attribute(w + "default") == "1"
                select style
            ).First().Attribute(w + "styleId");

        // Find all paragraphs in the document.
        var paragraphs =
            from para in xDoc
                         .Root
                         .Element(w + "body")
                         .Descendants(w + "p")
            let styleNode = para
                            .Elements(w + "pPr")
                            .Elements(w + "pStyle")
                            .FirstOrDefault()
            select new
            {
                ParagraphNode = para,
                StyleName = styleNode != null ?
                    (string)styleNode.Attribute(w + "val") :
                    defaultStyle
            };

        // Retrieve the text of each paragraph.
        var paraWithText =
            from para in paragraphs
            select new
            {
                ParagraphNode = para.ParagraphNode,
                StyleName = para.StyleName,
                Text = ParagraphText(para.ParagraphNode)
            };

        // The following is the new code that projects XML in a new shape.
        XElement root = new XElement("Root",
            from p in paraWithText
            select new XElement("Paragraph",
                new XElement("StyleName", p.StyleName),
                new XElement("Text", p.Text)
            )
        );

        Console.WriteLine(root);
    }
}
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As String In source
            sb.Append(s)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item))
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As T In source
            sb.Append(s).Append(separator)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String), ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item)).Append(separator)
        Next
        Return sb.ToString()
    End Function

    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w As XNamespace = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
    End Function

    ' Following function is required because Visual Basic doesn't support short circuit evaluation
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _
                                         ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = _
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"
        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (Not (styleRelation Is Nothing)) Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    '  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        Dim defaultStyle As String = _
            ( _
                From style In styleDoc.Root.<w:style> _
                Where style.@w:type = "paragraph" And _
                      style.@w:default = "1" _
                Select style _
            ).First().@w:styleId

        ' Find all paragraphs in the document.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        ' Retrieve the text of each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = ParagraphText(para.ParagraphNode) _
            }

        ' Following is the new code that projects XML in a new shape
        Dim root As XElement = _
            <Root>
                <%= _
                    From p In paraWithText _
                    Select _
                    <Paragraph>
                        <StyleName><%= p.StyleName %></StyleName>
                        <Text><%= p.Text %></Text>
                    </Paragraph> _
                %>
            </Root>

        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="a217c-115">この例の C# バージョンでは、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a217c-115">The C# version of this example produces the following output:</span></span>

```xml
<Root>
  <Paragraph>
    <StyleName>Heading1</StyleName>
    <Text>Parsing WordprocessingML with LINQ to XML</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text>The following example prints to the console.</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>using System;</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>class Program {</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>    public static void (string[] args) {</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>        Console.WriteLine("Hello World");</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>    }</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>}</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text>This example produces the following output:</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>Hello World</Text>
  </Paragraph>
</Root>
```

<span data-ttu-id="a217c-116">この例の Visual Basic バージョンでは、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a217c-116">The Visual Basic version of this example produces the following output:</span></span>

```xml
<Root>
  <Paragraph>
    <StyleName>Heading1</StyleName>
    <Text>Parsing WordprocessingML with LINQ to XML</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text>The following example prints to the console.</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>Imports System</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>Class Program</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>    Public Shared  Sub Main(ByVal args() As String)</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>        Console.WriteLine("Hello World")</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>    End Sub</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>End Class</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text>This example produces the following output:</Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Normal</StyleName>
    <Text></Text>
  </Paragraph>
  <Paragraph>
    <StyleName>Code</StyleName>
    <Text>Hello World</Text>
  </Paragraph>
</Root>
```

<span data-ttu-id="a217c-117">このチュートリアルの次の記事では、Word 文書内のすべてのテキストを検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a217c-117">The next article in this tutorial shows how to find all the text in a Word document:</span></span>

- [<span data-ttu-id="a217c-118">Word 文書内のテキストを検索する</span><span class="sxs-lookup"><span data-stu-id="a217c-118">Find text in Word documents</span></span>](find-text-word-documents.md)

## <a name="see-also"></a><span data-ttu-id="a217c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a217c-119">See also</span></span>

- [<span data-ttu-id="a217c-120">チュートリアル: WordprocessingML ドキュメント内のコンテンツを操作する</span><span class="sxs-lookup"><span data-stu-id="a217c-120">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
