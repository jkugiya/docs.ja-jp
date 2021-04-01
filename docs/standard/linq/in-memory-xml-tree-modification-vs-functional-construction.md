---
title: メモリ内の XML ツリーの変更と関数型構築の比較 - LINQ to XML
description: XML ツリーを変更する 2 つの別の方法の例について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411966"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a>メモリ内の XML ツリーの変更と関数型構築の比較 (LINQ to XML)

XML ドキュメントの構造を変更する場合は、XML ツリーを直接変更するのが従来の方法です。 一般的なアプリケーションでは、ドキュメントを DOM や LINQ to XML などのデータ ストアに読み込み、プログラミング インターフェイスを使用してノードを挿入、削除、またはその内容を変更し、その後に XML をファイルに保存するか、それをネットワーク上で送信します。

LINQ to XML には、もう 1 つ、多数のシナリオで役立つ "*関数型構築*" という方法があります。 関数型構築では、データの変更が、データ ストアの詳細な操作としてではなく変換の問題として扱われます。 データの表現をある形式から別の形式に効率よく変換できれば、データ ストアを何らかの方法で操作して別の構造にする場合と同じ結果を得られます。 関数型構築の方法で重要なのは、クエリの結果を <xref:System.Xml.Linq.XDocument> コンストラクターと <xref:System.Xml.Linq.XElement> コンストラクターに渡す処理です。

多くの場合、変換コードは、データ ストアを操作する場合に比べてわずかな時間で作成でき、その結果のコードはより堅牢で保守性に優れています。 この場合、変換する方法では、より大きな処理能力を必要とする可能性はありますが、より効率的にデータを変更できます。 開発者が関数型の方法に精通していれば、多くの場合、結果として得られるコードは理解しやすく、ツリーの各部分を変更するコードを簡単に見つけることができます。

DOM プログラマの多くは、XML ツリーを直接変更する方法に慣れています。これに対し、関数型の方法で記述されたコードは、それをまだ理解していない開発者とっては、なじみのないものです。 大きな XML ツリーに小さな変更を加えるだけであれば、ツリーを直接変更する方法の方が使用する CPU 時間が少ない場合がほとんどです。

この記事では、両方の方法の例を示します。 属性が要素となるように、次の単純な XML ドキュメントを変更したいとします。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

次の最初の例では、従来の直接変更する方法を使用し、2 番目の例では関数型構築の方法を使用しています。

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a>例: 従来の直接の方法を使用して属性を要素に変換する

属性から要素を作成した後に属性を削除する、次のようなプロシージャ コードを記述します。

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a>例: 関数型構築方法を使用して属性を要素に変換する

対照的に、関数型の方法のコードでは、新しいツリーを作成し、ソース ツリーから要素と属性を選択し、その要素と属性を新しいツリーに追加するときに適宜変換します。

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

この例では、最初の例と同じ XML が出力されます。 ただし、関数型の方法では、新しい XML の構造が実際に作成されます。 `Root` 要素、ソース ツリーから `Child1` 要素を取り出すコード、およびソース ツリーから取得した属性を新しいツリーの要素に変換するコードが作成されることがわかります。

ここで示した関数型の例は、最初の例と比べて短くも、単純でもありません。 しかし XML ツリーに多数の変更を加える場合、手続き型の方法はかなり複雑で、効率的ではなくなります。 一方、関数型の方法では、クエリと式を適宜組み込んだ必要な XML を作成するだけで、必要な内容を取り出せます。 関数型の方法で生成されたコードの方が、保守も簡単です。

この例では、ツリーを操作する方法に比べて関数型の方法のパフォーマンスが低くなる可能性があるので注意してください。 主な問題は、関数型の方法では存続期間の短いオブジェクトがより多く作成されることです。 その代わりに、関数型の方法の方がプログラマの生産性が高いという効果があります。

ここで示したのはごく単純な例ですが、2 つの方法に関する考え方の違いをよく表しています。 大きな XML ドキュメントを変換する場合は、関数型の方法を使用した方が生産性が高くなります。
