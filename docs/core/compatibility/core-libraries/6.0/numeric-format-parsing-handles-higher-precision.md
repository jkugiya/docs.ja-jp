---
title: '破壊的変更: 標準の数値書式の解析精度'
description: 標準の数値書式の解析でより高い有効桁数が処理される、Core .NET ライブラリでの .NET 6 の破壊的変更について説明します。
ms.date: 02/26/2021
ms.openlocfilehash: ad1555493bbc6198541365132cc421db7c01a5a2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256921"
---
# <a name="standard-numeric-format-parsing-precision"></a><span data-ttu-id="2eb7c-103">標準の数値書式の解析精度</span><span class="sxs-lookup"><span data-stu-id="2eb7c-103">Standard numeric format parsing precision</span></span>

<span data-ttu-id="2eb7c-104">.NET で、`ToString` および `TryFormat` を使用して数値を文字列として書式設定するときに、より高い精度の値がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-104">.NET now supports greater precision values when formatting numbers as strings using `ToString` and `TryFormat`.</span></span>

## <a name="change-description"></a><span data-ttu-id="2eb7c-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="2eb7c-105">Change description</span></span>

<span data-ttu-id="2eb7c-106">数値を文字列として書式設定するとき、[書式文字列](../../../../standard/base-types/standard-numeric-format-strings.md)の *精度指定子* は、結果の文字列の桁数を表します。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-106">When formatting numbers as strings, the *precision specifier* in the [format string](../../../../standard/base-types/standard-numeric-format-strings.md) represents the number of digits in the resulting string.</span></span> <span data-ttu-id="2eb7c-107">*書式指定子* ([文字列の先頭にある文字](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)) により、精度で合計桁数、有効桁数、または小数点以下の桁数を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-107">Depending on the *format specifier*, which is the [character at the beginning of the string](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers), the precision can represent the total number of digits, the number of significant digits, or the number of decimal digits.</span></span>

<span data-ttu-id="2eb7c-108">以前のバージョンの .NET では、標準の数値書式解析ロジックは 99 以下の有効桁数に制限されています。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-108">In previous .NET versions, the standard numeric format parsing logic is limited to a precision of 99 or less.</span></span> <span data-ttu-id="2eb7c-109">数値型によっては、精度はさらに高くなりますが、`ToString(string format)` ではそれが正しく展開されません。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-109">Some numeric types have more precision, but `ToString(string format)` does not expose it correctly.</span></span> <span data-ttu-id="2eb7c-110">たとえば、99 より大きい有効桁数を指定すると (`32.ToString("C100")` など)、書式指定文字列は "有効桁数 100 の通貨" ではなく、[カスタム数値書式文字列](../../../../standard/base-types/custom-numeric-format-strings.md)として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-110">If you specify a precision greater than 99, for example, `32.ToString("C100")`, the format string is interpreted as a [custom numeric format string](../../../../standard/base-types/custom-numeric-format-strings.md) instead of "currency with precision 100".</span></span> <span data-ttu-id="2eb7c-111">カスタム数値書式文字列では、文字は[文字リテラル](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-111">In custom numeric format strings, characters are interpreted as [character literals](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals).</span></span> <span data-ttu-id="2eb7c-112">また、無効な書式指定子が含まれる書式文字列は、有効桁数の値によって異なる方法で解釈されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-112">In addition, a format string that contains an invalid format specifier is interpreted differently depending on the precision value.</span></span> <span data-ttu-id="2eb7c-113">`H99` では無効な書式指定子を示す <xref:System.FormatException> がスローされますが、`H100` はカスタム数値書式文字列として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-113">`H99` throws a <xref:System.FormatException> for the invalid format specifier, while `H100` is interpreted as a custom numeric format string.</span></span>

<span data-ttu-id="2eb7c-114">.NET 6 以降では、.NET でサポートされる有効桁数は最大 <xref:System.Int32.MaxValue?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-114">Starting in .NET 6, .NET supports precision up to <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2eb7c-115">任意の桁数の書式指定子で構成される書式字列は、有効桁数を持つ標準の数値書式文字列として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-115">A format string that consists of a format specifier with any number of digits is interpreted as a standard numeric format string with precision.</span></span> <span data-ttu-id="2eb7c-116">次のいずれかまたは両方の条件に対しては、<xref:System.FormatException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-116">A <xref:System.FormatException> is thrown for either or both of the following conditions:</span></span>

- <span data-ttu-id="2eb7c-117">書式指定子文字は[標準書式指定子](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)ではありません。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-117">The format specifier character is not a [standard format specifier](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers).</span></span>
- <span data-ttu-id="2eb7c-118">有効桁数が <xref:System.Int32.MaxValue?displayProperty=nameWithType> を超えています。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-118">The precision is greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2eb7c-119">この変更は、すべての数値型に影響を与える解析ロジックで実装されました。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-119">This change was implemented in the parsing logic that affects all numeric types.</span></span>

<span data-ttu-id="2eb7c-120">次の表では、さまざまな書式文字列の動作変更を示します。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-120">The following table shows the behavior changes for various format strings.</span></span>

| <span data-ttu-id="2eb7c-121">[書式設定文字列]</span><span class="sxs-lookup"><span data-stu-id="2eb7c-121">Format string</span></span> | <span data-ttu-id="2eb7c-122">以前の動作</span><span class="sxs-lookup"><span data-stu-id="2eb7c-122">Previous behavior</span></span> | <span data-ttu-id="2eb7c-123">.NET 6 以降の動作</span><span class="sxs-lookup"><span data-stu-id="2eb7c-123">.NET 6+ behavior</span></span> |
| - | - | - |
| `C2` | <span data-ttu-id="2eb7c-124">小数点以下 2 桁の通貨を表します</span><span class="sxs-lookup"><span data-stu-id="2eb7c-124">Denotes currency with two decimal digits</span></span> | <span data-ttu-id="2eb7c-125">小数点以下 2 桁の通貨を表します (*変更なし*)</span><span class="sxs-lookup"><span data-stu-id="2eb7c-125">Denotes currency with two decimal digits (*no change*)</span></span> |
| `C100` | <span data-ttu-id="2eb7c-126">"C100" を出力するカスタム数値書式文字列を示します。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-126">Denotes custom numeric format string that prints "C100"</span></span> | <span data-ttu-id="2eb7c-127">小数点以下 100 桁の通貨を表します</span><span class="sxs-lookup"><span data-stu-id="2eb7c-127">Denotes currency with 100 decimal digits</span></span> |
| `H99` | <span data-ttu-id="2eb7c-128">無効な標準書式指定子 "H" のため <xref:System.FormatException> がスローされます</span><span class="sxs-lookup"><span data-stu-id="2eb7c-128">Throws <xref:System.FormatException> due to invalid standard format specifier "H"</span></span> | <span data-ttu-id="2eb7c-129">無効な標準書式指定子 "H" のため <xref:System.FormatException> がスローされます (*変更なし*)</span><span class="sxs-lookup"><span data-stu-id="2eb7c-129">Throws <xref:System.FormatException> due to invalid standard format specifier "H" (*no change*)</span></span> |
| `H100` | <span data-ttu-id="2eb7c-130">カスタム数値書式文字列を表します</span><span class="sxs-lookup"><span data-stu-id="2eb7c-130">Denotes custom numeric format string</span></span> | <span data-ttu-id="2eb7c-131">無効な標準書式指定子 "H" のため <xref:System.FormatException> がスローされます</span><span class="sxs-lookup"><span data-stu-id="2eb7c-131">Throws <xref:System.FormatException> due to invalid standard format specifier "H"</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="2eb7c-132">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="2eb7c-132">Version introduced</span></span>

<span data-ttu-id="2eb7c-133">6.0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="2eb7c-133">6.0 Preview 2</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2eb7c-134">変更理由</span><span class="sxs-lookup"><span data-stu-id="2eb7c-134">Reason for change</span></span>

<span data-ttu-id="2eb7c-135">この変更により、数値書式解析に対して高い有効桁数を使用したときの予期しない動作が修正されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-135">This change corrects unexpected behavior when using higher precision for numeric format parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2eb7c-136">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="2eb7c-136">Recommended action</span></span>

<span data-ttu-id="2eb7c-137">ほとんどの場合、アクションは必要なく、結果の文字列に正しい有効桁数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-137">In most cases, no action is necessary and the correct precision will be shown in the resulting strings.</span></span>

<span data-ttu-id="2eb7c-138">ただし、有効桁数が 99 を超える場合に書式指定子がリテラル文字として解釈される以前の動作に戻す場合は、その文字を単一引用符で囲むか、円記号でエスケープします。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-138">However, if you want to revert to the previous behavior where the format specifier is interpreted as a literal character when the precision is greater than 99, you can wrap that character in single quotes or escape it with a backslash.</span></span> <span data-ttu-id="2eb7c-139">たとえば、以前のバージョンの .NET では、`42.ToString("G999")` からは `G999` が返されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-139">For example, in previous .NET versions, `42.ToString("G999")` returns `G999`.</span></span> <span data-ttu-id="2eb7c-140">その動作を維持するには、書式文字列を `"'G'999"` または `"\\G999"` に変更します。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-140">To maintain that behavior, change the format string to `"'G'999"` or `"\\G999"`.</span></span> <span data-ttu-id="2eb7c-141">これは .NET Framework、.NET Core、.NET 5 以降で機能します。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-141">This will work on .NET Framework, .NET Core, and .NET 5+.</span></span>

<span data-ttu-id="2eb7c-142">次の書式文字列は、引き続きカスタム数値書式文字列として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-142">The following format strings will continue to be interpreted as custom numeric format strings:</span></span>

- <span data-ttu-id="2eb7c-143">ASCII アルファベット文字以外の文字 (`$` や `è` など) で始まる。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-143">Start with any character that is not an ASCII alphabetical character, for example, `$` or `è`.</span></span>
- <span data-ttu-id="2eb7c-144">ASCII アルファベット文字で始まり、その後が ASCII 数字ではない (例: `A$`)。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-144">Start with an ASCII alphabetical character that's not followed by an ASCII digit, for example, `A$`.</span></span>
- <span data-ttu-id="2eb7c-145">ASCII アルファベット文字で始まり、その後に一連の ASCII 数字があり、その後に ASCII 数字文字ではない文字がある (例: `A12A`)。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-145">Start with an ASCII alphabetical character, followed by an ASCII digit sequence, and then any character that is not an ASCII digit character, for example, `A12A`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2eb7c-146">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="2eb7c-146">Affected APIs</span></span>

<span data-ttu-id="2eb7c-147">この変更は、すべての数値型に影響を与える解析ロジックで実装されました。</span><span class="sxs-lookup"><span data-stu-id="2eb7c-147">This change was implemented in the parsing logic that affects all numeric types.</span></span>

- <xref:System.Numerics.BigInteger.ToString(System.String)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="2eb7c-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="2eb7c-148">See also</span></span>

- [<span data-ttu-id="2eb7c-149">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="2eb7c-149">Standard numeric format strings</span></span>](../../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="2eb7c-150">カスタム書式文字列内の文字リテラル</span><span class="sxs-lookup"><span data-stu-id="2eb7c-150">Character literals in custom format strings</span></span>](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.BigInteger.ToString(System.String)`
- `M:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)`
- `M:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int32.ToString(System.String)`
- `M:System.Int32.ToString(System.String,System.IFormatProvider)`
- `M:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt32.ToString(System.String)`
- `M:System.UInt32.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Byte.ToString(System.String)`
- `M:System.Byte.ToString(System.String,System.IFormatProvider)`
- `M:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.SByte.ToString(System.String)`
- `M:System.SByte.ToString(System.String,System.IFormatProvider)`
- `M:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int16.ToString(System.String)`
- `M:System.Int16.ToString(System.String,System.IFormatProvider)`
- `M:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt16.ToString(System.String)`
- `M:System.UInt16.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int64.ToString(System.String)`
- `M:System.Int64.ToString(System.String,System.IFormatProvider)`
- `M:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt64.ToString(System.String)`
- `M:System.UInt64.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Half.ToString(System.String)`
- `M:System.Half.ToString(System.String,System.IFormatProvider)`
- `M:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Single.ToString(System.String)`
- `M:System.Single.ToString(System.String,System.IFormatProvider)`
- `M:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Double.ToString(System.String)`
- `M:System.Double.ToString(System.String,System.IFormatProvider)`
- `M:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Decimal.ToString(System.String)`
- `M:System.Decimal.ToString(System.String,System.IFormatProvider)`
- `M:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`

-->
