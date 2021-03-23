---
description: where (ジェネリック型制約) - C# リファレンス
title: where (ジェネリック型制約) - C# リファレンス
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
- classconstraint_CSharpKeyword
- structconstraint_CSharpKeyword
- enumconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 83fb5b562d9e1e4caaef179ca2911adb60fc01fa
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872627"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="df815-103">where (ジェネリック型制約) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="df815-103">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="df815-104">ジェネリック定義の `where` 句では、型の制約を指定します。この型は、ジェネリック型、メソッド、デリゲート、またはローカル関数における型パラメーターの引数として使用されます。</span><span class="sxs-lookup"><span data-stu-id="df815-104">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="df815-105">制約では、インターフェイス (基底クラス) を指定したり、参照、値、またはアンマネージド型となるジェネリック型を要求したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="df815-105">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value, or unmanaged type.</span></span> <span data-ttu-id="df815-106">それらにより型引数が処理する必要がある機能が宣言されえます。</span><span class="sxs-lookup"><span data-stu-id="df815-106">They declare capabilities that the type argument must have.</span></span>

<span data-ttu-id="df815-107">たとえば、型パラメーター `T` が <xref:System.IComparable%601> インターフェイスを実装するように、次のように `AGenericClass` ジェネリック クラスを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="df815-107">For example, you can declare a generic class, `AGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="df815-108">クエリ式での where 句の詳細については、「[where 句](where-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df815-108">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="df815-109">`where` 句には基底クラスの制約を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="df815-109">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="df815-110">基底クラスの制約は、そのジェネリック型の型引数として使用される型が、指定されたクラスを基底クラスとして持つか、その基底クラスであることを示しています。</span><span class="sxs-lookup"><span data-stu-id="df815-110">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class, or is that base class.</span></span> <span data-ttu-id="df815-111">基底クラスの制約を使用する場合は、型パラメーターに関する制約よりも前に制約を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df815-111">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="df815-112">一部の型は、基底クラスの制約として許可されません (<xref:System.Object>、<xref:System.Array>、<xref:System.ValueType>)。</span><span class="sxs-lookup"><span data-stu-id="df815-112">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="df815-113">C# 7.3 より前は、<xref:System.Enum>、<xref:System.Delegate>、<xref:System.MulticastDelegate> も基底クラスの制約として許可されていません。</span><span class="sxs-lookup"><span data-stu-id="df815-113">Before C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="df815-114">次の例では、この型は基底クラスとして指定できるようになったことを示しています。</span><span class="sxs-lookup"><span data-stu-id="df815-114">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#2)]

<span data-ttu-id="df815-115">C# 8.0 以降の null 許容コンテキストでは、基本クラス型の null 許容属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="df815-115">In a nullable context in C# 8.0 and later, the nullability of the base class type is enforced.</span></span> <span data-ttu-id="df815-116">基底クラスが null 非許容の場合 (たとえば、`Base`)、型引数は null 非許容である必要があります。</span><span class="sxs-lookup"><span data-stu-id="df815-116">If the base class is non-nullable (for example `Base`), the type argument must be non-nullable.</span></span> <span data-ttu-id="df815-117">基底クラスが null 許容の場合 (`Base?` など)、型引数は null 許容型または null 非許容型のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="df815-117">If the base class is nullable (for example `Base?`), the type argument may be either a nullable or non-nullable reference type.</span></span> <span data-ttu-id="df815-118">基底クラスが null 非許容であるときに、型引数が null 許容の参照型である場合、コンパイラからは警告を発行されます。</span><span class="sxs-lookup"><span data-stu-id="df815-118">The compiler issues a warning if the type argument is a nullable reference type when the base class is non-nullable.</span></span>

<span data-ttu-id="df815-119">`where` 句では、型が `class` または `struct` であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="df815-119">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="df815-120">`struct` 制約では、`System.ValueType` の基底クラスの制約を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="df815-120">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="df815-121">`System.ValueType` 型は基底クラスの制約として使用できません。</span><span class="sxs-lookup"><span data-stu-id="df815-121">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="df815-122">`class` 制約と `struct` 制約の両方の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="df815-122">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#3)]

<span data-ttu-id="df815-123">C# 8.0 以降の null 許容コンテキストでは、`class` 制約には、型が null 非許容の参照型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="df815-123">In a nullable context in C# 8.0 and later, the `class` constraint requires a type to be a non-nullable reference type.</span></span> <span data-ttu-id="df815-124">null 許容の参照型を許可するには、`class?` 制約を使用して、null 許容と null 非許容の参照型の両方を許可します。</span><span class="sxs-lookup"><span data-stu-id="df815-124">To allow nullable reference types, use the `class?` constraint, which allows both nullable and non-nullable reference types.</span></span>

<span data-ttu-id="df815-125">`where` 句には、`notnull` 制約を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="df815-125">The `where` clause may include the `notnull` constraint.</span></span> <span data-ttu-id="df815-126">`notnull` 制約では、型パラメーターを null 非許容型に制限します。</span><span class="sxs-lookup"><span data-stu-id="df815-126">The `notnull` constraint limits the type parameter to non-nullable types.</span></span> <span data-ttu-id="df815-127">その型には、[値型](../builtin-types/value-types.md)または null 非許容参照型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="df815-127">That type may be a [value type](../builtin-types/value-types.md) or a non-nullable reference type.</span></span> <span data-ttu-id="df815-128">`notnull` 制約は、C# 8.0 以降の [`nullable enable` コンテキスト](../../nullable-references.md#nullable-contexts)でコンパイルされたコードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="df815-128">The `notnull` constraint is available starting in C# 8.0 for code compiled in a [`nullable enable` context](../../nullable-references.md#nullable-contexts).</span></span> <span data-ttu-id="df815-129">他の制約とは異なり、型引数が `notnull` 制約に違反すると、コンパイラによりエラーではなく警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="df815-129">Unlike other constraints, if a type argument violates the `notnull` constraint, the compiler generates a warning instead of an error.</span></span> <span data-ttu-id="df815-130">警告は、`nullable enable` コンテキストでのみ生成されます。</span><span class="sxs-lookup"><span data-stu-id="df815-130">Warnings are only generated in a `nullable enable` context.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df815-131">`notnull` 制約が含まれるジェネリック宣言は、null 許容が未指定のコンテキストで使用できますが、コンパイラではその制約は強制されません。</span><span class="sxs-lookup"><span data-stu-id="df815-131">Generic declarations that include the `notnull` constraint can be used in a nullable oblivious context, but compiler does not enforce the constraint.</span></span>

[!code-csharp[using the nonnull constraint](snippets/GenericWhereConstraints.cs#NotNull)]

<span data-ttu-id="df815-132">`where` 句には、`unmanaged` 制約を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="df815-132">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="df815-133">`unmanaged` 制約では、[アンマネージド型](../builtin-types/unmanaged-types.md)と呼ばれる型に対して型パラメーターを制限します。</span><span class="sxs-lookup"><span data-stu-id="df815-133">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="df815-134">`unmanaged` 制約を使用すると、C# でローレベルの相互運用コードを記述しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="df815-134">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="df815-135">この制約では、すべてのアンマネージド型にわたって再利用可能なルーチンを可能にします。</span><span class="sxs-lookup"><span data-stu-id="df815-135">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="df815-136">`unmanaged` 制約は、`class` や `struct` 制約と組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="df815-136">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="df815-137">`unmanaged` 制約は `struct` にする必要がある型を適用します。</span><span class="sxs-lookup"><span data-stu-id="df815-137">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#4)]

<span data-ttu-id="df815-138">`where` 句には、コンストラクター制約 `new()` を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="df815-138">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="df815-139">その制約では、`new` 演算子を使用して型パラメーターのインスタンスを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="df815-139">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="df815-140">[new() 制約](new-constraint.md)に基づいて、コンパイラで、指定されている型引数にはアクセス可能なパラメーターなしのコンストラクターが必要であることが認識されます。</span><span class="sxs-lookup"><span data-stu-id="df815-140">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless constructor.</span></span> <span data-ttu-id="df815-141">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="df815-141">For example:</span></span>

[!code-csharp[using the new constraint](snippets/GenericWhereConstraints.cs#5)]

<span data-ttu-id="df815-142">`new()` 制約は `where` 句の最後に示されます。</span><span class="sxs-lookup"><span data-stu-id="df815-142">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="df815-143">`new()` 制約は、`struct` や `unmanaged` 制約と組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="df815-143">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="df815-144">それらの制約を満たすすべての型には、`new()` 制約を重複させて、アクセス可能なパラメーターなしのコンストラクターが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="df815-144">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="df815-145">複数の型パラメーターがある場合には、型パラメーターごとに `where` 句を 1 つずつ使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="df815-145">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](snippets/GenericWhereConstraints.cs#6)]

<span data-ttu-id="df815-146">次の例に示すように、ジェネリック メソッドの型パラメーターにも制約を適用できます。</span><span class="sxs-lookup"><span data-stu-id="df815-146">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#7)]

<span data-ttu-id="df815-147">デリゲートに対する型パラメーター制約を記述する構文は、メソッドの構文と同じである点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="df815-147">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#8)]

<span data-ttu-id="df815-148">汎用デリゲートについては、「[汎用デリゲート](../../programming-guide/generics/generic-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df815-148">For information on generic delegates, see [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="df815-149">制約の構文と使用方法の詳細については、「[型パラメーターの制約](../../programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df815-149">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="df815-150">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="df815-150">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="df815-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="df815-151">See also</span></span>

- [<span data-ttu-id="df815-152">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="df815-152">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="df815-153">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="df815-153">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="df815-154">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="df815-154">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
- [<span data-ttu-id="df815-155">new 制約</span><span class="sxs-lookup"><span data-stu-id="df815-155">new Constraint</span></span>](./new-constraint.md)
- [<span data-ttu-id="df815-156">型パラメーターの制約</span><span class="sxs-lookup"><span data-stu-id="df815-156">Constraints on Type Parameters</span></span>](../../programming-guide/generics/constraints-on-type-parameters.md)
