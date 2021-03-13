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
# <a name="how-to-enable-case-insensitive-property-name-matching-with-systemtextjson"></a><span data-ttu-id="3e629-103">System.Text.Json で大文字と小文字を区別しないプロパティ名の照合を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="3e629-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="3e629-104">この記事では、`System.Text.Json` 名前空間を使用して、大文字と小文字を区別しないプロパティ名の照合を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e629-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="3e629-105">大文字と小文字を区別しないプロパティ照合</span><span class="sxs-lookup"><span data-stu-id="3e629-105">Case-insensitive property matching</span></span>

<span data-ttu-id="3e629-106">既定では、逆シリアル化では JSON とターゲット オブジェクトのプロパティとの間で大文字と小文字を区別したプロパティ名の一致が検索されます。</span><span class="sxs-lookup"><span data-stu-id="3e629-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="3e629-107">この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="3e629-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="3e629-108">[Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)では大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="3e629-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/DeserializeCaseInsensitive.vb" id="Deserialize":::

<span data-ttu-id="3e629-109">キャメル ケースのプロパティ名を持つ JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3e629-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="3e629-110">これはパスカル ケースのプロパティ名を持つ次の型に逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="3e629-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

## <a name="see-also"></a><span data-ttu-id="3e629-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e629-111">See also</span></span>

* [<span data-ttu-id="3e629-112">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="3e629-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="3e629-113">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="3e629-113">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="3e629-114">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="3e629-114">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="3e629-115">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="3e629-115">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="3e629-116">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="3e629-116">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="3e629-117">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="3e629-117">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="3e629-118">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="3e629-118">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="3e629-119">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="3e629-119">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="3e629-120">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="3e629-120">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="3e629-121">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="3e629-121">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="3e629-122">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="3e629-122">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="3e629-123">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="3e629-123">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="3e629-124">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="3e629-124">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="3e629-125">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="3e629-125">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="3e629-126">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="3e629-126">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="3e629-127">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="3e629-127">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="3e629-128">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="3e629-128">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
