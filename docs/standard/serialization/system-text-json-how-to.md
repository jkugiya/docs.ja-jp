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
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="be787-104">.NET 内で JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリングの解除) を行う方法</span><span class="sxs-lookup"><span data-stu-id="be787-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="be787-105">この記事では、<xref:System.Text.Json?displayProperty=fullName> 名前空間を使用して JavaScript Object Notation (JSON) のシリアル化と逆シリアル化を行う方法について示します。</span><span class="sxs-lookup"><span data-stu-id="be787-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="be787-106">`Newtonsoft.Json` から既存のコードを移植する場合は、[`System.Text.Json` に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be787-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="be787-107">指示とサンプル コードでは、ライブラリを [ASP.NET Core](/aspnet/core/) などのフレームワーク経由ではなく直接使用します。</span><span class="sxs-lookup"><span data-stu-id="be787-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="be787-108">シリアル化のサンプル コードの大部分では、JSON を "整形" するために <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します (人間が読みやすいようにインデントと空白文字が使用されます)。</span><span class="sxs-lookup"><span data-stu-id="be787-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="be787-109">運用環境で使用する場合は、通常、この設定の既定値である `false` をそのまま使用します。不要な空白を追加すると、パフォーマンスや帯域幅の使用率が著しく低下するおそれがあるためです。</span><span class="sxs-lookup"><span data-stu-id="be787-109">For production use, you would typically accept the default value of `false` for this setting, since adding unnecessary whitespace may incur a noticeable, negative impact on performance and bandwidth usage.</span></span>

<span data-ttu-id="be787-110">コード例では、次のクラスとそのバリアントを参照しています。</span><span class="sxs-lookup"><span data-stu-id="be787-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

## <a name="visual-basic-support"></a><span data-ttu-id="be787-111">Visual Basic のサポート</span><span class="sxs-lookup"><span data-stu-id="be787-111">Visual Basic support</span></span>

<span data-ttu-id="be787-112">System.Text.Json の一部で、Visual Basic でサポートされていない [ref 構造体](../../csharp/language-reference/builtin-types/struct.md#ref-struct)が使用されています。</span><span class="sxs-lookup"><span data-stu-id="be787-112">Parts of System.Text.Json use [ref structs](../../csharp/language-reference/builtin-types/struct.md#ref-struct), which are not supported by Visual Basic.</span></span> <span data-ttu-id="be787-113">Visual Basic で System.Text.Json ref 構造 API を使用しようとすると、BC40000 コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="be787-113">If you try to use System.Text.Json ref struct APIs with Visual Basic you get BC40000 compiler errors.</span></span> <span data-ttu-id="be787-114">このエラー メッセージは、問題が古い API であることを示していますが、実際の問題は、コンパイラでの ref 構造体のサポートの欠如です。</span><span class="sxs-lookup"><span data-stu-id="be787-114">The error message indicates that the problem is an obsolete API, but the actual issue is lack of ref struct support in the compiler.</span></span> <span data-ttu-id="be787-115">System.Text.Json の次の部分は、Visual Basic では使用できません。</span><span class="sxs-lookup"><span data-stu-id="be787-115">The following parts of System.Text.Json aren't usable from Visual Basic:</span></span>

* <span data-ttu-id="be787-116"><xref:System.Text.Json.Utf8JsonReader> クラスです。</span><span class="sxs-lookup"><span data-stu-id="be787-116">The <xref:System.Text.Json.Utf8JsonReader> class.</span></span> <span data-ttu-id="be787-117"><xref:System.Text.Json.Serialization.JsonConverter%601.Read%2A?displayProperty=nameWithType> メソッドは `Utf8JsonReader` パラメーターを受け取るため、この制限は、Visual Basic を使用してカスタム コンバーターを記述することはできないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="be787-117">Since the <xref:System.Text.Json.Serialization.JsonConverter%601.Read%2A?displayProperty=nameWithType> method takes a `Utf8JsonReader` parameter, this limitation means you can't use Visual Basic to write custom converters.</span></span> <span data-ttu-id="be787-118">これを回避するには、C# ライブラリ アセンブリにカスタム コンバーターを実装し、VB プロジェクトからそのアセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="be787-118">A workaround for this is to implement custom converters in a C# library assembly, and reference that assembly from your VB project.</span></span> <span data-ttu-id="be787-119">これは、Visual Basic で行うのが、コンバーターをシリアライザーに登録するだけであることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="be787-119">This assumes that all you do in Visual Basic is register the converters into the serializer.</span></span> <span data-ttu-id="be787-120">Visual Basic コードからコンバーターの `Read` メソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="be787-120">You can't call the `Read` methods of the converters from Visual Basic code.</span></span>
* <span data-ttu-id="be787-121"><xref:System.ReadOnlySpan%601> 型を含む他の API のオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="be787-121">Overloads of other APIs that include a <xref:System.ReadOnlySpan%601> type.</span></span> <span data-ttu-id="be787-122">ほとんどのメソッドには、`ReadOnlySpan` の代わりに `String` を使用するオーバーロードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="be787-122">Most methods include overloads that use `String` instead of `ReadOnlySpan`.</span></span>

<span data-ttu-id="be787-123">これらの制限が適用されるのは、"データを通過させる" だけの場合でも、言語サポートなしでは ref 構造体を安全に使用できないからです。</span><span class="sxs-lookup"><span data-stu-id="be787-123">These restrictions are in place because ref structs cannot be used safely without language support, even when just "passing data through."</span></span> <span data-ttu-id="be787-124">このエラーを無効にすると、メモリを破損するおそれのある Visual Basic コードが生成されるため、実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="be787-124">Subverting this error will result in Visual Basic code that can corrupt memory and should not be done.</span></span>

## <a name="namespaces"></a><span data-ttu-id="be787-125">名前空間</span><span class="sxs-lookup"><span data-stu-id="be787-125">Namespaces</span></span>

<span data-ttu-id="be787-126"><xref:System.Text.Json> 名前空間には、すべてのエントリ ポイントと主要な型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="be787-126">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="be787-127"><xref:System.Text.Json.Serialization> 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="be787-127">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="be787-128">この記事に示されているコード例では、次のいずれかまたは両方の名前空間に `using` ディレクティブが必要です。</span><span class="sxs-lookup"><span data-stu-id="be787-128">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

```vb
Imports System.Text.Json
Imports System.Text.Json.Serialization
```

> [!IMPORTANT]
> <span data-ttu-id="be787-129"><xref:System.Runtime.Serialization> 名前空間の属性は、`System.Text.Json` ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="be787-129">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="be787-130">.NET オブジェクトを JSON として書き込む方法 (シリアル化)</span><span class="sxs-lookup"><span data-stu-id="be787-130">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="be787-131">JSON を文字列またはファイルに書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="be787-131">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="be787-132">次の例では、JSON を文字列として作成します。</span><span class="sxs-lookup"><span data-stu-id="be787-132">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="Serialize":::

<span data-ttu-id="be787-133">次の例では、同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="be787-133">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFile.vb" id="Serialize":::

<span data-ttu-id="be787-134">次の例では、非同期コードを使用して JSON ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="be787-134">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFileAsync.vb" id="Serialize":::

<span data-ttu-id="be787-135">前の例では、シリアル化する型に型の推定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="be787-135">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="be787-136">`Serialize()` のオーバーロードでは、ジェネリック型パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="be787-136">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="be787-137">シリアル化の例</span><span class="sxs-lookup"><span data-stu-id="be787-137">Serialization example</span></span>

<span data-ttu-id="be787-138">コレクション型のプロパティとユーザー定義型を含むクラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be787-138">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="be787-139">"POCO" は、[Plain Old CLR Object (単純な従来の CLR オブジェクト)](https://en.wikipedia.org/wiki/Plain_old_CLR_object) を表します。</span><span class="sxs-lookup"><span data-stu-id="be787-139">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="be787-140">POCO は、継承や属性からなど、フレームワーク固有の型に依存しない .NET 型です。</span><span class="sxs-lookup"><span data-stu-id="be787-140">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="be787-141">前の型のインスタンスをシリアル化した場合の JSON 出力は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="be787-141">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="be787-142">既定では、JSON 出力は縮小されます (空白、インデント、および改行文字が削除されます)。</span><span class="sxs-lookup"><span data-stu-id="be787-142">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="be787-143">次の例では、同じ JSON ですが、書式設定されているもの (空白とインデントで整形されています) を示しています。</span><span class="sxs-lookup"><span data-stu-id="be787-143">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

## <a name="serialize-to-utf-8"></a><span data-ttu-id="be787-144">UTF-8 にシリアル化する</span><span class="sxs-lookup"><span data-stu-id="be787-144">Serialize to UTF-8</span></span>

<span data-ttu-id="be787-145">UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="be787-145">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Serialize":::

<span data-ttu-id="be787-146"><xref:System.Text.Json.Utf8JsonWriter> を受け取る <xref:System.Text.Json.JsonSerializer.Serialize%2A> オーバーロードも使用できます。</span><span class="sxs-lookup"><span data-stu-id="be787-146">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="be787-147">UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約 5-10% 高速です。</span><span class="sxs-lookup"><span data-stu-id="be787-147">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="be787-148">違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないことから生じます。</span><span class="sxs-lookup"><span data-stu-id="be787-148">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="be787-149">シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="be787-149">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="be787-150">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="be787-150">By default, all public properties are serialized.</span></span> <span data-ttu-id="be787-151">[無視するプロパティを指定する](system-text-json-ignore-properties.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="be787-151">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="be787-152">[既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="be787-152">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="be787-153">既定では、JSON は縮小されます。</span><span class="sxs-lookup"><span data-stu-id="be787-153">By default, JSON is minified.</span></span> <span data-ttu-id="be787-154">[JSON を整形](#serialize-to-formatted-json)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-154">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="be787-155">既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。</span><span class="sxs-lookup"><span data-stu-id="be787-155">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="be787-156">[JSON 名の大文字と小文字の区別をカスタマイズ](system-text-json-customize-properties.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-156">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="be787-157">既定では、循環参照が検出され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="be787-157">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="be787-158">[参照を保持し、循環参照を処理する](system-text-json-preserve-references.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="be787-158">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="be787-159">既定では、[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="be787-159">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="be787-160">[フィールドを含める](#include-fields)ことができます。</span><span class="sxs-lookup"><span data-stu-id="be787-160">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="be787-161">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="be787-161">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="be787-162">詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be787-162">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="be787-163">既定では、すべてのパブリック プロパティがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="be787-163">By default, all public properties are serialized.</span></span> <span data-ttu-id="be787-164">[無視するプロパティを指定する](system-text-json-ignore-properties.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="be787-164">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="be787-165">[既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="be787-165">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="be787-166">既定では、JSON は縮小されます。</span><span class="sxs-lookup"><span data-stu-id="be787-166">By default, JSON is minified.</span></span> <span data-ttu-id="be787-167">[JSON を整形](#serialize-to-formatted-json)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-167">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="be787-168">既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。</span><span class="sxs-lookup"><span data-stu-id="be787-168">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="be787-169">[JSON 名の大文字と小文字の区別をカスタマイズ](system-text-json-customize-properties.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-169">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="be787-170">循環参照が検出され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="be787-170">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="be787-171">[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。</span><span class="sxs-lookup"><span data-stu-id="be787-171">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="be787-172">サポートされる型には次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="be787-172">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="be787-173">数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。</span><span class="sxs-lookup"><span data-stu-id="be787-173">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="be787-174">ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="be787-174">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="be787-175">1 次元配列とジャグ配列 (`T[][]`)。</span><span class="sxs-lookup"><span data-stu-id="be787-175">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="be787-176">次の名前空間のコレクションとディクショナリ。</span><span class="sxs-lookup"><span data-stu-id="be787-176">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="be787-177">数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。</span><span class="sxs-lookup"><span data-stu-id="be787-177">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="be787-178">ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。</span><span class="sxs-lookup"><span data-stu-id="be787-178">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="be787-179">1 次元配列とジャグ配列 (`ArrayName[][]`)。</span><span class="sxs-lookup"><span data-stu-id="be787-179">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="be787-180">`Dictionary<string,TValue>`。`TValue` は `object`、`JsonElement`、または POCO です。</span><span class="sxs-lookup"><span data-stu-id="be787-180">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="be787-181">次の名前空間からのコレクション。</span><span class="sxs-lookup"><span data-stu-id="be787-181">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="be787-182">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、追加の型を処理したり、組み込みコンバーターではサポートされていない機能を提供したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="be787-182">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="be787-183">JSON を .NET オブジェクトとして読み取る方法 (逆シリアル化)</span><span class="sxs-lookup"><span data-stu-id="be787-183">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="be787-184">文字列またはファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="be787-184">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="be787-185">次の例では、文字列から JSON を読み取り、前に[シリアル化の例](#serialization-example)で示した `WeatherForecastWithPOCOs` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="be787-185">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="Deserialize":::

<span data-ttu-id="be787-186">同期コードを使用してファイルから逆シリアル化するには、次の例に示すように、ファイルを文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="be787-186">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFile.vb" id="Deserialize":::

<span data-ttu-id="be787-187">非同期コードを使用してファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="be787-187">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToFileAsync.vb" id="Deserialize":::

> [!TIP]
> <span data-ttu-id="be787-188">逆シリアル化する JSON があり、それを逆シリアル化するクラスがない場合は、Visual Studio 2019 によって必要なクラスを自動的に生成することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-188">If you have JSON that you want to deserialize, and you don't have the class to deserialize it into, Visual Studio 2019 can automatically generate the class you need:</span></span>
>
> 1. <span data-ttu-id="be787-189">逆シリアル化する必要がある JSON をコピーします。</span><span class="sxs-lookup"><span data-stu-id="be787-189">Copy the JSON that you need to deserialize.</span></span>
> 1. <span data-ttu-id="be787-190">クラス ファイルを作成し、テンプレート コードを削除します。</span><span class="sxs-lookup"><span data-stu-id="be787-190">Create a class file and delete the template code.</span></span>
> 1. <span data-ttu-id="be787-191">**[編集]**  >  **[形式を選択して貼り付け]**  >  **[JSON をクラスとして貼り付ける]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="be787-191">Choose **Edit** > **Paste Special** > **Paste JSON as Classes**.</span></span>
>
> <span data-ttu-id="be787-192">結果は、逆シリアル化ターゲットに使用できるクラスになります。</span><span class="sxs-lookup"><span data-stu-id="be787-192">The result is a class that you can use for your deserialization target.</span></span>

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="be787-193">UTF-8 からの逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="be787-193">Deserialize from UTF-8</span></span>

<span data-ttu-id="be787-194">UTF-8 から逆シリアル化するには、次の例に示すように、`ReadOnlySpan<byte>` または `Utf8JsonReader` を受け取る <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> オーバーロードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="be787-194">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="be787-195">この例では、JSON が jsonUtf8Bytes という名前のバイト配列内にあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="be787-195">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToUtf8.vb" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="be787-196">逆シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="be787-196">Deserialization behavior</span></span>

<span data-ttu-id="be787-197">JSON を逆シリアル化する場合、次の動作が適用されます。</span><span class="sxs-lookup"><span data-stu-id="be787-197">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="be787-198">既定では、プロパティ名の照合では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="be787-198">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="be787-199">[大文字と小文字を区別しないことを指定](system-text-json-character-casing.md)できます。</span><span class="sxs-lookup"><span data-stu-id="be787-199">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="be787-200">JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="be787-200">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="be787-201">非パブリック コンストラクターはシリアライザーにより無視されます。</span><span class="sxs-lookup"><span data-stu-id="be787-201">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="be787-202">不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be787-202">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="be787-203">「[不変の型とレコード](system-text-json-immutability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be787-203">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="be787-204">既定では、列挙型は数値としてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be787-204">By default, enums are supported as numbers.</span></span> <span data-ttu-id="be787-205">[列挙型名を文字列としてシリアル化](system-text-json-customize-properties.md#enums-as-strings)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-205">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="be787-206">既定では、フィールドは無視されます。</span><span class="sxs-lookup"><span data-stu-id="be787-206">By default, fields are ignored.</span></span> <span data-ttu-id="be787-207">[フィールドを含める](#include-fields)ことができます。</span><span class="sxs-lookup"><span data-stu-id="be787-207">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="be787-208">既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="be787-208">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="be787-209">[コメントと末尾のコンマを許可](system-text-json-invalid-json.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-209">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="be787-210">[既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。</span><span class="sxs-lookup"><span data-stu-id="be787-210">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="be787-211">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="be787-211">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="be787-212">詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be787-212">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="be787-213">既定では、プロパティ名の照合では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="be787-213">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="be787-214">[大文字と小文字を区別しないことを指定](system-text-json-character-casing.md)できます。</span><span class="sxs-lookup"><span data-stu-id="be787-214">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="be787-215">ASP.NET Core アプリの場合、[既定では大文字と小文字を区別しないことが指定](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)されます。</span><span class="sxs-lookup"><span data-stu-id="be787-215">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="be787-216">JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="be787-216">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="be787-217">逆シリアル化には、パラメーターなしのコンストラクター (public、internal、private のいずれか) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="be787-217">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="be787-218">不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="be787-218">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="be787-219">既定では、列挙型は数値としてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be787-219">By default, enums are supported as numbers.</span></span> <span data-ttu-id="be787-220">[列挙型名を文字列としてシリアル化](system-text-json-customize-properties.md#enums-as-strings)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-220">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="be787-221">フィールドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="be787-221">Fields aren't supported.</span></span>
* <span data-ttu-id="be787-222">既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="be787-222">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="be787-223">[コメントと末尾のコンマを許可](system-text-json-invalid-json.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="be787-223">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="be787-224">[既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。</span><span class="sxs-lookup"><span data-stu-id="be787-224">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="be787-225">ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="be787-225">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="be787-226">詳細については、「[JsonSerializerOptions の Web の規定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be787-226">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="be787-227">[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、組み込みコンバーターではサポートされていない機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="be787-227">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="be787-228">書式設定された JSON へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="be787-228">Serialize to formatted JSON</span></span>

<span data-ttu-id="be787-229">JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="be787-229">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/RoundtripToString.vb" id="SerializePrettyPrint":::

<span data-ttu-id="be787-230">シリアル化され、整形された JSON 出力の型の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be787-230">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/WeatherForecast.vb" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="be787-231">同じオプションで `JsonSerializerOptions` を繰り返し使用する場合、使用のたびに新しい `JsonSerializerOptions` インスタンスを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="be787-231">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="be787-232">すべての呼び出しで同じインスタンスを再利用します。</span><span class="sxs-lookup"><span data-stu-id="be787-232">Reuse the same instance for every call.</span></span> <span data-ttu-id="be787-233">詳細については、[JsonSerializerOptions インスタンスの再利用](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be787-233">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="be787-234">フィールドを含める</span><span class="sxs-lookup"><span data-stu-id="be787-234">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="be787-235">次の例で示されているように、シリアル化または逆シリアル化のときにフィールドを含めるには、<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> グローバル設定または [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="be787-235">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/Fields.vb" :::

<span data-ttu-id="be787-236">読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="be787-236">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="be787-237">.NET Core 3.1 では、System.Text.Json メソッドはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="be787-237">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="be787-238">この機能は、[カスタム コンバーター](system-text-json-converters-how-to.md)で提供できます。</span><span class="sxs-lookup"><span data-stu-id="be787-238">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="be787-239">HttpClient と HttpContent の拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="be787-239">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="be787-240">ネットワークからの JSON ペイロードのシリアル化と逆シリアル化は、一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="be787-240">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="be787-241">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) および [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) の拡張メソッドを使用すると、これらの操作を 1 行のコードで実行できます。</span><span class="sxs-lookup"><span data-stu-id="be787-241">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="be787-242">これらの拡張メソッドにおいては、[JsonSerializerOptions の Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="be787-242">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="be787-243">次の例では、<xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> と <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="be787-243">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/HttpClientExtensionMethods.vb" :::

<span data-ttu-id="be787-244">[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) には System.Text.Json 用の拡張メソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="be787-244">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="be787-245">`HttpClient` および `HttpContent` の拡張メソッドは、.NET Core 3.1 の System.Text.Json では使用できません。</span><span class="sxs-lookup"><span data-stu-id="be787-245">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="be787-246">関連項目</span><span class="sxs-lookup"><span data-stu-id="be787-246">See also</span></span>

* [<span data-ttu-id="be787-247">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="be787-247">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="be787-248">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="be787-248">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="be787-249">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="be787-249">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="be787-250">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="be787-250">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="be787-251">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="be787-251">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="be787-252">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="be787-252">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="be787-253">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="be787-253">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="be787-254">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="be787-254">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="be787-255">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="be787-255">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="be787-256">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="be787-256">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="be787-257">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="be787-257">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="be787-258">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="be787-258">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="be787-259">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="be787-259">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="be787-260">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="be787-260">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="be787-261">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="be787-261">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="be787-262">System.Text.Json でサポートされているコレクション型</span><span class="sxs-lookup"><span data-stu-id="be787-262">Supported collection types in System.Text.Json</span></span>](system-text-json-supported-collection-types.md)
* <span data-ttu-id="be787-263">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="be787-263">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="be787-264">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="be787-264">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
