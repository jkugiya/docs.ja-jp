---
title: GRPC クライアントライブラリの作成-WCF 開発者向け gRPC
description: GRPC サービス用の共有クライアントライブラリ/パッケージについて説明します。
ms.date: 01/06/2021
ms.openlocfilehash: dee62bc793ab384f2556f1b3ff2fcb856c040f3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427571"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="6a76d-103">GRPC クライアントライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="6a76d-103">Create gRPC client libraries</span></span>

<span data-ttu-id="6a76d-104">GRPC アプリケーション用のクライアントライブラリを配布する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6a76d-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="6a76d-105">組織内にファイルの共有ライブラリを作成することができ `.proto` ます。また、他のチームはこれらのファイルを使用して、独自のプロジェクトでクライアントコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6a76d-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="6a76d-106">ただし、プライベート NuGet リポジトリがあり、他の多くのチームが .NET を使用している場合は、サービスプロジェクトの一部としてクライアント NuGet パッケージを作成して発行することができます。</span><span class="sxs-lookup"><span data-stu-id="6a76d-106">But if you have a private NuGet repository and many other teams are using .NET, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="6a76d-107">この方法を使用すると、サービスを共有して昇格させることができます。</span><span class="sxs-lookup"><span data-stu-id="6a76d-107">This approach can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="6a76d-108">クライアントライブラリを配布する利点の1つは、生成された gRPC および Protobuf クラスを、便利な "便利な" メソッドとプロパティを使用して拡張できることです。</span><span class="sxs-lookup"><span data-stu-id="6a76d-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="6a76d-109">クライアントコードでは、サーバーと同様に、すべてのクラスがとして宣言されている `partial` ため、生成されたコードを編集しなくても、それらを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="6a76d-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="6a76d-110">この動作は、コンストラクター、メソッド、および計算されるプロパティを基本的な型に簡単に追加できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6a76d-110">This behavior means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="6a76d-111">カスタムコードを使用して、重要な機能を提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="6a76d-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="6a76d-112">共有ライブラリを使用する .NET チームにこの重要な機能を制限するのではなく、Python や Java などの他の言語やプラットフォームを使用するチームに提供する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6a76d-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="6a76d-113">可能な限り多くのチームが gRPC サービスにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a76d-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="6a76d-114">この機能を実行する最善の方法は、 `.proto` 開発者が独自のクライアントを生成できるようにファイルを共有することです。</span><span class="sxs-lookup"><span data-stu-id="6a76d-114">The best way to do this functionality is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="6a76d-115">このアプローチは、さまざまなチームがさまざまなプログラミング言語やフレームワークを頻繁に使用している場合や、API に外部からアクセスできる場合に、マルチプラットフォーム環境で特に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="6a76d-115">This approach is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="6a76d-116">便利な拡張機能</span><span class="sxs-lookup"><span data-stu-id="6a76d-116">Useful extensions</span></span>

<span data-ttu-id="6a76d-117">.NET では、オブジェクトのストリームを処理するために一般的に使用されるインターフェイスが2つあります。 <xref:System.Collections.Generic.IEnumerable%601> と <xref:System.IObservable%601> です。</span><span class="sxs-lookup"><span data-stu-id="6a76d-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="6a76d-118">.NET Core 3.0 および C# 8.0 以降では、ストリームを <xref:System.Collections.Generic.IAsyncEnumerable%601> 非同期的に処理するためのインターフェイスと、 `await foreach` インターフェイスを使用するための構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="6a76d-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="6a76d-119">このセクションでは、これらのインターフェイスを gRPC ストリームに適用する再利用可能なコードを示します。</span><span class="sxs-lookup"><span data-stu-id="6a76d-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="6a76d-120">.NET gRPC クライアントライブラリには、 `ReadAllAsync` インターフェイスを作成するの拡張メソッドが用意されて `IAsyncStreamReader<T>` `IAsyncEnumerable<T>` います。</span><span class="sxs-lookup"><span data-stu-id="6a76d-120">With the .NET gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="6a76d-121">事後対応型プログラミングを使用する開発者の場合、インターフェイスを作成するための同等の拡張メソッドは、 `IObservable<T>` 次のセクションの例のようになります。</span><span class="sxs-lookup"><span data-stu-id="6a76d-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="6a76d-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="6a76d-122">IObservable</span></span>

<span data-ttu-id="6a76d-123">`IObservable<T>`インターフェイスは、の "リアクティブ" 逆関数です `IEnumerable<T>` 。</span><span class="sxs-lookup"><span data-stu-id="6a76d-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="6a76d-124">ストリームから項目をプルするのではなく、事後対応型のアプローチによって、ストリームをサブスクライバーにプッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="6a76d-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="6a76d-125">この動作は gRPC ストリームによく似ており、インターフェイスのインターフェイスをラップするのは簡単です `IObservable<T>` `IAsyncStreamReader<T>` 。</span><span class="sxs-lookup"><span data-stu-id="6a76d-125">This behavior is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="6a76d-126">C# には `IAsyncEnumerable<T>` observable を操作するためのサポートが組み込まれていないため、このコードはコードよりも長くなっています。</span><span class="sxs-lookup"><span data-stu-id="6a76d-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="6a76d-127">実装クラスは手動で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a76d-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="6a76d-128">ただし、これはジェネリッククラスであるため、1つの実装がすべての型で動作します。</span><span class="sxs-lookup"><span data-stu-id="6a76d-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="6a76d-129">この監視可能な実装により、 `Subscribe` メソッドを1回だけ呼び出すことができます。これは、複数のサブスクライバーがストリームから読み取ろうとすると混乱が生じるためです。</span><span class="sxs-lookup"><span data-stu-id="6a76d-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="6a76d-130">`Replay`Observable では、この実装で使用できるように、バッファリングと反復可能な共有を有効にする、などの演算子が[あります。](https://www.nuget.org/packages/System.Reactive.Linq)</span><span class="sxs-lookup"><span data-stu-id="6a76d-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="6a76d-131">`GrpcStreamSubscription`クラスは、の列挙体を処理し `IAsyncStreamReader` ます。</span><span class="sxs-lookup"><span data-stu-id="6a76d-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="6a76d-132">ここで必要なのは、ストリームリーダーから観測可能なを作成するための単純な拡張メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6a76d-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="6a76d-133">まとめ</span><span class="sxs-lookup"><span data-stu-id="6a76d-133">Summary</span></span>

<span data-ttu-id="6a76d-134"><xref:System.Collections.Generic.IAsyncEnumerable%601>モデルと <xref:System.IObservable%601> モデルは、.net でのデータの非同期ストリームを処理するための適切にサポートされ、適切に記述された方法です。</span><span class="sxs-lookup"><span data-stu-id="6a76d-134">The <xref:System.Collections.Generic.IAsyncEnumerable%601> and <xref:System.IObservable%601> models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="6a76d-135">gRPC ストリームは、両方のパラダイムに適しており、.NET との密接な統合と、事後対応と非同期のプログラミングスタイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="6a76d-135">gRPC streams map well to both paradigms, offering close integration with .NET, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6a76d-136">[前へ](streaming-versus-repeated.md)
>[次へ](security.md)</span><span class="sxs-lookup"><span data-stu-id="6a76d-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
