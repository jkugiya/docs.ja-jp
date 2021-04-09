---
title: '破壊的変更:Razor: 古いとしてマークされた RazorEngine API'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Razor:古いとしてマークされた RazorEngine API'
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 08026cf32eec5ee391fab3d2ccdd9f22c4a3967b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497035"
---
# <a name="razor-razorengine-apis-marked-obsolete"></a><span data-ttu-id="d482d-103">Razor: 古いとしてマークされた RazorEngine API</span><span class="sxs-lookup"><span data-stu-id="d482d-103">Razor: RazorEngine APIs marked obsolete</span></span>

<span data-ttu-id="d482d-104">Blazor の <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> 型に関連する型は、古いとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="d482d-104">Types related to the <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> type in Blazor have been marked as obsolete.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d482d-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="d482d-105">Version introduced</span></span>

<span data-ttu-id="d482d-106">6.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="d482d-106">6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d482d-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="d482d-107">Old behavior</span></span>

<span data-ttu-id="d482d-108">`RazorEngine` API は古くありません。</span><span class="sxs-lookup"><span data-stu-id="d482d-108">The `RazorEngine` APIs aren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d482d-109">新しい動作</span><span class="sxs-lookup"><span data-stu-id="d482d-109">New behavior</span></span>

<span data-ttu-id="d482d-110">`RazorEngine` API は非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="d482d-110">The `RazorEngine` APIs are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d482d-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="d482d-111">Reason for change</span></span>

<span data-ttu-id="d482d-112">`RazorEngine` 型は、<xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> 型を優先して非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="d482d-112">The `RazorEngine` type has been deprecated in favor of the <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> type.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d482d-113">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="d482d-113">Recommended action</span></span>

<span data-ttu-id="d482d-114">`RazorEngine` 型から `RazorProjectEngine` 型にソース コードを移行します。</span><span class="sxs-lookup"><span data-stu-id="d482d-114">Migrate source code from the `RazorEngine` type to the `RazorProjectEngine` type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d482d-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="d482d-115">Affected APIs</span></span>

- `Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- [<span data-ttu-id="d482d-116">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span><span class="sxs-lookup"><span data-stu-id="d482d-116">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="d482d-117">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span><span class="sxs-lookup"><span data-stu-id="d482d-117">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="d482d-118">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span><span class="sxs-lookup"><span data-stu-id="d482d-118">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="d482d-119">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span><span class="sxs-lookup"><span data-stu-id="d482d-119">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

<!--

## Category

ASP.NET Core

## Affected APIs

- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register`
- `T:Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder`

-->
