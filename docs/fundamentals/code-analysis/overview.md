---
title: .NET のコード分析
titleSuffix: ''
description: .NET SDK のソース コード分析について説明します。
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 1a0b31f7aca6415510ed0fcd08e9f9a0f8f39bf5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876605"
---
# <a name="overview-of-net-source-code-analysis"></a><span data-ttu-id="183dc-103">.NET ソース コード分析の概要</span><span class="sxs-lookup"><span data-stu-id="183dc-103">Overview of .NET source code analysis</span></span>

<span data-ttu-id="183dc-104">.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コードの品質やスタイルに関する問題を検査できます。</span><span class="sxs-lookup"><span data-stu-id="183dc-104">.NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and style issues.</span></span> <span data-ttu-id="183dc-105">.NET 5.0 以降、これらのアナライザーは .NET SDK に含まれており、個別にインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="183dc-105">Starting in .NET 5.0, these analyzers are included with the .NET SDK and you don't need to install them separately.</span></span> <span data-ttu-id="183dc-106">プロジェクトが .NET 5 以降をターゲットとしている場合は、既定でコード分析が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-106">If your project targets .NET 5 or later, code analysis is enabled by default.</span></span> <span data-ttu-id="183dc-107">プロジェクトが .NET Core、.NET Standard、.NET Framework などの別の .NET 実装をターゲットとしている場合は、[EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを `true` に設定することにより、コード分析を手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="183dc-107">If your project targets a different .NET implementation, for example, .NET Core, .NET Standard, or .NET Framework, you must manually enable code analysis by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span>

<span data-ttu-id="183dc-108">.NET 5 以降の SDK に移行しない場合、SDK スタイル以外の .NET Framework プロジェクトを使用する場合、または NuGet パッケージベースのモデルを使用する場合は、[Microsoft.CodeAnalysis.NetAnalyzers NuGet パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)でアナライザーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="183dc-108">If you don't want to move to the .NET 5+ SDK, have a non-SDK-style .NET Framework project, or prefer a NuGet package-based model, the analyzers are also available in the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers).</span></span> <span data-ttu-id="183dc-109">オンデマンドのバージョン更新には、パッケージベースのモデルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="183dc-109">You might prefer a package-based model for on-demand version updates.</span></span>

> [!NOTE]
> <span data-ttu-id="183dc-110">.NET アナライザーは、ターゲット フレームワークに依存しません。</span><span class="sxs-lookup"><span data-stu-id="183dc-110">.NET analyzers are target-framework agnostic.</span></span> <span data-ttu-id="183dc-111">つまり、プロジェクトが特定の .NET 実装をターゲットにする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="183dc-111">That is, your project does not need to target a specific .NET implementation.</span></span> <span data-ttu-id="183dc-112">アナライザーは、`net5.0` のほか、以前のバージョンの .NET (`netcoreapp3.1` や `net472` など) をターゲットとするプロジェクトで機能します。</span><span class="sxs-lookup"><span data-stu-id="183dc-112">The analyzers work for projects that target `net5.0` as well as earlier .NET versions, such as `netcoreapp3.1` and `net472`.</span></span> <span data-ttu-id="183dc-113">ただし、[EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを使用してコード分析を有効にするには、プロジェクトが[プロジェクト SDK](../../core/project-sdk/overview.md) を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="183dc-113">However, to enable code analysis using the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property, your project must reference a [project SDK](../../core/project-sdk/overview.md).</span></span>

<span data-ttu-id="183dc-114">アナライザーによってルール違反が検出されると、各ルールの[構成](configuration-options.md)方法に応じて、修正候補、警告、またはエラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="183dc-114">If rule violations are found by an analyzer, they're reported as a suggestion, warning, or error, depending on how each rule is [configured](configuration-options.md).</span></span> <span data-ttu-id="183dc-115">コード分析違反は、コンパイラ エラーと区別するために "CA" または "IDE" というプレフィックスで示されます。</span><span class="sxs-lookup"><span data-stu-id="183dc-115">Code analysis violations appear with the prefix "CA" or "IDE" to differentiate them from compiler errors.</span></span>

## <a name="code-quality-analysis"></a><span data-ttu-id="183dc-116">コード品質の分析</span><span class="sxs-lookup"><span data-stu-id="183dc-116">Code quality analysis</span></span>

<span data-ttu-id="183dc-117">*コード品質の分析* ("CAxxxx") ルールでは、お使いの C# コードまたは Visual Basic コードにセキュリティ、パフォーマンス、設計などの問題がないか検査が行われます。</span><span class="sxs-lookup"><span data-stu-id="183dc-117">*Code quality analysis* ("CAxxxx") rules inspect your C# or Visual Basic code for security, performance, design and other issues.</span></span> <span data-ttu-id="183dc-118">分析は、.NET 5.0 以降をターゲットとするプロジェクトで既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-118">Analysis is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="183dc-119">[EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを `true` に設定すると、以前のバージョンの .NET を対象とするプロジェクトで、.NET コード分析を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="183dc-119">You can enable code analysis on projects that target earlier .NET versions by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span> <span data-ttu-id="183dc-120">`EnableNETAnalyzers` を `false` に設定すると、自分のプロジェクトでコード分析を無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="183dc-120">You can also disable code analysis for your project by setting `EnableNETAnalyzers` to `false`.</span></span>

> [!TIP]
> <span data-ttu-id="183dc-121">Visual Studio を使用している場合:</span><span class="sxs-lookup"><span data-stu-id="183dc-121">If you're using Visual Studio:</span></span>
>
> - <span data-ttu-id="183dc-122">多くのアナライザー ルールには、"*コード修正*" が関連付けられており、これを適用して問題を修正できます。</span><span class="sxs-lookup"><span data-stu-id="183dc-122">Many analyzer rules have associated *code fixes* that you can apply to correct the problem.</span></span> <span data-ttu-id="183dc-123">コード修正は、電球アイコン メニューに示されます。</span><span class="sxs-lookup"><span data-stu-id="183dc-123">Code fixes are shown in the light bulb icon menu.</span></span>
> - <span data-ttu-id="183dc-124">コード分析を有効または無効にするには、ソリューション エクスプローラーでプロジェクトを右クリックし、 **[プロパティ]**  >  **[コード分析]** タブ > **[Enable .NET analyzers]\(.NET アナライザーの有効化\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="183dc-124">You can enable or disable code analysis by right-clicking on a project in Solution Explorer and selecting **Properties** > **Code Analysis** tab > **Enable .NET analyzers**.</span></span>

### <a name="enabled-rules"></a><span data-ttu-id="183dc-125">有効なルール</span><span class="sxs-lookup"><span data-stu-id="183dc-125">Enabled rules</span></span>

<span data-ttu-id="183dc-126">.NET 5.0 では、既定で次のルールが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-126">The following rules are enabled, by default, in .NET 5.0.</span></span>

| <span data-ttu-id="183dc-127">診断 ID</span><span class="sxs-lookup"><span data-stu-id="183dc-127">Diagnostic ID</span></span> | <span data-ttu-id="183dc-128">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="183dc-128">Category</span></span> | <span data-ttu-id="183dc-129">重大度</span><span class="sxs-lookup"><span data-stu-id="183dc-129">Severity</span></span> | <span data-ttu-id="183dc-130">説明</span><span class="sxs-lookup"><span data-stu-id="183dc-130">Description</span></span> |
| - | - | - | - |
| [<span data-ttu-id="183dc-131">CA1416</span><span class="sxs-lookup"><span data-stu-id="183dc-131">CA1416</span></span>](/visualstudio/code-quality/ca1416) | <span data-ttu-id="183dc-132">相互運用性</span><span class="sxs-lookup"><span data-stu-id="183dc-132">Interoperability</span></span> | <span data-ttu-id="183dc-133">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-133">Warning</span></span> | <span data-ttu-id="183dc-134">プラットフォーム互換性アナライザー</span><span class="sxs-lookup"><span data-stu-id="183dc-134">Platform compatibility analyzer</span></span> |
| [<span data-ttu-id="183dc-135">CA1417</span><span class="sxs-lookup"><span data-stu-id="183dc-135">CA1417</span></span>](/visualstudio/code-quality/ca1417) | <span data-ttu-id="183dc-136">相互運用性</span><span class="sxs-lookup"><span data-stu-id="183dc-136">Interoperability</span></span> | <span data-ttu-id="183dc-137">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-137">Warning</span></span> | <span data-ttu-id="183dc-138">P/Invoke の文字列パラメーターに `OutAttribute` を使用しないでください</span><span class="sxs-lookup"><span data-stu-id="183dc-138">Do not use `OutAttribute` on string parameters for P/Invokes</span></span> |
| [<span data-ttu-id="183dc-139">CA1831</span><span class="sxs-lookup"><span data-stu-id="183dc-139">CA1831</span></span>](/visualstudio/code-quality/ca1831) | <span data-ttu-id="183dc-140">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="183dc-140">Performance</span></span> | <span data-ttu-id="183dc-141">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-141">Warning</span></span> | <span data-ttu-id="183dc-142">該当する場合、文字列に範囲ベースのインデクサーの代わりに `AsSpan` を使用します</span><span class="sxs-lookup"><span data-stu-id="183dc-142">Use `AsSpan` instead of range-based indexers for string when appropriate</span></span> |
| [<span data-ttu-id="183dc-143">CA2013</span><span class="sxs-lookup"><span data-stu-id="183dc-143">CA2013</span></span>](/visualstudio/code-quality/ca2013) | <span data-ttu-id="183dc-144">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="183dc-144">Reliability</span></span> | <span data-ttu-id="183dc-145">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-145">Warning</span></span> | <span data-ttu-id="183dc-146">値の型に `ReferenceEquals` を使用しないでください</span><span class="sxs-lookup"><span data-stu-id="183dc-146">Do not use `ReferenceEquals` with value types</span></span> |
| [<span data-ttu-id="183dc-147">CA2014</span><span class="sxs-lookup"><span data-stu-id="183dc-147">CA2014</span></span>](/visualstudio/code-quality/ca2014) | <span data-ttu-id="183dc-148">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="183dc-148">Reliability</span></span> | <span data-ttu-id="183dc-149">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-149">Warning</span></span> | <span data-ttu-id="183dc-150">ループで `stackalloc` を使用しないでください</span><span class="sxs-lookup"><span data-stu-id="183dc-150">Do not use `stackalloc` in loops</span></span> |
| [<span data-ttu-id="183dc-151">CA2015</span><span class="sxs-lookup"><span data-stu-id="183dc-151">CA2015</span></span>](/visualstudio/code-quality/ca2015) | <span data-ttu-id="183dc-152">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="183dc-152">Reliability</span></span> | <span data-ttu-id="183dc-153">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-153">Warning</span></span> | <span data-ttu-id="183dc-154"><xref:System.Buffers.MemoryManager%601> から派生した型にはファイナライザーを定義しないでください</span><span class="sxs-lookup"><span data-stu-id="183dc-154">Do not define finalizers for types derived from <xref:System.Buffers.MemoryManager%601></span></span> |
| [<span data-ttu-id="183dc-155">CA2200</span><span class="sxs-lookup"><span data-stu-id="183dc-155">CA2200</span></span>](/visualstudio/code-quality/ca2200) | <span data-ttu-id="183dc-156">使用法</span><span class="sxs-lookup"><span data-stu-id="183dc-156">Usage</span></span> | <span data-ttu-id="183dc-157">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-157">Warning</span></span> | <span data-ttu-id="183dc-158">スタック詳細を保持するために再度スローします</span><span class="sxs-lookup"><span data-stu-id="183dc-158">Rethrow to preserve stack details</span></span>
| [<span data-ttu-id="183dc-159">CA2247</span><span class="sxs-lookup"><span data-stu-id="183dc-159">CA2247</span></span>](/visualstudio/code-quality/ca2247) | <span data-ttu-id="183dc-160">使用法</span><span class="sxs-lookup"><span data-stu-id="183dc-160">Usage</span></span> | <span data-ttu-id="183dc-161">警告</span><span class="sxs-lookup"><span data-stu-id="183dc-161">Warning</span></span> | <span data-ttu-id="183dc-162">TaskCompletionSource コンストラクターに渡される引数は、<xref:System.Threading.Tasks.TaskContinuationOptions> ではなく <xref:System.Threading.Tasks.TaskCreationOptions> 列挙型である必要があります</span><span class="sxs-lookup"><span data-stu-id="183dc-162">Argument passed to TaskCompletionSource constructor should be <xref:System.Threading.Tasks.TaskCreationOptions> enum instead of <xref:System.Threading.Tasks.TaskContinuationOptions></span></span> |

<span data-ttu-id="183dc-163">これらのルールの重要度を変更して、無効にするか、エラーに昇格させることができます。</span><span class="sxs-lookup"><span data-stu-id="183dc-163">You can change the severity of these rules to disable them or elevate them to errors.</span></span> <span data-ttu-id="183dc-164">[追加のルールを有効にする](#enable-additional-rules)こともできます。</span><span class="sxs-lookup"><span data-stu-id="183dc-164">You can also [enable more rules](#enable-additional-rules).</span></span>

- <span data-ttu-id="183dc-165">各 .NET SDK バージョンに含まれるルールの一覧については、[アナライザーのリリース](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="183dc-165">For a list of rules that are included with each .NET SDK version, see [Analyzer releases](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>
- <span data-ttu-id="183dc-166">すべてのコード品質ルールの一覧については、「[コード品質ルール](quality-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183dc-166">For a list of all the code quality rules, see [Code quality rules](quality-rules/index.md).</span></span>

### <a name="enable-additional-rules"></a><span data-ttu-id="183dc-167">追加のルールを有効にする</span><span class="sxs-lookup"><span data-stu-id="183dc-167">Enable additional rules</span></span>

<span data-ttu-id="183dc-168">"*分析モード*" とは、事前に定義されたコード分析構成 (いずれのルールも有効になっていない、一部またはすべてのルールが有効になっている) を意味します。</span><span class="sxs-lookup"><span data-stu-id="183dc-168">*Analysis mode* refers to a predefined code analysis configuration where none, some, or all rules are enabled.</span></span> <span data-ttu-id="183dc-169">既定の分析モードでは、少数のルールのみが[ビルド警告として有効](#enabled-rules)になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-169">In the default analysis mode, only a small number of rules are [enabled as build warnings](#enabled-rules).</span></span> <span data-ttu-id="183dc-170">プロジェクト ファイルで [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) プロパティを設定することにより、プロジェクトの分析モードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="183dc-170">You can change the analysis mode for your project by setting the [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) property in the project file.</span></span> <span data-ttu-id="183dc-171">次の値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="183dc-171">The allowable values are:</span></span>

| <span data-ttu-id="183dc-172">値</span><span class="sxs-lookup"><span data-stu-id="183dc-172">Value</span></span> | <span data-ttu-id="183dc-173">説明</span><span class="sxs-lookup"><span data-stu-id="183dc-173">Description</span></span> |
| - | - |
| `AllDisabledByDefault` | <span data-ttu-id="183dc-174">これは、最も標準のモードです。</span><span class="sxs-lookup"><span data-stu-id="183dc-174">This is the most conservative mode.</span></span> <span data-ttu-id="183dc-175">すべてのルールは、既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-175">All rules are disabled by default.</span></span> <span data-ttu-id="183dc-176">個々のルールを選択的に[オプトイン](configuration-options.md)して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="183dc-176">You can selectively [opt into](configuration-options.md) individual rules to enable them.</span></span><br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | <span data-ttu-id="183dc-177">これは、最もアグレッシブなモードです。</span><span class="sxs-lookup"><span data-stu-id="183dc-177">This is the most aggressive mode.</span></span> <span data-ttu-id="183dc-178">すべてのルールがビルド警告として有効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-178">All rules are enabled as build warnings.</span></span> <span data-ttu-id="183dc-179">個々のルールを選択的に[オプトアウト](configuration-options.md)して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="183dc-179">You can selectively [opt out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | <span data-ttu-id="183dc-180">既定のモード。この場合、いくつかのルールは警告として有効になっており、一部のルールは対応するコード修正の Visual Studio IDE 修正候補としてのみ有効になっており、残りは完全に無効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-180">The default mode, where a handful of rules are enabled as warnings, others are enabled only as Visual Studio IDE suggestions with corresponding code fixes, and the rest are disabled completely.</span></span> <span data-ttu-id="183dc-181">個々のルールを選択的に[オプトインまたはオプトアウト](configuration-options.md)して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="183dc-181">You can selectively [opt into or out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>Default</AnalysisMode>` |

<span data-ttu-id="183dc-182">使用可能な各ルールの既定の重要度と、既定の分析モードでルールが有効になっているかどうかを確認するには、[ルールの完全な一覧](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183dc-182">To find the default severity for each available rule and whether or not the rule is enabled in the default analysis mode, see the [full list of rules](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>

### <a name="treat-warnings-as-errors"></a><span data-ttu-id="183dc-183">警告をエラーとして扱う</span><span class="sxs-lookup"><span data-stu-id="183dc-183">Treat warnings as errors</span></span>

<span data-ttu-id="183dc-184">プロジェクトをビルドするときに `-warnaserror` フラグを使用すると、すべてのコード分析の警告もエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="183dc-184">If you use the `-warnaserror` flag when you build your projects, all code analysis warnings are also treated as errors.</span></span> <span data-ttu-id="183dc-185">`-warnaserror` の存在下でコード品質の警告 (CAxxxx) がエラーとして扱われないようにするには、プロジェクト ファイル内の `CodeAnalysisTreatWarningsAsErrors` MSBuild プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="183dc-185">If you do not want code quality warnings (CAxxxx) to be treated as errors in presence of `-warnaserror`, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="183dc-186">コード分析の警告は引き続き表示されますが、ビルドが中断することはありません。</span><span class="sxs-lookup"><span data-stu-id="183dc-186">You'll still see any code analysis warnings, but they won't break your build.</span></span>

### <a name="latest-updates"></a><span data-ttu-id="183dc-187">最新の更新プログラム</span><span class="sxs-lookup"><span data-stu-id="183dc-187">Latest updates</span></span>

<span data-ttu-id="183dc-188">既定では、新しいバージョンの .NET SDK にアップグレードするときに、最新のコード分析ルールと、ルールの既定の重要度を取得します。</span><span class="sxs-lookup"><span data-stu-id="183dc-188">By default, you'll get the latest code analysis rules and default rule severities as you upgrade to newer versions of the .NET SDK.</span></span> <span data-ttu-id="183dc-189">この動作が望ましくない (たとえば、新しいルールが有効または無効にならないようにする) 場合は、次のいずれかの方法でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="183dc-189">If you don't want this behavior, for example, if you want to ensure that no new rules are enabled or disabled, you can override it in one of the following ways:</span></span>

- <span data-ttu-id="183dc-190">`AnalysisLevel` MSBuild プロパティを特定の値に設定して、警告をそのセットにロックします。</span><span class="sxs-lookup"><span data-stu-id="183dc-190">Set the `AnalysisLevel` MSBuild property to a specific value to lock the warnings to that set.</span></span> <span data-ttu-id="183dc-191">より新しい SDK にアップグレードすると、これらの警告のバグ修正が引き続き表示されますが、新しい警告は有効にならず、既存の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="183dc-191">When you upgrade to a newer SDK, you'll still get bug fixes for those warnings, but no new warnings will be enabled and no existing warnings will be disabled.</span></span> <span data-ttu-id="183dc-192">たとえば、ルールのセットを、.NET SDK バージョン 5.0 に付属するセットにロックするには、プロジェクト ファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="183dc-192">For example, to lock the set of rules to those that ship with version 5.0 of the .NET SDK, add the following entry to your project file.</span></span>

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > <span data-ttu-id="183dc-193">`AnalysisLevel` プロパティの既定値は `latest` です。これは、より新しいバージョンの .NET SDK に移行するときに、常に最新のコード分析ルールを取得することを意味します。</span><span class="sxs-lookup"><span data-stu-id="183dc-193">The default value for the `AnalysisLevel` property is `latest`, which means you always get the latest code analysis rules as you move to newer versions of the .NET SDK.</span></span>

  <span data-ttu-id="183dc-194">詳細情報、および使用可能な値の一覧については、「[AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183dc-194">For more information, and to see a list of possible values, see [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).</span></span>

- <span data-ttu-id="183dc-195">[Microsoft.CodeAnalysis.NetAnalyzers NuGet パッケージ](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers)をインストールして、.NET SDK の更新プログラムからルールの更新を分離します。</span><span class="sxs-lookup"><span data-stu-id="183dc-195">Install the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) to decouple rule updates from .NET SDK updates.</span></span> <span data-ttu-id="183dc-196">.NET 5 以降をターゲットとするプロジェクトでは、パッケージをインストールすると、組み込みの SDK アナライザーがオフになります。</span><span class="sxs-lookup"><span data-stu-id="183dc-196">For projects that target .NET 5+, installing the package turns off the built-in SDK analyzers.</span></span> <span data-ttu-id="183dc-197">NuGet パッケージよりも新しいバージョンのアナライザー アセンブリが SDK に含まれている場合は、ビルド警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="183dc-197">You'll get a build warning if the SDK contains a newer analyzer assembly version than that of the NuGet package.</span></span> <span data-ttu-id="183dc-198">警告を無効にするには、`_SkipUpgradeNetAnalyzersNuGetWarning` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="183dc-198">To disable the warning, set the `_SkipUpgradeNetAnalyzersNuGetWarning` property to `true`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="183dc-199">Microsoft.CodeAnalysis.NetAnalyzers NuGet パッケージをインストールする場合は、プロジェクト ファイルまたは *Directory.Build.props* ファイルに [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="183dc-199">If you install the Microsoft.CodeAnalysis.NetAnalyzers NuGet package, you should not add the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to either your project file or a *Directory.Build.props* file.</span></span> <span data-ttu-id="183dc-200">NuGet パッケージがインストールされ、`EnableNETAnalyzers` プロパティが `true` に設定されると、ビルド警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="183dc-200">When the NuGet package is installed and the `EnableNETAnalyzers` property is set to `true`, a build warning is generated.</span></span>

## <a name="code-style-analysis"></a><span data-ttu-id="183dc-201">コードスタイルの分析</span><span class="sxs-lookup"><span data-stu-id="183dc-201">Code-style analysis</span></span>

<span data-ttu-id="183dc-202">"*コードスタイルの分析*" ("IDExxxx") ルールを使用すると、コードベースで一貫性のあるコードスタイルを定義および維持することができます。</span><span class="sxs-lookup"><span data-stu-id="183dc-202">*Code-style analysis* ("IDExxxx") rules enable you to define and maintain consistent code style in your codebase.</span></span> <span data-ttu-id="183dc-203">既定の有効化設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="183dc-203">The default enablement settings are:</span></span>

- <span data-ttu-id="183dc-204">コマンドライン ビルド: コードスタイルの分析は、既定でコマンドライン ビルドのすべての .NET プロジェクトに対して無効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-204">Command-line build: Code-style analysis is disabled, by default, for all .NET projects on command-line builds.</span></span>

  <span data-ttu-id="183dc-205">.NET 5.0 以降では、コマンド ラインと Visual Studio 内の両方で、[ビルド時にコードスタイルの分析を有効にする](#enable-on-build)ことができます。</span><span class="sxs-lookup"><span data-stu-id="183dc-205">Starting in .NET 5.0, you can [enable code-style analysis on build](#enable-on-build), both at the command line and inside Visual Studio.</span></span> <span data-ttu-id="183dc-206">コード スタイルに違反すると、"IDE" プレフィックスが付いた警告またはエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="183dc-206">Code style violations appear as warnings or errors with an "IDE" prefix.</span></span> <span data-ttu-id="183dc-207">これにより、ビルド時に一貫したコード スタイルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="183dc-207">This enables you to enforce consistent code styles at build time.</span></span>

- <span data-ttu-id="183dc-208">Visual Studio: コードスタイルの分析は、既定で Visual Studio 内のすべての .NET プロジェクトに対して[コード リファクタリングのクイック アクション](/visualstudio/ide/code-generation-in-visual-studio)として有効になっています。</span><span class="sxs-lookup"><span data-stu-id="183dc-208">Visual Studio: Code-style analysis is enabled, by default, for all .NET projects inside Visual Studio as [code refactoring quick actions](/visualstudio/ide/code-generation-in-visual-studio).</span></span>

<span data-ttu-id="183dc-209">コードスタイルの分析ルールの完全な一覧については、「[コードスタイル ルール](style-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183dc-209">For a full list of code-style analysis rules, see [Code style rules](style-rules/index.md).</span></span>

### <a name="enable-on-build"></a><span data-ttu-id="183dc-210">ビルド時に有効にする</span><span class="sxs-lookup"><span data-stu-id="183dc-210">Enable on build</span></span>

<span data-ttu-id="183dc-211">.NET 5.0 SDK 以降のバージョンでは、コマンドラインや Visual Studio でビルドするときに、コードスタイルの分析を有効にすることができます</span><span class="sxs-lookup"><span data-stu-id="183dc-211">With the .NET 5.0 SDK and later versions, you can enable code-style analysis when building from the command-line and in Visual Studio.</span></span> <span data-ttu-id="183dc-212">(ただし、パフォーマンス上の理由から、[いくつかのコードスタイル ルール](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95)は Visual Studio IDE にのみ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="183dc-212">(However, for performance reasons, [a handful of code-style rules](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) will still apply only in the Visual Studio IDE.)</span></span>

<span data-ttu-id="183dc-213">ビルド時にコードスタイルの分析を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="183dc-213">Follow these steps to enable code-style analysis on build:</span></span>

1. <span data-ttu-id="183dc-214">MSBuild プロパティ [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="183dc-214">Set the MSBuild property [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) to `true`.</span></span>

1. <span data-ttu-id="183dc-215">*.editorconfig* ファイルで、ビルド時に実行する各 "IDE" コード スタイル ルールを警告またはエラーとして [構成](configuration-options.md)します。</span><span class="sxs-lookup"><span data-stu-id="183dc-215">In an *.editorconfig* file, [configure](configuration-options.md) each "IDE" code style rule that you wish to run on build as a warning or an error.</span></span> <span data-ttu-id="183dc-216">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="183dc-216">For example:</span></span>

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   <span data-ttu-id="183dc-217">また、既定では、カテゴリ全体を警告またはエラーとして構成してから、ビルド時に実行しないカテゴリのルールを選択的にオフにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="183dc-217">Alternatively, you can configure an entire category to be a warning or error, by default, and then selectively turn off rules in that category that you don't want to run on build.</span></span> <span data-ttu-id="183dc-218">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="183dc-218">For example:</span></span>

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

> [!NOTE]
> <span data-ttu-id="183dc-219">コードスタイルの分析機能は試験段階にあり、.NET 5 リリースと .NET 6 リリースの間で変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="183dc-219">The code-style analysis feature is experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

## <a name="suppress-a-warning"></a><span data-ttu-id="183dc-220">警告を抑制する</span><span class="sxs-lookup"><span data-stu-id="183dc-220">Suppress a warning</span></span>

<span data-ttu-id="183dc-221">ルール違反を抑制する方法の 1 つとして、EditorConfig ファイルでそのルール ID の重要度オプションを `none` に設定します。</span><span class="sxs-lookup"><span data-stu-id="183dc-221">One way to suppress a rule violation is to set the severity option for that rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="183dc-222">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="183dc-222">For example:</span></span>

```ini
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="183dc-223">詳細情報、および警告を非表示にするその他の方法については、「[コード分析の警告を抑制する方法](suppress-warnings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183dc-223">For more information and other ways to suppress warnings, see [How to suppress code analysis warnings](suppress-warnings.md).</span></span>

## <a name="third-party-analyzers"></a><span data-ttu-id="183dc-224">サード パーティのアナライザー</span><span class="sxs-lookup"><span data-stu-id="183dc-224">Third-party analyzers</span></span>

<span data-ttu-id="183dc-225">公式の .NET アナライザーに加えて、[StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、[Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/)、[XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)、[Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/) などのサードパーティ製アナライザーをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="183dc-225">In addition to the official .NET analyzers, you can also install third party analyzers, such as [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), and [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).</span></span>

## <a name="see-also"></a><span data-ttu-id="183dc-226">関連項目</span><span class="sxs-lookup"><span data-stu-id="183dc-226">See also</span></span>

- [<span data-ttu-id="183dc-227">コード品質の分析ルールのリファレンス</span><span class="sxs-lookup"><span data-stu-id="183dc-227">Code quality analysis rule reference</span></span>](quality-rules/index.md)
- [<span data-ttu-id="183dc-228">コード スタイルの分析ルールのリファレンス</span><span class="sxs-lookup"><span data-stu-id="183dc-228">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="183dc-229">Visual Studio でのコード分析</span><span class="sxs-lookup"><span data-stu-id="183dc-229">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="183dc-230">.NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="183dc-230">.NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="183dc-231">チュートリアル: 最初のアナライザーとコード修正を作成する</span><span class="sxs-lookup"><span data-stu-id="183dc-231">Tutorial: Write your first analyzer and code fix</span></span>](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
