---
title: 構造体型 - C# リファレンス
description: C# での構造体型について
ms.date: 10/23/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 3aaba057da6214992864cf8e907b0c06ec93264c
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255091"
---
# <a name="structure-types-c-reference"></a><span data-ttu-id="a22a5-103">構造体型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a22a5-103">Structure types (C# reference)</span></span>

<span data-ttu-id="a22a5-104">"*構造体型*" (または "*構造体型*") とは、データおよび関連する機能をカプセル化できる [値の型](value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="a22a5-104">A *structure type* (or *struct type*) is a [value type](value-types.md) that can encapsulate data and related functionality.</span></span> <span data-ttu-id="a22a5-105">構造体型を定義するには、`struct` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-105">You use the `struct` keyword to define a structure type:</span></span>

[!code-csharp[struct example](snippets/shared/StructType.cs#StructExample)]

<span data-ttu-id="a22a5-106">構造体型には、"*値のセマンティクス*" があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-106">Structure types have *value semantics*.</span></span> <span data-ttu-id="a22a5-107">つまり、構造体型の変数には、型のインスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-107">That is, a variable of a structure type contains an instance of the type.</span></span> <span data-ttu-id="a22a5-108">既定では、変数値が代入時にコピーされ、引数がメソッドに渡され、メソッドの結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-108">By default, variable values are copied on assignment, passing an argument to a method, and returning a method result.</span></span> <span data-ttu-id="a22a5-109">構造体型の変数の場合は、型のインスタンスがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-109">In the case of a structure-type variable, an instance of the type is copied.</span></span> <span data-ttu-id="a22a5-110">詳細については、[値の型](value-types.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22a5-110">For more information, see [Value types](value-types.md).</span></span>

<span data-ttu-id="a22a5-111">通常は、構造体型を使用して、ほとんどまたはまったく動作を提供しない小さなデータ中心型を設計します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-111">Typically, you use structure types to design small data-centric types that provide little or no behavior.</span></span> <span data-ttu-id="a22a5-112">たとえば、.NET では、構造体型を使用して数値 ([整数](integral-numeric-types.md)と[実数](floating-point-numeric-types.md)の両方)、[ブール値](bool.md)、[Unicode 文字](char.md)、[時刻インスタンス](xref:System.DateTime)が表現されます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-112">For example, .NET uses structure types to represent a number (both [integer](integral-numeric-types.md) and [real](floating-point-numeric-types.md)), a [Boolean value](bool.md), a [Unicode character](char.md), a [time instance](xref:System.DateTime).</span></span> <span data-ttu-id="a22a5-113">型の動作に重点を置いている場合は、[class](../keywords/class.md) を定義することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a22a5-113">If you're focused on the behavior of a type, consider defining a [class](../keywords/class.md).</span></span> <span data-ttu-id="a22a5-114">クラス型には "*参照セマンティクス*" があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-114">Class types have *reference semantics*.</span></span> <span data-ttu-id="a22a5-115">つまり、クラス型の変数には、インスタンス自体ではなく、型のインスタンスへの参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a22a5-115">That is, a variable of a class type contains a reference to an instance of the type, not the instance itself.</span></span>

<span data-ttu-id="a22a5-116">構造体型には値セマンティクスがあるため、"*変更不可*" の構造体型を定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a22a5-116">Because structure types have value semantics, we recommend you to define *immutable* structure types.</span></span>

## <a name="readonly-struct"></a><span data-ttu-id="a22a5-117">`readonly` 構造体</span><span class="sxs-lookup"><span data-stu-id="a22a5-117">`readonly` struct</span></span>

<span data-ttu-id="a22a5-118">C# 7.2 以降では、`readonly` 修飾子を使用して、構造体型が変更不可であることを宣言します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-118">Beginning with C# 7.2, you use the `readonly` modifier to declare that a structure type is immutable.</span></span> <span data-ttu-id="a22a5-119">`readonly` 構造体のすべてのデータ メンバーを、次のように読み取り専用にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-119">All data members of a `readonly` struct must be read-only as follows:</span></span>

- <span data-ttu-id="a22a5-120">すべてのフィールド宣言には、[`readonly` 修飾子が必要です](../keywords/readonly.md)</span><span class="sxs-lookup"><span data-stu-id="a22a5-120">Any field declaration must have the [`readonly` modifier](../keywords/readonly.md)</span></span>
- <span data-ttu-id="a22a5-121">自動的に実装されるものも含めて、すべてのプロパティは、読み取り専用である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-121">Any property, including auto-implemented ones, must be read-only.</span></span> <span data-ttu-id="a22a5-122">C# 9.0 以降では、プロパティに [`init` アクセサー](../keywords/init.md)が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-122">In C# 9.0 and later, a property may have an [`init` accessor](../keywords/init.md).</span></span>

<span data-ttu-id="a22a5-123">それにより、`readonly` 構造体のどのメンバーも構造体の状態を変更しないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-123">That guarantees that no member of a `readonly` struct modifies the state of the struct.</span></span> <span data-ttu-id="a22a5-124">C# 8.0 以降では、コンストラクターを除く他のインスタンス メンバーは、暗黙的に [`readonly`](#readonly-instance-members) になるということです。</span><span class="sxs-lookup"><span data-stu-id="a22a5-124">In C# 8.0 and later, that means that other instance members except constructors are implicitly [`readonly`](#readonly-instance-members).</span></span>

> [!NOTE]
> <span data-ttu-id="a22a5-125">`readonly` 構造体でも、変更可能な参照型のデータ メンバーは、それ自身の状態を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-125">In a `readonly` struct, a data member of a mutable reference type still can mutate its own state.</span></span> <span data-ttu-id="a22a5-126">たとえば、<xref:System.Collections.Generic.List%601> インスタンスを置き換えることはできませんが、新しい要素をそれに追加することはできます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-126">For example, you can't replace a <xref:System.Collections.Generic.List%601> instance, but you can add new elements to it.</span></span>

<span data-ttu-id="a22a5-127">次のコードでは、C# 9.0 以降で使用できる、init 専用プロパティの setter を持つ `readonly` 構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-127">The following code defines a `readonly` struct with init-only property setters, available in C# 9.0 and later:</span></span>

[!code-csharp[readonly struct](snippets/shared/StructType.cs#ReadonlyStruct)]

## <a name="readonly-instance-members"></a><span data-ttu-id="a22a5-128">`readonly` インスタンス メンバー</span><span class="sxs-lookup"><span data-stu-id="a22a5-128">`readonly` instance members</span></span>

<span data-ttu-id="a22a5-129">C# 8.0 以降では、`readonly` 修飾子を使用して、インスタンス メンバーで構造体の状態を変更しないことを宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-129">Beginning with C# 8.0, you can also use the `readonly` modifier to declare that an instance member doesn't modify the state of a struct.</span></span> <span data-ttu-id="a22a5-130">構造体の型全体を `readonly` として宣言できない場合は、`readonly` 修飾子を使用して、構造体の状態を変更しないインスタンス メンバーをマークします。</span><span class="sxs-lookup"><span data-stu-id="a22a5-130">If you can't declare the whole structure type as `readonly`, use the `readonly` modifier to mark the instance members that don't modify the state of the struct.</span></span>

<span data-ttu-id="a22a5-131">`readonly` インスタンス メンバー内では、構造体のインスタンス フィールドに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-131">Within a `readonly` instance member, you can't assign to structure's instance fields.</span></span> <span data-ttu-id="a22a5-132">ただし、`readonly` メンバーから非 `readonly` メンバーを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-132">However, a `readonly` member can call a non-`readonly` member.</span></span> <span data-ttu-id="a22a5-133">その場合、コンパイラを使用して構造体インスタンスのコピーを作成し、そのコピーで非 `readonly` メンバーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-133">In that case the compiler creates a copy of the structure instance and calls the non-`readonly` member on that copy.</span></span> <span data-ttu-id="a22a5-134">その結果、元の構造インスタンスは変更されません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-134">As a result, the original structure instance is not modified.</span></span>

<span data-ttu-id="a22a5-135">通常、`readonly` 修飾子を次の種類のインスタンス メンバーに適用します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-135">Typically, you apply the `readonly` modifier to the following kinds of instance members:</span></span>

- <span data-ttu-id="a22a5-136">メソッド:</span><span class="sxs-lookup"><span data-stu-id="a22a5-136">methods:</span></span>

  [!code-csharp[readonly method](snippets/shared/StructType.cs#ReadonlyMethod)]

  <span data-ttu-id="a22a5-137"><xref:System.Object?displayProperty=nameWithType> で宣言されたメソッドをオーバーライドするメソッドに `readonly` 修飾子を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-137">You can also apply the `readonly` modifier to methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>:</span></span>

  [!code-csharp[readonly override](snippets/shared/StructType.cs#ReadonlyOverride)]

- <span data-ttu-id="a22a5-138">プロパティとインデクサー:</span><span class="sxs-lookup"><span data-stu-id="a22a5-138">properties and indexers:</span></span>

  [!code-csharp[readonly property get](snippets/shared/StructType.cs#ReadonlyProperty)]

  <span data-ttu-id="a22a5-139">プロパティまたはインデクサーの両方のアクセサーに `readonly` 修飾子を適用する必要がある場合は、プロパティまたはインデクサーの宣言でそれを適用します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-139">If you need to apply the `readonly` modifier to both accessors of a property or indexer, apply it in the declaration of the property or indexer.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a22a5-140">プロパティの宣言に `readonly` 修飾子が存在するかどうかに関係なく、コンパイラによって[自動実装プロパティ](../../programming-guide/classes-and-structs/auto-implemented-properties.md)の `get` アクセサーが `readonly` として宣言されます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-140">The compiler declares a `get` accessor of an [auto-implemented property](../../programming-guide/classes-and-structs/auto-implemented-properties.md) as `readonly`, regardless of presence of the `readonly` modifier in a property declaration.</span></span>

  <span data-ttu-id="a22a5-141">C# 9.0 以降では、`init` アクセサーを持つプロパティまたはインデクサーに `readonly` 修飾子を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-141">In C# 9.0 and later, you may apply the `readonly` modifier to a property or indexer with an `init` accessor:</span></span>

  :::code language="csharp" source="snippets/shared/StructType.cs" id="ReadonlyWithInit":::

<span data-ttu-id="a22a5-142">`readonly` 修飾子を構造体型の静的メンバーに適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-142">You can't apply the `readonly` modifier to static members of a structure type.</span></span>

<span data-ttu-id="a22a5-143">パフォーマンスの最適化のためにコンパイラで `readonly` 修飾子を使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-143">The compiler may make use of the `readonly` modifier for performance optimizations.</span></span> <span data-ttu-id="a22a5-144">詳細については、「[安全で効率的な C# コードを記述する](../../write-safe-efficient-code.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a22a5-144">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="limitations-with-the-design-of-a-structure-type"></a><span data-ttu-id="a22a5-145">構造体型の設計に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="a22a5-145">Limitations with the design of a structure type</span></span>

<span data-ttu-id="a22a5-146">構造体型を設計する場合は、[class](../keywords/class.md) 型と同じ機能を使用できますが、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-146">When you design a structure type, you have the same capabilities as with a [class](../keywords/class.md) type, with the following exceptions:</span></span>

- <span data-ttu-id="a22a5-147">パラメーターなしのコンストラクターを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-147">You can't declare a parameterless constructor.</span></span> <span data-ttu-id="a22a5-148">すべての構造体型には、型の[既定値](default-values.md)を生成する暗黙的なパラメーターなしのコンストラクターが既に備わっています。</span><span class="sxs-lookup"><span data-stu-id="a22a5-148">Every structure type already provides an implicit parameterless constructor that produces the [default value](default-values.md) of the type.</span></span>

- <span data-ttu-id="a22a5-149">インスタンス フィールドまたはプロパティを、それらの宣言で初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-149">You can't initialize an instance field or property at its declaration.</span></span> <span data-ttu-id="a22a5-150">ただし、[static](../keywords/static.md) または [const](../keywords/const.md) フィールド、あるいは静的プロパティについては、それらの宣言で初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-150">However, you can initialize a [static](../keywords/static.md) or [const](../keywords/const.md) field or a static property at its declaration.</span></span>

- <span data-ttu-id="a22a5-151">構造体型のコンストラクターでは、型のすべてのインスタンス フィールドを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-151">A constructor of a structure type must initialize all instance fields of the type.</span></span>

- <span data-ttu-id="a22a5-152">構造体型は、他のクラスまたは構造体型から継承することができないほか、クラスのベースとすることもできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-152">A structure type can't inherit from other class or structure type and it can't be the base of a class.</span></span> <span data-ttu-id="a22a5-153">ただし、構造体型では [interfaces](../keywords/interface.md) を実装することができます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-153">However, a structure type can implement [interfaces](../keywords/interface.md).</span></span>

- <span data-ttu-id="a22a5-154">構造体型内で[ファイナライザー](../../programming-guide/classes-and-structs/destructors.md)を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-154">You can't declare a [finalizer](../../programming-guide/classes-and-structs/destructors.md) within a structure type.</span></span>

## <a name="instantiation-of-a-structure-type"></a><span data-ttu-id="a22a5-155">構造体型のインスタンス化</span><span class="sxs-lookup"><span data-stu-id="a22a5-155">Instantiation of a structure type</span></span>

<span data-ttu-id="a22a5-156">C# では、宣言された変数を使用するには、事前にこれを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-156">In C#, you must initialize a declared variable before it can be used.</span></span> <span data-ttu-id="a22a5-157">構造体型の変数は ([null 許容値型](nullable-value-types.md)の変数でない限り) `null` とすることができないため、対応する型のインスタンスをインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-157">Because a structure-type variable can't be `null` (unless it's a variable of a [nullable value type](nullable-value-types.md)), you must instantiate an instance of the corresponding type.</span></span> <span data-ttu-id="a22a5-158">それにはいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-158">There are several ways to do that.</span></span>

<span data-ttu-id="a22a5-159">通常は、[`new`](../operators/new-operator.md) 演算子を使用して適切なコンストラクターを呼び出すことによって、構造体型をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-159">Typically, you instantiate a structure type by calling an appropriate constructor with the [`new`](../operators/new-operator.md) operator.</span></span> <span data-ttu-id="a22a5-160">すべての構造体型に、少なくとも 1 つのコンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-160">Every structure type has at least one constructor.</span></span> <span data-ttu-id="a22a5-161">それは暗黙的なパラメーターなしのコンストラクターであり、型の[既定値](default-values.md)を生成するものです。</span><span class="sxs-lookup"><span data-stu-id="a22a5-161">That's an implicit parameterless constructor, which produces the [default value](default-values.md) of the type.</span></span> <span data-ttu-id="a22a5-162">また、[既定の値式](../operators/default.md)を使用して、型の既定値を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-162">You can also use a [default value expression](../operators/default.md) to produce the default value of a type.</span></span>

<span data-ttu-id="a22a5-163">構造体型のすべてのインスタンス フィールドにアクセスできる場合は、それを `new` 演算子なしでインスタンス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-163">If all instance fields of a structure type are accessible, you can also instantiate it without the `new` operator.</span></span> <span data-ttu-id="a22a5-164">その場合は、インスタンスを初めて使用する前に、すべてのインスタンス フィールドを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-164">In that case you must initialize all instance fields before the first use of the instance.</span></span> <span data-ttu-id="a22a5-165">その方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-165">The following example shows how to do that:</span></span>

[!code-csharp[without new](snippets/shared/StructType.cs#WithoutNew)]

<span data-ttu-id="a22a5-166">[組み込みの値型](value-types.md#built-in-value-types)の場合は、対応するリテラルを使用して型の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-166">In the case of the [built-in value types](value-types.md#built-in-value-types), use the corresponding literals to specify a value of the type.</span></span>

## <a name="passing-structure-type-variables-by-reference"></a><span data-ttu-id="a22a5-167">構造体型の変数を参照渡しする</span><span class="sxs-lookup"><span data-stu-id="a22a5-167">Passing structure-type variables by reference</span></span>

<span data-ttu-id="a22a5-168">構造体型の変数を引数としてメソッドに渡す場合、またはメソッドから構造体型の値を返す場合は、構造体型のインスタンス全体がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-168">When you pass a structure-type variable to a method as an argument or return a structure-type value from a method, the whole instance of a structure type is copied.</span></span> <span data-ttu-id="a22a5-169">これは、大規模な構造体型を必要とするハイパフォーマンスのシナリオの場合、ご利用のコードのパフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-169">That can affect the performance of your code in high-performance scenarios that involve large structure types.</span></span> <span data-ttu-id="a22a5-170">値のコピーを回避するには、構造体型の変数を参照渡しします。</span><span class="sxs-lookup"><span data-stu-id="a22a5-170">You can avoid value copying by passing a structure-type variable by reference.</span></span> <span data-ttu-id="a22a5-171">引数を参照渡しする必要があることを示すには、[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、[`out`](../keywords/out-parameter-modifier.md)、または [`in`](../keywords/in-parameter-modifier.md) のメソッド パラメーター修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-171">Use the [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md), or [`in`](../keywords/in-parameter-modifier.md) method parameter modifiers to indicate that an argument must be passed by reference.</span></span> <span data-ttu-id="a22a5-172">メソッドの結果を参照渡しによって返すには、[ref 戻り値](../../programming-guide/classes-and-structs/ref-returns.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-172">Use [ref returns](../../programming-guide/classes-and-structs/ref-returns.md) to return a method result by reference.</span></span> <span data-ttu-id="a22a5-173">詳細については、「[安全で効率的な C# コードを記述する](../../write-safe-efficient-code.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a22a5-173">For more information, see [Write safe and efficient C# code](../../write-safe-efficient-code.md).</span></span>

## <a name="ref-struct"></a><span data-ttu-id="a22a5-174">`ref` 構造体</span><span class="sxs-lookup"><span data-stu-id="a22a5-174">`ref` struct</span></span>

<span data-ttu-id="a22a5-175">C# 7.2 以降、`ref` 修飾子は、構造体型の宣言内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-175">Beginning with C# 7.2, you can use the `ref` modifier in the declaration of a structure type.</span></span> <span data-ttu-id="a22a5-176">`ref` 構造体型のインスタンスはスタック上に割り当てられます。マネージド ヒープにエスケープすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-176">Instances of a `ref` struct type are allocated on the stack and can't escape to the managed heap.</span></span> <span data-ttu-id="a22a5-177">これを確実にするために、コンパイラでは次のように `ref` 構造体型の使用が制限されます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-177">To ensure that, the compiler limits the usage of `ref` struct types as follows:</span></span>

- <span data-ttu-id="a22a5-178">`ref` 構造体を配列の要素型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-178">A `ref` struct can't be the element type of an array.</span></span>
- <span data-ttu-id="a22a5-179">`ref` 構造体をクラスまたは非 `ref` 構造体のフィールドの宣言型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-179">A `ref` struct can't be a declared type of a field of a class or a non-`ref` struct.</span></span>
- <span data-ttu-id="a22a5-180">`ref` 構造体ではインターフェイスを実装できません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-180">A `ref` struct can't implement interfaces.</span></span>
- <span data-ttu-id="a22a5-181">`ref` 構造体を <xref:System.ValueType?displayProperty=nameWithType> または <xref:System.Object?displayProperty=nameWithType> にボックス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-181">A `ref` struct can't be boxed to <xref:System.ValueType?displayProperty=nameWithType> or <xref:System.Object?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="a22a5-182">`ref` 構造体を型引数にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-182">A `ref` struct can't be a type argument.</span></span>
- <span data-ttu-id="a22a5-183">`ref` 構造体変数を[ラムダ式](../operators/lambda-expressions.md)または[ローカル関数](../../programming-guide/classes-and-structs/local-functions.md)でキャプチャすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-183">A `ref` struct variable can't be captured by a [lambda expression](../operators/lambda-expressions.md) or a [local function](../../programming-guide/classes-and-structs/local-functions.md).</span></span>
- <span data-ttu-id="a22a5-184">`ref` 構造体変数を [`async`](../keywords/async.md) メソッド内で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-184">A `ref` struct variable can't be used in an [`async`](../keywords/async.md) method.</span></span> <span data-ttu-id="a22a5-185">ただし、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返す場合など、同期メソッドで `ref` 構造体変数を使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="a22a5-185">However, you can use `ref` struct variables in synchronous methods, for example, in those that return <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="a22a5-186">`ref` 構造体変数を[反復子](../../iterators.md)内で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22a5-186">A `ref` struct variable can't be used in [iterators](../../iterators.md).</span></span>

<span data-ttu-id="a22a5-187">通常、`ref` 構造体型のデータ メンバーも含む型が必要な場合は、`ref` 構造体型を定義します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-187">Typically, you define a `ref` struct type when you need a type that also includes data members of `ref` struct types:</span></span>

[!code-csharp[ref struct](snippets/shared/StructType.cs#RefStruct)]

<span data-ttu-id="a22a5-188">`ref` 構造体を [`readonly`](#readonly-struct) として宣言するには、型宣言内で `readonly` 修飾子と `ref` 修飾子を組み合わせます (`readonly` 修飾子は `ref` 修飾子よりも前にある必要があります)。</span><span class="sxs-lookup"><span data-stu-id="a22a5-188">To declare a `ref` struct as [`readonly`](#readonly-struct), combine the `readonly` and `ref` modifiers in the type declaration (the `readonly` modifier must come before the `ref` modifier):</span></span>

[!code-csharp[readonly ref struct](snippets/shared/StructType.cs#ReadonlyRef)]

<span data-ttu-id="a22a5-189">.NET では、`ref` 構造体の例として <xref:System.Span%601?displayProperty=nameWithType> と <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> があります。</span><span class="sxs-lookup"><span data-stu-id="a22a5-189">In .NET, examples of a `ref` struct are <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

## <a name="struct-constraint"></a><span data-ttu-id="a22a5-190">struct 制約</span><span class="sxs-lookup"><span data-stu-id="a22a5-190">struct constraint</span></span>

<span data-ttu-id="a22a5-191">また、[`struct` 制約](../../programming-guide/generics/constraints-on-type-parameters.md)の `struct` キーワードを使用して、型パラメーターが null 非許容値型であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-191">You also use the `struct` keyword in the [`struct` constraint](../../programming-guide/generics/constraints-on-type-parameters.md) to specify that a type parameter is a non-nullable value type.</span></span> <span data-ttu-id="a22a5-192">構造体と[列挙型](enum.md)の型は、どちらも `struct` 制約を満たしています。</span><span class="sxs-lookup"><span data-stu-id="a22a5-192">Both structure and [enumeration](enum.md) types satisfy the `struct` constraint.</span></span>

## <a name="conversions"></a><span data-ttu-id="a22a5-193">変換</span><span class="sxs-lookup"><span data-stu-id="a22a5-193">Conversions</span></span>

<span data-ttu-id="a22a5-194">どの構造体型にも ([`ref` 構造体](#ref-struct)型を除く)、<xref:System.ValueType?displayProperty=nameWithType> 型と <xref:System.Object?displayProperty=nameWithType> 型の間に[ボックス化およびボックス化解除](../../programming-guide/types/boxing-and-unboxing.md)の変換が存在します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-194">For any structure type (except [`ref` struct](#ref-struct) types), there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.ValueType?displayProperty=nameWithType> and <xref:System.Object?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="a22a5-195">また、構造体型と、これによって実装されるインターフェイスとの間にも、ボックス化とボックス化解除の変換が存在します。</span><span class="sxs-lookup"><span data-stu-id="a22a5-195">There exist also boxing and unboxing conversions between a structure type and any interface that it implements.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a22a5-196">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a22a5-196">C# language specification</span></span>

<span data-ttu-id="a22a5-197">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[構造体](~/_csharplang/spec/structs.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22a5-197">For more information, see the [Structs](~/_csharplang/spec/structs.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="a22a5-198">C# 7.2 以降で導入された機能の詳細については、次の機能の提案に関するメモを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22a5-198">For more information about features introduced in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="a22a5-199">Readonly 構造体</span><span class="sxs-lookup"><span data-stu-id="a22a5-199">Readonly structs</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [<span data-ttu-id="a22a5-200">Readonly インスタンスのメンバー</span><span class="sxs-lookup"><span data-stu-id="a22a5-200">Readonly instance members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [<span data-ttu-id="a22a5-201">ref-like 型のコンパイル時の安全性</span><span class="sxs-lookup"><span data-stu-id="a22a5-201">Compile-time safety for ref-like types</span></span>](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a><span data-ttu-id="a22a5-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="a22a5-202">See also</span></span>

- [<span data-ttu-id="a22a5-203">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a22a5-203">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a22a5-204">デザインのガイドライン - クラスまたは構造体の選択</span><span class="sxs-lookup"><span data-stu-id="a22a5-204">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="a22a5-205">デザインのガイドライン - 構造体のデザイン</span><span class="sxs-lookup"><span data-stu-id="a22a5-205">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="a22a5-206">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="a22a5-206">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
