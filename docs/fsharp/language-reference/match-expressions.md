---
title: match 式
description: F# match 式により、式と一連のパターンとの比較に基づいて分岐がどのように制御されるかを説明します。
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627611"
---
# <a name="match-expressions"></a>match 式

`match` 式により、式と一連のパターンとの比較に基づいて分岐が制御されます。

## <a name="syntax"></a>構文

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>解説

パターン マッチング式を使用すると、テスト式と一連のパターンとの比較に基づいて、複雑な分岐が可能になります。 `match` 式では、各パターンと *test-expression* が比較され、一致が見つかると、対応する *result-expression* が評価され、結果の値が match 式の値として返されます。

前の構文で示されているパターン マッチング関数は、パターン マッチングが引数ですぐに実行されるラムダ式です。 前の構文で示されているパターン マッチング関数は、以下と同じです。

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

ラムダ式について詳しくは、「[ラムダ式: `fun` キーワード](./functions/lambda-expressions-the-fun-keyword.md)」を参照してください。

一連のパターン全体で、入力変数のすべての一致候補をカバーする必要があります。 多くの場合、それより前で一致していない入力値と一致させるために、最後のパターンとしてワイルドカード パターン (`_`) を使用します。

次のコードは、`match` 式が使用されるいくつかの方法を示しています。 使用可能なすべてのパターンの参照と例については、「[パターン マッチング](pattern-matching.md)」を参照してください。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>パターンでのガード

`when` 句を使用して、変数がパターンに一致するために満たす必要のある追加条件を指定できます。 このような句を *ガード* と呼びます。 `when` キーワードに続く式は、そのガードに関連付けられているパターンと一致しない限り評価されません。

次の例は、変数パターンの数値範囲を指定するためのガードの使用例を示しています。 複数の条件は、ブール演算子を使用することによって結合されていることに注意してください。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

リテラル以外の値はパターンで使用できないため、入力の一部を値と比較する必要がある場合は、`when` 句を使用する必要があります。 これを次のコードに示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

和集合パターンがガードでカバーされている場合、ガードは、最後のものだけでなく、**すべて** のパターンに適用されます。 たとえば、次のコードにおいて、ガード `when a > 12` は `A a` と `B a` の両方に適用されます。

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [アクティブ パターン](active-patterns.md)
- [パターン一致](pattern-matching.md)
