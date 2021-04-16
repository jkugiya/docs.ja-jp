---
title: コード分析ルールの構成ファイル
description: コード分析ルールを構成するためのさまざまな構成ファイルについて説明します。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: b98fdd48f2373bd23fcd3273834860a60c682969
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "99216383"
---
# <a name="configuration-files-for-code-analysis-rules"></a><span data-ttu-id="4c5c2-103">コード分析ルールの構成ファイル</span><span class="sxs-lookup"><span data-stu-id="4c5c2-103">Configuration files for code analysis rules</span></span>

<span data-ttu-id="4c5c2-104">コード分析ルールには、さまざまな[構成オプション](configuration-options.md)が用意されています。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-104">Code analysis rules have various [configuration options](configuration-options.md).</span></span> <span data-ttu-id="4c5c2-105">これらのオプションは、次のいずれかのアナライザー構成ファイルのキーと値のペアとして指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-105">You specify these options as key-value pairs in one of the following analyzer configuration files:</span></span>

- <span data-ttu-id="4c5c2-106">[EditorConfig](#editorconfig) ファイル: ファイルベースまたはフォルダーベースの構成オプション。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-106">[EditorConfig](#editorconfig) file: File-based or folder-based configuration options.</span></span>
- <span data-ttu-id="4c5c2-107">[Global AnalyzerConfig](#global-analyzerconfig) ファイル: プロジェクトレベルの構成オプション。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-107">[Global AnalyzerConfig](#global-analyzerconfig) file: Project-level configuration options.</span></span> <span data-ttu-id="4c5c2-108">一部のプロジェクト ファイルがプロジェクト フォルダーの外部にある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-108">Useful when some project files reside outside the project folder.</span></span>

## EditorConfig

<span data-ttu-id="4c5c2-109">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) ファイルは、**特定のソース ファイルまたはフォルダーに適用されるオプション** を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-109">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) files are used to provide **options that apply to specific source files or folders**.</span></span> <span data-ttu-id="4c5c2-110">オプションは、該当するファイルとフォルダーを識別するためにセクション ヘッダーの下に配置されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-110">Options are placed under section headers to identify the applicable files and folders.</span></span> <span data-ttu-id="4c5c2-111">構成するルールごとのエントリを追加し、対応するファイル拡張子セクションの下に配置します (たとえば `[*.cs]`)。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-111">Add an entry for each rule you want to configure, and place it under the corresponding file extension section, for example, `[*.cs]`.</span></span>

```ini
[*.cs]
<option_name> = <option_value>
```

<span data-ttu-id="4c5c2-112">上の例で、`[*.cs]` は editorconfig セクション ヘッダーで、サブフォルダーを含む現在のフォルダー内の `.cs` ファイル拡張子を持つすべての C# ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-112">In the above example, `[*.cs]` is an editorconfig section header to select all C# files with `.cs` file extension within the current folder, including subfolders.</span></span> <span data-ttu-id="4c5c2-113">後続のエントリ `<option_name> = <option_value>` は、すべての C# ファイルに適用されるアナライザー オプションです。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-113">The subsequent entry, `<option_name> = <option_value>`, is an analyzer option that will be applied to all the C# files.</span></span>

<span data-ttu-id="4c5c2-114">EditorConfig ファイル規則は、対応するディレクトリにファイルを配置することによって、フォルダー、プロジェクト、またはリポジトリ全体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-114">You can apply EditorConfig file conventions to a folder, a project, or an entire repo by placing the file in the corresponding directory.</span></span> <span data-ttu-id="4c5c2-115">これらのオプションは、ビルド時に分析を実行するときと、Visual Studio でコードを編集するときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-115">These options are applied when executing the analysis at build time and while you edit code in Visual Studio.</span></span>

<span data-ttu-id="4c5c2-116">インデント サイズや末尾の空白文字をトリミングするかどうかなど、エディター設定用の既存の *.editorconfig* ファイルがある場合は、コード分析の構成オプションを同じファイルに配置できます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-116">If you have an existing *.editorconfig* file for editor settings such as indent size or whether to trim trailing whitespace, you can place your code analysis configuration options in the same file.</span></span>

> [!TIP]
> <span data-ttu-id="4c5c2-117">Visual Studio には、これらのファイルの 1 つをプロジェクトに簡単に追加できるようにする、 *.editorconfig* 項目テンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-117">Visual Studio provides an *.editorconfig* item template that makes is easy to add one of these files to your project.</span></span> <span data-ttu-id="4c5c2-118">詳細については、「[EditorConfig ファイルをプロジェクトに追加する](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-118">For more information, see [Add an EditorConfig file to a project](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span></span>

### <a name="example"></a><span data-ttu-id="4c5c2-119">例</span><span class="sxs-lookup"><span data-stu-id="4c5c2-119">Example</span></span>

<span data-ttu-id="4c5c2-120">オプションとルールの重要度を構成する EditorConfig ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-120">Following is an example EditorConfig file to configure options and rule severity:</span></span>

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a><span data-ttu-id="4c5c2-121">グローバル AnalyzerConfig</span><span class="sxs-lookup"><span data-stu-id="4c5c2-121">Global AnalyzerConfig</span></span>

<span data-ttu-id="4c5c2-122">.NET 5 SDK (Visual Studio 2019 バージョン 16.8 以降でサポートされます) 以降では、グローバル _AnalyzerConfig_ ファイルを使用してアナライザー オプションを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-122">Starting with the .NET 5 SDK (which is supported in Visual Studio 2019 version 16.8 and later), you can also configure analyzer options with global _AnalyzerConfig_ files.</span></span> <span data-ttu-id="4c5c2-123">これらのファイルは、ファイル名やファイル パスに関係なく、**プロジェクト内のすべてのソース ファイルに適用されるオプション** を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-123">These files are used to provide **options that apply to all the source files in a project**, regardless of their file names or file paths.</span></span>

<span data-ttu-id="4c5c2-124">[EditorConfig](#editorconfig) ファイルとは異なり、グローバル構成ファイルは、インデント サイズや末尾の空白文字をトリミングするかどうかなど、IDE のエディター スタイル設定を構成するために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-124">Unlike [EditorConfig](#editorconfig) files, global config files can't be used to configure editor style settings for IDEs, such as indent size or whether to trim trailing whitespace.</span></span> <span data-ttu-id="4c5c2-125">そうではなく、これらは単にプロジェクト レベルのアナライザーの構成オプションを指定するだけの目的で設計されています。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-125">Instead, they are designed purely for specifying project-level analyzer configuration options.</span></span>

### <a name="format"></a><span data-ttu-id="4c5c2-126">フォーマット</span><span class="sxs-lookup"><span data-stu-id="4c5c2-126">Format</span></span>

<span data-ttu-id="4c5c2-127">EditorConfig ファイルには、該当するファイルとフォルダーを識別するために `[*.cs]` などのセクション ヘッダーを持つ必要がありますが、これとは異なりグローバル AnalyzerConfig ファイルにはセクション ヘッダーがありません。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-127">Unlike EditorConfig files, which must have section headers, such as `[*.cs]`, to identify the applicable files and folders, global AnalyzerConfig files don't have section headers.</span></span> <span data-ttu-id="4c5c2-128">代わりに、これらは通常の EditorConfig ファイルと区別するために、`is_global = true` という形式の最上位レベルのエントリが必要です。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-128">Instead, they require a top level entry of the form `is_global = true` to differentiate them from regular EditorConfig files.</span></span> <span data-ttu-id="4c5c2-129">これは、ファイル内のすべてのオプションがプロジェクト全体に適用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-129">This indicates that all the options in the file apply to the entire project.</span></span> <span data-ttu-id="4c5c2-130">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-130">For example:</span></span>

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a><span data-ttu-id="4c5c2-131">名前を付ける</span><span class="sxs-lookup"><span data-stu-id="4c5c2-131">Naming</span></span>

<span data-ttu-id="4c5c2-132">EditorConfig ファイルでは `.editorconfig` という名前を付ける必要がありますが、これとは異なりグローバル構成ファイルには特定の名前や拡張子を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-132">Unlike EditorConfig files, which must be named `.editorconfig`, global config files do not need to have a specific name or extension.</span></span> <span data-ttu-id="4c5c2-133">ただし、これらのファイルに `.globalconfig` という名前を付けた場合、これらはサブフォルダーを含む現在のフォルダー内のすべての C# および Visual Basic プロジェクトに暗黙的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-133">However, if you name these files as `.globalconfig` then they will be implicitly applied to all the C# and Visual Basic projects within the current folder, including subfolders.</span></span> <span data-ttu-id="4c5c2-134">それ以外の場合、MSBuild プロジェクト ファイルに `GlobalAnalyzerConfigFiles` 項目を明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-134">Otherwise, you must explicitly add the `GlobalAnalyzerConfigFiles` item to your MSBuild project file:</span></span>

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="4c5c2-135">ファイル名が `.globalconfig` の場合でも、最上位レベルのエントリ `is_global = true` が必要です。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-135">The top-level entry `is_global = true` is required even when the file is named `.globalconfig`.</span></span>

### <a name="example"></a><span data-ttu-id="4c5c2-136">例</span><span class="sxs-lookup"><span data-stu-id="4c5c2-136">Example</span></span>

<span data-ttu-id="4c5c2-137">次に示すのは、オプションとルールの重要度をプロジェクト レベルで構成するグローバル AnalyzerConfig ファイルの例です。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-137">Following is an example global AnalyzerConfig file to configure options and rule severity at the project level:</span></span>

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a><span data-ttu-id="4c5c2-138">優先順位</span><span class="sxs-lookup"><span data-stu-id="4c5c2-138">Precedence</span></span>

<span data-ttu-id="4c5c2-139">EditorConfig ファイルとグローバル AnalyzerConfig ファイルはどちらも各オプションのキーと値のペアを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-139">Both EditorConfig files and global AnalyzerConfig files specify a key-value pair for each option.</span></span> <span data-ttu-id="4c5c2-140">キーが同じで値が異なる複数のエントリが存在すると、競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-140">Conflicts arise when there are multiple entries with the same key but different values.</span></span>

### <a name="general-options"></a><span data-ttu-id="4c5c2-141">[全般] オプション</span><span class="sxs-lookup"><span data-stu-id="4c5c2-141">General options</span></span>

<span data-ttu-id="4c5c2-142">オプション間で競合が発生した場合、競合を解決するために次の優先順位ルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-142">When conflicts arise between options, the following precedence rules are used to resolve the conflicts:</span></span>

- <span data-ttu-id="4c5c2-143">同じ構成ファイル内のエントリが競合する場合: ファイル内で後の方に現れるエントリが優先されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-143">Conflicting entries in the same configuration file: The entry that appears later in the file wins.</span></span> <span data-ttu-id="4c5c2-144">これは 1 つの EditorConfig ファイル内のエントリの競合に当てはまり、さらに 1 つのグローバル AnalyzerConfig ファイル内でも同じです。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-144">This is true for conflicting entries within a single EditorConfig file and also within a single global AnalyzerConfig file.</span></span>

- <span data-ttu-id="4c5c2-145">2 つの EditorConfig ファイル内のエントリが競合する場合: EditorConfig ファイル内のエントリで、ファイル システム内の階層が深い方、つまり、ファイルのパスが長い方が優先されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-145">Conflicting entries in two EditorConfig files: The entry in the EditorConfig file that's deeper in the file system, and hence has a longer file path, wins.</span></span>

- <span data-ttu-id="4c5c2-146">2 つのグローバル AnalyzerConfig ファイル内のエントリが競合する場合: コンパイラの警告が報告され、両方のエントリが無視されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-146">Conflicting entries in two global AnalyzerConfig files: A compiler warning is reported and both entries are ignored.</span></span>

- <span data-ttu-id="4c5c2-147">EditorConfig ファイルとグローバル AnalyzerConfig ファイルのエントリが競合する場合: EditorConfig ファイル内のエントリが優先されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-147">Conflicting entries in an EditorConfig file and a Global AnalyzerConfig file: The entry in the EditorConfig file wins.</span></span>

### <a name="severity-options"></a><span data-ttu-id="4c5c2-148">重要度オプション</span><span class="sxs-lookup"><span data-stu-id="4c5c2-148">Severity options</span></span>

<span data-ttu-id="4c5c2-149">構成ファイルで指定されるすべてのオプションに、前の[一般的な優先順位ルール](#general-options)が適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-149">The previous [general precedence rules](#general-options) apply for all options specified in configuration files.</span></span> <span data-ttu-id="4c5c2-150">[重要度の構成](configuration-options.md#severity-level)オプションについては、次の追加の優先順位ルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-150">For [severity configuration](configuration-options.md#severity-level) options, the following additional precedence rules apply:</span></span>

- <span data-ttu-id="4c5c2-151">コンパイラ オプションとしてコマンド ラインで指定される重要度オプション (`/nowarn` または `/warnaserror`) は、EditorConfig とグローバル AnalyzerConfig ファイルで指定される[重要度構成](configuration-options.md#severity-level)オプションを常にオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-151">Severity options specified at the command line as compiler options (`/nowarn` or `/warnaserror`) always override [severity configuration](configuration-options.md#severity-level) options specified in EditorConfig and global AnalyzerConfig files.</span></span>

- <span data-ttu-id="4c5c2-152">重要度オプションは、[ルールセット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルで指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-152">Severity options can also be specified with a [Ruleset](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) file.</span></span> <span data-ttu-id="4c5c2-153">ただし、EditorConfig およびグローバル AnalyzerConfig ファイルが優先され、ルールセット ファイルは非推奨となっています。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-153">However, rulesets files are deprecated in favor of EditorConfig and global AnalyzerConfig files.</span></span> <span data-ttu-id="4c5c2-154">[ルールセットファイルを同等の EditorConfig ファイルに変換する](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)ことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-154">It's recommended that you [convert ruleset files to an equivalent EditorConfig file](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span></span> <span data-ttu-id="4c5c2-155">ルールセット ファイルと、EditorConfig またはグローバル AnalyzerConfig ファイルの競合する重要度エントリの優先順位は "_未定義_" です。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-155">Precedence for conflicting severity entries from a ruleset file and EditorConfig or global AnalyzerConfig files is _undefined_.</span></span>

- <span data-ttu-id="4c5c2-156">1 つのルールおよびそのルールが属するカテゴリに対して異なる重大度が指定されている場合など、異なるキーの関連する重要度オプションの優先順位ルールについては、「[コード分析の構成オプション](configuration-options.md#precedence)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c5c2-156">For information about precedence rules for related severity options with different keys, for example, when different severities are specified for a single rule and for the category that rule falls under, see [Configuration options for code analysis](configuration-options.md#precedence).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c5c2-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c5c2-157">See also</span></span>

- [<span data-ttu-id="4c5c2-158">EditorConfig とグローバル AnalyzerConfig の設計の問題</span><span class="sxs-lookup"><span data-stu-id="4c5c2-158">EditorConfig vs global AnalyzerConfig design issue</span></span>](https://github.com/dotnet/roslyn/issues/47707)
