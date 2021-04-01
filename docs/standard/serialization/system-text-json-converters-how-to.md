---
title: JSON シリアル化のためのカスタム コンバーターを作成する方法 - .NET
description: System.Text.Json 名前空間で提供される JSON シリアル化クラス用のカスタム コンバーターを作成する方法について説明します。
ms.date: 02/25/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 86f99e1156b8f077a7050cb6c0028a561f247df9
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206727"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>.NET で JSON シリアル化 (マーシャリング) のためのカスタム コンバーターを作成する方法

この記事では、<xref:System.Text.Json> 名前空間で提供される JSON シリアル化クラス用のカスタム コンバーターを作成する方法について説明します。 `System.Text.Json` の概要については、[.NET で JSON のシリアル化と逆シリアル化を行う方法](system-text-json-how-to.md)に関するページを参照してください。

"*コンバーター*" は、オブジェクトまたは値を JSON との間で双方向に変換するクラスです。 `System.Text.Json` 名前空間には、JavaScript のプリミティブに対応するほとんどのプリミティブ型に対して、組み込みのコンバーターがあります。 次の目的で、カスタム コンバーターを作成することができます。

* 組み込みコンバーターの既定の動作をオーバーライドするため。 たとえば、`DateTime` の値を、mm/dd/yyyy の形式で表したい場合があります。 既定では、RFC 3339 プロファイルを含め、ISO 8601-1:2019 がサポートされています。 詳細については、「[System.Text.Json での DateTime と DateTimeOffset のサポート](../datetime/system-text-json-support.md)」を参照してください。
* カスタム値型をサポートするため。 たとえば、`PhoneNumber` 構造体などです。

また、カスタム コンバーターを作成し、現在のリリースには含まれない機能で `System.Text.Json` をカスタマイズまたは拡張することもできます。 この記事ではこの後、次のシナリオについて説明します。

::: zone pivot="dotnet-5-0"

* [推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。
* [ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。
* [Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。
* [文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)。
* [ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。
* [Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。
::: zone-end

カスタム コンバーター用に作成したコードでは、新しい <xref:System.Text.Json.JsonSerializerOptions> インスタンスを使用することによってパフォーマンスが大幅に低下することに注意してください。 詳細については、[JsonSerializerOptions インスタンスの再利用](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)に関する説明を参照してください。

Visual Basic を使用してカスタム コンバーターを作成することはできませんが、C# ライブラリに実装されているコンバーターを呼び出すことができます。 詳細については、「[Visual Basic のサポート](system-text-json-how-to.md#visual-basic-support)」をご覧ください。

## <a name="custom-converter-patterns"></a>カスタム コンバーターのパターン

カスタム コンバーターの作成には、基本パターンとファクトリ パターンという 2 つのパターンがあります。 ファクトリ パターンは、`Enum` 型またはオープン ジェネリックを処理するコンバーター用です。 基本パターンは、非ジェネリック型およびクローズ ジェネリック型用です。  たとえば、次のような型のコンバーターには、ファクトリ パターンが必要です。

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

基本パターンで処理できる型の例としては、次のようなものがあります。

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

基本パターンでは、1 つの型を処理できるクラスが作成されます。 ファクトリ パターンによって作成されるクラスの場合は、実行時に必要な特定の型が決定されて、適切なコンバーターが動的に作成されます。

## <a name="sample-basic-converter"></a>基本コンバーターのサンプル

次のサンプルは、既存のデータ型に対する既定のシリアル化をオーバーライドするコンバーターです。 そのコンバーターでは、`DateTimeOffset` のプロパティに対して mm/dd/yyyy の形式が使用されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a>ファクトリ パターン コンバーターのサンプル

次のコードでは、`Dictionary<Enum,TValue>` で動作するカスタム コンバーターを示します。 そのコードは、1 番目のジェネリック型パラメーターが `Enum` で、2 番目がオープンであるため、ファクトリ パターンに従います。 `CanConvert` メソッドでは、2 つのジェネリック パラメーターを持つ `Dictionary` に対してのみ `true` が返されます。最初のパラメーターは `Enum` 型です。 内部のコンバーターでは、実行時に `TValue` に対して提供される任意の型を処理するために、既存のコンバーターが取得されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

上記のコードは、後の「[文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)」で示されているものと同じです。

## <a name="steps-to-follow-the-basic-pattern"></a>基本パターンに従うための手順

次の手順では、基本パターンに従ってコンバーターを作成する方法について説明します。

* <xref:System.Text.Json.Serialization.JsonConverter%601> から派生するクラスを作成します。`T` は、シリアル化および逆シリアル化される型です。
* 受信した JSON を逆シリアル化して `T` 型に変換するように、`Read` メソッドをオーバーライドします。 JSON を読み取るには、メソッドに渡される <xref:System.Text.Json.Utf8JsonReader> を使用します。 シリアライザーによって現在の JSON スコープのすべてのデータが渡されるため、部分的なデータの処理について心配する必要はありません。 したがって、<xref:System.Text.Json.Utf8JsonReader.Skip%2A> または <xref:System.Text.Json.Utf8JsonReader.TrySkip%2A> を呼び出したり、<xref:System.Text.Json.Utf8JsonReader.Read%2A> が `true` を返すことを検証したりする必要はありません。
* 受信した `T` 型のオブジェクトをシリアル化するように、`Write` メソッドをオーバーライドします。 JSON を書き込むには、メソッドに渡される <xref:System.Text.Json.Utf8JsonWriter> を使用します。
* `CanConvert` メソッドは、必要な場合にのみオーバーライドします。 変換する型が `T` 型である場合、既定の実装では `true` が返されます。 したがって、`T` 型だけをサポートするコンバーターでは、このメソッドをオーバーライドする必要はありません。 このメソッドをオーバーライドする必要があるコンバーターの例については、後の「[ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)」を参照してください。

カスタム コンバーターを作成するための参考の実装として、[組み込みコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/)を参照できます。

## <a name="steps-to-follow-the-factory-pattern"></a>ファクトリ パターンに従うための手順

次の手順では、ファクトリ パターンに従ってコンバーターを作成する方法について説明します。

* <xref:System.Text.Json.Serialization.JsonConverterFactory> から派生するクラスを作成します。
* 変換する型がコンバーターで処理できる型である場合は true を返すように、`CanConvert` メソッドをオーバーライドします。 たとえば、コンバーターが `List<T>` 用の場合は、`List<int>`、`List<string>`、`List<DateTime>` だけを処理できます。
* 実行時に提供される変換対象の型を処理するコンバーター クラスのインスタンスを返すように、`CreateConverter` メソッドをオーバーライドします。
* `CreateConverter` メソッドによってインスタンス化されるコンバーター クラスを作成します。

オブジェクトと文字列を双方向に変換するコードは、すべての型に対して同じではないため、オープン ジェネリックにはファクトリ パターンが必要です。 オープン ジェネリック型 (`List<T>` など) 用のコンバーターでは、背後にあるクローズ ジェネリック型 (`List<DateTime>` など) 用のコンバーターを作成する必要があります。 コンバーターで処理できる各クローズ ジェネリック型を処理するためのにコードを記述する必要があります。

`Enum` 型はオープン ジェネリック型に似ています。`Enum` 用のコンバーターでは、背後にある特定の `Enum` (`WeekdaysEnum` など) に対するコンバーターを作成する必要があります。

## <a name="error-handling"></a>エラー処理

シリアライザーは、<xref:System.Text.Json.JsonException> および <xref:System.NotSupportedException> の例外の種類を特別に処理します。

### <a name="jsonexception"></a>JsonException

メッセージなしで `JsonException` をスローする場合、シリアライザーがそのエラーの原因となった JSON の部分へのパスを含むメッセージを作成します。 たとえば、`throw new JsonException()` というステートメントでは、次の例のようなエラー メッセージが生成されます。

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

メッセージを指定した場合 (たとえば `throw new JsonException("Error occurred")` でも、シリアライザーは <xref:System.Text.Json.JsonException.Path>、<xref:System.Text.Json.JsonException.LineNumber>、および <xref:System.Text.Json.JsonException.BytePositionInLine> プロパティを設定します。

### <a name="notsupportedexception"></a>NotSupportedException

`NotSupportedException` をスローした場合は、メッセージには常にパス情報が含まれます。 メッセージを指定すると、そのメッセージにパス情報が追加されます。 たとえば、`throw new NotSupportedException("Error occurred.")` というステートメントでは、次の例のようなエラー メッセージが生成されます。

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a>どのようなときにどのような種類の例外をスローするか

JSON ペイロードに、逆シリアル化される型に無効なトークンが含まれている場合は `JsonException` をスローします。

特定の型を許可しない場合は、`NotSupportedException` をスローします。 この例外は、サポートされていない型にシリアライザーが自動的にスローします。 たとえば、セキュリティ上の理由で `System.Type` はサポートされていないため、これを逆シリアル化しようとすると、`NotSupportedException` になります。

必要に応じて他の例外をスローすることもできますが、それらには JSON パス情報は自動的に含まれません。

## <a name="register-a-custom-converter"></a>カスタム コンバーターを登録する

"*カスタム コンバーター*" を登録して、`Serialize` メソッドと `Deserialize` メソッドでそれが使用されるようにします。 次のいずれかの方法を使用します。

* コンバーター クラスのインスタンスを <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> コレクションに追加します。
* カスタム コンバーターを必要とするプロパティに、[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 属性を適用します。
* カスタム値型を表すクラスまたは構造体に、[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 属性を適用します。

## <a name="registration-sample---converters-collection"></a>登録の例 - Converters コレクション

[DateTimeOffsetJsonConverter](#sample-basic-converter) を <xref:System.DateTimeOffset> 型のプロパティの既定値にする例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

次の型のインスタンスをシリアル化するとします。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

カスタム コンバーターが使用されたことを示す JSON 出力の例を次に示します。

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

次のコードでは、同じ方法を使用し、カスタム `DateTimeOffset` コンバーターを使用して逆シリアル化します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a>登録の例 - [JsonConverter] プロパティ

次のコードでは、`Date` プロパティのカスタム コンバーターを選択します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

`WeatherForecastWithConverterAttribute` をシリアル化するコードでは、`JsonSerializeOptions.Converters` を使用する必要はありません。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

逆シリアル化するコードでも、`Converters` を使用する必要はありません。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a>登録の例 - 型での [JsonConverter]

構造体を作成し、それに `[JsonConverter]` 属性を適用するコードを次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

上記の構造体のカスタム コンバーターは次のようになります。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

構造体の `[JsonConvert]` 属性では、`Temperature` 型のプロパティに対する既定値としてカスタム コンバーターが登録されます。 次の型の `TemperatureCelsius` プロパティでは、シリアル化または逆シリアル化のときに、コンバーターが自動的に使用されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a>コンバーターの登録の優先順位

シリアル化または逆シリアル化のとき、コンバーターは各 JSON 要素に対して次の順序 (優先度が高い順) で選択されます。

* `[JsonConverter]` がプロパティに適用されます。
* `Converters` コレクションにコンバーターが追加されます。
* `[JsonConverter]` がカスタム値型または POCO に適用されます。

1 つの型に対して複数のカスタム コンバーターが `Converters` コレクションに登録されている場合は、`CanConvert` に対して true を返す最初のコンバーターが使用されます。

適用可能なカスタム コンバーターが登録されていない場合にのみ、組み込みコンバーターが選択されます。

## <a name="converter-samples-for-common-scenarios"></a>一般的なシナリオでのコンバーターの例

以下のセクションでは、組み込み機能では処理されない一般的なシナリオに対処するコンバーターの例を示します。

::: zone pivot="dotnet-5-0"

* [推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。
* [ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。
* [Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [推論された型をオブジェクトのプロパティに逆シリアル化する](#deserialize-inferred-types-to-object-properties)。
* [文字列以外のキーでディクショナリをサポートする](#support-dictionary-with-non-string-key)。
* [ポリモーフィックな逆シリアル化をサポートする](#support-polymorphic-deserialization)。
* [Stack\<T> のラウンドトリップをサポートする](#support-round-trip-for-stackt)。
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a>推論された型をオブジェクトのプロパティに逆シリアル化する

`object` 型のプロパティに逆シリアル化すると、`JsonElement` オブジェクトが作成されます。 その理由は、逆シリアライザーでは、作成する CLR 型がわからず、推測が試みられないためです。 たとえば、JSON プロパティが "true" である場合、逆シリアライザーでは値が `Boolean` であることは推定されません。また、要素が "01/01/2019" である場合、逆シリアライザーではそれが `DateTime` であることは推定されません。

型の推定は不正確になる可能性があります。 逆シリアライザーで、小数点を含まない JSON の数値が `long` と解析された場合、値がもともと `ulong` または `BigInteger` としてシリアル化されていたとすると、範囲外の問題が発生する可能性があります。 数値がもともと `decimal` としてシリアル化されていた場合、小数点を含む数値が `double` と解析されると、精度が失われる可能性があります。

次のコードでは、型の推定が必要なシナリオでの、`object` プロパティに対するカスタム コンバーターを示します。 次のような変換が行われます。

* `true` と `false` は `Boolean` に
* 小数点を含まない数値は `long` に
* 小数点を含む数値は `double` に
* 日付は `DateTime` に
* 文字列は `string` に
* それ以外はすべて `JsonElement` に

::: zone pivot="dotnet-5-0"

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterInferredTypesToObject.cs":::

この例は、コンバーター コードと、`object` プロパティを持つ `WeatherForecast` クラスを示しています。 `Main` メソッドは、最初はコンバーターを使用せずに、次にコンバーターを使用して、JSON 文字列を `WeatherForecast` インスタンスに逆シリアル化します。 コンソール出力には、コンバーターを使用しない場合、`Date` プロパティのランタイム型は `JsonElement` になり、コンバーターを使用した場合のランタイム型は `DateTime` になることが示されています。

`System.Text.Json.Serialization` 名前空間の[単体テスト フォルダー](https://github.com/dotnet/runtime/tree/c72b54243ade2e1118ab24476220a2eba6057466/src/libraries/System.Text.Json/tests/Serialization/)には、`object` プロパティへの逆シリアル化を処理するカスタム コンバーターの例がさらにあります。

:::zone-end

::: zone pivot="dotnet-core-3-1"

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

次のコードではコンバーターが登録されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

`object` プロパティを含む型の例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

次の逆シリアル化を行う JSON の例には、`DateTime`、`long`、`string` として逆シリアル化される値が含まれています。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

カスタム コンバーターを使用しないと、逆シリアル化によって各プロパティに `JsonElement` が挿入されます。

`System.Text.Json.Serialization` 名前空間の[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、`object` プロパティへの逆シリアル化を処理するカスタム コンバーターの例がさらにあります。

:::zone-end

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a>文字列以外のキーでディクショナリをサポートする

ディクショナリ コレクションに対する組み込みのサポートは `Dictionary<string, TValue>` 用です。 つまり、キーは文字列である必要があります。 キーが整数または他の型であるディクショナリをサポートするには、カスタム コンバーターが必要です。

次のコードでは、`Dictionary<Enum,TValue>` で動作するカスタム コンバーターを示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

次のコードではコンバーターが登録されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

このコンバーターでは、次の `Enum` を使用する次のクラスの `TemperatureRanges` プロパティをシリアル化および逆シリアル化できます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

シリアル化からの JSON 出力は、次の例のようになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

`System.Text.Json.Serialization` 名前空間の[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、文字列以外のキーのディクショナリを処理するカスタム コンバーターの例がさらにあります。
::: zone-end

### <a name="support-polymorphic-deserialization"></a>ポリモーフィックな逆シリアル化をサポートする

組み込み機能では、[ポリモーフィックなシリアル化](system-text-json-polymorphism.md)は限られた範囲で提供されていますが、逆シリアル化はまったくサポートされていません。 逆シリアル化を行うには、カスタム コンバーターが必要です。

たとえば、抽象基底クラス `Person` と、派生クラス `Employee` および `Customer` があるとします。 ポリモーフィックな逆シリアル化とは、デザイン時に逆シリアル化ターゲットとして `Person` を指定すると、実行時に JSON 内の `Customer` オブジェクトと `Employee` オブジェクトが正しく逆シリアル化されることを意味します。 逆シリアル化の間に、JSON で必要な型を識別する手掛かりを見つける必要があります。 使用できる手掛かりの種類は、シナリオによって異なります。 たとえば、識別子プロパティを使用できる場合や、特定のプロパティの有無に依存しなければならない場合があります。 `System.Text.Json` の現在のリリースでは、ポリモーフィックな逆シリアル化のシナリオを処理する方法を指定する属性が提供されていないため、カスタム コンバーターが必要になります。

次のコードでは、基底クラス、2 つの派生クラス、およびそれらのカスタム コンバーターを示します。 コンバーターでは、識別子プロパティを使用して、ポリモーフィックな逆シリアル化を行います。 型の識別子はクラス定義には含まれていませんが、シリアル化の間に作成され、逆シリアル化の間に読み取られます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

次のコードではコンバーターが登録されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

コンバーターでは、次のように、同じコンバーターを使用してシリアル化することによって作成された JSON を逆シリアル化できます。

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

前の例のコンバーターのコードでは、各プロパティの読み取りと書き込みを手動で行います。 別の方法として、`Deserialize` または `Serialize` を呼び出すことにより、一部の作業を行うことができます。 例としては、[こちらの StackOverflow の投稿](https://stackoverflow.com/a/59744873/12509023)を参照してください。

### <a name="support-round-trip-for-stackt"></a>Stack\<T> のラウンド トリップをサポートする

JSON 文字列を <xref:System.Collections.Generic.Stack%601> オブジェクトに逆シリアル化した後、そのオブジェクトをシリアル化した場合、スタックの内容は逆の順序になります。 この動作は、次の型とインターフェイス、およびそれらから派生するユーザー定義型に適用されます。

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

スタックの元の順序を維持するシリアル化と逆シリアル化をサポートするには、カスタム コンバーターが必要です。

次のコードでは、`Stack<T>` オブジェクトとの間でのラウンドトリップを可能にするカスタム コンバーターを示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

次のコードではコンバーターが登録されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a>null 値を処理する

既定では、null 値はシリアライザーにより次のように処理されます。

* 参照型と <xref:System.Nullable%601> 型の場合:

  * シリアル化のときにカスタム コンバーターに `null` は渡されません。
  * 逆シリアル化のときにカスタム コンバーターに `JsonTokenType.Null` は渡されません。
  * 逆シリアル化では `null` インスタンスが返されます。
  * シリアル化ではライターを使用して `null` が直接書き込まれます。

* null 非許容値型の場合:

  * 逆シリアル化のときにカスタム コンバーターに `JsonTokenType.Null` が渡されます。 (カスタム コンバーターが使用できない場合は、その型の内部コンバーターによって `JsonException` 例外がスローされます)。

この null 処理動作は、主に、コンバーターの余分な呼び出しをスキップすることでパフォーマンスを最適化するためのものです。 また、すべての `Read` および `Write` メソッドのオーバーライドの開始時に、null 許容型のコンバーターで `null` のチェックを強制的に行うことが回避されます。

::: zone pivot="dotnet-5-0"
カスタム コンバーターで参照型または値型の `null` を処理できるようにするには、次の例で示すように、<xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> をオーバーライドして `true` を返します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="18":::
::: zone-end

## <a name="preserve-references"></a>参照を保持する

::: zone pivot="dotnet-5-0"

既定では、参照データは <xref:System.Text.Json.JsonSerializer.Serialize%2A> または <xref:System.Text.Json.JsonSerializer.Deserialize%2A> への呼び出しごとにキャッシュされます。 ある `Serialize`/`Deserialize` 呼び出しから別の呼び出しへの参照を保持するには、`Serialize`/`Deserialize` の呼び出しサイトで <xref:System.Text.Json.Serialization.ReferenceResolver> インスタンスをルート化します。 このスクリプトの例を次のコードに示します。

* `Company` 型のカスタム コンバーターを記述する。
* `Employee` である `Supervisor` プロパティを手動でシリアル化せずに済むようにしたい。 これをシリアライザーに委任し、既に保存されている参照も保持したい。

`Employee` と `Company` のクラスを次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="EmployeeAndCompany":::

コンバーターは次のようになります。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="CompanyConverter":::

<xref:System.Text.Json.Serialization.ReferenceResolver> から派生するクラスは、参照をディクショナリに格納します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="MyReferenceResolver":::

<xref:System.Text.Json.Serialization.ReferenceHandler> から派生するクラスは、`MyReferenceResolver` のインスタンスを保持し、必要な場合にのみ新しいインスタンスを作成します (この例では `Reset` という名前のメソッド)。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="MyReferenceHandler":::

このサンプル コードは、シリアライザーを呼び出すときに、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> プロパティが `MyReferenceHandler` のインスタンスに設定されている <xref:System.Text.Json.JsonSerializerOptions> インスタンスを使用します。 このパターンに従う場合は、シリアル化が終了したときに必ず `ReferenceResolver` ディクショナリをリセットして、継続的に拡大しないようにしてください。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterPreserveReferences.cs" id="CallSerializer" highlight = "4-5,12":::

前の例ではシリアル化のみが行われますが、逆シリアル化にも同様のアプローチを採用できます。

::: zone-end
::: zone pivot="dotnet-core-3-1"

参照を保持する方法の詳細については、[このページの .NET 5.0 バージョン](system-text-json-converters-how-to.md?pivots=dotnet-5-0#preserve-references)を参照してください。

::: zone-end

## <a name="other-custom-converter-samples"></a>他のカスタム コンバーターのサンプル

[Newtonsoft.Json から System.Text.Json への移行](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事には、カスタム コンバーターの他のサンプルが含まれています。

`System.Text.Json.Serialization` のソース コードの[単体テスト フォルダー](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)には、次のような他のカスタム コンバーターのサンプルが含まれています。

* [逆シリアル化時に null を 0 に変換する Int32 コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [逆シリアル化時に文字列値と数値の両方に対応できる Int32 コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [Enum コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [外部データを受け入れる List\<T> コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [コンマ区切りの数値リストを処理する Long[] コンバーター](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

既存の組み込みコンバーターの動作を変更するコンバーターを作成する必要がある場合は、[既存のコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)を入手し、それを基にしてカスタマイズを始めることができ ます。

## <a name="additional-resources"></a>その他の技術情報

* [組み込みコンバーターのソース コード](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [System.Text.Json の概要](system-text-json-overview.md)
* [JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)
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
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
