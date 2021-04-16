---
title: 'ラムダ式: fun キーワード'
description: F# の "fun" キーワードを使用して、匿名関数であるラムダ式を定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630661"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>ラムダ式: fun キーワード (F#)

`fun` キーワードは、ラムダ式、つまり匿名関数を定義するために使用されます。

## <a name="syntax"></a>構文

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>解説

*parameter-list* は、通常、名前と、必要に応じてパラメーターの型で構成されます。 より一般的には、*parameter-list* は任意の F# パターンで構成できます。 使用可能なパターンの完全な一覧については、「[パターン マッチ](../pattern-matching.md)」をご覧ください。 有効なパラメーターの一覧を次の例に示します。

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

*expression* は関数の本体であり、その最後の式で戻り値が生成されます。 有効なラムダ式の例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>ラムダ式の使用

ラムダ式は、リストまたは他のコレクションに対して操作を実行する必要があり、関数を定義する余分な作業を避ける必要がある場合に特に便利です。 多くの F# ライブラリ関数は、引数として関数の値を受け取ります。このような場合は、ラムダ式を使用すると特に便利です。 次のコードは、リストの要素にラムダ式を適用します。 この場合、匿名関数により、リストのすべての要素に 1 が加算されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>関連項目

- [関数](index.md)
