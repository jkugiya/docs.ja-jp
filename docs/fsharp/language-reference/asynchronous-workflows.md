---
title: 非同期ワークフロー
description: 計算を非同期に実行して、他の作業の実行をブロックせずに実行するための F# プログラミング言語のサポートについて説明します。
ms.date: 08/15/2020
ms.openlocfilehash: 14146cc8a643f31831475075212cc06da5f8d6ff
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720271"
---
# <a name="asynchronous-workflows"></a>非同期ワークフロー

この記事では、計算を非同期的に実行する F# でのサポートについて説明します。つまり、他の作業の実行をブロックしないということです。 たとえば、非同期計算を使用すると、ユーザーに対する UI の応答性を維持しつつ他の作業を実行できるアプリケーションを作成できます。

## <a name="syntax"></a>構文

```fsharp
async { expression }
```

## <a name="remarks"></a>解説

前の構文では、`expression` によって表される計算が非同期的に実行されるように設定されています。つまり、非同期スリープ操作、I/O、その他の非同期操作が実行されるときに、現在の計算スレッドはブロックされません。 多くの場合、非同期計算はバックグラウンド スレッドで開始され、現在のスレッドの実行は継続します。 式の型は `Async<'T>` です。ここで、`'T` は、`return` キーワードが使用されている場合に式によって返される型です。 このような式のコードは、"*非同期ブロック (asynchronous block)* " または "*非同期ブロック (async block)* " と呼ばれます。

非同期プログラミングにはさまざまな方法があり、[`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html) クラスにはいくつかのシナリオをサポートするメソッドが用意されています。 一般的な方法は、非同期的に実行しようとしている 1 つまたは複数の計算を表す `Async` オブジェクトを作成してから、トリガー関数のいずれか 1 つを使用してこれらの計算を開始するというものです。 さまざまなトリガー関数によって、非同期計算を実行する各種の方法が提供されています。どの方法を使用するかは、現在のスレッド、バックグラウンド スレッド、.NET Framework タスク オブジェクトを使用するかどうか、また計算の終了時に実行する必要のある継続関数があるかどうかによって異なります。 たとえば、現在のスレッドで非同期計算を開始するには、[`Async.StartImmediate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#StartImmediate) を使用できます。 UI スレッドから非同期計算を開始する場合は、キーボード操作やマウス アクティビティなどのユーザー アクションを処理するメイン イベント ループがブロックされないため、アプリケーションの応答性が維持されます。

## <a name="asynchronous-binding-by-using-let"></a>let! を使用した非同期バインド

非同期ワークフローに含まれる式と操作には、同期的なものもあれば、結果を非同期的に返すよう設計されたより長い計算もあります。 メソッドを非同期的に呼び出す場合は、通常の `let` バインドではなく、`let!` を使用します。 `let!` の効果は、計算の実行中に他の計算やスレッドで実行を続行できるようになるというものです。 `let!` バインドの右側が返されたら、非同期ワークフローの残りの部分では実行が再開されます。

次のコードは、`let` と `let!` の違いを示しています。 `let` を使用するコード行では、非同期計算が、`Async.StartImmediate` や [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) などを使用して後で実行できるオブジェクトとして作成されるに過ぎません。 `let!` を使用するコード行では、計算が開始され、次いでスレッドが中断されます。結果が使用可能になると、その時点から実行が続行されます。

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

`let!` に加えて、`use!` を使用して非同期バインドを実行することもできます。 `let!` と `use!` の違いは、`let` と `use` の違いと同じです。 `use!` の場合、オブジェクトは現在のスコープの終了時に破棄されます。 現在のリリースの F# 言語では、`use!` で値を null に初期化することはできないことにご注意ください。一方、`use` ではそれが可能です。

## <a name="asynchronous-primitives"></a>非同期プリミティブ

1 つの非同期タスクを実行し、その結果を返すメソッドは、"*非同期プリミティブ*" と呼ばれており、これは `let!` 専用に設計されています。 いくつかの非同期プリミティブは、F# コア ライブラリで定義されています。 Web アプリケーション用にそのようなメソッドが 2 つ、モジュール [`FSharp.Control.WebExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html) に定義されています。[`WebRequest.AsyncGetResponse`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncGetResponse) と [`WebClient.AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) です。 どちらのプリミティブも、URL を指定されると、Web ページからデータをダウンロードします。 `AsyncGetResponse` は `System.Net.WebResponse` オブジェクトを生成し、`AsyncDownloadString` は Web ページの HTML を表す文字列を生成します。

非同期 I/O 操作のためのいくつかのプリミティブが [`FSharp.Control.CommonExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html) モジュールに含まれています。 `System.IO.Stream` クラスの拡張メソッドは [`Stream.AsyncRead`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncRead) と [`Stream.AsyncWrite`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncWrite) です。

また、本文全体が非同期ブロックで囲まれた関数を定義することで、独自の非同期プリミティブを作成することもできます。

F# の非同期プログラミング モデルを使用して他の非同期モデル用に設計された非同期メソッドを .NET Framework で使用するには、F# `Async` オブジェクトを返す関数を作成します。 F# ライブラリには、これを簡単に実行できる関数が用意されています。

非同期ワークフローの使用例を次に示します。[Async クラス](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html)のメソッドに関するドキュメントには、他にも多数の例が含まれています。

この例では、非同期ワークフローを使用して並列で計算を実行する方法を示します。

次のコード例では、関数 `fetchAsync` は Web 要求から返された HTML テキストを取得します。 `fetchAsync` 関数には、非同期のコード ブロックが含まれています。 非同期プリミティブ (このケースでは [`AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString)) の結果に対してバインドを行う場合、`let` の代わりに `let!` が使用されます。

関数 [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) を使用して非同期操作を実行し、その結果を待機します。 たとえば、[`Async.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#Parallel) 関数を `Async.RunSynchronously` 関数と共に使用することで、複数の非同期操作を並列で実行できます。 `Async.Parallel` 関数は、`Async` オブジェクトの一覧を受け取り、`Async` タスク オブジェクトごとにコードを並列で実行するように設定し、並列計算を表す `Async` オブジェクトを返します。 1 つの操作の場合と同じように、`Async.RunSynchronously` を呼び出して実行を開始します。

`runAll` 関数は、3 つの非同期ワークフローを並列で起動し、すべてが完了するまで待機します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [コンピュテーション式](computation-expressions.md)
- [Control.Async クラス](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html)
