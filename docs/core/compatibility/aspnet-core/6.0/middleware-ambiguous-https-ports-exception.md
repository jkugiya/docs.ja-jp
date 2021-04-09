---
title: 破壊的変更:ミドルウェア:HTTPS リダイレクト ミドルウェアがあいまいな HTTPS ポートで例外をスローする
description: 'ASP.NET Core 6.0 での破壊的変更について説明します。タイトル: ミドルウェア:HTTPS リダイレクト ミドルウェアがあいまいな HTTPS ポートで例外をスローする'
ms.author: scaddie
ms.date: 02/04/2021
ms.openlocfilehash: 5c41251fac29f7c2dc2bdc3eb5610bb571f438c9
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497022"
---
# <a name="middleware-https-redirection-middleware-throws-exception-on-ambiguous-https-ports"></a><span data-ttu-id="534b7-103">ミドルウェア:HTTPS リダイレクト ミドルウェアがあいまいな HTTPS ポートで例外をスローする</span><span class="sxs-lookup"><span data-stu-id="534b7-103">Middleware: HTTPS Redirection Middleware throws exception on ambiguous HTTPS ports</span></span>

<span data-ttu-id="534b7-104">ASP.NET Core 6.0 で [HTTPS リダイレクト ミドルウェア](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A)によって、サーバー構成で複数の HTTPS ポートが検出されると、<xref:System.InvalidOperationException> 型の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="534b7-104">In ASP.NET Core 6.0, the [HTTPS Redirection Middleware](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A) throws an exception of type <xref:System.InvalidOperationException> when it finds multiple HTTPS ports in the server configuration.</span></span> <span data-ttu-id="534b7-105">この例外メッセージには、"値が複数見つかり、IServerAddressesFeature から https ポートを判別できません。</span><span class="sxs-lookup"><span data-stu-id="534b7-105">The exception's message contains the text "Cannot determine the https port from IServerAddressesFeature, multiple values were found.</span></span> <span data-ttu-id="534b7-106">希望のポートを HttpsRedirectionOptions.HttpsPort に明示的に設定してください。" というテキストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="534b7-106">Set the desired port explicitly on HttpsRedirectionOptions.HttpsPort."</span></span>

<span data-ttu-id="534b7-107">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#29222](https://github.com/dotnet/aspnetcore/issues/29222) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="534b7-107">For discussion, see GitHub issue [dotnet/aspnetcore#29222](https://github.com/dotnet/aspnetcore/issues/29222).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="534b7-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="534b7-108">Version introduced</span></span>

<span data-ttu-id="534b7-109">6.0</span><span class="sxs-lookup"><span data-stu-id="534b7-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="534b7-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="534b7-110">Old behavior</span></span>

<span data-ttu-id="534b7-111">HTTPS リダイレクト ミドルウェアにポートが明示的に構成されていない場合、最初の要求時に <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature> が検索され、リダイレクト先の HTTPS ポートが決定されます。</span><span class="sxs-lookup"><span data-stu-id="534b7-111">When the HTTPS Redirection Middleware isn't explicitly configured with a port, it searches <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature> during the first request to determine the HTTPS port to which it should redirect.</span></span>

<span data-ttu-id="534b7-112">HTTPS ポートがない場合、または個別のポートが複数ある場合は、どのポートを使用すべきか判別できません。</span><span class="sxs-lookup"><span data-stu-id="534b7-112">If there are no HTTPS ports or multiple distinct ports, it's unclear which port should be used.</span></span> <span data-ttu-id="534b7-113">ミドルウェアが警告をログし、自身を無効にします。</span><span class="sxs-lookup"><span data-stu-id="534b7-113">The middleware logs a warning and disables itself.</span></span> <span data-ttu-id="534b7-114">HTTP 要求は正常に処理されます。</span><span class="sxs-lookup"><span data-stu-id="534b7-114">HTTP requests are processed normally.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="534b7-115">新しい動作</span><span class="sxs-lookup"><span data-stu-id="534b7-115">New behavior</span></span>

<span data-ttu-id="534b7-116">HTTPS リダイレクト ミドルウェアにポートが明示的に構成されていない場合、最初の要求時に `IServerAddressesFeature` が検索され、リダイレクト先の HTTPS ポートが決定されます。</span><span class="sxs-lookup"><span data-stu-id="534b7-116">When the HTTPS Redirection Middleware isn't explicitly configured with a port, it searches `IServerAddressesFeature` during the first request to determine the HTTPS port to which it should redirect.</span></span>

<span data-ttu-id="534b7-117">HTTPS ポートがない場合は、ミドルウェアが警告をログ記録し、自身を無効にします。</span><span class="sxs-lookup"><span data-stu-id="534b7-117">If there are no HTTPS ports, the middleware still logs a warning and disables itself.</span></span> <span data-ttu-id="534b7-118">HTTP 要求は正常に処理されます。</span><span class="sxs-lookup"><span data-stu-id="534b7-118">HTTP requests are processed normally.</span></span> <span data-ttu-id="534b7-119">この動作では、次がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="534b7-119">This behavior supports:</span></span>

* <span data-ttu-id="534b7-120">HTTPS を使用しない開発シナリオ。</span><span class="sxs-lookup"><span data-stu-id="534b7-120">Development scenarios without HTTPS.</span></span>
* <span data-ttu-id="534b7-121">サーバーに到達する前に TLS が終了するホストされるシナリオ。</span><span class="sxs-lookup"><span data-stu-id="534b7-121">Hosted scenarios in which TLS is terminated before reaching the server.</span></span>

<span data-ttu-id="534b7-122">個別のポートが複数ある場合は、どのポートを使用すべきか判別できません。</span><span class="sxs-lookup"><span data-stu-id="534b7-122">If there are multiple distinct ports, it's unclear which port should be used.</span></span> <span data-ttu-id="534b7-123">ミドルウェアが例外をスローし、HTTP 要求は失敗します。</span><span class="sxs-lookup"><span data-stu-id="534b7-123">The middleware throws an exception and fails the HTTP request.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="534b7-124">変更理由</span><span class="sxs-lookup"><span data-stu-id="534b7-124">Reason for change</span></span>

<span data-ttu-id="534b7-125">この変更により、HTTPS が使用できることがわかっているときに、機密である可能性があるデータが、暗号化されていない HTTP 接続を介して送信されなくなります。</span><span class="sxs-lookup"><span data-stu-id="534b7-125">This change prevents potentially sensitive data from being served over unencrypted HTTP connections when HTTPS is known to be available.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="534b7-126">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="534b7-126">Recommended action</span></span>

<span data-ttu-id="534b7-127">サーバーに個別の HTTPS ポートが複数ある場合に HTTPS リダイレクトを有効にするには、構成でポートを 1 つ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="534b7-127">To enable HTTPS redirection when the server has multiple distinct HTTPS ports, you must specify one port in the configuration.</span></span> <span data-ttu-id="534b7-128">詳細については、「[ポート構成](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="534b7-128">For more information, see [Port configuration](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration).</span></span>

<span data-ttu-id="534b7-129">お使いのアプリで HTTPS リダイレクト ミドルウェアが不要な場合は、*Startup.cs* から `UseHttpsRedirection` を削除します。</span><span class="sxs-lookup"><span data-stu-id="534b7-129">If you don't need the HTTPS Redirection Middleware in your app, remove `UseHttpsRedirection` from *Startup.cs*.</span></span>

<span data-ttu-id="534b7-130">正しい HTTPS ポートを動的に選択する必要がある場合は、GitHub のイシュー [dotnet/aspnetcore#21291](https://github.com/dotnet/aspnetcore/issues/21291) にフィードバックを提供してください。</span><span class="sxs-lookup"><span data-stu-id="534b7-130">If you need to select the correct HTTPS port dynamically, provide feedback in GitHub issue [dotnet/aspnetcore#21291](https://github.com/dotnet/aspnetcore/issues/21291).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="534b7-131">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="534b7-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection`

-->
