---
title: macOS に .NET をインストールする
description: .NET をインストールできる macOS のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 871263b820aaf4cc04e573dd4aa3022caa401857
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506306"
---
# <a name="install-net-on-macos"></a><span data-ttu-id="932cf-103">macOS に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="932cf-103">Install .NET on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

<span data-ttu-id="932cf-107">この記事では、macOS に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="932cf-107">In this article, you'll learn how to install .NET on macOS.</span></span> <span data-ttu-id="932cf-108">.NET は、ランタイムと SDK で構成されています。</span><span class="sxs-lookup"><span data-stu-id="932cf-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="932cf-109">ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="932cf-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="932cf-110">SDK は、.NET アプリとライブラリの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="932cf-111">.NET ランタイムは、常に SDK と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="932cf-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="932cf-112">.NET の最新バージョンは 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="932cf-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="932cf-113">.NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="932cf-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="932cf-114">サポートされているリリース</span><span class="sxs-lookup"><span data-stu-id="932cf-114">Supported releases</span></span>

<span data-ttu-id="932cf-115">次の表に、現在サポートされている .NET リリースと、それらがサポートされている macOS のバージョンの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="932cf-115">The following table is a list of currently supported .NET releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="932cf-116">これらのバージョンは、いずれかのバージョンの [.NET がサポート終了に達する](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)まで、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="932cf-116">These versions remain supported either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="932cf-117">✔️ は、.NET Core のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="932cf-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="932cf-118">❌ は、.NET Core のバージョンがサポートされていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="932cf-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="932cf-119">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="932cf-119">Operating System</span></span>          | <span data-ttu-id="932cf-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="932cf-120">.NET Core 2.1</span></span> | <span data-ttu-id="932cf-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="932cf-121">.NET Core 3.1</span></span> | <span data-ttu-id="932cf-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="932cf-122">.NET 5.0</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="932cf-123">macOS 11.0 "Big Sur"</span><span class="sxs-lookup"><span data-stu-id="932cf-123">macOS 11.0 "Big Sur"</span></span>        | <span data-ttu-id="932cf-124">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="932cf-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="932cf-125">✔️ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="932cf-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="932cf-126">✔️ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="932cf-126">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="932cf-127">macOS 10.15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="932cf-127">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="932cf-128">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="932cf-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="932cf-129">✔️ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="932cf-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="932cf-130">✔️ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="932cf-130">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="932cf-131">macOS 10.14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="932cf-131">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="932cf-132">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="932cf-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="932cf-133">✔️ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="932cf-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="932cf-134">✔️ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="932cf-134">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="932cf-135">macOS 10.13 "High Sierra"</span><span class="sxs-lookup"><span data-stu-id="932cf-135">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="932cf-136">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="932cf-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="932cf-137">✔️ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="932cf-137">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="932cf-138">✔️ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="932cf-138">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="932cf-139">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="932cf-139">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="932cf-140">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="932cf-140">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="932cf-141">❌ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="932cf-141">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="932cf-142">❌ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="932cf-142">❌ 5.0 ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="932cf-143">サポートされていないリリース</span><span class="sxs-lookup"><span data-stu-id="932cf-143">Unsupported releases</span></span>

<span data-ttu-id="932cf-144">次のバージョンの .NET は、❌ サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="932cf-144">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="932cf-145">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="932cf-145">The downloads for these still remain published:</span></span>

- <span data-ttu-id="932cf-146">3.0 ([リリース ノート][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="932cf-146">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="932cf-147">2.2 ([リリース ノート][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="932cf-147">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="932cf-148">2.0 ([リリース ノート][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="932cf-148">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="932cf-149">ランタイムに関する情報</span><span class="sxs-lookup"><span data-stu-id="932cf-149">Runtime information</span></span>

<span data-ttu-id="932cf-150">ランタイムは、.NET で作成されたアプリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-150">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="932cf-151">アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="932cf-151">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="932cf-152">ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="932cf-152">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="932cf-153">macOS には、2 つの異なるランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="932cf-153">There are two different runtimes you can install on macOS:</span></span>

- <span data-ttu-id="932cf-154">*ASP.NET Core ランタイム*</span><span class="sxs-lookup"><span data-stu-id="932cf-154">*ASP.NET Core runtime*</span></span>\
  <span data-ttu-id="932cf-155">ASP.NET Core アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="932cf-155">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="932cf-156">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="932cf-156">Includes the .NET runtime.</span></span>

- <span data-ttu-id="932cf-157">*.NET ランタイム*</span><span class="sxs-lookup"><span data-stu-id="932cf-157">*.NET runtime*</span></span>\
  <span data-ttu-id="932cf-158">このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="932cf-158">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="932cf-159">.NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="932cf-159">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="932cf-160">.NET ランタイムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="932cf-160">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="932cf-161">SDK に関する情報</span><span class="sxs-lookup"><span data-stu-id="932cf-161">SDK information</span></span>

<span data-ttu-id="932cf-162">SDK は、.NET アプリとライブラリを作成して公開するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-162">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="932cf-163">SDK のインストールには、次の両方の[ランタイム](#runtime-information)が含まれます: ASP.NET Core と .NET。</span><span class="sxs-lookup"><span data-stu-id="932cf-163">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="932cf-164">依存関係</span><span class="sxs-lookup"><span data-stu-id="932cf-164">Dependencies</span></span>

<span data-ttu-id="932cf-165">.NET は、次の macOS のリリースでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="932cf-165">.NET is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="932cf-166">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="932cf-166">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="932cf-167">.NET Core のバージョン</span><span class="sxs-lookup"><span data-stu-id="932cf-167">.NET Core Version</span></span> | <span data-ttu-id="932cf-168">macOS</span><span class="sxs-lookup"><span data-stu-id="932cf-168">macOS</span></span>                 | <span data-ttu-id="932cf-169">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="932cf-169">Architectures</span></span> | <span data-ttu-id="932cf-170">詳細情報</span><span class="sxs-lookup"><span data-stu-id="932cf-170">More information</span></span>    |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="932cf-171">5.0</span><span class="sxs-lookup"><span data-stu-id="932cf-171">5.0</span></span>               | <span data-ttu-id="932cf-172">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="932cf-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="932cf-173">X64</span><span class="sxs-lookup"><span data-stu-id="932cf-173">x64</span></span> | [<span data-ttu-id="932cf-174">詳細情報</span><span class="sxs-lookup"><span data-stu-id="932cf-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| <span data-ttu-id="932cf-175">3.1</span><span class="sxs-lookup"><span data-stu-id="932cf-175">3.1</span></span>               | <span data-ttu-id="932cf-176">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="932cf-176">High Sierra (10.13+)</span></span>  | <span data-ttu-id="932cf-177">X64</span><span class="sxs-lookup"><span data-stu-id="932cf-177">x64</span></span> | [<span data-ttu-id="932cf-178">詳細情報</span><span class="sxs-lookup"><span data-stu-id="932cf-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="932cf-179">3.0</span><span class="sxs-lookup"><span data-stu-id="932cf-179">3.0</span></span>               | <span data-ttu-id="932cf-180">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="932cf-180">High Sierra (10.13+)</span></span>  | <span data-ttu-id="932cf-181">X64</span><span class="sxs-lookup"><span data-stu-id="932cf-181">x64</span></span> | [<span data-ttu-id="932cf-182">詳細情報</span><span class="sxs-lookup"><span data-stu-id="932cf-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="932cf-183">2.2</span><span class="sxs-lookup"><span data-stu-id="932cf-183">2.2</span></span>               | <span data-ttu-id="932cf-184">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="932cf-184">Sierra (10.12+)</span></span>       | <span data-ttu-id="932cf-185">X64</span><span class="sxs-lookup"><span data-stu-id="932cf-185">x64</span></span> | [<span data-ttu-id="932cf-186">詳細情報</span><span class="sxs-lookup"><span data-stu-id="932cf-186">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="932cf-187">2.1</span><span class="sxs-lookup"><span data-stu-id="932cf-187">2.1</span></span>               | <span data-ttu-id="932cf-188">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="932cf-188">Sierra (10.12+)</span></span>       | <span data-ttu-id="932cf-189">X64</span><span class="sxs-lookup"><span data-stu-id="932cf-189">x64</span></span> | [<span data-ttu-id="932cf-190">詳細情報</span><span class="sxs-lookup"><span data-stu-id="932cf-190">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="932cf-191">macOS Catalina (バージョン 10.15) 以降では、2019 年 6 月 1 日より後に作成され、Developer ID と共に配布されたすべてのソフトウェアは公証される必要があります。</span><span class="sxs-lookup"><span data-stu-id="932cf-191">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="932cf-192">この要件は、.NET ランタイム、.NET SDK、および .NET を使用して作成されたソフトウェアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-192">This requirement applies to the .NET runtime, .NET SDK, and software created with .NET.</span></span>

<span data-ttu-id="932cf-193">.NET 5.0 と .NET Core 3.1、3.0、2.1 のランタイムおよび SDK のインストーラーは、2020 年 2 月 18 日から公証されています。</span><span class="sxs-lookup"><span data-stu-id="932cf-193">The runtime and SDK installers for .NET 5.0 and .NET Core 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="932cf-194">それより前にリリースされたバージョンは、公証されていません。</span><span class="sxs-lookup"><span data-stu-id="932cf-194">Prior released versions aren't notarized.</span></span> <span data-ttu-id="932cf-195">公証されていないアプリを実行すると、次のイメージのようなエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-195">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina の公証に関するアラート](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="932cf-197">公証の強制が .NET (および .NET アプリ) に与える影響の詳細については、[macOS Catalina の公証への対応](macos-notarization-issues.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="932cf-197">For more information about how enforced-notarization affects .NET (and your .NET apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="932cf-198">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="932cf-198">libgdiplus</span></span>

<span data-ttu-id="932cf-199">*System.Drawing.Common* アセンブリを使用する .NET アプリケーションの場合は、libgdiplus をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="932cf-199">.NET applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="932cf-200">libgdiplus を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。</span><span class="sxs-lookup"><span data-stu-id="932cf-200">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="932cf-201">*brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して libgdiplus をインストールします。</span><span class="sxs-lookup"><span data-stu-id="932cf-201">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="932cf-202">インストーラーを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="932cf-202">Install with an installer</span></span>

<span data-ttu-id="932cf-203">macOS には、.NET 5.0 SDK のインストールに使用できるスタンドアロン インストーラーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="932cf-203">macOS has standalone installers that can be used to install the .NET 5.0 SDK:</span></span>

- [<span data-ttu-id="932cf-204">x64 (64 ビット) CPU</span><span class="sxs-lookup"><span data-stu-id="932cf-204">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a><span data-ttu-id="932cf-205">手動でダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="932cf-205">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="932cf-206">.NET 用 macOS インストーラーの代わりに、SDK とランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="932cf-206">As an alternative to the macOS installers for .NET, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="932cf-207">手動インストールは、通常、継続的インテグレーション テストの一環として実行されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-207">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="932cf-208">開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet-core)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="932cf-208">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="932cf-209">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="932cf-209">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="932cf-210">まず、次のいずれかのサイトから SDK またはランタイムの **バイナリ** リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="932cf-210">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="932cf-211">✔️ [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="932cf-211">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="932cf-212">✔️ [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="932cf-212">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="932cf-213">✔️ [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="932cf-213">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="932cf-214">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="932cf-214">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="932cf-215">次に、ダウンロードしたファイルを抽出し、`export` コマンドを使用して .NET で使用される変数を設定してから、.NET が PATH に含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="932cf-215">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="932cf-216">ランタイムを抽出し、.NET CLI コマンドをターミナルで使用できるようにするには、最初に .NET のバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="932cf-216">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="932cf-217">次に、ターミナルを開き、ファイルが保存されているディレクトリから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="932cf-217">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="932cf-218">アーカイブ ファイル名は、ダウンロードした内容によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="932cf-218">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="932cf-219">**次のコマンドを使用して、ダウンロードしたランタイムまたは SDK を抽出します。**</span><span class="sxs-lookup"><span data-stu-id="932cf-219">**Use the following commands to extract the runtime or SDK that you downloaded.**</span></span> <span data-ttu-id="932cf-220">必ず `DOTNET_FILE` の値を実際のファイル名に変更してください。</span><span class="sxs-lookup"><span data-stu-id="932cf-220">Remember to change the `DOTNET_FILE` value to your file name:</span></span>

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> <span data-ttu-id="932cf-221">上記の `export` コマンドを使用すると、それを実行したターミナル セッションでのみ .NET CLI コマンドを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="932cf-221">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="932cf-222">シェル プロファイルを編集して、コマンドを永続的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="932cf-222">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="932cf-223">Linux ではさまざまなシェルを使用でき、それぞれに異なるプロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="932cf-223">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="932cf-224">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="932cf-224">For example:</span></span>
>
> - <span data-ttu-id="932cf-225">**Bash シェル**: *~/.bash_profile*、 *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="932cf-225">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="932cf-226">**Korn シェル**: *~/.kshrc* または *.profile*</span><span class="sxs-lookup"><span data-stu-id="932cf-226">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="932cf-227">**Z シェル**: *~/.zshrc* または *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="932cf-227">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="932cf-228">シェルの適切なソース ファイルを編集し、既存の `PATH` ステートメントの末尾に `:$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="932cf-228">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="932cf-229">`PATH` ステートメントが含まれていない場合は、`export PATH=$PATH:$HOME/dotnet` を含む新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="932cf-229">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="932cf-230">また、ファイルの末尾に `export DOTNET_ROOT=$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="932cf-230">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="932cf-231">この方法では、別々の場所に異なるバージョンをインストールして、どのアプリケーションにどれを使用するかを明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="932cf-231">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="932cf-232">Visual Studio for Mac を使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="932cf-232">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="932cf-233">Visual Studio for Mac を使用し、 **.NET** ワークロードを選択すると、.NET SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="932cf-233">Visual Studio for Mac installs the .NET SDK when the **.NET** workload is selected.</span></span> <span data-ttu-id="932cf-234">macOS で .NET の開発を始めるには、「[Visual Studio 2019 for Mac をインストールする](/visualstudio/mac/installation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="932cf-234">To get started with .NET development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

| <span data-ttu-id="932cf-235">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="932cf-235">.NET SDK version</span></span>      | <span data-ttu-id="932cf-236">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="932cf-236">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="932cf-237">5.0</span><span class="sxs-lookup"><span data-stu-id="932cf-237">5.0</span></span>                   | <span data-ttu-id="932cf-238">Visual Studio 2019 for Mac バージョン 8.8 以降。</span><span class="sxs-lookup"><span data-stu-id="932cf-238">Visual Studio 2019 for Mac version 8.8 or higher.</span></span> |
| <span data-ttu-id="932cf-239">3.1</span><span class="sxs-lookup"><span data-stu-id="932cf-239">3.1</span></span>                   | <span data-ttu-id="932cf-240">Visual Studio 2019 for Mac バージョン 8.4 以降。</span><span class="sxs-lookup"><span data-stu-id="932cf-240">Visual Studio 2019 for Mac version 8.4 or higher.</span></span> |
| <span data-ttu-id="932cf-241">2.1</span><span class="sxs-lookup"><span data-stu-id="932cf-241">2.1</span></span>                   | <span data-ttu-id="932cf-242">Visual Studio 2019 for Mac バージョン 8.0 以降。</span><span class="sxs-lookup"><span data-stu-id="932cf-242">Visual Studio 2019 for Mac version 8.0 or higher.</span></span> |

<span data-ttu-id="932cf-243">[![macOS Visual Studio 2019 for Mac と .NET ワークロード機能](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="932cf-243">[![macOS Visual Studio 2019 for Mac with .NET workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="932cf-244">Visual Studio Code と共にインストールする</span><span class="sxs-lookup"><span data-stu-id="932cf-244">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="932cf-245">Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="932cf-245">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="932cf-246">Visual Studio Code は、Windows、macOS、Linux で利用できます。</span><span class="sxs-lookup"><span data-stu-id="932cf-246">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="932cf-247">Visual Studio Code には、Visual Studio のような自動化された .NET インストーラーは付属していませんが、.NET のサポートを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="932cf-247">While Visual Studio Code doesn't come with an automated .NET installer like Visual Studio does, adding .NET support is simple.</span></span>

01. <span data-ttu-id="932cf-248">[Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="932cf-248">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="932cf-249">[.NET SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="932cf-249">[Download and install the .NET SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="932cf-250">[Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="932cf-250">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="932cf-251">bash オートメーションを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="932cf-251">Install with bash automation</span></span>

<span data-ttu-id="932cf-252">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの自動化および管理者以外によるインストールに使用されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-252">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="932cf-253">スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="932cf-253">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="932cf-254">スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="932cf-254">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="932cf-255">`current` スイッチを指定することで、特定のリリースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="932cf-255">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="932cf-256">ランタイムをインストールするには、`runtime` スイッチを含めます。</span><span class="sxs-lookup"><span data-stu-id="932cf-256">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="932cf-257">それ以外の場合は、スクリプトによって [SDK](./windows.md) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="932cf-257">Otherwise, the script installs the [SDK](./windows.md).</span></span>

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="932cf-258">前述のコマンドにより、互換性を最大限に高めるために ASP.NET Core ランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="932cf-258">The previous command installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="932cf-259">ASP.NET Core ランタイムには、標準の .NET ランタイムも含まれています。</span><span class="sxs-lookup"><span data-stu-id="932cf-259">The ASP.NET Core runtime also includes the standard .NET runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="932cf-260">Docker</span><span class="sxs-lookup"><span data-stu-id="932cf-260">Docker</span></span>

<span data-ttu-id="932cf-261">コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。</span><span class="sxs-lookup"><span data-stu-id="932cf-261">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="932cf-262">同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="932cf-262">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="932cf-263">.NET は Docker コンテナー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="932cf-263">.NET can run in a Docker container.</span></span> <span data-ttu-id="932cf-264">公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET Core の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet/)で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="932cf-264">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet/).</span></span> <span data-ttu-id="932cf-265">各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="932cf-265">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="932cf-266">Microsoft は、特定のシナリオに対応したイメージを用意しています。</span><span class="sxs-lookup"><span data-stu-id="932cf-266">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="932cf-267">たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="932cf-267">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="932cf-268">Docker コンテナー内で .NET Core を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="932cf-268">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="932cf-269">次の手順</span><span class="sxs-lookup"><span data-stu-id="932cf-269">Next steps</span></span>

- <span data-ttu-id="932cf-270">[.NET Core が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="932cf-270">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="932cf-271">[macOS Catalina の公証に対応する](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="932cf-271">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="932cf-272">[チュートリアル: macOS での作業を始める](../tutorials/with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="932cf-272">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="932cf-273">[チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="932cf-273">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="932cf-274">[チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="932cf-274">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
