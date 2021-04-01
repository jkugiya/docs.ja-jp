---
title: ファイルから XML を読み込む方法 - LINQ to XML
description: C# と Visual Basic で XElement.Load メソッドを使用し、ファイルから XML ドキュメントを読み込むことができます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 7ac77205eb1f7637982e8f40d31df0a422ecba22
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412017"
---
# <a name="how-to-load-xml-from-a-file-linq-to-xml"></a><span data-ttu-id="dc6ea-103">ファイルから XML を読み込む方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="dc6ea-103">How to load XML from a file (LINQ to XML)</span></span>

<span data-ttu-id="dc6ea-104">この記事では、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> メソッドを使用し、C# と Visual Basic でファイルから XML を読み込む方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="dc6ea-104">This article shows how to load XML from a file in C# and Visual Basic using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-load-xml-document-from-a-file"></a><span data-ttu-id="dc6ea-105">例: ファイルから XML ドキュメントを読み込む</span><span class="sxs-lookup"><span data-stu-id="dc6ea-105">Example: Load XML document from a file</span></span>

<span data-ttu-id="dc6ea-106">次の例には、ファイルを参照する URI と共に <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> を指定することでファイルから XML を読み込む方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="dc6ea-106">The following example shows how to load an XML document from a file by providing <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> with the URI that references the file.</span></span> <span data-ttu-id="dc6ea-107">例では、books.xml を読み込んで、XML ツリーをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="dc6ea-107">The example loads books.xml and outputs the XML tree to the console.</span></span>

<span data-ttu-id="dc6ea-108">books.xml の内容は、「[サンプル XML ファイル: 書籍](sample-xml-file-books.md)」に記載されています。</span><span class="sxs-lookup"><span data-stu-id="dc6ea-108">The contents of books.xml are shown in [Sample XML file: Books](sample-xml-file-books.md).</span></span>

```csharp
XElement booksFromFile = XElement.Load(@"books.xml");
Console.WriteLine(booksFromFile);
```

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
```

<span data-ttu-id="dc6ea-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="dc6ea-109">This example produces the following output:</span></span>

```xml
<Catalog>
  <Book id="bk101">
    <Author>Garghentini, Davide</Author>
    <Title>XML Developer's Guide</Title>
    <Genre>Computer</Genre>
    <Price>44.95</Price>
    <PublishDate>2000-10-01</PublishDate>
    <Description>An in-depth look at creating applications
      with XML.</Description>
  </Book>
  <Book id="bk102">
    <Author>Garcia, Debra</Author>
    <Title>Midnight Rain</Title>
    <Genre>Fantasy</Genre>
    <Price>5.95</Price>
    <PublishDate>2000-12-16</PublishDate>
    <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
  </Book>
</Catalog>
```
