---
title: XDocument クラスの概要
description: LINQ to XML XDocument クラスには、有効な XML ドキュメントに必要な情報が含まれています。 多くの場合、XDocument オブジェクトの機能は必要なく、代わりに XElement オブジェクトを使用できます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411954"
---
# <a name="xdocument-class-overview"></a>XDocument クラスの概要

<xref:System.Xml.Linq.XDocument> クラスには、XML 宣言、処理命令、コメントなど、有効な XML ドキュメントに必要な情報が含まれています。

<xref:System.Xml.Linq.XDocument> クラスが提供する特定の機能が必要な場合は、<xref:System.Xml.Linq.XDocument> オブジェクトを作成するだけで済みます。 多くの場合、<xref:System.Xml.Linq.XElement> を直接操作できます。 <xref:System.Xml.Linq.XElement> を直接操作するのは、比較的単純なプログラミング モデルです。

<xref:System.Xml.Linq.XDocument> は <xref:System.Xml.Linq.XContainer> から派生するため、子ノードを含めることができます。 ただし、<xref:System.Xml.Linq.XDocument> オブジェクトに格納できる子 <xref:System.Xml.Linq.XElement> ノードは 1 つだけです。 これは、XML ドキュメントにルート要素を 1 つしか持てないという XML 標準を反映しています。

## <a name="components-of-xdocument"></a>XDocument のコンポーネント

<xref:System.Xml.Linq.XDocument> には、次の要素を含めることができます。

- 1 つの <xref:System.Xml.Linq.XDeclaration> オブジェクト。 <xref:System.Xml.Linq.XDeclaration> では、XML 宣言の関連部分である XML バージョン、ドキュメントのエンコード、および XML ドキュメントがスタンドアロンかどうかを指定できます。
- 1 つの <xref:System.Xml.Linq.XElement> オブジェクト。 このオブジェクトは XML ドキュメントのルート ノードです。
- 任意の数の <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。 処理命令は、XML を処理するアプリケーションに情報を伝達します。
- 任意の数の <xref:System.Xml.Linq.XComment> オブジェクト。 コメントは、ルート要素の兄弟になります。 XML ドキュメントをコメントで始めることは無効であるため、<xref:System.Xml.Linq.XComment> オブジェクトをリストの最初の引数にすることはできません。
- DTD 用の 1 つの <xref:System.Xml.Linq.XDocumentType>。

<xref:System.Xml.Linq.XDocument> をシリアル化すると、`XDocument.Declaration` が `null` である場合でも、作成者が `Writer.Settings.OmitXmlDeclaration` を `false` (既定値) に設定していれば、出力には XML 宣言が含まれます。

既定では、LINQ to XML によってバージョンが "1.0" に、エンコードが "UTF-8" に設定されます。

## <a name="use-xelement-without-xdocument"></a>XDocument なしで XElement を使用する

既に説明したように、<xref:System.Xml.Linq.XElement> クラスは LINQ to XML プログラミング インターフェイスのメイン クラスです。 多くの場合、アプリケーションはドキュメントの作成を必要としません。 <xref:System.Xml.Linq.XElement> クラスを使用すると次のことが可能です。

- XML ツリーを作成します。
- それに他の XML ツリーを追加します。
- XML ツリーを変更します。
- ファイルを保存します。

## <a name="use-xdocument"></a>XDocument を使用する

<xref:System.Xml.Linq.XDocument> を構築するには、<xref:System.Xml.Linq.XElement> オブジェクトを構築する場合と同様に関数型構築を使用します。

次の例は、<xref:System.Xml.Linq.XDocument> オブジェクトおよび関連する格納されるオブジェクトを作成しています。

```csharp
XDocument d = new XDocument(
    new XComment("This is a comment."),
    new XProcessingInstruction("xml-stylesheet",
        "href='mystyle.css' title='Compact' type='text/css'"),
    new XElement("Pubs",
        new XElement("Book",
            new XElement("Title", "Artifacts of Roman Civilization"),
            new XElement("Author", "Moreno, Jordao")
        ),
        new XElement("Book",
            new XElement("Title", "Midieval Tools and Implements"),
            new XElement("Author", "Gazit, Inbar")
        )
    ),
    new XComment("This is another comment.")
);
d.Declaration = new XDeclaration("1.0", "utf-8", "true");
Console.WriteLine(d);

d.Save("test.xml");
```

```vb
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>
                       <!--This is a comment.-->
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
                       <Pubs>
                           <Book>
                               <Title>Artifacts of Roman Civilization</Title>
                               <Author>Moreno, Jordao</Author>
                           </Book>
                           <Book>
                               <Title>Midieval Tools and Implements</Title>
                               <Author>Gazit, Inbar</Author>
                           </Book>
                       </Pubs>
                       <!--This is another comment.-->
doc.Save("test.xml")
```

この例では、test.xml に次の出力が生成されます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--This is a comment.-->
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
<Pubs>
  <Book>
    <Title>Artifacts of Roman Civilization</Title>
    <Author>Moreno, Jordao</Author>
  </Book>
  <Book>
    <Title>Midieval Tools and Implements</Title>
    <Author>Gazit, Inbar</Author>
  </Book>
</Pubs>
<!--This is another comment.-->
```

## <a name="see-also"></a>関連項目

- [LINQ to XML の概要](linq-xml-overview.md)
