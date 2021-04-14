---
title: 移行するプロジェクトの順序を確認する
description: 通常、大規模なアプリは新しいプラットフォームにすべて一度に移行されるのではなく、一連の小規模なステップに分けて移行されます。 ASP.NET MVC アプリを ASP.NET Core に移行するためのステップを計画する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 452898da5839f8979a5e4f9ebf5d4c21b250e1fa
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401379"
---
# <a name="identify-sequence-of-projects-to-migrate"></a><span data-ttu-id="6eeff-104">移行するプロジェクトの順序を確認する</span><span class="sxs-lookup"><span data-stu-id="6eeff-104">Identify sequence of projects to migrate</span></span>

<span data-ttu-id="6eeff-105">複数のフロントエンド アプリを含むソリューションでは、アプリを 1 つずつ移行するのが最善の方法です。</span><span class="sxs-lookup"><span data-stu-id="6eeff-105">For solutions that involve multiple front-end apps, it's best to migrate the apps one by one.</span></span> <span data-ttu-id="6eeff-106">たとえば、1 つのフロントエンド アプリとその依存関係のみを含むソリューションを作成して、必要な作業のスコープを簡単に特定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6eeff-106">For example, create a solution that only includes one front-end app and its dependencies so you can easily identify the scope of work involved.</span></span> <span data-ttu-id="6eeff-107">ソリューションは軽量であり、必要に応じて複数のソリューション内にプロジェクトを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-107">Solutions are lightweight, and you can include projects in multiple solutions if needed.</span></span> <span data-ttu-id="6eeff-108">移行時には、ソリューションを整理ツールとして活用できます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-108">Take advantage of solutions as an organizational tool when migrating.</span></span>

<span data-ttu-id="6eeff-109">移行する ASP.NET アプリを特定し、それに依存するプロジェクトを (理想的には 1 つのソリューション内に) 一緒に配置したら、次のステップとしてフレームワークと NuGet の依存関係を特定します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-109">Once you've identified the ASP.NET app to migrate and have its dependent projects located with it (ideally in a solution), the next step is to identify framework and NuGet dependencies.</span></span> <span data-ttu-id="6eeff-110">すべての依存関係を特定したら、最もシンプルな移行のアプローチは "ボトムアップ" アプローチです。</span><span class="sxs-lookup"><span data-stu-id="6eeff-110">Having identified all dependencies, the simplest migration approach is a "bottom up" approach.</span></span> <span data-ttu-id="6eeff-111">このアプローチでは、最下位レベルの依存関係を最初に移行します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-111">With this approach, the lowest level of dependencies is migrated first.</span></span> <span data-ttu-id="6eeff-112">その後、最終的にフロントエンド アプリのみが残るまで、次のレベルの依存関係を移行していきます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-112">Then the next level of dependencies is migrated, until eventually the only thing left is the front-end app.</span></span> <span data-ttu-id="6eeff-113">図 3-1 に、1 つのアプリを構成するプロジェクトのセットの例を示します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-113">Figure 3-1 shows an example set of projects composing an app.</span></span> <span data-ttu-id="6eeff-114">下位レベルのクラス ライブラリが一番下に、ASP.NET MVC プロジェクトが一番上にあります。</span><span class="sxs-lookup"><span data-stu-id="6eeff-114">The low-level class libraries are at the bottom, and the ASP.NET MVC project is at the top.</span></span>

![プロジェクト依存関係](./media/Figure3-1.png)

<span data-ttu-id="6eeff-116">**図 3-1.**</span><span class="sxs-lookup"><span data-stu-id="6eeff-116">**Figure 3-1.**</span></span> <span data-ttu-id="6eeff-117">プロジェクトの依存関係のグラフ。</span><span class="sxs-lookup"><span data-stu-id="6eeff-117">Project dependencies graph.</span></span>

<span data-ttu-id="6eeff-118">1 つの特定のフロントエンド アプリ、1 つの ASP.NET MVC 5 / Web API 2 プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-118">Choose a particular front-end app, an ASP.NET MVC 5 / Web API 2 project.</span></span> <span data-ttu-id="6eeff-119">ソリューション内でその依存関係を特定し、完全な一覧ができるまでその依存関係をマップに書き出します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-119">Identify its dependencies in the solution, and map out their dependencies until you have a complete list.</span></span> <span data-ttu-id="6eeff-120">図 3-1 に示したような図が、プロジェクトの依存関係をマップに書き出すときに役立つでしょう。</span><span class="sxs-lookup"><span data-stu-id="6eeff-120">A diagram like the one shown in Figure 3-1 may be useful when mapping out project dependencies.</span></span> <span data-ttu-id="6eeff-121">Visual Studio では、ご使用のエディションに応じて[ソリューションの依存関係図](/visualstudio/modeling/create-layer-diagrams-from-your-code)を生成できます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-121">Visual Studio can produce a [dependency diagram for your solution](/visualstudio/modeling/create-layer-diagrams-from-your-code), depending on which edition you're using.</span></span> <span data-ttu-id="6eeff-122">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) でも、依存関係図を生成できます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-122">[The .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) can also produce dependency diagrams.</span></span>

<span data-ttu-id="6eeff-123">図 3-2 は、[.NET Portability Analyzer の Visual Studio 拡張機能](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)のインストーラを示しています。</span><span class="sxs-lookup"><span data-stu-id="6eeff-123">Figure 3-2 shows the installer for the [.NET Portability Analyzer Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer):</span></span>

![.NET Portability Analyzer の拡張機能のインストール](./media/Figure3-2.png)

<span data-ttu-id="6eeff-125">**図 3-2**</span><span class="sxs-lookup"><span data-stu-id="6eeff-125">**Figure 3-2.**</span></span> <span data-ttu-id="6eeff-126">.NET Portability Analyzer のインストーラ。</span><span class="sxs-lookup"><span data-stu-id="6eeff-126">.NET Portability Analyzer installer.</span></span>

<span data-ttu-id="6eeff-127">この拡張機能では、Visual Studio 2017 以降がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6eeff-127">The extension supports Visual Studio 2017 and later.</span></span> <span data-ttu-id="6eeff-128">インストールしたら、図 3-3 に示すように **[分析]**  >  **[Portability Analyzer Settings]\(Portability Analyzer の設定\)** メニューからそれを構成します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-128">Once installed, you configure it from the **Analyze** > **Portability Analyzer Settings** menu, as shown in Figure 3-3.</span></span>

![.NET Portability Analyzer の拡張機能の構成](./media/Figure3-3.png)

<span data-ttu-id="6eeff-130">**図 3-3**</span><span class="sxs-lookup"><span data-stu-id="6eeff-130">**Figure 3-3.**</span></span> <span data-ttu-id="6eeff-131">.NET Portability Analyzer の構成。</span><span class="sxs-lookup"><span data-stu-id="6eeff-131">Configure the .NET Portability Analyzer.</span></span>

<span data-ttu-id="6eeff-132">アナライザーにより、各アセンブリに関する詳細なレポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-132">The analyzer produces a detailed report for each assembly.</span></span> <span data-ttu-id="6eeff-133">このレポートは、</span><span class="sxs-lookup"><span data-stu-id="6eeff-133">The report:</span></span>

* <span data-ttu-id="6eeff-134">各プロジェクトと特定のターゲット フレームワーク (.NET Core 3.1 や .NET Standard 2.0 など) の互換性の状況を示します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-134">Describes how compatible each project is with a given target framework, such as .NET Core 3.1 or .NET Standard 2.0.</span></span>
* <span data-ttu-id="6eeff-135">特定のプロジェクトを特定のターゲット フレームワークに移植するために必要な作業量をチームが評価するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-135">Helps teams assess the effort required to port a particular project to a particular target framework.</span></span>

<span data-ttu-id="6eeff-136">この分析の詳細については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-136">The details of this analysis are covered in the next section.</span></span>

<span data-ttu-id="6eeff-137">プロジェクトとそれらの相互関係をマップに書き出したら、プロジェクトを移行する順序を決定できます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-137">Once you've mapped out the projects and their relationships with one another, you're ready to determine the order in which you'll migrate the projects.</span></span> <span data-ttu-id="6eeff-138">最初は、依存関係のないプロジェクトから始めます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-138">Begin with projects that have no dependencies.</span></span> <span data-ttu-id="6eeff-139">その後は、それらのプロジェクトに依存するプロジェクトへと、ツリーの上に向かって作業を進めます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-139">Then, work your way up the tree to the projects that depend on these projects.</span></span>

<span data-ttu-id="6eeff-140">図 3-1 に示した例では、*Contoso.Utils* プロジェクトから始めます。これは他のプロジェクトに依存していないからです。</span><span class="sxs-lookup"><span data-stu-id="6eeff-140">In the example shown in Figure 3-1, you would start with the *Contoso.Utils* project, since it doesn't depend on any other projects.</span></span> <span data-ttu-id="6eeff-141">次は *Contoso.Data* です。これは "Utils" にのみ依存しているからです。</span><span class="sxs-lookup"><span data-stu-id="6eeff-141">Next, *Contoso.Data* since it only depends on "Utils".</span></span> <span data-ttu-id="6eeff-142">続いて "BusinessLogic" ライブラリを移行し、最後にフロントエンドの ASP.NET "Web" プロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-142">Then migrate the "BusinessLogic" library, and finally the front-end ASP.NET "Web" project.</span></span> <span data-ttu-id="6eeff-143">この "ボトムアップ" アプローチは、すべてのプロジェクトの移行を完了すれば 1 つのユニットとして移行できる、比較的小規模で整然としたアプリに適しています。</span><span class="sxs-lookup"><span data-stu-id="6eeff-143">Following this "bottom up" approach works well for relatively small and well-factored apps that can be migrated as a unit once all of their projects have migrated.</span></span> <span data-ttu-id="6eeff-144">より複雑な、またはコードの量が多い大規模なアプリは移行にもっと時間がかかる可能性があり、より段階的な戦略を検討することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="6eeff-144">Larger apps with more complexity, or more code that will take longer to migrate, may need to consider more incremental strategies.</span></span>

## <a name="unit-tests"></a><span data-ttu-id="6eeff-145">単体テスト</span><span class="sxs-lookup"><span data-stu-id="6eeff-145">Unit tests</span></span>

<span data-ttu-id="6eeff-146">前の図には、単体テスト プロジェクトがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="6eeff-146">Missing from the previous diagrams are unit test projects.</span></span> <span data-ttu-id="6eeff-147">おそらくは、少なくとも、移植されるライブラリの既存の動作のいくつかを対象としたテストが存在するでしょう。</span><span class="sxs-lookup"><span data-stu-id="6eeff-147">Hopefully there are tests covering at least some of the existing behavior of the libraries being ported.</span></span>

<span data-ttu-id="6eeff-148">単体テストがある場合は、それらのプロジェクトを最初に変換するのが最善です。</span><span class="sxs-lookup"><span data-stu-id="6eeff-148">If you have unit tests, it's best to convert those projects first.</span></span> <span data-ttu-id="6eeff-149">今後も作業中のプロジェクトでの変更をテストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6eeff-149">You'll want to continue testing changes in the project you're working on.</span></span> <span data-ttu-id="6eeff-150">.NET Core への移植では、コードベースに大きな変更が加えられるという点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6eeff-150">Remember that porting to .NET Core is a significant change to your codebase.</span></span>

<span data-ttu-id="6eeff-151">MSTest、xUnit、NUnit はすべて .NET Core で動作します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-151">MSTest, xUnit, and NUnit all work on .NET Core.</span></span> <span data-ttu-id="6eeff-152">現在、アプリ用のテストがない場合は、システムの現在の動作を検証するいくつかの特性テストを構築することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6eeff-152">If you don't currently have tests for your app, consider building some characterization tests that verify the system's current behavior.</span></span> <span data-ttu-id="6eeff-153">その利点は、移行の完了後に、アプリの動作が変わっていないことを確認できることです。</span><span class="sxs-lookup"><span data-stu-id="6eeff-153">The benefit is that once the migration is complete, you can confirm the app's behavior remains unchanged.</span></span>

## <a name="considerations-for-migrating-many-apps"></a><span data-ttu-id="6eeff-154">多数のアプリの移行に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="6eeff-154">Considerations for migrating many apps</span></span>

<span data-ttu-id="6eeff-155">組織によっては、移行するアプリの数が多く、1 つずつ手作業で移行するのは必要なリソースが多すぎて不可能な場合があります。</span><span class="sxs-lookup"><span data-stu-id="6eeff-155">Some organizations will have many different apps to migrate, and migrating each one by hand may require too many resources to be tenable.</span></span> <span data-ttu-id="6eeff-156">そのような状況では、ある程度の自動化をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6eeff-156">In these situations, some degree of automation is recommended.</span></span> <span data-ttu-id="6eeff-157">この章で示した手順は自動化が可能です。</span><span class="sxs-lookup"><span data-stu-id="6eeff-157">The steps followed in this chapter can be automated.</span></span> <span data-ttu-id="6eeff-158">プロジェクト ファイルの違いや共通パッケージの更新などの構造的な変更は、スクリプトによって適用することができます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-158">Structural changes, like project file differences and updates to common packages, can be applied by scripts.</span></span> <span data-ttu-id="6eeff-159">これらのスクリプトは、より多くのプロジェクトで繰り返し実行する間に改善できます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-159">These scripts can be refined as they're run iteratively on more projects.</span></span> <span data-ttu-id="6eeff-160">実行のたびに、各プロジェクトでどのような手動のステップが必要かを確認します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-160">On each run, examine whatever manual steps are required for each project.</span></span> <span data-ttu-id="6eeff-161">それらの手動のステップを可能な限り自動化します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-161">Automate those manual steps, if possible.</span></span> <span data-ttu-id="6eeff-162">このアプローチを使用すると、組織は時間の経過と共にアプリの移行をより迅速かつ効率的に行えるようになり、各ステップで自動化のサポートが強化されます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-162">Using this approach, the organization should grow faster and better at porting their apps over time, with improved automation support each step of the way.</span></span>

<span data-ttu-id="6eeff-163">このアプローチの使用方法の概要を、[Mastercard の Lizzy Gallagher による dotNetConf のプレゼンテーション](https://www.youtube.com/watch?v=C-2haqb60No)でご覧いただけます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-163">Watch an overview of how to employ this approach in this [dotNetConf presentation by Lizzy Gallagher of Mastercard](https://www.youtube.com/watch?v=C-2haqb60No).</span></span> <span data-ttu-id="6eeff-164">このプレゼンテーションでは、次の 5 つのフェーズが使用されています。</span><span class="sxs-lookup"><span data-stu-id="6eeff-164">The five phases employed in this presentation included:</span></span>

- <span data-ttu-id="6eeff-165">サードパーティの NuGet の依存関係を移行する</span><span class="sxs-lookup"><span data-stu-id="6eeff-165">Migrate third-party NuGet dependencies</span></span>
- <span data-ttu-id="6eeff-166">新しい *.csproj* ファイル形式を使用するようにアプリを移行する</span><span class="sxs-lookup"><span data-stu-id="6eeff-166">Migrate apps to use new *.csproj* file format</span></span>
- <span data-ttu-id="6eeff-167">(.NET Framework をターゲットとする) ASP.NET Core にアプリを移行する</span><span class="sxs-lookup"><span data-stu-id="6eeff-167">Migrate apps to ASP.NET Core (targeting .NET Framework)</span></span>
- <span data-ttu-id="6eeff-168">内部の NuGet 依存関係を .NET Standard に更新する</span><span class="sxs-lookup"><span data-stu-id="6eeff-168">Update internal NuGet dependencies to .NET Standard</span></span>
- <span data-ttu-id="6eeff-169">すべてのアプリを .NET Core 3.1 をターゲットにするように更新する</span><span class="sxs-lookup"><span data-stu-id="6eeff-169">Update all apps to target .NET Core 3.1</span></span>

<span data-ttu-id="6eeff-170">大規模なアプリのスイートを自動化するときは、それらが一貫したコーディング ガイドラインとプロジェクト編成に従っていると非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-170">When automating a large suite of apps, it helps significantly if they follow consistent coding guidelines and project organization.</span></span> <span data-ttu-id="6eeff-171">自動化の作業を効率化できるかどうかは、この一貫性にかかっています。</span><span class="sxs-lookup"><span data-stu-id="6eeff-171">Automation efforts rely on this consistency to be effective.</span></span> <span data-ttu-id="6eeff-172">プロジェクト ファイルの解析と移行に加えて、一般的なコード パターンも自動的に移行できます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-172">In addition to parsing and migrating project files, common code patterns can be migrated automatically.</span></span> <span data-ttu-id="6eeff-173">一部のコード パターンの例では、コントローラー アクションの宣言方法やそれらが結果を返す方法に違いがあります。</span><span class="sxs-lookup"><span data-stu-id="6eeff-173">Some code pattern examples include differences in how controller actions are declared or how they return results.</span></span>

<span data-ttu-id="6eeff-174">たとえば、移行スクリプトで、*Controller.cs* に一致するファイルで次のいずれかのパターンに一致するコードの行を検索するとします。</span><span class="sxs-lookup"><span data-stu-id="6eeff-174">For example, a migration script could search files matching *Controller.cs* for lines of code matching one of these patterns:</span></span>

```csharp
   return new HttpStatusCodeResult(200);
   // or
   return new HttpStatusCodeResult(HttpStatusCode.OK);
```

<span data-ttu-id="6eeff-175">ASP.NET Core では、上記の行のどちらも以下で置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-175">In ASP.NET Core, either of the preceding lines of code can be replaced with:</span></span>

```csharp
    return Ok();
```

## <a name="summary"></a><span data-ttu-id="6eeff-176">まとめ</span><span class="sxs-lookup"><span data-stu-id="6eeff-176">Summary</span></span>

<span data-ttu-id="6eeff-177">大規模な .NET Framework アプリを .NET Core に移行するための最善のアプローチは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6eeff-177">The best approach to porting a large .NET Framework app to .NET Core is to:</span></span>

1. <span data-ttu-id="6eeff-178">プロジェクトの依存関係を特定します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-178">Identify project dependencies.</span></span>
1. <span data-ttu-id="6eeff-179">各プロジェクトを移植するために何が必要かを分析します。</span><span class="sxs-lookup"><span data-stu-id="6eeff-179">Analyze what's required to port each project.</span></span>
1. <span data-ttu-id="6eeff-180">下から始めて、上方向へと進めます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-180">Start from the bottom up.</span></span>

<span data-ttu-id="6eeff-181">.NET Portability Analyzer を使用して、既存のライブラリとターゲット プラットフォームの互換性の状況を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-181">You can use the .NET Portability Analyzer to determine how compatible existing libraries may be with target platforms.</span></span> <span data-ttu-id="6eeff-182">自動テストを使用すると、アプリの移植時に破壊的変更が行われていないことを確認するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6eeff-182">Automated tests will help ensure no breaking changes are introduced as the app is ported.</span></span> <span data-ttu-id="6eeff-183">このようなテスト プロジェクトは、最初に移植すべきプロジェクトの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6eeff-183">These test projects should be among the first projects ported.</span></span>

## <a name="references"></a><span data-ttu-id="6eeff-184">リファレンス</span><span class="sxs-lookup"><span data-stu-id="6eeff-184">References</span></span>

- [<span data-ttu-id="6eeff-185">.NET Framework から .NET Core への移植</span><span class="sxs-lookup"><span data-stu-id="6eeff-185">Porting from .NET Framework to .NET Core</span></span>](../../core/porting/index.md)
- [<span data-ttu-id="6eeff-186">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="6eeff-186">The .NET Portability Analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
- [<span data-ttu-id="6eeff-187">Channel 9: .NET Portability Analyzer の概要 (動画)</span><span class="sxs-lookup"><span data-stu-id="6eeff-187">Channel 9: A Brief Look at the .NET Portability Analyzer (Video)</span></span>](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer)
- [<span data-ttu-id="6eeff-188">2 年間で 200 のアプリ: .NET Core への大規模な移行 (動画)</span><span class="sxs-lookup"><span data-stu-id="6eeff-188">2 Years, 200 Apps: A .NET Core Migration at Scale (Video)</span></span>](https://www.youtube.com/watch?v=C-2haqb60No)

>[!div class="step-by-step"]
><span data-ttu-id="6eeff-189">[前へ](migrate-large-solutions.md)
>[次へ](understand-update-dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="6eeff-189">[Previous](migrate-large-solutions.md)
[Next](understand-update-dependencies.md)</span></span>
