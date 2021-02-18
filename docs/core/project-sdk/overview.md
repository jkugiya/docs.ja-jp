---
title: .NET プロジェクト SDK の概要
titleSuffix: ''
description: .NET プロジェクト SDK について説明します。
ms.date: 09/17/2020
ms.topic: conceptual
no-loc:
- EmbeddedResource
- Compile
- None
ms.openlocfilehash: e5a6d0a1c988818e507936b567fa0188675cedc3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432648"
---
# <a name="net-project-sdks"></a><span data-ttu-id="04a73-103">.NET プロジェクト SDK</span><span class="sxs-lookup"><span data-stu-id="04a73-103">.NET project SDKs</span></span>

<span data-ttu-id="04a73-104">.NET Core および .NET 5.0 以降のプロジェクトは、ソフトウェア開発キット (SDK) に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="04a73-104">.NET Core and .NET 5.0 and later projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="04a73-105">各 "*プロジェクト SDK*" は、MSBuild [ターゲット](/visualstudio/msbuild/msbuild-targets)と、コードのコンパイル、パッキング、発行を行う関連する [タスク](/visualstudio/msbuild/msbuild-tasks)のセットです。</span><span class="sxs-lookup"><span data-stu-id="04a73-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="04a73-106">プロジェクト SDK を参照するプロジェクトは、"*SDK スタイルのプロジェクト*" と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="04a73-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="04a73-107">使用可能な SDK</span><span class="sxs-lookup"><span data-stu-id="04a73-107">Available SDKs</span></span>

<span data-ttu-id="04a73-108">次の SDK を利用できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-108">The following SDKs are available:</span></span>

| <span data-ttu-id="04a73-109">ID</span><span class="sxs-lookup"><span data-stu-id="04a73-109">ID</span></span> | <span data-ttu-id="04a73-110">説明</span><span class="sxs-lookup"><span data-stu-id="04a73-110">Description</span></span> | <span data-ttu-id="04a73-111">リポジトリ</span><span class="sxs-lookup"><span data-stu-id="04a73-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="04a73-112">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="04a73-112">The .NET SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="04a73-113">.NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="04a73-113">The .NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="04a73-114">.NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="04a73-114">The .NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="04a73-115">.NET Worker Service SDK</span><span class="sxs-lookup"><span data-stu-id="04a73-115">The .NET Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="04a73-116">.NET [デスクトップ SDK](msbuild-props-desktop.md)。これには Windows フォーム (WinForms) と Windows Presentation Foundation (WPF) が含まれています。\*</span><span class="sxs-lookup"><span data-stu-id="04a73-116">The .NET [Desktop SDK](msbuild-props-desktop.md), which includes Windows Forms (WinForms) and Windows Presentation Foundation (WPF).\*</span></span> | <span data-ttu-id="04a73-117"><https://github.com/dotnet/winforms> および <https://github.com/dotnet/wpf></span><span class="sxs-lookup"><span data-stu-id="04a73-117"><https://github.com/dotnet/winforms> and <https://github.com/dotnet/wpf></span></span> |

<span data-ttu-id="04a73-118">.NET SDK は、.NET の基本 SDK です。</span><span class="sxs-lookup"><span data-stu-id="04a73-118">The .NET SDK is the base SDK for .NET.</span></span> <span data-ttu-id="04a73-119">その他の SDK からは .NET SDK が参照され、その他の SDK に関連付けられているプロジェクトでは、すべての .NET SDK プロパティが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="04a73-119">The other SDKs reference the .NET SDK, and projects that are associated with the other SDKs have all the .NET SDK properties available to them.</span></span> <span data-ttu-id="04a73-120">たとえば、Web SDK は、.NET SDK と Razor SDK の両方に依存しています。</span><span class="sxs-lookup"><span data-stu-id="04a73-120">The Web SDK, for example, depends on both the .NET SDK and the Razor SDK.</span></span>

<span data-ttu-id="04a73-121">NuGet を使用して配布できる独自の SDK を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="04a73-121">You can also author your own SDK that can be distributed via NuGet.</span></span>

<span data-ttu-id="04a73-122">\* .NET 5.0 以降、Windows フォームおよび Windows Presentation Foundation (WPF) プロジェクトでは、`Microsoft.NET.Sdk.WindowsDesktop` ではなく .NET SDK (`Microsoft.NET.Sdk`) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04a73-122">\* Starting in .NET 5.0, Windows Forms and Windows Presentation Foundation (WPF) projects should specify the .NET SDK (`Microsoft.NET.Sdk`) instead of `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="04a73-123">これらのプロジェクトでは、`TargetFramework` を `net5.0-windows` に、`UseWPF` または `UseWindowsForms` を `true` に設定することで、Windows デスクトップ SDK が自動的にインポートされます。</span><span class="sxs-lookup"><span data-stu-id="04a73-123">For these projects, setting `TargetFramework` to `net5.0-windows` and `UseWPF` or `UseWindowsForms` to `true` will automatically import the Windows desktop SDK.</span></span> <span data-ttu-id="04a73-124">プロジェクトで .NET 5.0 以降をターゲットとし、`Microsoft.NET.Sdk.WindowsDesktop` SDK を指定すると、ビルド警告 NETSDK1137 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-124">If your project targets .NET 5.0 or later and specifies the `Microsoft.NET.Sdk.WindowsDesktop` SDK, you'll get build warning NETSDK1137.</span></span>

## <a name="project-files"></a><span data-ttu-id="04a73-125">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="04a73-125">Project files</span></span>

<span data-ttu-id="04a73-126">.NET プロジェクトは、[MSBuild](/visualstudio/msbuild/msbuild) 形式に基づいています。</span><span class="sxs-lookup"><span data-stu-id="04a73-126">.NET projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="04a73-127">プロジェクト ファイルは、C# プロジェクトでは *.csproj*、F# プロジェクトでは *.fsproj* のような拡張子が付いていて、XML 形式です。</span><span class="sxs-lookup"><span data-stu-id="04a73-127">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="04a73-128">MSBuild プロジェクト ファイルのルート要素は、[Project](/visualstudio/msbuild/project-element-msbuild) 要素です。</span><span class="sxs-lookup"><span data-stu-id="04a73-128">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="04a73-129">`Project` 要素には、使用する SDK (およびバージョン) を指定する省略可能な `Sdk` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="04a73-129">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="04a73-130">.NET ツールを使用してコードをビルドするには、`Sdk` 属性を、「[使用可能な SDK](#available-sdks)」の表にあるいずれかの ID に設定します。</span><span class="sxs-lookup"><span data-stu-id="04a73-130">To use the .NET tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="04a73-131">NuGet から取得した SDK を指定するには、名前の末尾にバージョンを含めるか、*global.json* ファイルに名前とバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="04a73-131">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="04a73-132">SDK を指定する別の方法として、トップレベルの [SDK](/visualstudio/msbuild/sdk-element-msbuild) 要素を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="04a73-132">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="04a73-133">これらの方法のいずれかで SDK を参照すると、.NET のプロジェクト ファイルが大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-133">Referencing an SDK in one of these ways greatly simplifies project files for .NET.</span></span> <span data-ttu-id="04a73-134">プロジェクトの評価中に、MSBuild によってプロジェクト ファイルの先頭に `Sdk.props` の暗黙的なインポートと、末尾に `Sdk.targets` の暗黙的なインポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-134">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="04a73-135">Windows コンピューターでは、*Sdk.props* ファイルと *Sdk.targets* ファイルは *%ProgramFiles%\dotnet\sdk\\[バージョン]\Sdks\Microsoft.NET.Sdk\Sdk* フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="04a73-135">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="04a73-136">プロジェクト ファイルの前処理</span><span class="sxs-lookup"><span data-stu-id="04a73-136">Preprocess the project file</span></span>

<span data-ttu-id="04a73-137">MSBuild では、`dotnet msbuild -preprocess` コマンドを使用して、SDK とそのターゲットが取り込まれた後の完全に展開されたプロジェクトがどのようになるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-137">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="04a73-138">[`dotnet msbuild`](../tools/dotnet-msbuild.md) コマンドの [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) スイッチによって、インポートされるファイル、そのソース、ビルドに対するそのコントリビューションが、実際にプロジェクトをビルドすることなく、表示されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-138">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="04a73-139">プロジェクトにターゲット フレームワークが複数存在する場合は、1 つのフレームワークだけにコマンドの結果を集中させてください。そのためには、そのフレームワークを MSBuild プロパティとして指定します。</span><span class="sxs-lookup"><span data-stu-id="04a73-139">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="04a73-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="04a73-140">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

## <a name="default-includes-and-excludes"></a><span data-ttu-id="04a73-141">既定で含まれるものと除外されるもの</span><span class="sxs-lookup"><span data-stu-id="04a73-141">Default includes and excludes</span></span>

<span data-ttu-id="04a73-142">[`Compile` 項目](/visualstudio/msbuild/common-msbuild-project-items#compile)、[埋め込みリソース](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource)、[`None` 項目](/visualstudio/msbuild/common-msbuild-project-items#none)に既定で含まれるものと除外されるものが SDK で定義されています。</span><span class="sxs-lookup"><span data-stu-id="04a73-142">The default includes and excludes for [`Compile` items](/visualstudio/msbuild/common-msbuild-project-items#compile), [embedded resources](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource), and [`None` items](/visualstudio/msbuild/common-msbuild-project-items#none) are defined in the SDK.</span></span> <span data-ttu-id="04a73-143">SDK 以外の .NET Framework プロジェクトとは異なり、既定値がほとんどの一般的なユース ケースに対応しているため、これらの項目をプロジェクト ファイルで指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="04a73-143">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="04a73-144">この動作により、プロジェクト ファイルのサイズがより小さく、より簡単に理解できるようになり、必要に応じて手作業で編集できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-144">This behavior makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="04a73-145">次の表は、.NET SDK に組み込まれる、および除外される要素と [glob](https://en.wikipedia.org/wiki/Glob_(programming)) の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="04a73-145">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET SDK:</span></span>

| <span data-ttu-id="04a73-146">要素</span><span class="sxs-lookup"><span data-stu-id="04a73-146">Element</span></span>           | <span data-ttu-id="04a73-147">含まれる glob</span><span class="sxs-lookup"><span data-stu-id="04a73-147">Include glob</span></span>                              | <span data-ttu-id="04a73-148">除外される glob</span><span class="sxs-lookup"><span data-stu-id="04a73-148">Exclude glob</span></span>                                                  | <span data-ttu-id="04a73-149">glob の削除</span><span class="sxs-lookup"><span data-stu-id="04a73-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compile           | <span data-ttu-id="04a73-150">\*\*/\*.cs (または他の言語拡張機能)</span><span class="sxs-lookup"><span data-stu-id="04a73-150">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="04a73-151">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="04a73-151">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="04a73-152">N/A</span><span class="sxs-lookup"><span data-stu-id="04a73-152">N/A</span></span>                      |
| EmbeddedResource  | <span data-ttu-id="04a73-153">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="04a73-153">\*\*/\*.resx</span></span>                              | <span data-ttu-id="04a73-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="04a73-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="04a73-155">N/A</span><span class="sxs-lookup"><span data-stu-id="04a73-155">N/A</span></span>                      |
| None              | \*\*/\*                                   | <span data-ttu-id="04a73-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="04a73-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="04a73-157">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="04a73-157">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="04a73-158">`./bin` フォルダーと `./obj` フォルダーは、`$(BaseOutputPath)` と `$(BaseIntermediateOutputPath)` の MSBuild プロパティによって表され、既定で glob から除外されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-158">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="04a73-159">除外されるものは、[DefaultItemExcludes プロパティ](msbuild-props.md#defaultitemexcludes)によって表されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-159">Excludes are represented by the [DefaultItemExcludes property](msbuild-props.md#defaultitemexcludes).</span></span>

<span data-ttu-id="04a73-160">.NET デスクトップ SDK には、さらに多くの WPF に含まれるものと除外されるものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="04a73-160">The .NET Desktop SDK has more includes and excludes for WPF.</span></span> <span data-ttu-id="04a73-161">詳細については、「[WPF に含まれるものと除外されるもの](msbuild-props-desktop.md#wpf-default-includes-and-excludes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04a73-161">For more information, see [WPF default includes and excludes](msbuild-props-desktop.md#wpf-default-includes-and-excludes).</span></span>

### <a name="build-errors"></a><span data-ttu-id="04a73-162">ビルド エラー</span><span class="sxs-lookup"><span data-stu-id="04a73-162">Build errors</span></span>

<span data-ttu-id="04a73-163">これらの項目をプロジェクト ファイルに明示的に定義すると、次のような "NETSDK1022" ビルド エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04a73-163">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

> <span data-ttu-id="04a73-164">重複する 'Compile' 項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="04a73-164">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="04a73-165">.NET SDK には、既定でプロジェクト ディレクトリの 'Compile' 項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="04a73-165">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="04a73-166">これらの項目をプロジェクト ファイルから削除するか、プロジェクト ファイルに明示的に含める場合は 'EnableDefaultCompileItems' プロパティを 'false' に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-166">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

> <span data-ttu-id="04a73-167">重複する 'EmbeddedResource' 項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="04a73-167">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="04a73-168">.NET SDK には、既定でプロジェクト ディレクトリの 'EmbeddedResource' 項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="04a73-168">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="04a73-169">これらの項目をプロジェクト ファイルから削除するか、プロジェクト ファイルに明示的に含める場合は 'EnableDefaultEmbeddedResourceItems' プロパティを 'false' に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-169">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="04a73-170">このエラーを解決するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="04a73-170">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="04a73-171">前の表に列挙されている暗黙的な項目と一致する明示的な `Compile`、`EmbeddedResource`、または `None` の項目を削除します。</span><span class="sxs-lookup"><span data-stu-id="04a73-171">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="04a73-172">暗黙的なファイルの組み込みをすべて無効にするには、[EnableDefaultItems プロパティ](msbuild-props.md#enabledefaultitems)を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="04a73-172">Set the [EnableDefaultItems property](msbuild-props.md#enabledefaultitems) to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="04a73-173">アプリで発行する一部のファイルを指定する必要がある場合は、そのために既知の MSBuild のしくみ (たとえば `Content` 要素) を引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-173">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="04a73-174">`Compile`、`EmbeddedResource`、または `None` glob のみを選択的に無効にするには、[EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems)、[EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems)、または [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) のプロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="04a73-174">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems), or [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="04a73-175">`Compile` glob のみを無効にすると、Visual Studio のソリューション エクスプローラーに \*.cs 項目がプロジェクトの一部として (`None` 項目として組み込まれて) 引き続き表示されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-175">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="04a73-176">暗黙的な `None` glob を無効にするには、`EnableDefaultNoneItems` も `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="04a73-176">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="04a73-177">暗黙的なパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="04a73-177">Implicit package references</span></span>

<span data-ttu-id="04a73-178">.NET Core 1.0 から 2.2 または .NET Standard 1.0 から 2.0 をターゲットとする場合、.NET SDK により、特定の *メタパッケージ* への暗黙的な参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-178">When targeting .NET Core 1.0 - 2.2 or .NET Standard 1.0 - 2.0, the .NET SDK adds implicit references to certain *metapackages*.</span></span> <span data-ttu-id="04a73-179">メタパッケージは、他のパッケージの依存関係のみで構成されるフレームワーク ベースのパッケージです。</span><span class="sxs-lookup"><span data-stu-id="04a73-179">A metapackage is a framework-based package that consists only of dependencies on other packages.</span></span> <span data-ttu-id="04a73-180">メタパッケージは、プロジェクト ファイルの [TargetFramework](msbuild-props.md#targetframework) または [TargetFrameworks](msbuild-props.md#targetframeworks) プロパティで指定されたターゲット フレームワークに基づいて暗黙的に参照されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-180">Metapackages are implicitly referenced based on the target framework(s) specified in the [TargetFramework](msbuild-props.md#targetframework) or [TargetFrameworks](msbuild-props.md#targetframeworks) property of your project file.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp2.1</TargetFramework>
</PropertyGroup>
```

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="04a73-181">必要に応じて、[DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) プロパティを使用して暗黙的なパッケージ参照を無効にし、必要なフレームワークまたはパッケージのみに明示的な参照を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-181">If needed, you can disable implicit package references using the [DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) property, and add explicit references to just the frameworks or packages you need.</span></span>

<span data-ttu-id="04a73-182">推奨事項:</span><span class="sxs-lookup"><span data-stu-id="04a73-182">Recommendations:</span></span>

- <span data-ttu-id="04a73-183">.NET Framework、.NET Core 1.0 から 2.2、または .NET Standard 1.0 から 2.0 をターゲットとする場合は、プロジェクト ファイルの `<PackageReference>` アイテム経由で `Microsoft.NETCore.App` または `NETStandard.Library` メタパッケージを明示的に参照しないようにします。</span><span class="sxs-lookup"><span data-stu-id="04a73-183">When targeting .NET Framework, .NET Core 1.0 - 2.2, or .NET Standard 1.0 - 2.0, don't add an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span> <span data-ttu-id="04a73-184">.NET Core 1.0 から 2.2 および .NET Standard 1.0 から 2.0 のプロジェクトの場合、このようなメタパッケージは暗黙的に参照されます。</span><span class="sxs-lookup"><span data-stu-id="04a73-184">For .NET Core 1.0 - 2.2 and .NET Standard 1.0 - 2.0 projects, these metapackages are implicitly referenced.</span></span> <span data-ttu-id="04a73-185">.NET Framework プロジェクトの場合、.NET Standard ベースの NuGet パッケージを使用する場合、何らかのバージョンの `NETStandard.Library` が必要であれば、NuGet はそのバージョンを自動的にインストールします。</span><span class="sxs-lookup"><span data-stu-id="04a73-185">For .NET Framework projects, if any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>
- <span data-ttu-id="04a73-186">.NET Core 1.0 から 2.2 をターゲットとする場合、特定バージョンのランタイムが必要であれば、メタパッケージを参照するのではなく、プロジェクト内で `<RuntimeFrameworkVersion>` プロパティを使用します (`1.0.4` など)。</span><span class="sxs-lookup"><span data-stu-id="04a73-186">If you need a specific version of the runtime when targeting .NET Core 1.0 - 2.2, use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span> <span data-ttu-id="04a73-187">たとえば、[自己完結の配置](../deploying/index.md#publish-self-contained)を使用している場合は、1.0.0 LTS ランタイムの特定のパッチ バージョンが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="04a73-187">For example, you might need a specific patch version of 1.0.0 LTS runtime if you're using [self-contained deployments](../deploying/index.md#publish-self-contained).</span></span>
- <span data-ttu-id="04a73-188">.NET Standard 1.0 から 2.0 をターゲットとする場合、特定バージョンの `NETStandard.Library` メタパッケージが必要であれば、`<NetStandardImplicitPackageVersion>` プロパティを使用し、必要なバージョンを設定できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-188">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard 1.0 - 2.0, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>

## <a name="build-events"></a><span data-ttu-id="04a73-189">ビルド イベント</span><span class="sxs-lookup"><span data-stu-id="04a73-189">Build events</span></span>

<span data-ttu-id="04a73-190">SDK スタイルのプロジェクトでは、`PreBuild` または `PostBuild` という名前の MSBuild ターゲットを使用し、`PreBuild` の `BeforeTargets` プロパティまたは `AfterTargets` の `PostBuild` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="04a73-190">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>
> - <span data-ttu-id="04a73-191">MSBuild ターゲットには任意の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-191">You can use any name for the MSBuild targets.</span></span> <span data-ttu-id="04a73-192">ただし、`PreBuild` および `PostBuild` ターゲットは Visual Studio IDE によって認識されるため、これらの名前を使用することにより、IDE でコマンドを編集できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-192">However, the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so by using those names, you can edit the commands in the IDE.</span></span>
> - <span data-ttu-id="04a73-193">`$(ProjectDir)` などのマクロが解決されないため、SDK スタイルのプロジェクトでは、プロパティ `PreBuildEvent` と `PostBuildEvent` は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="04a73-193">The properties `PreBuildEvent` and `PostBuildEvent` are not recommended in SDK-style projects, because macros such as `$(ProjectDir)` aren't resolved.</span></span> <span data-ttu-id="04a73-194">たとえば、次のようなコードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="04a73-194">For example, the following code is not supported:</span></span>
>
> ```xml
> <PropertyGroup>
>   <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
> </PropertyGroup>
> ```

## <a name="customize-the-build"></a><span data-ttu-id="04a73-195">ビルドのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="04a73-195">Customize the build</span></span>

<span data-ttu-id="04a73-196">[ビルドをカスタマイズする](/visualstudio/msbuild/customize-your-build)には、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="04a73-196">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="04a73-197">プロパティを引数として [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) または [dotnet](../tools/index.md) コマンドに渡すことによって、プロパティをオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-197">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="04a73-198">また、プロパティをプロジェクト ファイルに追加することや、*Directory.Build.props* ファイルに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-198">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="04a73-199">.NET プロジェクトの便利なプロパティの一覧については、「[.NET SDK プロジェクトの MSBuild リファレンス](msbuild-props.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="04a73-199">For a list of useful properties for .NET projects, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="04a73-200">カスタム ターゲット</span><span class="sxs-lookup"><span data-stu-id="04a73-200">Custom targets</span></span>

<span data-ttu-id="04a73-201">.NET プロジェクトでは、プロジェクトで使用するカスタムの MSBuild ターゲットとプロパティをパッケージ化し、そのパッケージをプロジェクトで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-201">.NET projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="04a73-202">この種の拡張機能を使用するのは、次の場合です。</span><span class="sxs-lookup"><span data-stu-id="04a73-202">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="04a73-203">ビルド処理を拡張する。</span><span class="sxs-lookup"><span data-stu-id="04a73-203">Extend the build process.</span></span>
- <span data-ttu-id="04a73-204">ビルド プロセスの成果物 (生成されたファイルなど) にアクセスする。</span><span class="sxs-lookup"><span data-stu-id="04a73-204">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="04a73-205">どのような構成でビルドが呼び出されるかを検査する。</span><span class="sxs-lookup"><span data-stu-id="04a73-205">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="04a73-206">カスタムのビルド ターゲットまたはプロパティを追加するには、プロジェクトの *build* フォルダーに `<package_id>.targets` または `<package_id>.props` の形式のファイル (たとえば `Contoso.Utility.UsefulStuff.targets`) を配置します。</span><span class="sxs-lookup"><span data-stu-id="04a73-206">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="04a73-207">次の XML は *.csproj* ファイルからのスニペットです。パッケージ化する対象を [`dotnet pack`](../tools/dotnet-pack.md) コマンドに指示しています。</span><span class="sxs-lookup"><span data-stu-id="04a73-207">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="04a73-208">`<ItemGroup Label="dotnet pack instructions">` 要素で、パッケージ内の *build* フォルダーにターゲット ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="04a73-208">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="04a73-209">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 要素で、アセンブリと *.json* ファイルを *build* フォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="04a73-209">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...

</Project>
```

<span data-ttu-id="04a73-210">プロジェクトでカスタム ターゲットを使用するには、パッケージとそのバージョンを指す `PackageReference` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="04a73-210">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="04a73-211">ツールとは異なり、カスタム ターゲットのパッケージは、それを使用するプロジェクトの依存関係クロージャに含まれます。</span><span class="sxs-lookup"><span data-stu-id="04a73-211">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="04a73-212">カスタム ターゲットの使用方法を構成できます。</span><span class="sxs-lookup"><span data-stu-id="04a73-212">You can configure how to use the custom target.</span></span> <span data-ttu-id="04a73-213">それは MSBuild ターゲットであるため、指定されたターゲットに依存することや、別のターゲットの後に実行したり、`dotnet msbuild -t:<target-name>` コマンドを使用して手動で呼び出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-213">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="04a73-214">ただし、優れたユーザー エクスペリエンスを提供するために、プロジェクトごとのツールとカスタム ターゲットを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-214">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="04a73-215">このシナリオでは、必要なすべてのパラメーターをプロジェクトごとのツールで受け取り、受け取ったパラメーターを、ターゲットを実行する必要な [`dotnet msbuild`](../tools/dotnet-msbuild.md) の呼び出しに変換します。</span><span class="sxs-lookup"><span data-stu-id="04a73-215">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="04a73-216">このような相乗効果のサンプルは、[`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) プロジェクトの「[MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016)」 (MVP Summit 2016 ハッカソンのサンプル) レポートで参照することができます。</span><span class="sxs-lookup"><span data-stu-id="04a73-216">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="04a73-217">関連項目</span><span class="sxs-lookup"><span data-stu-id="04a73-217">See also</span></span>

- [<span data-ttu-id="04a73-218">.NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="04a73-218">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="04a73-219">MSBuild プロジェクト SDK の使用方法</span><span class="sxs-lookup"><span data-stu-id="04a73-219">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="04a73-220">カスタムの MSBuild ターゲットとプロパティを NuGet でパッケージ化する</span><span class="sxs-lookup"><span data-stu-id="04a73-220">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
