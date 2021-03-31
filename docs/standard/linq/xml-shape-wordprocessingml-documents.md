---
title: WordprocessingML ドキュメントの XML 構造 - LINQ to XML
description: WordprocessingML ドキュメントの XML 構造について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 1f5b8098923a56b638598516ed9640a28a90198a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103366028"
---
# <a name="the-xml-shape-of-wordprocessingml-documents-linq-to-xml"></a><span data-ttu-id="e1bcc-103">WordprocessingML ドキュメントの XML 構造 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e1bcc-103">The XML shape of WordprocessingML documents (LINQ to XML)</span></span>

<span data-ttu-id="e1bcc-104">この記事では、WordprocessingML ドキュメントの XML 構造について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-104">This article introduces the XML shape of a WordprocessingML document.</span></span>

## <a name="microsoft-office-formats"></a><span data-ttu-id="e1bcc-105">Microsoft Office 形式</span><span class="sxs-lookup"><span data-stu-id="e1bcc-105">Microsoft Office formats</span></span>

<span data-ttu-id="e1bcc-106">2007 Microsoft Office システムのネイティブ ファイル形式は Office Open XML (一般的な呼称は Open XML) です。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-106">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="e1bcc-107">Open XML は Ecma 標準の XML ベースの形式であり、現在は ISO-IEC 標準としての検討が進められている段階です。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-107">Open XML is an XML-based format that's an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="e1bcc-108">Open XML 内のワード プロセッシング ファイルのマークアップ言語は WordprocessingML と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-108">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="e1bcc-109">このチュートリアルの例では、WordprocessingML ソース ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-109">This tutorial uses WordprocessingML source files as input for the examples.</span></span>

<span data-ttu-id="e1bcc-110">Microsoft Office 2003 を使用しており、Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats をインストールしている場合は、Office Open XML 形式でドキュメントを保存できます。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-110">If you're using Microsoft Office 2003, you can save documents in the Office Open XML format if you've installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="e1bcc-111">WordprocessingML ドキュメントの構造</span><span class="sxs-lookup"><span data-stu-id="e1bcc-111">The shape of WordprocessingML documents</span></span>

<span data-ttu-id="e1bcc-112">最初に理解する必要があるのは WordprocessingML ドキュメントの XML 構造です。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-112">The first thing to understand is the XML shape of WordprocessingML documents.</span></span> <span data-ttu-id="e1bcc-113">WordprocessingML ドキュメントには、ドキュメントの段落を含む本文要素 (名前は `w:body`) が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-113">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="e1bcc-114">各段落には、1 つ以上のテキスト ラン (名前は `w:r`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-114">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="e1bcc-115">各テキスト ランには、1 つ以上のテキスト片 (名前は `w:t`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-115">Each text run contains one or more text pieces (named `w:t`).</span></span>

<span data-ttu-id="e1bcc-116">非常に単純な WordprocessingML ドキュメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-116">The following is a very simple WordprocessingML document:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<w:document
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"
xmlns:o="urn:schemas-microsoft-com:office:office"
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"
xmlns:v="urn:schemas-microsoft-com:vml"
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"
xmlns:w10="urn:schemas-microsoft-com:office:word"
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">
  <w:body>
    <w:p w:rsidR="00E22EB6"
         w:rsidRDefault="00E22EB6">
      <w:r>
        <w:t>This is a paragraph.</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00E22EB6"
         w:rsidRDefault="00E22EB6">
      <w:r>
        <w:t>This is another paragraph.</w:t>
      </w:r>
    </w:p>
  </w:body>
</w:document>
```

<span data-ttu-id="e1bcc-117">このドキュメントには、2 つの段落が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-117">This document contains two paragraphs.</span></span> <span data-ttu-id="e1bcc-118">各段落には 1 つのテキスト ランが含まれており、各テキスト ランには 1 つのテキスト片が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-118">They both contain a single text run, and each text run contains a single text piece.</span></span>

<span data-ttu-id="e1bcc-119">WordprocessingML ドキュメントの内容を XML 形式で表示する最も簡単な方法は、Microsoft Word を使用して WordprocessingML ドキュメントを作成および保存し、次のプログラムを実行してコンソールに XML を出力することです。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-119">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>

<span data-ttu-id="e1bcc-120">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-120">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="e1bcc-121">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1bcc-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
const string documentRelationshipType =
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string wordmlNamespace =
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))
{
    PackageRelationship relationship =
        wdPackage
        .GetRelationshipsByType(documentRelationshipType)
        .FirstOrDefault();
    if (relationship != null)
    {
        Uri documentUri =
            PackUriHelper.ResolvePartUri(
                new Uri("/", UriKind.Relative),
                relationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Get the officeDocument part from the package.
        //  Load the XML in the part into an XDocument instance.
        XDocument xdoc =
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));
        Console.WriteLine(xdoc.Root);
    }
}
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    Sub Main()
        Dim documentRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"

        Using wdPackage As Package = _
          Package.Open("SampleDoc.docx", _
                       FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage _
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _
                            New Uri("/", UriKind.Relative), _
                            docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                ' Get the officeDocument part from the package.
                ' Load the XML in the part into an XDocument instance.
                Dim xDoc As XDocument = _
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))
                Console.WriteLine(xDoc.Root)
            End If
        End Using
    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="e1bcc-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1bcc-122">See also</span></span>

- <span data-ttu-id="e1bcc-123">[Office (2007) Open XML ファイル形式の概要](/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="e1bcc-123">[Introducing the Office (2007) Open XML File Formats](/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>
- <span data-ttu-id="e1bcc-124">[WordprocessingML の概要](/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span><span class="sxs-lookup"><span data-stu-id="e1bcc-124">[Overview of WordprocessingML](/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>
- [<span data-ttu-id="e1bcc-125">WordProcessingML ファイルの構造</span><span class="sxs-lookup"><span data-stu-id="e1bcc-125">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="e1bcc-126">WordprocessingML の概要</span><span class="sxs-lookup"><span data-stu-id="e1bcc-126">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)
