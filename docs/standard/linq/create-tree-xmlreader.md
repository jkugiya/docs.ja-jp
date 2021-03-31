---
title: XmlReader からツリーを作成する方法 - LINQ to XML
description: C# または Visual Basic で XmlReader を使用し、XML を読み取り、XML ツリーを作成できます。 ある要素ノード上に XmlReader を適切に配置する必要があります。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 659135ae9930d4ba63b13e436ebd278807e4256b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412002"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-linq-to-xml"></a><span data-ttu-id="9c460-104">XmlReader からツリーを作成する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9c460-104">How to create a tree from an XmlReader (LINQ to XML)</span></span>

<span data-ttu-id="9c460-105">この記事では、C# または Visual Basic で、<xref:System.Xml.XmlReader> から直接、XML ツリーを作成する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="9c460-105">This article shows how to create an XML tree directly from an <xref:System.Xml.XmlReader> in C# or Visual Basic.</span></span> <span data-ttu-id="9c460-106"><xref:System.Xml.XmlReader> から <xref:System.Xml.Linq.XElement> を作成するには、ある要素ノード上に <xref:System.Xml.XmlReader> を配置します。</span><span class="sxs-lookup"><span data-stu-id="9c460-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="9c460-107"><xref:System.Xml.XmlReader> はコメントや処理命令をスキップしますが、<xref:System.Xml.XmlReader> がテキスト ノードに配置されている場合はエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="9c460-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="9c460-108">このようなエラーを回避するため、<xref:System.Xml.XmlReader> から XML ツリーを作成する前に <xref:System.Xml.XmlReader> を要素上に配置してください。</span><span class="sxs-lookup"><span data-stu-id="9c460-108">To avoid such errors, position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example-load-xelement-object-from-an-xmlreader-object"></a><span data-ttu-id="9c460-109">例: XmlReader オブジェクトから XElement オブジェクトを読み込む</span><span class="sxs-lookup"><span data-stu-id="9c460-109">Example: Load XElement object from an XmlReader object</span></span>

<span data-ttu-id="9c460-110">この例では、XML ドキュメント「[サンプル XML ファイル: 書籍](sample-xml-file-books.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="9c460-110">This example uses the XML document [Sample XML file: Books](sample-xml-file-books.md).</span></span>

<span data-ttu-id="9c460-111">次のコードでは、<xref:System.Xml.XmlReader> オブジェクトを作成し、最初の要素ノードが見つかるまでノードを読み取り、<xref:System.Xml.Linq.XElement> オブジェクトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9c460-111">The following code creates a <xref:System.Xml.XmlReader> object, reads nodes until it finds the first element node, and loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```csharp
XmlReader r = XmlReader.Create("books.xml");
while (r.NodeType != XmlNodeType.Element)
    r.Read();
XElement e = XElement.Load(r);
Console.WriteLine(e);
```

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="9c460-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c460-112">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9c460-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c460-113">See also</span></span>

- [<span data-ttu-id="9c460-114">解析 XML</span><span class="sxs-lookup"><span data-stu-id="9c460-114">Parse XML</span></span>](parse-string.md)
