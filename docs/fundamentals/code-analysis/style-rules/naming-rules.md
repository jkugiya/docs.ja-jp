---
title: コード スタイルの名前付けルール
description: コード要素に名前を付けるための .NET コード スタイル ルールについて説明します。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: a61d0ca8684134207a11f79e382b6aaf843ba956
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873251"
---
# <a name="naming-rules"></a>名前付け規則

`.editorconfig` ファイルで、NET プログラミング言語のコード要素&mdash;クラス、プロパティ、メソッドなど&mdash;の名前の付け方を指定および適用する **名前付けルール** を定義できます。 たとえば、パブリック メンバーは大文字表記とする必要があること、またはプライベート フィールドは `_` で始まる必要があることを指定できます。

名前付けルールには、次の 3 つのコンポーネントがあります。

* ルールの適用先となる **シンボル グループ** (例: パブリック メンバー、プライベート フィールド)。
* ルールと関連付けられる **名前付けスタイル** (例: 名前は大文字にしなければならない、アンダースコアで始まる必要がある)。
* 規則を適用するための重大度。

まず、シンボル グループと名前付けスタイルを指定し、それぞれにタイトルを付ける必要があります。 次に、すべてをリンクする名前付けルールを指定します。

## <a name="general-syntax"></a>一般的な構文

名前付けルール、シンボル グループ、または名前付けスタイルを定義するには、次の構文を使用して 1 つ以上のプロパティを設定します。

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

各プロパティは一度だけ設定する必要がありますが、一部の設定では複数のコンマ区切り値も使用できます。

プロパティの順序は重要ではありません。

### \<kind>

**\<kind>** は、定義される要素の種類 &mdash;名前付けルール、シンボル グループ、または名前付けスタイル&mdash; を指定します。次のいずれかである必要があります。

| 設定対象のプロパティ | 使用する \<kind> 値 | 例 |
| --- | --- | -- |
| 名前付けルール | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| シンボル グループ | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| 名前付けスタイル | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

定義のそれぞれの種類 &mdash;[名前付けルール](#naming-rule-properties)、[シンボル グループ](#symbol-group-properties)、または[名前付けスタイル](#naming-style-properties)&mdash; には、サポートされる独自のプロパティがあります。これについては、次のセクションで説明します。

### \<title>

**\<title>** は、複数のプロパティ設定を 1 つの定義に関連付ける、自由に選択できるわかりやすい名前です。 たとえば、次のプロパティでは、`interface` と `types` という 2 つのシンボル グループ定義が生成され、そのそれぞれに 2 つのプロパティが設定されています。

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a>名前付けルールのプロパティ

ルールを有効にするには、すべての名前付けルール プロパティが必要です。

| プロパティ | 説明 |
| -- | -- |
| `symbols` | シンボル グループのタイトル。この名前付けルールは、このグループ内のシンボルに適用されます |
| `style` | このルールに関連付ける必要がある名前付けスタイルのタイトル |
| `severity` |  名前付けルールを適用する際の重大度を設定します。 関連する値を、使用可能な[重大度レベル](../configuration-options.md#severity-level)のいずれかに設定します。<sup>1</sup> |

**注:**

1. 名前付けルール内での重大度指定は、Visual Studio などの開発 IDE 内でのみ遵守されます。 この設定は、C# や VB のコンパイラでは認識されないため、ビルド時には遵守されません。 ビルドで名前付けスタイル ルールを適用するには、代わりに[コード ルールの重大度構成](#rule-id-ide1006-naming-rule-violation)を使用して重大度を設定する必要があります。 詳細については、[こちらの GitHub の問題](https://github.com/dotnet/roslyn/issues/44201)のページを参照してください。

## <a name="symbol-group-properties"></a>シンボル グループのプロパティ

シンボル グループに対しては、次のプロパティを設定して、グループに含めるシンボルを制限できます。 1 つのプロパティに複数の値を指定するには、値をコンマで区切ります。

| プロパティ | 説明 | 使用できる値 | 必須 |
| -- | -- | -- | -- |
| `applicable_kinds` | グループ内のシンボルの種類 <sup>1</sup> | `*`(この値を使用すると、すべてのシンボルが指定されます)<br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | はい |
| `applicable_accessibilities` | グループ内のシンボルのアクセシビリティ レベル | `*`(この値を使用すると、すべてのアクセシビリティ レベルが指定されます)<br/>`public`<br/>`internal` または `friend`<br/>`private`<br/>`protected`<br/>`protected_internal` または `protected_friend`<br/>`private_protected`<br/>`local` (メソッド内で定義されたシンボルの場合) | はい |
| `required_modifiers` | 指定した修飾子を "_すべて_" 持つシンボルとのみ一致 <sup>2</sup> | `abstract` または `must_inherit`<br/>`async`<br/>`const`<br/>`readonly`<br/>`static` または `shared` <sup>3</sup> | いいえ |

**注:**

1. タプル メンバーは、今のところ `applicable_kinds` ではサポートされていません。
2. このシンボル グループは、`required_modifiers` プロパティに含まれる "_すべて_" の修飾子と一致します。  このプロパティを省略すると、一致するために特定の修飾子が必要とされなくなります。 このことは、この規則が適用されるかどうかに、シンボルの修飾子が影響を及ぼさないことを意味します。
3. `required_modifiers` プロパティに `static` または `shared` があるグループの場合、そのグループには `const` シンボルも含まれます。これは、それらのシンボルが暗黙的に `static`/`Shared` であるためです。 ただし、`static` 名前付けルールが `const` シンボルに適用されないようにしたい場合は、`const` のシンボル グループを使用して新しい名前付けルールを作成できます。

## <a name="naming-style-properties"></a>名前付けスタイルのプロパティ

名前付けスタイルは、そのルールで適用する規則を定義します。 次に例を示します。

* `PascalCase` で大文字にする
* `m_` で始まる
* `_g` で終わる
* `__` で単語を区切る

名前付けスタイルには、次のプロパティを設定できます。

| プロパティ | 説明 | 使用できる値 | 必須 |
| -- | -- | -- | -- |
| `capitalization` | シンボル内の単語の大文字/小文字スタイル | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | 可<sup>1</sup> |
| `required_prefix` | この文字で始まる必要がある | | いいえ |
| `required_suffix` | この文字で終わる必要がある | | いいえ |
| `word_separator` | このシンボル内の単語は、この文字で区切る必要がある | | いいえ |

**注:**

1. 名前付けスタイルの一部として大文字/小文字スタイルを指定する必要があります。そうしないと、名前付けスタイルは無視される可能性があります。

## <a name="rule-order"></a>ルールの順序

EditorConfig ファイルで名前付けルールを定義する順序に意味はありません。 名前付けルールは、ルール自体の定義に従って自動的に並べ替えられます。 [EditorConfig 言語サービス拡張機能](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)では、EditorConfig ファイルを分析して、ファイルでの規則の順序が実行時にコンパイラで使用される順序と異なる場合に報告できます。

> [!NOTE]
>
> Visual Studio 2019 バージョン 16.2 より前のバージョンの Visual Studio を使用している場合は、EditorConfig ファイル内で、最も限定的なものから最も限定的でないものの順に名前付けルールを並べ替える必要があります。 適用可能な最初に検出されたルールのみが適用されます。 ただし、同じ名前のルールの "*プロパティ*" が複数ある場合は、その名前の最も最近見つかったプロパティが優先されます。 詳細については、「[File hierarchy and precedence (ファイルの階層と優先順位)](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence)」を参照してください。

## <a name="default-naming-styles"></a>既定の名前付けスタイル

カスタムの名前付けルールをまったく指定しない場合は、次の既定のスタイルが使用されます。

- アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるクラス、構造体、列挙型、プロパティ、およびイベントでは、既定の名前付けスタイルはパスカル ケースです。

- アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるインターフェイスでは、既定の名前付けスタイルはパスカル ケースであり、プレフィックス **I** を付ける必要があります。

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a>コード ルール ID: `IDE1006 (Naming rule violation)`

すべての名前付けオプションにルール ID `IDE1006` とタイトル `Naming rule violation` が指定されます。 EditorConfig ファイルで次の構文を使用して、名前付け違反の重大度をグローバルに構成できます。

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

[ビルド時に適用](../overview.md#code-style-analysis)するには、重大度の値を `warning` または `error` にする必要があります。 使用できるすべての重大度の値については、「[重大度レベル](../configuration-options.md#severity-level)」を参照してください。

## <a name="example"></a>例

次の *.editorconfig* ファイルには、パブリック プロパティ、メソッド、フィールド、イベント、デリゲートを大文字で入力する必要があることを指定した名前付け規則が含まれています。 この名前付け規則では、コンマを使用して個々のシンボル値を区切ることにより、規則を適用する複数の種類のシンボルを指定しています。

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="see-also"></a>関連項目

- [言語規則](language-rules.md)
- [書式設定規則](formatting-rules.md)
- [Roslyn 名前付けルール](https://github.com/dotnet/roslyn/blob/main/.editorconfig#L63)
- [.NET コード スタイルの規則のリファレンス](index.md)
