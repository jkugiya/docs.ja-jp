---
description: '! (null 免除) 演算子 - C# リファレンス'
title: '! (null 免除) 演算子 - C# リファレンス'
ms.date: 11/13/2020
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 14bc4501dfed515e162a6e30137c9def89bb3651
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111076"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null 免除) 演算子 (C# リファレンス)

C# 8.0 以降では、単項の接尾辞 `!` 演算子は null 免除 (または null 抑制) 演算子です。 有効な [null 許容注釈コンテキスト](../../nullable-references.md#nullable-annotation-context)では、null 免除演算子を使用して、参照型の式 `x` が `null`: `x!` ではないことを宣言します。 単項の接頭辞 `!` 演算子は、[論理否定演算子](boolean-logical-operators.md#logical-negation-operator-)です。

null 免除演算子は実行時には影響を与えません。 式の null 状態を変更することによって、コンパイラの静的フロー分析にのみ影響を与えます。 実行時に、式 `x!` は基になる式 `x` の結果に評価されます。

null 許容参照型の機能の詳細については、「[null 許容参照型](../builtin-types/nullable-reference-types.md)」を参照してください。

## <a name="examples"></a>使用例

null 免除演算子のユース ケースの 1 つは、引数検証ロジックをテストすることです。 たとえば、次のクラスを考えてみます。

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

[MSTest テスト フレームワーク](../../../core/testing/unit-testing-with-mstest.md) を使用して、コンストラクターの検証ロジックに対して次のテストを作成できます。

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

null 免除演算子を使用しない場合は、コンパイラによって上のコードに対して次の警告が生成されます: `Warning CS8625: Cannot convert null literal to non-nullable reference type`。 null 免除演算子を使用すると、`null` を渡すことが予測されており、警告を生成しないことがコンパイラに通知されます。

また、式を `null` にできないことが明確にわかっているが、コンパイラでそのことを認識できない場合にも、null 免除演算子を使用できます。 次の例では、`IsValid` メソッドによって `true` が返された場合、その引数は `null` ではなく、安全に逆参照できます。

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

null 免除演算子を使用しない場合は、コンパイラによって `p.Name` コードに対して次の警告が生成されます: `Warning CS8602: Dereference of a possibly null reference`。

`IsValid` メソッドを変更できる場合は、[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) 属性を使用して、メソッドによって `true` が返されたときに `IsValid` メソッドの引数を `null` にできないことをコンパイラに通知することができます。

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

前の例では、null 免除演算子を使用する必要はありません。これは、`if` ステートメント内で `p` を `null` にできないことを把握するのに十分な情報がコンパイラに含まれているためです。 変数の null 状態に関する追加情報を提供するための属性の詳細については、[null 予測を定義する属性を使用した API のアップグレード](../attributes/nullable-analysis.md)に関するページを参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[null 許容参照型仕様の下書き](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)の「[null 免除演算子](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator)」セクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# の演算子と式](index.md)
- [チュートリアル: null 許容参照型を使用して設計する](../../whats-new/tutorials/nullable-reference-types.md)
