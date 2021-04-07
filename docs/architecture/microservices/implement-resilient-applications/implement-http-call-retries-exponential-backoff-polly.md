---
title: Polly で指数バックオフを含む HTTP 呼び出しの再試行を実装する
description: HTTP エラーを Polly と IHttpClientFactory で処理する方法について説明します
ms.date: 01/13/2021
ms.openlocfilehash: cd209aa7f2802ffea80e14f0e3e77cc4fc29b6d5
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122964"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>IHttpClientFactory ポリシーと Polly ポリシーで指数バックオフを含む HTTP 呼び出しの再試行を実装する

指数のバックオフでの再試行のためのアプローチとしては、オープン ソースである [Polly ライブラリ](https://github.com/App-vNext/Polly)のような高度な .NET ライブラリを利用することをお勧めします。

Polly とは、回復機能と一時的な障害処理の機能を提供する .NET ライブラリです。 このような機能は、再試行、遮断器、バルクヘッド分離、タイムアウト、フォールバックなどの Polly ポリシーを適用することで実装できます。 Polly は .NET Framework 4.x と .NET Standard 1.0、1.1、および 2.0 (.NET Core 以降をサポート) を対象としています。

次の手順では、前のセクションで説明した、`IHttpClientFactory` に統合された Polly で HTTP 再試行を使用する方法を示します。

**.NET 5 パッケージの参照**

`IHttpClientFactory` は .NET Core 2.1 以降で使用できますが、最新の .NET 5 パッケージを NuGet から入手し、プロジェクトで使用することをお勧めします。 また、通常は `Microsoft.Extensions.Http.Polly` 拡張機能パッケージを参照する必要もあります。

**Startup で、Polly の再試行ポリシーでクライアントを構成する**

前のセクションで示したように、標準の Startup.ConfigureServices(...) メソッドで、名前または型が指定された HttpClient 構成を定義する必要がありますが、今後は以下のように、指数バックオフを含む HTTP 再試行のポリシーを指定し、増分コードを追加します。

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** メソッドは、使用する `HttpClient` オブジェクトにポリシーを追加します。 この場合、指数バックオフを含む HTTP 再試行に対して Polly のポリシーが追加されます。

手法のモジュール性を高めるために、次のコードで示すように、`Startup.cs` ファイル内の個別メソッドに HTTP 再試行ポリシーを定義できます。

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

Polly では、再試行回数を指定した再試行ポリシー、指数バックオフの構成、HTTP 例外が発生した場合に実行するアクション (エラーの記録など) を定義できます。 上記のコードでは、指数関数的再試行で (最初は 2 秒) 6 回試すようにポリシーが構成されています。

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>再試行ポリシーにジッタ方式を追加する

通常の再試行ポリシーは、コンカレンシーやスケーラビリティが高い場合や、高競合状態下でシステムに影響を及ぼすことがあります。 部分的な停止で多くのクライアントから来る同様の再試行のピークを乗り越えるための賢い回避策は、ジッタ方式を再試行アルゴリズムまたはポリシーに追加することです。 この戦略により、エンドツーエンド システムの全体的なパフォーマンスを向上させることができます。 [Polly: Retry with Jitter](https://github.com/App-vNext/Polly/wiki/Retry-with-jitter) (ジッタで再試行) で推奨されているように、指数バックオフでの初期再試行遅延の中央値を適切に制御して、スムーズで均等に分散された再試行間隔を適用することで、優れたジッタ戦略を実施できます。 この方法は、問題が発生したときにスパイクを分散させることができます。 この原則を次の例で示します。

```csharp

var delay = Backoff.DecorrelatedJitterBackoffV2(medianFirstRetryDelay: TimeSpan.FromSeconds(1), retryCount: 5);

var retryPolicy = Policy
    .Handle<FooException>()
    .WaitAndRetryAsync(delay);
```

## <a name="additional-resources"></a>その他の技術情報

- **再試行パターン**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly および IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (.NET の復元および一時的な障害処理ライブラリ)**  
  <https://github.com/App-vNext/Polly>

- **Polly: ジッタで再試行**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marc Brooker.ジッタ:ランダム性を使って状況を改善する**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[前へ](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[次へ](implement-circuit-breaker-pattern.md)
