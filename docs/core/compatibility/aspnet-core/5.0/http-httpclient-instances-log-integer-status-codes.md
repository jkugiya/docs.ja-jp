---
title: 破壊的変更:HTTP:IHttpClientFactory ログの整数状態コードによって作成された HttpClient インスタンス
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: HTTP:IHttpClientFactory ログの整数状態コードによって作成された HttpClient インスタンス'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 59e64c7127a97b1c11587d13803e4a085dbc090b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497685"
---
# <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="81621-103">HTTP:IHttpClientFactory ログの整数状態コードによって作成された HttpClient インスタンス</span><span class="sxs-lookup"><span data-stu-id="81621-103">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="81621-104"><xref:System.Net.Http.IHttpClientFactory> によって作成された <xref:System.Net.Http.HttpClient> インスタンスでは、HTTP 状態コードが、状態コード名を付加するのではなく、整数としてログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="81621-104"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="81621-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="81621-105">Version introduced</span></span>

<span data-ttu-id="81621-106">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="81621-106">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="81621-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="81621-107">Old behavior</span></span>

<span data-ttu-id="81621-108">ログの HTTP 状態コードに説明テキストが使用されます。</span><span class="sxs-lookup"><span data-stu-id="81621-108">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="81621-109">次にログ メッセージの例を示します。</span><span class="sxs-lookup"><span data-stu-id="81621-109">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

## <a name="new-behavior"></a><span data-ttu-id="81621-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="81621-110">New behavior</span></span>

<span data-ttu-id="81621-111">ログの HTTP 状態コードに整数値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="81621-111">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="81621-112">次にログ メッセージの例を示します。</span><span class="sxs-lookup"><span data-stu-id="81621-112">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

## <a name="reason-for-change"></a><span data-ttu-id="81621-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="81621-113">Reason for change</span></span>

<span data-ttu-id="81621-114">このログの元の動作では、常に整数値が使用されている ASP.NET Core の他の部分と一貫性がありません。</span><span class="sxs-lookup"><span data-stu-id="81621-114">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="81621-115">一貫性がないため、[Elasticsearch](https://www.elastic.co/elasticsearch/) などの構造化ログ システムを使用したログのクエリが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="81621-115">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="81621-116">詳細については、[dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81621-116">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="81621-117">整数値を使用すると、値の範囲に対してクエリを実行できるようになるため、テキストよりも柔軟性が向上します。</span><span class="sxs-lookup"><span data-stu-id="81621-117">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="81621-118">整数の状態コードを取得するログ値を別に追加することが検討されました。</span><span class="sxs-lookup"><span data-stu-id="81621-118">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="81621-119">残念ながら、これを行うと、ASP.NET Core の残りの部分にさらに不整合が生じます。</span><span class="sxs-lookup"><span data-stu-id="81621-119">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="81621-120">HttpClient ログと HTTP サーバー/ホスト ログで既に同じ `StatusCode` キー名が使用されています。</span><span class="sxs-lookup"><span data-stu-id="81621-120">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="81621-121">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="81621-121">Recommended action</span></span>

<span data-ttu-id="81621-122">最適なオプションは、状態コードの整数値を使用するようにログ クエリを更新することです。</span><span class="sxs-lookup"><span data-stu-id="81621-122">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="81621-123">このオプションを選択すると、複数の ASP.NET Core バージョンに対するクエリの作成が難しくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="81621-123">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="81621-124">しかしながら、整数をこの目的に使用すると、ログのクエリの柔軟性が大きく向上します。</span><span class="sxs-lookup"><span data-stu-id="81621-124">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="81621-125">以前の動作との互換性を維持し、テキスト形式の状態コードを使用する必要がある場合は、`IHttpClientFactory` ログを独自のものに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="81621-125">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="81621-126">次のクラスの .NET Core 3.1 バージョンをプロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="81621-126">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="81621-127">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="81621-127">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="81621-128">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="81621-128">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="81621-129">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="81621-129">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="81621-130">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="81621-130">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="81621-131">[Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet パッケージでパブリック型との競合を避けるために、クラスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="81621-131">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="81621-132">プロジェクトの `Startup.ConfigureServices` メソッドで、`LoggingHttpMessageHandlerBuilderFilter` の組み込みの実装を独自のものに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="81621-132">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="81621-133">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="81621-133">For example:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        services.RemoveAll<IHttpMessageHandlerBuilderFilter>();

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="81621-134">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="81621-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:System.Net.Http.HttpClient`

-->
