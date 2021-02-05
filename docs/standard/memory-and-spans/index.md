---
title: メモリとスパン
ms.date: 10/03/2018
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: b81531d77bae1dce9d6cf58fe1b5439bf79f9e9c
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506371"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="e64f9-102">メモリおよびスパンに関連する型</span><span class="sxs-lookup"><span data-stu-id="e64f9-102">Memory- and span-related types</span></span>

<span data-ttu-id="e64f9-103">.NET Core 2.1 以降、.NET には、任意のメモリの厳密に型指定された連続する領域を表す、相互に関連する型が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="e64f9-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="e64f9-104">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="e64f9-104">These include:</span></span>

- <span data-ttu-id="e64f9-105"><xref:System.Span%601?displayProperty=nameWithType>: メモリの連続した領域にアクセスするために使う型です。</span><span class="sxs-lookup"><span data-stu-id="e64f9-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="e64f9-106"><xref:System.Span%601> インスタンスは、`T` 型の配列、<xref:System.String>、[stackalloc](../../csharp/language-reference/operators/stackalloc.md) を使って割り当てたバッファー、またはアンマネージ メモリへのポインターによってバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="e64f9-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="e64f9-107">これはスタック上に割り当てる必要があるため、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="e64f9-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="e64f9-108">たとえば、クラス内のフィールドを <xref:System.Span%601> 型にすることはできませんし、非同期操作でスパンを使うこともできません。</span><span class="sxs-lookup"><span data-stu-id="e64f9-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="e64f9-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>: <xref:System.Span%601> 構造体の変更できないバージョンです。</span><span class="sxs-lookup"><span data-stu-id="e64f9-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="e64f9-110"><xref:System.Memory%601?displayProperty=nameWithType>: メモリの隣接した領域に対するラッパーです。</span><span class="sxs-lookup"><span data-stu-id="e64f9-110"><xref:System.Memory%601?displayProperty=nameWithType>, a wrapper over a contiguous region of memory.</span></span> <span data-ttu-id="e64f9-111"><xref:System.Memory%601> インスタンスは、`T` 型の配列、<xref:System.String>、またはメモリ マネージャーによってバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="e64f9-111">A <xref:System.Memory%601> instance can be backed by an array of type `T`, or a <xref:System.String>, or a memory manager.</span></span> <span data-ttu-id="e64f9-112">これはマネージド ヒープに格納できるため、<xref:System.Memory%601> には <xref:System.Span%601> の制限事項はありません。</span><span class="sxs-lookup"><span data-stu-id="e64f9-112">As it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="e64f9-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>: <xref:System.Memory%601> 構造体の変更できないバージョンです。</span><span class="sxs-lookup"><span data-stu-id="e64f9-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="e64f9-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>: メモリ プールの厳密に型指定されたメモリ ブロックを、所有者に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e64f9-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="e64f9-115"><xref:System.Buffers.IMemoryOwner%601> インスタンスは、<xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> を呼び出すことでプールから借りてくることができ、<xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> を呼び出すことでプールにリリースします。</span><span class="sxs-lookup"><span data-stu-id="e64f9-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="e64f9-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>: メモリ ブロックの所有者を表し、その有効期間の管理をコントロールします。</span><span class="sxs-lookup"><span data-stu-id="e64f9-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="e64f9-117"><xref:System.Buffers.MemoryManager%601>: <xref:System.Memory%601> をセーフ ハンドルなどのその他の型でバックアップできるようにするために、<xref:System.Memory%601> の実装を置き換えるために使用できる抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="e64f9-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="e64f9-118"><xref:System.Buffers.MemoryManager%601> は高度なシナリオ向けです。</span><span class="sxs-lookup"><span data-stu-id="e64f9-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="e64f9-119"><xref:System.ArraySegment%601>: 特定のインデックスから始まる、特定の数の配列要素のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="e64f9-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="e64f9-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>: 文字列、配列、および配列セグメントを、<xref:System.Memory%601> ブロックに変換するための拡張メソッドのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="e64f9-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

<span data-ttu-id="e64f9-121"><xref:System.Span%601?displayProperty=nameWithType>、<xref:System.Memory%601?displayProperty=nameWithType>、およびそれらに対応する読み取り専用の型は、必要以上にメモリをコピーしたり、マネージド ヒープに割り当てたりすることのないアルゴリズムを作成できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e64f9-121"><xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Memory%601?displayProperty=nameWithType>, and their readonly counterparts are designed to allow the creation of algorithms that avoid copying memory or allocating on the managed heap more than necessary.</span></span> <span data-ttu-id="e64f9-122">(`Slice` またはそれらのコンストラクターを使用して) それらを作成しても、基になるバッファーの複製は行われません。ラップされたメモリの "ビュー" を表す関連する参照とオフセットのみが更新されます。</span><span class="sxs-lookup"><span data-stu-id="e64f9-122">Creating them (either via `Slice` or their constructors) does not involve duplicating the underlying buffers: only the relevant references and offsets, which represent the "view" of the wrapped memory, are updated.</span></span>

> [!NOTE]
> <span data-ttu-id="e64f9-123">以前のフレームワークでは、[System.Memory NuGet パッケージ](https://www.nuget.org/packages/System.Memory/)で <xref:System.Span%601> と <xref:System.Memory%601> を利用できます。</span><span class="sxs-lookup"><span data-stu-id="e64f9-123">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="e64f9-124">詳細については、「<xref:System.Buffers?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e64f9-124">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="e64f9-125">メモリとスパンを使った作業</span><span class="sxs-lookup"><span data-stu-id="e64f9-125">Working with memory and span</span></span>

<span data-ttu-id="e64f9-126">通常、メモリおよびスパンに関連する型は処理パイプラインにデータを格納するために使われます。そのため開発者は、<xref:System.Span%601>、<xref:System.Memory%601>、および関連する型を使う場合に、一連のベスト プラクティスに従うことが重要です。</span><span class="sxs-lookup"><span data-stu-id="e64f9-126">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="e64f9-127">これらのベスト プラクティスは、「[Memory\<T>T> と Span\<T>T> の使用ガイドライン](memory-t-usage-guidelines.md)」でドキュメント化されています。</span><span class="sxs-lookup"><span data-stu-id="e64f9-127">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e64f9-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e64f9-128">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
