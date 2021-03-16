---
title: 破壊的変更:キーと値のペアに対して PropertyNamingPolicy、PropertyNameCaseInsensitive、Encoder のオプションが許可される
description: .NET 5 での破壊的変更について学習します。キーと値のペア インスタンスの Key と Value のプロパティ名のシリアル化および逆シリアル化時、PropertyNamingPolicy、PropertyNameCaseInsensitive、Encoder のオプションが許可されます。
ms.date: 10/18/2020
ms.openlocfilehash: fe6298a677488574fdd7bdc7e887ed3b244ba8d6
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256323"
---
# <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a><span data-ttu-id="98ade-103">キーと値のペアのシリアル化および逆シリアル化時、PropertyNamingPolicy、PropertyNameCaseInsensitive、Encoder オプションが許可される</span><span class="sxs-lookup"><span data-stu-id="98ade-103">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>

<span data-ttu-id="98ade-104"><xref:System.Text.Json.JsonSerializer> で、<xref:System.Collections.Generic.KeyValuePair%602> インスタンスの <xref:System.Collections.Generic.KeyValuePair%602.Key> および <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティ名をシリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.Encoder> オプションが許可されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="98ade-104"><xref:System.Text.Json.JsonSerializer> now honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options when serializing the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names of a <xref:System.Collections.Generic.KeyValuePair%602> instance.</span></span> <span data-ttu-id="98ade-105">また、<xref:System.Text.Json.JsonSerializer> で <xref:System.Collections.Generic.KeyValuePair%602> インスタンスを逆シリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> オプションが許可されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="98ade-105">Additionally, <xref:System.Text.Json.JsonSerializer> honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options when deserializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span>

## <a name="change-description"></a><span data-ttu-id="98ade-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="98ade-106">Change description</span></span>

### <a name="serialization"></a><span data-ttu-id="98ade-107">シリアル化</span><span class="sxs-lookup"><span data-stu-id="98ade-107">Serialization</span></span>

<span data-ttu-id="98ade-108"><xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> オプションおよび <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> オプションがあった場合でも、.NET Core 3.x バージョンと、[System.Text.Json NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json)の 4.6.0 から 4.7.2 のバージョンで、<xref:System.Collections.Generic.KeyValuePair%602> インスタンスのプロパティは常に "キー" と "値" として正確にシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="98ade-108">In .NET Core 3.x versions and in the 4.6.0-4.7.2 versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), the properties of <xref:System.Collections.Generic.KeyValuePair%602> instances are always serialized as "Key" and "Value" exactly, regardless of any <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> and <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="98ade-109">次のコード例は、指定したプロパティの名前付けポリシーで指定されている場合でも、シリアル化後に <xref:System.Collections.Generic.KeyValuePair%602.Key> プロパティと <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティがキャメル ケースで表記 "*されない*" ことを示しています。</span><span class="sxs-lookup"><span data-stu-id="98ade-109">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are *not* camel-cased after serialization, even though the specified property-naming policy dictates so.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

<span data-ttu-id="98ade-110">.NET 5 以降では、<xref:System.Collections.Generic.KeyValuePair%602> インスタンスをシリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.Encoder> オプションが許可されます。</span><span class="sxs-lookup"><span data-stu-id="98ade-110">Starting in .NET 5, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are honored when serializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span> <span data-ttu-id="98ade-111">次のコード例は、指定したプロパティの名前付けポリシーに従い、シリアル化後に <xref:System.Collections.Generic.KeyValuePair%602.Key> プロパティと <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティがキャメル ケースで表示されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="98ade-111">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are camel-cased after serialization, in accordance with the specified property-naming policy.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

### <a name="deserialization"></a><span data-ttu-id="98ade-112">逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="98ade-112">Deserialization</span></span>

<span data-ttu-id="98ade-113">JSON プロパティの名前が大文字で始まらない場合など、正確に `Key` および `Value` でない場合、.NET Core 3.x のバージョンと [System.Text.Json NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json)の 4.7. x バージョンにより、<xref:System.Text.Json.JsonException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="98ade-113">In .NET Core 3.x versions and in the 4.7.x versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), a <xref:System.Text.Json.JsonException> is thrown when the JSON property names are not precisely `Key` and `Value`, for example, if they don't start with an uppercase letter.</span></span> <span data-ttu-id="98ade-114">この例外は、指定したプロパティの名前付けポリシーで明示的にそれが許可されている場合でもスローされます。</span><span class="sxs-lookup"><span data-stu-id="98ade-114">The exception is thrown even if a specified property-naming policy expressly permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

<span data-ttu-id="98ade-115">.NET 5 以降の場合、<xref:System.Text.Json.JsonSerializer> を使用してシリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> オプションが許可されます。</span><span class="sxs-lookup"><span data-stu-id="98ade-115">Starting in .NET 5, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options are honored when deserializing using <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="98ade-116">たとえば、以下のコードスニペットは、指定されたプロパティ命名ポリシーでそれが許可されているため、小文字の <xref:System.Collections.Generic.KeyValuePair%602.Key> と <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティ名の逆シリアル化に成功したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="98ade-116">For example, the following code snippet shows successful deserialization of lowercased <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names because the specified property-naming policy permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

<span data-ttu-id="98ade-117">以前のバージョンでシリアル化されたペイロードに対応するために、逆シリアル化で照合されるよう、"Key" と "Value" には特殊文字が使用されます。</span><span class="sxs-lookup"><span data-stu-id="98ade-117">To accommodate payloads that were serialized with previous versions, "Key" and "Value" are special-cased to match when deserializing.</span></span> <span data-ttu-id="98ade-118">次のコード例で、<xref:System.Collections.Generic.KeyValuePair%602.Key> プロパティ名と <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティ名は <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションに従ってキャメル ケースで表示されていませんが、正常に逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="98ade-118">Even though the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names aren't camel-cased according to the in <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> option in the following code example, they deserialize successfully.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

## <a name="version-introduced"></a><span data-ttu-id="98ade-119">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="98ade-119">Version introduced</span></span>

<span data-ttu-id="98ade-120">5.0</span><span class="sxs-lookup"><span data-stu-id="98ade-120">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="98ade-121">変更理由</span><span class="sxs-lookup"><span data-stu-id="98ade-121">Reason for change</span></span>

<span data-ttu-id="98ade-122">多くのお客様からのフィードバックにより、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> を許可する必要があることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="98ade-122">Substantial customer feedback indicated that the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> should be honored.</span></span> <span data-ttu-id="98ade-123">完全を期すために、他の単純な従来の CLR オブジェクト (POCO) と同様に <xref:System.Collections.Generic.KeyValuePair%602> インスタンスが扱われるよう、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> オプションと <xref:System.Text.Json.JsonSerializerOptions.Encoder> オプションも許可されています。</span><span class="sxs-lookup"><span data-stu-id="98ade-123">For completeness, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are also honored, so that <xref:System.Collections.Generic.KeyValuePair%602> instances are treated the same as any other plain old CLR object (POCO).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="98ade-124">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="98ade-124">Recommended action</span></span>

<span data-ttu-id="98ade-125">この変更による破壊的な影響がある場合は、希望のセマンティクスを実装する[カスタム コンバーター](../../../../standard/serialization/system-text-json-converters-how-to.md)を使用してください。</span><span class="sxs-lookup"><span data-stu-id="98ade-125">If this change is disruptive to you, you can use a [custom converter](../../../../standard/serialization/system-text-json-converters-how-to.md) that implements the desired semantics.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="98ade-126">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="98ade-126">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Serialize`
- `Overload:System.Text.Json.JsonSerializer.SerializeAsync`
- `Overload:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes`
- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
