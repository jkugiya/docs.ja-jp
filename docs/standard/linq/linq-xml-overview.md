---
title: 概要 - LINQ to XML
description: LINQ to XML には、.NET 機能に基づくメモリ内 XML プログラミング インターフェイスが用意されており、更新された DOM API と同等の機能を備えています。
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412027"
---
# <a name="linq-to-xml-overview"></a>LINQ to XML の概要

LINQ to XML には、.NET 統合言語クエリ (LINQ) フレームワークを利用したメモリ内 XML プログラミング インターフェイスが用意されています。 LINQ to XML では、.NET 機能を利用しており、更新および再設計されたドキュメント オブジェクト モデル (DOM) XML プログラミング インターフェイスと同等の機能を備えています。

XML は、多くのコンテキストでデータを書式設定する方法として広く採用されてきました。 たとえば、Web、構成ファイル、Microsoft Office Word ファイル、データベースで XML が使用されています。

LINQ to XML は、XML によるプログラミングのために再設計された最新の方法です。 ドキュメント オブジェクト モデル (DOM) のインメモリでのドキュメント変更機能を提供し、LINQ クエリ式をサポートします。 このクエリ式は、XPath と構文は異なりますが、機能が似ています。

## <a name="linq-to-xml-developers"></a>LINQ to XML の開発者

LINQ to XML は、さまざまな開発者を対象としています。 何らかの処理を行うだけの平均的な開発者にとっては、LINQ to XML を使用すると、SQL と同じようにクエリを作成できるので、XML の操作がより簡単になります。 プログラマは、短時間の学習で簡潔かつ強力なクエリを、選択したプログラミング言語で記述できるようになります。

熟練した開発者は、LINQ to XML を使用することで、生産性を大幅に向上させることができます。 LINQ to XML を使用すると、表現性がさらに優れ、より簡潔で強力なコードを、数を抑えて記述できます。 また、同時に複数のデータ ドメインからクエリ式を使用できます。

## <a name="linq-to-xml-is-an-xml-programming-interface"></a>XML プログラミング インターフェイスとしての LINQ to XML

LINQ to XML は、.NET プログラミング言語内で XML を操作できるようにする、LINQ に対応したメモリ内 XML プログラミング インターフェイスです。

LINQ to XML は、XML ドキュメントをメモリに読み込むという点で、ドキュメント オブジェクト モデル (DOM) に似ています。 ドキュメントに対するクエリや変更を行うことができ、変更したドキュメントをファイルに保存したり、シリアル化してインターネット経由で送信したりできます。 ただし、LINQ to XML は DOM とは異なります。

- より軽量で使いやすい、新しいオブジェクト モデルが用意されています。
- C# と Visual Basic の言語機能を利用できます。

LINQ to XML の最も重要な利点は、統合言語クエリ (LINQ) と統合されている点です。 この統合により、メモリ内の XML ドキュメントに対するクエリを記述して、要素および属性のコレクションを取得できます。 LINQ to XML のクエリ機能は、構文については異なりますが、XPath および XQuery と機能面で同等です。 LINQ に C# と Visual Basic が統合されていることで、厳密な型指定とコンパイル時のチェックが可能となり、デバッガー サポートが強化されます。

LINQ to XML のもう 1 つの利点は、クエリの結果を <xref:System.Xml.Linq.XElement> と <xref:System.Xml.Linq.XAttribute> の各オブジェクト コンストラクターに対するパラメーターとして使用できるので、強力な方法で XML ツリーを作成できるという点です。 *関数型構築* と呼ばれるこの方法では、開発者が XML ツリーの構造を簡単に変換できます。

たとえば、[サンプル XML ファイル (一般的な発注書)](sample-xml-file-typical-purchase-order.md) に関する記事で説明されているような、一般的な XML 発注書があるとします。 LINQ to XML を使用すると、発注書に記載されたすべての品目要素の部品番号属性を、次のクエリを実行して取得することができます。

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

C# では、これをメソッド構文形式で書き直すことができます。

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

もう 1 つの例として、金額が $100 を超える品目を部品番号順に並べた一覧が必要であるとします。 この情報を取得するには、次のクエリを実行します。

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

ここでも、C# では、これをメソッド構文形式で書き直すことができます。

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

これらの LINQ 機能に加え、LINQ to XML では、XML プログラミング インターフェイスが機能強化されています。 LINQ to XML を使用すると、次の操作が可能です。

- [ファイル](load-xml-file.md)または[ストリーム](stream-xml-fragments-xmlreader.md)からの XML の読み込み
- ファイルまたはストリームへの XML のシリアル化
- 関数型構築を使用した XML の新規作成
- XPath に類似した軸を使用した XML に対するクエリの実行
- <xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A>、<xref:System.Xml.Linq.XElement.SetValue%2A> などのメソッドを使用した、メモリ内の XML ツリーの操作
- XSD を使用した XML ツリーの検証
- 上記の機能を組み合わせて使用した XML ツリーの構造の変換

## <a name="create-xml-trees"></a>XML ツリーを作成する

LINQ to XML でのプログラミングで最も重要な利点の 1 つは、XML ツリーを簡単に作成できるという点です。 たとえば、小さな XML ツリーを作成するには、次のようにコードを記述します。

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
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

> [!NOTE]
> この例の Visual Basic バージョンでは、XML リテラルを使用します。 C# バージョンのように、Visual Basic で <xref:System.Xml.Linq.XElement> を使用することもできます。

詳細については、[XML ツリー](functional-construction.md)に関する記事を参照してください。

## <a name="see-also"></a>関連項目

- [参照](reference.md)
- [LINQ to XML およびDOM](linq-xml-vs-dom.md)
- [LINQ to XML とその他の XML テクノロジ](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
