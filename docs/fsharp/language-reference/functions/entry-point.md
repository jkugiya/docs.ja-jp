---
title: エントリ ポイント
description: 実行可能ファイルとしてコンパイルされる F# プログラムにエントリ ポイント (実行が正式に開始される位置) を設定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630523"
---
# <a name="entry-point"></a>エントリ ポイント

このトピックでは、F# プログラムにエントリ ポイントを設定する方法について説明します。

## <a name="syntax"></a>構文

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>解説

上記の構文で、*let-function-binding* は、`let` バインドで記述した関数の定義です。

実行可能ファイルとしてコンパイルされるプログラムのエントリ ポイントは、実行が正式に開始される位置です。 F# アプリケーションにエントリ ポイントを指定するには、プログラムの `main` 関数に `EntryPoint` 属性を適用します。 (`let` バインドを使用して作成される) この関数は、最後にコンパイルされるファイルの最後の関数である必要があります。 最後にコンパイルされるファイルは、プロジェクト内の最後のファイル、またはコマンド ラインに渡す最後のファイルです。

エントリ ポイント関数の型は `string array -> int` です。 コマンド ラインに指定された引数は、文字列の配列に入れて `main` 関数に渡されます。 配列の最初の要素は、最初の引数です。実行可能ファイルの名前は、他の言語のものであるため、配列には含まれません。 戻り値は、プロセスの終了コードとして使用されます。 通常、ゼロは成功を示します。ゼロ以外の値はエラーを示します。 ゼロ以外のリターン コードの特定の意味について規則はありません。リターン コードの意味は、アプリケーションによって異なります。

単純な `main` 関数の例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

このコードをコマンド ライン `EntryPoint.exe 1 2 3` を使用して実行すると、出力は次のようになります。

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>暗黙的なエントリ ポイント

エントリ ポイントを明示的に示す **EntryPoint** 属性がプログラムにない場合は、最後にコンパイルされるファイル内の最上位レベルのバインドがエントリ ポイントとして使用されます。

## <a name="see-also"></a>関連項目

- [関数](index.md)
- [let 束縛](let-bindings.md)
