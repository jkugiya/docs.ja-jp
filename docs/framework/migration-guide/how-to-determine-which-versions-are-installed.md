---
title: インストールされている .NET Framework バージョンを確認する
description: コード、regedit.exe、または PowerShell を使用して、Windows レジストリに対してクエリを実行することで、コンピューターにインストールされている .NET Framework のバージョンを検出します。
ms.date: 12/04/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining installed versions
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 817e7ad7b10e11675fb055b1243a8584196cc2b5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258625"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="daaef-103">方法: インストールされている .NET Framework バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="daaef-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="daaef-104">ユーザーはコンピューターに複数のバージョンの .NET Framework を[インストール](../install/index.md)して実行できます。</span><span class="sxs-lookup"><span data-stu-id="daaef-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="daaef-105">アプリを開発または配置する場合、どのバージョンの .NET Framework がユーザーのコンピューターにインストールされているかを確認しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="daaef-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="daaef-106">レジストリには、コンピューターにインストールされている .NET Framework のバージョンの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="daaef-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

> [!NOTE]
> <span data-ttu-id="daaef-107">この記事は .NET Framework に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="daaef-107">This article is specific to .NET Framework.</span></span> <span data-ttu-id="daaef-108">インストールされている .NET Core および .NET 5 以降の SDK とランタイムを確認するには、「[.NET が既にインストールされていることを確認する方法](../../core/install/how-to-detect-installed-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daaef-108">To determine which .NET Core and .NET 5+ SDKs and runtimes are installed, see [How to check that .NET is already installed](../../core/install/how-to-detect-installed-versions.md).</span></span>

<span data-ttu-id="daaef-109">.NET Framework は、個別にバージョン管理される 2 つの主要コンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="daaef-109">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="daaef-110">アプリに機能を提供する型やリソースのコレクションである一連のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="daaef-110">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="daaef-111">.NET Framework とアセンブリは同じバージョン番号を共有します。</span><span class="sxs-lookup"><span data-stu-id="daaef-111">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="daaef-112">たとえば、.NET Framework のバージョンには、4.5、4.6.1、および 4.7.2 が含まれます。</span><span class="sxs-lookup"><span data-stu-id="daaef-112">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="daaef-113">アプリのコードを管理および実行する共通言語ランタイム (CLR)。</span><span class="sxs-lookup"><span data-stu-id="daaef-113">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="daaef-114">1 つの CLR バージョンは、通常複数の NET Framework バージョンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="daaef-114">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="daaef-115">たとえば、CLR バージョン 4.0.30319.*xxxxx* で *xxxxx* が 42000 未満の場合、.NET Framework バージョン 4 から 4.5.2 がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="daaef-115">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="daaef-116">4\.0.30319.42000 以上の CLR バージョンでは、.NET Framework 4.6 以降の .NET Framework バージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="daaef-116">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="daaef-117">コミュニティで管理されているツールを使用して、インストールされている .NET Framework バージョンを検出できます。</span><span class="sxs-lookup"><span data-stu-id="daaef-117">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="daaef-118">.NET Framework 2.0 のコマンドライン ツール。</span><span class="sxs-lookup"><span data-stu-id="daaef-118">A .NET Framework 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="daaef-119">PowerShell 2.0 モジュール。</span><span class="sxs-lookup"><span data-stu-id="daaef-119">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="daaef-120">.NET Framework の各バージョン用にインストールされている更新プログラムの検出については、「[方法: インストールされている .NET Framework の更新プログラムを確認する](how-to-determine-which-net-framework-updates-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daaef-120">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="determine-which-net-implementation-and-version-an-app-is-running-on"></a><span data-ttu-id="daaef-121">アプリが実行されている .NET の実装とバージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="daaef-121">Determine which .NET implementation and version an app is running on</span></span>

<span data-ttu-id="daaef-122"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> プロパティを使用して、アプリが実行されている .NET の実装とバージョンを照会できます。</span><span class="sxs-lookup"><span data-stu-id="daaef-122">You can use the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property to query for which .NET implementation and version your app is running on.</span></span> <span data-ttu-id="daaef-123">アプリが .NET Framework で実行されている場合、出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="daaef-123">If the app is running on .NET Framework, the output will be similar to:</span></span>

```output
.NET Framework 4.8.4250.0
```

<span data-ttu-id="daaef-124">これに対して、アプリが .NET Core または .NET 5 以降で実行されている場合、出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="daaef-124">By comparison, if the app is running on .NET Core or .NET 5+, the output will be similar to:</span></span>

```output
.NET Core 3.1.9
.NET 5.0.0
```

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="daaef-125">.NET Framework 4.5 以降のバージョンを検出する</span><span class="sxs-lookup"><span data-stu-id="daaef-125">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="daaef-126">コンピューターにインストールされている .NET Framework (4.5 以降) のバージョンは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** のレジストリに一覧されています。</span><span class="sxs-lookup"><span data-stu-id="daaef-126">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="daaef-127">**Full** サブキーが見つからない場合、.NET Framework 4.5 以降はインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="daaef-127">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="daaef-128">レジストリ パスの **NET Framework Setup** サブキーの先頭は、ピリオドでは "*ありません*"。</span><span class="sxs-lookup"><span data-stu-id="daaef-128">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="daaef-129">レジストリの **Release** REG_DWORD の値は、インストールされている .NET Framework のバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="daaef-129">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="daaef-130">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="daaef-130">.NET Framework version</span></span> | <span data-ttu-id="daaef-131">**Release** の値</span><span class="sxs-lookup"><span data-stu-id="daaef-131">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="daaef-132">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="daaef-132">.NET Framework 4.5</span></span>     | <span data-ttu-id="daaef-133">すべての Windows オペレーティング システム:378389</span><span class="sxs-lookup"><span data-stu-id="daaef-133">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="daaef-134">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="daaef-134">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="daaef-135">Windows 8.1 および Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="daaef-135">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="daaef-136">他のすべての Windows オペレーティング システム:378758</span><span class="sxs-lookup"><span data-stu-id="daaef-136">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="daaef-137">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="daaef-137">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="daaef-138">すべての Windows オペレーティング システム:379893</span><span class="sxs-lookup"><span data-stu-id="daaef-138">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="daaef-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="daaef-139">.NET Framework 4.6</span></span>     | <span data-ttu-id="daaef-140">Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="daaef-140">On Windows 10: 393295</span></span><br /><span data-ttu-id="daaef-141">他のすべての Windows オペレーティング システム:393297</span><span class="sxs-lookup"><span data-stu-id="daaef-141">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="daaef-142">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="daaef-142">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="daaef-143">Windows 10 November Update システム:394254</span><span class="sxs-lookup"><span data-stu-id="daaef-143">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="daaef-144">他のすべての Windows オペレーティング システム (Windows 10 を含む):394271</span><span class="sxs-lookup"><span data-stu-id="daaef-144">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="daaef-145">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="daaef-145">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="daaef-146">Windows 10 Anniversary Update および Windows Server 2016 の場合:394802</span><span class="sxs-lookup"><span data-stu-id="daaef-146">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="daaef-147">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):394806</span><span class="sxs-lookup"><span data-stu-id="daaef-147">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="daaef-148">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="daaef-148">.NET Framework 4.7</span></span>     | <span data-ttu-id="daaef-149">Windows 10 Creators Update:460798</span><span class="sxs-lookup"><span data-stu-id="daaef-149">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="daaef-150">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):460805</span><span class="sxs-lookup"><span data-stu-id="daaef-150">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="daaef-151">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="daaef-151">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="daaef-152">Windows 10 Fall Creators Update および Windows Server バージョン 1709:461308</span><span class="sxs-lookup"><span data-stu-id="daaef-152">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="daaef-153">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):461310</span><span class="sxs-lookup"><span data-stu-id="daaef-153">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="daaef-154">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="daaef-154">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="daaef-155">Windows 10 April 2018 Update および Windows Server バージョン 1803:461808</span><span class="sxs-lookup"><span data-stu-id="daaef-155">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="daaef-156">Windows 10 April 2018 Update および Windows Server バージョン 1803 以外のすべての Windows オペレーティング システム:461814</span><span class="sxs-lookup"><span data-stu-id="daaef-156">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="daaef-157">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="daaef-157">.NET Framework 4.8</span></span>     | <span data-ttu-id="daaef-158">Windows 10 May 2019 Update および Windows 10 November 2019 Update:528040</span><span class="sxs-lookup"><span data-stu-id="daaef-158">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="daaef-159">On Windows 10 May 2020 Update および Windows 10 October 2020 Update: 528372</span><span class="sxs-lookup"><span data-stu-id="daaef-159">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="daaef-160">他のすべての Windows オペレーティング システム (他の Windows 10 オペレーティング システムを含む):528049</span><span class="sxs-lookup"><span data-stu-id="daaef-160">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="daaef-161">最小バージョン</span><span class="sxs-lookup"><span data-stu-id="daaef-161">Minimum version</span></span>

<span data-ttu-id="daaef-162">.NET Framework の "*最小*" バージョンが存在するかどうかを判断するには、**Release** REG_DWORD 値が次の表にある、それに対応する値以上かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="daaef-162">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="daaef-163">たとえば、アプリケーションが .NET Framework 4.8 以降のバージョンで実行されている場合、**Release** REG_DWORD の値が 528040 "*以上*" であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="daaef-163">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="daaef-164">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="daaef-164">.NET Framework version</span></span> | <span data-ttu-id="daaef-165">最小値</span><span class="sxs-lookup"><span data-stu-id="daaef-165">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="daaef-166">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="daaef-166">.NET Framework 4.5</span></span>     | <span data-ttu-id="daaef-167">378389</span><span class="sxs-lookup"><span data-stu-id="daaef-167">378389</span></span> |
| <span data-ttu-id="daaef-168">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="daaef-168">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="daaef-169">378675</span><span class="sxs-lookup"><span data-stu-id="daaef-169">378675</span></span> |
| <span data-ttu-id="daaef-170">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="daaef-170">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="daaef-171">379893</span><span class="sxs-lookup"><span data-stu-id="daaef-171">379893</span></span> |
| <span data-ttu-id="daaef-172">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="daaef-172">.NET Framework 4.6</span></span>     | <span data-ttu-id="daaef-173">393295</span><span class="sxs-lookup"><span data-stu-id="daaef-173">393295</span></span> |
| <span data-ttu-id="daaef-174">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="daaef-174">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="daaef-175">394254</span><span class="sxs-lookup"><span data-stu-id="daaef-175">394254</span></span> |
| <span data-ttu-id="daaef-176">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="daaef-176">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="daaef-177">394802</span><span class="sxs-lookup"><span data-stu-id="daaef-177">394802</span></span> |
| <span data-ttu-id="daaef-178">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="daaef-178">.NET Framework 4.7</span></span>     | <span data-ttu-id="daaef-179">460798</span><span class="sxs-lookup"><span data-stu-id="daaef-179">460798</span></span> |
| <span data-ttu-id="daaef-180">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="daaef-180">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="daaef-181">461308</span><span class="sxs-lookup"><span data-stu-id="daaef-181">461308</span></span> |
| <span data-ttu-id="daaef-182">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="daaef-182">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="daaef-183">461808</span><span class="sxs-lookup"><span data-stu-id="daaef-183">461808</span></span> |
| <span data-ttu-id="daaef-184">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="daaef-184">.NET Framework 4.8</span></span>     | <span data-ttu-id="daaef-185">528040</span><span class="sxs-lookup"><span data-stu-id="daaef-185">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="daaef-186">レジストリ エディターを使用する</span><span class="sxs-lookup"><span data-stu-id="daaef-186">Use Registry Editor</span></span>

1. <span data-ttu-id="daaef-187">**スタート** メニューの **[ファイル名を指定して実行]** を選択し、「*regedit*」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="daaef-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="daaef-188">(regedit を実行するには、管理特権が必要です。)</span><span class="sxs-lookup"><span data-stu-id="daaef-188">(You must have administrative credentials to run regedit.)</span></span>

1. <span data-ttu-id="daaef-189">レジストリ エディターで、次のサブキーを開きます。**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**。</span><span class="sxs-lookup"><span data-stu-id="daaef-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="daaef-190">**Full** サブキーが存在しない場合は、.NET Framework 4.5 以降はインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="daaef-190">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

1. <span data-ttu-id="daaef-191">**Release** という REG_DWORD のエントリを確認します。</span><span class="sxs-lookup"><span data-stu-id="daaef-191">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="daaef-192">それがある場合、.NET Framework 4.5 以降がインストールされています。</span><span class="sxs-lookup"><span data-stu-id="daaef-192">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="daaef-193">その値は、.NET Framework の特定のバージョンに対応しています。</span><span class="sxs-lookup"><span data-stu-id="daaef-193">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="daaef-194">たとえば、次の図では、**Release** エントリの値は 528040 で、これは .NET Framework 4.8 のリリース キーです。</span><span class="sxs-lookup"><span data-stu-id="daaef-194">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![.NET Framework 4.5 のレジストリ エントリ](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="daaef-196">PowerShell を使用して最小バージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="daaef-196">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="daaef-197">PowerShell コマンドを使用し、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** サブキーの **Release** エントリの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="daaef-197">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="daaef-198">次の例では、**Release** エントリの値を確認して、.NET Framework 4.6.2 以降がインストールされているかどうかを判断しています。</span><span class="sxs-lookup"><span data-stu-id="daaef-198">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="daaef-199">このコードでは、インストールされていない場合は、`True` が返され、されている場合は `False` が返されます。</span><span class="sxs-lookup"><span data-stu-id="daaef-199">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="daaef-200">コードを使用してレジストリのクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="daaef-200">Query the registry using code</span></span>

01. <span data-ttu-id="daaef-201"><xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> メソッドと <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> メソッドを使用し、Windows レジストリの **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="daaef-201">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="daaef-202">実行しているアプリが 32 ビットで、64 ビットの Windows で実行されている場合、レジストリ パスは前に示したものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="daaef-202">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="daaef-203">64 ビットのレジストリは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** サブキーで入手できます。</span><span class="sxs-lookup"><span data-stu-id="daaef-203">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="daaef-204">たとえば、.NET Framework 4.5 のレジストリ サブキーは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** になります。</span><span class="sxs-lookup"><span data-stu-id="daaef-204">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="daaef-205">**Release** REG_DWORD の値を確認して、インストールされているバージョンを判断します。</span><span class="sxs-lookup"><span data-stu-id="daaef-205">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="daaef-206">上位互換性があるかを確認するには、[.NET Framework のバージョンの表](#version_table)で示されている値以上の値があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="daaef-206">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="daaef-207">次の例では、レジストリから **Release** エントリの値を確認し、インストールされている .NET Framework 4.5 から 4.8 のバージョンを探しています。</span><span class="sxs-lookup"><span data-stu-id="daaef-207">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="daaef-208">この例では、次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="daaef-208">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="daaef-209">この例では、バージョンのチェックで推奨されている方法に従います。</span><span class="sxs-lookup"><span data-stu-id="daaef-209">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="daaef-210">**Release** エントリの値が、既知のリリース キー値 *以上* かどうかを確認しています。</span><span class="sxs-lookup"><span data-stu-id="daaef-210">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="daaef-211">最新バージョンから最も古いバージョンの順にチェックします。</span><span class="sxs-lookup"><span data-stu-id="daaef-211">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="daaef-212">.NET Framework 1.0 から 4.0 を検出する</span><span class="sxs-lookup"><span data-stu-id="daaef-212">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="daaef-213">.NET Framework 1.1 から 4.0 の各バージョンは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** のサブキーとして一覧されています。</span><span class="sxs-lookup"><span data-stu-id="daaef-213">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="daaef-214">次の表には、各 .NET Framework バージョンへのパスが一覧されています。</span><span class="sxs-lookup"><span data-stu-id="daaef-214">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="daaef-215">ほとんどのバージョンでは、`1` の **Install** REG_DWORD の値があり、このバージョンがインストールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="daaef-215">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="daaef-216">これらのサブキーには、バージョン文字列を含む **Version** REG_SZ の値もあります。</span><span class="sxs-lookup"><span data-stu-id="daaef-216">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="daaef-217">レジストリ パスの **NET Framework Setup** サブキーの先頭は、ピリオドでは "*ありません*"。</span><span class="sxs-lookup"><span data-stu-id="daaef-217">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="daaef-218">Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="daaef-218">Framework Version</span></span>  | <span data-ttu-id="daaef-219">レジストリ サブキー</span><span class="sxs-lookup"><span data-stu-id="daaef-219">Registry Subkey</span></span> | <span data-ttu-id="daaef-220">[値]</span><span class="sxs-lookup"><span data-stu-id="daaef-220">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="daaef-221">1.0</span><span class="sxs-lookup"><span data-stu-id="daaef-221">1.0</span></span>                | <span data-ttu-id="daaef-222">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span><span class="sxs-lookup"><span data-stu-id="daaef-222">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="daaef-223">**Install** REG_SZ は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="daaef-223">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="daaef-224">1.1</span><span class="sxs-lookup"><span data-stu-id="daaef-224">1.1</span></span>                | <span data-ttu-id="daaef-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="daaef-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="daaef-226">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="daaef-226">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="daaef-227">2.0</span><span class="sxs-lookup"><span data-stu-id="daaef-227">2.0</span></span>                | <span data-ttu-id="daaef-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="daaef-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="daaef-229">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="daaef-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="daaef-230">3.0</span><span class="sxs-lookup"><span data-stu-id="daaef-230">3.0</span></span>                | <span data-ttu-id="daaef-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span><span class="sxs-lookup"><span data-stu-id="daaef-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="daaef-232">**InstallSuccess** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="daaef-232">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="daaef-233">3.5</span><span class="sxs-lookup"><span data-stu-id="daaef-233">3.5</span></span>                | <span data-ttu-id="daaef-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span><span class="sxs-lookup"><span data-stu-id="daaef-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="daaef-235">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="daaef-235">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="daaef-236">4.0 Client Profile</span><span class="sxs-lookup"><span data-stu-id="daaef-236">4.0 Client Profile</span></span> | <span data-ttu-id="daaef-237">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span><span class="sxs-lookup"><span data-stu-id="daaef-237">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="daaef-238">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="daaef-238">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="daaef-239">4.0 Full Profile</span><span class="sxs-lookup"><span data-stu-id="daaef-239">4.0 Full Profile</span></span>   | <span data-ttu-id="daaef-240">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span><span class="sxs-lookup"><span data-stu-id="daaef-240">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="daaef-241">**Install** REG_DWORD は `1` と等しい</span><span class="sxs-lookup"><span data-stu-id="daaef-241">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="daaef-242">実行しているアプリが 32 ビットで、64 ビットの Windows で実行されている場合、レジストリ パスは前に示したものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="daaef-242">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="daaef-243">64 ビットのレジストリは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** サブキーで入手できます。</span><span class="sxs-lookup"><span data-stu-id="daaef-243">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="daaef-244">たとえば、.NET Framework 3.5 のレジストリ サブキーは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5** になります。</span><span class="sxs-lookup"><span data-stu-id="daaef-244">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="daaef-245">.NET Framework 1.0 サブキーへのレジストリ パスは、他のものとは異なるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="daaef-245">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="daaef-246">レジストリ エディターを使用する (古いバージョンのフレームワーク)</span><span class="sxs-lookup"><span data-stu-id="daaef-246">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="daaef-247">**スタート** メニューの **[ファイル名を指定して実行]** を選択し、「*regedit*」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="daaef-247">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="daaef-248">regedit を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="daaef-248">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="daaef-249">確認するバージョンと一致するサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="daaef-249">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="daaef-250">「[.NET Framework 1.0 から 4.0 を検出する](#detect-net-framework-10-through-40)」セクションの表を使用します。</span><span class="sxs-lookup"><span data-stu-id="daaef-250">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="daaef-251">次の図では、.NET Framework 3.5 のサブキーとその **Version** の値を示しています。</span><span class="sxs-lookup"><span data-stu-id="daaef-251">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="daaef-252">![.NET Framework 3.5 のレジストリ エントリ。](./media/net-4-and-earlier.png ".NET Framework 3.5 以前のバージョン")</span><span class="sxs-lookup"><span data-stu-id="daaef-252">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="daaef-253">コードを使用してレジストリのクエリを実行する (以前のバージョンのフレームワーク)</span><span class="sxs-lookup"><span data-stu-id="daaef-253">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="daaef-254"><xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> クラスを使用して、Windows レジストリの **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** サブキーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="daaef-254">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="daaef-255">実行しているアプリが 32 ビットで、64 ビットの Windows で実行されている場合、レジストリ パスは前に示したものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="daaef-255">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="daaef-256">64 ビットのレジストリは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** サブキーで入手できます。</span><span class="sxs-lookup"><span data-stu-id="daaef-256">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="daaef-257">たとえば、.NET Framework 3.5 のレジストリ サブキーは、**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5** になります。</span><span class="sxs-lookup"><span data-stu-id="daaef-257">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="daaef-258">次の例では、インストールされている .NET Framework のバージョン 1 から 4 が検索されています。</span><span class="sxs-lookup"><span data-stu-id="daaef-258">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="daaef-259">この例では、以下と類似した出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="daaef-259">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="daaef-260">CLR のバージョンを探す</span><span class="sxs-lookup"><span data-stu-id="daaef-260">Find CLR versions</span></span>

<span data-ttu-id="daaef-261">.NET Framework と共にインストールされる .NET Framework CLR は、個別にバージョン管理されます。</span><span class="sxs-lookup"><span data-stu-id="daaef-261">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="daaef-262">.NET Framework CLR のバージョンを検出するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="daaef-262">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="daaef-263">**Clrver.exe ツール**</span><span class="sxs-lookup"><span data-stu-id="daaef-263">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="daaef-264">[CLR バージョン ツール (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) を使用して、コンピューターにインストールされている CLR のバージョンを判断します。</span><span class="sxs-lookup"><span data-stu-id="daaef-264">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="daaef-265">[開発者向けのコマンドライン シェル](/visualstudio/ide/reference/command-prompt-powershell)を開き、「`clrver`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="daaef-265">Open a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell) and enter `clrver`.</span></span>

  <span data-ttu-id="daaef-266">出力例</span><span class="sxs-lookup"><span data-stu-id="daaef-266">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="daaef-267">**`Environment` クラス**</span><span class="sxs-lookup"><span data-stu-id="daaef-267">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="daaef-268">.NET Framework 4.5 以降のバージョンでは、CLR のバージョンの検出に <xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="daaef-268">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="daaef-269">代わりに、「[.NET Framework 4.5 以降のバージョンを検出する](#detect-net-framework-45-and-later-versions)」で説明するように、レジストリのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="daaef-269">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="daaef-270"><xref:System.Environment.Version?displayProperty=nameWithType> プロパティを照会し、<xref:System.Version> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="daaef-270">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="daaef-271">返された `System.Version` オブジェクトは、現在コードを実行しているランタイムのバージョンを示しています。</span><span class="sxs-lookup"><span data-stu-id="daaef-271">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="daaef-272">コンピューターにインストールされている可能性のある、アセンブリのバージョンやランタイムのその他のバージョンは返されません。</span><span class="sxs-lookup"><span data-stu-id="daaef-272">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="daaef-273">.NET Framework バージョン 4、4.5、4.5.1、4.5.2 の場合は、返される <xref:System.Version> オブジェクトの文字列表現は 4.0.30319.*xxxxx* という形式です。この *xxxxx* は 42000 未満になります。</span><span class="sxs-lookup"><span data-stu-id="daaef-273">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="daaef-274">.NET Framework 4.6 以降のバージョンの場合は、4.0.30319.42000 という形式です。</span><span class="sxs-lookup"><span data-stu-id="daaef-274">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="daaef-275">**Version** オブジェクトを取得したら、次のようにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="daaef-275">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="daaef-276">メジャー リリース識別子 (たとえば、バージョン 4.0 の場合の *4*) には、<xref:System.Version.Major%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="daaef-276">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="daaef-277">マイナー リリース識別子 (たとえば、バージョン 4.0 の場合の *0*) には、<xref:System.Version.Minor%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="daaef-277">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="daaef-278">バージョンの完全な文字列 (たとえば、*4.0.30319.18010*) には、<xref:System.Version.ToString%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="daaef-278">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="daaef-279">このメソッドでは、コードを実行しているランタイムのバージョンを示す値が 1 つ返されます。</span><span class="sxs-lookup"><span data-stu-id="daaef-279">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="daaef-280">コンピューターにインストールされている可能性のあるアセンブリ バージョンやその他のランタイム バージョンは返されません。</span><span class="sxs-lookup"><span data-stu-id="daaef-280">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="daaef-281">次の例では、<xref:System.Environment.Version%2A?displayProperty=nameWithType> プロパティを使用して CLR バージョンの情報を取得しています。</span><span class="sxs-lookup"><span data-stu-id="daaef-281">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="daaef-282">この例では、以下と類似した出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="daaef-282">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="daaef-283">関連項目</span><span class="sxs-lookup"><span data-stu-id="daaef-283">See also</span></span>

- [<span data-ttu-id="daaef-284">方法: インストールされている .NET Framework の更新プログラムを確認する</span><span class="sxs-lookup"><span data-stu-id="daaef-284">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="daaef-285">開発者向けの .NET Framework のインストール</span><span class="sxs-lookup"><span data-stu-id="daaef-285">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="daaef-286">.NET Framework のバージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="daaef-286">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
