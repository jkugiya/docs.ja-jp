---
description: '詳細情報: .NET でのバッファーの使用'
title: System.Buffers - .NET
ms.date: 12/05/2019
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 988ac5cae192b815ccac74f1bf15055538244bda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782430"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="73579-103">.NET でのバッファーの使用</span><span class="sxs-lookup"><span data-stu-id="73579-103">Work with Buffers in .NET</span></span>

<span data-ttu-id="73579-104">この記事では、複数のバッファーで実行されるデータの読み取りに役立つ型の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="73579-104">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="73579-105">これらは主に、<xref:System.IO.Pipelines.PipeReader> オブジェクトをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="73579-105">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="73579-106">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="73579-106">IBufferWriter\<T\></span></span>

<span data-ttu-id="73579-107"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> は、バッファーの同期を行う書き込みのためのコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="73579-107"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="73579-108">最下位レベルでは、インターフェイスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="73579-108">At the lowest level, the interface:</span></span>

- <span data-ttu-id="73579-109">基本的で、簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="73579-109">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="73579-110"><xref:System.Memory%601> または <xref:System.Span%601> へのアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="73579-110">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="73579-111">`Memory<T>` または `Span<T>` に書き込むことができ、書き込まれた `T` 項目の数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="73579-111">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="73579-112">上記のメソッドでは:</span><span class="sxs-lookup"><span data-stu-id="73579-112">The preceding method:</span></span>

- <span data-ttu-id="73579-113">`GetSpan(5)` を使用して、`IBufferWriter<byte>` から少なくとも 5 バイトのバッファーを要求します。</span><span class="sxs-lookup"><span data-stu-id="73579-113">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="73579-114">返された `Span<byte>` に、ASCII 文字列 "Hello" のバイトを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="73579-114">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="73579-115"><xref:System.Buffers.IBufferWriter%601> を呼び出して、バッファーに書き込まれたバイト数を示します。</span><span class="sxs-lookup"><span data-stu-id="73579-115">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="73579-116">この書き込みメソッドでは、`IBufferWriter<T>` によって提供される `Memory<T>`/`Span<T>` バッファーが使用されています。</span><span class="sxs-lookup"><span data-stu-id="73579-116">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="73579-117">代わりに、<xref:System.Buffers.BuffersExtensions.Write%2A> 拡張メソッドを使用して既存のバッファーを `IBufferWriter<T>` にコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="73579-117">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="73579-118">`Write` によって、`GetSpan`/`Advance` を呼び出す処理が適切に実行されます。そのため、書き込み後に `Advance` を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="73579-118">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="73579-119"><xref:System.Buffers.ArrayBufferWriter%601> は、バッキング ストアが単一の隣接した配列である `IBufferWriter<T>` の実装です。</span><span class="sxs-lookup"><span data-stu-id="73579-119"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="73579-120">IBufferWriter の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="73579-120">IBufferWriter common problems</span></span>

- <span data-ttu-id="73579-121">`GetSpan` および `GetMemory` では、少なくとも要求された量のメモリを持つバッファーを返します。</span><span class="sxs-lookup"><span data-stu-id="73579-121">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="73579-122">厳密なバッファー サイズを想定しないでください。</span><span class="sxs-lookup"><span data-stu-id="73579-122">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="73579-123">連続する呼び出しで同じバッファーまたは同じサイズのバッファーが返される保証はありません。</span><span class="sxs-lookup"><span data-stu-id="73579-123">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="73579-124">さらにデータの書き込みを続行するには、`Advance` を呼び出した後に新しいバッファーを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73579-124">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="73579-125">`Advance` を呼び出した後に、前に取得したバッファーに書き込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="73579-125">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="73579-126">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="73579-126">ReadOnlySequence\<T\></span></span>

![パイプ内のメモリと、その下に読み取り専用メモリのシーケンス位置を示す ReadOnlySequence](media/buffers/ro-sequence.png)

<span data-ttu-id="73579-128"><xref:System.Buffers.ReadOnlySequence%601> は、`T` の隣接したシーケンス、または隣接しないシーケンスを表すことができる構造体です。</span><span class="sxs-lookup"><span data-stu-id="73579-128"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="73579-129">これは次のものから構築できます。</span><span class="sxs-lookup"><span data-stu-id="73579-129">It can be constructed from:</span></span>

1. <span data-ttu-id="73579-130">`T[]`。</span><span class="sxs-lookup"><span data-stu-id="73579-130">A `T[]`</span></span>
1. <span data-ttu-id="73579-131">`ReadOnlyMemory<T>`。</span><span class="sxs-lookup"><span data-stu-id="73579-131">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="73579-132">リンク リスト ノード <xref:System.Buffers.ReadOnlySequenceSegment%601> と、シーケンスの開始位置および終了位置を表すインデックスのペア。</span><span class="sxs-lookup"><span data-stu-id="73579-132">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="73579-133">最も興味深いのは 3 番目の表現方法です。`ReadOnlySequence<T>` のさまざまな操作に対してパフォーマンスへの影響があるためです。</span><span class="sxs-lookup"><span data-stu-id="73579-133">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="73579-134">表現</span><span class="sxs-lookup"><span data-stu-id="73579-134">Representation</span></span>|<span data-ttu-id="73579-135">操作</span><span class="sxs-lookup"><span data-stu-id="73579-135">Operation</span></span>|<span data-ttu-id="73579-136">複雑さ</span><span class="sxs-lookup"><span data-stu-id="73579-136">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="73579-137">この混合表現のため、`ReadOnlySequence<T>` では整数ではなく `SequencePosition` としてインデックスが公開されます。</span><span class="sxs-lookup"><span data-stu-id="73579-137">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="73579-138">`SequencePosition` は:</span><span class="sxs-lookup"><span data-stu-id="73579-138">A `SequencePosition`:</span></span>

- <span data-ttu-id="73579-139">発生元の `ReadOnlySequence<T>` のインデックスを表す非透過的な値です。</span><span class="sxs-lookup"><span data-stu-id="73579-139">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="73579-140">整数とオブジェクトの 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="73579-140">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="73579-141">これらの 2 つの値によって表されるものは、`ReadOnlySequence<T>` の実装に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="73579-141">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="73579-142">データにアクセスする</span><span class="sxs-lookup"><span data-stu-id="73579-142">Access data</span></span>

<span data-ttu-id="73579-143">`ReadOnlySequence<T>` では、列挙可能な `ReadOnlyMemory<T>` としてデータが公開されます。</span><span class="sxs-lookup"><span data-stu-id="73579-143">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="73579-144">基本的な foreach を使用して、各セグメントの列挙を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="73579-144">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="73579-145">上記のメソッドでは、各セグメントで特定のバイトを検索しています。</span><span class="sxs-lookup"><span data-stu-id="73579-145">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="73579-146">各セグメントの `SequencePosition` を追跡する必要がある場合は、<xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> の方が適しています。</span><span class="sxs-lookup"><span data-stu-id="73579-146">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="73579-147">次のサンプルでは、整数ではなく `SequencePosition` を返すように前のコードを変更しています。</span><span class="sxs-lookup"><span data-stu-id="73579-147">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="73579-148">`SequencePosition` を返すことにより、呼び出し元が特定のインデックスのデータを取得するための 2 回目のスキャンを回避できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="73579-148">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="73579-149">`SequencePosition` と `TryGet` の組み合わせは列挙子のように動作します。</span><span class="sxs-lookup"><span data-stu-id="73579-149">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="73579-150">position フィールドは、各反復の開始時に、`ReadOnlySequence<T>` 内の各セグメントの開始位置に変更されます。</span><span class="sxs-lookup"><span data-stu-id="73579-150">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="73579-151">上記のメソッドは、`ReadOnlySequence<T>` の拡張メソッドとして存在しています。</span><span class="sxs-lookup"><span data-stu-id="73579-151">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="73579-152"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> を使用すると、上記のコードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="73579-152"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="73579-153">ReadOnlySequence\<T\> を処理する</span><span class="sxs-lookup"><span data-stu-id="73579-153">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="73579-154">`ReadOnlySequence<T>` の処理は困難な場合があります。シーケンス内の複数のセグメントにまたがってデータが分割されている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="73579-154">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="73579-155">最適なパフォーマンスを得るには、コードを次の 2 つのパスに分割します。</span><span class="sxs-lookup"><span data-stu-id="73579-155">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="73579-156">単一セグメントのケースを処理する高速パス。</span><span class="sxs-lookup"><span data-stu-id="73579-156">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="73579-157">セグメント間に分割されたデータを処理する低速パス。</span><span class="sxs-lookup"><span data-stu-id="73579-157">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="73579-158">複数のセグメントに分割されたシーケンスのデータを処理するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="73579-158">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="73579-159">[`SequenceReader<T>`](#sequencereadert) を使用する。</span><span class="sxs-lookup"><span data-stu-id="73579-159">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="73579-160">セグメントごとにデータを解析し、解析されたセグメント内の `SequencePosition` とインデックスを追跡する。</span><span class="sxs-lookup"><span data-stu-id="73579-160">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="73579-161">これにより不要な割り当てを回避できますが、非効率的になる可能性があります (特に小さなバッファーの場合)。</span><span class="sxs-lookup"><span data-stu-id="73579-161">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="73579-162">`ReadOnlySequence<T>` を隣接した配列にコピーし、それを 1 つのバッファーとして扱う。</span><span class="sxs-lookup"><span data-stu-id="73579-162">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="73579-163">`ReadOnlySequence<T>` のサイズが小さい場合は、[stackalloc](../../csharp/language-reference/operators/stackalloc.md) 演算子を使用して、スタック割り当てバッファーにデータをコピーすることが適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="73579-163">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="73579-164"><xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> を使用して、プールされた配列に `ReadOnlySequence<T>` をコピーします。</span><span class="sxs-lookup"><span data-stu-id="73579-164">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="73579-165">[`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A) を使用します。</span><span class="sxs-lookup"><span data-stu-id="73579-165">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="73579-166">これは、新しい `T[]` をヒープに割り当てるため、ホット パスでは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="73579-166">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="73579-167">次の例では、`ReadOnlySequence<byte>` を処理する一般的なケースをいくつか示しています。</span><span class="sxs-lookup"><span data-stu-id="73579-167">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="73579-168">バイナリ データの処理</span><span class="sxs-lookup"><span data-stu-id="73579-168">Process binary data</span></span>

<span data-ttu-id="73579-169">次の例では、`ReadOnlySequence<byte>` の先頭から、4 バイトのビッグ エンディアンの整数長を解析しています。</span><span class="sxs-lookup"><span data-stu-id="73579-169">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="73579-170">テキスト データの処理</span><span class="sxs-lookup"><span data-stu-id="73579-170">Process text data</span></span>

<span data-ttu-id="73579-171">次のような例です。</span><span class="sxs-lookup"><span data-stu-id="73579-171">The following example:</span></span>

- <span data-ttu-id="73579-172">`ReadOnlySequence<byte>` 内の最初の改行 (`\r\n`) を検索し、out 'line' パラメーターを使用してそれを返します。</span><span class="sxs-lookup"><span data-stu-id="73579-172">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="73579-173">その line をトリミングし、入力バッファーから `\r\n` を除外します。</span><span class="sxs-lookup"><span data-stu-id="73579-173">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="73579-174">空のセグメント</span><span class="sxs-lookup"><span data-stu-id="73579-174">Empty segments</span></span>

<span data-ttu-id="73579-175">`ReadOnlySequence<T>` 内に空のセグメントを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="73579-175">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="73579-176">セグメントを明示的に列挙するときに、空のセグメントが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73579-176">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="73579-177">上記のコードでは、空のセグメントを持つ `ReadOnlySequence<byte>` を作成し、それらの空のセグメントがさまざまな API にどのような影響を与えるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="73579-177">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="73579-178">空のセグメントを指す `SequencePosition` を使用した `ReadOnlySequence<T>.Slice` では、そのセグメントが保持されます。</span><span class="sxs-lookup"><span data-stu-id="73579-178">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="73579-179">int を使用した `ReadOnlySequence<T>.Slice` では、空のセグメントがスキップされます。</span><span class="sxs-lookup"><span data-stu-id="73579-179">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="73579-180">`ReadOnlySequence<T>` を列挙すると、空のセグメントが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="73579-180">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="73579-181">ReadOnlySequence\<T> と SequencePosition に関する潜在的な問題</span><span class="sxs-lookup"><span data-stu-id="73579-181">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="73579-182">`ReadOnlySequence<T>`/`SequencePosition` を扱うときには、通常の `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int` に対して、いくつかの通常とは異なる結果が発生します。</span><span class="sxs-lookup"><span data-stu-id="73579-182">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="73579-183">`SequencePosition` は特定の `ReadOnlySequence<T>` の位置マーカーであり、絶対位置ではありません。</span><span class="sxs-lookup"><span data-stu-id="73579-183">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="73579-184">これは特定の `ReadOnlySequence<T>` を基準にするため、発生元の `ReadOnlySequence<T>` の外部で使用されても意味がありません。</span><span class="sxs-lookup"><span data-stu-id="73579-184">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="73579-185">`ReadOnlySequence<T>` を使用せずに `SequencePosition` に対する算術演算を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="73579-185">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="73579-186">つまり、`position++` などの基本的な処理は、`ReadOnlySequence<T>.GetPosition(position, 1)` のように記述されます。</span><span class="sxs-lookup"><span data-stu-id="73579-186">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="73579-187">`GetPosition(long)` では、負のインデックスがサポートされて **いません**。</span><span class="sxs-lookup"><span data-stu-id="73579-187">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="73579-188">つまり、すべてのセグメントをたどることなく最後から 2 番目の文字を取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="73579-188">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="73579-189">2 つの `SequencePosition` を比較できないため、次のことが困難になります。</span><span class="sxs-lookup"><span data-stu-id="73579-189">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="73579-190">ある位置が別の位置より大きいか小さいかを確認する。</span><span class="sxs-lookup"><span data-stu-id="73579-190">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="73579-191">いくつかの解析アルゴリズムを記述する。</span><span class="sxs-lookup"><span data-stu-id="73579-191">Write some parsing algorithms.</span></span>
- <span data-ttu-id="73579-192">`ReadOnlySequence<T>` はオブジェクト参照よりも大きいため、可能な場合は [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) または [ref](../../csharp/language-reference/keywords/ref.md) によって渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="73579-192">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="73579-193">`in` または `ref` によって `ReadOnlySequence<T>` を渡すことで、[struct](../../csharp/language-reference/builtin-types/struct.md) のコピーを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="73579-193">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="73579-194">空のセグメントは:</span><span class="sxs-lookup"><span data-stu-id="73579-194">Empty segments:</span></span>
  - <span data-ttu-id="73579-195">`ReadOnlySequence<T>` 内で有効です。</span><span class="sxs-lookup"><span data-stu-id="73579-195">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="73579-196">`ReadOnlySequence<T>.TryGet` メソッドを使った反復処理中に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73579-196">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="73579-197">`SequencePosition` オブジェクトと共に `ReadOnlySequence<T>.Slice()` メソッドを使ったシーケンスのスライスで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73579-197">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="73579-198">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="73579-198">SequenceReader\<T\></span></span>

<span data-ttu-id="73579-199"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="73579-199"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="73579-200">`ReadOnlySequence<T>` の処理を簡略化するために .NET Core 3.0 で導入された新しい型です。</span><span class="sxs-lookup"><span data-stu-id="73579-200">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="73579-201">単一セグメントの `ReadOnlySequence<T>` と複数セグメントの `ReadOnlySequence<T>` の違いが統合されます。</span><span class="sxs-lookup"><span data-stu-id="73579-201">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="73579-202">複数のセグメントに分割されている場合でもされていない場合でも、バイナリ データとテキスト データ (`byte` と `char`) を読み取るためのヘルパーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="73579-202">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="73579-203">バイナリ データと区切られたデータの両方を処理するための組み込みメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="73579-203">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="73579-204">以下のセクションでは、これらの同じメソッドが `SequenceReader<T>` でどのように使用されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="73579-204">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="73579-205">データにアクセスする</span><span class="sxs-lookup"><span data-stu-id="73579-205">Access data</span></span>

<span data-ttu-id="73579-206">`SequenceReader<T>` には、`ReadOnlySequence<T>` 内のデータを直接列挙するためのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="73579-206">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="73579-207">次のコードは、一度に `byte` ずつ `ReadOnlySequence<byte>` を処理する例です。</span><span class="sxs-lookup"><span data-stu-id="73579-207">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="73579-208">`CurrentSpan` を使用すると、現在のセグメントの `Span` が公開されます。これは、このメソッド内で手動で行われたことに似ています。</span><span class="sxs-lookup"><span data-stu-id="73579-208">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="73579-209">位置の使用</span><span class="sxs-lookup"><span data-stu-id="73579-209">Use position</span></span>

<span data-ttu-id="73579-210">次のコードでは、`SequenceReader<T>` を使った `FindIndexOf` の実装例を示します。</span><span class="sxs-lookup"><span data-stu-id="73579-210">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="73579-211">バイナリ データの処理</span><span class="sxs-lookup"><span data-stu-id="73579-211">Process binary data</span></span>

<span data-ttu-id="73579-212">次の例では、`ReadOnlySequence<byte>` の先頭から、4 バイトのビッグ エンディアンの整数長を解析しています。</span><span class="sxs-lookup"><span data-stu-id="73579-212">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="73579-213">テキスト データの処理</span><span class="sxs-lookup"><span data-stu-id="73579-213">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="73579-214">SequenceReader\<T\> の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="73579-214">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="73579-215">`SequenceReader<T>` は変更可能な構造体であるため、常に[参照](../../csharp/language-reference/keywords/ref.md)渡しする必要があります。</span><span class="sxs-lookup"><span data-stu-id="73579-215">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="73579-216">`SequenceReader<T>` は [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) であるため、同期メソッド内でのみ使用でき、フィールドに格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="73579-216">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="73579-217">詳細については、「[安全で効率的な C# コードを記述する](../../csharp/write-safe-efficient-code.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="73579-217">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="73579-218">`SequenceReader<T>` は、順方向専用のリーダーとして使用するために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="73579-218">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="73579-219">`Rewind` は、他の `Read`、`Peek`、`IsNext` API を使用しても対処できない小規模なバックアップを目的としています。</span><span class="sxs-lookup"><span data-stu-id="73579-219">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
