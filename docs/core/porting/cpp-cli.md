---
title: C++/CLI プロジェクトの .NET Core への移行
description: C++/CLI プロジェクトの .NET Core への移植について説明します。
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: 1194e1ce03e5b86052d7e2584aa5c15acd01874b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873693"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a><span data-ttu-id="730f5-103">C++/CLI プロジェクトを .NET Core に移植する方法</span><span class="sxs-lookup"><span data-stu-id="730f5-103">How to port a C++/CLI project to .NET Core</span></span>

<span data-ttu-id="730f5-104">.NET Core 3.1 以降および Visual Studio 2019 バージョン 16.4 以降では、[C++/CLI プロジェクト](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) で .NET Core をターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="730f5-104">Beginning with .NET Core 3.1 and Visual Studio 2019 version 16.4, [C++/CLI projects](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) can target .NET Core.</span></span> <span data-ttu-id="730f5-105">このサポートにより、Windows デスクトップ アプリケーションを、C++/CLI 相互運用層を使用して .NET Core に移植できるようになります。</span><span class="sxs-lookup"><span data-stu-id="730f5-105">This support makes it possible to port Windows desktop applications with C++/CLI interop layers to .NET Core.</span></span> <span data-ttu-id="730f5-106">この記事では、C++/CLI プロジェクトを .NET Framework から .NET Core 3.1 に移植する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="730f5-106">This article describes how to port C++/CLI projects from .NET Framework to .NET Core 3.1.</span></span>

## <a name="ccli-net-core-limitations"></a><span data-ttu-id="730f5-107">C++/CLI .NET Core の制限事項</span><span class="sxs-lookup"><span data-stu-id="730f5-107">C++/CLI .NET Core limitations</span></span>

<span data-ttu-id="730f5-108">他の言語と比較して、C++/CLI プロジェクトを .NET Core に移植する場合、いくつかの重要な制限があります。</span><span class="sxs-lookup"><span data-stu-id="730f5-108">There are some important limitations to porting C++/CLI projects to .NET Core compared to other languages:</span></span>

* <span data-ttu-id="730f5-109">.NET Core の C++/CLI サポートは Windows のみです。</span><span class="sxs-lookup"><span data-stu-id="730f5-109">C++/CLI support for .NET Core is Windows only.</span></span>
* <span data-ttu-id="730f5-110">C++/CLI プロジェクトで .NET Standard をターゲットにすることはできません。できるのは .NET Core (または .NET Framework) だけです。</span><span class="sxs-lookup"><span data-stu-id="730f5-110">C++/CLI projects can't target .NET Standard, only .NET Core (or .NET Framework).</span></span>
* <span data-ttu-id="730f5-111">C++/CLI プロジェクトでは、SDK スタイルの新しいプロジェクト ファイル形式はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="730f5-111">C++/CLI projects don't support the new SDK-style project file format.</span></span> <span data-ttu-id="730f5-112">代わりに、C++/CLI プロジェクトでは、.NET Core をターゲットにしている場合でも、既存の vcxproj ファイル形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="730f5-112">Instead, even when targeting .NET Core, C++/CLI projects use the existing vcxproj file format.</span></span>
* <span data-ttu-id="730f5-113">C++/CLI プロジェクトでは、複数の .NET プラットフォームをマルチターゲットに設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="730f5-113">C++/CLI projects can't multitarget multiple .NET platforms.</span></span> <span data-ttu-id="730f5-114">.NET Framework と .NET Core の両方に対して C++/CLI プロジェクトをビルドする必要がある場合は、個別のプロジェクト ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="730f5-114">If you need to build a C++/CLI project for both .NET Framework and .NET Core, use separate project files.</span></span>
* <span data-ttu-id="730f5-115">.NET Core では、`-clr:pure` または `-clr:safe` のコンパイルはサポートされておらず、新しい `-clr:netcore` オプション (.NET Framework の `-clr` に相当) のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="730f5-115">.NET Core doesn't support `-clr:pure` or `-clr:safe` compilation, only the new `-clr:netcore` option (which is equivalent to `-clr` for .NET Framework).</span></span>

## <a name="port-a-ccli-project"></a><span data-ttu-id="730f5-116">C++/CLI プロジェクトを移植する</span><span class="sxs-lookup"><span data-stu-id="730f5-116">Port a C++/CLI project</span></span>

<span data-ttu-id="730f5-117">C++/CLI プロジェクトを .NET Core に移植するには、次のように vcxproj ファイルに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="730f5-117">To port a C++/CLI project to .NET Core, make the following changes to the vcxproj file.</span></span> <span data-ttu-id="730f5-118">C++/CLI プロジェクトでは SDK スタイルのプロジェクト ファイルが使用されていないため、これらの移行手順は、他のプロジェクト タイプに必要な手順とは異なります。</span><span class="sxs-lookup"><span data-stu-id="730f5-118">These migration steps differ from the steps needed for other project types because C++/CLI projects don't use SDK-style project files.</span></span>

1. <span data-ttu-id="730f5-119">`<CLRSupport>true</CLRSupport>` プロパティを `<CLRSupport>NetCore</CLRSupport>` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="730f5-119">Replace `<CLRSupport>true</CLRSupport>` properties with `<CLRSupport>NetCore</CLRSupport>`.</span></span> <span data-ttu-id="730f5-120">このプロパティは、多くの場合、構成固有のプロパティ グループに含まれているため、場合によっては、複数箇所でこれを置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="730f5-120">This property is often in configuration-specific property groups, so you may need to replace it in multiple places.</span></span>
2. <span data-ttu-id="730f5-121">`<TargetFrameworkVersion>` プロパティを `<TargetFramework>netcoreapp3.1</TargetFramework>` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="730f5-121">Replace `<TargetFrameworkVersion>` properties with `<TargetFramework>netcoreapp3.1</TargetFramework>`.</span></span>
3. <span data-ttu-id="730f5-122">.NET Framework の参照 (`<Reference Include="System" />` など) をすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="730f5-122">Remove any .NET Framework references (like `<Reference Include="System" />`).</span></span> <span data-ttu-id="730f5-123">`<CLRSupport>NetCore</CLRSupport>` を使用すると、.NET Core SDK アセンブリが自動的に参照されます。</span><span class="sxs-lookup"><span data-stu-id="730f5-123">.NET Core SDK assemblies are automatically referenced when using `<CLRSupport>NetCore</CLRSupport>`.</span></span>
4. <span data-ttu-id="730f5-124">必要に応じて、cpp ファイルの API 使用状況を更新して、.NET Core で使用できない API を削除します。</span><span class="sxs-lookup"><span data-stu-id="730f5-124">Update API usage in cpp files, as necessary, to remove APIs unavailable to .NET Core.</span></span> <span data-ttu-id="730f5-125">C++/CLI プロジェクトはかなり薄い相互運用層になる傾向があるため、多くの変更が必要になることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="730f5-125">Because C++/CLI projects tend to be fairly thin interop layers, there are often not many changes needed.</span></span> <span data-ttu-id="730f5-126">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) を使用すると、純粋なマネージド バイナリと同じように、C++/CLI バイナリで使用されるサポートされていない .NET API を識別できます。</span><span class="sxs-lookup"><span data-stu-id="730f5-126">The [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) can be used to identify unsupported .NET APIs used by C++/CLI binaries just as with purely managed binaries.</span></span> <span data-ttu-id="730f5-127">コードの移植性の判断と、.NET Core API で動作するプロジェクトの更新のガイドラインについては、[ライブラリの移植に関するガイダンス](./libraries.md#determine-portability)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="730f5-127">Guidelines for determining code portability and updating projects to work with .NET Core APIs are available in the [library porting guidance](./libraries.md#determine-portability).</span></span>

### <a name="wpf-and-windows-forms-usage"></a><span data-ttu-id="730f5-128">WPF と Windows フォームの使用方法</span><span class="sxs-lookup"><span data-stu-id="730f5-128">WPF and Windows Forms usage</span></span>

<span data-ttu-id="730f5-129">.NET Core C++/CLI プロジェクトでは、Windows フォーム API と WPF API を使用できます。</span><span class="sxs-lookup"><span data-stu-id="730f5-129">.NET Core C++/CLI projects can use Windows Forms and WPF APIs.</span></span> <span data-ttu-id="730f5-130">これらの Windows デスクトップ API を使用するには、明示的なフレームワーク参照を UI ライブラリに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="730f5-130">To use these Windows desktop APIs, you need to add explicit framework references to the UI libraries.</span></span> <span data-ttu-id="730f5-131">Windows デスクトップ API を使用する SDK スタイルのプロジェクトは、`Microsoft.NET.Sdk.WindowsDesktop` SDK を使用して、必要なフレームワーク ライブラリを自動的に参照します。</span><span class="sxs-lookup"><span data-stu-id="730f5-131">SDK-style projects that use Windows desktop APIs reference the necessary framework libraries automatically by using the `Microsoft.NET.Sdk.WindowsDesktop` SDK.</span></span> <span data-ttu-id="730f5-132">C++/CLI プロジェクトでは SDK スタイルのプロジェクト形式を使用していないため、.NET Core をターゲットにするときに、明示的なフレームワーク参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="730f5-132">Because C++/CLI projects don't use the SDK-style project format, they need to add explicit framework references when targeting .NET Core.</span></span>

<span data-ttu-id="730f5-133">Windows フォーム API を使用するには、次の参照を vcxproj ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="730f5-133">To use Windows Forms APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

<span data-ttu-id="730f5-134">WPF API を使用するには、次の参照を vcxproj ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="730f5-134">To use WPF APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

<span data-ttu-id="730f5-135">Windows フォーム API と WPF API の両方を使用するには、次の参照を vcxproj ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="730f5-135">To use both Windows Forms and WPF APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

<span data-ttu-id="730f5-136">現時点では、Visual Studio の参照マネージャーを使用してこれらの参照を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="730f5-136">Currently, it's not possible to add these references using Visual Studio's reference manager.</span></span> <span data-ttu-id="730f5-137">代わりに、プロジェクト ファイルを手動で更新します。</span><span class="sxs-lookup"><span data-stu-id="730f5-137">Instead, update the project file manually.</span></span> <span data-ttu-id="730f5-138">この更新は、Visual Studio でプロジェクトをアンロードしてからプロジェクト ファイルを編集することによって行うことができます。</span><span class="sxs-lookup"><span data-stu-id="730f5-138">This update can be done in Visual Studio by unloading the project and then editing the project file.</span></span> <span data-ttu-id="730f5-139">VS Code などの別のエディターを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="730f5-139">You can also use another editor like VS Code.</span></span>

## <a name="build-without-msbuild"></a><span data-ttu-id="730f5-140">MSBuild なしでビルドする</span><span class="sxs-lookup"><span data-stu-id="730f5-140">Build without MSBuild</span></span>

<span data-ttu-id="730f5-141">MSBuild を使用せずに C++/CLI プロジェクトをビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="730f5-141">It's also possible to build C++/CLI projects without using MSBuild.</span></span> <span data-ttu-id="730f5-142">次の手順に従って、*cl.exe* と *link.exe* を使用して、.NET Core 向けの C++/CLI プロジェクトを直接ビルドします。</span><span class="sxs-lookup"><span data-stu-id="730f5-142">Follow these steps to build a C++/CLI project for .NET Core directly with *cl.exe* and *link.exe*:</span></span>

1. <span data-ttu-id="730f5-143">コンパイル時に、*cl.exe* に `-clr:netcore` を渡します。</span><span class="sxs-lookup"><span data-stu-id="730f5-143">When compiling, pass `-clr:netcore` to *cl.exe*.</span></span>
2. <span data-ttu-id="730f5-144">必要な .NET Core 参照アセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="730f5-144">Reference necessary .NET Core reference assemblies.</span></span>
3. <span data-ttu-id="730f5-145">リンクするときに、.NET Core アプリのホスト ディレクトリを `LibPath` として指定します (*ijwhost.lib* が検出されるようにします)。</span><span class="sxs-lookup"><span data-stu-id="730f5-145">When linking, provide the .NET Core app host directory as a `LibPath` (so that *ijwhost.lib* can be found).</span></span>
4. <span data-ttu-id="730f5-146">*ijwhost.dll* を (.NET Core アプリのホスト ディレクトリから) プロジェクトの出力ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="730f5-146">Copy *ijwhost.dll* (from the .NET Core app host directory) to the project's output directory.</span></span>
5. <span data-ttu-id="730f5-147">マネージド コードを実行するアプリケーションの最初のコンポーネント用に [runtimeconfig. json](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) ファイルが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="730f5-147">Make sure a [runtimeconfig.json](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) file exists for the first component of the application that will run managed code.</span></span> <span data-ttu-id="730f5-148">アプリケーションにマネージド エントリ ポイントがある場合は、`runtime.config` ファイルが自動的に作成されてコピーされます。</span><span class="sxs-lookup"><span data-stu-id="730f5-148">If the application has a managed entry point, a `runtime.config` file will be created and copied automatically.</span></span> <span data-ttu-id="730f5-149">ただし、アプリケーションにネイティブ エントリ ポイントがある場合は、NET Core ランタイムを使用するために最初の C++/CLI ライブラリ用に `runtimeconfig.json` ファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="730f5-149">If the application has a native entry point, though, you need to create a `runtimeconfig.json` file for the first C++/CLI library to use the .NET Core runtime.</span></span>

## <a name="known-issues"></a><span data-ttu-id="730f5-150">既知の問題</span><span class="sxs-lookup"><span data-stu-id="730f5-150">Known issues</span></span>

<span data-ttu-id="730f5-151">.NET Core をターゲットとする C++/CLI プロジェクトを使用する場合は、注意すべき既知の問題がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="730f5-151">There are a couple known issues to look out for when working with C++/CLI projects targeting .NET Core.</span></span>

* <span data-ttu-id="730f5-152">.NET Core C++/CLI プロジェクトの WPF フレームワーク参照では、現在、シンボルをインポートできないという無関係な警告がいくつか発生しています。</span><span class="sxs-lookup"><span data-stu-id="730f5-152">A WPF framework reference in .NET Core C++/CLI projects currently causes some extraneous warnings about being unable to import symbols.</span></span> <span data-ttu-id="730f5-153">これらの警告は無視してかまいません。まもなく修正されるはずです。</span><span class="sxs-lookup"><span data-stu-id="730f5-153">These warnings can be safely ignored and should be fixed soon.</span></span>
* <span data-ttu-id="730f5-154">アプリケーションにネイティブ エントリ ポイントがある場合、最初にマネージド コードを実行する C++/CLI ライブラリには [runtimeconfig.json](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="730f5-154">If the application has a native entry point, the C++/CLI library that first executes managed code needs a [runtimeconfig.json](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) file.</span></span> <span data-ttu-id="730f5-155">この構成ファイルは、.NET Core ランタイムの起動時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="730f5-155">This config file is used when the .NET Core runtime starts.</span></span> <span data-ttu-id="730f5-156">C++/CLI プロジェクトでは、ビルド時に `runtimeconfig.json` ファイルが自動的に作成されないため、このファイルを手動で生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="730f5-156">C++/CLI projects don't create `runtimeconfig.json` files automatically at build time yet, so the file must be generated manually.</span></span> <span data-ttu-id="730f5-157">C++/CLI ライブラリがマネージド エントリ ポイントから呼び出された場合、その C++/CLI ライブラリには `runtimeconfig.json` ファイルは必要ありません (ランタイムの起動時に使用されるものがエントリ ポイント アセンブリに含まれているため)。</span><span class="sxs-lookup"><span data-stu-id="730f5-157">If a C++/CLI library is called from a managed entry point, then the C++/CLI library doesn't need a `runtimeconfig.json` file (since the entry point assembly will have one that is used when starting the runtime).</span></span> <span data-ttu-id="730f5-158">簡単なサンプルの `runtimeconfig.json` ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="730f5-158">A simple sample `runtimeconfig.json` file is shown below.</span></span> <span data-ttu-id="730f5-159">詳しくは、[GitHub で仕様](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="730f5-159">For more information, see the [spec on GitHub](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md).</span></span>

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
