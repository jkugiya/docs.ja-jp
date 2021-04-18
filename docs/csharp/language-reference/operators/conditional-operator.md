---
description: '?: 演算子 - C# リファレンス'
title: '?: 演算子 - C# リファレンス'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 84a740f3afeca94a706b4120b8cd8f191f49a048
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369570"
---
# <a name="-operator-c-reference"></a>?: 演算子 (C# リファレンス)

条件演算子 `?:` は、三項条件演算子とも呼ばれ、ブール式を評価し、ブール式の評価結果 (`true` または `false`) に応じて、2 つの式のいずれかの結果を返します。次の例を参照してください。

:::code language="csharp" interactive="try-dotnet-method" source="snippets/shared/ConditionalOperator.cs" id="BasicExample":::

前の例で示したように、条件演算子の構文は次のようになります。

```csharp
condition ? consequent : alternative
```

`condition` 式は `true` または `false` と評価する必要があります。 `condition` が `true` と評価された場合は、`consequent` 式が評価され、その結果が演算の結果になります。 `condition` が `false` と評価された場合は、`alternative` 式が評価され、その結果が演算の結果になります。 `consequent` または `alternative` のみが評価されます。

C# 9.0 以降、条件式はターゲット型になっています。 つまり、条件式のターゲット型がわかっている場合、次の例に示すように、`consequent` と `alternative` の型は、暗黙的にターゲット型に変換できる必要があります。

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

条件式のターゲット型が不明な場合 (たとえば、[`var`](../keywords/var.md) キーワードを使用する場合) または C# 8.0 以前の場合、`consequent` と `alternative` の型は同じであるか、またはある型から別の型に暗黙的に変換される必要があります。

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

条件演算子は右結合です。つまり、次の形式の式があるとします。

```csharp
a ? b : c ? d : e
```

これが次のように評価されます。

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> 次のニーモニック デバイスを使用して、条件演算子の評価方法を思い出すことができます。
>
> ```text
> is this condition true ? yes : no
> ```

## <a name="conditional-ref-expression"></a>ref 条件式

C# 7.2 以降、ref 条件式は、[ref ローカル](../keywords/ref.md#ref-locals)または [ref readonly ローカル](../keywords/ref.md#ref-readonly-locals)変数を使用して条件付きで割り当てることができます。 ref 条件式を[参照戻り値](../keywords/ref.md#reference-return-values)または [`ref` メソッドの引数](../keywords/ref.md#passing-an-argument-by-reference)として使用することもできます。

ref 条件式の構文は次のとおりです。

```csharp
condition ? ref consequent : ref alternative
```

ref 条件式では、元の条件演算子と同じように、2 つの式 (`consequent` または `alternative`) のいずれかのみが評価されます。

ref 条件式の場合、`consequent` と `alternative` の型は同じである必要があります。 ref 条件式は、ターゲット型ではありません。

ref 条件演算子の使用例を次に示します。

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>条件演算子と `if..else` ステートメント

[if-else](../keywords/if-else.md) ステートメントではなく条件演算子を使用すると、値の計算を条件付きで実行する必要がある場合に、コードをもっと簡潔にできる可能性があります。 次の例では、整数を負の値または負以外の値に分類するための 2 つの方法を示しています。

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は条件演算子をオーバーロードできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の「[条件演算子](~/_csharplang/spec/expressions.md#conditional-operator)」セクションを参照してください。

C# 7.2 以降に追加された機能の詳細については、機能の提案に関する次の記述を参照してください。

- [ref 条件式 (C# 7.2)](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [ターゲット型の条件式 (C# 9.0)](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# の演算子と式](index.md)
- [if-else ステートメント](../keywords/if-else.md)
- [?. および ?[] 演算子](member-access-operators.md#null-conditional-operators--and-)
- [?? および ??= 演算子](null-coalescing-operator.md)
- [ref キーワード](../keywords/ref.md)
