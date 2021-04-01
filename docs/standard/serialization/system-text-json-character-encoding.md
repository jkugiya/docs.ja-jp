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
# <a name="how-to-customize-character-encoding-with-systemtextjson"></a><span data-ttu-id="e9989-103">System.Text.Json で文字エンコードをカスタマイズする方法</span><span class="sxs-lookup"><span data-stu-id="e9989-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="e9989-104">既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="e9989-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="e9989-105">つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。</span><span class="sxs-lookup"><span data-stu-id="e9989-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="e9989-106">たとえば、次の JSON の `Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="e9989-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="e9989-107">言語文字セットのシリアル化</span><span class="sxs-lookup"><span data-stu-id="e9989-107">Serialize language character sets</span></span>

<span data-ttu-id="e9989-108">1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9989-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="LanguageSets":::

<span data-ttu-id="e9989-109">このコードでは、キリル文字やギリシャ文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="e9989-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="e9989-110">`Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="e9989-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="e9989-111">既定では、エンコーダーは <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> 範囲を使用して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e9989-111">By default, the encoder is initialized with the <xref:System.Text.Unicode.UnicodeRanges.BasicLatin> range.</span></span>

<span data-ttu-id="e9989-112">すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="e9989-112">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="e9989-113">特定の文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="e9989-113">Serialize specific characters</span></span>

<span data-ttu-id="e9989-114">別の方法として、エスケープせずに許可する個々の文字を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e9989-114">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="e9989-115">次の例では、`жарко` の最初の 2 文字のみをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="e9989-115">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="SelectedCharacters":::

<span data-ttu-id="e9989-116">上記のコードによって生成される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e9989-116">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="block-lists"></a><span data-ttu-id="e9989-117">ブロッ クリスト</span><span class="sxs-lookup"><span data-stu-id="e9989-117">Block lists</span></span>

<span data-ttu-id="e9989-118">前のセクションは、エスケープしたくないコード ポイントまたは範囲の許可リストを指定する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="e9989-118">The preceding sections show how to specify allow lists of code points or ranges that you don't want to be escaped.</span></span> <span data-ttu-id="e9989-119">ただし、許可リスト内の特定のコード ポイントをオーバーライドできるグローバルおよびエンコーダー固有のブロック リストがあります。</span><span class="sxs-lookup"><span data-stu-id="e9989-119">However, there are global and encoder-specific block lists that can override certain code points in your allow list.</span></span> <span data-ttu-id="e9989-120">ブロック リスト内のコード ポイントは、許可リストに含まれていても、常にエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="e9989-120">Code points in a block list are always escaped, even if they're included in your allow list.</span></span>

### <a name="global-block-list"></a><span data-ttu-id="e9989-121">グローバル ブロック リスト</span><span class="sxs-lookup"><span data-stu-id="e9989-121">Global block list</span></span>

<span data-ttu-id="e9989-122">グローバル ブロック リストには、プライベート用途の文字、制御文字、未定義のコード ポイント、および [Space_Separator カテゴリ](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D)などの特定の Unicode カテゴリ (`U+0020 SPACE` を除く) などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e9989-122">The global block list includes things like private-use characters, control characters, undefined code points, and certain Unicode categories, such as the [Space_Separator category](https://util.unicode.org/UnicodeJsps/list-unicodeset.jsp?a=%5B:General_Category=Space_Separator:%5D), excluding `U+0020 SPACE`.</span></span> <span data-ttu-id="e9989-123">たとえば、許可リストとして Unicode 範囲の [CJK 記号と句読点 (U+3000 から U+303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) を指定した場合でも、`U+3000 IDEOGRAPHIC SPACE` はエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="e9989-123">For example, `U+3000 IDEOGRAPHIC SPACE` is escaped even if you specify Unicode range [CJK Symbols and Punctuation (U+3000-U+303F)](xref:System.Text.Unicode.UnicodeRanges.CjkSymbolsandPunctuation) as your allow list.</span></span>

<span data-ttu-id="e9989-124">グローバル ブロック リストは、.NET Core および .NET 5 のすべてのリリースで変更された実装の詳細です。</span><span class="sxs-lookup"><span data-stu-id="e9989-124">The global block list is an implementation detail that has changed in every release of .NET Core and in .NET 5.</span></span> <span data-ttu-id="e9989-125">グローバル ブロック リストのメンバーである (またはメンバーではない) 文字に依存しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="e9989-125">Don't take a dependency on a character being a member of (or not being a member of) the global block list.</span></span>

### <a name="encoder-specific-block-lists"></a><span data-ttu-id="e9989-126">エンコーダー固有のブロック リスト</span><span class="sxs-lookup"><span data-stu-id="e9989-126">Encoder-specific block lists</span></span>

<span data-ttu-id="e9989-127">エンコーダー固有のブロックされたコード ポイントの例としては、[HTML エンコーダー](xref:System.Text.Encodings.Web.HtmlEncoder)の `'<'` と `'&'`、[JSON エンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder)の `'\'`、[URL エンコーダー](xref:System.Text.Encodings.Web.UrlEncoder)の `'%'` があります。</span><span class="sxs-lookup"><span data-stu-id="e9989-127">Examples of encoder-specific blocked code points include `'<'` and `'&'` for the [HTML encoder](xref:System.Text.Encodings.Web.HtmlEncoder), `'\'` for the [JSON encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder), and `'%'` for the [URL encoder](xref:System.Text.Encodings.Web.UrlEncoder).</span></span> <span data-ttu-id="e9989-128">たとえば、アンパサンド (`'&'`) が `BasicLatin` の範囲内にあり、すべてのエンコーダーが `BasicLatin` を使用して既定で初期化される場合でも、HTML エンコーダーではアンパサンドは常にエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="e9989-128">For example, the HTML encoder always escapes ampersands (`'&'`), even though the ampersand is in the `BasicLatin` range and all the encoders are initialized with `BasicLatin` by default.</span></span>

## <a name="serialize-all-characters"></a><span data-ttu-id="e9989-129">すべての文字のシリアル化</span><span class="sxs-lookup"><span data-stu-id="e9989-129">Serialize all characters</span></span>

<span data-ttu-id="e9989-130">エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9989-130">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/SerializeCustomEncoding.vb" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="e9989-131">既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。</span><span class="sxs-lookup"><span data-stu-id="e9989-131">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="e9989-132">`<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="e9989-132">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="e9989-133">クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。</span><span class="sxs-lookup"><span data-stu-id="e9989-133">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="e9989-134">安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="e9989-134">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="e9989-135">たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9989-135">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="e9989-136">未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="e9989-136">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9989-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9989-137">See also</span></span>

* [<span data-ttu-id="e9989-138">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="e9989-138">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e9989-139">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="e9989-139">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="e9989-140">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="e9989-140">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="e9989-141">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="e9989-141">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="e9989-142">プロパティの名前と値をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="e9989-142">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="e9989-143">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="e9989-143">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="e9989-144">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="e9989-144">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="e9989-145">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="e9989-145">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="e9989-146">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="e9989-146">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="e9989-147">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="e9989-147">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="e9989-148">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="e9989-148">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="e9989-149">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="e9989-149">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="e9989-150">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="e9989-150">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="e9989-151">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="e9989-151">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="e9989-152">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="e9989-152">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="e9989-153">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="e9989-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="e9989-154">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="e9989-154">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
