---
title: XML ツリーから要素、属性、ノードを削除する - LINQ to XML
description: XML ツリーから要素、属性、およびその他の種類のノードを削除する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 1a7c10892ccf1baaab7dde700266a134abe727de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412078"
---
# <a name="remove-elements-attributes-and-nodes-from-an-xml-tree-linq-to-xml"></a>XML ツリーから要素、属性、ノードを削除する (LINQ to XML)

要素、属性、およびその他の種類のノードを削除して、XML ツリーを変更できます。

1 つの要素または 1 つの属性は XML ドキュメントから簡単に削除できます。 一方、要素または属性のコレクションを削除する場合は、まずコレクションをリストに具体化し、そのリストから要素または属性を削除する必要があります。 最適な方法は、<xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用してこれを行うことです。

この方法を使用する主な理由は、XML ツリーから取得するコレクションのほとんどが遅延実行を使用して生成されるからです。 最初にコレクションをリストに具体化せず、拡張メソッドも使用しない場合、特定の種類のバグが発生する可能性があります。 詳細については、「[宣言型コードと命令型コードの混在バグ](mixed-declarative-imperative-code-bugs.md)」を参照してください。

ノードおよび属性を XML ツリーから削除するメソッドを次に示します。

|メソッド|説明|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XAttribute> をその親から削除します。|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|子ノードを <xref:System.Xml.Linq.XContainer> から削除します。|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|コンテンツおよび属性を <xref:System.Xml.Linq.XElement> から削除します。|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XElement> の属性を削除します。|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|値 `null` を渡す場合は、属性を削除します。|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|値 `null` を渡す場合は、子要素を削除します。|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XNode> をその親から削除します。|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|ソース コレクション内のすべての属性または要素をその親要素から削除します。|

## <a name="example-remove-a-single-element-and-remove-a-collection-of-elements-in-two-ways"></a>例: 1 つの要素を削除し、要素のコレクションを 2 つの方法で削除する

この例では、要素を削除する 3 つの方法を示します。 まず、1 つの要素を削除します。 次に、要素のコレクションを取得し、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 演算子を使用して要素を具体化してから、コレクションを削除します。 最後に、要素のコレクションを取得し、<xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用して要素を削除します。

<xref:System.Linq.Enumerable.ToList%2A> 演算子の詳細については、「[データ型の変換 (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md)」と「[データ型の変換 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)」を参照してください。

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1/>
            <GrandChild2/>
            <GrandChild3/>
        </Child1>
        <Child2>
            <GrandChild4/>
            <GrandChild5/>
            <GrandChild6/>
        </Child2>
        <Child3>
            <GrandChild7/>
            <GrandChild8/>
            <GrandChild9/>
        </Child3>
    </Root>
root.<Child1>.<GrandChild1>.Remove()
root.<Child2>.Elements().ToList().Remove()
root.<Child3>.Elements().Remove()
Console.WriteLine(root)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

最初の孫要素が `Child1` から削除され、すべての孫要素が `Child2` と `Child3` から削除されました。
