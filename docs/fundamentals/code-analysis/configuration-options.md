---
title: コード分析ルールの構成
description: アナライザー構成ファイルでコード分析ルールを構成する方法について説明します。
ms.date: 09/24/2020
no-loc:
- EditorConfig
ms.openlocfilehash: b9f934d13a510fa9e349d1cefc8131f22e9cd549
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740970"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="7f732-103">コード分析の構成オプション</span><span class="sxs-lookup"><span data-stu-id="7f732-103">Configuration options for code analysis</span></span>

<span data-ttu-id="7f732-104">コード分析ルールには、さまざまな構成オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7f732-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="7f732-105">これらのオプションは、`<option key> = <option value>` という構文を使用して、[アナライザー構成ファイル](configuration-files.md)内のキーと値のペアとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="7f732-106">最も一般的に構成されるオプションは、[ルールの重大度](#severity-level)です。</span><span class="sxs-lookup"><span data-stu-id="7f732-106">The most common option you'll configure is a [rule's severity](#severity-level).</span></span> <span data-ttu-id="7f732-107">[コード品質ルール](quality-rules/index.md)や[コード スタイル ルール](style-rules/index.md)などのすべてのアナライザー ルールについて、重大度レベルを構成できます。</span><span class="sxs-lookup"><span data-stu-id="7f732-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span> <span data-ttu-id="7f732-108">たとえば、あるルールを警告として有効にするには、次のキーと値のペアを EditorConfig ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="7f732-108">For example, to enable a rule as a warning, you can add the following key-value pair to an EditorConfig file.</span></span>

`dotnet_diagnostic.<rule ID>.severity = warning`

<span data-ttu-id="7f732-109">追加のオプションを構成して、ルールの動作をカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7f732-109">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="7f732-110">コード品質ルールには、ルールを適用する必要があるメソッド名など、動作を構成するための[追加オプション](code-quality-rule-options.md)が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7f732-110">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="7f732-111">コード スタイル ルールには、[カスタム コード スタイル オプション](code-style-rule-options.md)が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7f732-111">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="7f732-112">サード パーティのアナライザー ルールでは、カスタムのキー名と値の形式を使用して、独自の構成オプションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="7f732-112">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="7f732-113">[アナライザー構成ファイル](configuration-files.md)で特定のルールの重大度を構成する構文は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7f732-113">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="7f732-114">[全般] オプション</span><span class="sxs-lookup"><span data-stu-id="7f732-114">General options</span></span>

<span data-ttu-id="7f732-115">これらのオプションは、コード分析全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-115">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="7f732-116">これらを 1 つのルールやルール セットのみに対して適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="7f732-116">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="7f732-117">生成されたコードを除外する</span><span class="sxs-lookup"><span data-stu-id="7f732-117">Exclude generated code</span></span>

<span data-ttu-id="7f732-118">`generated_code = true | false` エントリを[構成ファイル](configuration-files.md)に追加することで、追加のファイルやフォルダーを生成されたコードとして扱うように構成することができます。</span><span class="sxs-lookup"><span data-stu-id="7f732-118">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="7f732-119">.NET コード アナライザーの警告は、デザイナーで生成されたファイルなどの、ユーザーが編集して違反を修正することのできない生成されたコード ファイルに対しては役立ちません。</span><span class="sxs-lookup"><span data-stu-id="7f732-119">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="7f732-120">ほとんどの場合、コード アナライザーは生成されたコード ファイルをスキップし、これらのファイルに関する違反を報告しません。</span><span class="sxs-lookup"><span data-stu-id="7f732-120">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="7f732-121">既定では、特定のファイル拡張子または自動生成されたファイル ヘッダーを持つファイルは、生成されたコード ファイルとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="7f732-121">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="7f732-122">たとえば、`.designer.cs` または `.generated.cs` で終わるファイル名は、生成されたコードと見なされます。</span><span class="sxs-lookup"><span data-stu-id="7f732-122">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="7f732-123">この構成オプションを使用することにより、追加の名前付けパターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7f732-123">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="7f732-124">たとえば、名前が `.MyGenerated.cs` で終わるすべてのファイルを生成されたコードとして扱うには、次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="7f732-124">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="7f732-125">ルール固有のオプション</span><span class="sxs-lookup"><span data-stu-id="7f732-125">Rule-specific options</span></span>

<span data-ttu-id="7f732-126">ルール固有のオプションは、1 つのルール、ルール セット、またはすべてのルールに適用できます。</span><span class="sxs-lookup"><span data-stu-id="7f732-126">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="7f732-127">ルール固有のオプションには、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="7f732-127">The rule-specific options include:</span></span>

- [<span data-ttu-id="7f732-128">ルールの重大度レベル</span><span class="sxs-lookup"><span data-stu-id="7f732-128">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="7f732-129">"*コード品質*" ルールに固有のオプション</span><span class="sxs-lookup"><span data-stu-id="7f732-129">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="7f732-130">重大度レベル</span><span class="sxs-lookup"><span data-stu-id="7f732-130">Severity level</span></span>

<span data-ttu-id="7f732-131">次の表に、[コード品質](quality-rules/index.md)ルールや[コード スタイル](style-rules/index.md)ルールなどのすべてのアナライザー ルールに対して構成できる、さまざまなルールの重大度を示します。</span><span class="sxs-lookup"><span data-stu-id="7f732-131">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="7f732-132">重大度の構成値</span><span class="sxs-lookup"><span data-stu-id="7f732-132">Severity configuration value</span></span> | <span data-ttu-id="7f732-133">ビルド時の動作</span><span class="sxs-lookup"><span data-stu-id="7f732-133">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="7f732-134">違反はビルドの "*エラー*" として表示され、ビルドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="7f732-134">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="7f732-135">違反はビルドの "*警告*" として表示されますが、ビルドは失敗しません (警告をエラーとして扱うようにオプションで設定している場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="7f732-135">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="7f732-136">違反はビルドの "*メッセージ*" として表示され、Visual Studio IDE に修正候補として表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-136">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="7f732-137">違反はユーザーに表示されません。</span><span class="sxs-lookup"><span data-stu-id="7f732-137">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="7f732-138">規則は完全に抑制されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-138">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="7f732-139">ルールの既定の重大度が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-139">The default severity of the rule is used.</span></span> <span data-ttu-id="7f732-140">各 .NET リリースの既定の重大度は、[roslyn-analyzers リポジトリ](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)に一覧で示されています。</span><span class="sxs-lookup"><span data-stu-id="7f732-140">The default severities for each .NET release are listed in the [roslyn-analyzers repo](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span> <span data-ttu-id="7f732-141">その表で、Disabled は `none` に、Hidden は `silent` に、Info は `suggestion` に相当します。</span><span class="sxs-lookup"><span data-stu-id="7f732-141">In that table, "Disabled" corresponds to `none`, "Hidden" corresponds to `silent`, and "Info" corresponds to `suggestion`.</span></span> |

> [!TIP]
> <span data-ttu-id="7f732-142">Visual Studio でルールの重大度がどのように表示されるかについては、[重大度レベル](/visualstudio/ide/editorconfig-language-conventions#severity-levels)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f732-142">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="7f732-143">Scope</span><span class="sxs-lookup"><span data-stu-id="7f732-143">Scope</span></span>

<span data-ttu-id="7f732-144">1 つのルールに対してルールの重大度を設定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f732-144">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="7f732-145">[ルールのカテゴリ](categories.md)に対して既定のルールの重大度を設定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f732-145">To set the default rule severity for a [category of rules](categories.md), use the following syntax.</span></span> <span data-ttu-id="7f732-146">各ルールのカテゴリは、個々のルールのリファレンス ページ (例: [CA1000](quality-rules/ca1000.md)) で説明されています。</span><span class="sxs-lookup"><span data-stu-id="7f732-146">The category for each rule is provided in the individual rule reference pages, for example, [CA1000](quality-rules/ca1000.md).</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="7f732-147">すべてのアナライザー ルールに対して既定のルールの重大度を設定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f732-147">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

> [!IMPORTANT]
> <span data-ttu-id="7f732-148">ルールの "*カテゴリ*" または "*すべて*" のルールに対して、1 つのエントリで複数のルールの重大度レベルを構成する場合、その重大度は [既定で有効](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)であるルールに対してのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-148">When you configure the severity level for multiple rules with a single entry, either for a *category* of rules or for *all* rules, the severity only applies to rules that are [enabled by default](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span> <span data-ttu-id="7f732-149">既定で無効であるルールを有効にするには、次のいずれかを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f732-149">To enable rules that are disabled by default, you must either:</span></span>
>
> - <span data-ttu-id="7f732-150">ルールごとに明示的な `dotnet_diagnostic.<rule ID>.severity = <severity>` 構成エントリを追加する。</span><span class="sxs-lookup"><span data-stu-id="7f732-150">Add an explicit `dotnet_diagnostic.<rule ID>.severity = <severity>` configuration entry for each rule.</span></span>
> - <span data-ttu-id="7f732-151">[\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) を `AllEnabledByDefault` に設定して、"*すべて*" のルールを有効にする。</span><span class="sxs-lookup"><span data-stu-id="7f732-151">Enable *all* rules by setting [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) to `AllEnabledByDefault`.</span></span>

#### <a name="precedence"></a><span data-ttu-id="7f732-152">優先順位</span><span class="sxs-lookup"><span data-stu-id="7f732-152">Precedence</span></span>

<span data-ttu-id="7f732-153">同一のルール ID に適用できる重大度構成エントリが複数ある場合は、次の順序で優先順位が選択されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-153">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="7f732-154">ID に基づく個々のルールに対するエントリは、カテゴリに対するエントリよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-154">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="7f732-155">カテゴリに対するエントリは、すべてのアナライザー ルールに対するエントリよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-155">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="7f732-156">次の例を考えてみましょう。[CA1822](/visualstudio/code-quality/ca1822) はカテゴリが "パフォーマンス" に指定されています。</span><span class="sxs-lookup"><span data-stu-id="7f732-156">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="7f732-157">前の例では、3 つの重大度エントリすべてが CA1822 に適用できます。</span><span class="sxs-lookup"><span data-stu-id="7f732-157">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="7f732-158">ただし、指定した優先順位ルールを使用すると、最初のルール ID ベースのエントリが次のエントリに優先されます。</span><span class="sxs-lookup"><span data-stu-id="7f732-158">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="7f732-159">この例の場合、CA1822 の有効な重大度は `error` です。</span><span class="sxs-lookup"><span data-stu-id="7f732-159">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="7f732-160">"パフォーマンス" カテゴリに含まれる他のすべてのルールは重大度が `warning` です。</span><span class="sxs-lookup"><span data-stu-id="7f732-160">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="7f732-161">ファイル間で優先度が決まる方法の詳細については、[構成ファイルに関する記事の「優先順位」セクション](configuration-files.md#precedence)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f732-161">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
