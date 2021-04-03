---
title: 定義済み構成ファイル (コード分析)
description: 定義済み editorconfig ファイルとルール セット ファイルを使用して、特定の種類のコード分析をターゲットとする方法について説明します。
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 748ab8a9ddfcfcadeb33da877769cedac901655a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876592"
---
# <a name="predefined-configuration-files"></a><span data-ttu-id="2baa5-103">定義済み構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2baa5-103">Predefined configuration files</span></span>

<span data-ttu-id="2baa5-104">定義済み EditorConfig ファイルと[ルール セット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルを利用して、セキュリティ ルールやデザイン ルールなどのコード品質ルールのカテゴリをすばやく簡単に有効にできます。</span><span class="sxs-lookup"><span data-stu-id="2baa5-104">Predefined EditorConfig and [rule set](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) files are available that make it quick and easy to enable a category of code quality rules, such as security or design rules.</span></span> <span data-ttu-id="2baa5-105">特定のカテゴリのルールを有効にすることにより、ターゲットとなる問題や特定の条件を識別できます。</span><span class="sxs-lookup"><span data-stu-id="2baa5-105">By enabling a specific category of rules, you can identify targeted issues and specific conditions.</span></span> <span data-ttu-id="2baa5-106">これらの定義済みファイルにアクセスするには、[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet アナライザー パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2baa5-106">To access these predefined files, install the [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer package.</span></span>

<span data-ttu-id="2baa5-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) には、定義済み EditorConfig ファイルと、次のルール カテゴリのルール セットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2baa5-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) includes predefined EditorConfig files and rule sets for the following rule categories:</span></span>

- <span data-ttu-id="2baa5-108">すべてのルール</span><span class="sxs-lookup"><span data-stu-id="2baa5-108">All rules</span></span>
- <span data-ttu-id="2baa5-109">データフロー</span><span class="sxs-lookup"><span data-stu-id="2baa5-109">Dataflow</span></span>
- <span data-ttu-id="2baa5-110">デザイン</span><span class="sxs-lookup"><span data-stu-id="2baa5-110">Design</span></span>
- <span data-ttu-id="2baa5-111">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2baa5-111">Documentation</span></span>
- <span data-ttu-id="2baa5-112">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="2baa5-112">Globalization</span></span>
- <span data-ttu-id="2baa5-113">相互運用性</span><span class="sxs-lookup"><span data-stu-id="2baa5-113">Interoperability</span></span>
- <span data-ttu-id="2baa5-114">保守容易性</span><span class="sxs-lookup"><span data-stu-id="2baa5-114">Maintainability</span></span>
- <span data-ttu-id="2baa5-115">名前を付ける</span><span class="sxs-lookup"><span data-stu-id="2baa5-115">Naming</span></span>
- <span data-ttu-id="2baa5-116">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="2baa5-116">Performance</span></span>
- <span data-ttu-id="2baa5-117">FxCop からの移植</span><span class="sxs-lookup"><span data-stu-id="2baa5-117">Ported from FxCop</span></span>
- <span data-ttu-id="2baa5-118">[信頼性]</span><span class="sxs-lookup"><span data-stu-id="2baa5-118">Reliability</span></span>
- <span data-ttu-id="2baa5-119">Security</span><span class="sxs-lookup"><span data-stu-id="2baa5-119">Security</span></span>
- <span data-ttu-id="2baa5-120">使用法</span><span class="sxs-lookup"><span data-stu-id="2baa5-120">Usage</span></span>

<span data-ttu-id="2baa5-121">これらのルールの各カテゴリには、次のための EditorConfig ファイルまたはルール セット ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="2baa5-121">Each of those categories of rules has an EditorConfig or rule set file to:</span></span>

- <span data-ttu-id="2baa5-122">カテゴリ内のすべてのルールを有効にする (および他のすべてのルールを無効にする)</span><span class="sxs-lookup"><span data-stu-id="2baa5-122">Enable all the rules in the category (and disable all other rules)</span></span>
- <span data-ttu-id="2baa5-123">各ルールの既定の重要度、および既定の設定で有効になっているものを使用する (および他のすべてのルールを無効にする)</span><span class="sxs-lookup"><span data-stu-id="2baa5-123">Use each rule's default severity and enabled by default setting (and disable all other rules)</span></span>

> [!TIP]
> <span data-ttu-id="2baa5-124">"すべてのルール" カテゴリには、すべてのルールを無効にするための追加の EditorConfig ファイルまたはルール セット ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="2baa5-124">The "all rules" category has an additional EditorConfig or rule set file to disable all rules.</span></span> <span data-ttu-id="2baa5-125">このファイルを使用すると、プロジェクト内のアナライザーの警告やエラーすべてをすぐに除去できます。</span><span class="sxs-lookup"><span data-stu-id="2baa5-125">Use this file to quickly get rid of any analyzer warnings or errors in a project.</span></span>

## <a name="predefined-editorconfig-files"></a><span data-ttu-id="2baa5-126">定義済み EditorConfig ファイル</span><span class="sxs-lookup"><span data-stu-id="2baa5-126">Predefined EditorConfig files</span></span>

<span data-ttu-id="2baa5-127">Microsoft.CodeAnalysis.NetAnalyzers アナライザー パッケージ用の定義済み EditorConfig ファイルは、NuGet パッケージがインストールされた場所の *editorconfig* サブディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="2baa5-127">The predefined EditorConfig files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *editorconfig* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="2baa5-128">たとえば、すべてのセキュリティ ルールを有効にする EditorConfig ファイルは、*editorconfig/SecurityRulesEnabled/.editorconfig* にあります。</span><span class="sxs-lookup"><span data-stu-id="2baa5-128">For example, the EditorConfig file to enable all security rules is located at *editorconfig/SecurityRulesEnabled/.editorconfig*.</span></span>

<span data-ttu-id="2baa5-129">選択した *.editorconfig* ファイルを、プロジェクトのルート ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="2baa5-129">Copy the chosen *.editorconfig* file to your project's root directory.</span></span>

## <a name="predefined-rule-sets"></a><span data-ttu-id="2baa5-130">定義済みの規則セット</span><span class="sxs-lookup"><span data-stu-id="2baa5-130">Predefined rule sets</span></span>

<span data-ttu-id="2baa5-131">Microsoft.CodeAnalysis.NetAnalyzers アナライザー パッケージ用の定義済みルール セット ファイルは、NuGet パッケージがインストールされた場所の *rulesets* サブディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="2baa5-131">The predefined rule set files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *rulesets* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="2baa5-132">たとえば、すべてのセキュリティ ルールを有効にするルール セット ファイルは、*rulesets/SecurityRulesEnabled.ruleset* にあります。</span><span class="sxs-lookup"><span data-stu-id="2baa5-132">For example, the rule set file to enable all security rules is located at *rulesets/SecurityRulesEnabled.ruleset*.</span></span> <span data-ttu-id="2baa5-133">このルール セットの中の 1 つまたは複数をコピーし、プロジェクトが格納されているディレクトリに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="2baa5-133">Copy one or more of the rule sets and paste them in the directory that contains your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="2baa5-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2baa5-134">See also</span></span>

- [<span data-ttu-id="2baa5-135">アナライザーの構成</span><span class="sxs-lookup"><span data-stu-id="2baa5-135">Analyzer configuration</span></span>](https://github.com/dotnet/roslyn-analyzers/blob/main/docs/Analyzer%20Configuration.md)
- [<span data-ttu-id="2baa5-136">EditorConfig 用 .NET コード スタイル ルール オプション</span><span class="sxs-lookup"><span data-stu-id="2baa5-136">.NET code style rule options for EditorConfig</span></span>](code-style-rule-options.md)
