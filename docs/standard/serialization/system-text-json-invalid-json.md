---
title: System.Text.Json でいくつかの種類の無効な JSON を許可する方法
description: .NET で JSON との間のシリアル化または逆シリアル化を行うときに、コメント、末尾のコンマ、および引用符で囲まれた数値を許可する方法について説明します。
ms.date: 12/03/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 19ceaeb882e8126826e7928122c25027bcb12275
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100581463"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-systemtextjson"></a>System.Text.Json でいくつかの種類の無効な JSON を許可する方法

この記事では、JSON でコメント、末尾のコンマ、および引用符で囲まれた数値を許可する方法と、数値を文字列として書き込む方法について説明します。

## <a name="allow-comments-and-trailing-commas"></a>コメントと末尾のコンマを許可する

既定では、JSON 内でコメントと末尾のコンマは使用できません。 JSON 内でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip` に設定します。
また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true` に設定します。 両方を許可する方法を次の例に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/DeserializeCommasComments.vb" id="Deserialize":::

次に、コメントと末尾のコンマを含む JSON の例を示します。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a>引用符で囲まれた数値を許可または記述する

::: zone pivot="dotnet-5-0"

シリアライザーの中には、数値が JSON 文字列としてエンコードされる (引用符で囲まれる) ものがあります。

例:

```json
{
    "DegreesCelsius": "23"
}
```

次の表記の代わりに、

```json
{
    "DegreesCelsius": 23
}
```

引用符で囲まれた数値をシリアル化したり、引用符で囲まれた数値を入力オブジェクト グラフ全体で受け付けるには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> を設定します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/QuotedNumbers.vb" :::

ASP.NET Core を通じて間接的に `System.Text.Json` を使用すると、ASP.NET Core により [Web の既定のオプション](xref:System.Text.Json.JsonSerializerDefaults.Web)が指定されるため、逆シリアル化のときに引用符で囲まれた数値を使用できます。

特定のプロパティ、フィールド、または型について引用符で囲まれた数値を許可または記述するには、[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 属性を使用します。
::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 の `System.Text.Json` では、引用符で囲まれた数値のシリアル化または逆シリアル化はサポートされていません。 詳細については、「[引用符で囲まれた数値を許可または記述する](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)」を参照してください。
::: zone-end

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [参照を保持する](system-text-json-preserve-references.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [Newtonsoft.Json から System.Text.Json に移行する](system-text-json-migrate-from-newtonsoft-how-to.md)
* [文字エンコードをカスタマイズする](system-text-json-character-encoding.md)
* [カスタム シリアライザーと逆シリアライザーを作成する](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターの作成](system-text-json-converters-how-to.md)
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
