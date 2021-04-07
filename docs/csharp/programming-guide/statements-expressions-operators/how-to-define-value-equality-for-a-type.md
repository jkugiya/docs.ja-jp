---
title: クラスまたは構造体の値の等価性を定義する方法 - C# プログラミング ガイド
description: クラスまたは構造体の値の等価性を定義する方法について説明します。 コード例を参照し、使用可能なリソースをご確認ください。
ms.date: 03/26/2021
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: fd8e1e14650a836178534b44dc332215c0d0586a
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079454"
---
# <a name="how-to-define-value-equality-for-a-class-or-struct-c-programming-guide"></a>クラスまたは構造体の値の等価性を定義する方法 (C# プログラミング ガイド)

[レコード](../classes-and-structs/records.md)を使用すると、値の等価性が自動的に実装されます。 ご利用の型によって、データをモデル化する場合や値の同等性を実装する必要がある場合は、`class` ではなく `record` を定義することを検討してください。

クラスまたは構造体を定義する場合は、型に値の等価性 (同値) のカスタム定義を作成することが有用かどうかを判断します。 通常、値の等価性を実装するのは、その型のオブジェクトをコレクションに追加する予定である場合、またはそれらの主な目的が一連のフィールドまたはプロパティを格納することである場合です。 値の等価性は、型のすべてのフィールドおよびプロパティの比較に基づいて定義できます。また、サブセットに基づいて定義することもできます。

いずれの場合も、クラスおよび構造体の両方について、等価性を保証する 5 つの条件に従って実装する必要があります (次のルールの場合、`x`、`y`、`z` が null ではないと想定しています)。  
  
1. 再帰プロパティ: `x.Equals(x)` から `true` が返されます。
  
2. 対称プロパティ: `x.Equals(y)` から、`y.Equals(x)` と同じ値が返されます。
  
3. 推移性プロパティ: `(x.Equals(y) && y.Equals(z))` から `true` が返される場合は、`x.Equals(z)` からは `true` が返されます。
  
4. `x.Equals(y)` が連続して呼び出された場合は、x と y によって参照されるオブジェクトが変更されていない限り、同じ値を返します。  
  
5. 非 null 値は null と等しくありません。 そのため、`x` が null である場合は、`x.Equals(y)` から例外がスローされます。 それにより、`Equals` の引数に基づき、ルール 1 または 2 が破られます。

構造体を定義すると、<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> メソッドの <xref:System.ValueType?displayProperty=nameWithType> オーバーライドから継承された値の等価性が既定で実装されます。 この実装では、リフレクションを使用して、型のフィールドとプロパティをすべて調べます。 この実装によって正しい結果が生成されますが、その型専用に記述したカスタム実装と比較すると、処理にかなり時間がかかります。  
  
値の等価性に関する実装の詳細は、クラスと構造体で異なりますが、 等価性を実装するための基本的な手順については、両方とも同じです。  
  
1. [仮想](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> メソッドをオーバーライドします。 ほとんどの場合、`bool Equals( object obj )` の実装には、<xref:System.IEquatable%601?displayProperty=nameWithType> インターフェイスの実装である型固有の `Equals` メソッドを呼び出すだけで済みます (手順 2 を参照)。  
  
2. 型固有の `Equals` メソッドを指定して、<xref:System.IEquatable%601?displayProperty=nameWithType> インターフェイスを実装します。 ここで実際の等価性の比較を実行します。 たとえば、型のフィールドを 1 ～ 2 個だけ比較することで等価性を定義できます。 `Equals` から例外をスローしないでください。 継承によって関連付けられているクラスの場合:

   * このメソッドはクラスで宣言されているフィールドのみを調べます。 基底クラスに含まれるフィールドを調べるには、`base.Equals` を呼び出す必要があります (型が <xref:System.Object> から直接継承されている場合は、`base.Equals` を呼び出さないでください。<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> の <xref:System.Object> 実装によって、参照の等価性チェックが実行されるためです)。

   * 比較対象の変数の実行時の型が同じである場合にのみ、2 つの変数は等しいと見なされます。 また、変数の実行時とコンパイル時の型が異なる場合は、実行時の型の `Equals` メソッドの `IEquatable` 実装を必ず使用してください。 実行時の型が常に正しく比較されるようにするための方法の 1 つは、`sealed` クラスにのみ `IEquatable` を実装することです。 詳細については、この記事で後述する「[クラスの例](#class-example)」を参照してください。
  
3. 推奨、ただし省略可能: [==](../../language-reference/operators/equality-operators.md#equality-operator-) および [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) 演算子をオーバーロードします。  
  
4. 値の等価性を持つ 2 つのオブジェクトによって同じハッシュ コードが生成されるように、<xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> をオーバーライドします。  
  
5. 省略可能:"大なり" または "小なり" の定義をサポートするには、型に対して <xref:System.IComparable%601> インターフェイスを実装したうえで、[<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) および [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) 演算子をオーバーロードします。  

> [!NOTE]
> C# 9.0 以降、レコードを利用し、不要な定型コードなしで値の等価性セマンティクスを取得できます。

## <a name="class-example"></a>クラスの例

次の例は、クラス (参照型) で値の等価性を実装する方法を示しています。

:::code language="csharp" source="snippets/how-to-define-value-equality-for-a-type/ValueEqualityClass/Program.cs":::

クラス (参照型) の場合、両方の <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> メソッドの既定の実装で、参照の等価性の比較は実行されますが、値の等価性のチェックは実行されません。 実装が仮想メソッドをオーバーライドする場合、その目的は、仮想メソッドに値の等価性のセマンティクスを提供することです。

`==` 演算子と `!=` 演算子は、オーバーロードされなくてもクラスで使用できます。 ただし、既定の動作として参照の等価性のチェックが実行されます。 クラスで `Equals` メソッドをオーバーロードする場合は、`==` 演算子と `!=` 演算子をオーバーロードすることをお勧めしますが、必須ではありません。

> [!IMPORTANT]
> 前のコード例では、すべての継承シナリオが期待どおりに処理されるとは限りません。 次のコードがあるとします。
>
> ```csharp
> TwoDPoint p1 = new ThreeDPoint(1, 2, 3);
> TwoDPoint p2 = new ThreeDPoint(1, 2, 4);
> Console.WriteLine(p1.Equals(p2)); // output: True
> ```
>
> このコードを実行すると、`z` の値が異なるにもかかわらず、`p1` は `p2` に等しいと報告されます。 この違いが無視される理由は、コンパイルではコンパイル時の型に基づいて `IEquatable` の `TwoDPoint` 実装のみが選択されることにあります。
>
> `record` 型の組み込み値が等価である場合、このようなシナリオは正しく処理されます。 `TwoDPoint` と `ThreeDPoint` の型が `record` であるならば、`p1.Equals(p2)` の結果は `False` になります。 詳細については、[`record` 型の継承階層の等価性](../../language-reference/builtin-types/record.md#equality-in-inheritance-hierarchies)に関するページを参照してください。

## <a name="struct-example"></a>構造体の例

次の例は、構造体 (値型) で値の等価性を実装する方法を示しています。

:::code language="csharp" source="snippets/how-to-define-value-equality-for-a-type/ValueEqualityStruct/Program.cs":::
  
構造体の場合、<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (<xref:System.ValueType?displayProperty=nameWithType> でオーバーライドされるバージョン) の既定の実装で、リフレクションを使用して値の等価性のチェックが実行され、型のすべてのフィールドの値が比較されます。 実装が構造体の仮想 `Equals` メソッドをオーバーライドする場合、その目的は、値の等価性のチェックをより効率的に実行することと、オプションで、構造体のフィールドまたはプロパティの一部のサブセットに基づいて比較を行うことです。
  
[==](../../language-reference/operators/equality-operators.md#equality-operator-) および [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) 演算子を使用して構造体で操作することは、その構造体によってそれらの演算子が明示的にオーバーロードされない限り、不可能です。

## <a name="see-also"></a>関連項目

- [等価比較](equality-comparisons.md)
- [C# プログラミング ガイド](../index.md)
