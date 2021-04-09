---
title: '破壊的変更: 認証:AzureAD.UI および AzureADB2C.UI の API とパッケージが非推奨としてマークされる'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: 認証: AzureAD.UI および AzureADB2C.UI の API とパッケージが非推奨としてマークされる'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 179b0b248131a7c02c5f79fbba4562be0ad49d77
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498270"
---
# <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="178de-103">認証:AzureAD.UI および AzureADB2C.UI の API とパッケージが非推奨としてマークされる</span><span class="sxs-lookup"><span data-stu-id="178de-103">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="178de-104">ASP.NET Core 2.1 では、Azure Active Directory (Azure AD) と Azure Active Directory B2C (Azure AD B2C) の認証の統合は、[Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) パッケージと [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) パッケージによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="178de-104">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="178de-105">これらのパッケージによって提供される機能は、Azure AD v1.0 エンドポイントに基づいています。</span><span class="sxs-lookup"><span data-stu-id="178de-105">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="178de-106">ASP.NET Core 5.0 以降では、Azure AD と Azure AD B2C の認証の統合は、[Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) パッケージによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="178de-106">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="178de-107">このパッケージは、以前は Azure AD v2.0 エンドポイントと呼ばれていた Microsoft ID プラットフォームに基づいています。</span><span class="sxs-lookup"><span data-stu-id="178de-107">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="178de-108">そのため、`Microsoft.AspNetCore.Authentication.AzureAD.UI` パッケージと `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` パッケージの古い API は非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="178de-108">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="178de-109">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="178de-109">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="178de-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="178de-110">Version introduced</span></span>

<span data-ttu-id="178de-111">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="178de-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="178de-112">以前の動作</span><span class="sxs-lookup"><span data-stu-id="178de-112">Old behavior</span></span>

<span data-ttu-id="178de-113">API は非推奨としてマークされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="178de-113">The APIs weren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="178de-114">新しい動作</span><span class="sxs-lookup"><span data-stu-id="178de-114">New behavior</span></span>

<span data-ttu-id="178de-115">API は非推奨としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="178de-115">The APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="178de-116">変更理由</span><span class="sxs-lookup"><span data-stu-id="178de-116">Reason for change</span></span>

<span data-ttu-id="178de-117">Azure AD および Azure AD B2C の認証機能は、`Microsoft.Identity.Web` によって提供される Microsoft Authentication Library (MSAL) API に移行されました。</span><span class="sxs-lookup"><span data-stu-id="178de-117">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="178de-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="178de-118">Recommended action</span></span>

<span data-ttu-id="178de-119">[Web アプリ](https://github.com/azuread/microsoft-identity-web/wiki/web-apps)と [Web API](https://github.com/azuread/microsoft-identity-web/wiki/web-apis) の `Microsoft.Identity.Web` API ガイダンスに従って下さい。</span><span class="sxs-lookup"><span data-stu-id="178de-119">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="178de-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="178de-120">Affected APIs</span></span>

* [<span data-ttu-id="178de-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="178de-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="178de-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="178de-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="178de-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span><span class="sxs-lookup"><span data-stu-id="178de-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="178de-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="178de-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="178de-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="178de-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="178de-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="178de-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
