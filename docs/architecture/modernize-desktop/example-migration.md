---
title: .NET 5 への移行の例
description: .NET Framework を対象とするサンプルアプリケーションを .NET 5 に移行する方法を示します。
ms.date: 01/19/2021
ms.openlocfilehash: 5b3743c68ee0426efffda6f999dffea788f493e9
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206543"
---
# <a name="example-of-migrating-to-net"></a><span data-ttu-id="95a68-103">.NET への移行の例</span><span class="sxs-lookup"><span data-stu-id="95a68-103">Example of migrating to .NET</span></span>

<span data-ttu-id="95a68-104">この章では、.NET Framework から .NET への既存のアプリケーションの移行を実行する際に役立つ実用的なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="95a68-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET.</span></span>

<span data-ttu-id="95a68-105">ここでは、適切に構成されたプロセスを紹介し、各ステップで考慮する必要がある最も重要なプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="95a68-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="95a68-106">次に、WinForms と WPF の両方のバージョンから、サンプルデスクトップアプリケーションのステップバイステップ移行プロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="95a68-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="95a68-107">移行プロセスの概要</span><span class="sxs-lookup"><span data-stu-id="95a68-107">Migration process overview</span></span>

<span data-ttu-id="95a68-108">移行プロセスは、次の4つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="95a68-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="95a68-109">**準備**: プロジェクトにおける依存関係について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="95a68-110">このステップでは、現在のプロジェクトを、移行の開始点を簡略化する状態にします。</span><span class="sxs-lookup"><span data-stu-id="95a68-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="95a68-111">**プロジェクトファイルの移行:** .net プロジェクトでは、SDK スタイルの新しいプロジェクト形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-111">**Migrate Project File:** .NET projects use the new SDK-style project format.</span></span> <span data-ttu-id="95a68-112">この形式で新しいプロジェクトファイルを作成するか、SDK スタイルを使用する必要があるものを更新します。</span><span class="sxs-lookup"><span data-stu-id="95a68-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="95a68-113">**コードを修正してビルドする:** .NET でコードをビルドし、.NET Framework と .NET の API レベルの違いを解決します。</span><span class="sxs-lookup"><span data-stu-id="95a68-113">**Fix code and build:** Build the code in .NET addressing API-level differences between .NET Framework and .NET.</span></span> <span data-ttu-id="95a68-114">必要に応じて、サードパーティのパッケージを .NET をサポートするパッケージに更新します。</span><span class="sxs-lookup"><span data-stu-id="95a68-114">If needed, update third-party packages to the ones that support .NET.</span></span>

4. <span data-ttu-id="95a68-115">**実行とテスト:** 実行時まで表示されない相違がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="95a68-116">そのため、必ずアプリケーションを実行し、すべてが期待どおりに動作することをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="95a68-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="95a68-117">準備</span><span class="sxs-lookup"><span data-stu-id="95a68-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="95a68-118">packages.config ファイルの移行</span><span class="sxs-lookup"><span data-stu-id="95a68-118">Migrate packages.config file</span></span>

<span data-ttu-id="95a68-119">.NET Framework アプリケーションでは、外部パッケージへのすべての参照が *packages.config* ファイルで宣言されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="95a68-120">.NET では、 *packages.config* ファイルを使用する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="95a68-120">In .NET, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="95a68-121">代わりに、プロジェクトファイル内の [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) プロパティを使用して、アプリの NuGet パッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="95a68-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="95a68-122">そのため、1つの形式から別の形式に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="95a68-123">更新を手動で実行するには、 *packages.config* ファイルに含まれている依存関係を取得し、という形式でプロジェクトファイルに移行し `PackageReference` ます。</span><span class="sxs-lookup"><span data-stu-id="95a68-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="95a68-124">または、Visual Studio で作業を実行できるようにするには、 *packages.config* ファイルを右クリックし、[ **packages.config を PackageReference に移行する** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="95a68-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net"></a><span data-ttu-id="95a68-125">.NET のすべての依存関係の互換性を確認する</span><span class="sxs-lookup"><span data-stu-id="95a68-125">Verify every dependency compatibility in .NET</span></span>

<span data-ttu-id="95a68-126">パッケージ参照を移行したら、各参照に互換性があるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="95a68-127">アプリケーションが [nuget.org](https://www.nuget.org/)で使用している各 NuGet パッケージの依存関係を調べることができます。パッケージに .NET Standard 依存関係がある場合、.net では、すべてのバージョンの .NET Standard が [サポート](../../standard/net-standard.md#net-implementation-support) されているため、.net 5.0 で動作します。</span><span class="sxs-lookup"><span data-stu-id="95a68-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET 5.0 because .NET [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="95a68-128">次の図は、パッケージの依存関係を示してい `Castle.Windsor` ます。</span><span class="sxs-lookup"><span data-stu-id="95a68-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Windsor パッケージの NuGet 依存関係のスクリーンショット](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="95a68-130">パッケージの互換性を確認するには、 <https://fuget.org> バージョンと依存関係に関するより詳細な情報を提供するツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="95a68-131">.NET をサポートしていない古いバージョンのパッケージがプロジェクトで参照されている可能性がありますが、それをサポートしている新しいバージョンが見つかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-131">Maybe the project is referencing older package versions that don't support .NET, but you might find newer versions that do support it.</span></span> <span data-ttu-id="95a68-132">そのため、通常は、パッケージを新しいバージョンに更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="95a68-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="95a68-133">ただし、パッケージバージョンを更新すると、コードの更新を必要とする重大な変更が発生する場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="95a68-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="95a68-134">互換性のあるバージョンが見つからない場合はどうなりますか。</span><span class="sxs-lookup"><span data-stu-id="95a68-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="95a68-135">これらの重大な変更のためにパッケージのバージョンを更新したくない場合はどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="95a68-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="95a68-136">.NET アプリケーションの .NET Framework パッケージに依存する可能性があるため、心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="95a68-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET application.</span></span> <span data-ttu-id="95a68-137">外部パッケージが .NET で使用できない API を呼び出す場合は、実行時エラーが発生する可能性があるため、必ずテストしてください。</span><span class="sxs-lookup"><span data-stu-id="95a68-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET.</span></span> <span data-ttu-id="95a68-138">これは、更新される予定のない古いパッケージを使用している場合に適しています。また、.NET での作業に再ターゲットすることもできます。</span><span class="sxs-lookup"><span data-stu-id="95a68-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="95a68-139">API の互換性を確認する</span><span class="sxs-lookup"><span data-stu-id="95a68-139">Check for API compatibility</span></span>

<span data-ttu-id="95a68-140">.NET Framework と .NET の API サーフェイスは似ていますが、同一ではありません。 .NET で使用可能な Api を確認してください。</span><span class="sxs-lookup"><span data-stu-id="95a68-140">Since the API surface in .NET Framework and .NET is similar but not identical, you must check which APIs are available on .NET and which aren't.</span></span> <span data-ttu-id="95a68-141">.Net 移植性アナライザーツールを使用すると、.NET では使用されていない Api を表示できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET.</span></span> <span data-ttu-id="95a68-142">アプリのバイナリレベルを確認し、呼び出されたすべての Api を抽出して、ターゲットフレームワークで使用できない Api (この場合は .NET 5.0) を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="95a68-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET 5.0 in this case).</span></span>

<span data-ttu-id="95a68-143">このツールの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95a68-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="95a68-144">このツールの興味深い点は、外部パッケージからのコードではなく、独自のコードの違いだけを表示し、変更できないことです。</span><span class="sxs-lookup"><span data-stu-id="95a68-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="95a68-145">.NET で動作するように、これらのパッケージのほとんどを更新しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-145">Remember you should have updated most of these packages to make them work with .NET.</span></span>

### <a name="migrate-with-try-convert-tool"></a><span data-ttu-id="95a68-146">Try Convert ツールを使用した移行</span><span class="sxs-lookup"><span data-stu-id="95a68-146">Migrate with Try Convert tool</span></span>

<span data-ttu-id="95a68-147">[ [変換の試行](https://github.com/dotnet/try-convert/releases) ] ツールは、プロジェクトを移行するための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="95a68-147">The [Try Convert](https://github.com/dotnet/try-convert/releases) tool is a great way to migrate a project.</span></span> <span data-ttu-id="95a68-148">これは、プロジェクトファイルを古いスタイルから新しい SDK スタイルにアップグレードしようとして、適用可能なプロジェクトを .NET 5 に対象するグローバルツールです。</span><span class="sxs-lookup"><span data-stu-id="95a68-148">It's a global tool that attempts to upgrade your project file from the old style to the new SDK style, and retargets applicable projects to .NET 5.</span></span> <span data-ttu-id="95a68-149">インストールが完了したら、次のコマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-149">Once installed, you can run the following commands:</span></span>

```dotnetcli
try-convert -p "<path to your project file>"
```

<span data-ttu-id="95a68-150">または:</span><span class="sxs-lookup"><span data-stu-id="95a68-150">Or:</span></span>

```dotnetcli
try-convert -w "<path to your solution>"
```

> [!NOTE]
> <span data-ttu-id="95a68-151">[変換の試行] ツールは、 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)の一部として自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-151">The try-convert tool is run automatically as part of the [.NET Upgrade Assistant tool](https://aka.ms/dotnet-upgrade-assistant).</span></span> <span data-ttu-id="95a68-152">完全アップグレードアシスタントを実行することを検討してください。変換を試すだけではありません。</span><span class="sxs-lookup"><span data-stu-id="95a68-152">Consider running the full Upgrade Assistant and not just Try Convert.</span></span>

<span data-ttu-id="95a68-153">ツールの変換が試行されたら、Visual Studio でファイルを再読み込みして実行し、テストします。</span><span class="sxs-lookup"><span data-stu-id="95a68-153">After the tool attempts the conversion, reload your files in Visual Studio to run and test.</span></span> <span data-ttu-id="95a68-154">お客様のプロジェクトの内容によっては、変換を実行できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-154">There's a possibility that Try Convert won't be able to perform the conversion due to the specifics of your project.</span></span> <span data-ttu-id="95a68-155">その場合は、以下の手順を参照できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-155">In that case, you can refer the below steps.</span></span>

#### <a name="migrate-manually"></a><span data-ttu-id="95a68-156">手動で移行する</span><span class="sxs-lookup"><span data-stu-id="95a68-156">Migrate manually</span></span>

1. <span data-ttu-id="95a68-157">新しい .NET プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="95a68-157">Create the new .NET project</span></span>

<span data-ttu-id="95a68-158">ほとんどの場合、既存のプロジェクトを新しい .NET 形式に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-158">In most cases, you'll want to update your existing project to the new .NET format.</span></span> <span data-ttu-id="95a68-159">ただし、古いプロジェクトを維持しながら新しいプロジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="95a68-159">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="95a68-160">古いプロジェクトを更新することによる主な欠点は、デザイナーのサポートが失われることです。これは、お客様と開発チームにとって重要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-160">The main drawback from updating the old project is that you lose designer support, which may be important to you and your development team.</span></span> <span data-ttu-id="95a68-161">デザイナーの使用を継続する場合は、古いものと同時に新しい .NET プロジェクトを作成し、アセットを共有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-161">If you want to keep using the designer, you must create a new .NET project in parallel with the old one and share assets.</span></span> <span data-ttu-id="95a68-162">デザイナーで UI 要素を変更する必要がある場合は、古いプロジェクトに切り替えてそれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="95a68-162">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="95a68-163">また、資産はリンクされているため、.NET プロジェクトでも更新されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-163">And since assets are linked, they'll be updated in the .NET project as well.</span></span>

<span data-ttu-id="95a68-164">.NET 用の [SDK スタイルのプロジェクト](../../core/project-sdk/msbuild-props.md) は、.NET Framework のプロジェクト形式よりもはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="95a68-164">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="95a68-165">前に説明したエントリとは別 `PackageReference` に、それ以上の操作は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="95a68-165">Apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="95a68-166">新しいプロジェクト形式には、ファイルやファイルなど、 [既定で特定の拡張子を持つファイルが含まれ](../../core/project-sdk/overview.md#default-includes-and-excludes)て `.cs` おり、それらを `.xaml` プロジェクトファイルに明示的に含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="95a68-166">The new project format [includes files with certain extensions by default](../../core/project-sdk/overview.md#default-includes-and-excludes), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="95a68-167">AssemblyInfo に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="95a68-167">AssemblyInfo considerations</span></span>

<span data-ttu-id="95a68-168">属性は .NET プロジェクトで自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-168">Attributes are autogenerated on .NET projects.</span></span> <span data-ttu-id="95a68-169">プロジェクトに *AssemblyInfo.cs* ファイルが含まれている場合は、定義が重複するため、コンパイルの競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="95a68-169">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="95a68-170">.Net プロジェクトファイルに次のエントリを追加することで、古い *AssemblyInfo.cs* ファイルを削除するか、自動生成を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="95a68-170">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="95a68-171">リソース</span><span class="sxs-lookup"><span data-stu-id="95a68-171">Resources</span></span>

<span data-ttu-id="95a68-172">埋め込みリソースは自動的にインクルードされますが、リソースは含まれないため、リソースを新しいプロジェクトファイルに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-172">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="95a68-173">パッケージ参照</span><span class="sxs-lookup"><span data-stu-id="95a68-173">Package references</span></span>

<span data-ttu-id="95a68-174">**PackageReference への packages.config 移行** オプションを使用すると、前に説明したように、外部パッケージの参照を新しい形式に簡単に移動できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-174">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="95a68-175">パッケージ参照の更新</span><span class="sxs-lookup"><span data-stu-id="95a68-175">Update package references</span></span>

<span data-ttu-id="95a68-176">前のセクションで示したように、互換性のあるものとして見つかったパッケージのバージョンを更新します。</span><span class="sxs-lookup"><span data-stu-id="95a68-176">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="95a68-177">コードを修正してビルドする</span><span class="sxs-lookup"><span data-stu-id="95a68-177">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="95a68-178">Microsoft. Windows. 互換性</span><span class="sxs-lookup"><span data-stu-id="95a68-178">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="95a68-179">アプリケーションが .NET で使用できない Api (レジストリ、Acl、WCF など) に依存している場合は、パッケージへの参照を含めて、これらの Windows 固有の Api を追加する必要があり `Microsoft.Windows.Compatibility` ます。</span><span class="sxs-lookup"><span data-stu-id="95a68-179">If your application depends on APIs that aren't available on .NET, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="95a68-180">これらは .NET で動作しますが、クロスプラットフォームではないため、含まれていません。</span><span class="sxs-lookup"><span data-stu-id="95a68-180">They work on .NET but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="95a68-181">API Analyzer () というツールを使用すると、 <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> コードと互換性のない api を識別できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-181">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="95a68-182">If ディレクティブを使用する \#</span><span class="sxs-lookup"><span data-stu-id="95a68-182">Use \#if directives</span></span>

<span data-ttu-id="95a68-183">.NET Framework と .NET を対象とする場合に異なる実行パスが必要な場合は、コンパイル定数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-183">If you need different execution paths when targeting .NET Framework and .NET, you should use compilation constants.</span></span> <span data-ttu-id="95a68-184">\#同じコードベースを両方のターゲットに保持するために、いくつかの if ディレクティブをコードに追加します。</span><span class="sxs-lookup"><span data-stu-id="95a68-184">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net"></a><span data-ttu-id="95a68-185">.NET で使用できないテクノロジ</span><span class="sxs-lookup"><span data-stu-id="95a68-185">Technologies not available on .NET</span></span>

<span data-ttu-id="95a68-186">次のような一部のテクノロジは .NET では使用できません。</span><span class="sxs-lookup"><span data-stu-id="95a68-186">Some technologies aren't available on .NET, such as:</span></span>

* <span data-ttu-id="95a68-187">AppDomain</span><span class="sxs-lookup"><span data-stu-id="95a68-187">AppDomains</span></span>
* <span data-ttu-id="95a68-188">リモート処理</span><span class="sxs-lookup"><span data-stu-id="95a68-188">Remoting</span></span>
* <span data-ttu-id="95a68-189">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="95a68-189">Code Access Security</span></span>
* <span data-ttu-id="95a68-190">WCF サーバー</span><span class="sxs-lookup"><span data-stu-id="95a68-190">WCF Server</span></span>
* <span data-ttu-id="95a68-191">Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="95a68-191">Windows Workflow</span></span>

<span data-ttu-id="95a68-192">そのため、これらのテクノロジをアプリケーションで使用している場合は、それらのテクノロジに代わるものを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-192">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="95a68-193">詳細については、「 [.Net Core および .net 5 + で使用できないテクノロジ .NET Framework](../../core/porting/net-framework-tech-unavailable.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95a68-193">For more information, see the [.NET Framework technologies unavailable on .NET Core and .NET 5+](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="95a68-194">自動生成したクライアントの再生成</span><span class="sxs-lookup"><span data-stu-id="95a68-194">Regenerate autogenerated clients</span></span>

<span data-ttu-id="95a68-195">アプリケーションが自動生成されたコード (WCF クライアントなど) を使用する場合は、.NET を対象とするようにこのコードを再生成する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-195">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET.</span></span> <span data-ttu-id="95a68-196">既定の .NET アセンブリセットの一部として含まれていない可能性があるため、不足している参照がいくつか見つかることがあります。</span><span class="sxs-lookup"><span data-stu-id="95a68-196">Sometimes, you can find some missing references since they may not be included as part of the default .NET assemblies set.</span></span> <span data-ttu-id="95a68-197">などのツールを使用 <https://apisof.net/> すると、不足している参照が存在するアセンブリを簡単に見つけて、NuGet から追加することができます。</span><span class="sxs-lookup"><span data-stu-id="95a68-197">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="95a68-198">パッケージバージョンのロールバック</span><span class="sxs-lookup"><span data-stu-id="95a68-198">Rolling back package versions</span></span>

<span data-ttu-id="95a68-199">一般的なルールとして、1つのパッケージバージョンを .NET と互換性を持つように更新することをお勧めしました。</span><span class="sxs-lookup"><span data-stu-id="95a68-199">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET.</span></span> <span data-ttu-id="95a68-200">ただし、アセンブリの更新バージョンと互換性のあるバージョンをターゲットにすると、支払いが行われないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="95a68-200">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="95a68-201">変更のコストが許容できない場合は、.NET Framework で使用しているパッケージのバージョンをロールバックすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="95a68-201">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="95a68-202">.NET を対象としていない場合もありますが、サポートされていない Api を呼び出す場合を除き、適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="95a68-202">Although they may not be targeting .NET, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="95a68-203">実行してテストする</span><span class="sxs-lookup"><span data-stu-id="95a68-203">Run and test</span></span>

<span data-ttu-id="95a68-204">エラーを発生させずにアプリケーションを構築した後は、すべての機能をテストすることで、移行の最後の手順を開始できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-204">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="95a68-205">この最後の手順では、アプリケーションの複雑さと使用している依存関係と Api に応じて、いくつかの異なる問題を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="95a68-205">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="95a68-206">たとえば、構成ファイル (*app.config*) を使用する場合、構成セクションが存在しないなど、実行時にエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="95a68-206">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="95a68-207">NuGet パッケージを使用する `Microsoft.Extensions.Configuration` と、そのエラーを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-207">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="95a68-208">エラーのもう1つの理由は、 `BeginInvoke` `EndInvoke` .net でサポートされていないメソッドとメソッドを使用することです。</span><span class="sxs-lookup"><span data-stu-id="95a68-208">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET.</span></span> <span data-ttu-id="95a68-209">.Net ではサポートされません。これは、.NET 上に存在しないリモート処理に依存しているためです。</span><span class="sxs-lookup"><span data-stu-id="95a68-209">They aren't supported on .NET because they have a dependency on Remoting, which doesn't exist on .NET.</span></span> <span data-ttu-id="95a68-210">この問題を解決するに `await` は、キーワード (使用可能な場合) またはメソッドを使用してください <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="95a68-210">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="95a68-211">互換性アナライザーを使用すると、.NET で実行時に問題を引き起こす可能性がある Api とコードパターンをコード内で識別できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-211">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET.</span></span> <span data-ttu-id="95a68-212">にアクセス <https://github.com/dotnet/platform-compat> し、プロジェクトで .NET API analyzer を使用します。</span><span class="sxs-lookup"><span data-stu-id="95a68-212">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="95a68-213">Windows フォームアプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="95a68-213">Migrating a Windows Forms application</span></span>

<span data-ttu-id="95a68-214">Windows フォームアプリケーションの移行プロセスを完了するには、で入手できる eShop サンプルアプリケーションを移行することを選択しました <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> 。</span><span class="sxs-lookup"><span data-stu-id="95a68-214">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="95a68-215">移行の完全な結果については、「」を参照 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> してください。</span><span class="sxs-lookup"><span data-stu-id="95a68-215">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="95a68-216">このアプリケーションは、製品カタログを表示し、ユーザーが製品の移動、フィルター処理、および検索を行えるようにします。</span><span class="sxs-lookup"><span data-stu-id="95a68-216">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="95a68-217">アーキテクチャの観点から見ると、アプリは、ファサードとして機能する外部の WCF サービスをバックエンドデータベースに依存しています。</span><span class="sxs-lookup"><span data-stu-id="95a68-217">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="95a68-218">メインアプリケーションウィンドウは、次の図のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-218">You can see the main application window in the following picture:</span></span>

![メインアプリケーションウィンドウ](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="95a68-220">.Csproj プロジェクトファイルを開くと、次のような内容が表示さ *れ* ます。</span><span class="sxs-lookup"><span data-stu-id="95a68-220">If you open the *.csproj* project file, you can see something like this:</span></span>

![.Csproj ファイルの内容のスクリーンショット](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="95a68-222">既に説明したように、.NET プロジェクトはよりコンパクトなスタイルであり、プロジェクトの構造を新しい .NET SDK スタイルに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-222">As previously mentioned, .NET project has a more compact style and you need to migrate the project structure to the new .NET SDK style.</span></span>

<span data-ttu-id="95a68-223">ソリューションエクスプローラーで Windows フォームプロジェクトを右クリックし、[プロジェクトの **アンロード**] [編集] の順に選択し  >  ます。</span><span class="sxs-lookup"><span data-stu-id="95a68-223">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="95a68-224">.Csproj ファイルを更新できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="95a68-224">Now you can update the .csproj file.</span></span> <span data-ttu-id="95a68-225">コンテンツ全体を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="95a68-225">You'll delete the entire content and replace it with the following code:</span></span>

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

<span data-ttu-id="95a68-226">プロジェクトを保存して再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="95a68-226">Save and reload the project.</span></span> <span data-ttu-id="95a68-227">これでプロジェクトファイルの更新が完了し、プロジェクトは .NET を対象としています。</span><span class="sxs-lookup"><span data-stu-id="95a68-227">You're now done updating the project file and the project is targeting the .NET.</span></span>

<span data-ttu-id="95a68-228">この時点でプロジェクトをコンパイルすると、WCF クライアントリファレンスに関連するエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-228">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="95a68-229">このコードは自動生成されるため、.NET を対象とするように再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-229">Since this code is autogenerated, you must regenerate it to target .NET.</span></span>

![Visual Studio でのコンパイルエラーのスクリーンショット](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="95a68-231">*Reference.cs* ファイルを削除し、新しいサービスクライアントを生成します。</span><span class="sxs-lookup"><span data-stu-id="95a68-231">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="95a68-232">**接続済みサービス** を右クリックし、[**接続済みサービスの追加**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="95a68-232">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![[接続済みサービスの追加] オプションが選択されている接続済みサービスメニューのスクリーンショット](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="95a68-234">[接続済みサービス] ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="95a68-234">The Connected Services window opens.</span></span> <span data-ttu-id="95a68-235">[ **MICROSOFT WCF Web サービス** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="95a68-235">Select the **Microsoft WCF Web Service** option.</span></span>

![[接続済みサービス] ウィンドウのスクリーンショット](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="95a68-237">この例と同じソリューションに WCF サービスがある場合は、サービス URL を指定する代わりに、 **Discover** オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-237">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![[WCF Web サービス参照の構成] ウィンドウのスクリーンショット](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="95a68-239">サービスが配置されると、このツールはサービスによって実装されている API コントラクトを反映します。</span><span class="sxs-lookup"><span data-stu-id="95a68-239">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="95a68-240">次の図に示すように、名前空間の名前をに変更し `eShopServiceReference` ます。</span><span class="sxs-lookup"><span data-stu-id="95a68-240">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![API コントラクトと名前空間が変更されたことを示すスクリーンショット](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="95a68-242">[ **完了** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="95a68-242">Select the **Finish** button.</span></span> <span data-ttu-id="95a68-243">しばらくすると、生成されたコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-243">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="95a68-244">次の3つの自動生成ファイルが表示できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-244">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="95a68-245">*はじめに*: WCF に関する情報を提供する GitHub へのリンク。</span><span class="sxs-lookup"><span data-stu-id="95a68-245">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="95a68-246">*ConnectedService.js*: サービスに接続するための構成パラメーター。</span><span class="sxs-lookup"><span data-stu-id="95a68-246">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="95a68-247">*Reference.cs*: 実際の WCF クライアントコード。</span><span class="sxs-lookup"><span data-stu-id="95a68-247">*Reference.cs*: the actual WCF client code.</span></span>

![自動生成された3つのファイルがある [ソリューションエクスプローラー] ウィンドウのスクリーンショット](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="95a68-249">もう一度コンパイルすると、*ヘルパー* フォルダー内の *.cs* ファイルから発生する多くのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-249">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="95a68-250">このフォルダーは .NET Framework バージョンに存在しましたが、古い *.csproj* には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="95a68-250">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="95a68-251">ただし、新しい SDK スタイルのプロジェクトでは、プロジェクトファイルの場所の下にあるすべてのコードファイルが既定で含まれています。</span><span class="sxs-lookup"><span data-stu-id="95a68-251">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="95a68-252">つまり、新しい .NET Core プロジェクトでは、 *ヘルパー* フォルダー内のファイルのコンパイルが試行されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-252">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="95a68-253">このフォルダーは必須ではないため、安全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-253">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="95a68-254">プロジェクトを再度コンパイルして実行すると、製品イメージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="95a68-254">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="95a68-255">問題は、ファイルへのパスが少し変更されたことです。</span><span class="sxs-lookup"><span data-stu-id="95a68-255">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="95a68-256">この問題を解決するには、パスに別の深さレベルを追加し、ファイル内で次の行を更新する必要があり `CatalogView.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="95a68-256">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="95a68-257">to</span><span class="sxs-lookup"><span data-stu-id="95a68-257">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="95a68-258">この変更を行った後、アプリケーションが起動され、.NET Core で想定どおりに実行されることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="95a68-258">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="95a68-259">WPF アプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="95a68-259">Migrating a WPF application</span></span>

<span data-ttu-id="95a68-260">サンプルアプリケーションを使用して `Shop.ClassicWPF` 移行を実行します。</span><span class="sxs-lookup"><span data-stu-id="95a68-260">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="95a68-261">次の図は、移行前のアプリのスクリーンショットを示しています。</span><span class="sxs-lookup"><span data-stu-id="95a68-261">The following image shows a screenshot of the app before migration:</span></span>

![移行前のサンプルアプリ](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="95a68-263">このアプリケーションでは、ローカルの SQL Server Express データベースを使用して、製品カタログ情報を保持します。</span><span class="sxs-lookup"><span data-stu-id="95a68-263">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="95a68-264">このデータベースには、WPF アプリケーションから直接アクセスします。</span><span class="sxs-lookup"><span data-stu-id="95a68-264">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="95a68-265">最初に、 *.csproj* ファイルを .net Core アプリケーションで使用される新しい SDK スタイルに更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-265">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="95a68-266">「Windows フォームの移行」で説明されているのと同じ手順に従います。プロジェクトをアンロードし、 *.csproj* ファイルを開き、内容を更新して、プロジェクトを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="95a68-266">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="95a68-267">この場合は、 *.csproj* ファイルのすべての内容を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="95a68-267">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

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

<span data-ttu-id="95a68-268">プロジェクトを再読み込みしてコンパイルすると、次のエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-268">If you reload the project and compile it, you'll get the following error:</span></span>

![Visual Studio でのコンパイルエラーのスクリーンショット](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="95a68-270">*.Csproj* の内容をすべて削除したため、古いプロジェクトに存在するプロジェクト参照の仕様が失われています。</span><span class="sxs-lookup"><span data-stu-id="95a68-270">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="95a68-271">次の行を *.csproj* ファイルに追加して、プロジェクト参照を戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a68-271">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="95a68-272">また、[ **依存関係** ] ノードを右クリックし、[ **プロジェクト参照の追加**] を選択して、Visual Studio が役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="95a68-272">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="95a68-273">ソリューションからプロジェクトを選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95a68-273">Select the project from the solution and click **OK**:</span></span>

![[参照マネージャー] ダイアログのスクリーンショット (eShop. SqlProvider プロジェクトが選択されている場合)](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="95a68-275">見つからないプロジェクト参照を追加すると、アプリケーションは .NET 上で期待どおりにコンパイルおよび実行されます。</span><span class="sxs-lookup"><span data-stu-id="95a68-275">Once you add the missing project reference, the application compiles and runs as expected on .NET.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="95a68-276">[前へ](windows-migration.md)
>[次へ](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="95a68-276">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
