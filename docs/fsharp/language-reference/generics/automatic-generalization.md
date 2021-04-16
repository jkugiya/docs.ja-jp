---
title: 自動ジェネリック化
description: F# で関数の引数や型を自動的にジェネリック化して、可能な場合に複数の型を処理できるようにする方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630626"
---
# <a name="automatic-generalization"></a>自動ジェネリック化

F# では、型の推定を使用して関数と式の型を評価します。 このトピックでは、F# で関数の引数や型を自動的にジェネリック化して、可能な場合に複数の型を処理できるようにする方法を説明します。

## <a name="automatic-generalization"></a>自動ジェネリック化

F# コンパイラによって関数に対して型の推定が実行されるときには、特定のパラメーターをジェネリックにできるかどうかが判断されます。 コンパイラによって各パラメーターが調査され、関数にそのパラメーターの特定の型に対する依存関係があるかどうかが判定されます。 ない場合は、型はジェネリックと推論されます。

次のコード例では、コンパイラによってジェネリックと推論される関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

型は、`'a -> 'a -> 'a` と推論されます。

この型により、この関数は、不明である同じ型を持つ 2 つの引数を指定されて、その同じ型の値を返すことがわかります。 前の関数がジェネリックになれる理由の 1 つは、大なり演算子 (`>`) 自体がジェネリックであることです。 大なり演算子のシグネチャは `'a -> 'a -> bool` です。 すべての演算子がジェネリックであるとは限りません。関数内のコードで、あるパラメーター型が非ジェネリック関数または演算子と共に使用されている場合、そのパラメーター型をジェネリック化することはできません。

`max` はジェネリックであるため、次の例に示すように、`int`、`float` などの型で使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

ただし、2 つの引数は同じ型である必要があります。 シグネチャは `'a -> 'a -> 'a` であり、`'a -> 'b -> 'a` ではありません。 したがって、次のコードでは型が一致しないため、エラーが生成されます。

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` 関数は、大なり演算子をサポートするどの型でも動作します。 したがって、次のコードに示すように、文字列で使用することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>値制限

コンパイラで自動ジェネリック化が実行されるのは、明示的な引数を持つ完全な関数定義と、単純な不変の値に対してのみです。

つまり、特定の型とするには制約が不十分であるものの、ジェネリック化することもできないコードをコンパイルしようとすると、コンパイラからエラーが発行されるということです。 この問題のエラー メッセージで、値の自動ジェネリック化に関するこの制約は "*値制限*" と呼ばれます。

通常、値制限エラーが発生するのは、コンストラクトをジェネリックにすることを希望しているものの、それをジェネリック化するための情報がコンパイラに不足している場合か、誤って非ジェネリック コンストラクトで十分な型情報を省略してしまった場合です。 値制限エラーの解決策は、型の推定の問題をより十分に制限するために、次のいずれかの方法で、より明示的な情報を提供することです。

- 値またはパラメーターに明示的な型の注釈を追加することにより、型を非ジェネリックに制約します。

- ジェネリック化できないコンストラクトを使ってジェネリック関数を定義していることが問題の場合 (関数合成や、完全適用されていないカリー化関数の引数など)、通常の関数定義として関数を書き直してみてください。

- 式が複雑すぎてジェネリック化できないことが問題である場合は、使用しない余分なパラメーターを追加して、式を関数にします。

- 明示的なジェネリック型パラメーターを追加します。 このオプションはほとんど使用されません。

- 次のコード例は、これらの各シナリオを示しています。

ケース 1: 式が複雑すぎる。 この例で、リスト `counter` は `int option ref` となるよう意図されていますが、単純な不変の値として定義されていません。

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

ケース 2: ジェネリック化できないコンストラクトを使用してジェネリック関数を定義する。 この例では、コンストラクトは、関数の引数の部分適用を伴うため、ジェネリック化できません。

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

ケース 3: 使用されない余分なパラメーターを追加する。 この式はジェネリック化できるほど単純ではないため、コンパイラから値制限エラーが発行されます。

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

ケース 4: 型パラメーターを追加する。

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

最後のケースでは、値が型関数になり、次に示す例のように、さまざまな型の値を作成するために使用できます。

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>関連項目

- [型推論](../type-inference.md)
- [ジェネリック](index.md)
- [静的に解決される型パラメーター](statically-resolved-type-parameters.md)
- [制約](constraints.md)
