---
title: コードスタイルの名前付け規則
description: コード要素に名前を付けるための .NET コードスタイル規則について説明します。
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
ms.openlocfilehash: 1fce275204b729b4d23729ca432e06a5a249620d
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065136"
---
# <a name="naming-rules"></a><span data-ttu-id="3c916-103">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="3c916-103">Naming rules</span></span>

<span data-ttu-id="3c916-104">ファイルでは `.editorconfig` 、クラス、プロパティ、メソッドなどの .net プログラミング言語コード要素の名前付け方法に関する **名前付け規則** を定義でき &mdash; &mdash; ます。</span><span class="sxs-lookup"><span data-stu-id="3c916-104">In your `.editorconfig` file, you can define **naming rules** for how .NET programming language code elements&mdash;such as classes, properties, and methods&mdash;should be named.</span></span> <span data-ttu-id="3c916-105">たとえば、パブリックメンバーを大文字にする必要がある場合や、プライベートフィールドの先頭がであることを指定でき `_` ます。</span><span class="sxs-lookup"><span data-stu-id="3c916-105">For example, you can specify that public members must be capitalized, or that private fields must begin with `_`.</span></span>

<span data-ttu-id="3c916-106">名前付け規則には、次の3つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="3c916-106">A naming rule has three components:</span></span>

* <span data-ttu-id="3c916-107">**シンボルグループ** は、 &mdash; ルールが適用されるシンボルのグループです。</span><span class="sxs-lookup"><span data-stu-id="3c916-107">The **symbol group**&mdash;the group of symbols the rule applies to.</span></span>
* <span data-ttu-id="3c916-108">規則に関連付ける **名前付けスタイル** 。</span><span class="sxs-lookup"><span data-stu-id="3c916-108">The **naming style** to associate with the rule.</span></span>
* <span data-ttu-id="3c916-109">規則を適用するための重大度。</span><span class="sxs-lookup"><span data-stu-id="3c916-109">The severity for enforcing the convention.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="3c916-110">一般的な構文</span><span class="sxs-lookup"><span data-stu-id="3c916-110">General syntax</span></span>

<span data-ttu-id="3c916-111">名前付け規則、シンボルグループ、または名前付けスタイルを定義するには、次の構文を使用して1つ以上のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="3c916-111">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="3c916-112">各プロパティは一度だけ設定する必要がありますが、一部の設定では複数のコンマ区切りの値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c916-112">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="3c916-113">プロパティの順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="3c916-113">The order of the properties is not important.</span></span>

### \<kind>

<span data-ttu-id="3c916-114">**\<kind>** 定義する &mdash; 名前付け規則、シンボルグループ、または名前付けスタイルの要素の種類を指定し &mdash; ます。次のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-114">**\<kind>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="3c916-115">のプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="3c916-115">To set a property for</span></span> | <span data-ttu-id="3c916-116">値を使用する \<kind></span><span class="sxs-lookup"><span data-stu-id="3c916-116">Use the \<kind> value</span></span> | <span data-ttu-id="3c916-117">例</span><span class="sxs-lookup"><span data-stu-id="3c916-117">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="3c916-118">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="3c916-118">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="3c916-119">シンボルグループ</span><span class="sxs-lookup"><span data-stu-id="3c916-119">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="3c916-120">名前付けスタイル</span><span class="sxs-lookup"><span data-stu-id="3c916-120">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="3c916-121">&mdash;次のセクションで説明するように、定義の[名前付け規則](#naming-rule-properties)、[シンボルグループ](#symbol-group-properties)、または[名前付けスタイル](#naming-style-properties)の各種類 &mdash; には、独自のサポートされるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3c916-121">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="3c916-122">**\<title>** 複数のプロパティ設定を1つの定義に関連付けるために選択するわかりやすい名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c916-122">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="3c916-123">たとえば、次のプロパティでは、とという2つのシンボルグループ定義が生成され `interface` `types` ます。それぞれに2つのプロパティが設定されています。</span><span class="sxs-lookup"><span data-stu-id="3c916-123">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="3c916-124">名前付け規則のプロパティ</span><span class="sxs-lookup"><span data-stu-id="3c916-124">Naming rule properties</span></span>

<span data-ttu-id="3c916-125">ルールを有効にするには、すべての名前付けルールプロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c916-125">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="3c916-126">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3c916-126">Property</span></span> | <span data-ttu-id="3c916-127">説明</span><span class="sxs-lookup"><span data-stu-id="3c916-127">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="3c916-128">シンボルグループのタイトル。このグループのシンボルには名前付け規則が適用されます</span><span class="sxs-lookup"><span data-stu-id="3c916-128">The title of a symbol group; the naming rule will be applied to the symbols in this group</span></span> |
| `style` | <span data-ttu-id="3c916-129">この規則に関連付ける必要がある名前付けスタイルのタイトル</span><span class="sxs-lookup"><span data-stu-id="3c916-129">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="3c916-130">名前付け規則を適用するための重大度を設定します。</span><span class="sxs-lookup"><span data-stu-id="3c916-130">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="3c916-131">関連する値を、使用可能な [重大度レベル](../configuration-options.md#severity-level)のいずれかに設定します。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3c916-131">Set the associated value to one of the available [severity levels](../configuration-options.md#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="3c916-132">**注:**</span><span class="sxs-lookup"><span data-stu-id="3c916-132">**Notes:**</span></span>

1. <span data-ttu-id="3c916-133">名前付け規則内の重要度の指定は、Visual Studio などの開発 Ide 内でのみ尊重されます。</span><span class="sxs-lookup"><span data-stu-id="3c916-133">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="3c916-134">この設定は、C# または VB コンパイラで認識されないため、ビルド時には尊重されません。</span><span class="sxs-lookup"><span data-stu-id="3c916-134">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="3c916-135">ビルドに名前付けスタイルルールを適用するには、代わりに [コード規則の重要度の構成](#rule-id-ide1006-naming-rule-violation)を使用して重大度を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-135">To enforce naming style rules on build, you should instead set the severity by using [code rule severity configuration](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="3c916-136">詳細については、[こちらの GitHub の問題](https://github.com/dotnet/roslyn/issues/44201)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c916-136">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="3c916-137">シンボルグループのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3c916-137">Symbol group properties</span></span>

<span data-ttu-id="3c916-138">シンボルグループの次のプロパティを設定して、グループに含めるシンボルを制限できます。</span><span class="sxs-lookup"><span data-stu-id="3c916-138">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="3c916-139">1つのプロパティに複数の値を指定するには、値をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="3c916-139">To specify multiple values for a single property, separate the values with a comma.</span></span>

| <span data-ttu-id="3c916-140">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3c916-140">Property</span></span> | <span data-ttu-id="3c916-141">説明</span><span class="sxs-lookup"><span data-stu-id="3c916-141">Description</span></span> | <span data-ttu-id="3c916-142">使用できる値</span><span class="sxs-lookup"><span data-stu-id="3c916-142">Allowed values</span></span> | <span data-ttu-id="3c916-143">必須</span><span class="sxs-lookup"><span data-stu-id="3c916-143">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="3c916-144">グループ<sup>1</sup>のシンボルの種類</span><span class="sxs-lookup"><span data-stu-id="3c916-144">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="3c916-145">`*`(この値を使用すると、すべてのシンボルが指定されます)</span><span class="sxs-lookup"><span data-stu-id="3c916-145">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="3c916-146">はい</span><span class="sxs-lookup"><span data-stu-id="3c916-146">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="3c916-147">グループ内のシンボルのアクセシビリティレベル</span><span class="sxs-lookup"><span data-stu-id="3c916-147">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="3c916-148">`*`(この値を使用すると、すべてのアクセシビリティ レベルが指定されます)</span><span class="sxs-lookup"><span data-stu-id="3c916-148">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="3c916-149">`internal` または `friend`</span><span class="sxs-lookup"><span data-stu-id="3c916-149">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="3c916-150">`protected_internal` または `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="3c916-150">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="3c916-151">`local` (メソッド内で定義されたシンボルの場合)</span><span class="sxs-lookup"><span data-stu-id="3c916-151">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="3c916-152">はい</span><span class="sxs-lookup"><span data-stu-id="3c916-152">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="3c916-153">指定した _すべて_ の修飾子を持つシンボルのみ一致 <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3c916-153">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="3c916-154">`abstract` または `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="3c916-154">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="3c916-155">`static` または `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3c916-155">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="3c916-156">いいえ</span><span class="sxs-lookup"><span data-stu-id="3c916-156">No</span></span> |

<span data-ttu-id="3c916-157">**注:**</span><span class="sxs-lookup"><span data-stu-id="3c916-157">**Notes:**</span></span>

1. <span data-ttu-id="3c916-158">組メンバーは現在ではサポートされていません `applicable_kinds` 。</span><span class="sxs-lookup"><span data-stu-id="3c916-158">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="3c916-159">シンボルグループは、プロパティ内の _すべて_ の修飾子と一致し `required_modifiers` ます。</span><span class="sxs-lookup"><span data-stu-id="3c916-159">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="3c916-160">このプロパティを省略した場合、一致には特定の修飾子は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3c916-160">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="3c916-161">このことは、この規則が適用されるかどうかに、シンボルの修飾子が影響を及ぼさないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="3c916-161">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="3c916-162">グループのプロパティにまたはが含まれている場合は、暗黙的に使用される `static` `shared` ため、グループに `required_modifiers` もシンボルが含まれ `const` `static` / `Shared` ます。</span><span class="sxs-lookup"><span data-stu-id="3c916-162">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="3c916-163">ただし、 `static` 名前付け規則をシンボルに適用しない場合は、 `const` のシンボルグループを使用して新しい名前付け規則を作成でき `const` ます。</span><span class="sxs-lookup"><span data-stu-id="3c916-163">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="3c916-164">名前付けスタイルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="3c916-164">Naming style properties</span></span>

<span data-ttu-id="3c916-165">名前付けスタイルは、規則に適用する規則を定義します。</span><span class="sxs-lookup"><span data-stu-id="3c916-165">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="3c916-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3c916-166">For example:</span></span>

* <span data-ttu-id="3c916-167">を大文字にする `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="3c916-167">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="3c916-168">で始まる `m_`</span><span class="sxs-lookup"><span data-stu-id="3c916-168">Starts with `m_`</span></span>
* <span data-ttu-id="3c916-169">で終わる `_g`</span><span class="sxs-lookup"><span data-stu-id="3c916-169">Ends with `_g`</span></span>
* <span data-ttu-id="3c916-170">単語の区切り `__`</span><span class="sxs-lookup"><span data-stu-id="3c916-170">Separate words with `__`</span></span>

<span data-ttu-id="3c916-171">名前付けスタイルには、次のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="3c916-171">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="3c916-172">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3c916-172">Property</span></span> | <span data-ttu-id="3c916-173">説明</span><span class="sxs-lookup"><span data-stu-id="3c916-173">Description</span></span> | <span data-ttu-id="3c916-174">使用できる値</span><span class="sxs-lookup"><span data-stu-id="3c916-174">Allowed values</span></span> | <span data-ttu-id="3c916-175">必須</span><span class="sxs-lookup"><span data-stu-id="3c916-175">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="3c916-176">シンボル内の単語の大文字/小文字のスタイル</span><span class="sxs-lookup"><span data-stu-id="3c916-176">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="3c916-177">可<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3c916-177">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="3c916-178">次の文字で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-178">Must begin with these characters</span></span> | | <span data-ttu-id="3c916-179">いいえ</span><span class="sxs-lookup"><span data-stu-id="3c916-179">No</span></span> |
| `required_suffix` | <span data-ttu-id="3c916-180">次の文字で終わる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-180">Must end with these characters</span></span> | | <span data-ttu-id="3c916-181">いいえ</span><span class="sxs-lookup"><span data-stu-id="3c916-181">No</span></span> |
| `word_separator` | <span data-ttu-id="3c916-182">シンボル内の単語は、この文字で区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-182">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="3c916-183">いいえ</span><span class="sxs-lookup"><span data-stu-id="3c916-183">No</span></span> |

<span data-ttu-id="3c916-184">**注:**</span><span class="sxs-lookup"><span data-stu-id="3c916-184">**Notes:**</span></span>

1. <span data-ttu-id="3c916-185">名前付けスタイルの一部として大文字/小文字スタイルを指定する必要があります。そうしないと、名前付けスタイルは無視される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-185">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="rule-order"></a><span data-ttu-id="3c916-186">ルールの順序</span><span class="sxs-lookup"><span data-stu-id="3c916-186">Rule order</span></span>

<span data-ttu-id="3c916-187">EditorConfig ファイルで名前付け規則を定義する順序は問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="3c916-187">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="3c916-188">名前付け規則は、規則自体の定義に従って自動的に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="3c916-188">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="3c916-189">[EditorConfig 言語サービス拡張機能](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)では、EditorConfig ファイルを分析して、ファイルでの規則の順序が実行時にコンパイラで使用される順序と異なる場合に報告できます。</span><span class="sxs-lookup"><span data-stu-id="3c916-189">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="3c916-190">Visual studio 2019 バージョン16.2 より前のバージョンの Visual Studio を使用している場合、EditorConfig ファイルでは、名前付け規則を最も限定的なものから最も限定的なものに順番に並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-190">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="3c916-191">適用可能な最初に検出されたルールのみが適用されます。</span><span class="sxs-lookup"><span data-stu-id="3c916-191">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="3c916-192">ただし、同じ名前のルールの "*プロパティ*" が複数ある場合は、その名前の最も最近見つかったプロパティが優先されます。</span><span class="sxs-lookup"><span data-stu-id="3c916-192">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="3c916-193">詳細については、「[File hierarchy and precedence (ファイルの階層と優先順位)](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c916-193">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="3c916-194">既定の名前付けスタイル</span><span class="sxs-lookup"><span data-stu-id="3c916-194">Default naming styles</span></span>

<span data-ttu-id="3c916-195">カスタム名前付け規則を指定しない場合は、次の既定のスタイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c916-195">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="3c916-196">アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるクラス、構造体、列挙型、プロパティ、およびイベントでは、既定の名前付けスタイルはパスカル ケースです。</span><span class="sxs-lookup"><span data-stu-id="3c916-196">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="3c916-197">アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるインターフェイスでは、既定の名前付けスタイルはパスカル ケースであり、プレフィックス **I** を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-197">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="3c916-198">コード規則 ID: `IDE1006 (Naming rule violation)`</span><span class="sxs-lookup"><span data-stu-id="3c916-198">Code Rule ID: `IDE1006 (Naming rule violation)`</span></span>

<span data-ttu-id="3c916-199">すべての名前付けオプションには、ルール ID `IDE1006` とタイトルがあり `Naming rule violation` ます。</span><span class="sxs-lookup"><span data-stu-id="3c916-199">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="3c916-200">EditorConfig ファイルでは、次の構文を使用して、名前付け違反の重大度をグローバルに構成できます。</span><span class="sxs-lookup"><span data-stu-id="3c916-200">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="3c916-201">重大度値は、 `warning` `error` [ビルドで適用](../overview.md#code-style-analysis)される必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c916-201">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="3c916-202">可能なすべての重要度の値については、「 [重大度レベル](../configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c916-202">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="example"></a><span data-ttu-id="3c916-203">例</span><span class="sxs-lookup"><span data-stu-id="3c916-203">Example</span></span>

<span data-ttu-id="3c916-204">次の *.editorconfig* ファイルには、パブリック プロパティ、メソッド、フィールド、イベント、デリゲートを大文字で入力する必要があることを指定した名前付け規則が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c916-204">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="3c916-205">この名前付け規則では、コンマを使用して個々のシンボル値を区切ることにより、規則を適用する複数の種類のシンボルを指定しています。</span><span class="sxs-lookup"><span data-stu-id="3c916-205">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3c916-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c916-206">See also</span></span>

- [<span data-ttu-id="3c916-207">言語規則</span><span class="sxs-lookup"><span data-stu-id="3c916-207">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="3c916-208">書式設定規則</span><span class="sxs-lookup"><span data-stu-id="3c916-208">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="3c916-209">Roslyn の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="3c916-209">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [<span data-ttu-id="3c916-210">.NET コードスタイル規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="3c916-210">.NET code style rules reference</span></span>](index.md)
