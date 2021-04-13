---
title: パターン - C# リファレンス
description: C# のパターン マッチング式およびステートメントでサポートされるパターンについての説明 - C# リファレンス
ms.date: 04/05/2021
f1_keywords:
- and_CSharpKeyword
- or_CSharpKeyword
- not_CSharpKeyword
helpviewer_keywords:
- pattern matching [C#]
- and keyword [C#]
- or keyword [C#]
- not keyword [C#]
ms.openlocfilehash: cac2208d41bca2c6befecffbe4bb0b8ca43042bc
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498577"
---
# <a name="patterns-c-reference"></a>パターン (C# リファレンス)

C# では、C# 7.0 でパターン マッチングが導入されました。 その後、C# の各メジャー バージョンで、パターン マッチング機能が拡張されています。 次の C# 式およびステートメントでは、パターン マッチングがサポートされています。

- [`is` 式](../keywords/is.md)
- `switch` [ステートメント](../keywords/switch.md)
- `switch` [式](switch-expression.md) (C# 8.0 で導入)

それらの構造体では、入力式を次の任意のパターンと一致させることができます。

- [宣言パターン](#declaration-and-type-patterns): 式のランタイム型をチェックし、一致が成功した場合は、宣言された変数に式の結果を代入します。 C# 7.0 で導入されました。
- [型パターン](#declaration-and-type-patterns): 式のランタイム型をチェックします。 C# 9.0 で導入されました。
- [定数パターン](#constant-pattern): 式の結果が指定された定数と等しいかどうかをテストします。 C# 7.0 で導入されました。
- [リレーショナル パターン](#relational-patterns): 式の結果と指定された定数を比較します。 C# 9.0 で導入されました。
- [論理パターン](#logical-patterns): 式がパターンの論理的な組み合わせと一致するかどうかをテストします。 C# 9.0 で導入されました。
- [プロパティ パターン](#property-pattern): 式のプロパティまたはフィールドが入れ子になったパターンに一致するかどうかをテストします。 C# 8.0 で導入されました。
- [位置指定パターン](#positional-pattern): 式の結果を分解し、結果の値が入れ子になったパターンに一致するかどうかをテストします。 C# 8.0 で導入されました。
- [`var` パターン](#var-pattern): 任意の式に一致させ、その結果を宣言された変数に代入します。 C# 7.0 で導入されました。
- [破棄パターン](#discard-pattern): 任意の式に一致させます。 C# 8.0 で導入されました。

[論理](#logical-patterns)、[プロパティ](#property-pattern)、および [位置指定](#positional-pattern)パターンは *再帰的* パターンです。 つまり、それらには *入れ子になった* パターンを含めることができます。

これらのパターンを使用してデータ ドリブン アルゴリズムを構築する方法の例については、「[チュートリアル: パターン マッチングを使用して、型ドリブンおよびデータ ドリブンのアルゴリズムを構築する](../../tutorials/pattern-matching.md)」を参照してください。

## <a name="declaration-and-type-patterns"></a>宣言パターンと型パターン

宣言パターンと型パターンを使用して、式のランタイム型が指定された型と互換性があるかどうかをチェックします。 宣言パターンでは、新しいローカル変数を宣言することもできます。 宣言パターンが式に一致すると、次の例に示すように、その変数に変換された式の結果が代入されます。

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="BasicExample":::

C# 7.0 以降、式の結果が null 以外で、次のいずれかの条件が満たされている場合に、`T` 型の *宣言パターン* が式に一致します。

- 式の結果のランタイム型は `T` です。

- 式の結果のランタイム型は、`T` 型から派生するか、インターフェイス `T` を実装するか、または、それから `T` への[暗黙的な参照変換](~/_csharplang/spec/conversions.md#implicit-reference-conversions)が存在します。 次の例は、この条件が満たされている場合の 2 つのケースを示しています。

  :::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="ReferenceConversion":::

  前の例では、`GetSourceLabel` メソッドへの最初の呼び出しで、引数 のランタイム型 `int[]` が <xref:System.Array> 型から派生しているため、最初のパターンが引数値と一致し ます。 `GetSourceLabel` メソッドへの 2 つ目の呼び出しでは、引数のランタイム型 <xref:System.Collections.Generic.List%601> は、<xref:System.Array> 型から派生していませんが、<xref:System.Collections.Generic.ICollection%601> インターフェイスを実装しています。

- 式の結果のランタイム型は、基になる型 `T` を持つ [Null 許容値型](../builtin-types/nullable-value-types.md)です。

- 式の結果のランタイム型から `T` 型までに、[ボックス化](../../programming-guide/types/boxing-and-unboxing.md#boxing)変換または[ボックス化解除](../../programming-guide/types/boxing-and-unboxing.md#unboxing)変換が存在します。

次の例は、最後の 2 つの条件を示しています。

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="NullableAndUnboxing":::

式の型のみをチェックする場合は、次の例に示すように、変数名の代わりに破棄 `_` を使用できます。

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="DiscardVariable":::

C# 9.0 以降、その目的のために、次の例に示すように *型パターン* を使用できます。

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="TypePattern":::

宣言パターンと同様に、式の結果が null 以外で、そのランタイム型が上記のいずれかの条件を満たす場合に、型パターンは式に一致します。

詳細については、機能提案ノートの「[宣言パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern)」と「[型パターン](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns)」セクションを参照してください。

## <a name="constant-pattern"></a>定数パターン

C# 7.0 以降、次の例に示すように、*定数パターン* を使用して、式の結果が指定された定数と等しいかどうかをテストします。

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="BasicExample":::

定数パターンでは、次のような任意の定数式を使用できます。

- [整数](../builtin-types/integral-numeric-types.md)または[浮動小数点](../builtin-types/floating-point-numeric-types.md)数値リテラル
- [char](../builtin-types/char.md) または[文字列](../builtin-types/reference-types.md#the-string-type)リテラル
- ブール値 `true` または `false`
- [列挙型](../builtin-types/enum.md)値
- 宣言された[定数](../keywords/const.md)フィールドまたはローカルの名前
- `null`

次の例に示すように、定数パターンを使用して `null` をチェックします。

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NullCheck":::

コンパイラにより、式 `x is null` が評価されるときに、ユーザーがオーバーロードした等値演算子 `==` が呼び出されないことが保証されます。

C# 9.0 以降、次の例に示すように、[否定された](#logical-patterns) `null` 定数パターンを使用して null 以外であるかをチェックできます。

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NonNullCheck":::

詳細については、機能提案ノートの「[定数パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern)」セクションを参照してください。

## <a name="relational-patterns"></a>リレーショナル パターン

C# 9.0 以降、次の例に示すように、*リレーショナル パターン* を使用して、式の結果を定数と比較します。

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="BasicExample":::

リレーショナル パターンでは、[関係演算子](comparison-operators.md) `<`、`>`、`<=`、または `>=` のいずれかを使用できます。 リレーショナル パターンの右側の部分は、定数式である必要があります。 定数式には、[整数](../builtin-types/integral-numeric-types.md)、[浮動小数点](../builtin-types/floating-point-numeric-types.md)、[char](../builtin-types/char.md)、または[列挙](../builtin-types/enum.md)型を指定できます。

式の結果が特定の範囲内にあるかどうかをチェックするには、次の例に示すように、[接続的`and`パターン](#logical-patterns)に対して、それを一致させます。

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="WithCombinators":::

式の結果が `null` であるか、null 許容変換またはボックス化解除変換によって定数の型に変換できない場合、リレーショナル パターンは式に一致しません。

詳細については、機能提案ノートの「[リレーショナル パターン](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns)」セクションを参照してください。

## <a name="logical-patterns"></a>論理パターン

C# 9.0 以降、`not`、`and`、および `or` パターン連結子を使用して、次の *論理パターン* を作成します。

- 否定されたパターンが式に一致しない場合に、式に一致する *否定*`not`パターン。 次の例に、[定数](#constant-pattern) `null` パターンを否定して、式が null でないかどうかを確認する方法を示します。

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="NotPattern":::

- 両方のパターンが式に一致する場合に、式に一致する *接続的*`and` パターン。 次の例に、[リレーショナル パターン](#relational-patterns)を組み合わせて、値が特定の範囲内にあるかどうかをチェックする方法を示します。

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="AndPattern":::

- 次の例に示すように、いずれかのパターンが式に一致する場合に、式に一致する *離接的* `or` パターン。

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="OrPattern":::

前の例に示すように、パターンでパターンの連結子を繰り返し使用できます。

`and` パターン連結子は、`or` よりも優先順位が高くなります。 次の例に示すように、優先順位を明示的に指定するには、かっこを使用します。

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="WithParentheses":::

> [!NOTE]
> パターンがチェックされる順序は定義されていません。 実行時に、`or` および `and` パターンの右側の入れ子になったパターンを最初にチェックできます。

詳細については、機能提案ノートの「[パターン連結子](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators)」セクションを参照してください。

## <a name="property-pattern"></a>プロパティ パターン

C# 8.0 以降、次の例に示すように、*プロパティ パターン* を使用して、入れ子になったパターンに対して、式のプロパティまたはフィールドを一致させます。

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="BasicExample":::

式の結果が null 以外で、すべての入れ子になったパターンが、式の結果の対応するプロパティまたはフィールドと一致する場合、プロパティ パターンは式に一致します。

次の例に示すように、ランタイム型チェックと変数宣言をプロパティ パターンに追加することもできます。

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="WithTypeCheck":::

プロパティ パターンは、再帰的パターンです。 つまり、入れ子になったパターンとして任意のパターンを使用できます。 次の例に示すように、入れ子になったパターンに対して、データの一部を一致させるには、プロパティ パターンを使用します。

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="RecursivePropertyPattern":::

前の例では、C# 9.0 以降で使用できる 2 つの機能 (`or`[パターン連結子](#logical-patterns)と[レコード型](../builtin-types/record.md)) を使用しています。

詳細については、機能提案ノートの「[プロパティ パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern)」セクションを参照してください。

## <a name="positional-pattern"></a>位置指定パターン

C# 8.0 以降、次の例に示すように、*位置指定パターン* を使用して、式の結果を分解し、結果の値を、対応する入れ子になったパターンに対して一致させます。

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="BasicExample":::

前の例では、式の型に [Deconstruct](../../deconstruct.md) メソッドが含まれており、これは、式の結果を分解するために使用されます。 また、位置指定パターンに対して[タプル型](../builtin-types/value-tuples.md)の式を一致させることもできます。 このようにして、次の例に示すように、複数の入力をさまざまなパターンに一致させることができます。

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="MatchTuple":::

前の例では、C# 9.0 以降で使用できる[リレーショナル](#relational-patterns) パターンと[論理](#logical-patterns)パターンを使用しています。

次の例に示すように、位置指定パターンでタプル要素と `Deconstruct` パラメーターの名前を使用できます。

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="UseIdentifiers":::

また、次のいずれかの方法で位置指定パターンを拡張することもできます。

- 次の例に示すように、ランタイム型チェックと変数宣言を追加します。

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithTypeCheck":::

  前の例では、`Deconstruct` メソッドを暗黙的に提供する[位置指定レコード](../builtin-types/record.md#positional-syntax-for-property-definition)を使用しています。

- 次の例に示すように、位置指定パターン内で[プロパティ パターン](#property-pattern)を使用します。

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithPropertyPattern":::

- 次の例に示すように、前の 2 つの使用方法を組み合わせます。

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="CompletePositionalPattern":::

位置指定パターンは、再帰的パターンです。 つまり、入れ子になったパターンとして任意のパターンを使用できます。

詳細については、機能提案ノートの「[位置指定パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern)」セクションを参照してください。

## <a name="var-pattern"></a>`var` パターン

C# 7.0 以降、次の例に示すように、 *`var` パターン* を使用して、`null` を含む任意の式に一致させ、その結果を新しいローカル変数に代入します。

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="KeepInterimResult":::

`var` パターンは、中間計算の結果を保持するためにブール式内に一時変数が必要な場合に便利です。 さらに、次の例に示すように、`switch` 式またはステートメントの `when` case guard で追加のチェックを実行する必要がある場合は、`var` パターンを使用することもできます。

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="WithCaseGuards":::

前の例で、パターン `var (x, y)` は [位置指定パターン](#positional-pattern) `(var x, var y)` と同じです。

`var` パターンでは、宣言された変数の型は、パターンに一致する式のコンパイル時の型になります。

詳細については、機能提案ノートの「[Var パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern)」セクションを参照してください。

## <a name="discard-pattern"></a>破棄パターン

C# 8.0 以降、次の例に示すように、*破棄パターン* `_` を使用して、`null` を含む任意の式に一致させます。

:::code language="csharp" source="snippets/patterns/DiscardPattern.cs" id="BasicExample":::

前の例では、破棄パターンを使用して、`null` と、<xref:System.DayOfWeek> 列挙型の対応するメンバーを持たない任意の整数値を処理しています。 これにより、例の `switch` 式ですべての可能な入力値が処理されることが保証されます。 `switch` 式で破棄パターンを使用せず、式のパターンが入力に一致しない場合、ランタイムによって、[例外がスロー](switch-expression.md#non-exhaustive-switch-expressions)されます。 `switch` 式ですべての可能な入力値が処理されない場合、コンパイラで警告が生成されます。

破棄パターンを、`is` 式または `switch` ステートメントでパターンにすることはできません。 そのような場合、任意の式に一致させるには、破棄を含む [`var` パターン](#var-pattern) `var _` を使用します。

詳細については、機能提案ノートの「[破棄パターン](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern)」セクションを参照してください。

## <a name="parenthesized-pattern"></a>かっこで囲まれたパターン

C# 9.0 以降、任意のパターンをかっこで囲むことができます。 一般にそれを行うのは、次の例に示すように、[論理パターン](#logical-patterns)の優先順位を強調または変更するためです。

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="ChangedPrecedence":::

## <a name="c-language-specification"></a>C# 言語仕様

詳しくは、次の機能提案メモをご覧ください。

- [C# 7.0 のパターン マッチング](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [再帰的なパターンマッチング (C# 8.0 で導入)](~/_csharplang/proposals/csharp-8.0/patterns.md)
- [C# 9.0 のパターン マッチングの変更](~/_csharplang/proposals/csharp-9.0/patterns3.md)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# の演算子と式](index.md)
- [チュートリアル: パターン マッチングを使用して、型ドリブンおよびデータ ドリブンのアルゴリズムを構築する](../../tutorials/pattern-matching.md)
