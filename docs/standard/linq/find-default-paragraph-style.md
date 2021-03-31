---
title: 既定の段落スタイルを検索する - LINQ to XML
description: WordprocessingML ドキュメントで既定の段落スタイルを検索する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 0e66856a551410dd488148ff678b684489396d62
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411948"
---
# <a name="find-the-default-paragraph-style-linq-to-xml"></a><span data-ttu-id="cca97-103">既定の段落スタイルを検索する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cca97-103">Find the default paragraph style (LINQ to XML)</span></span>

<span data-ttu-id="cca97-104">[WordprocessingML ドキュメント内のコンテンツの操作](xml-shape-wordprocessingml-documents.md)に関するチュートリアルでの最初のタスクは、ドキュメント内にある段落の既定のスタイルを検索することです。</span><span class="sxs-lookup"><span data-stu-id="cca97-104">The first task in [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) is to find the default style of paragraphs in the document.</span></span>

## <a name="example-find-the-default-style-name"></a><span data-ttu-id="cca97-105">例: 既定のスタイル名を検索する</span><span class="sxs-lookup"><span data-stu-id="cca97-105">Example: Find the default style name</span></span>

<span data-ttu-id="cca97-106">次の例では、Office Open XML WordprocessingML ドキュメントを開き、パッケージのドキュメント パーツとスタイル パーツを検索した後、既定のスタイル名を検索するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="cca97-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="cca97-107">Office Open XML ドキュメント パッケージおよびその構成パーツについて詳しくは、「[Office Open XML WordprocessingML ドキュメントの詳細](wordprocessingml-document-styles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cca97-107">For information about Office Open XML document packages, and the parts they comprise, see [Details of Office Open XML WordprocessingML documents](wordprocessingml-document-styles.md).</span></span>

<span data-ttu-id="cca97-108">このクエリは、値が "paragraph" である `w:style` という名前の属性と、値が "1" である `w:type` という名前の属性を持つ `w:default` という名前のノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="cca97-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="cca97-109">これらの属性を持つ XML ノードは 1 つしかないため、このクエリは、<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> 演算子を使用してコレクションをシングルトンに変換します。</span><span class="sxs-lookup"><span data-stu-id="cca97-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="cca97-110">次に、`w:styleId` という名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="cca97-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>

<span data-ttu-id="cca97-111">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="cca97-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="cca97-112">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="cca97-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

// The following query finds all the paragraphs that have the default style.
string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
              (string)style.Attribute(w + "default") == "1"
              select style
    ).First().Attribute(w + "styleId");

Console.WriteLine("The default style is: {0}", defaultStyle);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1

    Sub Main()

        Const fileName As String = "SampleDoc.docx"

        Const documentRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Const stylesRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If docPackageRelationship IsNot Nothing Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                ' Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                ' Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If styleRelation IsNot Nothing Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    ' Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        ' The following query finds all the paragraphs that have the default style.
        Dim defParas As IEnumerable(Of XElement) = _
            From style In styleDoc.Root.<w:style> _
            Where style.@w:type.Equals("paragraph") And _
                   style.@w:default.Equals("1") _
            Select style
        ' Then find the style of the first.
        Dim defaultStyle As String = defParas.First().@w:styleId

        Console.WriteLine("The default style is: " & defaultStyle)
    End Sub
End Module
```

<span data-ttu-id="cca97-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cca97-113">This example produces the following output:</span></span>

```output
The default style is: Normal
```

<span data-ttu-id="cca97-114">このチュートリアルの次の記事では、ドキュメント内のすべての段落およびそのスタイルを検索する同様のクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="cca97-114">In the next article in this tutorial you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>

- [<span data-ttu-id="cca97-115">段落とそのスタイルを取得する</span><span class="sxs-lookup"><span data-stu-id="cca97-115">Retrieve the paragraphs and their styles</span></span>](retrieve-paragraphs-styles.md)

## <a name="see-also"></a><span data-ttu-id="cca97-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cca97-116">See also</span></span>

- [<span data-ttu-id="cca97-117">チュートリアル: WordprocessingML ドキュメント内のコンテンツを操作する</span><span class="sxs-lookup"><span data-stu-id="cca97-117">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
