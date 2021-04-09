---
title: '破壊的変更:Blazor: NuGet パッケージのターゲット フレームワークを変更'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:NuGet パッケージのターゲット フレームワークを変更'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 02945c223410860c9336b6046afe54cacce878dd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498192"
---
# <a name="blazor-target-framework-of-nuget-packages-changed"></a><span data-ttu-id="09598-103">Blazor: NuGet パッケージのターゲット フレームワークを変更</span><span class="sxs-lookup"><span data-stu-id="09598-103">Blazor: Target framework of NuGet packages changed</span></span>

<span data-ttu-id="09598-104">Blazor 3.2 WebAssembly プロジェクトは、.NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`) をターゲットにするようコンパイルされていました。</span><span class="sxs-lookup"><span data-stu-id="09598-104">Blazor 3.2 WebAssembly projects were compiled to target .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`).</span></span> <span data-ttu-id="09598-105">ASP.NET Core 5.0 では、Blazor Server と Blazor WebAssembly プロジェクトの両方で .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`) がターゲットとされます。</span><span class="sxs-lookup"><span data-stu-id="09598-105">In ASP.NET Core 5.0, both Blazor Server and Blazor WebAssembly projects target .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`).</span></span> <span data-ttu-id="09598-106">ターゲット フレームワークの変更に対応するため、次の Blazor パッケージで .NET Standard 2.1 がターゲットとされることはなくなりました。</span><span class="sxs-lookup"><span data-stu-id="09598-106">To better align with the target framework change, the following Blazor packages no longer target .NET Standard 2.1:</span></span>

* [<span data-ttu-id="09598-107">Microsoft.AspNetCore.Components</span><span class="sxs-lookup"><span data-stu-id="09598-107">Microsoft.AspNetCore.Components</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [<span data-ttu-id="09598-108">Microsoft.AspNetCore.Components.Authorization</span><span class="sxs-lookup"><span data-stu-id="09598-108">Microsoft.AspNetCore.Components.Authorization</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [<span data-ttu-id="09598-109">Microsoft.AspNetCore.Components.Forms</span><span class="sxs-lookup"><span data-stu-id="09598-109">Microsoft.AspNetCore.Components.Forms</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [<span data-ttu-id="09598-110">Microsoft.AspNetCore.Components.Web</span><span class="sxs-lookup"><span data-stu-id="09598-110">Microsoft.AspNetCore.Components.Web</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [<span data-ttu-id="09598-111">Microsoft.AspNetCore.Components.WebAssembly</span><span class="sxs-lookup"><span data-stu-id="09598-111">Microsoft.AspNetCore.Components.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [<span data-ttu-id="09598-112">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span><span class="sxs-lookup"><span data-stu-id="09598-112">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [<span data-ttu-id="09598-113">Microsoft.JSInterop</span><span class="sxs-lookup"><span data-stu-id="09598-113">Microsoft.JSInterop</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop)
* [<span data-ttu-id="09598-114">Microsoft.JSInterop.WebAssembly</span><span class="sxs-lookup"><span data-stu-id="09598-114">Microsoft.JSInterop.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [<span data-ttu-id="09598-115">Microsoft.Authentication.WebAssembly.Msal</span><span class="sxs-lookup"><span data-stu-id="09598-115">Microsoft.Authentication.WebAssembly.Msal</span></span>](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

<span data-ttu-id="09598-116">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09598-116">For discussion, see GitHub issue [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="09598-117">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="09598-117">Version introduced</span></span>

<span data-ttu-id="09598-118">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="09598-118">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="09598-119">以前の動作</span><span class="sxs-lookup"><span data-stu-id="09598-119">Old behavior</span></span>

<span data-ttu-id="09598-120">Blazor 3.1 および 3.2 では、.NET Standard 2.1 and .NET Core 3.1 がパッケージによりターゲットとされます。</span><span class="sxs-lookup"><span data-stu-id="09598-120">In Blazor 3.1 and 3.2, packages target .NET Standard 2.1 and .NET Core 3.1.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="09598-121">新しい動作</span><span class="sxs-lookup"><span data-stu-id="09598-121">New behavior</span></span>

<span data-ttu-id="09598-122">ASP.NET Core 5.0 では、.NET 5.0 がパッケージによりターゲットとされます。</span><span class="sxs-lookup"><span data-stu-id="09598-122">In ASP.NET Core 5.0, packages target .NET 5.0.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="09598-123">変更理由</span><span class="sxs-lookup"><span data-stu-id="09598-123">Reason for change</span></span>

<span data-ttu-id="09598-124">.NET ターゲット フレームワークの要件に対応するために変更が行われました。</span><span class="sxs-lookup"><span data-stu-id="09598-124">The change was made to better align with .NET target framework requirements.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="09598-125">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="09598-125">Recommended action</span></span>

<span data-ttu-id="09598-126">Blazor 3.2 WebAssembly のプロジェクトは、パッケージ参照の 5.x.x への更新の一環として、.NET 5.0 をターゲットとする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09598-126">Blazor 3.2 WebAssembly projects should target .NET 5.0 as part of updating their package references to 5.x.x.</span></span> <span data-ttu-id="09598-127">これらのパッケージのいずれかを参照するライブラリでは、要件に応じて、.NET 5.0 をターゲットとするか、またはマルチターゲットとすることができます。</span><span class="sxs-lookup"><span data-stu-id="09598-127">Libraries that reference one of these packages can either target .NET 5.0 or multi-target depending on their requirements.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="09598-128">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="09598-128">Affected APIs</span></span>

<span data-ttu-id="09598-129">なし</span><span class="sxs-lookup"><span data-stu-id="09598-129">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
