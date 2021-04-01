---
title: スタイルを含む WordprocessingML ドキュメント - LINQ to XML
description: 段落がスタイルで書式設定されている WordprocessingML ドキュメントについて説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 7864ce5163d9dfb316c8288850210becdf55dc2d
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412005"
---
# <a name="wordprocessingml-document-with-styles-linq-to-xml"></a><span data-ttu-id="c9e35-103">スタイルを含む WordprocessingML ドキュメント (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c9e35-103">WordprocessingML document with styles (LINQ to XML)</span></span>

<span data-ttu-id="c9e35-104">この記事では、「[WordprocessingML ドキュメントの XML 構造](xml-shape-wordprocessingml-documents.md)」のそれより複雑な WordprocessingML ドキュメントを取り上げます。特に、段落がスタイルで書式設定されているドキュメントを取り上げます。</span><span class="sxs-lookup"><span data-stu-id="c9e35-104">This article presents a WordprocessingML document that is more complicated than the one in [The XML shape of WordprocessingML documents](xml-shape-wordprocessingml-documents.md); specifically, it presents a document whose paragraphs are formatted with styles.</span></span>

<span data-ttu-id="c9e35-105">スタイルを理解するには、ドキュメントの構造について知っておくと役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c9e35-105">To understand styles, it's helpful to know something about document structure.</span></span> <span data-ttu-id="c9e35-106">WordprocessingML ドキュメントは、"*パーツ*" で構成される "*パッケージ*" に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c9e35-106">A WordprocessingML document is stored in a *package* that comprises *parts*.</span></span> <span data-ttu-id="c9e35-107">正確に言うと、"*パッケージ*" という用語は ZIP アーカイブに相当し、"*パーツ*" という用語はその ZIP 内に格納されているファイルに相当します。</span><span class="sxs-lookup"><span data-stu-id="c9e35-107">Specifically, the term *package* corresponds to a ZIP archive and the term *part* corresponds to a file stored within the ZIP.</span></span> <span data-ttu-id="c9e35-108">スタイルで書式設定されている段落がドキュメントに含まれている場合、スタイルが適用されている段落が含まれるドキュメント パーツと、そのドキュメント パーツ内で参照されるスタイルを定義するスタイル パーツが存在します。</span><span class="sxs-lookup"><span data-stu-id="c9e35-108">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them, and a style part that defines the styles referenced in the document part.</span></span>

<span data-ttu-id="c9e35-109">Office Open XML ドキュメントを構成する XML を確認するには、「[Office Open XML ドキュメント パーツを出力する例](example-outputs-office-open-xml-document-parts.md)」に含まれるサンプルを実行するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="c9e35-109">The easiest way to see the XML that makes up an Office Open XML document is to run the example in [Example that outputs Office Open XML document parts](example-outputs-office-open-xml-document-parts.md).</span></span>

<span data-ttu-id="c9e35-110">パッケージにアクセスするとき、任意のパスを利用せず、パーツ間の関係を利用してください。</span><span class="sxs-lookup"><span data-stu-id="c9e35-110">When you access a package, you should do so through the relationships among parts, not through an arbitrary path.</span></span> <span data-ttu-id="c9e35-111">この問題は現在のチュートリアルの範囲外ですが、これと他のチュートリアル記事に含まれるサンプル プログラムは正しいアプローチを示すものです。</span><span class="sxs-lookup"><span data-stu-id="c9e35-111">This issue is beyond the scope of the current tutorial, but the example programs in this and other tutorial articles demonstrate the correct approach.</span></span>

## <a name="example-a-document-that-uses-styles"></a><span data-ttu-id="c9e35-112">例: スタイルを使用するドキュメント</span><span class="sxs-lookup"><span data-stu-id="c9e35-112">Example: A document that uses styles</span></span>

<span data-ttu-id="c9e35-113">次のドキュメントには、スタイルで書式設定されている段落が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c9e35-113">The following document has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="c9e35-114">最初の段落にはスタイル `Heading1` が含まれ、他の段落には `Code` スタイルか既定のスタイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9e35-114">The first paragraph has the style `Heading1` and other paragraphs have the `Code` style or the default style.</span></span> <span data-ttu-id="c9e35-115">既定以外のスタイルが設定されている段落では、段落要素に `w:pPr` という名前の子要素があり、この子要素には `w:pStyle` という子要素があります。</span><span class="sxs-lookup"><span data-stu-id="c9e35-115">For paragraphs with non-default styles the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="c9e35-116">`w:val` 要素には、スタイル名を格納する  という属性があります。</span><span class="sxs-lookup"><span data-stu-id="c9e35-116">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="c9e35-117">既定のスタイルが設定されている段落については、段落要素に `w:p.Pr` 子要素がありません。</span><span class="sxs-lookup"><span data-stu-id="c9e35-117">For paragraphs with the default style, the paragraph element doesn't have a `w:p.Pr` child element.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
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
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Heading1" />
      </w:pPr>
      <w:r>
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>The following example prints to the console.</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>using System;</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>class Program {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    public static void </w:t>
      </w:r>
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">
        <w:r w:rsidRPr="00876F34">
          <w:t>Main</w:t>
        </w:r>
      </w:smartTag>
      <w:r w:rsidRPr="00876F34">
        <w:t>(string[] args) {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    }</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>}</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>This example produces the following output:</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>Hello World</w:t>
      </w:r>
    </w:p>
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">
      <w:pgSz w:w="12240" w:h="15840" />
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />
      <w:cols w:space="720" />
      <w:docGrid w:linePitch="360" />
    </w:sectPr>
  </w:body>
</w:document>
```
