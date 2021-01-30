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
ms.openlocfilehash: efc440adb59da1ef9838ec5445d9c55544c14380
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216474"
---
# <a name="overview-of-net-source-code-analysis"></a><span data-ttu-id="d490e-103">.NET ソース コード分析の概要</span><span class="sxs-lookup"><span data-stu-id="d490e-103">Overview of .NET source code analysis</span></span>

<span data-ttu-id="d490e-104">.NET のコンパイラ プラットフォーム (Roslyn) アナライザーでは、お使いの C# または Visual Basic コードについて、コード品質やコード スタイルに関する問題を検査できます。</span><span class="sxs-lookup"><span data-stu-id="d490e-104">.NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="d490e-105">.NET 5.0 以降、これらのアナライザーは .NET SDK に含まれており、個別にインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d490e-105">Starting in .NET 5.0, these analyzers are included with the .NET SDK and you don't need to install them separately.</span></span> <span data-ttu-id="d490e-106">プロジェクトが .NET 5 以降を対象としている場合は、既定でコード分析が有効になります。</span><span class="sxs-lookup"><span data-stu-id="d490e-106">If your project targets .NET 5 or later, code analysis is enabled by default.</span></span> <span data-ttu-id="d490e-107">プロジェクトが .NET Core、.NET Standard、.NET Framework などの別の .NET 実装をターゲットにしている場合は、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することによって、手動でコード分析を有効にする必要があり `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d490e-107">If your project target a different .NET implementation, for example, .NET Core, .NET Standard, or .NET Framework, you must manually enable code analysis by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span>

<span data-ttu-id="d490e-108">.NET 5 + SDK に移行しない場合、または NuGet パッケージベースのモデルを使用する場合は、 [Microsoft の CodeAnalysis. Netanalyzers nuget パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)でアナライザーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d490e-108">If you don't want to move to the .NET 5+ SDK or if you prefer a NuGet package-based model, the analyzers are also available in the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers).</span></span> <span data-ttu-id="d490e-109">オンデマンドバージョン更新には、パッケージベースのモデルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d490e-109">You might prefer a package-based model for on-demand version updates.</span></span>

> [!NOTE]
> <span data-ttu-id="d490e-110">.NET アナライザーは、ターゲットフレームワークに依存しません。</span><span class="sxs-lookup"><span data-stu-id="d490e-110">.NET analyzers are target-framework agnostic.</span></span> <span data-ttu-id="d490e-111">つまり、プロジェクトは特定の .NET 実装をターゲットにする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="d490e-111">That is, your project does not need to target a specific .NET implementation.</span></span> <span data-ttu-id="d490e-112">アナライザーは、やなど、以前のバージョンの .NET を対象とするプロジェクトでも機能し `net5.0` `netcoreapp3.1` `net472` ます。</span><span class="sxs-lookup"><span data-stu-id="d490e-112">The analyzers work for projects that target `net5.0` as well as earlier .NET versions, such as `netcoreapp3.1` and `net472`.</span></span>

<span data-ttu-id="d490e-113">ルール違反が analyzer によって検出されると、各ルールの [構成](configuration-options.md)方法に応じて、候補、警告、またはエラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="d490e-113">If rule violations are found by an analyzer, they're reported as a suggestion, warning, or error, depending on how each rule is [configured](configuration-options.md).</span></span> <span data-ttu-id="d490e-114">コード分析違反は、コンパイラエラーと区別するために "CA" または "IDE" というプレフィックスで示されます。</span><span class="sxs-lookup"><span data-stu-id="d490e-114">Code analysis violations appear with the prefix "CA" or "IDE" to differentiate them from compiler errors.</span></span>

## <a name="code-quality-analysis"></a><span data-ttu-id="d490e-115">コード品質の分析</span><span class="sxs-lookup"><span data-stu-id="d490e-115">Code quality analysis</span></span>

<span data-ttu-id="d490e-116">*コード品質分析* ("caxxxx") ルールは、セキュリティ、パフォーマンス、設計などの問題について、C# または Visual Basic コードを検査します。</span><span class="sxs-lookup"><span data-stu-id="d490e-116">*Code quality analysis* ("CAxxxx") rules inspect your C# or Visual Basic code for security, performance, design and other issues.</span></span> <span data-ttu-id="d490e-117">.NET 5.0 以降を対象とするプロジェクトでは、既定で分析が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d490e-117">Analysis is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="d490e-118">以前のバージョンの .NET を対象とするプロジェクトでは、 [Enablenetanalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) プロパティをに設定することにより、コード分析を有効にすることができ `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d490e-118">You can enable code analysis on projects that target earlier .NET versions by setting the [EnableNETAnalyzers](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) property to `true`.</span></span> <span data-ttu-id="d490e-119">をに設定することにより、プロジェクトのコード分析を無効にすることもでき `EnableNETAnalyzers` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="d490e-119">You can also disable code analysis for your project by setting `EnableNETAnalyzers` to `false`.</span></span>

> [!TIP]
> <span data-ttu-id="d490e-120">Visual Studio を使用している場合:</span><span class="sxs-lookup"><span data-stu-id="d490e-120">If you're using Visual Studio:</span></span>
>
> - <span data-ttu-id="d490e-121">多くのアナライザールールには、問題を修正するために適用できる *コード修正プログラム* が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="d490e-121">Many analyzer rules have associated *code fixes* that you can apply to correct the problem.</span></span> <span data-ttu-id="d490e-122">コード修正は、電球アイコンメニューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d490e-122">Code fixes are shown in the light bulb icon menu.</span></span>
> - <span data-ttu-id="d490e-123">コード分析を有効または無効にするには、ソリューションエクスプローラーでプロジェクトを右クリックし、[**プロパティ**  >  ] [**コード分析**] タブ > [ **.net アナライザーの有効化**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="d490e-123">You can enable or disable code analysis by right-clicking on a project in Solution Explorer and selecting **Properties** > **Code Analysis** tab > **Enable .NET analyzers**.</span></span>

### <a name="enabled-rules"></a><span data-ttu-id="d490e-124">有効なルール</span><span class="sxs-lookup"><span data-stu-id="d490e-124">Enabled rules</span></span>

<span data-ttu-id="d490e-125">次の規則は、既定では .NET 5.0 で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d490e-125">The following rules are enabled, by default, in .NET 5.0.</span></span>

| <span data-ttu-id="d490e-126">診断 ID</span><span class="sxs-lookup"><span data-stu-id="d490e-126">Diagnostic ID</span></span> | <span data-ttu-id="d490e-127">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="d490e-127">Category</span></span> | <span data-ttu-id="d490e-128">重大度</span><span class="sxs-lookup"><span data-stu-id="d490e-128">Severity</span></span> | <span data-ttu-id="d490e-129">説明</span><span class="sxs-lookup"><span data-stu-id="d490e-129">Description</span></span> |
| - | - | - | - |
| [<span data-ttu-id="d490e-130">CA1416</span><span class="sxs-lookup"><span data-stu-id="d490e-130">CA1416</span></span>](/visualstudio/code-quality/ca1416) | <span data-ttu-id="d490e-131">相互運用性</span><span class="sxs-lookup"><span data-stu-id="d490e-131">Interoperability</span></span> | <span data-ttu-id="d490e-132">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-132">Warning</span></span> | <span data-ttu-id="d490e-133">プラットフォーム互換性アナライザー</span><span class="sxs-lookup"><span data-stu-id="d490e-133">Platform compatibility analyzer</span></span> |
| [<span data-ttu-id="d490e-134">CA1417</span><span class="sxs-lookup"><span data-stu-id="d490e-134">CA1417</span></span>](/visualstudio/code-quality/ca1417) | <span data-ttu-id="d490e-135">相互運用性</span><span class="sxs-lookup"><span data-stu-id="d490e-135">Interoperability</span></span> | <span data-ttu-id="d490e-136">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-136">Warning</span></span> | <span data-ttu-id="d490e-137">`OutAttribute`P/invoke に文字列パラメーターを使用しない</span><span class="sxs-lookup"><span data-stu-id="d490e-137">Do not use `OutAttribute` on string parameters for P/Invokes</span></span> |
| [<span data-ttu-id="d490e-138">CA1831</span><span class="sxs-lookup"><span data-stu-id="d490e-138">CA1831</span></span>](/visualstudio/code-quality/ca1831) | <span data-ttu-id="d490e-139">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="d490e-139">Performance</span></span> | <span data-ttu-id="d490e-140">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-140">Warning</span></span> | <span data-ttu-id="d490e-141">`AsSpan`必要に応じて、範囲ベースのインデクサーの代わりに文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="d490e-141">Use `AsSpan` instead of range-based indexers for string when appropriate</span></span> |
| [<span data-ttu-id="d490e-142">CA2013</span><span class="sxs-lookup"><span data-stu-id="d490e-142">CA2013</span></span>](/visualstudio/code-quality/ca2013) | <span data-ttu-id="d490e-143">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="d490e-143">Reliability</span></span> | <span data-ttu-id="d490e-144">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-144">Warning</span></span> | <span data-ttu-id="d490e-145">`ReferenceEquals`値型では使用しない</span><span class="sxs-lookup"><span data-stu-id="d490e-145">Do not use `ReferenceEquals` with value types</span></span> |
| [<span data-ttu-id="d490e-146">CA2014</span><span class="sxs-lookup"><span data-stu-id="d490e-146">CA2014</span></span>](/visualstudio/code-quality/ca2014) | <span data-ttu-id="d490e-147">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="d490e-147">Reliability</span></span> | <span data-ttu-id="d490e-148">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-148">Warning</span></span> | <span data-ttu-id="d490e-149">In ループを使用しない `stackalloc`</span><span class="sxs-lookup"><span data-stu-id="d490e-149">Do not use `stackalloc` in loops</span></span> |
| [<span data-ttu-id="d490e-150">CA2015</span><span class="sxs-lookup"><span data-stu-id="d490e-150">CA2015</span></span>](/visualstudio/code-quality/ca2015) | <span data-ttu-id="d490e-151">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="d490e-151">Reliability</span></span> | <span data-ttu-id="d490e-152">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-152">Warning</span></span> | <span data-ttu-id="d490e-153">から派生した型にはファイナライザーを定義しないでください。 <xref:System.Buffers.MemoryManager%601></span><span class="sxs-lookup"><span data-stu-id="d490e-153">Do not define finalizers for types derived from <xref:System.Buffers.MemoryManager%601></span></span> |
| [<span data-ttu-id="d490e-154">CA2200</span><span class="sxs-lookup"><span data-stu-id="d490e-154">CA2200</span></span>](/visualstudio/code-quality/ca2200) | <span data-ttu-id="d490e-155">使用法</span><span class="sxs-lookup"><span data-stu-id="d490e-155">Usage</span></span> | <span data-ttu-id="d490e-156">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-156">Warning</span></span> | <span data-ttu-id="d490e-157">スタック詳細を保持するために再度スローします</span><span class="sxs-lookup"><span data-stu-id="d490e-157">Rethrow to preserve stack details</span></span>
| [<span data-ttu-id="d490e-158">CA2247</span><span class="sxs-lookup"><span data-stu-id="d490e-158">CA2247</span></span>](/visualstudio/code-quality/ca2247) | <span data-ttu-id="d490e-159">使用法</span><span class="sxs-lookup"><span data-stu-id="d490e-159">Usage</span></span> | <span data-ttu-id="d490e-160">警告</span><span class="sxs-lookup"><span data-stu-id="d490e-160">Warning</span></span> | <span data-ttu-id="d490e-161">Taskのソースコンストラクターに渡される引数は、ではなく列挙型にする必要があり <xref:System.Threading.Tasks.TaskCreationOptions> ます <xref:System.Threading.Tasks.TaskContinuationOptions></span><span class="sxs-lookup"><span data-stu-id="d490e-161">Argument passed to TaskCompletionSource constructor should be <xref:System.Threading.Tasks.TaskCreationOptions> enum instead of <xref:System.Threading.Tasks.TaskContinuationOptions></span></span> |

<span data-ttu-id="d490e-162">これらのルールを無効にするか、エラーに昇格するように、これらのルールの重大度を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="d490e-162">You can change the severity of these rules to disable them or elevate them to errors.</span></span> <span data-ttu-id="d490e-163">[さらに多くのルールを有効に](#enable-additional-rules)することもできます。</span><span class="sxs-lookup"><span data-stu-id="d490e-163">You can also [enable more rules](#enable-additional-rules).</span></span>

- <span data-ttu-id="d490e-164">各 .NET SDK バージョンに含まれる規則の一覧については、「 [Analyzer のリリース](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d490e-164">For a list of rules that are included with each .NET SDK version, see [Analyzer releases](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>
- <span data-ttu-id="d490e-165">すべてのコード品質ルールの一覧については、「 [コード品質ルール](quality-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d490e-165">For a list of all the code quality rules, see [Code quality rules](quality-rules/index.md).</span></span>

### <a name="enable-additional-rules"></a><span data-ttu-id="d490e-166">追加のルールを有効にする</span><span class="sxs-lookup"><span data-stu-id="d490e-166">Enable additional rules</span></span>

<span data-ttu-id="d490e-167">*分析モード* とは、定義されていないコード分析構成を意味します。この構成では、すべての規則が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="d490e-167">*Analysis mode* refers to a predefined code analysis configuration where none, some, or all rules are enabled.</span></span> <span data-ttu-id="d490e-168">既定の分析モードでは、いくつかのルールのみが [ビルド警告として有効になり](#enabled-rules)ます。</span><span class="sxs-lookup"><span data-stu-id="d490e-168">In the default analysis mode, only a small number of rules are [enabled as build warnings](#enabled-rules).</span></span> <span data-ttu-id="d490e-169">プロジェクトファイルの [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) プロパティを設定することにより、プロジェクトの分析モードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d490e-169">You can change the analysis mode for your project by setting the [AnalysisMode](../../core/project-sdk/msbuild-props.md#analysismode) property in the project file.</span></span> <span data-ttu-id="d490e-170">使用できる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d490e-170">The allowable values are:</span></span>

| <span data-ttu-id="d490e-171">値</span><span class="sxs-lookup"><span data-stu-id="d490e-171">Value</span></span> | <span data-ttu-id="d490e-172">説明</span><span class="sxs-lookup"><span data-stu-id="d490e-172">Description</span></span> |
| - | - |
| `AllDisabledByDefault` | <span data-ttu-id="d490e-173">これは最も控えめなモードです。</span><span class="sxs-lookup"><span data-stu-id="d490e-173">This is the most conservative mode.</span></span> <span data-ttu-id="d490e-174">既定では、すべてのルールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d490e-174">All rules are disabled by default.</span></span> <span data-ttu-id="d490e-175">個々のルールを選択的に[オプトイン](configuration-options.md)して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d490e-175">You can selectively [opt into](configuration-options.md) individual rules to enable them.</span></span><br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | <span data-ttu-id="d490e-176">これは最も積極的なモードです。</span><span class="sxs-lookup"><span data-stu-id="d490e-176">This is the most aggressive mode.</span></span> <span data-ttu-id="d490e-177">すべてのルールがビルド警告として有効になります。</span><span class="sxs-lookup"><span data-stu-id="d490e-177">All rules are enabled as build warnings.</span></span> <span data-ttu-id="d490e-178">個別 [の](configuration-options.md) ルールを選択して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d490e-178">You can selectively [opt out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | <span data-ttu-id="d490e-179">既定のモードでは、いくつかのルールが警告として有効になっています。その他のルールは、対応するコード修正によって Visual Studio IDE 候補としてのみ有効になり、残りは完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="d490e-179">The default mode, where a handful of rules are enabled as warnings, others are enabled only as Visual Studio IDE suggestions with corresponding code fixes, and the rest are disabled completely.</span></span> <span data-ttu-id="d490e-180">個々 [の](configuration-options.md) ルールを選択して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d490e-180">You can selectively [opt into or out of](configuration-options.md) individual rules to disable them.</span></span><br /><br />`<AnalysisMode>Default</AnalysisMode>` |

<span data-ttu-id="d490e-181">使用可能な各ルールの既定の重要度と、ルールが既定の分析モードで有効になっているかどうかを確認するには、 [ルールの完全な一覧](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d490e-181">To find the default severity for each available rule and whether or not the rule is enabled in the default analysis mode, see the [full list of rules](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span>

### <a name="treat-warnings-as-errors"></a><span data-ttu-id="d490e-182">警告をエラーとして扱う</span><span class="sxs-lookup"><span data-stu-id="d490e-182">Treat warnings as errors</span></span>

<span data-ttu-id="d490e-183">`-warnaserror`プロジェクトをビルドするときにフラグを使用すると、コード分析のすべての警告もエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="d490e-183">If you use the `-warnaserror` flag when you build your projects, all code analysis warnings are also treated as errors.</span></span> <span data-ttu-id="d490e-184">コード品質警告 (CAxxxx) がの存在でエラーとして扱われないようにするには `-warnaserror` 、 `CodeAnalysisTreatWarningsAsErrors` プロジェクトファイルで MSBuild プロパティをに設定し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="d490e-184">If you do not want code quality warnings (CAxxxx) to be treated as errors in presence of `-warnaserror`, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="d490e-185">コード分析の警告は引き続き表示されますが、ビルドが破損することはありません。</span><span class="sxs-lookup"><span data-stu-id="d490e-185">You'll still see any code analysis warnings, but they won't break your build.</span></span>

### <a name="latest-updates"></a><span data-ttu-id="d490e-186">最新の更新プログラム</span><span class="sxs-lookup"><span data-stu-id="d490e-186">Latest updates</span></span>

<span data-ttu-id="d490e-187">既定では、新しいバージョンの .NET SDK にアップグレードするときに、最新のコード分析規則と既定の規則の重大度を取得します。</span><span class="sxs-lookup"><span data-stu-id="d490e-187">By default, you'll get the latest code analysis rules and default rule severities as you upgrade to newer versions of the .NET SDK.</span></span> <span data-ttu-id="d490e-188">この動作が望ましくない場合、たとえば、新しいルールが有効になっていないか無効になっていることを確認する場合は、次のいずれかの方法でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d490e-188">If you don't want this behavior, for example, if you want to ensure that no new rules are enabled or disabled, you can override it in one of the following ways:</span></span>

- <span data-ttu-id="d490e-189">`AnalysisLevel`MSBuild プロパティを特定の値に設定して、そのセットに警告をロックします。</span><span class="sxs-lookup"><span data-stu-id="d490e-189">Set the `AnalysisLevel` MSBuild property to a specific value to lock the warnings to that set.</span></span> <span data-ttu-id="d490e-190">新しい SDK にアップグレードすると、これらの警告のバグ修正が引き続き行われますが、新しい警告は有効になりません。また、既存の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="d490e-190">When you upgrade to a newer SDK, you'll still get bug fixes for those warnings, but no new warnings will be enabled and no existing warnings will be disabled.</span></span> <span data-ttu-id="d490e-191">たとえば、.NET SDK のバージョン5.0 に付属するルールのセットをロックするには、プロジェクトファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="d490e-191">For example, to lock the set of rules to those that ship with version 5.0 of the .NET SDK, add the following entry to your project file.</span></span>

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > <span data-ttu-id="d490e-192">プロパティの既定値 `AnalysisLevel` はです `latest` 。これは、.net SDK の新しいバージョンに移行するときに、常に最新のコード分析規則を取得することを意味します。</span><span class="sxs-lookup"><span data-stu-id="d490e-192">The default value for the `AnalysisLevel` property is `latest`, which means you always get the latest code analysis rules as you move to newer versions of the .NET SDK.</span></span>

  <span data-ttu-id="d490e-193">詳細については、および使用可能な値の一覧については、「 [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d490e-193">For more information, and to see a list of possible values, see [AnalysisLevel](../../core/project-sdk/msbuild-props.md#analysislevel).</span></span>

- <span data-ttu-id="d490e-194">.NET SDK の更新プログラムから規則の更新を分離するには、 [Microsoft Codeanalysis NuGet パッケージ](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="d490e-194">Install the [Microsoft.CodeAnalysis.NetAnalyzers NuGet package](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) to decouple rule updates from .NET SDK updates.</span></span> <span data-ttu-id="d490e-195">パッケージをインストールすると、組み込みの SDK アナライザーが無効になり、SDK に NuGet パッケージよりも新しいバージョンの analyzer アセンブリが含まれている場合は、ビルドの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d490e-195">Installing the package turns off the built-in SDK analyzers and generates a build warning if the SDK contains a newer analyzer assembly version than that of the NuGet package.</span></span>

## <a name="code-style-analysis"></a><span data-ttu-id="d490e-196">コードスタイルの分析</span><span class="sxs-lookup"><span data-stu-id="d490e-196">Code-style analysis</span></span>

<span data-ttu-id="d490e-197">*コードスタイルの分析* ("ide xxxx") 規則を使用すると、コードベースで一貫性のあるコードスタイルを定義および維持できます。</span><span class="sxs-lookup"><span data-stu-id="d490e-197">*Code-style analysis* ("IDExxxx") rules enable you to define and maintain consistent code style in your codebase.</span></span> <span data-ttu-id="d490e-198">既定の有効化設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d490e-198">The default enablement settings are:</span></span>

- <span data-ttu-id="d490e-199">コマンドラインビルド: コマンドラインビルドのすべての .NET プロジェクトに対して、コードスタイルの分析が既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d490e-199">Command-line build: Code-style analysis is disabled, by default, for all .NET projects on command-line builds.</span></span>

  <span data-ttu-id="d490e-200">.NET 5.0 以降では、コマンドラインと Visual Studio の両方で [ビルドに対してコードスタイルの分析を有効に](#enable-on-build)することができます。</span><span class="sxs-lookup"><span data-stu-id="d490e-200">Starting in .NET 5.0, you can [enable code-style analysis on build](#enable-on-build), both at the command line and inside Visual Studio.</span></span> <span data-ttu-id="d490e-201">コードスタイル違反は、"IDE" プレフィックスが付いた警告またはエラーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="d490e-201">Code style violations appear as warnings or errors with an "IDE" prefix.</span></span> <span data-ttu-id="d490e-202">これにより、ビルド時に一貫したコードスタイルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="d490e-202">This enables you to enforce consistent code styles at build time.</span></span>

- <span data-ttu-id="d490e-203">Visual Studio: コードスタイルの分析は、Visual Studio 内のすべての .NET プロジェクトに対して、 [コードリファクタリングのクイックアクション](/visualstudio/ide/code-generation-in-visual-studio)として既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="d490e-203">Visual Studio: Code-style analysis is enabled, by default, for all .NET projects inside Visual Studio as [code refactoring quick actions](/visualstudio/ide/code-generation-in-visual-studio).</span></span>

<span data-ttu-id="d490e-204">コードスタイルの分析規則の完全な一覧については、「 [コードスタイル規則](style-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d490e-204">For a full list of code-style analysis rules, see [Code style rules](style-rules/index.md).</span></span>

### <a name="enable-on-build"></a><span data-ttu-id="d490e-205">ビルドで有効にする</span><span class="sxs-lookup"><span data-stu-id="d490e-205">Enable on build</span></span>

<span data-ttu-id="d490e-206">.NET 5.0 SDK 以降のバージョンでは、コマンドラインや Visual Studio からビルドするときに、コードスタイルの分析を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d490e-206">With the .NET 5.0 SDK and later versions, you can enable code-style analysis when building from the command-line and in Visual Studio.</span></span> <span data-ttu-id="d490e-207">(ただし、パフォーマンス上の理由から、 [いくつかのコードスタイルルール](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) は、VISUAL Studio IDE にのみ適用されます)。</span><span class="sxs-lookup"><span data-stu-id="d490e-207">(However, for performance reasons, [a handful of code-style rules](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) will still apply only in the Visual Studio IDE.)</span></span>

<span data-ttu-id="d490e-208">ビルドでコードスタイルの分析を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d490e-208">Follow these steps to enable code-style analysis on build:</span></span>

1. <span data-ttu-id="d490e-209">MSBuild プロパティ [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) をに設定し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d490e-209">Set the MSBuild property [EnforceCodeStyleInBuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) to `true`.</span></span>

1. <span data-ttu-id="d490e-210">*Editorconfig* ファイルで、ビルド時に実行する各 "IDE" コードスタイルルールを警告またはエラーとして [構成](configuration-options.md)します。</span><span class="sxs-lookup"><span data-stu-id="d490e-210">In an *.editorconfig* file, [configure](configuration-options.md) each "IDE" code style rule that you wish to run on build as a warning or an error.</span></span> <span data-ttu-id="d490e-211">例:</span><span class="sxs-lookup"><span data-stu-id="d490e-211">For example:</span></span>

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   <span data-ttu-id="d490e-212">また、既定では、カテゴリ全体を警告またはエラーとして構成してから、ビルドで実行したくないカテゴリの規則を選択的にオフにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d490e-212">Alternatively, you can configure an entire category to be a warning or error, by default, and then selectively turn off rules in that category that you don't want to run on build.</span></span> <span data-ttu-id="d490e-213">例:</span><span class="sxs-lookup"><span data-stu-id="d490e-213">For example:</span></span>

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

> [!NOTE]
> <span data-ttu-id="d490e-214">コードスタイルの分析機能は試験段階であり、.NET 5 リリースと .NET 6 リリース間で変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d490e-214">The code-style analysis feature is experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

## <a name="suppress-a-warning"></a><span data-ttu-id="d490e-215">警告の非表示</span><span class="sxs-lookup"><span data-stu-id="d490e-215">Suppress a warning</span></span>

<span data-ttu-id="d490e-216">規則違反を抑制するには、その規則 ID の重大度オプションを `none` EditorConfig ファイルでに設定します。</span><span class="sxs-lookup"><span data-stu-id="d490e-216">To suppress a rule violation, set the severity option for that rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="d490e-217">例:</span><span class="sxs-lookup"><span data-stu-id="d490e-217">For example:</span></span>

```ini
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="d490e-218">Visual Studio には、コード分析規則からの警告を抑制するための追加の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d490e-218">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="d490e-219">詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d490e-219">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="d490e-220">規則の重大度の詳細については、「 [規則の重要度の構成](configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d490e-220">For more information about rule severities, see [Configure rule severity](configuration-options.md#severity-level).</span></span>

## <a name="third-party-analyzers"></a><span data-ttu-id="d490e-221">サード パーティのアナライザー</span><span class="sxs-lookup"><span data-stu-id="d490e-221">Third-party analyzers</span></span>

<span data-ttu-id="d490e-222">公式の .NET アナライザーに加えて、 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Rosl/ator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [Xunit](https://www.nuget.org/packages/xunit.analyzers/) [Analyzer、sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)などのサードパーティ製アナライザーをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d490e-222">In addition to the official .NET analyzers, you can also install third party analyzers, such as [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), and [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).</span></span>

## <a name="see-also"></a><span data-ttu-id="d490e-223">関連項目</span><span class="sxs-lookup"><span data-stu-id="d490e-223">See also</span></span>

- [<span data-ttu-id="d490e-224">コード品質分析ルールのリファレンス</span><span class="sxs-lookup"><span data-stu-id="d490e-224">Code quality analysis rule reference</span></span>](quality-rules/index.md)
- [<span data-ttu-id="d490e-225">コードスタイル分析規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="d490e-225">Code style analysis rule reference</span></span>](style-rules/index.md)
- [<span data-ttu-id="d490e-226">Visual Studio でのコード分析</span><span class="sxs-lookup"><span data-stu-id="d490e-226">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="d490e-227">.NET Compiler Platform SDK</span><span class="sxs-lookup"><span data-stu-id="d490e-227">.NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="d490e-228">チュートリアル: 最初のアナライザーとコード修正を作成する</span><span class="sxs-lookup"><span data-stu-id="d490e-228">Tutorial: Write your first analyzer and code fix</span></span>](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
