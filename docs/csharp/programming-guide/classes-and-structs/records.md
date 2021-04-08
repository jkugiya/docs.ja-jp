---
title: レコード - C# プログラミング ガイド
description: レコードの型と、その作成方法について説明します
ms.date: 02/26/2021
helpviewer_keywords:
- records [C#]
- C# language, records
ms.openlocfilehash: 99370e398d5e607def58334b33ae20aa59e21962
ms.sourcegitcommit: 872ca41d1c26f39d0aef57cc365d09503bac780d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2021
ms.locfileid: "106288031"
---
# <a name="records-c-programming-guide"></a>レコード (C# プログラミング ガイド)

[レコード](../../language-reference/builtin-types/record.md)とは、データ モデルを操作するための特殊な構文と動作を提供する[クラス](../../language-reference/keywords/class.md)です。 クラスについては、「[クラス (C# プログラミング ガイド)](classes.md)」を参照してください。

## <a name="when-to-use-records"></a>レコードを使用する場面

次のシナリオでは、クラスの代わりにレコードを使用することを検討してください。

* オブジェクトが不変となる参照型を定義する。
* [値の等価性](../statements-expressions-operators/equality-comparisons.md#value-equality)に依存するデータ モデルを定義する。

### <a name="immutability"></a>不変性

不変型とは、オブジェクトがインスタンス化された後にそのプロパティまたはフィールドの値を変更できないようにするためのものです。 不変性は、型をスレッドセーフにする必要がある場合またはハッシュ テーブル内で変化のないハッシュ コードに依存している場合に役立ちます。 レコードには、不変型を作成および操作するための簡潔な構文が用意されています。

不変性は、すべてのデータ シナリオに適しているわけではありません。 たとえば、[Entity Framework Core](/ef/core/) では、不変のエンティティ型を使用した更新がサポートされていません。

### <a name="value-equality"></a>値の等価性

レコードにおける値の等価性とは、型が一致し、かつプロパティおよびフィールドの値がすべて一致する場合にレコード型の 2 つの変数が等しいことを意味します。 クラスなどの他の参照型における等価性とは、[参照の等価性](../statements-expressions-operators/equality-comparisons.md#reference-equality)を意味します。 つまり、クラス型の 2 つの変数は、同じオブジェクトを参照する場合、等しいことになります。 2 つのレコード インスタンスが等しいかどうかを判断するメソッドと演算子では、値の等価性が使用されます。

すべてのデータ モデルが値の等価性に適しているわけではありません。 たとえば、[Entity Framework Core](/ef/core/) では、概念的に 1 つのエンティティであるものに対して、エンティティ型の 1 つのインスタンスだけが確実に使用されるようにするために、参照の等価性に依存します。 このため、レコード型は Entity Framework Core でエンティティ型として使用するのに適していません。

## <a name="how-records-differ-from-classes"></a>レコードとクラスの相違点

クラスを[宣言](classes.md#declaring-classes)および[インスタンス化](classes.md#creating-objects)するのと同じ構文がレコードでも使用できます。 キーワード `class` をキーワード `record` に置き換えるだけです。 同様に、継承関係を表す場合も同じ構文がレコードによってサポートされています。 レコードは次の点がクラスとは異なります。

* [位置指定パラメーター](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition)を使用して、不変プロパティを持つ型を作成してインスタンス化することができます。
* クラスで参照の等価性または非等価性を示すメソッドと演算子 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> や `==` など) は、レコードでは[値の等価性または非等価性](../../language-reference/builtin-types/record.md#value-equality)を示します。
* [`with` 式](../../language-reference/builtin-types/record.md#nondestructive-mutation)を使用すれば、選択したプロパティに新しい値を指定して、不変オブジェクトのコピーを作成することができます。
* レコードの `ToString` メソッドを使用すると、オブジェクトの型名とそのすべてのパブリック プロパティの名前および値を示す書式設定された文字列が作成されます。
* レコードは、[別のレコードから継承](../../language-reference/builtin-types/record.md#inheritance)できます。 レコードはクラスから継承できません。また、クラスはレコードから継承できません。

## <a name="examples"></a>例

次の例では、位置指定パラメーターを使用してレコードを宣言およびインスタンス化するパブリック レコードを定義します。 次に、型名とプロパティ値を出力します。

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

次の例では、レコードでの値の等価性を示します。

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

次の例では、`with` 式を使用して、不変オブジェクトをコピーし、プロパティの 1 つを変更する方法を示します。

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

詳細については、「[レコード (C# リファレンス)](../../language-reference/builtin-types/record.md)」を参照してください。
  
## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [クラス (C# プログラミング ガイド)](classes.md)
- [レコード (C# リファレンス)](../../language-reference/builtin-types/record.md)
- [C# プログラミング ガイド](../index.md)
- [オブジェクト指向プログラミング](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [ポリモーフィズム](polymorphism.md)
- [識別子名](../inside-a-program/identifier-names.md)
- [メンバー](members.md)
- [メソッド](methods.md)
- [コンストラクター](constructors.md)
- [ファイナライザー](destructors.md)
- [オブジェクト](objects.md)
