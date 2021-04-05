---
description: partial メソッド - C# リファレンス
title: partial メソッド - C# リファレンス
ms.date: 03/23/2021
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 240ad6f2f5792e4db9b032e36991f3c398f1d2f9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111011"
---
# <a name="partial-method-c-reference"></a>partial メソッド (C# リファレンス)

部分メソッドには、部分型の一部に定義されたシグネチャ、および部分型の別の部分に定義された実装があります。 部分メソッドを使用すると、イベント ハンドラーと同じように、開発者が実装するかどうかを決定できるメソッド フックをクラス デザイナーで提供できます。 開発者が実装を指定しない場合、コンパイラはコンパイル時にシグネチャを削除します。 部分メソッドには次の条件が適用されます。

- 宣言は、コンテキスト キーワード [partial](../../language-reference/keywords/partial-type.md) で始まる必要があります。

- 部分型の両方の部分のシグネチャが一致する必要がある。

次の場合には、部分メソッドを実装する必要はありません。

- アクセシビリティ修飾子 (既定の [private](../../language-reference/keywords/private.md) を含む) はありません。

- [void](../../language-reference/builtin-types/void.md) を返します。

- [out](../../language-reference/keywords/out-parameter-modifier.md) パラメーターはありません。

- [virtual](../../language-reference/keywords/virtual.md)、[override](../../language-reference/keywords/override.md)、[sealed](../../language-reference/keywords/sealed.md)、[new](../../language-reference/keywords/new-modifier.md)、[extern](../../language-reference/keywords/extern.md) のいずれの修飾子もありません。

これらのすべての制限に準拠していないメソッド (`public virtual partial void` メソッドなど) は、実装を提供する必要があります。

部分クラスの 2 つの部分に定義された部分メソッドを次の例に示します。

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

部分メソッドは、ソース ジェネレーターと組み合わせて使用することもできます。 たとえば、regex は、次のパターンを使用して定義できます。

```csharp
[RegexGenerated("(dog|cat|fish)")]
partial bool IsPetMatch(string input);
```

詳細については、「[部分クラスと部分メソッド](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [partial 型](partial-type.md)
