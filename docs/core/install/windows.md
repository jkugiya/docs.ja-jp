---
title: Windows に .NET をインストールする
description: .NET をインストールできる Windows のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 57cebc562949627be70aabe24e75ad4567d072fd
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536126"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="9d793-103">Windows に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="9d793-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

<span data-ttu-id="9d793-107">この記事では、Windows に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d793-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="9d793-108">.NET は、ランタイムと SDK で構成されています。</span><span class="sxs-lookup"><span data-stu-id="9d793-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="9d793-109">ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9d793-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="9d793-110">SDK は、.NET アプリとライブラリの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="9d793-111">.NET ランタイムは、常に SDK と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="9d793-112">.NET の最新バージョンは 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="9d793-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="9d793-113">.NET をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="9d793-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="9d793-114">サポートされているリリース</span><span class="sxs-lookup"><span data-stu-id="9d793-114">Supported releases</span></span>

<span data-ttu-id="9d793-115">以下の表は、現在サポートされている .NET リリースと、それらがサポートされている Windows のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="9d793-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="9d793-116">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Windows のバージョンの有効期限が切れるまで](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="9d793-117">Windows 10 のバージョンのサービス終了日は、エディションごとに分かれています。</span><span class="sxs-lookup"><span data-stu-id="9d793-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="9d793-118">次の表では、**Home**、**Pro**、**Pro Education**、**Pro for Workstations** の各エディションだけが考慮されています。</span><span class="sxs-lookup"><span data-stu-id="9d793-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="9d793-119">具体的な詳細については、「[Windows ライフサイクルのファクト シート](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)」を確認してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="9d793-120">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="9d793-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9d793-121">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="9d793-121">Operating System</span></span>            | <span data-ttu-id="9d793-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d793-122">.NET Core 2.1</span></span> | <span data-ttu-id="9d793-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9d793-123">.NET Core 3.1</span></span> | <span data-ttu-id="9d793-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="9d793-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="9d793-125">Windows 10 バージョン 20H2</span><span class="sxs-lookup"><span data-stu-id="9d793-125">Windows 10, Version 20H2</span></span>    | <span data-ttu-id="9d793-126">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-126">✔️</span></span>           | <span data-ttu-id="9d793-127">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-127">✔️</span></span>            | <span data-ttu-id="9d793-128">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-128">✔️</span></span>    |
| <span data-ttu-id="9d793-129">Windows 10 バージョン 2004</span><span class="sxs-lookup"><span data-stu-id="9d793-129">Windows 10, Version 2004</span></span>    | <span data-ttu-id="9d793-130">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-130">✔️</span></span>           | <span data-ttu-id="9d793-131">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-131">✔️</span></span>            | <span data-ttu-id="9d793-132">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-132">✔️</span></span>    |
| <span data-ttu-id="9d793-133">Windows 10 バージョン 1909</span><span class="sxs-lookup"><span data-stu-id="9d793-133">Windows 10, Version 1909</span></span>    | <span data-ttu-id="9d793-134">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-134">✔️</span></span>           | <span data-ttu-id="9d793-135">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-135">✔️</span></span>            | <span data-ttu-id="9d793-136">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-136">✔️</span></span>    |
| <span data-ttu-id="9d793-137">Windows 10 バージョン 1903</span><span class="sxs-lookup"><span data-stu-id="9d793-137">Windows 10, Version 1903</span></span>    | <span data-ttu-id="9d793-138">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-138">✔️</span></span>           | <span data-ttu-id="9d793-139">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-139">✔️</span></span>            | <span data-ttu-id="9d793-140">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-140">✔️</span></span>    |
| <span data-ttu-id="9d793-141">Windows 10 バージョン 1809</span><span class="sxs-lookup"><span data-stu-id="9d793-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="9d793-142">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-142">✔️</span></span>           | <span data-ttu-id="9d793-143">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-143">✔️</span></span>            | <span data-ttu-id="9d793-144">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-144">✔️</span></span>    |
| <span data-ttu-id="9d793-145"> Windows 10 バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="9d793-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="9d793-146">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-146">✔️</span></span>           | <span data-ttu-id="9d793-147">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-147">✔️</span></span>            | <span data-ttu-id="9d793-148">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-148">✔️</span></span>    |
| <span data-ttu-id="9d793-149">Windows 10 バージョン 1709</span><span class="sxs-lookup"><span data-stu-id="9d793-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="9d793-150">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-150">✔️</span></span>           | <span data-ttu-id="9d793-151">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-151">✔️</span></span>            | <span data-ttu-id="9d793-152">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-152">✔️</span></span>    |
| <span data-ttu-id="9d793-153">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="9d793-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="9d793-154">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-154">✔️</span></span>           | <span data-ttu-id="9d793-155">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-155">✔️</span></span>            | <span data-ttu-id="9d793-156">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-156">✔️</span></span>    |
| <span data-ttu-id="9d793-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="9d793-157">Windows 8.1</span></span>                 | <span data-ttu-id="9d793-158">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-158">✔️</span></span>           | <span data-ttu-id="9d793-159">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-159">✔️</span></span>            | <span data-ttu-id="9d793-160">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-160">✔️</span></span>    |
| <span data-ttu-id="9d793-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="9d793-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="9d793-162">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-162">✔️</span></span>           | <span data-ttu-id="9d793-163">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-163">✔️</span></span>            | <span data-ttu-id="9d793-164">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-164">✔️</span></span>    |
| <span data-ttu-id="9d793-165">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="9d793-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="9d793-166">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-166">✔️</span></span>           | <span data-ttu-id="9d793-167">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-167">✔️</span></span>            | <span data-ttu-id="9d793-168">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-168">✔️</span></span>    |
| <span data-ttu-id="9d793-169">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="9d793-169">Windows 10, Version 1607</span></span>    | <span data-ttu-id="9d793-170">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-170">✔️</span></span>           | <span data-ttu-id="9d793-171">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-171">✔️</span></span>            | <span data-ttu-id="9d793-172">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-172">✔️</span></span>    |
| <span data-ttu-id="9d793-173">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d793-173">Windows Server 2012 R2</span></span>      | <span data-ttu-id="9d793-174">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-174">✔️</span></span>           | <span data-ttu-id="9d793-175">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-175">✔️</span></span>            | <span data-ttu-id="9d793-176">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-176">✔️</span></span>    |
| <span data-ttu-id="9d793-177">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d793-177">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="9d793-178">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-178">✔️</span></span>           | <span data-ttu-id="9d793-179">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-179">✔️</span></span>            | <span data-ttu-id="9d793-180">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-180">✔️</span></span>    |
| <span data-ttu-id="9d793-181">Nano Server バージョン 1809 以上</span><span class="sxs-lookup"><span data-stu-id="9d793-181">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="9d793-182">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-182">✔️</span></span>           | <span data-ttu-id="9d793-183">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-183">✔️</span></span>            | <span data-ttu-id="9d793-184">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-184">✔️</span></span>    |
| <span data-ttu-id="9d793-185">Nano Server バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="9d793-185">Nano Server, Version 1803</span></span>   | <span data-ttu-id="9d793-186">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-186">✔️</span></span>           | <span data-ttu-id="9d793-187">✔️</span><span class="sxs-lookup"><span data-stu-id="9d793-187">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="9d793-188">サポートされていないリリース</span><span class="sxs-lookup"><span data-stu-id="9d793-188">Unsupported releases</span></span>

<span data-ttu-id="9d793-189">次のバージョンの .NET は、❌ サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="9d793-189">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="9d793-190">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="9d793-190">The downloads for these still remain published:</span></span>

- <span data-ttu-id="9d793-191">3.0</span><span class="sxs-lookup"><span data-stu-id="9d793-191">3.0</span></span>
- <span data-ttu-id="9d793-192">2.2</span><span class="sxs-lookup"><span data-stu-id="9d793-192">2.2</span></span>
- <span data-ttu-id="9d793-193">2.0</span><span class="sxs-lookup"><span data-stu-id="9d793-193">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="9d793-194">ランタイムに関する情報</span><span class="sxs-lookup"><span data-stu-id="9d793-194">Runtime information</span></span>

<span data-ttu-id="9d793-195">ランタイムは、.NET で作成されたアプリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-195">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="9d793-196">アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9d793-196">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="9d793-197">ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d793-197">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="9d793-198">Windows には、3 つの異なるランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="9d793-198">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="9d793-199">*ASP.NET Core ランタイム*</span><span class="sxs-lookup"><span data-stu-id="9d793-199">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="9d793-200">ASP.NET Core アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d793-200">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="9d793-201">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9d793-201">Includes the .NET runtime.</span></span>

<span data-ttu-id="9d793-202">*Desktop ランタイム*</span><span class="sxs-lookup"><span data-stu-id="9d793-202">*Desktop runtime*</span></span>\
<span data-ttu-id="9d793-203">Windows 用の .NET WPF と Windows フォームのデスクトップ アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d793-203">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="9d793-204">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9d793-204">Includes the .NET runtime.</span></span>

<span data-ttu-id="9d793-205">*.NET ランタイム*</span><span class="sxs-lookup"><span data-stu-id="9d793-205">*.NET runtime*</span></span>\
<span data-ttu-id="9d793-206">このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="9d793-206">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="9d793-207">.NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" と "*Desktop ランタイム*" の両方をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9d793-207">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="9d793-208">.NET ランタイムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="9d793-208">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="9d793-209">SDK に関する情報</span><span class="sxs-lookup"><span data-stu-id="9d793-209">SDK information</span></span>

<span data-ttu-id="9d793-210">SDK は、.NET アプリとライブラリを作成して公開するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-210">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="9d793-211">SDK のインストールには、次の 3 つの[ランタイム](#runtime-information)が含まれます: ASP.NET Core、Desktop、.NET。</span><span class="sxs-lookup"><span data-stu-id="9d793-211">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="9d793-212">依存関係</span><span class="sxs-lookup"><span data-stu-id="9d793-212">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="9d793-213">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="9d793-213">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="9d793-214">.NET 5.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-214">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="9d793-215">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="9d793-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9d793-216">OS</span><span class="sxs-lookup"><span data-stu-id="9d793-216">OS</span></span>                  | <span data-ttu-id="9d793-217">バージョン</span><span class="sxs-lookup"><span data-stu-id="9d793-217">Version</span></span>       | <span data-ttu-id="9d793-218">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9d793-218">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="9d793-219">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-219">Windows 10 Client</span></span>   | <span data-ttu-id="9d793-220">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="9d793-220">Version 1607+</span></span> | <span data-ttu-id="9d793-221">x64、x86、ARM64</span><span class="sxs-lookup"><span data-stu-id="9d793-221">x64, x86, ARM64</span></span> |
| <span data-ttu-id="9d793-222">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-222">Windows Client</span></span>      | <span data-ttu-id="9d793-223">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="9d793-223">7 SP1+, 8.1</span></span>   | <span data-ttu-id="9d793-224">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-224">x64, x86</span></span>        |
| <span data-ttu-id="9d793-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9d793-225">Windows Server</span></span>      | <span data-ttu-id="9d793-226">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="9d793-226">2012 R2+</span></span>      | <span data-ttu-id="9d793-227">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-227">x64, x86</span></span>        |
| <span data-ttu-id="9d793-228">Windows サーバー コア</span><span class="sxs-lookup"><span data-stu-id="9d793-228">Windows Server Core</span></span> | <span data-ttu-id="9d793-229">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="9d793-229">2012 R2+</span></span>      | <span data-ttu-id="9d793-230">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-230">x64, x86</span></span>        |
| <span data-ttu-id="9d793-231">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9d793-231">Nano Server</span></span>         | <span data-ttu-id="9d793-232">バージョン 1809+</span><span class="sxs-lookup"><span data-stu-id="9d793-232">Version 1809+</span></span> | <span data-ttu-id="9d793-233">X64</span><span class="sxs-lookup"><span data-stu-id="9d793-233">x64</span></span>             |

<span data-ttu-id="9d793-234">.NET 5.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)」 (.NET 5.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-234">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="9d793-235">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9d793-235">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="9d793-236">.NET Core 3.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-236">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="9d793-237">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="9d793-237">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9d793-238">OS</span><span class="sxs-lookup"><span data-stu-id="9d793-238">OS</span></span>                            | <span data-ttu-id="9d793-239">バージョン</span><span class="sxs-lookup"><span data-stu-id="9d793-239">Version</span></span>                        | <span data-ttu-id="9d793-240">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9d793-240">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9d793-241">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-241">Windows Client</span></span>                | <span data-ttu-id="9d793-242">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="9d793-242">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9d793-243">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-243">x64, x86</span></span>        |
| <span data-ttu-id="9d793-244">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-244">Windows 10 Client</span></span>             | <span data-ttu-id="9d793-245">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="9d793-245">Version 1607+</span></span>                  | <span data-ttu-id="9d793-246">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-246">x64, x86</span></span>        |
| <span data-ttu-id="9d793-247">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9d793-247">Windows Server</span></span>                | <span data-ttu-id="9d793-248">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="9d793-248">2012 R2+</span></span>                       | <span data-ttu-id="9d793-249">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-249">x64, x86</span></span>        |
| <span data-ttu-id="9d793-250">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9d793-250">Nano Server</span></span>                   | <span data-ttu-id="9d793-251">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="9d793-251">Version 1803+</span></span>                  | <span data-ttu-id="9d793-252">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="9d793-252">x64, ARM32</span></span>      |

<span data-ttu-id="9d793-253">.NET Core 3.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)」(.NET Core 3.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-253">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="9d793-254">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9d793-254">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="9d793-255">" *.NET Core 3.0 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="9d793-255">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="9d793-256">.NET Core 3.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-256">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="9d793-257">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="9d793-257">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9d793-258">OS</span><span class="sxs-lookup"><span data-stu-id="9d793-258">OS</span></span>                            | <span data-ttu-id="9d793-259">バージョン</span><span class="sxs-lookup"><span data-stu-id="9d793-259">Version</span></span>                        | <span data-ttu-id="9d793-260">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9d793-260">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9d793-261">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-261">Windows Client</span></span>                | <span data-ttu-id="9d793-262">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="9d793-262">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9d793-263">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-263">x64, x86</span></span>        |
| <span data-ttu-id="9d793-264">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-264">Windows 10 Client</span></span>             | <span data-ttu-id="9d793-265">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="9d793-265">Version 1607+</span></span>                  | <span data-ttu-id="9d793-266">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-266">x64, x86</span></span>        |
| <span data-ttu-id="9d793-267">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9d793-267">Windows Server</span></span>                | <span data-ttu-id="9d793-268">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="9d793-268">2012 R2+</span></span>                       | <span data-ttu-id="9d793-269">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-269">x64, x86</span></span>        |
| <span data-ttu-id="9d793-270">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9d793-270">Nano Server</span></span>                   | <span data-ttu-id="9d793-271">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="9d793-271">Version 1803+</span></span>                  | <span data-ttu-id="9d793-272">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="9d793-272">x64, ARM32</span></span>      |

<span data-ttu-id="9d793-273">.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)」(.NET Core 3.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-273">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="9d793-274">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="9d793-274">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="9d793-275">" *.NET Core 2.2 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="9d793-275">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="9d793-276">.NET Core 2.2 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-276">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="9d793-277">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="9d793-277">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9d793-278">OS</span><span class="sxs-lookup"><span data-stu-id="9d793-278">OS</span></span>                            | <span data-ttu-id="9d793-279">バージョン</span><span class="sxs-lookup"><span data-stu-id="9d793-279">Version</span></span>                        | <span data-ttu-id="9d793-280">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9d793-280">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9d793-281">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-281">Windows Client</span></span>                | <span data-ttu-id="9d793-282">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="9d793-282">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9d793-283">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-283">x64, x86</span></span>        |
| <span data-ttu-id="9d793-284">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-284">Windows 10 Client</span></span>             | <span data-ttu-id="9d793-285">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="9d793-285">Version 1607+</span></span>                  | <span data-ttu-id="9d793-286">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-286">x64, x86</span></span>        |
| <span data-ttu-id="9d793-287">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9d793-287">Windows Server</span></span>                | <span data-ttu-id="9d793-288">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="9d793-288">2008 R2 SP1+</span></span>                   | <span data-ttu-id="9d793-289">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-289">x64, x86</span></span>        |
| <span data-ttu-id="9d793-290">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9d793-290">Nano Server</span></span>                   | <span data-ttu-id="9d793-291">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="9d793-291">Version 1803+</span></span>                   | <span data-ttu-id="9d793-292">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="9d793-292">x64, ARM32</span></span>      |

<span data-ttu-id="9d793-293">.NET Core 2.2 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)」(.NET Core 2.2 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-293">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="9d793-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d793-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="9d793-295">.NET Core 2.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-295">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="9d793-296">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="9d793-296">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="9d793-297">OS</span><span class="sxs-lookup"><span data-stu-id="9d793-297">OS</span></span>                            | <span data-ttu-id="9d793-298">バージョン</span><span class="sxs-lookup"><span data-stu-id="9d793-298">Version</span></span>                        | <span data-ttu-id="9d793-299">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9d793-299">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="9d793-300">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-300">Windows Client</span></span>                | <span data-ttu-id="9d793-301">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="9d793-301">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="9d793-302">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-302">x64, x86</span></span>        |
| <span data-ttu-id="9d793-303">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="9d793-303">Windows 10 Client</span></span>             | <span data-ttu-id="9d793-304">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="9d793-304">Version 1607+</span></span>                  | <span data-ttu-id="9d793-305">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-305">x64, x86</span></span>        |
| <span data-ttu-id="9d793-306">Windows Server</span><span class="sxs-lookup"><span data-stu-id="9d793-306">Windows Server</span></span>                | <span data-ttu-id="9d793-307">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="9d793-307">2008 R2 SP1+</span></span>                   | <span data-ttu-id="9d793-308">x64、x86</span><span class="sxs-lookup"><span data-stu-id="9d793-308">x64, x86</span></span>        |
| <span data-ttu-id="9d793-309">Nano Server</span><span class="sxs-lookup"><span data-stu-id="9d793-309">Nano Server</span></span>                   | <span data-ttu-id="9d793-310">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="9d793-310">Version 1803+</span></span>                  | <span data-ttu-id="9d793-311">x64、</span><span class="sxs-lookup"><span data-stu-id="9d793-311">x64,</span></span>            |

<span data-ttu-id="9d793-312">.NET Core 2.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)」(.NET Core 2.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-312">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="9d793-313">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d793-313">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="9d793-314">次の Windows のバージョンに .NET SDK またはランタイムをインストールする場合は、さらに依存関係が必要になります。</span><span class="sxs-lookup"><span data-stu-id="9d793-314">More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

| <span data-ttu-id="9d793-315">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="9d793-315">Operating System</span></span>         | <span data-ttu-id="9d793-316">前提条件</span><span class="sxs-lookup"><span data-stu-id="9d793-316">Prerequisites</span></span>                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| <span data-ttu-id="9d793-317">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="9d793-317">Windows 7 SP1 [ESU][esu]</span></span> | <span data-ttu-id="9d793-318">- Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="9d793-318">- Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> <br> <span data-ttu-id="9d793-319">- KB3063858 [64 ビット][kb64] / [32 ビット][kb32]</span><span class="sxs-lookup"><span data-stu-id="9d793-319">- KB3063858 [64-bit][kb64] / [32-bit][kb32]</span></span> <br> <span data-ttu-id="9d793-320">- [MicrosoftRootCertificateAuthority2011.cer](https://go.microsoft.com/fwlink/?linkid=747875&clcid=0x409) (.NET Core 2.1 のみ)</span><span class="sxs-lookup"><span data-stu-id="9d793-320">- [MicrosoftRootCertificateAuthority2011.cer](https://go.microsoft.com/fwlink/?linkid=747875&clcid=0x409) (.NET Core 2.1 only)</span></span> |
| <span data-ttu-id="9d793-321">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="9d793-321">Windows Vista SP 2</span></span>       | <span data-ttu-id="9d793-322">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="9d793-322">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="9d793-323">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="9d793-323">Windows 8.1</span></span>              | <span data-ttu-id="9d793-324">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="9d793-324">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="9d793-325">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="9d793-325">Windows Server 2008 R2</span></span>   | <span data-ttu-id="9d793-326">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="9d793-326">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="9d793-327">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d793-327">Windows Server 2012 R2</span></span>   | <span data-ttu-id="9d793-328">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="9d793-328">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |

<span data-ttu-id="9d793-329">上記の要件は、次のいずれかの dll に関するエラーが発生した場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="9d793-329">The previous requirements are also required if you receive an error related to either of the following dlls:</span></span>

- <span data-ttu-id="9d793-330">*api-ms-win-crt-runtime-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="9d793-330">*api-ms-win-crt-runtime-l1-1-0.dll*</span></span>
- <span data-ttu-id="9d793-331">*api-ms-win-cor-timezone-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="9d793-331">*api-ms-win-cor-timezone-l1-1-0.dll*</span></span>
- <span data-ttu-id="9d793-332">*hostfxr.dll*</span><span class="sxs-lookup"><span data-stu-id="9d793-332">*hostfxr.dll*</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="9d793-333">PowerShell オートメーションを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="9d793-333">Install with PowerShell automation</span></span>

<span data-ttu-id="9d793-334">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの CI 自動化および管理者以外によるインストールに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-334">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="9d793-335">スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="9d793-335">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="9d793-336">スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-336">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9d793-337">`Channel` スイッチを指定することで、特定のリリースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9d793-337">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="9d793-338">ランタイムをインストールするには、`Runtime` スイッチを含めます。</span><span class="sxs-lookup"><span data-stu-id="9d793-338">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="9d793-339">それ以外の場合は、スクリプトによって SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-339">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="9d793-340">`-Runtime` スイッチを省略して SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9d793-340">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="9d793-341">この例では、`-Channel` スイッチが `Current` に設定されているため、サポートされている最新バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-341">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="9d793-342">Visual Studio を使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="9d793-342">Install with Visual Studio</span></span>

<span data-ttu-id="9d793-343">次の表で、Visual Studio を使用して .NET アプリを開発している場合に、ターゲットの .NET SDK バージョンに基づいて最低限必要な Visual Studio のバージョンを説明しています。</span><span class="sxs-lookup"><span data-stu-id="9d793-343">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="9d793-344">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="9d793-344">.NET SDK version</span></span>      | <span data-ttu-id="9d793-345">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="9d793-345">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="9d793-346">5.0</span><span class="sxs-lookup"><span data-stu-id="9d793-346">5.0</span></span>                   | <span data-ttu-id="9d793-347">Visual Studio 2019 バージョン 16.8 以降。</span><span class="sxs-lookup"><span data-stu-id="9d793-347">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="9d793-348">3.1</span><span class="sxs-lookup"><span data-stu-id="9d793-348">3.1</span></span>                   | <span data-ttu-id="9d793-349">Visual Studio 2019 バージョン 16.4 以降。</span><span class="sxs-lookup"><span data-stu-id="9d793-349">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="9d793-350">3.0</span><span class="sxs-lookup"><span data-stu-id="9d793-350">3.0</span></span>                   | <span data-ttu-id="9d793-351">Visual Studio 2019 バージョン 16.3 以降。</span><span class="sxs-lookup"><span data-stu-id="9d793-351">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="9d793-352">2.2</span><span class="sxs-lookup"><span data-stu-id="9d793-352">2.2</span></span>                   | <span data-ttu-id="9d793-353">Visual Studio 2017 バージョン 15.9 以降。</span><span class="sxs-lookup"><span data-stu-id="9d793-353">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="9d793-354">2.1</span><span class="sxs-lookup"><span data-stu-id="9d793-354">2.1</span></span>                   | <span data-ttu-id="9d793-355">Visual Studio 2017 バージョン 15.7 以降。</span><span class="sxs-lookup"><span data-stu-id="9d793-355">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="9d793-356">Visual Studio を既にインストールしてある場合は、次の手順でバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9d793-356">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="9d793-357">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="9d793-357">Open Visual Studio.</span></span>
01. <span data-ttu-id="9d793-358">**[ヘルプ]**  >  **[Microsoft Visual Studio のバージョン情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d793-358">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="9d793-359">**[バージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="9d793-359">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="9d793-360">Visual Studio には、最新の .NET SDK とランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="9d793-360">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="9d793-361">[Visual Studio をダウンロードします](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="9d793-361">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="9d793-362">ワークロードを選択する</span><span class="sxs-lookup"><span data-stu-id="9d793-362">Select a workload</span></span>

<span data-ttu-id="9d793-363">Visual Studio をインストールまたは変更するときは、ビルドするアプリケーションの種類に応じて、次の 1 つ以上のワークロードを選択します。</span><span class="sxs-lookup"><span data-stu-id="9d793-363">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="9d793-364">**[他のツールセット]** セクションの **[.NET Core クロスプラットフォームの開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="9d793-364">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="9d793-365">**[Web クラウド]** セクションの **[ASP.NET と Web 開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="9d793-365">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9d793-366">**[Web クラウド]** セクションの **[Azure の開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="9d793-366">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="9d793-367">**[デスクトップとモバイル]** セクションの **[.NET デスクトップ開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="9d793-367">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="9d793-368">[![Windows Visual Studio 2019 と .NET Core ワークロード](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="9d793-368">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="9d793-369">Visual Studio Code と共にインストールする</span><span class="sxs-lookup"><span data-stu-id="9d793-369">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="9d793-370">Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="9d793-370">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="9d793-371">Visual Studio Code は、Windows、macOS、Linux で利用できます。</span><span class="sxs-lookup"><span data-stu-id="9d793-371">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9d793-372">Visual Studio Code には、Visual Studio のような自動化された .NET Core インストーラーは付属していませんが、.NET Core のサポートを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="9d793-372">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="9d793-373">[Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="9d793-373">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="9d793-374">[.NET Core SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="9d793-374">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="9d793-375">[Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="9d793-375">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="9d793-376">Windows インストーラー</span><span class="sxs-lookup"><span data-stu-id="9d793-376">Windows Installer</span></span>

<span data-ttu-id="9d793-377">.NET の[ダウンロード ページ](https://dotnet.microsoft.com/download/dotnet-core)には、Windows インストーラーの実行可能ファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9d793-377">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="9d793-378">Windows インストーラーを使用して .NET をインストールする場合、`DOTNETHOME_X64` および `DOTNETHOME_X86` パラメーターを設定することによってインストール パスをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="9d793-378">When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

<span data-ttu-id="9d793-379">運用環境で、または継続的インテグレーションをサポートするために .NET をサイレント インストールする場合は、次のスイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d793-379">If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:</span></span>

- `/install`\
<span data-ttu-id="9d793-380">.NET をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9d793-380">Installs .NET.</span></span>

- `/quiet`\
<span data-ttu-id="9d793-381">UI やプロンプトが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="9d793-381">Prevents any UI and prompts from displaying.</span></span>

- `norestart`\
<span data-ttu-id="9d793-382">再起動の試行を抑制します。</span><span class="sxs-lookup"><span data-stu-id="9d793-382">Suppresses any attempts to restart.</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

<span data-ttu-id="9d793-383">詳細については、「[インストーラーの標準コマンドライン オプション](/windows/win32/msi/standard-installer-command-line-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-383">For more information, see [Standard Installer Command-Line Options](/windows/win32/msi/standard-installer-command-line-options).</span></span>

> [!TIP]
> <span data-ttu-id="9d793-384">成功した場合は、インストーラーから終了コード 0 が返されます。再起動が必要であることを示す場合は、終了コード 3010 が返されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-384">The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required.</span></span> <span data-ttu-id="9d793-385">その他の値は通常、エラー コードです。</span><span class="sxs-lookup"><span data-stu-id="9d793-385">Any other value is generally an error code.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="9d793-386">手動でダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="9d793-386">Download and manually install</span></span>

<span data-ttu-id="9d793-387">.NET 用 Windows インストーラーの代わりに、SDK またはランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9d793-387">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="9d793-388">手動インストールは、通常、継続的インテグレーション テストの一環として実行されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-388">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="9d793-389">開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet-core)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9d793-389">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="9d793-390">.NET SDK と .NET ランタイムはどちらも、ダウンロード後に手動でインストールできます。</span><span class="sxs-lookup"><span data-stu-id="9d793-390">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="9d793-391">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9d793-391">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="9d793-392">まず、次のいずれかのサイトから SDK またはランタイムのバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9d793-392">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="9d793-393">.NET 5.0 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="9d793-393">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="9d793-394">.NET Core 3.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="9d793-394">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="9d793-395">.NET Core 2.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="9d793-395">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="9d793-396">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="9d793-396">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="9d793-397">.NET を抽出するためのディレクトリを作成します (`%USERPROFILE%\dotnet` など)。</span><span class="sxs-lookup"><span data-stu-id="9d793-397">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="9d793-398">次に、ダウンロードした zip ファイルをそのディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="9d793-398">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="9d793-399">既定では、この方法でインストールされた .NET は、.NET CLI コマンドおよびアプリから使用されないため、使用することを明示的に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d793-399">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="9d793-400">これを行うには、アプリケーションの起動に使用する環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="9d793-400">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="9d793-401">この方法では、複数のバージョンを別々の場所にインストールして、その場所を参照する環境変数を使ってアプリケーションを実行することで、アプリケーションによって使用されるインストール場所を明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="9d793-401">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="9d793-402">`DOTNET_MULTILEVEL_LOOKUP` が `0` に設定されている場合、.NET により、グローバルにインストールされている .NET のバージョンはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-402">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="9d793-403">アプリケーションを実行するための最適なフレームワークを選択するときに、.NET によりグローバル インストールの既定の場所が考慮されるようにするには、その環境設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="9d793-403">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="9d793-404">通常、既定値は `C:\Program Files\dotnet` です。インストーラーによってここに .NET がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="9d793-404">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="9d793-405">Docker</span><span class="sxs-lookup"><span data-stu-id="9d793-405">Docker</span></span>

<span data-ttu-id="9d793-406">コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。</span><span class="sxs-lookup"><span data-stu-id="9d793-406">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="9d793-407">同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d793-407">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="9d793-408">.NET は Docker コンテナー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="9d793-408">.NET can run in a Docker container.</span></span> <span data-ttu-id="9d793-409">公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet)で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="9d793-409">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="9d793-410">各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9d793-410">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="9d793-411">Microsoft は、特定のシナリオに対応したイメージを用意しています。</span><span class="sxs-lookup"><span data-stu-id="9d793-411">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="9d793-412">たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9d793-412">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="9d793-413">Docker コンテナー内で .NET を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d793-413">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9d793-414">次のステップ</span><span class="sxs-lookup"><span data-stu-id="9d793-414">Next steps</span></span>

- <span data-ttu-id="9d793-415">[.NET が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="9d793-415">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="9d793-416">[チュートリアル: Hello World チュートリアル](../tutorials/with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9d793-416">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="9d793-417">[チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="9d793-417">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="9d793-418">[チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="9d793-418">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/en-us/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/en-us/download/details.aspx?id=47409
