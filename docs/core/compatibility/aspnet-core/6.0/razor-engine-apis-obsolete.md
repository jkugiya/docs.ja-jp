---
title: '破壊的変更:Razor: 古いとしてマークされた RazorEngine API'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Razor:古いとしてマークされた RazorEngine API'
author: scottaddie
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 173ff0ee5c062f050c967c6edc7bed333d1a2031
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488228"
---
# <a name="razor-razorengine-apis-marked-obsolete"></a><span data-ttu-id="a5255-103">Razor: 古いとしてマークされた RazorEngine API</span><span class="sxs-lookup"><span data-stu-id="a5255-103">Razor: RazorEngine APIs marked obsolete</span></span>

<span data-ttu-id="a5255-104">Blazor の <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> 型に関連する型は、古いとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="a5255-104">Types related to the <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> type in Blazor have been marked as obsolete.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a5255-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a5255-105">Version introduced</span></span>

<span data-ttu-id="a5255-106">6.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="a5255-106">6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a5255-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="a5255-107">Old behavior</span></span>

<span data-ttu-id="a5255-108">`RazorEngine` API は古くありません。</span><span class="sxs-lookup"><span data-stu-id="a5255-108">The `RazorEngine` APIs aren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a5255-109">新しい動作</span><span class="sxs-lookup"><span data-stu-id="a5255-109">New behavior</span></span>

<span data-ttu-id="a5255-110">`RazorEngine` API は非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="a5255-110">The `RazorEngine` APIs are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a5255-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="a5255-111">Reason for change</span></span>

<span data-ttu-id="a5255-112">`RazorEngine` 型は、<xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> 型を優先して非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="a5255-112">The `RazorEngine` type has been deprecated in favor of the <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> type.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a5255-113">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="a5255-113">Recommended action</span></span>

<span data-ttu-id="a5255-114">`RazorEngine` 型から `RazorProjectEngine` 型にソース コードを移行します。</span><span class="sxs-lookup"><span data-stu-id="a5255-114">Migrate source code from the `RazorEngine` type to the `RazorProjectEngine` type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a5255-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a5255-115">Affected APIs</span></span>

- [<span data-ttu-id="a5255-116">Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register</span><span class="sxs-lookup"><span data-stu-id="a5255-116">Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.razor.extensions.injectdirective.register?view=aspnetcore-3.1&preserve-view=true)
- [<span data-ttu-id="a5255-117">Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register</span><span class="sxs-lookup"><span data-stu-id="a5255-117">Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.razor.extensions.namespacedirective.register?view=aspnetcore-2.2&preserve-view=true)
- [<span data-ttu-id="a5255-118">Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register</span><span class="sxs-lookup"><span data-stu-id="a5255-118">Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.razor.extensions.namespacedirective.register?view=aspnetcore-2.2&preserve-view=true)
- [<span data-ttu-id="a5255-119">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span><span class="sxs-lookup"><span data-stu-id="a5255-119">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="a5255-120">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span><span class="sxs-lookup"><span data-stu-id="a5255-120">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="a5255-121">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span><span class="sxs-lookup"><span data-stu-id="a5255-121">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="a5255-122">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span><span class="sxs-lookup"><span data-stu-id="a5255-122">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

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
