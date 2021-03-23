---
title: Windows に .NET をインストールする
description: .NET をインストールできる Windows のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9b0c5c2ea26546a142029b730dfd38923231bae4
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873745"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="163e5-103">Windows に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="163e5-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

<span data-ttu-id="163e5-107">この記事では、Windows に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="163e5-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="163e5-108">.NET は、ランタイムと SDK で構成されています。</span><span class="sxs-lookup"><span data-stu-id="163e5-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="163e5-109">ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="163e5-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="163e5-110">SDK は、.NET アプリとライブラリの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="163e5-111">.NET ランタイムは、常に SDK と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="163e5-112">.NET の最新バージョンは 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="163e5-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="163e5-113">.NET をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="163e5-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet)

## <a name="supported-releases"></a><span data-ttu-id="163e5-114">サポートされているリリース</span><span class="sxs-lookup"><span data-stu-id="163e5-114">Supported releases</span></span>

<span data-ttu-id="163e5-115">以下の表は、現在サポートされている .NET リリースと、それらがサポートされている Windows のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="163e5-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="163e5-116">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Windows のバージョンの有効期限が切れるまで](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="163e5-117">Windows 10 のバージョンのサービス終了日は、エディションごとに分かれています。</span><span class="sxs-lookup"><span data-stu-id="163e5-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="163e5-118">次の表では、**Home**、**Pro**、**Pro Education**、**Pro for Workstations** の各エディションだけが考慮されています。</span><span class="sxs-lookup"><span data-stu-id="163e5-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="163e5-119">具体的な詳細については、「[Windows ライフサイクルのファクト シート](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)」を確認してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="163e5-120">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="163e5-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="163e5-121">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="163e5-121">Operating System</span></span>            | <span data-ttu-id="163e5-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="163e5-122">.NET Core 2.1</span></span> | <span data-ttu-id="163e5-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="163e5-123">.NET Core 3.1</span></span> | <span data-ttu-id="163e5-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="163e5-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="163e5-125">Windows 10 / Windows Server バージョン 20H2</span><span class="sxs-lookup"><span data-stu-id="163e5-125">Windows 10 / Windows Server, Version 20H2</span></span>    | <span data-ttu-id="163e5-126">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-126">✔️</span></span>           | <span data-ttu-id="163e5-127">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-127">✔️</span></span>            | <span data-ttu-id="163e5-128">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-128">✔️</span></span>    |
| <span data-ttu-id="163e5-129">Windows 10 / Windows Server バージョン 2004</span><span class="sxs-lookup"><span data-stu-id="163e5-129">Windows 10 / Windows Server, Version 2004</span></span>    | <span data-ttu-id="163e5-130">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-130">✔️</span></span>           | <span data-ttu-id="163e5-131">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-131">✔️</span></span>            | <span data-ttu-id="163e5-132">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-132">✔️</span></span>    |
| <span data-ttu-id="163e5-133">Windows 10 / Windows Server バージョン 1909</span><span class="sxs-lookup"><span data-stu-id="163e5-133">Windows 10 / Windows Server, Version 1909</span></span>    | <span data-ttu-id="163e5-134">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-134">✔️</span></span>           | <span data-ttu-id="163e5-135">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-135">✔️</span></span>            | <span data-ttu-id="163e5-136">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-136">✔️</span></span>    |
| <span data-ttu-id="163e5-137">Windows 10 / Windows Server バージョン 1903</span><span class="sxs-lookup"><span data-stu-id="163e5-137">Windows 10 / Windows Server, Version 1903</span></span>    | <span data-ttu-id="163e5-138">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-138">✔️</span></span>           | <span data-ttu-id="163e5-139">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-139">✔️</span></span>            | <span data-ttu-id="163e5-140">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-140">✔️</span></span>    |
| <span data-ttu-id="163e5-141">Windows 10 バージョン 1809</span><span class="sxs-lookup"><span data-stu-id="163e5-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="163e5-142">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-142">✔️</span></span>           | <span data-ttu-id="163e5-143">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-143">✔️</span></span>            | <span data-ttu-id="163e5-144">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-144">✔️</span></span>    |
| <span data-ttu-id="163e5-145"> Windows 10 バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="163e5-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="163e5-146">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-146">✔️</span></span>           | <span data-ttu-id="163e5-147">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-147">✔️</span></span>            | <span data-ttu-id="163e5-148">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-148">✔️</span></span>    |
| <span data-ttu-id="163e5-149">Windows 10 バージョン 1709</span><span class="sxs-lookup"><span data-stu-id="163e5-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="163e5-150">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-150">✔️</span></span>           | <span data-ttu-id="163e5-151">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-151">✔️</span></span>            | <span data-ttu-id="163e5-152">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-152">✔️</span></span>    |
| <span data-ttu-id="163e5-153">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="163e5-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="163e5-154">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-154">✔️</span></span>           | <span data-ttu-id="163e5-155">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-155">✔️</span></span>            | <span data-ttu-id="163e5-156">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-156">✔️</span></span>    |
| <span data-ttu-id="163e5-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="163e5-157">Windows 8.1</span></span>                 | <span data-ttu-id="163e5-158">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-158">✔️</span></span>           | <span data-ttu-id="163e5-159">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-159">✔️</span></span>            | <span data-ttu-id="163e5-160">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-160">✔️</span></span>    |
| <span data-ttu-id="163e5-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="163e5-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="163e5-162">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-162">✔️</span></span>           | <span data-ttu-id="163e5-163">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-163">✔️</span></span>            | <span data-ttu-id="163e5-164">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-164">✔️</span></span>    |
| <span data-ttu-id="163e5-165">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="163e5-165">Windows Server 2019</span></span><br><span data-ttu-id="163e5-166">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="163e5-166">Windows Server 2016</span></span><br><span data-ttu-id="163e5-167">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="163e5-167">Windows Server 2012 R2</span></span><br>      | <span data-ttu-id="163e5-168">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-168">✔️</span></span>           | <span data-ttu-id="163e5-169">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-169">✔️</span></span>            | <span data-ttu-id="163e5-170">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-170">✔️</span></span>    |
| <span data-ttu-id="163e5-171">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="163e5-171">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="163e5-172">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-172">✔️</span></span>           | <span data-ttu-id="163e5-173">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-173">✔️</span></span>            | <span data-ttu-id="163e5-174">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-174">✔️</span></span>    |
| <span data-ttu-id="163e5-175">Nano Server バージョン 1809 以上</span><span class="sxs-lookup"><span data-stu-id="163e5-175">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="163e5-176">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-176">✔️</span></span>           | <span data-ttu-id="163e5-177">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-177">✔️</span></span>            | <span data-ttu-id="163e5-178">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-178">✔️</span></span>    |
| <span data-ttu-id="163e5-179">Nano Server バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="163e5-179">Nano Server, Version 1803</span></span>   | <span data-ttu-id="163e5-180">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-180">✔️</span></span>           | <span data-ttu-id="163e5-181">✔️</span><span class="sxs-lookup"><span data-stu-id="163e5-181">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="163e5-182">サポートされていないリリース</span><span class="sxs-lookup"><span data-stu-id="163e5-182">Unsupported releases</span></span>

<span data-ttu-id="163e5-183">次のバージョンの .NET は、❌ サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="163e5-183">The following versions of .NET are ❌ no longer supported:</span></span>

- <span data-ttu-id="163e5-184">3.0</span><span class="sxs-lookup"><span data-stu-id="163e5-184">3.0</span></span>
- <span data-ttu-id="163e5-185">2.2</span><span class="sxs-lookup"><span data-stu-id="163e5-185">2.2</span></span>
- <span data-ttu-id="163e5-186">2.0</span><span class="sxs-lookup"><span data-stu-id="163e5-186">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="163e5-187">ランタイムに関する情報</span><span class="sxs-lookup"><span data-stu-id="163e5-187">Runtime information</span></span>

<span data-ttu-id="163e5-188">ランタイムは、.NET で作成されたアプリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-188">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="163e5-189">アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="163e5-189">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="163e5-190">ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="163e5-190">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="163e5-191">Windows には、3 つの異なるランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="163e5-191">There are three different runtimes you can install on Windows:</span></span>

- <span data-ttu-id="163e5-192">*ASP.NET Core ランタイム*</span><span class="sxs-lookup"><span data-stu-id="163e5-192">*ASP.NET Core runtime*</span></span>\
  <span data-ttu-id="163e5-193">ASP.NET Core アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="163e5-193">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="163e5-194">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="163e5-194">Includes the .NET runtime.</span></span>

- <span data-ttu-id="163e5-195">*Desktop ランタイム*</span><span class="sxs-lookup"><span data-stu-id="163e5-195">*Desktop runtime*</span></span>\
  <span data-ttu-id="163e5-196">Windows 用の .NET WPF と Windows フォームのデスクトップ アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="163e5-196">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="163e5-197">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="163e5-197">Includes the .NET runtime.</span></span>

- <span data-ttu-id="163e5-198">*.NET ランタイム*</span><span class="sxs-lookup"><span data-stu-id="163e5-198">*.NET runtime*</span></span>\
  <span data-ttu-id="163e5-199">このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="163e5-199">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="163e5-200">.NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" と "*Desktop ランタイム*" の両方をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="163e5-200">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="163e5-201">.NET ランタイムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="163e5-201">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet)

## <a name="sdk-information"></a><span data-ttu-id="163e5-202">SDK に関する情報</span><span class="sxs-lookup"><span data-stu-id="163e5-202">SDK information</span></span>

<span data-ttu-id="163e5-203">SDK は、.NET アプリとライブラリを作成して公開するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-203">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="163e5-204">SDK のインストールには、次の 3 つの[ランタイム](#runtime-information)が含まれます: ASP.NET Core、Desktop、.NET。</span><span class="sxs-lookup"><span data-stu-id="163e5-204">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="163e5-205">依存関係</span><span class="sxs-lookup"><span data-stu-id="163e5-205">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="163e5-206">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="163e5-206">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="163e5-207">.NET 5.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-207">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="163e5-208">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="163e5-208">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="163e5-209">OS</span><span class="sxs-lookup"><span data-stu-id="163e5-209">OS</span></span>                  | <span data-ttu-id="163e5-210">バージョン</span><span class="sxs-lookup"><span data-stu-id="163e5-210">Version</span></span>       | <span data-ttu-id="163e5-211">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="163e5-211">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="163e5-212">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-212">Windows 10 Client</span></span>   | <span data-ttu-id="163e5-213">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="163e5-213">Version 1607+</span></span> | <span data-ttu-id="163e5-214">x64、x86、ARM64</span><span class="sxs-lookup"><span data-stu-id="163e5-214">x64, x86, ARM64</span></span> |
| <span data-ttu-id="163e5-215">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-215">Windows Client</span></span>      | <span data-ttu-id="163e5-216">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="163e5-216">7 SP1+, 8.1</span></span>   | <span data-ttu-id="163e5-217">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-217">x64, x86</span></span>        |
| <span data-ttu-id="163e5-218">Windows Server</span><span class="sxs-lookup"><span data-stu-id="163e5-218">Windows Server</span></span>      | <span data-ttu-id="163e5-219">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="163e5-219">2012 R2+</span></span>      | <span data-ttu-id="163e5-220">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-220">x64, x86</span></span>        |
| <span data-ttu-id="163e5-221">Windows サーバー コア</span><span class="sxs-lookup"><span data-stu-id="163e5-221">Windows Server Core</span></span> | <span data-ttu-id="163e5-222">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="163e5-222">2012 R2+</span></span>      | <span data-ttu-id="163e5-223">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-223">x64, x86</span></span>        |
| <span data-ttu-id="163e5-224">Nano Server</span><span class="sxs-lookup"><span data-stu-id="163e5-224">Nano Server</span></span>         | <span data-ttu-id="163e5-225">バージョン 1809+</span><span class="sxs-lookup"><span data-stu-id="163e5-225">Version 1809+</span></span> | <span data-ttu-id="163e5-226">X64</span><span class="sxs-lookup"><span data-stu-id="163e5-226">x64</span></span>             |

<span data-ttu-id="163e5-227">.NET 5.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md)」 (.NET 5.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-227">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="163e5-228">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="163e5-228">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="163e5-229">.NET Core 3.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-229">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="163e5-230">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="163e5-230">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="163e5-231">OS</span><span class="sxs-lookup"><span data-stu-id="163e5-231">OS</span></span>                            | <span data-ttu-id="163e5-232">バージョン</span><span class="sxs-lookup"><span data-stu-id="163e5-232">Version</span></span>                        | <span data-ttu-id="163e5-233">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="163e5-233">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="163e5-234">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-234">Windows Client</span></span>                | <span data-ttu-id="163e5-235">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="163e5-235">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="163e5-236">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-236">x64, x86</span></span>        |
| <span data-ttu-id="163e5-237">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-237">Windows 10 Client</span></span>             | <span data-ttu-id="163e5-238">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="163e5-238">Version 1607+</span></span>                  | <span data-ttu-id="163e5-239">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-239">x64, x86</span></span>        |
| <span data-ttu-id="163e5-240">Windows Server</span><span class="sxs-lookup"><span data-stu-id="163e5-240">Windows Server</span></span>                | <span data-ttu-id="163e5-241">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="163e5-241">2012 R2+</span></span>                       | <span data-ttu-id="163e5-242">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-242">x64, x86</span></span>        |
| <span data-ttu-id="163e5-243">Nano Server</span><span class="sxs-lookup"><span data-stu-id="163e5-243">Nano Server</span></span>                   | <span data-ttu-id="163e5-244">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="163e5-244">Version 1803+</span></span>                  | <span data-ttu-id="163e5-245">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="163e5-245">x64, ARM32</span></span>      |

<span data-ttu-id="163e5-246">.NET Core 3.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md)」(.NET Core 3.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-246">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="163e5-247">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="163e5-247">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="163e5-248">" *.NET Core 3.0 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="163e5-248">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="163e5-249">.NET Core 3.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-249">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="163e5-250">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="163e5-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="163e5-251">OS</span><span class="sxs-lookup"><span data-stu-id="163e5-251">OS</span></span>                            | <span data-ttu-id="163e5-252">バージョン</span><span class="sxs-lookup"><span data-stu-id="163e5-252">Version</span></span>                        | <span data-ttu-id="163e5-253">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="163e5-253">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="163e5-254">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-254">Windows Client</span></span>                | <span data-ttu-id="163e5-255">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="163e5-255">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="163e5-256">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-256">x64, x86</span></span>        |
| <span data-ttu-id="163e5-257">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-257">Windows 10 Client</span></span>             | <span data-ttu-id="163e5-258">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="163e5-258">Version 1607+</span></span>                  | <span data-ttu-id="163e5-259">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-259">x64, x86</span></span>        |
| <span data-ttu-id="163e5-260">Windows Server</span><span class="sxs-lookup"><span data-stu-id="163e5-260">Windows Server</span></span>                | <span data-ttu-id="163e5-261">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="163e5-261">2012 R2+</span></span>                       | <span data-ttu-id="163e5-262">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-262">x64, x86</span></span>        |
| <span data-ttu-id="163e5-263">Nano Server</span><span class="sxs-lookup"><span data-stu-id="163e5-263">Nano Server</span></span>                   | <span data-ttu-id="163e5-264">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="163e5-264">Version 1803+</span></span>                  | <span data-ttu-id="163e5-265">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="163e5-265">x64, ARM32</span></span>      |

<span data-ttu-id="163e5-266">.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md)」(.NET Core 3.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-266">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="163e5-267">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="163e5-267">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="163e5-268">" *.NET Core 2.2 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="163e5-268">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="163e5-269">.NET Core 2.2 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-269">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="163e5-270">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="163e5-270">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="163e5-271">OS</span><span class="sxs-lookup"><span data-stu-id="163e5-271">OS</span></span>                            | <span data-ttu-id="163e5-272">バージョン</span><span class="sxs-lookup"><span data-stu-id="163e5-272">Version</span></span>                        | <span data-ttu-id="163e5-273">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="163e5-273">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="163e5-274">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-274">Windows Client</span></span>                | <span data-ttu-id="163e5-275">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="163e5-275">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="163e5-276">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-276">x64, x86</span></span>        |
| <span data-ttu-id="163e5-277">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-277">Windows 10 Client</span></span>             | <span data-ttu-id="163e5-278">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="163e5-278">Version 1607+</span></span>                  | <span data-ttu-id="163e5-279">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-279">x64, x86</span></span>        |
| <span data-ttu-id="163e5-280">Windows Server</span><span class="sxs-lookup"><span data-stu-id="163e5-280">Windows Server</span></span>                | <span data-ttu-id="163e5-281">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="163e5-281">2008 R2 SP1+</span></span>                   | <span data-ttu-id="163e5-282">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-282">x64, x86</span></span>        |
| <span data-ttu-id="163e5-283">Nano Server</span><span class="sxs-lookup"><span data-stu-id="163e5-283">Nano Server</span></span>                   | <span data-ttu-id="163e5-284">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="163e5-284">Version 1803+</span></span>                   | <span data-ttu-id="163e5-285">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="163e5-285">x64, ARM32</span></span>      |

<span data-ttu-id="163e5-286">.NET Core 2.2 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md)」(.NET Core 2.2 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-286">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="163e5-287">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="163e5-287">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="163e5-288">.NET Core 2.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-288">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="163e5-289">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="163e5-289">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="163e5-290">OS</span><span class="sxs-lookup"><span data-stu-id="163e5-290">OS</span></span>                            | <span data-ttu-id="163e5-291">バージョン</span><span class="sxs-lookup"><span data-stu-id="163e5-291">Version</span></span>                        | <span data-ttu-id="163e5-292">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="163e5-292">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="163e5-293">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-293">Windows Client</span></span>                | <span data-ttu-id="163e5-294">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="163e5-294">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="163e5-295">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-295">x64, x86</span></span>        |
| <span data-ttu-id="163e5-296">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="163e5-296">Windows 10 Client</span></span>             | <span data-ttu-id="163e5-297">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="163e5-297">Version 1607+</span></span>                  | <span data-ttu-id="163e5-298">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-298">x64, x86</span></span>        |
| <span data-ttu-id="163e5-299">Windows Server</span><span class="sxs-lookup"><span data-stu-id="163e5-299">Windows Server</span></span>                | <span data-ttu-id="163e5-300">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="163e5-300">2008 R2 SP1+</span></span>                   | <span data-ttu-id="163e5-301">x64、x86</span><span class="sxs-lookup"><span data-stu-id="163e5-301">x64, x86</span></span>        |
| <span data-ttu-id="163e5-302">Nano Server</span><span class="sxs-lookup"><span data-stu-id="163e5-302">Nano Server</span></span>                   | <span data-ttu-id="163e5-303">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="163e5-303">Version 1803+</span></span>                  | <span data-ttu-id="163e5-304">x64、</span><span class="sxs-lookup"><span data-stu-id="163e5-304">x64,</span></span>            |

<span data-ttu-id="163e5-305">.NET Core 2.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md)」(.NET Core 2.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-305">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md).</span></span>

### <a name="offline-install-for-windows-7"></a><span data-ttu-id="163e5-306">Windows 7 用のオフライン インストール</span><span class="sxs-lookup"><span data-stu-id="163e5-306">Offline install for Windows 7</span></span>

<span data-ttu-id="163e5-307">Windows 7 で .NET Core 2.1 用のオフライン インストールを実行する場合は、まず最新の [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) がターゲット コンピューターにインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="163e5-307">When doing an offline install for .NET Core 2.1 on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="163e5-308">_certmgr.exe_ ツールを使用すると、証明書のインストールを自動化できます。これは、Visual Studio または Windows SDK から取得されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-308">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="163e5-309">.NET Core 2.1 インストーラーを実行する前に、次のコマンドを使用して証明書をインストールします。</span><span class="sxs-lookup"><span data-stu-id="163e5-309">The following command is used to install the certificate before running the .NET Core 2.1 installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

<span data-ttu-id="163e5-310">[以下の Windows 7](#additional-deps) に必要な依存関係を確認してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-310">Be sure to review the dependencies required for [Windows 7 below](#additional-deps).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="163e5-311">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="163e5-311">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="163e5-312">次の Windows のバージョンに .NET SDK またはランタイムをインストールする場合は、さらに依存関係が必要になります。</span><span class="sxs-lookup"><span data-stu-id="163e5-312">More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

| <span data-ttu-id="163e5-313">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="163e5-313">Operating System</span></span>         | <span data-ttu-id="163e5-314">前提条件</span><span class="sxs-lookup"><span data-stu-id="163e5-314">Prerequisites</span></span>                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| <span data-ttu-id="163e5-315">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="163e5-315">Windows 7 SP1 [ESU][esu]</span></span> | <span data-ttu-id="163e5-316">- Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="163e5-316">- Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> <br> <span data-ttu-id="163e5-317">- KB3063858 [64 ビット][kb64] / [32 ビット][kb32]</span><span class="sxs-lookup"><span data-stu-id="163e5-317">- KB3063858 [64-bit][kb64] / [32-bit][kb32]</span></span> <br> <span data-ttu-id="163e5-318">- [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (.NET Core 2.1 のオフライン インストーラーのみ)</span><span class="sxs-lookup"><span data-stu-id="163e5-318">- [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (.NET Core 2.1 offline installer only)</span></span> |
| <span data-ttu-id="163e5-319">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="163e5-319">Windows Vista SP 2</span></span>       | <span data-ttu-id="163e5-320">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="163e5-320">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="163e5-321">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="163e5-321">Windows 8.1</span></span>              | <span data-ttu-id="163e5-322">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="163e5-322">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="163e5-323">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="163e5-323">Windows Server 2008 R2</span></span>   | <span data-ttu-id="163e5-324">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="163e5-324">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="163e5-325">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="163e5-325">Windows Server 2012 R2</span></span>   | <span data-ttu-id="163e5-326">Microsoft Visual C++ 2015-2019 再頒布可能パッケージ [64 ビット][vcc64] / [32 ビット][vcc32]</span><span class="sxs-lookup"><span data-stu-id="163e5-326">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |

<span data-ttu-id="163e5-327">上記の要件は、次のいずれかの dll に関するエラーが発生した場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="163e5-327">The previous requirements are also required if you receive an error related to either of the following dlls:</span></span>

- <span data-ttu-id="163e5-328">*api-ms-win-crt-runtime-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="163e5-328">*api-ms-win-crt-runtime-l1-1-0.dll*</span></span>
- <span data-ttu-id="163e5-329">*api-ms-win-cor-timezone-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="163e5-329">*api-ms-win-cor-timezone-l1-1-0.dll*</span></span>
- <span data-ttu-id="163e5-330">*hostfxr.dll*</span><span class="sxs-lookup"><span data-stu-id="163e5-330">*hostfxr.dll*</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="163e5-331">PowerShell オートメーションを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="163e5-331">Install with PowerShell automation</span></span>

<span data-ttu-id="163e5-332">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの CI 自動化および管理者以外によるインストールに使用されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-332">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="163e5-333">スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="163e5-333">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="163e5-334">スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-334">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="163e5-335">`Channel` スイッチを指定することで、特定のリリースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="163e5-335">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="163e5-336">ランタイムをインストールするには、`Runtime` スイッチを含めます。</span><span class="sxs-lookup"><span data-stu-id="163e5-336">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="163e5-337">それ以外の場合は、スクリプトによって SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-337">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="163e5-338">`-Runtime` スイッチを省略して SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="163e5-338">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="163e5-339">この例では、`-Channel` スイッチが `Current` に設定されているため、サポートされている最新バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-339">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="163e5-340">Visual Studio を使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="163e5-340">Install with Visual Studio</span></span>

<span data-ttu-id="163e5-341">次の表で、Visual Studio を使用して .NET アプリを開発している場合に、ターゲットの .NET SDK バージョンに基づいて最低限必要な Visual Studio のバージョンを説明しています。</span><span class="sxs-lookup"><span data-stu-id="163e5-341">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="163e5-342">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="163e5-342">.NET SDK version</span></span>      | <span data-ttu-id="163e5-343">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="163e5-343">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="163e5-344">5.0</span><span class="sxs-lookup"><span data-stu-id="163e5-344">5.0</span></span>                   | <span data-ttu-id="163e5-345">Visual Studio 2019 バージョン 16.8 以降。</span><span class="sxs-lookup"><span data-stu-id="163e5-345">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="163e5-346">3.1</span><span class="sxs-lookup"><span data-stu-id="163e5-346">3.1</span></span>                   | <span data-ttu-id="163e5-347">Visual Studio 2019 バージョン 16.4 以降。</span><span class="sxs-lookup"><span data-stu-id="163e5-347">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="163e5-348">3.0</span><span class="sxs-lookup"><span data-stu-id="163e5-348">3.0</span></span>                   | <span data-ttu-id="163e5-349">Visual Studio 2019 バージョン 16.3 以降。</span><span class="sxs-lookup"><span data-stu-id="163e5-349">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="163e5-350">2.2</span><span class="sxs-lookup"><span data-stu-id="163e5-350">2.2</span></span>                   | <span data-ttu-id="163e5-351">Visual Studio 2017 バージョン 15.9 以降。</span><span class="sxs-lookup"><span data-stu-id="163e5-351">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="163e5-352">2.1</span><span class="sxs-lookup"><span data-stu-id="163e5-352">2.1</span></span>                   | <span data-ttu-id="163e5-353">Visual Studio 2017 バージョン 15.7 以降。</span><span class="sxs-lookup"><span data-stu-id="163e5-353">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="163e5-354">Visual Studio を既にインストールしてある場合は、次の手順でバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="163e5-354">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="163e5-355">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="163e5-355">Open Visual Studio.</span></span>
01. <span data-ttu-id="163e5-356">**[ヘルプ]**  >  **[Microsoft Visual Studio のバージョン情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="163e5-356">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="163e5-357">**[バージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="163e5-357">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="163e5-358">Visual Studio には、最新の .NET SDK とランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="163e5-358">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="163e5-359">[Visual Studio をダウンロードします](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="163e5-359">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="163e5-360">ワークロードを選択する</span><span class="sxs-lookup"><span data-stu-id="163e5-360">Select a workload</span></span>

<span data-ttu-id="163e5-361">Visual Studio をインストールまたは変更するときは、ビルドするアプリケーションの種類に応じて、次の 1 つ以上のワークロードを選択します。</span><span class="sxs-lookup"><span data-stu-id="163e5-361">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="163e5-362">**[他のツールセット]** セクションの **[.NET Core クロスプラットフォームの開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="163e5-362">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="163e5-363">**[Web クラウド]** セクションの **[ASP.NET と Web 開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="163e5-363">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="163e5-364">**[Web クラウド]** セクションの **[Azure の開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="163e5-364">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="163e5-365">**[デスクトップとモバイル]** セクションの **[.NET デスクトップ開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="163e5-365">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="163e5-366">[![Windows Visual Studio 2019 と .NET Core ワークロード](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="163e5-366">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="163e5-367">Visual Studio Code と共にインストールする</span><span class="sxs-lookup"><span data-stu-id="163e5-367">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="163e5-368">Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="163e5-368">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="163e5-369">Visual Studio Code は、Windows、macOS、Linux で利用できます。</span><span class="sxs-lookup"><span data-stu-id="163e5-369">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="163e5-370">Visual Studio Code には、Visual Studio のような自動化された .NET Core インストーラーは付属していませんが、.NET Core のサポートを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="163e5-370">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="163e5-371">[Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="163e5-371">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="163e5-372">[.NET Core SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="163e5-372">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet).</span></span>
01. <span data-ttu-id="163e5-373">[Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="163e5-373">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="163e5-374">Windows インストーラー</span><span class="sxs-lookup"><span data-stu-id="163e5-374">Windows Installer</span></span>

<span data-ttu-id="163e5-375">.NET の[ダウンロード ページ](https://dotnet.microsoft.com/download/dotnet)には、Windows インストーラーの実行可能ファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="163e5-375">The [download page](https://dotnet.microsoft.com/download/dotnet) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="163e5-376">Windows インストーラーを使用して .NET をインストールする場合、`DOTNETHOME_X64` および `DOTNETHOME_X86` パラメーターを設定することによってインストール パスをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="163e5-376">When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

<span data-ttu-id="163e5-377">運用環境で、または継続的インテグレーションをサポートするために .NET をサイレント インストールする場合は、次のスイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="163e5-377">If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:</span></span>

- `/install`\
<span data-ttu-id="163e5-378">.NET をインストールします。</span><span class="sxs-lookup"><span data-stu-id="163e5-378">Installs .NET.</span></span>

- `/quiet`\
<span data-ttu-id="163e5-379">UI やプロンプトが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="163e5-379">Prevents any UI and prompts from displaying.</span></span>

- `norestart`\
<span data-ttu-id="163e5-380">再起動の試行を抑制します。</span><span class="sxs-lookup"><span data-stu-id="163e5-380">Suppresses any attempts to restart.</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

<span data-ttu-id="163e5-381">詳細については、「[インストーラーの標準コマンドライン オプション](/windows/win32/msi/standard-installer-command-line-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-381">For more information, see [Standard Installer Command-Line Options](/windows/win32/msi/standard-installer-command-line-options).</span></span>

> [!TIP]
> <span data-ttu-id="163e5-382">成功した場合は、インストーラーから終了コード 0 が返されます。再起動が必要であることを示す場合は、終了コード 3010 が返されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-382">The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required.</span></span> <span data-ttu-id="163e5-383">その他の値は通常、エラー コードです。</span><span class="sxs-lookup"><span data-stu-id="163e5-383">Any other value is generally an error code.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="163e5-384">手動でダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="163e5-384">Download and manually install</span></span>

<span data-ttu-id="163e5-385">.NET 用 Windows インストーラーの代わりに、SDK またはランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="163e5-385">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="163e5-386">手動インストールは、通常、継続的インテグレーション テストの一環として行われます。</span><span class="sxs-lookup"><span data-stu-id="163e5-386">Manual install is usually done as part of continuous integration testing.</span></span> <span data-ttu-id="163e5-387">開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="163e5-387">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet).</span></span>

<span data-ttu-id="163e5-388">.NET SDK と .NET ランタイムはどちらも、ダウンロード後に手動でインストールできます。</span><span class="sxs-lookup"><span data-stu-id="163e5-388">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="163e5-389">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="163e5-389">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="163e5-390">まず、次のいずれかのサイトから SDK またはランタイムのバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="163e5-390">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="163e5-391">.NET 5.0 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="163e5-391">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="163e5-392">.NET Core 3.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="163e5-392">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/3.1)
- [<span data-ttu-id="163e5-393">.NET Core 2.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="163e5-393">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/2.1)
- [<span data-ttu-id="163e5-394">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="163e5-394">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet)

<span data-ttu-id="163e5-395">.NET を抽出するためのディレクトリを作成します (`%USERPROFILE%\dotnet` など)。</span><span class="sxs-lookup"><span data-stu-id="163e5-395">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="163e5-396">次に、ダウンロードした zip ファイルをそのディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="163e5-396">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="163e5-397">既定では、この方法でインストールされた .NET は、.NET CLI コマンドおよびアプリから使用されないため、使用することを明示的に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="163e5-397">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="163e5-398">これを行うには、アプリケーションの起動に使用する環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="163e5-398">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="163e5-399">この方法では、複数のバージョンを別々の場所にインストールして、その場所を参照する環境変数を使ってアプリケーションを実行することで、アプリケーションによって使用されるインストール場所を明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="163e5-399">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="163e5-400">`DOTNET_MULTILEVEL_LOOKUP` が `0` に設定されている場合、.NET により、グローバルにインストールされている .NET のバージョンはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-400">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="163e5-401">アプリケーションを実行するための最適なフレームワークを選択するときに、.NET によりグローバル インストールの既定の場所が考慮されるようにするには、その環境設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="163e5-401">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="163e5-402">通常、既定値は `C:\Program Files\dotnet` です。インストーラーによってここに .NET がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="163e5-402">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="163e5-403">Docker</span><span class="sxs-lookup"><span data-stu-id="163e5-403">Docker</span></span>

<span data-ttu-id="163e5-404">コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。</span><span class="sxs-lookup"><span data-stu-id="163e5-404">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="163e5-405">同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="163e5-405">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="163e5-406">.NET は Docker コンテナー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="163e5-406">.NET can run in a Docker container.</span></span> <span data-ttu-id="163e5-407">公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet)で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="163e5-407">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="163e5-408">各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="163e5-408">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="163e5-409">Microsoft は、特定のシナリオに対応したイメージを用意しています。</span><span class="sxs-lookup"><span data-stu-id="163e5-409">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="163e5-410">たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="163e5-410">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="163e5-411">Docker コンテナー内で .NET を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md)ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="163e5-411">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="163e5-412">次のステップ</span><span class="sxs-lookup"><span data-stu-id="163e5-412">Next steps</span></span>

- <span data-ttu-id="163e5-413">[.NET が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="163e5-413">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="163e5-414">[チュートリアル: Hello World チュートリアル](../tutorials/with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="163e5-414">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="163e5-415">[チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="163e5-415">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="163e5-416">[チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="163e5-416">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/download/details.aspx?id=47409
