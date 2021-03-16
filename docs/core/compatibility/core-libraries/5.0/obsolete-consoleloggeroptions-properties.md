---
title: 破壊的変更:ConsoleLoggerOptions の古いプロパティ
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。ConsoleLoggerFormat 型と ConsoleLoggerOptions のいくつかのプロパティは、古くなりました。
ms.date: 11/01/2020
ms.openlocfilehash: c6ee294f90e304cebd517bd0139c58a6c7a41e0c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257311"
---
# <a name="obsolete-properties-on-consoleloggeroptions"></a>ConsoleLoggerOptions の古いプロパティ

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型および <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> のいくつかのプロパティは、互換性のために残されています。

## <a name="change-description"></a>変更内容

.NET 5 以降では、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型および <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> のいくつかのプロパティは、互換性のために残されています。 互換性のために残されているプロパティは、次のとおりです。

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

新しいフォーマッタの導入により、これらのプロパティを個々のフォーマッタで使用できるようになりました。

## <a name="reason-for-change"></a>変更理由

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> プロパティは列挙型であり、カスタム フォーマッタを表すことはできません。

残りのプロパティは、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> に設定され、コンソール ログ用の組み込みの書式の両方に適用されていました。 ただし、新しいフォーマッタ API を導入することで、フォーマッタ固有のオプションでの書式設定がよりわかりやすくなります。 この変更により、ロガーとロガー フォーマッタの分離が改善されます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> プロパティの代わりに、新しい <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> プロパティを使用します。 次に例を示します。

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> と <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> にはいくつかの違いがあります。

  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> には、`Default` と `Systemd` の 2 つのオプションがあるのみです。
  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> では、大文字と小文字は区別されず、任意の文字列を指定できます。 予約された組み込みの名前は、`Simple`、`Systemd`、`Json` (.NET 5 以降) です。
  - `"Format": "Systemd"` は `"FormatterName": "Systemd"` にマップされます。
  - `"Format": "Default"` は `"FormatterName": "Simple"` にマップされます。

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> の各プロパティについては、新しい <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> 型、<xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> 型、または <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 型の対応するプロパティを代わりに使用します。 たとえば、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> の対応する設定は <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> です。

  以前のコード:

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

  新しいコード:

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.ColorBehavior = LoggerColorBehavior.Disabled;
  });
  ```

次の 2 つの JSON スニペットは、構成ファイルがどのように変更されているかを示しています。 古い構成ファイル:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "Format": "Systemd",
      "IncludeScopes": true,
      "TimestampFormat": "HH:mm:ss",
      "UseUtcTimestamp": true
    }
  },
  "AllowedHosts": "*"
}
```

新しい構成ファイル:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "FormatterName": "Systemd",
      "FormatterOptions": {
        "IncludeScopes": true,
        "TimestampFormat": "HH:mm:ss",
        "UseUtcTimestamp": true
      }
    }
  },
  "AllowedHosts": "*"
}
```

## <a name="affected-apis"></a>影響を受ける API

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET

### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
