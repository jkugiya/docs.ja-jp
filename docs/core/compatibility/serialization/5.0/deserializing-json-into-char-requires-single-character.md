---
title: 破壊的変更:char の逆シリアル化で 1 文字の文字列が求められる
description: System.Text.Json では、char ターゲットに逆シリアル化するとき、JSON に 1 文字の文字が必要になるという、.NET 5 の破壊的変更について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: e901f8ee7e7521af948a3bcde5cf969640436f7f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256336"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a>System.Text.Json では、char の逆シリアル化に 1 文字の文字列が必要です

<xref:System.Text.Json> を利用して <xref:System.Char> を正常に逆シリアル化するには、JSON 文字列に 1 文字を含める必要があります。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、JSON に複数の `char` からなる文字列があっても、`char` プロパティまたはフィールドに正常に逆シリアル化されます。 次の例のように、文字列の最初の `char` のみが使用されます。

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

.NET 5 以降では、`char` が 1 つの文字列以外を渡すと、逆シリアル化のターゲットが `char` のとき、<xref:System.Text.Json.JsonException> がスローされます。 次の例の文字列は、すべての .NET バージョンで正常に逆シリアル化されます。

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="reason-for-change"></a>変更理由

逆シリアル化の解析は、指定されたペイロードがターゲットの型に対して有効なときにのみ、成功しなければなりません。 `char` 型の場合、有効なペイロードは `char` が 1 つの文字列のみです。

## <a name="recommended-action"></a>推奨アクション

JSON を `char` ターゲットに逆シリアル化するとき、文字列が 1 つの `char` で構成されるようにしてください。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
