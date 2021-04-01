---
title: C# で名前空間を持つドキュメントを作成する方法 - LINQ to XML
description: C# で XNamespace オブジェクトを使用して、既定の名前空間またはプレフィックスが付いた名前空間を持つドキュメントを作成します。
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 3ec9624bcc599a73a6872e5c4c79504a1a4b4380
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412052"
---
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a>C# で名前空間を持つドキュメントを作成する方法 (LINQ to XML)

この記事では、C# で名前空間を持つドキュメントを作成する方法について説明します。

## <a name="example-declare-and-initialize-a-default-namespace"></a>例: 既定の名前空間を宣言して初期化する

名前空間にある要素や属性を作成するには、最初に <xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化します。 次に、加算演算子オーバーロードを使用して名前空間をローカル名に連結し、文字列として表します。

次の例では、1 つの名前空間を持つドキュメントを作成します。 既定では、LINQ to XML によって、このドキュメントが既定の名前空間でシリアル化されます。

```csharp
// Create an XML tree in a namespace.
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

この例を実行すると、次の出力が生成されます。

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child>child content</Child>
</Root>
```

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a>例: 名前空間と属性を持つドキュメントを作成する

次の例では、1 つの名前空間を持つドキュメントを作成します。 名前空間プレフィックスを持つ名前空間を宣言する属性も作成します。 プレフィックス付きの名前空間を宣言する属性を作成するには、属性名が名前空間プレフィックスで、この名前が <xref:System.Xml.Linq.XNamespace.Xmlns%2A> 名前空間にある属性を作成します。 この属性の値は名前空間の URI です。

```csharp
// Create an XML tree in a namespace, with a specified prefix
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>例: 2 つの名前空間を持つドキュメントを作成し、1 つにプレフィックスを付ける

次の例では、2 つの名前空間が含まれるドキュメントを作成します。 1 つは既定の名前空間で、もう 1 つはプレフィックスが付いた名前空間です。

ルート要素に名前空間属性を含めることによって名前空間がシリアル化され、`http://www.adventure-works.com` が既定の名前空間となり、`www.fourthcoffee.com` は `fc` のプレフィックスでシリアル化されます。 既定の名前空間を宣言する属性を作成するには、`xmlns` という名前の属性を、名前空間を指定せずに作成します。 属性の値は、既定の名前空間 URI です。

```csharp
// The http://www.adventure-works.com namespace is forced to be the default namespace.
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute("xmlns", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

この例を実行すると、次の出力が生成されます。

```xml
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <DifferentChild>other content</DifferentChild>
  </fc:Child>
  <Child2>c2 content</Child2>
  <fc:Child3>c3 content</fc:Child3>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>例: 2 つの名前空間を持つドキュメントを作成し、両方にプレフィックスを付ける

次の例では、名前空間プレフィックスのある名前空間を 2 つ含むドキュメントを作成します。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="example-create-a-namespace-using-expanded-names"></a>例: 展開名を使用して名前空間を作成する

<xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して作成する代わりに、展開名を使用しても同じ結果が得られます。

ただし、この方法はパフォーマンスに影響を与えます。 展開名が含まれた文字列を LINQ to XML に渡すたびに、LINQ to XML は名前を解析して、アトミック化された名前空間を検索し、アトミック化された名前を見つける必要があります。 この処理は CPU 時間を消費します。 パフォーマンスが重要な場合には、<xref:System.Xml.Linq.XNamespace> オブジェクトを明示的に宣言して使用することをお勧めします。

パフォーマンスが重要な場合、詳細については、「[XName オブジェクトの事前アトミック化](pre-atomization-xname-objects.md)」を参照してください。

```csharp
// Create an XML tree in a namespace, with a specified prefix
XElement root = new XElement("{http://www.adventure-works.com}Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement("{http://www.adventure-works.com}Child", "child content")
);
Console.WriteLine(root);
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="see-also"></a>関連項目

- [名前空間の概要](namespaces-overview.md)
