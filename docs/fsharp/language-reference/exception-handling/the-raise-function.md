---
title: '例外: raise 関数'
description: F# 'raise' 関数を使用して、エラーまたは例外条件が発生したことを示す方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630290"
---
# <a name="exceptions-the-raise-function"></a>例外: raise 関数

`raise` 関数は、エラーまたは例外条件が発生したことを示すために使用されます。 エラーに関する情報は、例外オブジェクトでキャプチャされます。

## <a name="syntax"></a>構文

```fsharp
raise (expression)
```

## <a name="remarks"></a>解説

`raise` 関数は、例外オブジェクトを生成し、スタックのアンワインド プロセスを開始します。 スタックのアンワインド プロセスは共通言語ランタイム (CLR) によって管理されているため、このプロセスの動作は他のすべての .NET 言語と同じになります。 スタックのアンワインド プロセスでは、生成された例外に一致する例外ハンドラーを検索します。 検索は、現在の `try...with` 式 (存在する場合) で開始されます。 `with` ブロック内の各パターンが順番に確認されます。 一致する例外ハンドラーが見つかった場合、例外は処理済みと見なされます。それ以外の場合、スタックはアンワインドされ、一致するハンドラーが見つかるまで呼び出しチェーンの上部にある `with` ブロックが確認されます。 呼び出しチェーンで見つかった `finally` ブロックも、スタックのアンワインドと同様に順番に実行されます。

`raise` 関数は、C# または C++ の `throw` に相当します。 catch ハンドラーで `reraise` を使用して、同じ例外を呼び出しチェーンの上部に伝達します。

次のコード例は、`raise` 関数を使用して例外を生成する方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` 関数は、次の例に示すように、.NET の例外を発生させるためにも使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...with` 式](the-try-with-expression.md)
- [例外: `try...finally` 式](the-try-finally-expression.md)
- [例外: `failwith` 関数](the-failwith-function.md)
- [例外: `invalidArg` 関数](the-invalidArg-function.md)
