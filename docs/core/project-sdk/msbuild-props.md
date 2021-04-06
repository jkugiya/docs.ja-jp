---
title: Microsoft.NET.Sdk の MSBuild プロパティ
description: .NET SDK によって認識される MSBuild のプロパティと項目のリファレンスです。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: effcb704056f553b2986ee4a61f73c0dc58af599
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636767"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="f14e7-103">.NET SDK プロジェクトの MSBuild リファレンス</span><span class="sxs-lookup"><span data-stu-id="f14e7-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="f14e7-104">このページは、.NET プロジェクトの構成に使用できる、MSBuild のプロパティと項目のリファレンスです。</span><span class="sxs-lookup"><span data-stu-id="f14e7-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="f14e7-105">このページの編集は進行中であり、.NET SDK の便利な MSBuild プロパティがすべて記載されている訳ではありません。</span><span class="sxs-lookup"><span data-stu-id="f14e7-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="f14e7-106">一般的な MSBuild プロパティの一覧については、「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="f14e7-107">フレームワークのプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-107">Framework properties</span></span>

<span data-ttu-id="f14e7-108">このセクションでは、次の MSBuild プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-108">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="f14e7-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="f14e7-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="f14e7-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="f14e7-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="f14e7-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="f14e7-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="f14e7-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="f14e7-112">TargetFramework</span></span>

<span data-ttu-id="f14e7-113">`TargetFramework` プロパティには、アプリのターゲット フレームワーク バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-113">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="f14e7-114">有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-frameworks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="f14e7-115">詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="f14e7-116">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="f14e7-116">TargetFrameworks</span></span>

<span data-ttu-id="f14e7-117">アプリで複数のプラットフォームをターゲットにする場合は、`TargetFrameworks` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="f14e7-118">有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-frameworks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="f14e7-119">`TargetFramework` (単数形) が指定されている場合、このプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="f14e7-120">詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="f14e7-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="f14e7-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="f14e7-122">このプロパティは、`netstandard1.x` を使用するプロジェクトにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="f14e7-123">`netstandard2.x` を使用するプロジェクトには適用されません。</span><span class="sxs-lookup"><span data-stu-id="f14e7-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="f14e7-124">メタパッケージ バージョンよりも低いフレームワーク バージョンを指定する場合は、`NetStandardImplicitPackageVersion` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="f14e7-125">次の例のプロジェクト ファイルは、`netstandard1.3` をターゲットにしていますが、`NETStandard.Library` の 1.6.0 バージョンを使用しています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="assembly-info-generation-properties"></a><span data-ttu-id="f14e7-126">アセンブリ情報生成のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-126">Assembly info generation properties</span></span>

- [<span data-ttu-id="f14e7-127">GenerateAssemblyCompanyAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-127">GenerateAssemblyCompanyAttribute</span></span>](#generateassemblycompanyattribute)
- [<span data-ttu-id="f14e7-128">GenerateAssemblyConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-128">GenerateAssemblyConfigurationAttribute</span></span>](#generateassemblyconfigurationattribute)
- [<span data-ttu-id="f14e7-129">GenerateAssemblyCopyrightAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-129">GenerateAssemblyCopyrightAttribute</span></span>](#generateassemblycopyrightattribute)
- [<span data-ttu-id="f14e7-130">GenerateAssemblyDescriptionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-130">GenerateAssemblyDescriptionAttribute</span></span>](#generateassemblydescriptionattribute)
- [<span data-ttu-id="f14e7-131">GenerateAssemblyFileVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-131">GenerateAssemblyFileVersionAttribute</span></span>](#generateassemblyfileversionattribute)
- [<span data-ttu-id="f14e7-132">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="f14e7-132">GenerateAssemblyInfo</span></span>](#generateassemblyinfo)
- [<span data-ttu-id="f14e7-133">GenerateAssemblyInformationalVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-133">GenerateAssemblyInformationalVersionAttribute</span></span>](#generateassemblyinformationalversionattribute)
- [<span data-ttu-id="f14e7-134">GenerateAssemblyProductAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-134">GenerateAssemblyProductAttribute</span></span>](#generateassemblyproductattribute)
- [<span data-ttu-id="f14e7-135">GenerateAssemblyTitleAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-135">GenerateAssemblyTitleAttribute</span></span>](#generateassemblytitleattribute)
- [<span data-ttu-id="f14e7-136">GenerateAssemblyVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-136">GenerateAssemblyVersionAttribute</span></span>](#generateassemblyversionattribute)
- [<span data-ttu-id="f14e7-137">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="f14e7-137">GeneratedAssemblyInfoFile</span></span>](#generatedassemblyinfofile)
- [<span data-ttu-id="f14e7-138">GenerateNeutralResourcesLanguageAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-138">GenerateNeutralResourcesLanguageAttribute</span></span>](#generateneutralresourceslanguageattribute)

### <a name="generateassemblycompanyattribute"></a><span data-ttu-id="f14e7-139">GenerateAssemblyCompanyAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-139">GenerateAssemblyCompanyAttribute</span></span>

<span data-ttu-id="f14e7-140">このプロパティは、`Company` プロパティがアセンブリの <xref:System.Reflection.AssemblyCompanyAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-140">This property controls whether or not the `Company` property generates the <xref:System.Reflection.AssemblyCompanyAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-141">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-141">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyCompanyAttribute>false</GenerateAssemblyCompanyAttribute>
</PropertyGroup>
```

### <a name="generateassemblyconfigurationattribute"></a><span data-ttu-id="f14e7-142">GenerateAssemblyConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-142">GenerateAssemblyConfigurationAttribute</span></span>

<span data-ttu-id="f14e7-143">このプロパティは、`Configuration` プロパティがアセンブリの <xref:System.Reflection.AssemblyConfigurationAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-143">This property controls whether or not the `Configuration` property generates the <xref:System.Reflection.AssemblyConfigurationAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-144">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-144">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyConfigurationAttribute>false</GenerateAssemblyConfigurationAttribute>
</PropertyGroup>
```

### <a name="generateassemblycopyrightattribute"></a><span data-ttu-id="f14e7-145">GenerateAssemblyCopyrightAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-145">GenerateAssemblyCopyrightAttribute</span></span>

<span data-ttu-id="f14e7-146">このプロパティは、`Copyright` プロパティがアセンブリの <xref:System.Reflection.AssemblyCopyrightAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-146">This property controls whether or not the `Copyright` property generates the <xref:System.Reflection.AssemblyCopyrightAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-147">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-147">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyCopyrightAttribute>false</GenerateAssemblyCopyrightAttribute>
</PropertyGroup>
```

### <a name="generateassemblydescriptionattribute"></a><span data-ttu-id="f14e7-148">GenerateAssemblyDescriptionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-148">GenerateAssemblyDescriptionAttribute</span></span>

<span data-ttu-id="f14e7-149">このプロパティは、`Description` プロパティがアセンブリの <xref:System.Reflection.AssemblyDescriptionAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-149">This property controls whether or not the `Description` property generates the <xref:System.Reflection.AssemblyDescriptionAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-150">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-150">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyDescriptionAttribute>false</GenerateAssemblyDescriptionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyfileversionattribute"></a><span data-ttu-id="f14e7-151">GenerateAssemblyFileVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-151">GenerateAssemblyFileVersionAttribute</span></span>

<span data-ttu-id="f14e7-152">このプロパティは、`FileVersion` プロパティがアセンブリの <xref:System.Reflection.AssemblyFileVersionAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-152">This property controls whether or not the `FileVersion` property generates the <xref:System.Reflection.AssemblyFileVersionAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-153">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-153">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyFileVersionAttribute>false</GenerateAssemblyFileVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyinfo"></a><span data-ttu-id="f14e7-154">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="f14e7-154">GenerateAssemblyInfo</span></span>

<span data-ttu-id="f14e7-155">プロジェクトの `AssemblyInfo` 属性の生成を制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-155">Controls `AssemblyInfo` attribute generation for the project.</span></span> <span data-ttu-id="f14e7-156">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-156">The default value is `true`.</span></span> <span data-ttu-id="f14e7-157">ファイルの生成を無効にするには、`false` を使用します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-157">Use `false` to disable generation of the file:</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
</PropertyGroup>
```

<span data-ttu-id="f14e7-158">[GeneratedAssemblyInfoFile](#generatedassemblyinfofile) 設定は、生成されるファイルの名前を制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-158">The [GeneratedAssemblyInfoFile](#generatedassemblyinfofile) setting controls the name of the generated file.</span></span>

<span data-ttu-id="f14e7-159">`GenerateAssemblyInfo` 値が `true` の場合、プロジェクトのプロパティは `AssemblyInfo` 属性に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-159">When the `GenerateAssemblyInfo` value is `true`, project properties are transformed into `AssemblyInfo` attributes.</span></span> <span data-ttu-id="f14e7-160">次の表に、属性を生成するプロジェクトのプロパティとその生成を無効にできるプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-160">The following table lists the project properties that generate the attributes, and the properties that can disable that generation:</span></span>

| <span data-ttu-id="f14e7-161">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-161">Property</span></span>               | <span data-ttu-id="f14e7-162">属性</span><span class="sxs-lookup"><span data-stu-id="f14e7-162">Attribute</span></span>                                                      | <span data-ttu-id="f14e7-163">無効にするプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-163">Property to disable</span></span>                                                                               |
|------------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| `Company`              | <xref:System.Reflection.AssemblyCompanyAttribute>              | [`GenerateAssemblyCompanyAttribute`](#generateassemblycompanyattribute)                           |
| `Configuration`        | <xref:System.Reflection.AssemblyConfigurationAttribute>        | [`GenerateAssemblyConfigurationAttribute`](#generateassemblyconfigurationattribute)               |
| `Copyright`            | <xref:System.Reflection.AssemblyCopyrightAttribute>            | [`GenerateAssemblyCopyrightAttribute`](#generateassemblycopyrightattribute)                       |
| `Description`          | <xref:System.Reflection.AssemblyDescriptionAttribute>          | [`GenerateAssemblyDescriptionAttribute`](#generateassemblydescriptionattribute)                   |
| `FileVersion`          | <xref:System.Reflection.AssemblyFileVersionAttribute>          | [`GenerateAssemblyFileVersionAttribute`](#generateassemblyfileversionattribute)                   |
| `InformationalVersion` | <xref:System.Reflection.AssemblyInformationalVersionAttribute> | [`GenerateAssemblyInformationalVersionAttribute`](#generateassemblyinformationalversionattribute) |
| `Product`              | <xref:System.Reflection.AssemblyProductAttribute>              | [`GenerateAssemblyProductAttribute`](#generateassemblyproductattribute)                           |
| `AssemblyTitle`        | <xref:System.Reflection.AssemblyTitleAttribute>                | [`GenerateAssemblyTitleAttribute`](#generateassemblytitleattribute)                               |
| `AssemblyVersion`      | <xref:System.Reflection.AssemblyVersionAttribute>              | [`GenerateAssemblyVersionAttribute`](#generateassemblyversionattribute)                           |
| `NeutralLanguage`      | <xref:System.Resources.NeutralResourcesLanguageAttribute>      | [`GenerateNeutralResourcesLanguageAttribute`](#generateneutralresourceslanguageattribute)         |

<span data-ttu-id="f14e7-164">これらの設定に関する注意事項:</span><span class="sxs-lookup"><span data-stu-id="f14e7-164">Notes about these settings:</span></span>

- <span data-ttu-id="f14e7-165">`AssemblyVersion` と `FileVersion` の既定値は、サフィックスのない `$(Version)` の値です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-165">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="f14e7-166">たとえば、`$(Version)` が `1.2.3-beta.4` の場合、値は `1.2.3` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-166">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="f14e7-167">`InformationalVersion` の既定値は、`$(Version)` の値です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-167">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="f14e7-168">`$(SourceRevisionId)` プロパティが存在する場合は、それが `InformationalVersion` の後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-168">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="f14e7-169">`IncludeSourceRevisionInInformationalVersion` を使用して、この動作を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-169">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="f14e7-170">NuGet メタデータには、`Copyright` および `Description` プロパティも使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-170">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="f14e7-171">`Configuration` (既定値は `Debug`) は、すべての MSBuild ターゲットと共有されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-171">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="f14e7-172">これは、`dotnet` コマンド ([dotnet pack](../tools/dotnet-pack.md) など) の `--configuration` オプションを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-172">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>
- <span data-ttu-id="f14e7-173">一部のプロパティは、NuGet パッケージを作成するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-173">Some of the properties are used when creating a NuGet package.</span></span> <span data-ttu-id="f14e7-174">詳細については、「[パッケージのプロパティ](#package-properties)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-174">For more information, see [Package properties](#package-properties).</span></span>

#### <a name="migrating-from-net-framework"></a><span data-ttu-id="f14e7-175">.NET Framework からの移行</span><span class="sxs-lookup"><span data-stu-id="f14e7-175">Migrating from .NET Framework</span></span>

<span data-ttu-id="f14e7-176">.NET Framework プロジェクト テンプレートでは、これらのアセンブリ情報属性を設定したコード ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-176">.NET Framework project templates create a code file with these assembly info attributes set.</span></span> <span data-ttu-id="f14e7-177">通常、このファイルは *.\Properties\AssemblyInfo.cs* または *.\Properties\AssemblyInfo.vb* にあります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-177">The file is typically located at *.\Properties\AssemblyInfo.cs* or *.\Properties\AssemblyInfo.vb*.</span></span> <span data-ttu-id="f14e7-178">SDK スタイルのプロジェクトでは、プロジェクトの設定に基づいてこのファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-178">SDK-style projects generate this file for you based on the project settings.</span></span> <span data-ttu-id="f14e7-179">**両方を持つことはできません。**</span><span class="sxs-lookup"><span data-stu-id="f14e7-179">**You can't have both.**</span></span> <span data-ttu-id="f14e7-180">コードを .NET 5 (および .NET Core 3.1) 以降に移植する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f14e7-180">When porting your code to .NET 5 (and .NET Core 3.1) or later, do one of the following:</span></span>

- <span data-ttu-id="f14e7-181">`GenerateAssemblyInfo` を `false` に設定することにより、アセンブリ情報属性を含む一時コード ファイルの生成を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f14e7-181">Disable the generation of the temporary code file that contains the assembly info attributes by setting `GenerateAssemblyInfo` to `false`.</span></span> <span data-ttu-id="f14e7-182">これにより、*AssemblyInfo* ファイルを保持することができます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-182">This enables you to keep your *AssemblyInfo* file.</span></span>
- <span data-ttu-id="f14e7-183">`AssemblyInfo` ファイルの設定をプロジェクト ファイルに移行し、`AssemblyInfo` ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-183">Migrate the settings in the `AssemblyInfo` file to the project file, and delete the `AssemblyInfo` file.</span></span>

### <a name="generateassemblyinformationalversionattribute"></a><span data-ttu-id="f14e7-184">GenerateAssemblyInformationalVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-184">GenerateAssemblyInformationalVersionAttribute</span></span>

<span data-ttu-id="f14e7-185">このプロパティは、`InformationalVersion` プロパティがアセンブリの <xref:System.Reflection.AssemblyInformationalVersionAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-185">This property controls whether or not the `InformationalVersion` property generates the <xref:System.Reflection.AssemblyInformationalVersionAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-186">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-186">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyInformationalVersionAttribute>false</GenerateAssemblyInformationalVersionAttribute>
</PropertyGroup>
```

### <a name="generateassemblyproductattribute"></a><span data-ttu-id="f14e7-187">GenerateAssemblyProductAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-187">GenerateAssemblyProductAttribute</span></span>

<span data-ttu-id="f14e7-188">このプロパティは、`Product` プロパティがアセンブリの <xref:System.Reflection.AssemblyProductAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-188">This property controls whether or not the `Product` property generates the <xref:System.Reflection.AssemblyProductAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-189">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-189">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyProductAttribute>false</GenerateAssemblyProductAttribute>
</PropertyGroup>
```

### <a name="generateassemblytitleattribute"></a><span data-ttu-id="f14e7-190">GenerateAssemblyTitleAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-190">GenerateAssemblyTitleAttribute</span></span>

<span data-ttu-id="f14e7-191">このプロパティは、`AssemblyTitle` プロパティがアセンブリの <xref:System.Reflection.AssemblyTitleAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-191">This property controls whether or not the `AssemblyTitle` property generates the <xref:System.Reflection.AssemblyTitleAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-192">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-192">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyTitleAttribute>false</GenerateAssemblyTitleAttribute>
</PropertyGroup>
```

### <a name="generateassemblyversionattribute"></a><span data-ttu-id="f14e7-193">GenerateAssemblyVersionAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-193">GenerateAssemblyVersionAttribute</span></span>

<span data-ttu-id="f14e7-194">このプロパティは、`AssemblyVersion` プロパティがアセンブリの <xref:System.Reflection.AssemblyVersionAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-194">This property controls whether or not the `AssemblyVersion` property generates the <xref:System.Reflection.AssemblyVersionAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-195">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-195">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateAssemblyVersionAttribute>false</GenerateAssemblyVersionAttribute>
</PropertyGroup>
```

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="f14e7-196">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="f14e7-196">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="f14e7-197">このプロパティは、生成されるアセンブリ情報ファイルの相対パスまたは絶対パスを定義します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-197">The property defines the relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="f14e7-198">既定値は、`$(IntermediateOutputPath)` (通常は *obj*) ディレクトリ内の *[プロジェクト名].AssemblyInfo.[cs|vb]* という名前のファイルです。</span><span class="sxs-lookup"><span data-stu-id="f14e7-198">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (usually the *obj*) directory.</span></span>

```xml
<PropertyGroup>
  <GeneratedAssemblyInfoFile>assemblyinfo.cs</GeneratedAssemblyInfoFile>
</PropertyGroup>
```

### <a name="generateneutralresourceslanguageattribute"></a><span data-ttu-id="f14e7-199">GenerateNeutralResourcesLanguageAttribute</span><span class="sxs-lookup"><span data-stu-id="f14e7-199">GenerateNeutralResourcesLanguageAttribute</span></span>

<span data-ttu-id="f14e7-200">このプロパティは、`NeutralLanguage` プロパティがアセンブリの <xref:System.Resources.NeutralResourcesLanguageAttribute> を生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-200">This property controls whether or not the `NeutralLanguage` property generates the <xref:System.Resources.NeutralResourcesLanguageAttribute> for the assembly.</span></span> <span data-ttu-id="f14e7-201">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-201">The default value is `true`.</span></span>

```xml
<PropertyGroup>
  <GenerateNeutralResourcesLanguageAttribute>false</GenerateNeutralResourcesLanguageAttribute>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="f14e7-202">パッケージのプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-202">Package properties</span></span>

<span data-ttu-id="f14e7-203">`PackageId`、`PackageVersion`、`PackageIcon`、`Title`、`Description` などのプロパティを指定し、プロジェクトから作成されたパッケージについて説明できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-203">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="f14e7-204">以上のプロパティとその他のプロパティの詳細については、「[pack ターゲット](/nuget/reference/msbuild-targets#pack-target)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-204">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-related-properties"></a><span data-ttu-id="f14e7-205">公開関連のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-205">Publish-related properties</span></span>

<span data-ttu-id="f14e7-206">このセクションでは、次の MSBuild プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-206">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="f14e7-207">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="f14e7-207">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="f14e7-208">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="f14e7-208">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="f14e7-209">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="f14e7-209">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="f14e7-210">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="f14e7-210">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="f14e7-211">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="f14e7-211">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="f14e7-212">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="f14e7-212">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="f14e7-213">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="f14e7-213">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="f14e7-214">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="f14e7-214">UseAppHost</span></span>](#useapphost)

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="f14e7-215">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="f14e7-215">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="f14e7-216">`AppendTargetFrameworkToOutputPath` プロパティは、[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) を出力パス ([OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters) で定義されている) に追加するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-216">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="f14e7-217">.NET SDK はターゲット フレームワークを、それが存在する場合にはランタイム識別子を出力パスに自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-217">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="f14e7-218">`AppendTargetFrameworkToOutputPath` を `false` に設定すると、TFM が出力パスに追加されなくなります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-218">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="f14e7-219">ただし、出力パスに TFM がないと、複数のビルド成果物が相互に上書きされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-219">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="f14e7-220">たとえば、.NET 5.0 アプリの場合、出力パスは次の設定を使用して `bin\Debug\net5.0` から `bin\Debug` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-220">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="f14e7-221">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="f14e7-221">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="f14e7-222">`AppendRuntimeIdentifierToOutputPath` プロパティは、[ランタイム識別子 (RID)](../rid-catalog.md) を出力パスに追加するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-222">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="f14e7-223">.NET SDK はターゲット フレームワークを、それが存在する場合にはランタイム識別子を出力パスに自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-223">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="f14e7-224">`AppendRuntimeIdentifierToOutputPath` を `false` に設定すると、RID が出力パスに追加されなくなります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-224">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="f14e7-225">たとえば、.NET 5.0 アプリで RID が `win10-x64` の場合、出力パスは次の設定を使用して `bin\Debug\net5.0\win10-x64` から `bin\Debug\net5.0` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-225">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="f14e7-226">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="f14e7-226">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="f14e7-227">`CopyLocalLockFileAssemblies` プロパティは、他のライブラリに依存しているプラグイン プロジェクトにとって便利です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-227">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="f14e7-228">このプロパティを `true` に設定すると、NuGet パッケージの依存関係が出力ディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-228">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="f14e7-229">つまり、`dotnet build` の出力を使用し、任意のコンピューターでプラグインを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-229">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="f14e7-230">あるいは、`dotnet publish` を使用し、クラス ライブラリを発行できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-230">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="f14e7-231">詳細については、「[dotnet publish](../tools/dotnet-publish.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-231">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="f14e7-232">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="f14e7-232">PreserveCompilationContext</span></span>

<span data-ttu-id="f14e7-233">`PreserveCompilationContext` プロパティを使うと、ビルド時に使用されたのと同じ設定で、ビルドまたは発行されたアプリケーションで実行時により多くのコードをコンパイルできるようになります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-233">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="f14e7-234">ビルド時に参照されるアセンブリは、出力ディレクトリの *ref* サブディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-234">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="f14e7-235">参照アセンブリの名前は、コンパイラに渡されるオプションと共に、アプリケーションの *.deps.json* ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-235">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="f14e7-236">この情報は、<xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> と <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> のプロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-236">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="f14e7-237">この機能は、ほとんどの場合、Razor ファイルの実行時コンパイルをサポートするために ASP.NET Core MVC と Razor Pages によって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-237">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="f14e7-238">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="f14e7-238">PreserveCompilationReferences</span></span>

<span data-ttu-id="f14e7-239">`PreserveCompilationReferences` プロパティは [PreserveCompilationContext](#preservecompilationcontext) プロパティと似ていますが、 *.deps.json* ファイルではなく、発行ディレクトリに参照アセンブリのみがコピーされる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-239">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="f14e7-240">詳細については、「[Razor SDK」の「プロパティ](/aspnet/core/razor-pages/sdk#properties)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-240">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="f14e7-241">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="f14e7-241">RuntimeIdentifier</span></span>

<span data-ttu-id="f14e7-242">`RuntimeIdentifier` プロパティを使用すると、プロジェクトに 1 つの[ランタイム識別子 (RID)](../rid-catalog.md) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-242">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="f14e7-243">RID により、自己完結型の展開を発行できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-243">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="f14e7-244">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="f14e7-244">RuntimeIdentifiers</span></span>

<span data-ttu-id="f14e7-245">`RuntimeIdentifiers` プロパティには、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) のセミコロン区切りリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-245">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="f14e7-246">複数のランタイムに発行する必要がある場合は、このプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-246">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="f14e7-247">`RuntimeIdentifiers` は、復元時に適切な資産をグラフに確実に含めるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-247">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="f14e7-248">`RuntimeIdentifier` (単数形) を使用すると、必要なランタイムが 1 つだけのとき、ビルドが速くなります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-248">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="useapphost"></a><span data-ttu-id="f14e7-249">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="f14e7-249">UseAppHost</span></span>

<span data-ttu-id="f14e7-250">`UseAppHost` プロパティにより、デプロイ用にネイティブ実行可能ファイルを作成するかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-250">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="f14e7-251">自己完結型の配置にはネイティブの実行可能ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-251">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="f14e7-252">.NET Core 3.0 以降のバージョンでは、既定でフレームワークに依存する実行可能ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-252">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="f14e7-253">実行可能ファイルの生成を無効にするには、`UseAppHost` プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-253">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="f14e7-254">配置の詳細については、[.NET アプリケーションの配置](../deploying/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-254">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compilation-related-properties"></a><span data-ttu-id="f14e7-255">コンパイル関連のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-255">Compilation-related properties</span></span>

<span data-ttu-id="f14e7-256">このセクションでは、次の MSBuild プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-256">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="f14e7-257">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="f14e7-257">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="f14e7-258">LangVersion</span><span class="sxs-lookup"><span data-stu-id="f14e7-258">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="f14e7-259">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="f14e7-259">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="f14e7-260">`EmbeddedResourceUseDependentUponConvention` プロパティは、リソース マニフェスト ファイル名が、リソース ファイルと併置されているソース ファイルの型情報から生成されるかどうかを定義します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-260">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="f14e7-261">たとえば、*Form1.vb* が *Form1.cs* と同じフォルダーにあり、`EmbeddedResourceUseDependentUponConvention` が `true` に設定されている場合、生成された *.resources* ファイルは *Form1.cs* で定義されている最初の型から名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-261">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="f14e7-262">たとえば、`MyNamespace.Form1` が *Form1.cs* で定義されている最初の型である場合、生成されたファイル名は *MyNamespace.Form1.resources* になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-262">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="f14e7-263">`LogicalName`、`ManifestResourceName`、または `DependentUpon` メタデータが `EmbeddedResource` 項目に対して指定されている場合、そのリソース ファイルに対して生成されたマニフェスト ファイル名は、代わりにそのメタデータがベースになります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-263">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="f14e7-264">既定では、新しい .NET プロジェクトでは、このプロパティは `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-264">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="f14e7-265">`false` に設定され、かつプロジェクト ファイルの `EmbeddedResource` 項目に `LogicalName`、`ManifestResourceName`、`DependentUpon` のメタデータがどれも指定されていない場合、リソース マニフェストのファイル名は、プロジェクトのルート名前空間と、 *.resx* ファイルへの相対ファイル パスがベースになります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-265">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="f14e7-266">詳細については、「[リソース マニフェスト ファイルの名前付けの方法](../resources/manifest-file-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-266">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="f14e7-267">LangVersion</span><span class="sxs-lookup"><span data-stu-id="f14e7-267">LangVersion</span></span>

<span data-ttu-id="f14e7-268">`LangVersion` プロパティを使用すると、特定のプログラミング言語バージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-268">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="f14e7-269">たとえば、C# プレビュー機能にアクセスする場合は、`LangVersion` を `preview` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-269">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f14e7-270">詳細については、「[C# 言語のバージョン管理](../../csharp/language-reference/configure-language-version.md#override-a-default)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-270">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="f14e7-271">既定の項目の包含プロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-271">Default item inclusion properties</span></span>

<span data-ttu-id="f14e7-272">このセクションでは、次の MSBuild プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-272">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="f14e7-273">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="f14e7-273">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="f14e7-274">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="f14e7-274">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="f14e7-275">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-275">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="f14e7-276">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-276">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="f14e7-277">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-277">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="f14e7-278">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-278">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="f14e7-279">詳細については、「[既定で含まれるものと除外されるもの](overview.md#default-includes-and-excludes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-279">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="f14e7-280">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="f14e7-280">DefaultItemExcludes</span></span>

<span data-ttu-id="f14e7-281">`DefaultItemExcludes` プロパティを使用して、含まれる、除外される、および削除の glob から除外するファイルとフォルダーの glob パターンを定義します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-281">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="f14e7-282">既定では、 *./bin* および *./obj* フォルダーは、glob パターンから除外されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-282">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="f14e7-283">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="f14e7-283">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="f14e7-284">`DefaultExcludesInProjectFolder` プロパティを使用して、含まれる、除外される、および削除の glob から除外する、プロジェクト フォルダーのファイルとフォルダーの glob パターンを定義します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-284">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="f14e7-285">既定では、ピリオド (`.`) で始まるフォルダー ( *.git* や *.vs* など) は、glob パターンから除外されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-285">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="f14e7-286">このプロパティは、プロジェクト フォルダー内のファイルとフォルダーのみが考慮される点を除いて、`DefaultItemExcludes` プロパティとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-286">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="f14e7-287">glob パターンが意図せずにプロジェクト フォルダー外の項目と相対パスを照合する場合は、`DefaultItemExcludes` プロパティの代わりに `DefaultExcludesInProjectFolder` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-287">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="f14e7-288">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-288">EnableDefaultItems</span></span>

<span data-ttu-id="f14e7-289">`EnableDefaultItems` プロパティは、コンパイル項目、埋め込みリソース項目、および `None` 項目がプロジェクトに暗黙的に含まれるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-289">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="f14e7-290">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-290">The default value is `true`.</span></span> <span data-ttu-id="f14e7-291">`EnableDefaultItems` プロパティを `false` に設定して、暗黙的なファイルの組み込みをすべて無効にします。</span><span class="sxs-lookup"><span data-stu-id="f14e7-291">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="f14e7-292">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-292">EnableDefaultCompileItems</span></span>

<span data-ttu-id="f14e7-293">`EnableDefaultCompileItems` プロパティは、コンパイル項目がプロジェクトに暗黙的に含まれるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-293">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="f14e7-294">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-294">The default value is `true`.</span></span> <span data-ttu-id="f14e7-295">`EnableDefaultCompileItems` プロパティを `false` に設定して、\*.cs およびその他の言語拡張ファイルの暗黙的な包含を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f14e7-295">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="f14e7-296">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-296">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="f14e7-297">`EnableDefaultEmbeddedResourceItems` プロパティは、埋め込みリソース項目がプロジェクトに暗黙的に含まれるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-297">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="f14e7-298">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-298">The default value is `true`.</span></span> <span data-ttu-id="f14e7-299">埋め込みリソース ファイルの暗黙的な包含を無効にするには、`EnableDefaultEmbeddedResourceItems` プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-299">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="f14e7-300">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="f14e7-300">EnableDefaultNoneItems</span></span>

<span data-ttu-id="f14e7-301">`EnableDefaultNoneItems` プロパティは、`None` 項目 (ビルド プロセスでロールがないファイル) がプロジェクトに暗黙的に含まれるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-301">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="f14e7-302">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-302">The default value is `true`.</span></span> <span data-ttu-id="f14e7-303">`EnableDefaultNoneItems` プロパティを `false` に設定して、`None` 項目の暗黙的な包含を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f14e7-303">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="f14e7-304">コード分析のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-304">Code analysis properties</span></span>

<span data-ttu-id="f14e7-305">このセクションでは、次の MSBuild プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-305">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="f14e7-306">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="f14e7-306">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="f14e7-307">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="f14e7-307">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="f14e7-308">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="f14e7-308">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="f14e7-309">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="f14e7-309">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="f14e7-310">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="f14e7-310">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="f14e7-311">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="f14e7-311">AnalysisLevel</span></span>

<span data-ttu-id="f14e7-312">`AnalysisLevel` プロパティを使用すると、コード分析レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-312">The `AnalysisLevel` property lets you specify a code-analysis level.</span></span> <span data-ttu-id="f14e7-313">たとえば、プレビューのコード アナライザーにアクセスする場合は、`AnalysisLevel` を `preview` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-313">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span>

<span data-ttu-id="f14e7-314">既定値:</span><span class="sxs-lookup"><span data-stu-id="f14e7-314">Default value:</span></span>

- <span data-ttu-id="f14e7-315">プロジェクトのターゲットが .NET 5.0 以降の場合、または [AnalysisMode](#analysismode) プロパティを追加した場合、既定値は `latest` になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-315">If your project targets .NET 5.0 or later, or if you've added the [AnalysisMode](#analysismode) property, the default value is `latest`.</span></span>
- <span data-ttu-id="f14e7-316">それ以外の場合、このプロパティは、プロジェクト ファイルに明示的に追加されていない限り省略されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-316">Otherwise, this property is omitted unless you explicitly add it to the project file.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="f14e7-317">次の表で利用可能なオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-317">The following table shows the available options.</span></span>

| <span data-ttu-id="f14e7-318">値</span><span class="sxs-lookup"><span data-stu-id="f14e7-318">Value</span></span> | <span data-ttu-id="f14e7-319">説明</span><span class="sxs-lookup"><span data-stu-id="f14e7-319">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="f14e7-320">リリースされている最新のコード アナライザーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-320">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="f14e7-321">既定値です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-321">This is the default.</span></span> |
| `preview` | <span data-ttu-id="f14e7-322">最新のコード アナライザーが、プレビュー段階であっても使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-322">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="f14e7-323">新しいルールが使用可能な場合でも、.NET 5.0 リリースで有効になっていた一連のルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-323">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="f14e7-324">新しいルールが使用可能な場合でも、.NET 5.0 リリースで有効になっていた一連のルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-324">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

> [!NOTE]
> <span data-ttu-id="f14e7-325">このプロパティは、[プロジェクト SDK](overview.md) を参照しないプロジェクト (たとえば、Microsoft. CodeAnalysis. NetAnalyzers NuGet パッケージを参照するレガシ .NET Framework プロジェクト) のコード分析には影響しません。</span><span class="sxs-lookup"><span data-stu-id="f14e7-325">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="analysismode"></a><span data-ttu-id="f14e7-326">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="f14e7-326">AnalysisMode</span></span>

<span data-ttu-id="f14e7-327">.NET 5.0 以降、.NET SDK には、すべての ["CA" コード品質ルール](../../fundamentals/code-analysis/quality-rules/index.md)が付属しています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-327">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="f14e7-328">既定では、ビルド警告として[一部のルールが有効](../../fundamentals/code-analysis/overview.md#enabled-rules)になっています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-328">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="f14e7-329">`AnalysisMode` プロパティを使用すると、既定で有効になるルールのセットをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-329">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="f14e7-330">より積極的な (オプトアウト) 分析モード、またはより保守的な (オプトイン) 分析モードに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-330">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="f14e7-331">たとえば、既定ですべてのルールをビルド警告として有効にする場合は、値を `AllEnabledByDefault` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-331">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="f14e7-332">次の表で利用可能なオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-332">The following table shows the available options.</span></span>

| <span data-ttu-id="f14e7-333">値</span><span class="sxs-lookup"><span data-stu-id="f14e7-333">Value</span></span> | <span data-ttu-id="f14e7-334">説明</span><span class="sxs-lookup"><span data-stu-id="f14e7-334">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="f14e7-335">既定のモードでは、特定のルールがビルド警告として有効になり、特定のルールが Visual Studio IDE の提案として有効になり、残りは無効になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-335">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="f14e7-336">積極的な (オプトアウト) モード。すべてのルールが既定でビルド警告として有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-336">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="f14e7-337">個々のルールを選択的に[オプトアウト](../../fundamentals/code-analysis/configuration-options.md)して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-337">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="f14e7-338">保守的な (オプトイン) モード。すべてのルールが既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-338">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="f14e7-339">個々のルールを選択的に[オプトイン](../../fundamentals/code-analysis/configuration-options.md)して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-339">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

> [!NOTE]
> <span data-ttu-id="f14e7-340">このプロパティは、[プロジェクト SDK](overview.md) を参照しないプロジェクト (たとえば、Microsoft. CodeAnalysis. NetAnalyzers NuGet パッケージを参照するレガシ .NET Framework プロジェクト) のコード分析には影響しません。</span><span class="sxs-lookup"><span data-stu-id="f14e7-340">This property has no effect on code analysis in projects that don't reference a [project SDK](overview.md), for example, legacy .NET Framework projects that reference the Microsoft.CodeAnalysis.NetAnalyzers NuGet package.</span></span>

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="f14e7-341">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="f14e7-341">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="f14e7-342">`CodeAnalysisTreatWarningsAsErrors` プロパティを使用すると、コード品質分析の警告 (CAxxxx) を警告として扱い、ビルドを中断するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-342">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="f14e7-343">プロジェクトをビルドするときに `-warnaserror` フラグを使用すると、[.NET コード品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)の警告もエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-343">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="f14e7-344">コード品質分析の警告がエラーとして扱われないようにするには、プロジェクト ファイル内の `CodeAnalysisTreatWarningsAsErrors` MSBuild プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-344">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="f14e7-345">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="f14e7-345">EnableNETAnalyzers</span></span>

<span data-ttu-id="f14e7-346">.NET 5.0 以降をターゲットとするプロジェクトでは、[.NET コード品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)が既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-346">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="f14e7-347">以前のバージョンの .NET をターゲットとする SDK スタイルのプロジェクトで .NET コード分析を有効にするには、`EnableNETAnalyzers` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-347">You can enable .NET code analysis for SDK-style projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="f14e7-348">任意のプロジェクトでコード分析を無効にするには、このプロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-348">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="f14e7-349">このプロパティは、特に、.NET 5+ SDK の組み込みアナライザーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-349">This property applies specifically to the built-in analyzers in the .NET 5+ SDK.</span></span> <span data-ttu-id="f14e7-350">これは NuGet コード分析パッケージをインストールするときには使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-350">It should not be used when you install a NuGet code analysis package.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="f14e7-351">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="f14e7-351">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="f14e7-352">この機能は現在試験段階にあり、.NET 5 リリースと .NET 6 リリースの間で変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-352">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="f14e7-353">すべての .NET プロジェクトのビルドでは、[.NET コード スタイル分析](../../fundamentals/code-analysis/overview.md#code-style-analysis)は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-353">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="f14e7-354">`EnforceCodeStyleInBuild` プロパティを `true` に設定して、.NET プロジェクトのコード スタイル分析を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-354">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="f14e7-355">警告またはエラーになるように[構成](../../fundamentals/code-analysis/overview.md#code-style-analysis)されているすべてのコード スタイル ルールは、ビルド時に実行され、違反を報告します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-355">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="f14e7-356">ランタイム構成プロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-356">Run-time configuration properties</span></span>

<span data-ttu-id="f14e7-357">アプリのプロジェクト ファイルに MSBuild プロパティを指定することで一部のランタイム動作を構成できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-357">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="f14e7-358">ランタイム動作のその他の構成方法については、[ランタイム構成設定](../run-time-config/index.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-358">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="f14e7-359">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f14e7-359">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="f14e7-360">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="f14e7-360">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="f14e7-361">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f14e7-361">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="f14e7-362">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f14e7-362">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="f14e7-363">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="f14e7-363">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="f14e7-364">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="f14e7-364">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="f14e7-365">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="f14e7-365">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="f14e7-366">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="f14e7-366">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="f14e7-367">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="f14e7-367">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="f14e7-368">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f14e7-368">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="f14e7-369">`ConcurrentGarbageCollection` プロパティでは、[バックグラウンド (同時実行) ガベージ コレクション](../../standard/garbage-collection/background-gc.md)の有効または無効が設定されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-369">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="f14e7-370">この値を `false` に設定すると、バックグラウンド ガベージ コレクションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-370">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="f14e7-371">詳細については、「[バックグラウンド GC](../run-time-config/garbage-collector.md#background-gc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-371">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="f14e7-372">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="f14e7-372">InvariantGlobalization</span></span>

<span data-ttu-id="f14e7-373">`InvariantGlobalization` プロパティでは、アプリを *globalization-invariant* モードで実行するかどうかを設定します。このモードでは、カルチャ固有のデータにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="f14e7-373">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="f14e7-374">この値を `true` に設定すると、globalization-invariant モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-374">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="f14e7-375">詳細については、「[インバリアント モード](../run-time-config/globalization.md#invariant-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-375">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="f14e7-376">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f14e7-376">RetainVMGarbageCollection</span></span>

<span data-ttu-id="f14e7-377">`RetainVMGarbageCollection` プロパティでは、将来利用する目的で削除済みメモリ セグメントを待機一覧に載せるように、あるいは削除済みメモリ セグメントを解放するようにガベージ コレクターを設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-377">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="f14e7-378">この値を `true` に設定すると、セグメントを待機一覧に載せるよう、ガベージ コレクターが命令されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-378">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="f14e7-379">詳細については、「[VM の保持](../run-time-config/garbage-collector.md#retain-vm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-379">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="f14e7-380">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f14e7-380">ServerGarbageCollection</span></span>

<span data-ttu-id="f14e7-381">`ServerGarbageCollection` プロパティでは、アプリケーションで使用するガベージ コレクションとして[ワークステーション ガベージ コレクションまたはサーバー ガベージ コレクション](../../standard/garbage-collection/workstation-server-gc.md)を設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-381">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="f14e7-382">この値を `true` に設定すると、サーバー ガベージ コレクションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-382">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="f14e7-383">詳細については、「[ワークステーションとサーバー](../run-time-config/garbage-collector.md#workstation-vs-server)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-383">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="f14e7-384">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="f14e7-384">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="f14e7-385">`ThreadPoolMaxThreads` プロパティでは、ワーカー スレッド プールの最大スレッド数を設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-385">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="f14e7-386">詳細については、「[最大スレッド数](../run-time-config/threading.md#maximum-threads)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-386">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="f14e7-387">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="f14e7-387">ThreadPoolMinThreads</span></span>

<span data-ttu-id="f14e7-388">`ThreadPoolMinThreads` プロパティでは、ワーカー スレッド プールの最小スレッド数を設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-388">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="f14e7-389">詳細については、「[最小スレッド数](../run-time-config/threading.md#minimum-threads)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-389">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="f14e7-390">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="f14e7-390">TieredCompilation</span></span>

<span data-ttu-id="f14e7-391">`TieredCompilation` プロパティでは、Just-In-Time (JIT) コンパイラで[階層型コンパイル](../whats-new/dotnet-core-3-0.md#tiered-compilation)を使用するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-391">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="f14e7-392">この値を `false` に設定すると、階層型コンパイルが無効になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-392">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="f14e7-393">詳細については、「[階層型コンパイル](../run-time-config/compilation.md#tiered-compilation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-393">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="f14e7-394">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="f14e7-394">TieredCompilationQuickJit</span></span>

<span data-ttu-id="f14e7-395">`TieredCompilationQuickJit` プロパティでは、JIT コンパイラでクイック JIT を使用するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-395">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="f14e7-396">この値を `false` に設定すると、クイック JIT が無効になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-396">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="f14e7-397">詳細については、「[クイック JIT](../run-time-config/compilation.md#quick-jit)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-397">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="f14e7-398">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="f14e7-398">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="f14e7-399">`TieredCompilationQuickJitForLoops` プロパティでは、ループを含むメソッドに対して JIT コンパイラでクリック JIT を使用するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-399">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="f14e7-400">この値を `true` に設定すると、ループが含まれるメソッドでクイック JIT が有効になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-400">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="f14e7-401">詳細については、「[ループに対するクイック JIT](../run-time-config/compilation.md#quick-jit-for-loops)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-401">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="f14e7-402">参照のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-402">Reference properties</span></span>

<span data-ttu-id="f14e7-403">このセクションでは、次の MSBuild プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-403">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="f14e7-404">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="f14e7-404">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="f14e7-405">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="f14e7-405">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="f14e7-406">復元関連のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-406">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="f14e7-407">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="f14e7-407">AssetTargetFallback</span></span>

<span data-ttu-id="f14e7-408">`AssetTargetFallback` プロパティを使用すると、プロジェクト参照と NuGet パッケージに対して、互換性のある追加のフレームワーク バージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-408">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="f14e7-409">たとえば、`PackageReference` を使用してパッケージの依存関係を指定し、そのパッケージにプロジェクトの `TargetFramework` と互換性のある資産が含まれない場合は、`AssetTargetFallback` プロパティが機能します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-409">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="f14e7-410">参照されたパッケージの互換性は、`AssetTargetFallback` で指定された各ターゲット フレームワークを使用して再確認されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-410">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="f14e7-411">このプロパティは、非推奨のプロパティ `PackageTargetFallback` に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="f14e7-411">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="f14e7-412">`AssetTargetFallback` プロパティを 1 つ以上の[ターゲット フレームワーク バージョン](../../standard/frameworks.md#supported-target-frameworks)に設定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-412">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="f14e7-413">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="f14e7-413">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="f14e7-414">`DisableImplicitFrameworkReferences` プロパティを使用すると、.NET Core 3.0 以降のバージョンを対象とする場合に、暗黙的な `FrameworkReference` の項目を制御できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-414">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="f14e7-415">.NET Core 2.1 または .NET Standard 2.0 以前のバージョンを対象としている場合は、これにより、メタパッケージ内のパッケージに対する暗黙的な [PackageReference](#packagereference) の項目が制御されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-415">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="f14e7-416">(メタパッケージは、他のパッケージの依存関係のみで構成されるフレームワーク ベースのパッケージです)。また、このプロパティを使用すると、.NET Framework を対象としている場合に、`System` や `System.Core` などの暗黙的な参照も制御できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-416">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="f14e7-417">このプロパティを `true` に設定して、暗黙的な `FrameworkReference` または [PackageReference](#packagereference) の項目を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f14e7-417">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="f14e7-418">このプロパティを `true` に設定すると、必要なフレームワークまたはパッケージだけに明示的な参照を追加できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-418">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="f14e7-419">復元関連のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-419">Restore-related properties</span></span>

<span data-ttu-id="f14e7-420">参照されたパッケージを復元すると、その直接的な依存関係と間接的な依存関係がすべてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-420">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="f14e7-421">`RestorePackagesPath` や `RestoreIgnoreFailedSources` など、プロパティを指定することでパッケージ復元をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-421">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="f14e7-422">以上のプロパティとその他のプロパティの詳細については、「[restore ターゲット](/nuget/reference/msbuild-targets#restore-target)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-422">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-related-properties"></a><span data-ttu-id="f14e7-423">実行関連のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-423">Run-related properties</span></span>

<span data-ttu-id="f14e7-424">次のプロパティは、[`dotnet run`](../tools/dotnet-run.md) コマンドを使用してアプリを起動するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-424">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="f14e7-425">RunArguments</span><span class="sxs-lookup"><span data-stu-id="f14e7-425">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="f14e7-426">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="f14e7-426">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="f14e7-427">RunArguments</span><span class="sxs-lookup"><span data-stu-id="f14e7-427">RunArguments</span></span>

<span data-ttu-id="f14e7-428">`RunArguments` プロパティを使用すると、実行時にアプリに渡される引数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-428">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="f14e7-429">[`dotnet run` に ](../tools/dotnet-run.md#options)`--` オプションを使用して、アプリに渡す追加の引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-429">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="f14e7-430">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="f14e7-430">RunWorkingDirectory</span></span>

<span data-ttu-id="f14e7-431">`RunWorkingDirectory` プロパティを使用すると、開始するアプリケーション プロセスの作業ディレクトリが定義されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-431">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="f14e7-432">絶対パスまたはプロジェクト ディレクトリに対する相対パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-432">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="f14e7-433">ディレクトリを指定しない場合、作業ディレクトリとして `OutDir` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-433">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-related-properties"></a><span data-ttu-id="f14e7-434">ホスティング関連のプロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-434">Hosting-related properties</span></span>

<span data-ttu-id="f14e7-435">このセクションでは、次の MSBuild プロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-435">The following MSBuild properties are documented in this section:</span></span>

- [<span data-ttu-id="f14e7-436">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="f14e7-436">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="f14e7-437">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="f14e7-437">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="f14e7-438">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="f14e7-438">EnableComHosting</span></span>

<span data-ttu-id="f14e7-439">`EnableComHosting` プロパティは、アセンブリで COM サーバーが提供されることを示します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-439">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="f14e7-440">`EnableComHosting` を `true` に設定することは、[EnableDynamicLoading](#enabledynamicloading) が `true` であることも意味します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-440">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="f14e7-441">詳細については、[COM への .NET コンポーネントの公開](../native-interop/expose-components-to-com.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-441">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="f14e7-442">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="f14e7-442">EnableDynamicLoading</span></span>

<span data-ttu-id="f14e7-443">`EnableDynamicLoading` プロパティは、アセンブリが動的に読み込まれたコンポーネントであることを示します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-443">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="f14e7-444">コンポーネントには、[COM ライブラリ](/windows/win32/com/the-component-object-model)、または[ネイティブ ホストから使用](../tutorials/netcore-hosting.md)できる非 COM ライブラリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-444">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="f14e7-445">このプロパティを `true` に設定すると、次のような効果があります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-445">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="f14e7-446">" *.runtimeconfig.json*" ファイルが生成される。</span><span class="sxs-lookup"><span data-stu-id="f14e7-446">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="f14e7-447">[ロール フォワード](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)が `LatestMinor` に設定される。</span><span class="sxs-lookup"><span data-stu-id="f14e7-447">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="f14e7-448">NuGet 参照がローカルにコピーされる。</span><span class="sxs-lookup"><span data-stu-id="f14e7-448">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="items"></a><span data-ttu-id="f14e7-449">アイテム</span><span class="sxs-lookup"><span data-stu-id="f14e7-449">Items</span></span>

<span data-ttu-id="f14e7-450">[MSBuild 項目](/visualstudio/msbuild/msbuild-items)はビルド システムへの入力です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-450">[MSBuild items](/visualstudio/msbuild/msbuild-items) are inputs into the build system.</span></span> <span data-ttu-id="f14e7-451">項目は、要素名である型に従って指定されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-451">Items are specified according to their type, which is the element name.</span></span> <span data-ttu-id="f14e7-452">たとえば、`Compile` と `Reference` は 2 つの[一般的な項目の種類](/visualstudio/msbuild/common-msbuild-project-items)です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-452">For example, `Compile` and `Reference` are two [common item types](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="f14e7-453">.NET SDK では、次の追加の項目の種類を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-453">The following additional item types are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="f14e7-454">PackageReference</span><span class="sxs-lookup"><span data-stu-id="f14e7-454">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="f14e7-455">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="f14e7-455">TrimmerRootAssembly</span></span>](#trimmerrootassembly)

<span data-ttu-id="f14e7-456">これらの項目には、標準の[項目属性](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements) (`Include` や `Update` など) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-456">You can use any of the standard [item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), for example, `Include` and `Update`, on these items.</span></span> <span data-ttu-id="f14e7-457">`Include` を使用して新しい項目を追加し、`Update` を使用して既存の項目を変更します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-457">Use `Include` to add a new item, and use `Update` to modify an existing item.</span></span> <span data-ttu-id="f14e7-458">たとえば、`Update` は、.NET SDK によって暗黙的に追加された項目を変更するためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-458">For example, `Update` is often used to modify an item that has implicitly been added by the .NET SDK.</span></span>

### <a name="packagereference"></a><span data-ttu-id="f14e7-459">PackageReference</span><span class="sxs-lookup"><span data-stu-id="f14e7-459">PackageReference</span></span>

<span data-ttu-id="f14e7-460">`PackageReference` 項目では、NuGet パッケージへの参照が定義されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-460">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="f14e7-461">`Include` 属性は、パッケージ ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-461">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="f14e7-462">`Version` 属性では、バージョンまたはバージョン範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="f14e7-462">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="f14e7-463">最小バージョン、最大バージョン、範囲、厳密一致を指定する方法については、「[バージョン範囲](/nuget/concepts/package-versioning#version-ranges)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-463">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

<span data-ttu-id="f14e7-464">次の例のプロジェクト ファイル スニペットでは、[System.Runtime](https://www.nuget.org/packages/System.Runtime/) パッケージを参照しています。</span><span class="sxs-lookup"><span data-stu-id="f14e7-464">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="f14e7-465">`PrivateAssets` などのメタデータを使用して[依存関係資産を制御](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets)することもできます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-465">You can also [control dependency assets](/nuget/consume-packages/package-references-in-project-files#controlling-dependency-assets) using metadata such as `PrivateAssets`.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0">
    <PrivateAssets>all</PrivateAssets>
  </PackageReference>
</ItemGroup>
```

<span data-ttu-id="f14e7-466">詳細については、[プロジェクト ファイルのパッケージ参照](/nuget/consume-packages/package-references-in-project-files)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f14e7-466">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="trimmerrootassembly"></a><span data-ttu-id="f14e7-467">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="f14e7-467">TrimmerRootAssembly</span></span>

<span data-ttu-id="f14e7-468">`TrimmerRootAssembly` 項目ではアセンブリを "[*トリミング*](../deploying/trim-self-contained.md)" から除外できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-468">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="f14e7-469">トリミングとは、パッケージ化されたアプリケーションからランタイムの未使用部分を削除するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f14e7-469">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="f14e7-470">必要な参照がトリミングによって間違って削除されることもあります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-470">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="f14e7-471">次の XML では、トリミングから `System.Security` アセンブリが除外されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-471">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="item-metadata"></a><span data-ttu-id="f14e7-472">項目メタデータ</span><span class="sxs-lookup"><span data-stu-id="f14e7-472">Item metadata</span></span>

<span data-ttu-id="f14e7-473">標準の [MSBuild 項目属性](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements)に加えて、次の項目メタデータ タグが .NET SDK によって利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-473">In addition to the standard [MSBuild item attributes](/visualstudio/msbuild/item-element-msbuild#attributes-and-elements), the following item metadata tags are made available by the .NET SDK:</span></span>

- [<span data-ttu-id="f14e7-474">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="f14e7-474">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="f14e7-475">LinkBase</span><span class="sxs-lookup"><span data-stu-id="f14e7-475">LinkBase</span></span>](#linkbase)

### <a name="copytopublishdirectory"></a><span data-ttu-id="f14e7-476">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="f14e7-476">CopyToPublishDirectory</span></span>

<span data-ttu-id="f14e7-477">MSBuild 項目の `CopyToPublishDirectory` メタデータにより、項目が発行ディレクトリにコピーされるタイミングが制御されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-477">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="f14e7-478">使用できる値は、項目が変更された場合にのみコピーする `PreserveNewest`、常に項目をコピーする `Always`、項目をコピーしない `Never` です。</span><span class="sxs-lookup"><span data-stu-id="f14e7-478">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="f14e7-479">パフォーマンスの観点からは、インクリメンタル ビルドが有効になるので `PreserveNewest` をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f14e7-479">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="f14e7-480">LinkBase</span><span class="sxs-lookup"><span data-stu-id="f14e7-480">LinkBase</span></span>

<span data-ttu-id="f14e7-481">プロジェクト ディレクトリとそのサブディレクトリの外部にある項目の場合、発行先で項目のコピー先を決定するために、項目の [Link メタデータ](/visualstudio/msbuild/common-msbuild-item-metadata)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-481">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="f14e7-482">また、プロジェクト ツリーの外部にある項目が Visual Studio の [ソリューション エクスプローラー] ウィンドウにどのように表示されるかも、`Link` によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-482">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="f14e7-483">プロジェクト コーンの外部にある項目に対して `Link` が指定されていない場合は、既定で `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` になります。</span><span class="sxs-lookup"><span data-stu-id="f14e7-483">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="f14e7-484">`LinkBase` を使用して、プロジェクト コーンの外部の項目に適切なベース フォルダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-484">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="f14e7-485">ベース フォルダーの下のフォルダー階層は、`RecursiveDir` によって保持されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-485">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="f14e7-486">`LinkBase` を指定しないと、それは `Link` パスから省略されます。</span><span class="sxs-lookup"><span data-stu-id="f14e7-486">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="f14e7-487">次の図は、前の項目の `Include` glob によって含められるファイルがソリューション エクスプローラーにどのように表示されるかを示したものです。</span><span class="sxs-lookup"><span data-stu-id="f14e7-487">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="LinkBase メタデータが指定された項目が表示されているソリューション エクスプローラー。":::

## <a name="see-also"></a><span data-ttu-id="f14e7-489">関連項目</span><span class="sxs-lookup"><span data-stu-id="f14e7-489">See also</span></span>

- [<span data-ttu-id="f14e7-490">MSBuild スキーマ リファレンス</span><span class="sxs-lookup"><span data-stu-id="f14e7-490">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="f14e7-491">MSBuild の共通プロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-491">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="f14e7-492">NuGet pack の MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-492">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="f14e7-493">NuGet restore の MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="f14e7-493">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="f14e7-494">ビルドのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="f14e7-494">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
