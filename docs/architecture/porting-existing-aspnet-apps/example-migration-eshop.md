---
title: ASP.NET Core への eShop の移行例
description: サンプルのオンライン ストア アプリを参照として使用して、既存の ASP.NET MVC アプリを ASP.NET Core に移行するためのチュートリアルです。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 119ba64134813fa17848cf9f5fe02cb1a14f8a5d
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122977"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a><span data-ttu-id="dad5a-103">ASP.NET Core への eShop の移行例</span><span class="sxs-lookup"><span data-stu-id="dad5a-103">Example migration of eShop to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="dad5a-104">この章では、.NET Framework アプリを .NET Core に移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-104">In this chapter, you'll see how to migrate a .NET Framework app to .NET Core.</span></span> <span data-ttu-id="dad5a-105">この章では、ASP.NET 5.0 用に作成されたサンプルのオンライン ストア アプリについて確認します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-105">The chapter examines a sample online store app written for ASP.NET 5.0.</span></span> <span data-ttu-id="dad5a-106">このアプリでは、本書で既に説明した多くの概念とツールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-106">The app will use many of the concepts and tools described earlier in this book.</span></span> <span data-ttu-id="dad5a-107">出発点となるアプリは [*eShopModernizing* GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)にあります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-107">You'll find the starting point app in the [*eShopModernizing* GitHub repository](https://github.com/dotnet-architecture/eShopModernizing).</span></span> <span data-ttu-id="dad5a-108">出発点となるアプリは複数あります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-108">There are several different starting point apps.</span></span> <span data-ttu-id="dad5a-109">この章では、*eShopLegacyMVCSolution* に焦点を当てます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-109">This chapter focuses on the *eShopLegacyMVCSolution*.</span></span>

<span data-ttu-id="dad5a-110">図 4-1 は、プロジェクトの初期バージョンを示しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-110">The initial version of the project is shown in Figure 4-1.</span></span> <span data-ttu-id="dad5a-111">これは、ごく標準的な ASP.NET MVC 5 アプリです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-111">It's a fairly standard ASP.NET MVC 5 app.</span></span>

![図 4-1](media/Figure4-1.png)

<span data-ttu-id="dad5a-113">**図 4-1**</span><span class="sxs-lookup"><span data-stu-id="dad5a-113">**Figure 4-1.**</span></span> <span data-ttu-id="dad5a-114">*eShopModernizing* MVC サンプル プロジェクトの構造。</span><span class="sxs-lookup"><span data-stu-id="dad5a-114">The *eShopModernizing* MVC sample project structure.</span></span>

<span data-ttu-id="dad5a-115">この章では、アップグレード手順の多くを手動で実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-115">This chapter demonstrates how to perform many of the upgrade steps by hand.</span></span> <span data-ttu-id="dad5a-116">または、[.NET Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant)を使用して、プロジェクト ファイルの変換、ターゲット フレームワークの変更、NuGet パッケージの更新など、初期手順の多くを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-116">Alternatively, you can use the [.NET Upgrade Assistant tool](https://aka.ms/dotnet-upgrade-assistant) to perform many of the initial steps, like converting the project file, changing the target framework, and updating NuGet packages.</span></span>

## <a name="run-apiport-to-identify-problematic-apis"></a><span data-ttu-id="dad5a-117">*ApiPort* を実行して問題のある API を特定する</span><span class="sxs-lookup"><span data-stu-id="dad5a-117">Run *ApiPort* to identify problematic APIs</span></span>

<span data-ttu-id="dad5a-118">移行準備の最初の手順は、*ApiPort* ツールを実行することです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-118">The first step in preparing to migrate is to run the *ApiPort* tool.</span></span> <span data-ttu-id="dad5a-119">このツールでは、アプリが呼び出す .NET Framework API の数と、それに相当する .NET Standard または .NET Core の API の数を特定します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-119">The tool identifies how many .NET Framework APIs the app calls and how many of these have .NET Standard or .NET Core equivalents.</span></span> <span data-ttu-id="dad5a-120">サードパーティの依存関係ではなく独自のアプリのロジックを重視し、移植する必要のある `System.Web` の依存関係に注意してください。</span><span class="sxs-lookup"><span data-stu-id="dad5a-120">Focus primarily on your own app's logic, not third-party dependencies, and pay attention to `System.Web` dependencies that will need to be ported.</span></span> <span data-ttu-id="dad5a-121">ApiPort ツールは、前の[依存関係の把握と更新](understand-update-dependencies.md)に関する章で導入されました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-121">The ApiPort tool was introduced in the last chapter on [understanding and updating dependencies](understand-update-dependencies.md).</span></span>

<span data-ttu-id="dad5a-122">[*ApiPort* ツールをインストールおよび構成](../../standard/analyzers/portability-analyzer.md)したら、図 4-2 に示すように Visual Studio 内から分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-122">After [installing and configuring the *ApiPort* tool](../../standard/analyzers/portability-analyzer.md), run the analysis from within Visual Studio, as shown in Figure 4-2.</span></span>

![図 4-2](media/Figure4-2.png)

<span data-ttu-id="dad5a-124">**図 4-2**</span><span class="sxs-lookup"><span data-stu-id="dad5a-124">**Figure 4-2.**</span></span> <span data-ttu-id="dad5a-125">Visual Studio でアセンブリの移植性を分析する。</span><span class="sxs-lookup"><span data-stu-id="dad5a-125">Analyze assembly portability in Visual Studio.</span></span>

<span data-ttu-id="dad5a-126">図 4-3 に示すように、プロジェクトの *bin* フォルダーから Web プロジェクトのアセンブリを選択します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-126">Choose the web project's assembly from the project's *bin* folder, as shown in Figure 4-3.</span></span>

![図 4-3](media/Figure4-3.png)

<span data-ttu-id="dad5a-128">**図 4-3**</span><span class="sxs-lookup"><span data-stu-id="dad5a-128">**Figure 4-3.**</span></span> <span data-ttu-id="dad5a-129">プロジェクトの Web アセンブリを選択する。</span><span class="sxs-lookup"><span data-stu-id="dad5a-129">Choose the project's web assembly.</span></span>

<span data-ttu-id="dad5a-130">ソリューションに複数のプロジェクトが含まれている場合は、すべてを選択できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-130">If your solution includes several projects, you can choose all of them.</span></span> <span data-ttu-id="dad5a-131">*eShop* サンプルに含まれている MVC プロジェクトは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-131">The *eShop* sample includes just a single MVC project.</span></span>

<span data-ttu-id="dad5a-132">レポートが生成されたら、ファイルを開いて結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-132">Once the report is generated, open the file and review the results.</span></span> <span data-ttu-id="dad5a-133">概要では、アプリが実行する .NET Framework 呼び出しのうち、互換性のあるバージョンを持つ呼び出しの割合が示されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-133">The summary provides a high-level view of what percentage of .NET Framework calls your app is making have compatible versions.</span></span> <span data-ttu-id="dad5a-134">図 4-4 は、*eShop* MVC プロジェクトの概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-134">Figure 4-4 shows the summary for the *eShop* MVC project.</span></span>

![図 4-4](media/Figure4-4.png)

<span data-ttu-id="dad5a-136">**図 4-4**</span><span class="sxs-lookup"><span data-stu-id="dad5a-136">**Figure 4-4.**</span></span> <span data-ttu-id="dad5a-137">ApiPort の概要。</span><span class="sxs-lookup"><span data-stu-id="dad5a-137">ApiPort summary.</span></span>

<span data-ttu-id="dad5a-138">このアプリの場合、約 80% の .NET Framework の呼び出しに互換性があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-138">For this app, about 80 percent of the .NET Framework calls are compatible.</span></span> <span data-ttu-id="dad5a-139">20% の呼び出しは、移植プロセス中に対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-139">20 percent of the calls need to be addressed during the porting process.</span></span> <span data-ttu-id="dad5a-140">詳細を表示すると、互換性のないすべての呼び出しが `System.Web` に含まれていることがわかります。これは、想定された非互換性です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-140">Viewing the details reveals that all of the incompatible calls are part of `System.Web`, which is an expected incompatibility.</span></span> <span data-ttu-id="dad5a-141">`System.Web` の呼び出しへの依存関係は、後の手順でアプリのコントローラーと関連するクラスが移行されるときに対処されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-141">The dependencies on `System.Web` calls will be addressed when the app's controllers and related classes are migrated in a later step.</span></span> <span data-ttu-id="dad5a-142">図 4-5 は、ツールで検出された型の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-142">Figure 4-5 lists some of the specific types found by the tool:</span></span>

![図 4-5](media/Figure4-5.png)

<span data-ttu-id="dad5a-144">**図 4-5**</span><span class="sxs-lookup"><span data-stu-id="dad5a-144">**Figure 4-5.**</span></span> <span data-ttu-id="dad5a-145">*ApiPort* の互換性のない型の詳細。</span><span class="sxs-lookup"><span data-stu-id="dad5a-145">*ApiPort* incompatible type details.</span></span>

<span data-ttu-id="dad5a-146">互換性のない型のほとんどは、`Controller` および ASP.NET Core に同等の属性を持つさまざまな関連属性を参照します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-146">Most of the incompatible types refer to `Controller` and various related attributes that have equivalents in ASP.NET Core.</span></span>

## <a name="update-project-files-and-nuget-reference-syntax"></a><span data-ttu-id="dad5a-147">プロジェクト ファイルと NuGet 参照構文を更新する</span><span class="sxs-lookup"><span data-stu-id="dad5a-147">Update project files and NuGet reference syntax</span></span>

<span data-ttu-id="dad5a-148">次に、古い *.csproj* ファイル構造を、.NET Core で導入されたより新しくシンプルな構造に移行します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-148">Next, migrate from the older *.csproj* file structure to the newer, simpler structure introduced with .NET Core.</span></span> <span data-ttu-id="dad5a-149">その場合、NuGet 参照用の *packages.config* ファイルの使用が、プロジェクト ファイル内の `<PackageReference>` 要素の使用に移行されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-149">In doing so, you'll also migrate from using a *packages.config* file for NuGet references to using `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="dad5a-150">旧形式のプロジェクト ファイルでも `<PackageReference>` 要素が使用される場合があるため、新しいプロジェクト ファイル形式にアップグレードする前に、まずすべての NuGet パッケージ参照をこの形式に移行することが通常理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-150">Old-style project files may also use `<PackageReference>` elements, so it usually makes sense to migrate all NuGet package references to this format first, before upgrading to the new project file format.</span></span>

<span data-ttu-id="dad5a-151">元のプロジェクトの *eShopLegacyMVC.csproj* ファイルの長さは 418 行です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-151">The original project's *eShopLegacyMVC.csproj* file is 418 lines long.</span></span> <span data-ttu-id="dad5a-152">図 4-6 は、プロジェクト ファイルのサンプルを示しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-152">A sample of the project file is shown in Figure 4-6.</span></span> <span data-ttu-id="dad5a-153">全体のサイズと複雑さを把握できるように、画像の右側にはファイル全体が縮小表示されています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-153">To offer a sense of its overall size and complexity, the right side of the image contains a miniature view of the entire file.</span></span>

![図 4-6](media/Figure4-6.png)

<span data-ttu-id="dad5a-155">**図 4-6**</span><span class="sxs-lookup"><span data-stu-id="dad5a-155">**Figure 4-6.**</span></span> <span data-ttu-id="dad5a-156">*eShopLegacyMVC.csproj* ファイルの構造。</span><span class="sxs-lookup"><span data-stu-id="dad5a-156">The *eShopLegacyMVC.csproj* file structure.</span></span>

<span data-ttu-id="dad5a-157">既存の ASP.NET プロジェクト用の新しいプロジェクト ファイルを作成する一般的な方法としては、`dotnet new` または Visual Studio の **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を使用して新しい ASP.NET Core アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-157">A common way to create a new project file for an existing ASP.NET project is to create a new ASP.NET Core app using `dotnet new` or **File** > **New** > **Project** in Visual Studio.</span></span> <span data-ttu-id="dad5a-158">次に、古いプロジェクトから新しいプロジェクトにファイルをコピーして、移行を完了できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-158">Then files can be copied from the old project to the new one to complete the migration.</span></span>

<span data-ttu-id="dad5a-159">図 4-7 に示すように、C# プロジェクト ファイルに加えて、NuGet の依存関係が個別の 45 行の *packages.config* ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-159">In addition to the C# project file, NuGet dependencies are stored in a separate 45-line *packages.config* file, as shown in Figure 4-7.</span></span>

![図 4-7](media/Figure4-7.png)

<span data-ttu-id="dad5a-161">**図 4-7**</span><span class="sxs-lookup"><span data-stu-id="dad5a-161">**Figure 4-7.**</span></span> <span data-ttu-id="dad5a-162">*packages.config* ファイル。</span><span class="sxs-lookup"><span data-stu-id="dad5a-162">The *packages.config* file.</span></span>

<span data-ttu-id="dad5a-163">Visual Studio を使用してクラス ライブラリ プロジェクト内の *packages.config* を移行できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-163">You can migrate *packages.config* in class library projects using Visual Studio.</span></span> <span data-ttu-id="dad5a-164">ただし、この機能は ASP.NET プロジェクトでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-164">This functionality doesn't work with ASP.NET projects, however.</span></span> <span data-ttu-id="dad5a-165">[Visual Studio で *packages.config* を `<PackageReference>` に移行する方法](/nuget/consume-packages/migrate-packages-config-to-package-reference)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dad5a-165">[Learn more about migrating *packages.config* to `<PackageReference>` in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span> <span data-ttu-id="dad5a-166">多数のプロジェクトを移行する場合は、[このコミュニティ ツール](https://github.com/MarkKharitonov/NuGetPCToPRMigrator)が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-166">If you have a large number of projects to migrate, [this community tool may help](https://github.com/MarkKharitonov/NuGetPCToPRMigrator).</span></span> <span data-ttu-id="dad5a-167">ツールを使用してプロジェクト ファイルを新しい形式に移行している場合は、`<PackageReverence>` を使用するためにすべての NuGet 参照の移行を完了した後にそれを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-167">If you're using a tool to migrate the project file to the new format, you should do that after you've finished migrating all NuGet references to use `<PackageReverence>`.</span></span>

## <a name="create-new-aspnet-core-project"></a><span data-ttu-id="dad5a-168">新しい ASP.NET Core プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="dad5a-168">Create new ASP.NET Core project</span></span>

<span data-ttu-id="dad5a-169">新しい ASP.NET Core プロジェクトを既存のアプリのソリューションに追加して、ファイルを簡単に移動できるようにします。ほとんどの作業は Visual Studio の **ソリューション エクスプローラー** 内から実行できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-169">Add a new ASP.NET Core project to the existing app's solution to make moving files easier, as most of the work can be done from within Visual Studio's **Solution Explorer**.</span></span> <span data-ttu-id="dad5a-170">Visual Studio で、アプリのソリューションを右クリックし、 **[新しいプロジェクトの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-170">In Visual Studio, right-click on your app's solution and choose **Add New Project**.</span></span> <span data-ttu-id="dad5a-171">**[ASP.NET Core Web アプリケーション]** を選択し、図 4-8 に示すように、新しいプロジェクトに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-171">Choose **ASP.NET Core web application**, and give the new project a name as shown in Figure 4-8.</span></span>

![図 4-8](media/Figure4-8.png)

<span data-ttu-id="dad5a-173">**図 4-8**</span><span class="sxs-lookup"><span data-stu-id="dad5a-173">**Figure 4-8.**</span></span> <span data-ttu-id="dad5a-174">新しい ASP.NET Core Web アプリケーションを追加する。</span><span class="sxs-lookup"><span data-stu-id="dad5a-174">Add new ASP.NET Core web application.</span></span>

<span data-ttu-id="dad5a-175">次のダイアログでは、使用するテンプレートの選択を求められます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-175">The next dialog will ask you to choose which template to use.</span></span> <span data-ttu-id="dad5a-176">**[空]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-176">Select the **Empty** template.</span></span> <span data-ttu-id="dad5a-177">また、ドロップダウンを **.Net Core** から **.NET Framework** に変更します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-177">Be sure to also change the dropdown from **.NET Core** to **.NET Framework**.</span></span> <span data-ttu-id="dad5a-178">図 4-9 に示すように、 **[ASP.NET Core 2.2]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-178">Select **ASP.NET Core 2.2**, as shown in Figure 4-9.</span></span>

![図 4-9](media/Figure4-9.png)

<span data-ttu-id="dad5a-180">**図 4-9**</span><span class="sxs-lookup"><span data-stu-id="dad5a-180">**Figure 4-9.**</span></span> <span data-ttu-id="dad5a-181">.NET Framework と ASP.NET Core 2.2 をターゲットとする空のプロジェクト テンプレートを選択する。</span><span class="sxs-lookup"><span data-stu-id="dad5a-181">Choose an Empty project template targeting .NET Framework with ASP.NET Core 2.2.</span></span>

### <a name="migrating-nuget-packages"></a><span data-ttu-id="dad5a-182">NuGet パッケージの移行</span><span class="sxs-lookup"><span data-stu-id="dad5a-182">Migrating NuGet Packages</span></span>

<span data-ttu-id="dad5a-183">*packages.config* を `<PackageReference>` に移行するための組み込みの移行ツールは ASP.NET プロジェクトでは機能しないため、代わりにコミュニティ ツールを使用するか、手動で移行を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-183">Since the built-in migration tool for migrating *packages.config* to `<PackageReference>` doesn't work on ASP.NET projects, you can use a community tool instead, or migrate by hand.</span></span> <span data-ttu-id="dad5a-184">[私が使用したコミュニティ ツール](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf)では、XSL ファイルを使用して形式を変換します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-184">A [community tool I've used](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) uses an XSL file to transform from one format to the other.</span></span> <span data-ttu-id="dad5a-185">これを使用するには、まず、新しく作成した ASP.NET Core プロジェクト フォルダーに *packages.config* ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-185">To use it, first copy the *packages.config* file to the newly created ASP.NET Core project folder.</span></span> <span data-ttu-id="dad5a-186">ファイルのバックアップを作成します。このスクリプトでは、スクリプトの実行場所にあるすべてのフォルダーから *packages.config* ファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-186">Make a backup of your files, as this script removes the *packages.config* file from all folders under where you run the script.</span></span> <span data-ttu-id="dad5a-187">次に、プロジェクト フォルダーから (または、必要に応じてソリューション全体に対して) 次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-187">Then run these commands from the project folder (or for the entire solution if you prefer):</span></span>

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

<span data-ttu-id="dad5a-188">最初の 2 つのコマンドは、ファイルをダウンロードしてローカルに配置します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-188">The first two commands download files so that they exist locally.</span></span> <span data-ttu-id="dad5a-189">最後の行でスクリプトが実行されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-189">The last line runs the script.</span></span> <span data-ttu-id="dad5a-190">実行後、新しいプロジェクトのビルドを試してください。</span><span class="sxs-lookup"><span data-stu-id="dad5a-190">After running it, try to build the new project.</span></span> <span data-ttu-id="dad5a-191">おそらく何らかのエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-191">You'll most likely get some errors.</span></span> <span data-ttu-id="dad5a-192">これらを解決するには、一部の参照 (たとえば、`Microsoft.AspNet` パッケージと `System` パッケージのほとんど) を削除します。また、一部の `xmlns` 属性を削除しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-192">To resolve them, you'll want to eliminate some references (like most of the `Microsoft.AspNet` and `System` packages), and you may need to remove some `xmlns` attributes.</span></span>

<span data-ttu-id="dad5a-193">ほとんどの ASP.NET MVC アプリでは、Bootstrap や jQuery などの多くのクライアント側の依存関係が NuGet パッケージを使用してデプロイされていました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-193">In most ASP.NET MVC apps, many client-side dependencies like Bootstrap and jQuery were deployed using NuGet packages.</span></span> <span data-ttu-id="dad5a-194">ASP.NET Core では、NuGet パッケージはサーバー側の機能にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-194">In ASP.NET Core, NuGet packages are only used for server-side functionality.</span></span> <span data-ttu-id="dad5a-195">クライアント ファイルは、他の方法で管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-195">Client files should be managed through other means.</span></span> <span data-ttu-id="dad5a-196">追加された `<PackageReference>` 要素のリストを確認し、次に示すクライアント ライブラリ用の要素をすべてメモして削除します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-196">Review the list of `<PackageReference>` elements added and remove and make note of any that are for client libraries, including:</span></span>

- <span data-ttu-id="dad5a-197">ブートストラップ</span><span class="sxs-lookup"><span data-stu-id="dad5a-197">Bootstrap</span></span>
- <span data-ttu-id="dad5a-198">jQuery</span><span class="sxs-lookup"><span data-stu-id="dad5a-198">jQuery</span></span>
- <span data-ttu-id="dad5a-199">jQuery.Validation</span><span class="sxs-lookup"><span data-stu-id="dad5a-199">jQuery.Validation</span></span>
- <span data-ttu-id="dad5a-200">Modernizr</span><span class="sxs-lookup"><span data-stu-id="dad5a-200">Modernizr</span></span>
- <span data-ttu-id="dad5a-201">popper.js</span><span class="sxs-lookup"><span data-stu-id="dad5a-201">popper.js</span></span>
- <span data-ttu-id="dad5a-202">対応</span><span class="sxs-lookup"><span data-stu-id="dad5a-202">Respond</span></span>

<span data-ttu-id="dad5a-203">NuGet によってインストールされたこれらのパッケージ用の静的クライアント ファイルは、新しいプロジェクトの *wwwroot* フォルダーにコピーされ、その場所からホストされます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-203">The static client files installed by NuGet for these packages will be copied over to the new project's *wwwroot* folder and hosted from there.</span></span> <span data-ttu-id="dad5a-204">これらのファイルがアプリで引き続き必要かどうか、およびこれらのファイルを引き続きホストする方法と、代わりにコンテンツ配信ネットワーク (CDN) を使用する方法のどちらが妥当かを検討してください。</span><span class="sxs-lookup"><span data-stu-id="dad5a-204">It's worth considering whether these files are still needed by the app, and whether it makes sense to continue hosting them or to use a content delivery network (CDN) instead.</span></span> <span data-ttu-id="dad5a-205">これらのライブラリ バージョンは、[LibMan](/aspnet/core/client-side/libman/) や [npm](https://www.npmjs.com/) などのツールを使用してビルド時に管理できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-205">These library versions can be managed at build time using tools like [LibMan](/aspnet/core/client-side/libman/) or [npm](https://www.npmjs.com/).</span></span> <span data-ttu-id="dad5a-206">図 4-10 は、変換ツールを使用してパッケージ参照を移行し、不要なパッケージを削除した後の完全な *eShopPorted.csproj* ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-206">Figure 4-10 shows the full *eShopPorted.csproj* file after migrating package references using the conversion tool shown and removing unnecessary packages.</span></span>

![図 4-10](media/Figure4-10.png)

<span data-ttu-id="dad5a-208">**図 4-10**</span><span class="sxs-lookup"><span data-stu-id="dad5a-208">**Figure 4-10.**</span></span> <span data-ttu-id="dad5a-209">*eShopPorted.csproj* ファイル内のパッケージ参照。</span><span class="sxs-lookup"><span data-stu-id="dad5a-209">Package references in the *eShopPorted.csproj* file.</span></span>

<span data-ttu-id="dad5a-210">`<PackageReference>` で `<Version>1.0.0.0</Version>` 要素を `Version=1.0.0.0` 属性にすることで、パッケージ参照をさらに圧縮できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-210">The package references can be further compacted by making the `<Version>1.0.0.0</Version>` element a `Version=1.0.0.0` attribute on `<PackageReference>`.</span></span>

### <a name="migrate-static-files"></a><span data-ttu-id="dad5a-211">静的ファイルを移行する</span><span class="sxs-lookup"><span data-stu-id="dad5a-211">Migrate static files</span></span>

<span data-ttu-id="dad5a-212">アプリが使用するすべての静的ファイル (サードパーティのスクリプトやフレームワークだけでなく、カスタム画像やスタイルシートも含む) を古いプロジェクトから新しいプロジェクトにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-212">Any static files the app uses, including third-party scripts and frameworks but also custom images and stylesheets, must be copied from the old project to the new one.</span></span> <span data-ttu-id="dad5a-213">ASP.NET MVC アプリでは、ファイルへのアクセスは通常、プロジェクト フォルダー内のファイルの場所に基づいて行われていました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-213">In ASP.NET MVC apps, files were typically accessed based on their location within the project folder.</span></span> <span data-ttu-id="dad5a-214">ASP.NET Core アプリでは、このような静的ファイルへのアクセスは、*wwwroot* フォルダー内のファイルの場所に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-214">In ASP.NET Core apps, these static files will be accessed based on their location within the *wwwroot* folder.</span></span> <span data-ttu-id="dad5a-215">*eShop* プロジェクトの場合、静的ファイルは次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-215">For the *eShop* project, there are static files in the following folders:</span></span>

* <span data-ttu-id="dad5a-216">*コンテンツ*</span><span class="sxs-lookup"><span data-stu-id="dad5a-216">*Content*</span></span>
* <span data-ttu-id="dad5a-217">*fonts*</span><span class="sxs-lookup"><span data-stu-id="dad5a-217">*fonts*</span></span>
* <span data-ttu-id="dad5a-218">*イメージ*</span><span class="sxs-lookup"><span data-stu-id="dad5a-218">*Images*</span></span>
* <span data-ttu-id="dad5a-219">*Pics*</span><span class="sxs-lookup"><span data-stu-id="dad5a-219">*Pics*</span></span>
* <span data-ttu-id="dad5a-220">*スクリプト*</span><span class="sxs-lookup"><span data-stu-id="dad5a-220">*Scripts*</span></span>

<span data-ttu-id="dad5a-221">前の手順で使用した **空** のプロジェクト テンプレートには、既定ではこのフォルダーが含まれていません。また、このフォルダーが動作するために必要なミドルウェアもありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-221">The **Empty** project template used in the previous step doesn't include this folder by default, or the middleware needed for it to work.</span></span> <span data-ttu-id="dad5a-222">これらを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-222">You'll need to add them.</span></span>

<span data-ttu-id="dad5a-223">プロジェクトのルートに *wwwroot* フォルダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-223">Add a *wwwroot* folder to the root of the project.</span></span>

<span data-ttu-id="dad5a-224">バージョン 2.2.0 の `Microsoft.AspNetCore.StaticFiles` NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-224">Add version 2.2.0 of the `Microsoft.AspNetCore.StaticFiles` NuGet package.</span></span>

<span data-ttu-id="dad5a-225">*Startup.cs* で、`Configure` メソッドに `app.UseStaticFiles()` の呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-225">In *Startup.cs*, add a call to `app.UseStaticFiles()` in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseStaticFiles();

    // ...
}
```

<span data-ttu-id="dad5a-226">ASP.NET MVC アプリから新しいプロジェクトの *wwwroot* フォルダーに *Content* フォルダーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-226">Copy the *Content* folder from the ASP.NET MVC app to the new project's *wwwroot* folder.</span></span>

<span data-ttu-id="dad5a-227">アプリを実行し、その */Content/base.css* フォルダーに移動して、必要なパスから静的ファイルが正しく提供されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-227">Run the app and navigate to its */Content/base.css* folder to verify that the static file is served correctly from its expected path.</span></span> <span data-ttu-id="dad5a-228">静的ファイルが格納されている残りのフォルダーを新しいプロジェクトに続けてコピーします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-228">Continue copying the rest of the folders containing static files to the new project.</span></span> <span data-ttu-id="dad5a-229">また、必要に応じて、プロジェクトのルートから *wwwroot* フォルダーに *favicon.ico* ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-229">You'll also want to copy the *favicon.ico* file from the project's root to the *wwwroot* folder.</span></span> <span data-ttu-id="dad5a-230">図 4-11 は、これらのファイルとフォルダーがすべてコピーされた後の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-230">Figure 4-11 shows the results after these files and their folders have all been copied.</span></span>

![図 4-11](media/Figure4-11.png)

<span data-ttu-id="dad5a-232">**図 4-11**</span><span class="sxs-lookup"><span data-stu-id="dad5a-232">**Figure 4-11.**</span></span> <span data-ttu-id="dad5a-233">*wwwroot* フォルダーにコピーされた静的フォルダー。</span><span class="sxs-lookup"><span data-stu-id="dad5a-233">Static folders copied over to *wwwroot* folder.</span></span>

### <a name="migrate-c-files"></a><span data-ttu-id="dad5a-234">C# ファイルを移行する</span><span class="sxs-lookup"><span data-stu-id="dad5a-234">Migrate C# files</span></span>

<span data-ttu-id="dad5a-235">次に、アプリで使用される C# ファイルをコピーします。これには、標準の MVC フォルダーとそのコンテンツ (*Controllers*、*Models*、*ViewModel*、*Services* など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-235">Next, copy over the C# files used by the app, including standard MVC folders and their contents like *Controllers*, *Models*, *ViewModel*, and *Services*.</span></span> <span data-ttu-id="dad5a-236">多くの場合、これらのファイルにはいくつかの変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-236">There will most likely be some changes needed in these files.</span></span> <span data-ttu-id="dad5a-237">一度に 1 つのフォルダー (またはサブフォルダー) をコピーしてコンパイルし、対処する必要のあるエラーを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-237">It's best to copy one folder (or subfolder) at a time and compile to see what errors need to be addressed as you go.</span></span>

<span data-ttu-id="dad5a-238">*eShop* サンプルの場合、移行対象として最初に選択したフォルダーは、C# エンティティと Entity Framework クラスを含む *Models* フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-238">For the *eShop* sample, the first folder I choose to migrate is the *Models* folder, which includes C# entities and Entity Framework classes.</span></span> <span data-ttu-id="dad5a-239">このフォルダーのクラスは他のほとんどのクラスで使用されるので、これらのクラスがコピーされるまでは他のクラスが機能しません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-239">This folder's classes are used by most of the others, so they won't work until these classes have been copied.</span></span> <span data-ttu-id="dad5a-240">フォルダーをコピーしてビルドを実行した後で、見つからない名前空間 `System.Web.Hosting` に関連するエラー、`HostingEnvironment` に関連するアクセス、および `ConfigurationManager.AppSettings` への参照をコンパイラが検出しました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-240">After copying the folder and building, the compiler revealed errors related to missing namespace `System.Web.Hosting`, related access to `HostingEnvironment`, and a reference to `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="dad5a-241">このような問題の解決策として、必要なパス データを渡します。現時点では、問題のある行をコメント アウトし、各行に `TODO:` コメントを追加して追跡します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-241">The solution to these issues will be to pass in the necessary path data; for now the breaking lines are commented out and a `TODO:` comment is added to each one to track it.</span></span> <span data-ttu-id="dad5a-242">5 つの行を変更すると、**タスク一覧** に 5 つの項目とプロジェクト ビルドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-242">After changing five lines, the **Task List** shows five items and the project builds.</span></span>

<span data-ttu-id="dad5a-243">次に、1 つのクラスを含む *ViewModel* フォルダーがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-243">Next, the *ViewModel* folder, with its one class, is copied over.</span></span> <span data-ttu-id="dad5a-244">これは簡単な処理であり、即座にビルドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-244">It's an easy one, and builds immediately.</span></span>

<span data-ttu-id="dad5a-245">*Services* フォルダーがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-245">The *Services* folder is copied over.</span></span> <span data-ttu-id="dad5a-246">このフォルダーのクラスは、*Models* フォルダーの Entity Framework クラスに依存しているため、そのフォルダーの後にコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-246">This folder's classes depend on Entity Framework classes from the *Models* folder, which is why it needed to be copied after that folder.</span></span> <span data-ttu-id="dad5a-247">さいわいなことに、ビルド時にエラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-247">Fortunately, it too builds without errors.</span></span>

<span data-ttu-id="dad5a-248">これで、残りは *Controllers* フォルダーとその 2 つの `Controller` クラスになりました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-248">That leaves the *Controllers* folder and its two `Controller` classes.</span></span> <span data-ttu-id="dad5a-249">このフォルダーを新しいプロジェクトにコピーしてビルドを実行すると、7 つのビルド エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-249">After copying the folder to the new project and building, there are seven build errors.</span></span> <span data-ttu-id="dad5a-250">このうちの 4 つは `ViewBag` アクセスに関連するもので、次のようなエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-250">Four of them are related to `ViewBag` access and report an error of:</span></span>

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

<span data-ttu-id="dad5a-251">このエラーを解決するには、NuGet パッケージ参照を C# に追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-251">To resolve this error add a NuGet package reference to C#:</span></span>

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

<span data-ttu-id="dad5a-252">残りの 3 つのエラーは、参照されていないアセンブリで定義されている型を示します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-252">The remaining three errors specify types that are defined in an assembly that isn't referenced.</span></span> <span data-ttu-id="dad5a-253">具体的には次の型です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-253">Specifically these types:</span></span>

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

<span data-ttu-id="dad5a-254">エラーを 1 つずつ確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="dad5a-254">Let's look at each error one by one.</span></span> <span data-ttu-id="dad5a-255">最初のエラーは、既に存在しない `Controller` の `Server` プロパティを参照しようとすると発生します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-255">The first error occurs while trying to reference the `Server` property of `Controller`, which no longer exists.</span></span> <span data-ttu-id="dad5a-256">この操作の目的は、アプリ内の画像ファイルへのパスを取得することです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-256">The goal of the operation is to get the path to an image file in the app:</span></span>

```csharp
if (item != null)
{
    var webRoot = Server.MapPath("~/Pics"); // compiler error on this line
    var path = Path.Combine(webRoot, item.PictureFileName);

    string imageFileExtension = Path.GetExtension(item.PictureFileName);
    string mimetype = GetImageMimeTypeFromImageFileExtension(imageFileExtension);

    var buffer = System.IO.File.ReadAllBytes(path);

    return File(buffer, mimetype);
}
```

<span data-ttu-id="dad5a-257">この問題には 2 つの解決策があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-257">There are two possible solutions to this problem.</span></span> <span data-ttu-id="dad5a-258">1 つ目は、機能をそのまま維持する方法です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-258">The first is to keep the functionality as it is.</span></span> <span data-ttu-id="dad5a-259">この場合、`Server.MapPath` を使用するのではなく、*wwwroot* 内の画像ファイルの場所を参照する修正されたパスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-259">In this case, rather than using `Server.MapPath`, a fixed path referencing the image files' location in *wwwroot* should be used.</span></span> <span data-ttu-id="dad5a-260">または、このアクション メソッドの唯一の目的は静的な画像ファイルを返すことであるため、ビュー ファイル内のこのアクションへの参照を更新して静的ファイルを直接参照することができます。これにより、実行時のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-260">Alternately, since the only purpose of this action method is to return a static image file, the references to this action in view files can be updated to reference the static files directly, which improves runtime performance.</span></span> <span data-ttu-id="dad5a-261">このアクションの一部としては何の処理も行われないため、ファイルを直接提供しない理由はありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-261">Since no processing is being done as part of this action, there's no reason not to just serve the files directly.</span></span> <span data-ttu-id="dad5a-262">このアクションへのすべての参照を更新できない場合は、アクションを書き換えて、静的ファイルの場所へのリダイレクトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-262">If it's not tenable to update all references to this action, the action could be rewritten to produce a redirect to the static file's location.</span></span>

<span data-ttu-id="dad5a-263">次の 2 つのエラーは、どちらも同じコード行の同じプライベート メソッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-263">The next two errors both occur in the same private method in the same line of code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="dad5a-264">`this.Url` と `this.Request` の両方が原因でコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-264">Both `this.Url` and `this.Request` cause compiler errors.</span></span> <span data-ttu-id="dad5a-265">このコードの使用方法によると、これは画像ファイルをレンダリングする `PicController` アクションへのリンクを作成することを目的としたコードです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-265">Looking at how this code is used, its purpose is to build a link to the `PicController` action that renders image files.</span></span> <span data-ttu-id="dad5a-266">先ほど検出されたのと同じものが、*wwwroot* にある静的ファイルへの直接リンクに置き換えられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-266">The same one we just discovered could probably be replaced with direct links to the static files located in *wwwroot*.</span></span> <span data-ttu-id="dad5a-267">現時点では、このコードをコメント アウトして、別の方法で Pics を参照する `TODO:` コメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-267">For now, it's worth commenting out this code and adding a `TODO:` comment to reference the pics another way.</span></span>

<span data-ttu-id="dad5a-268">注目すべき点は、このコードが表示されている `CatalogController` クラスで使用される基底クラス `Controller` が引き続き `System.Web.Mvc.Controller` を参照していることです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-268">It's worth noting that the base `Controller` class, used by the `CatalogController` class in which this code appears, is still referring to `System.Web.Mvc.Controller`.</span></span> <span data-ttu-id="dad5a-269">ASP.NET Core を使用するようにこれを更新すると、修正が必要なエラーの数は間違いなく増加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-269">There will undoubtedly be more errors to fix once we update this to use ASP.NET Core.</span></span> <span data-ttu-id="dad5a-270">最初に、`CatalogController` の `using` ステートメントのリストから `using System.Web.Mvc;` 行を削除します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-270">First, remove the `using System.Web.Mvc;` line from the list of `using` statements in `CatalogController`.</span></span> <span data-ttu-id="dad5a-271">次に、NuGet パッケージ `Microsoft.AspNetCore.Mvc` を追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-271">Next, add the NuGet package `Microsoft.AspNetCore.Mvc`.</span></span> <span data-ttu-id="dad5a-272">最後に、`using Microsoft.AspNetCore.Mvc;` ステートメントを追加して、アプリをもう一度ビルドします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-272">Finally, add a `using Microsoft.AspNetCore.Mvc;` statement, and build the app again.</span></span>

<span data-ttu-id="dad5a-273">今回は 16 個のエラーがあります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-273">This time, there are 16 errors:</span></span>

- <span data-ttu-id="dad5a-274">`Include` が有効な名前付き属性引数ではありません (2)</span><span class="sxs-lookup"><span data-stu-id="dad5a-274">`Include` is not a valid named attribute argument (2)</span></span>
- <span data-ttu-id="dad5a-275">`HttpStatusCodeResult` が見つかりません (3)</span><span class="sxs-lookup"><span data-stu-id="dad5a-275">`HttpStatusCodeResult` not found (3)</span></span>
- <span data-ttu-id="dad5a-276">`HttpNotFound` が存在しません (3)</span><span class="sxs-lookup"><span data-stu-id="dad5a-276">`HttpNotFound` does not exist (3)</span></span>
- <span data-ttu-id="dad5a-277">`SelectList` が見つかりません (8)</span><span class="sxs-lookup"><span data-stu-id="dad5a-277">`SelectList` not found (8)</span></span>

<span data-ttu-id="dad5a-278">再び、これらのエラーを 1 つずつ確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="dad5a-278">Once more, let's review these errors one by one.</span></span> <span data-ttu-id="dad5a-279">最初に、`using Microsoft.AspNetCore.Mvc.Rendering;` を追加して `SelectList` を修正できます。これで、半分のエラーが解消します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-279">First, `SelectList` can be fixed by adding `using Microsoft.AspNetCore.Mvc.Rendering;`, which eliminates half of the errors.</span></span>

<span data-ttu-id="dad5a-280">`return HttpNotFound();` へのすべての参照を `return NotFound();` に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-280">All references to `return HttpNotFound();` should be replaced with `return NotFound();`.</span></span>

<span data-ttu-id="dad5a-281">`return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` へのすべての参照を `return BadRequest();` に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-281">All references to `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` should be replaced with `return BadRequest();`.</span></span>

<span data-ttu-id="dad5a-282">これで、次に示すようないくつかのアクション メソッドにおける `[Bind]` 属性を指定した `Include` の使用が残ります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-282">That just leaves the use of `Include` with a `[Bind]` attribute on a couple of action methods that look like this:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="dad5a-283">上のコードでは、モデル バインドを `Include` 文字列に示されているプロパティに制限しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-283">The preceding code restricts model binding to the properties listed in the `Include` string.</span></span> <span data-ttu-id="dad5a-284">ASP.NET Core MVC では、`[Bind]` 属性は引き続き存在しますが、`Include =` 引数は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-284">In ASP.NET Core MVC, the `[Bind]` attribute still exists, but no longer needs the `Include =` argument.</span></span> <span data-ttu-id="dad5a-285">`[Bind]` 属性にプロパティのリストを直接渡します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-285">Pass the list of properties directly to the `[Bind]` attribute:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="dad5a-286">これらの変更により、プロジェクトがもう一度コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-286">With these changes, the project compiles once more.</span></span> <span data-ttu-id="dad5a-287">通常は、ドメイン モデルまたはデータ モデルの型に対して直接モデル バインドを使用するのではなく、コントローラーの入力に個別のモデルの型を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-287">It's generally a better practice to use separate model types for controller inputs, rather than using model binding directly to your domain model or data model types.</span></span>

## <a name="migrate-views"></a><span data-ttu-id="dad5a-288">ビューを移行する</span><span class="sxs-lookup"><span data-stu-id="dad5a-288">Migrate views</span></span>

<span data-ttu-id="dad5a-289">ビューに関連する ASP.NET Core MVC の 2 つの最大の機能は、[Razor Pages](/aspnet/core/razor-pages/) と[タグ ヘルパー](/aspnet/core/mvc/views/tag-helpers/built-in/)です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-289">The two biggest ASP.NET Core MVC features related to views are [Razor Pages](/aspnet/core/razor-pages/) and [Tag Helpers](/aspnet/core/mvc/views/tag-helpers/built-in/).</span></span> <span data-ttu-id="dad5a-290">最初の移行では、どちらの機能も使用しません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-290">For the initial migration, we won't use either feature.</span></span> <span data-ttu-id="dad5a-291">ただし、移行後もアプリのサポートを継続する場合は、これらの機能を記憶に留めておいてください。</span><span class="sxs-lookup"><span data-stu-id="dad5a-291">You should, however, keep the features in mind if you continue supporting the app once it's been migrated.</span></span> <span data-ttu-id="dad5a-292">次の手順では、*Views* フォルダーを元のプロジェクトから新しいプロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-292">The next step is to copy the *Views* folder from the original project into the new one.</span></span> <span data-ttu-id="dad5a-293">ビルド後は次に示す 9 つのエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-293">After building, there are nine errors:</span></span>

- <span data-ttu-id="dad5a-294">HttpContext が存在しません (2)</span><span class="sxs-lookup"><span data-stu-id="dad5a-294">HttpContext does not exist (2)</span></span>
- <span data-ttu-id="dad5a-295">スクリプトが存在しません (5)</span><span class="sxs-lookup"><span data-stu-id="dad5a-295">Scripts does not exist (5)</span></span>
- <span data-ttu-id="dad5a-296">スタイルが存在しません (1)</span><span class="sxs-lookup"><span data-stu-id="dad5a-296">Styles does not exist (1)</span></span>
- <span data-ttu-id="dad5a-297">HtmlString が見つかりませんでした (1)</span><span class="sxs-lookup"><span data-stu-id="dad5a-297">HtmlString could not be found(1)</span></span>

<span data-ttu-id="dad5a-298">これらのエラーを調べると、ほとんどがメインの *_Layout.cshtml* で発生していることがわかります。エラーには、スクリプトとスタイルのタグのレンダリングに関連するものと、アプリをホストしているサーバーが最後に再起動されたときの表示に関連するものがあります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-298">Investigating these errors finds that most of them are in the main *_Layout.cshtml*, with several related to rendering script and style tags, or displaying when the server hosting the app was last restarted.</span></span> <span data-ttu-id="dad5a-299">次のコード リストは、 *_Layout.cshtml* ファイル内で問題が発生している部分を示しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-299">The following code listing shows problem areas in the *_Layout.cshtml* file:</span></span>

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

<span data-ttu-id="dad5a-300">Modernizr への参照は削除できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-300">The reference to Modernizr can be removed.</span></span> <span data-ttu-id="dad5a-301">Bootstrap と jQuery への参照は、適切なバージョンへの CDN リンクに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-301">The references to Bootstrap and jQuery can be replaced with CDN links to the appropriate version.</span></span>

<span data-ttu-id="dad5a-302">`@Styles.Render` 行を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-302">Replace `@Styles.Render` line with:</span></span>

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

<span data-ttu-id="dad5a-303">最後の 2 つの `Scripts.Render` 行を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-303">Replace the last two `Scripts.Render` lines with:</span></span>

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

<span data-ttu-id="dad5a-304">最後は、Bootstrap `<link>` の後に、アプリで使用するローカル スタイルの `<link>` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-304">Finally, after the Bootstrap `<link>`, add additional `<link>` elements for local styles your app uses.</span></span> <span data-ttu-id="dad5a-305">*eShop* の場合、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-305">For *eShop*, the result is shown here:</span></span>

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

<span data-ttu-id="dad5a-306">`<link>` 要素の表示順序を決定するには、元のアプリのレンダリングされた HTML を確認します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-306">To determine the order in which the `<link>` elements should appear, look at your original app's rendered HTML.</span></span> <span data-ttu-id="dad5a-307">または、*BundleConfig.cs* を確認します。*eShop* サンプルの場合、このファイルには、適切なシーケンスを示す次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-307">Alternatively, review *BundleConfig.cs*, which for the *eShop* sample includes this code indicating the appropriate sequence:</span></span>

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

<span data-ttu-id="dad5a-308">再度ビルドすると、"*作成*" ビューと "*編集*" ビューにおける jQuery Validation の読み込みエラーがもう 1 つ発生します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-308">Building again reveals one more error loading jQuery Validation on the *Create* and *Edit* views.</span></span> <span data-ttu-id="dad5a-309">これを次のスクリプトに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-309">Replace it with this script:</span></span>

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

<span data-ttu-id="dad5a-310">ビューで最後に修正するのは、アプリが実行されている時間とマシンを表示する `Session` への参照です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-310">The last thing to fix in the views is the reference to `Session` to display how long the app has been running, and on which machine.</span></span> <span data-ttu-id="dad5a-311">このデータをサイトの *_Layout.cshtml* に直接表示するには、`System.Environment.MachineName` および `System.Diagnostics.Process.GetCurrentProcess().StartTime` を使用します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-311">We can display this data directly in the site's *_Layout.cshtml* by using `System.Environment.MachineName` and `System.Diagnostics.Process.GetCurrentProcess().StartTime`:</span></span>

```razor
<section class="col-sm-6">
    <img class="esh-app-footer-text hidden-xs" src="~/images/main_footer_text.png" width="335" height="26" alt="footer text image" />
    <br />
<small>@Environment.MachineName - @System.Diagnostics.Process.GetCurrentProcess().StartTime.ToString() UTC</small>
</section>
```

<span data-ttu-id="dad5a-312">この時点で、再度アプリがビルドされ、正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-312">At this point, the app once more builds successfully.</span></span> <span data-ttu-id="dad5a-313">ただし、それを実行しようとすると *Hello World!* が中断します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-313">However, trying to run it just yields *Hello World!*</span></span> <span data-ttu-id="dad5a-314">これは、**空** の ASP.NET Core テンプレートが要求に応じてそのプログラムを表示するようにのみ構成されているためです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-314">because the **Empty** ASP.NET Core template is only configured to display that in response to any request.</span></span> <span data-ttu-id="dad5a-315">次のセクションでは、ASP.NET Core MVC を使用するようにアプリを構成して移行を完了します。これには、依存関係の挿入や構成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-315">In the next section, I complete the migration by configuring the app to use ASP.NET Core MVC, including dependency injection and configuration.</span></span> <span data-ttu-id="dad5a-316">準備が整ったら、アプリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-316">Once that's in place, the app should run.</span></span> <span data-ttu-id="dad5a-317">その後で、以前に作成された `TODO:` タスクを修正します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-317">Then it will be time to fix the `TODO:` tasks that were created earlier.</span></span>

## <a name="migrate-app-startup-components"></a><span data-ttu-id="dad5a-318">アプリのスタートアップ コンポーネントを移行する</span><span class="sxs-lookup"><span data-stu-id="dad5a-318">Migrate app startup components</span></span>

<span data-ttu-id="dad5a-319">最後の移行手順では、*Global.asax* からアプリのスタートアップ タスクを実行し、そのアプリが呼び出すクラスを ASP.NET Core のクラスに移行します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-319">The last migration step is to take the app startup tasks from *Global.asax*, and the classes it calls, and migrate these to their ASP.NET Core equivalents.</span></span> <span data-ttu-id="dad5a-320">これらのタスクには、MVC 自体の構成、依存関係の挿入の設定、新しい構成システムの操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-320">These tasks include configuration of MVC itself, setting up dependency injection, and working with the new configuration system.</span></span> <span data-ttu-id="dad5a-321">ASP.NET Core では、これらのタスクは *Startup.cs* ファイルで処理されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-321">In ASP.NET Core, these tasks are handled in the *Startup.cs* file.</span></span>

### <a name="configure-mvc"></a><span data-ttu-id="dad5a-322">MVC を構成する</span><span class="sxs-lookup"><span data-stu-id="dad5a-322">Configure MVC</span></span>

<span data-ttu-id="dad5a-323">元の ASP.NET MVC アプリでは、*Global.asax* の `Application_Start` に次のコードが含まれています。このコードはアプリの起動時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-323">The original ASP.NET MVC app has the following code in its `Application_Start` in *Global.asax*, which runs when the app starts up:</span></span>

```csharp
protected void Application_Start()
{
    container = RegisterContainer();
    AreaRegistration.RegisterAllAreas();
    FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
    RouteConfig.RegisterRoutes(RouteTable.Routes);
    BundleConfig.RegisterBundles(BundleTable.Bundles);
    ConfigDataBase();
}
```

<span data-ttu-id="dad5a-324">これらを 1 行ずつ確認すると、`RegisterContainer` メソッドは依存関係の挿入を設定します。これは以下に示すように移植されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-324">Looking at these lines one by one, the `RegisterContainer` method sets up dependency injection, which will be ported below.</span></span> <span data-ttu-id="dad5a-325">次の 3 行は、MVC のさまざまなパーツ (区分、フィルター、ルート) を構成します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-325">The next three lines configure different parts of MVC: areas, filters, and routes.</span></span> <span data-ttu-id="dad5a-326">バンドルは、移植されたアプリ内の静的ファイルに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-326">Bundles are replaced by static files in the ported app.</span></span> <span data-ttu-id="dad5a-327">最後の行は、アプリのデータ アクセスを設定します。これについては後述します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-327">The last line sets up data access for the app, which will be shown in a later section.</span></span>

<span data-ttu-id="dad5a-328">このアプリは実際には区分を使用していないため、区分登録の呼び出しを移行するために必要な作業はありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-328">Since this app isn't actually using areas, there's nothing that needs to be done to migrate the area registration call.</span></span> <span data-ttu-id="dad5a-329">アプリで区分を移行する必要がある場合は、[ASP.NET Core における区分の構成方法がドキュメントで指定されています](/aspnet/core/mvc/controllers/areas)。</span><span class="sxs-lookup"><span data-stu-id="dad5a-329">If your app does need to migrate areas, the [docs specify how to configure areas in ASP.NET Core](/aspnet/core/mvc/controllers/areas).</span></span>

<span data-ttu-id="dad5a-330">グローバル フィルターの登録のための呼び出しでは、アプリの *App_Start* フォルダー内の `FilterConfig` クラスでヘルパーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-330">The call to register global filters invokes a helper on the `FilterConfig` class in the app's *App_Start* folder:</span></span>

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

<span data-ttu-id="dad5a-331">アプリに追加される属性は、ASP.NET MVC フィルター `HandleErrorAttribute` のみです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-331">The only attribute added to the app is the ASP.NET MVC filter, `HandleErrorAttribute`.</span></span> <span data-ttu-id="dad5a-332">このフィルターにより、要求の一部として例外が発生したときに、例外の詳細ではなく既定のアクションとビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-332">This filter ensures that when an exception occurs as part of a request, a default action and view are displayed, rather than the exception details.</span></span> <span data-ttu-id="dad5a-333">ASP.NET Core では、この同じ機能が `UseExceptionHandler` ミドルウェアによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-333">In ASP.NET Core, this same functionality is performed by the `UseExceptionHandler` middleware.</span></span> <span data-ttu-id="dad5a-334">詳細なエラー メッセージは、既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-334">The detailed error messages aren't enabled by default.</span></span> <span data-ttu-id="dad5a-335">`UseDeveloperExceptionPage` ミドルウェアを使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-335">They must be configured using the `UseDeveloperExceptionPage` middleware.</span></span> <span data-ttu-id="dad5a-336">元のアプリと一致するようにこの動作を構成するには、*Startup.cs* の `Configure` メソッドの先頭に次のコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-336">To configure this behavior to match the original app, the following code must be added to the start of the `Configure` method in *Startup.cs*:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
    }
    // ...
}
```

<span data-ttu-id="dad5a-337">これは、eShop アプリで使用される唯一のフィルターを処理します。ここでは、組み込みのミドルウェアを使用して実行されました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-337">This takes care of the only filter used by the eShop app, and in this case it was done by using built-in middleware.</span></span> <span data-ttu-id="dad5a-338">グローバル フィルターをアプリで構成する必要がある場合は、MVC が `ConfigureServices` メソッドで追加されるときにこの処理が行われます。これについては、本章で後述します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-338">If you have global filters that must be configured in your app, this is done when MVC is added in the `ConfigureServices` method, which is shown later in this chapter.</span></span>

<span data-ttu-id="dad5a-339">移行が必要な MVC 関連のロジックの最後の部分は、アプリの既定のルートです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-339">The last piece of MVC-related logic that needs to be migrated are the app's default routes.</span></span> <span data-ttu-id="dad5a-340">`RouteConfig.RegisterRoutes(RouteTable.Routes)` の呼び出しにより、MVC ルート テーブルが `RegisterRoutes` ヘルパー メソッドに渡されます。このメソッドでは、アプリの起動時に次のコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-340">The call to `RouteConfig.RegisterRoutes(RouteTable.Routes)` passes the MVC route table to the `RegisterRoutes` helper method, where the following code is executed when the app starts up:</span></span>

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.MapMvcAttributeRoutes();
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Catalog", action = "Index", id = UrlParameter.Optional }
    );
}
```

<span data-ttu-id="dad5a-341">このコードを 1 行ずつ確認すると、最初の行では属性ルートのサポートが設定されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-341">Taking this code line-by-line, the first line sets up support for attribute routes.</span></span> <span data-ttu-id="dad5a-342">これは ASP.NET Core に組み込まれているため、個別に構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-342">This is built into ASP.NET Core, so it's unnecessary to configure it separately.</span></span> <span data-ttu-id="dad5a-343">同様に、 *{resource}.axd* ファイルは ASP.NET Core では使用されないため、このようなルートを無視する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-343">Likewise, *{resource}.axd* files aren't used with ASP.NET Core, so there's no need to ignore such routes.</span></span> <span data-ttu-id="dad5a-344">`MapRoute` メソッドは、一般的な `{controller}/{action}/{id}` ルート テンプレートを使用する MVC の既定値を構成します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-344">The `MapRoute` method configures the default for MVC, which uses the typical `{controller}/{action}/{id}` route template.</span></span> <span data-ttu-id="dad5a-345">また、`CatalogController` が使用される既定のコントローラー、`Index` メソッドが既定のアクションになるように、このテンプレートの既定値も指定します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-345">It also specifies the defaults for this template, such that the `CatalogController` is the default controller used and the `Index` method is the default action.</span></span> <span data-ttu-id="dad5a-346">大規模なアプリには、追加のルートを設定するために `MapRoute` の呼び出しが多く含まれていることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-346">Larger apps will frequently include more calls to `MapRoute` to set up additional routes.</span></span>

<span data-ttu-id="dad5a-347">ASP.NET Core MVC では、[従来のルーティングと属性ルーティング](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2)がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-347">ASP.NET Core MVC supports [conventional routing and attribute routing](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2).</span></span> <span data-ttu-id="dad5a-348">従来のルーティングは、前述の `RegisterRoutes` メソッドでルート テーブルを構成する方法に似ています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-348">Conventional routing is analogous to how the route table is configured in the `RegisterRoutes` method listed previously.</span></span> <span data-ttu-id="dad5a-349">既定のルート (*eShop* アプリで使用されるものなど) を使用して従来のルーティングを設定するには、*Startup.cs* の `Configure` メソッドの末尾に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-349">To set up conventional routing with a default route like the one used in the *eShop* app, add the following code to the bottom of the `Configure` method in *Startup.cs*:</span></span>

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> <span data-ttu-id="dad5a-350">ASP.NET Core 3.0 以降では、これがエンドポイントを使用するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-350">With ASP.NET Core 3.0 and later, this is changed to use endpoints.</span></span> <span data-ttu-id="dad5a-351">ASP.NET Core 2.2 への最初の移植では、これが従来のルートのマッピングに適した構文です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-351">For the initial port to ASP.NET Core 2.2, this is the proper syntax for mapping conventional routes.</span></span>

<span data-ttu-id="dad5a-352">これらの変更が適用されると、`Configure` メソッドはほぼ完了です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-352">With these changes in place, the `Configure` method is almost done.</span></span> <span data-ttu-id="dad5a-353">*Hello World!* を出力する元のテンプレートの `app.Run` メソッド</span><span class="sxs-lookup"><span data-stu-id="dad5a-353">The original template's `app.Run` method that prints *Hello World!*</span></span> <span data-ttu-id="dad5a-354">は削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-354">should be deleted.</span></span> <span data-ttu-id="dad5a-355">この時点で、メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-355">At this point, the method is as shown here:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
    }

    app.UseStaticFiles();

    app.UseMvc(routes =>
    {
        routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="dad5a-356">次に、MVC サービスを構成し、続いてアプリによる依存関係の挿入 (DI) のサポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-356">Now it's time to configure MVC services, followed by the rest of the app's support for dependency injection (DI).</span></span> <span data-ttu-id="dad5a-357">ここまでは、*eShopPorted* プロジェクトの `ConfigureServices` メソッドは空のままです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-357">So far, the *eShopPorted* project's `ConfigureServices` method has remained empty.</span></span> <span data-ttu-id="dad5a-358">ここで読み込みを開始します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-358">Now it's time to start populating it.</span></span>

<span data-ttu-id="dad5a-359">まず、ASP.NET Core MVC を適切に動作させるために、次のように追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-359">First, to get ASP.NET Core MVC to work properly, it needs to be added:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

<span data-ttu-id="dad5a-360">上のコードは、MVC の機能を使用するために必要な最小限の構成です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-360">The preceding code is the minimal configuration required to get MVC features working.</span></span> <span data-ttu-id="dad5a-361">この呼び出しから構成できる追加機能は多数あります (この章で後ほど詳しく説明しています) が、ここでは、これでアプリをビルドするのに十分です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-361">There are many additional features that can be configured from this call (some of which are detailed later in this chapter), but for now this will suffice to build the app.</span></span> <span data-ttu-id="dad5a-362">これを実行すると、既定の要求が適切にルーティングされるようになりましたが、DI をまだ構成していないため、`CatalogController` をアクティブ化する際にエラーが発生します。これは、`ICatalogService` 型の実装がまだ指定されていないためです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-362">Running it now routes the default request properly, but since we've not yet configured DI, an error occurs while activating `CatalogController`, because no implementation of type `ICatalogService` has been provided yet.</span></span> <span data-ttu-id="dad5a-363">MVC の追加の構成については後述します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-363">We'll return to configure MVC further in a moment.</span></span> <span data-ttu-id="dad5a-364">ここでは、アプリの依存関係の挿入を移行してみましょう。</span><span class="sxs-lookup"><span data-stu-id="dad5a-364">For now, let's migrate the app's dependency injection.</span></span>

#### <a name="migrate-dependency-injection-configuration"></a><span data-ttu-id="dad5a-365">依存関係の挿入の構成を移行する</span><span class="sxs-lookup"><span data-stu-id="dad5a-365">Migrate dependency injection configuration</span></span>

<span data-ttu-id="dad5a-366">元のアプリの *Global.asax* ファイルでは、アプリの起動時に呼び出される次のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-366">The original app's *Global.asax* file defines the following method, called when the app starts up:</span></span>

```csharp
protected IContainer RegisterContainer()
{
  var builder = new ContainerBuilder();

  builder.RegisterControllers(typeof(MvcApplication).Assembly);

  var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
  builder.RegisterModule(new ApplicationModule(mockData));

  var container = builder.Build();
  DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

  return container;
}
```

<span data-ttu-id="dad5a-367">このコードは、[Autofac](https://autofac.org/) コンテナーを構成し、構成設定を読み取って、実際のデータとモック データのどちらを使用する必要があるかを判断し、この設定を (アプリの */Modules* ディレクトリにある) Autofac モジュールに渡します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-367">This code configures an [Autofac](https://autofac.org/) container, reads a config setting to determine whether real or mock data should be used, and passes this setting into an Autofac module (found in the app's */Modules* directory).</span></span> <span data-ttu-id="dad5a-368">さいわいなことに、Autofac では .NET Core がサポートされるので、モジュールを直接移行できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-368">Fortunately, Autofac supports .NET Core, so the module can be migrated directly.</span></span> <span data-ttu-id="dad5a-369">フォルダーを新しいプロジェクトにコピーし、クラスの名前空間を更新して、コンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-369">Copy the folder into the new project and updates the class's namespace and it should compile.</span></span>

<span data-ttu-id="dad5a-370">ASP.NET Core には依存関係の挿入のサポートが組み込まれていますが、必要に応じて、Autofac などのサードパーティのコンテナーを簡単に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-370">ASP.NET Core has built-in support for dependency injection, but you can wire up a third-party container such as Autofac easily if necessary.</span></span> <span data-ttu-id="dad5a-371">この場合、アプリは Autofac を使用するように既に構成されているので、その使用を維持することが最も簡単な解決策です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-371">In this case, since the app is already configured to use Autofac, the simplest solution is to maintain its usage.</span></span> <span data-ttu-id="dad5a-372">そのためには、`ConfigureServices` メソッド シグネチャを変更して `IServiceProvider` を返す必要があります。また、Autofac コンテナー インスタンスを構成してメソッドから返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-372">To do so, the `ConfigureServices` method signature must be modified to return an `IServiceProvider`, and the Autofac container instance must be configured and returned from the method.</span></span>

<span data-ttu-id="dad5a-373">**注:** .NET Core 3.0 以降では、サードパーティの DI コンテナーを統合するためのプロセスが変更されました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-373">**Note:** In .NET Core 3.0 and later, the process for integrating a third-party DI container has changed.</span></span>

<span data-ttu-id="dad5a-374">Autofac の構成の一部では、`builder.Populate(services)` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-374">Part of configuring Autofac requires a call to `builder.Populate(services)`.</span></span> <span data-ttu-id="dad5a-375">この拡張機能は、`Autofac.Extensions.DependencyInjection` NuGet パッケージに含まれています。このパッケージは、コードをコンパイルする前にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-375">This extension is found in the `Autofac.Extensions.DependencyInjection` NuGet package, which must be installed before the code will compile.</span></span>

<span data-ttu-id="dad5a-376">Autofac コンテナーを構成するために `ConfigureServices` を変更した後、新しいメソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-376">After modifying `ConfigureServices` to configure an Autofac container, the new method is as shown here:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    bool useMockData = true; // TODO: read from config
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

<span data-ttu-id="dad5a-377">ここでは、`useMockData` は `true` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-377">For now, the setting for `useMockData` is set to `true`.</span></span> <span data-ttu-id="dad5a-378">この設定はすぐに構成から読み取られます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-378">This setting will be read from configuration in a moment.</span></span> <span data-ttu-id="dad5a-379">図 4-12 に示すように、この時点でアプリがコンパイルされ、実行時に正常に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-379">At this point, the app compiles and should load successfully when run, as shown in Figure 4-12.</span></span>

![図 4-12](media/Figure4-12.png)

<span data-ttu-id="dad5a-381">**図 4-12**</span><span class="sxs-lookup"><span data-stu-id="dad5a-381">**Figure 4-12.**</span></span> <span data-ttu-id="dad5a-382">移植された *eShop* アプリ (モック データを使用してローカルで実行)。</span><span class="sxs-lookup"><span data-stu-id="dad5a-382">Ported *eShop* app running locally with mock data.</span></span>

#### <a name="migrate-app-settings"></a><span data-ttu-id="dad5a-383">アプリの設定を移行する</span><span class="sxs-lookup"><span data-stu-id="dad5a-383">Migrate app settings</span></span>

<span data-ttu-id="dad5a-384">ASP.NET Core は新しい [構成システム](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2)を使用します。既定では、*appsettings.json* ファイルが活用されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-384">ASP.NET Core uses a new [configuration system](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2), which by default leverages an *appsettings.json* file.</span></span> <span data-ttu-id="dad5a-385">*Program.cs* の `CreateDefaultBuilder` を使用して、既定の構成がアプリで既に設定されています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-385">By using `CreateDefaultBuilder` in *Program.cs*, the default configuration is already set up in the app.</span></span> <span data-ttu-id="dad5a-386">構成にアクセスするには、クラスのコンストラクターで構成を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-386">To access configuration, classes just need to request it in their constructor.</span></span> <span data-ttu-id="dad5a-387">`Startup` クラスは例外ではありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-387">The `Startup` class is no exception.</span></span> <span data-ttu-id="dad5a-388">`Startup` の構成と残りのアプリへのアクセスを開始するには、そのコンストラクターから `IConfiguration` のインスタンスを要求します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-388">To start accessing configuration in `Startup` and the rest of the app, request an instance of `IConfiguration` from its constructor:</span></span>

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

<span data-ttu-id="dad5a-389">元のアプリでは、`ConfigurationManager.AppSettings` を使用してその設定を参照していました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-389">The original app referenced its settings using `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="dad5a-390">この条件のすべての参照のクイック検索を実行すると、新しいアプリに必要な一連の設定が生成されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-390">A quick search for all references of this term yields the set of settings the new app needs.</span></span> <span data-ttu-id="dad5a-391">生成されるのは次の 2 つだけです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-391">There are only two:</span></span>

- `UseMockData`
- `UseCustomizationData`

<span data-ttu-id="dad5a-392">アプリの構成が複雑な場合 (特にカスタム構成セクションを使用している場合) は、オブジェクトを作成して、アプリの構成のさまざまな部分にバインドすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-392">If your app has more complex configuration, especially if it's using custom configuration sections, you'll probably want to create and bind objects to different parts of your app's configuration.</span></span> <span data-ttu-id="dad5a-393">[オプション パターン](../../core/extensions/options.md)を使用してこれらの型にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-393">These types can then be accessed using the [options pattern](../../core/extensions/options.md).</span></span> <span data-ttu-id="dad5a-394">ただし、参照先のドキュメントで示されているように、このパターンを `ConfigureServices` で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-394">However, as noted in the referenced doc, this pattern shouldn't be used in `ConfigureServices`.</span></span> <span data-ttu-id="dad5a-395">代わりに、移植されたアプリは `UseMockData` 構成値を直接参照します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-395">Instead the ported app will reference the `UseMockData` configuration value directly.</span></span>

<span data-ttu-id="dad5a-396">まず、移植されたアプリの `appsettings.json` ファイルを変更して、ルートに 2 つの設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-396">First, modify the ported app's `appsettings.json` file and add the two settings in the root:</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "true",
  "UseCustomizationData" :  "true"
}
```

<span data-ttu-id="dad5a-397">次に、`Configuration` プロパティから `UseMockData` 設定 (以前に値を `true` に設定) にアクセスするように `ConfigureServices` を変更します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-397">Now, modify `ConfigureServices` to access the `UseMockData` setting from the `Configuration` property (where previously we set the value to `true`):</span></span>

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

<span data-ttu-id="dad5a-398">この時点で、構成から設定がプルされます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-398">At this point, the setting is pulled from configuration.</span></span> <span data-ttu-id="dad5a-399">もう 1 つの設定である `UseCustomizationData` は `CatalogDBInitializer` クラスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-399">The other setting, `UseCustomizationData`, is used by the `CatalogDBInitializer` class.</span></span> <span data-ttu-id="dad5a-400">このクラスを最初に移植したときに、`ConfigurationManager.AppSettings["UseCustomizationData"]` へのアクセスをコメント アウトしています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-400">When you first ported this class, you commented out the access to `ConfigurationManager.AppSettings["UseCustomizationData"]`.</span></span> <span data-ttu-id="dad5a-401">次に、ASP.NET Core 構成を使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-401">Now it's time to modify it to use ASP.NET Core configuration.</span></span> <span data-ttu-id="dad5a-402">`CatalogDBInitializer` のコンストラクターを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-402">Modify the constructor of `CatalogDBInitializer` as follows:</span></span>

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

<span data-ttu-id="dad5a-403">新しい `IConfiguration` 型を使用するには、Web アプリ内の構成へのすべてのアクセスをこの方法で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-403">All access to configuration within the web app should be modified in this manner to use the new `IConfiguration` type.</span></span> <span data-ttu-id="dad5a-404">.NET Framework 構成へのアクセスを必要とする依存関係では、Web プロジェクトに追加された *app.config* ファイルにこのような設定を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-404">Dependencies that require access to .NET Framework configuration can include such settings in an *app.config* file added to the web project.</span></span> <span data-ttu-id="dad5a-405">依存プロジェクトは、`ConfigurationManager` を使用して設定にアクセスできます。また、この方法を既に使用している場合、変更は不要です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-405">The dependent projects can work with `ConfigurationManager` to access settings, and shouldn't require any changes if they already use this approach.</span></span> <span data-ttu-id="dad5a-406">ただし、ASP.NET Core アプリは独自の実行可能ファイルとして実行されるため、*web.config* ではなく *app.config* を参照します。レガシ アプリの *web.config* ファイルから ASP.NET Core アプリ内の新しい *app.config* ファイルに設定を移行することで、`ConfigurationManager` を使用して設定にアクセスするコンポーネントは引き続き適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-406">However, since ASP.NET Core apps run as their own executable, they don't reference *web.config* but rather *app.config*. By migrating settings from the legacy app's *web.config* file to a new *app.config* file in the ASP.NET Core app, components that use `ConfigurationManager` to access their settings will continue to function properly.</span></span>

<span data-ttu-id="dad5a-407">アプリの移行はほぼ完了です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-407">The app's migration is nearly complete.</span></span> <span data-ttu-id="dad5a-408">残りのタスクはデータ アクセスの構成のみです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-408">The only remaining task is data access configuration.</span></span>
  
## <a name="data-access-considerations"></a><span data-ttu-id="dad5a-409">データ アクセスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="dad5a-409">Data access considerations</span></span>

<span data-ttu-id="dad5a-410">.NET Framework で実行されている ASP.NET Core アプリは Entity Framework (EF) を引き続き活用できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-410">ASP.NET Core apps running on .NET Framework can continue to leverage Entity Framework (EF).</span></span> <span data-ttu-id="dad5a-411">増分移行を実行する場合は、EF Core を使用するためにデータ アクセス移植する前に、アプリが EF 6 を使用するように設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dad5a-411">If performing an incremental migration, getting the app working with EF 6 before trying to port its data access to use EF Core may be worthwhile.</span></span> <span data-ttu-id="dad5a-412">これにより、別のブロックの移行作業が開始される前に、アプリの移行に関する問題を特定して対処することができます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-412">In this way, any problems with the app's migration can be identified and addressed before another block of migration effort is begun.</span></span>

<span data-ttu-id="dad5a-413">この作業は Autofac の `ApplicationModule` で実行されたため、eShop サンプルの移行で EF 6 を構成する場合、特別な作業は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-413">As it happens, configuring EF 6 in the eShop sample migration doesn't require any special work, since this work was performed in the Autofac `ApplicationModule`.</span></span> <span data-ttu-id="dad5a-414">唯一の問題は、現時点で、`CatalogDBContext` クラスが *web.config* から接続文字列の読み取りを試行することです。これに対処するには、接続の詳細を *appsettings.json* に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-414">The only problem is that currently the `CatalogDBContext` class tries to read its connection string from *web.config*. To address this, the connection details need to be added to *appsettings.json*.</span></span> <span data-ttu-id="dad5a-415">次に、接続文字列の作成時に、その文字列を `CatalogDBContext` に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-415">Then the connection string must be passed into `CatalogDBContext` when it's created.</span></span>

<span data-ttu-id="dad5a-416">*appsettings.json* を更新して、接続文字列を含めます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-416">Update the *appsettings.json* to include the connection string.</span></span> <span data-ttu-id="dad5a-417">ファイル全体は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-417">The full file is listed here:</span></span>

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=eShopPorted;Trusted_Connection=True;MultipleActiveResultSets=true"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "false",
  "UseCustomizationData": "true"
}
```

<span data-ttu-id="dad5a-418">`DbContext` の作成時に、接続文字列をコンストラクターに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-418">The connection string must be passed into the constructor when the `DbContext` is created.</span></span> <span data-ttu-id="dad5a-419">インスタンスは Autofac で作成されるため、`ApplicationModule` で変更を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-419">Since the instances are created by Autofac, the change needs to be made in `ApplicationModule`.</span></span> <span data-ttu-id="dad5a-420">モジュールを変更し、`connectionString` をコンストラクターに取り込んでフィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-420">Modify the module to take in a `connectionString` in its constructor and assign it to a field.</span></span> <span data-ttu-id="dad5a-421">次に、`CatalogDBContext` の登録を変更して、接続文字列をパラメーターとして追加します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-421">Then modify the registration for `CatalogDBContext` to add connection string as a parameter:</span></span>

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

<span data-ttu-id="dad5a-422">このパラメーターは、`CatalogDBContext` 自体の新しいコンストラクターのオーバーロードにも追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-422">The parameter must also be added to a new constructor overload in `CatalogDBContext` itself:</span></span>

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

<span data-ttu-id="dad5a-423">最後に、`ConfigureServices` が `Config` から接続文字列を読み取り、そのインスタンスを作成するときに `ApplicationModule` に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-423">Finally, `ConfigureServices` must read the connection string from `Config` and pass it into the `ApplicationModule` when it instantiates it:</span></span>

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

<span data-ttu-id="dad5a-424">このコードにより、アプリは以前と同じように実行され、`UseMockData` が `false` のときに SQL Server データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-424">With this code in place, the app runs as it did before, connecting to a SQL Server database when `UseMockData` is `false`.</span></span>

<span data-ttu-id="dad5a-425">この時点で、アプリを運用環境にデプロイして実行できます。アプリは ASP.NET Core に変換されますが、引き続き .NET Framework と EF 6 で実行されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-425">The app can be deployed and run in production at this point, converted to ASP.NET Core but still running on .NET Framework and EF 6.</span></span> <span data-ttu-id="dad5a-426">必要に応じて、.NET Core と Entity Framework Core で実行するためにアプリを移行できます。これにより、前の章で説明した追加の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-426">If desired, the app can be migrated to run on .NET Core and Entity Framework Core, which will bring additional advantages described in earlier chapters.</span></span> <span data-ttu-id="dad5a-427">Entity Framework については、[このドキュメントで EF Core と EF 6 を比較](/ef/efcore-and-ef6/)しています。また、個別のさまざまな機能がサポートされるライブラリを示す表も含まれています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-427">Specific to Entity Framework, [this documentation compares EF Core and EF 6](/ef/efcore-and-ef6/) and includes a grid showing which library supports each of dozens of individual features.</span></span>

### <a name="migrate-to-entity-framework-core"></a><span data-ttu-id="dad5a-428">Entity Framework Core に移行する</span><span class="sxs-lookup"><span data-stu-id="dad5a-428">Migrate to Entity Framework Core</span></span>

<span data-ttu-id="dad5a-429">EF Core への移行を決定したと仮定すると、特に元のアプリでコード ベース モデルのアプローチを使用していた場合は、手順が非常に簡単になります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-429">Assuming a decision is made to migrate to EF Core, the steps can be fairly straightforward, especially if the original app used a code-based model approach.</span></span> <span data-ttu-id="dad5a-430">[EF 6 から EF Core への移植の準備](/ef/efcore-and-ef6/porting/)の際、移植先のバージョンの EF Core で機能が使用可能かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-430">When [preparing to port from EF 6 to EF Core](/ef/efcore-and-ef6/porting/), review the availability of features in the destination version of EF Core you'll be using.</span></span> <span data-ttu-id="dad5a-431">[EDMX ベース モデルからの移植](/ef/efcore-and-ef6/porting/port-edmx)および[コード ベース モデルからの移植](/ef/efcore-and-ef6/porting/port-code)に関するドキュメントを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dad5a-431">Review the documentation on [porting from and EDMX-based model](/ef/efcore-and-ef6/porting/port-edmx) versus [porting from a code-based model](/ef/efcore-and-ef6/porting/port-code).</span></span>

<span data-ttu-id="dad5a-432">EF Core 2.2 にアップグレードする場合の基本的な手順として、適切な NuGet パッケージを追加し、名前空間を更新します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-432">To upgrade to EF Core 2.2, the basic steps involved are to add the appropriate NuGet package(s) and update namespaces.</span></span> <span data-ttu-id="dad5a-433">次に、接続文字列を `DbContext` 型に渡す方法と、依存関係の挿入用にそれらを関連付ける方法を調整します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-433">Then adjust how the connection string is passed to the `DbContext` type and how they're wired up for dependency injection.</span></span>

<span data-ttu-id="dad5a-434">EF Core は、パッケージ参照としてプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-434">EF Core is added as a package reference to the project:</span></span>

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

<span data-ttu-id="dad5a-435">EF 6 への参照は削除されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-435">The reference to EF 6 is removed:</span></span>

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

<span data-ttu-id="dad5a-436">コンパイラは、`CatalogDBContext` と `CatalogDBInitializer` でエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-436">The compiler will report errors in `CatalogDBContext` and `CatalogDBInitializer`.</span></span> <span data-ttu-id="dad5a-437">`CatalogDbContext` では、古い名前空間を削除して `Microsoft.EntityFrameworkCore` に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-437">`CatalogDbContext` needs to have the old namespaces removed and replaced with `Microsoft.EntityFrameworkCore`.</span></span> <span data-ttu-id="dad5a-438">そのコンストラクターは削除できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-438">Its constructors can be removed.</span></span> <span data-ttu-id="dad5a-439">`DbModelBuilder` は `ModelBuilder` に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-439">`DbModelBuilder` should be replaced with `ModelBuilder`.</span></span> <span data-ttu-id="dad5a-440">型を構成するためのヘルパー メソッドは、`IEntityTypeConfiguration<T>` を実装する別のクラスに移動されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-440">The helper methods for configuring types are moved to separate classes implementing `IEntityTypeConfiguration<T>`.</span></span> <span data-ttu-id="dad5a-441">これで、`CatalogDBContext` クラスの `OnModelCreating` メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-441">Then the `CatalogDBContext` class's `OnModelCreating` method simply becomes:</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

<span data-ttu-id="dad5a-442">関連するその他の変更点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-442">Other changes involved include:</span></span>

- <span data-ttu-id="dad5a-443">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` が `ValueGeneratedNever()` に置き換えられる</span><span class="sxs-lookup"><span data-stu-id="dad5a-443">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` replaced with `ValueGeneratedNever()`</span></span>
- <span data-ttu-id="dad5a-444">`HasRequired<T>` が `HasOne<T>` に置き換えられる</span><span class="sxs-lookup"><span data-stu-id="dad5a-444">`HasRequired<T>` replaced with `HasOne<T>`</span></span>
- <span data-ttu-id="dad5a-445">`Microsoft.EntityFrameworkCore.Relational` パッケージがインストールされる</span><span class="sxs-lookup"><span data-stu-id="dad5a-445">Installed `Microsoft.EntityFrameworkCore.Relational` package</span></span>
- <span data-ttu-id="dad5a-446">コンストラクターを `CatalogDBContext` に追加し、`DbContextOptions` を取得して基底コンストラクターに渡す</span><span class="sxs-lookup"><span data-stu-id="dad5a-446">Add a constructor to `CatalogDBContext` taking `DbContextOptions` and passing it to the base constructor</span></span>

<span data-ttu-id="dad5a-447">`CatalogType` の構成クラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-447">An example configuration class for `CatalogType` is shown here:</span></span>

```csharp
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Metadata.Builders;

namespace eShopPorted.Models.Config
{
    public class CatalogTypeConfig : IEntityTypeConfiguration<CatalogType>
    {
        public void Configure(EntityTypeBuilder<CatalogType> builder)
        {
            builder.ToTable(nameof(CatalogType));

            builder.HasKey(ci => ci.Id);

            builder.Property(ci => ci.Id)
               .IsRequired();

            builder.Property(cb => cb.Type)
                .IsRequired()
                .HasMaxLength(100);
        }
    }
}
```

<span data-ttu-id="dad5a-448">`CatalogDBInitializer` とその基底クラス `CreateDatabaseIfNotExists<T>` には、EF Core との互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-448">The `CatalogDBInitializer` and its base class, `CreateDatabaseIfNotExists<T>`, are incompatible with EF Core.</span></span> <span data-ttu-id="dad5a-449">このクラスの目的は、データベースを作成してシードすることです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-449">The purpose of this class is to create and seed the database.</span></span> <span data-ttu-id="dad5a-450">EF Core では、次のメソッドを使用して、[`DbContext` の関連データベースが作成および削除](/ef/core/managing-schemas/ensure-created)されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-450">Using EF Core will [create and drop the associated database for a `DbContext`](/ef/core/managing-schemas/ensure-created) using these methods:</span></span>

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

<span data-ttu-id="dad5a-451">EF Core におけるデータのシードは、手動のスクリプトを使用するか、型構成の一部として行うことができます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-451">Seeding data in EF Core can be done with manual scripts, or as part of the type configuration.</span></span> <span data-ttu-id="dad5a-452">他のエンティティ プロパティと共に、`builder.HasData()` を使用して、`IEntityTypeConfiguration` クラスでシード データを構成できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-452">Along with other entity properties, seed data can be configured in `IEntityTypeConfiguration` classes by using `builder.HasData()`.</span></span> <span data-ttu-id="dad5a-453">元のアプリは、*Setup* ディレクトリ内の CSV ファイルからシード データを読み込みました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-453">The original app loaded seed data from CSV files in the *Setup* directory.</span></span> <span data-ttu-id="dad5a-454">項目数が少ない場合は、代わりにこれらのデータ レコードをエンティティ構成の一部として追加できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-454">Given that there are only a handful of items, these data records can instead be added as part of the entity configuration.</span></span> <span data-ttu-id="dad5a-455">この方法は、変更頻度の低いテーブル内のデータの検索に適しています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-455">This approach works well for lookup data in tables that change infrequently.</span></span> <span data-ttu-id="dad5a-456">次のコードを `CatalogTypeConfig` の `Configure` メソッドに追加すると、データベースの作成時に、関連付けられている行が確実に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-456">Adding the following to `CatalogTypeConfig`'s `Configure` method ensures the associated rows are present when the database is created:</span></span>

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

<span data-ttu-id="dad5a-457">初期のアプリには `CatalogBrand` と `CatalogType` のデータを含む `PreconfiguredData` クラスが含まれているため、このメソッドを使用すると、`HasData` の呼び出しが次のように少なくなります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-457">The initial app includes a `PreconfiguredData` class, which includes data for `CatalogBrand` and `CatalogType`, so using this method the `HasData` call reduces to:</span></span>

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

<span data-ttu-id="dad5a-458">また、`CatalogItem` データを `PreconfiguredData` からプルすることもできます。関連付けられている画像がソース管理で保持されると仮定すると、これはアプリが機能するために必要な最後のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-458">The `CatalogItem` data can also be pulled from `PreconfiguredData`, and assuming the associated images are kept in source control, that is the last table needed for the app to function.</span></span> <span data-ttu-id="dad5a-459">`CatalogDBInitializer` クラスは、そのクラスへの参照と共に削除できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-459">The `CatalogDBInitializer` class can be removed, along with any references to it.</span></span> <span data-ttu-id="dad5a-460">`CatalogItemHiLoGenerator` クラスと `Infrastructure` ディレクトリ内の SQL ファイルも、それらへの参照 (`CatalogService`、`ApplicationModule` 内) と共に削除されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-460">The `CatalogItemHiLoGenerator` class and the SQL files in the `Infrastructure` directory are also removed, along with any references to them (in `CatalogService`, `ApplicationModule`).</span></span>

<span data-ttu-id="dad5a-461">`CatalogItem` の特殊なキー ジェネレーター クラスを削除することで、このコードは `CatalogItemConfig` から削除されました。</span><span class="sxs-lookup"><span data-stu-id="dad5a-461">With the elimination of the special key generator classes for `CatalogItem`, this code now is removed from `CatalogItemConfig`:</span></span>

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

<span data-ttu-id="dad5a-462">このような変更により、ASP.NET Core アプリはビルドされますが、まだ EF Core を使用できません。依存関係の挿入用の構成をアプリで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-462">With these modifications, the ASP.NET Core app builds, but it doesn't yet work with EF Core, which must still be configured for dependency injection.</span></span> <span data-ttu-id="dad5a-463">EF Core では、`ConfigureServices` でアプリを構成するのが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-463">With EF Core, the simplest way to configure it is in `ConfigureServices`:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    bool useMockData = Configuration.GetValue<bool>("UseMockData");
    if (!useMockData)
    {
        string connectionString = Configuration.GetConnectionString("DefaultConnection");

        services.AddDbContext<CatalogDBContext>(options =>
            options.UseSqlServer(connectionString)
        );
    }

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

<span data-ttu-id="dad5a-464">Autofac の `ApplicationModule` の最終バージョンでは、アプリがモック データを使用するように構成されているかどうかに応じて、1 つの型だけを構成します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-464">The final version of Autofac's `ApplicationModule` only configures one type, depending on whether the app is configured to use mock data:</span></span>

```csharp
public class ApplicationModule : Module
{
    private bool _useMockData;

    public ApplicationModule(bool useMockData)
    {
        _useMockData = useMockData;
    }

    protected override void Load(ContainerBuilder builder)
    {
        if (_useMockData)
        {
            builder.RegisterType<CatalogServiceMock>()
                .As<ICatalogService>()
                .SingleInstance();
        }
        else
        {
            builder.RegisterType<CatalogService>()
                .As<ICatalogService>()
                .InstancePerLifetimeScope();
        }
    }
}
```

<span data-ttu-id="dad5a-465">移植されたアプリは実行されますが、モック以外のデータを使用するように構成されている場合はデータが表示されません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-465">The ported app runs, but doesn't display any data if configured to use non-mock data.</span></span> <span data-ttu-id="dad5a-466">`HasData` によって追加されたシード データは、移行が適用されるときにのみ挿入されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-466">The seed data added through `HasData` is only inserted when migrations are applied.</span></span> <span data-ttu-id="dad5a-467">ソース アプリでは移行を使用していませんでしたが、使用していた場合でも、現状のような移行は行われません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-467">The source app didn't use migrations, and if it had, they wouldn't migrate as-is.</span></span> <span data-ttu-id="dad5a-468">新しい移行スクリプトで作業を開始するのが最適な方法です。</span><span class="sxs-lookup"><span data-stu-id="dad5a-468">The best approach is to start with a new migration script.</span></span> <span data-ttu-id="dad5a-469">そのためには、`Microsoft.EntityFrameworkCore.Design` のパッケージ参照を追加し、プロジェクト ルートでターミナル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-469">To do this, add a package reference for `Microsoft.EntityFrameworkCore.Design` and open a terminal window in the project root.</span></span> <span data-ttu-id="dad5a-470">次に、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-470">Then run:</span></span>

```dotnetcli
dotnet ef migrations add Initial
```

<span data-ttu-id="dad5a-471">既存の *eShopPorted* データベースが存在する場合は削除して、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-471">Drop the existing *eShopPorted* database if it exists, then run:</span></span>

```dotnetcli
dotnet ef database update
```

<span data-ttu-id="dad5a-472">これにより、データベースが作成され、シードされます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-472">This creates and seeds the database.</span></span> <span data-ttu-id="dad5a-473">これで実行の準備が整いました。ただし、対処が必要となる小さな更新がいくつか残されています。</span><span class="sxs-lookup"><span data-stu-id="dad5a-473">It's now ready to run, with a few small updates left to address.</span></span>

## <a name="fix-all-todo-tasks"></a><span data-ttu-id="dad5a-474">すべての TODO タスクを修正する</span><span class="sxs-lookup"><span data-stu-id="dad5a-474">Fix all TODO tasks</span></span>

<span data-ttu-id="dad5a-475">移植されたアプリをこの時点で実行すると、ページに画像が表示されないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-475">Running the ported app at this point reveals that no pictures are shown on the page.</span></span> <span data-ttu-id="dad5a-476">これは、`CatalogItem` の `PictureUri` プロパティが設定されていないためです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-476">This is because the `PictureUri` property of `CatalogItem` is never set.</span></span> <span data-ttu-id="dad5a-477">Visual Studio の **タスク一覧** を使用して作成した `TODO` 項目の一覧を確認すると、残っているのは "Reference pic from wwwroot" というメモの付いた、`CatalogController` 内の項目のみです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-477">Looking at the list of `TODO` items we created using Visual Studio's **Task List**, the only one that remains is in `CatalogController`, with a note to "Reference pic from wwwroot."</span></span> <span data-ttu-id="dad5a-478">対象のコードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-478">The code in question is:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="dad5a-479">最も簡単な修正方法は、サイトのパブリック ディレクトリである *wwwroot/Pics* 内の公開されている画像ファイルを参照することです。</span><span class="sxs-lookup"><span data-stu-id="dad5a-479">The simplest fix is to reference the public image files in the site's public *wwwroot/Pics* directory.</span></span> <span data-ttu-id="dad5a-480">このタスクを実行するには、メソッドを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-480">This task can be accomplished by replacing the method with the following code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

<span data-ttu-id="dad5a-481">この変更により、アプリを実行すると、画像が以前と同じように表示されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-481">With this change, running the app reveals the images work as before.</span></span>

## <a name="additional-mvc-customizations"></a><span data-ttu-id="dad5a-482">MVC の追加のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="dad5a-482">Additional MVC customizations</span></span>

<span data-ttu-id="dad5a-483">*eShopLegacyMVC* アプリは非常にシンプルなので、既定の MVC の動作に関する構成作業はあまり多くはありません。</span><span class="sxs-lookup"><span data-stu-id="dad5a-483">The *eShopLegacyMVC* app is fairly simple, so there isn't much to configure in terms of default MVC behavior.</span></span> <span data-ttu-id="dad5a-484">ただし、追加の MVC コンポーネント (CORS、フィルター、ルート制約など) を構成する必要がある場合、通常はこの情報を `Startup.ConfigureServices` で提供します。ここでは `UseMvc` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-484">However, if you do need to configure additional MVC components, such as CORS, filters, and route constraints, you generally provide this information in `Startup.ConfigureServices`, where `UseMvc` is called.</span></span> <span data-ttu-id="dad5a-485">たとえば、次のコード リストでは、[CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) を構成し、グローバル アクション フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-485">For example, the following code listing configures [CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) and sets up a global action filter:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddCors(options =>
    {
        options.AddPolicy(MyAllowSpecificOrigins,
            builder =>
                builder.WithOrigins("http://example.com", "http://www.contoso.com")
                    .AllowAnyHeader()
                    .AllowAnyMethod());
    });

    services.AddMvc(options =>
    {
      options.Filters.Add(new SampleGlobalActionFilter());
    }).SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
}
```

> [!Note]
> <span data-ttu-id="dad5a-486">CORS の構成を完了するには、`app.UseCors()` を `Configure` で呼び出す必要もあります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-486">To finish configuring CORS, you must also call `app.UseCors()` in `Configure`.</span></span>

<span data-ttu-id="dad5a-487">[カスタム モデル バインダー](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2)やフォーマッタの追加など、その他の高度なシナリオについては、ASP.NET Core の詳細なドキュメントを参照してください。これらは通常、個々のコントローラーやアクション単位で、または前述のコード リストに示されているのと同じオプションをグローバルに使用して適用できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-487">Other advanced scenarios, like adding [custom model binders](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2), formatters, and more are covered in the detailed ASP.NET Core docs. Generally these can be applied on an individual controller or action basis, or globally using the same options approach shown in the previous code listing.</span></span>

## <a name="other-dependencies"></a><span data-ttu-id="dad5a-488">その他の依存関係</span><span class="sxs-lookup"><span data-stu-id="dad5a-488">Other dependencies</span></span>

<span data-ttu-id="dad5a-489">WCF クライアントの型やトレース コードなど、レガシ構成モデルに依存していた .NET Framework 機能を使用する依存関係は、移植時に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-489">Dependencies that use .NET Framework features that had a dependency on the legacy configuration model, such as the WCF client type and tracing code, must be modified when ported.</span></span> <span data-ttu-id="dad5a-490">このような型によって構成情報を直接取り込むのではなく、コードで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-490">Rather than having these types pull in their configuration information directly, they should be configured in code.</span></span> <span data-ttu-id="dad5a-491">たとえば、ASP.NET アプリの *web.config* で `basicHttpBinding` を使用するように構成された WCF サービスへの接続は、次のコードを使用してプログラムで構成できます。</span><span class="sxs-lookup"><span data-stu-id="dad5a-491">For example, a connection to a WCF service that was configured in an ASP.NET app's *web.config* to use `basicHttpBinding` could instead be configured programmatically with the following code:</span></span>

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

<span data-ttu-id="dad5a-492">WCF クライアントおよびその他の .NET Framework 型の設定は、設定の構成ファイルに依存するのではなく、コードで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad5a-492">Rather than relying on config files for its settings, WCF clients and other .NET Framework types should have their settings specified in code.</span></span> <span data-ttu-id="dad5a-493">この方法で構成すると、これらの型は ASP.NET Core 2.2 アプリで引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="dad5a-493">Configured in this manner, these types can continue to work in ASP.NET Core 2.2 apps.</span></span>

## <a name="references"></a><span data-ttu-id="dad5a-494">References</span><span class="sxs-lookup"><span data-stu-id="dad5a-494">References</span></span>

- [<span data-ttu-id="dad5a-495">eShopModernizing GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="dad5a-495">eShopModernizing GitHub repository</span></span>](https://github.com/dotnet-architecture/eShopModernizing)
- [<span data-ttu-id="dad5a-496">.NET Upgrade Assistant ツール</span><span class="sxs-lookup"><span data-stu-id="dad5a-496">.NET Upgrade Assistant tool</span></span>](https://aka.ms/dotnet-upgrade-assistant)
- [<span data-ttu-id="dad5a-497">Your API and ViewModels Should Not Reference Domain Models (API と ViewModels でドメイン モデルを参照できない)</span><span class="sxs-lookup"><span data-stu-id="dad5a-497">Your API and ViewModels Should Not Reference Domain Models</span></span>](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [<span data-ttu-id="dad5a-498">開発者例外ページ ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="dad5a-498">Developer Exception Page Middleware</span></span>](/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [<span data-ttu-id="dad5a-499">EF Core の HasData の詳細情報</span><span class="sxs-lookup"><span data-stu-id="dad5a-499">Deep Dive into EF Core HasData</span></span>](/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
><span data-ttu-id="dad5a-500">[前へ](more-migration-scenarios.md)
>[次へ](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="dad5a-500">[Previous](more-migration-scenarios.md)
[Next](deployment-scenarios.md)</span></span>
