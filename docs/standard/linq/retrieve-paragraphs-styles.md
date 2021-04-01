---
title: 段落とそのスタイルを取得する - LINQ to XML
description: WordprocessingML ドキュメントから段落ノードとそのスタイルを取得する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 43c6173441dda841236a4397e28d0bb2c7c8d003
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412075"
---
# <a name="retrieve-the-paragraphs-and-their-styles-linq-to-xml"></a>段落とそのスタイルを取得する (LINQ to XML)

この例では、WordprocessingML ドキュメントから段落ノードを取得するクエリを記述します。 それぞれの段落のスタイルも特定します。

このクエリの基になった前の例「[既定の段落スタイルの検索](find-default-paragraph-style.md)」のクエリでは、スタイルの一覧から既定のスタイルを取得しています。 スタイルが明示的に設定されていない段落のスタイルをクエリで特定するには、この情報が必要です。 段落のスタイルは、`w:pPr` 要素を通して設定されます。この要素が含まれていない段落は、既定のスタイルを使用して書式設定されます。

この記事では、クエリを構成するいくつかの要素の意味を説明し、完全な作業例の一部分であるクエリを紹介します。

## <a name="example-retrieve-all-the-paragraphs-in-a-document-and-the-paragraph-styles"></a>例: ドキュメント内のすべての段落と段落のスタイルを取得する

次のコードは、ドキュメント内のすべての段落とそのスタイルを取得するクエリです。

```csharp
xDoc.Root.Element(w + "body").Descendants(w + "p")
```

```vb
xDoc.Root.<w:body>...<w:p>
```

この式は、前の例「[既定の段落スタイルの検索](find-default-paragraph-style.md)」のクエリのソースと似ています。 主な違いは、<xref:System.Xml.Linq.XContainer.Descendants%2A> 軸の代わりに <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を使用している点です。 クエリで <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用しているのは、セクションが含まれているドキュメントの場合、段落が本文要素の直接の子とならず、階層内で 2 つ下のレベルに位置するためです。 コードで <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用すると、ドキュメントでセクションが使用されているかどうかにかかわらず機能するようになります。

## <a name="example-use-a-let-clause-to-determine-the-element-that-contains-the-style-node"></a>例: `let` 句を使用して、スタイル ノードが含まれる要素を特定します。

次のクエリは、`let` 句を使用して、スタイル ノードが含まれる要素を特定します。

```csharp
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()
```

 ```vb
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()
```

`let` 句 (Visual Basic バージョンでは `Let`) は、まず <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を使用して `pPr` という名前の要素すべてを検索し、次に <xref:System.Xml.Linq.Extensions.Elements%2A> 拡張メソッドを使用して `pStyle` という名前の子要素すべてを検索し、最後に <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準クエリ演算子を使用してコレクションをシングルトンに変換します。 コレクションが空の場合、`styleNode` は `null` (Visual Basic バージョンでは `Nothing`) に設定されます。 これは、`pStyle` 子孫ノードを検索するのに便利な表現形式です。 `pPr` 子ノードが存在しない場合、コードが例外をスローして失敗することはなく、`styleNode` が `null` (`Nothing`) に設定されます。これは、この `let` (`Let`) 句の望ましい動作です。

要素がない場合は、`styleNode` が `null` (`Nothing`) に設定されます。

このクエリは、匿名型のコレクションを射影します。このコレクションには、`StyleName` および `ParagraphNode` の 2 つのメンバーがあります。

## <a name="example-retrieve-the-paragraph-nodes-from-a-wordprocessingml-document"></a>例: WordprocessingML ドキュメントから段落ノードを取得する

この例では、WordprocessingML ドキュメントを処理して、段落ノードを取得します。 それぞれの段落のスタイルも特定します。 この例は、このチュートリアルのこれまでの例に基づいています。 新しいクエリについては、以下のコード内にあるコメントで説明が示されています。

この例のソース ドキュメントを作成する方法の手順については、「[ソースとなる Office Open XML ドキュメントを作成する](create-source-office-open-xml-document.md)」を参照してください。

この例では、WindowsBase アセンブリに含まれるクラスを使用します。 また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。

```csharp
const string fileName = "SampleDoc.docx";

const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

XDocument xDoc = null;
XDocument styleDoc = null;

using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
{
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
    if (docPackageRelationship != null)
    {
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Load the document XML in the part into an XDocument instance.
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

        //  Find the styles part. There will only be one.
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
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

// Following is the new query that finds all paragraphs in the
// document and their styles.
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

foreach (var p in paragraphs)
    Console.WriteLine("StyleName:{0}", p.StyleName);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
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

        ' Following is the new query that finds all paragraphs in the
        ' document and their styles.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        For Each p In paragraphs
            Console.WriteLine("StyleName:{0}", p.StyleName)
        Next

    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
StyleName:Heading1
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
```

このチュートリアルの次の記事では、段落のテキストを取得するクエリを作成する方法について説明します。

- [段落のテキストを取得する](retrieve-text-paragraphs.md)

## <a name="see-also"></a>関連項目

- [チュートリアル: WordprocessingML ドキュメント内のコンテンツを操作する](xml-shape-wordprocessingml-documents.md)
