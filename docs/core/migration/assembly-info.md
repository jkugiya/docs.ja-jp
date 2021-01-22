---
title: AssemblyInfo プロパティ
description: アセンブリ属性と、それらが .NET Core 2.1 以降のバージョンでの MSBuild プロパティとどのように対応するかについて説明します。
ms.topic: reference
ms.date: 01/08/2021
ms.openlocfilehash: a2c431b3fe3da428f21582624ca5f357887e2815
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192874"
---
# <a name="map-assemblyinfo-attributes-to-properties"></a><span data-ttu-id="5536d-103">AssemblyInfo 属性をプロパティにマップする</span><span class="sxs-lookup"><span data-stu-id="5536d-103">Map AssemblyInfo attributes to properties</span></span>

<span data-ttu-id="5536d-104">.NET Core 2.0 以前のバージョンにおいて *AssemblyInfo* ファイルに通常存在していた[アセンブリ属性](../../standard/assembly/set-attributes.md)は、.NET Core 2.1 以降では、MSBuild プロパティから自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="5536d-104">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file in .NET Core 2.0 and earlier versions are automatically generated from MSBuild properties, starting in .NET Core 2.1.</span></span>

## <a name="properties-per-attribute"></a><span data-ttu-id="5536d-105">属性ごとのプロパティ</span><span class="sxs-lookup"><span data-stu-id="5536d-105">Properties per attribute</span></span>

<span data-ttu-id="5536d-106">次の表に示すように、各属性にはその内容を制御する対応するプロパティと、その生成を無効にする別のものがあります。</span><span class="sxs-lookup"><span data-stu-id="5536d-106">As shown in the following table, each attribute has a corresponding property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="5536d-107">属性</span><span class="sxs-lookup"><span data-stu-id="5536d-107">Attribute</span></span>                                                      | <span data-ttu-id="5536d-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5536d-108">Property</span></span>               | <span data-ttu-id="5536d-109">無効にするプロパティ</span><span class="sxs-lookup"><span data-stu-id="5536d-109">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="5536d-110">メモ:</span><span class="sxs-lookup"><span data-stu-id="5536d-110">Notes:</span></span>

- <span data-ttu-id="5536d-111">`AssemblyVersion` と `FileVersion` の既定値は、サフィックスのない `$(Version)` の値です。</span><span class="sxs-lookup"><span data-stu-id="5536d-111">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="5536d-112">たとえば、`$(Version)` が `1.2.3-beta.4` の場合、値は `1.2.3` です。</span><span class="sxs-lookup"><span data-stu-id="5536d-112">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="5536d-113">`InformationalVersion` の既定値は、`$(Version)` の値です。</span><span class="sxs-lookup"><span data-stu-id="5536d-113">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="5536d-114">`$(SourceRevisionId)` プロパティが存在する場合は、それが `InformationalVersion` の後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="5536d-114">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="5536d-115">`IncludeSourceRevisionInInformationalVersion` を使用して、この動作を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5536d-115">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="5536d-116">NuGet メタデータには、`Copyright` および `Description` プロパティも使用されます。</span><span class="sxs-lookup"><span data-stu-id="5536d-116">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="5536d-117">`Configuration` (既定値は `Debug`) は、すべての MSBuild ターゲットと共有されます。</span><span class="sxs-lookup"><span data-stu-id="5536d-117">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="5536d-118">これは、`dotnet` コマンド ([dotnet pack](../tools/dotnet-pack.md) など) の `--configuration` オプションを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="5536d-118">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>

## <a name="generateassemblyinfo"></a><span data-ttu-id="5536d-119">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="5536d-119">GenerateAssemblyInfo</span></span>

<span data-ttu-id="5536d-120">AssemblyInfo の生成を有効または無効にするブール値。</span><span class="sxs-lookup"><span data-stu-id="5536d-120">A Boolean that enables or disables the AssemblyInfo generation.</span></span> <span data-ttu-id="5536d-121">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="5536d-121">The default value is `true`.</span></span>

## <a name="generatedassemblyinfofile"></a><span data-ttu-id="5536d-122">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="5536d-122">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="5536d-123">生成されるアセンブリ情報ファイルの相対パスまたは絶対パス。</span><span class="sxs-lookup"><span data-stu-id="5536d-123">The relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="5536d-124">既定値は、`$(IntermediateOutputPath)` (*obj*) ディレクトリ内の *[プロジェクト名].AssemblyInfo.[cs|vb]* という名前のファイルです。</span><span class="sxs-lookup"><span data-stu-id="5536d-124">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (*obj*) directory.</span></span>
