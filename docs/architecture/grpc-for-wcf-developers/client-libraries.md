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
# <a name="create-grpc-client-libraries"></a>gRPC クライアント ライブラリを作成する

gRPC アプリケーション用のクライアント ライブラリを配布する必要はありません。 組織内に `.proto` ファイルの共有ライブラリを作成することができます。他のチームは、これらのファイルを使用して、各自のプロジェクトでクライアント コードを生成できます。 ただし、プライベート NuGet リポジトリがあり、他の多くのチームが .NET を使用している場合は、サービス プロジェクトの一部としてクライアント NuGet パッケージを作成して発行することができます。 この方法を使用すると、サービスを共有して昇格させることができます。

クライアント ライブラリを配布する利点の 1 つは、生成された gRPC および Protobuf クラスを、有益で "便利な" メソッドとプロパティを使用して拡張できることです。 クライアント コードでは、サーバーと同様に、すべてのクラスが `partial` として宣言されるため、生成されたコードを編集せずにそれらを拡張できます。 この動作は、コンストラクター、メソッド、および計算されるプロパティを基本型に簡単に追加できることを意味します。

> [!CAUTION]
> カスタム コードを使用して、重要な機能を用意しないでください。 その重要な機能を共有ライブラリを使用する .NET チームに制限する必要はなく、Python や Java などの他の言語やプラットフォームを使用するチームに提供しないようにする必要もありません。

可能な限り多くのチームが gRPC サービスにアクセスできることを確認します。 この機能を実行する最善の方法は、開発者が独自のクライアントを生成できるように `.proto` ファイルを共有することです。 このアプローチは、複数のチームがさまざまなプログラミング言語やフレームワークを頻繁に使用したり、API に外部からアクセスできたりするマルチプラットフォーム環境に特に当てはまります。

## <a name="useful-extensions"></a>便利な拡張機能

.NET では、オブジェクトのストリームを処理するために一般的に使用されるインターフェイスが 2 つあります。<xref:System.Collections.Generic.IEnumerable%601> と <xref:System.IObservable%601> です。 .NET Core 3.0 と C# 8.0 以降では、ストリームを非同期的に処理するための <xref:System.Collections.Generic.IAsyncEnumerable%601> インターフェイスと、インターフェイスを使用するための `await foreach` 構文が用意されています。 このセクションでは、これらのインターフェイスを gRPC ストリームに適用する再利用可能なコードを示します。

.NET gRPC クライアント ライブラリには、`IAsyncEnumerable<T>` インターフェイスを作成する `IAsyncStreamReader<T>` の `ReadAllAsync` 拡張メソッドがあります。 リアクティブ プログラミングを使用する開発者の場合、`IObservable<T>` インターフェイスを作成するための同等の拡張メソッドは、次のセクションの例のようになります。

### <a name="iobservable"></a>IObservable

`IObservable<T>` インターフェイスは、`IEnumerable<T>` の "リアクティブな" 反転です。 ストリームから項目をプルするのではなく、リアクティブ アプローチによって、ストリームでサブスクライバーに項目をプッシュさせることができます。 この動作は gRPC ストリームによく似ており、`IObservable<T>` インターフェイスで `IAsyncStreamReader<T>` インターフェイスをラップするのは簡単です。

C# には Observable を操作するためのサポートが組み込まれていないため、このコードは `IAsyncEnumerable<T>` コードよりも長くなっています。 実装クラスは手動で作成する必要があります。 ただし、それはジェネリック クラスであるため、単一の実装ですべての型が動作します。

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
> この Observable の実装により、`Subscribe` メソッドを 1 回だけ呼び出すことができます。これは、複数のサブスクライバーがストリームから読み取ろうとすると混乱が生じるためです。 この実装では、Observable のバッファリングと反復可能な共有を有効にする演算子 ([System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) の `Replay` など) を使用できます。

`GrpcStreamSubscription` クラスは、`IAsyncStreamReader` の列挙型を処理します。

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

ここで必要なのは、ストリーム リーダーから Observable を作成するための単純な拡張メソッドです。

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

## <a name="summary"></a>まとめ

<xref:System.Collections.Generic.IAsyncEnumerable%601> モデルと <xref:System.IObservable%601> モデルは、.NET でのデータの非同期ストリームを処理するための適切にサポートされ、適切に記述されている方法です。 gRPC ストリームは、両方のパラダイムに適しており、.NET との密接な統合と、リアクティブな非同期のプログラミング スタイルを提供します。

>[!div class="step-by-step"]
>[前へ](streaming-versus-repeated.md)
>[次へ](security.md)
