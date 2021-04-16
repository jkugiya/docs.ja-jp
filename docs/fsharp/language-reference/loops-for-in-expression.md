---
title: 'ループ: for...in 式'
description: 列挙可能なコレクションのパターンと一致するかどうかの照合を反復処理するために、F# for...in 式のループ コンストラクトをどのように使用するかについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216453"
---
# <a name="loops-forin-expression"></a>ループ: for...in 式

このループ コンストラクトは、列挙可能なコレクション (範囲表現、シーケンス、リスト、配列、または列挙型をサポートするその他のコンストラクト) のパターンと一致するかどうかの照合を反復処理するために使用されます。

## <a name="syntax"></a>構文

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>解説

列挙可能なコレクションの値をループ処理するために使用されるため、`for...in` 式は、他の .NET 言語の `for each` ステートメントと比較できます。 ただし、`for...in` では、単にコレクション全体に対して反復処理するだけでなく、コレクションに対するパターン マッチングもサポートされています。

列挙可能な式は、列挙可能なコレクションとしても、`..` 演算子を使用して整数型の範囲としても指定することができます。 列挙可能なコレクションには、リスト、シーケンス、配列、セット、マップなどが含まれます。 `System.Collections.IEnumerable` を実装する任意の型を使用することができます。

`..` 演算子を使用して範囲を表現する場合、次の構文を使用することができます。

*start* .. *finish*

次のコードのように、*skip* と呼ばれるインクリメントを含むバージョンを使用することもできます。

*start* .. *skip* .. *finish*

整数の範囲と単純なカウンター変数をパターンとして使用する場合の一般的な動作は、各反復処理でカウンター変数を 1 ずつインクリメントすることですが、範囲に skip 値が含まれている場合は、代わりに skip 値ごとにカウンターがインクリメントされます。

パターンに一致した値は、本文の式にも使用できます。

次のコード例では、`for...in` 式の使用例を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

出力は次のとおりです。

```console
1
5
100
450
788
```

次の例では、シーケンスをループ処理する方法と、単純な変数の代わりにタプル パターンを使用する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

出力は次のとおりです。

```console
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

次の例では、単純な整数範囲をループ処理する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

function1 の出力は次のとおりです。

```console
1 2 3 4 5 6 7 8 9 10
```

次の例では、範囲を skip 2 でループ処理する方法を示しています。範囲の要素が 1 つおきに含まれます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

`function2` の出力は次のとおりです。

```console
1 3 5 7 9
```

次の例では、文字範囲を使用する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

`function3` の出力は次のとおりです。

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

次の例では、負の skip 値を使用して、逆の反復処理を行う方法を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

`function4` の出力は次のとおりです。

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

次のコードのように、範囲の先頭と末尾には、関数などの式を指定することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

この入力による `function5` の出力は次のとおりです。

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

次の例は、ループで要素が不要な場合に、ワイルドカード文字 (\_) を使用する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

出力は次のとおりです。

```console
Number of elements in list1: 5
```

`Note` `for...in` は、シーケンス式やその他のコンピュテーション式で使用することができます。その場合は、`for...in` 式のカスタマイズされたバージョンを使用します。 詳細については、「[シーケンス](sequences.md)」、「[非同期ワークフロー](asynchronous-workflows.md)」、「[コンピュテーション式](computation-expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [ループ: `for...to` 式](loops-for-to-expression.md)
- [ループ: `while...do` 式](loops-while-do-expression.md)
