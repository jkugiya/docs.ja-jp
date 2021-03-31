---
title: グローバル名前空間の使用 (Visual Basic) - LINQ to XML
description: 名前空間が既定の名前空間の場合でも、名前空間にプレフィックスが付いている場合でも、Visual Basic で Imports ステートメントを使用して名前空間を宣言します。 この記事では、Import ステートメントと、名前空間使用のその他の面について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412113"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a>グローバル名前空間の使用 (Visual Basic) (LINQ to XML)

Visual Basic での XML リテラルの重要な機能の 1 つは、`Imports` ステートメントを使用して XML 名前空間を宣言できることです。 この機能を使用することで、プレフィックスを使用する XML 名前空間または既定の XML 名前空間を宣言できます。

この機能は 2 つの状況で役立ちます。

- XML リテラルで宣言された名前空間は、組み込み式に引き継がれません。 グローバル名前空間を宣言すると、名前空間を伴う組み込み式を使用しなければならない作業が軽減されます。
- 名前空間と XML プロパティを併用するためには、グローバル名前空間を宣言する必要があります。

グローバル名前空間はプロジェクト レベルで宣言できます。 また、モジュール レベルでもグローバル名前空間を宣言できます。その場合、プロジェクト レベルのグローバル名前空間はオーバーライドされます。 最終的に、グローバル名前空間は XML リテラルでオーバーライドできます。

グローバルに宣言された名前空間に含まれる XML リテラルまたは XML プロパティを使用する場合は、Visual Studio で XML リテラルまたはプロパティにカーソルを合わせることで、それらの展開名が表示されます。 拡張名はツールヒントに表示されます。

グローバル名前空間に対応する <xref:System.Xml.Linq.XNamespace> オブジェクトを取得するには、`GetXmlNamespace` メソッドを使用します。

## <a name="example-use-imports-to-declare-a-global-namespace"></a>例: `Imports` を使用してグローバル名前空間を宣言する

次の例では、`Imports` ステートメントを使用して既定のグローバル名前空間を宣言し、XML リテラルを使用してその名前空間内で <xref:System.Xml.Linq.XElement> オブジェクトを初期化します。

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a>例: プレフィックスが付いたグローバル名前空間を宣言する

次の例では、プレフィックスを付けてグローバル名前空間を宣言し、XML リテラルを使用して要素を初期化します。

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a>例: 既定の名前空間を宣言し、`Child` 要素に埋め込み式を使用する

XML リテラルで宣言される名前空間は、組み込み式に引き継がれません。 次の例では、既定の名前空間を宣言し、`Child` 要素に埋め込み式を使用します。

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

結果的に生成される XML では、`Child` 要素がどの名前空間にも属さないように、既定の名前空間の宣言が含まれています。

次のように、組み込み式で別の名前空間を宣言できます。

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

ただし、既定のグローバル名前空間を使用することで、名前空間を宣言せずに XML リテラルを使用できます。 結果的に生成される XML は、この例のように、グローバルに宣言された既定の名前空間に属することになります。

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a>例: 名前空間と XML プロパティを併用する

名前空間に含まれている XML ツリーを操作する場合に XML プロパティを使用するときは、XML プロパティが正しい名前空間に含まれるように、グローバル名前空間を使用する必要があります。 次の例では、名前空間で XML ツリーを宣言し、`Child` 要素の数を出力します。

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

この例は `Child` 要素が存在しないことを示しています。 次が出力されます。

```output
0
```

ただし、既定のグローバル名前空間を宣言すると、XML リテラルと XML プロパティの両方が既定のグローバル名前空間に含まれます。

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

この例は、`Child` 要素が 1 つ存在することを示しています。 次が出力されます。

```output
1
```

プレフィックスを持つグローバル名前空間を宣言すると、そのプレフィックスを XML リテラルと XML プロパティの両方で使用できます。

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a>例: `GetXmlNamespace` を使用して `XNamespace` を取得する

`GetXmlNamespace` メソッドを使用して <xref:System.Xml.Linq.XNamespace> オブジェクトを取得できます。

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
http://www.adventure-works.com
```

## <a name="see-also"></a>関連項目

- [名前空間の概要](namespaces-overview.md)
