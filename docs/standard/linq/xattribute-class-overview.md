---
title: XAttribute クラスの概要
description: XAttribute クラスは、XML 属性を表します。 LINQ to XML での属性の操作は、要素の操作に似ています。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411959"
---
# <a name="xattribute-class-overview"></a>XAttribute クラスの概要

属性は、要素に関連付けられている名前と値のペアです。 <xref:System.Xml.Linq.XAttribute> クラスは、XML 属性を表します。

LINQ to XML での属性の操作は、要素の操作に似ています。 コンストラクターはほぼ同じです。 それぞれのコレクションの取得に使用するメソッドもほぼ同じです。 属性のコレクションの LINQ クエリ式は、要素のコレクションの LINQ クエリ式と似ています。

属性が要素に追加された順序は保持されます。 つまり、属性を反復処理する場合、属性は追加された順序と同じ順序で表示されます。

## <a name="the-xattribute-constructor"></a>XAttribute コンストラクター

最もよく使用する <xref:System.Xml.Linq.XAttribute> クラスのコンストラクターを次に示します。

|コンストラクター|説明|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|<xref:System.Xml.Linq.XAttribute> オブジェクトを作成します。 `name` 引数には属性の名前を指定し、`content` には属性のコンテンツを指定します。|

## <a name="example-create-an-element-with-an-attribute"></a>例: 属性を持つ要素を作成する

次の例は、属性を含む要素を作成する一般的なタスクを示しています。

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

この例を実行すると、次の出力が生成されます。

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a>例: 属性の関数型構築

<xref:System.Xml.Linq.XAttribute> オブジェクトは、次の例に示すように、<xref:System.Xml.Linq.XElement> オブジェクトの構築と共にインラインで構築できます。

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

この例を実行すると、次の出力が生成されます。

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a>属性はノードではない

属性と要素には、いくつかの違いがあります。 <xref:System.Xml.Linq.XAttribute> オブジェクトは、XML ツリーのノードではありません。 属性は、XML 要素に関連付けられている名前と値のペアです。 ドキュメント オブジェクト モデル (DOM) とは異なり、XML の構造をより密接に反映します。 <xref:System.Xml.Linq.XAttribute> オブジェクトは実際には XML ツリーのノードではありませんが、<xref:System.Xml.Linq.XAttribute> オブジェクトの操作は <xref:System.Xml.Linq.XElement> オブジェクトの操作と似ています。

属性と要素の区別は主に、ノード レベルで XML ツリーを操作するコードを記述する開発者にとってのみ重要な意味を持ちます。 多くの開発者は、この区別を考慮する必要はありません。

## <a name="see-also"></a>関連項目

- [LINQ to XML の概要](linq-xml-overview.md)
