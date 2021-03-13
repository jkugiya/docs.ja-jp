---
title: System.Text.Json でオーバーフロー JSON を処理する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、オーバーフロー JSON を処理する方法について説明します。
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
ms.openlocfilehash: 61f21d131922bc98d7f70093abf55eed3dcd8a61
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583703"
---
# <a name="how-to-handle-overflow-json-with-systemtextjson"></a>System.Text.Json でオーバーフロー JSON を処理する方法

この記事では、`System.Text.Json` 名前空間を使用してオーバーフロー JSON を処理する方法について説明します。

## <a name="handle-overflow-json"></a>オーバーフロー JSON の処理

逆シリアル化中に、ターゲット型のプロパティで表されないデータを JSON 内で受け取ることがあります。 たとえば、ターゲット型が次のようになっているとします。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

逆シリアル化される JSON は次のとおりです。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

表示されている JSON を示されている型に逆シリアル化すると、`DatesAvailable` と `SummaryWords` のプロパティは行き先がなくなり、失われます。 これらのプロパティのような余分なデータをキャプチャするには、[[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 属性を `Dictionary<string,object>` 型または `Dictionary<string,JsonElement>` 型のプロパティに適用します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithExtensionData":::

前に示した JSON をこのサンプル型に逆シリアル化すると、余分なデータが `ExtensionData` プロパティのキーと値のペアになります。

| プロパティ | 値 | メモ |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | 大文字と小文字の区別が一致しないため (JSON では `temperatureCelsius`)、プロパティは設定されません。 |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | 大文字と小文字の区別が一致しなかったため、この JSON プロパティは余分で、ディクショナリ内のキーと値のペアになります。 |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。 |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。 |

ターゲット オブジェクトがシリアル化されると、拡張データのキーと値のペアは、受信 JSON 内にあった場合と同様に JSON プロパティになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

JSON には `ExtensionData` プロパティ名が表示されないことに注意してください。 この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンド トリップを行うことができます。

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
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
