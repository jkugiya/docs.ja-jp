---
title: gRPC クライアント ライブラリを作成する - WCF 開発者向け gRPC
description: gRPC サービス用の共有クライアント ライブラリ/パッケージについて説明します。
ms.date: 01/06/2021
ms.openlocfilehash: dee62bc793ab384f2556f1b3ff2fcb856c040f3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427571"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="578ec-103">gRPC クライアント ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="578ec-103">Create gRPC client libraries</span></span>

<span data-ttu-id="578ec-104">gRPC アプリケーション用のクライアント ライブラリを配布する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="578ec-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="578ec-105">組織内に `.proto` ファイルの共有ライブラリを作成することができます。他のチームは、これらのファイルを使用して、各自のプロジェクトでクライアント コードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="578ec-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="578ec-106">ただし、プライベート NuGet リポジトリがあり、他の多くのチームが .NET を使用している場合は、サービス プロジェクトの一部としてクライアント NuGet パッケージを作成して発行することができます。</span><span class="sxs-lookup"><span data-stu-id="578ec-106">But if you have a private NuGet repository and many other teams are using .NET, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="578ec-107">この方法を使用すると、サービスを共有して昇格させることができます。</span><span class="sxs-lookup"><span data-stu-id="578ec-107">This approach can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="578ec-108">クライアント ライブラリを配布する利点の 1 つは、生成された gRPC および Protobuf クラスを、有益で "便利な" メソッドとプロパティを使用して拡張できることです。</span><span class="sxs-lookup"><span data-stu-id="578ec-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="578ec-109">クライアント コードでは、サーバーと同様に、すべてのクラスが `partial` として宣言されるため、生成されたコードを編集せずにそれらを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="578ec-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="578ec-110">この動作は、コンストラクター、メソッド、および計算されるプロパティを基本型に簡単に追加できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="578ec-110">This behavior means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="578ec-111">カスタム コードを使用して、重要な機能を用意しないでください。</span><span class="sxs-lookup"><span data-stu-id="578ec-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="578ec-112">その重要な機能を共有ライブラリを使用する .NET チームに制限する必要はなく、Python や Java などの他の言語やプラットフォームを使用するチームに提供しないようにする必要もありません。</span><span class="sxs-lookup"><span data-stu-id="578ec-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="578ec-113">可能な限り多くのチームが gRPC サービスにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="578ec-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="578ec-114">この機能を実行する最善の方法は、開発者が独自のクライアントを生成できるように `.proto` ファイルを共有することです。</span><span class="sxs-lookup"><span data-stu-id="578ec-114">The best way to do this functionality is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="578ec-115">このアプローチは、複数のチームがさまざまなプログラミング言語やフレームワークを頻繁に使用したり、API に外部からアクセスできたりするマルチプラットフォーム環境に特に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="578ec-115">This approach is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="578ec-116">便利な拡張機能</span><span class="sxs-lookup"><span data-stu-id="578ec-116">Useful extensions</span></span>

<span data-ttu-id="578ec-117">.NET では、オブジェクトのストリームを処理するために一般的に使用されるインターフェイスが 2 つあります。<xref:System.Collections.Generic.IEnumerable%601> と <xref:System.IObservable%601> です。</span><span class="sxs-lookup"><span data-stu-id="578ec-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="578ec-118">.NET Core 3.0 と C# 8.0 以降では、ストリームを非同期的に処理するための <xref:System.Collections.Generic.IAsyncEnumerable%601> インターフェイスと、インターフェイスを使用するための `await foreach` 構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="578ec-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="578ec-119">このセクションでは、これらのインターフェイスを gRPC ストリームに適用する再利用可能なコードを示します。</span><span class="sxs-lookup"><span data-stu-id="578ec-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="578ec-120">.NET gRPC クライアント ライブラリには、`IAsyncEnumerable<T>` インターフェイスを作成する `IAsyncStreamReader<T>` の `ReadAllAsync` 拡張メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="578ec-120">With the .NET gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="578ec-121">リアクティブ プログラミングを使用する開発者の場合、`IObservable<T>` インターフェイスを作成するための同等の拡張メソッドは、次のセクションの例のようになります。</span><span class="sxs-lookup"><span data-stu-id="578ec-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="578ec-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="578ec-122">IObservable</span></span>

<span data-ttu-id="578ec-123">`IObservable<T>` インターフェイスは、`IEnumerable<T>` の "リアクティブな" 反転です。</span><span class="sxs-lookup"><span data-stu-id="578ec-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="578ec-124">ストリームから項目をプルするのではなく、リアクティブ アプローチによって、ストリームでサブスクライバーに項目をプッシュさせることができます。</span><span class="sxs-lookup"><span data-stu-id="578ec-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="578ec-125">この動作は gRPC ストリームによく似ており、`IObservable<T>` インターフェイスで `IAsyncStreamReader<T>` インターフェイスをラップするのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="578ec-125">This behavior is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="578ec-126">C# には Observable を操作するためのサポートが組み込まれていないため、このコードは `IAsyncEnumerable<T>` コードよりも長くなっています。</span><span class="sxs-lookup"><span data-stu-id="578ec-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="578ec-127">実装クラスは手動で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="578ec-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="578ec-128">ただし、それはジェネリック クラスであるため、単一の実装ですべての型が動作します。</span><span class="sxs-lookup"><span data-stu-id="578ec-128">It's a generic class, though, so a single implementation works across all types.</span></span>

```csharp
using System;
using System.Threading;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public GrpcStreamObservable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader ?? throw new ArgumentNullException(nameof(reader));
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription<T>(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="578ec-129">この Observable の実装により、`Subscribe` メソッドを 1 回だけ呼び出すことができます。これは、複数のサブスクライバーがストリームから読み取ろうとすると混乱が生じるためです。</span><span class="sxs-lookup"><span data-stu-id="578ec-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="578ec-130">この実装では、Observable のバッファリングと反復可能な共有を有効にする演算子 ([System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) の `Replay` など) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="578ec-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="578ec-131">`GrpcStreamSubscription` クラスは、`IAsyncStreamReader` の列挙型を処理します。</span><span class="sxs-lookup"><span data-stu-id="578ec-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

```csharp
public class GrpcStreamSubscription<T> : IDisposable
{
    private readonly IAsyncStreamReader<T> _reader;
    private readonly IObserver<T> _observer;

    private readonly CancellationTokenSource _tokenSource;

    private readonly Task _task;

    private bool _completed;

    public GrpcStreamSubscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token = default)
    {
        _reader = reader ?? throw new ArgumentNullException(nameof(reader));
        _observer = observer ?? throw new ArgumentNullException(nameof(observer));

        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);

        _task = Run(_tokenSource.Token);
    }

    private async Task Run(CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await _reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                _observer.OnError(e);
                _completed = true;
                return;
            }

            _observer.OnNext(_reader.Current);
        }

        _completed = true;
        _observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

<span data-ttu-id="578ec-132">ここで必要なのは、ストリーム リーダーから Observable を作成するための単純な拡張メソッドです。</span><span class="sxs-lookup"><span data-stu-id="578ec-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

```csharp
using System;
using System.Threading;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(
            this IAsyncStreamReader<T> reader,
            CancellationToken cancellationToken = default) =>
            new GrpcStreamObservable<T>(reader, cancellationToken);
    }
}
```

## <a name="summary"></a><span data-ttu-id="578ec-133">まとめ</span><span class="sxs-lookup"><span data-stu-id="578ec-133">Summary</span></span>

<span data-ttu-id="578ec-134"><xref:System.Collections.Generic.IAsyncEnumerable%601> モデルと <xref:System.IObservable%601> モデルは、.NET でのデータの非同期ストリームを処理するための適切にサポートされ、適切に記述されている方法です。</span><span class="sxs-lookup"><span data-stu-id="578ec-134">The <xref:System.Collections.Generic.IAsyncEnumerable%601> and <xref:System.IObservable%601> models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="578ec-135">gRPC ストリームは、両方のパラダイムに適しており、.NET との密接な統合と、リアクティブな非同期のプログラミング スタイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="578ec-135">gRPC streams map well to both paradigms, offering close integration with .NET, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="578ec-136">[前へ](streaming-versus-repeated.md)
>[次へ](security.md)</span><span class="sxs-lookup"><span data-stu-id="578ec-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
