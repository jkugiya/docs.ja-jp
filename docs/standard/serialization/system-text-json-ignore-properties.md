---
title: System.Text.Json でプロパティを無視する方法
description: .NET の System.Text.Json を使用してシリアル化するときにプロパティを無視する方法について説明します。
ms.date: 01/15/2021
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
ms.openlocfilehash: b2ff4c147e2fac0ba5bf3367f881fc9d8ee8f1af
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583911"
---
# <a name="how-to-ignore-properties-with-systemtextjson"></a>System.Text.Json でプロパティを無視する方法

C# オブジェクトを JavaScript Object Notation (JSON) にシリアル化する場合、既定では、すべてのパブリック プロパティがシリアル化されます。 生成される JSON にその一部を出現させないようにするには、いくつかのオプションがあります。 この記事では、さまざまな条件に基づいてプロパティを無視する方法について説明します。

::: zone pivot="dotnet-5-0"

* [個々のプロパティ](#ignore-individual-properties)
* [すべての読み取り専用プロパティ](#ignore-all-read-only-properties)
* [すべての null 値プロパティ](#ignore-all-null-value-properties)
* [すべての既定値のプロパティ](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [個々のプロパティ](#ignore-individual-properties)
* [すべての読み取り専用プロパティ](#ignore-all-read-only-properties)
* [すべての null 値プロパティ](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a>個々のプロパティを無視する

個々のプロパティを無視するには、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性を使用します。

シリアル化する型と JSON 出力の例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティを設定することによって、条件付き除外を指定できます。 <xref:System.Text.Json.Serialization.JsonIgnoreCondition> 列挙型には、次のオプションがあります。

* `Always` - プロパティを常に無視します。 `Condition` を指定しないと、このオプションが想定されます。
* `Never` - グローバル設定 `DefaultIgnoreCondition`、`IgnoreReadOnlyProperties`、`IgnoreReadOnlyFields` に関係なく、プロパティは常にシリアル化および逆シリアル化されます。
* `WhenWritingDefault` - プロパティが参照型 `null`、null 許容値型 `null`、または値型 `default` の場合、シリアル化時に無視されます。
* `WhenWritingNull` - プロパティが参照型 `null` または null 許容値型 `null` の場合、シリアル化時に無視されます。

次の例では、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティの使用方法を示します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/JsonIgnoreAttributeExample.vb" :::
::: zone-end

## <a name="ignore-all-read-only-properties"></a>すべての読み取り専用プロパティを無視する

パブリック ゲッターが含まれていてもパブリック セッターがない場合、プロパティは読み取り専用です。 シリアル化のときにすべての読み取り専用プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> を `true` に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeExcludeReadOnlyProperties.vb" id="Serialize":::

シリアル化する型と JSON 出力の例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

このオプションは、シリアル化にのみ適用されます。 逆シリアル化中、既定では読み取り専用プロパティが無視されます。

::: zone pivot="dotnet-5-0"
このオプションは、プロパティにのみ適用されます。 [フィールドをシリアル化する](system-text-json-how-to.md#include-fields)ときに読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。
::: zone-end

## <a name="ignore-all-null-value-properties"></a>すべての null 値プロパティを無視する

::: zone pivot="dotnet-5-0"
すべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/IgnoreNullOnSerialize.vb" :::

::: zone-end

::: zone pivot="dotnet-core-3-1"
シリアル化のときにすべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> プロパティを `true` に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeExcludeNullValueProperties.vb" id="Serialize":::

シリアル化するオブジェクトと JSON 出力の例を次に示します。

| プロパティ             | 値                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a>既定値のプロパティをすべて無視する

::: zone pivot="dotnet-5-0"
値型プロパティで既定値がシリアル化されないようにするには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/IgnoreValueDefaultOnSerialize.vb" :::
::: zone-end

<xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> を設定すると、null 値参照型および null 許容値型のプロパティもシリアル化されなくなります。

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 の `System.Text.Json` で、値型の既定値のプロパティがシリアル化されないようにするための組み込みの方法はありません。
::: zone-end

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
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
