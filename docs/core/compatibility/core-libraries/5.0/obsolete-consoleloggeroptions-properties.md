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
# <a name="obsolete-properties-on-consoleloggeroptions"></a><span data-ttu-id="b0e6e-103">ConsoleLoggerOptions の古いプロパティ</span><span class="sxs-lookup"><span data-stu-id="b0e6e-103">Obsolete properties on ConsoleLoggerOptions</span></span>

<span data-ttu-id="b0e6e-104"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型および <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> のいくつかのプロパティは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-104">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and some properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are now obsolete.</span></span>

## <a name="change-description"></a><span data-ttu-id="b0e6e-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="b0e6e-105">Change description</span></span>

<span data-ttu-id="b0e6e-106">.NET 5 以降では、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型および <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> のいくつかのプロパティは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-106">Starting in .NET 5, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and several properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are obsolete.</span></span> <span data-ttu-id="b0e6e-107">互換性のために残されているプロパティは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-107">The obsolete properties are:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

<span data-ttu-id="b0e6e-108">新しいフォーマッタの導入により、これらのプロパティを個々のフォーマッタで使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-108">With the introduction of new formatters, these properties are now available on the individual formatters.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b0e6e-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="b0e6e-109">Reason for change</span></span>

<span data-ttu-id="b0e6e-110"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> プロパティは列挙型であり、カスタム フォーマッタを表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-110">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> property is an enumeration type, which cannot represent a custom formatter.</span></span>

<span data-ttu-id="b0e6e-111">残りのプロパティは、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> に設定され、コンソール ログ用の組み込みの書式の両方に適用されていました。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-111">The remaining properties were set on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> and applied to both of the built-in formats for console logs.</span></span> <span data-ttu-id="b0e6e-112">ただし、新しいフォーマッタ API を導入することで、フォーマッタ固有のオプションでの書式設定がよりわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-112">However, with the introduction of a new formatter API, it makes more sense for formatting to be represented on the formatter-specific options.</span></span> <span data-ttu-id="b0e6e-113">この変更により、ロガーとロガー フォーマッタの分離が改善されます。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-113">This change provides better separation between the logger and logger formatters.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b0e6e-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b0e6e-114">Version introduced</span></span>

<span data-ttu-id="b0e6e-115">5.0</span><span class="sxs-lookup"><span data-stu-id="b0e6e-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b0e6e-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="b0e6e-116">Recommended action</span></span>

- <span data-ttu-id="b0e6e-117"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> プロパティの代わりに、新しい <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-117">Use the new <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> property in place of the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b0e6e-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-118">For example:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <span data-ttu-id="b0e6e-119"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> と <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> にはいくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-119">There are several differences between <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span></span>

  - <span data-ttu-id="b0e6e-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> には、`Default` と `Systemd` の 2 つのオプションがあるのみです。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> has only two possible options: `Default` and `Systemd`.</span></span>
  - <span data-ttu-id="b0e6e-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> では、大文字と小文字は区別されず、任意の文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> is case insensitive and can be any string.</span></span> <span data-ttu-id="b0e6e-122">予約された組み込みの名前は、`Simple`、`Systemd`、`Json` (.NET 5 以降) です。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-122">The reserved, built-in names are `Simple`, `Systemd`, and `Json` (.NET 5 and later).</span></span>
  - <span data-ttu-id="b0e6e-123">`"Format": "Systemd"` は `"FormatterName": "Systemd"` にマップされます。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-123">`"Format": "Systemd"` maps to `"FormatterName": "Systemd"`.</span></span>
  - <span data-ttu-id="b0e6e-124">`"Format": "Default"` は `"FormatterName": "Simple"` にマップされます。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-124">`"Format": "Default"` maps to `"FormatterName": "Simple"`.</span></span>

- <span data-ttu-id="b0e6e-125"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> の各プロパティについては、新しい <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> 型、<xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> 型、または <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 型の対応するプロパティを代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-125">For the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>, and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> properties, use the corresponding property on the new <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>, or <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> types instead.</span></span> <span data-ttu-id="b0e6e-126">たとえば、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> の対応する設定は <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-126">For example, the corresponding setting for <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> is <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType>.</span></span>

  <span data-ttu-id="b0e6e-127">以前のコード:</span><span class="sxs-lookup"><span data-stu-id="b0e6e-127">Previous code:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

  <span data-ttu-id="b0e6e-128">新しいコード:</span><span class="sxs-lookup"><span data-stu-id="b0e6e-128">New code:</span></span>

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.ColorBehavior = LoggerColorBehavior.Disabled;
  });
  ```

<span data-ttu-id="b0e6e-129">次の 2 つの JSON スニペットは、構成ファイルがどのように変更されているかを示しています。</span><span class="sxs-lookup"><span data-stu-id="b0e6e-129">The following two JSON snippets show how the configuration file changes.</span></span> <span data-ttu-id="b0e6e-130">古い構成ファイル:</span><span class="sxs-lookup"><span data-stu-id="b0e6e-130">Old configuration file:</span></span>

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

<span data-ttu-id="b0e6e-131">新しい構成ファイル:</span><span class="sxs-lookup"><span data-stu-id="b0e6e-131">New configuration file:</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="b0e6e-132">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b0e6e-132">Affected APIs</span></span>

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
