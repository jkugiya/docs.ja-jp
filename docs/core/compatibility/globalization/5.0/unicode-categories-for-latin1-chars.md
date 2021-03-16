---
title: '破壊的変更: 一部の Latin-1 文字に対して変更された Unicode カテゴリ'
description: .NET 5 でのグローバリゼーションに関する破壊的変更について学習します。Char メソッドで、Latin-1 範囲の文字に対して正しい Unicode カテゴリが返されるようになりました。
ms.date: 04/07/2020
ms.openlocfilehash: 03355c488d2bdae78f989e647c9b5b7913d73649
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256674"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="94ea6-103">一部の Latin-1 文字に対して変更された Unicode カテゴリ</span><span class="sxs-lookup"><span data-stu-id="94ea6-103">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="94ea6-104"><xref:System.Char> メソッドで、Latin-1 範囲の文字に対して正しい Unicode カテゴリが返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="94ea6-104"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="94ea6-105">そのカテゴリは、Unicode 標準のカテゴリと一致します。</span><span class="sxs-lookup"><span data-stu-id="94ea6-105">The category matches that of the Unicode standard.</span></span>

## <a name="change-description"></a><span data-ttu-id="94ea6-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="94ea6-106">Change description</span></span>

<span data-ttu-id="94ea6-107">以前のバージョンの .NET の <xref:System.Char> メソッドでは、Latin-1 範囲の文字に対して Unicode カテゴリの固定リストが使用されていました。</span><span class="sxs-lookup"><span data-stu-id="94ea6-107">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="94ea6-108">ただし、それらの API が実装された後に、Unicode 標準でこれらの文字の一部のカテゴリが変更されたため、不一致が発生していました。</span><span class="sxs-lookup"><span data-stu-id="94ea6-108">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="94ea6-109">また、<xref:System.Char> と、Unicode 標準に準拠する <xref:System.Globalization.CharUnicodeInfo> API の間でも一致していませんでした。</span><span class="sxs-lookup"><span data-stu-id="94ea6-109">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="94ea6-110">.NET 5 以降のバージョンの <xref:System.Char> メソッドでは、すべての文字について Unicode 標準に一致する Unicode カテゴリが使用され、返されます。</span><span class="sxs-lookup"><span data-stu-id="94ea6-110">In .NET 5 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="94ea6-111">次の表では、.NET 5.0 で Unicode カテゴリが変更された文字を示します。</span><span class="sxs-lookup"><span data-stu-id="94ea6-111">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="94ea6-112">文字</span><span class="sxs-lookup"><span data-stu-id="94ea6-112">Character</span></span>    | <span data-ttu-id="94ea6-113">Unicode カテゴリ</span><span class="sxs-lookup"><span data-stu-id="94ea6-113">Unicode category</span></span><br><span data-ttu-id="94ea6-114">以前の .NET バージョンの場合</span><span class="sxs-lookup"><span data-stu-id="94ea6-114">in previous .NET versions</span></span> | <span data-ttu-id="94ea6-115">Unicode カテゴリ</span><span class="sxs-lookup"><span data-stu-id="94ea6-115">Unicode category</span></span><br><span data-ttu-id="94ea6-116">.NET 5 以降のバージョンの場合</span><span class="sxs-lookup"><span data-stu-id="94ea6-116">in .NET 5 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="94ea6-117">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="94ea6-117">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="94ea6-118">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="94ea6-118">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="94ea6-119">SHY (\u00ad)</span><span class="sxs-lookup"><span data-stu-id="94ea6-119">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="94ea6-120">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="94ea6-120">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="94ea6-121">º (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="94ea6-121">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a><span data-ttu-id="94ea6-122">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="94ea6-122">Version introduced</span></span>

<span data-ttu-id="94ea6-123">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="94ea6-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="94ea6-124">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="94ea6-124">Recommended action</span></span>

<span data-ttu-id="94ea6-125"><xref:System.Char> クラスを使用して Unicode 文字カテゴリを取得し、カテゴリが変更されないものと想定しているコードがある場合は、更新が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="94ea6-125">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="94ea6-126">変更理由</span><span class="sxs-lookup"><span data-stu-id="94ea6-126">Reason for change</span></span>

<span data-ttu-id="94ea6-127">この変更は、<xref:System.Char> 型によって返されるカテゴリを、Unicode 標準および <xref:System.Globalization.CharUnicodeInfo> 型の両方と一致させるために行われました。</span><span class="sxs-lookup"><span data-stu-id="94ea6-127">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="94ea6-128">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="94ea6-128">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="94ea6-129">また、Unicode 文字カテゴリを取得するために <xref:System.Char> に依存するクラス (<xref:System.Text.RegularExpressions.Regex> など) も、この変更による影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="94ea6-129">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
