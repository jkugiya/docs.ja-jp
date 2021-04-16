---
title: 遅延式
description: F# の遅延式を使ってアプリとライブラリのパフォーマンスを向上させる方法について説明します。
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425504"
---
# <a name="lazy-expressions"></a>遅延式

"*遅延式*" は、すぐには評価されず、結果が必要なときに評価される式です。 これは、コードのパフォーマンスを向上させるのに役立ちます。

## <a name="syntax"></a>構文

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>解説

前の構文では、*expression* は結果が必要な場合にのみ評価されるコードであり、*identifier* は結果を格納する値です。 値は `Lazy<'T>` 型であり、`'T` に使用される実際の型は、式の結果から決定されます。

遅延式を使用すると、式の実行を、結果が必要な場合のみに制限することで、パフォーマンスを向上させることができます。

式を強制的に実行するには、メソッド `Force` を呼び出します。 `Force` を使用すると、実行が一度だけ行われます。 その後で `Force` を呼び出すと、同じ結果が返されますが、コードは実行されません。

次のコードは、遅延式の使用方法と `Force` の使用方法を示しています。 このコードでは、`result` の型は `Lazy<int>` で、`Force` メソッドは `int` を返します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

`Lazy` 型ではない遅延評価は、シーケンスにも使用されます。 詳細については、[シーケンス](sequences.md)にするページをご覧ください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [LazyExtensions モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
