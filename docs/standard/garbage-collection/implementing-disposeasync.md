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
# <a name="implement-a-disposeasync-method"></a>DisposeAsync メソッドの実装

<xref:System.IAsyncDisposable?displayProperty=nameWithType> インターフェイスが、C# 8.0 の一部として導入されました。 <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> メソッドは、[Dispose メソッドの実装](implementing-dispose.md)と同様、リソースのクリーンアップを実行する必要がある場合に実装します。 両者の重要な違いの 1 つは、この実装により、非同期のクリーンアップ操作が可能になることです。 <xref:System.IAsyncDisposable.DisposeAsync> は、非同期の破棄操作を表す <xref:System.Threading.Tasks.ValueTask> を返します。

通常、<xref:System.IAsyncDisposable> インターフェイスを実装するとき、そのクラスでは <xref:System.IDisposable> インターフェイスも実装します。 <xref:System.IAsyncDisposable> インターフェイスの推奨される実装パターンは、同期の破棄か非同期の破棄のために準備をすることです。 破棄パターンの実装に関するガイダンスのすべての説明は、非同期の実装にも適用されます。 この記事では、読者が [Dispose メソッドの実装](implementing-dispose.md)方法について既に理解していることを前提としています。

[!INCLUDE [disposables-and-dependency-injection](includes/disposables-and-dependency-injection.md)]

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync() および DisposeAsyncCore()

<xref:System.IAsyncDisposable> インターフェイスは、パラメーターなしの単一のメソッド <xref:System.IAsyncDisposable.DisposeAsync> を宣言します。 すべての非シールド クラスには、追加の `DisposeAsyncCore()` メソッドが必要です。このメソッドも <xref:System.Threading.Tasks.ValueTask> を返します。

- パラメーターを持たない `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> の実装。
- 次のシグネチャを持つ `protected virtual ValueTask DisposeAsyncCore()` メソッド。

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a>DisposeAsync() メソッド

`public` のパラメーターなしの `DisposeAsync()` メソッドは、`await using` ステートメントで暗黙的に呼び出されます。その目的は、アンマネージド リソースを解放し、通常のクリーンアップを実行し、ファイナライザーが存在する場合、それを実行する必要がないことを示すことです。 管理されたオブジェクトに関連付けられているメモリを解放するのは、常に[ガベージ コレクター](index.md)のドメインです。 このため、次のような標準的な実装があります。

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
> 非同期の破棄パターンでの、その破棄パターンとの主な違いの 1 つは、<xref:System.IAsyncDisposable.DisposeAsync> から `Dispose(bool)` オーバーロード メソッドへの呼び出しで、`false` が引数として渡されることです。 一方、<xref:System.IDisposable.Dispose?displayProperty=nameWithType> メソッドを実装する場合は、代わりに `true` が渡されます。 これにより、同期の破棄パターンとの機能の等価性が確保されるほか、ファイナライザーのコード パスが引き続き呼び出されるようにできます。 言い換えると、`DisposeAsyncCore()` メソッドでは管理対象リソースが非同期的に破棄されるため、同期的にも破棄される必要はありません。 したがって、`Dispose(true)` ではなく `Dispose(false)` を呼び出します。

### <a name="the-disposeasynccore-method"></a>DisposeAsyncCore() メソッド

`DisposeAsyncCore()` メソッドは、管理対象リソースを非同期でクリーンアップすることか、`DisposeAsync()` に呼び出しをカスケードすることを意図しています。 <xref:System.IAsyncDisposable> の実装である基底クラスをサブクラスが継承するとき、共通の非同期クリーンアップ操作がカプセル化されます。 `DisposeAsyncCore()` メソッドは `virtual` であるので、派生クラスはオーバーライドで追加のクリーンアップを定義できます。

> [!TIP]
> <xref:System.IAsyncDisposable> の実装が `sealed` の場合、`DisposeAsyncCore()` メソッドは不要です。また、非同期クリーンアップは <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> メソッドで直接実行できます。

## <a name="implement-the-async-dispose-pattern"></a>非同期の破棄パターンの実装

非シールド クラスは、継承される可能性があるため、潜在的な基底クラスと見なす必要があります。 潜在的な基底クラスに対して非同期の破棄パターンを実装する場合、`protected virtual ValueTask DisposeAsyncCore()` メソッドを指定する必要があります。 次に、<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> を使用する非同期の破棄パターンの実装例を示します。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

前の例では、<xref:System.Text.Json.Utf8JsonWriter> を使用しています。 `System.Text.Json` の詳細については、「[Newtonsoft.Json から System.Text.Json に移行する方法](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md)」を参照してください。

## <a name="implement-both-dispose-and-async-dispose-patterns"></a>破棄と非同期の破棄の両方のパターンを実装する

場合によっては、<xref:System.IDisposable> と <xref:System.IAsyncDisposable> の両方のインターフェイスを実装する必要があります。クラスのスコープにこれらの実装のインスタンスが含まれている場合は特にそうです。 こうすることで、クリーンアップの呼び出しを適切に連鎖させることができます。 両方のインターフェイスを実装し、クリーンアップの適切なガイダンスを示すクラスの例を次に示します。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

<xref:System.IDisposable.Dispose?displayProperty=nameWithType> と <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> の実装は、どちらも単純な定型コードです。

`Dispose(bool)` オーバーロード メソッドでは、<xref:System.IDisposable> インスタンスは、`null` でない場合に条件により破棄されます。 <xref:System.IAsyncDisposable> インスタンスは <xref:System.IDisposable> としてキャストされ、これも `null` でない場合は破棄されます。 その後、両方のインスタンスは `null` に割り当てられます。

`DisposeAsyncCore()` メソッドでは、同じ論理的アプローチに従います。 <xref:System.IAsyncDisposable> インスタンスが `null` ではない場合、`DisposeAsync().ConfigureAwait(false)` への呼び出しは待機されます。 <xref:System.IDisposable> インスタンスも <xref:System.IAsyncDisposable> の実装である場合、これも非同期的に破棄されます。 その後、両方のインスタンスは `null` に割り当てられます。

## <a name="using-async-disposable"></a>非同期の破棄可能の使用

<xref:System.IAsyncDisposable> インターフェイスを実装するオブジェクトを適切に使用するには、[await](../../csharp/language-reference/operators/await.md) キーワードと [using](../../csharp/language-reference/keywords/using-statement.md) キーワードを一緒に使用します。 `ExampleAsyncDisposable` クラスがインスタンス化され、`await using` ステートメントでラップされる次の例について考察してください。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> 元のコンテキストやスケジューラでタスクの継続をマーシャリングする方法を構成するには、<xref:System.IAsyncDisposable> インターフェイスの <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> 拡張メソッドを使用します。 `ConfigureAwait` の詳細については、「[ConfigureAwait に関する FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/)」を参照してください。

`ConfigureAwait` を使用する必要がない場合、`await using` ステートメントは次のように簡略化できます。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

さらに、[using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)の暗黙的なスコープを使用するように記述することもできます。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>using の積み重ね

<xref:System.IAsyncDisposable> を実装する複数のオブジェクトを作成して使用する場合、<xref:System.Threading.Tasks.ValueTask.ConfigureAwait%2A> で `await using` ステートメントを積み重ねると、誤った条件で <xref:System.IAsyncDisposable.DisposeAsync> を呼び出すことができなくなるおそれがあります。 常に <xref:System.IAsyncDisposable.DisposeAsync> が確実に呼び出されるようにするには、スタックを避ける必要があります。 次の 3 つのコード例に、代わりに使用できるパターンを示します。

### <a name="acceptable-pattern-one"></a>使用可能なパターン 1

:::code language="csharp" id="one" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

前の例では、各非同期クリーンアップ操作は、`await using` ブロックの下で明示的にスコープ設定されています。 外側のスコープは、`objOne` が `objTwo` を囲む中かっこを設定する方法によって定義されます。そのため、最初に `objTwo` が、その後に `objOne` が破棄されます。 どちらの `IAsyncDisposable` インスタンスでも <xref:System.IAsyncDisposable.DisposeAsync> メソッドを待機させているため、各インスタンスによって非同期のクリーンアップ操作が実行されます。 呼び出しは、積み重ねではなく、入れ子になっています。

### <a name="acceptable-pattern-two"></a>使用可能なパターン 2

:::code language="csharp" id="two" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

前の例では、各非同期クリーンアップ操作は、`await using` ブロックの下で明示的にスコープ設定されています。 各ブロックの最後で、対応する `IAsyncDisposable` インスタンスの <xref:System.IAsyncDisposable.DisposeAsync> メソッドが待機状態になっているので、非同期クリーンアップ操作が実行されます。 呼び出しは、積み重ねではなく、シーケンシャルになっています。 このシナリオでは、`objOne` が最初に破棄され、次に `objTwo` が破棄されます。

### <a name="acceptable-pattern-three"></a>使用可能なパターン 3

:::code language="csharp" id="three" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

前の例では、各非同期クリーンアップ操作は、含まれているメソッド本体で暗黙的にスコープ設定されています。 外側のブロックの最後で、`IAsyncDisposable` インスタンスによって、非同期のクリーンアップ操作が実行されます。 これは、宣言された順序と逆の順序で実行されます。つまり、`objOne` の前に `objTwo` が破棄されることを意味します。

### <a name="unacceptable-pattern"></a>許容できないパターン

次のコードの強調表示されている行は、"using の積み重ね" を持つことの意味を示しています。 `AnotherAsyncDisposable` コンストラクターから例外がスローされた場合、`objOne` は正しく破棄されません。

:::code language="csharp" id="dontdothis" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs" highlight="9-10":::

> [!TIP]
> 予期しない動作につながるおそれがあるため、このパターンは避けてください。

## <a name="see-also"></a>関連項目

`IDisposable` と `IAsyncDisposable` を両方実装する例については、[GitHub](https://github.com/dotnet/runtime/blob/035b729d829368c2790d825bd02db14f0c0fd2ea/src/libraries/System.Text.Json/src/System/Text/Json/Writer/Utf8JsonWriter.cs#L297-L345) の <xref:System.Text.Json.Utf8JsonWriter> ソース コードに関する説明を参照してください。

- [サービスの破棄](../../core/extensions/dependency-injection-guidelines.md#disposal-of-services)
- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
