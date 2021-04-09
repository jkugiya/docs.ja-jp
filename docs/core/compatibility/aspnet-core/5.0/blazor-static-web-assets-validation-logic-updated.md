---
title: '破壊的変更:Blazor: 静的な Web アセットの検証ロジックの更新'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Blazor:静的な Web アセットの検証ロジックの更新'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b6fb8e9a10157a97119fa07a95fb3dbb8b207214
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498153"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a><span data-ttu-id="6e2c5-103">Blazor: 静的な Web アセットの検証ロジックの更新</span><span class="sxs-lookup"><span data-stu-id="6e2c5-103">Blazor: Updated validation logic for static web assets</span></span>

<span data-ttu-id="6e2c5-104">ASP.NET Core 3.1 と Blazor WebAssembly 3.2 の静的な Web アセットの競合の検証で問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-104">There was an issue in conflict validation for static web assets in ASP.NET Core 3.1 and Blazor WebAssembly 3.2.</span></span> <span data-ttu-id="6e2c5-105">問題は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-105">The issue:</span></span>

* <span data-ttu-id="6e2c5-106">ホストのアセットと、Razor クラスライブラリ (RCL) および Blazor WebAssembly アプリからのアセット間の適切な競合検出が阻止されました。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-106">Prevented proper conflict detection between the host assets and assets from Razor Class Libraries (RCLs) and Blazor WebAssembly apps.</span></span>
* <span data-ttu-id="6e2c5-107">ほとんどの場合、Blazor WebAssembly アプリに影響します。既定では、RCL の静的な Web 資産は `_content/$(PackageId)` プレフィックス付きで提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-107">Mostly affects Blazor WebAssembly apps, since by default, static web assets in RCLs are served under the `_content/$(PackageId)` prefix.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6e2c5-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="6e2c5-108">Version introduced</span></span>

<span data-ttu-id="6e2c5-109">5.0</span><span class="sxs-lookup"><span data-stu-id="6e2c5-109">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="6e2c5-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="6e2c5-110">Old behavior</span></span>

<span data-ttu-id="6e2c5-111">開発中、RCL の静的な Web アセットは、同じホスト パス上にあるホスト プロジェクトのアセットで警告なしでオーバーライドされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-111">During development, an RCL's static web assets could be silently overridden with host project assets on the same host path.</span></span> <span data-ttu-id="6e2c5-112">*/folder/file.txt* で提供される静的な Web アセットを定義した RCL を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-112">Consider an RCL that has defined a static web asset to be served at */folder/file.txt*.</span></span> <span data-ttu-id="6e2c5-113">ホストによって *wwwroot/folder/file.txt* にファイルが配置された場合、RCL または Blazor WebAssembly アプリ上のファイルがこのサーバー上のファイルで警告なしでオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-113">If the host placed a file at *wwwroot/folder/file.txt*, the file on the server silently overrode the file on the RCL or Blazor WebAssembly app.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="6e2c5-114">新しい動作</span><span class="sxs-lookup"><span data-stu-id="6e2c5-114">New behavior</span></span>

<span data-ttu-id="6e2c5-115">この問題が発生すると、ASP.NET Core によって正しく検出されます。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-115">ASP.NET Core correctly detects when this issue happens.</span></span> <span data-ttu-id="6e2c5-116">適切な操作を実行できるように、競合があることがユーザーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-116">It informs you, the user, of the conflict so that you can take the appropriate action.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="6e2c5-117">変更理由</span><span class="sxs-lookup"><span data-stu-id="6e2c5-117">Reason for change</span></span>

<span data-ttu-id="6e2c5-118">静的 Web アセットは、プロジェクトの *wwwroot* ホスト上のファイルによってオーバーライド可能なものとは想定されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-118">Static web assets weren't intended to be overridable by files on the *wwwroot* host of the project.</span></span> <span data-ttu-id="6e2c5-119">これらのファイルをオーバーライドできるようにすると、診断が困難なエラーが発生するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-119">Allowing for the overriding of those files could lead to errors that are difficult to diagnose.</span></span> <span data-ttu-id="6e2c5-120">結果として、発行されたアプリで未定義の動作変更が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-120">The result could be undefined behavior changes in published apps.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6e2c5-121">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="6e2c5-121">Recommended action</span></span>

<span data-ttu-id="6e2c5-122">既定では、RCL ファイルがホスト上のファイルと競合する理由はありません。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-122">By default, there's no reason for an RCL file to conflict with a file on the host.</span></span> <span data-ttu-id="6e2c5-123">RCL ファイルには `_content/${PackageId}` がプレフィックスとして付けられます。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-123">RCL files are prefixed with `_content/${PackageId}`.</span></span> <span data-ttu-id="6e2c5-124">Blazor WebAssembly ファイルはホストの URL 空間のルートに配置されるため、競合が起きやすくなります。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-124">Blazor WebAssembly files are placed at the root of the host URL space, which makes conflicts easier.</span></span> <span data-ttu-id="6e2c5-125">たとえば、Blazor WebAssembly アプリには *favicon.ico* ファイルが含まれており、これはホストもその *wwwroot* フォルダーに配置している場合があります。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-125">For example, Blazor WebAssembly apps contain a *favicon.ico* file that the host might also include in its *wwwroot* folder.</span></span>

<span data-ttu-id="6e2c5-126">競合のソースが RCL ファイルの場合、多くの場合、コードによってライブラリからプロジェクトの *wwwroot* フォルダーにアセットがコピーされていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-126">If the conflict's source is an RCL file, it often means code is copying assets from the library into the project's *wwwroot* folder.</span></span> <span data-ttu-id="6e2c5-127">ファイルをコピーするコードを記述することにより、静的な Web 資産の主な目的が損なわれます。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-127">Writing code to copy files defeats a primary goal of static web assets.</span></span> <span data-ttu-id="6e2c5-128">この目的は、新しいコンパイルをトリガーすることなくコンテンツが更新されるときに、ブラウザーで更新プログラムを取得するための基本となります。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-128">This goal is fundamental to get updates on the browser when the contents are updated without having to trigger a new compilation.</span></span>

<span data-ttu-id="6e2c5-129">この動作を維持し、ホスト上のファイルを維持することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-129">You may choose to preserve this behavior and maintain the file on the host.</span></span> <span data-ttu-id="6e2c5-130">これを行うには、カスタム MSBuild ターゲットを使用して静的 Web アセットの一覧からそのファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-130">To do so, remove the file from the list of static web assets with a custom MSBuild target.</span></span>

<span data-ttu-id="6e2c5-131">ホスト プロジェクトのファイルではなく、RCL のファイルまたは Blazor WebAssembly アプリのファイルを使用するには、ホスト プロジェクトからそのファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="6e2c5-131">To use the RCL's file or the Blazor WebAssembly app's file instead of the host project's file, remove the file from the host project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6e2c5-132">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="6e2c5-132">Affected APIs</span></span>

<span data-ttu-id="6e2c5-133">なし</span><span class="sxs-lookup"><span data-stu-id="6e2c5-133">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
