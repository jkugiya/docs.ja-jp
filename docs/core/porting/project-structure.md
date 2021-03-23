---
title: .NET Framework および .NET Core のプロジェクトを整理する
description: プロジェクト所有者が横並びの .NET Framework と .NET Core に対してソリューションをコンパイルするときに役立ちます。
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: 0d495ce7b21b45d3fabe444f117667e5908ac81a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873667"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="e429f-103">.NET Framework と .NET Core の両方をサポートするようにプロジェクトを整理する</span><span class="sxs-lookup"><span data-stu-id="e429f-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="e429f-104">.NET Framework と .NET Core 両方のコンパイルに同時に対応するソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e429f-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="e429f-105">この記事では、この目標を達成するために役立つ、いくつかのプロジェクトの整理のオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e429f-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="e429f-106">ここでは、.NET Core でプロジェクト レイアウトを設定する方法について決定するときに考慮する典型的なシナリオを紹介します。</span><span class="sxs-lookup"><span data-stu-id="e429f-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="e429f-107">この一覧はプロジェクトのニーズに基づいて選択されており、すべてを網羅しるわけではりません。</span><span class="sxs-lookup"><span data-stu-id="e429f-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="e429f-108">**既存のプロジェクトと .NET Core プロジェクトを結合し、シングル プロジェクトを作成する**</span><span class="sxs-lookup"><span data-stu-id="e429f-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="e429f-109">*効果:*</span><span class="sxs-lookup"><span data-stu-id="e429f-109">*What this is good for:*</span></span>
  - <span data-ttu-id="e429f-110">複数のプロジェクトではなくシングル プロジェクトをコンパイルすることで、ビルド プロセスをシンプルにします。それぞれ、異なる .NET Framework バージョンまたはプラットフォームをターゲットにします。</span><span class="sxs-lookup"><span data-stu-id="e429f-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="e429f-111">ターゲットが複数のプロジェクトのソース ファイル管理をシンプルにします。シングル プロジェクト ファイルを管理することになります。</span><span class="sxs-lookup"><span data-stu-id="e429f-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="e429f-112">ソース ファイルの追加または削除時に、代替方法では、これらを他のプロジェクトと手動で同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e429f-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="e429f-113">使用する NuGet パッケージを簡単に生成します。</span><span class="sxs-lookup"><span data-stu-id="e429f-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="e429f-114">コンパイラ ディレクティブを利用することで、ライブラリの特定の .NET Framework バージョンに対してコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="e429f-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="e429f-115">*サポートされていないシナリオ:*</span><span class="sxs-lookup"><span data-stu-id="e429f-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="e429f-116">既存のプロジェクトを開くには、開発者が Visual Studio 2017 以降を使用している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e429f-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="e429f-117">旧バージョンの Visual Studio をサポートするには、[プロジェクト ファイルを異なるフォルダーで保持する](#support-vs)ことが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="e429f-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="e429f-118">[**既存のプロジェクトと新しい .NET Core プロジェクトを別々に保存する**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="e429f-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="e429f-119">*効果:*</span><span class="sxs-lookup"><span data-stu-id="e429f-119">*What this is good for:*</span></span>
  - <span data-ttu-id="e429f-120">Visual Studio 2017 以降を持っていない場合がある開発者と共同作成者に対して、既存のプロジェクトの開発をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e429f-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="e429f-121">既存のプロジェクトで新しいバグが発生する可能性が減ります。既存のプロジェクトではコード チャーンが要求されないためです。</span><span class="sxs-lookup"><span data-stu-id="e429f-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="e429f-122">例</span><span class="sxs-lookup"><span data-stu-id="e429f-122">Example</span></span>

<span data-ttu-id="e429f-123">次のリポジトリを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="e429f-123">Consider the repository below:</span></span>

![既存のプロジェクト](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="e429f-125">**ソース コード**</span><span class="sxs-lookup"><span data-stu-id="e429f-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library/)

<span data-ttu-id="e429f-126">下に説明する既存のプロジェクトの制約や複雑性にもよりますが、このリポジトリのために .NET Core のサポートを追加する方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e429f-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="e429f-127">既存のプロジェクトとターゲットが複数ある .NET Core Project を置換します</span><span class="sxs-lookup"><span data-stu-id="e429f-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="e429f-128">リポジトリを再整理できます。既存の *\*.csproj* ファイルが削除され、複数のフレームワークをターゲットにするシングル *\*.csproj* ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e429f-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="e429f-129">異なるフレームワークに対してシングル プロジェクトでコンパイルできるので、この方法が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="e429f-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="e429f-130">さまざまなコンパイル オプション、ターゲットにするフレームワークごとの依存関係などを処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="e429f-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![複数のフレームワークをターゲットにする csproj の作成](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="e429f-132">**ソース コード**</span><span class="sxs-lookup"><span data-stu-id="e429f-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="e429f-133">注目するべき変更点:</span><span class="sxs-lookup"><span data-stu-id="e429f-133">Changes to note are:</span></span>

- <span data-ttu-id="e429f-134">*packages.config* と *\*.csproj* が新しい [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/src/Car/Car.csproj) に置き換わりました。</span><span class="sxs-lookup"><span data-stu-id="e429f-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="e429f-135">NuGet パッケージが `<PackageReference> ItemGroup` で指定されています。</span><span class="sxs-lookup"><span data-stu-id="e429f-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="e429f-136">既存のプロジェクトを保持し、.NET Core プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="e429f-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="e429f-137">古いフレームワークをターゲットにする既存のプロジェクトがあるとき、そのようなプロジェクトをそのまま残し、.NET Core プロジェクトを利用して今後のフレームワークをターゲットにすると効率的な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e429f-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![別のフォルダーに既存のプロジェクトがある .NET Core プロジェクト](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="e429f-139">**ソース コード**</span><span class="sxs-lookup"><span data-stu-id="e429f-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="e429f-140">.NET Core と既存のプロジェクトを別々のフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="e429f-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="e429f-141">プロジェクトを別々のフォルダーに保存すれば、Visual Studio 2017 以降のバージョンを所有する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="e429f-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="e429f-142">古いプロジェクトだけを開く別個のソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e429f-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="e429f-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="e429f-143">See also</span></span>

- [<span data-ttu-id="e429f-144">.NET Core の移植に関するドキュメント</span><span class="sxs-lookup"><span data-stu-id="e429f-144">.NET Core porting documentation</span></span>](index.md)
