---
title: '破壊的変更: グローバリゼーション API では Windows 上の ICU ライブラリが使用される'
description: .NET 5 でのグローバリゼーションに関する破壊的変更について学習します。NLS ではなく、グローバリゼーション機能に ICU ライブラリが使用されます。
ms.date: 05/19/2020
ms.openlocfilehash: 4b8580fcb3ba3c9b95357a7922e3a3062ccd3728
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256752"
---
# <a name="globalization-apis-use-icu-libraries-on-windows"></a>グローバリゼーション API では Windows 上の ICU ライブラリが使用される

.NET 5 以降のバージョンでは、Windows 10 May 2019 Update 以降で実行されると、グローバリゼーション機能用に [International Components for Unicode (ICU)](http://site.icu-project.org/home) ライブラリが使用されます。

## <a name="change-description"></a>変更の説明

.NET Core 1.0 から 3.1 および .NET Framework 4 以降では、Windows でのグローバリゼーション機能のために[各国語サポート (NLS)](/windows/win32/intl/national-language-support) API が .NET ライブラリにより使用されます。 たとえば、NLS 関数は、文字列の比較、カルチャ情報の取得、適切なカルチャでの文字列の大文字と小文字の使い分けの実行に使用されていました。

.NET 5 以降では、アプリが Windows 10 May 2019 Update 以降で実行されている場合、[ICU](http://site.icu-project.org/home) グローバリゼーション API が既定で .NET ライブラリにより使用されます。

> [!NOTE]
> Windows 10 May 2019 Update 以降のバージョンには、ICU ネイティブ ライブラリが付属しています。 .NET ランタイムで ICU を読み込むことができない場合は、代わりに NLS が使用されます。

## <a name="behavioral-differences"></a>動作の違い

グローバリゼーション機能を使用していることを認識していない場合でも、アプリでの変更に気付くことがあります。 ここでは、気付く可能性のある動作の変更をいくつか示しますが、これらの他にもあります。

### <a name="stringindexof"></a>String.IndexOf

文字列内の改行文字のインデックスを調べるために <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> を呼び出す次のコードについて考えます。

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- Windows 上の以前のバージョンの .NET では、スニペットにより `6` と出力されます。
- Windows 19H1 以降のバージョン上の .NET 5 以降のバージョンでは、スニペットにより `-1` と出力されます。

カルチャ依存検索ではなく序数検索を実行してこのコードを修正するには、<xref:System.String.IndexOf(System.String,System.StringComparison)> のオーバーロードを呼び出し、<xref:System.StringComparison.Ordinal?displayProperty=nameWithType> を引数として渡します。

コード分析規則 [CA1307: 明確化のために StringComparison を指定する](../../../../fundamentals/code-analysis/quality-rules/ca1307.md)および [CA1309: 順序に基づく StringComparison を使用する](../../../../fundamentals/code-analysis/quality-rules/ca1309.md)を実行して、コード内でのこれらの呼び出しサイトを検索できます。

詳細については、「[.NET 5 以降で文字列を比較するときの動作の変更](../../../../standard/base-types/string-comparison-net-5-plus.md)」を参照してください。

### <a name="currency-symbol"></a>通貨記号

通貨書式指定子 `C` を使用して文字列の書式を設定する次のコードについて考えます。 現在のスレッドのカルチャは、国ではなく言語のみを含むカルチャに設定されています。

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- Windows 上の以前のバージョンの .NET では、テキストの値は `"100,00 €"` になります。
- Windows 19H1 以降のバージョン上の .NET 5 以降のバージョンでは、テキストの値は `"100,00 ¤"` になり、ユーロではなく国際通貨記号が使用されます。 ICU では、通貨は言語ではなく国または地域のプロパティであるように設計されています。

## <a name="reason-for-change"></a>変更理由

この変更は、サポートされているすべてのオペレーティング システムで .NET のグローバリゼーション動作を統一するために導入されました。 また、それにより、オペレーティング システムの組み込みライブラリに依存するのではなく、アプリケーションで独自のグローバリゼーション ライブラリをバンドルする機能も提供されます。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨アクション

開発者側では、何も行う必要はありません。 ただし、NLS グローバリゼーション API を引き続き使いたい場合は、[ランタイム スイッチ](../../../run-time-config/globalization.md#nls)を設定して、その動作に戻すことができます。 使用可能なスイッチの詳細については、「[.NET グローバリゼーションと ICU](../../../../standard/globalization-localization/globalization-icu.md)」の記事をご覧ください。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <xref:System.Globalization?displayProperty=fullName> 名前空間のほとんどの型
- <xref:System.Array.Sort%2A?displayProperty=fullName> (文字列の配列を並べ替えるとき)
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (リストの要素が文字列のとき)
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (キーが文字列のとき)
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (キーが文字列のとき)
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (セットに文字列が含まれるとき)

<!--

### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

### Category

- Core .NET libraries
- Globalization

-->
