---
title: .NET にカスタム ログ プロバイダーを実装する
description: .NET アプリケーションにカスタム ログ プロバイダーを実装する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 04/07/2021
ms.topic: how-to
ms.openlocfilehash: 56dd3aa9962d2cdaf13df85960a99aab7b050477
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255130"
---
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="0cfbe-103">.NET にカスタム ログ プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="0cfbe-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="0cfbe-104">一般的なログのニーズに使用できる[ログ プロバイダー](logging-providers.md)は、数多くあります。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="0cfbe-105">利用可能なプロバイダーの 1 つがアプリケーションのニーズに合わない場合は、カスタム <xref:Microsoft.Extensions.Logging.ILoggerProvider> を実装する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="0cfbe-106">この記事では、コンソールでログの色付けをするために使用できるカスタム ログ プロバイダーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="0cfbe-107">カスタム ロガーの構成のサンプル</span><span class="sxs-lookup"><span data-stu-id="0cfbe-107">Sample custom logger configuration</span></span>

<span data-ttu-id="0cfbe-108">このサンプルは、次の構成の種類を使用して、ログ レベルとイベント ID ごとに異なるカラー コンソール エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="0cfbe-109">上記のコードでは、既定のレベルを `Information` に設定し、色を `Green` に設定します。`EventId` は暗黙的に `0` です。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="0cfbe-110">カスタム ロガーを作成する</span><span class="sxs-lookup"><span data-stu-id="0cfbe-110">Create the custom logger</span></span>

<span data-ttu-id="0cfbe-111">`ILogger` 実装カテゴリ名は、通常、ログ ソースです。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="0cfbe-112">たとえば、ロガーが作成される型は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="0cfbe-113">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-113">The preceding code:</span></span>

- <span data-ttu-id="0cfbe-114">カテゴリ名ごとにロガー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="0cfbe-115">各 `logLevel` に一意のロガーがあるようにするため、`IsEnabled` で `_config.LogLevels.ContainsKey(logLevel)` を確認します。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-115">Checks `_config.LogLevels.ContainsKey(logLevel)` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="0cfbe-116">ロガーは、すべての上位ログ レベルに対しても有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="0cfbe-117">カスタム ロガー プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0cfbe-117">Custom logger provider</span></span>

<span data-ttu-id="0cfbe-118">`ILoggerProvider` オブジェクトは、ロガー インスタンスを作成する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="0cfbe-119">カテゴリごとにロガー インスタンスを作成する必要はないかもしれませんが、これは NLog や log4net などの一部のロガーでは理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="0cfbe-120">これを行うと、必要に応じて、カテゴリごとに異なるログ出力ターゲットを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="0cfbe-121">上記のコードでは、<xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> によってカテゴリ名ごとに `ColorConsoleLogger` のインスタンスが 1 つ作成され、それが [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span> <span data-ttu-id="0cfbe-122">また、<xref:Microsoft.Extensions.Options.IOptionsMonitor%601> インターフェイスが、基になる `ColorConsoleLoggerConfiguration` オブジェクトに対する変更を更新するために必要です。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-122">Additionally, the <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> interface is required to update changes to the underlying `ColorConsoleLoggerConfiguration` object.</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="0cfbe-123">カスタム ロガーの使用と登録</span><span class="sxs-lookup"><span data-stu-id="0cfbe-123">Usage and registration of the custom logger</span></span>

<span data-ttu-id="0cfbe-124">カスタム ログ プロバイダーおよび対応するロガーを追加するには、<xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> から <xref:Microsoft.Extensions.Logging.ILoggerProvider> と <xref:Microsoft.Extensions.Logging.ILoggingBuilder> を追加します。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-124">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-33":::

<span data-ttu-id="0cfbe-125">`ILoggingBuilder` により、1 つ以上の `ILogger` インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-125">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="0cfbe-126">`ILogger` インスタンスは、情報をログに記録するためにフレームワークによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-126">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="0cfbe-127">慣例により、`ILoggingBuilder` の拡張メソッドを使用して、カスタム プロバイダーが登録されます。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-127">By convention, extension methods on `ILoggingBuilder` are used to register the custom provider:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="0cfbe-128">この単純なアプリケーションを実行すると、次の図のような色の出力がコンソール ウィンドウにレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="0cfbe-128">Running this simple application will render color output to the console window similar to the following image:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="カラー コンソール ロガーのサンプル出力":::

## <a name="see-also"></a><span data-ttu-id="0cfbe-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cfbe-130">See also</span></span>

- [<span data-ttu-id="0cfbe-131">.NET でのログの記録</span><span class="sxs-lookup"><span data-stu-id="0cfbe-131">Logging in .NET</span></span>](logging.md)
- [<span data-ttu-id="0cfbe-132">.NET でのログ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0cfbe-132">Logging providers in .NET</span></span>](logging-providers.md)
- [<span data-ttu-id="0cfbe-133">.NET での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="0cfbe-133">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="0cfbe-134">.NET での高パフォーマンスのログ</span><span class="sxs-lookup"><span data-stu-id="0cfbe-134">High-performance logging in .NET</span></span>](high-performance-logging.md)
