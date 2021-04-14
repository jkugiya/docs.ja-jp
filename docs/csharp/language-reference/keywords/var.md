---
description: var - C# リファレンス
title: var - C# リファレンス
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: b3590ebbcff0894b7864cd4a227a6ea068de42a2
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075512"
---
# <a name="var-c-reference"></a>var (C# リファレンス)

C# 3 以降、メソッド スコープで宣言された変数には暗黙的な "型" `var` を与えることができます。 暗黙的に型指定されたローカル変数では、型を自分で宣言した場合と同様に厳密に型指定されますが、コンパイラが型を決定します。 次の 2 つの `i` の宣言は機能的に等しくなります。

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> `var` を [null 許容参照型](../builtin-types/nullable-reference-types.md)を有効にして使用すると、式の型で null 値が許容されない場合でも、常に null 値を許容する参照型を表します。

`var` キーワードは、コンストラクターの呼び出し式と共に使用するのが一般的です。 `var` を使用すると、次の例に示すように、変数宣言およびオブジェクトのインスタンス化において型名を繰り返す必要がなくなります。

```csharp
var xs = new List<int>();
```

C# 9.0 以降では、代替としてターゲット型の [`new` 式](../operators/new-operator.md)を使用できます。

```csharp
List<int> xs = new();
List<int>? ys = new();
```

パターン マッチングでは、`var` キーワードが [`var` パターン](../operators/patterns.md#var-pattern)で使用されます。

## <a name="example"></a>例

次の例は、2 つのクエリ式を示しています。 最初の式では、`var` の使用が許可されますが、必須ではありません。クエリ結果の型を `IEnumerable<string>` として明示的に指定できるためです。 一方、2 つ目の式の `var` では、匿名型のコレクションとしての結果が許され、その型の名前にはコンパイラ自体以外はアクセスできません。 `var` を使うと、結果のために新しいクラスを作成する必要がなくなります。 例 #2 では、`foreach` 繰り返し変数 `item` も暗黙的に型指定する必要があります。

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [暗黙的に型指定されるローカル変数](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [LINQ クエリ操作での型の関係](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
