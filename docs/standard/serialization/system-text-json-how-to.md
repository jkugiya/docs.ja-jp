---
title: C# を使用して JSON をシリアル化および逆シリアル化する方法 - .NET
description: System.Text.Json 名前空間を使用して .NET 内で JSON のシリアル化と逆シリアル化を行う方法について学習します。 サンプル コードが含まれています。
ms.date: 01/19/2021
ms.custom: contperf-fy21q2
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
ms.openlocfilehash: 4fc2686aee58512cbb39f5fb13375f271d255659
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624228"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>.NET 内で JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリングの解除) を行う方法

この記事では、<xref:System.Text.Json?displayProperty=fullName> 名前空間を使用して JavaScript Object Notation (JSON) のシリアル化と逆シリアル化を行う方法について示します。 `Newtonsoft.Json` から既存のコードを移植する場合は、[`System.Text.Json` に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事を参照してください。

指示とサンプル コードでは、ライブラリを [ASP.NET Core](/aspnet/core/) などのフレームワーク経由ではなく直接使用します。

シリアル化のサンプル コードの大部分では、JSON を "整形" するために <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します (人間が読みやすいようにインデントと空白文字が使用されます)。 運用環境で使用する場合は、通常、この設定の既定値である `false` をそのまま使用します。不要な空白を追加すると、パフォーマンスや帯域幅の使用率が著しく低下するおそれがあるためです。

コード例では、次のクラスとそのバリアントを参照しています。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

## <a name="visual-basic-support"></a>Visual Basic のサポート

System.Text.Json の一部で、Visual Basic でサポートされていない [ref 構造体](../../csharp/language-reference/builtin-types/struct.md#ref-struct)が使用されています。 Visual Basic で System.Text.Json ref 構造 API を使用しようとすると、BC40000 コンパイラ エラーが発生します。 このエラー メッセージは、問題が古い API であることを示していますが、実際の問題は、コンパイラでの ref 構造体のサポートの欠如です。 System.Text.Json の次の部分は、Visual Basic では使用できません。

* <xref:System.Text.Json.Utf8JsonReader> クラスです。 <xref:System.Text.Json.Serialization.JsonConverter%601.Read%2A?displayProperty=nameWithType> メソッドは `Utf8JsonReader` パラメーターを受け取るため、この制限は、Visual Basic を使用してカスタム コンバーターを記述することはできないことを意味します。 これを回避するには、C# ライブラリ アセンブリにカスタム コンバーターを実装し、VB プロジェクトからそのアセンブリを参照します。 これは、Visual Basic で行うのが、コンバーターをシリアライザーに登録するだけであることを前提としています。 Visual Basic コードからコンバーターの `Read` メソッドを呼び出すことはできません。
* <xref:System.ReadOnlySpan%601> 型を含む他の API のオーバーロード。 ほとんどのメソッドには、`ReadOnlySpan` の代わりに `String` を使用するオーバーロードが含まれています。

これらの制限が適用されるのは、"データを通過させる" だけの場合でも、言語サポートなしでは ref 構造体を安全に使用できないからです。 このエラーを無効にすると、メモリを破損するおそれのある Visual Basic コードが生成されるため、実行しないでください。

## <a name="namespaces"></a>名前空間

<xref:System.Text.Json> 名前空間には、すべてのエントリ ポイントと主要な型が含まれています。 <xref:System.Text.Json.Serialization> 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と API が含まれています。 この記事に示されているコード例では、次のいずれかまたは両方の名前空間に `using` ディレクティブが必要です。

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

```vb
Imports System.Text.Json
Imports System.Text.Json.Serialization
```

> [!IMPORTANT]
> <xref:System.Runtime.Serialization> 名前空間の属性は、`System.Text.Json` ではサポートされていません。

## <a name="how-to-write-net-objects-as-json-serialize"></a>.NET オブジェクトを JSON として書き込む方法 (シリアル化)

JSON を文字列またはファイルに書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。

次の例では、JSON を文字列として作成します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="Serialize":::

次の例では、同期コードを使用して JSON ファイルを作成します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFile.vb" id="Serialize":::

次の例では、非同期コードを使用して JSON ファイルを作成します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFileAsync.vb" id="Serialize":::

前の例では、シリアル化する型に型の推定を使用しています。 `Serialize()` のオーバーロードでは、ジェネリック型パラメーターを受け取ります。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a>シリアル化の例

コレクション型のプロパティとユーザー定義型を含むクラスの例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithPOCOs":::

> [!TIP]
> "POCO" は、[Plain Old CLR Object (単純な従来の CLR オブジェクト)](https://en.wikipedia.org/wiki/Plain_old_CLR_object) を表します。 POCO は、継承や属性からなど、フレームワーク固有の型に依存しない .NET 型です。

前の型のインスタンスをシリアル化した場合の JSON 出力は、次の例のようになります。 既定では、JSON 出力は縮小されます (空白、インデント、および改行文字が削除されます)。

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

次の例では、同じ JSON ですが、書式設定されているもの (空白とインデントで整形されています) を示しています。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

## <a name="serialize-to-utf-8"></a>UTF-8 にシリアル化する

UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Serialize":::

<xref:System.Text.Json.Utf8JsonWriter> を受け取る <xref:System.Text.Json.JsonSerializer.Serialize%2A> オーバーロードも使用できます。

UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約 5-10% 高速です。 違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないことから生じます。

## <a name="serialization-behavior"></a>シリアル化の動作

::: zone pivot="dotnet-5-0"

* 既定では、すべてのパブリック プロパティがシリアル化されます。 [無視するプロパティを指定する](system-text-json-ignore-properties.md)ことができます。
* [既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。
* 既定では、JSON は縮小されます。 [JSON を整形](#serialize-to-formatted-json)することができます。
* 既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。 [JSON 名の大文字と小文字の区別をカスタマイズ](system-text-json-customize-properties.md)することができます。
* 既定では、循環参照が検出され、例外がスローされます。 [参照を保持し、循環参照を処理する](system-text-json-preserve-references.md)ことができます。
* 既定では、[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。 [フィールドを含める](#include-fields)ことができます。

ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。 詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 既定では、すべてのパブリック プロパティがシリアル化されます。 [無視するプロパティを指定する](system-text-json-ignore-properties.md)ことができます。
* [既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。
* 既定では、JSON は縮小されます。 [JSON を整形](#serialize-to-formatted-json)することができます。
* 既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。 [JSON 名の大文字と小文字の区別をカスタマイズ](system-text-json-customize-properties.md)することができます。
* 循環参照が検出され、例外がスローされます。
* [フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。
::: zone-end

サポートされる型には次のようなものがあります。
::: zone pivot="dotnet-5-0"

* 数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。
* ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。
* 1 次元配列とジャグ配列 (`T[][]`)。
* 次の名前空間のコレクションとディクショナリ。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。
* ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。
* 1 次元配列とジャグ配列 (`ArrayName[][]`)。
* `Dictionary<string,TValue>`。`TValue` は `object`、`JsonElement`、または POCO です。
* 次の名前空間からのコレクション。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、追加の型を処理したり、組み込みコンバーターではサポートされていない機能を提供したりすることができます。

## <a name="how-to-read-json-as-net-objects-deserialize"></a>JSON を .NET オブジェクトとして読み取る方法 (逆シリアル化)

文字列またはファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。

次の例では、文字列から JSON を読み取り、前に[シリアル化の例](#serialization-example)で示した `WeatherForecastWithPOCOs` クラスのインスタンスを作成します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="Deserialize":::

同期コードを使用してファイルから逆シリアル化するには、次の例に示すように、ファイルを文字列に読み取ります。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFile.vb" id="Deserialize":::

非同期コードを使用してファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> メソッドを呼び出します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFileAsync.vb" id="Deserialize":::

> [!TIP]
> 逆シリアル化する JSON があり、それを逆シリアル化するクラスがない場合は、Visual Studio 2019 によって必要なクラスを自動的に生成することができます。
>
> 1. 逆シリアル化する必要がある JSON をコピーします。
> 1. クラス ファイルを作成し、テンプレート コードを削除します。
> 1. **[編集]**  >  **[形式を選択して貼り付け]**  >  **[JSON をクラスとして貼り付ける]** を選択します。
>
> 結果は、逆シリアル化ターゲットに使用できるクラスになります。

## <a name="deserialize-from-utf-8"></a>UTF-8 からの逆シリアル化

UTF-8 から逆シリアル化するには、次の例に示すように、`ReadOnlySpan<byte>` または `Utf8JsonReader` を受け取る <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> オーバーロードを呼び出します。 この例では、JSON が jsonUtf8Bytes という名前のバイト配列内にあることを想定しています。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Deserialize2":::

## <a name="deserialization-behavior"></a>逆シリアル化の動作

JSON を逆シリアル化する場合、次の動作が適用されます。

::: zone pivot="dotnet-5-0"

* 既定では、プロパティ名の照合では大文字と小文字が区別されます。 [大文字と小文字を区別しないことを指定](system-text-json-character-casing.md)できます。
* JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。
* 非パブリック コンストラクターはシリアライザーにより無視されます。
* 不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされています。 「[不変の型とレコード](system-text-json-immutability.md)」を参照してください。
* 既定では、列挙型は数値としてサポートされています。 [列挙型名を文字列としてシリアル化](system-text-json-customize-properties.md#enums-as-strings)することができます。
* 既定では、フィールドは無視されます。 [フィールドを含める](#include-fields)ことができます。
* 既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。 [コメントと末尾のコンマを許可](system-text-json-invalid-json.md)することができます。
* [既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。

ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。 詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 既定では、プロパティ名の照合では大文字と小文字が区別されます。 [大文字と小文字を区別しないことを指定](system-text-json-character-casing.md)できます。 ASP.NET Core アプリの場合、[既定では大文字と小文字を区別しないことが指定](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)されます。
* JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。
* 逆シリアル化には、パラメーターなしのコンストラクター (public、internal、private のいずれか) が使用されます。
* 不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。
* 既定では、列挙型は数値としてサポートされています。 [列挙型名を文字列としてシリアル化](system-text-json-customize-properties.md#enums-as-strings)することができます。
* フィールドはサポートされません。
* 既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。 [コメントと末尾のコンマを許可](system-text-json-invalid-json.md)することができます。
* [既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。

ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。 詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。
::: zone-end

[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、組み込みコンバーターではサポートされていない機能を提供できます。

## <a name="serialize-to-formatted-json"></a>書式設定された JSON へのシリアル化

JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="SerializePrettyPrint":::

シリアル化され、整形された JSON 出力の型の例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

同じオプションで `JsonSerializerOptions` を繰り返し使用する場合、使用のたびに新しい `JsonSerializerOptions` インスタンスを作成しないでください。 すべての呼び出しで同じインスタンスを再利用します。 詳細については、[JsonSerializerOptions インスタンスの再利用](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)に関する説明を参照してください。

## <a name="include-fields"></a>フィールドを含める

::: zone pivot="dotnet-5-0"
次の例で示されているように、シリアル化または逆シリアル化のときにフィールドを含めるには、<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> グローバル設定または [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/Fields.vb" :::

読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。
::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 では、System.Text.Json メソッドはサポートされていません。 この機能は、[カスタム コンバーター](system-text-json-converters-how-to.md)で提供できます。
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>HttpClient と HttpContent の拡張メソッド

::: zone pivot="dotnet-5-0"

ネットワークからの JSON ペイロードのシリアル化と逆シリアル化は、一般的な操作です。 [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) および [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) の拡張メソッドを使用すると、これらの操作を 1 行のコードで実行できます。 これらの拡張メソッドにおいては、[JsonSerializerOptions の Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)が使用されます。

次の例では、<xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> と <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> の使用方法を示します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/HttpClientExtensionMethods.vb" :::

[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) には System.Text.Json 用の拡張メソッドもあります。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`HttpClient` および `HttpContent` の拡張メソッドは、.NET Core 3.1 の System.Text.Json では使用できません。
::: zone-end

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JsonSerializerOptions インスタンスのインスタンスを作成する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
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
* [System.Text.Json でサポートされているコレクション型](system-text-json-supported-collection-types.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
