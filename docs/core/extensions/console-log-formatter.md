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
# <a name="console-log-formatting"></a>コンソール ログの書式設定

.NET 5 では、`Microsoft.Extensions.Logging.Console` 名前空間のコンソール ログにカスタム書式設定のサポートが追加されました。 [`Simple`](#simple)、[`Systemd`](#systemd)、[`Json`](#json) の 3 つの定義済み書式設定オプションを使用できます。

> [!IMPORTANT]
> それまでは、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> 列挙型を使用して、人間が判読できる書式設定 (こちらが `Default`) または `Systemd` とも呼ばれる単一行の、どちらか望ましいログ書式設定を選択できました。 ただし、これらはカスタマイズ **できず**、現在は非推奨になっています。

この記事では、コンソール ログのフォーマッタについて説明します。 サンプルのソース コードでは、次の方法が示されています。

- 新しいフォーマッタを登録する
- 登録されているフォーマッタから使用するものを選択する
  - コードまたは[構成](configuration.md)のいずれかで
- カスタム フォーマッタを実装する
  - <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> で構成を更新する
  - 色のカスタム書式設定を有効にする

## <a name="register-formatter"></a>フォーマッタを登録する

[`Console` ログ プロバイダー](logging-providers.md#console)にはいくつかの定義済みのフォーマッタがあり、独自のカスタム フォーマッタを作成する機能が公開されています。 使用可能ないずれかのフォーマッタを登録するには、対応する `Add{Type}Console` 拡張メソッドを使用します。

| 使用可能な種類 | 種類を登録するメソッド |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a>シンプル

`Simple` コンソール フォーマッタを使用するには、`AddSimpleConsole` でそれを登録します。

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

前のサンプル ソース コードでは、<xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> フォーマッタが登録されました。 それにより、時間やログレ ベルなどの情報を各ログ メッセージにラップする機能だけでなく、ANSI の色の埋め込みとメッセージのインデントを可能にする機能も、ログに提供されます。

### <a name="systemd"></a>Systemd

<xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> コンソール ロガー:

- "Syslog" ログ レベルの形式と重大度が使用されます
- メッセージの色の書式は設定 **されません**
- 常に 1 行のメッセージが記録されます

これは一般にコンテナーに便利であり、通常は `Systemd` コンソール ログ記録が使用されます。 .NET 5 の `Simple` コンソール ロガーでは、単一行に記録されるコンパクト バージョンが有効になり、前のサンプルで示したように色を無効にすることもできます。

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a>Json

JSON 形式でログを書き込むには、`Json` コンソール フォーマッタを使用します。 サンプルのソース コードでは、ASP.NET Core アプリでそれを登録する方法が示されています。 `webapp` テンプレートを使用し、[dotnet new](../tools/dotnet-new.md) コマンドで新しい ASP.NET Core アプリを作成します。

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

テンプレート コードを使用してアプリを実行すると、次の既定のログ形式が取得されます。

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

既定の構成では、`Simple` コンソール ログ フォーマッタが選択されます。 これを変更するには、*Program.cs* で `AddJsonConsole` を呼び出します。

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

上のように変更してアプリをもう一度実行すると、ログ メッセージは JSON として書式設定されます。

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> 既定の `Json` コンソール フォーマッタを使用すると、各メッセージが 1 行に記録されます。 フォーマッタを構成するときにそれをさらに読みやすくするには、<xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> を `true` に設定します。

## <a name="set-formatter-with-configuration"></a>構成でフォーマッタを設定する

前のサンプルには、フォーマッタをプログラムで登録する方法が示されています。 または、[構成](configuration.md)を使用してこれを行うこともできます。 前に示した Web アプリケーションのサンプル ソースコードについて考えます。*Program.cs* ファイルで `ConfigureLogging` を呼び出すのではなく、*appsettings.json* ファイルを更新すると、同じ結果が得られる可能性があります。 更新された `appsettings.json` ファイルでは、フォーマッタが次のように構成されます。

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

設定が必要な 2 つのキー値は、`"FormatterName"` と `"FormatterOptions"` です。 値が `"FormatterName"` に設定されているフォーマッタが既に登録されている場合、そのフォーマッタが選択され、そのプロパティが `"FormatterOptions"` ノード内のキーとして指定されている限り、それを構成できます。 定義済みのフォーマッタ名は、<xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> の下に予約されています。

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a>カスタム フォーマッタを実装する

カスタム フォーマッタを実装するには、以下のことを行う必要があります。

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> のサブクラスを作成します。これはカスタム フォーマッタを表します
- 以下を使用してカスタム フォーマッタを登録します
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

これを自動的に処理する拡張メソッドを作成します。

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

`CustomOptions` の定義は次のとおりです。

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

上記のコードでは、オプションは <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> のサブクラスです。

`AddConsoleFormatter` API:

- `ConsoleFormatter` のサブクラスを登録します
- 構成を処理します。
  - [オプション パターン](options.md)と [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) インターフェイスに基づき、変更トークンを使用して更新を同期します

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

`ConsoleFormatter` の `CustomerFormatter` サブクラスを定義します。

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

上の `CustomFormatter.Write<TState>` API により、各ログ メッセージをラップするテキストが指示されます。 標準の `ConsoleFormatter` では、少なくとも、ログのスコープ、タイムスタンプ、重大度レベルをラップできるはずです。 さらに、ログ メッセージで ANSI の色をエンコードし、必要なインデントを指定することもできます。 `CustomFormatter.Write<TState>` の実装には、これらの機能はありません。

書式設定をさらにカスタマイズする発想を得るには、`Microsoft.Extensions.Logging.Console` 名前空間の既存の実装を参照してください。

- [SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs)
- [SystemdConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [JsonConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a>色のカスタム書式設定を実装する

カスタム ログ フォーマッタで色の機能を適切に有効にするには、ログで色を有効にするのに役立つ <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> プロパティが含まれる <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> を拡張できます。

`SimpleConsoleFormatterOptions` から派生する `CustomColorOptions` を作成します。

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

次に、`TextWriterExtensions` クラスで、書式設定されたログ メッセージ内に ANSI コード化された色を簡単に埋め込むことができる拡張メソッドをいくつか記述します。

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

カスタム色の適用を処理するカスタム色フォーマッタの定義は、次のようになります。

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

アプリケーションを実行すると、`FormatterOptions.ColorBehavior` が `Enabled` の場合、ログにより `CustomPrefix` メッセージが緑色で表示されます。

> [!NOTE]
> <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> が `Disabled` の場合は、ログ メッセージ内に埋め込まれたみ ANSI の色コードは、ログ メッセージによって解釈 "_されません_"。 代わりに、生のメッセージが出力されます。 たとえば、次のことを考慮してください。
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> これにより逐語的文字列が出力され、色分けされ "_ません_"。
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a>関連項目

- [.NET でのログの記録](logging.md)
- [.NET にカスタム ログ プロバイダーを実装する](custom-logging-provider.md)
- [.NET での高パフォーマンスのログ](high-performance-logging.md)
