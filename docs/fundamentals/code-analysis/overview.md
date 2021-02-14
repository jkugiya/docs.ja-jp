---
title: .NET でのコード分析
titleSuffix: ''
description: .NET SDK のソースコード分析について説明します。
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: eb978d6af6695fd2e4b5473ac5c0dc216e726e52
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100459956"
---
# <a name="overview-of-net-source-code-analysis"></a><span data-ttu-id="d2378-103">.NET ソース コード分析の概要</span><span class="sxs-lookup"><span data-stu-id="d2378-103">Overview of .NET source code analysis</span></span>

<span data-ttu-id="d2378-104">.NET compiler platform (Roslyn) アナライザーは、コードの品質とスタイルの問題について、C# または Visual Basic コードを検査します。</span><span class="sxs-lookup"><span data-stu-id="d2378-104">.NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and style issues.</span></span> <span data-ttu-id="d2378-105">.NET 5.0 以降、これらのアナライザーは .NET SDK に含まれており、個別にインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d2378-105">Starting in .NET 5.0, these analyzers are included with the .NET SDK and you don't need to install them separately.</span></span> <span data-ttu-id="d2378-106">プロジェクトが .NET 5 以降を対象としている場合は、既定でコード分析が有効になります。</span><span class="sxs-lookup"><span data-stu-id="d2378-106">If your project targets .NET 5 or later, code analysis is enabled by default.</span></span> <span data-ttu-id="d2378-107">プロジェクトが .NET Core、.NET Standard、.NET Framework などの別の .NET 実装を対象としている場合は、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することによって、手動でコード分析を有効にする必要があり `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-107">If your project targets a different .NET implementation, for example, .NET Core, .NET Standard, or .NET Framework, you must manually enable code analysis by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span>

<span data-ttu-id="d2378-108">.NET 5 + SDK に移行しない場合、SDK 形式以外の .NET Framework プロジェクトを使用する場合、または NuGet パッケージベースのモデルを使用する場合は、 [Microsoft の CodeAnalysis. Netanalyzers NuGet パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)でアナライザーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2378-108">If you don't want to move to the .NET 5+ SDK, have a non-SDK-style .NET Framework project, or prefer a NuGet package-based model, the analyzers are also available in the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers).</span></span> <span data-ttu-id="d2378-109">オンデマンドバージョン更新には、パッケージベースのモデルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d2378-109">You might prefer a package-based model for on-demand version updates.</span></span>

> [!NOTE]
> <span data-ttu-id="d2378-110">.NET アナライザーは、ターゲットフレームワークに依存しません。</span><span class="sxs-lookup"><span data-stu-id="d2378-110">.NET analyzers are target-framework agnostic.</span></span> <span data-ttu-id="d2378-111">つまり、プロジェクトは特定の .NET 実装をターゲットにする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="d2378-111">That is, your project does not need to target a specific .NET implementation.</span></span> <span data-ttu-id="d2378-112">アナライザーは、やなど、以前のバージョンの .NET を対象とするプロジェクトでも機能し `net5.0` `netcoreapp3.1` `net472` ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-112">The analyzers work for projects that target `net5.0` as well as earlier .NET versions, such as `netcoreapp3.1` and `net472`.</span></span> <span data-ttu-id="d2378-113">ただし、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティを使用してコード分析を有効にするには、プロジェクトで [プロジェクト SDK](../../core/project-sdk/overview.md)を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2378-113">However, to enable code analysis using the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property, your project must reference a [project SDK](../../core/project-sdk/overview.md).</span></span>

<span data-ttu-id="d2378-114">ルール違反が analyzer によって検出されると、各ルールの [構成](configuration-options.md)方法に応じて、候補、警告、またはエラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="d2378-114">If rule violations are found by an analyzer, they're reported as a suggestion, warning, or error, depending on how each rule is [configured](configuration-options.md).</span></span> <span data-ttu-id="d2378-115">コード分析違反は、コンパイラエラーと区別するために "CA" または "IDE" というプレフィックスで示されます。</span><span class="sxs-lookup"><span data-stu-id="d2378-115">Code analysis violations appear with the prefix "CA" or "IDE" to differentiate them from compiler errors.</span></span>

## <a name="code-quality-analysis"></a><span data-ttu-id="d2378-116">コード品質の分析</span><span class="sxs-lookup"><span data-stu-id="d2378-116">Code quality analysis</span></span>

<span data-ttu-id="d2378-117">*コード品質分析* ("caxxxx") ルールは、セキュリティ、パフォーマンス、設計などの問題について、C# または Visual Basic コードを検査します。</span><span class="sxs-lookup"><span data-stu-id="d2378-117">*Code quality analysis* ("CAxxxx") rules inspect your C# or Visual Basic code for security, performance, design and other issues.</span></span> <span data-ttu-id="d2378-118">.NET 5.0 以降を対象とするプロジェクトでは、既定で分析が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d2378-118">Analysis is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="d2378-119">以前のバージョンの .NET を対象とするプロジェクトでは、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することにより、コード分析を有効にすることができ `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-119">You can enable code analysis on projects that target earlier .NET versions by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span> <span data-ttu-id="d2378-120">をに設定することにより、プロジェクトのコード分析を無効にすることもでき `EnableNETAnalyzers` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-120">You can also disable code analysis for your project by setting `EnableNETAnalyzers` to `false`.</span></span>

> [!TIP]
> <span data-ttu-id="d2378-121">Visual Studio を使用している場合:</span><span class="sxs-lookup"><span data-stu-id="d2378-121">If you're using Visual Studio:</span></span>
>
> - <span data-ttu-id="d2378-122">多くのアナライザールールには、問題を修正するために適用できる *コード修正プログラム* が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="d2378-122">Many analyzer rules have associated *code fixes* that you can apply to correct the problem.</span></span> <span data-ttu-id="d2378-123">コード修正は、電球アイコンメニューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2378-123">Code fixes are shown in the light bulb icon menu.</span></span>
> - <span data-ttu-id="d2378-124">コード分析を有効または無効にするには、ソリューションエクスプローラーでプロジェクトを右クリックし、[**プロパティ**  >  ] [**コード分析**] タブ > [ **.net アナライザーの有効化**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="d2378-124">You can enable or disable code analysis by right-clicking on a project in Solution Explorer and selecting **Properties** > **Code Analysis** tab > **Enable .NET analyzers**.</span></span>

### <a name="enabled-rules"></a><span data-ttu-id="d2378-125">有効なルール</span><span class="sxs-lookup"><span data-stu-id="d2378-125">Enabled rules</span></span>

<span data-ttu-id="d2378-126">次の規則は、既定では .NET 5.0 で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d2378-126">The following rules are enabled, by default, in .NET 5.0.</span></span>

| <span data-ttu-id="d2378-127">診断 ID</span><span class="sxs-lookup"><span data-stu-id="d2378-127">Diagnostic ID</span></span> | <span data-ttu-id="d2378-128">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="d2378-128">Category</span></span> | <span data-ttu-id="d2378-129">重大度</span><span class="sxs-lookup"><span data-stu-id="d2378-129">Severity</span></span> | <span data-ttu-id="d2378-130">[説明]</span><span class="sxs-lookup"><span data-stu-id="d2378-130">Description</span></span> |
| - | - | - | - |
| [<span data-ttu-id="d2378-131">CA1416</span><span class="sxs-lookup"><span data-stu-id="d2378-131">CA1416</span></span>](/visualstudio/code-quality/ca1416) | <span data-ttu-id="d2378-132">相互運用性</span><span class="sxs-lookup"><span data-stu-id="d2378-132">Interoperability</span></span> | <span data-ttu-id="d2378-133">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-133">Warning</span></span> | <span data-ttu-id="d2378-134">プラットフォーム互換性アナライザー</span><span class="sxs-lookup"><span data-stu-id="d2378-134">Platform compatibility analyzer</span></span> |
| [<span data-ttu-id="d2378-135">CA1417</span><span class="sxs-lookup"><span data-stu-id="d2378-135">CA1417</span></span>](/visualstudio/code-quality/ca1417) | <span data-ttu-id="d2378-136">相互運用性</span><span class="sxs-lookup"><span data-stu-id="d2378-136">Interoperability</span></span> | <span data-ttu-id="d2378-137">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-137">Warning</span></span> | <span data-ttu-id="d2378-138">`OutAttribute`P/invoke に文字列パラメーターを使用しない</span><span class="sxs-lookup"><span data-stu-id="d2378-138">Do not use `OutAttribute` on string parameters for P/Invokes</span></span> |
| [<span data-ttu-id="d2378-139">CA1831</span><span class="sxs-lookup"><span data-stu-id="d2378-139">CA1831</span></span>](/visualstudio/code-quality/ca1831) | <span data-ttu-id="d2378-140">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="d2378-140">Performance</span></span> | <span data-ttu-id="d2378-141">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-141">Warning</span></span> | <span data-ttu-id="d2378-142">`AsSpan`必要に応じて、範囲ベースのインデクサーの代わりに文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2378-142">Use `AsSpan` instead of range-based indexers for string when appropriate</span></span> |
| [<span data-ttu-id="d2378-143">CA2013</span><span class="sxs-lookup"><span data-stu-id="d2378-143">CA2013</span></span>](/visualstudio/code-quality/ca2013) | <span data-ttu-id="d2378-144">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="d2378-144">Reliability</span></span> | <span data-ttu-id="d2378-145">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-145">Warning</span></span> | <span data-ttu-id="d2378-146">`ReferenceEquals`値型では使用しない</span><span class="sxs-lookup"><span data-stu-id="d2378-146">Do not use `ReferenceEquals` with value types</span></span> |
| [<span data-ttu-id="d2378-147">CA2014</span><span class="sxs-lookup"><span data-stu-id="d2378-147">CA2014</span></span>](/visualstudio/code-quality/ca2014) | <span data-ttu-id="d2378-148">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="d2378-148">Reliability</span></span> | <span data-ttu-id="d2378-149">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-149">Warning</span></span> | <span data-ttu-id="d2378-150">In ループを使用しない `stackalloc`</span><span class="sxs-lookup"><span data-stu-id="d2378-150">Do not use `stackalloc` in loops</span></span> |
| [<span data-ttu-id="d2378-151">CA2015</span><span class="sxs-lookup"><span data-stu-id="d2378-151">CA2015</span></span>](/visualstudio/code-quality/ca2015) | <span data-ttu-id="d2378-152">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="d2378-152">Reliability</span></span> | <span data-ttu-id="d2378-153">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-153">Warning</span></span> | <span data-ttu-id="d2378-154">から派生した型にはファイナライザーを定義しないでください。 <xref:System.Buffers.MemoryManager%601></span><span class="sxs-lookup"><span data-stu-id="d2378-154">Do not define finalizers for types derived from <xref:System.Buffers.MemoryManager%601></span></span> |
| [<span data-ttu-id="d2378-155">CA2200</span><span class="sxs-lookup"><span data-stu-id="d2378-155">CA2200</span></span>](/visualstudio/code-quality/ca2200) | <span data-ttu-id="d2378-156">使用</span><span class="sxs-lookup"><span data-stu-id="d2378-156">Usage</span></span> | <span data-ttu-id="d2378-157">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-157">Warning</span></span> | <span data-ttu-id="d2378-158">スタック詳細を保持するために再度スローします</span><span class="sxs-lookup"><span data-stu-id="d2378-158">Rethrow to preserve stack details</span></span>
| [<span data-ttu-id="d2378-159">CA2247</span><span class="sxs-lookup"><span data-stu-id="d2378-159">CA2247</span></span>](/visualstudio/code-quality/ca2247) | <span data-ttu-id="d2378-160">使用</span><span class="sxs-lookup"><span data-stu-id="d2378-160">Usage</span></span> | <span data-ttu-id="d2378-161">警告</span><span class="sxs-lookup"><span data-stu-id="d2378-161">Warning</span></span> | <span data-ttu-id="d2378-162">Taskのソースコンストラクターに渡される引数は、ではなく列挙型にする必要があり <xref:System.Threading.Tasks.TaskCreationOptions> ます <xref:System.Threading.Tasks.TaskContinuationOptions></span><span class="sxs-lookup"><span data-stu-id="d2378-162">Argument passed to TaskCompletionSource constructor should be <xref:System.Threading.Tasks.TaskCreationOptions> enum instead of <xref:System.Threading.Tasks.TaskContinuationOptions></span></span> |

<span data-ttu-id="d2378-163">これらのルールを無効にするか、エラーに昇格するように、これらのルールの重大度を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="d2378-163">You can change the severity of these rules to disable them or elevate them to errors.</span></span> <span data-ttu-id="d2378-164">[さらに多くのルールを有効に](#enable-additional-rules)することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2378-164">You can also [enable more rules](#enable-additional-rules).</span></span>

- <span data-ttu-id="d2378-165">各 .NET SDK バージョンに含まれる規則の一覧については、「 [Analyzer のリリース](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2378-165">For a list of rules that are included with each .NET SDK version, see [Analyzer releases](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>
- <span data-ttu-id="d2378-166">すべてのコード品質ルールの一覧については、「 [コード品質ルール](quality-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2378-166">For a list of all the code quality rules, see [Code quality rules](quality-rules/index.md).</span></span>

### <a name="enable-additional-rules"></a><span data-ttu-id="d2378-167">追加のルールを有効にする</span><span class="sxs-lookup"><span data-stu-id="d2378-167">Enable additional rules</span></span>

<span data-ttu-id="d2378-168">*分析モード* とは、定義されていないコード分析構成を意味します。この構成では、すべての規則が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="d2378-168">*Analysis mode* refers to a predefined code analysis configuration where none, some, or all rules are enabled.</span></span> <span data-ttu-id="d2378-169">既定の分析モードでは、いくつかのルールのみが [ビルド警告として有効になり](#enabled-rules)ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-169">In the default analysis mode, only a small number of rules are [enabled as build warnings](#enabled-rules).</span></span> <span data-ttu-id="d2378-170">プロジェクトファイルでプロパティを設定することにより、プロジェクトの分析モードを変更でき [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-170">You can change the analysis mode for your project by setting the [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) property in the project file.</span></span> <span data-ttu-id="d2378-171">使用できる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2378-171">The allowable values are:</span></span>

| <span data-ttu-id="d2378-172">[値]</span><span class="sxs-lookup"><span data-stu-id="d2378-172">Value</span></span> | <span data-ttu-id="d2378-173">[説明]</span><span class="sxs-lookup"><span data-stu-id="d2378-173">Description</span></span> |
| - | - |
| `AllDisabledByDefault` | <span data-ttu-id="d2378-174">これは最も控えめなモードです。</span><span class="sxs-lookup"><span data-stu-id="d2378-174">This is the most conservative mode.</span></span> <span data-ttu-id="d2378-175">既定では、すべてのルールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d2378-175">All rules are disabled by default.</span></span> <span data-ttu-id="d2378-176">個々のルールを選択的に[オプトイン](configuration-options.md)して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d2378-176">You can selectively [opt into](configuration-options.md) individual rules to enable them.</span></span><br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | <span data-ttu-id="d2378-177">これは最も積極的なモードです。</span><span class="sxs-lookup"><span data-stu-id="d2378-177">This is the most aggressive mode.</span></span> <span data-ttu-id="d2378-178">すべてのルールがビルド警告として有効になります。</span><span class="sxs-lookup"><span data-stu-id="d2378-178">All rules are enabled as build warnings.</span></span> <span data-ttu-id="d2378-179">個別 [の](configuration-options.md) ルールを選択して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d2378-179">You can selectively [opt out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | <span data-ttu-id="d2378-180">既定のモードでは、いくつかのルールが警告として有効になっています。その他のルールは、対応するコード修正によって Visual Studio IDE 候補としてのみ有効になり、残りは完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="d2378-180">The default mode, where a handful of rules are enabled as warnings, others are enabled only as Visual Studio IDE suggestions with corresponding code fixes, and the rest are disabled completely.</span></span> <span data-ttu-id="d2378-181">個々 [の](configuration-options.md) ルールを選択して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d2378-181">You can selectively [opt into or out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>Default</AnalysisMode>` |

<span data-ttu-id="d2378-182">使用可能な各ルールの既定の重要度と、ルールが既定の分析モードで有効になっているかどうかを確認するには、 [ルールの完全な一覧](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2378-182">To find the default severity for each available rule and whether or not the rule is enabled in the default analysis mode, see the [full list of rules](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>

### <a name="treat-warnings-as-errors"></a><span data-ttu-id="d2378-183">警告をエラーとして扱う</span><span class="sxs-lookup"><span data-stu-id="d2378-183">Treat warnings as errors</span></span>

<span data-ttu-id="d2378-184">`-warnaserror`プロジェクトをビルドするときにフラグを使用すると、コード分析のすべての警告もエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="d2378-184">If you use the `-warnaserror` flag when you build your projects, all code analysis warnings are also treated as errors.</span></span> <span data-ttu-id="d2378-185">コード品質警告 (CAxxxx) がの存在でエラーとして扱われないようにするには `-warnaserror` 、 `CodeAnalysisTreatWarningsAsErrors` プロジェクトファイルで MSBuild プロパティをに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-185">If you do not want code quality warnings (CAxxxx) to be treated as errors in presence of `-warnaserror`, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="d2378-186">コード分析の警告は引き続き表示されますが、ビルドが破損することはありません。</span><span class="sxs-lookup"><span data-stu-id="d2378-186">You'll still see any code analysis warnings, but they won't break your build.</span></span>

### <a name="latest-updates"></a><span data-ttu-id="d2378-187">最新の更新プログラム</span><span class="sxs-lookup"><span data-stu-id="d2378-187">Latest updates</span></span>

<span data-ttu-id="d2378-188">既定では、新しいバージョンの .NET SDK にアップグレードするときに、最新のコード分析規則と既定の規則の重大度を取得します。</span><span class="sxs-lookup"><span data-stu-id="d2378-188">By default, you'll get the latest code analysis rules and default rule severities as you upgrade to newer versions of the .NET SDK.</span></span> <span data-ttu-id="d2378-189">この動作が望ましくない場合、たとえば、新しいルールが有効になっていないか無効になっていることを確認する場合は、次のいずれかの方法でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d2378-189">If you don't want this behavior, for example, if you want to ensure that no new rules are enabled or disabled, you can override it in one of the following ways:</span></span>

- <span data-ttu-id="d2378-190">`AnalysisLevel`MSBuild プロパティを特定の値に設定して、そのセットに警告をロックします。</span><span class="sxs-lookup"><span data-stu-id="d2378-190">Set the `AnalysisLevel` MSBuild property to a specific value to lock the warnings to that set.</span></span> <span data-ttu-id="d2378-191">新しい SDK にアップグレードすると、これらの警告のバグ修正が引き続き行われますが、新しい警告は有効になりません。また、既存の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="d2378-191">When you upgrade to a newer SDK, you'll still get bug fixes for those warnings, but no new warnings will be enabled and no existing warnings will be disabled.</span></span> <span data-ttu-id="d2378-192">たとえば、.NET SDK のバージョン5.0 に付属するルールのセットをロックするには、プロジェクトファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="d2378-192">For example, to lock the set of rules to those that ship with version 5.0 of the .NET SDK, add the following entry to your project file.</span></span>

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > <span data-ttu-id="d2378-193">プロパティの既定値 `AnalysisLevel` はです `latest` 。これは、.net SDK の新しいバージョンに移行するときに、常に最新のコード分析規則を取得することを意味します。</span><span class="sxs-lookup"><span data-stu-id="d2378-193">The default value for the `AnalysisLevel` property is `latest`, which means you always get the latest code analysis rules as you move to newer versions of the .NET SDK.</span></span>

  <span data-ttu-id="d2378-194">詳細については、および使用可能な値の一覧については、「 [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2378-194">For more information, and to see a list of possible values, see [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).</span></span>

- <span data-ttu-id="d2378-195">.NET SDK の更新プログラムから規則の更新を分離するには、 [Microsoft Codeanalysis NuGet パッケージ](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="d2378-195">Install the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) to decouple rule updates from .NET SDK updates.</span></span> <span data-ttu-id="d2378-196">パッケージをインストールすると、組み込みの SDK アナライザーが無効になり、SDK に NuGet パッケージよりも新しいバージョンの analyzer アセンブリが含まれている場合は、ビルドの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d2378-196">Installing the package turns off the built-in SDK analyzers and generates a build warning if the SDK contains a newer analyzer assembly version than that of the NuGet package.</span></span>

## <a name="code-style-analysis"></a><span data-ttu-id="d2378-197">コードスタイルの分析</span><span class="sxs-lookup"><span data-stu-id="d2378-197">Code-style analysis</span></span>

<span data-ttu-id="d2378-198">*コードスタイルの分析* ("ide xxxx") 規則を使用すると、コードベースで一貫性のあるコードスタイルを定義および維持できます。</span><span class="sxs-lookup"><span data-stu-id="d2378-198">*Code-style analysis* ("IDExxxx") rules enable you to define and maintain consistent code style in your codebase.</span></span> <span data-ttu-id="d2378-199">既定の有効化設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2378-199">The default enablement settings are:</span></span>

- <span data-ttu-id="d2378-200">コマンドラインビルド: コマンドラインビルドのすべての .NET プロジェクトに対して、コードスタイルの分析が既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d2378-200">Command-line build: Code-style analysis is disabled, by default, for all .NET projects on command-line builds.</span></span>

  <span data-ttu-id="d2378-201">.NET 5.0 以降では、コマンドラインと Visual Studio の両方で [ビルドに対してコードスタイルの分析を有効に](#enable-on-build)することができます。</span><span class="sxs-lookup"><span data-stu-id="d2378-201">Starting in .NET 5.0, you can [enable code-style analysis on build](#enable-on-build), both at the command line and inside Visual Studio.</span></span> <span data-ttu-id="d2378-202">コードスタイル違反は、"IDE" プレフィックスが付いた警告またはエラーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2378-202">Code style violations appear as warnings or errors with an "IDE" prefix.</span></span> <span data-ttu-id="d2378-203">これにより、ビルド時に一貫したコードスタイルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="d2378-203">This enables you to enforce consistent code styles at build time.</span></span>

- <span data-ttu-id="d2378-204">Visual Studio: コードスタイルの分析は、Visual Studio 内のすべての .NET プロジェクトに対して、 [コードリファクタリングのクイックアクション](/visualstudio/ide/code-generation-in-visual-studio)として既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d2378-204">Visual Studio: Code-style analysis is enabled, by default, for all .NET projects inside Visual Studio as [code refactoring quick actions](/visualstudio/ide/code-generation-in-visual-studio).</span></span>

<span data-ttu-id="d2378-205">コードスタイルの分析規則の完全な一覧については、「 [コードスタイル規則](style-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2378-205">For a full list of code-style analysis rules, see [Code style rules](style-rules/index.md).</span></span>

### <a name="enable-on-build"></a><span data-ttu-id="d2378-206">ビルドで有効にする</span><span class="sxs-lookup"><span data-stu-id="d2378-206">Enable on build</span></span>

<span data-ttu-id="d2378-207">.NET 5.0 SDK 以降のバージョンでは、コマンドラインや Visual Studio からビルドするときに、コードスタイルの分析を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d2378-207">With the .NET 5.0 SDK and later versions, you can enable code-style analysis when building from the command-line and in Visual Studio.</span></span> <span data-ttu-id="d2378-208">(ただし、パフォーマンス上の理由から、 [いくつかのコードスタイルルール](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) は、VISUAL Studio IDE にのみ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="d2378-208">(However, for performance reasons, [a handful of code-style rules](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) will still apply only in the Visual Studio IDE.)</span></span>

<span data-ttu-id="d2378-209">ビルドでコードスタイルの分析を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d2378-209">Follow these steps to enable code-style analysis on build:</span></span>

1. <span data-ttu-id="d2378-210">MSBuild プロパティ [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) をに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d2378-210">Set the MSBuild property [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) to `true`.</span></span>

1. <span data-ttu-id="d2378-211">*Editorconfig* ファイルで、ビルド時に実行する各 "IDE" コードスタイルルールを警告またはエラーとして [構成](configuration-options.md)します。</span><span class="sxs-lookup"><span data-stu-id="d2378-211">In an *.editorconfig* file, [configure](configuration-options.md) each "IDE" code style rule that you wish to run on build as a warning or an error.</span></span> <span data-ttu-id="d2378-212">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d2378-212">For example:</span></span>

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   <span data-ttu-id="d2378-213">また、既定では、カテゴリ全体を警告またはエラーとして構成してから、ビルドで実行したくないカテゴリの規則を選択的にオフにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d2378-213">Alternatively, you can configure an entire category to be a warning or error, by default, and then selectively turn off rules in that category that you don't want to run on build.</span></span> <span data-ttu-id="d2378-214">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d2378-214">For example:</span></span>

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

> [!NOTE]
> <span data-ttu-id="d2378-215">コードスタイルの分析機能は試験段階であり、.NET 5 リリースと .NET 6 リリース間で変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d2378-215">The code-style analysis feature is experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

## <a name="suppress-a-warning"></a><span data-ttu-id="d2378-216">警告の非表示</span><span class="sxs-lookup"><span data-stu-id="d2378-216">Suppress a warning</span></span>

<span data-ttu-id="d2378-217">規則違反を抑制する方法の1つとして、 `none` EditorConfig ファイル内の規則 ID の重大度オプションをに設定します。</span><span class="sxs-lookup"><span data-stu-id="d2378-217">One way to suppress a rule violation is to set the severity option for that rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="d2378-218">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d2378-218">For example:</span></span>

```ini
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="d2378-219">警告を非表示にするための詳細およびその他の方法については、「 [コード分析の警告を抑制する方法](suppress-warnings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2378-219">For more information and other ways to suppress warnings, see [How to suppress code analysis warnings](suppress-warnings.md).</span></span>

## <a name="third-party-analyzers"></a><span data-ttu-id="d2378-220">サード パーティのアナライザー</span><span class="sxs-lookup"><span data-stu-id="d2378-220">Third-party analyzers</span></span>

<span data-ttu-id="d2378-221">公式の .NET アナライザーに加えて、 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Rosl/ator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [Xunit](https://www.nuget.org/packages/xunit.analyzers/) [Analyzer、sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)などのサードパーティ製アナライザーをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d2378-221">In addition to the official .NET analyzers, you can also install third party analyzers, such as [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), and [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2378-222">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2378-222">See also</span></span>

- [<span data-ttu-id="d2378-223">コード品質分析ルールのリファレンス</span><span class="sxs-lookup"><span data-stu-id="d2378-223">Code quality analysis rule reference</span></span>](quality-rules/index.md)
- [<span data-ttu-id="d2378-224">コードスタイル分析規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="d2378-224">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="d2378-225">Visual Studio でのコード分析</span><span class="sxs-lookup"><span data-stu-id="d2378-225">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="d2378-226">.NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="d2378-226">.NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="d2378-227">チュートリアル: 最初のアナライザーとコード修正を作成する</span><span class="sxs-lookup"><span data-stu-id="d2378-227">Tutorial: Write your first analyzer and code fix</span></span>](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
