---
title: .NET にカスタム ログ プロバイダーを実装する
description: .NET アプリケーションにカスタム ログ プロバイダーを実装する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.topic: how-to
ms.openlocfilehash: 3a0af6296c2ade15ff1b75dce5a5f99bfe235ebf
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2020
ms.locfileid: "102401994"
---
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="2dd26-103">.NET にカスタム ログ プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="2dd26-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="2dd26-104">一般的なログのニーズに使用できる[ログ プロバイダー](logging-providers.md)は、数多くあります。</span><span class="sxs-lookup"><span data-stu-id="2dd26-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="2dd26-105">利用可能なプロバイダーの 1 つがアプリケーションのニーズに合わない場合は、カスタム <xref:Microsoft.Extensions.Logging.ILoggerProvider> を実装する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="2dd26-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="2dd26-106">この記事では、コンソールでログの色付けをするために使用できるカスタム ログ プロバイダーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2dd26-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="2dd26-107">カスタム ロガーの構成のサンプル</span><span class="sxs-lookup"><span data-stu-id="2dd26-107">Sample custom logger configuration</span></span>

<span data-ttu-id="2dd26-108">このサンプルは、次の構成の種類を使用して、ログ レベルとイベント ID ごとに異なるカラー コンソール エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2dd26-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="2dd26-109">上記のコードでは、既定のレベルを `Information` に設定し、色を `Green` に設定します。`EventId` は暗黙的に `0` です。</span><span class="sxs-lookup"><span data-stu-id="2dd26-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="2dd26-110">カスタム ロガーを作成する</span><span class="sxs-lookup"><span data-stu-id="2dd26-110">Create the custom logger</span></span>

<span data-ttu-id="2dd26-111">`ILogger` 実装カテゴリ名は、通常、ログ ソースです。</span><span class="sxs-lookup"><span data-stu-id="2dd26-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="2dd26-112">たとえば、ロガーが作成される型は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2dd26-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="2dd26-113">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="2dd26-113">The preceding code:</span></span>

- <span data-ttu-id="2dd26-114">カテゴリ名ごとにロガー インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2dd26-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="2dd26-115">各 `logLevel` に一意のロガーがあるようにするため、`IsEnabled` で `logLevel == _config.LogLevel` を確認します。</span><span class="sxs-lookup"><span data-stu-id="2dd26-115">Checks `logLevel == _config.LogLevel` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="2dd26-116">ロガーは、すべての上位ログ レベルに対しても有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dd26-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="2dd26-117">カスタム ロガー プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2dd26-117">Custom logger provider</span></span>

<span data-ttu-id="2dd26-118">`ILoggerProvider` オブジェクトは、ロガー インスタンスを作成する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="2dd26-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="2dd26-119">カテゴリごとにロガー インスタンスを作成する必要はないかもしれませんが、これは NLog や log4net などの一部のロガーでは理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="2dd26-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="2dd26-120">これを行うと、必要に応じて、カテゴリごとに異なるログ出力ターゲットを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="2dd26-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="2dd26-121">上記のコードでは、<xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> によってカテゴリ名ごとに `ColorConsoleLogger` のインスタンスが 1 つ作成され、それが [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) に格納されます。</span><span class="sxs-lookup"><span data-stu-id="2dd26-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="2dd26-122">カスタム ロガーの使用と登録</span><span class="sxs-lookup"><span data-stu-id="2dd26-122">Usage and registration of the custom logger</span></span>

<span data-ttu-id="2dd26-123">カスタム ログ プロバイダーおよび対応するロガーを追加するには、<xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> から <xref:Microsoft.Extensions.Logging.ILoggerProvider> と <xref:Microsoft.Extensions.Logging.ILoggingBuilder> を追加します。</span><span class="sxs-lookup"><span data-stu-id="2dd26-123">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

<span data-ttu-id="2dd26-124">`ILoggingBuilder` により、1 つ以上の `ILogger` インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2dd26-124">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="2dd26-125">`ILogger` インスタンスは、情報をログに記録するためにフレームワークによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="2dd26-125">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="2dd26-126">上記のコードでは、`ILoggerFactory` に少なくとも 1 つの拡張メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="2dd26-126">For the preceding code, provide at least one extension method for the `ILoggerFactory`:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="2dd26-127">この単純なアプリケーションを実行すると、次のようなコンソール ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dd26-127">Running this simple application will render similar to the following console window:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="カラー コンソール ロガーのサンプル出力":::

## <a name="see-also"></a><span data-ttu-id="2dd26-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dd26-129">See also</span></span>

- <span data-ttu-id="2dd26-130">[.NET でのログ](logging.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-130">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="2dd26-131">[.NET でのログ プロバイダー](logging-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-131">[Logging providers in .NET](logging-providers.md).</span></span>
- <span data-ttu-id="2dd26-132">[.NET での高パフォーマンスのログ](high-performance-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="2dd26-132">[High-performance logging in .NET](high-performance-logging.md).</span></span>
