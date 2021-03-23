---
title: メンバー アクセス演算子と式 - C# リファレンス
description: 型のメンバーにアクセスするために使用できる C# 演算子について説明します。
ms.date: 11/13/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: b3ba56c7485d27d2692a589e2a8e5b330ea0de85
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873901"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="75399-103">メンバー アクセス演算子と式 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="75399-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="75399-104">型のメンバーにアクセスするときは、次の演算子と式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="75399-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="75399-105">[`.` (メンバー アクセス) ](#member-access-expression-): 名前空間または型のメンバーにアクセスします</span><span class="sxs-lookup"><span data-stu-id="75399-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="75399-106">[`[]` (配列要素またはインデクサー アクセス) ](#indexer-operator-): 配列要素または型のインデクサーにアクセスします</span><span class="sxs-lookup"><span data-stu-id="75399-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="75399-107">[`?.` および `?[]` (null 条件演算子)](#null-conditional-operators--and-): オペランドが null でない場合にのみ、メンバーまたは要素へのアクセス操作を実行します</span><span class="sxs-lookup"><span data-stu-id="75399-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="75399-108">[`()` (呼び出し)](#invocation-expression-): アクセスしたメソッドを呼び出すか、デリゲートを呼び出します</span><span class="sxs-lookup"><span data-stu-id="75399-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="75399-109">[`^` (末尾からのインデックス)](#index-from-end-operator-): 要素の位置がシーケンスの末尾からであることを示します</span><span class="sxs-lookup"><span data-stu-id="75399-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="75399-110">[`..` (範囲)](#range-operator-): シーケンス要素の範囲を取得するために使用できるインデックスの範囲を指定します</span><span class="sxs-lookup"><span data-stu-id="75399-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="75399-111">メンバー アクセス式 .</span><span class="sxs-lookup"><span data-stu-id="75399-111">Member access expression .</span></span>

<span data-ttu-id="75399-112">以下の例に示すように、名前空間のメンバーまたは型にアクセスするために `.` トークンを使います。</span><span class="sxs-lookup"><span data-stu-id="75399-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="75399-113">次の [`using` ディレクティブ](../keywords/using-directive.md)の例に示すように、`.` を使って、名前空間内の入れ子になった名前空間にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="75399-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/shared/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="75399-114">次のコードに示すように、`.` を使って "*修飾名*" を作成して名前空間内の型にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="75399-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/shared/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="75399-115">[`using` ディレクティブ](../keywords/using-directive.md)を使い、必要に応じて修飾名を利用します。</span><span class="sxs-lookup"><span data-stu-id="75399-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="75399-116">次のコードに示すように、`.` を使って、[型のメンバー](../../programming-guide/classes-and-structs/index.md#members) (静的および非静的) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="75399-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/shared/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="75399-117">また、`.` を使って[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)にアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="75399-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="75399-118">インデクサー演算子 []</span><span class="sxs-lookup"><span data-stu-id="75399-118">Indexer operator []</span></span>

<span data-ttu-id="75399-119">通常、角かっこ `[]` は、配列、インデクサー、またはポインター要素へのアクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="75399-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="75399-120">配列へのアクセス</span><span class="sxs-lookup"><span data-stu-id="75399-120">Array access</span></span>

<span data-ttu-id="75399-121">次の例は、配列要素へのアクセス方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="75399-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/shared/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="75399-122">配列インデックスが配列の対応するディメンションの範囲に含まれない場合、<xref:System.IndexOutOfRangeException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="75399-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="75399-123">前述の例が示すように、配列型の宣言と配列インスタンスのインスタンス化にも角かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="75399-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="75399-124">配列の詳細については、「[配列](../../programming-guide/arrays/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="75399-125">インデクサーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="75399-125">Indexer access</span></span>

<span data-ttu-id="75399-126">次の例では、インデクサーへのアクセスを示すために .NET <xref:System.Collections.Generic.Dictionary%602> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="75399-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/shared/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="75399-127">インデクサーを使用すると、配列のインデックス作成と同様の方法でユーザー定義型のインスタンスのインデックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="75399-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="75399-128">整数である必要がある配列インデックスとは異なり、任意の型を持つインデクサー パラメーターを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="75399-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="75399-129">インデクサーの詳細については、「[インデクサー](../../programming-guide/indexers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="75399-130">[] の他の使用方法</span><span class="sxs-lookup"><span data-stu-id="75399-130">Other usages of []</span></span>

<span data-ttu-id="75399-131">ポインター要素へのアクセスの詳細については、[ポインターに関連する演算子](pointer-related-operators.md)に関する記事の「[ポインター要素アクセス演算子 []](pointer-related-operators.md#pointer-element-access-operator-)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="75399-132">角かっこは、[属性](../../programming-guide/concepts/attributes/index.md)を指定するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="75399-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="75399-133">Null 条件演算子 ?.</span><span class="sxs-lookup"><span data-stu-id="75399-133">Null-conditional operators ?.</span></span> <span data-ttu-id="75399-134">および ?[]</span><span class="sxs-lookup"><span data-stu-id="75399-134">and ?[]</span></span>

<span data-ttu-id="75399-135">C# 6 以降で使用できる Null 条件付き演算子は、そのオペランドが null 以外と評価された場合にのみ、オペランドに[メンバー アクセス](#member-access-expression-)操作 (`?.`) または[要素アクセス](#indexer-operator-)操作 (`?[]`) を適用し、それ以外の場合は、`null` を返します。</span><span class="sxs-lookup"><span data-stu-id="75399-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="75399-136">つまり、以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="75399-136">That is,</span></span>

- <span data-ttu-id="75399-137">`a` が `null` と評価された場合、`a?.x` または `a?[x]` の結果は `null` です。</span><span class="sxs-lookup"><span data-stu-id="75399-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="75399-138">`a` が null 以外と評価された場合、`a?.x` または `a?[x]` の結果は、`a.x` または `a[x]` の結果とそれぞれ同じです。</span><span class="sxs-lookup"><span data-stu-id="75399-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="75399-139">`a.x` または `a[x]` が例外をスローした場合は、`a?.x` または `a?[x]` が、null 以外の `a` に対して同じ例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="75399-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="75399-140">たとえば、`a` が null 以外の配列インスタンスで、`x` が `a`の範囲外にある場合、`a?[x]` は <xref:System.IndexOutOfRangeException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="75399-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="75399-141">Null 条件演算子はショートサーキットです。</span><span class="sxs-lookup"><span data-stu-id="75399-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="75399-142">つまり、条件付きのメンバーまたは要素アクセス操作のチェーン内にある 1 つの操作から `null` が返された場合、残りのチェーンは実行されません。</span><span class="sxs-lookup"><span data-stu-id="75399-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="75399-143">次の例では、`A` が `null` と評価されると `B` は評価されず、`A` または `B` が `null` と評価されると `C` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="75399-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="75399-144">`?.` および `?[]` 演算子の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="75399-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/shared/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="75399-145">前の例では、null 条件演算の結果が `null` の場合に評価する代替の式を指定するために、[null 合体演算子 `??`](null-coalescing-operator.md) も使用しています。</span><span class="sxs-lookup"><span data-stu-id="75399-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="75399-146">`a.x` または `a[x]` が null 非許容値型の `T` の場合は、`a?.x` または `a?[x]` は対応する [null 許容値型](../builtin-types/nullable-value-types.md)の `T?` になります。</span><span class="sxs-lookup"><span data-stu-id="75399-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="75399-147">`T` 型の式が必要な場合は、次の例に示すように、null 合体演算子 `??` を null 条件式に適用します。</span><span class="sxs-lookup"><span data-stu-id="75399-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/shared/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="75399-148">前の例では、`??` 演算子を使用しなければ、`numbers` が `null` の場合、`numbers?.Length < 2` は `false` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="75399-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="75399-149">Null 条件メンバー アクセス演算子 `?.` は Elvis 演算子とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="75399-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="75399-150">スレッドセーフなデリゲートの呼び出し</span><span class="sxs-lookup"><span data-stu-id="75399-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="75399-151">次のコードに示すように、`?.` 演算子を使用してデリゲートが null 以外かどうかを確認し、それをスレッドセーフな方法で呼び出します (たとえば、[イベントを発生させる](../../../standard/events/how-to-raise-and-consume-events.md)場合)。</span><span class="sxs-lookup"><span data-stu-id="75399-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="75399-152">このコードは、C# 5 以前で使用する次のコードと同等です。</span><span class="sxs-lookup"><span data-stu-id="75399-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="75399-153">これは、null 以外の `handler` のみが呼び出されるようにするためのスレッドセーフな方法です。</span><span class="sxs-lookup"><span data-stu-id="75399-153">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="75399-154">デリゲート インスタンスは不変であるため、`handler` ローカル変数によって参照されるオブジェクトを変更できるスレッドはありません。</span><span class="sxs-lookup"><span data-stu-id="75399-154">Because delegate instances are immutable, no thread can change the object referenced by the `handler` local variable.</span></span> <span data-ttu-id="75399-155">具体的には、別のスレッドによって実行されるコードが `PropertyChanged` イベントから登録解除され、`handler` が呼び出される前に `PropertyChanged` が `null` になる場合、`handler` によって参照されるオブジェクトは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="75399-155">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the object referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="75399-156">`?.` 演算子では、左側のオペランドが 1 回だけ評価され、null 以外として検証された後に `null` に変更できないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="75399-156">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="75399-157">呼び出し式 ()</span><span class="sxs-lookup"><span data-stu-id="75399-157">Invocation expression ()</span></span>

<span data-ttu-id="75399-158">かっこ `()` は、[メソッド](../../programming-guide/classes-and-structs/methods.md)を呼び出すとき、または[デリゲート](../../programming-guide/delegates/index.md)を呼び出すときに使用します。</span><span class="sxs-lookup"><span data-stu-id="75399-158">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="75399-159">メソッドを呼び出す方法 (引数を指定した場合と指定しない場合) とデリゲートを呼び出す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="75399-159">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/shared/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="75399-160">かっこは、[`new`](new-operator.md) 演算子を使用して[コンストラクター](../../programming-guide/classes-and-structs/constructors.md)を呼び出すときにも使用します。</span><span class="sxs-lookup"><span data-stu-id="75399-160">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="75399-161">() の他の使用方法</span><span class="sxs-lookup"><span data-stu-id="75399-161">Other usages of ()</span></span>

<span data-ttu-id="75399-162">式に含まれる演算を評価する順序を調整する場合にもかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="75399-162">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="75399-163">詳細については、[C# 演算子](index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-163">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="75399-164">明示的な型変換を実行する[キャスト式](type-testing-and-cast.md#cast-expression)でも、かっこが使われます。</span><span class="sxs-lookup"><span data-stu-id="75399-164">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="75399-165">末尾からのインデックス演算子 ^</span><span class="sxs-lookup"><span data-stu-id="75399-165">Index from end operator ^</span></span>

<span data-ttu-id="75399-166">`^` 演算子は C# 8.0 以降で使用することができ、要素の位置がシーケンスの末尾からであることを示します。</span><span class="sxs-lookup"><span data-stu-id="75399-166">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="75399-167">長さが `length` のシーケンスの場合、`^n` は、シーケンスの先頭からのオフセットが `length - n` である要素を指します。</span><span class="sxs-lookup"><span data-stu-id="75399-167">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="75399-168">たとえば、`^1` は、シーケンスの最後の要素を指し、`^length` は、シーケンスの最初の要素を指します。</span><span class="sxs-lookup"><span data-stu-id="75399-168">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/shared/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="75399-169">前の例で示すように、式 `^e` は <xref:System.Index?displayProperty=nameWithType> 型です。</span><span class="sxs-lookup"><span data-stu-id="75399-169">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="75399-170">式 `^e`で、`e` の結果は `int` に暗黙に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="75399-170">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="75399-171">さらに、`^` 演算子を[範囲演算子 ](#range-operator-) と組み合わせて使用してインデックスの範囲を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="75399-171">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="75399-172">詳細については、「[インデックスと範囲](../../whats-new/tutorials/ranges-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-172">For more information, see [Indices and ranges](../../whats-new/tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="75399-173">範囲演算子 .</span><span class="sxs-lookup"><span data-stu-id="75399-173">Range operator ..</span></span>

<span data-ttu-id="75399-174">`..` 演算子は C# 8.0 以降で使用することができ、インデックスの範囲の先頭と末尾をオペランドとして指定します。</span><span class="sxs-lookup"><span data-stu-id="75399-174">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="75399-175">左側のオペランドは "*包含的*" で、範囲の先頭を含みます。</span><span class="sxs-lookup"><span data-stu-id="75399-175">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="75399-176">右側のオペランドは "*排他的*" で、範囲の末尾を含みません。</span><span class="sxs-lookup"><span data-stu-id="75399-176">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="75399-177">次の例で示すように、どちらのオペランドであっても、シーケンスの先頭または末尾からのインデックスとすることができます。</span><span class="sxs-lookup"><span data-stu-id="75399-177">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/shared/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="75399-178">前の例で示すように、式 `a..b` は <xref:System.Range?displayProperty=nameWithType> 型です。</span><span class="sxs-lookup"><span data-stu-id="75399-178">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="75399-179">式 `a..b` で、`a` および `b` の結果は暗黙に `int` または <xref:System.Index> に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="75399-179">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="75399-180">`..` 演算子のオペランドのいずれかを省略して、変更可能な範囲を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="75399-180">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="75399-181">`a..` は `a..^0` と同じです。</span><span class="sxs-lookup"><span data-stu-id="75399-181">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="75399-182">`..b` は `0..b` と同じです。</span><span class="sxs-lookup"><span data-stu-id="75399-182">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="75399-183">`..` は `0..^0` と同じです。</span><span class="sxs-lookup"><span data-stu-id="75399-183">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/shared/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="75399-184">詳細については、「[インデックスと範囲](../../whats-new/tutorials/ranges-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-184">For more information, see [Indices and ranges](../../whats-new/tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="75399-185">演算子のオーバーロード可/不可</span><span class="sxs-lookup"><span data-stu-id="75399-185">Operator overloadability</span></span>

<span data-ttu-id="75399-186">`.`、`()`、`^`、および `..` の各演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="75399-186">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="75399-187">`[]` 演算子も、オーバーロードできない演算子と見なされます。</span><span class="sxs-lookup"><span data-stu-id="75399-187">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="75399-188">ユーザー定義型を使用したインデックス作成をサポートするには、[インデクサー](../../programming-guide/indexers/index.md)を使用してください。</span><span class="sxs-lookup"><span data-stu-id="75399-188">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="75399-189">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="75399-189">C# language specification</span></span>

<span data-ttu-id="75399-190">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-190">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="75399-191">メンバー アクセス</span><span class="sxs-lookup"><span data-stu-id="75399-191">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="75399-192">要素アクセス</span><span class="sxs-lookup"><span data-stu-id="75399-192">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="75399-193">NULL 条件演算子</span><span class="sxs-lookup"><span data-stu-id="75399-193">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="75399-194">呼び出し式</span><span class="sxs-lookup"><span data-stu-id="75399-194">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="75399-195">インデックスと範囲について詳しくは、[機能提案メモ](~/_csharplang/proposals/csharp-8.0/ranges.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75399-195">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75399-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="75399-196">See also</span></span>

- [<span data-ttu-id="75399-197">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="75399-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="75399-198">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="75399-198">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="75399-199">?? (Null 合体演算子)</span><span class="sxs-lookup"><span data-stu-id="75399-199">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="75399-200">:: 演算子</span><span class="sxs-lookup"><span data-stu-id="75399-200">:: operator</span></span>](namespace-alias-qualifier.md)
