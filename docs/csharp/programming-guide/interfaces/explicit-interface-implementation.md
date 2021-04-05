---
title: 明示的なインターフェイスの実装 - C# プログラミング ガイド
description: C# では、クラスによって、シグネチャが同じメンバーを含むインターフェイスを実装できます。 明示的な実装では、1 つのインターフェイスに固有のクラス メンバーが作成されます。
ms.date: 03/24/2021
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.openlocfilehash: 2ca7e8a10c009b01b43e0c09d25d2dd99cbee2ec
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610864"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>明示的なインターフェイスの実装 (C# プログラミング ガイド)

シグネチャが同じメンバーが含まれる 2 つのインターフェイスをある[クラス](../../language-reference/keywords/class.md)が実装する場合、そのクラスでそのメンバーを実装することで、実装としてそのメンバーが両方のインターフェイスで使用されます。 次の例では、`Paint` のすべての呼び出しで同じメソッドが呼び出されます。 この最初のサンプルでは、型が定義されます。

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

次のサンプルでは、メソッドが呼び出されます。

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

ただし、両方のインターフェイスに対して同じ実装を呼び出さないようにすることもできます。 使用中のインターフェイスに応じて異なる実装を呼び出すには、インターフェイス メンバーを明示的に実装します。 明示的なインターフェイスの実装は、指定されたインターフェイスを介してのみ呼び出されるクラス メンバーです。 インターフェイスの名前とピリオドを使ってプレフィックスを付けて、クラス メンバーに名前を付けます。 次に例を示します。

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

クラス メンバー `IControl.Paint` は `IControl` インターフェイス経由でのみ利用できます。`ISurface.Paint` は `ISurface` 経由でのみ利用できます。 いずれのメソッド実装も個別であり、どちらもクラスで直接利用できません。 次に例を示します。

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

2 つのインターフェイスで、それぞれが同じ名前の別のメンバー (プロパティやメソッドなど) を宣言するような場合の解決には、明示的な実装も利用されます。 両方のインターフェイスを実装するには、コンパイラ エラーを回避するために、クラスはプロパティ `P`、メソッド `P`、または両方に明示的な実装を利用する必要があります。 次に例を示します。

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

明示的なインターフェイスの実装には、定義されている型のメンバーとしてアクセスできないため、アクセス修飾子がありません。 代わりに、インターフェイスのインスタンスを介して呼び出された場合にのみアクセスできます。 明示的なインターフェイスの実装にアクセス修飾子を指定すると、コンパイラ エラー [CS0106](../../language-reference/compiler-messages/cs0106.md) が発生します。 詳細については、「[`interface` (C# リファレンス)](../../language-reference/keywords/interface.md)」を参照してください。

[C# 8.0](../../whats-new/csharp-8.md#default-interface-methods) 以降では、インターフェイスで宣言されたメンバーの実装を定義できます。 クラスでインターフェイスからメソッド実装が継承される場合、そのメソッドにはインターフェイス型の参照を利用する方法でのみアクセスできます。 継承したメンバーは、パブリック インターフェイスの一部として表示されません。 次のサンプルでは、インターフェイス メソッドの既定の実装が定義されます。

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

次のサンプルでは、既定の実装が呼び出されます。

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

`IControl` インターフェイスを実装するあらゆるクラスによって、既定の `Paint` メソッドをパブリック メソッドか明示的なインターフェイス実装としてオーバーライドできます。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [クラスと構造体](../classes-and-structs/index.md)
- [インターフェイス](./index.md)
- [継承](../classes-and-structs/inheritance.md)
