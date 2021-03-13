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
# <a name="how-to-allow-some-kinds-of-invalid-json-with-systemtextjson"></a><span data-ttu-id="f4245-103">System.Text.Json でいくつかの種類の無効な JSON を許可する方法</span><span class="sxs-lookup"><span data-stu-id="f4245-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="f4245-104">この記事では、JSON でコメント、末尾のコンマ、および引用符で囲まれた数値を許可する方法と、数値を文字列として書き込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4245-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="f4245-105">コメントと末尾のコンマを許可する</span><span class="sxs-lookup"><span data-stu-id="f4245-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="f4245-106">既定では、JSON 内でコメントと末尾のコンマは使用できません。</span><span class="sxs-lookup"><span data-stu-id="f4245-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="f4245-107">JSON 内でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f4245-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="f4245-108">また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f4245-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f4245-109">両方を許可する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="f4245-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/DeserializeCommasComments.vb" id="Deserialize":::

<span data-ttu-id="f4245-110">次に、コメントと末尾のコンマを含む JSON の例を示します。</span><span class="sxs-lookup"><span data-stu-id="f4245-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="f4245-111">引用符で囲まれた数値を許可または記述する</span><span class="sxs-lookup"><span data-stu-id="f4245-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="f4245-112">シリアライザーの中には、数値が JSON 文字列としてエンコードされる (引用符で囲まれる) ものがあります。</span><span class="sxs-lookup"><span data-stu-id="f4245-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="f4245-113">例:</span><span class="sxs-lookup"><span data-stu-id="f4245-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="f4245-114">次の表記の代わりに、</span><span class="sxs-lookup"><span data-stu-id="f4245-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="f4245-115">引用符で囲まれた数値をシリアル化したり、引用符で囲まれた数値を入力オブジェクト グラフ全体で受け付けるには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> を設定します。</span><span class="sxs-lookup"><span data-stu-id="f4245-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/QuotedNumbers.vb" :::

<span data-ttu-id="f4245-116">ASP.NET Core を通じて間接的に `System.Text.Json` を使用すると、ASP.NET Core により [Web の既定のオプション](xref:System.Text.Json.JsonSerializerDefaults.Web)が指定されるため、逆シリアル化のときに引用符で囲まれた数値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4245-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="f4245-117">特定のプロパティ、フィールド、または型について引用符で囲まれた数値を許可または記述するには、[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="f4245-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="f4245-118">.NET Core 3.1 の `System.Text.Json` では、引用符で囲まれた数値のシリアル化または逆シリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f4245-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="f4245-119">詳細については、「[引用符で囲まれた数値を許可または記述する](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4245-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="f4245-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4245-120">See also</span></span>

* [<span data-ttu-id="f4245-121">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="f4245-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f4245-122">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="f4245-122">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="f4245-123">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="f4245-123">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="f4245-124">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="f4245-124">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="f4245-125">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="f4245-125">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="f4245-126">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="f4245-126">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="f4245-127">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="f4245-127">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="f4245-128">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="f4245-128">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="f4245-129">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="f4245-129">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="f4245-130">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="f4245-130">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="f4245-131">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="f4245-131">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f4245-132">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="f4245-132">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="f4245-133">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="f4245-133">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="f4245-134">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="f4245-134">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="f4245-135">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="f4245-135">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="f4245-136">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f4245-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f4245-137">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f4245-137">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
