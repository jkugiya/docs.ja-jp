---
title: コード分析規則の構成
description: アナライザーの構成ファイルでコード分析規則を構成する方法について説明します。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 8f76c9c86c202ef1bad23bffe8379b0b93a53f17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787722"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="06ad2-103">コード分析の構成オプション</span><span class="sxs-lookup"><span data-stu-id="06ad2-103">Configuration options for code analysis</span></span>

<span data-ttu-id="06ad2-104">コード分析規則には、さまざまな構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="06ad2-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="06ad2-105">これらのオプションは、構文を使用して、 [アナライザー構成ファイル](configuration-files.md) のキーと値のペアとして指定され `<option key> = <option value>` ます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="06ad2-106">最も一般的に構成するオプションは、 [ルールの重要度](#severity-level)です。</span><span class="sxs-lookup"><span data-stu-id="06ad2-106">The most common option you'll configure is a [rule's severity](#severity-level).</span></span> <span data-ttu-id="06ad2-107">[コード品質ルール](quality-rules/index.md)や[コードスタイルルール](style-rules/index.md)など、すべてのアナライザールールの重大度レベルを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span> <span data-ttu-id="06ad2-108">たとえば、警告としてルールを有効にするには、次のキーと値のペアをファイルに追加し EditorConfig ます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-108">For example, to enable a rule as a warning, you can add the following key-value pair to an EditorConfig file.</span></span>

`dotnet_diagnostic.<rule ID>.severity = warning`

<span data-ttu-id="06ad2-109">ルールの動作をカスタマイズするための追加のオプションを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-109">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="06ad2-110">コード品質ルールには、ルールを適用する必要があるメソッド名など、動作を構成するための [追加のオプション](code-quality-rule-options.md) があります。</span><span class="sxs-lookup"><span data-stu-id="06ad2-110">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="06ad2-111">コードスタイル規則には、 [カスタムコードスタイルオプション](code-style-rule-options.md)があります。</span><span class="sxs-lookup"><span data-stu-id="06ad2-111">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="06ad2-112">サードパーティの analyzer ルールでは、独自の構成オプションを定義できます。カスタムキー名と値の形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-112">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="06ad2-113">[Analyzer 構成ファイル](configuration-files.md)で特定のルールの重要度を構成するための構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="06ad2-113">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="06ad2-114">[全般] オプション</span><span class="sxs-lookup"><span data-stu-id="06ad2-114">General options</span></span>

<span data-ttu-id="06ad2-115">これらのオプションは、コード分析全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-115">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="06ad2-116">1つのルールまたは一連のルールのみに適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="06ad2-116">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="06ad2-117">生成されたコードを除外する</span><span class="sxs-lookup"><span data-stu-id="06ad2-117">Exclude generated code</span></span>

<span data-ttu-id="06ad2-118">`generated_code = true | false`[構成ファイル](configuration-files.md)にエントリを追加することで、生成されたコードとして扱われる追加のファイルとフォルダーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-118">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="06ad2-119">.NET コードアナライザーの警告は、デザイナーで生成されたファイルなど、生成されたコードファイルでは役に立ちません。ユーザーは、このファイルを編集して違反を修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="06ad2-119">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="06ad2-120">ほとんどの場合、コードアナライザーは生成されたコードファイルをスキップし、これらのファイルに対する違反を報告しません。</span><span class="sxs-lookup"><span data-stu-id="06ad2-120">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="06ad2-121">既定では、特定のファイル拡張子または自動生成されたファイルヘッダーを持つファイルは、生成されたコードファイルとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-121">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="06ad2-122">たとえば、またはで終わるファイル名 `.designer.cs` `.generated.cs` は、生成されたコードと見なされます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-122">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="06ad2-123">この構成オプションを使用すると、追加の命名パターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-123">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="06ad2-124">たとえば、名前がで終わるすべてのファイルを、 `.MyGenerated.cs` 生成されたコードとして扱うには、次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="06ad2-124">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="06ad2-125">ルール固有のオプション</span><span class="sxs-lookup"><span data-stu-id="06ad2-125">Rule-specific options</span></span>

<span data-ttu-id="06ad2-126">ルール固有のオプションは、1つのルール、一連のルール、またはすべてのルールに適用できます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-126">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="06ad2-127">ルール固有のオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="06ad2-127">The rule-specific options include:</span></span>

- [<span data-ttu-id="06ad2-128">ルールの重大度レベル</span><span class="sxs-lookup"><span data-stu-id="06ad2-128">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="06ad2-129">*コード品質* 規則に固有のオプション</span><span class="sxs-lookup"><span data-stu-id="06ad2-129">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="06ad2-130">重大度レベル</span><span class="sxs-lookup"><span data-stu-id="06ad2-130">Severity level</span></span>

<span data-ttu-id="06ad2-131">次の表は、 [コード品質](quality-rules/index.md) や [コードスタイル](style-rules/index.md) の規則など、すべてのアナライザーの規則に対して構成できるさまざまな規則の重大度を示しています。</span><span class="sxs-lookup"><span data-stu-id="06ad2-131">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="06ad2-132">重大度</span><span class="sxs-lookup"><span data-stu-id="06ad2-132">Severity</span></span> | <span data-ttu-id="06ad2-133">ビルド時の動作</span><span class="sxs-lookup"><span data-stu-id="06ad2-133">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="06ad2-134">違反はビルド *エラー* として表示され、ビルドが失敗します。</span><span class="sxs-lookup"><span data-stu-id="06ad2-134">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="06ad2-135">違反はビルドの *警告* として表示されますが、ビルドが失敗することはありません (警告をエラーとして扱うオプションが設定されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="06ad2-135">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="06ad2-136">違反は、Visual Studio IDE のビルド *メッセージ* および提案として表示されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-136">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="06ad2-137">違反はユーザーに表示されません。</span><span class="sxs-lookup"><span data-stu-id="06ad2-137">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="06ad2-138">規則は完全に抑制されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-138">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="06ad2-139">ルールの既定の重要度が使用されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-139">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="06ad2-140">Visual Studio でのルールの重大度の詳細については、「 [重大度レベル](/visualstudio/ide/editorconfig-language-conventions#severity-levels)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06ad2-140">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="06ad2-141">Scope</span><span class="sxs-lookup"><span data-stu-id="06ad2-141">Scope</span></span>

<span data-ttu-id="06ad2-142">ルールの重要度を1つのルールに設定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="06ad2-142">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="06ad2-143">[ルールのカテゴリ](categories.md)の既定のルールの重要度を設定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="06ad2-143">To set the default rule severity for a [category of rules](categories.md), use the following syntax.</span></span> <span data-ttu-id="06ad2-144">各ルールのカテゴリは、個々のルールの参照ページ ( [CA1000](quality-rules/ca1000.md)など) に表示されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-144">The category for each rule is provided in the individual rule reference pages, for example, [CA1000](quality-rules/ca1000.md).</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="06ad2-145">すべてのアナライザールールの既定のルールの重要度を設定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="06ad2-145">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="06ad2-146">優先順位</span><span class="sxs-lookup"><span data-stu-id="06ad2-146">Precedence</span></span>

<span data-ttu-id="06ad2-147">同じ規則 ID に適用できる重要度の構成エントリが複数ある場合は、次の順序で優先順位が選択されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-147">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="06ad2-148">ID による個々のルールのエントリは、カテゴリのエントリよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-148">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="06ad2-149">カテゴリのエントリは、すべてのアナライザールールのエントリよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-149">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="06ad2-150">次の例を考えてみます。 [CA1822](/visualstudio/code-quality/ca1822) には "Performance" というカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="06ad2-150">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="06ad2-151">前の例では、3つの重要度のエントリすべてが CA1822 に適用されます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-151">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="06ad2-152">ただし、指定された優先順位規則を使用すると、最初の規則 ID ベースのエントリは次のエントリに優先します。</span><span class="sxs-lookup"><span data-stu-id="06ad2-152">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="06ad2-153">この例では、CA1822 の有効な重要度は `error` です。</span><span class="sxs-lookup"><span data-stu-id="06ad2-153">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="06ad2-154">"パフォーマンス" カテゴリ内のその他のすべてのルールの重要度はになり `warning` ます。</span><span class="sxs-lookup"><span data-stu-id="06ad2-154">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="06ad2-155">ファイルの優先順位の決定方法の詳細については、 [構成ファイルの記事の「優先順位」セクション](configuration-files.md#precedence)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06ad2-155">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
