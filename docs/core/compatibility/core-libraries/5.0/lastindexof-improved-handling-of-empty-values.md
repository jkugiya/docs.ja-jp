---
title: 破壊的変更:LastIndexOf では、空の検索文字列の処理が改善されています
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、LastIndexOf と関連 API により、長さ 0 の substring を検索するときに正しい値が返されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 9dc34300d867fe1bb9264494b3f2261bad2c1eea
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257428"
---
# <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a><span data-ttu-id="ce29a-103">LastIndexOf では、空の検索文字列の処理が改善されています</span><span class="sxs-lookup"><span data-stu-id="ce29a-103">LastIndexOf has improved handling of empty search strings</span></span>

<span data-ttu-id="ce29a-104"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> と関連 API により、より大きな文字列内で長さ 0 の (または長さ 0 と同等の) サブ文字列を検索するときに、正しい値が返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ce29a-104"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs now return correct values when searching for a zero-length (or zero-length equivalent) substring within a larger string.</span></span>

## <a name="change-description"></a><span data-ttu-id="ce29a-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="ce29a-105">Change description</span></span>

<span data-ttu-id="ce29a-106">.NET Framework と .NET Core 1.0 から 3.1 では、呼び出し元が長さ 0 のサブ文字列を検索するときに、<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> と関連 API によって不正な値が返されることがありました。</span><span class="sxs-lookup"><span data-stu-id="ce29a-106">In .NET Framework and .NET Core 1.0 - 3.1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs might return an incorrect value when the caller searches for a zero-length substring.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

<span data-ttu-id="ce29a-107">.NET 5 以降では、これらの API によって `LastIndexOf` の正しい値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ce29a-107">Starting with .NET 5, these APIs return the correct value for `LastIndexOf`.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

<span data-ttu-id="ce29a-108">これらの例では、`"Hello".Substring(5)` と `"Hello".AsSpan().Slice(5)` の両方で空の文字列が生成されるため、`5` は正しい答えです。これは、検索対象の空のサブ文字列と同等です。</span><span class="sxs-lookup"><span data-stu-id="ce29a-108">In these examples, `5` is the correct answer because `"Hello".Substring(5)` and `"Hello".AsSpan().Slice(5)` both produce an empty string, which is trivially equal to the empty substring that is sought.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ce29a-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="ce29a-109">Reason for change</span></span>

<span data-ttu-id="ce29a-110">この変更は、.NET 5 の文字列処理に関する全般的なバグ修正作業の一環として行われました。</span><span class="sxs-lookup"><span data-stu-id="ce29a-110">This change was part of an overall bug fixing effort around string handling for .NET 5.</span></span> <span data-ttu-id="ce29a-111">またこれは、Windows の動作と Windows 以外のプラットフォームの動作を統合するのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ce29a-111">It also helps unify our behavior between Windows and non-Windows platforms.</span></span> <span data-ttu-id="ce29a-112">詳細については、[dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) および [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce29a-112">For more information, see [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) and [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ce29a-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ce29a-113">Version introduced</span></span>

<span data-ttu-id="ce29a-114">5.0</span><span class="sxs-lookup"><span data-stu-id="ce29a-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ce29a-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="ce29a-115">Recommended action</span></span>

<span data-ttu-id="ce29a-116">何らかのアクションをとる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ce29a-116">You don't need to take any action.</span></span> <span data-ttu-id="ce29a-117">.NET 5 ランタイムでは、新しい動作が自動的に提供されます。</span><span class="sxs-lookup"><span data-stu-id="ce29a-117">The .NET 5 runtime provides the new behaviors automatically.</span></span>

<span data-ttu-id="ce29a-118">以前の動作を復元するための互換性スイッチはありません。</span><span class="sxs-lookup"><span data-stu-id="ce29a-118">There is no compatibility switch to restore the old behavior.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ce29a-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="ce29a-119">Affected APIs</span></span>

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
