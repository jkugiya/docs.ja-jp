---
title: アサーション
description: F# プログラミング言語で式をテストするためのデバッグ機能として 'assert' 式を使用する方法について説明します。
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799059"
---
# <a name="assertions"></a>アサーション

`assert` 式は、式のテストに使用できるデバッグ機能です。 デバッグ モードでエラーが発生すると、アサーションによってシステム エラーのダイアログ ボックスが生成されます。

## <a name="syntax"></a>構文

```fsharp
assert condition
```

## <a name="remarks"></a>解説

`assert` 式の型は `bool -> unit` です。

`assert` 関数は <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> に解決されます。 これは、その動作が <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> を直接呼び出した場合と同じであることを意味します。

アサーション チェックは、デバッグ モードでコンパイルした場合にのみ有効になります。つまり、定数 `DEBUG` が定義されている場合です。 プロジェクト システムでは、既定で、デバッグ構成の場合に `DEBUG` 定数が定義されますが、リリース構成の場合には定義されません。

F# 例外処理を使用してアサーション エラーをキャッチすることはできません。

## <a name="example"></a>例

次のコードは、`assert` 式の使用例を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
