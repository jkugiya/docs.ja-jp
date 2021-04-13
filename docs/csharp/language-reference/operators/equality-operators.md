---
title: 等値演算子 - C# リファレンス
description: C# の等値比較演算子と C# の型の等価性について学習します。
ms.date: 10/30/2020
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: ee45869dff19712d8e4ef30f2fc01c2d4633acf1
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255455"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="8ddc7-103">等値演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8ddc7-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="8ddc7-104">[`==` (等価)](#equality-operator-) と [`!=` (非等値)](#inequality-operator-) 演算子は、そのオペランドが等しいかどうを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="8ddc7-105">等値演算子 ==</span><span class="sxs-lookup"><span data-stu-id="8ddc7-105">Equality operator ==</span></span>

<span data-ttu-id="8ddc7-106">等値演算子 `==` は、そのオペランドが等しい場合には `true` を返し、それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="8ddc7-107">値の型の等価性</span><span class="sxs-lookup"><span data-stu-id="8ddc7-107">Value types equality</span></span>

<span data-ttu-id="8ddc7-108">[組み込みの値の型](../builtin-types/value-types.md#built-in-value-types)のオペランドは、その値が等しい場合は等しくなります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="8ddc7-109">`==`、[`<`、`>`、`<=`、および `>=`](comparison-operators.md) 演算子の場合、いずれかのオペランドが数値 (<xref:System.Double.NaN?displayProperty=nameWithType> または <xref:System.Single.NaN?displayProperty=nameWithType>) でない場合、演算結果は `false` になります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="8ddc7-110">つまり、`NaN` の値は、`NaN` を含む他のどの `double` (または `float`) の値を上回ることも、下回ることも、等しいこともありません。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="8ddc7-111">詳細およびサンプルについては、<xref:System.Double.NaN?displayProperty=nameWithType> または <xref:System.Single.NaN?displayProperty=nameWithType> の参照記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="8ddc7-112">同じ[列挙](../builtin-types/enum.md)型の 2 つのオペランドは、基になる整数型の対応する値が等しい場合は等しくなります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="8ddc7-113">既定ではユーザー定義 [struct](../builtin-types/struct.md) 型は `==` 演算子をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="8ddc7-114">`==` 演算子をサポートするには、ユーザー定義 struct でそれを[オーバーロード](operator-overloading.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="8ddc7-115">C# 7.3 より、`==` および `!=` 演算子は C# の[タプル](../builtin-types/value-tuples.md)によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="8ddc7-116">詳細については、[タプル型](../builtin-types/value-tuples.md)に関する記事の[タプルの等価性](../builtin-types/value-tuples.md#tuple-equality)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="8ddc7-117">参照型の等価性</span><span class="sxs-lookup"><span data-stu-id="8ddc7-117">Reference types equality</span></span>

<span data-ttu-id="8ddc7-118">既定では、レコードではない 2 つの参照型オペランドは、同じオブジェクトを参照しているときに等しくなります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-118">By default, two non-record reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="8ddc7-119">次の例は、ユーザー定義の参照型が既定で `==` 演算子をサポートしていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="8ddc7-120">ただし、参照型は `==` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="8ddc7-121">参照型が `==` 演算子をオーバーロードする場合、その型の 2 つの参照が同じオブジェクトを参照しているかどうかを調べるには <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="record-types-equality"></a><span data-ttu-id="8ddc7-122">レコードの型の等価性</span><span class="sxs-lookup"><span data-stu-id="8ddc7-122">Record types equality</span></span>

<span data-ttu-id="8ddc7-123">C# 9.0 以降で利用できる[レコードの型](../builtin-types/record.md)では、既定で値の等価性セマンティクスを提供する `==` 演算子と `!=` 演算子をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-123">Available in C# 9.0 and later, [record types](../builtin-types/record.md) support the `==` and `!=` operators that by default provide value equality semantics.</span></span> <span data-ttu-id="8ddc7-124">つまり、2 つのレコード オペランドは、いずれも `null` であるか、すべてのフィールドと自動実装プロパティの該当値が等しいときに等しくなります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-124">That is, two record operands are equal when both of them are `null` or corresponding values of all fields and auto-implemented properties are equal.</span></span>

:::code language="csharp" source="snippets/shared/EqualityOperators.cs" id="RecordTypesEquality":::

<span data-ttu-id="8ddc7-125">前の例からわかるように、レコードではない参照型メンバーの場合、参照されるインスタンスではなく、参照値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-125">As the preceding example shows, in case of non-record reference-type members their reference values are compared, not the referenced instances.</span></span>

### <a name="string-equality"></a><span data-ttu-id="8ddc7-126">文字列の等価性</span><span class="sxs-lookup"><span data-stu-id="8ddc7-126">String equality</span></span>

<span data-ttu-id="8ddc7-127">2 つの [string](../builtin-types/reference-types.md#the-string-type) オペランドは、その両方が `null` であるか、両方の文字列インスタンスの長さが同じで、それぞれの文字列の位置に同じ文字が含まれている場合に等しくなります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-127">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="8ddc7-128">序数の比較では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-128">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="8ddc7-129">文字列の比較に関する詳細については、「[C# で文字列を比較する方法](../../how-to/compare-strings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-129">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="8ddc7-130">デリゲートの等価性</span><span class="sxs-lookup"><span data-stu-id="8ddc7-130">Delegate equality</span></span>

<span data-ttu-id="8ddc7-131">同じランタイム型を持つ 2 つの[デリゲート](../../programming-guide/delegates/index.md) オペランドが等しくなるのは、それらの両方が `null` であるか、それらの呼び出しリストが同じ長さで、各位置に等しいエントリを含んでいる場合です。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-131">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="8ddc7-132">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[Delegate equality operators (デリゲートの等値演算子)](~/_csharplang/spec/expressions.md#delegate-equality-operators)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-132">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8ddc7-133">次の例に示すように、意味的に等しい[ラムダ式](lambda-expressions.md)を評価して生成されるデリゲートは、等しくありません。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-133">Delegates that are produced from evaluation of semantically identical [lambda expressions](lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="8ddc7-134">非等値演算子 !=</span><span class="sxs-lookup"><span data-stu-id="8ddc7-134">Inequality operator !=</span></span>

<span data-ttu-id="8ddc7-135">非等値演算子 `!=` は、そのオペランドが等しくない場合には `true` を返し、それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-135">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="8ddc7-136">[組み込み型](../builtin-types/built-in-types.md)のオペランドの場合、式 `x != y` と式 `!(x == y)` では同じ結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-136">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="8ddc7-137">等価型の詳細については、「[等値演算子](#equality-operator-)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-137">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="8ddc7-138">`!=` 演算子の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-138">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="8ddc7-139">演算子のオーバーロード可/不可</span><span class="sxs-lookup"><span data-stu-id="8ddc7-139">Operator overloadability</span></span>

<span data-ttu-id="8ddc7-140">ユーザー定義型は `==` 演算子と `!=` 演算子を[オーバーロード](operator-overloading.md)できます。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-140">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="8ddc7-141">ある型でこの 2 つの演算子の 1 つをオーバーロードする場合は、もう 1 つの演算子もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-141">If a type overloads one of the two operators, it must also overload the other one.</span></span>

<span data-ttu-id="8ddc7-142">レコードの型で `==` 演算子と `!=` 演算子を明示的にオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-142">A record type cannot explicitly overload the `==` and `!=` operators.</span></span> <span data-ttu-id="8ddc7-143">レコードの型 `T` の `==` 演算子と `!=` 演算子の動作を変更する必要がある場合、次のシグネチャで <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-143">If you need to change the behavior of the `==` and `!=` operators for record type `T`, implement the <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> method with the following signature:</span></span>

```csharp
public virtual bool Equals(T? other);
```

## <a name="c-language-specification"></a><span data-ttu-id="8ddc7-144">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="8ddc7-144">C# language specification</span></span>

<span data-ttu-id="8ddc7-145">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)に関するページの「[関係演算子と型検査演算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-145">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8ddc7-146">レコードの型の等価性に関する詳細については、[レコード機能提案メモ](~/_csharplang/proposals/csharp-9.0/records.md) ページの「[等値メンバー](~/_csharplang/proposals/csharp-9.0/records.md#equality-members)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ddc7-146">For more information about equality of record types, see the [Equality members](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) section of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ddc7-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ddc7-147">See also</span></span>

- [<span data-ttu-id="8ddc7-148">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="8ddc7-148">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8ddc7-149">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="8ddc7-149">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8ddc7-150">等価比較</span><span class="sxs-lookup"><span data-stu-id="8ddc7-150">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="8ddc7-151">比較演算子</span><span class="sxs-lookup"><span data-stu-id="8ddc7-151">Comparison operators</span></span>](comparison-operators.md)
