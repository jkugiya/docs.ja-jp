---
title: .NET コード スタイル ルール オプション
description: .NET コード スタイルのオプションを指定する方法について説明します。
ms.date: 09/25/2020
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 52419591447b2b92e67a68ab911af49af242d33a
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740983"
---
# <a name="code-style-rule-options"></a>コード スタイル ルール オプション

.NET コード スタイル ルール オプションを [EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) ファイルで定義することにより、一貫性のある "*コード スタイル*" を定義してコードベースで維持することができます。 これらのルールは、コードを編集するときに、Visual Studio などのさまざまな開発 IDE によって表示されます。 .NET プロジェクトの場合は、これらのルールを[ビルド時に適用](overview.md#code-style-analysis)することもできます。 個々のルールを有効または無効にしたり、各ルールを適用するレベルを重大度レベルで構成したりすることができます。

> [!TIP]
>
> - EditorConfig ファイルでコード スタイル オプションを定義すると、[コード スタイル アナライザー](overview.md#code-style-analysis)によるコードの分析方法も構成されます。 EditorConfig ファイルは、これらのアナライザーに対する構成ファイルです。
>
> - コード スタイル オプションは、Visual Studio の[テキスト エディターの [オプション]](/visualstudio/ide/code-styles-and-code-cleanup) ダイアログで設定することもできます。 これらは、Visual Studio での編集時にのみ遵守されるユーザーごとのオプションです。 これらのオプションは、ビルド時や他の IDE によって遵守されることはありません。 また、Visual Studio 内で開かれたプロジェクトまたはソリューションに EditorConfig ファイルがある場合は、EditorConfig ファイルのオプションが優先されます。

コード スタイル ルールは、次のサブカテゴリに分類されます。

- [言語規則](style-rules/language-rules.md)

- [不要なコード規則](style-rules/unnecessary-code-rules.md)

- [書式設定規則](style-rules/formatting-rules.md)

- [名前付け規則](style-rules/naming-rules.md)

これらのサブカテゴリごとに、オプションを指定するための独自の構文が定義されています。 これらのルールおよび対応するオプションの詳細については、[コード スタイル ルールのリファレンス](style-rules/index.md)を参照してください。

## <a name="example-editorconfig-file"></a>EditorConfig ファイルの例

作業の開始に役立つように、ここでは既定のオプションを使用する *.editorconfig* ファイルの例を示します。

> [!TIP]
> Visual Studio では、このファイルを生成してプロジェクトに保存するには、 **[ツール]**  >  **[オプション]**  >  **[テキスト エディター]** > **[C#]** または **[Basic]** > **[コード スタイル]**  >  **[全般]** の順に選択します。 次に、 **[設定から editorconfig ファイルを生成]** ボタンをクリックします。 詳細については、「[コードのスタイル設定](/visualstudio/ide/code-styles-and-code-cleanup)」を参照してください。

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

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### .NET Coding Conventions ####

# Organize usings
dotnet_separate_import_directive_groups = false
dotnet_sort_system_directives_first = false
file_header_template = unset

# this. and Me. preferences
dotnet_style_qualification_for_event = false:silent
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_property = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent

# Expression-level preferences
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_object_initializer = true:suggestion
dotnet_style_operator_placement_when_wrapping = beginning_of_line
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_compound_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:suggestion
dotnet_style_prefer_simplified_boolean_expressions = true:suggestion
dotnet_style_prefer_simplified_interpolation = true:suggestion

# Field preferences
dotnet_style_readonly_field = true:suggestion

# Parameter preferences
dotnet_code_quality_unused_parameters = all:suggestion

# Suppression preferences
dotnet_remove_unnecessary_suppression_exclusions = none

#### C# Coding Conventions ####

# var preferences
csharp_style_var_elsewhere = false:silent
csharp_style_var_for_built_in_types = false:silent
csharp_style_var_when_type_is_apparent = false:silent

# Expression-bodied members
csharp_style_expression_bodied_accessors = true:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent

# Pattern matching preferences
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_prefer_not_pattern = true:suggestion
csharp_style_prefer_pattern_matching = true:silent
csharp_style_prefer_switch_expression = true:suggestion

# Null-checking preferences
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_prefer_static_local_function = true:suggestion
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:silent

# Code-block preferences
csharp_prefer_braces = true:silent
csharp_prefer_simple_using_statement = true:suggestion

# Expression-level preferences
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
csharp_style_throw_expression = true:suggestion
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
csharp_style_unused_value_expression_statement_preference = discard_variable:silent

# 'using' directive preferences
csharp_using_directive_placement = inside_namespace:silent

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = true
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = suggestion
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i

dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case

dotnet_naming_rule.non_field_members_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.non_field_members_should_be_pascal_case.symbols = non_field_members
dotnet_naming_rule.non_field_members_should_be_pascal_case.style = pascal_case

# Symbol specifications

dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.interface.required_modifiers =

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.types.required_modifiers =

dotnet_naming_symbols.non_field_members.applicable_kinds = property, event, method
dotnet_naming_symbols.non_field_members.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.non_field_members.required_modifiers =

# Naming styles

dotnet_naming_style.pascal_case.required_prefix =
dotnet_naming_style.pascal_case.required_suffix =
dotnet_naming_style.pascal_case.word_separator =
dotnet_naming_style.pascal_case.capitalization = pascal_case

dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.required_suffix =
dotnet_naming_style.begins_with_i.word_separator =
dotnet_naming_style.begins_with_i.capitalization = pascal_case

```

## <a name="see-also"></a>関連項目

- [コード スタイルの分析ルールのリファレンス](style-rules/index.md)
- [ビルド時にコード スタイルを適用する](overview.md#code-style-analysis)
- [Visual Studio のクイック アクション](/visualstudio/ide/quick-actions)
- [Visual Studio で移植可能なカスタム エディター オプションを作成する](/visualstudio/ide/create-portable-custom-editor-options)
- [.NET Compiler Platform "Roslyn" .editorconfig ファイル](https://github.com/dotnet/roslyn/blob/main/.editorconfig)
- [.NET ランタイムの .editorconfig ファイル](https://github.com/dotnet/runtime/blob/main/.editorconfig)
