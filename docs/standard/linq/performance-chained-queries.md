---
title: 連結クエリのパフォーマンス - LINQ to XML
description: 複雑で大きな単一クエリと同様のパフォーマンスを発揮する連結クエリについて説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: c1dae1eaf008a1f17c6884ef6b8e67d042719ad9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411988"
---
# <a name="performance-of-chained-queries-linq-to-xml"></a>連結クエリのパフォーマンス (LINQ to XML)

LINQ (および LINQ to XML) の重要な利点の 1 つは、連結クエリがそれより大きく複雑な単一クエリと同様のパフォーマンスを発揮できるという点です。

連結クエリとは、別のクエリをソースとして使用するクエリです。 たとえば、次の単純なコードでは、`query2` のソースとして `query1` があります。

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

この例を実行すると、次の出力が生成されます。

```output
4
```

この連結クエリは、リンク リストの反復と同じパフォーマンス プロファイルを提供します。

- <xref:System.Xml.Linq.XContainer.Elements%2A> 軸のパフォーマンスは、基本的にリンク リストの反復と同じです。 <xref:System.Xml.Linq.XContainer.Elements%2A> は、遅延実行のある反復子として実装されます。 つまり、リンク リストの反復の他に、反復子オブジェクトの割り当てや実行状態の追跡などの作業をします。 この作業は、反復子の設定時に行われる作業と、各反復中に行われる作業の 2 つのカテゴリに分けることができます。 設定作業は一定量の小さい作業であり、各反復中に行われる作業はソース コレクションの項目数に比例します。
- `query1` では、`where` 句 (Visual Basic の場合は `Where`) によってクエリは <xref:System.Linq.Enumerable.Where%2A> メソッドを呼び出します。 このメソッドも反復子として実装されています。 設定作業は、ラムダ式を参照するデリゲートのインスタンス化と、反復子の通常の設定から成ります。 反復ごとに、デリゲートが呼び出されて述語を実行します。 設定作業と、各反復中に行われる作業は、軸の反復中に行われる作業に似ています。
- `query1` では、SELECT 句によってクエリが <xref:System.Linq.Enumerable.Select%2A> メソッドを呼び出します。 このメソッドには <xref:System.Linq.Enumerable.Where%2A> メソッドと同じパフォーマンス プロファイルがあります。
- `query2` では、`where` 句 (Visual Basic の場合は `Where`)と `select` 句の両方に `query1` と同じパフォーマンス プロファイルがあります。

したがって、`query2` の反復は最初のクエリのソースにある項目数に直接比例します。つまり線形時間となります。

反復子の詳細については、「[yield](../../csharp/language-reference/keywords/yield.md)」を参照してください。

クエリの連結に関する詳細なチュートリアルについては、「[チュートリアル: クエリを連結する (C#)](chain-queries-example.md)」を参照してください。
