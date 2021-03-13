---
title: System.Text.Json で大文字と小文字を区別しないプロパティ名の照合を有効にする方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、大文字と小文字を区別しないプロパティ名の照合を有効にする方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d0d4bf8841cd8057b20f51ab7d2ab407e2299152
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584374"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-systemtextjson"></a>System.Text.Json で大文字と小文字を区別しないプロパティ名の照合を有効にする方法

この記事では、`System.Text.Json` 名前空間を使用して、大文字と小文字を区別しないプロパティ名の照合を有効にする方法について説明します。

## <a name="case-insensitive-property-matching"></a>大文字と小文字を区別しないプロパティ照合

既定では、逆シリアル化では JSON とターゲット オブジェクトのプロパティとの間で大文字と小文字を区別したプロパティ名の一致が検索されます。 この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true` に設定します。

> [!NOTE]
> [Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)では大文字と小文字が区別されません。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/DeserializeCaseInsensitive.vb" id="Deserialize":::

キャメル ケースのプロパティ名を持つ JSON の例を次に示します。 これはパスカル ケースのプロパティ名を持つ次の型に逆シリアル化できます。

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
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
