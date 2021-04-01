---
title: 名前空間プレフィックスを制御する方法 - LINQ to XML
description: C# と Visual Basic で XML ツリーをシリアル化するとき、名前空間プレフィックスを制御できます。 これを行うには、名前空間を宣言する属性を挿入します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411974"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a>名前空間プレフィックスを制御する方法 (LINQ to XML)

この記事では、C# と Visual Basic で XML ツリーをシリアル化するとき、名前空間プレフィックスを制御する方法について説明します。

多くの場合、名前空間プレフィックスを制御する必要はありません。 ただし、特定の XML プログラミング ツールではそれが必要になります。 たとえば、特定の名前空間プレフィックスを参照する組み込み XPath 式が含まれる XSLT スタイル シートまたは XAML ドキュメントを操作することがあります。 その場合、そのプレフィックスでドキュメントをシリアル化することが重要です。 これは、名前空間プレフィックスを制御する一般的な理由です。

もう 1 つの理由として、ユーザーが XML ドキュメントを手動で編集できるようにし、ユーザーにとって入力しやすい名前空間プレフィックスを作成する必要性が挙げられます。 たとえば、XSD ドキュメントを生成するとします。 スキーマの規則では、スキーマ名前空間のプレフィックスとして `xs` または `xsd` のいずれかを使用することが推奨されています。

名前空間プレフィックスを制御するには、名前空間を宣言する属性を挿入します。 特定のプレフィックスを持つ名前空間を宣言すると、LINQ to XML はシリアル化の場合にその名前空間プレフィックスの使用を試みます。

プレフィックスを持つ名前空間を宣言する属性を作成するには、属性の名前の名前空間が <xref:System.Xml.Linq.XNamespace.Xmlns%2A> で、属性の名前が名前空間プレフィックスであるような属性を作成します。 属性の値は、名前空間の URI です。

## <a name="example-create-two-namespaces-that-have-prefixes"></a>例: プレフィックスを持つ名前空間を 2 つ作成する

この例では、2 つの名前空間を宣言します。 `http://www.adventure-works.com` 名前空間にプレフィックス `aw` を指定し、`www.fourthcoffee.com` 名前空間にプレフィックス `fc` を指定します。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a>関連項目

- [名前空間の概要](namespaces-overview.md)
