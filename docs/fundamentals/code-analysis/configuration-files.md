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
# <a name="configuration-files-for-code-analysis-rules"></a>コード分析ルールの構成ファイル

コード分析ルールには、さまざまな[構成オプション](configuration-options.md)が用意されています。 これらのオプションは、次のいずれかのアナライザー構成ファイルのキーと値のペアとして指定します。

- [EditorConfig](#editorconfig) ファイル: ファイルベースまたはフォルダーベースの構成オプション。
- [Global AnalyzerConfig](#global-analyzerconfig) ファイル: プロジェクトレベルの構成オプション。 一部のプロジェクト ファイルがプロジェクト フォルダーの外部にある場合に便利です。

## EditorConfig

[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) ファイルは、**特定のソース ファイルまたはフォルダーに適用されるオプション** を提供するために使用されます。 オプションは、該当するファイルとフォルダーを識別するためにセクション ヘッダーの下に配置されます。 構成するルールごとのエントリを追加し、対応するファイル拡張子セクションの下に配置します (たとえば `[*.cs]`)。

```ini
[*.cs]
<option_name> = <option_value>
```

上の例で、`[*.cs]` は editorconfig セクション ヘッダーで、サブフォルダーを含む現在のフォルダー内の `.cs` ファイル拡張子を持つすべての C# ファイルを選択します。 後続のエントリ `<option_name> = <option_value>` は、すべての C# ファイルに適用されるアナライザー オプションです。

EditorConfig ファイル規則は、対応するディレクトリにファイルを配置することによって、フォルダー、プロジェクト、またはリポジトリ全体に適用できます。 これらのオプションは、ビルド時に分析を実行するときと、Visual Studio でコードを編集するときに適用されます。

インデント サイズや末尾の空白文字をトリミングするかどうかなど、エディター設定用の既存の *.editorconfig* ファイルがある場合は、コード分析の構成オプションを同じファイルに配置できます。

> [!TIP]
> Visual Studio には、これらのファイルの 1 つをプロジェクトに簡単に追加できるようにする、 *.editorconfig* 項目テンプレートがあります。 詳細については、「[EditorConfig ファイルをプロジェクトに追加する](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)」を参照してください。

### <a name="example"></a>例

オプションとルールの重要度を構成する EditorConfig ファイルの例を次に示します。

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

## <a name="global-analyzerconfig"></a>グローバル AnalyzerConfig

.NET 5 SDK (Visual Studio 2019 バージョン 16.8 以降でサポートされます) 以降では、グローバル _AnalyzerConfig_ ファイルを使用してアナライザー オプションを構成することもできます。 これらのファイルは、ファイル名やファイル パスに関係なく、**プロジェクト内のすべてのソース ファイルに適用されるオプション** を提供するために使用されます。

[EditorConfig](#editorconfig) ファイルとは異なり、グローバル構成ファイルは、インデント サイズや末尾の空白文字をトリミングするかどうかなど、IDE のエディター スタイル設定を構成するために使用することはできません。 そうではなく、これらは単にプロジェクト レベルのアナライザーの構成オプションを指定するだけの目的で設計されています。

### <a name="format"></a>フォーマット

EditorConfig ファイルには、該当するファイルとフォルダーを識別するために `[*.cs]` などのセクション ヘッダーを持つ必要がありますが、これとは異なりグローバル AnalyzerConfig ファイルにはセクション ヘッダーがありません。 代わりに、これらは通常の EditorConfig ファイルと区別するために、`is_global = true` という形式の最上位レベルのエントリが必要です。 これは、ファイル内のすべてのオプションがプロジェクト全体に適用されることを示します。 次に例を示します。

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a>名前を付ける

EditorConfig ファイルでは `.editorconfig` という名前を付ける必要がありますが、これとは異なりグローバル構成ファイルには特定の名前や拡張子を付ける必要はありません。 ただし、これらのファイルに `.globalconfig` という名前を付けた場合、これらはサブフォルダーを含む現在のフォルダー内のすべての C# および Visual Basic プロジェクトに暗黙的に適用されます。 それ以外の場合、MSBuild プロジェクト ファイルに `GlobalAnalyzerConfigFiles` 項目を明示的に追加する必要があります。

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> ファイル名が `.globalconfig` の場合でも、最上位レベルのエントリ `is_global = true` が必要です。

### <a name="example"></a>例

次に示すのは、オプションとルールの重要度をプロジェクト レベルで構成するグローバル AnalyzerConfig ファイルの例です。

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

## <a name="precedence"></a>優先順位

EditorConfig ファイルとグローバル AnalyzerConfig ファイルはどちらも各オプションのキーと値のペアを指定します。 キーが同じで値が異なる複数のエントリが存在すると、競合が発生します。

### <a name="general-options"></a>[全般] オプション

オプション間で競合が発生した場合、競合を解決するために次の優先順位ルールが使用されます。

- 同じ構成ファイル内のエントリが競合する場合: ファイル内で後の方に現れるエントリが優先されます。 これは 1 つの EditorConfig ファイル内のエントリの競合に当てはまり、さらに 1 つのグローバル AnalyzerConfig ファイル内でも同じです。

- 2 つの EditorConfig ファイル内のエントリが競合する場合: EditorConfig ファイル内のエントリで、ファイル システム内の階層が深い方、つまり、ファイルのパスが長い方が優先されます。

- 2 つのグローバル AnalyzerConfig ファイル内のエントリが競合する場合: コンパイラの警告が報告され、両方のエントリが無視されます。

- EditorConfig ファイルとグローバル AnalyzerConfig ファイルのエントリが競合する場合: EditorConfig ファイル内のエントリが優先されます。

### <a name="severity-options"></a>重要度オプション

構成ファイルで指定されるすべてのオプションに、前の[一般的な優先順位ルール](#general-options)が適用されます。 [重要度の構成](configuration-options.md#severity-level)オプションについては、次の追加の優先順位ルールが適用されます。

- コンパイラ オプションとしてコマンド ラインで指定される重要度オプション (`/nowarn` または `/warnaserror`) は、EditorConfig とグローバル AnalyzerConfig ファイルで指定される[重要度構成](configuration-options.md#severity-level)オプションを常にオーバーライドします。

- 重要度オプションは、[ルールセット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルで指定することもできます。 ただし、EditorConfig およびグローバル AnalyzerConfig ファイルが優先され、ルールセット ファイルは非推奨となっています。 [ルールセットファイルを同等の EditorConfig ファイルに変換する](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)ことをお勧めします。 ルールセット ファイルと、EditorConfig またはグローバル AnalyzerConfig ファイルの競合する重要度エントリの優先順位は "_未定義_" です。

- 1 つのルールおよびそのルールが属するカテゴリに対して異なる重大度が指定されている場合など、異なるキーの関連する重要度オプションの優先順位ルールについては、「[コード分析の構成オプション](configuration-options.md#precedence)」を参照してください。

## <a name="see-also"></a>関連項目

- [EditorConfig とグローバル AnalyzerConfig の設計の問題](https://github.com/dotnet/roslyn/issues/47707)
