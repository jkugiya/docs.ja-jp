---
title: インデックスと範囲を使用してデータの範囲を調べる
description: この詳細なチュートリアルでは、一連の連続するデータ セットの範囲を、インデックスと範囲を使用して調べる方法について説明します。
ms.date: 09/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: c0484a42233466e3a2a70a673aee81fce91fe31b
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585404"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="771a6-103">インデックスと範囲</span><span class="sxs-lookup"><span data-stu-id="771a6-103">Indices and ranges</span></span>

<span data-ttu-id="771a6-104">範囲とインデックスには、シーケンス内の 1 つの要素または範囲にアクセスできる簡潔な構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="771a6-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="771a6-105">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="771a6-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="771a6-106">シーケンス内の範囲に構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="771a6-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="771a6-107">各シーケンスの開始と終了に関する設計上の決定について説明します。</span><span class="sxs-lookup"><span data-stu-id="771a6-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="771a6-108"><xref:System.Index> 型と <xref:System.Range> 型のシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="771a6-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="771a6-109">インデックスと範囲の言語サポート</span><span class="sxs-lookup"><span data-stu-id="771a6-109">Language support for indices and ranges</span></span>

<span data-ttu-id="771a6-110">この言語のサポートでは、次の 2 つの新しい型と 2 つの新しい演算子が使用されています。</span><span class="sxs-lookup"><span data-stu-id="771a6-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="771a6-111"><xref:System.Index?displayProperty=nameWithType> はシーケンスとしてインデックスを表します。</span><span class="sxs-lookup"><span data-stu-id="771a6-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="771a6-112">index from end 演算子の `^`。シーケンスの末尾から相対的なインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="771a6-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="771a6-113"><xref:System.Range?displayProperty=nameWithType> はシーケンスのサブ範囲を表します。</span><span class="sxs-lookup"><span data-stu-id="771a6-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="771a6-114">範囲演算子の `..`。範囲の先頭と末尾をそのオペランドとして指定します。</span><span class="sxs-lookup"><span data-stu-id="771a6-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="771a6-115">インデックスのルールから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="771a6-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="771a6-116">配列 `sequence` を考えます。</span><span class="sxs-lookup"><span data-stu-id="771a6-116">Consider an array `sequence`.</span></span> <span data-ttu-id="771a6-117">`0` インデックスは `sequence[0]` と同じです。</span><span class="sxs-lookup"><span data-stu-id="771a6-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="771a6-118">`^0` インデックスは `sequence[sequence.Length]` と同じです。</span><span class="sxs-lookup"><span data-stu-id="771a6-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="771a6-119">`sequence[^0]` 式からは、`sequence[sequence.Length]` の場合と同様に、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="771a6-119">The expression `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="771a6-120">任意の数値 `n` の場合、インデックス `^n` は `sequence[sequence.Length - n]` と同じです。</span><span class="sxs-lookup"><span data-stu-id="771a6-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="771a6-121">末尾の単語は `^1` インデックスで取得できます。</span><span class="sxs-lookup"><span data-stu-id="771a6-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="771a6-122">初期化の下に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="771a6-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="771a6-123">範囲は、範囲の *先頭* と *末尾* を指定します。</span><span class="sxs-lookup"><span data-stu-id="771a6-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="771a6-124">範囲は排他的です。つまり、"*末尾*" は範囲に含まれません。</span><span class="sxs-lookup"><span data-stu-id="771a6-124">Ranges are exclusive, meaning the *end* isn't included in the range.</span></span> <span data-ttu-id="771a6-125">範囲 `[0..^0]` は、`[0..sequence.Length]` が範囲全体を表すのと同じように、範囲全体を表します。</span><span class="sxs-lookup"><span data-stu-id="771a6-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="771a6-126">次のコードでは、単語 "quick"、"brown"、"fox" から成る部分範囲が作成されます。</span><span class="sxs-lookup"><span data-stu-id="771a6-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="771a6-127">それには、`words[1]` から `words[3]` までが含まれます。</span><span class="sxs-lookup"><span data-stu-id="771a6-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="771a6-128">要素 `words[4]` が範囲内にありません。</span><span class="sxs-lookup"><span data-stu-id="771a6-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="771a6-129">同じメソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="771a6-129">Add the following code to the same method.</span></span> <span data-ttu-id="771a6-130">それをコピーして、対話型ウィンドウの下部に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="771a6-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="771a6-131">次のコードでは、"lazy" と "dog" の範囲が返されます。</span><span class="sxs-lookup"><span data-stu-id="771a6-131">The following code returns the range with "lazy" and "dog".</span></span> <span data-ttu-id="771a6-132">それには、`words[^2]` と `words[^1]` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="771a6-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="771a6-133">末尾インデックス `words[^0]` は含まれません。</span><span class="sxs-lookup"><span data-stu-id="771a6-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="771a6-134">次のコードも追加します。</span><span class="sxs-lookup"><span data-stu-id="771a6-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="771a6-135">次の例では、先頭と末尾の一方または両方が開いている範囲が作成されます。</span><span class="sxs-lookup"><span data-stu-id="771a6-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="771a6-136">範囲やインデックスを変数として宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="771a6-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="771a6-137">この変数は、文字 `[` と `]` の内側で使用できます。</span><span class="sxs-lookup"><span data-stu-id="771a6-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="771a6-138">次のサンプルは、こうした選択肢の理由の多くを示しています。</span><span class="sxs-lookup"><span data-stu-id="771a6-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="771a6-139">`x`、`y`、`z` を変更してさまざまな組み合わせを試してください。</span><span class="sxs-lookup"><span data-stu-id="771a6-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="771a6-140">実験するときには、有効な組み合わせになるように `x` が `y` 未満の値、`y` が `z` 未満の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="771a6-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="771a6-141">新しいメソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="771a6-141">Add the following code in a new method.</span></span> <span data-ttu-id="771a6-142">さまざまな組み合わせを試してください。</span><span class="sxs-lookup"><span data-stu-id="771a6-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="771a6-143">インデックスと範囲の型のサポート</span><span class="sxs-lookup"><span data-stu-id="771a6-143">Type support for indices and ranges</span></span>

<span data-ttu-id="771a6-144">インデックスと範囲を使用すると、シーケンス内の 1 つの要素または要素の範囲にアクセスする構文を明確かつ簡潔に指定できます。</span><span class="sxs-lookup"><span data-stu-id="771a6-144">Indexes and ranges provide clear, concise syntax to access a single element or a range of elements in a sequence.</span></span> <span data-ttu-id="771a6-145">インデックス式は、一般的に、シーケンスの要素の型を返します。</span><span class="sxs-lookup"><span data-stu-id="771a6-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="771a6-146">範囲式は、一般的に、ソース シーケンスと同じシーケンス型を返します。</span><span class="sxs-lookup"><span data-stu-id="771a6-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="771a6-147"><xref:System.Index> または <xref:System.Range> パラメーターを持つ[インデクサー](../programming-guide/indexers/index.md)が用意されている型では、インデックスまたは範囲がそれぞれ明示的にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="771a6-147">Any type that provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="771a6-148">1 つの <xref:System.Range> パラメーターをとるインデクサーからは、<xref:System.Span%601?displayProperty=nameWithType> などの別のシーケンス型が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="771a6-148">An indexer that takes a single <xref:System.Range> parameter may return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="771a6-149">範囲演算子を使用したコードのパフォーマンスは、シーケンス オペランドの型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="771a6-149">The performance of code using the range operator depends on the type of the sequence operand.</span></span>
>
> <span data-ttu-id="771a6-150">範囲演算子の時間計算量は、シーケンスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="771a6-150">The time complexity of the range operator depends on the sequence type.</span></span> <span data-ttu-id="771a6-151">たとえば、シーケンスが `string` または配列の場合、指定したセクションの入力のコピーが結果として返されるため、時間計算量は *O(N)* になります (ここで N は範囲の長さです)。</span><span class="sxs-lookup"><span data-stu-id="771a6-151">For example, if the sequence is a `string` or an array, then the result is a copy of the specified section of the input, so the time complexity is *O(N)* (where N is the length of the range).</span></span> <span data-ttu-id="771a6-152">一方、<xref:System.Span%601?displayProperty=nameWithType> または <xref:System.Memory%601?displayProperty=nameWithType> の場合、結果で同じバッキング ストアが参照されます。つまり、コピーは行われず、操作は *O(1)* になります。</span><span class="sxs-lookup"><span data-stu-id="771a6-152">On the other hand, if it's a <xref:System.Span%601?displayProperty=nameWithType> or a <xref:System.Memory%601?displayProperty=nameWithType>, the result references the same backing store, which means there is no copy and the operation is *O(1)*.</span></span>
>
> <span data-ttu-id="771a6-153">これでは時間計算量以外に、パフォーマンスに影響する割り当てとコピーも追加で発生します。</span><span class="sxs-lookup"><span data-stu-id="771a6-153">In addition to the time complexity, this causes extra allocations and copies, impacting performance.</span></span> <span data-ttu-id="771a6-154">パフォーマンスが重視されるコードでは、シーケンス型として範囲演算子が割り当てられない `Span<T>` または `Memory<T>` を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="771a6-154">In performance sensitive code, consider using `Span<T>` or `Memory<T>` as the sequence type, since the range operator does not allocate for them.</span></span>

<span data-ttu-id="771a6-155">アクセス可能なゲッターと戻り値の型 `int` を持つ `Length` または `Count` という名前のプロパティがある場合、型は **可算** です。</span><span class="sxs-lookup"><span data-stu-id="771a6-155">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="771a6-156">インデックスまたは範囲を明示的にサポートしていない可算型は、それらを暗黙的にサポートしている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="771a6-156">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="771a6-157">詳細については、[機能の提案に関する注記](~/_csharplang/proposals/csharp-8.0/ranges.md)の「[暗黙的なインデックスのサポート](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support)」と「[暗黙的な範囲のサポート](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="771a6-157">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="771a6-158">暗黙的な範囲のサポートを使用している範囲によって返されるのは、ソース シーケンスと同じシーケンス型です。</span><span class="sxs-lookup"><span data-stu-id="771a6-158">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="771a6-159">たとえば、次の .NET 型ではインデックスと範囲の両方がサポートされています: <xref:System.String>、<xref:System.Span%601>、および <xref:System.ReadOnlySpan%601>。</span><span class="sxs-lookup"><span data-stu-id="771a6-159">For example, the following .NET types support both indices and ranges: <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="771a6-160"><xref:System.Collections.Generic.List%601> はインデックスをサポートしていますが、範囲はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="771a6-160">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

<span data-ttu-id="771a6-161"><xref:System.Array> には、より微妙な動作があります。</span><span class="sxs-lookup"><span data-stu-id="771a6-161"><xref:System.Array> has more nuanced behavior.</span></span> <span data-ttu-id="771a6-162">1 次元配列では、インデックスと範囲の両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="771a6-162">Single dimension arrays support both indices and ranges.</span></span> <span data-ttu-id="771a6-163">多次元配列では、インデクサーまたは範囲はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="771a6-163">Multi-dimensional arrays don't support indexers or ranges.</span></span> <span data-ttu-id="771a6-164">多次元配列のインデクサーには、1 つのパラメーターではなく、複数のパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="771a6-164">The indexer for a multi-dimensional array has multiple parameters, not a single parameter.</span></span> <span data-ttu-id="771a6-165">配列の配列とも呼ばれるジャグ配列では、範囲とインデクサーの両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="771a6-165">Jagged arrays, also referred to as an array of arrays, support both ranges and indexers.</span></span> <span data-ttu-id="771a6-166">次の例では、ジャグ配列の四角形サブセクションを反復処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="771a6-166">The following example shows how to iterate a rectangular subsection of a jagged array.</span></span> <span data-ttu-id="771a6-167">最初と最後の 3 つの行と、選択された各行の最初と最後の 2 つの列を除いて、中央のセクションが反復処理されます。</span><span class="sxs-lookup"><span data-stu-id="771a6-167">It iterates the section in the center, excluding the first and last three rows, and the first and last two columns from each selected row:</span></span>

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

<span data-ttu-id="771a6-168">いずれの場合も、<xref:System.Array> の範囲演算子では、返される要素を格納する配列が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="771a6-168">In all cases, the range operator for <xref:System.Array> allocates an array to store the elements returned.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="771a6-169">インデックスと範囲のシナリオ</span><span class="sxs-lookup"><span data-stu-id="771a6-169">Scenarios for indices and ranges</span></span>

<span data-ttu-id="771a6-170">長いシーケンスの部分を分析するときは、多くの場合、範囲とインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="771a6-170">You'll often use ranges and indices when you want to analyze a portion of a larger sequence.</span></span> <span data-ttu-id="771a6-171">新しい構文では、シーケンスのどの部分が関係しているかをより正確に読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="771a6-171">The new syntax is clearer in reading exactly what portion of the sequence is involved.</span></span> <span data-ttu-id="771a6-172">ローカル関数 `MovingAverage` は、引数として <xref:System.Range> を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="771a6-172">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="771a6-173">このメソッドでは、最小値、最大値、および平均値を計算するときに、その範囲のみが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="771a6-173">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="771a6-174">プロジェクトで次のコードを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="771a6-174">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
