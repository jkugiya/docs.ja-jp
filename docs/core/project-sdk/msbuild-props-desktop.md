---
title: Microsoft.NET.Sdk.Desktop の MSBuild プロパティ
description: .NET デスクトップ SDK によって認識される MSBuild のプロパティと項目のリファレンス (WPF と WinForms を含む)。
ms.date: 02/04/2021
ms.topic: reference
author: adegeo
ms.author: adegeo
ms.custom: updateeachrelease
no-loc:
- App.xaml
- Application.xaml
- ApplicationDefinition
- Page
- EmbeddedResource
- Compile
- None
ms.openlocfilehash: 6d1903558dd03776a72eb6ee56ddae09fb66615b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488249"
---
# <a name="msbuild-reference-for-net-desktop-sdk-projects"></a><span data-ttu-id="f0368-103">.NET デスクトップ SDK プロジェクトの MSBuild リファレンス</span><span class="sxs-lookup"><span data-stu-id="f0368-103">MSBuild reference for .NET Desktop SDK projects</span></span>

<span data-ttu-id="f0368-104">このページは、.NET デスクトップ SDK で Windows フォーム (WinForms) および Windows Presentation Foundation (WPF) プロジェクトを構成するために使用する MSBuild のプロパティと項目についてのリファレンスです。</span><span class="sxs-lookup"><span data-stu-id="f0368-104">This page is a reference for the MSBuild properties and items that you use to configure Windows Forms (WinForms) and Windows Presentation Foundation (WPF) projects with the .NET Desktop SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="f0368-105">この記事では、デスクトップ アプリに関連する .NET SDK の MSBuild プロパティのサブセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f0368-105">This article documents a subset of the MSBuild properties for the .NET SDK as it relates to desktop apps.</span></span> <span data-ttu-id="f0368-106">.NET SDK 固有の一般的な MSBuild プロパティの一覧については、「[.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-106">For a list of common .NET SDK-specific MSBuild properties, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span> <span data-ttu-id="f0368-107">一般的な MSBuild プロパティの一覧については、「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="enable-net-desktop-sdk"></a><span data-ttu-id="f0368-108">.NET デスクトップ SDK を有効にする</span><span class="sxs-lookup"><span data-stu-id="f0368-108">Enable .NET Desktop SDK</span></span>

<span data-ttu-id="f0368-109">WinForms または WPF を使用するには、プロジェクト ファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="f0368-109">To use WinForms or WPF, configure your project file.</span></span>

### <a name="net-50"></a><span data-ttu-id="f0368-110">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f0368-110">.NET 5.0</span></span>

<span data-ttu-id="f0368-111">WinForms または WPF プロジェクトのプロジェクト ファイルで、次の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0368-111">Specify the following settings in the project file of your WinForms or WPF project:</span></span>

- <span data-ttu-id="f0368-112">.NET SDK `Microsoft.NET.Sdk` をターゲットとする。</span><span class="sxs-lookup"><span data-stu-id="f0368-112">Target the .NET SDK `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="f0368-113">詳細については、「[プロジェクト ファイル](overview.md#project-files)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-113">For more information, see [Project files](overview.md#project-files).</span></span>
- <span data-ttu-id="f0368-114">[`TargetFramework`](msbuild-props.md#targetframework) を `net5.0-windows` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-114">Set [`TargetFramework`](msbuild-props.md#targetframework) to `net5.0-windows`.</span></span>
- <span data-ttu-id="f0368-115">UI フレームワーク プロパティを 1 つ (または、必要に応じて両方) を追加する。</span><span class="sxs-lookup"><span data-stu-id="f0368-115">Add a UI framework property (or both, if necessary):</span></span>
  - <span data-ttu-id="f0368-116">WPF をインポートして使用する場合は、[`UseWPF`](#usewpf) を `true` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-116">Set [`UseWPF`](#usewpf) to `true` to import and use WPF.</span></span>
  - <span data-ttu-id="f0368-117">WinForms をインポートして使用する場合は、[`UseWindowsForms`](#usewindowsforms) を `true` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-117">Set [`UseWindowsForms`](#usewindowsforms) to `true` to import and use WinForms.</span></span>
- <span data-ttu-id="f0368-118">(省略可能) `OutputType` を `WinExe` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-118">(Optional) Set `OutputType` to `WinExe`.</span></span> <span data-ttu-id="f0368-119">これにより、ライブラリではなく、アプリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-119">This produces an app as opposed to a library.</span></span> <span data-ttu-id="f0368-120">ライブラリを生成する場合は、このプロパティを省略してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-120">To produce a library, omit this property.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

### <a name="net-core-31"></a><span data-ttu-id="f0368-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f0368-121">.NET Core 3.1</span></span>

<span data-ttu-id="f0368-122">WinForms または WPF プロジェクトのプロジェクト ファイルで、次の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0368-122">Specify the following settings in the project file of your WinForms or WPF project:</span></span>

- <span data-ttu-id="f0368-123">.NET SDK `Microsoft.NET.Sdk.WindowsDesktop` をターゲットとする。</span><span class="sxs-lookup"><span data-stu-id="f0368-123">Target the .NET SDK `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="f0368-124">詳細については、「[プロジェクト ファイル](overview.md#project-files)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-124">For more information, see [Project files](overview.md#project-files).</span></span>
- <span data-ttu-id="f0368-125">[`TargetFramework`](msbuild-props.md#targetframework) を `netcoreapp3.1` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-125">Set [`TargetFramework`](msbuild-props.md#targetframework) to `netcoreapp3.1`.</span></span>
- <span data-ttu-id="f0368-126">UI フレームワーク プロパティを 1 つ (または、必要に応じて両方) を追加する。</span><span class="sxs-lookup"><span data-stu-id="f0368-126">Add a UI framework property (or both, if necessary):</span></span>
  - <span data-ttu-id="f0368-127">WPF をインポートして使用する場合は、[`UseWPF`](#usewpf) を `true` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-127">Set [`UseWPF`](#usewpf) to `true` to import and use WPF.</span></span>
  - <span data-ttu-id="f0368-128">WinForms をインポートして使用する場合は、[`UseWindowsForms`](#usewindowsforms) を `true` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-128">Set [`UseWindowsForms`](#usewindowsforms) to `true` to import and use WinForms.</span></span>
- <span data-ttu-id="f0368-129">(省略可能) `OutputType` を `WinExe` に設定する。</span><span class="sxs-lookup"><span data-stu-id="f0368-129">(Optional) Set `OutputType` to `WinExe`.</span></span> <span data-ttu-id="f0368-130">これにより、ライブラリではなく、アプリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-130">This produces an app as opposed to a library.</span></span> <span data-ttu-id="f0368-131">ライブラリを生成する場合は、このプロパティを省略してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-131">To produce a library, omit this property.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

## <a name="wpf-default-includes-and-excludes"></a><span data-ttu-id="f0368-132">WPF に既定で含まれるものと除外されるもの</span><span class="sxs-lookup"><span data-stu-id="f0368-132">WPF default includes and excludes</span></span>

<span data-ttu-id="f0368-133">SDK プロジェクトでは、プロジェクトからファイルを暗黙的に含めるまたは除外する規則のセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="f0368-133">SDK projects define a set of rules to implicitly include or exclude files from the project.</span></span> <span data-ttu-id="f0368-134">これらの規則により、ファイルのビルド アクションも自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-134">These rules also automatically set the file's build action.</span></span> <span data-ttu-id="f0368-135">これは、既定で含めるまたは除外する規則がない古い SDK 以外の .NET Framework プロジェクトとは異なります。</span><span class="sxs-lookup"><span data-stu-id="f0368-135">This is unlike the older non-SDK .NET Framework projects, which have no default include or exclude rules.</span></span> <span data-ttu-id="f0368-136">.NET Framework プロジェクトでは、プロジェクトに含めるファイルを明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0368-136">.NET Framework projects require you to explicitly declare which files to include in the project.</span></span>

<span data-ttu-id="f0368-137">.NET プロジェクト ファイルには、ファイルを自動的に処理するための[規則の標準セット](overview.md#default-includes-and-excludes)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0368-137">.NET project files include a [standard set of rules](overview.md#default-includes-and-excludes) for automatically processing files.</span></span> <span data-ttu-id="f0368-138">WPF プロジェクトではさらに規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="f0368-138">WPF projects add additional rules.</span></span>

<span data-ttu-id="f0368-139">次の表には、[`UseWPF`](#usewpf) プロジェクト プロパティが `true` に設定されている場合に、.NET デスクトップ SDK に含まれる、および除外される要素と [glob](https://en.wikipedia.org/wiki/Glob_(programming)) が示されています。</span><span class="sxs-lookup"><span data-stu-id="f0368-139">The following table shows which elements and [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Desktop SDK when the [`UseWPF`](#usewpf) project property is set to `true`:</span></span>

| <span data-ttu-id="f0368-140">要素</span><span class="sxs-lookup"><span data-stu-id="f0368-140">Element</span></span>               | <span data-ttu-id="f0368-141">含まれる glob</span><span class="sxs-lookup"><span data-stu-id="f0368-141">Include glob</span></span>                 | <span data-ttu-id="f0368-142">除外される glob</span><span class="sxs-lookup"><span data-stu-id="f0368-142">Exclude glob</span></span>                                                                                           | <span data-ttu-id="f0368-143">glob の削除</span><span class="sxs-lookup"><span data-stu-id="f0368-143">Remove glob</span></span>  |
|-----------------------|------------------------------|--------------------------------------------------------------------|--------------|
| ApplicationDefinition | <span data-ttu-id="f0368-144">App.xaml または Application.xaml</span><span class="sxs-lookup"><span data-stu-id="f0368-144">App.xaml or Application.xaml</span></span> | <span data-ttu-id="f0368-145">該当なし</span><span class="sxs-lookup"><span data-stu-id="f0368-145">N/A</span></span>                                                                | <span data-ttu-id="f0368-146">該当なし</span><span class="sxs-lookup"><span data-stu-id="f0368-146">N/A</span></span>          |
| Page                  | <span data-ttu-id="f0368-147">\*\*/\*.xaml</span><span class="sxs-lookup"><span data-stu-id="f0368-147">\*\*/\*.xaml</span></span>                 | <span data-ttu-id="f0368-148">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f0368-148">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span><br><span data-ttu-id="f0368-149">*ApplicationDefinition* によって定義されたすべての XAML</span><span class="sxs-lookup"><span data-stu-id="f0368-149">Any XAML defined by *ApplicationDefinition*</span></span> | <span data-ttu-id="f0368-150">該当なし</span><span class="sxs-lookup"><span data-stu-id="f0368-150">N/A</span></span>          |
| None                  | <span data-ttu-id="f0368-151">該当なし</span><span class="sxs-lookup"><span data-stu-id="f0368-151">N/A</span></span>                          | <span data-ttu-id="f0368-152">該当なし</span><span class="sxs-lookup"><span data-stu-id="f0368-152">N/A</span></span>                                                                | <span data-ttu-id="f0368-153">\*\*/\*.xaml</span><span class="sxs-lookup"><span data-stu-id="f0368-153">\*\*/\*.xaml</span></span> |

<span data-ttu-id="f0368-154">以下は、すべてのプロジェクトの種類について、既定で含まれるものと除外されるものの設定です。</span><span class="sxs-lookup"><span data-stu-id="f0368-154">Here are the default include and exclude settings for all project types.</span></span> <span data-ttu-id="f0368-155">詳細については、「[既定で含まれるものと除外されるもの](overview.md#default-includes-and-excludes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-155">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

| <span data-ttu-id="f0368-156">要素</span><span class="sxs-lookup"><span data-stu-id="f0368-156">Element</span></span>           | <span data-ttu-id="f0368-157">含まれる glob</span><span class="sxs-lookup"><span data-stu-id="f0368-157">Include glob</span></span>                              | <span data-ttu-id="f0368-158">除外される glob</span><span class="sxs-lookup"><span data-stu-id="f0368-158">Exclude glob</span></span>                                                  | <span data-ttu-id="f0368-159">glob の削除</span><span class="sxs-lookup"><span data-stu-id="f0368-159">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compile           | <span data-ttu-id="f0368-160">\*\*/\*.cs; \*\*/\*.vb (またはその他の言語拡張)</span><span class="sxs-lookup"><span data-stu-id="f0368-160">\*\*/\*.cs; \*\*/\*.vb (or other language extensions)</span></span> | <span data-ttu-id="f0368-161">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f0368-161">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="f0368-162">N/A</span><span class="sxs-lookup"><span data-stu-id="f0368-162">N/A</span></span>          |
| EmbeddedResource  | <span data-ttu-id="f0368-163">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f0368-163">\*\*/\*.resx</span></span>                              | <span data-ttu-id="f0368-164">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f0368-164">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f0368-165">N/A</span><span class="sxs-lookup"><span data-stu-id="f0368-165">N/A</span></span>                      |
| None              | \*\*/\*                                   | <span data-ttu-id="f0368-166">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f0368-166">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f0368-167">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f0368-167">\*\*/\*.cs; \*\*/\*.resx</span></span> |

### <a name="errors-related-to-duplicate-items"></a><span data-ttu-id="f0368-168">"重複する" 項目に関するエラー</span><span class="sxs-lookup"><span data-stu-id="f0368-168">Errors related to "duplicate" items</span></span>

<span data-ttu-id="f0368-169">ファイルをプロジェクトに明示的に追加した場合、またはプロジェクトにファイルを自動的に含めるように XAML glob が設定されている場合は、次のいずれかのエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f0368-169">If you explicitly added files to your project, or have XAML globs to automatically include files in your project, you might get one of the following errors:</span></span>

* <span data-ttu-id="f0368-170">重複する 'ApplicationDefinition' 項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="f0368-170">Duplicate 'ApplicationDefinition' items were included.</span></span>
* <span data-ttu-id="f0368-171">重複する 'Page' 項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="f0368-171">Duplicate 'Page' items were included.</span></span>

<span data-ttu-id="f0368-172">これらのエラーは、ご自分の設定と競合する暗黙的な "*含まれる*" glob の結果です。</span><span class="sxs-lookup"><span data-stu-id="f0368-172">These errors are a result of the implicit *Include* globs conflicting with your settings.</span></span> <span data-ttu-id="f0368-173">この問題を回避するには、[`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) または [`EnableDefaultPageItems`](#enabledefaultpageitems) を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f0368-173">To work around this problem, set either [`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) or [`EnableDefaultPageItems`](#enabledefaultpageitems) to `false`.</span></span> <span data-ttu-id="f0368-174">これらの値を `false` に設定すると、プロジェクトで既定の glob を明示的に定義するか、プロジェクトに含めるファイルを明示的に定義する必要があった以前の SDK の動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="f0368-174">Setting these values to `false` reverts to the behavior of previous SDKs where you had to explicitly define the default globs in your project, or explicitly define the files to include in the project.</span></span>

<span data-ttu-id="f0368-175">[`EnableDefaultItems` プロパティ](msbuild-props.md#enabledefaultitems)を `false` に設定することにより、暗黙的な含まれるものを完全に無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0368-175">You can completely disable all implicit includes by setting the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) to `false`.</span></span>

## <a name="wpf-settings"></a><span data-ttu-id="f0368-176">WPF の設定</span><span class="sxs-lookup"><span data-stu-id="f0368-176">WPF settings</span></span>

- [<span data-ttu-id="f0368-177">UseWPF</span><span class="sxs-lookup"><span data-stu-id="f0368-177">UseWPF</span></span>](#usewpf)
- [<span data-ttu-id="f0368-178">EnableDefaultApplicationDefinition</span><span class="sxs-lookup"><span data-stu-id="f0368-178">EnableDefaultApplicationDefinition</span></span>](#enabledefaultapplicationdefinition)
- [<span data-ttu-id="f0368-179">EnableDefaultPageItems</span><span class="sxs-lookup"><span data-stu-id="f0368-179">EnableDefaultPageItems</span></span>](#enabledefaultpageitems)

<span data-ttu-id="f0368-180">WPF 固有ではないプロジェクト設定については、「[.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-180">For information about non-WPF-specific project settings, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="usewpf"></a><span data-ttu-id="f0368-181">UseWPF</span><span class="sxs-lookup"><span data-stu-id="f0368-181">UseWPF</span></span>

<span data-ttu-id="f0368-182">`UseWPF` プロパティにより、WPF ライブラリへの参照を含めるかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-182">The `UseWPF` property controls whether or not to include references to WPF libraries.</span></span> <span data-ttu-id="f0368-183">また、これにより、WPF プロジェクトと関連ファイルを正しく処理するために MSBuild パイプラインが変更されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-183">This also alters the MSBuild pipeline to correctly process a WPF project and related files.</span></span> <span data-ttu-id="f0368-184">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="f0368-184">The default value is `false`.</span></span> <span data-ttu-id="f0368-185">`UseWPF` プロパティを `true` に設定して、WPF のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f0368-185">Set the `UseWPF` property to `true` to enable WPF support.</span></span> <span data-ttu-id="f0368-186">このプロパティが有効になっている場合にのみ、Windows プラットフォームをターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0368-186">You can only target the Windows platform when this property is enabled.</span></span>

```xml
<PropertyGroup>
  <UseWPF>true</UseWPF>
</PropertyGroup>
```

<span data-ttu-id="f0368-187">このプロパティが `true` に設定されている場合は、.NET 5.0 以降のプロジェクトで [.NET デスクトップ SDK](#enable-net-desktop-sdk) が自動的にインポートされます。</span><span class="sxs-lookup"><span data-stu-id="f0368-187">When this property is set to `true`, .NET 5.0+ projects will automatically import the [.NET Desktop SDK](#enable-net-desktop-sdk).</span></span>

<span data-ttu-id="f0368-188">.NET Core 3.1 のプロジェクトの場合、このプロパティを使用するには [.NET デスクトップ SDK](#enable-net-desktop-sdk) を明示的にターゲットとする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0368-188">.NET Core 3.1 projects need to explicitly target the [.NET Desktop SDK](#enable-net-desktop-sdk) to use this property.</span></span>

### <a name="enabledefaultapplicationdefinition"></a><span data-ttu-id="f0368-189">EnableDefaultApplicationDefinition</span><span class="sxs-lookup"><span data-stu-id="f0368-189">EnableDefaultApplicationDefinition</span></span>

<span data-ttu-id="f0368-190">`EnableDefaultApplicationDefinition` プロパティにより、`ApplicationDefinition` 項目がプロジェクトに暗黙的に含まれるかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-190">The `EnableDefaultApplicationDefinition` property controls whether `ApplicationDefinition` items are implicitly included in the project.</span></span> <span data-ttu-id="f0368-191">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f0368-191">The default value is `true`.</span></span> <span data-ttu-id="f0368-192">`EnableDefaultApplicationDefinition` プロパティを `false` に設定して、暗黙的なファイルの組み込みを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f0368-192">Set the `EnableDefaultApplicationDefinition` property to `false` to disable the implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultApplicationDefinition>false</EnableDefaultApplicationDefinition>
</PropertyGroup>
```

<span data-ttu-id="f0368-193">このプロパティを使用するには、[`EnableDefaultItems` プロパティ](msbuild-props.md#enabledefaultitems)が `true` に設定されている (既定の設定) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0368-193">This property requires that the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) property is set to `true`, which is the default setting.</span></span>

### <a name="enabledefaultpageitems"></a><span data-ttu-id="f0368-194">EnableDefaultPageItems</span><span class="sxs-lookup"><span data-stu-id="f0368-194">EnableDefaultPageItems</span></span>

<span data-ttu-id="f0368-195">`EnableDefaultPageItems` プロパティにより、 _.xaml_ ファイルである `Page` 項目がプロジェクトに暗黙的に含まれるかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-195">The `EnableDefaultPageItems` property controls whether `Page` items, which are _.xaml_ files, are implicitly included in the project.</span></span> <span data-ttu-id="f0368-196">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f0368-196">The default value is `true`.</span></span> <span data-ttu-id="f0368-197">`EnableDefaultPageItems` プロパティを `false` に設定して、暗黙的なファイルの組み込みを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f0368-197">Set the `EnableDefaultPageItems` property to `false` to disable the implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultPageItems>false</EnableDefaultPageItems>
</PropertyGroup>
```

<span data-ttu-id="f0368-198">このプロパティを使用するには、[`EnableDefaultItems` プロパティ](msbuild-props.md#enabledefaultitems)が `true` に設定されている (既定の設定) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0368-198">This property requires that the [`EnableDefaultItems` property](msbuild-props.md#enabledefaultitems) property is set to `true`, which is the default setting.</span></span>

## <a name="windows-forms-settings"></a><span data-ttu-id="f0368-199">Windows フォームの設定</span><span class="sxs-lookup"><span data-stu-id="f0368-199">Windows Forms settings</span></span>

- [<span data-ttu-id="f0368-200">UseWindowsForms</span><span class="sxs-lookup"><span data-stu-id="f0368-200">UseWindowsForms</span></span>](#usewindowsforms)

<span data-ttu-id="f0368-201">WinForms 固有ではないプロジェクト プロパティについては、「[.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0368-201">For information about non-WinForms-specific project properties, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="usewindowsforms"></a><span data-ttu-id="f0368-202">UseWindowsForms</span><span class="sxs-lookup"><span data-stu-id="f0368-202">UseWindowsForms</span></span>

<span data-ttu-id="f0368-203">`UseWindowsForms` プロパティにより、Windows フォームをターゲットとするようにアプリケーションがビルドされるかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-203">The `UseWindowsForms` property controls whether or not your application is built to target Windows Forms.</span></span> <span data-ttu-id="f0368-204">このプロパティにより、Windows フォーム プロジェクトと関連ファイルを正しく処理するために MSBuild パイプラインが変更されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-204">This property alters the MSBuild pipeline to correctly process a Windows Forms project and related files.</span></span> <span data-ttu-id="f0368-205">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="f0368-205">The default value is `false`.</span></span> <span data-ttu-id="f0368-206">`UseWindowsForms` プロパティを `true` に設定して、Windows フォームのサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f0368-206">Set the `UseWindowsForms` property to `true` to enable Windows Forms support.</span></span> <span data-ttu-id="f0368-207">この設定が有効になっている場合にのみ、Windows プラットフォームをターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="f0368-207">You can only target the Windows platform when this setting is enabled.</span></span>

```xml
<PropertyGroup>
  <UseWindowsForms>true</UseWindowsForms>
</PropertyGroup>
```

<span data-ttu-id="f0368-208">このプロパティが `true` に設定されている場合は、.NET 5.0 以降のプロジェクトで [.NET デスクトップ SDK](#enable-net-desktop-sdk) が自動的にインポートされます。</span><span class="sxs-lookup"><span data-stu-id="f0368-208">When this property is set to `true`, .NET 5.0+ projects will automatically import the [.NET Desktop SDK](#enable-net-desktop-sdk).</span></span>

<span data-ttu-id="f0368-209">.NET Core 3.1 のプロジェクトの場合、このプロパティを使用するには [.NET デスクトップ SDK](#enable-net-desktop-sdk) を明示的にターゲットとする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0368-209">.NET Core 3.1 projects need to explicitly target the [.NET Desktop SDK](#enable-net-desktop-sdk) to use this property.</span></span>

## <a name="shared-settings"></a><span data-ttu-id="f0368-210">共有設定</span><span class="sxs-lookup"><span data-stu-id="f0368-210">Shared settings</span></span>

- [<span data-ttu-id="f0368-211">DisableWinExeOutputInference</span><span class="sxs-lookup"><span data-stu-id="f0368-211">DisableWinExeOutputInference</span></span>](#disablewinexeoutputinference)

### <a name="disablewinexeoutputinference"></a><span data-ttu-id="f0368-212">DisableWinExeOutputInference</span><span class="sxs-lookup"><span data-stu-id="f0368-212">DisableWinExeOutputInference</span></span>

<span data-ttu-id="f0368-213">.NET 5.0 SDK 以降に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-213">Applies to .NET 5.0 SDK and later.</span></span>

<span data-ttu-id="f0368-214">アプリで `OutputType` プロパティに対して `Exe` 値が設定されているときに、そのアプリがコンソールから実行されていない場合はコンソール ウィンドウが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-214">When an app has the `Exe` value set for the `OutputType` property, a console window is created if the app isn't running from a console.</span></span> <span data-ttu-id="f0368-215">これは通常、Windows デスクトップ アプリの望ましい動作ではありません。</span><span class="sxs-lookup"><span data-stu-id="f0368-215">This is generally not the desired behavior of a Windows Desktop app.</span></span> <span data-ttu-id="f0368-216">`WinExe` 値を使用すると、コンソール ウィンドウは作成されません。</span><span class="sxs-lookup"><span data-stu-id="f0368-216">With the `WinExe` value, a console window isn't created.</span></span> <span data-ttu-id="f0368-217">.NET 5.0 SDK 以降では、`Exe` 値が `WinExe` に自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f0368-217">Starting with the .NET 5.0 SDK, the `Exe` value is automatically transformed to `WinExe`.</span></span>

<span data-ttu-id="f0368-218">`DisableWinExeOutputInference` プロパティは、`Exe` を `WinExe` として扱う動作を元に戻します。</span><span class="sxs-lookup"><span data-stu-id="f0368-218">The `DisableWinExeOutputInference` property reverts the behavior of treating `Exe` as `WinExe`.</span></span> <span data-ttu-id="f0368-219">この値を `true` に設定して、`Exe` の `OutputType` プロパティ値の動作を復元します。</span><span class="sxs-lookup"><span data-stu-id="f0368-219">Set this value to `true` to restore the behavior of the `OutputType` property value of `Exe`.</span></span> <span data-ttu-id="f0368-220">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="f0368-220">The default value is `false`.</span></span>

```xml
<PropertyGroup>
  <DisableWinExeOutputInference>true</DisableWinExeOutputInference>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="f0368-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0368-221">See also</span></span>

- [<span data-ttu-id="f0368-222">.NET プロジェクト SDK</span><span class="sxs-lookup"><span data-stu-id="f0368-222">.NET project SDKs</span></span>](overview.md)
- [<span data-ttu-id="f0368-223">.NET SDK プロジェクトの MSBuild リファレンス</span><span class="sxs-lookup"><span data-stu-id="f0368-223">MSBuild reference for .NET SDK projects</span></span>](msbuild-props.md)
- [<span data-ttu-id="f0368-224">MSBuild スキーマ リファレンス</span><span class="sxs-lookup"><span data-stu-id="f0368-224">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="f0368-225">MSBuild の共通プロパティ</span><span class="sxs-lookup"><span data-stu-id="f0368-225">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="f0368-226">ビルドのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="f0368-226">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
