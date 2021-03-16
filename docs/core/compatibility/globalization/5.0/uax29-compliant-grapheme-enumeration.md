---
title: 破壊的変更:StringInfo と TextElementEnumerator は現在 UAX29 に準拠する
description: .NET 5 でのグローバリゼーションの破壊的変更について学習します。この変更後、StringInfo と TextElementEnumerator により、最新バージョンの Unicode 標準に従って書記素クラスターが処理されるようになりました。
ms.date: 04/07/2020
ms.openlocfilehash: cf770e30bfadf1973bbe018cc9d2783ed6234723
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256706"
---
# <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="a8c2b-103">StringInfo と TextElementEnumerator は現在 UAX29 に準拠する</span><span class="sxs-lookup"><span data-stu-id="a8c2b-103">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="a8c2b-104">この変更の前に、<xref:System.Globalization.StringInfo?displayProperty=fullName> と <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> によって一部の書記素クラスターが正しく処理されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-104">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="a8c2b-105">一部の書記素がまとめて保持されずに、構成要素に分割されていました。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-105">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="a8c2b-106">現在は、<xref:System.Globalization.StringInfo> と <xref:System.Globalization.TextElementEnumerator> によって最新バージョンの Unicode 標準に従って書記素クラスターが処理されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-106">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="a8c2b-107">また、Visual Basic 内の文字列の文字を反転する <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> メソッドも、書記素クラスターの Unicode 標準に従うようになりました。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-107">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

## <a name="change-description"></a><span data-ttu-id="a8c2b-108">変更の説明</span><span class="sxs-lookup"><span data-stu-id="a8c2b-108">Change description</span></span>

<span data-ttu-id="a8c2b-109">[書記素](https://www.unicode.org/glossary/#grapheme)または[拡張書記素クラスター](https://www.unicode.org/glossary/#extended_grapheme_cluster)は、ユーザーが認識できる単一の文字であり、複数の Unicode コード ポイントで構成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-109">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="a8c2b-110">たとえば、タイ語の文字 "kam" (:::no-loc text="กำ":::) を含む文字列は、次の 2 つの文字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-110">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="a8c2b-111">:::no-loc text="ก"::: (= '\u0e01') タイ語の文字 KO KAI</span><span class="sxs-lookup"><span data-stu-id="a8c2b-111">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="a8c2b-112">:::no-loc text=" ำ"::: (= '\u0e33') タイ語の文字 SARA AM</span><span class="sxs-lookup"><span data-stu-id="a8c2b-112">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="a8c2b-113">ユーザーに表示されると、オペレーティング システムではこれらの 2 つの文字が結合されて、1 つの表示文字 (書記素) "kam" (:::no-loc text="กำ":::) が形成されます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-113">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="a8c2b-114">また、絵文字も同様に、結合して表示する複数の文字で構成できます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-114">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="a8c2b-115">.NET ドキュメントでは、書記素を表す際に "テキスト要素" という用語が使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-115">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="a8c2b-116"><xref:System.Globalization.StringInfo> クラスと <xref:System.Globalization.TextElementEnumerator> クラスによって文字列が検査され、含まれている書記素に関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-116">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="a8c2b-117">.NET Framework (すべてのバージョン) および .NET Core 3.x 以前では、これらの 2 つのクラスにより、いくつかの結合クラスを処理するカスタム ロジックが使用されますが、これらのクラスは [Unicode 標準](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)に完全には準拠していません。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-117">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="a8c2b-118">たとえば、<xref:System.Globalization.StringInfo> クラスと <xref:System.Globalization.TextElementEnumerator> クラスにより、1 つのタイ語の文字 "kam" がまとめて保持されずに、その構成要素に誤って分割されます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-118">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="a8c2b-119">また、これらのクラスにより、絵文字文字 "🤷🏽♀️" が 1 つの書記素クラスターとして保持されずに、4 つのクラスター (肩をすくめる人、肌色修飾子、性別修飾子、および非表示のコンバイナー) に誤って分割されます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-119">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="a8c2b-120">.NET 5 以降では、<xref:System.Globalization.StringInfo> クラスと <xref:System.Globalization.TextElementEnumerator> クラスにより、[Unicode 標準の付属書 \#29、リビジョン 35、セクション 3](https://www.unicode.org/reports/tr29/tr29-35.html) で定義されている Unicode 標準が実装されます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-120">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="a8c2b-121">具体的には、すべての結合クラスで、[拡張書記素クラスター](https://www.unicode.org/glossary/#extended_grapheme_cluster)が返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-121">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="a8c2b-122">次の C# コードについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-122">Consider the following C# code:</span></span>

```csharp
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

<span data-ttu-id="a8c2b-123">.NET Framework と .NET Core 3.x 以前のバージョンでは、書記素は分割され、コンソールの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-123">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

<span data-ttu-id="a8c2b-124">.NET 5 以降のバージョンでは、書記素はまとめて保持され、コンソールの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-124">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="a8c2b-125">また、.NET 5 以降では、Visual Basic 内の文字列の文字を反転する <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> メソッドも、書記素クラスターの Unicode 標準に従うようになりました。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-125">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="a8c2b-126">これらの変更は、.NET での Unicode と UTF-8 のさまざまな機能強化の一環です。これには、.NET Core 3.0 の <xref:System.Text.Rune?displayProperty=fullName> 型で導入された Unicode スカラー値列挙 API を補完する拡張書記素クラスター列挙 API などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-126">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a8c2b-127">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a8c2b-127">Version introduced</span></span>

<span data-ttu-id="a8c2b-128">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a8c2b-128">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a8c2b-129">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a8c2b-129">Recommended action</span></span>

<span data-ttu-id="a8c2b-130">何らかのアクションをとる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-130">You don't need to take any action.</span></span> <span data-ttu-id="a8c2b-131">アプリは、さまざまなグローバリゼーション関連のシナリオで、標準に準拠した方法で自動的に動作します。</span><span class="sxs-lookup"><span data-stu-id="a8c2b-131">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a8c2b-132">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a8c2b-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

### Category

Globalization

-->
