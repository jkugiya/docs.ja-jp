---
title: with 式 - C# リファレンス
description: C# レコードの非破壊的な変更を実行する with 式について説明します
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 24b9fdfcef6fe042204217323bb09c047c58296c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872536"
---
# <a name="with-expression-c-reference"></a>with 式 (C# リファレンス)

C# 9.0 以降で使用可能な `with` 式は、指定されたプロパティと変更されたフィールドにより、[レコード](../builtin-types/record.md) オペランドのコピーを生成します。

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

前の例で示したように、変更するメンバーとその新しい値は、[オブジェクト初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)構文を使用して指定します。 `with` 式では、左側のオペランドがレコード型である必要があります。

次の例に示すように、`with` 式の結果は、式のオペランドと同じランタイム型になります。

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

参照型のメンバーの場合、レコードがコピーされるときにインスタンスへの参照のみがコピーされます。 コピーと元のレコードの両方が、同じ参照型のインスタンスにアクセスできます。 次の例は、その動作を示します。

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

すべてのレコード型には、"*コピー コンストラクター*" があります。 これは、含んでいるレコード型の 1 つのパラメーターを持つコンストラクターです。 その引数の状態が新しいレコード インスタンスにコピーされます。 `with` 式の評価では、コピー コンストラクターが呼び出され、元のレコードに基づいて新しいレコード インスタンスがインスタンス化されます。 その後、新しいインスタンスは、指定された変更に従って更新されます。 既定では、コピー コンストラクターは暗黙的、つまり、コンパイラによって生成されます。 レコード コピーのセマンティクスをカスタマイズする必要がある場合は、必要な動作が含まれるコピー コンストラクターを明示的に宣言します。 次の例では、明示的なコピー コンストラクターを使用して前の例が更新されます。 新しいコピー動作では、レコードがコピーされるときにリスト参照ではなくリスト項目がコピーされます。

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[レコード機能提案メモ](~/_csharplang/proposals/csharp-9.0/records.md)の次のセクションを参照してください。

- [`with` 式](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [コピー メンバーとクローン メンバー](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# の演算子と式](index.md)
- [レコード](../builtin-types/record.md)
