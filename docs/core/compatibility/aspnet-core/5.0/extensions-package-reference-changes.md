---
title: 破壊的変更:拡張機能:一部の NuGet パッケージに影響するパッケージ参照の変更
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: 拡張機能: 一部の NuGet パッケージに影響するパッケージ参照の変更'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 4a525d9f7aad4409fd507fcf80c00968ff4b63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759423"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="d0da2-103">拡張機能:一部の NuGet パッケージに影響するパッケージ参照の変更</span><span class="sxs-lookup"><span data-stu-id="d0da2-103">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="d0da2-104">[aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411) に説明があるように、[dotnet/extensions](https://github.com/dotnet/extensions) リポジトリから [dotnet/runtime](https://github.com/dotnet/runtime) に一部の `Microsoft.Extensions.*` NuGet パッケージを移行するとき、移行されたパッケージの一部にパッケージングの変更が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d0da2-104">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="d0da2-105">この問題に関するディスカッションについては、[dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0da2-105">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d0da2-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="d0da2-106">Version introduced</span></span>

<span data-ttu-id="d0da2-107">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="d0da2-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d0da2-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="d0da2-108">Old behavior</span></span>

<span data-ttu-id="d0da2-109">一部の `Microsoft.Extensions.*` パッケージには、アプリが依存していた API のパッケージ参照が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="d0da2-109">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d0da2-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="d0da2-110">New behavior</span></span>

<span data-ttu-id="d0da2-111">アプリによっては、`Microsoft.Extensions.*` パッケージ依存関係を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0da2-111">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d0da2-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="d0da2-112">Reason for change</span></span>

<span data-ttu-id="d0da2-113">*dotnet/runtime* リポジトリと足並みをそろえるよう、パッケージング ポリシーが更新されました。</span><span class="sxs-lookup"><span data-stu-id="d0da2-113">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="d0da2-114">新しいポリシーの下では、パッケージング中、未使用のパッケージ参照が *.nupkg* ファイルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="d0da2-114">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d0da2-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="d0da2-115">Recommended action</span></span>

<span data-ttu-id="d0da2-116">影響を受けるパッケージを利用しているとき、削除したパッケージ依存関係からの API が使用されている場合、自分のプロジェクトで、削除したパッケージ依存関係に直接的な依存関係を追加してください。</span><span class="sxs-lookup"><span data-stu-id="d0da2-116">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="d0da2-117">影響を受けるパッケージとそれが該当する変更をまとめたものが次の表です。</span><span class="sxs-lookup"><span data-stu-id="d0da2-117">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="d0da2-118">パッケージ名</span><span class="sxs-lookup"><span data-stu-id="d0da2-118">Package name</span></span>|<span data-ttu-id="d0da2-119">変更の説明</span><span class="sxs-lookup"><span data-stu-id="d0da2-119">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="d0da2-120">Microsoft.Extensions.Configuration.Binder</span><span class="sxs-lookup"><span data-stu-id="d0da2-120">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="d0da2-121">`Microsoft.Extensions.Configuration` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-121">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="d0da2-122">Microsoft.Extensions.Configuration.Json</span><span class="sxs-lookup"><span data-stu-id="d0da2-122">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="d0da2-123">`System.Threading.Tasks.Extensions` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-123">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="d0da2-124">Microsoft.Extensions.Hosting.Abstractions</span><span class="sxs-lookup"><span data-stu-id="d0da2-124">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="d0da2-125">`Microsoft.Extensions.Logging.Abstractions` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-125">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="d0da2-126">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="d0da2-126">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="d0da2-127">`Microsoft.Extensions.Configuration.Binder` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-127">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="d0da2-128">Microsoft.Extensions.Logging.Console</span><span class="sxs-lookup"><span data-stu-id="d0da2-128">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="d0da2-129">`Microsoft.Extensions.Configuration.Abstractions` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-129">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="d0da2-130">Microsoft.Extensions.Logging.EventLog</span><span class="sxs-lookup"><span data-stu-id="d0da2-130">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="d0da2-131">.NET Framework 4.6.1 ターゲット フレームワーク モニカーの `System.Diagnostics.EventLog` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-131">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="d0da2-132">Microsoft.Extensions.Logging.EventSource</span><span class="sxs-lookup"><span data-stu-id="d0da2-132">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="d0da2-133">`System.Threading.Tasks.Extensions` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-133">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="d0da2-134">Microsoft.Extensions.Options</span><span class="sxs-lookup"><span data-stu-id="d0da2-134">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="d0da2-135">`System.ComponentModel.Annotations` の参照を削除しました</span><span class="sxs-lookup"><span data-stu-id="d0da2-135">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="d0da2-136">たとえば、`Microsoft.Extensions.Configuration` のパッケージ参照が `Microsoft.Extensions.Configuration.Binder` から削除されました。</span><span class="sxs-lookup"><span data-stu-id="d0da2-136">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="d0da2-137">依存関係からの API はパッケージで使用されていません。</span><span class="sxs-lookup"><span data-stu-id="d0da2-137">No API from the dependency was used in the package.</span></span> <span data-ttu-id="d0da2-138">`Microsoft.Extensions.Configuration` からの API に依存する `Microsoft.Extensions.Configuration.Binder` のユーザーは、自分のプロジェクトで、その直接的な参照を追加してください。</span><span class="sxs-lookup"><span data-stu-id="d0da2-138">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d0da2-139">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="d0da2-139">Affected APIs</span></span>

<span data-ttu-id="d0da2-140">None</span><span class="sxs-lookup"><span data-stu-id="d0da2-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->