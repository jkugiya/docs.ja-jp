---
title: LINQ to XML およびDOM
description: LINQ to XML と DOM の間には大きな違いがあります。 LINQ to XML では、関数型構築と XML リテラルをサポートしています。これらは、ビルドする XML ツリーの構造をわかりやすくします。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412021"
---
# <a name="linq-to-xml-vs-dom"></a>LINQ to XML およびDOM

この記事では、LINQ to XML と、現在主流の XML プログラミング API である W3C ドキュメント オブジェクト モデル (DOM) との主な違いについて説明します。

## <a name="new-ways-to-construct-xml-trees"></a>XML ツリーを構築する新しい方法

W3C DOM では、XML ツリーをボトムアップ方式で作成します。つまり、ドキュメントを作成し、要素を作成して、要素をドキュメントに追加することによって作成します。

たとえば、次の例は、Microsoft の DOM の実装である <xref:System.Xml.XmlDocument> を使用して XML ツリーを作成する典型的な方法を使用しています。

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
XmlElement phone1 = doc.CreateElement("Phone");
phone1.SetAttribute("Type", "Home");
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");
phone2.SetAttribute("Type", "Work");
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";
XmlElement city = doc.CreateElement("City");
city.InnerText = "Mercer Island";
XmlElement state = doc.CreateElement("State");
state.InnerText = "WA";
XmlElement postal = doc.CreateElement("Postal");
postal.InnerText = "68042";
XmlElement address = doc.CreateElement("Address");
address.AppendChild(street1);
address.AppendChild(city);
address.AppendChild(state);
address.AppendChild(postal);
XmlElement contact = doc.CreateElement("Contact");
contact.AppendChild(name);
contact.AppendChild(phone1);
contact.AppendChild(phone2);
contact.AppendChild(address);
XmlElement contacts = doc.CreateElement("Contacts");
contacts.AppendChild(contact);
doc.AppendChild(contacts);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
Dim phone1 As XmlElement = doc.CreateElement("Phone")
phone1.SetAttribute("Type", "Home")
phone1.InnerText = "206-555-0144"
Dim phone2 As XmlElement = doc.CreateElement("Phone")
phone2.SetAttribute("Type", "Work")
phone2.InnerText = "425-555-0145"
Dim street1 As XmlElement = doc.CreateElement("Street1")
street1.InnerText = "123 Main St"
Dim city As XmlElement = doc.CreateElement("City")
city.InnerText = "Mercer Island"
Dim state As XmlElement = doc.CreateElement("State")
state.InnerText = "WA"
Dim postal As XmlElement = doc.CreateElement("Postal")
postal.InnerText = "68042"
Dim address As XmlElement = doc.CreateElement("Address")
address.AppendChild(street1)
address.AppendChild(city)
address.AppendChild(state)
address.AppendChild(postal)
Dim contact As XmlElement = doc.CreateElement("Contact")
contact.AppendChild(name)
contact.AppendChild(phone1)
contact.AppendChild(phone2)
contact.AppendChild(address)
Dim contacts As XmlElement = doc.CreateElement("Contacts")
contacts.AppendChild(contact)
doc.AppendChild(contacts)
Console.WriteLine(doc.OuterXml)
```

このコーディング形式では、XML ツリーの構造は表示されません。 LINQ to XML では、構造をよりよく示す、"*関数型構築*" という別の方法もサポートしています。 この方法は、<xref:System.Xml.Linq.XElement> と <xref:System.Xml.Linq.XAttribute> コンストラクターを使用して実行できます。 Visual Basic では、XML リテラルで行うことも可能です。 次の例では、関数型構築を使用して同じ XML ツリーを構築する方法を示しています。

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144",
                new XAttribute("Type", "Home")),
            new XElement("phone", "425-555-0145",
                new XAttribute("Type", "Work")),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="Home">206-555-0144</Phone>
            <Phone Type="Work">425-555-0145</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

このように、XML ツリーを構築するコードのインデントにより、基になる XML の構造が示されます。 Visual Basic のバージョンでは、XML リテラルを使用しています。

詳細については、[XML ツリー](functional-construction.md)に関する記事を参照してください。

## <a name="work-directly-with-xml-elements"></a>XML 要素を直接操作する

一般に、XML によるプログラミングで重視されるのは XML 要素であり、その属性が重要となる場合が多くあります。 LINQ to XML では、XML の要素と属性を直接操作できます。 たとえば、次のようなことが可能です。

- ドキュメント オブジェクトを一切使用せずに XML 要素を作成する。 これにより、XML ツリーのフラグメントを操作する際のプログラミングが単純化されます。
- `T:System.Xml.Linq.XElement` オブジェクトを直接 XML ファイルから読み込む。
- `T:System.Xml.Linq.XElement` オブジェクトをファイルやストリームにシリアル化する。

これに対して、XML ドキュメントが XML ツリーの論理的コンテナーとして使用される W3C DOM では、 XML ノード (要素や属性を含む) は XML ドキュメントのコンテキストで作成する必要があります。 DOM で name 要素を作成するコードの断片を次に示します。

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

要素を複数のドキュメントで使用する場合は、ノードをドキュメント間でインポートする必要があります。 LINQ to XML では、こうした複雑さを回避できます。

LINQ to XML を使用する場合、<xref:System.Xml.Linq.XDocument> クラスを使用するのは、ドキュメントのルート レベルにコメントや処理命令を追加する場合だけです。

## <a name="simplified-handling-of-names-and-namespaces"></a>名前と名前空間の処理の単純化

一般に XML プログラミングでは、名前、名前空間、および名前空間プレフィックスの処理が複雑になります。 LINQ to XML では、名前空間のプレフィックスを処理する必要がないため、名前と名前空間が単純になっています。 必要に応じて名前空間プレフィックスを制御することはできますが、 明示的に制御しないようにすることもできます。その場合、LINQ to XML がシリアル中に名前空間プレフィックスを必要に応じて割り当てます。必要ない場合は、既定の名前空間を使用してシリアル化します。 既定の名前空間が使用された場合は、結果のドキュメントには名前空間プレフィックスは含まれません。 詳細については、[名前空間の概要](namespaces-overview.md)に関するページを参照してください。

DOM にはその他に、ノードの名前を変更できない問題があります。 ノード名の変更が必要な場合は、新しいノードを作成し、そこにすべての子ノードをコピーする必要があります。この場合、元のノード固有の特性は失われます。 LINQ to XML では、この問題を回避するために、ノードに <xref:System.Xml.Linq.XName> プロパティを設定できます。

## <a name="static-method-support-for-loading-xml"></a>XML を読み込む静的メソッドのサポート

LINQ to XML では、インスタンス メソッドではなく静的メソッドを使用して XML を読み込むことができます。 これにより、読み込みと解析が簡略化されます。 詳細については、[ファイルから XML を読み込む方法](load-xml-file.md)に関するページを参照してください。

## <a name="removal-of-support-for-dtd-constructs"></a>DTD コンストラクトのサポートの削除

LINQ to XML では、XML のプログラミングをさらに簡単にするために、エンティティとエンティティ参照のサポートが削除されています。 エンティティの管理は複雑で、ほとんど利用されていません。 これらのサポートを削除することにより、パフォーマンスが向上し、プログラミング インターフェイスが簡略化されます。 LINQ to XML ツリーが設定されると、すべての DTD エンティティが展開されます。

## <a name="support-for-fragments"></a>フラグメントのサポート

LINQ to XML には、`XmlDocumentFragment` クラスに相当するものがありません。 ただし、`XmlDocumentFragment` の概念は、多くの場合、<xref:System.Xml.Linq.XNode> の <xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> として型指定したクエリの結果で処理できます。

## <a name="support-for-xpathnavigator"></a>XPathNavigator のサポート

LINQ to XML では、<xref:System.Xml.XPath?displayProperty=nameWithType> 名前空間の拡張メソッドで <xref:System.Xml.XPath.XPathNavigator> をサポートしています。 詳細については、「<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>」を参照してください。

## <a name="support-for-white-space-and-indentation"></a>空白とインデントのサポート

LINQ to XML での空白の処理は、DOM よりも単純です。

一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。 書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。 これが LINQ to XML の既定の動作です。

もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。 場合によっては、このインデントを一切変更しないようにする必要があります。 LINQ to XML では、次の方法でこれを行うことができます。

- XML の読み込み時または解析時に空白を維持する。
- XML をシリアル化するときに書式設定を無効にする。

LINQ to XML で空白は、DOM にある専用の <xref:System.Xml.XmlNodeType.Whitespace> ノード型ではなく、<xref:System.Xml.Linq.XText> ノードとして格納されます。

## <a name="support-for-annotations"></a>注釈のサポート

LINQ to XML 要素は、拡張可能な注釈のセットをサポートしています。 このサポートは、スキーマの情報、要素が UI にバインドされているかどうかの情報、またはアプリケーション固有のその他の情報など、要素に関するさまざまな情報を追跡する場合に利用できます。 詳細については、[LINQ to XML の注釈](linq-xml-annotations.md)に関するページを参照してください。

## <a name="support-for-schema-information"></a>スキーマ情報のサポート

LINQ to XML では、<xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間の拡張メソッドで XSD 検証をサポートしています。 これにより、XML ツリーが XSD に準拠しているかどうかを検証できます。 また、スキーマ検証後の情報セット (PSVI) を使用して XML ツリーを設定できます。 詳細については、「[XSD を使用して検証する方法](validate-xsd.md)」および「<xref:System.Xml.Schema.Extensions>」を参照してください。

## <a name="see-also"></a>関連項目

- [LINQ to XML の概要](linq-xml-overview.md)
