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
# <a name="how-to-create-a-tree-from-an-xmlreader-linq-to-xml"></a>XmlReader からツリーを作成する方法 (LINQ to XML)

この記事では、C# または Visual Basic で、<xref:System.Xml.XmlReader> から直接、XML ツリーを作成する方法を紹介します。 <xref:System.Xml.XmlReader> から <xref:System.Xml.Linq.XElement> を作成するには、ある要素ノード上に <xref:System.Xml.XmlReader> を配置します。 <xref:System.Xml.XmlReader> はコメントや処理命令をスキップしますが、<xref:System.Xml.XmlReader> がテキスト ノードに配置されている場合はエラーがスローされます。 このようなエラーを回避するため、<xref:System.Xml.XmlReader> から XML ツリーを作成する前に <xref:System.Xml.XmlReader> を要素上に配置してください。

## <a name="example-load-xelement-object-from-an-xmlreader-object"></a>例: XmlReader オブジェクトから XElement オブジェクトを読み込む

この例では、XML ドキュメント「[サンプル XML ファイル: 書籍](sample-xml-file-books.md)」を使用します。

次のコードでは、<xref:System.Xml.XmlReader> オブジェクトを作成し、最初の要素ノードが見つかるまでノードを読み取り、<xref:System.Xml.Linq.XElement> オブジェクトを読み込みます。

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

この例を実行すると、次の出力が生成されます。

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

## <a name="see-also"></a>関連項目

- [解析 XML](parse-string.md)
