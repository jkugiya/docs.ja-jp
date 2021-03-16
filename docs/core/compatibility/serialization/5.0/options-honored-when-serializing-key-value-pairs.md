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
# <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a>キーと値のペアのシリアル化および逆シリアル化時、PropertyNamingPolicy、PropertyNameCaseInsensitive、Encoder オプションが許可される

<xref:System.Text.Json.JsonSerializer> で、<xref:System.Collections.Generic.KeyValuePair%602> インスタンスの <xref:System.Collections.Generic.KeyValuePair%602.Key> および <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティ名をシリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.Encoder> オプションが許可されるようになりました。 また、<xref:System.Text.Json.JsonSerializer> で <xref:System.Collections.Generic.KeyValuePair%602> インスタンスを逆シリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> オプションが許可されるようになりました。

## <a name="change-description"></a>変更内容

### <a name="serialization"></a>シリアル化

<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> オプションおよび <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> オプションがあった場合でも、.NET Core 3.x バージョンと、[System.Text.Json NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json)の 4.6.0 から 4.7.2 のバージョンで、<xref:System.Collections.Generic.KeyValuePair%602> インスタンスのプロパティは常に "キー" と "値" として正確にシリアル化されます。 次のコード例は、指定したプロパティの名前付けポリシーで指定されている場合でも、シリアル化後に <xref:System.Collections.Generic.KeyValuePair%602.Key> プロパティと <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティがキャメル ケースで表記 "*されない*" ことを示しています。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

.NET 5 以降では、<xref:System.Collections.Generic.KeyValuePair%602> インスタンスをシリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.Encoder> オプションが許可されます。 次のコード例は、指定したプロパティの名前付けポリシーに従い、シリアル化後に <xref:System.Collections.Generic.KeyValuePair%602.Key> プロパティと <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティがキャメル ケースで表示されることを示しています。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

### <a name="deserialization"></a>逆シリアル化

JSON プロパティの名前が大文字で始まらない場合など、正確に `Key` および `Value` でない場合、.NET Core 3.x のバージョンと [System.Text.Json NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json)の 4.7. x バージョンにより、<xref:System.Text.Json.JsonException> がスローされます。 この例外は、指定したプロパティの名前付けポリシーで明示的にそれが許可されている場合でもスローされます。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

.NET 5 以降の場合、<xref:System.Text.Json.JsonSerializer> を使用してシリアル化するときに、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションと <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> オプションが許可されます。 たとえば、以下のコードスニペットは、指定されたプロパティ命名ポリシーでそれが許可されているため、小文字の <xref:System.Collections.Generic.KeyValuePair%602.Key> と <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティ名の逆シリアル化に成功したことを示しています。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

以前のバージョンでシリアル化されたペイロードに対応するために、逆シリアル化で照合されるよう、"Key" と "Value" には特殊文字が使用されます。 次のコード例で、<xref:System.Collections.Generic.KeyValuePair%602.Key> プロパティ名と <xref:System.Collections.Generic.KeyValuePair%602.Value> プロパティ名は <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> オプションに従ってキャメル ケースで表示されていませんが、正常に逆シリアル化されます。

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="reason-for-change"></a>変更理由

多くのお客様からのフィードバックにより、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> を許可する必要があることがわかりました。 完全を期すために、他の単純な従来の CLR オブジェクト (POCO) と同様に <xref:System.Collections.Generic.KeyValuePair%602> インスタンスが扱われるよう、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> オプションと <xref:System.Text.Json.JsonSerializerOptions.Encoder> オプションも許可されています。

## <a name="recommended-action"></a>推奨される操作

この変更による破壊的な影響がある場合は、希望のセマンティクスを実装する[カスタム コンバーター](../../../../standard/serialization/system-text-json-converters-how-to.md)を使用してください。

## <a name="affected-apis"></a>影響を受ける API

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
