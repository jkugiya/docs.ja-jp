---
title: コード スタイルの書式設定規則
description: インデント、スペース、および改行を書式設定するためのコード スタイル規則について説明します。
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE0055
- formatting rules
helpviewer_keywords:
- IDE0055
- formatting code style rules [EditorConfig]
- formatting rules
- EditorConfig formatting conventions
ms.openlocfilehash: 866949692341f65a5b78c7dd5b8eec918873d3b7
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511802"
---
# <a name="formatting-rules"></a><span data-ttu-id="e2249-103">書式設定規則</span><span class="sxs-lookup"><span data-stu-id="e2249-103">Formatting rules</span></span>

<span data-ttu-id="e2249-104">書式設定規則は、.NET プログラミング言語の構造に合わせてインデント、スペース、および改行を揃える方法に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="e2249-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="e2249-105">この規則は次のカテゴリに分けられます。</span><span class="sxs-lookup"><span data-stu-id="e2249-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="e2249-106">[.NET 書式設定規則](#net-formatting-rules): C# と Visual Basic の両方に適用される規則。</span><span class="sxs-lookup"><span data-stu-id="e2249-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="e2249-107">これらの規則の EditorConfig オプション名は `dotnet_` プレフィックスで始まります。</span><span class="sxs-lookup"><span data-stu-id="e2249-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="e2249-108">[C# 書式設定規則](#c-formatting-rules): C# 言語のみに固有の規則。</span><span class="sxs-lookup"><span data-stu-id="e2249-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="e2249-109">これらの規則の EditorConfig オプション名は `csharp_` プレフィックスで始まります。</span><span class="sxs-lookup"><span data-stu-id="e2249-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="e2249-110">規則 ID: "IDE0055" (書式設定の修正)</span><span class="sxs-lookup"><span data-stu-id="e2249-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="e2249-111">書式設定オプションはすべて、規則 ID が `IDE0055`、タイトルが `Fix formatting` になります。</span><span class="sxs-lookup"><span data-stu-id="e2249-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="e2249-112">EditorConfig ファイルで次の構成行を使用して、書式設定違反の重大度を設定します。</span><span class="sxs-lookup"><span data-stu-id="e2249-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="e2249-113">[ビルド時に適用](../overview.md#code-style-analysis)するには、重大度の値を `warning` または `error` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2249-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="e2249-114">使用できるすべての重大度の値については、「[重大度レベル](../configuration-options.md#severity-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2249-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="e2249-115">オプションの書式</span><span class="sxs-lookup"><span data-stu-id="e2249-115">Option format</span></span>

<span data-ttu-id="e2249-116">書式設定規則のオプションは、EditorConfig ファイルで、次の形式で指定できます。</span><span class="sxs-lookup"><span data-stu-id="e2249-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="e2249-117">多くのルールでは、`value` に対して `true` (このスタイルを優先する) または `false` (このスタイルを優先しない) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2249-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="e2249-118">他のルールでは、`flush_left` や `before_and_after` のような値を指定して、ルールを適用する状況と場所を記述します。</span><span class="sxs-lookup"><span data-stu-id="e2249-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="e2249-119">重要度は指定しません。</span><span class="sxs-lookup"><span data-stu-id="e2249-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="e2249-120">.NET 書式設定規則</span><span class="sxs-lookup"><span data-stu-id="e2249-120">.NET formatting rules</span></span>

<span data-ttu-id="e2249-121">このセクションの書式設定規則は、C# と Visual Basic の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e2249-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="e2249-122">using の整理</span><span class="sxs-lookup"><span data-stu-id="e2249-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="e2249-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="e2249-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="e2249-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="e2249-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="e2249-125">using ディレクティブの整理</span><span class="sxs-lookup"><span data-stu-id="e2249-125">Organize using directives</span></span>

<span data-ttu-id="e2249-126">これらの書式ルールは、`using` ディレクティブと `Imports` ステートメントの並べ替えと表示に関係します。</span><span class="sxs-lookup"><span data-stu-id="e2249-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="e2249-127">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="e2249-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="e2249-128">dotnet\_sort\_system\_directives_first</span><span class="sxs-lookup"><span data-stu-id="e2249-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="e2249-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-129">Property</span></span>|<span data-ttu-id="e2249-130">値</span><span class="sxs-lookup"><span data-stu-id="e2249-130">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-131">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-131">**Option name**</span></span> | <span data-ttu-id="e2249-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="e2249-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="e2249-133">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-133">**Applicable languages**</span></span> | <span data-ttu-id="e2249-134">C# および Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2249-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="e2249-135">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-135">**Introduced version**</span></span> | <span data-ttu-id="e2249-136">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-137">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-137">**Option values**</span></span> | <span data-ttu-id="e2249-138">`true` - `System.*` `using` ディレクティブをアルファベット順に並べ替え、他の using ディレクティブの前に配置します。</span><span class="sxs-lookup"><span data-stu-id="e2249-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="e2249-139">`false` - `System.*` `using` ディレクティブを他の `using` ディレクティブの前に配置しません。</span><span class="sxs-lookup"><span data-stu-id="e2249-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="e2249-140">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-140">Code examples:</span></span>

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="e2249-141">dotnet\_separate\_import\_directive\_groups</span><span class="sxs-lookup"><span data-stu-id="e2249-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="e2249-142">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-142">Property</span></span>|<span data-ttu-id="e2249-143">値</span><span class="sxs-lookup"><span data-stu-id="e2249-143">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-144">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-144">**Option name**</span></span> | <span data-ttu-id="e2249-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="e2249-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="e2249-146">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-146">**Applicable languages**</span></span> | <span data-ttu-id="e2249-147">C# および Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2249-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="e2249-148">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-148">**Introduced version**</span></span> | <span data-ttu-id="e2249-149">Visual Studio 2017 バージョン 15.5</span><span class="sxs-lookup"><span data-stu-id="e2249-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="e2249-150">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-150">**Option values**</span></span> | <span data-ttu-id="e2249-151">`true` - `using` ディレクティブ グループの間に空白行を配置します。</span><span class="sxs-lookup"><span data-stu-id="e2249-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="e2249-152">`false` - `using` ディレクティブ グループの間に空白行を配置しません。</span><span class="sxs-lookup"><span data-stu-id="e2249-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="e2249-153">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-153">Code examples:</span></span>

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-rules"></a><span data-ttu-id="e2249-154">C# 書式設定規則</span><span class="sxs-lookup"><span data-stu-id="e2249-154">C# formatting rules</span></span>

<span data-ttu-id="e2249-155">このセクションの書式ルールは、C# コードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e2249-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="e2249-156">改行オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="e2249-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="e2249-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="e2249-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="e2249-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="e2249-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="e2249-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="e2249-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="e2249-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="e2249-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="e2249-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="e2249-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="e2249-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="e2249-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="e2249-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="e2249-164">インデント オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="e2249-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="e2249-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="e2249-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="e2249-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="e2249-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="e2249-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="e2249-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="e2249-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="e2249-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="e2249-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="e2249-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="e2249-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="e2249-171">スペース オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="e2249-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="e2249-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="e2249-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="e2249-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="e2249-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="e2249-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="e2249-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="e2249-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="e2249-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="e2249-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="e2249-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="e2249-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="e2249-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="e2249-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="e2249-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="e2249-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="e2249-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="e2249-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="e2249-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="e2249-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="e2249-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="e2249-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="e2249-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="e2249-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="e2249-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="e2249-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="e2249-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="e2249-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="e2249-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="e2249-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="e2249-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="e2249-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="e2249-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="e2249-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="e2249-194">折り返しオプション</span><span class="sxs-lookup"><span data-stu-id="e2249-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="e2249-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="e2249-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="e2249-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="e2249-197">using ディレクティブ オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="e2249-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="e2249-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="e2249-199">改行オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-199">New-line options</span></span>

<span data-ttu-id="e2249-200">これらの書式ルールは、コードの書式を設定する場合の改行の使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="e2249-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="e2249-201">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="e2249-201">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="e2249-202">csharp\_new\_line\_before\_open_brace</span><span class="sxs-lookup"><span data-stu-id="e2249-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="e2249-203">このルールは、左中かっこ (`{`) を前のコードと同じ行に配置するか、新しい行に配置するかに関するものです。</span><span class="sxs-lookup"><span data-stu-id="e2249-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="e2249-204">このルールでは、**all**、**none**、または **methods** や **properties** などの 1 つ以上のコード要素を指定して、このルールを適用する必要があるタイミングを定義します。</span><span class="sxs-lookup"><span data-stu-id="e2249-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="e2249-205">複数のコード要素を指定するには、コンマ (,) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="e2249-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="e2249-206">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-206">Property</span></span>|<span data-ttu-id="e2249-207">値</span><span class="sxs-lookup"><span data-stu-id="e2249-207">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-208">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-208">**Option name**</span></span> | <span data-ttu-id="e2249-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="e2249-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="e2249-210">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-210">**Applicable languages**</span></span> | <span data-ttu-id="e2249-211">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-211">C#</span></span> |
| <span data-ttu-id="e2249-212">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-212">**Introduced version**</span></span> | <span data-ttu-id="e2249-213">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-214">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-214">**Option values**</span></span> | <span data-ttu-id="e2249-215">`all` - 中かっこはすべての式の新しい行に配置する必要があります ("Allman" スタイル)。</span><span class="sxs-lookup"><span data-stu-id="e2249-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="e2249-216">`none` - 中かっこはすべての式の同じ行に配置する必要があります ("K&R")。</span><span class="sxs-lookup"><span data-stu-id="e2249-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="e2249-217">`accessors`、`anonymous_methods`、`anonymous_types`、`control_blocks`、`events`、`indexers`、`lambdas`、`local_functions`、`methods`、`object_collection_array_initializers`、`properties`、`types` - 中かっこは指定されたコード要素の新しい行に配置する必要があります ("Allman" スタイル)。</span><span class="sxs-lookup"><span data-stu-id="e2249-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="e2249-218">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-218">Code examples:</span></span>

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="e2249-219">csharp\_new\_line\_before_else</span><span class="sxs-lookup"><span data-stu-id="e2249-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="e2249-220">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-220">Property</span></span>|<span data-ttu-id="e2249-221">値</span><span class="sxs-lookup"><span data-stu-id="e2249-221">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-222">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-222">**Option name**</span></span> | <span data-ttu-id="e2249-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="e2249-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="e2249-224">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-224">**Applicable languages**</span></span> | <span data-ttu-id="e2249-225">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-225">C#</span></span> |
| <span data-ttu-id="e2249-226">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-226">**Introduced version**</span></span> | <span data-ttu-id="e2249-227">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-228">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-228">**Option values**</span></span> | <span data-ttu-id="e2249-229">`true` - 新しい行に `else` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="e2249-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="e2249-230">`false` - 同じ行に `else` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="e2249-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="e2249-231">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-231">Code examples:</span></span>

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="e2249-232">csharp\_new\_line\_before_catch</span><span class="sxs-lookup"><span data-stu-id="e2249-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="e2249-233">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-233">Property</span></span>|<span data-ttu-id="e2249-234">値</span><span class="sxs-lookup"><span data-stu-id="e2249-234">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-235">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-235">**Option name**</span></span> | <span data-ttu-id="e2249-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="e2249-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="e2249-237">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-237">**Applicable languages**</span></span> | <span data-ttu-id="e2249-238">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-238">C#</span></span> |
| <span data-ttu-id="e2249-239">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-239">**Introduced version**</span></span> | <span data-ttu-id="e2249-240">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-241">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-241">**Option values**</span></span> | <span data-ttu-id="e2249-242">`true` - 新しい行に `catch` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="e2249-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="e2249-243">`false` - 同じ行に `catch` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="e2249-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="e2249-244">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-244">Code examples:</span></span>

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="e2249-245">csharp\_new\_line\_before_finally</span><span class="sxs-lookup"><span data-stu-id="e2249-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="e2249-246">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-246">Property</span></span>|<span data-ttu-id="e2249-247">値</span><span class="sxs-lookup"><span data-stu-id="e2249-247">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-248">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-248">**Option name**</span></span> | <span data-ttu-id="e2249-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="e2249-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="e2249-250">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-250">**Applicable languages**</span></span> | <span data-ttu-id="e2249-251">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-251">C#</span></span> |
| <span data-ttu-id="e2249-252">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-252">**Introduced version**</span></span> | <span data-ttu-id="e2249-253">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-254">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-254">**Option values**</span></span> | <span data-ttu-id="e2249-255">`true` - `finally` ステートメントを右中かっこの後の新しい行に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2249-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="e2249-256">`false` - `finally` ステートメントを右中かっこと同じ行に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2249-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="e2249-257">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-257">Code examples:</span></span>

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="e2249-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span><span class="sxs-lookup"><span data-stu-id="e2249-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="e2249-259">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-259">Property</span></span>|<span data-ttu-id="e2249-260">値</span><span class="sxs-lookup"><span data-stu-id="e2249-260">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-261">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-261">**Option name**</span></span> | <span data-ttu-id="e2249-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="e2249-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="e2249-263">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-263">**Applicable languages**</span></span> | <span data-ttu-id="e2249-264">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-264">C#</span></span> |
| <span data-ttu-id="e2249-265">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-265">**Introduced version**</span></span> | <span data-ttu-id="e2249-266">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-267">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-267">**Option values**</span></span> | <span data-ttu-id="e2249-268">`true` - オブジェクト初期化子のメンバーを別の行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="e2249-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="e2249-269">`false` - オブジェクト初期化子のメンバーを同じ行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="e2249-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="e2249-270">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-270">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="e2249-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="e2249-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="e2249-272">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-272">Property</span></span>|<span data-ttu-id="e2249-273">値</span><span class="sxs-lookup"><span data-stu-id="e2249-273">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-274">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-274">**Option name**</span></span> | <span data-ttu-id="e2249-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="e2249-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="e2249-276">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-276">**Applicable languages**</span></span> | <span data-ttu-id="e2249-277">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-277">C#</span></span> |
| <span data-ttu-id="e2249-278">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-278">**Introduced version**</span></span> | <span data-ttu-id="e2249-279">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-280">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-280">**Option values**</span></span> | <span data-ttu-id="e2249-281">`true` - 匿名型のメンバーを別の行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="e2249-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="e2249-282">`false` - 匿名型のメンバーを同じ行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="e2249-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="e2249-283">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-283">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="e2249-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="e2249-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="e2249-285">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-285">Property</span></span>|<span data-ttu-id="e2249-286">値</span><span class="sxs-lookup"><span data-stu-id="e2249-286">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-287">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-287">**Option name**</span></span> | <span data-ttu-id="e2249-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="e2249-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="e2249-289">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-289">**Applicable languages**</span></span> | <span data-ttu-id="e2249-290">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-290">C#</span></span> |
| <span data-ttu-id="e2249-291">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-291">**Introduced version**</span></span> | <span data-ttu-id="e2249-292">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-293">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-293">**Option values**</span></span> | <span data-ttu-id="e2249-294">`true` - クエリ式の句の要素を別の行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="e2249-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="e2249-295">`false` - クエリ式の句の要素を同じ行に配置する必要があります</span><span class="sxs-lookup"><span data-stu-id="e2249-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="e2249-296">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="e2249-297">インデント オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-297">Indentation options</span></span>

<span data-ttu-id="e2249-298">これらの書式ルールは、コードの書式を設定する場合のインデントの使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="e2249-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="e2249-299">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="e2249-299">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="e2249-300">csharp\_indent\_case_contents</span><span class="sxs-lookup"><span data-stu-id="e2249-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="e2249-301">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-301">Property</span></span>|<span data-ttu-id="e2249-302">値</span><span class="sxs-lookup"><span data-stu-id="e2249-302">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-303">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-303">**Option name**</span></span> | <span data-ttu-id="e2249-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="e2249-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="e2249-305">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-305">**Applicable languages**</span></span> | <span data-ttu-id="e2249-306">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-306">C#</span></span> |
| <span data-ttu-id="e2249-307">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-307">**Introduced version**</span></span> | <span data-ttu-id="e2249-308">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-309">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-309">**Option values**</span></span> | <span data-ttu-id="e2249-310">`true` - `switch` ケース コンテンツにインデントを付けます</span><span class="sxs-lookup"><span data-stu-id="e2249-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="e2249-311">`false` - `switch` ケース コンテンツにインデントを付けません</span><span class="sxs-lookup"><span data-stu-id="e2249-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="e2249-312">このルールが **true** に設定されている場合は、i。</span><span class="sxs-lookup"><span data-stu-id="e2249-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="e2249-313">このルールが **false** に設定されている場合は、d。</span><span class="sxs-lookup"><span data-stu-id="e2249-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="e2249-314">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-314">Code examples:</span></span>

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="e2249-315">csharp\_indent\_switch_labels</span><span class="sxs-lookup"><span data-stu-id="e2249-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="e2249-316">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-316">Property</span></span>|<span data-ttu-id="e2249-317">値</span><span class="sxs-lookup"><span data-stu-id="e2249-317">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-318">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-318">**Option name**</span></span> | <span data-ttu-id="e2249-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="e2249-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="e2249-320">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-320">**Applicable languages**</span></span> | <span data-ttu-id="e2249-321">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-321">C#</span></span> |
| <span data-ttu-id="e2249-322">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-322">**Introduced version**</span></span> | <span data-ttu-id="e2249-323">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-324">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-324">**Option values**</span></span> | <span data-ttu-id="e2249-325">`true` - `switch` ラベルをインデントします</span><span class="sxs-lookup"><span data-stu-id="e2249-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="e2249-326">`false` - `switch` ラベルをインデントしません</span><span class="sxs-lookup"><span data-stu-id="e2249-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="e2249-327">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-327">Code examples:</span></span>

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a><span data-ttu-id="e2249-328">csharp\_indent_labels</span><span class="sxs-lookup"><span data-stu-id="e2249-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="e2249-329">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-329">Property</span></span>|<span data-ttu-id="e2249-330">値</span><span class="sxs-lookup"><span data-stu-id="e2249-330">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-331">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-331">**Option name**</span></span> | <span data-ttu-id="e2249-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="e2249-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="e2249-333">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-333">**Applicable languages**</span></span> | <span data-ttu-id="e2249-334">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-334">C#</span></span> |
| <span data-ttu-id="e2249-335">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-335">**Introduced version**</span></span> | <span data-ttu-id="e2249-336">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-337">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-337">**Option values**</span></span> | <span data-ttu-id="e2249-338">`flush_left` - ラベルは左端の列に配置されます</span><span class="sxs-lookup"><span data-stu-id="e2249-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="e2249-339">`one_less_than_current` - ラベルは、現在のコンテキストのインデントを 1 つ減らした位置に配置されます</span><span class="sxs-lookup"><span data-stu-id="e2249-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="e2249-340">`no_change` - ラベルは、現在のコンテキストと同じインデントで配置されます</span><span class="sxs-lookup"><span data-stu-id="e2249-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="e2249-341">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-341">Code examples:</span></span>

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="e2249-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="e2249-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="e2249-343">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-343">Property</span></span>|<span data-ttu-id="e2249-344">値</span><span class="sxs-lookup"><span data-stu-id="e2249-344">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-345">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-345">**Option name**</span></span> | <span data-ttu-id="e2249-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="e2249-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="e2249-347">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-347">**Applicable languages**</span></span> | <span data-ttu-id="e2249-348">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-348">C#</span></span> |
| <span data-ttu-id="e2249-349">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="e2249-350">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-350">Code examples:</span></span>

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a><span data-ttu-id="e2249-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="e2249-351">csharp_indent_braces</span></span>

|<span data-ttu-id="e2249-352">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-352">Property</span></span>|<span data-ttu-id="e2249-353">値</span><span class="sxs-lookup"><span data-stu-id="e2249-353">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-354">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-354">**Option name**</span></span> | <span data-ttu-id="e2249-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="e2249-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="e2249-356">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-356">**Applicable languages**</span></span> | <span data-ttu-id="e2249-357">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-357">C#</span></span> |
| <span data-ttu-id="e2249-358">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="e2249-359">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-359">Code examples:</span></span>

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="e2249-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="e2249-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="e2249-361">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-361">Property</span></span>|<span data-ttu-id="e2249-362">値</span><span class="sxs-lookup"><span data-stu-id="e2249-362">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-363">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-363">**Option name**</span></span> | <span data-ttu-id="e2249-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="e2249-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="e2249-365">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-365">**Applicable languages**</span></span> | <span data-ttu-id="e2249-366">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-366">C#</span></span> |
| <span data-ttu-id="e2249-367">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="e2249-368">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-368">Code examples:</span></span>

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a><span data-ttu-id="e2249-369">スペース オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-369">Spacing options</span></span>

<span data-ttu-id="e2249-370">これらの書式ルールは、コードの書式を設定する場合の空白文字の使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="e2249-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="e2249-371">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="e2249-371">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="e2249-372">csharp\_space\_after_cast</span><span class="sxs-lookup"><span data-stu-id="e2249-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="e2249-373">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-373">Property</span></span>|<span data-ttu-id="e2249-374">値</span><span class="sxs-lookup"><span data-stu-id="e2249-374">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-375">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-375">**Option name**</span></span> | <span data-ttu-id="e2249-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="e2249-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="e2249-377">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-377">**Applicable languages**</span></span> | <span data-ttu-id="e2249-378">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-378">C#</span></span> |
| <span data-ttu-id="e2249-379">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-379">**Introduced version**</span></span> | <span data-ttu-id="e2249-380">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-381">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-381">**Option values**</span></span> | <span data-ttu-id="e2249-382">`true` - キャストと値の間に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="e2249-383">`false` - キャストと値の間の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="e2249-384">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="e2249-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="e2249-386">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-386">Property</span></span>|<span data-ttu-id="e2249-387">値</span><span class="sxs-lookup"><span data-stu-id="e2249-387">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-388">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-388">**Option name**</span></span> | <span data-ttu-id="e2249-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="e2249-390">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-390">**Applicable languages**</span></span> | <span data-ttu-id="e2249-391">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-391">C#</span></span> |
| <span data-ttu-id="e2249-392">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-392">**Introduced version**</span></span> | <span data-ttu-id="e2249-393">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-394">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-394">**Option values**</span></span> | <span data-ttu-id="e2249-395">`true` - `for` ループなど、制御フロー ステートメントのキーワードの後に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="e2249-396">`false` - `for` ループなど、制御フロー ステートメントのキーワードの後の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="e2249-397">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="e2249-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="e2249-399">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-399">Property</span></span>|<span data-ttu-id="e2249-400">値</span><span class="sxs-lookup"><span data-stu-id="e2249-400">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-401">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-401">**Option name**</span></span> | <span data-ttu-id="e2249-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="e2249-403">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-403">**Applicable languages**</span></span> | <span data-ttu-id="e2249-404">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-404">C#</span></span> |
| <span data-ttu-id="e2249-405">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-405">**Introduced version**</span></span> | <span data-ttu-id="e2249-406">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-407">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-407">**Option values**</span></span> | <span data-ttu-id="e2249-408">`control_flow_statements` - 制御フロー ステートメントのかっこの間にスペースを配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="e2249-409">`expressions` - 式のかっこの間にスペースを配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="e2249-410">`type_casts` - 型キャストのかっこの間にスペースを配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="e2249-411">このルールを省略するか、`control_flow_statements`、`expressions`、または `type_casts` 以外の値を使用する場合、設定は適用されません。</span><span class="sxs-lookup"><span data-stu-id="e2249-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="e2249-412">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="e2249-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="e2249-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="e2249-414">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-414">Property</span></span>|<span data-ttu-id="e2249-415">値</span><span class="sxs-lookup"><span data-stu-id="e2249-415">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-416">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-416">**Option name**</span></span> | <span data-ttu-id="e2249-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="e2249-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="e2249-418">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-418">**Applicable languages**</span></span> | <span data-ttu-id="e2249-419">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-419">C#</span></span> |
| <span data-ttu-id="e2249-420">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-420">**Introduced version**</span></span> | <span data-ttu-id="e2249-421">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="e2249-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="e2249-422">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-422">**Option values**</span></span> | <span data-ttu-id="e2249-423">`true` - 型宣言ではベースまたはインターフェイスのコロンの前に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="e2249-424">`false` - 型宣言ではベースまたはインターフェイスのコロンの前の空白文字を除去します</span><span class="sxs-lookup"><span data-stu-id="e2249-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="e2249-425">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-425">Code examples:</span></span>

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="e2249-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="e2249-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="e2249-427">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-427">Property</span></span>|<span data-ttu-id="e2249-428">値</span><span class="sxs-lookup"><span data-stu-id="e2249-428">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-429">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-429">**Option name**</span></span> | <span data-ttu-id="e2249-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="e2249-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="e2249-431">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-431">**Applicable languages**</span></span> | <span data-ttu-id="e2249-432">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-432">C#</span></span> |
| <span data-ttu-id="e2249-433">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-433">**Introduced version**</span></span> | <span data-ttu-id="e2249-434">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="e2249-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="e2249-435">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-435">**Option values**</span></span> | <span data-ttu-id="e2249-436">`true` - 型宣言ではベースまたはインターフェイスのコロンの後に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="e2249-437">`false` - 型宣言ではベースまたはインターフェイスのコロンの後の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="e2249-438">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-438">Code examples:</span></span>

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="e2249-439">csharp\_space\_around\_binary_operators</span><span class="sxs-lookup"><span data-stu-id="e2249-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="e2249-440">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-440">Property</span></span>|<span data-ttu-id="e2249-441">値</span><span class="sxs-lookup"><span data-stu-id="e2249-441">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-442">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-442">**Option name**</span></span> | <span data-ttu-id="e2249-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="e2249-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="e2249-444">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-444">**Applicable languages**</span></span> | <span data-ttu-id="e2249-445">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-445">C#</span></span> |
| <span data-ttu-id="e2249-446">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-446">**Introduced version**</span></span> | <span data-ttu-id="e2249-447">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="e2249-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="e2249-448">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-448">**Option values**</span></span> | <span data-ttu-id="e2249-449">`before_and_after` - バイナリ演算子の前後にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="e2249-450">`none` - バイナリ演算子の前後のスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="e2249-451">`ignore` - バイナリ演算子の前後のスペースを無視します</span><span class="sxs-lookup"><span data-stu-id="e2249-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="e2249-452">このルールを省略するか、`before_and_after`、`none`、または `ignore` 以外の値を使用する場合、設定は適用されません。</span><span class="sxs-lookup"><span data-stu-id="e2249-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="e2249-453">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="e2249-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="e2249-455">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-455">Property</span></span>|<span data-ttu-id="e2249-456">値</span><span class="sxs-lookup"><span data-stu-id="e2249-456">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-457">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-457">**Option name**</span></span> | <span data-ttu-id="e2249-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="e2249-459">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-459">**Applicable languages**</span></span> | <span data-ttu-id="e2249-460">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-460">C#</span></span> |
| <span data-ttu-id="e2249-461">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-461">**Introduced version**</span></span> | <span data-ttu-id="e2249-462">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-463">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-463">**Option values**</span></span> | <span data-ttu-id="e2249-464">`true` - メソッド宣言パラメーター リストの始めかっこの後と終わりかっこの前に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="e2249-465">`false` - メソッド宣言パラメーター リストの始めかっこの後と終わりかっこの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="e2249-466">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="e2249-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="e2249-468">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-468">Property</span></span>|<span data-ttu-id="e2249-469">値</span><span class="sxs-lookup"><span data-stu-id="e2249-469">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-470">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-470">**Option name**</span></span> | <span data-ttu-id="e2249-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="e2249-472">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-472">**Applicable languages**</span></span> | <span data-ttu-id="e2249-473">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-473">C#</span></span> |
| <span data-ttu-id="e2249-474">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-474">**Introduced version**</span></span> | <span data-ttu-id="e2249-475">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="e2249-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="e2249-476">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-476">**Option values**</span></span> | <span data-ttu-id="e2249-477">`true` - メソッド宣言の空のパラメーター リストのかっこ内にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="e2249-478">`false` - メソッド宣言の空のパラメーター リストのかっこ内にスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="e2249-479">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-479">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="e2249-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="e2249-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="e2249-481">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-481">Property</span></span>|<span data-ttu-id="e2249-482">値</span><span class="sxs-lookup"><span data-stu-id="e2249-482">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-483">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-483">**Option name**</span></span> | <span data-ttu-id="e2249-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="e2249-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="e2249-485">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-485">**Applicable languages**</span></span> | <span data-ttu-id="e2249-486">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-486">C#</span></span> |
| <span data-ttu-id="e2249-487">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-487">**Option values**</span></span> | <span data-ttu-id="e2249-488">`true` - メソッド宣言のメソッド名と始めかっこの間に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="e2249-489">`false` - メソッド宣言のメソッド名と始めかっこの間の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="e2249-490">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="e2249-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="e2249-492">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-492">Property</span></span>|<span data-ttu-id="e2249-493">値</span><span class="sxs-lookup"><span data-stu-id="e2249-493">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-494">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-494">**Option name**</span></span> | <span data-ttu-id="e2249-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="e2249-496">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-496">**Applicable languages**</span></span> | <span data-ttu-id="e2249-497">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-497">C#</span></span> |
| <span data-ttu-id="e2249-498">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-498">**Introduced version**</span></span> | <span data-ttu-id="e2249-499">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-500">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-500">**Option values**</span></span> | <span data-ttu-id="e2249-501">`true` - メソッド呼び出しの始めかっこの後と終わりかっこの前に空白文字を配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="e2249-502">`false` - メソッド呼び出しの始めかっこの後と終わりかっこの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="e2249-503">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="e2249-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="e2249-505">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-505">Property</span></span>|<span data-ttu-id="e2249-506">値</span><span class="sxs-lookup"><span data-stu-id="e2249-506">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-507">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-507">**Option name**</span></span> | <span data-ttu-id="e2249-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="e2249-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="e2249-509">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-509">**Applicable languages**</span></span> | <span data-ttu-id="e2249-510">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-510">C#</span></span> |
| <span data-ttu-id="e2249-511">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-511">**Introduced version**</span></span> | <span data-ttu-id="e2249-512">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="e2249-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="e2249-513">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-513">**Option values**</span></span> | <span data-ttu-id="e2249-514">`true` - 空の引数リストのかっこ内にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="e2249-515">`false` - 空の引数リストのかっこ内にスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="e2249-516">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-516">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="e2249-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="e2249-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="e2249-518">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-518">Property</span></span>|<span data-ttu-id="e2249-519">値</span><span class="sxs-lookup"><span data-stu-id="e2249-519">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-520">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-520">**Option name**</span></span> | <span data-ttu-id="e2249-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="e2249-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="e2249-522">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-522">**Applicable languages**</span></span> | <span data-ttu-id="e2249-523">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-523">C#</span></span> |
| <span data-ttu-id="e2249-524">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-524">**Introduced version**</span></span> | <span data-ttu-id="e2249-525">Visual Studio 2017 バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="e2249-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="e2249-526">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-526">**Option values**</span></span> | <span data-ttu-id="e2249-527">`true` - メソッド呼び出し名と左かっこの間にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="e2249-528">`false` - メソッド呼び出し名と左かっこの間にスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="e2249-529">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-529">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="e2249-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="e2249-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="e2249-531">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-531">Property</span></span>|<span data-ttu-id="e2249-532">値</span><span class="sxs-lookup"><span data-stu-id="e2249-532">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-533">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-533">**Option name**</span></span> | <span data-ttu-id="e2249-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="e2249-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="e2249-535">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-535">**Applicable languages**</span></span> | <span data-ttu-id="e2249-536">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-536">C#</span></span> |
| <span data-ttu-id="e2249-537">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-537">**Option values**</span></span> | <span data-ttu-id="e2249-538">`true` - コンマの後にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="e2249-539">`false` - コンマの後のスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="e2249-540">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="e2249-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="e2249-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="e2249-542">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-542">Property</span></span>|<span data-ttu-id="e2249-543">値</span><span class="sxs-lookup"><span data-stu-id="e2249-543">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-544">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-544">**Option name**</span></span> | <span data-ttu-id="e2249-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="e2249-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="e2249-546">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-546">**Applicable languages**</span></span> | <span data-ttu-id="e2249-547">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-547">C#</span></span> |
| <span data-ttu-id="e2249-548">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-548">**Option values**</span></span> | <span data-ttu-id="e2249-549">`true` - コンマの前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="e2249-550">`false` - コンマの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="e2249-551">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="e2249-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="e2249-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="e2249-553">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-553">Property</span></span>|<span data-ttu-id="e2249-554">値</span><span class="sxs-lookup"><span data-stu-id="e2249-554">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-555">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-555">**Option name**</span></span> | <span data-ttu-id="e2249-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="e2249-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="e2249-557">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-557">**Applicable languages**</span></span> | <span data-ttu-id="e2249-558">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-558">C#</span></span> |
| <span data-ttu-id="e2249-559">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-559">**Option values**</span></span> | <span data-ttu-id="e2249-560">`true` - ドットの後にスペースを挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="e2249-561">`false` - ドットの後のスペースを削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="e2249-562">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="e2249-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="e2249-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="e2249-564">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-564">Property</span></span>|<span data-ttu-id="e2249-565">値</span><span class="sxs-lookup"><span data-stu-id="e2249-565">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-566">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-566">**Option name**</span></span> | <span data-ttu-id="e2249-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="e2249-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="e2249-568">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-568">**Applicable languages**</span></span> | <span data-ttu-id="e2249-569">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-569">C#</span></span> |
| <span data-ttu-id="e2249-570">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-570">**Option values**</span></span> | <span data-ttu-id="e2249-571">`true` - ドットの前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="e2249-572">`false` - ドットの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="e2249-573">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="e2249-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="e2249-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="e2249-575">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-575">Property</span></span>|<span data-ttu-id="e2249-576">値</span><span class="sxs-lookup"><span data-stu-id="e2249-576">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-577">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-577">**Option name**</span></span> | <span data-ttu-id="e2249-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="e2249-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="e2249-579">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-579">**Applicable languages**</span></span> | <span data-ttu-id="e2249-580">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-580">C#</span></span> |
| <span data-ttu-id="e2249-581">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-581">**Option values**</span></span> | <span data-ttu-id="e2249-582">`true` - `for` ステートメントの各セミコロンの後に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="e2249-583">`false` - `for` ステートメントの各セミコロンの後の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="e2249-584">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

#### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="e2249-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="e2249-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="e2249-586">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-586">Property</span></span>|<span data-ttu-id="e2249-587">値</span><span class="sxs-lookup"><span data-stu-id="e2249-587">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-588">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-588">**Option name**</span></span> | <span data-ttu-id="e2249-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="e2249-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="e2249-590">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-590">**Applicable languages**</span></span> | <span data-ttu-id="e2249-591">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-591">C#</span></span> |
| <span data-ttu-id="e2249-592">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-592">**Option values**</span></span> | <span data-ttu-id="e2249-593">`true` - `for` ステートメントの各セミコロンの前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="e2249-594">`false` - `for` ステートメントの各セミコロンの前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="e2249-595">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="e2249-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="e2249-597">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-597">Property</span></span>|<span data-ttu-id="e2249-598">値</span><span class="sxs-lookup"><span data-stu-id="e2249-598">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-599">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-599">**Option name**</span></span> | <span data-ttu-id="e2249-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="e2249-601">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-601">**Applicable languages**</span></span> | <span data-ttu-id="e2249-602">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-602">C#</span></span> |
| <span data-ttu-id="e2249-603">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-603">**Option values**</span></span> | <span data-ttu-id="e2249-604">`ignore` - 宣言ステートメント内の余分な空白文字を削除しません</span><span class="sxs-lookup"><span data-stu-id="e2249-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="e2249-605">`false` - 宣言ステートメント内の余分な空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="e2249-606">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="e2249-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="e2249-608">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-608">Property</span></span>|<span data-ttu-id="e2249-609">値</span><span class="sxs-lookup"><span data-stu-id="e2249-609">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-610">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-610">**Option name**</span></span> | <span data-ttu-id="e2249-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="e2249-612">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-612">**Applicable languages**</span></span> | <span data-ttu-id="e2249-613">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-613">C#</span></span> |
| <span data-ttu-id="e2249-614">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-614">**Option values**</span></span> | <span data-ttu-id="e2249-615">`true` - 始め角かっこ `[` の前に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="e2249-616">`false` - 始め角かっこ `[` の前の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="e2249-617">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="e2249-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="e2249-619">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-619">Property</span></span>|<span data-ttu-id="e2249-620">値</span><span class="sxs-lookup"><span data-stu-id="e2249-620">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-621">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-621">**Option name**</span></span> | <span data-ttu-id="e2249-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="e2249-623">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-623">**Applicable languages**</span></span> | <span data-ttu-id="e2249-624">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-624">C#</span></span> |
| <span data-ttu-id="e2249-625">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-625">**Option values**</span></span> | <span data-ttu-id="e2249-626">`true` - 空の角かっこ `[ ]` の間に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="e2249-627">`false` - 空の角かっこ `[]` の間の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="e2249-628">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="e2249-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="e2249-630">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-630">Property</span></span>|<span data-ttu-id="e2249-631">値</span><span class="sxs-lookup"><span data-stu-id="e2249-631">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-632">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-632">**Option name**</span></span> | <span data-ttu-id="e2249-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="e2249-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="e2249-634">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-634">**Applicable languages**</span></span> | <span data-ttu-id="e2249-635">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-635">C#</span></span> |
| <span data-ttu-id="e2249-636">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-636">**Option values**</span></span> | <span data-ttu-id="e2249-637">`true` - 空ではない角かっこ `[ 0 ]` に空白文字を挿入します</span><span class="sxs-lookup"><span data-stu-id="e2249-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="e2249-638">`false` - 空ではない角かっこ `[0]` の空白文字を削除します</span><span class="sxs-lookup"><span data-stu-id="e2249-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="e2249-639">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="e2249-640">折り返しオプション</span><span class="sxs-lookup"><span data-stu-id="e2249-640">Wrap options</span></span>

<span data-ttu-id="e2249-641">これらの書式ルールは、ステートメントとコード ブロックでの 1 行と別の行の使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="e2249-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="e2249-642">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="e2249-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="e2249-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="e2249-644">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-644">Property</span></span>|<span data-ttu-id="e2249-645">値</span><span class="sxs-lookup"><span data-stu-id="e2249-645">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-646">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-646">**Option name**</span></span> | <span data-ttu-id="e2249-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="e2249-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="e2249-648">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-648">**Applicable languages**</span></span> | <span data-ttu-id="e2249-649">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-649">C#</span></span> |
| <span data-ttu-id="e2249-650">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-650">**Introduced version**</span></span> | <span data-ttu-id="e2249-651">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-652">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-652">**Option values**</span></span> | <span data-ttu-id="e2249-653">`true` - 1 行に複数のステートメントとメンバー宣言を表示します</span><span class="sxs-lookup"><span data-stu-id="e2249-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="e2249-654">`false` - 別の行にステートメントとメンバー宣言を表示します</span><span class="sxs-lookup"><span data-stu-id="e2249-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="e2249-655">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="e2249-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="e2249-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="e2249-657">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-657">Property</span></span>|<span data-ttu-id="e2249-658">値</span><span class="sxs-lookup"><span data-stu-id="e2249-658">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-659">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-659">**Option name**</span></span> | <span data-ttu-id="e2249-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="e2249-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="e2249-661">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-661">**Applicable languages**</span></span> | <span data-ttu-id="e2249-662">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-662">C#</span></span> |
| <span data-ttu-id="e2249-663">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-663">**Introduced version**</span></span> | <span data-ttu-id="e2249-664">Visual Studio 2017 バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="e2249-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="e2249-665">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-665">**Option values**</span></span> | <span data-ttu-id="e2249-666">`true` - コード ブロックを単一行に配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="e2249-667">`false` - コード ブロックを別の行に配置します</span><span class="sxs-lookup"><span data-stu-id="e2249-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="e2249-668">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="e2249-669">using ディレクティブ オプション</span><span class="sxs-lookup"><span data-stu-id="e2249-669">Using directive options</span></span>

<span data-ttu-id="e2249-670">この書式ルールは、名前空間の内部と外部に配置される using ディレクティブの使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="e2249-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="e2249-671">*.editorconfig* ファイルの例:</span><span class="sxs-lookup"><span data-stu-id="e2249-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="e2249-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="e2249-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="e2249-673">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2249-673">Property</span></span>|<span data-ttu-id="e2249-674">値</span><span class="sxs-lookup"><span data-stu-id="e2249-674">Value</span></span>|
|-|-|
| <span data-ttu-id="e2249-675">**オプション名**</span><span class="sxs-lookup"><span data-stu-id="e2249-675">**Option name**</span></span> | <span data-ttu-id="e2249-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="e2249-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="e2249-677">**該当言語**</span><span class="sxs-lookup"><span data-stu-id="e2249-677">**Applicable languages**</span></span> | <span data-ttu-id="e2249-678">C#</span><span class="sxs-lookup"><span data-stu-id="e2249-678">C#</span></span> |
| <span data-ttu-id="e2249-679">**導入されたバージョン**</span><span class="sxs-lookup"><span data-stu-id="e2249-679">**Introduced version**</span></span> | <span data-ttu-id="e2249-680">Visual Studio 2019 バージョン 16.1</span><span class="sxs-lookup"><span data-stu-id="e2249-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="e2249-681">**オプションの値**</span><span class="sxs-lookup"><span data-stu-id="e2249-681">**Option values**</span></span> | <span data-ttu-id="e2249-682">`outside_namespace` - 名前空間の外部のディレクティブが使用されます</span><span class="sxs-lookup"><span data-stu-id="e2249-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="e2249-683">`inside_namespace` - 名前空間の内部のディレクティブが使用されます</span><span class="sxs-lookup"><span data-stu-id="e2249-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="e2249-684">コード例:</span><span class="sxs-lookup"><span data-stu-id="e2249-684">Code examples:</span></span>

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a><span data-ttu-id="e2249-685">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2249-685">See also</span></span>

- [<span data-ttu-id="e2249-686">言語規則</span><span class="sxs-lookup"><span data-stu-id="e2249-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="e2249-687">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="e2249-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="e2249-688">.NET コード スタイルの規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="e2249-688">.NET code style rules reference</span></span>](index.md)
