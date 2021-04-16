---
title: 'ループ: while...do 式'
description: while...do 式を使用して、指定したテスト条件が true の間に反復実行 (ループ) を行う方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 73526279358db101f8d07721a200920f1e87f119
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216636"
---
# <a name="loops-whiledo-expression"></a>ループ: while...do 式

`while...do` 式は、指定したテスト条件が true の間に反復実行 (ループ) を行う場合に使用します。

## <a name="syntax"></a>構文

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>解説

*test-expression* が評価されます。それが `true` の場合、*body-expression* が実行され、テスト式が再評価されます。 *body-expression* には型 `unit` が必要です。 テスト式が `false` の場合、反復は終了します。

`while...do` 式の使用例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

前のコードの出力は、1 から 20 までのランダムな数値のストリームで、最後は 10 になります。

```console
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> `while...do` は、シーケンス式やその他のコンピュテーション式で使用することができます。その場合は、`while...do` 式のカスタマイズされたバージョンを使用します。 詳細については、「[シーケンス](sequences.md)」、「[非同期ワークフロー](asynchronous-workflows.md)」、「[コンピュテーション式](computation-expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [ループ: `for...in` 式](loops-for-in-expression.md)
- [ループ: `for...to` 式](loops-for-to-expression.md)
