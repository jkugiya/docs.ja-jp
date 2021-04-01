---
title: System.Text.Json で参照を保持する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、参照を保持し、循環参照を処理する方法について説明します。
ms.date: 01/12/2021
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
ms.openlocfilehash: 0dda695c7e21090f68703309da03d5158fc858f1
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584057"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-systemtextjson"></a><span data-ttu-id="a5f6b-103">System.Text.Json で参照を保持して循環参照を処理する</span><span class="sxs-lookup"><span data-stu-id="a5f6b-103">How to preserve references and handle circular references with System.Text.Json</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="a5f6b-104">参照を保持し、循環参照を処理するには、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> を <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-104">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="a5f6b-105">これを設定すると、次のような動作になります。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-105">This setting causes the following behavior:</span></span>

* <span data-ttu-id="a5f6b-106">シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="a5f6b-106">On serialize:</span></span>

  <span data-ttu-id="a5f6b-107">複合型を書き込むとき、シリアライザーによってメタデータのプロパティ (`$id`、`$values`、`$ref`) も書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-107">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="a5f6b-108">逆シリアル化のとき:</span><span class="sxs-lookup"><span data-stu-id="a5f6b-108">On deserialize:</span></span>

  <span data-ttu-id="a5f6b-109">メタデータが想定され (必須ではありません)、逆シリアライザーによってその理解が試みられます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-109">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="a5f6b-110">次のコードでは、`Preserve` 設定の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-110">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/PreserveReferences.vb" :::

<span data-ttu-id="a5f6b-111">この機能を使用して、値型または不変型を保持することはできません。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-111">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="a5f6b-112">逆シリアル化のとき、不変型のインスタンスは、ペイロード全体が読み取られた後で作成されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-112">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="a5f6b-113">そのため、同じインスタンスへの参照が JSON ペイロード内に含まれている場合、それを逆シリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-113">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="a5f6b-114">値型、不変型、配列の場合、参照メタデータはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-114">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="a5f6b-115">逆シリアル化では、`$ref` または `$id` が検出されると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-115">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="a5f6b-116">ただし、Newtonsoft.Json を使用してシリアル化されたペイロードを逆シリアル化できるようにするため、`$id` (および、コレクションの場合は `$values`) は値型で無視されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-116">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="a5f6b-117">Newtonsoft.Json の場合は、そのような型のメタデータがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-117">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="a5f6b-118">オブジェクトが等しいかどうかを判断するために System.Text.Json によって使用される <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> では、2 つのオブジェクト インスタンスを比較するときに、値の等価性 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>) ではなく参照の等価性 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-118">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="a5f6b-119">参照がシリアル化および逆シリアル化される方法の詳細については、<xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-119">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a5f6b-120">シリアル化および逆シリアル化で参照を維持するための動作は、<xref:System.Text.Json.Serialization.ReferenceResolver> クラスによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-120">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="a5f6b-121">カスタム動作を指定するには、派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-121">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="a5f6b-122">例については、[GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-122">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

## <a name="persist-reference-metadata-across-multiple-serialization-and-deserialization-calls"></a><span data-ttu-id="a5f6b-123">複数のシリアル化および逆シリアル化呼び出し間で参照メタデータを保持する</span><span class="sxs-lookup"><span data-stu-id="a5f6b-123">Persist reference metadata across multiple serialization and deserialization calls</span></span>

<span data-ttu-id="a5f6b-124">既定では、参照データは <xref:System.Text.Json.JsonSerializer.Serialize%2A> または <xref:System.Text.Json.JsonSerializer.Deserialize%2A> への呼び出しごとにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-124">By default, reference data is only cached for each call to <xref:System.Text.Json.JsonSerializer.Serialize%2A> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A>.</span></span> <span data-ttu-id="a5f6b-125">ある `Serialize`/`Deserialize` 呼び出しから別の呼び出しへの参照を保持するには、`Serialize`/`Deserialize` の呼び出しサイトで <xref:System.Text.Json.Serialization.ReferenceResolver> インスタンスをルート化します。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-125">To persist references from one `Serialize`/`Deserialize` call to another one, root the <xref:System.Text.Json.Serialization.ReferenceResolver> instance in the call site of `Serialize`/`Deserialize`.</span></span> <span data-ttu-id="a5f6b-126">このスクリプトの例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-126">The following code shows an example for this scenario:</span></span>

* <span data-ttu-id="a5f6b-127">`Employee` のリストがあり、それぞれを個別にシリアル化する必要がある。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-127">You have a list of `Employee`s and you have to serialize each one individually.</span></span>
* <span data-ttu-id="a5f6b-128">`ReferenceHandler` のリゾルバーに保存されている参照を利用したい。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-128">you want to take advantage of the references saved in the `ReferenceHandler`'s resolver.</span></span>

<span data-ttu-id="a5f6b-129">ここでは `Employee` クラスです。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-129">Here is the `Employee` class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="Employee":::

<span data-ttu-id="a5f6b-130"><xref:System.Text.Json.Serialization.ReferenceResolver> から派生するクラスは、参照をディクショナリに格納します。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-130">A class that derives from <xref:System.Text.Json.Serialization.ReferenceResolver> stores the references in a dictionary:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceResolver":::

<span data-ttu-id="a5f6b-131"><xref:System.Text.Json.Serialization.ReferenceHandler> から派生するクラスは、`MyReferenceResolver` のインスタンスを保持し、必要な場合にのみ新しいインスタンスを作成します (この例では `Reset` という名前のメソッド)。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-131">A class that derives from <xref:System.Text.Json.Serialization.ReferenceHandler> holds an instance of `MyReferenceResolver` and creates a new instance only when needed (in a method named `Reset` in this example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceHandler":::

<span data-ttu-id="a5f6b-132">このサンプル コードは、シリアライザーを呼び出すときに、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> プロパティが `MyReferenceHandler` のインスタンスに設定されている <xref:System.Text.Json.JsonSerializerOptions> インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-132">When the sample code calls the serializer, it uses a <xref:System.Text.Json.JsonSerializerOptions> instance in which the <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> property is set to an instance of `MyReferenceHandler`.</span></span> <span data-ttu-id="a5f6b-133">このパターンに従う場合は、シリアル化が終了したときに必ず `ReferenceResolver` ディクショナリをリセットして、継続的に拡大しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-133">When you follow this pattern, be sure to reset the `ReferenceResolver` dictionary when you're finished serializing, to keep it from growing forever.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="CallSerializer" highlight = "3-4,14":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="a5f6b-134">.NET Core 3.1 の System.Text.Json でサポートされているのは値によるシリアル化のみであり、循環参照の場合は例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a5f6b-134">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="a5f6b-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5f6b-135">See also</span></span>

* [<span data-ttu-id="a5f6b-136">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="a5f6b-136">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="a5f6b-137">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="a5f6b-137">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="a5f6b-138">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="a5f6b-138">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="a5f6b-139">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="a5f6b-139">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="a5f6b-140">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="a5f6b-140">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="a5f6b-141">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="a5f6b-141">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="a5f6b-142">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="a5f6b-142">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="a5f6b-143">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="a5f6b-143">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="a5f6b-144">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="a5f6b-144">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="a5f6b-145">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="a5f6b-145">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="a5f6b-146">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="a5f6b-146">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="a5f6b-147">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="a5f6b-147">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="a5f6b-148">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="a5f6b-148">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="a5f6b-149">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="a5f6b-149">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="a5f6b-150">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="a5f6b-150">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="a5f6b-151">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a5f6b-151">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="a5f6b-152">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="a5f6b-152">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
