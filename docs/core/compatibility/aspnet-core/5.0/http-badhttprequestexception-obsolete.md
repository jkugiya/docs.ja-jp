---
title: 破壊的変更:HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5837018def634b732b4f273f1a794267f4d17972
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498140"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="f938f-103">HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました</span><span class="sxs-lookup"><span data-stu-id="f938f-103">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="f938f-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は非推奨となっており、`Microsoft.AspNetCore.Http.BadHttpRequestException` から誘導するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="f938f-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="f938f-105">Kestrel サーバーと IIS サーバーでは、下位互換性のために、今後も以前の例外型がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f938f-105">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="f938f-106">非推奨になった型は、将来のリリースで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="f938f-106">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="f938f-107">ディスカッションについては、[dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f938f-107">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f938f-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f938f-108">Version introduced</span></span>

<span data-ttu-id="f938f-109">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="f938f-109">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="f938f-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="f938f-110">Old behavior</span></span>

<span data-ttu-id="f938f-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と`Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は <xref:System.IO.IOException?displayProperty=nameWithType> から派生しています。</span><span class="sxs-lookup"><span data-stu-id="f938f-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="f938f-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="f938f-112">New behavior</span></span>

<span data-ttu-id="f938f-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="f938f-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="f938f-114">型は、`System.IO.IOException` の派生型である `Microsoft.AspNetCore.Http.BadHttpRequestException` からも派生します。</span><span class="sxs-lookup"><span data-stu-id="f938f-114">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f938f-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="f938f-115">Reason for change</span></span>

<span data-ttu-id="f938f-116">次の変更が行われました。</span><span class="sxs-lookup"><span data-stu-id="f938f-116">The change was made to:</span></span>

* <span data-ttu-id="f938f-117">重複する型を統合します。</span><span class="sxs-lookup"><span data-stu-id="f938f-117">Consolidate duplicate types.</span></span>
* <span data-ttu-id="f938f-118">異なるサーバー実装間で動作を統一します。</span><span class="sxs-lookup"><span data-stu-id="f938f-118">Unify behavior across server implementations.</span></span>

<span data-ttu-id="f938f-119">Kestrel または IIS の使用時、アプリで基本例外 `Microsoft.AspNetCore.Http.BadHttpRequestException` をキャッチできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f938f-119">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f938f-120">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f938f-120">Recommended action</span></span>

<span data-ttu-id="f938f-121">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` の使用状況を `Microsoft.AspNetCore.Http.BadHttpRequestException` に置換します。</span><span class="sxs-lookup"><span data-stu-id="f938f-121">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f938f-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f938f-122">Affected APIs</span></span>

- [<span data-ttu-id="f938f-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="f938f-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="f938f-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="f938f-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
