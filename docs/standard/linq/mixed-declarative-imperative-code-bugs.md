---
title: 宣言型と命令型のコードの混在時のバグ - LINQ to XML
description: コードで 1 つの軸が反復処理されるときに発生するおそれのある問題を把握し、回避する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412011"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a>宣言型と命令型のコードの混在時のバグ (LINQ to XML)

LINQ to XML には、XML ツリーを直接変更する方法が多数あります。 たとえば、要素の追加、要素の削除、要素の内容の変更、属性の追加などの操作を行うことができます。 このプログラミング インターフェイスについては、[XML ツリーの変更](in-memory-xml-tree-modification-vs-functional-construction.md)に関するページで説明しています。 いずれかの軸 (<xref:System.Xml.Linq.XContainer.Elements%2A> など) を反復処理する場合に、その過程で XML ツリーを変更すると、見慣れないバグが発生することがあります。

この問題は、"ハロウィーン問題" と呼ばれることがあります。

コレクションを反復処理するコードを LINQ を使用して記述する場合は、宣言型スタイルでコードを記述することになります。 この場合、"*どのように*" 処理するかではなく、"*何が*" 必要かを記述します。 たとえば、1) 最初の要素を取得する、2) この要素を何らかの条件に対してテストする、3) この要素を変更する、4) この要素をリストに戻す、というコードを記述した場合、それは命令型のコードです。 コンピューターに、必要な処理を "*どのように*" 行うかを指示します。

この 2 つのスタイルのコードが同じ操作に混在していると、問題の原因になります。 次に例を示します。

3 つの項目 (a、b、および c) を含むリンク リストがあるとします。

> a -> b -> c

このリンク リスト内を移動しながら 3 つの新しい項目 (a'、b'、および c') を追加して、 次のようなリンク リストが生成されるようにします。

 > a -> a' -> b -> b' -> c -> c'

ここで、リストを反復処理して各項目の後ろに新しいアイテムを追加するコードを記述した場合、 その結果は、コードによって最初に `a` 要素が検出され、その後ろに `a'` が追加されます。 これで、お使いのコードは現在は `a'` のリストの次のノードに移動します。つまり、リストの a' と b の間に新しい項目が追加されます。

これを解決するにはどうすればよいでしょうか。 まず、元のリンク リストをコピーして、まったく新しいリストを作成する方法が考えられます。 また、純粋な命令型のコードを記述するのであれば、最初の項目を検出し、新しい項目を追加したら、リンク リストの 2 つ先 (追加した要素を越えた先) に移動するという方法もあります。

## <a name="example-adding-while-iterating"></a>例: 反復処理しながら追加する

たとえば、次のように、ツリーのすべての要素の複製を作成するコードを記述したいとします。

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

このコードは、無限ループに入ります。 `foreach` ステートメントは、`Elements()` 軸を反復処理して `doc` 要素に新しい要素を追加しますが、 追加した要素も反復処理されることになります。 ループが繰り返されるたびに新しいオブジェクトが割り当てられるため、最後には使用可能なメモリがすべて消費されてしまいます。

この問題を修正するには、次のように、標準クエリ演算子の <xref:System.Linq.Enumerable.ToList%2A> を使用してコレクションをメモリに読み込みます。

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    root.Add(new XElement(e.Name, (string)e));
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

これで、コードが機能するようになります。 結果の XML ツリーは次のようになります。

```xml
<Root>
  <A>1</A>
  <B>2</B>
  <C>3</C>
  <A>1</A>
  <B>2</B>
  <C>3</C>
</Root>
```

## <a name="example-deleting-while-iterating"></a>例: 反復処理しながら削除する

特定のレベルのノードをすべて削除する場合、次のようなコードを記述することが考えられます。

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

しかし、これでは目的の処理は行われません。 この場合、最初の要素 A を削除すると、ルートに含まれる XML ツリーから削除され、反復処理を行っている Elements メソッド内のコードが次の要素を見つけられなくなります。

この例を実行すると、次の出力が生成されます。

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

この問題を解決するには、先ほどと同じように、<xref:System.Linq.Enumerable.ToList%2A> を呼び出してコレクションを具体化します。

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

この例を実行すると、次の出力が生成されます。

```xml
<Root />
```

他の方法として、親要素で <xref:System.Xml.Linq.XElement.RemoveAll%2A> を呼び出して、反復処理を完全に取り除くこともできます。

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a>例: LINQ がこれらの問題を自動的に処理できない理由

まず、レイジー評価を行う代わりに常にすべてをメモリに読み込む方法が考えられます。 しかし、この方法では、パフォーマンスとメモリ使用量のコストが非常に高くなります。 実際、LINQ および LINQ to XML でこの方法を使用したとしても、現実には使いものにならないでしょう。

その他に、ある種のトランザクション構文を LINQ に追加して、特定のコレクションを具体化する必要があるかどうかをコンパイラにコードを分析させ判断させる方法があります。 しかし、副作用のあるコードをすべて特定しようとすると非常に複雑になります。 次のコードがあるとします。

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

このような分析コードで副作用のあるコードの有無を特定するには、TestSomeCondition および DoMyProjection の 2 つのメソッドと、これらが呼び出すすべてのメソッドを分析する必要があります。 しかし、その分析コードでは、ただ副作用のあるコードを探すだけでなく、 この状況では、`root` の子要素に対して副作用があるコードのみを選択する必要があります。

LINQ to XML ではこのような分析は行いません。 これらの問題は、自分で回避する必要があります。

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a>例: 既存のツリーを変更するのではなく、宣言型コードを使用して新しい XML ツリーを生成する

このような問題を回避するには、お使いのコレクションのセマンティクスと XML ツリーを変更するメソッドのセマンティクスを正確に把握している場合でも、宣言型と命令型のコードを混在させないでください。 問題を回避するコードを記述した場合でも、今後、その問題を明確に把握していない他の開発者が自分のコードを管理することになります。 宣言型と命令型のコーディング スタイルが混在していると、コードが不安定になります。  これらの問題を回避するためにコレクションを具体化するコードを記述する場合は、コードを保守するプログラマが問題を把握できるように、必要に応じてコメントを付けるようにしてください。

パフォーマンスやその他の事情が許すのであれば、宣言型のコードのみを使用するようにします。 既存の XML ツリーは変更せずに、 代わりに、次の例のとおり新しいものを生成します。

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
XElement newRoot = new XElement("Root",
    root.Elements(),
    root.Elements()
);
Console.WriteLine(newRoot);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```
