---
title: '破壊的変更:Blazor: コンパイル時にコンポーネントからトリミングされる無意味な空白文字'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:コンパイル時にコンポーネントからトリミングされる無意味な空白文字'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: d29171c43e587eba648de3f877e1cbb1c7156499
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498205"
---
# <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="63b77-103">Blazor: コンパイル時にコンポーネントからトリミングされる無意味な空白文字</span><span class="sxs-lookup"><span data-stu-id="63b77-103">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="63b77-104">ASP.NET Core 5.0 Preview 7 より、Razor コンパイラでは、コンパイル時に Blazor コンポーネント ( *.razor* ファイル) の無意味な空白文字が除外されます。</span><span class="sxs-lookup"><span data-stu-id="63b77-104">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="63b77-105">ディスカッションについては、イシュー [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63b77-105">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="63b77-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="63b77-106">Version introduced</span></span>

<span data-ttu-id="63b77-107">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="63b77-107">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="63b77-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="63b77-108">Old behavior</span></span>

<span data-ttu-id="63b77-109">Blazor Server と Blazor WebAssembly の 3.x バージョンでは、コンポーネントのソース コードで空白文字が許可されます。</span><span class="sxs-lookup"><span data-stu-id="63b77-109">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="63b77-110">空白文字のみのテキスト ノードは、視覚効果がないときでも、ブラウザーのドキュメント オブジェクト モデル (DOM) にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="63b77-110">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="63b77-111">次の Blazor コンポーネント コードについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="63b77-111">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="63b77-112">前の例では、次の場所で 2 つの空白文字ノードがレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="63b77-112">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="63b77-113">`@foreach` コード ブロックの外側。</span><span class="sxs-lookup"><span data-stu-id="63b77-113">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="63b77-114">`<li>` 要素の前後。</span><span class="sxs-lookup"><span data-stu-id="63b77-114">Around the `<li>` element.</span></span>
* <span data-ttu-id="63b77-115">`@item.Text` 出力の前後。</span><span class="sxs-lookup"><span data-stu-id="63b77-115">Around the `@item.Text` output.</span></span>

<span data-ttu-id="63b77-116">100 項目が含まれるリストの場合、402 の空白文字ノードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="63b77-116">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="63b77-117">これは、レンダリングされる出力に視覚的に影響を与える空白文字ノードがない場合でも、レンダリングされる全ノードの半分以上です。</span><span class="sxs-lookup"><span data-stu-id="63b77-117">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="63b77-118">コンポーネントの静的 HTML をレンダリングする場合、タグ内の空白文字は保持されませんでした。</span><span class="sxs-lookup"><span data-stu-id="63b77-118">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="63b77-119">たとえば、次のコンポーネントのソースをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="63b77-119">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="63b77-120">空白文字が保持されていません。</span><span class="sxs-lookup"><span data-stu-id="63b77-120">Whitespace isn't preserved.</span></span> <span data-ttu-id="63b77-121">プレレンダリングされた出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="63b77-121">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

## <a name="new-behavior"></a><span data-ttu-id="63b77-122">新しい動作</span><span class="sxs-lookup"><span data-stu-id="63b77-122">New behavior</span></span>

<span data-ttu-id="63b77-123">`@preservewhitespace` ディレクティブが値 `true` と共に使用されない限り、空白文字ノードは次の場合に削除されます。</span><span class="sxs-lookup"><span data-stu-id="63b77-123">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="63b77-124">要素内で先頭または末尾にある。</span><span class="sxs-lookup"><span data-stu-id="63b77-124">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="63b77-125">`RenderFragment` パラメーター内の先頭または末尾にある。</span><span class="sxs-lookup"><span data-stu-id="63b77-125">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="63b77-126">たとえば、別のコンポーネントに渡される子コンテンツです。</span><span class="sxs-lookup"><span data-stu-id="63b77-126">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="63b77-127">`@if` や `@foreach` のような、C# コード ブロックの前か後にある。</span><span class="sxs-lookup"><span data-stu-id="63b77-127">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="63b77-128">変更理由</span><span class="sxs-lookup"><span data-stu-id="63b77-128">Reason for change</span></span>

<span data-ttu-id="63b77-129">ASP.NET Core 5.0 の Blazor の目標は、レンダリングと比較のパフォーマンスを改善することです。</span><span class="sxs-lookup"><span data-stu-id="63b77-129">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="63b77-130">無意味な空白文字ツリー ノードによって、ベンチマークでは、レンダリング時間の最大 40% が消費されていました。</span><span class="sxs-lookup"><span data-stu-id="63b77-130">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="63b77-131">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="63b77-131">Recommended action</span></span>

<span data-ttu-id="63b77-132">ほとんどの場合、レンダリングされたコンポーネントのビジュアル レイアウトは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="63b77-132">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="63b77-133">ただし、空白文字の削除は、`white-space: pre` などの CSS ルールを使用するときに、レンダリングされた出力に影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="63b77-133">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="63b77-134">このパフォーマンスの最適化を無効にして、空白を保持するには、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="63b77-134">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="63b77-135">特定のコンポーネントに設定を適用するには、 *.razor* ファイルの先頭に `@preservewhitespace true` ディレクティブを追加する。</span><span class="sxs-lookup"><span data-stu-id="63b77-135">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="63b77-136">サブディレクトリ全体またはプロジェクト全体に設定を適用するには、 *_Imports.razor* ファイル内に `@preservewhitespace true` ディレクティブを追加する。</span><span class="sxs-lookup"><span data-stu-id="63b77-136">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="63b77-137">ほとんどの場合、アプリケーションでは一般的に通常の動作が続行されるため (ただし、速くなります)、何の措置も必要ありません。</span><span class="sxs-lookup"><span data-stu-id="63b77-137">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="63b77-138">空白文字の削除で特定のコンポーネントに問題が発生する場合、そのコンポーネントで `@preservewhitespace true` を使用し、この最適化を無効にします。</span><span class="sxs-lookup"><span data-stu-id="63b77-138">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="63b77-139">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="63b77-139">Affected APIs</span></span>

<span data-ttu-id="63b77-140">なし</span><span class="sxs-lookup"><span data-stu-id="63b77-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
