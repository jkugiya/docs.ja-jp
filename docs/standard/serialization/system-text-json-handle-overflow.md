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
# <a name="how-to-handle-overflow-json-with-systemtextjson"></a><span data-ttu-id="ba3df-103">System.Text.Json でオーバーフロー JSON を処理する方法</span><span class="sxs-lookup"><span data-stu-id="ba3df-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="ba3df-104">この記事では、`System.Text.Json` 名前空間を使用してオーバーフロー JSON を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba3df-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="ba3df-105">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="ba3df-105">Handle overflow JSON</span></span>

<span data-ttu-id="ba3df-106">逆シリアル化中に、ターゲット型のプロパティで表されないデータを JSON 内で受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="ba3df-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="ba3df-107">たとえば、ターゲット型が次のようになっているとします。</span><span class="sxs-lookup"><span data-stu-id="ba3df-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

<span data-ttu-id="ba3df-108">逆シリアル化される JSON は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ba3df-108">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="ba3df-109">表示されている JSON を示されている型に逆シリアル化すると、`DatesAvailable` と `SummaryWords` のプロパティは行き先がなくなり、失われます。</span><span class="sxs-lookup"><span data-stu-id="ba3df-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="ba3df-110">これらのプロパティのような余分なデータをキャプチャするには、[[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 属性を `Dictionary<string,object>` 型または `Dictionary<string,JsonElement>` 型のプロパティに適用します。</span><span class="sxs-lookup"><span data-stu-id="ba3df-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithExtensionData":::

<span data-ttu-id="ba3df-111">前に示した JSON をこのサンプル型に逆シリアル化すると、余分なデータが `ExtensionData` プロパティのキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="ba3df-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="ba3df-112">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ba3df-112">Property</span></span> | <span data-ttu-id="ba3df-113">値</span><span class="sxs-lookup"><span data-stu-id="ba3df-113">Value</span></span> | <span data-ttu-id="ba3df-114">メモ</span><span class="sxs-lookup"><span data-stu-id="ba3df-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="ba3df-115">大文字と小文字の区別が一致しないため (JSON では `temperatureCelsius`)、プロパティは設定されません。</span><span class="sxs-lookup"><span data-stu-id="ba3df-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="ba3df-116">大文字と小文字の区別が一致しなかったため、この JSON プロパティは余分で、ディクショナリ内のキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="ba3df-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="ba3df-117">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="ba3df-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="ba3df-118">JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。</span><span class="sxs-lookup"><span data-stu-id="ba3df-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="ba3df-119">ターゲット オブジェクトがシリアル化されると、拡張データのキーと値のペアは、受信 JSON 内にあった場合と同様に JSON プロパティになります。</span><span class="sxs-lookup"><span data-stu-id="ba3df-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="ba3df-120">JSON には `ExtensionData` プロパティ名が表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ba3df-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="ba3df-121">この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンド トリップを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ba3df-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba3df-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba3df-122">See also</span></span>

* [<span data-ttu-id="ba3df-123">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="ba3df-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="ba3df-124">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="ba3df-124">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="ba3df-125">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="ba3df-125">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="ba3df-126">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="ba3df-126">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="ba3df-127">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ba3df-127">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="ba3df-128">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="ba3df-128">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="ba3df-129">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="ba3df-129">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="ba3df-130">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="ba3df-130">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="ba3df-131">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="ba3df-131">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="ba3df-132">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="ba3df-132">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="ba3df-133">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="ba3df-133">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="ba3df-134">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ba3df-134">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="ba3df-135">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="ba3df-135">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="ba3df-136">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="ba3df-136">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="ba3df-137">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="ba3df-137">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="ba3df-138">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="ba3df-138">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="ba3df-139">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="ba3df-139">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
