---
title: DisposeAsync メソッドの実装
description: DisposeAsync メソッドと DisposeAsyncCore メソッドを実装し、非同期リソース クリーンアップを実行する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 04/07/2021
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 777036b83cd217418994e3cbc31958d13d5c3268
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107260509"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="25b92-103">DisposeAsync メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="25b92-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="25b92-104"><xref:System.IAsyncDisposable?displayProperty=nameWithType> インターフェイスが、C# 8.0 の一部として導入されました。</span><span class="sxs-lookup"><span data-stu-id="25b92-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="25b92-105"><xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> メソッドは、[Dispose メソッドの実装](implementing-dispose.md)と同様、リソースのクリーンアップを実行する必要がある場合に実装します。</span><span class="sxs-lookup"><span data-stu-id="25b92-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="25b92-106">両者の重要な違いの 1 つは、この実装により、非同期のクリーンアップ操作が可能になることです。</span><span class="sxs-lookup"><span data-stu-id="25b92-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="25b92-107"><xref:System.IAsyncDisposable.DisposeAsync> は、非同期の破棄操作を表す <xref:System.Threading.Tasks.ValueTask> を返します。</span><span class="sxs-lookup"><span data-stu-id="25b92-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="25b92-108">通常、<xref:System.IAsyncDisposable> インターフェイスを実装するとき、そのクラスでは <xref:System.IDisposable> インターフェイスも実装します。</span><span class="sxs-lookup"><span data-stu-id="25b92-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="25b92-109"><xref:System.IAsyncDisposable> インターフェイスの推奨される実装パターンは、同期の破棄か非同期の破棄のために準備をすることです。</span><span class="sxs-lookup"><span data-stu-id="25b92-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous or asynchronous dispose.</span></span> <span data-ttu-id="25b92-110">破棄パターンの実装に関するガイダンスのすべての説明は、非同期の実装にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="25b92-111">この記事では、読者が [Dispose メソッドの実装](implementing-dispose.md)方法について既に理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="25b92-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

[!INCLUDE [disposables-and-dependency-injection](includes/disposables-and-dependency-injection.md)]

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="25b92-112">DisposeAsync() および DisposeAsyncCore()</span><span class="sxs-lookup"><span data-stu-id="25b92-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="25b92-113"><xref:System.IAsyncDisposable> インターフェイスは、パラメーターなしの単一のメソッド <xref:System.IAsyncDisposable.DisposeAsync> を宣言します。</span><span class="sxs-lookup"><span data-stu-id="25b92-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="25b92-114">すべての非シールド クラスには、追加の `DisposeAsyncCore()` メソッドが必要です。このメソッドも <xref:System.Threading.Tasks.ValueTask> を返します。</span><span class="sxs-lookup"><span data-stu-id="25b92-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="25b92-115">パラメーターを持たない `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> の実装。</span><span class="sxs-lookup"><span data-stu-id="25b92-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="25b92-116">次のシグネチャを持つ `protected virtual ValueTask DisposeAsyncCore()` メソッド。</span><span class="sxs-lookup"><span data-stu-id="25b92-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="25b92-117">DisposeAsync() メソッド</span><span class="sxs-lookup"><span data-stu-id="25b92-117">The DisposeAsync() method</span></span>

<span data-ttu-id="25b92-118">`public` のパラメーターなしの `DisposeAsync()` メソッドは、`await using` ステートメントで暗黙的に呼び出されます。その目的は、アンマネージド リソースを解放し、通常のクリーンアップを実行し、ファイナライザーが存在する場合、それを実行する必要がないことを示すことです。</span><span class="sxs-lookup"><span data-stu-id="25b92-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="25b92-119">管理されたオブジェクトに関連付けられているメモリを解放するのは、常に[ガベージ コレクター](index.md)のドメインです。</span><span class="sxs-lookup"><span data-stu-id="25b92-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="25b92-120">このため、次のような標準的な実装があります。</span><span class="sxs-lookup"><span data-stu-id="25b92-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of unmanaged resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="25b92-121">非同期の破棄パターンでの、その破棄パターンとの主な違いの 1 つは、<xref:System.IAsyncDisposable.DisposeAsync> から `Dispose(bool)` オーバーロード メソッドへの呼び出しで、`false` が引数として渡されることです。</span><span class="sxs-lookup"><span data-stu-id="25b92-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="25b92-122">一方、<xref:System.IDisposable.Dispose?displayProperty=nameWithType> メソッドを実装する場合は、代わりに `true` が渡されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however, `true` is passed instead.</span></span> <span data-ttu-id="25b92-123">これにより、同期の破棄パターンとの機能の等価性が確保されるほか、ファイナライザーのコード パスが引き続き呼び出されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="25b92-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="25b92-124">言い換えると、`DisposeAsyncCore()` メソッドでは管理対象リソースが非同期的に破棄されるため、同期的にも破棄される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="25b92-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="25b92-125">したがって、`Dispose(true)` ではなく `Dispose(false)` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b92-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="25b92-126">DisposeAsyncCore() メソッド</span><span class="sxs-lookup"><span data-stu-id="25b92-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="25b92-127">`DisposeAsyncCore()` メソッドは、管理対象リソースを非同期でクリーンアップすることか、`DisposeAsync()` に呼び出しをカスケードすることを意図しています。</span><span class="sxs-lookup"><span data-stu-id="25b92-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="25b92-128"><xref:System.IAsyncDisposable> の実装である基底クラスをサブクラスが継承するとき、共通の非同期クリーンアップ操作がカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="25b92-129">`DisposeAsyncCore()` メソッドは `virtual` であるので、派生クラスはオーバーライドで追加のクリーンアップを定義できます。</span><span class="sxs-lookup"><span data-stu-id="25b92-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="25b92-130"><xref:System.IAsyncDisposable> の実装が `sealed` の場合、`DisposeAsyncCore()` メソッドは不要です。また、非同期クリーンアップは <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> メソッドで直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="25b92-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="25b92-131">非同期の破棄パターンの実装</span><span class="sxs-lookup"><span data-stu-id="25b92-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="25b92-132">非シールド クラスは、継承される可能性があるため、潜在的な基底クラスと見なす必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b92-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="25b92-133">潜在的な基底クラスに対して非同期の破棄パターンを実装する場合、`protected virtual ValueTask DisposeAsyncCore()` メソッドを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b92-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="25b92-134">次に、<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> を使用する非同期の破棄パターンの実装例を示します。</span><span class="sxs-lookup"><span data-stu-id="25b92-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="25b92-135">前の例では、<xref:System.Text.Json.Utf8JsonWriter> を使用しています。</span><span class="sxs-lookup"><span data-stu-id="25b92-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="25b92-136">`System.Text.Json` の詳細については、「[Newtonsoft.Json から System.Text.Json に移行する方法](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25b92-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="implement-both-dispose-and-async-dispose-patterns"></a><span data-ttu-id="25b92-137">破棄と非同期の破棄の両方のパターンを実装する</span><span class="sxs-lookup"><span data-stu-id="25b92-137">Implement both dispose and async dispose patterns</span></span>

<span data-ttu-id="25b92-138">場合によっては、<xref:System.IDisposable> と <xref:System.IAsyncDisposable> の両方のインターフェイスを実装する必要があります。クラスのスコープにこれらの実装のインスタンスが含まれている場合は特にそうです。</span><span class="sxs-lookup"><span data-stu-id="25b92-138">You may need to implement both the <xref:System.IDisposable> and <xref:System.IAsyncDisposable> interfaces, especially when your class scope contains instances of these implementations.</span></span> <span data-ttu-id="25b92-139">こうすることで、クリーンアップの呼び出しを適切に連鎖させることができます。</span><span class="sxs-lookup"><span data-stu-id="25b92-139">Doing so ensures that you can properly cascade clean up calls.</span></span> <span data-ttu-id="25b92-140">両方のインターフェイスを実装し、クリーンアップの適切なガイダンスを示すクラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="25b92-140">Here is an example class that implements both interfaces and demonstrates the proper guidance for cleanup.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

<span data-ttu-id="25b92-141"><xref:System.IDisposable.Dispose?displayProperty=nameWithType> と <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> の実装は、どちらも単純な定型コードです。</span><span class="sxs-lookup"><span data-stu-id="25b92-141">The <xref:System.IDisposable.Dispose?displayProperty=nameWithType> and <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementations are both simple boilerplate code.</span></span>

<span data-ttu-id="25b92-142">`Dispose(bool)` オーバーロード メソッドでは、<xref:System.IDisposable> インスタンスは、`null` でない場合に条件により破棄されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-142">In the `Dispose(bool)` overload method, the <xref:System.IDisposable> instance is conditionally disposed of if it is not `null`.</span></span> <span data-ttu-id="25b92-143"><xref:System.IAsyncDisposable> インスタンスは <xref:System.IDisposable> としてキャストされ、これも `null` でない場合は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-143">The <xref:System.IAsyncDisposable> instance is cast as <xref:System.IDisposable>, and if it is also not `null`, it is disposed of as well.</span></span> <span data-ttu-id="25b92-144">その後、両方のインスタンスは `null` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="25b92-144">Both instances are then assigned to `null`.</span></span>

<span data-ttu-id="25b92-145">`DisposeAsyncCore()` メソッドでは、同じ論理的アプローチに従います。</span><span class="sxs-lookup"><span data-stu-id="25b92-145">With the `DisposeAsyncCore()` method, the same logical approach is followed.</span></span> <span data-ttu-id="25b92-146"><xref:System.IAsyncDisposable> インスタンスが `null` ではない場合、`DisposeAsync().ConfigureAwait(false)` への呼び出しは待機されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-146">If the <xref:System.IAsyncDisposable> instance is not `null`, its call to `DisposeAsync().ConfigureAwait(false)` is awaited.</span></span> <span data-ttu-id="25b92-147"><xref:System.IDisposable> インスタンスも <xref:System.IAsyncDisposable> の実装である場合、これも非同期的に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-147">If the <xref:System.IDisposable> instance is also an implementation of <xref:System.IAsyncDisposable>, it's also disposed of asynchronously.</span></span> <span data-ttu-id="25b92-148">その後、両方のインスタンスは `null` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="25b92-148">Both instances are then assigned to `null`.</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="25b92-149">非同期の破棄可能の使用</span><span class="sxs-lookup"><span data-stu-id="25b92-149">Using async disposable</span></span>

<span data-ttu-id="25b92-150"><xref:System.IAsyncDisposable> インターフェイスを実装するオブジェクトを適切に使用するには、[await](../../csharp/language-reference/operators/await.md) キーワードと [using](../../csharp/language-reference/keywords/using-statement.md) キーワードを一緒に使用します。</span><span class="sxs-lookup"><span data-stu-id="25b92-150">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md) and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="25b92-151">`ExampleAsyncDisposable` クラスがインスタンス化され、`await using` ステートメントでラップされる次の例について考察してください。</span><span class="sxs-lookup"><span data-stu-id="25b92-151">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="25b92-152">元のコンテキストやスケジューラでタスクの継続をマーシャリングする方法を構成するには、<xref:System.IAsyncDisposable> インターフェイスの <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="25b92-152">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="25b92-153">`ConfigureAwait` の詳細については、「[ConfigureAwait に関する FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25b92-153">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="25b92-154">`ConfigureAwait` を使用する必要がない場合、`await using` ステートメントは次のように簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="25b92-154">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="25b92-155">さらに、[using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)の暗黙的なスコープを使用するように記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="25b92-155">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="25b92-156">using の積み重ね</span><span class="sxs-lookup"><span data-stu-id="25b92-156">Stacked usings</span></span>

<span data-ttu-id="25b92-157"><xref:System.IAsyncDisposable> を実装する複数のオブジェクトを作成して使用する場合、<xref:System.Threading.Tasks.ValueTask.ConfigureAwait%2A> で `await using` ステートメントを積み重ねると、誤った条件で <xref:System.IAsyncDisposable.DisposeAsync> を呼び出すことができなくなるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="25b92-157">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `await using` statements with <xref:System.Threading.Tasks.ValueTask.ConfigureAwait%2A> could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync> in errant conditions.</span></span> <span data-ttu-id="25b92-158">常に <xref:System.IAsyncDisposable.DisposeAsync> が確実に呼び出されるようにするには、スタックを避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b92-158">To ensure that <xref:System.IAsyncDisposable.DisposeAsync> is always called, you should avoid stacking.</span></span> <span data-ttu-id="25b92-159">次の 3 つのコード例に、代わりに使用できるパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="25b92-159">The following three code examples show acceptable patterns to use instead.</span></span>

### <a name="acceptable-pattern-one"></a><span data-ttu-id="25b92-160">使用可能なパターン 1</span><span class="sxs-lookup"><span data-stu-id="25b92-160">Acceptable pattern one</span></span>

:::code language="csharp" id="one" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

<span data-ttu-id="25b92-161">前の例では、各非同期クリーンアップ操作は、`await using` ブロックの下で明示的にスコープ設定されています。</span><span class="sxs-lookup"><span data-stu-id="25b92-161">In the preceding example, each asynchronous clean up operation is explicitly scoped under the `await using` block.</span></span> <span data-ttu-id="25b92-162">外側のスコープは、`objOne` が `objTwo` を囲む中かっこを設定する方法によって定義されます。そのため、最初に `objTwo` が、その後に `objOne` が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-162">The outer scope is defined by how `objOne` sets its braces, enclosing `objTwo`, as such `objTwo` is disposed first, followed by `objOne`.</span></span> <span data-ttu-id="25b92-163">どちらの `IAsyncDisposable` インスタンスでも <xref:System.IAsyncDisposable.DisposeAsync> メソッドを待機させているため、各インスタンスによって非同期のクリーンアップ操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-163">Both `IAsyncDisposable` instances have their <xref:System.IAsyncDisposable.DisposeAsync> method awaited, so each instance performs its asynchronous clean up operation.</span></span> <span data-ttu-id="25b92-164">呼び出しは、積み重ねではなく、入れ子になっています。</span><span class="sxs-lookup"><span data-stu-id="25b92-164">The calls are nested, not stacked.</span></span>

### <a name="acceptable-pattern-two"></a><span data-ttu-id="25b92-165">使用可能なパターン 2</span><span class="sxs-lookup"><span data-stu-id="25b92-165">Acceptable pattern two</span></span>

:::code language="csharp" id="two" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

<span data-ttu-id="25b92-166">前の例では、各非同期クリーンアップ操作は、`await using` ブロックの下で明示的にスコープ設定されています。</span><span class="sxs-lookup"><span data-stu-id="25b92-166">In the preceding example, each asynchronous clean up operation is explicitly scoped under the `await using` block.</span></span> <span data-ttu-id="25b92-167">各ブロックの最後で、対応する `IAsyncDisposable` インスタンスの <xref:System.IAsyncDisposable.DisposeAsync> メソッドが待機状態になっているので、非同期クリーンアップ操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-167">At the end of each block, the corresponding `IAsyncDisposable` instance has its <xref:System.IAsyncDisposable.DisposeAsync> method awaited, thus performing its asynchronous clean up operation.</span></span> <span data-ttu-id="25b92-168">呼び出しは、積み重ねではなく、シーケンシャルになっています。</span><span class="sxs-lookup"><span data-stu-id="25b92-168">The calls are sequential, not stacked.</span></span> <span data-ttu-id="25b92-169">このシナリオでは、`objOne` が最初に破棄され、次に `objTwo` が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-169">In this scenario `objOne` is disposed first, then `objTwo` is disposed.</span></span>

### <a name="acceptable-pattern-three"></a><span data-ttu-id="25b92-170">使用可能なパターン 3</span><span class="sxs-lookup"><span data-stu-id="25b92-170">Acceptable pattern three</span></span>

:::code language="csharp" id="three" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

<span data-ttu-id="25b92-171">前の例では、各非同期クリーンアップ操作は、含まれているメソッド本体で暗黙的にスコープ設定されています。</span><span class="sxs-lookup"><span data-stu-id="25b92-171">In the preceding example, each asynchronous clean up operation is implicitly scoped with the containing method body.</span></span> <span data-ttu-id="25b92-172">外側のブロックの最後で、`IAsyncDisposable` インスタンスによって、非同期のクリーンアップ操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="25b92-172">At the end of the enclosing block, the `IAsyncDisposable` instances perform their asynchronous clean up operations.</span></span> <span data-ttu-id="25b92-173">これは、宣言された順序と逆の順序で実行されます。つまり、`objOne` の前に `objTwo` が破棄されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="25b92-173">This runs in reverse order from which they were declared, meaning that `objTwo` is disposed before `objOne`.</span></span>

### <a name="unacceptable-pattern"></a><span data-ttu-id="25b92-174">許容できないパターン</span><span class="sxs-lookup"><span data-stu-id="25b92-174">Unacceptable pattern</span></span>

<span data-ttu-id="25b92-175">次のコードの強調表示されている行は、"using の積み重ね" を持つことの意味を示しています。</span><span class="sxs-lookup"><span data-stu-id="25b92-175">The highlighted lines in the following code show what it means to have "stacked usings".</span></span> <span data-ttu-id="25b92-176">`AnotherAsyncDisposable` コンストラクターから例外がスローされた場合、`objOne` は正しく破棄されません。</span><span class="sxs-lookup"><span data-stu-id="25b92-176">If an exception is thrown from the `AnotherAsyncDisposable` constructor, then `objOne` does not get properly disposed.</span></span>

:::code language="csharp" id="dontdothis" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs" highlight="9-10":::

> [!TIP]
> <span data-ttu-id="25b92-177">予期しない動作につながるおそれがあるため、このパターンは避けてください。</span><span class="sxs-lookup"><span data-stu-id="25b92-177">Avoid this pattern as it could lead to unexpected behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="25b92-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="25b92-178">See also</span></span>

<span data-ttu-id="25b92-179">`IDisposable` と `IAsyncDisposable` を両方実装する例については、[GitHub](https://github.com/dotnet/runtime/blob/035b729d829368c2790d825bd02db14f0c0fd2ea/src/libraries/System.Text.Json/src/System/Text/Json/Writer/Utf8JsonWriter.cs#L297-L345) の <xref:System.Text.Json.Utf8JsonWriter> ソース コードに関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25b92-179">For a dual implementation example of `IDisposable` and `IAsyncDisposable`, see the <xref:System.Text.Json.Utf8JsonWriter> source code [on GitHub](https://github.com/dotnet/runtime/blob/035b729d829368c2790d825bd02db14f0c0fd2ea/src/libraries/System.Text.Json/src/System/Text/Json/Writer/Utf8JsonWriter.cs#L297-L345).</span></span>

- [<span data-ttu-id="25b92-180">サービスの破棄</span><span class="sxs-lookup"><span data-stu-id="25b92-180">Disposal of services</span></span>](../../core/extensions/dependency-injection-guidelines.md#disposal-of-services)
- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
