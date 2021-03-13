---
title: 匿名型またはタプル型の選択
description: 匿名型またはタプル型を選択する適切なタイミングについて学習します。
author: IEvangelist
ms.author: dapine
ms.topic: conceptual
ms.date: 07/01/2020
ms.openlocfilehash: 1f171851c383862828600f6f43ce1e3fc1b3a168
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693086"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="b43ad-103">匿名型またはタプル型の選択</span><span class="sxs-lookup"><span data-stu-id="b43ad-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="b43ad-104">適切な型を選択するには、他の型と比較し、その使いやすさ、パフォーマンス、およびトレードオフを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="b43ad-105">匿名型は C# 3.0 以降に使用できるようになりましたが、ジェネリック <xref:System.Tuple%602?displayProperty=nameWithType> 型は .NET Framework 4.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="b43ad-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="b43ad-106">その後、<xref:System.ValueTuple%602?displayProperty=nameWithType> など、言語レベルのサポートで新しいオプションが導入されています。これにより、名前が示すように、匿名型の柔軟性を持つ値の型が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="b43ad-107">この記事では、ある型よりもう一方を選択する適切なタイミングについて学習します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="b43ad-108">使いやすさと機能</span><span class="sxs-lookup"><span data-stu-id="b43ad-108">Usability and functionality</span></span>

<span data-ttu-id="b43ad-109">匿名型は、C# 3.0 で統合言語クエリ (LINQ) 式と共に導入されました。</span><span class="sxs-lookup"><span data-stu-id="b43ad-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="b43ad-110">LINQ では、開発者は多くの場合、クエリからの結果を、操作するオブジェクトから選択されたいくつかのプロパティを保持する匿名型に射影します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="b43ad-111"><xref:System.DateTime> オブジェクトの配列をインスタンス化し、2 つのプロパティを持つ匿名型に射影して、それらを反復処理する以下の例について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

<span data-ttu-id="b43ad-112">匿名型は、[`new`](../../csharp/language-reference/operators/new-operator.md) 演算子を使用してインスタンス化され、プロパティの名前と型は宣言から推論されます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="b43ad-113">同じアセンブリ内の複数の匿名オブジェクト初期化子で、同じ順序で同じ名前と型を持つプロパティのシーケンスを指定した場合、コンパイラではそのオブジェクトを同じ型のインスタンスとして処理します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="b43ad-114">これらのオブジェクトは、コンパイラで生成された同一の型情報を共有します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="b43ad-115">前の C# スニペットでは、次のコンパイラによって生成された C# クラスと同様に、2 つのプロパティを持つ匿名型を射影しています。</span><span class="sxs-lookup"><span data-stu-id="b43ad-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

<span data-ttu-id="b43ad-116">詳細については、「[匿名型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b43ad-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="b43ad-117">LINQ クエリに射影する場合、タプルと同じ機能が存在します。プロパティを選択して、タプルにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="b43ad-118">これらのタプルは、匿名型の場合と同様に、クエリを通過します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="b43ad-119">次は、`System.Tuple<string, long>` を使用する以下の例を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

<span data-ttu-id="b43ad-120"><xref:System.Tuple%602?displayProperty=nameWithType> では、インスタンスで `Item1`や `Item2` などの番号付きの項目プロパティが公開されます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="b43ad-121">プロパティ名では序数のみが提供されるため、これらのプロパティ名を使用すると、プロパティ値の意図を理解するのがより難しくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="b43ad-122">さらに、`System.Tuple` 型は参照 `class` 型となります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="b43ad-123">しかし、<xref:System.ValueTuple%602?displayProperty=nameWithType> は `struct` 型の値です。</span><span class="sxs-lookup"><span data-stu-id="b43ad-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="b43ad-124">次の C# スニペットでは、`ValueTuple<string, long>` を使用して射影します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="b43ad-125">この場合、リテラル構文を使用して割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-125">In doing so, it assigns using a literal syntax.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

<span data-ttu-id="b43ad-126">タプルの詳細については、「[タプル型 (C# リファレンス)](../../csharp/language-reference/builtin-types/value-tuples.md)」または「[タプル (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b43ad-126">For more information about tuples, see [Tuple types (C# reference)](../../csharp/language-reference/builtin-types/value-tuples.md) or [Tuples (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md).</span></span>

<span data-ttu-id="b43ad-127">上記の例はすべて機能的には同等ですが、その使いやすさと基盤となる実装にはわずかな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-127">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="b43ad-128">トレードオフ</span><span class="sxs-lookup"><span data-stu-id="b43ad-128">Tradeoffs</span></span>

<span data-ttu-id="b43ad-129"><xref:System.Tuple>、および匿名型より優先して、常に <xref:System.ValueTuple> を使用することはできますが、考慮すべきトレードオフがあります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-129">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="b43ad-130"><xref:System.ValueTuple> 型は変更可能ですが、<xref:System.Tuple> は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="b43ad-130">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="b43ad-131">匿名型は式ツリーで使用できますが、タプルは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b43ad-131">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="b43ad-132">次の表に、主ないくつかの相違点の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-132">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="b43ad-133">主な相違点</span><span class="sxs-lookup"><span data-stu-id="b43ad-133">Key differences</span></span>

| <span data-ttu-id="b43ad-134">名前</span><span class="sxs-lookup"><span data-stu-id="b43ad-134">Name</span></span>                     | <span data-ttu-id="b43ad-135">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="b43ad-135">Access modifier</span></span> | <span data-ttu-id="b43ad-136">種類</span><span class="sxs-lookup"><span data-stu-id="b43ad-136">Type</span></span>     | <span data-ttu-id="b43ad-137">カスタム メンバー名</span><span class="sxs-lookup"><span data-stu-id="b43ad-137">Custom member name</span></span> | <span data-ttu-id="b43ad-138">分解のサポート</span><span class="sxs-lookup"><span data-stu-id="b43ad-138">Deconstruction support</span></span> | <span data-ttu-id="b43ad-139">式ツリーのサポート</span><span class="sxs-lookup"><span data-stu-id="b43ad-139">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="b43ad-140">匿名型</span><span class="sxs-lookup"><span data-stu-id="b43ad-140">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="b43ad-141">✔️</span><span class="sxs-lookup"><span data-stu-id="b43ad-141">✔️</span></span>                   | ❌                     | <span data-ttu-id="b43ad-142">✔️</span><span class="sxs-lookup"><span data-stu-id="b43ad-142">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="b43ad-143">✔️</span><span class="sxs-lookup"><span data-stu-id="b43ad-143">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="b43ad-144">✔️</span><span class="sxs-lookup"><span data-stu-id="b43ad-144">✔️</span></span>                   | <span data-ttu-id="b43ad-145">✔️</span><span class="sxs-lookup"><span data-stu-id="b43ad-145">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="b43ad-146">シリアル化</span><span class="sxs-lookup"><span data-stu-id="b43ad-146">Serialization</span></span>

<span data-ttu-id="b43ad-147">型を選択する際の重要な考慮事項の 1 つは、シリアル化する必要があるかどうかです。</span><span class="sxs-lookup"><span data-stu-id="b43ad-147">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="b43ad-148">シリアル化とは、オブジェクトの状態を永続化または転送できる形式に変換するプロセスのことです。</span><span class="sxs-lookup"><span data-stu-id="b43ad-148">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="b43ad-149">詳細については、[シリアル化](../../csharp/programming-guide/concepts/serialization/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b43ad-149">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="b43ad-150">シリアル化が重要な場合、`class` や `struct` の作成は、匿名型やタプル型よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="b43ad-150">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="b43ad-151">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="b43ad-151">Performance</span></span>

<span data-ttu-id="b43ad-152">これらの型の間のパフォーマンスは、シナリオによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-152">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="b43ad-153">大きな影響は、割り当てとコピーの間のトレードオフに関係します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-153">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="b43ad-154">ほとんどのシナリオでは、影響は小さくなります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-154">In most scenarios, the impact is small.</span></span> <span data-ttu-id="b43ad-155">大きな影響が生じる可能性がある場合は、決定を知らせるために測定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-155">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="b43ad-156">まとめ</span><span class="sxs-lookup"><span data-stu-id="b43ad-156">Conclusion</span></span>

<span data-ttu-id="b43ad-157">開発者がタプル型または匿名型を選択する際に、考慮すべきいくつかの要素があります。</span><span class="sxs-lookup"><span data-stu-id="b43ad-157">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="b43ad-158">一般的には、[式ツリー](../../csharp/expression-trees.md)を操作せず、タプル構文に慣れている場合は、<xref:System.ValueTuple> を選択します。これは、名前プロパティに柔軟性のある値型が提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="b43ad-158">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="b43ad-159">式ツリーを操作し、名前プロパティの方が好ましい場合は、匿名型を選択します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-159">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="b43ad-160">それ以外の場合は、<xref:System.Tuple> を使用します。</span><span class="sxs-lookup"><span data-stu-id="b43ad-160">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b43ad-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="b43ad-161">See also</span></span>

- [<span data-ttu-id="b43ad-162">匿名型</span><span class="sxs-lookup"><span data-stu-id="b43ad-162">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="b43ad-163">式ツリー</span><span class="sxs-lookup"><span data-stu-id="b43ad-163">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="b43ad-164">タプル型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b43ad-164">Tuple types (C# reference)</span></span>](../../csharp/language-reference/builtin-types/value-tuples.md)
- [<span data-ttu-id="b43ad-165">タプル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b43ad-165">Tuples (Visual Basic)</span></span>](../../visual-basic/programming-guide/language-features/data-types/tuples.md)
- [<span data-ttu-id="b43ad-166">型のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b43ad-166">Type design guidelines</span></span>](../design-guidelines/type.md)
