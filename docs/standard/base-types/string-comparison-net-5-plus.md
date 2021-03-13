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
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a><span data-ttu-id="2ea8e-103">.NET 5 以降で文字列を比較するときの動作の変更</span><span class="sxs-lookup"><span data-stu-id="2ea8e-103">Behavior changes when comparing strings on .NET 5+</span></span>

<span data-ttu-id="2ea8e-104">.NET 5.0 で導入されたランタイム動作の変更により、グローバリゼーション API では、サポートされているすべてのプラットフォームで [ICU が既定で使用される](../../core/compatibility/globalization/5.0/icu-globalization-api.md)ようになりました。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-104">.NET 5.0 introduces a runtime behavioral change where globalization APIs [now use ICU by default](../../core/compatibility/globalization/5.0/icu-globalization-api.md) across all supported platforms.</span></span> <span data-ttu-id="2ea8e-105">これは、Windows で実行されるときはオペレーティング システムの各国語サポート (NLS) 機能を利用する以前のバージョンの .NET Core と .NET Framework とは異なります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-105">This is a departure from earlier versions of .NET Core and from .NET Framework, which utilize the operating system's national language support (NLS) functionality when running on Windows.</span></span> <span data-ttu-id="2ea8e-106">動作の変更を元に戻すことができる互換性スイッチなど、これらの変更の詳細については、「[.NET グローバリゼーションと ICU](../globalization-localization/globalization-icu.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-106">For more information on these changes, including compatibility switches that can revert the behavior change, see [.NET globalization and ICU](../globalization-localization/globalization-icu.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2ea8e-107">変更理由</span><span class="sxs-lookup"><span data-stu-id="2ea8e-107">Reason for change</span></span>

<span data-ttu-id="2ea8e-108">この変更は、サポートされているすべてのオペレーティング システムで .NET のグローバリゼーション動作を統一するために導入されました。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-108">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="2ea8e-109">また、それにより、OS の組み込みライブラリに依存するのではなく、アプリケーションで独自のグローバリゼーション ライブラリをバンドルする機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-109">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the OS's built-in libraries.</span></span> <span data-ttu-id="2ea8e-110">詳細については、[破壊的変更の通知](../../core/compatibility/globalization/5.0/icu-globalization-api.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-110">For more information, see [the breaking change notification](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="2ea8e-111">動作の違い</span><span class="sxs-lookup"><span data-stu-id="2ea8e-111">Behavioral differences</span></span>

<span data-ttu-id="2ea8e-112"><xref:System.StringComparison> 引数を受け取るオーバーロードを呼び出さずに `string.IndexOf(string)` のような関数を使用する場合は、"*序数*" 検索を実行するつもりであっても、意図せずカルチャ固有の動作に依存します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-112">If you use functions like `string.IndexOf(string)` without calling the overload that takes a <xref:System.StringComparison> argument, you might intend to perform an *ordinal* search, but instead you inadvertently take a dependency on culture-specific behavior.</span></span> <span data-ttu-id="2ea8e-113">NLS と ICU では言語比較子で実装されているロジックが異なるため、`string.IndexOf(string)` のようなメソッドの結果で、予期しない値が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-113">Since NLS and ICU implement different logic in their linguistic comparers, the results of methods like `string.IndexOf(string)` can return unexpected values.</span></span>

<span data-ttu-id="2ea8e-114">これは、常にグローバリゼーション機能がアクティブになっている必要がない場所であっても発生します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-114">This can manifest itself even in places where you aren't always expecting globalization facilities to be active.</span></span> <span data-ttu-id="2ea8e-115">たとえば、次のコードからは、現在のランタイムにより異なる結果が生成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-115">For example, the following code can produce a different answer depending on the current runtime.</span></span>

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

## <a name="guard-against-unexpected-behavior"></a><span data-ttu-id="2ea8e-116">予期しない動作を防ぐ</span><span class="sxs-lookup"><span data-stu-id="2ea8e-116">Guard against unexpected behavior</span></span>

<span data-ttu-id="2ea8e-117">このセクションでは、.NET 5.0 における予期しない動作の変更に対処するための 2 つのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-117">This section provides two options for dealing with unexpected behavior changes in .NET 5.0.</span></span>

### <a name="enable-code-analyzers"></a><span data-ttu-id="2ea8e-118">コード アナライザーを有効にする</span><span class="sxs-lookup"><span data-stu-id="2ea8e-118">Enable code analyzers</span></span>

<span data-ttu-id="2ea8e-119">[コード アナライザー](../../fundamentals/code-analysis/overview.md)を使用すると、バグがある可能性のある呼び出しサイトを検出できます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-119">[Code analyzers](../../fundamentals/code-analysis/overview.md) can detect possibly buggy call sites.</span></span> <span data-ttu-id="2ea8e-120">予期せぬ動作を防ぐには、自分のプロジェクトで .NET コンパイラ プラットフォーム (Roslyn) アナライザーを有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-120">To help guard against any surprising behaviors, we recommend enabling .NET compiler platform (Roslyn) analyzers in your project.</span></span> <span data-ttu-id="2ea8e-121">アナライザーは、序数比較子を意図していると思われる箇所で誤って言語比較子が使用されている場合、コードにフラグを設定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-121">The analyzers help flag code that might inadvertently be using a linguistic comparer when an ordinal comparer was likely intended.</span></span> <span data-ttu-id="2ea8e-122">これらの問題にフラグを設定するには、次の規則が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-122">The following rules should help flag these issues:</span></span>

- [<span data-ttu-id="2ea8e-123">CA1307:意味を明確にするための StringComparison の指定</span><span class="sxs-lookup"><span data-stu-id="2ea8e-123">CA1307: Specify StringComparison for clarity</span></span>](../../fundamentals/code-analysis/quality-rules/ca1307.md)
- [<span data-ttu-id="2ea8e-124">CA1309:順序を示す StringComparison を使用します</span><span class="sxs-lookup"><span data-stu-id="2ea8e-124">CA1309: Use ordinal StringComparison</span></span>](../../fundamentals/code-analysis/quality-rules/ca1309.md)
- [<span data-ttu-id="2ea8e-125">CA1310:正確な StringComparison の指定</span><span class="sxs-lookup"><span data-stu-id="2ea8e-125">CA1310: Specify StringComparison for correctness</span></span>](../../fundamentals/code-analysis/quality-rules/ca1310.md)

<span data-ttu-id="2ea8e-126">これらの特定の規則は、既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-126">These specific rules aren't enabled by default.</span></span> <span data-ttu-id="2ea8e-127">これらを有効にし、違反をビルド エラーとして表示するには、自分のプロジェクト ファイルで次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-127">To enable them and show any violations as build errors, set the following properties in your project file:</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
  <WarningsAsErrors>$(WarningsAsErrors);CA1307;CA1309;CA1310</WarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="2ea8e-128">次のスニペットは、関連するコード アナライザーの警告またはエラーを生成するコード例を示しています。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-128">The following snippet shows examples of code that produces the relevant code analyzer warnings or errors.</span></span>

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

<span data-ttu-id="2ea8e-129">同様に、並べ替えられた文字列のコレクションをインスタンス化したり、既存の文字列ベースのコレクションを並べ替えたりする場合は、明示的な比較子を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-129">Similarly, when instantiating a sorted collection of strings or sorting an existing string-based collection, specify an explicit comparer.</span></span>

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

### <a name="revert-back-to-nls-behaviors"></a><span data-ttu-id="2ea8e-130">NLS の動作に戻す</span><span class="sxs-lookup"><span data-stu-id="2ea8e-130">Revert back to NLS behaviors</span></span>

<span data-ttu-id="2ea8e-131">Windows で実行されるときに、.NET 5 アプリケーションを古い NLS の動作に戻すには、「[.NET グローバリゼーションと ICU](../globalization-localization/globalization-icu.md)」の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-131">To revert .NET 5 applications back to older NLS behaviors when running on Windows, follow the steps in [.NET Globalization and ICU](../globalization-localization/globalization-icu.md).</span></span> <span data-ttu-id="2ea8e-132">このアプリケーション全体の互換性スイッチは、アプリケーション レベルで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-132">This application-wide compatibility switch must be set at the application level.</span></span> <span data-ttu-id="2ea8e-133">個々のライブラリについてこの動作をオプトインまたはオプトアウトすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-133">Individual libraries cannot opt-in or opt-out of this behavior.</span></span>

> [!TIP]
> <span data-ttu-id="2ea8e-134">コードの安全性を向上させ、既存の潜在的なバグを検出するため、[CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md)、[CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md)、および [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) のコード分析規則を有効にすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-134">We strongly recommend you enable the [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), and [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) code analysis rules to help improve code hygiene and discover any existing latent bugs.</span></span> <span data-ttu-id="2ea8e-135">詳細については、「[コード アナライザーを有効にする](#enable-code-analyzers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-135">For more information, see [Enable code analyzers](#enable-code-analyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2ea8e-136">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="2ea8e-136">Affected APIs</span></span>

<span data-ttu-id="2ea8e-137">ほとんどの .NET アプリケーションでは、.NET 5.0 の変更によって予期しない動作が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-137">Most .NET applications won't encounter any unexpected behaviors due to the changes in .NET 5.0.</span></span> <span data-ttu-id="2ea8e-138">ただし、影響を受ける API の数と、これらの API が広範な .NET エコシステムの基礎になっているため、.NET 5.0 によって望ましくない動作が発生したり、アプリケーションに既に存在する潜在的なバグが明らかになったりする可能性があることに、注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-138">However, due to the number of affected APIs and how foundational these APIs are to the wider .NET ecosystem, you should be aware of the potential for .NET 5.0 to introduce unwanted behaviors or to expose latent bugs that already exist in your application.</span></span>

<span data-ttu-id="2ea8e-139">影響を受ける API は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-139">The affected APIs include:</span></span>

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <span data-ttu-id="2ea8e-140"><xref:System.Globalization.TextInfo?displayProperty=fullName> (ほとんどのメンバー)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-140"><xref:System.Globalization.TextInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="2ea8e-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (ほとんどのメンバー)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="2ea8e-142"><xref:System.Array.Sort%2A?displayProperty=fullName> (文字列の配列を並べ替えるとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-142"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting arrays of strings)</span></span>
- <span data-ttu-id="2ea8e-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (リストの要素が文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="2ea8e-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (キーが文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="2ea8e-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (キーが文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="2ea8e-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (セットに文字列が含まれるとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

> [!NOTE]
> <span data-ttu-id="2ea8e-147">これは、影響を受けるすべての API を網羅した一覧ではありません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-147">This is not an exhaustive list of affected APIs.</span></span>

<span data-ttu-id="2ea8e-148">既定では、上記のすべての API において、スレッドの [現在のカルチャ](xref:System.Threading.Thread.CurrentCulture)を使用する "*言語*" 文字列の検索と比較が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-148">All of the above APIs use *linguistic* string searching and comparison using the thread's [current culture](xref:System.Threading.Thread.CurrentCulture), by default.</span></span> <span data-ttu-id="2ea8e-149">"*言語*" と "*序数*" での検索と比較の違いについては、「[序数と言語での検索と比較](#ordinal-vs-linguistic-search-and-comparison)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-149">The differences between *linguistic* and *ordinal* search and comparison are called out in the [Ordinal vs. linguistic search and comparison](#ordinal-vs-linguistic-search-and-comparison).</span></span>

<span data-ttu-id="2ea8e-150">ICU で実装されている言語文字列比較は NLS と異なるため、以前のバージョンの .NET Core または .NET Framework から .NET 5.0 にアップグレードした Windows ベースのアプリケーションで、影響を受ける API のいずれかが呼び出されている場合、API が異なる動作を示し始めることに気付く場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-150">Because ICU implements linguistic string comparisons differently from NLS, Windows-based applications that upgrade to .NET 5.0 from an earlier version of .NET Core or .NET Framework and that call one of the affected APIs may notice that the APIs begin exhibiting different behaviors.</span></span>

### <a name="exceptions"></a><span data-ttu-id="2ea8e-151">例外</span><span class="sxs-lookup"><span data-stu-id="2ea8e-151">Exceptions</span></span>

* <span data-ttu-id="2ea8e-152">明示的な `StringComparison` または `CultureInfo` パラメーターを受け取る API の場合、そのパラメーターによって API の既定の動作がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-152">If an API accepts an explicit `StringComparison` or `CultureInfo` parameter, that parameter overrides the API's default behavior.</span></span>
* <span data-ttu-id="2ea8e-153">最初のパラメーターが `char` 型である `System.String` のメンバーの場合 (例: <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>)、呼び出し元によって `CurrentCulture[IgnoreCase]` または `InvariantCulture[IgnoreCase]` を指定する明示的な `StringComparison` 引数が渡されない限り、序数検索が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-153">`System.String` members where the first parameter is of type `char` (for example, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>) use ordinal searching, unless the caller passes an explicit `StringComparison` argument that specifies `CurrentCulture[IgnoreCase]` or `InvariantCulture[IgnoreCase]`.</span></span>

<span data-ttu-id="2ea8e-154">各 <xref:System.String> API の既定の動作の詳細な分析については、「[既定の検索と比較の種類](#default-search-and-comparison-types)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-154">For a more detailed analysis of the default behavior of each <xref:System.String> API, see the [Default search and comparison types](#default-search-and-comparison-types) section.</span></span>

## <a name="ordinal-vs-linguistic-search-and-comparison"></a><span data-ttu-id="2ea8e-155">序数と言語での検索と比較</span><span class="sxs-lookup"><span data-stu-id="2ea8e-155">Ordinal vs. linguistic search and comparison</span></span>

<span data-ttu-id="2ea8e-156">"*序数*" ("*非言語*" とも呼ばれます) による検索と比較の場合は、文字列が個別の `char` 要素に分解された後、文字単位の検索または比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-156">*Ordinal* (also known as *non-linguistic*) search and comparison decomposes a string into its individual `char` elements and performs a char-by-char search or comparison.</span></span> <span data-ttu-id="2ea8e-157">たとえば、文字列 `"dog"` と `"dog"` は、2 つの文字列が完全に同じ文字のシーケンスで構成されているため、`Ordinal` 比較子で "*等しい*" と比較されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-157">For example, the strings `"dog"` and `"dog"` compare as *equal* under an `Ordinal` comparer, since the two strings consist of the exact same sequence of chars.</span></span> <span data-ttu-id="2ea8e-158">一方、`"dog"` と `"Dog"` は、それらが完全に同じ文字のシーケンスで構成されていないため、`Ordinal` 比較子で "*等しくない*" と比較されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-158">However, `"dog"` and `"Dog"` compare as *not equal* under an `Ordinal` comparer, because they don't consist of the exact same sequence of chars.</span></span> <span data-ttu-id="2ea8e-159">つまり、大文字 `'D'` のコード ポイント `U+0044` は、小文字 `'d'` のコード ポイント `U+0064` より前にあるので、`"dog"` は `"Dog"` より前に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-159">That is, uppercase `'D'`'s code point `U+0044` occurs before lowercase `'d'`'s code point `U+0064`, resulting in `"dog"` sorting before `"Dog"`.</span></span>

<span data-ttu-id="2ea8e-160">`OrdinalIgnoreCase` 比較子はやはり文字単位で動作しますが、操作の実行中に大文字と小文字の違いがなくなります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-160">An `OrdinalIgnoreCase` comparer still operates on a char-by-char basis, but it eliminates case differences while performing the operation.</span></span> <span data-ttu-id="2ea8e-161">`OrdinalIgnoreCase` 比較子の下では、文字のペア `'d'` と `'D'` は、文字のペア `'á'` と `'Á'` の場合と同様に、"*等しい*" として比較されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-161">Under an `OrdinalIgnoreCase` comparer, the char pairs `'d'` and `'D'` compare as *equal*, as do the char pairs `'á'` and `'Á'`.</span></span> <span data-ttu-id="2ea8e-162">しかし、アクセントが付いていない文字 `'a'` とアクセントが付いている文字 `'á'` の場合は、"*等しくない*" と比較されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-162">But the unaccented char `'a'` compares as *not equal* to the accented char `'á'`.</span></span>

<span data-ttu-id="2ea8e-163">これについてのいくつかの例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-163">Some examples of this are provided in the following table:</span></span>

| <span data-ttu-id="2ea8e-164">String 1</span><span class="sxs-lookup"><span data-stu-id="2ea8e-164">String 1</span></span> | <span data-ttu-id="2ea8e-165">文字列 2</span><span class="sxs-lookup"><span data-stu-id="2ea8e-165">String 2</span></span> | <span data-ttu-id="2ea8e-166">`Ordinal` 比較</span><span class="sxs-lookup"><span data-stu-id="2ea8e-166">`Ordinal` comparison</span></span> | <span data-ttu-id="2ea8e-167">`OrdinalIgnoreCase` 比較</span><span class="sxs-lookup"><span data-stu-id="2ea8e-167">`OrdinalIgnoreCase` comparison</span></span> |
|---|---|---|---|
| `"dog"` | `"dog"` | <span data-ttu-id="2ea8e-168">equal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-168">equal</span></span> | <span data-ttu-id="2ea8e-169">equal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-169">equal</span></span> |
| `"dog"` | `"Dog"` | <span data-ttu-id="2ea8e-170">等しくない</span><span class="sxs-lookup"><span data-stu-id="2ea8e-170">not equal</span></span> | <span data-ttu-id="2ea8e-171">equal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-171">equal</span></span> |
| `"resume"` | `"Resume"` | <span data-ttu-id="2ea8e-172">等しくない</span><span class="sxs-lookup"><span data-stu-id="2ea8e-172">not equal</span></span> | <span data-ttu-id="2ea8e-173">equal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-173">equal</span></span> |
| `"resume"` | `"résumé"` | <span data-ttu-id="2ea8e-174">等しくない</span><span class="sxs-lookup"><span data-stu-id="2ea8e-174">not equal</span></span> | <span data-ttu-id="2ea8e-175">等しくない</span><span class="sxs-lookup"><span data-stu-id="2ea8e-175">not equal</span></span> |

<span data-ttu-id="2ea8e-176">Unicode の場合も、文字列に複数の異なるメモリ内表現を使用することが認められています。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-176">Unicode also allows strings to have several different in-memory representations.</span></span> <span data-ttu-id="2ea8e-177">たとえば、e アキュート (é) は、次の 2 つの方法で表すことができます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-177">For example, an e-acute (é) can be represented in two possible ways:</span></span>

* <span data-ttu-id="2ea8e-178">1 つのリテラル `'é'` 文字 (`'\u00E9'` とも記述されます)。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-178">A single literal `'é'` character (also written as `'\u00E9'`).</span></span>
* <span data-ttu-id="2ea8e-179">リテラルのアクセントなし `'e'` 文字の後に、結合アクセント修飾子文字 `'\u0301'` を付けたもの。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-179">A literal unaccented `'e'` character, followed by a combining accent modifier character `'\u0301'`.</span></span>

<span data-ttu-id="2ea8e-180">これは、構成要素が異なる場合でも、次の "_4 つ_" の文字列はすべて表示されるときは `"résumé"` になることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-180">This means that the following _four_ strings all result in `"résumé"` when displayed, even though their constituent pieces are different.</span></span> <span data-ttu-id="2ea8e-181">これらの文字列には、リテラル `'é'` 文字またはリテラル非アクセント `'e'` 文字と結合アクセント修飾子 `'\u0301'` の組み合わせが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-181">The strings use a combination of literal `'é'` characters or literal unaccented `'e'` characters plus the combining accent modifier `'\u0301'`.</span></span>

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

<span data-ttu-id="2ea8e-182">序数比較子では、これらのどの文字列も相互に等しくないと比較されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-182">Under an ordinal comparer, none of these strings compare as equal to each other.</span></span> <span data-ttu-id="2ea8e-183">これは、画面にレンダリングされるときはすべて同じように見えても、含まれる基の文字シーケンスが異なるためです。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-183">This is because they all contain different underlying char sequences, even though when they're rendered to the screen, they all look the same.</span></span>

<span data-ttu-id="2ea8e-184">`string.IndexOf(..., StringComparison.Ordinal)` 操作を実行すると、ランタイムにより完全に一致する部分文字列が検索されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-184">When performing a `string.IndexOf(..., StringComparison.Ordinal)` operation, the runtime looks for an exact substring match.</span></span> <span data-ttu-id="2ea8e-185">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-185">The results are as follows.</span></span>

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

<span data-ttu-id="2ea8e-186">序数検索と序数比較のルーチンは、現在のスレッドのカルチャ設定の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-186">Ordinal search and comparison routines are never affected by the current thread's culture setting.</span></span>

<span data-ttu-id="2ea8e-187">"*言語*" の検索および比較ルーチンの場合、文字列が "*照合順序要素*" に分解されてから、これらの要素に対して検索や比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-187">*Linguistic* search and comparison routines decompose a string into *collation elements* and perform searches or comparisons on these elements.</span></span> <span data-ttu-id="2ea8e-188">文字列の文字とそれを構成する照合順序要素の間に、1:1 のマッピングが存在するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-188">There's not necessarily a 1:1 mapping between a string's characters and its constituent collation elements.</span></span> <span data-ttu-id="2ea8e-189">たとえば、長さが 2 の文字列でも、単一の照合順序要素で構成されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-189">For example, a string of length 2 may consist of only a single collation element.</span></span> <span data-ttu-id="2ea8e-190">2 つの文字列を言語対応の方法で比較すると、文字列のリテラル文字が異なる場合でも、比較子により、2 つの文字列の照合順序要素のセマンティックな意味が同じかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-190">When two strings are compared in a linguistic-aware fashion, the comparer checks whether the two strings' collation elements have the same semantic meaning, even if the string's literal characters are different.</span></span>

<span data-ttu-id="2ea8e-191">再び、文字列 `"résumé"` とその 4 つの異なる表現を検討します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-191">Consider again the string `"résumé"` and its four different representations.</span></span> <span data-ttu-id="2ea8e-192">次の表は、各表現を照合順序要素に分割したものです。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-192">The following table shows each representation broken down into its collation elements.</span></span>

| <span data-ttu-id="2ea8e-193">文字列型</span><span class="sxs-lookup"><span data-stu-id="2ea8e-193">String</span></span> | <span data-ttu-id="2ea8e-194">照合順序要素</span><span class="sxs-lookup"><span data-stu-id="2ea8e-194">As collation elements</span></span> |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

<span data-ttu-id="2ea8e-195">照合順序要素は、読み手が 1 つの文字または文字の塊として認識するものと緩く対応しています。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-195">A collation element corresponds loosely to what readers would think of as a single character or cluster of characters.</span></span> <span data-ttu-id="2ea8e-196">概念的には[書記素クラスター](character-encoding-introduction.md#grapheme-clusters)に似ていますが、より大きな包括的なものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-196">It's conceptually similar to a [grapheme cluster](character-encoding-introduction.md#grapheme-clusters) but encompasses a somewhat larger umbrella.</span></span>

<span data-ttu-id="2ea8e-197">言語比較子では、完全一致は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-197">Under a linguistic comparer, exact matches aren't necessary.</span></span> <span data-ttu-id="2ea8e-198">照合順序要素が、そのセマンティックの意味に基づいて代わりに比較されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-198">Collation elements are instead compared based on their semantic meaning.</span></span> <span data-ttu-id="2ea8e-199">たとえば、部分文字列 `"\u00E9"` と `"e\u0301"` は、いずれも "アキュート アクセント修飾子付きの小文字の e" を意味するものとして、言語比較子に等しく扱われます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-199">For example, a linguistic comparer treats the substrings `"\u00E9"` and `"e\u0301"` as equal since they both semantically mean "a lowercase e with an acute accent modifier."</span></span> <span data-ttu-id="2ea8e-200">これにより、次のコード サンプルに示すように、`IndexOf` メソッドを使用すると、セマンティック的に等しい部分文字列 `"\u00E9"` が含まれる大きな文字列内で部分文字列 `"e\u0301"` を照合できます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-200">This allows the `IndexOf` method to match the substring `"e\u0301"` within a larger string that contains the semantically equivalent substring `"\u00E9"`, as shown in the following code sample.</span></span>

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

<span data-ttu-id="2ea8e-201">このため、言語比較を使用した場合、長さが異なる 2 つの文字列が等しいと見なされることがあります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-201">As a consequence of this, two strings of different lengths may compare as equal if a linguistic comparison is used.</span></span> <span data-ttu-id="2ea8e-202">呼び出し元は、このようなシナリオで文字列の長さを扱う特殊なケースのロジックを使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-202">Callers should take care not to special-case logic that deals with string length in such scenarios.</span></span>

<span data-ttu-id="2ea8e-203">"*カルチャ対応*" の検索および比較ルーチンは、言語検索および比較ルーチンの特殊な形式です。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-203">*Culture-aware* search and comparison routines are a special form of linguistic search and comparison routines.</span></span> <span data-ttu-id="2ea8e-204">カルチャ対応の比較子の場合、照合順序要素の概念が拡張され、指定されたカルチャに固有の情報が含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-204">Under a culture-aware comparer, the concept of a collation element is extended to include information specific to the specified culture.</span></span>

<span data-ttu-id="2ea8e-205">たとえば、[ハンガリー語アルファベット](https://en.wikipedia.org/wiki/Hungarian_alphabet)では、2 つの文字 \<dz\> が連続して出現する場合、それらは \<d\> または \<z\> とは異なるそれ自体で一意の文字と見なされます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-205">For example, [in the Hungarian alphabet](https://en.wikipedia.org/wiki/Hungarian_alphabet), when the two characters \<dz\> appear back-to-back, they are considered their own unique letter distinct from either \<d\> or \<z\>.</span></span> <span data-ttu-id="2ea8e-206">つまり、文字列に \<dz\> が含まれると、ハンガリー語のカルチャ対応の比較子により、それは単一の照合順序要素として扱われます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-206">This means that when \<dz\> is seen in a string, a Hungarian culture-aware comparer treats it as a single collation element.</span></span>

| <span data-ttu-id="2ea8e-207">文字列型</span><span class="sxs-lookup"><span data-stu-id="2ea8e-207">String</span></span> | <span data-ttu-id="2ea8e-208">照合順序要素</span><span class="sxs-lookup"><span data-stu-id="2ea8e-208">As collation elements</span></span> | <span data-ttu-id="2ea8e-209">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ea8e-209">Remarks</span></span> |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | <span data-ttu-id="2ea8e-210">(標準の言語比較子を使用)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-210">(using a standard linguistic comparer)</span></span> |
| `"endz"` | `"e" + "n" + "dz"` | <span data-ttu-id="2ea8e-211">(ハンガリー語のカルチャ対応比較子を使用)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-211">(using a Hungarian culture-aware comparer)</span></span> |

<span data-ttu-id="2ea8e-212">ハンガリー語のカルチャ対応比較子を使用する場合、<\dz\> と <\z\> はセマンティックの意味が異なる照合順序要素と見なされるため、文字列 `"endz"` は部分文字列 `"z"` で終わって "*いない*" ことを意味します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-212">When using a Hungarian culture-aware comparer, this means that the string `"endz"` *does not* end with the substring `"z"`, as <\dz\> and <\z\> are considered collation elements with different semantic meaning.</span></span>

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
> - <span data-ttu-id="2ea8e-213">動作: 言語対応およびカルチャ対応の比較子は、ときどき動作の調整が行われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-213">Behavior: Linguistic and culture-aware comparers can undergo behavioral adjustments from time to time.</span></span> <span data-ttu-id="2ea8e-214">ICU と古い Windows NLS 機能はどちらも、世界的な言語の変化を考慮して更新されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-214">Both ICU and the older Windows NLS facility are updated to account for how world languages change.</span></span> <span data-ttu-id="2ea8e-215">詳細については、ブログ記事「[ロケール (カルチャ) データの変動](/archive/blogs/shawnste/locale-culture-data-churn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-215">For more information, see the blog post [Locale (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn).</span></span> <span data-ttu-id="2ea8e-216">"*序数*" 比較子の動作は、完全にビットごとの検索と比較が実行されるため、変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-216">The *Ordinal* comparer's behavior will never change since it performs exact bitwise searching and comparison.</span></span> <span data-ttu-id="2ea8e-217">ただし、*OrdinalIgnoreCase* 比較子の動作は、Unicode の拡大によって含まれる文字セットが増え、既存の大文字小文字データの不備が修正されると、変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-217">However, the *OrdinalIgnoreCase* comparer's behavior may change as Unicode grows to encompass more character sets and corrects omissions in existing casing data.</span></span>
> - <span data-ttu-id="2ea8e-218">使用方法: 比較子 `StringComparison.InvariantCulture` と `StringComparison.InvariantCultureIgnoreCase` は、カルチャ対応ではない言語比較子です。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-218">Usage: The comparers `StringComparison.InvariantCulture` and `StringComparison.InvariantCultureIgnoreCase` are linguistic comparers that are not culture-aware.</span></span> <span data-ttu-id="2ea8e-219">つまり、これらの比較子では、é のようなアクセント付き文字には複数の可能な基になる表現があり、そのようなすべての表現を等しいと見なす必要がある、といった概念が理解されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-219">That is, these comparers understand concepts such as the accented character é having multiple possible underlying representations, and that all such representations should be treated equal.</span></span> <span data-ttu-id="2ea8e-220">しかし、非カルチャ対応の言語比較子には、上記のような \<d\> や \<z\> とは異なる \<dz\> の特殊な処理は含まれません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-220">But non-culture-aware linguistic comparers won't contain special handling for \<dz\> as distinct from \<d\> or \<z\>, as shown above.</span></span> <span data-ttu-id="2ea8e-221">また、ドイツ語の Eszett (ß) のような特殊なケースの文字もありません。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-221">They also won't special-case characters like the German Eszett (ß).</span></span>

<span data-ttu-id="2ea8e-222">.NET には、"*インバリアント グローバリゼーション モード*" も用意されています。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-222">.NET also offers the *invariant globalization mode*.</span></span> <span data-ttu-id="2ea8e-223">このオプトイン モードを使用すると、言語検索および比較ルーチンを処理するコード パスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-223">This opt-in mode disables code paths that deal with linguistic search and comparison routines.</span></span> <span data-ttu-id="2ea8e-224">このモードでは、呼び出し元が提供する `CultureInfo` または `StringComparison` の引数に関係なく、すべての操作で *Ordinal* または *OrdinalIgnoreCase* の動作が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-224">In this mode, all operations use *Ordinal* or *OrdinalIgnoreCase* behaviors, regardless of what `CultureInfo` or `StringComparison` argument the caller provides.</span></span> <span data-ttu-id="2ea8e-225">詳細については、「[グローバリゼーションのランタイム構成オプション](../../core/run-time-config/globalization.md)」および「[.NET Core のグローバリゼーション インバリアント モード](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-225">For more information, see [Run-time configuration options for globalization](../../core/run-time-config/globalization.md) and [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

<span data-ttu-id="2ea8e-226">詳細については、「[.NET での文字列の比較に関するベスト プラクティス](best-practices-strings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-226">For more information, see [Best practices for comparing strings in .NET](best-practices-strings.md).</span></span>

## <a name="security-implications"></a><span data-ttu-id="2ea8e-227">セキュリティへの影響</span><span class="sxs-lookup"><span data-stu-id="2ea8e-227">Security implications</span></span>

<span data-ttu-id="2ea8e-228">影響を受ける API をアプリでフィルター処理に使用している場合、CA1307 と CA1309 のコード分析規則を有効にすることをお勧めします。これにより、序数検索の代わりに言語検索が意図せずに使用される可能性がある場所を特定することができます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-228">If your app uses an affected API for filtering, we recommend enabling the CA1307 and CA1309 code analysis rules to help locate places where a linguistic search may have inadvertently been used instead of an ordinal search.</span></span> <span data-ttu-id="2ea8e-229">次のようなコード パターンは、セキュリティ攻撃の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-229">Code patterns like the following may be susceptible to security exploits.</span></span>

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

<span data-ttu-id="2ea8e-230">`string.IndexOf(string)` メソッドでは既定で言語検索が使用されるため、文字列にリテラルの `'<'` または `'&'` 文字が含まれる可能性があり、`string.IndexOf(string)` ルーチンで検索部分文字列が見つからなかったことを示す `-1` が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-230">Because the `string.IndexOf(string)` method uses a linguistic search by default, it's possible for a string to contain a literal `'<'` or `'&'` character and for the `string.IndexOf(string)` routine to return `-1`, indicating that the search substring was not found.</span></span> <span data-ttu-id="2ea8e-231">コード分析規則 CA1307 と CA1309 フラグを使用すると、このような呼び出しサイトが識別され、潜在的な問題があることが開発者に通知されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-231">Code analysis rules CA1307 and CA1309 flag such call sites and alert the developer that there's a potential problem.</span></span>

## <a name="default-search-and-comparison-types"></a><span data-ttu-id="2ea8e-232">既定の検索と比較の種類</span><span class="sxs-lookup"><span data-stu-id="2ea8e-232">Default search and comparison types</span></span>

<span data-ttu-id="2ea8e-233">次の表では、さまざまな文字列 API と文字列に似た API での既定の検索と比較の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-233">The following table lists the default search and comparison types for various string and string-like APIs.</span></span> <span data-ttu-id="2ea8e-234">呼び出し元によって明示的な `CultureInfo` または `StringComparison` パラメーターが提供された場合は、そのパラメーターが既定値より優先されます。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-234">If the caller provides an explicit `CultureInfo` or `StringComparison` parameter, that parameter will be honored over any default.</span></span>

| <span data-ttu-id="2ea8e-235">API</span><span class="sxs-lookup"><span data-stu-id="2ea8e-235">API</span></span> | <span data-ttu-id="2ea8e-236">既定の動作</span><span class="sxs-lookup"><span data-stu-id="2ea8e-236">Default behavior</span></span> | <span data-ttu-id="2ea8e-237">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ea8e-237">Remarks</span></span> |
|---|---|---|
| `string.Compare` | <span data-ttu-id="2ea8e-238">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-238">CurrentCulture</span></span> | |
| `string.CompareTo` | <span data-ttu-id="2ea8e-239">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-239">CurrentCulture</span></span> | |
| `string.Contains` | <span data-ttu-id="2ea8e-240">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-240">Ordinal</span></span> | |
| `string.EndsWith` | <span data-ttu-id="2ea8e-241">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-241">Ordinal</span></span> | <span data-ttu-id="2ea8e-242">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-242">(when the first parameter is a `char`)</span></span> |
| `string.EndsWith` | <span data-ttu-id="2ea8e-243">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-243">CurrentCulture</span></span> | <span data-ttu-id="2ea8e-244">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-244">(when the first parameter is a `string`)</span></span> |
| `string.Equals` | <span data-ttu-id="2ea8e-245">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-245">Ordinal</span></span> | |
| `string.GetHashCode` | <span data-ttu-id="2ea8e-246">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-246">Ordinal</span></span> | |
| `string.IndexOf` | <span data-ttu-id="2ea8e-247">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-247">Ordinal</span></span> | <span data-ttu-id="2ea8e-248">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-248">(when the first parameter is a `char`)</span></span> |
| `string.IndexOf` | <span data-ttu-id="2ea8e-249">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-249">CurrentCulture</span></span> | <span data-ttu-id="2ea8e-250">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-250">(when the first parameter is a `string`)</span></span> |
| `string.IndexOfAny` | <span data-ttu-id="2ea8e-251">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-251">Ordinal</span></span> | |
| `string.LastIndexOf` | <span data-ttu-id="2ea8e-252">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-252">Ordinal</span></span> | <span data-ttu-id="2ea8e-253">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-253">(when the first parameter is a `char`)</span></span> |
| `string.LastIndexOf` | <span data-ttu-id="2ea8e-254">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-254">CurrentCulture</span></span> | <span data-ttu-id="2ea8e-255">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-255">(when the first parameter is a `string`)</span></span> |
| `string.LastIndexOfAny` | <span data-ttu-id="2ea8e-256">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-256">Ordinal</span></span> | |
| `string.Replace` | <span data-ttu-id="2ea8e-257">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-257">Ordinal</span></span> | |
| `string.Split` | <span data-ttu-id="2ea8e-258">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-258">Ordinal</span></span> | |
| `string.StartsWith` | <span data-ttu-id="2ea8e-259">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-259">Ordinal</span></span> | <span data-ttu-id="2ea8e-260">(1 番目のパラメーターが `char` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-260">(when the first parameter is a `char`)</span></span> |
| `string.StartsWith` | <span data-ttu-id="2ea8e-261">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-261">CurrentCulture</span></span> | <span data-ttu-id="2ea8e-262">(1 番目のパラメーターが `string` のとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-262">(when the first parameter is a `string`)</span></span> |
| `string.ToLower` | <span data-ttu-id="2ea8e-263">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-263">CurrentCulture</span></span> | |
| `string.ToLowerInvariant` | <span data-ttu-id="2ea8e-264">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-264">InvariantCulture</span></span> | |
| `string.ToUpper` | <span data-ttu-id="2ea8e-265">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-265">CurrentCulture</span></span> | |
| `string.ToUpperInvariant` | <span data-ttu-id="2ea8e-266">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-266">InvariantCulture</span></span> | |
| `string.Trim` | <span data-ttu-id="2ea8e-267">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-267">Ordinal</span></span> | |
| `string.TrimEnd` | <span data-ttu-id="2ea8e-268">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-268">Ordinal</span></span> | |
| `string.TrimStart` | <span data-ttu-id="2ea8e-269">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-269">Ordinal</span></span> | |
| `string == string` | <span data-ttu-id="2ea8e-270">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-270">Ordinal</span></span> | |
| `string != string` | <span data-ttu-id="2ea8e-271">Ordinal</span><span class="sxs-lookup"><span data-stu-id="2ea8e-271">Ordinal</span></span> | |

<span data-ttu-id="2ea8e-272">`string` API とは異なり、すべての `MemoryExtensions` API で "*序数*" による検索と比較が既定で実行されますが、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-272">Unlike `string` APIs, all `MemoryExtensions` APIs perform *Ordinal* searches and comparisons by default, with the following exceptions.</span></span>

| <span data-ttu-id="2ea8e-273">API</span><span class="sxs-lookup"><span data-stu-id="2ea8e-273">API</span></span> | <span data-ttu-id="2ea8e-274">既定の動作</span><span class="sxs-lookup"><span data-stu-id="2ea8e-274">Default behavior</span></span> | <span data-ttu-id="2ea8e-275">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ea8e-275">Remarks</span></span> |
|---|---|---|
| `MemoryExtensions.ToLower` | <span data-ttu-id="2ea8e-276">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-276">CurrentCulture</span></span> | <span data-ttu-id="2ea8e-277">(`CultureInfo` 引数で null が渡されたとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-277">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToLowerInvariant` | <span data-ttu-id="2ea8e-278">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-278">InvariantCulture</span></span> | |
| `MemoryExtensions.ToUpper` | <span data-ttu-id="2ea8e-279">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-279">CurrentCulture</span></span> | <span data-ttu-id="2ea8e-280">(`CultureInfo` 引数で null が渡されたとき)</span><span class="sxs-lookup"><span data-stu-id="2ea8e-280">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToUpperInvariant` | <span data-ttu-id="2ea8e-281">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="2ea8e-281">InvariantCulture</span></span> | |

<span data-ttu-id="2ea8e-282">結果として、コードを `string` の使用から `ReadOnlySpan<char>` の使用に変換すると、動作が誤って変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-282">A consequence is that when converting code from consuming `string` to consuming `ReadOnlySpan<char>`, behavioral changes may be introduced inadvertently.</span></span> <span data-ttu-id="2ea8e-283">たとえば次のような場合です。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-283">An example of this follows.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

<span data-ttu-id="2ea8e-284">これに対処するには、明示的な `StringComparison` パラメーターをこれらの API に渡すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-284">The recommended way to address this is to pass an explicit `StringComparison` parameter to these APIs.</span></span> <span data-ttu-id="2ea8e-285">コード分析規則 CA1307 と CA1309 がこれに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ea8e-285">The code analysis rules CA1307 and CA1309 can assist with this.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a><span data-ttu-id="2ea8e-286">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ea8e-286">See also</span></span>

- [<span data-ttu-id="2ea8e-287">グローバリゼーションに関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="2ea8e-287">Globalization breaking changes</span></span>](../../core/compatibility/globalization.md)
- [<span data-ttu-id="2ea8e-288">.NET での文字列の比較に関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="2ea8e-288">Best practices for comparing strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="2ea8e-289">C# で文字列を比較する方法</span><span class="sxs-lookup"><span data-stu-id="2ea8e-289">How to compare strings in C#</span></span>](../../csharp/how-to/compare-strings.md)
- [<span data-ttu-id="2ea8e-290">.NET グローバリゼーションと ICU</span><span class="sxs-lookup"><span data-stu-id="2ea8e-290">.NET globalization and ICU</span></span>](../globalization-localization/globalization-icu.md)
- [<span data-ttu-id="2ea8e-291">序数対応とカルチャ対応の文字列操作</span><span class="sxs-lookup"><span data-stu-id="2ea8e-291">Ordinal vs. culture-sensitive string operations</span></span>](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [<span data-ttu-id="2ea8e-292">.NET ソース コード分析の概要</span><span class="sxs-lookup"><span data-stu-id="2ea8e-292">Overview of .NET source code analysis</span></span>](../../fundamentals/code-analysis/overview.md)
