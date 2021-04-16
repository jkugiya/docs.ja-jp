---
title: モジュール、ハンドラー、ミドルウェア
description: モジュール、ハンドラー、およびミドルウェアによる HTTP 要求の処理について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 10/11/2019
ms.openlocfilehash: dbb0a94b0401d58139c024fd8ca3e00353a19efa
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "97678029"
---
# <a name="modules-handlers-and-middleware"></a>モジュール、ハンドラー、ミドルウェア

ASP.NET Core アプリは一連の *ミドルウェア* に基づいて構築されます。 ミドルウェアは、要求と応答を処理するためにパイプラインに配置されるハンドラーです。 Web Forms アプリでは、HTTP ハンドラーとモジュールによって同様の問題が解決されます。 ASP.NET Core では、モジュール、ハンドラー、*global.asax*、およびアプリのライフ サイクルはミドルウェアに置き換えられます。 この章では、Blazor アプリのコンテキストでのミドルウェアについて説明します。

## <a name="overview"></a>概要

ASP.NET Core 要求パイプラインは、順番に呼び出される一連の要求デリゲートで構成されています。 次の図は、その概念を示しています。 実行のスレッドは黒い矢印をたどります。

![pipeline](media/middleware/request-delegate-pipeline.png)

上の図には、ライフサイクル イベントの概念がありません。 この概念は、ASP.NET Web Forms 要求がどのように処理されるかの基礎となります。 このシステムにより、どのようなプロセスが発生しているかを判断しやすくなり、どの時点でもミドルウェアを挿入できるようになります。 ミドルウェアは、要求パイプラインに追加された順序で実行されます。 それらは、構成ファイル (通常、*Startup.cs* 内) ではなくコードにも追加されます。

## <a name="katana"></a>Katana

Katana に慣れている読者は、ASP.NET Core に不安を感じないでしょう。 実際に、Katana は、ASP.NET Core から派生したフレームワークです。 ASP.NET 4.x に似たミドルウェアとパイプライン パターンが導入されています。 Katana 用に設計されたミドルウェアは、ASP.NET Core パイプラインで動作するように適合させることができます。

## <a name="common-middleware"></a>共通のミドルウェア

ASP.NET 4.x には多くのモジュールが含まれています。 同様に、ASP.NET Core にも多くのミドルウェア コンポーネントが用意されています。 ASP.NET Core を使用した特定の事例では、IIS モジュールを使用できます。 他の事例では、ネイティブ ASP.NET Core ミドルウェアも使用できます。

次の表に、ASP.NET Core での代替のミドルウェアとコンポーネントの一覧を示します。

|モジュール                 |ASP.NET 4.x           |ASP.NET Core オプション|
|-----------------------|-----------------------------|-------------------|
|HTTP エラー            |`CustomErrorModule`          |[状態コード ページ ミドルウェア](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|既定のドキュメント       |`DefaultDocumentModule`      |[既定のファイル ミドルウェア](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|ディレクトリ参照     |`DirectoryListingModule`     |[ディレクトリ参照ミドルウェア](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|動的な圧縮    |`DynamicCompressionModule`   |[応答圧縮ミドルウェア](/aspnet/core/performance/response-compression)|
|失敗した要求のトレース|`FailedRequestsTracingModule`|[ASP.NET Core のログ](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|ファイル キャッシュ           |`FileCacheModule`            |[応答キャッシュ ミドルウェア](/aspnet/core/performance/caching/middleware)|
|HTTP キャッシュ           |`HttpCacheModule`            |[応答キャッシュ ミドルウェア](/aspnet/core/performance/caching/middleware)|
|HTTP ログ           |`HttpLoggingModule`          |[ASP.NET Core のログ](/aspnet/core/fundamentals/logging/index)|
|HTTP リダイレクト       |`HttpRedirectionModule`      |[URL リライト ミドルウェア](/aspnet/core/fundamentals/url-rewriting)|
|ISAPI フィルター          |`IsapiFilterModule`          |[ミドルウェア](/aspnet/core/fundamentals/middleware/index)|
|ISAPI                  |`IsapiModule`                |[ミドルウェア](/aspnet/core/fundamentals/middleware/index)|
|要求のフィルタリング      |`RequestFilteringModule`     |[URL リライト ミドルウェア IRule](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|URL リライト&#8224;   |`RewriteModule`              |[URL リライト ミドルウェア](/aspnet/core/fundamentals/url-rewriting)|
|静的圧縮     |`StaticCompressionModule`    |[応答圧縮ミドルウェア](/aspnet/core/performance/response-compression)|
|静的コンテンツ         |`StaticFileModule`           |[静的ファイル ミドルウェア](/aspnet/core/fundamentals/static-files)|
|URL 承認      |`UrlAuthorizationModule`     |[ASP.NET Core ID](/aspnet/core/security/authentication/identity)|

この一覧は完全に網羅したものではありませんが、2 つのフレームワーク間にどのようなマッピングが存在するのかを把握できるはずです。 詳細な一覧については、「[ASP.NET Core での IIS モジュール](/aspnet/core/host-and-deploy/iis/modules)」を参照してください。

## <a name="custom-middleware"></a>カスタム ミドルウェア

組み込みのミドルウェアでは、アプリに必要なすべてのシナリオを処理することはできません。 そのような場合は、独自のミドルウェアを作成することが理にかなっています。 ミドルウェアを定義する方法は複数ありますが、最も簡単なのは単純な委任です。 クエリ文字列からカルチャ要求を受け取る次のミドルウェアを考えます。

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

ミドルウェアは、`IMiddleware` インターフェイスを実装するか、次のミドルウェア規則に従って、クラスとして定義することもできます。 詳細については、「[カスタム ASP.NET Core ミドルウェアを記述する](/aspnet/core/fundamentals/middleware/write)」を参照してください。

>[!div class="step-by-step"]
>[前へ](data.md)
>[次へ](config.md)
