---
title: .NET 5 以降で文字列を比較するときの動作の変更
description: Windows の .NET 5 以降のバージョンでの文字列比較の動作の変更について説明します。
ms.topic: conceptual
ms.date: 12/07/2020
ms.openlocfilehash: 0db8477ce4e8c3a7167c719e2a29a32e5346a8e7
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692696"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a>.NET 5 以降で文字列を比較するときの動作の変更

.NET 5.0 で導入されたランタイム動作の変更により、グローバリゼーション API では、サポートされているすべてのプラットフォームで [ICU が既定で使用される](../../core/compatibility/globalization/5.0/icu-globalization-api.md)ようになりました。 これは、Windows で実行されるときはオペレーティング システムの各国語サポート (NLS) 機能を利用する以前のバージョンの .NET Core と .NET Framework とは異なります。 動作の変更を元に戻すことができる互換性スイッチなど、これらの変更の詳細については、「[.NET グローバリゼーションと ICU](../globalization-localization/globalization-icu.md)」を参照してください。

## <a name="reason-for-change"></a>変更理由

この変更は、サポートされているすべてのオペレーティング システムで .NET のグローバリゼーション動作を統一するために導入されました。 また、それにより、OS の組み込みライブラリに依存するのではなく、アプリケーションで独自のグローバリゼーション ライブラリをバンドルする機能も提供されます。 詳細については、[破壊的変更の通知](../../core/compatibility/globalization/5.0/icu-globalization-api.md)に関するページを参照してください。

## <a name="behavioral-differences"></a>動作の違い

<xref:System.StringComparison> 引数を受け取るオーバーロードを呼び出さずに `string.IndexOf(string)` のような関数を使用する場合は、"*序数*" 検索を実行するつもりであっても、意図せずカルチャ固有の動作に依存します。 NLS と ICU では言語比較子で実装されているロジックが異なるため、`string.IndexOf(string)` のようなメソッドの結果で、予期しない値が返されることがあります。

これは、常にグローバリゼーション機能がアクティブになっている必要がない場所であっても発生します。 たとえば、次のコードからは、現在のランタイムにより異なる結果が生成される場合があります。

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a>予期しない動作を防ぐ

このセクションでは、.NET 5.0 における予期しない動作の変更に対処するための 2 つのオプションについて説明します。

### <a name="enable-code-analyzers"></a>コード アナライザーを有効にする

[コード アナライザー](../../fundamentals/code-analysis/overview.md)を使用すると、バグがある可能性のある呼び出しサイトを検出できます。 予期せぬ動作を防ぐには、自分のプロジェクトで .NET コンパイラ プラットフォーム (Roslyn) アナライザーを有効にすることをお勧めします。 アナライザーは、序数比較子を意図していると思われる箇所で誤って言語比較子が使用されている場合、コードにフラグを設定するのに役立ちます。 これらの問題にフラグを設定するには、次の規則が役立ちます。

- [CA1307:意味を明確にするための StringComparison の指定](../../fundamentals/code-analysis/quality-rules/ca1307.md)
- [CA1309:順序を示す StringComparison を使用します](../../fundamentals/code-analysis/quality-rules/ca1309.md)
- [CA1310:正確な StringComparison の指定](../../fundamentals/code-analysis/quality-rules/ca1310.md)

これらの特定の規則は、既定では有効になっていません。 これらを有効にし、違反をビルド エラーとして表示するには、自分のプロジェクト ファイルで次のプロパティを設定します。

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
  <WarningsAsErrors>$(WarningsAsErrors);CA1307;CA1309;CA1310</WarningsAsErrors>
</PropertyGroup>
```

次のスニペットは、関連するコード アナライザーの警告またはエラーを生成するコード例を示しています。

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1310 for string; CA1307 matches on char ','
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

同様に、並べ替えられた文字列のコレクションをインスタンス化したり、既存の文字列ベースのコレクションを並べ替えたりする場合は、明示的な比較子を指定します。

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

### <a name="revert-back-to-nls-behaviors"></a>NLS の動作に戻す

Windows で実行されるときに、.NET 5 アプリケーションを古い NLS の動作に戻すには、「[.NET グローバリゼーションと ICU](../globalization-localization/globalization-icu.md)」の手順のようにします。 このアプリケーション全体の互換性スイッチは、アプリケーション レベルで設定する必要があります。 個々のライブラリについてこの動作をオプトインまたはオプトアウトすることはできません。

> [!TIP]
> コードの安全性を向上させ、既存の潜在的なバグを検出するため、[CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md)、[CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md)、および [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) のコード分析規則を有効にすることを強くお勧めします。 詳細については、「[コード アナライザーを有効にする](#enable-code-analyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

ほとんどの .NET アプリケーションでは、.NET 5.0 の変更によって予期しない動作が発生することはありません。 ただし、影響を受ける API の数と、これらの API が広範な .NET エコシステムの基礎になっているため、.NET 5.0 によって望ましくない動作が発生したり、アプリケーションに既に存在する潜在的なバグが明らかになったりする可能性があることに、注意する必要があります。

影響を受ける API は次のとおりです。

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <xref:System.Globalization.TextInfo?displayProperty=fullName> (ほとんどのメンバー)
- <xref:System.Globalization.CompareInfo?displayProperty=fullName> (ほとんどのメンバー)
- <xref:System.Array.Sort%2A?displayProperty=fullName> (文字列の配列を並べ替えるとき)
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (リストの要素が文字列のとき)
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (キーが文字列のとき)
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (キーが文字列のとき)
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (セットに文字列が含まれるとき)

> [!NOTE]
> これは、影響を受けるすべての API を網羅した一覧ではありません。

既定では、上記のすべての API において、スレッドの [現在のカルチャ](xref:System.Threading.Thread.CurrentCulture)を使用する "*言語*" 文字列の検索と比較が使用されます。 "*言語*" と "*序数*" での検索と比較の違いについては、「[序数と言語での検索と比較](#ordinal-vs-linguistic-search-and-comparison)」を参照してください。

ICU で実装されている言語文字列比較は NLS と異なるため、以前のバージョンの .NET Core または .NET Framework から .NET 5.0 にアップグレードした Windows ベースのアプリケーションで、影響を受ける API のいずれかが呼び出されている場合、API が異なる動作を示し始めることに気付く場合があります。

### <a name="exceptions"></a>例外

* 明示的な `StringComparison` または `CultureInfo` パラメーターを受け取る API の場合、そのパラメーターによって API の既定の動作がオーバーライドされます。
* 最初のパラメーターが `char` 型である `System.String` のメンバーの場合 (例: <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>)、呼び出し元によって `CurrentCulture[IgnoreCase]` または `InvariantCulture[IgnoreCase]` を指定する明示的な `StringComparison` 引数が渡されない限り、序数検索が使用されます。

各 <xref:System.String> API の既定の動作の詳細な分析については、「[既定の検索と比較の種類](#default-search-and-comparison-types)」セクションを参照してください。

## <a name="ordinal-vs-linguistic-search-and-comparison"></a>序数と言語での検索と比較

"*序数*" ("*非言語*" とも呼ばれます) による検索と比較の場合は、文字列が個別の `char` 要素に分解された後、文字単位の検索または比較が実行されます。 たとえば、文字列 `"dog"` と `"dog"` は、2 つの文字列が完全に同じ文字のシーケンスで構成されているため、`Ordinal` 比較子で "*等しい*" と比較されます。 一方、`"dog"` と `"Dog"` は、それらが完全に同じ文字のシーケンスで構成されていないため、`Ordinal` 比較子で "*等しくない*" と比較されます。 つまり、大文字 `'D'` のコード ポイント `U+0044` は、小文字 `'d'` のコード ポイント `U+0064` より前にあるので、`"dog"` は `"Dog"` より前に並べ替えられます。

`OrdinalIgnoreCase` 比較子はやはり文字単位で動作しますが、操作の実行中に大文字と小文字の違いがなくなります。 `OrdinalIgnoreCase` 比較子の下では、文字のペア `'d'` と `'D'` は、文字のペア `'á'` と `'Á'` の場合と同様に、"*等しい*" として比較されます。 しかし、アクセントが付いていない文字 `'a'` とアクセントが付いている文字 `'á'` の場合は、"*等しくない*" と比較されます。

これについてのいくつかの例を次の表に示します。

| String 1 | 文字列 2 | `Ordinal` 比較 | `OrdinalIgnoreCase` 比較 |
|---|---|---|---|
| `"dog"` | `"dog"` | equal | equal |
| `"dog"` | `"Dog"` | 等しくない | equal |
| `"resume"` | `"Resume"` | 等しくない | equal |
| `"resume"` | `"résumé"` | 等しくない | 等しくない |

Unicode の場合も、文字列に複数の異なるメモリ内表現を使用することが認められています。 たとえば、e アキュート (é) は、次の 2 つの方法で表すことができます。

* 1 つのリテラル `'é'` 文字 (`'\u00E9'` とも記述されます)。
* リテラルのアクセントなし `'e'` 文字の後に、結合アクセント修飾子文字 `'\u0301'` を付けたもの。

これは、構成要素が異なる場合でも、次の "_4 つ_" の文字列はすべて表示されるときは `"résumé"` になることを意味します。 これらの文字列には、リテラル `'é'` 文字またはリテラル非アクセント `'e'` 文字と結合アクセント修飾子 `'\u0301'` の組み合わせが使用されます。

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

序数比較子では、これらのどの文字列も相互に等しくないと比較されます。 これは、画面にレンダリングされるときはすべて同じように見えても、含まれる基の文字シーケンスが異なるためです。

`string.IndexOf(..., StringComparison.Ordinal)` 操作を実行すると、ランタイムにより完全に一致する部分文字列が検索されます。 結果は次のようになります。

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

序数検索と序数比較のルーチンは、現在のスレッドのカルチャ設定の影響を受けません。

"*言語*" の検索および比較ルーチンの場合、文字列が "*照合順序要素*" に分解されてから、これらの要素に対して検索や比較が実行されます。 文字列の文字とそれを構成する照合順序要素の間に、1:1 のマッピングが存在するとは限りません。 たとえば、長さが 2 の文字列でも、単一の照合順序要素で構成されている場合があります。 2 つの文字列を言語対応の方法で比較すると、文字列のリテラル文字が異なる場合でも、比較子により、2 つの文字列の照合順序要素のセマンティックな意味が同じかどうかが確認されます。

再び、文字列 `"résumé"` とその 4 つの異なる表現を検討します。 次の表は、各表現を照合順序要素に分割したものです。

| 文字列型 | 照合順序要素 |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

照合順序要素は、読み手が 1 つの文字または文字の塊として認識するものと緩く対応しています。 概念的には[書記素クラスター](character-encoding-introduction.md#grapheme-clusters)に似ていますが、より大きな包括的なものが含まれています。

言語比較子では、完全一致は必要ありません。 照合順序要素が、そのセマンティックの意味に基づいて代わりに比較されます。 たとえば、部分文字列 `"\u00E9"` と `"e\u0301"` は、いずれも "アキュート アクセント修飾子付きの小文字の e" を意味するものとして、言語比較子に等しく扱われます。 これにより、次のコード サンプルに示すように、`IndexOf` メソッドを使用すると、セマンティック的に等しい部分文字列 `"\u00E9"` が含まれる大きな文字列内で部分文字列 `"e\u0301"` を照合できます。

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

このため、言語比較を使用した場合、長さが異なる 2 つの文字列が等しいと見なされることがあります。 呼び出し元は、このようなシナリオで文字列の長さを扱う特殊なケースのロジックを使用しないようにする必要があります。

"*カルチャ対応*" の検索および比較ルーチンは、言語検索および比較ルーチンの特殊な形式です。 カルチャ対応の比較子の場合、照合順序要素の概念が拡張され、指定されたカルチャに固有の情報が含まれるようになります。

たとえば、[ハンガリー語アルファベット](https://en.wikipedia.org/wiki/Hungarian_alphabet)では、2 つの文字 \<dz\> が連続して出現する場合、それらは \<d\> または \<z\> とは異なるそれ自体で一意の文字と見なされます。 つまり、文字列に \<dz\> が含まれると、ハンガリー語のカルチャ対応の比較子により、それは単一の照合順序要素として扱われます。

| 文字列型 | 照合順序要素 | Remarks |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | (標準の言語比較子を使用) |
| `"endz"` | `"e" + "n" + "dz"` | (ハンガリー語のカルチャ対応比較子を使用) |

ハンガリー語のカルチャ対応比較子を使用する場合、<\dz\> と <\z\> はセマンティックの意味が異なる照合順序要素と見なされるため、文字列 `"endz"` は部分文字列 `"z"` で終わって "*いない*" ことを意味します。

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - 動作: 言語対応およびカルチャ対応の比較子は、ときどき動作の調整が行われる場合があります。 ICU と古い Windows NLS 機能はどちらも、世界的な言語の変化を考慮して更新されます。 詳細については、ブログ記事「[ロケール (カルチャ) データの変動](/archive/blogs/shawnste/locale-culture-data-churn)」を参照してください。 "*序数*" 比較子の動作は、完全にビットごとの検索と比較が実行されるため、変更されることはありません。 ただし、*OrdinalIgnoreCase* 比較子の動作は、Unicode の拡大によって含まれる文字セットが増え、既存の大文字小文字データの不備が修正されると、変更される可能性があります。
> - 使用方法: 比較子 `StringComparison.InvariantCulture` と `StringComparison.InvariantCultureIgnoreCase` は、カルチャ対応ではない言語比較子です。 つまり、これらの比較子では、é のようなアクセント付き文字には複数の可能な基になる表現があり、そのようなすべての表現を等しいと見なす必要がある、といった概念が理解されます。 しかし、非カルチャ対応の言語比較子には、上記のような \<d\> や \<z\> とは異なる \<dz\> の特殊な処理は含まれません。 また、ドイツ語の Eszett (ß) のような特殊なケースの文字もありません。

.NET には、"*インバリアント グローバリゼーション モード*" も用意されています。 このオプトイン モードを使用すると、言語検索および比較ルーチンを処理するコード パスが無効になります。 このモードでは、呼び出し元が提供する `CultureInfo` または `StringComparison` の引数に関係なく、すべての操作で *Ordinal* または *OrdinalIgnoreCase* の動作が使用されます。 詳細については、「[グローバリゼーションのランタイム構成オプション](../../core/run-time-config/globalization.md)」および「[.NET Core のグローバリゼーション インバリアント モード](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)」を参照してください。

詳細については、「[.NET での文字列の比較に関するベスト プラクティス](best-practices-strings.md)」を参照してください。

## <a name="security-implications"></a>セキュリティへの影響

影響を受ける API をアプリでフィルター処理に使用している場合、CA1307 と CA1309 のコード分析規則を有効にすることをお勧めします。これにより、序数検索の代わりに言語検索が意図せずに使用される可能性がある場所を特定することができます。 次のようなコード パターンは、セキュリティ攻撃の影響を受ける可能性があります。

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

`string.IndexOf(string)` メソッドでは既定で言語検索が使用されるため、文字列にリテラルの `'<'` または `'&'` 文字が含まれる可能性があり、`string.IndexOf(string)` ルーチンで検索部分文字列が見つからなかったことを示す `-1` が返される可能性があります。 コード分析規則 CA1307 と CA1309 フラグを使用すると、このような呼び出しサイトが識別され、潜在的な問題があることが開発者に通知されます。

## <a name="default-search-and-comparison-types"></a>既定の検索と比較の種類

次の表では、さまざまな文字列 API と文字列に似た API での既定の検索と比較の種類を示します。 呼び出し元によって明示的な `CultureInfo` または `StringComparison` パラメーターが提供された場合は、そのパラメーターが既定値より優先されます。

| API | 既定の動作 | Remarks |
|---|---|---|
| `string.Compare` | CurrentCulture | |
| `string.CompareTo` | CurrentCulture | |
| `string.Contains` | Ordinal | |
| `string.EndsWith` | Ordinal | (1 番目のパラメーターが `char` のとき) |
| `string.EndsWith` | CurrentCulture | (1 番目のパラメーターが `string` のとき) |
| `string.Equals` | Ordinal | |
| `string.GetHashCode` | Ordinal | |
| `string.IndexOf` | Ordinal | (1 番目のパラメーターが `char` のとき) |
| `string.IndexOf` | CurrentCulture | (1 番目のパラメーターが `string` のとき) |
| `string.IndexOfAny` | Ordinal | |
| `string.LastIndexOf` | Ordinal | (1 番目のパラメーターが `char` のとき) |
| `string.LastIndexOf` | CurrentCulture | (1 番目のパラメーターが `string` のとき) |
| `string.LastIndexOfAny` | Ordinal | |
| `string.Replace` | Ordinal | |
| `string.Split` | Ordinal | |
| `string.StartsWith` | Ordinal | (1 番目のパラメーターが `char` のとき) |
| `string.StartsWith` | CurrentCulture | (1 番目のパラメーターが `string` のとき) |
| `string.ToLower` | CurrentCulture | |
| `string.ToLowerInvariant` | InvariantCulture | |
| `string.ToUpper` | CurrentCulture | |
| `string.ToUpperInvariant` | InvariantCulture | |
| `string.Trim` | Ordinal | |
| `string.TrimEnd` | Ordinal | |
| `string.TrimStart` | Ordinal | |
| `string == string` | Ordinal | |
| `string != string` | Ordinal | |

`string` API とは異なり、すべての `MemoryExtensions` API で "*序数*" による検索と比較が既定で実行されますが、次の例外があります。

| API | 既定の動作 | Remarks |
|---|---|---|
| `MemoryExtensions.ToLower` | CurrentCulture | (`CultureInfo` 引数で null が渡されたとき) |
| `MemoryExtensions.ToLowerInvariant` | InvariantCulture | |
| `MemoryExtensions.ToUpper` | CurrentCulture | (`CultureInfo` 引数で null が渡されたとき) |
| `MemoryExtensions.ToUpperInvariant` | InvariantCulture | |

結果として、コードを `string` の使用から `ReadOnlySpan<char>` の使用に変換すると、動作が誤って変更される可能性があります。 たとえば次のような場合です。

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

これに対処するには、明示的な `StringComparison` パラメーターをこれらの API に渡すことをお勧めします。 コード分析規則 CA1307 と CA1309 がこれに役立つ場合があります。

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a>関連項目

- [グローバリゼーションに関する破壊的変更](../../core/compatibility/globalization.md)
- [.NET での文字列の比較に関するベスト プラクティス](best-practices-strings.md)
- [C# で文字列を比較する方法](../../csharp/how-to/compare-strings.md)
- [.NET グローバリゼーションと ICU](../globalization-localization/globalization-icu.md)
- [序数対応とカルチャ対応の文字列操作](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [.NET ソース コード分析の概要](../../fundamentals/code-analysis/overview.md)
