---
title: '破壊的変更:Blazor: JSObjectReference および JSInProcessObjectReference 型を internal に変更'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:JSObjectReference および JSInProcessObjectReference 型を internal に変更'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 44e4c902ff22e18fa9ab8b484952082e5b81be94
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497854"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="6c13d-103">Blazor: JSObjectReference および JSInProcessObjectReference 型を internal に変更</span><span class="sxs-lookup"><span data-stu-id="6c13d-103">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="6c13d-104">ASP.NET Core 5.0 RC1 で導入された新しい `Microsoft.JSInterop.JSObjectReference` および `Microsoft.JSInterop.JSInProcessObjectReference` 型は `internal` としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="6c13d-104">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6c13d-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="6c13d-105">Version introduced</span></span>

<span data-ttu-id="6c13d-106">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="6c13d-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="6c13d-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="6c13d-107">Old behavior</span></span>

<span data-ttu-id="6c13d-108">`JSObjectReference` は、`IJSRuntime` 経由で JavaScript の相互運用呼び出しから取得できます。</span><span class="sxs-lookup"><span data-stu-id="6c13d-108">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="6c13d-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6c13d-109">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a><span data-ttu-id="6c13d-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="6c13d-110">New behavior</span></span>

<span data-ttu-id="6c13d-111">`JSObjectReference` では [internal](../../../../csharp/language-reference/keywords/internal.md) アクセス修飾子が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6c13d-111">`JSObjectReference` uses the [internal](../../../../csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="6c13d-112">代わりに `public` `IJSObjectReference` インターフェイスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c13d-112">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="6c13d-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6c13d-113">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="6c13d-114">`JSInProcessObjectReference` も `internal` としてマークされ、`IJSInProcessObjectReference` によって置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="6c13d-114">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="6c13d-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="6c13d-115">Reason for change</span></span>

<span data-ttu-id="6c13d-116">この変更により、JavaScript の相互運用機能が Blazor 内の他のパターンとより一貫したものになります。</span><span class="sxs-lookup"><span data-stu-id="6c13d-116">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="6c13d-117">`IJSObjectReference` は、同様の目的で機能し、同様のメソッドと拡張機能を備えているという点で `IJSRuntime` に似ています。</span><span class="sxs-lookup"><span data-stu-id="6c13d-117">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6c13d-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="6c13d-118">Recommended action</span></span>

<span data-ttu-id="6c13d-119">`JSObjectReference` と `JSInProcessObjectReference` の使用を、それぞれ `IJSObjectReference` と `IJSInProcessObjectReference` に置換します。</span><span class="sxs-lookup"><span data-stu-id="6c13d-119">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6c13d-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="6c13d-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
