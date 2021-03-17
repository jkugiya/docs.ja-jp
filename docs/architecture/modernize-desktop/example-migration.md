---
title: .NET 5 への移行の例
description: .NET Framework をターゲットとするサンプル アプリケーションを .NET 5 に移行する方法を示します。
ms.date: 01/19/2021
ms.openlocfilehash: 02a45859dfca891598e235e3de1ed968aefb5bf4
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605166"
---
# <a name="example-of-migrating-to-net"></a><span data-ttu-id="7e9e1-103">.NET への移行の例</span><span class="sxs-lookup"><span data-stu-id="7e9e1-103">Example of migrating to .NET</span></span>

<span data-ttu-id="7e9e1-104">この章では、.NET Framework から .NET への既存のアプリケーションの移行を実行する際に役立つ実用的なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET.</span></span>

<span data-ttu-id="7e9e1-105">従うことができる適切に構成されたプロセスと、各手順で考慮する必要がある最も重要なことを示します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="7e9e1-106">その後、WinForms と WPF の両方のバージョンからのサンプル デスクトップ アプリケーションのステップバイステップ移行プロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="7e9e1-107">移行プロセスの概要</span><span class="sxs-lookup"><span data-stu-id="7e9e1-107">Migration process overview</span></span>

<span data-ttu-id="7e9e1-108">移行プロセスは次の 4 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="7e9e1-109">**準備**: プロジェクトで先のことを見据えて考える必要がある依存関係について理解します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="7e9e1-110">この手順では、現在のプロジェクトを、移行の開始点を簡略化する状態にします。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="7e9e1-111">**プロジェクト ファイルを移行する:** .NET プロジェクトでは、SDK スタイルの新しいプロジェクト形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-111">**Migrate Project File:** .NET projects use the new SDK-style project format.</span></span> <span data-ttu-id="7e9e1-112">この形式で新しいプロジェクト ファイルを作成するか、SDK スタイルを使用する必要があるものを更新します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="7e9e1-113">**コードを修正してビルドする:** .NET でコードをビルドし、.NET Framework と .NET の API レベルの違いに対処します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-113">**Fix code and build:** Build the code in .NET addressing API-level differences between .NET Framework and .NET.</span></span> <span data-ttu-id="7e9e1-114">必要に応じて、サードパーティのパッケージを、.NET をサポートするものに更新します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-114">If needed, update third-party packages to the ones that support .NET.</span></span>

4. <span data-ttu-id="7e9e1-115">**実行してテストする:** 実行時まで現れない違いがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="7e9e1-116">そのため、必ずアプリケーションを実行し、すべてが期待どおりに動作することをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="7e9e1-117">準備</span><span class="sxs-lookup"><span data-stu-id="7e9e1-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="7e9e1-118">packages.config ファイルを移行する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-118">Migrate packages.config file</span></span>

<span data-ttu-id="7e9e1-119">.NET Framework アプリケーションでは、外部パッケージへのすべての参照が *packages.config* ファイルで宣言されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="7e9e1-120">.NET では、*packages.config* ファイルを使用する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-120">In .NET, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="7e9e1-121">代わりに、プロジェクト ファイル内で [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) プロパティを使用して、ご利用のアプリの NuGet パッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="7e9e1-122">そのため、形式間の移行が必要になります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="7e9e1-123">手動で更新するには、*packages.config* ファイルに含まれている依存関係を取得し、`PackageReference` という形式でプロジェクト ファイルに移行します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="7e9e1-124">または、Visual Studio で自動的に作業が行われるようにすることができます。その場合は、*packages.config* ファイルを右クリックし、 **[packages.config を PackageReference に移行する]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net"></a><span data-ttu-id="7e9e1-125">.NET のすべての依存関係の互換性を確認する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-125">Verify every dependency compatibility in .NET</span></span>

<span data-ttu-id="7e9e1-126">パッケージ参照を移行したら、各参照に互換性があるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="7e9e1-127">[nuget.org](https://www.nuget.org/) で、アプリケーションによって使用される各 NuGet パッケージの依存関係を調べることができます。そのパッケージに .NET Standard の依存関係がある場合は、.NET 5.0 で機能します。.NET ではすべてのバージョンの .NET Standard が[サポートされる](../../standard/net-standard.md#net-implementation-support)ためです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET 5.0 because .NET [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="7e9e1-128">次の画像には、`Castle.Windsor` パッケージの依存関係が示されています。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Castle.Windsor パッケージの NuGet 依存関係のスクリーンショット](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="7e9e1-130">パッケージの互換性を確認するために、バージョンと依存関係に関するより詳細な情報を提供するツール <https://fuget.org> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="7e9e1-131">.NET をサポートしていない古いバージョンのパッケージがプロジェクトで参照されている可能性がありますが、それをサポートする新しいバージョンが見つかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-131">Maybe the project is referencing older package versions that don't support .NET, but you might find newer versions that do support it.</span></span> <span data-ttu-id="7e9e1-132">そのため、通常はパッケージを新しいバージョンに更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="7e9e1-133">しかし、パッケージ バージョンを更新すると、コードの更新を強制するいくつかの破壊的変更が発生する場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="7e9e1-134">互換性のあるバージョンが見つからない場合はどうなりますか。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="7e9e1-135">これらの破壊的変更のため、パッケージのバージョンを更新したくない場合はどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="7e9e1-136">.NET アプリケーションの .NET Framework パッケージに依存する可能性があるため、心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET application.</span></span> <span data-ttu-id="7e9e1-137">外部パッケージにより .NET で使用できない API が呼び出されると、実行時エラーが発生する可能性があるため、必ずテストしてください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET.</span></span> <span data-ttu-id="7e9e1-138">これは、更新する予定のない古いパッケージを使用しており、.NET で作業するために再ターゲットするだけで済む場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="7e9e1-139">API の互換性を確認する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-139">Check for API compatibility</span></span>

<span data-ttu-id="7e9e1-140">.NET Framework と .NET の API サーフェイスは似ていますが、同一ではないため、.NET で使用できる API とできないものを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-140">Since the API surface in .NET Framework and .NET is similar but not identical, you must check which APIs are available on .NET and which aren't.</span></span> <span data-ttu-id="7e9e1-141">.NET Portability Analyzer ツールを利用すると、使用されている API のうち、.NET には存在しないものを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET.</span></span> <span data-ttu-id="7e9e1-142">アプリのバイナリ レベルが確認され、呼び出されたすべての API が抽出されてから、ターゲット フレームワーク (この場合は、.NET 5.0) で使用できない API が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET 5.0 in this case).</span></span>

<span data-ttu-id="7e9e1-143">このツールの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="7e9e1-144">このツールの興味深い点は、変更できない外部パッケージのコードではなく、独自のコードの違いのみが表示されることです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="7e9e1-145">.NET で動作するように、これらのパッケージのほとんどを更新しておく必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-145">Remember you should have updated most of these packages to make them work with .NET.</span></span>

### <a name="migrate-with-try-convert-tool"></a><span data-ttu-id="7e9e1-146">Try Convert ツールを使用して移行する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-146">Migrate with Try Convert tool</span></span>

<span data-ttu-id="7e9e1-147">[Try Convert](https://github.com/dotnet/try-convert/releases) ツールは、プロジェクトを移行するための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-147">The [Try Convert](https://github.com/dotnet/try-convert/releases) tool is a great way to migrate a project.</span></span> <span data-ttu-id="7e9e1-148">これはグローバル ツールであり、古いスタイルから新しい SDK スタイルへのプロジェクト ファイルのアップグレードの試行と、.NET 5 への適用可能なプロジェクトの再ターゲットが行われます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-148">It's a global tool that attempts to upgrade your project file from the old style to the new SDK style, and retargets applicable projects to .NET 5.</span></span> <span data-ttu-id="7e9e1-149">インストールが完了したら、次のコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-149">Once installed, you can run the following commands:</span></span>

```dotnetcli
try-convert -p "<path to your project file>"
```

<span data-ttu-id="7e9e1-150">または:</span><span class="sxs-lookup"><span data-stu-id="7e9e1-150">Or:</span></span>

```dotnetcli
try-convert -w "<path to your solution>"
```

> [!NOTE]
> <span data-ttu-id="7e9e1-151">try-convert ツールは、[.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)の一部として自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-151">The try-convert tool is run automatically as part of the [.NET Upgrade Assistant tool](https://aka.ms/dotnet-upgrade-assistant).</span></span> <span data-ttu-id="7e9e1-152">Try Convert だけでなく、完全な Upgrade Assistant の実行を検討してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-152">Consider running the full Upgrade Assistant and not just Try Convert.</span></span>

<span data-ttu-id="7e9e1-153">ツールにより変換が試行された後、Visual Studio にファイルを再度読み込み、実行してテストします。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-153">After the tool attempts the conversion, reload your files in Visual Studio to run and test.</span></span> <span data-ttu-id="7e9e1-154">プロジェクトの仕様によっては、Try Convert で変換を実行できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-154">There's a possibility that Try Convert won't be able to perform the conversion due to the specifics of your project.</span></span> <span data-ttu-id="7e9e1-155">その場合は、以下の手順を参照できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-155">In that case, you can refer the below steps.</span></span>

#### <a name="migrate-manually"></a><span data-ttu-id="7e9e1-156">手動で移行する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-156">Migrate manually</span></span>

1. <span data-ttu-id="7e9e1-157">新しい .NET プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-157">Create the new .NET project</span></span>

<span data-ttu-id="7e9e1-158">ほとんどの場合、既存のプロジェクトを新しい .NET 形式に更新したいと考えます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-158">In most cases, you'll want to update your existing project to the new .NET format.</span></span> <span data-ttu-id="7e9e1-159">しかし、古いプロジェクトを維持しながら新しいものを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-159">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="7e9e1-160">古いプロジェクトの更新の主な欠点は、デザイナーのサポートが失われることです。これは、お客様と開発チームにとって重要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-160">The main drawback from updating the old project is that you lose designer support, which may be important to you and your development team.</span></span> <span data-ttu-id="7e9e1-161">引き続きデザイナーを使用する場合は、古い .NET プロジェクトを維持しながら新しいものを作成し、資産を共有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-161">If you want to keep using the designer, you must create a new .NET project in parallel with the old one and share assets.</span></span> <span data-ttu-id="7e9e1-162">デザイナーで UI 要素を変更する必要がある場合は、古いプロジェクトに切り替えてそれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-162">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="7e9e1-163">また、資産はリンクされているため、.NET プロジェクトでも更新されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-163">And since assets are linked, they'll be updated in the .NET project as well.</span></span>

<span data-ttu-id="7e9e1-164">.NET の [SDK スタイルのプロジェクト](../../core/project-sdk/msbuild-props.md)は、.NET Framework のプロジェクト形式よりもはるかにシンプルです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-164">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="7e9e1-165">前述の `PackageReference` エントリとは別に、それ以上の操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-165">Apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="7e9e1-166">新しいプロジェクト形式には、`.cs` および `.xaml` ファイルなど、[既定で特定の拡張子を持つファイルが含まれており](../../core/project-sdk/overview.md#default-includes-and-excludes)、それらをプロジェクト ファイルに明示的に含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-166">The new project format [includes files with certain extensions by default](../../core/project-sdk/overview.md#default-includes-and-excludes), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="7e9e1-167">AssemblyInfo に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="7e9e1-167">AssemblyInfo considerations</span></span>

<span data-ttu-id="7e9e1-168">属性は .NET プロジェクトで自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-168">Attributes are autogenerated on .NET projects.</span></span> <span data-ttu-id="7e9e1-169">そのプロジェクトに *AssemblyInfo.cs* ファイルが含まれている場合は、定義が重複するため、コンパイルの競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-169">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="7e9e1-170">.NET プロジェクト ファイルに次のエントリを追加することで、古い *AssemblyInfo.cs* ファイルを削除したり、自動生成を無効にしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-170">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="7e9e1-171">リソース</span><span class="sxs-lookup"><span data-stu-id="7e9e1-171">Resources</span></span>

<span data-ttu-id="7e9e1-172">埋め込みリソースは自動的に含まれますが、リソースは含まれないため、そのリソースを新しいプロジェクト ファイルに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-172">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="7e9e1-173">パッケージ参照</span><span class="sxs-lookup"><span data-stu-id="7e9e1-173">Package references</span></span>

<span data-ttu-id="7e9e1-174">**[packages.config を PackageReference に移行する]** オプションを使用すると、前述のとおり、外部パッケージの参照を新しい形式に簡単に移動できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-174">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="7e9e1-175">パッケージ参照の更新</span><span class="sxs-lookup"><span data-stu-id="7e9e1-175">Update package references</span></span>

<span data-ttu-id="7e9e1-176">前のセクションで示したように、互換性があることがわかったパッケージのバージョンを更新します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-176">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="7e9e1-177">コードを修正してビルドする</span><span class="sxs-lookup"><span data-stu-id="7e9e1-177">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="7e9e1-178">Microsoft.Windows.Compatibility</span><span class="sxs-lookup"><span data-stu-id="7e9e1-178">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="7e9e1-179">アプリケーションが .NET で使用できない API (レジストリ、ACL、WCF など) に依存している場合は、`Microsoft.Windows.Compatibility` パッケージへの参照を含めて、これらの Windows 固有の API を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-179">If your application depends on APIs that aren't available on .NET, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="7e9e1-180">これらは .NET で動作しますが、クロスプラットフォームではないため含まれていません。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-180">They work on .NET but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="7e9e1-181">API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) というツールがあります。これは、コードと互換性のない API を特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-181">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="7e9e1-182">\#If ディレクティブを使用する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-182">Use \#if directives</span></span>

<span data-ttu-id="7e9e1-183">.NET Framework と .NET をターゲットとする際に異なる実行パスが必要な場合は、コンパイル定数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-183">If you need different execution paths when targeting .NET Framework and .NET, you should use compilation constants.</span></span> <span data-ttu-id="7e9e1-184">両方のターゲットに対して同じコード ベースを保持するために、いくつかの \#if ディレクティブをコードに追加します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-184">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net"></a><span data-ttu-id="7e9e1-185">.NET で使用できないテクノロジ</span><span class="sxs-lookup"><span data-stu-id="7e9e1-185">Technologies not available on .NET</span></span>

<span data-ttu-id="7e9e1-186">次のような一部のテクノロジは .NET では使用できません。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-186">Some technologies aren't available on .NET, such as:</span></span>

* <span data-ttu-id="7e9e1-187">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7e9e1-187">AppDomains</span></span>
* <span data-ttu-id="7e9e1-188">リモート処理</span><span class="sxs-lookup"><span data-stu-id="7e9e1-188">Remoting</span></span>
* <span data-ttu-id="7e9e1-189">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7e9e1-189">Code Access Security</span></span>
* <span data-ttu-id="7e9e1-190">WCF サーバー</span><span class="sxs-lookup"><span data-stu-id="7e9e1-190">WCF Server</span></span>
* <span data-ttu-id="7e9e1-191">Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="7e9e1-191">Windows Workflow</span></span>

<span data-ttu-id="7e9e1-192">そのため、これらのテクノロジをアプリケーションで使用する場合は、それらに代わるものを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-192">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="7e9e1-193">詳細については、「[.NET Core および .NET 5 以降で使用できない .NET Framework テクノロジ](../../core/porting/net-framework-tech-unavailable.md)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-193">For more information, see the [.NET Framework technologies unavailable on .NET Core and .NET 5+](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="7e9e1-194">自動生成されたクライアントを再生成する</span><span class="sxs-lookup"><span data-stu-id="7e9e1-194">Regenerate autogenerated clients</span></span>

<span data-ttu-id="7e9e1-195">自動生成されたコード (WCF クライアントなど) がアプリケーションによって使用される場合は、.NET をターゲットとするようにこのコードを再生成する必要があることがあります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-195">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET.</span></span> <span data-ttu-id="7e9e1-196">場合によっては、欠落している参照がいくつか見つかることがあります。これらは既定の .NET アセンブリ セットの一部として含まれない場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-196">Sometimes, you can find some missing references since they may not be included as part of the default .NET assemblies set.</span></span> <span data-ttu-id="7e9e1-197"><https://apisof.net/> などのツールを使用すると、欠落している参照が存在するアセンブリを簡単に見つけて、NuGet から追加することができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-197">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="7e9e1-198">パッケージ バージョンのロールバック</span><span class="sxs-lookup"><span data-stu-id="7e9e1-198">Rolling back package versions</span></span>

<span data-ttu-id="7e9e1-199">前述のとおり、通常はすべてのパッケージ バージョンを .NET と互換性を持つように更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-199">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET.</span></span> <span data-ttu-id="7e9e1-200">しかし、更新された互換性のあるバージョンのアセンブリをターゲットにするだけでは効果がないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-200">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="7e9e1-201">変更のコストを許容できない場合は、パッケージ バージョンをロールバックし、.NET Framework で使用しているものを維持することを検討できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-201">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="7e9e1-202">.NET をターゲットとしない場合もありますが、一部のサポートされていない API を呼び出す場合を除き、適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-202">Although they may not be targeting .NET, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="7e9e1-203">実行してテストする</span><span class="sxs-lookup"><span data-stu-id="7e9e1-203">Run and test</span></span>

<span data-ttu-id="7e9e1-204">エラーが発生することなくアプリケーションがビルドされたら、すべての機能をテストすることで、移行の最後の手順を開始できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-204">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="7e9e1-205">この最後の手順では、アプリケーションの複雑さ、および使用している依存関係と API に応じて、いくつかの異なる問題を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-205">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="7e9e1-206">たとえば、構成ファイル (*app.config*) を使用する場合、実行時にエラー (構成セクションが存在しないなど) がいくつか見つかることがあります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-206">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="7e9e1-207">`Microsoft.Extensions.Configuration` NuGet パッケージを使用すれば、そのエラーが修正されるはずです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-207">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="7e9e1-208">エラーのもう 1 つの理由は、`BeginInvoke` および `EndInvoke` メソッドの使用です。これらは .NET でサポートされていないためです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-208">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET.</span></span> <span data-ttu-id="7e9e1-209">これらは .NET 上に存在しないリモート処理に依存しているため、.NET でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-209">They aren't supported on .NET because they have a dependency on Remoting, which doesn't exist on .NET.</span></span> <span data-ttu-id="7e9e1-210">この問題を解決するために、`await` キーワード (使用可能な場合) または <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> メソッドを使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-210">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7e9e1-211">互換性アナライザーを使用すると、実行時に .NET に関する問題を引き起こす可能性がある API とコード パターンをコード内で特定できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-211">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET.</span></span> <span data-ttu-id="7e9e1-212"><https://github.com/dotnet/platform-compat> に移動し、プロジェクトで .NET API アナライザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-212">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="7e9e1-213">Windows フォーム アプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="7e9e1-213">Migrating a Windows Forms application</span></span>

<span data-ttu-id="7e9e1-214">Windows フォーム アプリケーションの完全な移行プロセスを示すために、ここでは <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> で入手できる eShop サンプル アプリケーションを移行することにしました。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-214">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="7e9e1-215">移行の完全な結果は、<https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> で確認できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-215">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="7e9e1-216">このアプリケーションにより製品カタログが示され、ユーザーは製品を移動、フィルター処理、および検索することができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-216">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="7e9e1-217">アーキテクチャの観点から見ると、アプリは、バックエンド データベースに対するファサードとして機能する外部の WCF サービスに依存しています。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-217">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="7e9e1-218">メイン アプリケーション ウィンドウは、次の画像のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-218">You can see the main application window in the following picture:</span></span>

![メイン アプリケーション ウィンドウ](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="7e9e1-220">*.csproj* プロジェクト ファイルを開くと、このようになっています。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-220">If you open the *.csproj* project file, you can see something like this:</span></span>

![csproj ファイルの内容のスクリーンショット](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="7e9e1-222">前述のとおり、.NET プロジェクトのスタイルはよりコンパクトなものであり、プロジェクトの構造を新しい .NET SDK スタイルに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-222">As previously mentioned, .NET project has a more compact style and you need to migrate the project structure to the new .NET SDK style.</span></span>

<span data-ttu-id="7e9e1-223">ソリューション エクスプローラーで Windows フォーム プロジェクトを右クリックし、 **[プロジェクトのアンロード]**  >  **[編集]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-223">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="7e9e1-224">これで、.csproj ファイルを更新できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-224">Now you can update the .csproj file.</span></span> <span data-ttu-id="7e9e1-225">内容全体を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-225">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="7e9e1-226">プロジェクトを保存して再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-226">Save and reload the project.</span></span> <span data-ttu-id="7e9e1-227">これでプロジェクト ファイルの更新が完了し、プロジェクトのターゲットは .NET となります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-227">You're now done updating the project file and the project is targeting the .NET.</span></span>

<span data-ttu-id="7e9e1-228">この時点でプロジェクトをコンパイルすると、WCF クライアント参照に関するエラーがいくつか見つかります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-228">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="7e9e1-229">このコードは自動生成されるため、.NET をターゲットとするように再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-229">Since this code is autogenerated, you must regenerate it to target .NET.</span></span>

![エラーを示す Visual Studio の [エラー一覧]](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="7e9e1-231">*Reference.cs* ファイルを削除し、新しいサービス クライアントを生成します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-231">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="7e9e1-232">**[接続済みサービス]** を右クリックし、 **[接続済みサービスの追加]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-232">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![[接続済みサービスの追加] オプションが選択されている [接続済みサービス] メニューのスクリーンショット](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="7e9e1-234">[接続済みサービス] ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-234">The Connected Services window opens.</span></span> <span data-ttu-id="7e9e1-235">**[Microsoft WCF Web Service]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-235">Select the **Microsoft WCF Web Service** option.</span></span>

![[接続済みサービス] ウィンドウのスクリーンショット](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="7e9e1-237">この例と同じソリューションに WCF サービスがある場合は、サービス URL を指定する代わりに、 **[検出]** オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-237">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![[WCF Web Service Reference の構成] ウィンドウのスクリーンショット](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="7e9e1-239">サービスが配置されると、ツールにはサービスによって実装された API コントラクトが反映されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-239">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="7e9e1-240">次の画像に示されているように、名前空間の名前を `eShopServiceReference` に変更します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-240">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![API コントラクトと変更された名前空間のスクリーンショット](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="7e9e1-242">**[完了]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-242">Select the **Finish** button.</span></span> <span data-ttu-id="7e9e1-243">しばらくすると、生成されたコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-243">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="7e9e1-244">自動生成された次の 3 つのファイルが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-244">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="7e9e1-245">*はじめに*: WCF に関する情報を提供する GitHub へのリンク。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-245">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="7e9e1-246">*ConnectedService.js*: サービスに接続するための構成パラメーター。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-246">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="7e9e1-247">*Reference.cs*: 実際の WCF クライアント コード。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-247">*Reference.cs*: the actual WCF client code.</span></span>

![自動生成された 3 つのファイルがあるソリューション エクスプローラー ウィンドウのスクリーンショット](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="7e9e1-249">もう一度コンパイルすると、*Helper* フォルダー内の *.cs* ファイルから発生する多くのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-249">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="7e9e1-250">このフォルダーは .NET Framework バージョンに存在しましたが、古い *.csproj* には含まれていませんでした。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-250">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="7e9e1-251">しかし、新しい SDK スタイルのプロジェクトでは、プロジェクト ファイルの場所の下にあるすべてのコード ファイルが既定で含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-251">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="7e9e1-252">つまり、新しい .NET Core プロジェクトにより、*Helper* フォルダー内のファイルのコンパイルが試行されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-252">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="7e9e1-253">そのフォルダーは必要ではないため、安全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-253">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="7e9e1-254">プロジェクトをもう一度コンパイルして実行すると、製品イメージが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-254">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="7e9e1-255">ここでの問題は、ファイルへのパスが少し変更されたことです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-255">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="7e9e1-256">この問題を解決するには、パスに別の深さのレベルを追加し、`CatalogView.cs` ファイル内で次の行を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-256">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="7e9e1-257">to</span><span class="sxs-lookup"><span data-stu-id="7e9e1-257">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="7e9e1-258">この変更後に、アプリケーションが起動し、.NET Core で想定どおりに実行されることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-258">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="7e9e1-259">WPF アプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="7e9e1-259">Migrating a WPF application</span></span>

<span data-ttu-id="7e9e1-260">`Shop.ClassicWPF` サンプル アプリケーションを使用して移行を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-260">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="7e9e1-261">次の画像は、移行前のアプリのスクリーンショットを示しています。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-261">The following image shows a screenshot of the app before migration:</span></span>

![移行前のサンプル アプリ](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="7e9e1-263">このアプリケーションでは、ローカルの SQL Server Express データベースを使用して、製品カタログ情報を保持します。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-263">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="7e9e1-264">このデータベースには、WPF アプリケーションから直接アクセスします。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-264">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="7e9e1-265">最初に、 *.csproj* ファイルを、.NET Core アプリケーションで使用される新しい SDK スタイルに更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-265">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="7e9e1-266">Windows フォームの移行で説明されているのと同じ手順に従います。プロジェクトをアンロードし、 *.csproj* ファイルを開き、その内容を更新して、プロジェクトを再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-266">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="7e9e1-267">この場合は、 *.csproj* ファイルのすべての内容を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-267">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
 <Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWpf>true</UseWpf>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="7e9e1-268">プロジェクトを再度読み込んでコンパイルすると、次のエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-268">If you reload the project and compile it, you'll get the following error:</span></span>

![1 つのエラー CS0234 が示されている Visual Studio の [エラー一覧]](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="7e9e1-270">*.csproj* の内容をすべて削除したため、古いプロジェクトに存在するプロジェクト参照の仕様が失われています。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-270">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="7e9e1-271">ここで必要なのは、この行を *.csproj* ファイルに追加し、プロジェクト参照を再度含めることだけです。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-271">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="7e9e1-272">また、 **[依存関係]** ノードを右クリックし、 **[プロジェクト参照の追加]** を選択することで、Visual Studio で作業を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-272">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="7e9e1-273">ソリューションからプロジェクトを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-273">Select the project from the solution and click **OK**:</span></span>

![eShop.SqlProvider プロジェクトが選択されている [参照マネージャー] ダイアログのスクリーンショット](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="7e9e1-275">欠落しているプロジェクト参照を追加すると、アプリケーションは .NET 上で予期したとおりにコンパイルおよび実行されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e1-275">Once you add the missing project reference, the application compiles and runs as expected on .NET.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7e9e1-276">[前へ](windows-migration.md)
>[次へ](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="7e9e1-276">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
