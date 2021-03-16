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
# <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="0a33e-103">グローバリゼーション API では Windows 上の ICU ライブラリが使用される</span><span class="sxs-lookup"><span data-stu-id="0a33e-103">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="0a33e-104">.NET 5 以降のバージョンでは、Windows 10 May 2019 Update 以降で実行されると、グローバリゼーション機能用に [International Components for Unicode (ICU)](http://site.icu-project.org/home) ライブラリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-104">.NET 5 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

## <a name="change-description"></a><span data-ttu-id="0a33e-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="0a33e-105">Change description</span></span>

<span data-ttu-id="0a33e-106">.NET Core 1.0 から 3.1 および .NET Framework 4 以降では、Windows でのグローバリゼーション機能のために[各国語サポート (NLS)](/windows/win32/intl/national-language-support) API が .NET ライブラリにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-106">In .NET Core 1.0 - 3.1 and .NET Framework 4 and later, .NET libraries use [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality on Windows.</span></span> <span data-ttu-id="0a33e-107">たとえば、NLS 関数は、文字列の比較、カルチャ情報の取得、適切なカルチャでの文字列の大文字と小文字の使い分けの実行に使用されていました。</span><span class="sxs-lookup"><span data-stu-id="0a33e-107">For example, NLS functions were used to compare strings, get culture information, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="0a33e-108">.NET 5 以降では、アプリが Windows 10 May 2019 Update 以降で実行されている場合、[ICU](http://site.icu-project.org/home) グローバリゼーション API が既定で .NET ライブラリにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-108">Starting in .NET 5, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs, by default.</span></span>

> [!NOTE]
> <span data-ttu-id="0a33e-109">Windows 10 May 2019 Update 以降のバージョンには、ICU ネイティブ ライブラリが付属しています。</span><span class="sxs-lookup"><span data-stu-id="0a33e-109">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="0a33e-110">.NET ランタイムで ICU を読み込むことができない場合は、代わりに NLS が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-110">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="0a33e-111">動作の違い</span><span class="sxs-lookup"><span data-stu-id="0a33e-111">Behavioral differences</span></span>

<span data-ttu-id="0a33e-112">グローバリゼーション機能を使用していることを認識していない場合でも、アプリでの変更に気付くことがあります。</span><span class="sxs-lookup"><span data-stu-id="0a33e-112">You might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="0a33e-113">ここでは、気付く可能性のある動作の変更をいくつか示しますが、これらの他にもあります。</span><span class="sxs-lookup"><span data-stu-id="0a33e-113">This section lists a couple of the behavioral changes you might see, but there are others too.</span></span>

### <a name="stringindexof"></a><span data-ttu-id="0a33e-114">String.IndexOf</span><span class="sxs-lookup"><span data-stu-id="0a33e-114">String.IndexOf</span></span>

<span data-ttu-id="0a33e-115">文字列内の改行文字のインデックスを調べるために <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> を呼び出す次のコードについて考えます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-115">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="0a33e-116">Windows 上の以前のバージョンの .NET では、スニペットにより `6` と出力されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-116">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="0a33e-117">Windows 19H1 以降のバージョン上の .NET 5 以降のバージョンでは、スニペットにより `-1` と出力されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-117">In .NET 5 and later versions on Windows 19H1 and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="0a33e-118">カルチャ依存検索ではなく序数検索を実行してこのコードを修正するには、<xref:System.String.IndexOf(System.String,System.StringComparison)> のオーバーロードを呼び出し、<xref:System.StringComparison.Ordinal?displayProperty=nameWithType> を引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="0a33e-118">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="0a33e-119">コード分析規則 [CA1307: 明確化のために StringComparison を指定する](../../../../fundamentals/code-analysis/quality-rules/ca1307.md)および [CA1309: 順序に基づく StringComparison を使用する](../../../../fundamentals/code-analysis/quality-rules/ca1309.md)を実行して、コード内でのこれらの呼び出しサイトを検索できます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-119">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="0a33e-120">詳細については、「[.NET 5 以降で文字列を比較するときの動作の変更](../../../../standard/base-types/string-comparison-net-5-plus.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a33e-120">For more information, see [Behavior changes when comparing strings on .NET 5+](../../../../standard/base-types/string-comparison-net-5-plus.md).</span></span>

### <a name="currency-symbol"></a><span data-ttu-id="0a33e-121">通貨記号</span><span class="sxs-lookup"><span data-stu-id="0a33e-121">Currency symbol</span></span>

<span data-ttu-id="0a33e-122">通貨書式指定子 `C` を使用して文字列の書式を設定する次のコードについて考えます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-122">Consider the following code that formats a string using the currency format specifier `C`.</span></span> <span data-ttu-id="0a33e-123">現在のスレッドのカルチャは、国ではなく言語のみを含むカルチャに設定されています。</span><span class="sxs-lookup"><span data-stu-id="0a33e-123">The current thread's culture is set to a culture that includes only the language and not the country.</span></span>

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- <span data-ttu-id="0a33e-124">Windows 上の以前のバージョンの .NET では、テキストの値は `"100,00 €"` になります。</span><span class="sxs-lookup"><span data-stu-id="0a33e-124">In previous versions of .NET on Windows, the value of text is `"100,00 €"`.</span></span>
- <span data-ttu-id="0a33e-125">Windows 19H1 以降のバージョン上の .NET 5 以降のバージョンでは、テキストの値は `"100,00 ¤"` になり、ユーロではなく国際通貨記号が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-125">In .NET 5 and later versions on Windows 19H1 and later versions, the value of text is `"100,00 ¤"`, which uses the international currency symbol instead of the euro.</span></span> <span data-ttu-id="0a33e-126">ICU では、通貨は言語ではなく国または地域のプロパティであるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="0a33e-126">In ICU, the design is that a currency is a property of a country or region, not a language.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0a33e-127">変更理由</span><span class="sxs-lookup"><span data-stu-id="0a33e-127">Reason for change</span></span>

<span data-ttu-id="0a33e-128">この変更は、サポートされているすべてのオペレーティング システムで .NET のグローバリゼーション動作を統一するために導入されました。</span><span class="sxs-lookup"><span data-stu-id="0a33e-128">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="0a33e-129">また、それにより、オペレーティング システムの組み込みライブラリに依存するのではなく、アプリケーションで独自のグローバリゼーション ライブラリをバンドルする機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-129">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the operating system's built-in libraries.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0a33e-130">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="0a33e-130">Version introduced</span></span>

<span data-ttu-id="0a33e-131">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0a33e-131">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0a33e-132">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="0a33e-132">Recommended action</span></span>

<span data-ttu-id="0a33e-133">開発者側では、何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0a33e-133">No action is required on the part of the developer.</span></span> <span data-ttu-id="0a33e-134">ただし、NLS グローバリゼーション API を引き続き使いたい場合は、[ランタイム スイッチ](../../../run-time-config/globalization.md#nls)を設定して、その動作に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="0a33e-134">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="0a33e-135">使用可能なスイッチの詳細については、「[.NET グローバリゼーションと ICU](../../../../standard/globalization-localization/globalization-icu.md)」の記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0a33e-135">For more information about the available switches, see the [.NET globalization and ICU](../../../../standard/globalization-localization/globalization-icu.md) article.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0a33e-136">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="0a33e-136">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="0a33e-137"><xref:System.Globalization?displayProperty=fullName> 名前空間のほとんどの型</span><span class="sxs-lookup"><span data-stu-id="0a33e-137">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>
- <span data-ttu-id="0a33e-138"><xref:System.Array.Sort%2A?displayProperty=fullName> (文字列の配列を並べ替えるとき)</span><span class="sxs-lookup"><span data-stu-id="0a33e-138"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting an array of strings)</span></span>
- <span data-ttu-id="0a33e-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (リストの要素が文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="0a33e-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="0a33e-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (キーが文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="0a33e-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="0a33e-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (キーが文字列のとき)</span><span class="sxs-lookup"><span data-stu-id="0a33e-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="0a33e-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (セットに文字列が含まれるとき)</span><span class="sxs-lookup"><span data-stu-id="0a33e-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

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
