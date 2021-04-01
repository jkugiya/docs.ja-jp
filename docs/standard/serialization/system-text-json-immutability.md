---
title: System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、変更できない型と非パブリック アクセサーを使用する方法について説明します。
ms.date: 02/08/2021
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
ms.openlocfilehash: 188ed6a5582f4677eb60963af72036963b5fe821
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206675"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-systemtextjson"></a><span data-ttu-id="37edf-103">System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法</span><span class="sxs-lookup"><span data-stu-id="37edf-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="37edf-104">この記事では、`System.Text.Json` 名前空間で不変の型、パラメーター化されたパブリック コンストラクター、および非パブリック アクセサーを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37edf-104">This article shows how to use immutable types, public parameterized constructors, and non-public accessors with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="37edf-105">不変の型とレコード</span><span class="sxs-lookup"><span data-stu-id="37edf-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="37edf-106">`System.Text.Json` ではパラメーター化されたパブリック コンストラクターを使用できるので、不変のクラスまたは構造体を逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="37edf-106">`System.Text.Json` can use a public parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="37edf-107">クラスの場合、パラメーター化されたコンストラクターしかない場合は、そのコンストラクターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="37edf-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="37edf-108">構造体または複数のコンストラクターを持つクラスの場合は、[[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) 属性を適用することにより、使用するコンストラクターを指定します。</span><span class="sxs-lookup"><span data-stu-id="37edf-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) attribute.</span></span> <span data-ttu-id="37edf-109">その属性を使用しないと、パラメーターなしのパブリック コンストラクターが存在する場合は常にそれが使用されます。</span><span class="sxs-lookup"><span data-stu-id="37edf-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="37edf-110">その属性は、パブリック コンストラクターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="37edf-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="37edf-111">次の例では、`[JsonConstructor]` 属性が使用されています。</span><span class="sxs-lookup"><span data-stu-id="37edf-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/ImmutableTypes.vb" :::

<span data-ttu-id="37edf-112">パラメーター化されたコンストラクターのパラメーター名は、プロパティ名と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="37edf-112">The parameter names of a parameterized constructor must match the property names.</span></span> <span data-ttu-id="37edf-113">一致では大文字と小文字は区別されません。また、[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) を使用してプロパティの名前を変更する場合でも、コンストラクター パラメーターは実際のプロパティ名と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="37edf-113">Matching is case-insensitive, and the constructor parameter must match the actual property name even if you use [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) to rename a property.</span></span> <span data-ttu-id="37edf-114">次の例では、`TemperatureC` プロパティの名前は、JSON では `celsius` に変更されていますが、コンストラクター パラメーターには引き続き `temperatureC` の名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="37edf-114">In the following example, the name for the `TemperatureC` property is changed to `celsius` in the JSON, but the constructor parameter is still named `temperatureC`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypesCtorParms.cs" highlight="10,14-16":::

<span data-ttu-id="37edf-115">`[JsonPropertyName]` に加え、次の属性でもパラメーター化されたコンストラクターでの逆シリアル化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="37edf-115">Besides `[JsonPropertyName]` the following attributes support deserialization with parameterized constructors:</span></span>

* <span data-ttu-id="37edf-116">[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)</span><span class="sxs-lookup"><span data-stu-id="37edf-116">[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)</span></span>
* <span data-ttu-id="37edf-117">[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)</span><span class="sxs-lookup"><span data-stu-id="37edf-117">[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)</span></span>
* <span data-ttu-id="37edf-118">[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)</span><span class="sxs-lookup"><span data-stu-id="37edf-118">[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)</span></span>
* <span data-ttu-id="37edf-119">[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute)</span><span class="sxs-lookup"><span data-stu-id="37edf-119">[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute)</span></span>

<span data-ttu-id="37edf-120">次の例で示されているように、C# 9 のレコードもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="37edf-120">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="37edf-121">すべてのプロパティ セッターが非パブリックであるために不変の型の場合は、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37edf-121">For types that are immutable because all their property setters are non-public, see the following section.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="37edf-122">`JsonConstructorAttribute` と C# 9 のレコードのサポートは、.NET Core 3.1 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="37edf-122">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="37edf-123">パブリックでないプロパティ アクセサー</span><span class="sxs-lookup"><span data-stu-id="37edf-123">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="37edf-124">パブリックでないプロパティ アクセサーを使用できるようにするには、次の例で示されているように、[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="37edf-124">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/NonPublicAccessors.vb" :::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="37edf-125">パブリックでないプロパティ アクセサーは、.NET Core 3.1 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="37edf-125">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="37edf-126">詳細については、[Newtonsoft.Json からの移行の記事](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37edf-126">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="37edf-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="37edf-127">See also</span></span>

* [<span data-ttu-id="37edf-128">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="37edf-128">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="37edf-129">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="37edf-129">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="37edf-130">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="37edf-130">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="37edf-131">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="37edf-131">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="37edf-132">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="37edf-132">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="37edf-133">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="37edf-133">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="37edf-134">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="37edf-134">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="37edf-135">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="37edf-135">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="37edf-136">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="37edf-136">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="37edf-137">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="37edf-137">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="37edf-138">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="37edf-138">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="37edf-139">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="37edf-139">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="37edf-140">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="37edf-140">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="37edf-141">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="37edf-141">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="37edf-142">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="37edf-142">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="37edf-143">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="37edf-143">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="37edf-144">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="37edf-144">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
