---
title: コンソール ログの書式設定
description: コンソール ログで使用可能な書式設定を使用する方法、または .NET アプリケーション用にカスタム ログ書式設定を実装する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 12/17/2020
ms.openlocfilehash: 0ec8fc2018febe4273aa646d1682be197933f925
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "102402118"
---
# <a name="console-log-formatting"></a><span data-ttu-id="5595e-103">コンソール ログの書式設定</span><span class="sxs-lookup"><span data-stu-id="5595e-103">Console log formatting</span></span>

<span data-ttu-id="5595e-104">.NET 5 では、`Microsoft.Extensions.Logging.Console` 名前空間のコンソール ログにカスタム書式設定のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="5595e-104">In .NET 5, support for custom formatting was added to console logs in the `Microsoft.Extensions.Logging.Console` namespace.</span></span> <span data-ttu-id="5595e-105">[`Simple`](#simple)、[`Systemd`](#systemd)、[`Json`](#json) の 3 つの定義済み書式設定オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5595e-105">There are three predefined formatting options available: [`Simple`](#simple), [`Systemd`](#systemd), and [`Json`](#json).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5595e-106">それまでは、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> 列挙型を使用して、人間が判読できる書式設定 (こちらが `Default`) または `Systemd` とも呼ばれる単一行の、どちらか望ましいログ書式設定を選択できました。</span><span class="sxs-lookup"><span data-stu-id="5595e-106">Previously, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> enum allowed for selecting the desired log format, either human readable which was the `Default`, or single line which is also known as `Systemd`.</span></span> <span data-ttu-id="5595e-107">ただし、これらはカスタマイズ **できず**、現在は非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="5595e-107">However, these were **not** customizable, and are now deprecated.</span></span>

<span data-ttu-id="5595e-108">この記事では、コンソール ログのフォーマッタについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5595e-108">In this article, you will learn about console log formatters.</span></span> <span data-ttu-id="5595e-109">サンプルのソース コードでは、次の方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="5595e-109">The sample source code demonstrates how to:</span></span>

- <span data-ttu-id="5595e-110">新しいフォーマッタを登録する</span><span class="sxs-lookup"><span data-stu-id="5595e-110">Register a new formatter</span></span>
- <span data-ttu-id="5595e-111">登録されているフォーマッタから使用するものを選択する</span><span class="sxs-lookup"><span data-stu-id="5595e-111">Select a registered formatter to use</span></span>
  - <span data-ttu-id="5595e-112">コードまたは[構成](configuration.md)のいずれかで</span><span class="sxs-lookup"><span data-stu-id="5595e-112">Either through code, or [configuration](configuration.md)</span></span>
- <span data-ttu-id="5595e-113">カスタム フォーマッタを実装する</span><span class="sxs-lookup"><span data-stu-id="5595e-113">Implement a custom formatter</span></span>
  - <span data-ttu-id="5595e-114"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601> で構成を更新する</span><span class="sxs-lookup"><span data-stu-id="5595e-114">Update configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span></span>
  - <span data-ttu-id="5595e-115">色のカスタム書式設定を有効にする</span><span class="sxs-lookup"><span data-stu-id="5595e-115">Enable custom color formatting</span></span>

## <a name="register-formatter"></a><span data-ttu-id="5595e-116">フォーマッタを登録する</span><span class="sxs-lookup"><span data-stu-id="5595e-116">Register formatter</span></span>

<span data-ttu-id="5595e-117">[`Console` ログ プロバイダー](logging-providers.md#console)にはいくつかの定義済みのフォーマッタがあり、独自のカスタム フォーマッタを作成する機能が公開されています。</span><span class="sxs-lookup"><span data-stu-id="5595e-117">The [`Console` logging provider](logging-providers.md#console) has several predefined formatters, and exposes the ability to author your own custom formatter.</span></span> <span data-ttu-id="5595e-118">使用可能ないずれかのフォーマッタを登録するには、対応する `Add{Type}Console` 拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="5595e-118">To register any of the available formatters, use the corresponding `Add{Type}Console` extension method:</span></span>

| <span data-ttu-id="5595e-119">使用可能な種類</span><span class="sxs-lookup"><span data-stu-id="5595e-119">Available types</span></span> | <span data-ttu-id="5595e-120">種類を登録するメソッド</span><span class="sxs-lookup"><span data-stu-id="5595e-120">Method to register type</span></span> |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a><span data-ttu-id="5595e-121">シンプル</span><span class="sxs-lookup"><span data-stu-id="5595e-121">Simple</span></span>

<span data-ttu-id="5595e-122">`Simple` コンソール フォーマッタを使用するには、`AddSimpleConsole` でそれを登録します。</span><span class="sxs-lookup"><span data-stu-id="5595e-122">To use the `Simple` console formatter, register it with `AddSimpleConsole`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

<span data-ttu-id="5595e-123">前のサンプル ソース コードでは、<xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> フォーマッタが登録されました。</span><span class="sxs-lookup"><span data-stu-id="5595e-123">In the preceding sample source code, the <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> formatter was registered.</span></span> <span data-ttu-id="5595e-124">それにより、時間やログレ ベルなどの情報を各ログ メッセージにラップする機能だけでなく、ANSI の色の埋め込みとメッセージのインデントを可能にする機能も、ログに提供されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-124">It provides logs with the ability to not only wrap information such as time and log level in each log message, but also allows for ANSI color embedding and indentation of messages.</span></span>

### <a name="systemd"></a><span data-ttu-id="5595e-125">Systemd</span><span class="sxs-lookup"><span data-stu-id="5595e-125">Systemd</span></span>

<span data-ttu-id="5595e-126"><xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> コンソール ロガー:</span><span class="sxs-lookup"><span data-stu-id="5595e-126">The <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> console logger:</span></span>

- <span data-ttu-id="5595e-127">"Syslog" ログ レベルの形式と重大度が使用されます</span><span class="sxs-lookup"><span data-stu-id="5595e-127">Uses the "Syslog" log level format and severities</span></span>
- <span data-ttu-id="5595e-128">メッセージの色の書式は設定 **されません**</span><span class="sxs-lookup"><span data-stu-id="5595e-128">Does **not** format messages with colors</span></span>
- <span data-ttu-id="5595e-129">常に 1 行のメッセージが記録されます</span><span class="sxs-lookup"><span data-stu-id="5595e-129">Always logs messages in a single line</span></span>

<span data-ttu-id="5595e-130">これは一般にコンテナーに便利であり、通常は `Systemd` コンソール ログ記録が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-130">This is commonly useful for containers, which often make use of `Systemd` console logging.</span></span> <span data-ttu-id="5595e-131">.NET 5 の `Simple` コンソール ロガーでは、単一行に記録されるコンパクト バージョンが有効になり、前のサンプルで示したように色を無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5595e-131">With .NET 5, the `Simple` console logger also enables a compact version that logs in a single line, and also allows for disabling colors as shown in an earlier sample.</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a><span data-ttu-id="5595e-132">Json</span><span class="sxs-lookup"><span data-stu-id="5595e-132">Json</span></span>

<span data-ttu-id="5595e-133">JSON 形式でログを書き込むには、`Json` コンソール フォーマッタを使用します。</span><span class="sxs-lookup"><span data-stu-id="5595e-133">To write logs in a JSON format, the `Json` console formatter is used.</span></span> <span data-ttu-id="5595e-134">サンプルのソース コードでは、ASP.NET Core アプリでそれを登録する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="5595e-134">The sample source code shows how an ASP.NET Core app might register it.</span></span> <span data-ttu-id="5595e-135">`webapp` テンプレートを使用し、[dotnet new](../tools/dotnet-new.md) コマンドで新しい ASP.NET Core アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5595e-135">Using the `webapp` template, create a new ASP.NET Core app with the [dotnet new](../tools/dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

<span data-ttu-id="5595e-136">テンプレート コードを使用してアプリを実行すると、次の既定のログ形式が取得されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-136">When running the app, using the template code, you get the default log format below:</span></span>

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

<span data-ttu-id="5595e-137">既定の構成では、`Simple` コンソール ログ フォーマッタが選択されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-137">By default, the `Simple` console log formatter is selected with default configuration.</span></span> <span data-ttu-id="5595e-138">これを変更するには、*Program.cs* で `AddJsonConsole` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5595e-138">You change this by calling `AddJsonConsole` in the *Program.cs*:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

<span data-ttu-id="5595e-139">上のように変更してアプリをもう一度実行すると、ログ メッセージは JSON として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-139">Run the app again, with the above change, the log message is now formatted as JSON:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> <span data-ttu-id="5595e-140">既定の `Json` コンソール フォーマッタを使用すると、各メッセージが 1 行に記録されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-140">The `Json` console formatter, by default, logs each message in a single line.</span></span> <span data-ttu-id="5595e-141">フォーマッタを構成するときにそれをさらに読みやすくするには、<xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="5595e-141">In order to make it more readable while configuring the formatter, set <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> to `true`.</span></span>

## <a name="set-formatter-with-configuration"></a><span data-ttu-id="5595e-142">構成でフォーマッタを設定する</span><span class="sxs-lookup"><span data-stu-id="5595e-142">Set formatter with configuration</span></span>

<span data-ttu-id="5595e-143">前のサンプルには、フォーマッタをプログラムで登録する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="5595e-143">The previous samples have shown how to register a formatter programmatically.</span></span> <span data-ttu-id="5595e-144">または、[構成](configuration.md)を使用してこれを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="5595e-144">Alternatively, this can be done with [configuration](configuration.md).</span></span> <span data-ttu-id="5595e-145">前に示した Web アプリケーションのサンプル ソースコードについて考えます。*Program.cs* ファイルで `ConfigureLogging` を呼び出すのではなく、*appsettings.json* ファイルを更新すると、同じ結果が得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5595e-145">Consider the previous web application sample source code, if you update the *appsettings.json* file rather than calling `ConfigureLogging` in the *Program.cs* file, you could get the same outcome.</span></span> <span data-ttu-id="5595e-146">更新された `appsettings.json` ファイルでは、フォーマッタが次のように構成されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-146">The updated `appsettings.json` file would configure the formatter as follows:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

<span data-ttu-id="5595e-147">設定が必要な 2 つのキー値は、`"FormatterName"` と `"FormatterOptions"` です。</span><span class="sxs-lookup"><span data-stu-id="5595e-147">The two key values that need to be set are `"FormatterName"` and `"FormatterOptions"`.</span></span> <span data-ttu-id="5595e-148">値が `"FormatterName"` に設定されているフォーマッタが既に登録されている場合、そのフォーマッタが選択され、そのプロパティが `"FormatterOptions"` ノード内のキーとして指定されている限り、それを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5595e-148">If a formatter with the value set for `"FormatterName"` is already registered, that formatter is selected, and its properties can be configured as long as they are provided as a key inside the `"FormatterOptions"` node.</span></span> <span data-ttu-id="5595e-149">定義済みのフォーマッタ名は、<xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> の下に予約されています。</span><span class="sxs-lookup"><span data-stu-id="5595e-149">The predefined formatter names are reserved under <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames>:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a><span data-ttu-id="5595e-150">カスタム フォーマッタを実装する</span><span class="sxs-lookup"><span data-stu-id="5595e-150">Implement a custom formatter</span></span>

<span data-ttu-id="5595e-151">カスタム フォーマッタを実装するには、以下のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5595e-151">To implement a custom formatter, you need to:</span></span>

- <span data-ttu-id="5595e-152"><xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> のサブクラスを作成します。これはカスタム フォーマッタを表します</span><span class="sxs-lookup"><span data-stu-id="5595e-152">Create a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter>, this represents your custom formatter</span></span>
- <span data-ttu-id="5595e-153">以下を使用してカスタム フォーマッタを登録します</span><span class="sxs-lookup"><span data-stu-id="5595e-153">Register your custom formatter with</span></span>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

<span data-ttu-id="5595e-154">これを自動的に処理する拡張メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="5595e-154">Create an extension method to handle this for you:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

<span data-ttu-id="5595e-155">`CustomOptions` の定義は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5595e-155">The `CustomOptions` are defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

<span data-ttu-id="5595e-156">上記のコードでは、オプションは <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="5595e-156">In the preceding code, the options are a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>.</span></span>

<span data-ttu-id="5595e-157">`AddConsoleFormatter` API:</span><span class="sxs-lookup"><span data-stu-id="5595e-157">The `AddConsoleFormatter` API:</span></span>

- <span data-ttu-id="5595e-158">`ConsoleFormatter` のサブクラスを登録します</span><span class="sxs-lookup"><span data-stu-id="5595e-158">Registers a subclass of `ConsoleFormatter`</span></span>
- <span data-ttu-id="5595e-159">構成を処理します。</span><span class="sxs-lookup"><span data-stu-id="5595e-159">Handles configuration:</span></span>
  - <span data-ttu-id="5595e-160">[オプション パターン](options.md)と [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) インターフェイスに基づき、変更トークンを使用して更新を同期します</span><span class="sxs-lookup"><span data-stu-id="5595e-160">Uses a change token to synchronize updates, based on the [options pattern](options.md), and the [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) interface</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

<span data-ttu-id="5595e-161">`ConsoleFormatter` の `CustomerFormatter` サブクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="5595e-161">Define a `CustomerFormatter` subclass of `ConsoleFormatter`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

<span data-ttu-id="5595e-162">上の `CustomFormatter.Write<TState>` API により、各ログ メッセージをラップするテキストが指示されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-162">The preceding `CustomFormatter.Write<TState>` API dictates what text gets wrapped around each log message.</span></span> <span data-ttu-id="5595e-163">標準の `ConsoleFormatter` では、少なくとも、ログのスコープ、タイムスタンプ、重大度レベルをラップできるはずです。</span><span class="sxs-lookup"><span data-stu-id="5595e-163">A standard `ConsoleFormatter` should be able to wrap around scopes, time stamps, and severity level of logs at a minimum.</span></span> <span data-ttu-id="5595e-164">さらに、ログ メッセージで ANSI の色をエンコードし、必要なインデントを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5595e-164">Additionally, you can encode ANSI colors in the log messages, and provide desired indentations as well.</span></span> <span data-ttu-id="5595e-165">`CustomFormatter.Write<TState>` の実装には、これらの機能はありません。</span><span class="sxs-lookup"><span data-stu-id="5595e-165">The implementation of the `CustomFormatter.Write<TState>` lacks these capabilities.</span></span>

<span data-ttu-id="5595e-166">書式設定をさらにカスタマイズする発想を得るには、`Microsoft.Extensions.Logging.Console` 名前空間の既存の実装を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5595e-166">For inspiration on further customizing formatting, see the existing implementations in the `Microsoft.Extensions.Logging.Console` namespace:</span></span>

- <span data-ttu-id="5595e-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs)</span><span class="sxs-lookup"><span data-stu-id="5595e-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).</span></span>
- [<span data-ttu-id="5595e-168">SystemdConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="5595e-168">SystemdConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [<span data-ttu-id="5595e-169">JsonConsoleFormatter</span><span class="sxs-lookup"><span data-stu-id="5595e-169">JsonConsoleFormatter</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a><span data-ttu-id="5595e-170">色のカスタム書式設定を実装する</span><span class="sxs-lookup"><span data-stu-id="5595e-170">Implement custom color formatting</span></span>

<span data-ttu-id="5595e-171">カスタム ログ フォーマッタで色の機能を適切に有効にするには、ログで色を有効にするのに役立つ <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> プロパティが含まれる <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="5595e-171">In order to properly enable color capabilities in your custom logging formatter, you can extend the <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> as it has a <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> property that can be useful for enabling colors in logs.</span></span>

<span data-ttu-id="5595e-172">`SimpleConsoleFormatterOptions` から派生する `CustomColorOptions` を作成します。</span><span class="sxs-lookup"><span data-stu-id="5595e-172">Create a `CustomColorOptions` that derives from `SimpleConsoleFormatterOptions`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

<span data-ttu-id="5595e-173">次に、`TextWriterExtensions` クラスで、書式設定されたログ メッセージ内に ANSI コード化された色を簡単に埋め込むことができる拡張メソッドをいくつか記述します。</span><span class="sxs-lookup"><span data-stu-id="5595e-173">Next, write some extension methods in a `TextWriterExtensions` class that allow for conveniently embedding ANSI coded colors within formatted log messages:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

<span data-ttu-id="5595e-174">カスタム色の適用を処理するカスタム色フォーマッタの定義は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5595e-174">A custom color formatter that handles applying custom colors could be defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

<span data-ttu-id="5595e-175">アプリケーションを実行すると、`FormatterOptions.ColorBehavior` が `Enabled` の場合、ログにより `CustomPrefix` メッセージが緑色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-175">When you run the application, the logs will show the `CustomPrefix` message in the color green when `FormatterOptions.ColorBehavior` is `Enabled`.</span></span>

> [!NOTE]
> <span data-ttu-id="5595e-176"><xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> が `Disabled` の場合は、ログ メッセージ内に埋め込まれたみ ANSI の色コードは、ログ メッセージによって解釈 "_されません_"。</span><span class="sxs-lookup"><span data-stu-id="5595e-176">When <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> is `Disabled`, log messages do _not_ interpret embedded ANSI color codes within log messages.</span></span> <span data-ttu-id="5595e-177">代わりに、生のメッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="5595e-177">Instead, they output the raw message.</span></span> <span data-ttu-id="5595e-178">たとえば、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="5595e-178">For example, consider the following:</span></span>
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> <span data-ttu-id="5595e-179">これにより逐語的文字列が出力され、色分けされ "_ません_"。</span><span class="sxs-lookup"><span data-stu-id="5595e-179">This would output the verbatim string, and it is _not_ colorized.</span></span>
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a><span data-ttu-id="5595e-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="5595e-180">See also</span></span>

- [<span data-ttu-id="5595e-181">.NET でのログの記録</span><span class="sxs-lookup"><span data-stu-id="5595e-181">Logging in .NET</span></span>](logging.md)
- [<span data-ttu-id="5595e-182">.NET にカスタム ログ プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="5595e-182">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="5595e-183">.NET での高パフォーマンスのログ</span><span class="sxs-lookup"><span data-stu-id="5595e-183">High-performance logging in .NET</span></span>](high-performance-logging.md)
