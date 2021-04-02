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
# <a name="naming-rules"></a><span data-ttu-id="7d02d-103">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="7d02d-103">Naming rules</span></span>

<span data-ttu-id="7d02d-104">`.editorconfig` ファイルで、NET プログラミング言語のコード要素&mdash;クラス、プロパティ、メソッドなど&mdash;の名前の付け方を指定および適用する **名前付けルール** を定義できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-104">In your `.editorconfig` file, you can define **naming rules** that specify and enforce how .NET programming language code elements&mdash;such as classes, properties, and methods&mdash;should be named.</span></span> <span data-ttu-id="7d02d-105">たとえば、パブリック メンバーは大文字表記とする必要があること、またはプライベート フィールドは `_` で始まる必要があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-105">For example, you can specify that public members must be capitalized, or that private fields must begin with `_`.</span></span>

<span data-ttu-id="7d02d-106">名前付けルールには、次の 3 つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-106">A naming rule has three components:</span></span>

* <span data-ttu-id="7d02d-107">ルールの適用先となる **シンボル グループ** (例: パブリック メンバー、プライベート フィールド)。</span><span class="sxs-lookup"><span data-stu-id="7d02d-107">The **symbol group** that the rule applies to, for example, public members or private fields.</span></span>
* <span data-ttu-id="7d02d-108">ルールと関連付けられる **名前付けスタイル** (例: 名前は大文字にしなければならない、アンダースコアで始まる必要がある)。</span><span class="sxs-lookup"><span data-stu-id="7d02d-108">The **naming style** to associate with the rule, for example, that the name must be capitalized or start with an underscore.</span></span>
* <span data-ttu-id="7d02d-109">規則を適用するための重大度。</span><span class="sxs-lookup"><span data-stu-id="7d02d-109">The severity for enforcing the convention.</span></span>

<span data-ttu-id="7d02d-110">まず、シンボル グループと名前付けスタイルを指定し、それぞれにタイトルを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-110">First, you must specify the symbol group and naming style and give each of them a title.</span></span> <span data-ttu-id="7d02d-111">次に、すべてをリンクする名前付けルールを指定します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-111">Then you specify the naming rule, which links everything together.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="7d02d-112">一般的な構文</span><span class="sxs-lookup"><span data-stu-id="7d02d-112">General syntax</span></span>

<span data-ttu-id="7d02d-113">名前付けルール、シンボル グループ、または名前付けスタイルを定義するには、次の構文を使用して 1 つ以上のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-113">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="7d02d-114">各プロパティは一度だけ設定する必要がありますが、一部の設定では複数のコンマ区切り値も使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-114">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="7d02d-115">プロパティの順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="7d02d-115">The order of the properties is not important.</span></span>

### \<kind>

<span data-ttu-id="7d02d-116">**\<kind>** は、定義される要素の種類 &mdash;名前付けルール、シンボル グループ、または名前付けスタイル&mdash; を指定します。次のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-116">**\<kind>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="7d02d-117">設定対象のプロパティ</span><span class="sxs-lookup"><span data-stu-id="7d02d-117">To set a property for</span></span> | <span data-ttu-id="7d02d-118">使用する \<kind> 値</span><span class="sxs-lookup"><span data-stu-id="7d02d-118">Use the \<kind> value</span></span> | <span data-ttu-id="7d02d-119">例</span><span class="sxs-lookup"><span data-stu-id="7d02d-119">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="7d02d-120">名前付けルール</span><span class="sxs-lookup"><span data-stu-id="7d02d-120">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="7d02d-121">シンボル グループ</span><span class="sxs-lookup"><span data-stu-id="7d02d-121">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="7d02d-122">名前付けスタイル</span><span class="sxs-lookup"><span data-stu-id="7d02d-122">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="7d02d-123">定義のそれぞれの種類 &mdash;[名前付けルール](#naming-rule-properties)、[シンボル グループ](#symbol-group-properties)、または[名前付けスタイル](#naming-style-properties)&mdash; には、サポートされる独自のプロパティがあります。これについては、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-123">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="7d02d-124">**\<title>** は、複数のプロパティ設定を 1 つの定義に関連付ける、自由に選択できるわかりやすい名前です。</span><span class="sxs-lookup"><span data-stu-id="7d02d-124">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="7d02d-125">たとえば、次のプロパティでは、`interface` と `types` という 2 つのシンボル グループ定義が生成され、そのそれぞれに 2 つのプロパティが設定されています。</span><span class="sxs-lookup"><span data-stu-id="7d02d-125">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="7d02d-126">名前付けルールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="7d02d-126">Naming rule properties</span></span>

<span data-ttu-id="7d02d-127">ルールを有効にするには、すべての名前付けルール プロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="7d02d-127">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="7d02d-128">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7d02d-128">Property</span></span> | <span data-ttu-id="7d02d-129">説明</span><span class="sxs-lookup"><span data-stu-id="7d02d-129">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="7d02d-130">シンボル グループのタイトル。この名前付けルールは、このグループ内のシンボルに適用されます</span><span class="sxs-lookup"><span data-stu-id="7d02d-130">The title of a symbol group; the naming rule will be applied to the symbols in this group</span></span> |
| `style` | <span data-ttu-id="7d02d-131">このルールに関連付ける必要がある名前付けスタイルのタイトル</span><span class="sxs-lookup"><span data-stu-id="7d02d-131">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="7d02d-132">名前付けルールを適用する際の重大度を設定します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-132">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="7d02d-133">関連する値を、使用可能な[重大度レベル](../configuration-options.md#severity-level)のいずれかに設定します。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7d02d-133">Set the associated value to one of the available [severity levels](../configuration-options.md#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="7d02d-134">**注:**</span><span class="sxs-lookup"><span data-stu-id="7d02d-134">**Notes:**</span></span>

1. <span data-ttu-id="7d02d-135">名前付けルール内での重大度指定は、Visual Studio などの開発 IDE 内でのみ遵守されます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-135">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="7d02d-136">この設定は、C# や VB のコンパイラでは認識されないため、ビルド時には遵守されません。</span><span class="sxs-lookup"><span data-stu-id="7d02d-136">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="7d02d-137">ビルドで名前付けスタイル ルールを適用するには、代わりに[コード ルールの重大度構成](#rule-id-ide1006-naming-rule-violation)を使用して重大度を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-137">To enforce naming style rules on build, you should instead set the severity by using [code rule severity configuration](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="7d02d-138">詳細については、[こちらの GitHub の問題](https://github.com/dotnet/roslyn/issues/44201)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d02d-138">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="7d02d-139">シンボル グループのプロパティ</span><span class="sxs-lookup"><span data-stu-id="7d02d-139">Symbol group properties</span></span>

<span data-ttu-id="7d02d-140">シンボル グループに対しては、次のプロパティを設定して、グループに含めるシンボルを制限できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-140">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="7d02d-141">1 つのプロパティに複数の値を指定するには、値をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-141">To specify multiple values for a single property, separate the values with a comma.</span></span>

| <span data-ttu-id="7d02d-142">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7d02d-142">Property</span></span> | <span data-ttu-id="7d02d-143">説明</span><span class="sxs-lookup"><span data-stu-id="7d02d-143">Description</span></span> | <span data-ttu-id="7d02d-144">使用できる値</span><span class="sxs-lookup"><span data-stu-id="7d02d-144">Allowed values</span></span> | <span data-ttu-id="7d02d-145">必須</span><span class="sxs-lookup"><span data-stu-id="7d02d-145">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="7d02d-146">グループ内のシンボルの種類 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7d02d-146">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="7d02d-147">`*`(この値を使用すると、すべてのシンボルが指定されます)</span><span class="sxs-lookup"><span data-stu-id="7d02d-147">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="7d02d-148">はい</span><span class="sxs-lookup"><span data-stu-id="7d02d-148">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="7d02d-149">グループ内のシンボルのアクセシビリティ レベル</span><span class="sxs-lookup"><span data-stu-id="7d02d-149">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="7d02d-150">`*`(この値を使用すると、すべてのアクセシビリティ レベルが指定されます)</span><span class="sxs-lookup"><span data-stu-id="7d02d-150">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="7d02d-151">`internal` または `friend`</span><span class="sxs-lookup"><span data-stu-id="7d02d-151">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="7d02d-152">`protected_internal` または `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="7d02d-152">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="7d02d-153">`local` (メソッド内で定義されたシンボルの場合)</span><span class="sxs-lookup"><span data-stu-id="7d02d-153">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="7d02d-154">はい</span><span class="sxs-lookup"><span data-stu-id="7d02d-154">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="7d02d-155">指定した修飾子を "_すべて_" 持つシンボルとのみ一致 <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7d02d-155">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="7d02d-156">`abstract` または `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="7d02d-156">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="7d02d-157">`static` または `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="7d02d-157">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="7d02d-158">いいえ</span><span class="sxs-lookup"><span data-stu-id="7d02d-158">No</span></span> |

<span data-ttu-id="7d02d-159">**注:**</span><span class="sxs-lookup"><span data-stu-id="7d02d-159">**Notes:**</span></span>

1. <span data-ttu-id="7d02d-160">タプル メンバーは、今のところ `applicable_kinds` ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7d02d-160">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="7d02d-161">このシンボル グループは、`required_modifiers` プロパティに含まれる "_すべて_" の修飾子と一致します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-161">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="7d02d-162">このプロパティを省略すると、一致するために特定の修飾子が必要とされなくなります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-162">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="7d02d-163">このことは、この規則が適用されるかどうかに、シンボルの修飾子が影響を及ぼさないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-163">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="7d02d-164">`required_modifiers` プロパティに `static` または `shared` があるグループの場合、そのグループには `const` シンボルも含まれます。これは、それらのシンボルが暗黙的に `static`/`Shared` であるためです。</span><span class="sxs-lookup"><span data-stu-id="7d02d-164">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="7d02d-165">ただし、`static` 名前付けルールが `const` シンボルに適用されないようにしたい場合は、`const` のシンボル グループを使用して新しい名前付けルールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-165">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="7d02d-166">名前付けスタイルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="7d02d-166">Naming style properties</span></span>

<span data-ttu-id="7d02d-167">名前付けスタイルは、そのルールで適用する規則を定義します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-167">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="7d02d-168">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7d02d-168">For example:</span></span>

* <span data-ttu-id="7d02d-169">`PascalCase` で大文字にする</span><span class="sxs-lookup"><span data-stu-id="7d02d-169">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="7d02d-170">`m_` で始まる</span><span class="sxs-lookup"><span data-stu-id="7d02d-170">Starts with `m_`</span></span>
* <span data-ttu-id="7d02d-171">`_g` で終わる</span><span class="sxs-lookup"><span data-stu-id="7d02d-171">Ends with `_g`</span></span>
* <span data-ttu-id="7d02d-172">`__` で単語を区切る</span><span class="sxs-lookup"><span data-stu-id="7d02d-172">Separate words with `__`</span></span>

<span data-ttu-id="7d02d-173">名前付けスタイルには、次のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-173">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="7d02d-174">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7d02d-174">Property</span></span> | <span data-ttu-id="7d02d-175">説明</span><span class="sxs-lookup"><span data-stu-id="7d02d-175">Description</span></span> | <span data-ttu-id="7d02d-176">使用できる値</span><span class="sxs-lookup"><span data-stu-id="7d02d-176">Allowed values</span></span> | <span data-ttu-id="7d02d-177">必須</span><span class="sxs-lookup"><span data-stu-id="7d02d-177">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="7d02d-178">シンボル内の単語の大文字/小文字スタイル</span><span class="sxs-lookup"><span data-stu-id="7d02d-178">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="7d02d-179">可<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7d02d-179">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="7d02d-180">この文字で始まる必要がある</span><span class="sxs-lookup"><span data-stu-id="7d02d-180">Must begin with these characters</span></span> | | <span data-ttu-id="7d02d-181">いいえ</span><span class="sxs-lookup"><span data-stu-id="7d02d-181">No</span></span> |
| `required_suffix` | <span data-ttu-id="7d02d-182">この文字で終わる必要がある</span><span class="sxs-lookup"><span data-stu-id="7d02d-182">Must end with these characters</span></span> | | <span data-ttu-id="7d02d-183">いいえ</span><span class="sxs-lookup"><span data-stu-id="7d02d-183">No</span></span> |
| `word_separator` | <span data-ttu-id="7d02d-184">このシンボル内の単語は、この文字で区切る必要がある</span><span class="sxs-lookup"><span data-stu-id="7d02d-184">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="7d02d-185">いいえ</span><span class="sxs-lookup"><span data-stu-id="7d02d-185">No</span></span> |

<span data-ttu-id="7d02d-186">**注:**</span><span class="sxs-lookup"><span data-stu-id="7d02d-186">**Notes:**</span></span>

1. <span data-ttu-id="7d02d-187">名前付けスタイルの一部として大文字/小文字スタイルを指定する必要があります。そうしないと、名前付けスタイルは無視される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-187">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="rule-order"></a><span data-ttu-id="7d02d-188">ルールの順序</span><span class="sxs-lookup"><span data-stu-id="7d02d-188">Rule order</span></span>

<span data-ttu-id="7d02d-189">EditorConfig ファイルで名前付けルールを定義する順序に意味はありません。</span><span class="sxs-lookup"><span data-stu-id="7d02d-189">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="7d02d-190">名前付けルールは、ルール自体の定義に従って自動的に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-190">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="7d02d-191">[EditorConfig 言語サービス拡張機能](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)では、EditorConfig ファイルを分析して、ファイルでの規則の順序が実行時にコンパイラで使用される順序と異なる場合に報告できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-191">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="7d02d-192">Visual Studio 2019 バージョン 16.2 より前のバージョンの Visual Studio を使用している場合は、EditorConfig ファイル内で、最も限定的なものから最も限定的でないものの順に名前付けルールを並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-192">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="7d02d-193">適用可能な最初に検出されたルールのみが適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-193">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="7d02d-194">ただし、同じ名前のルールの "*プロパティ*" が複数ある場合は、その名前の最も最近見つかったプロパティが優先されます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-194">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="7d02d-195">詳細については、「[File hierarchy and precedence (ファイルの階層と優先順位)](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d02d-195">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="7d02d-196">既定の名前付けスタイル</span><span class="sxs-lookup"><span data-stu-id="7d02d-196">Default naming styles</span></span>

<span data-ttu-id="7d02d-197">カスタムの名前付けルールをまったく指定しない場合は、次の既定のスタイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-197">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="7d02d-198">アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるクラス、構造体、列挙型、プロパティ、およびイベントでは、既定の名前付けスタイルはパスカル ケースです。</span><span class="sxs-lookup"><span data-stu-id="7d02d-198">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="7d02d-199">アクセシビリティが `public`、`private`、`internal`、`protected`、または `protected_internal` であるインターフェイスでは、既定の名前付けスタイルはパスカル ケースであり、プレフィックス **I** を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-199">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="7d02d-200">コード ルール ID: `IDE1006 (Naming rule violation)`</span><span class="sxs-lookup"><span data-stu-id="7d02d-200">Code Rule ID: `IDE1006 (Naming rule violation)`</span></span>

<span data-ttu-id="7d02d-201">すべての名前付けオプションにルール ID `IDE1006` とタイトル `Naming rule violation` が指定されます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-201">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="7d02d-202">EditorConfig ファイルで次の構文を使用して、名前付け違反の重大度をグローバルに構成できます。</span><span class="sxs-lookup"><span data-stu-id="7d02d-202">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="7d02d-203">[ビルド時に適用](../overview.md#code-style-analysis)するには、重大度の値を `warning` または `error` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d02d-203">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="7d02d-204">使用できるすべての重大度の値については、「[重大度レベル](../configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d02d-204">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="example"></a><span data-ttu-id="7d02d-205">例</span><span class="sxs-lookup"><span data-stu-id="7d02d-205">Example</span></span>

<span data-ttu-id="7d02d-206">次の *.editorconfig* ファイルには、パブリック プロパティ、メソッド、フィールド、イベント、デリゲートを大文字で入力する必要があることを指定した名前付け規則が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d02d-206">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="7d02d-207">この名前付け規則では、コンマを使用して個々のシンボル値を区切ることにより、規則を適用する複数の種類のシンボルを指定しています。</span><span class="sxs-lookup"><span data-stu-id="7d02d-207">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7d02d-208">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d02d-208">See also</span></span>

- [<span data-ttu-id="7d02d-209">言語規則</span><span class="sxs-lookup"><span data-stu-id="7d02d-209">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="7d02d-210">書式設定規則</span><span class="sxs-lookup"><span data-stu-id="7d02d-210">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="7d02d-211">Roslyn 名前付けルール</span><span class="sxs-lookup"><span data-stu-id="7d02d-211">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/main/.editorconfig#L63)
- [<span data-ttu-id="7d02d-212">.NET コード スタイルの規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="7d02d-212">.NET code style rules reference</span></span>](index.md)
