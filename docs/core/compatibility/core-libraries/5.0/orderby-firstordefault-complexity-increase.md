---
title: 破壊的変更:LINQ OrderBy.First{OrDefault} の複雑さが増大
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。OrderBy.First の実装が変更されました。
ms.date: 11/01/2020
ms.openlocfilehash: 4cd2dda5f60976f935505d6a6cb1e4c23d150d09
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257272"
---
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="3ad5f-103">LINQ OrderBy.First{OrDefault} の複雑さが増大</span><span class="sxs-lookup"><span data-stu-id="3ad5f-103">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="3ad5f-104"><xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> と <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> の実装が変更され、その結果として操作の複雑さが増大します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-104">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

## <a name="change-description"></a><span data-ttu-id="3ad5f-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="3ad5f-105">Change description</span></span>

<span data-ttu-id="3ad5f-106">.NET Core 1.x - 3.x では、<xref:System.Linq.Enumerable.OrderBy%2A> または <xref:System.Linq.Enumerable.OrderByDescending%2A> に続けて、<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> または <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> を呼び出した場合、`O(N)` の複雑さで動作します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-106">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="3ad5f-107">最初の (または既定の) 要素のみが必要であるため、それを検索するのに必要な列挙は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-107">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="3ad5f-108">ただし、<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> または <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> に指定された述語は厳密には `N` 回呼び出されます。ここで、`N` はシーケンスの長さです。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="3ad5f-109">.NET 5 以降のバージョンでは、次のような[変更が加えられました](https://github.com/dotnet/runtime/pull/36643): <xref:System.Linq.Enumerable.OrderBy%2A> または <xref:System.Linq.Enumerable.OrderByDescending%2A> の後に <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> または <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> を呼び出すと、`O(N)` の複雑さではなく `O(N log N)` の複雑さで動作します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-109">In .NET 5 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="3ad5f-110">ただし、<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> または <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> に指定された述語の呼び出し回数は、`N` 回より "*少なく*" することができます。これは、全体的なパフォーマンスにとって重要なことです。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-110">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="3ad5f-111">この変更は、.NET Framework での操作の実装と複雑さに一致します。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-111">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3ad5f-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="3ad5f-112">Reason for change</span></span>

<span data-ttu-id="3ad5f-113">述語を呼び出す回数を減らすことの利点は、全体的な複雑さが低いことより重要であるため、.NET Core 1.0 で導入された実装は元に戻されました。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-113">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="3ad5f-114">詳細については、[こちらの dotnet、ランタイムに関する問題](https://github.com/dotnet/runtime/issues/31554)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-114">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3ad5f-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="3ad5f-115">Version introduced</span></span>

<span data-ttu-id="3ad5f-116">5.0</span><span class="sxs-lookup"><span data-stu-id="3ad5f-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3ad5f-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="3ad5f-117">Recommended action</span></span>

<span data-ttu-id="3ad5f-118">開発者側では、何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3ad5f-118">No action is required on the developer's part.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3ad5f-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="3ad5f-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
