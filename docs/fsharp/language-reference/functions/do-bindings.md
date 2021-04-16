---
title: do 束縛
description: F# 'do' バインドを使用して、関数または値を定義せずにコードを実行する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630530"
---
# <a name="do-bindings"></a>do 束縛

`do` バインドは、関数または値を定義せずにコードを実行するのに使用されます。 また、do バインドはクラスで使用することもできます。「[クラスの `do` バインド](../members/do-bindings-in-classes.md)」を参照してください。

## <a name="syntax"></a>構文

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>解説

関数または値の定義とは別にコードを実行する場合は、`do` バインドを使用します。 `do` バインド内の式は `unit` を返す必要があります。 最上位レベルの `do` バインド内のコードは、モジュールが初期化されたときに実行されます。 キーワード `do` は省略可能です。

最上位レベルの `do` バインドに属性を適用できます。 たとえば、プログラムで COM 相互運用が使用している場合は、プログラムに `STAThread` 属性を適用できます。 これを行うには、次のコードに示すように、`do` バインドの属性を使用します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](../index.md)
- [関数](index.md)
