---
title: クラス内の let 束縛
description: クラス定義で 'let' バインドを使用して、F# クラスのプライベート フィールドとプライベート関数を定義する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216533"
---
# <a name="let-bindings-in-classes"></a>クラス内の let 束縛

クラス定義で `let` バインドを使用して、F# クラスのプライベート フィールドとプライベート関数を定義することができます。

## <a name="syntax"></a>構文

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>解説

前の構文は、クラスの見出しと継承宣言の後、メンバー定義の前に使用します。 構文は、クラスの外部の `let` バインドの場合と似ていますが、クラスで定義されている名前には、クラスに限定されたスコープがあります。 `let` バインドでは、プライベート フィールドまたは関数が作成されます。データまたは関数を公開するには、プロパティまたはメンバー メソッドを宣言します。

静的でない `let` バインドは、インスタンス `let` バインドと呼ばれます。 インスタンス `let` バインドは、オブジェクトの作成時に実行されます。 静的 `let` バインドはクラスの静的初期化子の一部であり、型が最初に使用される前に確実に実行されます。

インスタンス `let` バインド内のコードでは、プライマリ コンストラクターのパラメーターを使用できます。

属性とアクセシビリティ修飾子は、クラス内の `let` バインドでは使用できません。

次のコード例は、クラス内での何種類かの `let` バインドを示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

出力は次のとおりです。

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>フィールドを作成する別の方法

また、`val` キーワードを使用してプライベート フィールドを作成することもできます。 `val` キーワードを使用する場合、オブジェクトの作成時にフィールドに値は与えられませんが、代わりに既定値を使用して初期化されます。 詳細については、「[明示的なフィールド: val キーワード](explicit-fields-the-val-keyword.md)」を参照してください。

メンバー定義を使用し、キーワード `private` を定義に追加することで、クラスのプライベート フィールドを定義することもできます。 これは、コードを書き直さずにメンバーのアクセシビリティを変更する必要がある場合に便利です。 詳しくは、「[アクセス制御](../access-control.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- [[メンバー]](index.md)
- [クラス内の `do` バインド](do-bindings-in-classes.md)
- [`let` バインド](../functions/let-bindings.md)
