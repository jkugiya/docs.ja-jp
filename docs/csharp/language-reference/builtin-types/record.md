---
title: レコード - C# リファレンス
description: C# のレコード型について説明します
ms.date: 02/25/2021
f1_keywords:
- record_CSharpKeyword
helpviewer_keywords:
- record keyword [C#]
- record type [C#]
ms.openlocfilehash: 57474caf0f1106380e52da7fcb7608b62a0f23e5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872653"
---
# <a name="records-c-reference"></a>レコード (C# リファレンス)

C#9 以降では、`record` キーワードを使用して、データをカプセル化するための組み込み機能を提供する[参照型](reference-types.md)を定義します。 位置指定パラメーターまたは標準のプロパティ構文を使用して、不変のプロパティを持つレコード型を作成できます。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalRecord":::
:::code language="csharp" source="snippets/shared/RecordType.cs" id="ImmutableRecord":::

また、変更可能なプロパティとフィールドを使用してレコード型を作成することもできます。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="MutableRecord":::

レコードは変更可能ですが、これらは主に不変のデータ モデルをサポートすることを目的としています。 レコード型には次の機能があります。

* [不変プロパティを持つ参照型を作成するための簡潔な構文](#positional-syntax-for-property-definition)
* データ中心の参照型に役立つ組み込みの動作:
  * [値の等価性](#value-equality)
  * [非破壊的な変化の簡潔な構文](#nondestructive-mutation)
  * [表示用の組み込みの書式設定](#built-in-formatting-for-display)
* [継承階層のサポート](#inheritance)

[構造型](struct.md)を使用して、値の等価性があり、動作がほとんどない、またはまったくないデータ中心の型を設計することもできます。 ただし、比較的大規模なデータ モデルの場合、構造体型にはいくつかの欠点があります。

* 継承はサポートされていません。
* 値の等価性を決定する場合には効率的ではありません。 値型の場合、<xref:System.ValueType.Equals%2A?displayProperty=nameWithType> メソッドによってリフレクションが使用され、すべてのフィールドが検索されます。 レコードの場合、コンパイラによって `Equals` メソッドが生成されます。 実際のところ、レコードでの値の等価性の実装は、多少は高速です。
* すべてのインスタンスにすべてのデータの完全なコピーがあるため、一部のシナリオではより多くのメモリが使用されます。 レコード型は[参照型](reference-types.md)であるため、レコード インスタンスにはデータへの参照のみが含まれます。

## <a name="positional-syntax-for-property-definition"></a>プロパティ定義の位置指定構文

位置指定パラメーターを使用すると、レコードのプロパティを宣言し、インスタンスを作成するときにプロパティ値を初期化できます。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="InstantiatePositional":::

プロパティ定義に位置指定構文を使用すると、コンパイラにより、以下が作成されます。

* レコード宣言で指定される各位置指定パラメーターのパブリック init 専用自動実装プロパティ。 [init 専用](../../whats-new/csharp-9.md#init-only-setters)プロパティは、コンストラクターで、またはプロパティ初期化子を使用して設定できます。
* パラメーターがレコード宣言の位置指定パラメーターと一致するプライマリ コンストラクター。
* レコード宣言で指定された各定位置指定パラメーターの `out` パラメーターを使用する `Deconstruct` メソッド。 このメソッドは、2 つ以上の位置指定パラメーターがある場合にのみ指定されます。 このメソッドにより、位置指定構文を使用して定義されたプロパティは分解されます。標準のプロパティ構文を使用して定義されたプロパティは無視されます。

生成された自動実装プロパティ定義が目的の内容ではない場合は、同じ名前の独自のプロパティを定義できます。 これを行うと、そのプロパティ定義が生成されたコンストラクターとデコンストラクターに使用されます。 たとえば、次の例では、`public` ではなく `FirstName` 位置指定プロパティ `internal` が作成されます。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalWithManualProperty":::

レコード型の場合、位置指定プロパティを宣言する必要はありません。 次の例のように、位置指定プロパティを使用せずにレコードを宣言することや、追加のフィールドとプロパティを宣言することができます。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="MixedSyntax":::

標準のプロパティ構文を使用してプロパティを定義し、アクセス修飾子を省略した場合、プロパティは暗黙的に `public` になります。
<!-- Todo -- Explain issues surrounding use of attributes on positional properties. -->

## <a name="immutability"></a>不変性

レコード型は必ずしも不変ではありません。 `readonly` ではない `set` アクセサーとフィールドを使用してプロパティを宣言できます。 ただし、レコードは変更可能ですが、不変のデータ モデルを簡単に作成できます。

不変性は、データ中心の型をスレッドセーフにする必要がある場合またはハッシュ テーブル内で変化のないハッシュ コードに依存している場合に役立ちます。 ただし、不変性は、すべてのデータ シナリオに適しているわけではありません。 たとえば、[Entity Framework Core](/ef/core/) では、不変のエンティティ型を使用した更新がサポートされていません。

位置指定パラメーターから作成されたか、`init` アクセサーを指定して作成されたかにかかわらず、init 専用プロパティには "*浅い不変性*" があります。 初期化後に、値型プロパティの値または参照型プロパティの参照を変更することはできません。 ただし、参照型プロパティから参照されるデータは変更できます。 次の例は、参照型の不変プロパティ (この場合は配列) の内容が変更可能であることを示しています。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ShallowImmutability":::

レコード型に固有の機能は、コンパイラによって合成されたメソッドによって実装されます。このようなメソッドのいずれを使用してオブジェクトの状態を変更しても、不変性は損なわれません。

## <a name="value-equality"></a>値の等価性

値の等価性とは、型が一致し、かつプロパティおよびフィールドの値がすべて一致する場合にレコード型の 2 つの変数が等しいことを意味します。 その他の参照型の場合、等価性は ID を意味します。 つまり、参照型の 2 つの変数は、同じオブジェクトを参照する場合、等しいことになります。

一部のデータ モデルでは、参照の等価性が必要です。 たとえば、[Entity Framework Core](/ef/core/) では、概念的に 1 つのエンティティであるものに対して、エンティティ型の 1 つのインスタンスだけが確実に使用されるようにするために、参照の等価性に依存します。 このため、レコード型は Entity Framework Core でエンティティ型として使用するのに適していません。

次の例は、レコード型の値が等しいことを示しています。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="Equality":::

値の等価性を実装するために、コンパイラにより、次のメソッドが合成されます。

* <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> のオーバーライド。

  このメソッドは、両方のパラメーターが null でない場合に、<xref:System.Object.Equals(System.Object,System.Object)?displayProperty=nameWithType> 静的メソッドの基礎として使用されます。

* パラメーターがレコード型である仮想 `Equals` メソッド。 このメソッドは、<xref:System.IEquatable%601> を実装します。

* <xref:System.Object.GetHashCode?displayProperty=nameWithType> のオーバーライド。

* 演算子 `==` および `!=` のオーバーライド。

`class` 型では、等価性メソッドと演算子を手動でオーバーライドして値の等価性を実現できますが、そのコードの開発とテストには時間がかかり、エラーが発生しやすいものです。 この機能を組み込むと、プロパティまたはフィールドが追加または変更されたときにカスタムのオーバーライド コードの更新を忘れたことで発生するバグを防ぐことができます。

このような合成されたメソッドのいずれかを置き換えるために、独自の実装を作成できます。 レコード型に、いずれかの合成メソッドのシグネチャと一致するメソッドがある場合、コンパイラでそのメソッドは合成されません。

レコード型で `Equals` の独自の実装を用意する場合は、`GetHashCode` の実装も用意してください。

## <a name="nondestructive-mutation"></a>非破壊な変化

レコード インスタンスの不変プロパティを変更する必要がある場合は、`with` 式を使用して "*非破壊的な変化*" を実現できます。 `with` 式を使用すると、指定したプロパティとフィールドが変更された、既存のレコード インスタンスのコピーである新しいレコード インスタンスが作成されます。 次の例に示すように、[オブジェクト初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)構文を使用して、変更する値を指定します。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="WithExpressions":::

`with` 式により、位置指定プロパティ、または標準のプロパティ構文を使用して作成されたプロパティを設定できます。 位置指定ではないプロパティの場合、`with` 式で変更される `init` または `set` アクセサーが必要です。

`with` 式の結果は "*浅いコピー*" です。つまり、参照プロパティの場合、インスタンスへの参照のみがコピーされます。 元のレコードとコピーの両方が、同じインスタンスへの参照になります。

この機能を実装するために、コンパイラにより、クローン メソッドとコピー コンストラクターが合成されます。 コンストラクターにより、コピーされるレコードのインスタンスが取得され、クローン メソッドが呼び出されます。 `with` 式を使用すると、コピー コンストラクターを呼び出すコードがコンパイラによって作成され、`with` 式で指定されたプロパティが設定されます。

別のコピー動作が必要な場合は、独自のコピー コンストラクターを作成できます。 こうすると、コンパイラによって合成されません。 レコードが `sealed` の場合はコンストラクターが `private` になり、それ以外の場合は `protected` になります。

クローン メソッドをオーバーライドすることや、`Clone` という名前のメンバーを作成することはできません。 クローン メソッドの実際の名前はコンパイラによって生成されます。

## <a name="built-in-formatting-for-display"></a>表示用の組み込みの書式設定

レコード型には、パブリック プロパティとフィールドの名前と値を表示する、コンパイラによって生成された <xref:System.Object.ToString%2A> メソッドがあります。 `ToString` メソッドからは、次の形式の文字列が返されます。

> \<record type name> { \<property name> = \<value>, \<property name> = \<value>, ...}

参照型の場合、プロパティ値ではなく、プロパティから参照されるオブジェクトの型名が表示されます。 次の例では、配列は参照型であるため、実際の配列要素値ではなく `System.String[]` が表示されます。

```
Person { FirstName = Nancy, LastName = Davolio, ChildNames = System.String[] }
```

この機能を実装するために、コンパイラにより、仮想 `PrintMembers` メソッドと <xref:System.Object.ToString%2A> のオーバーライドが合成されます。
`ToString` のオーバーライドにより、型名の後に左角かっこが続く <xref:System.Text.StringBuilder> オブジェクトが作成されます。 プロパティの名前と値を追加する `PrintMembers` が呼び出され、右角かっこが追加されます。 次の例は、合成されたオーバーライドに含まれているものと似たコードを示しています。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ToStringOverrideDefault":::

`PrintMembers` または `ToString` のオーバーライドに独自の実装を用意できます。 たとえば、この記事で後述する「[派生レコードに含まれる `PrintMembers` の書式設定](#printmembers-formatting-in-derived-records)」です。

## <a name="inheritance"></a>継承

レコードは、別のレコードから継承できます。 ただし、レコードはクラスから継承できません。また、クラスはレコードから継承できません。

### <a name="positional-parameters-in-derived-record-types"></a>派生レコード型の位置指定パラメーター

派生レコードにより、基本レコードのプライマリ コンストラクターに含まれるすべてのパラメーターに対する位置指定パラメーターが宣言されます。 基本レコードにより、それらのプロパティが宣言されて初期化されます。 派生レコードによってそれらは隠ぺいされませんが、基本レコードで宣言されていないパラメーターのプロパティのみが作成されて初期化されます。

次の例は、位置指定プロパティ構文を使用した継承を示しています。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalInheritance":::

### <a name="equality-in-inheritance-hierarchies"></a>継承階層の等価性

2 つのレコード変数が等しくなるには、ランタイム型が等しくなければなりません。 含まれている変数型は異なっていていても構いません。 これを次のコード例に示します。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="InheritanceEquality":::

この例では、すべてのインスタンスが同じプロパティであり、同じプロパティ値です。 ただし、両方とも `Person` 型の変数であっても、`student == teacher` から `False` が返されます。また、いずれかが `Person` 変数でもう一方が `Student` 変数であっても `student == student2` から `True` が返されます。

この動作を実装するために、コンパイラにより、レコード型と一致する <xref:System.Type> オブジェクトを返す `EqualityContract` プロパティが合成されます。 これで、等価性メソッドを使用して、等価性の確認時にオブジェクトのランタイム型を比較できるようになります。 レコードの基本データ型が `object` の場合、このプロパティは `virtual` です。 基本データ型が別のレコード型である場合、プロパティはオーバーライドになります。 レコード型が `sealed` の場合、プロパティは `sealed` です。

派生型の 2 つのインスタンスを比較する場合、合成された等価性メソッドにより、基本型と派生型のすべてのプロパティの等価性が確認されます。 合成された `GetHashCode` メソッドには、基本データ型と派生レコード型で宣言されたすべてのプロパティとフィールドからの `GetHashCode` メソッドが使用されます。

### <a name="with-expressions-in-derived-records"></a>派生レコードの `with` 式

合成されたクローン メソッドには[共変の戻り値の型](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)が使用されるため、`with` 式の結果は式のオペランドと同じランタイム型になります。 ランタイム型のすべてのプロパティがコピーされますが、次の例に示すように、コンパイル時型のプロパティのみを設定できます。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="WithExpressionInheritance":::

### <a name="printmembers-formatting-in-derived-records"></a>派生レコードに含まれる `PrintMembers` の書式設定

派生レコード型の合成された `PrintMembers` メソッドから、基本実装が呼び出されます。 その結果、次の例に示すように、派生型と基本型の両方のすべてのパブリック プロパティとフィールドが `ToString` の出力に含まれます。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ToStringInheritance":::

`PrintMembers` メソッドの独自の実装を用意できます。 その場合は、次のシグネチャを使用します。

* `object` から派生した (基本レコードを宣言しない) `sealed` レコードの場合: `private bool PrintMembers(StringBuilder builder)`;
* 別のレコードから派生した `sealed` レコードの場合: `protected sealed override bool PrintMembers(StringBuilder builder)`;
* `sealed` ではなく、オブジェクトから派生したレコードの場合: `protected virtual bool PrintMembers(StringBuilder builder);`
* `sealed` ではなく、別のレコードから派生したレコードの場合: `protected override bool PrintMembers(StringBuilder builder);`

合成された `PrintMembers` メソッドを置き換えるコードの例を次に示します。1 つはオブジェクトから派生するレコード型であり、もう 1 つは別のレコードから派生するレコード型です。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PrintMembersImplementation":::

### <a name="deconstructor-behavior-in-derived-records"></a>派生レコードのデコンストラクターの動作

派生レコードの `Deconstruct` メソッドからは、コンパイル時型のすべての位置指定プロパティの値が返されます。 変数の型が基本レコードの場合、オブジェクトが派生型にキャストされない限り、基本レコードのプロパティのみが分解されます。 派生レコードに対してデコンストラクターを呼び出す方法の例を次に示します。

:::code language="csharp" source="snippets/shared/RecordType.cs" id="DeconstructorInheritance":::

## <a name="generic-constraints"></a>ジェネリック制約

型をレコードにする必要があるジェネリック制約はありません。 レコードは `class` 制約を満たしています。 レコード型の特定の階層に制約を設定するには、基底クラスと同じように基本レコードに制約を設定します。 詳細については、「[型パラメーターの制約](../../programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[クラス](~/_csharplang/spec/classes.md)」セクションを参照してください。

C# 9 以降で導入された機能の詳細については、次の機能の提案に関するメモを参照してください。

- [レコード](~/_csharplang/proposals/csharp-9.0/records.md)
- [init 専用セッター](~/_csharplang/proposals/csharp-9.0/init.md)
- [covariant の戻り値](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [デザインのガイドライン - クラスまたは構造体の選択](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [デザインのガイドライン - 構造体のデザイン](../../../standard/design-guidelines/struct.md)
- [クラスと構造体](../../programming-guide/classes-and-structs/index.md)
- [`with` 式](../operators/with-expression.md)
