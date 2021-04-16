---
title: '例外: failwith 関数'
description: "'failwith' 関数で F# 例外が生成される方法について説明します。"
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630324"
---
# <a name="exceptions-the-failwith-function"></a>例外: failwith 関数

`failwith` 関数で F# 例外が生成されます。

## <a name="syntax"></a>構文

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>解説

前の構文の *error-message-string* は、リテラル文字列または型 `string` の値です。 これは、例外の `Message` プロパティになります。

`failwith` によって生成される例外は `System.Exception` 例外です。これは、F# コードで名前が `Failure` の参照です。 次のコードは、例外をスローするための `failwith` の使用例を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...with` 式](the-try-with-expression.md)
- [例外: `try...finally` 式](the-try-finally-expression.md)
- [例外: `raise` 関数](the-raise-function.md)
