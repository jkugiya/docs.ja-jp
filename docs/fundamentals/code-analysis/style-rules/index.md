---
title: コード スタイル ルールの概要
description: さまざまな .NET コード スタイル ルールとカテゴリについて説明します。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 53c23b1489f3419b0e3c0c3eefdb1cebade5f966
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "103235231"
---
# <a name="code-style-rules"></a>コード スタイル規則

.NET コード スタイルの分析には、コードベースで一貫性のある "*コード スタイル*" を維持することを目的としたルールが用意されています。 これらのルールには、ルール ID に "IDE" というプレフィックスが付いています。 ほとんどのルールには、希望のスタイルをカスタマイズするためのオプションが関連付けられています。 ルールは、次のサブカテゴリに分類されます。

- [言語規則](language-rules.md)

   C# または Visual Basic 言語に関するルール。 たとえば、変数を定義するときの `var` の使用に関するルールや、式形式のメンバーを優先するかどうかを指定できます。

- [不要なコード規則](unnecessary-code-rules.md)

   読みやすさ、保守性、パフォーマンス、または機能上の問題を示す、不要なコードに関するルール。 たとえば、メソッドや使用されていない非公開フィールド、プロパティ、またはメソッド内の到達できないコードは、不要なコードです。

- [書式設定規則](formatting-rules.md)

   コードを読みやすくするためのレイアウトや構造に関するルール。 たとえば、オールマンでの中かっこに関するルールや、制御ブロックでスペースを優先するかどうかを指定できます。

- [名前付け規則](naming-rules.md)

   コード要素の名前付けに関するルール。 たとえば、`async` メソッド名に "Async" サフィックスが必要であることを指定できます。

- [その他の規則](miscellaneous-rules.md)

   他のカテゴリに属さないルール。

## <a name="index"></a>インデックス

次の表に、すべてのコード スタイル ルールを ID とオプション (存在する場合) ごとに示します。

> [!div class="mx-tdCol3BreakAll"]
> | ルールの ID | タイトル | オプション |
> | - | - | - |
> | [IDE0001](ide0001.md) | 名前を簡略化する | |
> | [IDE0002](ide0002.md) | メンバー アクセスを簡略化する | |
> | [IDE0003](ide0003-ide0009.md) | `this` または `Me` の修飾を削除する | [dotnet_style_qualification_for_field](ide0003-ide0009.md#dotnet_style_qualification_for_field)<br/> [dotnet_style_qualification_for_property](ide0003-ide0009.md#dotnet_style_qualification_for_property)<br/> [dotnet_style_qualification_for_method](ide0003-ide0009.md#dotnet_style_qualification_for_method)<br/> [dotnet_style_qualification_for_event](ide0003-ide0009.md#dotnet_style_qualification_for_event) |
> | [IDE0004](ide0004.md) | 不要なキャストを削除する | |
> | [IDE0005](ide0005.md) | 不要なインポートを削除する | |
> | [IDE0007](ide0007-ide0008.md) | 明示的な型の代わりに `var` を使用する | [csharp_style_var_for_built_in_types](ide0007-ide0008.md#csharp_style_var_for_built_in_types)<br/> [csharp_style_var_when_type_is_apparent](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)<br/> [csharp_style_var_elsewhere](ide0007-ide0008.md#csharp_style_var_elsewhere)<br/> |
> | [IDE0008](ide0007-ide0008.md) | `var` の代わりに明示的な型を使用する | [csharp_style_var_for_built_in_types](ide0007-ide0008.md#csharp_style_var_for_built_in_types)<br/> [csharp_style_var_when_type_is_apparent](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)<br/> [csharp_style_var_elsewhere](ide0007-ide0008.md#csharp_style_var_elsewhere)<br/> |
> | [IDE0009](ide0003-ide0009.md) | `this` または `Me` の修飾を追加する | [dotnet_style_qualification_for_field](ide0003-ide0009.md#dotnet_style_qualification_for_field)<br/> [dotnet_style_qualification_for_property](ide0003-ide0009.md#dotnet_style_qualification_for_property)<br/> [dotnet_style_qualification_for_method](ide0003-ide0009.md#dotnet_style_qualification_for_method)<br/> [dotnet_style_qualification_for_event](ide0003-ide0009.md#dotnet_style_qualification_for_event) |
> | [IDE0010](ide0010.md) | 不足しているケースを switch ステートメントに追加する | |
> | [IDE0011](ide0011.md) | 中かっこを追加する | [csharp_prefer_braces](ide0011.md#csharp_prefer_braces) |
> | [IDE0016](ide0016.md) | throw 式を使用する | [csharp_style_throw_expression](ide0016.md#csharp_style_throw_expression) |
> | [IDE0017](ide0017.md) | オブジェクト初期化子を使用する | [dotnet_style_object_initializer](ide0017.md#dotnet_style_object_initializer) |
> | [IDE0018](ide0018.md) | インライン変数宣言 | [csharp_style_inlined_variable_declaration](ide0018.md#csharp_style_inlined_variable_declaration) |
> | [IDE0019](ide0019.md) | パターン マッチングを使用して `as` の後に `null` チェックが発生しないようにする | [csharp_style_pattern_matching_over_as_with_null_check](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check) |
> | [IDE0020](ide0020-ide0038.md) | パターン マッチングを使用して、`is` チェックの後にキャスト (変数を含む) が発生しないようにする | [csharp_style_pattern_matching_over_is_with_cast_check](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check) |
> | [IDE0021](ide0021.md) | コンストラクターに式本体を使用する | [csharp_style_expression_bodied_constructors](ide0021.md#csharp_style_expression_bodied_constructors) |
> | [IDE0022](ide0022.md) | メソッドに式本体を使用する | [csharp_style_expression_bodied_methods](ide0022.md#csharp_style_expression_bodied_methods) |
> | [IDE0023](ide0023-ide0024.md) | 変換演算子に式本体を使用する | [csharp_style_expression_bodied_operators](ide0023-ide0024.md#csharp_style_expression_bodied_operators) |
> | [IDE0024](ide0023-ide0024.md) | 演算子に式本体を使用する | [csharp_style_expression_bodied_operators](ide0023-ide0024.md#csharp_style_expression_bodied_operators) |
> | [IDE0025](ide0025.md) | プロパティに式本体を使用する | [csharp_style_expression_bodied_properties](ide0025.md#csharp_style_expression_bodied_properties) |
> | [IDE0026](ide0026.md) | インデクサーに式本体を使用する | [csharp_style_expression_bodied_indexers](ide0026.md#csharp_style_expression_bodied_indexers) |
> | [IDE0027](ide0027.md) | アクセサーに式本体を使用する | [csharp_style_expression_bodied_accessors](ide0027.md#csharp_style_expression_bodied_accessors) |
> | [IDE0028](ide0028.md) | コレクション初期化子を使用する | [dotnet_style_collection_initializer](ide0028.md#dotnet_style_collection_initializer) |
> | [IDE0029](ide0029-ide0030.md) | coalesce 式を使用する (null 非許容型) | [dotnet_style_coalesce_expression](ide0029-ide0030.md#dotnet_style_coalesce_expression) |
> | [IDE0030](ide0029-ide0030.md) | coalesce 式を使用する (null 許容型) | [dotnet_style_coalesce_expression](ide0029-ide0030.md#dotnet_style_coalesce_expression) |
> | [IDE0031](ide0031.md) | null 値の反映を使用する | [dotnet_style_null_propagation](ide0031.md#dotnet_style_null_propagation) |
> | [IDE0032](ide0032.md) | 自動プロパティを使用する | [dotnet_style_prefer_auto_properties](ide0032.md#dotnet_style_prefer_auto_properties) |
> | [IDE0033](ide0033.md) | 明示的に提供されたタプル名を使用する | [dotnet_style_explicit_tuple_names](ide0033.md#dotnet_style_explicit_tuple_names) |
> | [IDE0034](ide0034.md) | `default` 式を簡略化する | [csharp_prefer_simple_default_expression](ide0034.md#csharp_prefer_simple_default_expression) |
> | [IDE0035](ide0035.md) | 到達できないコードの削除 | |
> | [IDE0036](ide0036.md) | 修飾子を順序付けする | [csharp_preferred_modifier_order](ide0036.md#csharp_preferred_modifier_order)<br/> [visual_basic_preferred_modifier_order](ide0036.md#visual_basic_preferred_modifier_order)<br/> |
> | [IDE0037](ide0037.md) | 推定メンバーの名前を使用する | [dotnet_style_prefer_inferred_tuple_names](ide0037.md#dotnet_style_prefer_inferred_tuple_names)<br/> [dotnet_style_prefer_inferred_anonymous_type_member_names](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names) |
> | [IDE0038](ide0020-ide0038.md) | パターン マッチングを使用して、`is` チェックの後にキャスト (変数を含まない) が発生しないようにする | [csharp_style_pattern_matching_over_is_with_cast_check](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check) |
> | [IDE0039](ide0039.md) | ラムダの代わりにローカル関数を使用する | [csharp_style_pattern_local_over_anonymous_function](ide0039.md#csharp_style_pattern_local_over_anonymous_function) |
> | [IDE0040](ide0040.md) | アクセシビリティ修飾子の追加 | [dotnet_style_require_accessibility_modifiers](ide0040.md#dotnet_style_require_accessibility_modifiers) |
> | [IDE0041](ide0041.md) | is null チェックを使用する | [dotnet_style_prefer_is_null_check_over_reference_equality_method](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method) |
> | [IDE0042](ide0042.md) | 変数宣言を分解する | [csharp_style_deconstructed_variable_declaration](ide0042.md#csharp_style_deconstructed_variable_declaration) |
> | [IDE0044](ide0044.md) | 読み取り専用修飾子を追加する | [dotnet_style_readonly_field](ide0044.md#dotnet_style_readonly_field) |
> | [IDE0045](ide0045.md) | 代入に条件式を使用する | [dotnet_style_prefer_conditional_expression_over_assignment](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment) |
> | [IDE0046](ide0046.md) | 戻り値に条件式を使用する | [dotnet_style_prefer_conditional_expression_over_return](ide0046.md#dotnet_style_prefer_conditional_expression_over_return) |
> | [IDE0047](ide0047-ide0048.md) | 不要なかっこを削除する | [dotnet_style_parentheses_in_arithmetic_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)<br/> [dotnet_style_parentheses_in_relational_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)<br/> [dotnet_style_parentheses_in_other_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)<br/> [dotnet_style_parentheses_in_other_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators) |
> | [IDE0048](ide0047-ide0048.md) | わかりやすくするためにかっこを追加する | [dotnet_style_parentheses_in_arithmetic_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)<br/> [dotnet_style_parentheses_in_relational_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)<br/> [dotnet_style_parentheses_in_other_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)<br/> [dotnet_style_parentheses_in_other_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators) |
> | [IDE0049](ide0049.md) | 型参照のためのフレームワーク型名の代わりに言語キーワードを使用する | [dotnet_style_predefined_type_for_locals_parameters_members](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)<br/> [dotnet_style_predefined_type_for_member_access](ide0049.md#dotnet_style_predefined_type_for_member_access)<br/> |
> | [IDE0050](ide0050.md) | 匿名型をタプルに変換する | |
> | [IDE0051](ide0051.md) | 使用されていない非公開メンバーを削除する | |
> | [IDE0052](ide0052.md) | 読み取られていない非公開メンバーを削除する | |
> | [IDE0053](ide0053.md) | ラムダに式本体を使用する | [csharp_style_expression_bodied_lambdas](ide0053.md#csharp_style_expression_bodied_lambdas) |
> | [IDE0054](ide0054-ide0074.md) | 複合代入を使用する | [dotnet_style_prefer_compound_assignment](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment) |
> | [IDE0055](formatting-rules.md) | 書式設定を修正する | |
> | [IDE0056](ide0056.md) | インデックス演算子を使用する | [csharp_style_prefer_index_operator](ide0056.md#csharp_style_prefer_index_operator) |
> | [IDE0057](ide0057.md) | 範囲演算子を使用する | [csharp_style_prefer_range_operator](ide0057.md#csharp_style_prefer_range_operator) |
> | [IDE0058](ide0058.md) | 使用されていない式の値を削除する | [csharp_style_unused_value_expression_statement_preference](ide0058.md#csharp_style_unused_value_expression_statement_preference)<br/> [visual_basic_style_unused_value_expression_statement_preference](ide0058.md#visual_basic_style_unused_value_expression_statement_preference) |
> | [IDE0059](ide0059.md) | 不要な値の代入を削除する | [csharp_style_unused_value_assignment_preference](ide0059.md#csharp_style_unused_value_assignment_preference)<br/> [visual_basic_style_unused_value_assignment_preference](ide0059.md#visual_basic_style_unused_value_assignment_preference) |
> | [IDE0060](ide0060.md) | 使用されていないパラメーターを削除する | [dotnet_code_quality_unused_parameters](ide0060.md#dotnet_code_quality_unused_parameters) |
> | [IDE0061](ide0061.md) | ローカル関数に式本体を使用する | [csharp_style_expression_bodied_local_functions](ide0061.md#csharp_style_expression_bodied_local_functions) |
> | [IDE0062](ide0062.md) | ローカル関数を静的にする | [csharp_prefer_static_local_function](ide0062.md#csharp_prefer_static_local_function) |
> | [IDE0063](ide0063.md) | 単純な `using` ステートメントを使用する | [csharp_prefer_simple_using_statement](ide0063.md#csharp_prefer_simple_using_statement) |
> | [IDE0064](ide0064.md) | 構造体のフィールドを書き込み可能にする | |
> | [IDE0065](ide0065.md) | `using` ディレクティブの配置 | [csharp_using_directive_placement](ide0065.md#csharp_using_directive_placement) |
> | [IDE0066](ide0066.md) | switch 式を使用する | [csharp_style_prefer_switch_expression](ide0066.md#csharp_style_prefer_switch_expression) |
> | [IDE0070](ide0070.md) | <xref:System.HashCode.Combine%2A?displayProperty=fullName> を使用します | |
> | [IDE0071](ide0071.md) | 補間を簡略化する | [dotnet_style_prefer_simplified_interpolation](ide0071.md#dotnet_style_prefer_simplified_interpolation) |
> | [IDE0072](ide0072.md) | 不足しているケースを switch 式に追加する | |
> | [IDE0073](ide0073.md) | ファイル ヘッダーを使用する | [file_header_template](ide0073.md#file_header_template) |
> | [IDE0074](ide0054-ide0074.md) | 結合複合代入を使用する | [dotnet_style_prefer_compound_assignment](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment) |
> | [IDE0075](ide0075.md) | 条件式を簡略化する | [dotnet_style_prefer_simplified_boolean_expressions](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions) |
> | [IDE0076](ide0076.md) | 無効でグローバルな `SuppressMessageAttribute` を削除する | |
> | [IDE0077](ide0077.md) | グローバルな `SuppressMessageAttribute` でレガシ形式のターゲットを回避する | |
> | [IDE0078](ide0078.md) | パターン マッチングの使用 | [csharp_style_prefer_pattern_matching](ide0078.md#csharp_style_prefer_pattern_matching) |
> | [IDE0079](ide0079.md) | 不要な抑制を削除する | [dotnet_remove_unnecessary_suppression_exclusions](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions) |
> | [IDE0080](ide0080.md) | 不要な抑制演算子を削除する | |
> | [IDE0081](ide0081.md) | `ByVal` を削除します | |
> | [IDE0082](ide0082.md) | `typeof` を `nameof` に変換する | |
> | [IDE0083](ide0083.md) | パターン マッチングを使用する (`not` 演算子) | [csharp_style_prefer_not_pattern](ide0083.md#csharp_style_prefer_not_pattern) |
> | [IDE0084](ide0084.md) | パターン マッチングを使用する (`IsNot` 演算子) | [visual_basic_style_prefer_isnot_expression](ide0084.md#visual_basic_style_prefer_isnot_expression) |
> | [IDE0090](ide0090.md) | `new` 式を簡略化する | [csharp_style_implicit_object_creation_when_type_is_apparent](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent) |
> | [IDE0100](ide0100.md) | 不要な等値演算子を削除する | |
> | [IDE0110](ide0110.md) | [Remove unnecessary discard]\(不要な破棄を削除する\) | |
> | [IDE1005](ide1005.md) | 条件付き代理呼び出しを使用する | [csharp_style_conditional_delegate_call](ide1005.md#csharp_style_conditional_delegate_call) |
> | [IDE1006](naming-rules.md) | 命名スタイル | |

## <a name="legend"></a>凡例

次の表は、参照ドキュメントの各ルールについて提供されている情報の種類を示しています。

|項目|説明|
|----------|-----------------|
| **ルール ID** |規則の一意の識別子。 ルール ID は、ルールの重要度を構成し、コード ファイルでの警告を抑制するために使用されます。|
| **Title** |ルールのタイトル。|
| **カテゴリ** | ルールのカテゴリ。 |
| **Subcategory** | ルールのサブカテゴリ (言語ルール、書式設定ルール、名前付けルールなど)。 |
| **該当言語** |最低限の言語バージョン (存在する場合) で適用可能な .NET の言語 (C# または Visual Basic)。|
| **導入されたバージョン** |ルールが最初に導入されたときの .NET SDK または Visual Studio のバージョン。|

ルールの各オプションについて、次の情報が提供されます。

|項目|説明|
|----------|-----------------|
| **オプション名** |ルールのコード スタイル オプション名 (存在する場合)。 スタイルをカスタマイズするためのオプションは、EditorConfig ファイルで指定されています。|
| **オプションの値** |ルール オプションのコード スタイル オプションの値 (存在する場合)。|
| **既定のオプションの値** |ルール オプションの既定のコード スタイル オプションの値 (存在する場合)。
| **使用例** |オプションに対応するコード スタイルの例。|

## <a name="see-also"></a>関連項目

- [ビルド時にコード スタイルを適用する](../overview.md#code-style-analysis)
- [Visual Studio のクイック アクション](/visualstudio/ide/quick-actions)
- [Visual Studio で移植可能なカスタム エディター オプションを作成する](/visualstudio/ide/create-portable-custom-editor-options)
