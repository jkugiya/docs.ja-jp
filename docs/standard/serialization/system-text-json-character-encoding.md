---
title: System.Text.Json で文字エンコードをカスタマイズする方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、文字エンコードをカスタマイズする方法について説明します。
ms.date: 01/22/2021
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
ms.openlocfilehash: 5788065ac127f856a66fe1c7c325fdc1f0066e78
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584448"
---
# <a name="how-to-customize-character-encoding-with-systemtextjson"></a>System.Text.Json で文字エンコードをカスタマイズする方法

既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。 つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。 たとえば、次の JSON の `Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a>言語文字セットのシリアル化

1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="LanguageSets":::

このコードでは、キリル文字やギリシャ文字はエスケープされません。 `Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

既定では、エンコーダーは <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> 範囲を使用して初期化されます。

すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。

## <a name="serialize-specific-characters"></a>特定の文字のシリアル化

別の方法として、エスケープせずに許可する個々の文字を指定することもできます。 次の例では、`жарко` の最初の 2 文字のみをシリアル化します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="SelectedCharacters":::

上記のコードによって生成される JSON の例を次に示します。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="block-lists"></a>ブロッ クリスト

前のセクションは、エスケープしたくないコード ポイントまたは範囲の許可リストを指定する方法について説明しています。 ただし、許可リスト内の特定のコード ポイントをオーバーライドできるグローバルおよびエンコーダー固有のブロック リストがあります。 ブロック リスト内のコード ポイントは、許可リストに含まれていても、常にエスケープされます。

### <a name="global-block-list"></a>グローバル ブロック リスト

グローバル ブロック リストには、プライベート用途の文字、制御文字、未定義のコード ポイント、および [Space_Separator カテゴリ](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D)などの特定の Unicode カテゴリ (`U+0020 SPACE` を除く) などが含まれます。 たとえば、許可リストとして Unicode 範囲の [CJK 記号と句読点 (U+3000 から U+303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) を指定した場合でも、`U+3000 IDEOGRAPHIC SPACE` はエスケープされます。

グローバル ブロック リストは、.NET Core および .NET 5 のすべてのリリースで変更された実装の詳細です。 グローバル ブロック リストのメンバーである (またはメンバーではない) 文字に依存しないようにしてください。

### <a name="encoder-specific-block-lists"></a>エンコーダー固有のブロック リスト

エンコーダー固有のブロックされたコード ポイントの例としては、[HTML エンコーダー](xref:System.Text.Encodings.Web.HtmlEncoder)の `'<'` と `'&'`、[JSON エンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder)の `'\'`、[URL エンコーダー](xref:System.Text.Encodings.Web.UrlEncoder)の `'%'` があります。 たとえば、アンパサンド (`'&'`) が `BasicLatin` の範囲内にあり、すべてのエンコーダーが `BasicLatin` を使用して既定で初期化される場合でも、HTML エンコーダーではアンパサンドは常にエスケープされます。

## <a name="serialize-all-characters"></a>すべての文字のシリアル化

エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="UnsafeRelaxed":::

> [!CAUTION]
> 既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。
>
> * `<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。
> * クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。
>
> 安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。 たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。 未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。

## <a name="see-also"></a>関連項目

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
* [カスタム シリアライザーと逆シリアライザーを作成する](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターの作成](system-text-json-converters-how-to.md)
* [DateTime および DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
* [System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)
