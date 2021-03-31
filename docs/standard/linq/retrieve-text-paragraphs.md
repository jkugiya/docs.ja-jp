---
title: 段落のテキストを取得する - LINQ to XML
description: WordprocessingML ドキュメント内の段落ノードを検索し、各ノードのテキストを文字列として取得する方法について学習します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: f41e0206f91f022993ed2c48681f124bf84ec603
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412194"
---
# <a name="retrieve-the-text-of-the-paragraphs-linq-to-xml"></a><span data-ttu-id="2546f-103">段落のテキストを取得する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2546f-103">Retrieve the text of the paragraphs (LINQ to XML)</span></span>

<span data-ttu-id="2546f-104">この例は、前の「[段落とそのスタイルを取得する](retrieve-paragraphs-styles.md)」の例を基にしています。</span><span class="sxs-lookup"><span data-stu-id="2546f-104">This example builds on the previous example, [Retrieve the paragraphs and their styles](retrieve-paragraphs-styles.md).</span></span> <span data-ttu-id="2546f-105">この新しい例では、各段落のテキストを文字列として取得します。</span><span class="sxs-lookup"><span data-stu-id="2546f-105">This new example retrieves the text of each paragraph as a string.</span></span>

<span data-ttu-id="2546f-106">テキストを取得するため、この例で追加するクエリでは、匿名型のコレクションを反復処理し、新しいメンバー `Text` を追加して匿名型の新しいコレクションを射影します。</span><span class="sxs-lookup"><span data-stu-id="2546f-106">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="2546f-107">また、<xref:System.Linq.Enumerable.Aggregate%2A> 標準クエリ演算子を使用して、複数の文字列を 1 つの文字列に連結します。</span><span class="sxs-lookup"><span data-stu-id="2546f-107">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>

<span data-ttu-id="2546f-108">この手法 (まず匿名型のコレクションに射影した後、このコレクションを使用して匿名型の新しいコレクションに射影する) は、一般的で便利なものです。</span><span class="sxs-lookup"><span data-stu-id="2546f-108">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful one.</span></span> <span data-ttu-id="2546f-109">最初の匿名型に射影せずに、このクエリを記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2546f-109">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="2546f-110">しかし、レイジー評価のため、これを行うために追加の処理能力はそれほど必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2546f-110">However, because of lazy evaluation, doing so doesn't use much additional processing power.</span></span> <span data-ttu-id="2546f-111">この手法を使用すると、ヒープ上に有効期間の短いオブジェクトがより多く作成されますが、パフォーマンスが大幅に低下することはありません。</span><span class="sxs-lookup"><span data-stu-id="2546f-111">The technique does create more short-lived objects on the heap, but that doesn't substantially degrade performance.</span></span>

<span data-ttu-id="2546f-112">もちろん、段落、各段落のスタイル、および各段落のテキストを取得する機能を持つ 1 つのクエリを記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2546f-112">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="2546f-113">しかし、多くの場合、より複雑なクエリは複数のクエリに分割した方が便利です。これは、結果コードのモジュール性が高まり、保守がより簡単になるためです。</span><span class="sxs-lookup"><span data-stu-id="2546f-113">However, it's often useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="2546f-114">また、クエリの一部を再利用する必要がある場合、クエリをこの手法で記述すると、リファクタリングがより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="2546f-114">Further, if you need to reuse a portion of the query, it's easier to refactor if the queries are written in this manner.</span></span>

<span data-ttu-id="2546f-115">連結されたこれらのクエリでは、[クエリの連結の例](chain-queries-example.md)に関する記事で確認している処理モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="2546f-115">These queries, which are chained together, use the processing model that's examined in the article [Chain queries example](chain-queries-example.md).</span></span>

## <a name="example-determine-the-element-node-style-name-and-text-of-each-paragraph"></a><span data-ttu-id="2546f-116">例: 各段落の要素ノード、スタイル名、テキストを決定する</span><span class="sxs-lookup"><span data-stu-id="2546f-116">Example: Determine the element node, style name, and text of each paragraph</span></span>

<span data-ttu-id="2546f-117">この例では、WordprocessingML ドキュメントを処理して、要素ノード、スタイル名、各段落のテキストを決定します。</span><span class="sxs-lookup"><span data-stu-id="2546f-117">This example processes a WordprocessingML document, determining the element node, style name, and text of each paragraph.</span></span> <span data-ttu-id="2546f-118">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="2546f-118">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="2546f-119">新しいクエリについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="2546f-119">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="2546f-120">この例のソース ドキュメントを作成する方法の手順については、「[ソースとなる Office Open XML ドキュメントを作成する](create-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2546f-120">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="2546f-121">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2546f-121">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="2546f-122">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="2546f-122">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
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
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
            PackagePart stylePart = wdPackage.GetPart(styleUri);

            //  Load the style XML in the part into an XDocument instance.
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
        }
    }
}

string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
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

// Following is the new query that retrieves the text of
// each paragraph.
var paraWithText =
    from para in paragraphs
    select new
    {
        ParagraphNode = para.ParagraphNode,
        StyleName = para.StyleName,
        Text = para
               .ParagraphNode
               .Elements(w + "r")
               .Elements(w + "t")
               .Aggregate(
                   new StringBuilder(),
                   (s, i) => s.Append((string)i),
                   s => s.ToString()
               )
    };

foreach (var p in paraWithText)
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
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
                If (styleRelation IsNot Nothing) Then
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

        ' Following is the new query that retrieves the text of
        ' each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.ParagraphNode.<w:r>.<w:t> _
                    .Aggregate(New StringBuilder(), _
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _
                               Function(s As StringBuilder) s.ToString) _
            }

        For Each p In paraWithText
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next

    End Sub
End Module
```

<span data-ttu-id="2546f-123">この例の C# バージョンでは、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2546f-123">The C# version of this example produces the following output:</span></span>

```conssole
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >using System;<
StyleName:Code ><
StyleName:Code >class Program {<
StyleName:Code >    public static void (string[] args) {<
StyleName:Code >        Console.WriteLine("Hello World");<
StyleName:Code >    }<
StyleName:Code >}<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="2546f-124">この例の Visual Basic バージョンでは、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2546f-124">The Visual Basic version of this example produces the following output:</span></span>

```output
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >Imports System<
StyleName:Code ><
StyleName:Code >Class Program<
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<
StyleName:Code >        Console.WriteLine("Hello World")<
StyleName:Code >   End Sub<
StyleName:Code >End Class<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="2546f-125">このチュートリアルの次の記事では、<xref:System.Linq.Enumerable.Aggregate%2A> の代わりに拡張メソッドを使用して、複数の文字列を 1 つの文字列に連結する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2546f-125">The next article in this tutorial shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string:</span></span>

- [<span data-ttu-id="2546f-126">拡張メソッドを使用してリファクタリングする</span><span class="sxs-lookup"><span data-stu-id="2546f-126">Refactor using an extension method</span></span>](refactor-extension-method.md)

## <a name="see-also"></a><span data-ttu-id="2546f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="2546f-127">See also</span></span>

- [<span data-ttu-id="2546f-128">チュートリアル: WordprocessingML ドキュメント内のコンテンツを操作する</span><span class="sxs-lookup"><span data-stu-id="2546f-128">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="2546f-129">遅延実行とレイジー評価</span><span class="sxs-lookup"><span data-stu-id="2546f-129">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
