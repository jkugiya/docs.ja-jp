---
title: Visual Basic で名前空間を持つドキュメントを作成する方法 - LINQ to XML
description: Visual Basic で XML リテラルを使用して、既定の名前空間またはプレフィックスが付いた名前空間を持つドキュメントを作成します。
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412050"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a>Visual Basic で名前空間を持つドキュメントを作成する方法 (LINQ to XML)

この記事では、Visual Basic で名前空間を持つドキュメントを作成する方法について説明します。

Visual Basic で XML リテラルを使用している場合、ユーザーは 1 つのグローバルな既定の XML 名前空間を定義できます。 この名前空間は、XML リテラルと XML プロパティの両方の既定の名前空間です。 既定の XML 名前空間は、プロジェクト レベルまたはファイル レベルで定義できます。 ファイル レベルで定義すると、プロジェクト レベルの既定の名前空間がオーバーライドされます。

他の名前空間を定義して、それらの名前空間のプレフィックスを指定することもできます。 `Imports` キーワードを使用して、両方の名前空間の種類を定義します。

詳細については、「[Visual Basic の XML リテラル](xml-literals.md)」を参照してください。

既定の XML 名前空間は要素だけに適用され、属性には適用されないことに注意してください。 既定では、属性は既定の名前空間にあります。 ただし、名前空間プレフィックスを使用して属性を名前空間に含めることができます。

## <a name="example-create-a-document-that-has-a-namespace"></a>例: 名前空間を持つドキュメントを作成する

この例では、1 つの名前空間を含むドキュメントを作成します。

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>例: 2 つの名前空間を持つドキュメントを作成し、1 つにプレフィックスを付ける

この例では、2 つの名前空間を含むドキュメントを作成します。 1 つは既定の名前空間で、もう 1 つはプレフィックスが付いています。

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>例: 2 つの名前空間を持つドキュメントを作成し、両方にプレフィックスを付ける

次の例では、名前空間プレフィックスのある名前空間を 2 つ含むドキュメントを作成します。

XML ツリーをシリアル化するとき、各要素が指定された名前空間に含まれるように、LINQ to XML によって必要に応じて名前空間宣言が生成されます。

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

End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a>関連項目

- [名前空間の概要](namespaces-overview.md)
