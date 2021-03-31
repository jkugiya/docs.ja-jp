---
title: アトミック化された XName および XNamespace オブジェクト - LINQ to XML
description: アトミック化された XName オブジェクトと XNamespace オブジェクトで名前が同じときにインスタンスを共有するしくみについて説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 05df7b5348fecebb7504ebb4e2623f688b6549e1
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "103366034"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a>アトミック化された XName および XNamespace オブジェクト (LINQ to XML)

<xref:System.Xml.Linq.XName> オブジェクトと <xref:System.Xml.Linq.XNamespace> オブジェクトは "*アトミック化*" されています。つまり、同じ修飾名を含んでいる場合は、同じオブジェクトを参照します。 これによってクエリのパフォーマンスが向上します。これは、2 つのアトミック化された名前の等価性を比べる場合に、基になる中間言語が、2 つの参照が同じオブジェクトを指しているかどうかを判別するだけで済むためです。 基になるコードは、時間のかかることがある文字列比較を行う必要がありません。

## <a name="atomization-semantics"></a>アトミック化のセマンティクス

アトミック化とは、2 個の <xref:System.Xml.Linq.XName> オブジェクトのローカル名が同じであり、これらのオブジェクトが同じ名前空間にある場合に、同じインスタンスを共有するという意味です。 同様に、2 個の <xref:System.Xml.Linq.XNamespace> オブジェクトに同じ名前空間 URI がある場合も、これらのオブジェクトは同じインスタンスを共有します。

アトミック化されたオブジェクトをクラスに対して有効にするには、クラスのコンストラクターがパブリックではなく、プライベートであることが必要です。 その理由は、コンストラクターがパブリックであれば、アトミック化されていないオブジェクトを作成できるからです。 <xref:System.Xml.Linq.XName> クラスと <xref:System.Xml.Linq.XNamespace> クラスは暗黙的な変換演算子を実装して、文字列を <xref:System.Xml.Linq.XName> または <xref:System.Xml.Linq.XNamespace> に変換します。 この方法でこれらのオブジェクトのインスタンスを取得します。 コンストラクターにはアクセスできないため、コンストラクターを使用してインスタンスを取得することはできません。

<xref:System.Xml.Linq.XName> と <xref:System.Xml.Linq.XNamespace> では、等値演算子と非等値演算子も実装されます。これらの演算子では、比較する 2 個のオブジェクトが同じインスタンスを参照しているか判断されます。

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a>例: オブジェクトを作成し、同じ名前でインスタンスを共有していることを示す

次のコードは <xref:System.Xml.Linq.XElement> オブジェクトを作成して、同じ名前が同じインスタンスを共有することを示します。

```csharp
var r1 = new XElement("Root", "data1");
XElement r2 = XElement.Parse("<Root>data2</Root>");

if ((object)r1.Name == (object)r2.Name)
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");
else
    Console.WriteLine("Different");

XName n = "Root";

if ((object)n == (object)r1.Name)
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");
else
    Console.WriteLine("Different");
```

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

この例を実行すると、次の出力が生成されます。

```output
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

前述のように、アトミック化されたオブジェクトの利点は、パラメーターとして <xref:System.Xml.Linq.XName> がある軸メソッドの 1 つを使用するときに、目的の要素を選択するために、軸メソッドが、2 つの名前が同じインスタンスを参照していることを判別するだけで済むことです。

次の例では、<xref:System.Xml.Linq.XName> を <xref:System.Xml.Linq.XContainer.Descendants%2A> メソッド呼び出しに渡すので、アトミック化パターンによってパフォーマンスが向上します。

```csharp
var root = new XElement("Root",
    new XElement("C1", 1),
    new XElement("Z1",
        new XElement("C1", 2),
        new XElement("C1", 1)
    )
);

var query = from e in root.Descendants("C1")
            where (int)e == 1
            select e;

foreach (var z in query)
    Console.WriteLine(z);
```

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1

For Each z In query
    Console.WriteLine(z)
Next
```

この例を実行すると、次の出力が生成されます。

```xml
<C1>1</C1>
<C1>1</C1>
```
