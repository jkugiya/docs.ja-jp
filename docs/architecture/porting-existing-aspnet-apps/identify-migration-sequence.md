---
title: 移行するプロジェクトの順序を確認する
description: 通常、大規模なアプリは、一度に新しいプラットフォームに移行されることはありませんが、一連の小さな手順で実行されます。 ASP.NET MVC アプリを ASP.NET Core に移行するための手順を計画する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 452898da5839f8979a5e4f9ebf5d4c21b250e1fa
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401379"
---
# <a name="identify-sequence-of-projects-to-migrate"></a><span data-ttu-id="7e24f-104">移行するプロジェクトの順序を確認する</span><span class="sxs-lookup"><span data-stu-id="7e24f-104">Identify sequence of projects to migrate</span></span>

<span data-ttu-id="7e24f-105">複数のフロントエンドアプリに関連するソリューションの場合は、アプリを1つずつ移行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e24f-105">For solutions that involve multiple front-end apps, it's best to migrate the apps one by one.</span></span> <span data-ttu-id="7e24f-106">たとえば、1つのフロントエンドアプリとその依存関係のみを含むソリューションを作成し、関連する作業の範囲を簡単に識別できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7e24f-106">For example, create a solution that only includes one front-end app and its dependencies so you can easily identify the scope of work involved.</span></span> <span data-ttu-id="7e24f-107">ソリューションは軽量であり、必要に応じて複数のソリューションにプロジェクトを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-107">Solutions are lightweight, and you can include projects in multiple solutions if needed.</span></span> <span data-ttu-id="7e24f-108">移行時には、ソリューションを組織のツールとして活用できます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-108">Take advantage of solutions as an organizational tool when migrating.</span></span>

<span data-ttu-id="7e24f-109">移行する ASP.NET アプリを特定し、それに依存するプロジェクトがあることを確認したら (理想的にはソリューションで)、次の手順として、フレームワークと NuGet の依存関係を識別します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-109">Once you've identified the ASP.NET app to migrate and have its dependent projects located with it (ideally in a solution), the next step is to identify framework and NuGet dependencies.</span></span> <span data-ttu-id="7e24f-110">すべての依存関係を特定することで、最も簡単な移行方法は "ボトムアップ" アプローチです。</span><span class="sxs-lookup"><span data-stu-id="7e24f-110">Having identified all dependencies, the simplest migration approach is a "bottom up" approach.</span></span> <span data-ttu-id="7e24f-111">この方法では、最も低いレベルの依存関係が最初に移行されます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-111">With this approach, the lowest level of dependencies is migrated first.</span></span> <span data-ttu-id="7e24f-112">次のレベルの依存関係は、最終的にはフロントエンドアプリだけに移行されます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-112">Then the next level of dependencies is migrated, until eventually the only thing left is the front-end app.</span></span> <span data-ttu-id="7e24f-113">図3-1 は、アプリを作成するプロジェクトのセットの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="7e24f-113">Figure 3-1 shows an example set of projects composing an app.</span></span> <span data-ttu-id="7e24f-114">下位レベルのクラスライブラリは一番下にあり、ASP.NET MVC プロジェクトは一番上にあります。</span><span class="sxs-lookup"><span data-stu-id="7e24f-114">The low-level class libraries are at the bottom, and the ASP.NET MVC project is at the top.</span></span>

![プロジェクト依存関係](./media/Figure3-1.png)

<span data-ttu-id="7e24f-116">**図 3-1.**</span><span class="sxs-lookup"><span data-stu-id="7e24f-116">**Figure 3-1.**</span></span> <span data-ttu-id="7e24f-117">プロジェクトの依存関係グラフ。</span><span class="sxs-lookup"><span data-stu-id="7e24f-117">Project dependencies graph.</span></span>

<span data-ttu-id="7e24f-118">特定のフロントエンドアプリ、ASP.NET MVC 5/Web API 2 プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-118">Choose a particular front-end app, an ASP.NET MVC 5 / Web API 2 project.</span></span> <span data-ttu-id="7e24f-119">ソリューション内の依存関係を特定し、完全な一覧が表示されるまで依存関係をマッピングします。</span><span class="sxs-lookup"><span data-stu-id="7e24f-119">Identify its dependencies in the solution, and map out their dependencies until you have a complete list.</span></span> <span data-ttu-id="7e24f-120">図3-1 に示すような図は、プロジェクトの依存関係をマップするときに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e24f-120">A diagram like the one shown in Figure 3-1 may be useful when mapping out project dependencies.</span></span> <span data-ttu-id="7e24f-121">Visual Studio では、使用しているエディションに応じて、 [ソリューションの依存関係図](/visualstudio/modeling/create-layer-diagrams-from-your-code)を生成できます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-121">Visual Studio can produce a [dependency diagram for your solution](/visualstudio/modeling/create-layer-diagrams-from-your-code), depending on which edition you're using.</span></span> <span data-ttu-id="7e24f-122">[.Net 移植性アナライザーは、](../../standard/analyzers/portability-analyzer.md) 依存関係図を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-122">[The .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) can also produce dependency diagrams.</span></span>

<span data-ttu-id="7e24f-123">図3-2 は、 [.Net 移植性アナライザーの Visual Studio 拡張機能](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)のインストーラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="7e24f-123">Figure 3-2 shows the installer for the [.NET Portability Analyzer Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer):</span></span>

![.NET 移植性アナライザー拡張機能のインストール](./media/Figure3-2.png)

<span data-ttu-id="7e24f-125">**図 3-2.**</span><span class="sxs-lookup"><span data-stu-id="7e24f-125">**Figure 3-2.**</span></span> <span data-ttu-id="7e24f-126">.NET 移植性アナライザーのインストーラー。</span><span class="sxs-lookup"><span data-stu-id="7e24f-126">.NET Portability Analyzer installer.</span></span>

<span data-ttu-id="7e24f-127">拡張機能は、Visual Studio 2017 以降をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7e24f-127">The extension supports Visual Studio 2017 and later.</span></span> <span data-ttu-id="7e24f-128">インストールが完了したら、   >  図3-3 に示すように、[**移植性アナライザーの設定** の分析] メニューから構成します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-128">Once installed, you configure it from the **Analyze** > **Portability Analyzer Settings** menu, as shown in Figure 3-3.</span></span>

![.NET 移植性アナライザー拡張機能を構成する](./media/Figure3-3.png)

<span data-ttu-id="7e24f-130">**図 3-3.**</span><span class="sxs-lookup"><span data-stu-id="7e24f-130">**Figure 3-3.**</span></span> <span data-ttu-id="7e24f-131">.NET 移植性アナライザーを構成します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-131">Configure the .NET Portability Analyzer.</span></span>

<span data-ttu-id="7e24f-132">アナライザーによって、各アセンブリの詳細なレポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-132">The analyzer produces a detailed report for each assembly.</span></span> <span data-ttu-id="7e24f-133">レポート:</span><span class="sxs-lookup"><span data-stu-id="7e24f-133">The report:</span></span>

* <span data-ttu-id="7e24f-134">各プロジェクトが特定のターゲットフレームワーク (.NET Core 3.1 や .NET Standard 2.0 など) とどのように互換性があるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-134">Describes how compatible each project is with a given target framework, such as .NET Core 3.1 or .NET Standard 2.0.</span></span>
* <span data-ttu-id="7e24f-135">特定のプロジェクトを特定のターゲットフレームワークに移植するために必要な作業をチームが評価するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-135">Helps teams assess the effort required to port a particular project to a particular target framework.</span></span>

<span data-ttu-id="7e24f-136">この分析の詳細については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-136">The details of this analysis are covered in the next section.</span></span>

<span data-ttu-id="7e24f-137">プロジェクトとそれらの関係を相互にマップしたら、プロジェクトを移行する順序を決めることができます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-137">Once you've mapped out the projects and their relationships with one another, you're ready to determine the order in which you'll migrate the projects.</span></span> <span data-ttu-id="7e24f-138">依存関係のないプロジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-138">Begin with projects that have no dependencies.</span></span> <span data-ttu-id="7e24f-139">次に、これらのプロジェクトに依存するプロジェクトのツリーを操作します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-139">Then, work your way up the tree to the projects that depend on these projects.</span></span>

<span data-ttu-id="7e24f-140">図3-1 に示されている例では、他のプロジェクトに依存していないため、 *Contoso. ユーティリティ* プロジェクトから開始します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-140">In the example shown in Figure 3-1, you would start with the *Contoso.Utils* project, since it doesn't depend on any other projects.</span></span> <span data-ttu-id="7e24f-141">次に、 *Contoso. データ* は "ユーティリティ" にのみ依存しています。</span><span class="sxs-lookup"><span data-stu-id="7e24f-141">Next, *Contoso.Data* since it only depends on "Utils".</span></span> <span data-ttu-id="7e24f-142">次に、"BusinessLogic" ライブラリを移行し、最後にフロントエンドの ASP.NET "Web" プロジェクトを移行します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-142">Then migrate the "BusinessLogic" library, and finally the front-end ASP.NET "Web" project.</span></span> <span data-ttu-id="7e24f-143">この "ボトムアップ" アプローチは、すべてのプロジェクトが移行された後に1つの単位として移行できる、比較的小規模で十分に考慮されていないアプリに適しています。</span><span class="sxs-lookup"><span data-stu-id="7e24f-143">Following this "bottom up" approach works well for relatively small and well-factored apps that can be migrated as a unit once all of their projects have migrated.</span></span> <span data-ttu-id="7e24f-144">より複雑な大規模なアプリや、移行に時間がかかるコードが多いほど、より多くの増分戦略を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e24f-144">Larger apps with more complexity, or more code that will take longer to migrate, may need to consider more incremental strategies.</span></span>

## <a name="unit-tests"></a><span data-ttu-id="7e24f-145">単体テスト</span><span class="sxs-lookup"><span data-stu-id="7e24f-145">Unit tests</span></span>

<span data-ttu-id="7e24f-146">前の図には、単体テストプロジェクトがありません。</span><span class="sxs-lookup"><span data-stu-id="7e24f-146">Missing from the previous diagrams are unit test projects.</span></span> <span data-ttu-id="7e24f-147">おそらく、移植されているライブラリの既存の動作を少なくともいくつかカバーするテストがあります。</span><span class="sxs-lookup"><span data-stu-id="7e24f-147">Hopefully there are tests covering at least some of the existing behavior of the libraries being ported.</span></span>

<span data-ttu-id="7e24f-148">単体テストを使用している場合は、最初にこれらのプロジェクトを変換することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e24f-148">If you have unit tests, it's best to convert those projects first.</span></span> <span data-ttu-id="7e24f-149">作業中のプロジェクトで変更のテストを続行します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-149">You'll want to continue testing changes in the project you're working on.</span></span> <span data-ttu-id="7e24f-150">.NET Core への移植は、コードベースに大きな変更があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7e24f-150">Remember that porting to .NET Core is a significant change to your codebase.</span></span>

<span data-ttu-id="7e24f-151">MSTest、xUnit、NUnit はすべて .NET Core で動作します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-151">MSTest, xUnit, and NUnit all work on .NET Core.</span></span> <span data-ttu-id="7e24f-152">現在アプリのテストがない場合は、システムの現在の動作を検証するいくつかの特徴テストを構築することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7e24f-152">If you don't currently have tests for your app, consider building some characterization tests that verify the system's current behavior.</span></span> <span data-ttu-id="7e24f-153">その利点は、移行が完了したら、アプリの動作が変更されていないことを確認できることです。</span><span class="sxs-lookup"><span data-stu-id="7e24f-153">The benefit is that once the migration is complete, you can confirm the app's behavior remains unchanged.</span></span>

## <a name="considerations-for-migrating-many-apps"></a><span data-ttu-id="7e24f-154">多数のアプリの移行に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="7e24f-154">Considerations for migrating many apps</span></span>

<span data-ttu-id="7e24f-155">組織によっては、移行するアプリが多数あり、それぞれを手動で移行すると、大量のリソースを使用する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e24f-155">Some organizations will have many different apps to migrate, and migrating each one by hand may require too many resources to be tenable.</span></span> <span data-ttu-id="7e24f-156">このような状況では、何らかのレベルの自動化が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-156">In these situations, some degree of automation is recommended.</span></span> <span data-ttu-id="7e24f-157">この章の手順を自動化することができます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-157">The steps followed in this chapter can be automated.</span></span> <span data-ttu-id="7e24f-158">プロジェクトファイルの相違点や共通パッケージの更新などの構造的な変更は、スクリプトで適用できます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-158">Structural changes, like project file differences and updates to common packages, can be applied by scripts.</span></span> <span data-ttu-id="7e24f-159">これらのスクリプトは、より多くのプロジェクトで繰り返し実行されるため、洗練されています。</span><span class="sxs-lookup"><span data-stu-id="7e24f-159">These scripts can be refined as they're run iteratively on more projects.</span></span> <span data-ttu-id="7e24f-160">各実行時に、各プロジェクトに必要な手動の手順をすべて確認します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-160">On each run, examine whatever manual steps are required for each project.</span></span> <span data-ttu-id="7e24f-161">可能であれば、これらの手動の手順を自動化します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-161">Automate those manual steps, if possible.</span></span> <span data-ttu-id="7e24f-162">このアプローチを使用すると、時間の経過と共にアプリの移植をより迅速かつ効率的に実行できるようになり、自動化のサポートが改善されます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-162">Using this approach, the organization should grow faster and better at porting their apps over time, with improved automation support each step of the way.</span></span>

<span data-ttu-id="7e24f-163">この [Dotnetconf プレゼンテーションで、Lizzy Gallagher Of Mastercard を](https://www.youtube.com/watch?v=C-2haqb60No)使用してこの方法を採用する方法の概要をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e24f-163">Watch an overview of how to employ this approach in this [dotNetConf presentation by Lizzy Gallagher of Mastercard](https://www.youtube.com/watch?v=C-2haqb60No).</span></span> <span data-ttu-id="7e24f-164">このプレゼンテーションで採用されている5つのフェーズは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e24f-164">The five phases employed in this presentation included:</span></span>

- <span data-ttu-id="7e24f-165">サードパーティの NuGet 依存関係を移行する</span><span class="sxs-lookup"><span data-stu-id="7e24f-165">Migrate third-party NuGet dependencies</span></span>
- <span data-ttu-id="7e24f-166">新しい *.csproj* ファイル形式を使用するようにアプリを移行する</span><span class="sxs-lookup"><span data-stu-id="7e24f-166">Migrate apps to use new *.csproj* file format</span></span>
- <span data-ttu-id="7e24f-167">アプリを ASP.NET Core に移行する (.NET Framework をターゲットにする)</span><span class="sxs-lookup"><span data-stu-id="7e24f-167">Migrate apps to ASP.NET Core (targeting .NET Framework)</span></span>
- <span data-ttu-id="7e24f-168">内部の NuGet 依存関係を .NET Standard に更新します</span><span class="sxs-lookup"><span data-stu-id="7e24f-168">Update internal NuGet dependencies to .NET Standard</span></span>
- <span data-ttu-id="7e24f-169">.NET Core 3.1 を対象とするようにすべてのアプリを更新する</span><span class="sxs-lookup"><span data-stu-id="7e24f-169">Update all apps to target .NET Core 3.1</span></span>

<span data-ttu-id="7e24f-170">アプリの大規模なスイートを自動化する場合、一貫したコーディングのガイドラインとプロジェクトの編成に従うと、大幅に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-170">When automating a large suite of apps, it helps significantly if they follow consistent coding guidelines and project organization.</span></span> <span data-ttu-id="7e24f-171">Automation の取り組みは、この一貫性を効果的にするために依存します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-171">Automation efforts rely on this consistency to be effective.</span></span> <span data-ttu-id="7e24f-172">プロジェクトファイルの解析と移行に加えて、一般的なコードパターンを自動的に移行することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-172">In addition to parsing and migrating project files, common code patterns can be migrated automatically.</span></span> <span data-ttu-id="7e24f-173">一部のコードパターンの例には、コントローラーアクションの宣言方法や結果の取得方法の違いが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e24f-173">Some code pattern examples include differences in how controller actions are declared or how they return results.</span></span>

<span data-ttu-id="7e24f-174">たとえば、移行スクリプトでは、 *Controller.cs* に一致するファイルを検索して、次のいずれかのパターンに一致するコード行を検索できます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-174">For example, a migration script could search files matching *Controller.cs* for lines of code matching one of these patterns:</span></span>

```csharp
   return new HttpStatusCodeResult(200);
   // or
   return new HttpStatusCodeResult(HttpStatusCode.OK);
```

<span data-ttu-id="7e24f-175">ASP.NET Core では、上記のコード行のいずれかを次のように置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-175">In ASP.NET Core, either of the preceding lines of code can be replaced with:</span></span>

```csharp
    return Ok();
```

## <a name="summary"></a><span data-ttu-id="7e24f-176">まとめ</span><span class="sxs-lookup"><span data-stu-id="7e24f-176">Summary</span></span>

<span data-ttu-id="7e24f-177">大規模な .NET Framework アプリを .NET Core に移植するには、次の方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e24f-177">The best approach to porting a large .NET Framework app to .NET Core is to:</span></span>

1. <span data-ttu-id="7e24f-178">プロジェクトの依存関係を特定します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-178">Identify project dependencies.</span></span>
1. <span data-ttu-id="7e24f-179">各プロジェクトの移植に必要なものを分析します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-179">Analyze what's required to port each project.</span></span>
1. <span data-ttu-id="7e24f-180">下から開始します。</span><span class="sxs-lookup"><span data-stu-id="7e24f-180">Start from the bottom up.</span></span>

<span data-ttu-id="7e24f-181">.NET 移植性アナライザーを使用して、ターゲットプラットフォームと互換性のある既存のライブラリを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-181">You can use the .NET Portability Analyzer to determine how compatible existing libraries may be with target platforms.</span></span> <span data-ttu-id="7e24f-182">自動テストを使用すると、アプリが移植される際に重大な変更が発生しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e24f-182">Automated tests will help ensure no breaking changes are introduced as the app is ported.</span></span> <span data-ttu-id="7e24f-183">これらのテストプロジェクトは、移植された最初のプロジェクトの中にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e24f-183">These test projects should be among the first projects ported.</span></span>

## <a name="references"></a><span data-ttu-id="7e24f-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e24f-184">References</span></span>

- [<span data-ttu-id="7e24f-185">.NET Framework から .NET Core への移植</span><span class="sxs-lookup"><span data-stu-id="7e24f-185">Porting from .NET Framework to .NET Core</span></span>](../../core/porting/index.md)
- [<span data-ttu-id="7e24f-186">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="7e24f-186">The .NET Portability Analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
- [<span data-ttu-id="7e24f-187">Channel 9: .NET 移植性アナライザーの概要 (ビデオ)</span><span class="sxs-lookup"><span data-stu-id="7e24f-187">Channel 9: A Brief Look at the .NET Portability Analyzer (Video)</span></span>](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer)
- [<span data-ttu-id="7e24f-188">2年間、200アプリ: 大規模な .NET Core の移行 (ビデオ)</span><span class="sxs-lookup"><span data-stu-id="7e24f-188">2 Years, 200 Apps: A .NET Core Migration at Scale (Video)</span></span>](https://www.youtube.com/watch?v=C-2haqb60No)

>[!div class="step-by-step"]
><span data-ttu-id="7e24f-189">[前へ](migrate-large-solutions.md)
>[次へ](understand-update-dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="7e24f-189">[Previous](migrate-large-solutions.md)
[Next](understand-update-dependencies.md)</span></span>
