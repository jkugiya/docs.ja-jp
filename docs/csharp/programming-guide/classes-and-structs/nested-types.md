---
title: 入れ子にされた型 - C# プログラミング ガイド
description: クラス、構造体、またはインターフェイスの中で定義された型は、C# では入れ子にされた型と呼ばれます。
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 853138beed6ad9ddffa789f0080ca1fd2ba9d700
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511919"
---
# <a name="nested-types-c-programming-guide"></a>入れ子にされた型 (C# プログラミング ガイド)

[クラス](../../language-reference/keywords/class.md)、[構造体](../../language-reference/builtin-types/struct.md)、[インターフェイス](../../language-reference/keywords/interface.md)の中で定義された型は、入れ子にされた型と呼ばれます。 次に例を示します。

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

外側の型がクラス、構造体、入れ子にされた型のいずれであっても、入れ子にされた型は既定で [private](../../language-reference/keywords/private.md) になり、それが含まれる型からのみアクセスできます。 前の例では、`Nested` クラスは外部の型にアクセスできません。

次のように、[アクセス修飾子](../../language-reference/keywords/access-modifiers.md)を指定して、入れ子にされた型のアクセシビリティを定義することもできます。

- **クラス** の入れ子にされた型は、[public](../../language-reference/keywords/public.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md)、[private](../../language-reference/keywords/private.md)、[private protected](../../language-reference/keywords/private-protected.md) になります。

   ただし、[シール クラス](../../language-reference/keywords/sealed.md)内で `protected`、`protected internal`、`private protected` の入れ子にされたクラスを定義すると、コンパイラの警告 [CS0628](../../misc/cs0628.md)、"新規のプロテクト メンバーがシール クラスで宣言されました" が生成されます。

   また、入れ子になった型を外部から参照できるようにすることは、コード品質ルール [CA1034](../../../fundamentals/code-analysis/quality-rules/ca1034.md) の "入れ子にされた型を参照可能にすることはできません" に違反することにもご注意ください。

- **構造体** の入れ子にされた型は、は、[public](../../language-reference/keywords/public.md)、[internal](../../language-reference/keywords/internal.md)、または [private](../../language-reference/keywords/private.md) のいずれかが可能です。

次の例では、`Nested` クラスを public にします。

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

入れ子にされた型 (内側の型) は、包含する型 (外側の型) にアクセスできます。 包含する型にアクセスするには、その型を引数として入れ子にされた型のコンストラクターに渡します。 次に例を示します。

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

入れ子にされた型は、包含する型にアクセス可能なすべてのメンバーにアクセスできます。 入れ子にされた型は、継承されたプロテクト メンバーを含む、包含する型のプライベート メンバーとプロテクト メンバーにアクセスできます。

上記の宣言では、クラス `Nested` の完全名は `Container.Nested` です。 これは、次のように入れ子になったクラスの新しいインスタンスを作成するときに使用される名前です。

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [クラスと構造体](./index.md)
- [アクセス修飾子](./access-modifiers.md)
- [コンストラクター](./constructors.md)
- [CA1034 ルール](../../../fundamentals/code-analysis/quality-rules/ca1034.md)
