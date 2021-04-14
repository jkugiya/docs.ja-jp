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
# <a name="implement-a-custom-logging-provider-in-net"></a>.NET にカスタム ログ プロバイダーを実装する

一般的なログのニーズに使用できる[ログ プロバイダー](logging-providers.md)は、数多くあります。 利用可能なプロバイダーの 1 つがアプリケーションのニーズに合わない場合は、カスタム <xref:Microsoft.Extensions.Logging.ILoggerProvider> を実装する必要がある場合があります。 この記事では、コンソールでログの色付けをするために使用できるカスタム ログ プロバイダーを実装する方法について説明します。

### <a name="sample-custom-logger-configuration"></a>カスタム ロガーの構成のサンプル

このサンプルは、次の構成の種類を使用して、ログ レベルとイベント ID ごとに異なるカラー コンソール エントリを作成します。

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

上記のコードでは、既定のレベルを `Information` に設定し、色を `Green` に設定します。`EventId` は暗黙的に `0` です。

### <a name="create-the-custom-logger"></a>カスタム ロガーを作成する

`ILogger` 実装カテゴリ名は、通常、ログ ソースです。 たとえば、ロガーが作成される型は次のようになります。

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

上記のコードでは次の操作が行われます。

- カテゴリ名ごとにロガー インスタンスを作成します。
- 各 `logLevel` に一意のロガーがあるようにするため、`IsEnabled` で `_config.LogLevels.ContainsKey(logLevel)` を確認します。 ロガーは、すべての上位ログ レベルに対しても有効にする必要があります。

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a>カスタム ロガー プロバイダー

`ILoggerProvider` オブジェクトは、ロガー インスタンスを作成する役割を担います。 カテゴリごとにロガー インスタンスを作成する必要はないかもしれませんが、これは NLog や log4net などの一部のロガーでは理にかなっています。 これを行うと、必要に応じて、カテゴリごとに異なるログ出力ターゲットを選択することもできます。

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

上記のコードでは、<xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> によってカテゴリ名ごとに `ColorConsoleLogger` のインスタンスが 1 つ作成され、それが [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) に格納されます。 また、<xref:Microsoft.Extensions.Options.IOptionsMonitor%601> インターフェイスが、基になる `ColorConsoleLoggerConfiguration` オブジェクトに対する変更を更新するために必要です。

## <a name="usage-and-registration-of-the-custom-logger"></a>カスタム ロガーの使用と登録

カスタム ログ プロバイダーおよび対応するロガーを追加するには、<xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> から <xref:Microsoft.Extensions.Logging.ILoggerProvider> と <xref:Microsoft.Extensions.Logging.ILoggingBuilder> を追加します。

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-33":::

`ILoggingBuilder` により、1 つ以上の `ILogger` インスタンスが作成されます。 `ILogger` インスタンスは、情報をログに記録するためにフレームワークによって使用されます。

慣例により、`ILoggingBuilder` の拡張メソッドを使用して、カスタム プロバイダーが登録されます。

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

この単純なアプリケーションを実行すると、次の図のような色の出力がコンソール ウィンドウにレンダリングされます。

:::image type="content" source="media/color-console-logger.png" alt-text="カラー コンソール ロガーのサンプル出力":::

## <a name="see-also"></a>関連項目

- [.NET でのログの記録](logging.md)
- [.NET でのログ プロバイダー](logging-providers.md)
- [.NET での依存関係の挿入](dependency-injection.md)
- [.NET での高パフォーマンスのログ](high-performance-logging.md)
