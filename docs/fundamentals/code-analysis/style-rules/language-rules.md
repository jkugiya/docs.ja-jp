---
title: コード スタイルの言語規則
description: C# および Visual Basic 言語コンストラクトの使用に関するさまざまなコード スタイルの規則について説明します。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
- language rules
- EditorConfig language conventions
ms.openlocfilehash: 2aa2261534363f1da6a2109f092e08d210ebd915
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "98957976"
---
# <a name="language-rules"></a>言語規則

コードスタイルの言語規則は、.NET プログラミング言語のさまざまなコンストラクト (修飾子、かっこなど) の使用方法に影響します。 この規則は次のカテゴリに分けられます。

- [.NET スタイル規則](#net-style-rules): C# と Visual Basic の両方に適用される規則。 これらの規則の EditorConfig オプション名は `dotnet_style_` プレフィックスで始まります。
- [C# スタイル規則](#c-style-rules): C# 言語のみに固有の規則。 これらの規則の EditorConfig オプション名は `csharp_style_` プレフィックスで始まります。
- [Visual Basic スタイル規則](#visual-basic-style-rules): Visual Basic 言語のみに固有の規則。 これらの規則の EditorConfig オプション名は `visual_basic_style_` プレフィックスで始まります。

## <a name="option-format"></a>オプションの書式

言語規則のオプションは、EditorConfig ファイルで、次の形式で指定できます。

`option_name = value` (Visual Studio 2019 バージョン 16.9 プレビュー 2 以降)

または

`option_name = value:severity`

- **Value**

  各言語規則では、そのスタイルを優先する場合や状況を指定します。 多くのルールでは、`true` (このスタイルを優先する) または `false` (このスタイルを優先しない) の値が受け付けられます。 それ以外では、`when_on_single_line` や `never` などの値が受け付けられます。

- **Severity** (Visual Studio 2019 バージョン 16.9 プレビュー 2 以降のバージョンでは省略可能)

  規則の 2 番目の部分では、規則の[重大度レベル](../configuration-options.md#severity-level)を指定します。 この方法で指定した場合、重大度の設定は、Visual Studio などの開発 IDE 内でのみ遵守されます。 ビルド時には遵守 *されません*。

  ビルド時にコード スタイルの規則を適用するには、代わりにアナライザーに対して規則 ID ベースの重大度構成構文を使用して重大度を設定します。 この構文では `dotnet_diagnostic.<rule ID>.severity = <severity>` 形式が使用されます。たとえば、`dotnet_diagnostic.IDE0040.severity = silent` のようになります。 詳細については、「[重大度レベル](../configuration-options.md#severity-level)」を参照してください。

> [!TIP]
>
> Visual Studio 2019 バージョン 16.3 以降、スタイル違反後、[[クイック アクション]](/visualstudio/ide/quick-actions) という電球メニューからコード スタイルの規則を構成できます。 詳細については、[Visual Studio でのコード スタイルの自動的な構成](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio)に関するページを参照してください。

## <a name="net-style-rules"></a>.NET スタイル規則

このセクションのスタイル ルールは、C# および Visual Basic の両方に適用されます。

- ['this.' と 'Me.' 修飾子](ide0003-ide0009.md)
  - [dotnet_style_qualification_for_field](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [dotnet_style_qualification_for_property](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [dotnet_style_qualification_for_method](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [dotnet_style_qualification_for_event](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [型参照のためのフレームワーク型名の代わりの言語キーワード](ide0049.md)
  - [dotnet_style_predefined_type_for_locals_parameters_members](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [dotnet_style_predefined_type_for_member_access](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [修飾子の基本設定](modifier-preferences.md#net-modifier-preferences)
  - [dotnet_style_require_accessibility_modifiers](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [csharp_preferred_modifier_order](ide0036.md#csharp_preferred_modifier_order)
  - [visual_basic_preferred_modifier_order](ide0036.md#visual_basic_preferred_modifier_order)
  - [dotnet_style_readonly_field](ide0044.md#dotnet_style_readonly_field)
- [かっこの基本設定](ide0047-ide0048.md)
  - [dotnet_style_parentheses_in_arithmetic_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [dotnet_style_parentheses_in_relational_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [dotnet_style_parentheses_in_other_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [dotnet_style_parentheses_in_other_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [式レベル基本設定](expression-level-preferences.md#net-expression-level-preferences)
  - [dotnet_style_object_initializer](ide0017.md#dotnet_style_object_initializer)
  - [dotnet_style_collection_initializer](ide0028.md#dotnet_style_collection_initializer)
  - [dotnet_style_explicit_tuple_names](ide0033.md#dotnet_style_explicit_tuple_names)
  - [dotnet_style_prefer_inferred_tuple_names](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [dotnet_style_prefer_inferred_anonymous_type_member_names](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [dotnet_style_prefer_auto_properties](ide0032.md#dotnet_style_prefer_auto_properties)
  - [dotnet_style_prefer_conditional_expression_over_assignment](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [dotnet_style_prefer_conditional_expression_over_return](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [dotnet_style_prefer_compound_assignment](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [dotnet_style_prefer_simplified_interpolation](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [dotnet_style_prefer_simplified_boolean_expressions](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - [不足しているケースを switch ステートメントに追加する](ide0010.md) - この規則にはコード スタイル オプションがありません。
  - [匿名型からタプルへの変換](ide0050.md) -この規則にはコード スタイル オプションがありません。
  - ['System.Hashcode.Combine' を使用します](ide0070.md) - この規則にはコード スタイル オプションがありません。
  - ['typeof' を 'nameof' に変換](ide0082.md) - この規則にはコード スタイル オプションがありません。
- ["Null" 検査設定](null-checking-preferences.md#net-null-checking-preferences)
  - [dotnet_style_coalesce_expression](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [dotnet_style_null_propagation](ide0031.md#dotnet_style_null_propagation)
  - [dotnet_style_prefer_is_null_check_over_reference_equality_method](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [ファイル ヘッダーの基本設定](ide0073.md)
  - [file_header_template](ide0073.md#file_header_template)

## <a name="c-style-rules"></a>C# スタイル規則

このセクションのスタイル規則は、C# 言語のみに適用されます。

- ['var' の基本設定](ide0007-ide0008.md)
  - [csharp_style_var_for_built_in_types](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [csharp_style_var_when_type_is_apparent](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [csharp_style_var_elsewhere](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [式形式のメンバー](expression-bodied-members.md)
  - [csharp_style_expression_bodied_methods](ide0022.md#csharp_style_expression_bodied_methods)
  - [csharp_style_expression_bodied_constructors](ide0021.md#csharp_style_expression_bodied_constructors)
  - [csharp_style_expression_bodied_operators](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [csharp_style_expression_bodied_properties](ide0025.md#csharp_style_expression_bodied_properties)
  - [csharp_style_expression_bodied_indexers](ide0026.md#csharp_style_expression_bodied_indexers)
  - [csharp_style_expression_bodied_accessors](ide0027.md#csharp_style_expression_bodied_accessors)
  - [csharp_style_expression_bodied_lambdas](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [csharp_style_expression_bodied_local_functions](ide0061.md#csharp_style_expression_bodied_local_functions)
- [パターン マッチング設定](pattern-matching-preferences.md)
  - [csharp_style_pattern_matching_over_is_with_cast_check](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [csharp_style_pattern_matching_over_as_with_null_check](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [csharp_style_prefer_switch_expression](ide0066.md#csharp_style_prefer_switch_expression)
  - [csharp_style_prefer_pattern_matching](ide0078.md#csharp_style_prefer_pattern_matching)
  - [csharp_style_prefer_not_pattern](ide0083.md#csharp_style_prefer_not_pattern)
- [式レベル基本設定](expression-level-preferences.md#c-expression-level-preferences)
  - [csharp_style_inlined_variable_declaration](ide0018.md#csharp_style_inlined_variable_declaration)
  - [csharp_prefer_simple_default_expression](ide0034.md#csharp_prefer_simple_default_expression)
  - [csharp_style_pattern_local_over_anonymous_function](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [csharp_style_deconstructed_variable_declaration](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [csharp_style_prefer_index_operator](ide0056.md#csharp_style_prefer_index_operator)
  - [csharp_style_prefer_range_operator](ide0057.md#csharp_style_prefer_range_operator)
  - [csharp_style_implicit_object_creation_when_type_is_apparent](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - [不足しているケースを switch 式に追加する](ide0072.md) - この規則にはコード スタイル オプションがありません。
- ["null" チェック設定](null-checking-preferences.md#c-null-checking-preferences)
  - [csharp_style_throw_expression](ide0016.md#csharp_style_throw_expression)
  - [csharp_style_conditional_delegate_call](ide1005.md#csharp_style_conditional_delegate_call)
- [コード ブロック基本設定](code-block-preferences.md)
  - [csharp_prefer_braces](ide0011.md#csharp_prefer_braces)
  - [csharp_prefer_simple_using_statement](ide0063.md#csharp_prefer_simple_using_statement)
- [using ディレクティブの基本設定](ide0065.md)
  - [csharp_using_directive_placement](ide0065.md#csharp_using_directive_placement)
- [修飾子の基本設定](modifier-preferences.md#c-modifier-preferences)
  - [csharp_prefer_static_local_function](ide0062.md#csharp_prefer_static_local_function)
  - [構造体フィールドを書き込み可能にする](ide0064.md) - この規則にはコード スタイル オプションがありません。

## <a name="visual-basic-style-rules"></a>Visual Basic のスタイル規則

このセクションのスタイル規則は、Visual Basic 言語のみに適用されます。

- [パターン マッチング設定](pattern-matching-preferences.md)
  - [visual_basic_style_prefer_isnot_expression](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a>関連項目

- [不要なコード規則](unnecessary-code-rules.md)
- [書式設定規則](formatting-rules.md)
- [名前付け規則](naming-rules.md)
- [.NET コード スタイルの規則のリファレンス](index.md)
