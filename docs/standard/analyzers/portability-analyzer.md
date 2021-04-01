---
title: .NET Portability Analyzer - .NET
description: .NET Portability Analyzer ツールを使って、さまざまな .NET の実装 (.NET Core、.NET Standard、UWP、Xamarin など) の間でのコードの移植性を評価する方法について説明します。
ms.date: 09/13/2019
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: c53560176c66f1b69a5e3d7208e91fd4c4ec7dbd
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584383"
---
# <a name="the-net-portability-analyzer"></a><span data-ttu-id="10bf3-103">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="10bf3-103">The .NET Portability Analyzer</span></span>

<span data-ttu-id="10bf3-104">ライブラリでマルチプラットフォームをサポートしたい場合や、</span><span class="sxs-lookup"><span data-stu-id="10bf3-104">Want to make your libraries support multi-platform?</span></span> <span data-ttu-id="10bf3-105">.NET Framework アプリケーションを .NET Core で実行するのに必要な作業量を知りたい場合、</span><span class="sxs-lookup"><span data-stu-id="10bf3-105">Want to see how much work is required to make your .NET Framework application run on .NET Core?</span></span> <span data-ttu-id="10bf3-106">[.NET Portability Analyzer](https://github.com/microsoft/dotnet-apiport) というツールがアセンブリを分析し、指定された対象の .NET プラットフォームでアプリケーションまたはライブラリを移植するために不足している .NET API の詳細なレポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-106">The [.NET Portability Analyzer](https://github.com/microsoft/dotnet-apiport) is a tool that analyzes assemblies and provides a detailed report on .NET APIs that are missing for the applications or libraries to be portable on your specified targeted .NET platforms.</span></span> <span data-ttu-id="10bf3-107">[Visual Studio 拡張機能](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)として提供されている Portability Analyzer ではプロジェクトごとにアセンブリが 1 つ分析され、[ApiPort コンソール アプリ](https://aka.ms/apiportdownload)として提供されている Portability Analyzer では指定したファイルまたはディレクトリごとにアセンブリが分析されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-107">The Portability Analyzer is offered as a [Visual Studio Extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), which analyzes one assembly per project, and as a [ApiPort console app](https://aka.ms/apiportdownload), which analyzes assemblies by specified files or directory.</span></span>

<span data-ttu-id="10bf3-108">.NET Core などの新しいプラットフォームを対象とするようにプロジェクトを変換したら、Roslyn ベースの [API Analyzer ツール](api-analyzer.md)を使用して、<xref:System.PlatformNotSupportedException> の例外とその他の互換性の問題をスローする API を特定することができます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-108">Once you've converted your project to target the new platform, like .NET Core, you can use the Roslyn-based [API Analyzer tool](api-analyzer.md) to identify APIs throwing <xref:System.PlatformNotSupportedException> exceptions and other compatibility issues.</span></span>

## <a name="common-targets"></a><span data-ttu-id="10bf3-109">一般的なターゲット</span><span class="sxs-lookup"><span data-stu-id="10bf3-109">Common targets</span></span>

- <span data-ttu-id="10bf3-110">[.NET Core](../../core/introduction.md): モジュール型の設計で、side-by-side インストールをサポートしており、クロスプラットフォームのシナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="10bf3-110">[.NET Core](../../core/introduction.md): Has a modular design, supports side-by-side installation, and targets cross-platform scenarios.</span></span> <span data-ttu-id="10bf3-111">side-by-side インストールにより、他のアプリに影響を与えることなく新しい .NET Core バージョンを導入することができます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-111">Side-by-side installation allows you to adopt new .NET Core versions without breaking other apps.</span></span> <span data-ttu-id="10bf3-112">.NET Core にアプリを移植し、複数のプラットフォームをサポートすることが目的である場合は、これが推奨されるターゲットです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-112">If your goal is to port your app to .NET Core and support multiple platforms, this is the recommended target.</span></span>
- <span data-ttu-id="10bf3-113">[.NET Standard](../net-standard.md): .NET のすべての実装で使用できる .NET Standard API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="10bf3-113">.[NET Standard](../net-standard.md): Includes the .NET Standard APIs available on all .NET implementations.</span></span> <span data-ttu-id="10bf3-114">.NET でサポートされるすべてのプラットフォームでライブラリを実行させることが目的である場合は、これが推奨されるターゲットです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-114">If your goal is to make your library run on all .NET supported platforms, this is recommended target.</span></span>
- <span data-ttu-id="10bf3-115">[ASP.NET Core](/aspnet/core): .NET Core 上に構築された最新の Web フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-115">[ASP.NET Core](/aspnet/core): A modern web-framework built on .NET Core.</span></span> <span data-ttu-id="10bf3-116">複数のプラットフォームをサポートするために .NET Core に Web アプリを移植することが目的である場合は、これが推奨されるターゲットです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-116">If your goal is to port your web app to .NET Core to support multiple platforms, this is the recommended target.</span></span>
- <span data-ttu-id="10bf3-117">.NET Core と[プラットフォーム拡張機能](../../core/porting/windows-compat-pack.md): Windows 互換機能パックに加えて .NET Core API が含まれます。 .NET Framework で利用可能なテクノロジの多くが提供されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-117">.NET Core + [Platform Extensions](../../core/porting/windows-compat-pack.md): Includes the .NET Core APIs in addition to the Windows Compatibility Pack, which provides many of the .NET Framework available technologies.</span></span> <span data-ttu-id="10bf3-118">Windows で .NET Framework から .NET Core にアプリを移植する場合は、これが推奨されるターゲットです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-118">This is a recommended target for porting your app from .NET Framework to .NET Core on Windows.</span></span>
- <span data-ttu-id="10bf3-119">.NET Standard と[プラットフォーム拡張機能](../../core/porting/windows-compat-pack.md): Windows 互換機能パックに加えて .NET Standard API が含まれます。 .NET Framework で利用可能なテクノロジの多くが提供されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-119">.NET Standard + [Platform Extensions](../../core/porting/windows-compat-pack.md): Includes the .NET Standard APIs in addition to the Windows Compatibility Pack, which provides many of the .NET Framework available technologies.</span></span> <span data-ttu-id="10bf3-120">Windows で .NET Framework から .NET Core にライブラリを移植する場合は、これが推奨されるターゲットです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-120">This is a recommended target for porting your library from .NET Framework to .NET Core on Windows.</span></span>

## <a name="how-to-use-the-net-portability-analyzer"></a><span data-ttu-id="10bf3-121">.NET Portability Analyzer の使用方法</span><span class="sxs-lookup"><span data-stu-id="10bf3-121">How to use the .NET Portability Analyzer</span></span>

<span data-ttu-id="10bf3-122">Visual Studio で .NET Portability Analyzer を使用するには、[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) から拡張機能をダウンロードし、インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="10bf3-122">To begin using the .NET Portability Analyzer in Visual Studio, you first need to download and install the extension from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span> <span data-ttu-id="10bf3-123">Visual Studio 2017 以降のバージョンで機能します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-123">It works on Visual Studio 2017 and later versions.</span></span> <span data-ttu-id="10bf3-124">Visual Studio で構成するには、 **[Analyze]\(分析\)**  >  **[Portability Analyzer Settings]\(Portability Analyzer の設定\)** でターゲット プラットフォームを選択します。ターゲット プラットフォームとは、アセンブリが現在ビルドされているプラットフォーム/バージョンと比較をする、移植における違いを評価する .NET プラットフォーム/バージョンです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-124">Configure it in Visual Studio via **Analyze** > **Portability Analyzer Settings** and select your Target Platforms, which are the .NET platforms/versions that you want to evaluate the portability gaps comparing with the platform/version that your current assembly is built with.</span></span>

![移植性アナライザーのスクリーンショット。](./media/portability-analyzer/portability-screenshot.png)

<span data-ttu-id="10bf3-126">ApiPort コンソール アプリケーションを使用して、[ApiPort リポジトリ](https://aka.ms/apiportdownload)からダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-126">You can also use the ApiPort console application, download it from [ApiPort repository](https://aka.ms/apiportdownload).</span></span> <span data-ttu-id="10bf3-127">`listTargets` コマンド オプションを使って使用可能なターゲットの一覧を表示した後、`-t` または `--target` コマンド オプションを指定することによってターゲット プラットフォームを選択できます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-127">You can use `listTargets` command option to display the available target list, then pick target platforms by specifying `-t` or `--target` command option.</span></span>

### <a name="solution-wide-view"></a><span data-ttu-id="10bf3-128">ソリューション全体の表示</span><span class="sxs-lookup"><span data-stu-id="10bf3-128">Solution wide view</span></span>

<span data-ttu-id="10bf3-129">多数のプロジェクトが含まれるソリューションを分析するためのステップとしては、アセンブリのサブセットのどれが何に依存しているのかを把握するために、依存関係を視覚化するのが有用です。</span><span class="sxs-lookup"><span data-stu-id="10bf3-129">A useful step in analyzing a solution with many projects would be to visualize the dependencies to understand which subset of assemblies depend on what.</span></span> <span data-ttu-id="10bf3-130">一般的には、依存関係グラフのリーフ ノードで始まるボトムアップ アプローチで分析結果を適用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-130">The general recommendation is to apply the results of the analysis in a bottom-up approach starting with the leaf nodes in a dependency graph.</span></span>

<span data-ttu-id="10bf3-131">これを取得するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-131">To retrieve this, you may run the following command:</span></span>

```console
ApiPort.exe analyze -r DGML -f [directory or file]
```

<span data-ttu-id="10bf3-132">この結果を Visual Studio で開くと次のようになります。</span><span class="sxs-lookup"><span data-stu-id="10bf3-132">A result of this would look like the following when opened in Visual Studio:</span></span>

![DGML 分析のスクリーンショット。](./media/portability-analyzer/dgml-example.png)

### <a name="analyze-portability"></a><span data-ttu-id="10bf3-134">移植性を分析する</span><span class="sxs-lookup"><span data-stu-id="10bf3-134">Analyze portability</span></span>

<span data-ttu-id="10bf3-135">Visual Studio でプロジェクト全体を分析するには、**ソリューション エクスプローラー** でプロジェクトを右クリックし、 **[Analyze Assembly Portability]\(アセンブリの移植性を分析する\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-135">To analyze your entire project in Visual Studio, right-click on your project in **Solution Explorer** and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="10bf3-136">または、 **[分析]** メニューで **[Analyze Assembly Portability]** (アセンブリの移植性を分析) を選択します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-136">Otherwise, go to the **Analyze** menu and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="10bf3-137">そこから、プロジェクトの実行可能ファイルまたは DLL を選択します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-137">From there, select your project's executable or DLL.</span></span>

![ソリューション エクスプローラーからの移植性アナライザーのスクリーンショット。](./media/portability-analyzer/portability-solution-explorer.png)

<span data-ttu-id="10bf3-139">[ApiPort コンソール アプリ](https://aka.ms/apiportdownload)を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-139">You can also use the [ApiPort console app](https://aka.ms/apiportdownload).</span></span>

<span data-ttu-id="10bf3-140">現在のディレクトリを分析するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-140">Type the following command to analyze the current directory:</span></span>

```console
ApiPort.exe analyze -f .
```

<span data-ttu-id="10bf3-141">特定の .dll ファイルの一覧を分析するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-141">To analyze a specific list of .dll files, type the following command:</span></span>

```console
ApiPort.exe analyze -f first.dll -f second.dll -f third.dll
```

<span data-ttu-id="10bf3-142">特定のバージョンをターゲットにするには、`-t` パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-142">To target a specific version, use the `-t` parameter:</span></span>

```console
ApiPort.exe analyze -t ".NET, Version=5.0" -f .
```

<span data-ttu-id="10bf3-143">詳細なヘルプを表示するには `ApiPort.exe -?` を実行します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-143">Run `ApiPort.exe -?` to get more help.</span></span>

<span data-ttu-id="10bf3-144">自分が所有していて移植したいすべての関連する exe と dll ファイルを含め、アプリが依存しているけれども自分で所有しているのではなく移植できないファイルを除外することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="10bf3-144">It is recommended that you include all the related exe and dll files that you own and want to port, and exclude the files that your app depends on, but you don't own and can't port.</span></span> <span data-ttu-id="10bf3-145">これにより、最も関連のある移植性レポートが得られます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-145">This will give you most relevant portability report.</span></span>

### <a name="view-and-interpret-portability-result"></a><span data-ttu-id="10bf3-146">移植性の結果を表示して解釈する</span><span class="sxs-lookup"><span data-stu-id="10bf3-146">View and interpret portability result</span></span>

<span data-ttu-id="10bf3-147">レポートには、ターゲット プラットフォームによってサポートされていない API のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-147">Only APIs that are unsupported by a Target Platform appear in the report.</span></span>
<span data-ttu-id="10bf3-148">Visual Studio で分析を実行すると、.NET 移植性レポート ファイルのリンクがポップアップ表示されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-148">After running the analysis in Visual Studio, you'll see your .NET Portability report file link pops up.</span></span> <span data-ttu-id="10bf3-149">[ApiPort コンソール アプリ](https://aka.ms/apiportdownload)を使った場合は、.NET 移植性レポートは指定した形式のファイルとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-149">If you used the [ApiPort console app](https://aka.ms/apiportdownload), your .NET Portability report is saved as a file in the format you specified.</span></span> <span data-ttu-id="10bf3-150">既定では、現在のディレクトリの Excel ファイル ( *.xlsx*) です。</span><span class="sxs-lookup"><span data-stu-id="10bf3-150">The default is in an Excel file (*.xlsx*) in your current directory.</span></span>

#### <a name="portability-summary"></a><span data-ttu-id="10bf3-151">移植性の概要</span><span class="sxs-lookup"><span data-stu-id="10bf3-151">Portability Summary</span></span>

![移植性の概要のスクリーンショット。](./media/portability-analyzer/api-catalog-portablility-summary.png)

<span data-ttu-id="10bf3-153">レポートの [Portability Summary]\(移植性の概要\) セクションでは、実行に含まれる各アセンブリの移植性の割合が示されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-153">The Portability Summary section of the report shows the portability percentage for each assembly included in the run.</span></span> <span data-ttu-id="10bf3-154">前の例では、`svcutil` アプリで使われている .NET Framework API の 71.24% が、.NET Core とプラットフォーム拡張機能で使用できます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-154">In the previous example, 71.24% of the .NET Framework APIs used in the `svcutil` app are available in .NET Core + Platform Extensions.</span></span> <span data-ttu-id="10bf3-155">複数のアセンブリに対して .NET Portability Analyzer ツールを実行した場合、移植性の概要レポートでは各アセンブリが 1 行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-155">If you run the .NET Portability Analyzer tool against multiple assemblies, each assembly should have a row in the Portability Summary report.</span></span>

#### <a name="details"></a><span data-ttu-id="10bf3-156">説明</span><span class="sxs-lookup"><span data-stu-id="10bf3-156">Details</span></span>

![移植性の詳細のスクリーンショット。](./media/portability-analyzer/api-catalog-portablility-details.png)

<span data-ttu-id="10bf3-158">レポートの **[説明]** セクションには、選択した **ターゲット プラットフォーム** のいずれからも欠落している API が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-158">The **Details** section of the report lists the APIs missing from any of the selected **Targeted Platforms**.</span></span>

- <span data-ttu-id="10bf3-159">[Target type]\(ターゲットの型\): 型にターゲット プラットフォームに存在しない API があります</span><span class="sxs-lookup"><span data-stu-id="10bf3-159">Target type: the type has missing API from a Target Platform</span></span>
- <span data-ttu-id="10bf3-160">[Target member]\(ターゲットのメンバー\): メンバーがターゲット プラットフォームにありません</span><span class="sxs-lookup"><span data-stu-id="10bf3-160">Target member: the method is missing from a Target Platform</span></span>
- <span data-ttu-id="10bf3-161">[Assembly name]\(アセンブリ名\): ない API が存在する .NET Framework アセンブリです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-161">Assembly name: the .NET Framework assembly that the missing API lives in.</span></span>
- <span data-ttu-id="10bf3-162">選択されているターゲット プラットフォームごとに 1 つの列 (".NET Core" など): [Not supported]\(サポートされていません\) という値は、その API がこのターゲット プラットフォームでサポートされていないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-162">Each of the selected Target Platforms is one column, such as ".NET Core": "Not supported" value means the API is not supported on this Target Platform.</span></span>
- <span data-ttu-id="10bf3-163">[Recommended Changes]\(推奨される変更\): それに変更することが推奨される API またはテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-163">Recommended Changes: the recommended API or technology to change to.</span></span> <span data-ttu-id="10bf3-164">現時点では、このフィールドは空であるか、多くの API に対応しなくなっています。</span><span class="sxs-lookup"><span data-stu-id="10bf3-164">Currently, this field is empty or out of date for many APIs.</span></span> <span data-ttu-id="10bf3-165">API の数は多く、最新の状態に保つために尽力しているところです。</span><span class="sxs-lookup"><span data-stu-id="10bf3-165">Due to the large number of APIs, we have a significant challenge to keep it up to date.</span></span> <span data-ttu-id="10bf3-166">お客様に役に立つ情報を提供する代わりの解決策を検討中です。</span><span class="sxs-lookup"><span data-stu-id="10bf3-166">We're looking at alternative solutions to provide helpful information to customers.</span></span>

#### <a name="missing-assemblies"></a><span data-ttu-id="10bf3-167">足りないアセンブリ</span><span class="sxs-lookup"><span data-stu-id="10bf3-167">Missing Assemblies</span></span>

![足りないアセンブリのスクリーンショット。](./media/portability-analyzer/api-catalog-missing-assemblies.png)

<span data-ttu-id="10bf3-169">レポートには [Missing Assemblies]\(足りないアセンブリ\) セクションが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="10bf3-169">You may find a Missing Assemblies section in your report.</span></span> <span data-ttu-id="10bf3-170">このセクションには、分析されたアセンブリによって参照されている、分析されていないアセンブリの一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-170">This section contains a list of assemblies that are referenced by your analyzed assemblies and were not analyzed.</span></span> <span data-ttu-id="10bf3-171">自分が所有しているアセンブリの場合は、API Portability Analyzer の実行にそれを含めて、そのアセンブリに関する API レベルの詳細な移植性レポートを取得できます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-171">If it's an assembly that you own, include it in the API portability analyzer run so that you can get a detailed, API-level portability report for it.</span></span> <span data-ttu-id="10bf3-172">それがサードパーティ製のライブラリである場合は、ご自分のターゲット プラットフォームをサポートする新しいバージョンがあるかどうかを確認し、その新しいバージョンに移行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="10bf3-172">If it's a third-party library, check if there is a newer version that supports your target platform, and consider moving to the newer version.</span></span> <span data-ttu-id="10bf3-173">この一覧には最終的に、アプリが依存し、ターゲット プラットフォームをサポートするバージョンのすべてのサード パーティ アセンブリが含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="10bf3-173">Eventually, the list should include all the third-party assemblies that your app depends on that have a version supporting your target platform.</span></span>

<span data-ttu-id="10bf3-174">.NET Portability Analyzer の詳細については、[GitHub ドキュメント](https://github.com/Microsoft/dotnet-apiport#documentation)にアクセスし、Channel 9 動画の「[A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer)」 (.NET Portability Analyzer の概要) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="10bf3-174">For more information on the .NET Portability Analyzer, visit the [GitHub documentation](https://github.com/Microsoft/dotnet-apiport#documentation) and [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span></span>
