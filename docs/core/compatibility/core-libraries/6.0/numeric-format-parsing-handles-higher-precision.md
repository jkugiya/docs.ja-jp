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
# <a name="standard-numeric-format-parsing-precision"></a>標準の数値書式の解析精度

.NET で、`ToString` および `TryFormat` を使用して数値を文字列として書式設定するときに、より高い精度の値がサポートされるようになりました。

## <a name="change-description"></a>変更内容

数値を文字列として書式設定するとき、[書式文字列](../../../../standard/base-types/standard-numeric-format-strings.md)の *精度指定子* は、結果の文字列の桁数を表します。 *書式指定子* ([文字列の先頭にある文字](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)) により、精度で合計桁数、有効桁数、または小数点以下の桁数を表すことができます。

以前のバージョンの .NET では、標準の数値書式解析ロジックは 99 以下の有効桁数に制限されています。 数値型によっては、精度はさらに高くなりますが、`ToString(string format)` ではそれが正しく展開されません。 たとえば、99 より大きい有効桁数を指定すると (`32.ToString("C100")` など)、書式指定文字列は "有効桁数 100 の通貨" ではなく、[カスタム数値書式文字列](../../../../standard/base-types/custom-numeric-format-strings.md)として解釈されます。 カスタム数値書式文字列では、文字は[文字リテラル](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)として解釈されます。 また、無効な書式指定子が含まれる書式文字列は、有効桁数の値によって異なる方法で解釈されます。 `H99` では無効な書式指定子を示す <xref:System.FormatException> がスローされますが、`H100` はカスタム数値書式文字列として解釈されます。

.NET 6 以降では、.NET でサポートされる有効桁数は最大 <xref:System.Int32.MaxValue?displayProperty=nameWithType> です。 任意の桁数の書式指定子で構成される書式字列は、有効桁数を持つ標準の数値書式文字列として解釈されます。 次のいずれかまたは両方の条件に対しては、<xref:System.FormatException> がスローされます。

- 書式指定子文字は[標準書式指定子](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)ではありません。
- 有効桁数が <xref:System.Int32.MaxValue?displayProperty=nameWithType> を超えています。

この変更は、すべての数値型に影響を与える解析ロジックで実装されました。

次の表では、さまざまな書式文字列の動作変更を示します。

| [書式設定文字列] | 以前の動作 | .NET 6 以降の動作 |
| - | - | - |
| `C2` | 小数点以下 2 桁の通貨を表します | 小数点以下 2 桁の通貨を表します (*変更なし*) |
| `C100` | "C100" を出力するカスタム数値書式文字列を示します。 | 小数点以下 100 桁の通貨を表します |
| `H99` | 無効な標準書式指定子 "H" のため <xref:System.FormatException> がスローされます | 無効な標準書式指定子 "H" のため <xref:System.FormatException> がスローされます (*変更なし*) |
| `H100` | カスタム数値書式文字列を表します | 無効な標準書式指定子 "H" のため <xref:System.FormatException> がスローされます |

## <a name="version-introduced"></a>導入されたバージョン

6.0 Preview 2

## <a name="reason-for-change"></a>変更理由

この変更により、数値書式解析に対して高い有効桁数を使用したときの予期しない動作が修正されます。

## <a name="recommended-action"></a>推奨アクション

ほとんどの場合、アクションは必要なく、結果の文字列に正しい有効桁数が表示されます。

ただし、有効桁数が 99 を超える場合に書式指定子がリテラル文字として解釈される以前の動作に戻す場合は、その文字を単一引用符で囲むか、円記号でエスケープします。 たとえば、以前のバージョンの .NET では、`42.ToString("G999")` からは `G999` が返されます。 その動作を維持するには、書式文字列を `"'G'999"` または `"\\G999"` に変更します。 これは .NET Framework、.NET Core、.NET 5 以降で機能します。

次の書式文字列は、引き続きカスタム数値書式文字列として解釈されます。

- ASCII アルファベット文字以外の文字 (`$` や `è` など) で始まる。
- ASCII アルファベット文字で始まり、その後が ASCII 数字ではない (例: `A$`)。
- ASCII アルファベット文字で始まり、その後に一連の ASCII 数字があり、その後に ASCII 数字文字ではない文字がある (例: `A12A`)。

## <a name="affected-apis"></a>影響を受ける API

この変更は、すべての数値型に影響を与える解析ロジックで実装されました。

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

## <a name="see-also"></a>関連項目

- [標準の数値書式指定文字列](../../../../standard/base-types/standard-numeric-format-strings.md)
- [カスタム書式文字列内の文字リテラル](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)

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
