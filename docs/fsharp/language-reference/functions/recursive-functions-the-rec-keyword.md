---
title: '再帰関数: rec キーワード'
description: 再帰関数を定義するために F# 'let' キーワードと共に 'rec' キーワードを使用する方法について説明します。
ms.date: 08/12/2020
ms.openlocfilehash: 27f215f7b6f09646e847898c2618cfac10175e6e
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215713"
---
# <a name="recursive-functions-the-rec-keyword"></a>再帰関数: rec キーワード

`rec` キーワードは、`let` キーワードと共に使用して、再帰関数を定義します。

## <a name="syntax"></a>構文

```fsharp
// Recursive function:
let rec function-nameparameter-list =
    function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
    function1-body

and function2-nameparameter-list =
    function2-body
...
```

## <a name="remarks"></a>解説

再帰関数 (それ自身を呼び出す関数) は、F# 言語では、`rec` キーワードを使用して明示的に識別します。 `rec` キーワードを使用すると、`let` バインドの名前をその本体で使用できるようになります。

次の例は、数学的な定義を使用して *n*<sup> </sup>番目のフィボナッチ数を計算する再帰関数を示しています。

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> n
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> 実際には、前のサンプルのようなコードは、既に計算されている値を不必要に再計算しているため、理想的ではありません。 これは、この記事で詳しく説明されている末尾再帰ではないためです。

メソッドは、それが定義されている型内で暗黙的に再帰になるため、`rec` キーワードを追加する必要はありません。 次に例を示します。

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> n
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

ただし、クラス内の let バインドは暗黙的に再帰ではありません。 すべての `let` バインド関数には `rec` キーワードが必要です。

## <a name="tail-recursion"></a>末尾再帰

再帰関数によっては、より "純粋な" 定義を[末尾再帰](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)にリファクターする必要があります。 これにより、不必要な再計算が防止されます。 たとえば、前のフィボナッチ数ジェネレーターは、次のように書き換えることができます。

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

これは、より複雑な実装です。 フィボナッチ数の生成は、数学的には純粋であるものの実際には非効率である "単純な" アルゴリズムの好例です。 再帰的に定義されていることに変わりないものの、次のいくつかの側面によって、F# での効率が上がります。

* `loop` という名前の再帰的な内部関数。これは F# の慣用的なパターンです。
* 2 つのアキュムレータ パラメーター。これらは累積値を再帰呼び出しに渡します。
* `n` の値をチェックして、特定の累積値を返します。

ループを使用して反復的にこの例を記述したとすると、そのコードは、特定の条件が満たされるまで 2 つの異なる数値を累積していくものになります。

これが末尾再帰であると言えるのは、この再帰呼び出しでは、コール スタックに値を保存する必要がないためです。 計算されるすべての中間値は、内部関数への入力によって累積されます。 こうすれば、`while` ループのようなものを記述した場合と同様に高速になるよう、F# コンパイラでコードを最適化することもできます。

前の例で示したように、内部および外部関数を使用して何かを再帰的に処理する F# コードを記述するのは、一般的なことです。 内部関数では末尾再帰を使用しますが、外部関数は呼び出し元に対してより適切なインターフェイスを備えています。

## <a name="mutually-recursive-functions"></a>相互再帰関数

場合によっては、関数が "*相互再帰*" になることがあります。これは呼び出しが環状になって、最初に呼び出した別の関数から、今度は自分が呼び出されることです。両者の間の呼び出し回数は任意です。 このような関数は、1 つの `let` バインドの中で一緒に定義し、`and` キーワードを使用してそれらをリンクする必要があります。

次の例は、2 つの相互再帰関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a>再帰的な値

`let` バインドの値が再帰的になるように定義することもできます。 これは、ログ記録のために行われることがあります。 F# 5 と `nameof` 関数を使用すると、次の操作を実行できます。

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a>関連項目

- [関数](index.md)
