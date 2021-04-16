---
title: '例外: try...finally 式'
description: F# の 'try...finally' 式を使用して、コードのブロックで例外がスローされた場合でもクリーンアップ コードを実行できるようにする方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083004"
---
# <a name="exceptions-the-tryfinally-expression"></a>例外: try...finally 式

`try...finally` 式を使用すると、コードのブロックで例外がスローされた場合でもクリーンアップ コードを実行できます。

## <a name="syntax"></a>構文

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>解説

`try...finally` 式を使用すると、上記の構文で *expression1* の実行中に例外が生成されたかどうかに関係なく、*expression2* のコードを実行することができます。

*expression2* の型は、式全体の値には影響しません。例外が発生しなかったときに返される型は、*expression1* の最後の値です。 例外が発生した場合、値は返されず、制御のフローは、コール スタックの上位にある次の一致する例外ハンドラーに移ります。 例外ハンドラーが見つからない場合、プログラムは終了します。 一致するハンドラー内のコードが実行される前、またはプログラムが終了する前に、`finally` 分岐内のコードが実行されます。

`try...finally` 式を使用したコードの例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

コンソールへの出力は次のとおりです。

```console
Closing stream
Exception handled.
```

出力からわかるように、外側の例外が処理される前にストリームが閉じられています。また、ファイル `test.txt` にテキスト `test1` が含まれているということは、例外によって制御が外側の例外ハンドラーに移ったにもかかわらず、バッファーがフラッシュされてディスクに書き込まれたことを示しています。

`try...with` コンストラクトは、`try...finally` コンストラクトとは別のコンストラクトであることにご注意ください。 したがって、コードに `with` ブロックと `finally` ブロックの両方が必要な場合は、次のコード例に示すように、2 つのコンストラクトを入れ子にする必要があります。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

コンピュテーション式のコンテキスト (シーケンス式と非同期ワークフローを含む) では、**try...finally** 式にカスタム実装を含めることができます。 詳細については、「[コンピュテーション式](../computation-expressions.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外: `try...with` 式](the-try-with-expression.md)
