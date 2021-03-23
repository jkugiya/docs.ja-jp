---
title: Visual Studio を使用して .NET Core アプリを展開する
description: Visual Studio で .NET Core アプリをデプロイする方法を説明します。
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4fe2663f7fd428035aaca61e4e47bd2bf2a4f391
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872913"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="7ccc0-103">Visual Studio を使用して .NET Core アプリを展開する</span><span class="sxs-lookup"><span data-stu-id="7ccc0-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="7ccc0-104">.NET Core アプリケーションは、アプリケーション バイナリは含むが、対象のシステムに .NET Core があるかどうかに依存する *フレームワークに依存する展開*、またはアプリケーションと .NET Core バイナリの両方を含む *自己完結型の展開* のいずれかで展開できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="7ccc0-105">.NET Core アプリケーションの展開の概要については、「[.NET Core アプリケーションの展開](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="7ccc0-106">次のセクションでは、Microsoft Visual Studio を使用して、次のような展開を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="7ccc0-107">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="7ccc0-108">サードパーティの依存関係を含む、フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="7ccc0-109">自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-109">Self-contained deployment</span></span>
- <span data-ttu-id="7ccc0-110">サードパーティの依存関係を含む、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="7ccc0-111">Visual Studio を使用して、.NET Core アプリケーションを開発する方法の詳細については、[.NET Core の依存関係と要件](../install/windows.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/windows.md).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="7ccc0-112">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-112">Framework-dependent deployment</span></span>

<span data-ttu-id="7ccc0-113">サードパーティの依存関係を含まない、フレームワークに依存する展開を展開するプロセスには、アプリのビルド、テスト、および発行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="7ccc0-114">C# で記述された次の単純な例は、このプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-114">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="7ccc0-115">プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-115">Create the project.</span></span>

   <span data-ttu-id="7ccc0-116">**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="7ccc0-117">**[新しいプロジェクト]** ダイアログの **[インストール]** プロジェクトの種類ウィンドウでお使いの言語 (C# または Visual Basic) のプロジェクト カテゴリを展開し、 **[.NET Core]** を選択し、中央のウィンドウで **[コンソール アプリケーション (.NET Core)]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="7ccc0-118">**[名前]** テキスト ボックスに、"FDD" などのプロジェクト名を入力します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="7ccc0-119">**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="7ccc0-120">アプリケーションのソース コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-120">Add the application's source code.</span></span>

   <span data-ttu-id="7ccc0-121">エディターで *Program.cs* または *Program.vb* ファイルを開き、自動生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="7ccc0-122">テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="7ccc0-123">正規表現 `\w+` を使用して、入力テキストの単語を分離します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. <span data-ttu-id="7ccc0-124">アプリのデバッグ ビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="7ccc0-125">**[ビルド]**  >  **[ソリューションのビルド]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="7ccc0-126">**[デバッグ]**  >  **[デバッグ開始]** を選択して、アプリケーションのデバッグ ビルドをコンパイルして、実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="7ccc0-127">アプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-127">Deploy your app.</span></span>

   <span data-ttu-id="7ccc0-128">プログラムをデバッグしてテストしたら、アプリと共に配置するファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="7ccc0-129">Visual Studio から発行するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="7ccc0-130">アプリの (デバッグではなく) リリース バージョンを構築するために、ツールバーでソリューションの構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="7ccc0-131">**ソリューション エクスプローラー** で (ソリューションではなく) プロジェクトを右クリックし、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="7ccc0-132">**[発行]** タブで **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="7ccc0-133">Visual Studio が、アプリケーションを構成するファイルをローカル ファイル システムに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="7ccc0-134">これで **[発行]** タブには、 **[FolderProfile]** という 1 つのプロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="7ccc0-135">プロファイルの構成設定が、タブの **[概要]** セクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="7ccc0-136">作成されたファイルは、ご自分のプロジェクトの *.\bin\release\netcoreapp2.1* サブディレクトリのサブディレクトリ内にある、`Publish` (Windows の場合) または `publish` (Unix システムの場合) という名前のディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="7ccc0-137">アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="7ccc0-138">このファイルは、主に例外のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="7ccc0-139">これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="7ccc0-140">ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="7ccc0-141">アプリケーション ファイルの完全なセットは、任意の方法で展開できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="7ccc0-142">たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="7ccc0-143">インストールしたら、ユーザーはアプリケーションを、`dotnet` コマンドを使用し、`dotnet fdd.dll` などのアプリケーションのファイル名を提供して実行できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="7ccc0-144">また、アプリケーション インストールの一環として、インストーラーはアプリケーション バイナリに加えて、共有フレームワーク インストーラーをバンドルするか、または前提条件として共有フレームワークがあるか確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="7ccc0-145">共有フレームワークのインストールは、コンピューター全体が対象なので、管理者/ルート アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="7ccc0-146">サードパーティの依存関係を含む、フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="7ccc0-147">1 つ以上のサードパーティの依存関係を備えたフレームワークに依存する展開を展開するには、すべての依存関係をプロジェクトに使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="7ccc0-148">アプリをビルドする前に、次の追加手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="7ccc0-149">**NuGet パッケージ マネージャー** を使用し、プロジェクトに NuGet パッケージへの参照を追加します。このとき、パッケージがシステムにまだない場合はそれをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="7ccc0-150">パッケージ マネージャーを開くには、 **[ツール]**  >  **[NuGet パッケージ マネージャー]**  >  **[ソリューションの NuGet パッケージの管理]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="7ccc0-151">サードパーティの依存関係 (`Newtonsoft.Json` など) がシステムにインストールされていることを確認し、インストールされていない場合はインストールします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="7ccc0-152">**[インストール済み]** タブに、システムにインストールされた NuGet パッケージの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="7ccc0-153">`Newtonsoft.Json` がそこにない場合、 **[参照]** タブを選択し、検索ボックスに "Newtonsoft.Json" と入力します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="7ccc0-154">`Newtonsoft.Json` を選択し、右側のウィンドウでプロジェクトを選択してから、 **[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="7ccc0-155">`Newtonsoft.Json` が既にシステムにインストールされている場合、 **[ソリューション パッケージの管理]** タブの右のウィンドウからプロジェクトを選択し、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="7ccc0-156">サードパーティの依存関係を含む、フレームワークに依存する展開は、サードパーティの依存関係と同じ移植性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-156">A framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="7ccc0-157">たとえば、サードパーティ ライブラリが macOS のみをサポートする場合、そのアプリを Windows システムに移植することはできません。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="7ccc0-158">この状況は、サードパーティの依存関係自体がネイティブ コードに依存する場合に生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="7ccc0-159">このよい例は、[libuv](https://github.com/libuv/libuv) に対してネイティブの依存関係が必要な [Kestrel サーバー](/aspnet/core/fundamentals/servers/kestrel)です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-159">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="7ccc0-160">このようなサードパーティの依存関係を含むアプリケーションに対して FDD が作成されると、発行された出力には、ネイティブの依存関係がサポートする (そして、その NuGet パッケージ内に存在する) 各[ランタイム識別子 (RID)](../rid-catalog.md) のフォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a> <span data-ttu-id="7ccc0-161">サードパーティの依存関係を含まない、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="7ccc0-162">サードパーティの依存関係を含まない自己完結型の展開を展開するプロセスには、プロジェクトの作成、*csproj* ファイルの変更、アプリのビルド、テスト、および発行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="7ccc0-163">C# で記述された次の単純な例は、このプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="7ccc0-164">フレームワーク依存の展開の場合と同じように、ご自分のプロジェクトの作成、コーディング、テストを開始します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="7ccc0-165">プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-165">Create the project.</span></span>

   <span data-ttu-id="7ccc0-166">**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="7ccc0-167">**[新しいプロジェクト]** ダイアログの **[インストール]** プロジェクトの種類ウィンドウでお使いの言語 (C# または Visual Basic) のプロジェクト カテゴリを展開し、 **[.NET Core]** を選択し、中央のウィンドウで **[コンソール アプリケーション (.NET Core)]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="7ccc0-168">**[名前]** テキスト ボックスに、"SCD" などのプロジェクト名を入力し、 **[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="7ccc0-169">アプリケーションのソース コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-169">Add the application's source code.</span></span>

   <span data-ttu-id="7ccc0-170">エディターで *Program.cs* または *Program.vb* ファイルを開き、自動生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="7ccc0-171">テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="7ccc0-172">正規表現 `\w+` を使用して、入力テキストの単語を分離します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. <span data-ttu-id="7ccc0-173">グローバリゼーション インバリアント モードを使用するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="7ccc0-174">特にアプリの対象が Linux の場合、[グローバリゼーション インバリアント モード](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md)を活用することで展開の合計サイズを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).</span></span> <span data-ttu-id="7ccc0-175">グローバリゼーション インバリアント モードは、全世界を意識するものではなく、[インバリアント カルチャ](xref:System.Globalization.CultureInfo.InvariantCulture)の書式設定規則、大文字/小文字の区別規則、文字列比較、並べ替え順序を使用できるアプリケーションにとって便利です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="7ccc0-176">インバリアント モードを有効にするには、**ソリューション エクスプローラー** で (ソリューションではなく) プロジェクトを右クリックし、 **[SCD.csproj の編集]** または **[SCD.vbproj の編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="7ccc0-177">次の強調表示された行をファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](./snippets/deploy-with-vs/xml/invariant.csproj?highlight=7-9)]

1. <span data-ttu-id="7ccc0-178">アプリケーションのデバッグ ビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="7ccc0-179">**[ビルド]**  >  **[ソリューションのビルド]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="7ccc0-180">**[デバッグ]**  >  **[デバッグ開始]** を選択して、アプリケーションのデバッグ ビルドをコンパイルして、実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="7ccc0-181">このデバッグ手順では、ホスト プラットフォームで実行するときのアプリケーションの問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="7ccc0-182">引き続き、それぞれのターゲット プラットフォームでテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="7ccc0-183">グローバリゼーション インバリアント モードを有効にした場合、カルチャ感度の高いデータの欠如が自分のアプリケーションに適しているのかどうかを特にテストしてください。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="7ccc0-184">デバッグが終了したら、自己完結型の展開を発行できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="7ccc0-185">Visual Studio 15.6 以前</span><span class="sxs-lookup"><span data-stu-id="7ccc0-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="7ccc0-186">プログラムをデバッグしてテストしたら、アプリと共に展開するファイルをアプリの対象のプラットフォームごとに作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="7ccc0-187">Visual Studio でアプリを発行するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="7ccc0-188">アプリの対象プラットフォームを定義します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="7ccc0-189">**ソリューション エクスプローラー** で (ソリューションではなく) プロジェクトを右クリックし、 **[Edit SCD.csproj]\(SCD.csproj の編集\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="7ccc0-190">*csproj* ファイルの `<PropertyGroup>` セクションに、アプリの対象のプラットフォームを定義する `<RuntimeIdentifiers>` タグを作成し、対象とするプラットフォームごとにランタイム識別子 (RID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="7ccc0-191">なお、RID を分離するにはセミコロンを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-191">You also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="7ccc0-192">ランタイム識別子の一覧については、[ランタイム識別子のカタログ](../rid-catalog.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-192">See [Runtime identifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="7ccc0-193">たとえば、次の例は、アプリが 64 ビット Windows 10 オペレーティング システムおよび 64 ビット OS X バージョン 10.11 オペレーティング システムで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="7ccc0-194">`<RuntimeIdentifiers>` 要素は、*csproj* ファイルの任意の `<PropertyGroup>` に入れることが可能です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-194">The `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="7ccc0-195">*csproj* ファイルの完全なサンプルは、このセクションの後の部分で示しています。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="7ccc0-196">アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-196">Publish your app.</span></span>

   <span data-ttu-id="7ccc0-197">プログラムをデバッグしてテストしたら、アプリと共に展開するファイルをアプリの対象のプラットフォームごとに作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="7ccc0-198">Visual Studio でアプリを発行するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="7ccc0-199">アプリの (デバッグではなく) リリース バージョンを構築するために、ツールバーでソリューションの構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="7ccc0-200">**ソリューション エクスプローラー** で (ソリューションではなく) プロジェクトを右クリックし、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="7ccc0-201">**[発行]** タブで **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="7ccc0-202">Visual Studio が、アプリケーションを構成するファイルをローカル ファイル システムに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="7ccc0-203">これで **[発行]** タブには、 **[FolderProfile]** という 1 つのプロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="7ccc0-204">プロファイルの構成設定が、タブの **[概要]** セクションに表示されます。 **[Target Runtime]** \(ターゲット ランタイム\) では、発行されたランタイムを識別し、 **[対象の場所]** は自己完結型の展開が書き込まれた場所を識別します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="7ccc0-205">Visual Studio は、発行されたすべてのファイルを、既定で 1 つのディレクトリに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="7ccc0-206">ターゲット ランタイムごとに別のプロファイルを作成し、発行したファイルはプラットフォームごとのディレクトリに配置すると便利なのでお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="7ccc0-207">これを行う場合、対象のプラットフォームごとに別の発行プロファイルも作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="7ccc0-208">ここでは、次の手順でプラットフォームごとにアプリケーションを再構築します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="7ccc0-209">**[発行]** ダイアログで、 **[新しいプロファイルの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="7ccc0-210">**[Pick a publish target]** \(発行する対象の選択)\ ダイアログで **[Choose a folder]** \(フォルダーを選択)\ の場所を *bin\Release\PublishOutput\win10-x64* に変更します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="7ccc0-211">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-211">Select **OK**.</span></span>

         1. <span data-ttu-id="7ccc0-212">新しいプロファイル (**FolderProfile1**) をプロファイルの一覧から選択し、 **[Target Runtime]** \(ターゲット ランタイム\) が `win10-x64` であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="7ccc0-213">違う場合は、 **[設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="7ccc0-214">**[プロファイルの設定]** ダイアログで、 **[Target Runtime]** \(ターゲット ランタイム\) を `win10-x64` に変更して、 **[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="7ccc0-215">それ以外の場合、 **[キャンセル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="7ccc0-216">64 ビットの Windows 10 プラットフォーム用にアプリを発行するために、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="7ccc0-217">前の手順を繰り返して、`osx.10.11-x64` プラットフォームのプロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="7ccc0-218">**[対象の場所]** が *bin\Release\PublishOutput\osx.10.11-x64* で、 **[Target Runtime]** \(ターゲット ランタイム\) は [`osx.10.11-x64`] です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="7ccc0-219">Visual Studio がこのプロファイルに割り当てる名前は、**FolderProfile2** です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="7ccc0-220">それぞれの対象の場所には、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-220">Each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="7ccc0-221">アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="7ccc0-222">このファイルは、主に例外のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="7ccc0-223">これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="7ccc0-224">ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="7ccc0-225">発行したファイルは、任意の方法で展開できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="7ccc0-226">たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="7ccc0-227">このプロジェクトの完全な *csproj* ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="7ccc0-228">Visual Studio 15.7 以降</span><span class="sxs-lookup"><span data-stu-id="7ccc0-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="7ccc0-229">プログラムをデバッグしてテストしたら、アプリと共に展開するファイルをアプリの対象のプラットフォームごとに作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="7ccc0-230">これを行う場合、対象のプラットフォームごとに別のプロファイルも作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="7ccc0-231">アプリケーションの対象となるプラットフォームごとに次を行います。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="7ccc0-232">ターゲット プラットフォーム用のプロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="7ccc0-233">これが自分で作成した最初のプロファイルの場合、**ソリューション エクスプローラー** で (ソリューションではなく) プロジェクトを右クリックし、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="7ccc0-234">プロファイルを既に作成している場合、そのプロファイルを右クリックし、 **[発行]** ダイアログを開きます (まだ開いていない場合)。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="7ccc0-235">**[新しいプロファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="7ccc0-236">**[発行先を選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-236">The **Pick a Publish Target** dialog box opens.</span></span>

1. <span data-ttu-id="7ccc0-237">Visual Studio によってアプリケーションが発行される場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="7ccc0-238">発行先のプラットフォームが 1 つだけの場合、 **[フォルダーを選択してください]** テキスト ボックスで既定値をそのまま選択しても問題ありません。これでアプリケーションのフレームワーク依存展開が *\<project-directory>\bin\Release\netcoreapp2.1\publish* ディレクトリに発行されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="7ccc0-239">発行先のプラットフォームが複数になる場合、ターゲット プラットフォームを識別する文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="7ccc0-240">たとえば、文字列 "linux" をファイル パスに追加する場合、Visual Studio によって、アプリケーションのフレームワーク依存展開が *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* ディレクトリに発行されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="7ccc0-241">**[発行]** ボタンの隣にあるドロップダウン リスト アイコンを選択し、 **[プロファイルの作成]** を選択してプロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="7ccc0-242">次に、 **[プロファイルの作成]** ボタンを選択し、プロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="7ccc0-243">自己完結型の展開を発行することを示し、アプリの対象となるプラットフォームを定義します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="7ccc0-244">**[発行]** ダイアログで **[構成]** リンクを選択し、 **[プロファイル設定]** ダイアログを開きます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="7ccc0-245">**[配置モード]** リスト ボックスで **[自己完結]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="7ccc0-246">**[ターゲット ランタイム]** リスト ボックスで、アプリケーションのターゲットとなるプラットフォームを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="7ccc0-247">**[保存]** を選択して変更を適用し、ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="7ccc0-248">プロファイルに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-248">Name your profile.</span></span>

   1. <span data-ttu-id="7ccc0-249">**[アクション]**  >  **[プロファイル名の変更]** の順に選択し、プロファイルに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="7ccc0-250">ターゲット プラットフォームを識別する名前をプロファイルに割り当て、\* *[保存]* を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="7ccc0-251">以上の手順を繰り返し、アプリケーションの対象となる追加ターゲット プラットフォームを定義します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="7ccc0-252">これでプロファイルが構成されたので、アプリを発行できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="7ccc0-253">この操作を行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-253">To do this:</span></span>

   1. <span data-ttu-id="7ccc0-254">この時点で **[発行]** ウィンドウが開いていない場合、**ソリューション エクスプローラー** で (ソリューションではなく) プロジェクトを右クリックし、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="7ccc0-255">発行するプロファイルを選択し、 **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="7ccc0-256">発行するプロファイルごとにこれを行います。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="7ccc0-257">それぞれの対象の場所 (今回の例では、bin\release\netcoreapp2.1\publish\\*profile-name*) には、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-257">Each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="7ccc0-258">アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="7ccc0-259">このファイルは、主に例外のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="7ccc0-260">これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="7ccc0-261">ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="7ccc0-262">発行したファイルは、任意の方法で展開できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="7ccc0-263">たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="7ccc0-264">このプロジェクトの完全な *csproj* ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="7ccc0-265">また、Visual Studio によって、対象とするプラットフォームごとに別個の発行プロファイル (\*.pubxml) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="7ccc0-266">たとえば、linux プロファイルのファイル (linux.pubxml) は次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121.
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="7ccc0-267">サードパーティの依存関係を含む、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="7ccc0-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="7ccc0-268">1 つまたは複数のサードパーティの依存関係を含む自己完結型の展開を展開するプロセスには、依存関係の追加が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="7ccc0-269">アプリをビルドする前に、次の追加手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="7ccc0-270">**NuGet パッケージ マネージャー** を使用し、プロジェクトに NuGet パッケージへの参照を追加します。このとき、パッケージがシステムにまだない場合はそれをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="7ccc0-271">パッケージ マネージャーを開くには、 **[ツール]**  >  **[NuGet パッケージ マネージャー]**  >  **[ソリューションの NuGet パッケージの管理]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="7ccc0-272">サードパーティの依存関係 (`Newtonsoft.Json` など) がシステムにインストールされていることを確認し、インストールされていない場合はインストールします。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="7ccc0-273">**[インストール済み]** タブに、システムにインストールされた NuGet パッケージの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="7ccc0-274">`Newtonsoft.Json` がそこにない場合、 **[参照]** タブを選択し、検索ボックスに "Newtonsoft.Json" と入力します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="7ccc0-275">`Newtonsoft.Json` を選択し、右側のウィンドウでプロジェクトを選択してから、 **[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="7ccc0-276">`Newtonsoft.Json` が既にシステムにインストールされている場合、 **[ソリューション パッケージの管理]** タブの右のウィンドウからプロジェクトを選択し、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="7ccc0-277">このプロジェクトの完全な *csproj* ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="7ccc0-278">Visual Studio 15.6 以前</span><span class="sxs-lookup"><span data-stu-id="7ccc0-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="7ccc0-279">Visual Studio 15.7 以降</span><span class="sxs-lookup"><span data-stu-id="7ccc0-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="7ccc0-280">アプリケーションを展開すると、アプリで使用されるすべてのサードパーティの依存関係も、アプリケーション ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="7ccc0-281">アプリが実行されているシステムには、サードパーティ ライブラリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="7ccc0-282">サードパーティ ライブラリを含む自己完結型の展開は、そのライブラリでサポートされるプラットフォームにのみ展開できます。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-282">You can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="7ccc0-283">これは、フレームワークに依存する展開にサード パーティの依存関係とネイティブの依存関係があり、ネイティブの依存関係は前にインストールしていた場合を除き、対象のプラットフォームにない場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="7ccc0-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ccc0-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ccc0-284">See also</span></span>

- [<span data-ttu-id="7ccc0-285">.NET Core アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="7ccc0-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="7ccc0-286">.NET Core ランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="7ccc0-286">.NET Core Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
