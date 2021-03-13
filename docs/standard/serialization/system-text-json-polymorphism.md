---
title: System.Text.Json で派生クラスのプロパティをシリアル化する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、ポリモーフィック オブジェクトをシリアル化する方法について説明します。
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
ms.openlocfilehash: e72264902a532435c41d933823a5fde3497e2e75
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584474"
---
# <a name="how-to-serialize-properties-of-derived-classes-with-systemtextjson"></a><span data-ttu-id="d1879-103">System.Text.Json で派生クラスのプロパティをシリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="d1879-103">How to serialize properties of derived classes with System.Text.Json</span></span>

<span data-ttu-id="d1879-104">この記事では、`System.Text.Json` 名前空間を使用して派生クラスのプロパティをシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1879-104">In this article, you will learn how to serialize properties of derived classes with the `System.Text.Json` namespace.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="d1879-105">派生クラスのプロパティのシリアル化</span><span class="sxs-lookup"><span data-stu-id="d1879-105">Serialize properties of derived classes</span></span>

<span data-ttu-id="d1879-106">ポリモーフィック型の階層のシリアル化はサポートされて "_いません_"。</span><span class="sxs-lookup"><span data-stu-id="d1879-106">Serialization of a polymorphic type hierarchy is _not_ supported.</span></span> <span data-ttu-id="d1879-107">たとえば、プロパティがインターフェイスまたは抽象クラスとして定義されている場合は、ランタイム型に追加のプロパティがある場合でも、インターフェイスまたは抽象クラスに定義されたプロパティのみがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="d1879-107">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="d1879-108">この動作の例外については、このセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="d1879-108">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="d1879-109">たとえば、`WeatherForecast` クラスと派生クラス `WeatherForecastDerived` があるとします。</span><span class="sxs-lookup"><span data-stu-id="d1879-109">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFDerived":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFDerived":::

<span data-ttu-id="d1879-110">また、コンパイル時の `Serialize` メソッドの型引数が `WeatherForecast` であるとします。</span><span class="sxs-lookup"><span data-stu-id="d1879-110">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeDefault":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeDefault":::

<span data-ttu-id="d1879-111">このシナリオでは、`weatherForecast` オブジェクトが実際には `WeatherForecastDerived` オブジェクトであっても、`WindSpeed` プロパティはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="d1879-111">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="d1879-112">基本クラスのプロパティのみがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="d1879-112">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="d1879-113">この動作は、ランタイムによって作成される派生型内でデータが誤って公開されるのを防ぐためのものです。</span><span class="sxs-lookup"><span data-stu-id="d1879-113">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="d1879-114">前の例で派生型のプロパティをシリアル化するには、次のいずれかのアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1879-114">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="d1879-115">実行時に型を指定できるようにする <xref:System.Text.Json.JsonSerializer.Serialize%2A> のオーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d1879-115">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeGetType":::
  :::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeGetType":::

* <span data-ttu-id="d1879-116">オブジェクトを `object` としてシリアル化するように宣言します。</span><span class="sxs-lookup"><span data-stu-id="d1879-116">Declare the object to be serialized as `object`.</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeObject":::
  :::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeObject":::

<span data-ttu-id="d1879-117">前の例のシナリオでは、どちらのアプローチでも、`WindSpeed` プロパティが JSON 出力に含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1879-117">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="d1879-118">これらのアプローチでは、シリアル化するルート オブジェクトに対してのみポリモーフィックなシリアル化が提供され、そのルート オブジェクトのプロパティに対しては提供されません。</span><span class="sxs-lookup"><span data-stu-id="d1879-118">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="d1879-119">`object` 型として定義すると、下位レベルのオブジェクトのポリモーフィックなシリアル化を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d1879-119">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="d1879-120">たとえば、`WeatherForecast` クラスに、`WeatherForecast` または `object` 型として定義できる `PreviousForecast` という名前のプロパティがあるとします。</span><span class="sxs-lookup"><span data-stu-id="d1879-120">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPrevious":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithPrevious":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPreviousAsObject":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithPreviousAsObject":::

<span data-ttu-id="d1879-121">`PreviousForecast` プロパティに `WeatherForecastDerived` のインスタンスが含まれる場合:</span><span class="sxs-lookup"><span data-stu-id="d1879-121">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="d1879-122">`WeatherForecastWithPrevious` のシリアル化からの JSON 出力には `WindSpeed` が **含まれていません**。</span><span class="sxs-lookup"><span data-stu-id="d1879-122">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="d1879-123">`WeatherForecastWithPreviousAsObject` のシリアル化からの JSON 出力には `WindSpeed` が **含まれています**。</span><span class="sxs-lookup"><span data-stu-id="d1879-123">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="d1879-124">ルート オブジェクトは派生型である可能性があるものではないため、`WeatherForecastWithPreviousAsObject` をシリアル化するために `Serialize<object>` または `GetType` を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d1879-124">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="d1879-125">次のコード例では `Serialize<object>` または `GetType` は呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="d1879-125">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeSecondLevel":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeSecondLevel":::

<span data-ttu-id="d1879-126">上記のコードでは、`WeatherForecastWithPreviousAsObject` が正しくシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="d1879-126">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="d1879-127">`object` と同じプロパティ定義のアプローチがインターフェイスで機能します。</span><span class="sxs-lookup"><span data-stu-id="d1879-127">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="d1879-128">次のインターフェイスと実装があり、実装インスタンスを含むプロパティを使用してクラスをシリアル化するとします。</span><span class="sxs-lookup"><span data-stu-id="d1879-128">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/IForecast.cs":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/IForecast.vb":::

<span data-ttu-id="d1879-129">`Forecasts` のインスタンスをシリアル化する場合、`Tuesday` は `object` として定義されているので、`Tuesday` にのみ `WindSpeed` プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1879-129">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeInterface":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializePolymorphic.vb" id="SerializeInterface":::

<span data-ttu-id="d1879-130">次の例は、前のコードから生成された JSON を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1879-130">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="d1879-131">ポリモーフィック **シリアル化** の詳細、および **逆シリアル化** の詳細については、「[Newtonsoft.Json から System.Text.Json に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1879-131">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1879-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1879-132">See also</span></span>

* [<span data-ttu-id="d1879-133">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="d1879-133">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="d1879-134">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="d1879-134">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="d1879-135">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="d1879-135">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="d1879-136">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="d1879-136">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="d1879-137">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="d1879-137">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="d1879-138">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="d1879-138">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="d1879-139">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="d1879-139">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="d1879-140">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="d1879-140">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="d1879-141">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="d1879-141">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="d1879-142">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="d1879-142">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="d1879-143">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="d1879-143">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="d1879-144">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="d1879-144">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="d1879-145">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="d1879-145">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="d1879-146">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="d1879-146">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="d1879-147">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="d1879-147">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="d1879-148">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d1879-148">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="d1879-149">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="d1879-149">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
