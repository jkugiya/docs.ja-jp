---
title: 制約
description: ジェネリック型パラメーターに適用して、ジェネリック型または関数の型引数の要件を指定する F# の制約について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425015"
---
# <a name="constraints"></a><span data-ttu-id="87cf6-103">制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-103">Constraints</span></span>

<span data-ttu-id="87cf6-104">このトピックでは、ジェネリック型パラメーターに適用して、ジェネリック型または関数内の型引数の要件を指定できる制約について説明します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="87cf6-105">構文</span><span class="sxs-lookup"><span data-stu-id="87cf6-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="87cf6-106">解説</span><span class="sxs-lookup"><span data-stu-id="87cf6-106">Remarks</span></span>

<span data-ttu-id="87cf6-107">ジェネリック型で使用できる型を制限するために適用できる、いくつかの異なる制約があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="87cf6-108">次の表に、これらの制約の一覧とその説明を示します。</span><span class="sxs-lookup"><span data-stu-id="87cf6-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="87cf6-109">制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-109">Constraint</span></span>|<span data-ttu-id="87cf6-110">構文</span><span class="sxs-lookup"><span data-stu-id="87cf6-110">Syntax</span></span>|<span data-ttu-id="87cf6-111">説明</span><span class="sxs-lookup"><span data-stu-id="87cf6-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="87cf6-112">型制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-112">Type Constraint</span></span>|<span data-ttu-id="87cf6-113">*type-parameter* :&gt; *type*</span><span class="sxs-lookup"><span data-stu-id="87cf6-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="87cf6-114">規定される型は、指定する型と同じか、またはそれから派生したものである必要があります。または、型がインターフェイスの場合、規定される型ではそのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="87cf6-115">Null 制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-115">Null Constraint</span></span>|<span data-ttu-id="87cf6-116">*type-parameter* : null</span><span class="sxs-lookup"><span data-stu-id="87cf6-116">*type-parameter* : null</span></span>|<span data-ttu-id="87cf6-117">規定される型では、NULL リテラルがサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-117">The provided type must support the null literal.</span></span> <span data-ttu-id="87cf6-118">これには、すべての .NET オブジェクト型が含まれます。ただし、F# リスト、タプル、関数、クラス、レコード、共用体型は除きます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="87cf6-119">明示的なメンバー制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-119">Explicit Member Constraint</span></span>|<span data-ttu-id="87cf6-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span><span class="sxs-lookup"><span data-stu-id="87cf6-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="87cf6-121">規定される型引数の少なくとも 1 つに、指定するシグネチャを持つメンバーが必要です。一般的な使用を目的としたものではありません。</span><span class="sxs-lookup"><span data-stu-id="87cf6-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="87cf6-122">メンバーは、明示的なメンバー制約のターゲットとして有効であるために、型に明示的に定義されているか、暗黙的な型拡張の一部でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="87cf6-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="87cf6-123">コンストラクターの制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-123">Constructor Constraint</span></span>|<span data-ttu-id="87cf6-124">*type-parameter* : ( new : unit -&gt; 'a )</span><span class="sxs-lookup"><span data-stu-id="87cf6-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="87cf6-125">規定される型には、パラメーターなしのコンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="87cf6-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="87cf6-126">値の型の制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-126">Value Type Constraint</span></span>|<span data-ttu-id="87cf6-127">: struct</span><span class="sxs-lookup"><span data-stu-id="87cf6-127">: struct</span></span>|<span data-ttu-id="87cf6-128">規定される型は、.NET の値の型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="87cf6-129">参照型の制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-129">Reference Type Constraint</span></span>|<span data-ttu-id="87cf6-130">: not struct</span><span class="sxs-lookup"><span data-stu-id="87cf6-130">: not struct</span></span>|<span data-ttu-id="87cf6-131">規定される型は、.NET の参照型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="87cf6-132">列挙型の制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="87cf6-133">: enum&lt;*underlying-type*&gt;</span><span class="sxs-lookup"><span data-stu-id="87cf6-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="87cf6-134">規定される型は、指定された基になる型を持つ列挙型である必要があります。一般的な使用を目的としたものではありません。</span><span class="sxs-lookup"><span data-stu-id="87cf6-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="87cf6-135">デリゲート制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-135">Delegate Constraint</span></span>|<span data-ttu-id="87cf6-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span><span class="sxs-lookup"><span data-stu-id="87cf6-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="87cf6-137">規定される型は、指定された引数と戻り値を持つデリゲート型である必要があります。一般的な使用を目的としたものではありません。</span><span class="sxs-lookup"><span data-stu-id="87cf6-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="87cf6-138">比較制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-138">Comparison Constraint</span></span>|<span data-ttu-id="87cf6-139">: comparison</span><span class="sxs-lookup"><span data-stu-id="87cf6-139">: comparison</span></span>|<span data-ttu-id="87cf6-140">規定される型では、比較がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="87cf6-141">等値制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-141">Equality Constraint</span></span>|<span data-ttu-id="87cf6-142">: equality</span><span class="sxs-lookup"><span data-stu-id="87cf6-142">: equality</span></span>|<span data-ttu-id="87cf6-143">規定される型では、等値がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="87cf6-144">アンマネージド制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-144">Unmanaged Constraint</span></span>|<span data-ttu-id="87cf6-145">: unmanaged</span><span class="sxs-lookup"><span data-stu-id="87cf6-145">: unmanaged</span></span>|<span data-ttu-id="87cf6-146">規定される型は、アンマネージド型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf6-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="87cf6-147">アンマネージ型とは、特定のプリミティブ型 (`sbyte`、`byte`、`char`、`nativeint`、`unativeint`、`float32`、`float`、`int16`、`uint16`、`int32`、`uint32`、`int64`、`uint64`、または `decimal`)、列挙型、`nativeptr<_>`、またはフィールドがすべてアンマネージ型である非ジェネリック構造体のことです。</span><span class="sxs-lookup"><span data-stu-id="87cf6-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="87cf6-148">制約を追加する必要があるのは、制約型の上では使用できても、型一般の上では使用できない機能をコードで使用する必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="87cf6-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="87cf6-149">たとえば、型制約を使用してクラス型を指定する場合は、ジェネリック関数または型で、そのクラスの任意のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="87cf6-150">型パラメーターを明示的に記述するときに制約の指定が必要になることがあります。制約がないと、コンパイラには、使用しようとしている機能が、実行時に型パラメーターに提供される可能性のあるすべての型で利用できることを確認する方法がないためです。</span><span class="sxs-lookup"><span data-stu-id="87cf6-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="87cf6-151">F# コードで使用する最も一般的な制約は、基底クラスまたはインターフェイスを指定する型制約です。</span><span class="sxs-lookup"><span data-stu-id="87cf6-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="87cf6-152">他の制約は、算術演算子の演算子のオーバーロードを実装するために使用される明示的なメンバー制約など、特定の機能を実装するために F# ライブラリによって使用されるか、共通言語ランタイムによってサポートされている制約一式が F# でサポートされているということが主な理由で提供されているかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="87cf6-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="87cf6-153">型の推定プロセスでは、一部の制約がコンパイラによって自動的に推定されます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="87cf6-154">たとえば、関数で `+` 演算子を使用する場合、コンパイラでは、式で使用されている変数型に対する明示的なメンバー制約が推定されます。</span><span class="sxs-lookup"><span data-stu-id="87cf6-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="87cf6-155">次のコードでは、いくつかの制約宣言を示しています。</span><span class="sxs-lookup"><span data-stu-id="87cf6-155">The following code illustrates some constraint declarations:</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> =
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="87cf6-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="87cf6-156">See also</span></span>

- [<span data-ttu-id="87cf6-157">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="87cf6-157">Generics</span></span>](index.md)
- [<span data-ttu-id="87cf6-158">制約</span><span class="sxs-lookup"><span data-stu-id="87cf6-158">Constraints</span></span>](constraints.md)
