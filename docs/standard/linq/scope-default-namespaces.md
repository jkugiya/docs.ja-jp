---
title: 既定の名前空間のスコープ - LINQ to XML
description: XML ツリーで表される既定の名前空間は、クエリのスコープ内にありません。 クエリの実行方法として適切な方法と不適切な方法を次に示します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366019"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a>既定の名前空間のスコープ (LINQ to XML)

XML ツリーで表される既定の名前空間は、クエリのスコープ内にありません。 XML が既定の名前空間に属する場合、名前空間とローカル名を組み合わせ、クエリで使用する修飾名を作る必要があります。

既定の名前空間を持つ XML ツリーにクエリを実行するときによくある間違いは、その XML が名前空間に属していないかのようにクエリを作成することです。 最初の例で確認できる既定の名前空間のクエリは、不適切なクエリとして典型的なものです。 2 つ目からは適切なクエリを確認できます。

## <a name="example-improper-query-of-xml-in-a-namespace"></a>例: 名前空間における XML の不適切なクエリ

この例では、名前空間で XML が作成されており、不適切なクエリから空の結果セットが返されています。

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a>例: 名前空間における XML の適切なクエリ

この例では、名前空間で XML が作成されており、クリエは適切です。

C# の場合、正しいアプローチは、<xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化し、そのオブジェクトを <xref:System.Xml.Linq.XName> オブジェクトの指定時に使用することです。 この場合、<xref:System.Xml.Linq.XContainer.Elements%2A> メソッドの引数は <xref:System.Xml.Linq.XName> オブジェクトです。

Visual Basic を使用する場合は、グローバルな既定の名前空間を宣言して初期化するのが正しい方法です。 これにより、すべての XML プロパティが既定の名前空間に配置されます。

次にコードを示します。

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>関連項目

- [名前空間の概要](namespaces-overview.md)
