---
title: EShop から ASP.NET Core への移行の例
description: サンプルオンラインストアアプリを参照として使用して、既存の ASP.NET MVC アプリを ASP.NET Core に移行するチュートリアルです。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 498eb3b11c44381ff6d261b37caed15a2698b166
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605257"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a><span data-ttu-id="97d55-103">EShop から ASP.NET Core への移行の例</span><span class="sxs-lookup"><span data-stu-id="97d55-103">Example migration of eShop to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="97d55-104">この章では、.NET Framework アプリを .NET Core に移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="97d55-104">In this chapter, you'll see how to migrate a .NET Framework app to .NET Core.</span></span> <span data-ttu-id="97d55-105">この章では、ASP.NET 5.0 用に作成されたオンラインストアアプリのサンプルを調べます。</span><span class="sxs-lookup"><span data-stu-id="97d55-105">The chapter examines a sample online store app written for ASP.NET 5.0.</span></span> <span data-ttu-id="97d55-106">このアプリでは、このブックで前述した概念とツールの多くを使用します。</span><span class="sxs-lookup"><span data-stu-id="97d55-106">The app will use many of the concepts and tools described earlier in this book.</span></span> <span data-ttu-id="97d55-107">[ *EShopModernizing* GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing)に開始ポイントアプリがあります。</span><span class="sxs-lookup"><span data-stu-id="97d55-107">You'll find the starting point app in the [*eShopModernizing* GitHub repository](https://github.com/dotnet-architecture/eShopModernizing).</span></span> <span data-ttu-id="97d55-108">いくつかの異なる開始ポイントアプリがあります。</span><span class="sxs-lookup"><span data-stu-id="97d55-108">There are several different starting point apps.</span></span> <span data-ttu-id="97d55-109">この章では、 *eShopLegacyMVCSolution* を中心に説明します。</span><span class="sxs-lookup"><span data-stu-id="97d55-109">This chapter focuses on the *eShopLegacyMVCSolution*.</span></span>

<span data-ttu-id="97d55-110">プロジェクトの初期バージョンは、図4-1 に示されています。</span><span class="sxs-lookup"><span data-stu-id="97d55-110">The initial version of the project is shown in Figure 4-1.</span></span> <span data-ttu-id="97d55-111">これは、非常に標準的な ASP.NET MVC 5 アプリです。</span><span class="sxs-lookup"><span data-stu-id="97d55-111">It's a fairly standard ASP.NET MVC 5 app.</span></span>

![図4-1](media/Figure4-1.png)

<span data-ttu-id="97d55-113">**図 4-1**</span><span class="sxs-lookup"><span data-stu-id="97d55-113">**Figure 4-1.**</span></span> <span data-ttu-id="97d55-114">*EShopModernizing* MVC サンプルプロジェクトの構造。</span><span class="sxs-lookup"><span data-stu-id="97d55-114">The *eShopModernizing* MVC sample project structure.</span></span>

<span data-ttu-id="97d55-115">この章では、アップグレードの手順の多くを手動で実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="97d55-115">This chapter demonstrates how to perform many of the upgrade steps by hand.</span></span> <span data-ttu-id="97d55-116">または、 [.Net Upgrade Assistant ツール](https://aka.ms/dotnet-upgrade-assistant) を使用して、プロジェクトファイルの変換、ターゲットフレームワークの変更、NuGet パッケージの更新など、初期手順の多くを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="97d55-116">Alternatively, you can use the [.NET Upgrade Assistant tool](https://aka.ms/dotnet-upgrade-assistant) to perform many of the initial steps, like converting the project file, changing the target framework, and updating NuGet packages.</span></span>

## <a name="run-apiport-to-identify-problematic-apis"></a><span data-ttu-id="97d55-117">*Apiport* を実行して問題のある api を特定する</span><span class="sxs-lookup"><span data-stu-id="97d55-117">Run *ApiPort* to identify problematic APIs</span></span>

<span data-ttu-id="97d55-118">移行を準備するための最初の手順は、 *Apiport* ツールを実行することです。</span><span class="sxs-lookup"><span data-stu-id="97d55-118">The first step in preparing to migrate is to run the *ApiPort* tool.</span></span> <span data-ttu-id="97d55-119">このツールでは、アプリが呼び出す .NET Framework Api の数と、それに相当する .NET Standard または .NET Core の数が識別されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-119">The tool identifies how many .NET Framework APIs the app calls and how many of these have .NET Standard or .NET Core equivalents.</span></span> <span data-ttu-id="97d55-120">主に、サードパーティの依存関係ではなく、独自のアプリのロジックに重点を置いて、移植する必要がある依存関係に注意して `System.Web` ください。</span><span class="sxs-lookup"><span data-stu-id="97d55-120">Focus primarily on your own app's logic, not third-party dependencies, and pay attention to `System.Web` dependencies that will need to be ported.</span></span> <span data-ttu-id="97d55-121">ApiPort ツールは、 [依存関係の理解と更新](understand-update-dependencies.md)に関する最後の章で導入されました。</span><span class="sxs-lookup"><span data-stu-id="97d55-121">The ApiPort tool was introduced in the last chapter on [understanding and updating dependencies](understand-update-dependencies.md).</span></span>

<span data-ttu-id="97d55-122">[ *Apiport* ツールをインストールして構成](../../standard/analyzers/portability-analyzer.md)した後、図4-2 に示すように、Visual Studio 内から分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="97d55-122">After [installing and configuring the *ApiPort* tool](../../standard/analyzers/portability-analyzer.md), run the analysis from within Visual Studio, as shown in Figure 4-2.</span></span>

![図4-2](media/Figure4-2.png)

<span data-ttu-id="97d55-124">**図 4-2**</span><span class="sxs-lookup"><span data-stu-id="97d55-124">**Figure 4-2.**</span></span> <span data-ttu-id="97d55-125">Visual Studio でアセンブリの移植性を分析します。</span><span class="sxs-lookup"><span data-stu-id="97d55-125">Analyze assembly portability in Visual Studio.</span></span>

<span data-ttu-id="97d55-126">図4-3 に示すように、プロジェクトの *bin* フォルダーから web プロジェクトのアセンブリを選択します。</span><span class="sxs-lookup"><span data-stu-id="97d55-126">Choose the web project's assembly from the project's *bin* folder, as shown in Figure 4-3.</span></span>

![図4-3](media/Figure4-3.png)

<span data-ttu-id="97d55-128">**図 4-3**</span><span class="sxs-lookup"><span data-stu-id="97d55-128">**Figure 4-3.**</span></span> <span data-ttu-id="97d55-129">プロジェクトの web アセンブリを選択します。</span><span class="sxs-lookup"><span data-stu-id="97d55-129">Choose the project's web assembly.</span></span>

<span data-ttu-id="97d55-130">ソリューションに複数のプロジェクトが含まれている場合は、すべてを選択できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-130">If your solution includes several projects, you can choose all of them.</span></span> <span data-ttu-id="97d55-131">*EShop* サンプルには、1つの MVC プロジェクトだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97d55-131">The *eShop* sample includes just a single MVC project.</span></span>

<span data-ttu-id="97d55-132">レポートが生成されたら、ファイルを開き、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="97d55-132">Once the report is generated, open the file and review the results.</span></span> <span data-ttu-id="97d55-133">概要では、アプリに対する互換性のあるバージョンの .NET Framework 呼び出しの割合が大まかに示されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-133">The summary provides a high-level view of what percentage of .NET Framework calls your app is making have compatible versions.</span></span> <span data-ttu-id="97d55-134">図4-4 は、 *eShop* MVC プロジェクトの概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d55-134">Figure 4-4 shows the summary for the *eShop* MVC project.</span></span>

![図4-4](media/Figure4-4.png)

<span data-ttu-id="97d55-136">**図 4-4**</span><span class="sxs-lookup"><span data-stu-id="97d55-136">**Figure 4-4.**</span></span> <span data-ttu-id="97d55-137">ApiPort の概要。</span><span class="sxs-lookup"><span data-stu-id="97d55-137">ApiPort summary.</span></span>

<span data-ttu-id="97d55-138">このアプリでは、.NET Framework の呼び出しの約80% に互換性があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-138">For this app, about 80 percent of the .NET Framework calls are compatible.</span></span> <span data-ttu-id="97d55-139">呼び出しの20% は、移植プロセス中に対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-139">20 percent of the calls need to be addressed during the porting process.</span></span> <span data-ttu-id="97d55-140">詳細を表示すると、互換性のないすべての呼び出しがの一部であることがわかり `System.Web` ます。これは、予期しない非互換性です。</span><span class="sxs-lookup"><span data-stu-id="97d55-140">Viewing the details reveals that all of the incompatible calls are part of `System.Web`, which is an expected incompatibility.</span></span> <span data-ttu-id="97d55-141">呼び出しの依存関係は、 `System.Web` 後の手順でアプリのコントローラーと関連クラスが移行されるときに解決されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-141">The dependencies on `System.Web` calls will be addressed when the app's controllers and related classes are migrated in a later step.</span></span> <span data-ttu-id="97d55-142">図4-5 に、ツールによって検出された特定の型の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="97d55-142">Figure 4-5 lists some of the specific types found by the tool:</span></span>

![図4-5](media/Figure4-5.png)

<span data-ttu-id="97d55-144">**図 4-5.**</span><span class="sxs-lookup"><span data-stu-id="97d55-144">**Figure 4-5.**</span></span> <span data-ttu-id="97d55-145">*Apiport* に互換性のない型の詳細があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-145">*ApiPort* incompatible type details.</span></span>

<span data-ttu-id="97d55-146">互換性のない型のほとんどは、 `Controller` および ASP.NET Core に相当する関連属性を参照します。</span><span class="sxs-lookup"><span data-stu-id="97d55-146">Most of the incompatible types refer to `Controller` and various related attributes that have equivalents in ASP.NET Core.</span></span>

## <a name="update-project-files-and-nuget-reference-syntax"></a><span data-ttu-id="97d55-147">プロジェクトファイルと NuGet 参照構文の更新</span><span class="sxs-lookup"><span data-stu-id="97d55-147">Update project files and NuGet reference syntax</span></span>

<span data-ttu-id="97d55-148">次に、古い *.csproj* ファイル構造から、.net Core で導入されたより新しいより単純な構造に移行します。</span><span class="sxs-lookup"><span data-stu-id="97d55-148">Next, migrate from the older *.csproj* file structure to the newer, simpler structure introduced with .NET Core.</span></span> <span data-ttu-id="97d55-149">その場合は、NuGet 参照のために *packages.config* ファイルを使用するから、 `<PackageReference>` プロジェクトファイル内の要素を使用するように移行することもできます。</span><span class="sxs-lookup"><span data-stu-id="97d55-149">In doing so, you'll also migrate from using a *packages.config* file for NuGet references to using `<PackageReference>` elements in the project file.</span></span>

<span data-ttu-id="97d55-150">元のプロジェクトの *eShopLegacyMVC* ファイルの長さは418行です。</span><span class="sxs-lookup"><span data-stu-id="97d55-150">The original project's *eShopLegacyMVC.csproj* file is 418 lines long.</span></span> <span data-ttu-id="97d55-151">図4-6 に、プロジェクトファイルのサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="97d55-151">A sample of the project file is shown in Figure 4-6.</span></span> <span data-ttu-id="97d55-152">全体のサイズと複雑さを理解するために、イメージの右側にはファイル全体の小さなビューが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97d55-152">To offer a sense of its overall size and complexity, the right side of the image contains a miniature view of the entire file.</span></span>

![図4-6](media/Figure4-6.png)

<span data-ttu-id="97d55-154">**図 4-6**</span><span class="sxs-lookup"><span data-stu-id="97d55-154">**Figure 4-6.**</span></span> <span data-ttu-id="97d55-155">*EShopLegacyMVC* ファイル構造体。</span><span class="sxs-lookup"><span data-stu-id="97d55-155">The *eShopLegacyMVC.csproj* file structure.</span></span>

<span data-ttu-id="97d55-156">既存の ASP.NET プロジェクト用の新しいプロジェクトファイルを作成する一般的な方法は、 `dotnet new` または  >    >  Visual Studio で新しい **プロジェクト** を使用して新しい ASP.NET Core アプリを作成することです。</span><span class="sxs-lookup"><span data-stu-id="97d55-156">A common way to create a new project file for an existing ASP.NET project is to create a new ASP.NET Core app using `dotnet new` or **File** > **New** > **Project** in Visual Studio.</span></span> <span data-ttu-id="97d55-157">その後、古いプロジェクトから新しいプロジェクトにファイルをコピーして、移行を完了できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-157">Then files can be copied from the old project to the new one to complete the migration.</span></span>

<span data-ttu-id="97d55-158">C# プロジェクトファイルに加えて、NuGet の依存関係は、図4-7 に示すように、別の45行 *packages.config* ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-158">In addition to the C# project file, NuGet dependencies are stored in a separate 45-line *packages.config* file, as shown in Figure 4-7.</span></span>

![図4-7](media/Figure4-7.png)

<span data-ttu-id="97d55-160">**図 4-7**</span><span class="sxs-lookup"><span data-stu-id="97d55-160">**Figure 4-7.**</span></span> <span data-ttu-id="97d55-161">*packages.config* ファイル。</span><span class="sxs-lookup"><span data-stu-id="97d55-161">The *packages.config* file.</span></span>

<span data-ttu-id="97d55-162">新しい *.csproj* ファイル形式にアップグレードした後、Visual Studio を使用してクラスライブラリプロジェクトの *packages.config* を移行できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-162">After upgrading to the new *.csproj* file format, you can migrate *packages.config* in class library projects using Visual Studio.</span></span> <span data-ttu-id="97d55-163">ただし、この機能は ASP.NET プロジェクトでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="97d55-163">This functionality doesn't work with ASP.NET projects, however.</span></span> <span data-ttu-id="97d55-164">[ `<PackageReference>` Visual Studio で *packages.config* をに移行する方法の詳細については、こちらを参照して](/nuget/consume-packages/migrate-packages-config-to-package-reference)ください。</span><span class="sxs-lookup"><span data-stu-id="97d55-164">[Learn more about migrating *packages.config* to `<PackageReference>` in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span> <span data-ttu-id="97d55-165">多数のプロジェクトを移行する場合は、 [このコミュニティツールが役に立ち](https://github.com/MarkKharitonov/NuGetPCToPRMigrator)ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-165">If you have a large number of projects to migrate, [this community tool may help](https://github.com/MarkKharitonov/NuGetPCToPRMigrator).</span></span>

## <a name="create-new-aspnet-core-project"></a><span data-ttu-id="97d55-166">新しい ASP.NET Core プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="97d55-166">Create new ASP.NET Core project</span></span>

<span data-ttu-id="97d55-167">新しい ASP.NET Core プロジェクトを既存のアプリのソリューションに追加して、ファイルを簡単に移動できるようにします。ほとんどの作業は Visual Studio の **ソリューションエクスプローラー** 内から実行できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-167">Add a new ASP.NET Core project to the existing app's solution to make moving files easier, as most of the work can be done from within Visual Studio's **Solution Explorer**.</span></span> <span data-ttu-id="97d55-168">Visual Studio で、アプリのソリューションを右クリックし、[ **新しいプロジェクトの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="97d55-168">In Visual Studio, right-click on your app's solution and choose **Add New Project**.</span></span> <span data-ttu-id="97d55-169">[ **ASP.NET Core web アプリケーション**] を選択し、図4-8 に示すように、新しいプロジェクトに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="97d55-169">Choose **ASP.NET Core web application**, and give the new project a name as shown in Figure 4-8.</span></span>

![図4-8](media/Figure4-8.png)

<span data-ttu-id="97d55-171">**図 4-8.**</span><span class="sxs-lookup"><span data-stu-id="97d55-171">**Figure 4-8.**</span></span> <span data-ttu-id="97d55-172">新しい ASP.NET Core web アプリケーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-172">Add new ASP.NET Core web application.</span></span>

<span data-ttu-id="97d55-173">次のダイアログボックスで、使用するテンプレートを選択するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-173">The next dialog will ask you to choose which template to use.</span></span> <span data-ttu-id="97d55-174">**[空]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="97d55-174">Select the **Empty** template.</span></span> <span data-ttu-id="97d55-175">また、ドロップダウンリストを **.Net Core** から **.NET Framework** に変更します。</span><span class="sxs-lookup"><span data-stu-id="97d55-175">Be sure to also change the dropdown from **.NET Core** to **.NET Framework**.</span></span> <span data-ttu-id="97d55-176">図4-9 に示すように、 **ASP.NET Core 2.2** を選択します。</span><span class="sxs-lookup"><span data-stu-id="97d55-176">Select **ASP.NET Core 2.2**, as shown in Figure 4-9.</span></span>

![図4-9](media/Figure4-9.png)

<span data-ttu-id="97d55-178">**図 4-9**</span><span class="sxs-lookup"><span data-stu-id="97d55-178">**Figure 4-9.**</span></span> <span data-ttu-id="97d55-179">ASP.NET Core 2.2 で .NET Framework をターゲットとする空のプロジェクトテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="97d55-179">Choose an Empty project template targeting .NET Framework with ASP.NET Core 2.2.</span></span>

### <a name="migrating-nuget-packages"></a><span data-ttu-id="97d55-180">NuGet パッケージの移行</span><span class="sxs-lookup"><span data-stu-id="97d55-180">Migrating NuGet Packages</span></span>

<span data-ttu-id="97d55-181">*packages.config* をに移行するための組み込みの移行ツールは `<PackageReference>` ASP.NET プロジェクトでは機能しないため、代わりにコミュニティツールを使用するか、手動で移行することができます。</span><span class="sxs-lookup"><span data-stu-id="97d55-181">Since the built-in migration tool for migrating *packages.config* to `<PackageReference>` doesn't work on ASP.NET projects, you can use a community tool instead, or migrate by hand.</span></span> <span data-ttu-id="97d55-182">[私が使用したコミュニティツール](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf)では、XSL ファイルを使用して、ある形式から別の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="97d55-182">A [community tool I've used](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) uses an XSL file to transform from one format to the other.</span></span> <span data-ttu-id="97d55-183">これを使用するには、まず、新しく作成した ASP.NET Core プロジェクトフォルダーに *packages.config* ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="97d55-183">To use it, first copy the *packages.config* file to the newly created ASP.NET Core project folder.</span></span> <span data-ttu-id="97d55-184">ファイルのバックアップを作成します。このスクリプトでは、スクリプトの実行場所にあるすべてのフォルダーから *packages.config* ファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-184">Make a backup of your files, as this script removes the *packages.config* file from all folders under where you run the script.</span></span> <span data-ttu-id="97d55-185">次に、プロジェクトフォルダー (または、必要に応じてソリューション全体) から次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="97d55-185">Then run these commands from the project folder (or for the entire solution if you prefer):</span></span>

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

<span data-ttu-id="97d55-186">最初の2つのコマンドは、ファイルがローカルに存在するようにファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="97d55-186">The first two commands download files so that they exist locally.</span></span> <span data-ttu-id="97d55-187">最後の行では、スクリプトが実行されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-187">The last line runs the script.</span></span> <span data-ttu-id="97d55-188">実行後、新しいプロジェクトをビルドしてみてください。</span><span class="sxs-lookup"><span data-stu-id="97d55-188">After running it, try to build the new project.</span></span> <span data-ttu-id="97d55-189">多くの場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="97d55-189">You'll most likely get some errors.</span></span> <span data-ttu-id="97d55-190">これを解決するには、一部の参照 (およびパッケージのほとんど) を削除し、 `Microsoft.AspNet` 一部の `System` 属性を削除しなければならないことがあり `xmlns` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-190">To resolve them, you'll want to eliminate some references (like most of the `Microsoft.AspNet` and `System` packages), and you may need to remove some `xmlns` attributes.</span></span>

<span data-ttu-id="97d55-191">ほとんどの ASP.NET MVC アプリでは、ブートストラップや jQuery などの多くのクライアント側の依存関係が NuGet パッケージを使用してデプロイされていました。</span><span class="sxs-lookup"><span data-stu-id="97d55-191">In most ASP.NET MVC apps, many client-side dependencies like Bootstrap and jQuery were deployed using NuGet packages.</span></span> <span data-ttu-id="97d55-192">ASP.NET Core では、NuGet パッケージはサーバー側の機能にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-192">In ASP.NET Core, NuGet packages are only used for server-side functionality.</span></span> <span data-ttu-id="97d55-193">クライアントファイルは、他の方法で管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-193">Client files should be managed through other means.</span></span> <span data-ttu-id="97d55-194">追加された要素の一覧を確認し、 `<PackageReference>` 次のようなクライアントライブラリのものをすべて削除してメモします。</span><span class="sxs-lookup"><span data-stu-id="97d55-194">Review the list of `<PackageReference>` elements added and remove and make note of any that are for client libraries, including:</span></span>

- <span data-ttu-id="97d55-195">ブートストラップ</span><span class="sxs-lookup"><span data-stu-id="97d55-195">Bootstrap</span></span>
- <span data-ttu-id="97d55-196">jQuery</span><span class="sxs-lookup"><span data-stu-id="97d55-196">jQuery</span></span>
- <span data-ttu-id="97d55-197">jQuery。検証</span><span class="sxs-lookup"><span data-stu-id="97d55-197">jQuery.Validation</span></span>
- <span data-ttu-id="97d55-198">Modernizr</span><span class="sxs-lookup"><span data-stu-id="97d55-198">Modernizr</span></span>
- <span data-ttu-id="97d55-199">popper.js</span><span class="sxs-lookup"><span data-stu-id="97d55-199">popper.js</span></span>
- <span data-ttu-id="97d55-200">対応</span><span class="sxs-lookup"><span data-stu-id="97d55-200">Respond</span></span>

<span data-ttu-id="97d55-201">これらのパッケージの NuGet によってインストールされた静的クライアントファイルは、新しいプロジェクトの *wwwroot* フォルダーにコピーされ、そこからホストされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-201">The static client files installed by NuGet for these packages will be copied over to the new project's *wwwroot* folder and hosted from there.</span></span> <span data-ttu-id="97d55-202">これらのファイルがアプリで依然として必要かどうか、およびそれらのファイルを引き続きホストするか、代わりに content delivery network (CDN) を使用するかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="97d55-202">It's worth considering whether these files are still needed by the app, and whether it makes sense to continue hosting them or to use a content delivery network (CDN) instead.</span></span> <span data-ttu-id="97d55-203">これらのライブラリのバージョンは、 [Libman](/aspnet/core/client-side/libman/) や [npm](https://www.npmjs.com/)などのツールを使用してビルド時に管理できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-203">These library versions can be managed at build time using tools like [LibMan](/aspnet/core/client-side/libman/) or [npm](https://www.npmjs.com/).</span></span> <span data-ttu-id="97d55-204">図4-10 に、変換ツールを使用してパッケージ参照を移行し、不要なパッケージを削除した後の完全な *eShopPorted* ファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="97d55-204">Figure 4-10 shows the full *eShopPorted.csproj* file after migrating package references using the conversion tool shown and removing unnecessary packages.</span></span>

![図4-10](media/Figure4-10.png)

<span data-ttu-id="97d55-206">**図 4-10**</span><span class="sxs-lookup"><span data-stu-id="97d55-206">**Figure 4-10.**</span></span> <span data-ttu-id="97d55-207">*EShopPorted* ファイル内のパッケージ参照。</span><span class="sxs-lookup"><span data-stu-id="97d55-207">Package references in the *eShopPorted.csproj* file.</span></span>

<span data-ttu-id="97d55-208">要素に属性を設定することにより、パッケージ参照をさらに圧縮でき `<Version>1.0.0.0</Version>` `Version=1.0.0.0` `<PackageReference>` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-208">The package references can be further compacted by making the `<Version>1.0.0.0</Version>` element a `Version=1.0.0.0` attribute on `<PackageReference>`.</span></span>

### <a name="migrate-static-files"></a><span data-ttu-id="97d55-209">静的ファイルを移行する</span><span class="sxs-lookup"><span data-stu-id="97d55-209">Migrate static files</span></span>

<span data-ttu-id="97d55-210">アプリケーションが使用するすべての静的ファイル (サードパーティのスクリプトやフレームワークを含むが、カスタムイメージやスタイルシートも含む) は、古いプロジェクトから新しいプロジェクトにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-210">Any static files the app uses, including third-party scripts and frameworks but also custom images and stylesheets, must be copied from the old project to the new one.</span></span> <span data-ttu-id="97d55-211">ASP.NET MVC アプリでは、通常、ファイルはプロジェクトフォルダー内の場所に基づいてアクセスされていました。</span><span class="sxs-lookup"><span data-stu-id="97d55-211">In ASP.NET MVC apps, files were typically accessed based on their location within the project folder.</span></span> <span data-ttu-id="97d55-212">ASP.NET Core アプリでは、これらの静的ファイルは *wwwroot* フォルダー内の場所に基づいてアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-212">In ASP.NET Core apps, these static files will be accessed based on their location within the *wwwroot* folder.</span></span> <span data-ttu-id="97d55-213">*EShop* プロジェクトの場合、次のフォルダーに静的ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="97d55-213">For the *eShop* project, there are static files in the following folders:</span></span>

* <span data-ttu-id="97d55-214">*コンテンツ*</span><span class="sxs-lookup"><span data-stu-id="97d55-214">*Content*</span></span>
* <span data-ttu-id="97d55-215">*フォント*</span><span class="sxs-lookup"><span data-stu-id="97d55-215">*fonts*</span></span>
* <span data-ttu-id="97d55-216">*イメージ*</span><span class="sxs-lookup"><span data-stu-id="97d55-216">*Images*</span></span>
* <span data-ttu-id="97d55-217">*写真*</span><span class="sxs-lookup"><span data-stu-id="97d55-217">*Pics*</span></span>
* <span data-ttu-id="97d55-218">*スクリプト*</span><span class="sxs-lookup"><span data-stu-id="97d55-218">*Scripts*</span></span>

<span data-ttu-id="97d55-219">前の手順で使用した **空** のプロジェクトテンプレートには、既定ではこのフォルダーが含まれていません。また、このフォルダーが動作するために必要なミドルウェアもありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-219">The **Empty** project template used in the previous step doesn't include this folder by default, or the middleware needed for it to work.</span></span> <span data-ttu-id="97d55-220">追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-220">You'll need to add them.</span></span>

<span data-ttu-id="97d55-221">*Wwwroot* フォルダーをプロジェクトのルートに追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-221">Add a *wwwroot* folder to the root of the project.</span></span>

<span data-ttu-id="97d55-222">バージョン2.2.0 の `Microsoft.AspNetCore.StaticFiles` NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-222">Add version 2.2.0 of the `Microsoft.AspNetCore.StaticFiles` NuGet package.</span></span>

<span data-ttu-id="97d55-223">*Startup.cs* で、メソッドにの呼び出しを追加し `app.UseStaticFiles()` `Configure` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-223">In *Startup.cs*, add a call to `app.UseStaticFiles()` in the `Configure` method:</span></span>

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

<span data-ttu-id="97d55-224">ASP.NET MVC アプリから新しいプロジェクトの *wwwroot* フォルダーに *コンテンツ* フォルダーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="97d55-224">Copy the *Content* folder from the ASP.NET MVC app to the new project's *wwwroot* folder.</span></span>

<span data-ttu-id="97d55-225">アプリを実行し、その */Content/base.css* フォルダーに移動して、必要なパスから静的ファイルが正しく提供されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="97d55-225">Run the app and navigate to its */Content/base.css* folder to verify that the static file is served correctly from its expected path.</span></span> <span data-ttu-id="97d55-226">静的ファイルが格納されている残りのフォルダーを新しいプロジェクトにコピーし続けます。</span><span class="sxs-lookup"><span data-stu-id="97d55-226">Continue copying the rest of the folders containing static files to the new project.</span></span> <span data-ttu-id="97d55-227">また、プロジェクトのルートから *wwwroot* フォルダーに *favicon* ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="97d55-227">You'll also want to copy the *favicon.ico* file from the project's root to the *wwwroot* folder.</span></span> <span data-ttu-id="97d55-228">図4-11 は、これらのファイルとそのフォルダーがすべてコピーされた後の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d55-228">Figure 4-11 shows the results after these files and their folders have all been copied.</span></span>

![図4-11](media/Figure4-11.png)

<span data-ttu-id="97d55-230">**図 4-11**</span><span class="sxs-lookup"><span data-stu-id="97d55-230">**Figure 4-11.**</span></span> <span data-ttu-id="97d55-231">静的フォルダーが *wwwroot* フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-231">Static folders copied over to *wwwroot* folder.</span></span>

### <a name="migrate-c-files"></a><span data-ttu-id="97d55-232">C# ファイルを移行する</span><span class="sxs-lookup"><span data-stu-id="97d55-232">Migrate C# files</span></span>

<span data-ttu-id="97d55-233">次に、アプリで使用される C# ファイルをコピーします。これには、標準の MVC フォルダーや、 *コントローラー*、 *モデル*、 *ビュー* モデル、 *サービス* などのコンテンツが含まれます。</span><span class="sxs-lookup"><span data-stu-id="97d55-233">Next, copy over the C# files used by the app, including standard MVC folders and their contents like *Controllers*, *Models*, *ViewModel*, and *Services*.</span></span> <span data-ttu-id="97d55-234">多くの場合、これらのファイルにはいくつかの変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="97d55-234">There will most likely be some changes needed in these files.</span></span> <span data-ttu-id="97d55-235">一度に1つのフォルダー (またはサブフォルダー) をコピーしてコンパイルし、どのようなエラーに対処する必要があるかを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97d55-235">It's best to copy one folder (or subfolder) at a time and compile to see what errors need to be addressed as you go.</span></span>

<span data-ttu-id="97d55-236">*EShop* サンプルの場合、移行対象として最初に選択したフォルダーは、C# エンティティと Entity Framework クラスを含む [*モデル*] フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="97d55-236">For the *eShop* sample, the first folder I choose to migrate is the *Models* folder, which includes C# entities and Entity Framework classes.</span></span> <span data-ttu-id="97d55-237">このフォルダーのクラスは、ほとんどの場合に使用されるので、これらのクラスがコピーされるまでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="97d55-237">This folder's classes are used by most of the others, so they won't work until these classes have been copied.</span></span> <span data-ttu-id="97d55-238">フォルダーとビルドをコピーした後、コンパイラは、見つからない名前空間 `System.Web.Hosting` 、への関連アクセス `HostingEnvironment` 、およびへの参照に関連するエラーを検出しました `ConfigurationManager.AppSettings` 。</span><span class="sxs-lookup"><span data-stu-id="97d55-238">After copying the folder and building, the compiler revealed errors related to missing namespace `System.Web.Hosting`, related access to `HostingEnvironment`, and a reference to `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="97d55-239">これらの問題の解決策は、必要なパスデータを渡すことです。ここでは、改行をコメントアウトし、 `TODO:` 各行にコメントを追加して追跡します。</span><span class="sxs-lookup"><span data-stu-id="97d55-239">The solution to these issues will be to pass in the necessary path data; for now the breaking lines are commented out and a `TODO:` comment is added to each one to track it.</span></span> <span data-ttu-id="97d55-240">5行を変更すると、 **タスク一覧** に5つの項目とプロジェクトビルドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-240">After changing five lines, the **Task List** shows five items and the project builds.</span></span>

<span data-ttu-id="97d55-241">次に、1つのクラスを持つ *ビューモデル* フォルダーがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-241">Next, the *ViewModel* folder, with its one class, is copied over.</span></span> <span data-ttu-id="97d55-242">簡単なものであり、すぐにビルドできます。</span><span class="sxs-lookup"><span data-stu-id="97d55-242">It's an easy one, and builds immediately.</span></span>

<span data-ttu-id="97d55-243">*Services* フォルダーがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-243">The *Services* folder is copied over.</span></span> <span data-ttu-id="97d55-244">このフォルダーのクラスは、[ *モデル* ] フォルダーの Entity Framework クラスに依存しているため、そのフォルダーの後にコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-244">This folder's classes depend on Entity Framework classes from the *Models* folder, which is why it needed to be copied after that folder.</span></span> <span data-ttu-id="97d55-245">幸いにも、エラーが発生することなくビルドされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-245">Fortunately, it too builds without errors.</span></span>

<span data-ttu-id="97d55-246">これにより、 *Controllers* フォルダーとその2つのクラスが残り `Controller` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-246">That leaves the *Controllers* folder and its two `Controller` classes.</span></span> <span data-ttu-id="97d55-247">フォルダーを新しいプロジェクトにコピーしてビルドすると、7つのビルドエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="97d55-247">After copying the folder to the new project and building, there are seven build errors.</span></span> <span data-ttu-id="97d55-248">これらの4つはアクセスに関連 `ViewBag` しており、次のようなエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-248">Four of them are related to `ViewBag` access and report an error of:</span></span>

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

<span data-ttu-id="97d55-249">このエラーを解決するには、NuGet パッケージ参照を C# に追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-249">To resolve this error add a NuGet package reference to C#:</span></span>

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

<span data-ttu-id="97d55-250">残りの3つのエラーは、参照されていないアセンブリで定義されている型を指定します。</span><span class="sxs-lookup"><span data-stu-id="97d55-250">The remaining three errors specify types that are defined in an assembly that isn't referenced.</span></span> <span data-ttu-id="97d55-251">具体的には、次の種類があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-251">Specifically these types:</span></span>

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

<span data-ttu-id="97d55-252">各エラーを1つずつ見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="97d55-252">Let's look at each error one by one.</span></span> <span data-ttu-id="97d55-253">最初のエラーは、のプロパティを参照しようとしたときに、存在しなくなった場合に発生し `Server` `Controller` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-253">The first error occurs while trying to reference the `Server` property of `Controller`, which no longer exists.</span></span> <span data-ttu-id="97d55-254">操作の目的は、アプリ内のイメージファイルへのパスを取得することです。</span><span class="sxs-lookup"><span data-stu-id="97d55-254">The goal of the operation is to get the path to an image file in the app:</span></span>

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

<span data-ttu-id="97d55-255">この問題には、2つの解決策が考えられます。</span><span class="sxs-lookup"><span data-stu-id="97d55-255">There are two possible solutions to this problem.</span></span> <span data-ttu-id="97d55-256">1つ目は、機能をそのまま維持することです。</span><span class="sxs-lookup"><span data-stu-id="97d55-256">The first is to keep the functionality as it is.</span></span> <span data-ttu-id="97d55-257">この場合、を使用するのではなく、 `Server.MapPath` *wwwroot* 内のイメージファイルの場所を参照する固定パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-257">In this case, rather than using `Server.MapPath`, a fixed path referencing the image files' location in *wwwroot* should be used.</span></span> <span data-ttu-id="97d55-258">または、このアクションメソッドの唯一の目的は静的イメージファイルを返すことであるため、ビューファイル内のこのアクションへの参照を更新して静的ファイルを直接参照することができます。これにより、実行時のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="97d55-258">Alternately, since the only purpose of this action method is to return a static image file, the references to this action in view files can be updated to reference the static files directly, which improves runtime performance.</span></span> <span data-ttu-id="97d55-259">この操作の一部として処理は行われないため、ファイルを直接処理するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-259">Since no processing is being done as part of this action, there's no reason not to just serve the files directly.</span></span> <span data-ttu-id="97d55-260">不都合でこのアクションへのすべての参照を更新しない場合は、静的ファイルの場所へのリダイレクトを生成するためにアクションを書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="97d55-260">If it's not tenable to update all references to this action, the action could be rewritten to produce a redirect to the static file's location.</span></span>

<span data-ttu-id="97d55-261">次の2つのエラーは、両方とも同じコード行の同じプライベートメソッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="97d55-261">The next two errors both occur in the same private method in the same line of code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="97d55-262">`this.Url`との両方で `this.Request` コンパイラエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="97d55-262">Both `this.Url` and `this.Request` cause compiler errors.</span></span> <span data-ttu-id="97d55-263">このコードの使用方法については、 `PicController` イメージファイルをレンダリングするアクションへのリンクを作成することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="97d55-263">Looking at how this code is used, its purpose is to build a link to the `PicController` action that renders image files.</span></span> <span data-ttu-id="97d55-264">先ほど見たものと同じものが、 *wwwroot* にある静的ファイルへの直接リンクに置き換えられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-264">The same one we just discovered could probably be replaced with direct links to the static files located in *wwwroot*.</span></span> <span data-ttu-id="97d55-265">ここでは、このコードをコメントアウトし、別の `TODO:` 方法を参照するコメントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-265">For now, it's worth commenting out this code and adding a `TODO:` comment to reference the pics another way.</span></span>

<span data-ttu-id="97d55-266">`Controller`このコードが記述されているクラスで使用される基底クラスは、を参照していることに注意 `CatalogController` `System.Web.Mvc.Controller` してください。</span><span class="sxs-lookup"><span data-stu-id="97d55-266">It's worth noting that the base `Controller` class, used by the `CatalogController` class in which this code appears, is still referring to `System.Web.Mvc.Controller`.</span></span> <span data-ttu-id="97d55-267">ASP.NET Core を使用するように更新した後は、修正が必要なエラーが発生することは間違いありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-267">There will undoubtedly be more errors to fix once we update this to use ASP.NET Core.</span></span> <span data-ttu-id="97d55-268">最初に、 `using System.Web.Mvc;` のステートメントのリストから行を削除 `using` `CatalogController` します。</span><span class="sxs-lookup"><span data-stu-id="97d55-268">First, remove the `using System.Web.Mvc;` line from the list of `using` statements in `CatalogController`.</span></span> <span data-ttu-id="97d55-269">次に、NuGet パッケージを追加し `Microsoft.AspNetCore.Mvc` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-269">Next, add the NuGet package `Microsoft.AspNetCore.Mvc`.</span></span> <span data-ttu-id="97d55-270">最後に、ステートメントを追加 `using Microsoft.AspNetCore.Mvc;` し、アプリをもう一度ビルドします。</span><span class="sxs-lookup"><span data-stu-id="97d55-270">Finally, add a `using Microsoft.AspNetCore.Mvc;` statement, and build the app again.</span></span>

<span data-ttu-id="97d55-271">今回は、16個のエラーがあります。</span><span class="sxs-lookup"><span data-stu-id="97d55-271">This time, there are 16 errors:</span></span>

- <span data-ttu-id="97d55-272">`Include` が有効な名前付き属性引数ではありません (2)</span><span class="sxs-lookup"><span data-stu-id="97d55-272">`Include` is not a valid named attribute argument (2)</span></span>
- <span data-ttu-id="97d55-273">`HttpStatusCodeResult` 見つかりませんでした (3)</span><span class="sxs-lookup"><span data-stu-id="97d55-273">`HttpStatusCodeResult` not found (3)</span></span>
- <span data-ttu-id="97d55-274">`HttpNotFound` 存在しません (3)</span><span class="sxs-lookup"><span data-stu-id="97d55-274">`HttpNotFound` does not exist (3)</span></span>
- <span data-ttu-id="97d55-275">`SelectList` 見つかりません (8)</span><span class="sxs-lookup"><span data-stu-id="97d55-275">`SelectList` not found (8)</span></span>

<span data-ttu-id="97d55-276">さらに、これらのエラーを1つずつ確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="97d55-276">Once more, let's review these errors one by one.</span></span> <span data-ttu-id="97d55-277">まず、を `SelectList` 追加して修正でき `using Microsoft.AspNetCore.Mvc.Rendering;` ます。これにより、エラーの半分が解消されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-277">First, `SelectList` can be fixed by adding `using Microsoft.AspNetCore.Mvc.Rendering;`, which eliminates half of the errors.</span></span>

<span data-ttu-id="97d55-278">へのすべて `return HttpNotFound();` の参照は、に置き換える必要があり `return NotFound();` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-278">All references to `return HttpNotFound();` should be replaced with `return NotFound();`.</span></span>

<span data-ttu-id="97d55-279">へのすべて `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` の参照は、に置き換える必要があり `return BadRequest();` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-279">All references to `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` should be replaced with `return BadRequest();`.</span></span>

<span data-ttu-id="97d55-280">これにより、次 `Include` `[Bind]` のようないくつかのアクションメソッドの属性でが使用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-280">That just leaves the use of `Include` with a `[Bind]` attribute on a couple of action methods that look like this:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="97d55-281">上記のコードでは、モデルバインドを文字列に示されているプロパティに限定して `Include` います。</span><span class="sxs-lookup"><span data-stu-id="97d55-281">The preceding code restricts model binding to the properties listed in the `Include` string.</span></span> <span data-ttu-id="97d55-282">ASP.NET Core MVC では、 `[Bind]` 属性はまだ存在しますが、引数は必要ありません `Include =` 。</span><span class="sxs-lookup"><span data-stu-id="97d55-282">In ASP.NET Core MVC, the `[Bind]` attribute still exists, but no longer needs the `Include =` argument.</span></span> <span data-ttu-id="97d55-283">属性にプロパティの一覧を直接渡し `[Bind]` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-283">Pass the list of properties directly to the `[Bind]` attribute:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="97d55-284">これらの変更により、プロジェクトはさらにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-284">With these changes, the project compiles once more.</span></span> <span data-ttu-id="97d55-285">通常は、ドメインモデルまたはデータモデルの型にモデルバインドを直接使用するのではなく、コントローラー入力に個別のモデルの種類を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97d55-285">It's generally a better practice to use separate model types for controller inputs, rather than using model binding directly to your domain model or data model types.</span></span>

## <a name="migrate-views"></a><span data-ttu-id="97d55-286">ビューの移行</span><span class="sxs-lookup"><span data-stu-id="97d55-286">Migrate views</span></span>

<span data-ttu-id="97d55-287">ビューに関連する最大の ASP.NET Core MVC 機能は、 [Razor Pages](/aspnet/core/razor-pages/) と [タグヘルパー](/aspnet/core/mvc/views/tag-helpers/built-in/)の2つです。</span><span class="sxs-lookup"><span data-stu-id="97d55-287">The two biggest ASP.NET Core MVC features related to views are [Razor Pages](/aspnet/core/razor-pages/) and [Tag Helpers](/aspnet/core/mvc/views/tag-helpers/built-in/).</span></span> <span data-ttu-id="97d55-288">最初の移行では、どちらの機能も使用しません。</span><span class="sxs-lookup"><span data-stu-id="97d55-288">For the initial migration, we won't use either feature.</span></span> <span data-ttu-id="97d55-289">ただし、移行後にアプリのサポートを継続する場合は、機能を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-289">You should, however, keep the features in mind if you continue supporting the app once it's been migrated.</span></span> <span data-ttu-id="97d55-290">次の手順では、 *Views* フォルダーを元のプロジェクトから新しいプロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="97d55-290">The next step is to copy the *Views* folder from the original project into the new one.</span></span> <span data-ttu-id="97d55-291">ビルド後、次の9つのエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="97d55-291">After building, there are nine errors:</span></span>

- <span data-ttu-id="97d55-292">HttpContext が存在しません (2)</span><span class="sxs-lookup"><span data-stu-id="97d55-292">HttpContext does not exist (2)</span></span>
- <span data-ttu-id="97d55-293">スクリプトが存在しません (5)</span><span class="sxs-lookup"><span data-stu-id="97d55-293">Scripts does not exist (5)</span></span>
- <span data-ttu-id="97d55-294">スタイルが存在しません (1)</span><span class="sxs-lookup"><span data-stu-id="97d55-294">Styles does not exist (1)</span></span>
- <span data-ttu-id="97d55-295">HtmlString が見つかりませんでした (1)</span><span class="sxs-lookup"><span data-stu-id="97d55-295">HtmlString could not be found(1)</span></span>

<span data-ttu-id="97d55-296">これらのエラーを調査することで、そのほとんどがメイン _Layout に含まれていることがわかります。これには、スクリプトとスタイルタグのレンダリングに関連するものと、アプリをホストしているサーバーが最後に再起動された日時が表示され *ます。*</span><span class="sxs-lookup"><span data-stu-id="97d55-296">Investigating these errors finds that most of them are in the main *_Layout.cshtml*, with several related to rendering script and style tags, or displaying when the server hosting the app was last restarted.</span></span> <span data-ttu-id="97d55-297">次のコードリストは、_Layout ファイル内の問題の領域を示して *い* ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-297">The following code listing shows problem areas in the *_Layout.cshtml* file:</span></span>

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

<span data-ttu-id="97d55-298">Modernizr への参照は削除できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-298">The reference to Modernizr can be removed.</span></span> <span data-ttu-id="97d55-299">ブートストラップと jQuery への参照は、適切なバージョンへの CDN リンクに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="97d55-299">The references to Bootstrap and jQuery can be replaced with CDN links to the appropriate version.</span></span>

<span data-ttu-id="97d55-300">`@Styles.Render`行の置換後の文字列:</span><span class="sxs-lookup"><span data-stu-id="97d55-300">Replace `@Styles.Render` line with:</span></span>

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

<span data-ttu-id="97d55-301">最後の 2 `Scripts.Render` 行を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="97d55-301">Replace the last two `Scripts.Render` lines with:</span></span>

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

<span data-ttu-id="97d55-302">最後に、ブートストラップの後に、 `<link>` `<link>` アプリで使用するローカルスタイルの要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-302">Finally, after the Bootstrap `<link>`, add additional `<link>` elements for local styles your app uses.</span></span> <span data-ttu-id="97d55-303">*EShop* の場合、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-303">For *eShop*, the result is shown here:</span></span>

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

<span data-ttu-id="97d55-304">要素の表示順序を決定するには `<link>` 、元のアプリのレンダリングされた HTML を確認します。</span><span class="sxs-lookup"><span data-stu-id="97d55-304">To determine the order in which the `<link>` elements should appear, look at your original app's rendered HTML.</span></span> <span data-ttu-id="97d55-305">または、 *BundleConfig.cs* を確認してください。これには、 *eShop* サンプルに適したシーケンスを示す次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97d55-305">Alternatively, review *BundleConfig.cs*, which for the *eShop* sample includes this code indicating the appropriate sequence:</span></span>

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

<span data-ttu-id="97d55-306">もう一度ビルドすると、 *Create* ビューと *Edit* ビューでの jQuery 検証の読み込みエラーがもう1つ表示されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-306">Building again reveals one more error loading jQuery Validation on the *Create* and *Edit* views.</span></span> <span data-ttu-id="97d55-307">次のスクリプトで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="97d55-307">Replace it with this script:</span></span>

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

<span data-ttu-id="97d55-308">ビューで最後に修正することは、 `Session` アプリが実行された時間とコンピューターを表示するためのへの参照です。</span><span class="sxs-lookup"><span data-stu-id="97d55-308">The last thing to fix in the views is the reference to `Session` to display how long the app has been running, and on which machine.</span></span> <span data-ttu-id="97d55-309">このデータをで `Startup` 静的変数として収集し、レイアウトページに変数を表示できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-309">We can collect this data in `Startup` as static variables and display the variables on the layout page.</span></span> <span data-ttu-id="97d55-310">次のプロパティを *Startup.cs* に追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-310">Add the following properties to *Startup.cs*:</span></span>

```csharp
public static DateTime StartTime { get; } = DateTime.UtcNow;
public static string MachineName { get; } = Environment.MachineName;
```

<span data-ttu-id="97d55-311">次に、レイアウトのフッターの内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="97d55-311">Then replace the content of the footer in the layout with the following code:</span></span>

```razor
<section class="col-sm-6">
    <img class="esh-app-footer-text hidden-xs" src="~/images/main_footer_text.png" width="335" height="26" alt="footer text image" />
    <br />
<small>@eShopPorted.Startup.MachineName - @eShopPorted.Startup.StartTime.ToString() UTC</small>
</section>
```

<span data-ttu-id="97d55-312">この時点で、アプリはさらに正常にビルドされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-312">At this point, the app once more builds successfully.</span></span> <span data-ttu-id="97d55-313">ただし、これを実行しようとすると Hello World が生成され *ます。*</span><span class="sxs-lookup"><span data-stu-id="97d55-313">However, trying to run it just yields *Hello World!*</span></span> <span data-ttu-id="97d55-314">**空** の ASP.NET Core テンプレートは、要求に応じて表示されるようにのみ構成されているためです。</span><span class="sxs-lookup"><span data-stu-id="97d55-314">because the **Empty** ASP.NET Core template is only configured to display that in response to any request.</span></span> <span data-ttu-id="97d55-315">次のセクションでは、ASP.NET Core MVC を使用するようにアプリを構成して移行を完了します。これには、依存関係の挿入や構成も含まれます。</span><span class="sxs-lookup"><span data-stu-id="97d55-315">In the next section, I complete the migration by configuring the app to use ASP.NET Core MVC, including dependency injection and configuration.</span></span> <span data-ttu-id="97d55-316">その後、アプリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-316">Once that's in place, the app should run.</span></span> <span data-ttu-id="97d55-317">その後、前に作成したタスクを修正し `TODO:` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-317">Then it will be time to fix the `TODO:` tasks that were created earlier.</span></span>

## <a name="migrate-app-startup-components"></a><span data-ttu-id="97d55-318">アプリのスタートアップコンポーネントの移行</span><span class="sxs-lookup"><span data-stu-id="97d55-318">Migrate app startup components</span></span>

<span data-ttu-id="97d55-319">最後の移行手順では、 *global.asax* からアプリのスタートアップタスクを実行し、そのタスクが呼び出すクラスを使用して、これらのタスクを同等の ASP.NET Core に移行します。</span><span class="sxs-lookup"><span data-stu-id="97d55-319">The last migration step is to take the app startup tasks from *Global.asax*, and the classes it calls, and migrate these to their ASP.NET Core equivalents.</span></span> <span data-ttu-id="97d55-320">これらのタスクには、MVC 自体の構成、依存関係の挿入の設定、および新しい構成システムの操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="97d55-320">These tasks include configuration of MVC itself, setting up dependency injection, and working with the new configuration system.</span></span> <span data-ttu-id="97d55-321">ASP.NET Core では、これらのタスクは *Startup.cs* ファイルで処理されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-321">In ASP.NET Core, these tasks are handled in the *Startup.cs* file.</span></span>

### <a name="configure-mvc"></a><span data-ttu-id="97d55-322">MVC の構成</span><span class="sxs-lookup"><span data-stu-id="97d55-322">Configure MVC</span></span>

<span data-ttu-id="97d55-323">元の ASP.NET MVC アプリは、アプリの起動時に実行される global.asax のに次のコードを持ち `Application_Start` ます。 </span><span class="sxs-lookup"><span data-stu-id="97d55-323">The original ASP.NET MVC app has the following code in its `Application_Start` in *Global.asax*, which runs when the app starts up:</span></span>

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

<span data-ttu-id="97d55-324">これらの行を1つずつ見ると、 `RegisterContainer` メソッドは依存関係の注入を設定します。これは次のように移植されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-324">Looking at these lines one by one, the `RegisterContainer` method sets up dependency injection, which will be ported below.</span></span> <span data-ttu-id="97d55-325">次の3つの行は、MVC のさまざまな部分 (区分、フィルター、およびルート) を構成します。</span><span class="sxs-lookup"><span data-stu-id="97d55-325">The next three lines configure different parts of MVC: areas, filters, and routes.</span></span> <span data-ttu-id="97d55-326">バンドルは、移植されたアプリの静的ファイルに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="97d55-326">Bundles are replaced by static files in the ported app.</span></span> <span data-ttu-id="97d55-327">最後の行では、アプリのデータアクセスを設定します。これは後のセクションで示します。</span><span class="sxs-lookup"><span data-stu-id="97d55-327">The last line sets up data access for the app, which will be shown in a later section.</span></span>

<span data-ttu-id="97d55-328">このアプリは実際には区分を使用していないため、区分登録の呼び出しを移行するために必要な作業はありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-328">Since this app isn't actually using areas, there's nothing that needs to be done to migrate the area registration call.</span></span> <span data-ttu-id="97d55-329">アプリで領域を移行する必要がある場合、 [ドキュメントでは ASP.NET Core での領域の構成方法を指定](/aspnet/core/mvc/controllers/areas)します。</span><span class="sxs-lookup"><span data-stu-id="97d55-329">If your app does need to migrate areas, the [docs specify how to configure areas in ASP.NET Core](/aspnet/core/mvc/controllers/areas).</span></span>

<span data-ttu-id="97d55-330">グローバルフィルターの登録を呼び出すと、 `FilterConfig` アプリの *App_Start* フォルダー内のクラスのヘルパーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-330">The call to register global filters invokes a helper on the `FilterConfig` class in the app's *App_Start* folder:</span></span>

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

<span data-ttu-id="97d55-331">アプリに追加される属性は、ASP.NET MVC フィルター () のみです `HandleErrorAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="97d55-331">The only attribute added to the app is the ASP.NET MVC filter, `HandleErrorAttribute`.</span></span> <span data-ttu-id="97d55-332">このフィルターにより、例外の詳細ではなく、例外が要求の一部として発生したときに、既定のアクションとビューが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-332">This filter ensures that when an exception occurs as part of a request, a default action and view are displayed, rather than the exception details.</span></span> <span data-ttu-id="97d55-333">ASP.NET Core では、この同じ機能がミドルウェアでも実行され `UseExceptionHandler` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-333">In ASP.NET Core, this same functionality is performed by the `UseExceptionHandler` middleware.</span></span> <span data-ttu-id="97d55-334">詳細なエラーメッセージは、既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="97d55-334">The detailed error messages aren't enabled by default.</span></span> <span data-ttu-id="97d55-335">ミドルウェアを使用して構成する必要があり `UseDeveloperExceptionPage` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-335">They must be configured using the `UseDeveloperExceptionPage` middleware.</span></span> <span data-ttu-id="97d55-336">元のアプリに一致するようにこの動作を構成するには、Startup.cs のメソッドの先頭に次のコードを追加する必要があり `Configure` ます。 </span><span class="sxs-lookup"><span data-stu-id="97d55-336">To configure this behavior to match the original app, the following code must be added to the start of the `Configure` method in *Startup.cs*:</span></span>

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

<span data-ttu-id="97d55-337">これは、eShop アプリによって使用される唯一のフィルターを処理します。この場合は、組み込みのミドルウェアを使用して実行されています。</span><span class="sxs-lookup"><span data-stu-id="97d55-337">This takes care of the only filter used by the eShop app, and in this case it was done by using built-in middleware.</span></span> <span data-ttu-id="97d55-338">アプリで構成する必要があるグローバルフィルターがある場合は、MVC がメソッドに追加されるときにこの処理が行われます。これについては、 `ConfigureServices` この章で後ほど説明します。</span><span class="sxs-lookup"><span data-stu-id="97d55-338">If you have global filters that must be configured in your app, this is done when MVC is added in the `ConfigureServices` method, which is shown later in this chapter.</span></span>

<span data-ttu-id="97d55-339">移行が必要な MVC 関連のロジックの最後の部分は、アプリの既定のルートです。</span><span class="sxs-lookup"><span data-stu-id="97d55-339">The last piece of MVC-related logic that needs to be migrated are the app's default routes.</span></span> <span data-ttu-id="97d55-340">の呼び出しは、 `RouteConfig.RegisterRoutes(RouteTable.Routes)` MVC ルートテーブルを `RegisterRoutes` ヘルパーメソッドに渡します。このメソッドでは、アプリの起動時に次のコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-340">The call to `RouteConfig.RegisterRoutes(RouteTable.Routes)` passes the MVC route table to the `RegisterRoutes` helper method, where the following code is executed when the app starts up:</span></span>

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

<span data-ttu-id="97d55-341">このコードを1行ずつ取得すると、最初の行で属性ルートのサポートが設定されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-341">Taking this code line-by-line, the first line sets up support for attribute routes.</span></span> <span data-ttu-id="97d55-342">これは ASP.NET Core に組み込まれているため、個別に構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-342">This is built into ASP.NET Core, so it's unnecessary to configure it separately.</span></span> <span data-ttu-id="97d55-343">同様に、 *{resource} の axd* ファイルは ASP.NET Core では使用されないため、このようなルートを無視する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-343">Likewise, *{resource}.axd* files aren't used with ASP.NET Core, so there's no need to ignore such routes.</span></span> <span data-ttu-id="97d55-344">メソッドは、 `MapRoute` 一般的なルートテンプレートを使用する MVC の既定値を構成し `{controller}/{action}/{id}` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-344">The `MapRoute` method configures the default for MVC, which uses the typical `{controller}/{action}/{id}` route template.</span></span> <span data-ttu-id="97d55-345">また、 `CatalogController` が既定のコントローラーとして使用され、メソッドが既定のアクションであるように、このテンプレートの既定値も指定し `Index` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-345">It also specifies the defaults for this template, such that the `CatalogController` is the default controller used and the `Index` method is the default action.</span></span> <span data-ttu-id="97d55-346">大規模なアプリには、追加のルートを設定するために多くの呼び出しが含まれることがよくあり `MapRoute` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-346">Larger apps will frequently include more calls to `MapRoute` to set up additional routes.</span></span>

<span data-ttu-id="97d55-347">MVC ASP.NET Core は [、従来のルーティングと属性ルーティングを](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2)サポートしています。</span><span class="sxs-lookup"><span data-stu-id="97d55-347">ASP.NET Core MVC supports [conventional routing and attribute routing](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2).</span></span> <span data-ttu-id="97d55-348">従来のルーティングは、前述の方法でルートテーブルを構成する方法に似てい `RegisterRoutes` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-348">Conventional routing is analogous to how the route table is configured in the `RegisterRoutes` method listed previously.</span></span> <span data-ttu-id="97d55-349">既定のルート ( *eShop* アプリで使用されるものなど) を使用して従来のルーティングを設定するには、 `Configure` *Startup.cs* のメソッドの最後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-349">To set up conventional routing with a default route like the one used in the *eShop* app, add the following code to the bottom of the `Configure` method in *Startup.cs*:</span></span>

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> <span data-ttu-id="97d55-350">ASP.NET Core 3.0 以降では、エンドポイントを使用するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-350">With ASP.NET Core 3.0 and later, this is changed to use endpoints.</span></span> <span data-ttu-id="97d55-351">ASP.NET Core 2.2 の初期ポートでは、これは、従来のルートをマッピングするための適切な構文です。</span><span class="sxs-lookup"><span data-stu-id="97d55-351">For the initial port to ASP.NET Core 2.2, this is the proper syntax for mapping conventional routes.</span></span>

<span data-ttu-id="97d55-352">これらの変更が適用されると、 `Configure` メソッドはほぼ完了します。</span><span class="sxs-lookup"><span data-stu-id="97d55-352">With these changes in place, the `Configure` method is almost done.</span></span> <span data-ttu-id="97d55-353">`app.Run`Hello World を出力する元のテンプレートのメソッド *。*</span><span class="sxs-lookup"><span data-stu-id="97d55-353">The original template's `app.Run` method that prints *Hello World!*</span></span> <span data-ttu-id="97d55-354">削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-354">should be deleted.</span></span> <span data-ttu-id="97d55-355">この時点で、メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-355">At this point, the method is as shown here:</span></span>

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

<span data-ttu-id="97d55-356">次に、MVC サービスを構成してから、残りのアプリの依存関係の挿入 (DI) をサポートします。</span><span class="sxs-lookup"><span data-stu-id="97d55-356">Now it's time to configure MVC services, followed by the rest of the app's support for dependency injection (DI).</span></span> <span data-ttu-id="97d55-357">これまでは、 *eShopPorted* プロジェクトの `ConfigureServices` メソッドは空のままです。</span><span class="sxs-lookup"><span data-stu-id="97d55-357">So far, the *eShopPorted* project's `ConfigureServices` method has remained empty.</span></span> <span data-ttu-id="97d55-358">ここで、作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="97d55-358">Now it's time to start populating it.</span></span>

<span data-ttu-id="97d55-359">最初に ASP.NET Core MVC を正常に動作させるには、次のように追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-359">First, to get ASP.NET Core MVC to work properly, it needs to be added:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

<span data-ttu-id="97d55-360">上記のコードは、MVC 機能を使用するために必要な最小限の構成です。</span><span class="sxs-lookup"><span data-stu-id="97d55-360">The preceding code is the minimal configuration required to get MVC features working.</span></span> <span data-ttu-id="97d55-361">この呼び出しから構成できる追加機能は多数ありますが、ここではアプリをビルドするのに十分です。</span><span class="sxs-lookup"><span data-stu-id="97d55-361">There are many additional features that can be configured from this call, but for now this will suffice to build the app.</span></span> <span data-ttu-id="97d55-362">実行すると、既定の要求が適切にルーティングされるようになりましたが、DI をまだ構成していないため、 `CatalogController` 型の実装 `ICatalogService` がまだ提供されていないため、アクティブ化中にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="97d55-362">Running it now routes the default request properly, but since we've not yet configured DI, an error occurs while activating `CatalogController`, because no implementation of type `ICatalogService` has been provided yet.</span></span> <span data-ttu-id="97d55-363">MVC の構成については、後で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="97d55-363">We'll return to configure MVC further in a moment.</span></span> <span data-ttu-id="97d55-364">ここでは、アプリの依存関係の挿入を移行してみましょう。</span><span class="sxs-lookup"><span data-stu-id="97d55-364">For now, let's migrate the app's dependency injection.</span></span>

#### <a name="migrate-dependency-injection-configuration"></a><span data-ttu-id="97d55-365">依存関係挿入構成の移行</span><span class="sxs-lookup"><span data-stu-id="97d55-365">Migrate dependency injection configuration</span></span>

<span data-ttu-id="97d55-366">元のアプリの *global.asax* ファイルは、アプリの起動時に呼び出される次のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="97d55-366">The original app's *Global.asax* file defines the following method, called when the app starts up:</span></span>

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

<span data-ttu-id="97d55-367">このコードは、 [Autofac](https://autofac.org/) コンテナーを構成し、構成設定を読み取り、実際のデータまたはモックデータを使用する必要があるかどうかを判断し、この設定を Autofac モジュール (アプリの */Modules* ディレクトリにあります) に渡します。</span><span class="sxs-lookup"><span data-stu-id="97d55-367">This code configures an [Autofac](https://autofac.org/) container, reads a config setting to determine whether real or mock data should be used, and passes this setting into an Autofac module (found in the app's */Modules* directory).</span></span> <span data-ttu-id="97d55-368">幸い、Autofac は .NET Core をサポートしているので、モジュールを直接移行することができます。</span><span class="sxs-lookup"><span data-stu-id="97d55-368">Fortunately, Autofac supports .NET Core, so the module can be migrated directly.</span></span> <span data-ttu-id="97d55-369">フォルダーを新しいプロジェクトにコピーし、クラスの名前空間を更新して、コンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-369">Copy the folder into the new project and updates the class's namespace and it should compile.</span></span>

<span data-ttu-id="97d55-370">ASP.NET Core には依存関係の挿入のサポートが組み込まれていますが、必要に応じて、Autofac などのサードパーティのコンテナーを簡単に接続できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-370">ASP.NET Core has built-in support for dependency injection, but you can wire up a third-party container such as Autofac easily if necessary.</span></span> <span data-ttu-id="97d55-371">この場合、アプリは Autofac を使用するように既に構成されているため、最も簡単な解決策は、その使用を維持することです。</span><span class="sxs-lookup"><span data-stu-id="97d55-371">In this case, since the app is already configured to use Autofac, the simplest solution is to maintain its usage.</span></span> <span data-ttu-id="97d55-372">これを行うには、メソッドシグネチャを変更してを `ConfigureServices` 返す必要があり `IServiceProvider` ます。また、Autofac container インスタンスを構成し、メソッドから返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-372">To do so, the `ConfigureServices` method signature must be modified to return an `IServiceProvider`, and the Autofac container instance must be configured and returned from the method.</span></span>

<span data-ttu-id="97d55-373">**注:** .NET Core 3.0 以降では、サードパーティの DI コンテナーを統合するためのプロセスが変更されました。</span><span class="sxs-lookup"><span data-stu-id="97d55-373">**Note:** In .NET Core 3.0 and later, the process for integrating a third-party DI container has changed.</span></span>

<span data-ttu-id="97d55-374">Autofac の構成の一部では、を呼び出す必要があり `builder.Populate(services)` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-374">Part of configuring Autofac requires a call to `builder.Populate(services)`.</span></span> <span data-ttu-id="97d55-375">この拡張機能は、NuGet パッケージに含まれ `Autofac.Extensions.DependencyInjection` ています。このパッケージは、コードをコンパイルする前にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-375">This extension is found in the `Autofac.Extensions.DependencyInjection` NuGet package, which must be installed before the code will compile.</span></span>

<span data-ttu-id="97d55-376">`ConfigureServices`Autofac コンテナーを構成するための変更後、新しいメソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-376">After modifying `ConfigureServices` to configure an Autofac container, the new method is as shown here:</span></span>

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

<span data-ttu-id="97d55-377">現時点では、の設定 `useMockData` はに設定されて `true` います。</span><span class="sxs-lookup"><span data-stu-id="97d55-377">For now, the setting for `useMockData` is set to `true`.</span></span> <span data-ttu-id="97d55-378">この設定はすぐに構成から読み取られます。</span><span class="sxs-lookup"><span data-stu-id="97d55-378">This setting will be read from configuration in a moment.</span></span> <span data-ttu-id="97d55-379">この時点で、図4-12 に示すように、アプリはコンパイルされ、実行時に正常に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="97d55-379">At this point, the app compiles and should load successfully when run, as shown in Figure 4-12.</span></span>

![図4-12](media/Figure4-12.png)

<span data-ttu-id="97d55-381">**図 4-12**</span><span class="sxs-lookup"><span data-stu-id="97d55-381">**Figure 4-12.**</span></span> <span data-ttu-id="97d55-382">モックデータを使用してローカルで実行されている *eShop* アプリを移植します。</span><span class="sxs-lookup"><span data-stu-id="97d55-382">Ported *eShop* app running locally with mock data.</span></span>

#### <a name="migrate-app-settings"></a><span data-ttu-id="97d55-383">アプリ設定の移行</span><span class="sxs-lookup"><span data-stu-id="97d55-383">Migrate app settings</span></span>

<span data-ttu-id="97d55-384">ASP.NET Core は新しい [構成システム](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2)を使用します。既定では、ファイル *のappsettings.js* が利用されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-384">ASP.NET Core uses a new [configuration system](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2), which by default leverages an *appsettings.json* file.</span></span> <span data-ttu-id="97d55-385">Program.cs のを使用することにより、 `CreateDefaultBuilder` 既定の構成はアプリで既に設定されています。 </span><span class="sxs-lookup"><span data-stu-id="97d55-385">By using `CreateDefaultBuilder` in *Program.cs*, the default configuration is already set up in the app.</span></span> <span data-ttu-id="97d55-386">構成にアクセスするには、クラスをコンストラクターで要求するだけです。</span><span class="sxs-lookup"><span data-stu-id="97d55-386">To access configuration, classes just need to request it in their constructor.</span></span> <span data-ttu-id="97d55-387">`Startup`クラスは例外ではありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-387">The `Startup` class is no exception.</span></span> <span data-ttu-id="97d55-388">とその他のアプリの構成へのアクセスを開始するには `Startup` 、そのコンストラクターからのインスタンスを要求し `IConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-388">To start accessing configuration in `Startup` and the rest of the app, request an instance of `IConfiguration` from its constructor:</span></span>

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

<span data-ttu-id="97d55-389">元のアプリはを使用してその設定を参照して `ConfigurationManager.AppSettings` います。</span><span class="sxs-lookup"><span data-stu-id="97d55-389">The original app referenced its settings using `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="97d55-390">この用語のすべての参照をすばやく検索すると、新しいアプリに必要な一連の設定が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-390">A quick search for all references of this term yields the set of settings the new app needs.</span></span> <span data-ttu-id="97d55-391">次の2つしかありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-391">There are only two:</span></span>

- `UseMockData`
- `UseCustomizationData`

<span data-ttu-id="97d55-392">アプリの構成が複雑な場合、特にカスタム構成セクションを使用している場合は、アプリケーションの構成のさまざまな部分にオブジェクトを作成し、バインドすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97d55-392">If your app has more complex configuration, especially if it's using custom configuration sections, you'll probably want to create and bind objects to different parts of your app's configuration.</span></span> <span data-ttu-id="97d55-393">これらの型には、 [オプションパターン](../../core/extensions/options.md)を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="97d55-393">These types can then be accessed using the [options pattern](../../core/extensions/options.md).</span></span> <span data-ttu-id="97d55-394">ただし、参照されているドキュメントに記載されているように、このパターンはでは使用でき `ConfigureServices` ません。</span><span class="sxs-lookup"><span data-stu-id="97d55-394">However, as noted in the referenced doc, this pattern shouldn't be used in `ConfigureServices`.</span></span> <span data-ttu-id="97d55-395">代わりに、移植されたアプリは `UseMockData` 構成値を直接参照します。</span><span class="sxs-lookup"><span data-stu-id="97d55-395">Instead the ported app will reference the `UseMockData` configuration value directly.</span></span>

<span data-ttu-id="97d55-396">まず、移植されたアプリのファイルを変更 `appsettings.json` し、ルートに次の2つの設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-396">First, modify the ported app's `appsettings.json` file and add the two settings in the root:</span></span>

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

<span data-ttu-id="97d55-397">次に、を変更して、 `ConfigureServices` `UseMockData` プロパティから設定にアクセスし `Configuration` ます (以前に値をに設定してい `true` ます)。</span><span class="sxs-lookup"><span data-stu-id="97d55-397">Now, modify `ConfigureServices` to access the `UseMockData` setting from the `Configuration` property (where previously we set the value to `true`):</span></span>

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

<span data-ttu-id="97d55-398">この時点で、構成から設定がプルされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-398">At this point, the setting is pulled from configuration.</span></span> <span data-ttu-id="97d55-399">もう1つの設定は、 `UseCustomizationData` クラスによって使用され `CatalogDBInitializer` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-399">The other setting, `UseCustomizationData`, is used by the `CatalogDBInitializer` class.</span></span> <span data-ttu-id="97d55-400">このクラスを最初に移植したときに、へのアクセスをコメント化して `ConfigurationManager.AppSettings["UseCustomizationData"]` います。</span><span class="sxs-lookup"><span data-stu-id="97d55-400">When you first ported this class, you commented out the access to `ConfigurationManager.AppSettings["UseCustomizationData"]`.</span></span> <span data-ttu-id="97d55-401">次に、ASP.NET Core 構成を使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="97d55-401">Now it's time to modify it to use ASP.NET Core configuration.</span></span> <span data-ttu-id="97d55-402">のコンストラクターを次のように変更 `CatalogDBInitializer` します。</span><span class="sxs-lookup"><span data-stu-id="97d55-402">Modify the constructor of `CatalogDBInitializer` as follows:</span></span>

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

<span data-ttu-id="97d55-403">新しい型を使用するには、web アプリ内の構成へのすべてのアクセスをこの方法で変更する必要があり `IConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-403">All access to configuration within the web app should be modified in this manner to use the new `IConfiguration` type.</span></span> <span data-ttu-id="97d55-404">.NET Framework 構成へのアクセスを必要とする依存関係では、web プロジェクトに追加された *app.config* ファイルにそのような設定を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="97d55-404">Dependencies that require access to .NET Framework configuration can include such settings in an *app.config* file added to the web project.</span></span> <span data-ttu-id="97d55-405">依存プロジェクトは、を使用して `ConfigurationManager` 設定にアクセスできます。また、この方法を既に使用している場合は、変更を必要としません。</span><span class="sxs-lookup"><span data-stu-id="97d55-405">The dependent projects can work with `ConfigurationManager` to access settings, and shouldn't require any changes if they already use this approach.</span></span> <span data-ttu-id="97d55-406">ただし、ASP.NET Core アプリは独自の実行可能ファイルとして実行されるため、 *web.config* を参照するのではなく、 *app.config* します。レガシアプリの *web.config* ファイルから ASP.NET Core アプリの新しい *app.config* ファイルに設定を移行することによって、 `ConfigurationManager` 設定へのアクセスにを使用するコンポーネントは引き続き正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="97d55-406">However, since ASP.NET Core apps run as their own executable, they don't reference *web.config* but rather *app.config*. By migrating settings from the legacy app's *web.config* file to a new *app.config* file in the ASP.NET Core app, components that use `ConfigurationManager` to access their settings will continue to function properly.</span></span>

<span data-ttu-id="97d55-407">アプリの移行はほぼ完了しています。</span><span class="sxs-lookup"><span data-stu-id="97d55-407">The app's migration is nearly complete.</span></span> <span data-ttu-id="97d55-408">残りのタスクは、データアクセス構成のみです。</span><span class="sxs-lookup"><span data-stu-id="97d55-408">The only remaining task is data access configuration.</span></span>
  
## <a name="data-access-considerations"></a><span data-ttu-id="97d55-409">データアクセスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="97d55-409">Data access considerations</span></span>

<span data-ttu-id="97d55-410">.NET Framework で実行されている ASP.NET Core アプリは Entity Framework (EF) を引き続き利用できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-410">ASP.NET Core apps running on .NET Framework can continue to leverage Entity Framework (EF).</span></span> <span data-ttu-id="97d55-411">増分移行を実行する場合は、データアクセスに EF Core を使用するように移植する前に、EF 6 を使用してアプリを操作することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97d55-411">If performing an incremental migration, getting the app working with EF 6 before trying to port its data access to use EF Core may be worthwhile.</span></span> <span data-ttu-id="97d55-412">これにより、別の移行作業ブロックが開始される前に、アプリの移行に関する問題を特定し、対処することができます。</span><span class="sxs-lookup"><span data-stu-id="97d55-412">In this way, any problems with the app's migration can be identified and addressed before another block of migration effort is begun.</span></span>

<span data-ttu-id="97d55-413">この作業は Autofac で実行されているため、eShop サンプルの移行で EF 6 を構成する場合、特別な作業は必要ありません `ApplicationModule` 。</span><span class="sxs-lookup"><span data-stu-id="97d55-413">As it happens, configuring EF 6 in the eShop sample migration doesn't require any special work, since this work was performed in the Autofac `ApplicationModule`.</span></span> <span data-ttu-id="97d55-414">唯一の問題は、現在 `CatalogDBContext` クラスが *web.config* から接続文字列を読み取ろうとしていることです。これに対処するには、接続の詳細を *appsettings.js* に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-414">The only problem is that currently the `CatalogDBContext` class tries to read its connection string from *web.config*. To address this, the connection details need to be added to *appsettings.json*.</span></span> <span data-ttu-id="97d55-415">次に、接続文字列を作成するときに、その接続文字列をに渡す必要があり `CatalogDBContext` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-415">Then the connection string must be passed into `CatalogDBContext` when it's created.</span></span>

<span data-ttu-id="97d55-416">の *appsettings.js* を更新して、接続文字列を含めます。</span><span class="sxs-lookup"><span data-stu-id="97d55-416">Update the *appsettings.json* to include the connection string.</span></span> <span data-ttu-id="97d55-417">完全なファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="97d55-417">The full file is listed here:</span></span>

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

<span data-ttu-id="97d55-418">の作成時に、接続文字列をコンストラクターに渡す必要があり `DbContext` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-418">The connection string must be passed into the constructor when the `DbContext` is created.</span></span> <span data-ttu-id="97d55-419">インスタンスは Autofac によって作成されるため、で変更を行う必要があり `ApplicationModule` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-419">Since the instances are created by Autofac, the change needs to be made in `ApplicationModule`.</span></span> <span data-ttu-id="97d55-420">モジュールを変更して、コンストラクター内のを取得 `connectionString` し、フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="97d55-420">Modify the module to take in a `connectionString` in its constructor and assign it to a field.</span></span> <span data-ttu-id="97d55-421">次に、の登録を変更し `CatalogDBContext` て、接続文字列をパラメーターとして追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-421">Then modify the registration for `CatalogDBContext` to add connection string as a parameter:</span></span>

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

<span data-ttu-id="97d55-422">パラメーターは、それ自体の新しいコンストラクターオーバーロードにも追加する必要があり `CatalogDBContext` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-422">The parameter must also be added to a new constructor overload in `CatalogDBContext` itself:</span></span>

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

<span data-ttu-id="97d55-423">最後に、は `ConfigureServices` から接続文字列を読み取り、それを `Config` インスタンス化するときにに渡す必要があり `ApplicationModule` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-423">Finally, `ConfigureServices` must read the connection string from `Config` and pass it into the `ApplicationModule` when it instantiates it:</span></span>

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

<span data-ttu-id="97d55-424">このコードを配置すると、アプリは前と同じように実行され、がのときに SQL Server データベースに接続し `UseMockData` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-424">With this code in place, the app runs as it did before, connecting to a SQL Server database when `UseMockData` is `false`.</span></span>

<span data-ttu-id="97d55-425">このアプリは、この時点で運用環境でデプロイして実行できます。 ASP.NET Core に変換されますが、.NET Framework および EF 6 で実行されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-425">The app can be deployed and run in production at this point, converted to ASP.NET Core but still running on .NET Framework and EF 6.</span></span> <span data-ttu-id="97d55-426">必要に応じて、アプリを .NET Core および Entity Framework Core で実行するように移行できます。これにより、前の章で説明した追加の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="97d55-426">If desired, the app can be migrated to run on .NET Core and Entity Framework Core, which will bring additional advantages described in earlier chapters.</span></span> <span data-ttu-id="97d55-427">Entity Framework に固有の [このドキュメントでは EF Core と EF 6 を比較](/ef/efcore-and-ef6/) し、さまざまな個別の機能をサポートするライブラリを示すグリッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97d55-427">Specific to Entity Framework, [this documentation compares EF Core and EF 6](/ef/efcore-and-ef6/) and includes a grid showing which library supports each of dozens of individual features.</span></span>

### <a name="migrate-to-entity-framework-core"></a><span data-ttu-id="97d55-428">Entity Framework Core への移行</span><span class="sxs-lookup"><span data-stu-id="97d55-428">Migrate to Entity Framework Core</span></span>

<span data-ttu-id="97d55-429">EF Core に移行することを決定した場合、特に元のアプリでコードベースのモデルアプローチを使用した場合は、手順が非常に簡単になります。</span><span class="sxs-lookup"><span data-stu-id="97d55-429">Assuming a decision is made to migrate to EF Core, the steps can be fairly straightforward, especially if the original app used a code-based model approach.</span></span> <span data-ttu-id="97d55-430">[EF 6 から EF Core への移植を準備](/ef/efcore-and-ef6/porting/)するときに、使用する EF Core の移行先バージョンの機能が使用可能かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="97d55-430">When [preparing to port from EF 6 to EF Core](/ef/efcore-and-ef6/porting/), review the availability of features in the destination version of EF Core you'll be using.</span></span> <span data-ttu-id="97d55-431">[および EDMX ベースのモデルからの移植と](/ef/efcore-and-ef6/porting/port-edmx)、[コードベースのモデルからの移植](/ef/efcore-and-ef6/porting/port-code)に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="97d55-431">Review the documentation on [porting from and EDMX-based model](/ef/efcore-and-ef6/porting/port-edmx) versus [porting from a code-based model](/ef/efcore-and-ef6/porting/port-code).</span></span>

<span data-ttu-id="97d55-432">EF Core 2.2 にアップグレードするには、適切な NuGet パッケージを追加し、名前空間を更新するという基本的な手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="97d55-432">To upgrade to EF Core 2.2, the basic steps involved are to add the appropriate NuGet package(s) and update namespaces.</span></span> <span data-ttu-id="97d55-433">次に、接続文字列を型に渡す方法 `DbContext` と、依存関係の挿入に使用する方法を調整します。</span><span class="sxs-lookup"><span data-stu-id="97d55-433">Then adjust how the connection string is passed to the `DbContext` type and how they're wired up for dependency injection.</span></span>

<span data-ttu-id="97d55-434">EF Core は、プロジェクトへのパッケージ参照として追加されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-434">EF Core is added as a package reference to the project:</span></span>

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

<span data-ttu-id="97d55-435">EF 6 への参照は削除されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-435">The reference to EF 6 is removed:</span></span>

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

<span data-ttu-id="97d55-436">コンパイラは、およびでエラーを報告し `CatalogDBContext` `CatalogDBInitializer` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-436">The compiler will report errors in `CatalogDBContext` and `CatalogDBInitializer`.</span></span> <span data-ttu-id="97d55-437">`CatalogDbContext` 古い名前空間を削除してに置き換える必要があり `Microsoft.EntityFrameworkCore` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-437">`CatalogDbContext` needs to have the old namespaces removed and replaced with `Microsoft.EntityFrameworkCore`.</span></span> <span data-ttu-id="97d55-438">そのコンストラクターは削除できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-438">Its constructors can be removed.</span></span> <span data-ttu-id="97d55-439">`DbModelBuilder` はに置き換える必要があり `ModelBuilder` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-439">`DbModelBuilder` should be replaced with `ModelBuilder`.</span></span> <span data-ttu-id="97d55-440">型を構成するためのヘルパーメソッドは、を実装する別のクラスに移動され `IEntityTypeConfiguration<T>` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-440">The helper methods for configuring types are moved to separate classes implementing `IEntityTypeConfiguration<T>`.</span></span> <span data-ttu-id="97d55-441">その後、 `CatalogDBContext` クラスの `OnModelCreating` メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-441">Then the `CatalogDBContext` class's `OnModelCreating` method simply becomes:</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

<span data-ttu-id="97d55-442">関連するその他の変更点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="97d55-442">Other changes involved include:</span></span>

- <span data-ttu-id="97d55-443">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` 置換後 `ValueGeneratedNever()`</span><span class="sxs-lookup"><span data-stu-id="97d55-443">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` replaced with `ValueGeneratedNever()`</span></span>
- <span data-ttu-id="97d55-444">`HasRequired<T>` 置換後 `HasOne<T>`</span><span class="sxs-lookup"><span data-stu-id="97d55-444">`HasRequired<T>` replaced with `HasOne<T>`</span></span>
- <span data-ttu-id="97d55-445">インストール済み `Microsoft.EntityFrameworkCore.Relational` パッケージ</span><span class="sxs-lookup"><span data-stu-id="97d55-445">Installed `Microsoft.EntityFrameworkCore.Relational` package</span></span>
- <span data-ttu-id="97d55-446">`CatalogDBContext`取得 `DbContextOptions` して基本コンストラクターに渡すコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="97d55-446">Add a constructor to `CatalogDBContext` taking `DbContextOptions` and passing it to the base constructor</span></span>

<span data-ttu-id="97d55-447">の構成クラスの例を次 `CatalogType` に示します。</span><span class="sxs-lookup"><span data-stu-id="97d55-447">An example configuration class for `CatalogType` is shown here:</span></span>

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

<span data-ttu-id="97d55-448">`CatalogDBInitializer`とその基本クラスは、 `CreateDatabaseIfNotExists<T>` EF Core と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-448">The `CatalogDBInitializer` and its base class, `CreateDatabaseIfNotExists<T>`, are incompatible with EF Core.</span></span> <span data-ttu-id="97d55-449">このクラスの目的は、データベースを作成およびシードすることです。</span><span class="sxs-lookup"><span data-stu-id="97d55-449">The purpose of this class is to create and seed the database.</span></span> <span data-ttu-id="97d55-450">EF Core を使用すると、次のメソッドを使用して[、 `DbContext` に関連付けられているデータベースが作成および削除](/ef/core/managing-schemas/ensure-created)されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-450">Using EF Core will [create and drop the associated database for a `DbContext`](/ef/core/managing-schemas/ensure-created) using these methods:</span></span>

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

<span data-ttu-id="97d55-451">EF Core でのデータのシード処理は、手動スクリプトを使用するか、型構成の一部として行うことができます。</span><span class="sxs-lookup"><span data-stu-id="97d55-451">Seeding data in EF Core can be done with manual scripts, or as part of the type configuration.</span></span> <span data-ttu-id="97d55-452">他のエンティティプロパティと共に、を使用して、クラスでシードデータを構成でき `IEntityTypeConfiguration` `builder.HasData()` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-452">Along with other entity properties, seed data can be configured in `IEntityTypeConfiguration` classes by using `builder.HasData()`.</span></span> <span data-ttu-id="97d55-453">元のアプリは、 *セットアップ* ディレクトリの CSV ファイルからシードデータを読み込みました。</span><span class="sxs-lookup"><span data-stu-id="97d55-453">The original app loaded seed data from CSV files in the *Setup* directory.</span></span> <span data-ttu-id="97d55-454">項目が少数しかない場合、これらのデータレコードはエンティティ構成の一部として追加できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-454">Given that there are only a handful of items, these data records can instead be added as part of the entity configuration.</span></span> <span data-ttu-id="97d55-455">この方法は、頻繁に変更されるテーブル内の参照データに適しています。</span><span class="sxs-lookup"><span data-stu-id="97d55-455">This approach works well for lookup data in tables that change infrequently.</span></span> <span data-ttu-id="97d55-456">次のメソッドをに追加する `CatalogTypeConfig` `Configure` と、データベースの作成時に、関連付けられている行が確実に存在するようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-456">Adding the following to `CatalogTypeConfig`'s `Configure` method ensures the associated rows are present when the database is created:</span></span>

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

<span data-ttu-id="97d55-457">初期アプリには、 `PreconfiguredData` とのデータを含むクラスが含まれている `CatalogBrand` `CatalogType` ため、このメソッドを使用すると、 `HasData` 次のようになります。</span><span class="sxs-lookup"><span data-stu-id="97d55-457">The initial app includes a `PreconfiguredData` class, which includes data for `CatalogBrand` and `CatalogType`, so using this method the `HasData` call reduces to:</span></span>

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

<span data-ttu-id="97d55-458">`CatalogItem`また、データはから取得することもでき `PreconfiguredData` ます。また、関連付けられたイメージがソース管理に保持されることを前提としています。これは、アプリが機能するために必要な最後のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="97d55-458">The `CatalogItem` data can also be pulled from `PreconfiguredData`, and assuming the associated images are kept in source control, that is the last table needed for the app to function.</span></span> <span data-ttu-id="97d55-459">`CatalogDBInitializer`クラスは、そのクラスへの参照と共に削除できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-459">The `CatalogDBInitializer` class can be removed, along with any references to it.</span></span> <span data-ttu-id="97d55-460">`CatalogItemHiLoGenerator`ディレクトリ内のクラスと SQL ファイル `Infrastructure` も、それらへの参照 (、、) と共に削除され `CatalogService` `ApplicationModule` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-460">The `CatalogItemHiLoGenerator` class and the SQL files in the `Infrastructure` directory are also removed, along with any references to them (in `CatalogService`, `ApplicationModule`).</span></span>

<span data-ttu-id="97d55-461">の特殊なキージェネレータークラスを削除することで `CatalogItem` 、このコードはから削除されました `CatalogItemConfig` 。</span><span class="sxs-lookup"><span data-stu-id="97d55-461">With the elimination of the special key generator classes for `CatalogItem`, this code now is removed from `CatalogItemConfig`:</span></span>

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

<span data-ttu-id="97d55-462">これらの変更により、ASP.NET Core アプリはビルドされますが、まだ EF Core では使用できません。これは、依存関係の挿入のために構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-462">With these modifications, the ASP.NET Core app builds, but it doesn't yet work with EF Core, which must still be configured for dependency injection.</span></span> <span data-ttu-id="97d55-463">EF Core では、最も簡単に構成する方法は `ConfigureServices` 次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="97d55-463">With EF Core, the simplest way to configure it is in `ConfigureServices`:</span></span>

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

<span data-ttu-id="97d55-464">Autofac の最終バージョンでは、 `ApplicationModule` アプリがモックデータを使用するように構成されているかどうかに応じて、1つの型のみを構成します。</span><span class="sxs-lookup"><span data-stu-id="97d55-464">The final version of Autofac's `ApplicationModule` only configures one type, depending on whether the app is configured to use mock data:</span></span>

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

<span data-ttu-id="97d55-465">移植されたアプリは実行されますが、モック以外のデータを使用するように構成されている場合、データは表示されません。</span><span class="sxs-lookup"><span data-stu-id="97d55-465">The ported app runs, but doesn't display any data if configured to use non-mock data.</span></span> <span data-ttu-id="97d55-466">によって追加されたシードデータ `HasData` は、移行が適用されたときにのみ挿入されます。</span><span class="sxs-lookup"><span data-stu-id="97d55-466">The seed data added through `HasData` is only inserted when migrations are applied.</span></span> <span data-ttu-id="97d55-467">ソースアプリは移行を使用していませんでしたが、そのような場合は移行できません。</span><span class="sxs-lookup"><span data-stu-id="97d55-467">The source app didn't use migrations, and if it had, they wouldn't migrate as-is.</span></span> <span data-ttu-id="97d55-468">新しい移行スクリプトから始めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97d55-468">The best approach is to start with a new migration script.</span></span> <span data-ttu-id="97d55-469">これを行うには、のパッケージ参照を追加 `Microsoft.EntityFrameworkCore.Design` し、プロジェクトルートでターミナルウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="97d55-469">To do this, add a package reference for `Microsoft.EntityFrameworkCore.Design` and open a terminal window in the project root.</span></span> <span data-ttu-id="97d55-470">次に、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="97d55-470">Then run:</span></span>

```dotnetcli
dotnet ef migrations add Initial
```

<span data-ttu-id="97d55-471">既存の *eShopPorted* データベースが存在する場合は削除し、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="97d55-471">Drop the existing *eShopPorted* database if it exists, then run:</span></span>

```dotnetcli
dotnet ef database update
```

<span data-ttu-id="97d55-472">これにより、データベースが作成され、シードされます。</span><span class="sxs-lookup"><span data-stu-id="97d55-472">This creates and seeds the database.</span></span> <span data-ttu-id="97d55-473">これで、いくつかの小さな更新プログラムを実行する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="97d55-473">It's now ready to run, with a few small updates left to address.</span></span>

## <a name="fix-all-todo-tasks"></a><span data-ttu-id="97d55-474">すべての TODO タスクを修正します</span><span class="sxs-lookup"><span data-stu-id="97d55-474">Fix all TODO tasks</span></span>

<span data-ttu-id="97d55-475">この時点で移植されたアプリを実行すると、ページに画像が表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="97d55-475">Running the ported app at this point reveals that no pictures are shown on the page.</span></span> <span data-ttu-id="97d55-476">これは、 `PictureUri` のプロパティ `CatalogItem` が設定されていないためです。</span><span class="sxs-lookup"><span data-stu-id="97d55-476">This is because the `PictureUri` property of `CatalogItem` is never set.</span></span> <span data-ttu-id="97d55-477">`TODO`Visual Studio の **タスク一覧** を使用して作成した項目の一覧を見ると、残っているのは `CatalogController` "Wwwroot から pic を参照" というメモが付いているもののみです。</span><span class="sxs-lookup"><span data-stu-id="97d55-477">Looking at the list of `TODO` items we created using Visual Studio's **Task List**, the only one that remains is in `CatalogController`, with a note to "Reference pic from wwwroot."</span></span> <span data-ttu-id="97d55-478">問題のコードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="97d55-478">The code in question is:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="97d55-479">最も簡単な解決策は、サイトのパブリック *wwwroot/Pics* ディレクトリにある公開イメージファイルを参照することです。</span><span class="sxs-lookup"><span data-stu-id="97d55-479">The simplest fix is to reference the public image files in the site's public *wwwroot/Pics* directory.</span></span> <span data-ttu-id="97d55-480">このタスクを実行するには、メソッドを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="97d55-480">This task can be accomplished by replacing the method with the following code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

<span data-ttu-id="97d55-481">この変更により、アプリを実行すると、イメージが以前と同じように動作することがわかります。</span><span class="sxs-lookup"><span data-stu-id="97d55-481">With this change, running the app reveals the images work as before.</span></span>

## <a name="additional-mvc-customizations"></a><span data-ttu-id="97d55-482">追加の MVC カスタマイズ</span><span class="sxs-lookup"><span data-stu-id="97d55-482">Additional MVC customizations</span></span>

<span data-ttu-id="97d55-483">*EShopLegacyMVC* アプリはかなり単純なので、既定の MVC の動作に関して構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="97d55-483">The *eShopLegacyMVC* app is fairly simple, so there isn't much to configure in terms of default MVC behavior.</span></span> <span data-ttu-id="97d55-484">ただし、CORS、フィルター、ルート制約などの追加の MVC コンポーネントを構成する必要がある場合は、通常、この情報をに提供し `Startup.ConfigureServices` ます。ここで、 `UseMvc` はを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97d55-484">However, if you do need to configure additional MVC components, such as CORS, filters, and route constraints, you generally provide this information in `Startup.ConfigureServices`, where `UseMvc` is called.</span></span> <span data-ttu-id="97d55-485">たとえば、次のコードリストでは、 [CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) を構成し、グローバルアクションフィルターを設定しています。</span><span class="sxs-lookup"><span data-stu-id="97d55-485">For example, the following code listing configures [CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) and sets up a global action filter:</span></span>

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
> <span data-ttu-id="97d55-486">CORS の構成を完了するには、でもを呼び出す必要があり `app.UseCors()` `Configure` ます。</span><span class="sxs-lookup"><span data-stu-id="97d55-486">To finish configuring CORS, you must also call `app.UseCors()` in `Configure`.</span></span>

<span data-ttu-id="97d55-487">[カスタムモデルバインダー](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2)やフォーマッタなどの追加の高度なシナリオについては、詳細な ASP.NET Core のドキュメントを参照してください。通常、これらは、個々のコントローラーまたはアクションに適用することも、前のコードリストに示されているのと同じオプションの方法を使用してグローバルに適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="97d55-487">Other advanced scenarios, like adding [custom model binders](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2), formatters, and more are covered in the detailed ASP.NET Core docs. Generally these can be applied on an individual controller or action basis, or globally using the same options approach shown in the previous code listing.</span></span>

## <a name="other-dependencies"></a><span data-ttu-id="97d55-488">その他の依存関係</span><span class="sxs-lookup"><span data-stu-id="97d55-488">Other dependencies</span></span>

<span data-ttu-id="97d55-489">WCF クライアントの種類やトレースコードなど、レガシ構成モデルに依存している .NET Framework 機能を使用する依存関係は、移植時に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-489">Dependencies that use .NET Framework features that had a dependency on the legacy configuration model, such as the WCF client type and tracing code, must be modified when ported.</span></span> <span data-ttu-id="97d55-490">これらの型が構成情報を直接取得するのではなく、コードで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-490">Rather than having these types pull in their configuration information directly, they should be configured in code.</span></span> <span data-ttu-id="97d55-491">たとえば、ASP.NET アプリの *web.config* で使用するように構成された WCF サービスへの接続は、 `basicHttpBinding` 次のコードを使用してプログラムで構成できます。</span><span class="sxs-lookup"><span data-stu-id="97d55-491">For example, a connection to a WCF service that was configured in an ASP.NET app's *web.config* to use `basicHttpBinding` could instead be configured programmatically with the following code:</span></span>

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

<span data-ttu-id="97d55-492">設定の構成ファイルに依存するのではなく、WCF クライアントおよびその他の .NET Framework の種類には、コードで設定を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d55-492">Rather than relying on config files for its settings, WCF clients and other .NET Framework types should have their settings specified in code.</span></span> <span data-ttu-id="97d55-493">このように構成すると、これらの型は ASP.NET Core 2.2 アプリで引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="97d55-493">Configured in this manner, these types can continue to work in ASP.NET Core 2.2 apps.</span></span>

## <a name="references"></a><span data-ttu-id="97d55-494">リファレンス</span><span class="sxs-lookup"><span data-stu-id="97d55-494">References</span></span>

- [<span data-ttu-id="97d55-495">eShopModernizing GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="97d55-495">eShopModernizing GitHub repository</span></span>](https://github.com/dotnet-architecture/eShopModernizing)
- [<span data-ttu-id="97d55-496">.NET Upgrade Assistant ツール</span><span class="sxs-lookup"><span data-stu-id="97d55-496">.NET Upgrade Assistant tool</span></span>](https://aka.ms/dotnet-upgrade-assistant)
- [<span data-ttu-id="97d55-497">API と Viewmodel がドメインモデルを参照することはできません</span><span class="sxs-lookup"><span data-stu-id="97d55-497">Your API and ViewModels Should Not Reference Domain Models</span></span>](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [<span data-ttu-id="97d55-498">開発者の例外ページミドルウェア</span><span class="sxs-lookup"><span data-stu-id="97d55-498">Developer Exception Page Middleware</span></span>](/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [<span data-ttu-id="97d55-499">EF Core HasData の詳細</span><span class="sxs-lookup"><span data-stu-id="97d55-499">Deep Dive into EF Core HasData</span></span>](/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
><span data-ttu-id="97d55-500">[前へ](more-migration-scenarios.md)
>[次へ](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="97d55-500">[Previous](more-migration-scenarios.md)
[Next](deployment-scenarios.md)</span></span>
