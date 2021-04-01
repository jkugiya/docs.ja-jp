---
title: Memory<T> と Span<T> の使用ガイドライン
description: この記事では、Memory<T> および Span<T> について説明します。これらは、.NET Core の構造化データのバッファーであり、パイプラインで使用できます。
ms.date: 02/05/2021
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: b09c2444a4edab0c5f7bdecc64a19aadca37df34
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103635"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="43a07-103">Memory\<T> と Span\<T> の使用ガイドライン</span><span class="sxs-lookup"><span data-stu-id="43a07-103">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="43a07-104">.NET Core には、任意の連続したメモリ領域を表す多くの型があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-104">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="43a07-105">.NET Core 2.0 では <xref:System.Span%601> と <xref:System.ReadOnlySpan%601> が導入されました。これらはマネージド メモリまたはアンマネージド メモリへの参照をラップする軽量のメモリ バッファーです。</span><span class="sxs-lookup"><span data-stu-id="43a07-105">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that wrap references to managed or unmanaged memory.</span></span> <span data-ttu-id="43a07-106">このような型はスタック上にのみ格納できるため、非同期メソッドの呼び出しを含む多くのシナリオには適していません。</span><span class="sxs-lookup"><span data-stu-id="43a07-106">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="43a07-107">.NET Core 2.1 では、<xref:System.Memory%601>、<xref:System.ReadOnlyMemory%601>、<xref:System.Buffers.IMemoryOwner%601>、<xref:System.Buffers.MemoryPool%601> など、さらに多くの型が追加されています。</span><span class="sxs-lookup"><span data-stu-id="43a07-107">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="43a07-108"><xref:System.Span%601> と同様に、<xref:System.Memory%601> とそれに関連する型は、マネージド メモリとアンマネージド メモリの両方でサポートできます。</span><span class="sxs-lookup"><span data-stu-id="43a07-108">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="43a07-109"><xref:System.Span%601> とは異なり、<xref:System.Memory%601> はマネージド ヒープ上に格納できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-109">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="43a07-110"><xref:System.Span%601> と <xref:System.Memory%601> は、どちらもパイプラインで使用できる構造化データのバッファーのラッパーです。</span><span class="sxs-lookup"><span data-stu-id="43a07-110">Both <xref:System.Span%601> and <xref:System.Memory%601> are wrappers over buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="43a07-111">つまり、データの一部または全部をパイプライン内のコンポーネントに効率的に渡すことができるように設計されています。そのため、データを処理し、必要に応じてバッファーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-111">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="43a07-112"><xref:System.Memory%601> とその関連する型には、複数のコンポーネントまたは複数のスレッドからアクセスできるため、開発者が標準的な使用ガイドラインに従って堅牢なコードを作成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="43a07-112">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="43a07-113">所有者、コンシューマー、有効期間管理</span><span class="sxs-lookup"><span data-stu-id="43a07-113">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="43a07-114">バッファーは API 間で渡すことができ、複数のスレッドからバッファーにアクセスされることがあるため、有効期間管理を考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="43a07-114">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="43a07-115">次の 3 つの中心的な概念があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-115">There are three core concepts:</span></span>

- <span data-ttu-id="43a07-116">**所有権**。</span><span class="sxs-lookup"><span data-stu-id="43a07-116">**Ownership**.</span></span> <span data-ttu-id="43a07-117">バッファー インスタンスの所有者は、バッファーが使用されなくなったときにバッファーを破棄することを含め、有効期間の管理を担当します。</span><span class="sxs-lookup"><span data-stu-id="43a07-117">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="43a07-118">すべてのバッファーの所有者は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="43a07-118">All buffers have a single owner.</span></span> <span data-ttu-id="43a07-119">通常、所有者とは、バッファーを作成したコンポーネント、またはファクトリーからバッファーを受け取ったコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="43a07-119">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="43a07-120">所有権は譲渡することもできます。**コンポーネント A** はバッファーの制御を **コンポーネント B** に譲渡することができます。その時点で **コンポーネント A** はバッファーを使用できなくなり、**コンポーネント B** が、使用されなくなったバッファーの破棄を担当します。</span><span class="sxs-lookup"><span data-stu-id="43a07-120">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="43a07-121">**消費**。</span><span class="sxs-lookup"><span data-stu-id="43a07-121">**Consumption**.</span></span> <span data-ttu-id="43a07-122">バッファー インスタンスのコンシューマーは、読み取り、場合によっては書き込みでバッファー インスタンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-122">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="43a07-123">何らかの外部の同期メカニズムが提供されていない限り、バッファーは同時に持つことができるコンシューマーは 1 つです。</span><span class="sxs-lookup"><span data-stu-id="43a07-123">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="43a07-124">バッファーのアクティブなコンシューマーは必ずしもバッファーの所有者ではありません。</span><span class="sxs-lookup"><span data-stu-id="43a07-124">The active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="43a07-125">**リース**。</span><span class="sxs-lookup"><span data-stu-id="43a07-125">**Lease**.</span></span> <span data-ttu-id="43a07-126">リースは、特定のコンポーネントがバッファーの消費者になることができる時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="43a07-126">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="43a07-127">これら 3 つの概念を示す疑似コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="43a07-127">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="43a07-128">擬似コード内の `Buffer` は、<xref:System.Char> 型の <xref:System.Memory%601> または<xref:System.Span%601> のバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="43a07-128">`Buffer` in the pseudo-code represents a <xref:System.Memory%601> or <xref:System.Span%601> buffer of type <xref:System.Char>.</span></span> <span data-ttu-id="43a07-129">`Main` メソッドはバッファーをインスタンス化し、`WriteInt32ToBuffer` メソッドを呼び出して整数の文字列表現をバッファーに書き込み、次に `DisplayBufferToConsole` メソッドを呼び出してバッファーの値を表示します。</span><span class="sxs-lookup"><span data-stu-id="43a07-129">The `Main` method instantiates the buffer, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

<span data-ttu-id="43a07-130">`Main` メソッドによってバッファーが作成され、その所有者も作成されます。</span><span class="sxs-lookup"><span data-stu-id="43a07-130">The `Main` method creates the buffer and so is its owner.</span></span> <span data-ttu-id="43a07-131">そのため、`Main` には使用されなくなったバッファーを破棄する責任があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-131">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="43a07-132">擬似コードは、バッファーで `Destroy` メソッドを呼び出すことによってこれを示します。</span><span class="sxs-lookup"><span data-stu-id="43a07-132">The pseudo-code illustrates this by calling a `Destroy` method on the buffer.</span></span> <span data-ttu-id="43a07-133">(<xref:System.Memory%601> と <xref:System.Span%601> は、どちらも実際には `Destroy` メソッドを持ちません。</span><span class="sxs-lookup"><span data-stu-id="43a07-133">(Neither <xref:System.Memory%601> nor <xref:System.Span%601> actually has a `Destroy` method.</span></span> <span data-ttu-id="43a07-134">実際のコード例については、この記事で後ほど示します)。</span><span class="sxs-lookup"><span data-stu-id="43a07-134">You'll see actual code examples later in this article.)</span></span>

<span data-ttu-id="43a07-135">バッファーには `WriteInt32ToBuffer` と `DisplayBufferToConsole` という 2 つのコンシューマーがあります。</span><span class="sxs-lookup"><span data-stu-id="43a07-135">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="43a07-136">同時に存在するコンシューマーは 1 つのみであり (最初は `WriteInt32ToBuffer`、次に `DisplayBufferToConsole`)、どちらのコンシューマーもバッファーを所有していません。</span><span class="sxs-lookup"><span data-stu-id="43a07-136">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="43a07-137">この文脈における "コンシューマー" は、バッファーの読み取り専用ビューを意味していない点にも注意してください。バッファーの読み取り/書き込みビューがある場合、コンシューマーは `WriteInt32ToBuffer` と同様にバッファーの内容を変更できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-137">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="43a07-138">メソッド呼び出しの開始からメソッドから返されるまでの間に、`WriteInt32ToBuffer` メソッドはバッファー上にリースを持ちます (消費することができます)。</span><span class="sxs-lookup"><span data-stu-id="43a07-138">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="43a07-139">同様に、`DisplayBufferToConsole` は実行中にバッファー上にリースを持ち、メソッドがアンワインドするとリースは解放されます</span><span class="sxs-lookup"><span data-stu-id="43a07-139">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="43a07-140">(リース管理のための API はありません。"リース" は概念的なものです)。</span><span class="sxs-lookup"><span data-stu-id="43a07-140">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="43a07-141">Memory\<T> と所有者またはコンシューマー モデル</span><span class="sxs-lookup"><span data-stu-id="43a07-141">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="43a07-142">「[所有者、コンシューマー、有効期間管理](#owners-consumers-and-lifetime-management)」セクションで説明したように、バッファーには常に所有者がいます。</span><span class="sxs-lookup"><span data-stu-id="43a07-142">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="43a07-143">.NET Core は 2 つの所有権モデルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="43a07-143">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="43a07-144">単一の所有権をサポートするモデル。</span><span class="sxs-lookup"><span data-stu-id="43a07-144">A model that supports single ownership.</span></span> <span data-ttu-id="43a07-145">バッファーは、その有効期間全体にわたって単一の所有者を持ちます。</span><span class="sxs-lookup"><span data-stu-id="43a07-145">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="43a07-146">所有権の譲渡をサポートするモデル。</span><span class="sxs-lookup"><span data-stu-id="43a07-146">A model that supports ownership transfer.</span></span> <span data-ttu-id="43a07-147">バッファーの所有権は、元の所有者 (作成者) から別のコンポーネントに譲渡できます。譲渡されたコンポーネントがバッファーの有効期間管理を担当するようになります。</span><span class="sxs-lookup"><span data-stu-id="43a07-147">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="43a07-148">さらにその所有者が所有権を別のコンポーネントに譲渡することもできます。</span><span class="sxs-lookup"><span data-stu-id="43a07-148">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="43a07-149">明示的にバッファーの所有権を管理するには、<xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="43a07-149">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="43a07-150"><xref:System.Buffers.IMemoryOwner%601> は両方の所有権モデルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="43a07-150"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="43a07-151"><xref:System.Buffers.IMemoryOwner%601> の参照を持つコンポーネントがバッファーを所有します。</span><span class="sxs-lookup"><span data-stu-id="43a07-151">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="43a07-152">次の例では、<xref:System.Buffers.IMemoryOwner%601?> インスタンスを使用して <xref:System.Memory%601> バッファーの所有権を反映しています。</span><span class="sxs-lookup"><span data-stu-id="43a07-152">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of a <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="43a07-153">この例を [`using`](../../csharp/language-reference/keywords/using-statement.md) と記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="43a07-153">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="43a07-154">このコードの場合:</span><span class="sxs-lookup"><span data-stu-id="43a07-154">In this code:</span></span>

- <span data-ttu-id="43a07-155">`Main` メソッドは <xref:System.Buffers.IMemoryOwner%601> インスタンスへの参照を保持しているため、`Main` メソッドはバッファーの所有者です。</span><span class="sxs-lookup"><span data-stu-id="43a07-155">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="43a07-156">`WriteInt32ToBuffer` および `DisplayBufferToConsole` メソッドは、<xref:System.Memory%601> をパブリック API として受け入れます。</span><span class="sxs-lookup"><span data-stu-id="43a07-156">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="43a07-157">そのため、これらはバッファーの消費者です。</span><span class="sxs-lookup"><span data-stu-id="43a07-157">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="43a07-158">また、消費できるのは一度に 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="43a07-158">And they only consume it one at a time.</span></span>

<span data-ttu-id="43a07-159">`WriteInt32ToBuffer` メソッドはバッファーに値を書き込むことが意図されていますが、`DisplayBufferToConsole` メソッドではそうではありません。</span><span class="sxs-lookup"><span data-stu-id="43a07-159">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="43a07-160">これを反映するために、型 <xref:System.ReadOnlyMemory%601> の引数を受け入れておくことができます。</span><span class="sxs-lookup"><span data-stu-id="43a07-160">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="43a07-161"><xref:System.ReadOnlyMemory%601> の詳細については、「[規則 2:バッファーを読み取り専用にする場合は ReadOnlySpan\<T> または ReadOnlyMemory\<T> を使用する](#rule-2)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43a07-161">For more information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="43a07-162">"所有者なし" の Memory\<T> インスタンス</span><span class="sxs-lookup"><span data-stu-id="43a07-162">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="43a07-163"><xref:System.Buffers.IMemoryOwner%601> を使用せずに <xref:System.Memory%601> インスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-163">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="43a07-164">この場合、バッファーの所有権は明示的ではなく暗黙的であり、単一の所有者モデルのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="43a07-164">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="43a07-165">これは次の方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-165">You can do this by:</span></span>

- <span data-ttu-id="43a07-166">次の例のように、<xref:System.Memory%601> コンストラクターのいずれかを直接呼び出し、`T[]` を渡します。</span><span class="sxs-lookup"><span data-stu-id="43a07-166">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="43a07-167">[String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) 拡張メソッドを呼び出して `ReadOnlyMemory<char>` インスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="43a07-167">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="43a07-168">最初に <xref:System.Memory%601> インスタンスを作成したメソッドは、バッファーの暗黙的な所有者です。</span><span class="sxs-lookup"><span data-stu-id="43a07-168">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="43a07-169">譲渡を支援する <xref:System.Buffers.IMemoryOwner%601> インスタンスはないため、所有権を他のコンポーネントに譲渡することはできません</span><span class="sxs-lookup"><span data-stu-id="43a07-169">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="43a07-170">(または、ランタイムのガベージ コレクターがバッファーを所有していて、すべてのメソッドがバッファーを消費するだけであると想像することもできます)。</span><span class="sxs-lookup"><span data-stu-id="43a07-170">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="43a07-171">使用ガイドライン</span><span class="sxs-lookup"><span data-stu-id="43a07-171">Usage guidelines</span></span>

<span data-ttu-id="43a07-172">メモリ ブロックは所有されていますが、複数のコンポーネントに渡されることが意図されており、その一部は特定のメモリ ブロック上で同時に動作する可能性があるため、<xref:System.Memory%601> と <xref:System.Span%601> の両方を使用するためのガイドラインを確立することが重要です。</span><span class="sxs-lookup"><span data-stu-id="43a07-172">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="43a07-173">ガイドラインが必要な理由は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="43a07-173">Guidelines are necessary because:</span></span>

- <span data-ttu-id="43a07-174">所有者がメモリ ブロックを解放した後に、コンポーネントがメモリ ブロックへの参照を保持する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-174">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="43a07-175">あるコンポーネントがバッファーに対して動作し、それ同時に他のコンポーネントがそのバッファーに対して動作する可能性があり、そのようなプロセスでは、バッファー内のデータが破損します。</span><span class="sxs-lookup"><span data-stu-id="43a07-175">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="43a07-176">スタックに割り当てられる <xref:System.Span%601> の性質によってパフォーマンスが最適化され、<xref:System.Span%601> はメモリ ブロック上での操作に適した型になりますが、<xref:System.Span%601> にはいくつかの大きな制限もあります。</span><span class="sxs-lookup"><span data-stu-id="43a07-176">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="43a07-177"><xref:System.Span%601> を使用するタイミングと、<xref:System.Memory%601> を使用するタイミングを把握することが重要です。</span><span class="sxs-lookup"><span data-stu-id="43a07-177">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="43a07-178">以下は、<xref:System.Memory%601> とその関連する型を正しく使用するためのレコメンデーションです。</span><span class="sxs-lookup"><span data-stu-id="43a07-178">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="43a07-179">特に明記しない限り、<xref:System.Memory%601> と <xref:System.Span%601> に適用されるガイダンスは <xref:System.ReadOnlyMemory%601> と <xref:System.ReadOnlySpan%601> にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="43a07-179">Guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="43a07-180">**規則 1:同期 API の場合、可能であればパラメーターとして Memory\<T> ではなく Span\<T> を使用する。**</span><span class="sxs-lookup"><span data-stu-id="43a07-180">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="43a07-181"><xref:System.Span%601> は <xref:System.Memory%601> よりも汎用性が高く、さまざまな連続するメモリ バッファーを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="43a07-181"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="43a07-182"><xref:System.Span%601> は <xref:System.Memory%601>> よりもパフォーマンスに優れています。</span><span class="sxs-lookup"><span data-stu-id="43a07-182"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="43a07-183">最後に、<xref:System.Memory%601.Span?displayProperty=nameWithType> プロパティを使用して <xref:System.Memory%601> インスタンスを <xref:System.Span%601> に変換することはできますが、Span\<T> から Memory\<T> に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="43a07-183">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="43a07-184">そのため、呼び出し元が <xref:System.Memory%601> インスタンスを持っていた場合、いずれにしても <xref:System.Span%601> パラメーターを使用してメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="43a07-184">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="43a07-185">型 <xref:System.Memory%601> ではなく型 <xref:System.Span%601> のパラメーターを使用すると、適切な消費メソッドの実装を記述する場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="43a07-185">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="43a07-186">メソッドのリース時間を過ぎてバッファーにアクセスを試行しないように、コンパイル時のチェックが自動的に実行されます (詳細については後述します)。</span><span class="sxs-lookup"><span data-stu-id="43a07-186">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="43a07-187">完全に同期していても、<xref:System.Span%601> パラメーターではなく <xref:System.Memory%601> パラメーターの使用が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-187">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="43a07-188">おそらく、利用している API は <xref:System.Memory%601> 引数のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="43a07-188">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="43a07-189">これは問題ありませんが、<xref:System.Memory%601> を同期的に使用するときに伴うトレードオフに注意してください。</span><span class="sxs-lookup"><span data-stu-id="43a07-189">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2"></a>

<span data-ttu-id="43a07-190">**規則 2:バッファーを読み取り専用にする場合は ReadOnlySpan\<T> または ReadOnlyMemory\<T> を使用する。**</span><span class="sxs-lookup"><span data-stu-id="43a07-190">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="43a07-191">前述の例では、`DisplayBufferToConsole` メソッドはバッファーからの読み取りのみを行います。バッファーの内容は変更しません。</span><span class="sxs-lookup"><span data-stu-id="43a07-191">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="43a07-192">メソッドのシグネチャは次のように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-192">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="43a07-193">実際、この規則と規則 1 を組み合わせると、さらに改善され、メソッドのシグネチャを次のように書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="43a07-193">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="43a07-194">`DisplayBufferToConsole` メソッドは、考えられるほぼすべてのバッファー型 (`T[]`、[stackalloc](../../csharp/language-reference/operators/stackalloc.md) で割り当てられたストレージなど) で動作します。</span><span class="sxs-lookup"><span data-stu-id="43a07-194">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="43a07-195"><xref:System.String> を直接渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="43a07-195">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="43a07-196">**規則 3:メソッドが Memory\<T> を受け入れて `void` を返した場合、メソッドが返した後に Memory\<T> インスタンスを使用してはならない。**</span><span class="sxs-lookup"><span data-stu-id="43a07-196">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="43a07-197">これは、前述した "リース" の概念に関連しています。</span><span class="sxs-lookup"><span data-stu-id="43a07-197">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="43a07-198"><xref:System.Memory%601> インスタンスに対する void を返すメソッドのリースは、メソッドが開始時に開始され、メソッドの終了時に終了します。</span><span class="sxs-lookup"><span data-stu-id="43a07-198">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="43a07-199">コンソールからの入力に基づいてループで `Log` を呼び出す次の例を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="43a07-199">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="43a07-200">`Log` が完全同期メソッドである場合、メモリ インスタンスのアクティブなコンシューマーは常に 1 つのみなので、このコードは予想どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="43a07-200">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="43a07-201">ただし、代わりに `Log` がこの実装を持っている場合を想像してください。</span><span class="sxs-lookup"><span data-stu-id="43a07-201">But imagine instead that `Log` has this implementation.</span></span>

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

<span data-ttu-id="43a07-202">この実装では、元のメソッドから返された後も、`Log` はバックグラウンドで <xref:System.Memory%601> インスタンスを使用しようとするため、リースに違反することになります。</span><span class="sxs-lookup"><span data-stu-id="43a07-202">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="43a07-203">`Main` メソッドがバッファーを変更しているときに、`Log` がバッファーを読み込もうとすると、データが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-203">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="43a07-204">これを解決する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="43a07-204">There are several ways to resolve this:</span></span>

- <span data-ttu-id="43a07-205">以下の `Log` メソッドの実装のように、`Log` メソッドは `void` ではなく <xref:System.Threading.Tasks.Task> を返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-205">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="43a07-206">`Log` は代わりに次のように実装できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-206">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="43a07-207">**規則 4:メソッドが Memory\<T> を受け入れて Task を返す場合、Task が終了状態に遷移した後に Memory\<T> インスタンスを使用してはならない。**</span><span class="sxs-lookup"><span data-stu-id="43a07-207">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="43a07-208">これは規則 3 の単なる非同期版です。</span><span class="sxs-lookup"><span data-stu-id="43a07-208">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="43a07-209">前の例の `Log` メソッドは、この規則に従うために次のように記述することができます。</span><span class="sxs-lookup"><span data-stu-id="43a07-209">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="43a07-210">ここで、"終了状態" とは、タスクの状態が完了、失敗、またはキャンセル済みに移行することを意味します。</span><span class="sxs-lookup"><span data-stu-id="43a07-210">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="43a07-211">つまり、"終了状態" とは、"スローまたは実行継続の待機を発生させるすべてのもの" を意味します。</span><span class="sxs-lookup"><span data-stu-id="43a07-211">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="43a07-212">このガイダンスは、<xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.ValueTask%601>、または同様の型を返すメソッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="43a07-212">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="43a07-213">**規則 5:コンストラクターがパラメーターとして Memory\<T> を受け入れる場合、構築されたオブジェクトのインスタンス メソッドは Memory\<T> インスタンスの消費者であると見なされる。**</span><span class="sxs-lookup"><span data-stu-id="43a07-213">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="43a07-214">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="43a07-214">Consider the following example:</span></span>

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

<span data-ttu-id="43a07-215">ここで、`OddValueExtractor` コンストラクターは `ReadOnlyMemory<int>` をコンストラクター パラメーターとして受け入れます。そのため、コンストラクター自体が `ReadOnlyMemory<int>` インスタンスのコンシューマーであり、戻り値に対するすべてのインスタンス メソッドも元の `ReadOnlyMemory<int>` インスタンスのコンシューマーです。</span><span class="sxs-lookup"><span data-stu-id="43a07-215">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="43a07-216">つまり、インスタンスが `TryReadNextOddValue` メソッドに直接渡されない場合でも、`TryReadNextOddValue` は `ReadOnlyMemory<int>` インスタンスを消費します。</span><span class="sxs-lookup"><span data-stu-id="43a07-216">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="43a07-217">**規則 6:型に設定できる Memory\<T> 型のプロパティ (または同等のインスタンス メソッド) がある場合、そのオブジェクトに対するインスタンス メソッドは Memory\<T> インスタンスの消費者であると見なされる。**</span><span class="sxs-lookup"><span data-stu-id="43a07-217">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="43a07-218">これは単に規則 5 の一種です。</span><span class="sxs-lookup"><span data-stu-id="43a07-218">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="43a07-219">この規則が存在する理由は、プロパティ セッターまたは同等のメソッドは入力をキャプチャして永続化すると想定されているため、同じオブジェクトに対するインスタンス メソッドがキャプチャした状態を利用する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="43a07-219">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="43a07-220">この規則をトリガーする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="43a07-220">The following example triggers this rule:</span></span>

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

<span data-ttu-id="43a07-221">**規則 7:IMemoryOwner\<T> 参照がある場合、どこかの時点でそれを破棄するか所有権を譲渡する必要がある (両方を実行する必要はない)。**</span><span class="sxs-lookup"><span data-stu-id="43a07-221">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="43a07-222"><xref:System.Memory%601> インスタンスはマネージド メモリまたはアンマネージド メモリのいずれかでサポートされている可能性があるため、<xref:System.Memory%601> インスタンスに対して実行された作業が完了したら、所有者は <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-222">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="43a07-223">または、所有者が <xref:System.Buffers.IMemoryOwner%601> インスタンスの所有権を別のコンポーネントに譲渡することもできます。譲渡の時点で、獲得した側のコンポーネントは適切なタイミングで <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> を呼び出す責任を負います (詳細については後述します)。</span><span class="sxs-lookup"><span data-stu-id="43a07-223">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="43a07-224"><xref:System.Buffers.MemoryPool%601.Dispose%2A> メソッドの呼び出しに失敗すると、マネージド メモリのリークやその他のパフォーマンス低下が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-224">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="43a07-225">この規則は、<xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> のようなファクトリ メソッドを呼び出すコードにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="43a07-225">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="43a07-226">呼び出し元は、返された <xref:System.Buffers.IMemoryOwner%601> の所有者になり、終了時にインスタンスを破棄する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="43a07-226">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="43a07-227">**規則 8:API サーフェスに IMemoryOwner\<T> パラメーターがある場合、そのインスタンスの所有権を受け入れていることを示す。**</span><span class="sxs-lookup"><span data-stu-id="43a07-227">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="43a07-228">この種類のシグナルを持つインスタンスを受け入れることは、コンポーネントがこのインスタンスの所有権を取得しようとしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="43a07-228">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="43a07-229">規則 7 に従い、コンポーネントは適切な破棄の責任を負うようになります。</span><span class="sxs-lookup"><span data-stu-id="43a07-229">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="43a07-230"><xref:System.Buffers.IMemoryOwner%601> インスタンスの所有権を別のコンポーネントに譲渡したコンポーネントは、メソッド呼び出しの完了後にそのインスタンスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="43a07-230">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43a07-231">コンストラクターがパラメーターとして <xref:System.Buffers.IMemoryOwner%601>を受け入れる場合、その型は <xref:System.IDisposable> を実装し、<xref:System.IDisposable.Dispose%2A> メソッドは <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-231">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="43a07-232">**規則 9:同期的 p/invoke メソッドをラップしている場合、API は Span\<T> をパラメーターとして受け入れる必要がある。**</span><span class="sxs-lookup"><span data-stu-id="43a07-232">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="43a07-233">規則 1 に従うと、<xref:System.Span%601> は一般に同期的 API に使用するために適した型です。</span><span class="sxs-lookup"><span data-stu-id="43a07-233">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="43a07-234">次の例のように、[`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) キーワードを介して <xref:System.Span%601> インスタンスを固定できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-234">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="43a07-235">前の例では、入力の範囲が空の場合などに、`pbData` が null になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43a07-235">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="43a07-236">`cbData` が 0 であっても、エクスポートされたメソッドで `pbData` を null 以外にする必要がある場合、このメソッドは次のように実装できます。</span><span class="sxs-lookup"><span data-stu-id="43a07-236">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="43a07-237">**規則 10:同期的 p/invoke メソッドをラップしている場合、API は Memory\<T> をパラメーターとして受け入れる必要がある。**</span><span class="sxs-lookup"><span data-stu-id="43a07-237">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="43a07-238">非同期操作で [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) キーワードは使用できないので、インスタンスが表す連続するメモリの種類に関係なく、<xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> メソッドを使用して <xref:System.Memory%601> インスタンスを固定します。</span><span class="sxs-lookup"><span data-stu-id="43a07-238">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="43a07-239">次の例は、この API を使用して非同期の p/invoke 呼び出しを実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="43a07-239">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)(handle.Target);
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a><span data-ttu-id="43a07-240">関連項目</span><span class="sxs-lookup"><span data-stu-id="43a07-240">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
