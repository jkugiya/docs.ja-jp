---
title: 'チュートリアル: 最初のアナライザーとコード修正を作成する'
description: このチュートリアルでは、.NET Compiler SDK (Roslyn API) を使用してアナライザーとコード修正を作成する手順を詳しく説明します。
ms.date: 03/02/2021
ms.custom: mvc
ms.openlocfilehash: b712cb4df5ab6dae825407212685cb1a08b2d189
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637248"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="aaa7e-103">チュートリアル: 最初のアナライザーとコード修正を作成する</span><span class="sxs-lookup"><span data-stu-id="aaa7e-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="aaa7e-104">.NET Compiler Platform SDK には、C# または Visual Basic コードをターゲットとするカスタム診断 (アナライザー)、コード修正、コード リファクタリング、診断サプレッサーを作成するために必要なツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-104">The .NET Compiler Platform SDK provides the tools you need to create custom diagnostics (analyzers), code fixes, code refactoring, and diagnostic suppressors that target C# or Visual Basic code.</span></span> <span data-ttu-id="aaa7e-105">**アナライザー** には、規則違反を認識するコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-105">An **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="aaa7e-106">**コード修正** には、違反を修正するコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="aaa7e-107">実装する規則には、コード構造から、コーディング スタイル、名前付け規則などがあります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="aaa7e-108">.NET Compiler Platform には、開発者がコードを作成するときに分析を実行するためのフレームワークと、コードを修正するためのすべての Visual Studio UI 機能が用意されています。具体的には、エディターに波線を表示する、Visual Studio のエラー一覧を表示する、"電球" の提案を作成する、推奨される修正の豊富なプレビューを表示するなどの機能です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="aaa7e-109">このチュートリアルでは、Roslyn API を使用して **アナライザー** とそれに付随する **コード修正** の作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="aaa7e-110">アナライザーは、ソース コードの分析を実行し、問題をユーザーに報告する方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="aaa7e-111">必要に応じて、コード修正プログラムをアナライザーに関連付けて、ユーザーのソース コードの変更を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-111">Optionally, a code fix can be associated with the analyzer to represent a modification to the user's source code.</span></span> <span data-ttu-id="aaa7e-112">このチュートリアルでは、`const` 修飾子を使用して宣言できますが、実際は宣言されていないローカル変数宣言を検出するアナライザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="aaa7e-113">付随するコード修正は、それらの宣言を修正して `const` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aaa7e-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="aaa7e-114">Prerequisites</span></span>

- <span data-ttu-id="aaa7e-115">[Visual Studio 2019](https://www.visualstudio.com/downloads) バージョン 16.8 以降</span><span class="sxs-lookup"><span data-stu-id="aaa7e-115">[Visual Studio 2019](https://www.visualstudio.com/downloads) version 16.8 or later</span></span>

<span data-ttu-id="aaa7e-116">Visual Studio インストーラーで **.NET Compiler Platform SDK** をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-116">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="aaa7e-117">アナライザーの作成と検証にはいくつかの手順があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-117">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="aaa7e-118">ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-118">Create the solution.</span></span>
1. <span data-ttu-id="aaa7e-119">アナライザーの名前と説明を登録します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-119">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="aaa7e-120">アナライザーの警告と推奨事項を報告します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-120">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="aaa7e-121">推奨事項を受け取るコード修正を実装します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-121">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="aaa7e-122">単体テストで分析を改善します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-122">Improve the analysis through unit tests.</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="aaa7e-123">ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="aaa7e-123">Create the solution</span></span>

- <span data-ttu-id="aaa7e-124">Visual Studio で、 **[ファイル] > [新規] > [プロジェクト]** の順に選択して、[新しいプロジェクト] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-124">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="aaa7e-125">**[Visual C#] > [Extensibility]** で、 **[Analyzer with code fix (.NET Standard)]\(コード修正付きアナライザー (.NET Standard)\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-125">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="aaa7e-126">プロジェクトに「**MakeConst**」という名前を付けて、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-126">Name your project "**MakeConst**" and click OK.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="aaa7e-127">アナライザー テンプレートを調べる</span><span class="sxs-lookup"><span data-stu-id="aaa7e-127">Explore the analyzer template</span></span>

<span data-ttu-id="aaa7e-128">コード修正テンプレート付きアナライザーを使用すると、5 つのプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-128">The analyzer with code fix template creates five projects:</span></span>

- <span data-ttu-id="aaa7e-129">**MakeConst**: アナライザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-129">**MakeConst**, which contains the analyzer.</span></span>
- <span data-ttu-id="aaa7e-130">**MakeConst.CodeFixes**: コード修正が含まれています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-130">**MakeConst.CodeFixes**, which contains the code fix.</span></span>
- <span data-ttu-id="aaa7e-131">**MakeConst.Package**: アナライザーとコード修正の NuGet パッケージを生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-131">**MakeConst.Package**, which is used to produce NuGet package for the analyzer and code fix.</span></span>
- <span data-ttu-id="aaa7e-132">**MakeConst.Test**: 単体テスト プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-132">**MakeConst.Test**, which is a unit test project.</span></span>
- <span data-ttu-id="aaa7e-133">**MakeConst.Vsix**: 新しいアナライザーが読み込まれた Visual Studio の 2 番目のインスタンスを起動する既定のスタートアップ プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-133">**MakeConst.Vsix**, which is the default startup project that starts a second instance of Visual Studio that has loaded your new analyzer.</span></span> <span data-ttu-id="aaa7e-134"><kbd>F5</kbd> キーを押して、VSIX プロジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-134">Press <kbd>F5</kbd> to start the VSIX project.</span></span>

> [!TIP]
> <span data-ttu-id="aaa7e-135">アナライザーを実行するときは、Visual Studio の 2 つ目のコピーを開始します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-135">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="aaa7e-136">この 2 つ目のコピーは、別のレジストリ ハイブを使用して設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-136">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="aaa7e-137">これにより、Visual Studio の 2 つのコピーのビジュアル設定を区別することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-137">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="aaa7e-138">Visual Studio の実験的な実行のために、別のテーマを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-138">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="aaa7e-139">また、設定のローミングや、Visual Studio アカウントへのログインには、Visual Studio の実験的な実行が使用されません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-139">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="aaa7e-140">そのため、設定を分けておくことができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-140">That keeps the settings different.</span></span>

<span data-ttu-id="aaa7e-141">開始した 2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成します (任意のターゲット フレームワークが動作し、アナライザーはソース レベルで動作します)。波線の下線が表示されているトークンにマウス カーソルを移動すると、アナライザーに設定されている警告テキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-141">In the second Visual Studio instance that you just started, create a new C# Console Application project (any target framework will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="aaa7e-142">テンプレートを使用すると、次の図のように、型名が小文字の個々の型宣言に対して警告を報告するアナライザーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-142">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![警告を報告するアナライザー](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="aaa7e-144">また、テンプレートには、小文字を含むすべての型名をすべて大文字に変更するコード修正も用意されています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-144">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="aaa7e-145">警告が表示された電球をクリックすると、推奨される変更が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-145">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="aaa7e-146">推奨される変更を受け入れると、型の名前と、ソリューション内のその型に対するすべての参照が更新されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-146">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="aaa7e-147">最初のアナライザーの動作を確認したら、2 つ目の Visual Studio インスタンスを閉じ、アナライザー プロジェクトに戻ります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-147">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="aaa7e-148">アナライザーのすべての変更をテストするために、Visual Studio の 2 つ目のコピーを開始して、新しいコードを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-148">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="aaa7e-149">このテンプレートを使用すると、単体テスト プロジェクトも自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-149">The template also creates a unit test project for you.</span></span> <span data-ttu-id="aaa7e-150">このプロジェクトには 2 つのテストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-150">That project contains two tests.</span></span> <span data-ttu-id="aaa7e-151">`TestMethod1` では、診断をトリガーせずにコードを分析するテストの一般的な形式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-151">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="aaa7e-152">`TestMethod2` では、診断をトリガーするテストの形式が表示され、推奨されたコード修正が適用されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-152">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="aaa7e-153">アナライザーとコード修正をビルドするときに、異なるコード構造のテストを作成して作業を検証します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-153">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="aaa7e-154">アナライザーの単体テストは、Visual Studio を使用して対話的にテストするよりもはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-154">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="aaa7e-155">アナライザーの単体テストは、アナライザーをトリガーするべきコード構造とトリガーするべきではないコード構造を知りたいときに最適なツールです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-155">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="aaa7e-156">Visual Studio のもう 1 つのコピーにアナライザーを読み込むことは、まだ検討していない可能性のあるコンストラクトを探索して見つけるために最適なツールです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-156">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

<span data-ttu-id="aaa7e-157">このチュートリアルでは、ローカル定数に変換できるローカル変数宣言をユーザーに報告するアナライザーを記述します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-157">In this tutorial, you write an analyzer that reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="aaa7e-158">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-158">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="aaa7e-159">上記のコードでは、`x` には定数値が割り当てられており、変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-159">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="aaa7e-160">これは `const` 修飾子を使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-160">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="aaa7e-161">変数を定数にすることができるかどうかを判断するために、構文解析、初期化子式の定数分析、および変数に書き込まれないというデータフロー分析が必要です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-161">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="aaa7e-162">.NET Compiler Platform には、この分析を簡単に実行できる API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-162">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="aaa7e-163">アナライザーの登録を作成する</span><span class="sxs-lookup"><span data-stu-id="aaa7e-163">Create analyzer registrations</span></span>

<span data-ttu-id="aaa7e-164">このテンプレートを使用すると、*MakeConstAnalyzer.cs* ファイルに初期の `DiagnosticAnalyzer` クラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-164">The template creates the initial `DiagnosticAnalyzer` class, in the *MakeConstAnalyzer.cs* file.</span></span> <span data-ttu-id="aaa7e-165">この初期のアナライザーは、あらゆるアナライザーが持つ 2 つの重要な特性を示しています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-165">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="aaa7e-166">すべての診断アナライザーは、動作する言語を記述する `[DiagnosticAnalyzer]` 属性を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-166">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="aaa7e-167">すべての診断アナライザーは、<xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> クラスから (直接または間接的に) 派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-167">Every diagnostic analyzer must derive (directly or indirectly) from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="aaa7e-168">このテンプレートは、アナライザーの一部である基本機能も示しています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-168">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="aaa7e-169">アクションを登録します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-169">Register actions.</span></span> <span data-ttu-id="aaa7e-170">アクションは、アナライザーをトリガーしてコード違反を調べるコードの変更を表します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-170">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="aaa7e-171">Visual Studio で、登録済みのアクションと一致するコード編集が検出されると、アナライザーの登録済みメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-171">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="aaa7e-172">診断を作成します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-172">Create diagnostics.</span></span> <span data-ttu-id="aaa7e-173">アナライザーで違反を検出されると、違反をユーザーに通知するために Visual Studio で使用される診断オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-173">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="aaa7e-174"><xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> メソッドのオーバーライドでアクションを登録します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-174">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="aaa7e-175">このチュートリアルでは、**構文ノード** にアクセスしてローカル宣言を探し、定数値を持つものを調べます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-175">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="aaa7e-176">宣言が定数であれば、アナライザーによって診断が作成され、報告されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-176">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="aaa7e-177">最初の手順は、登録定数が "Make Const" アナライザーを示すように、登録定数と `Initialize` メソッドを更新することです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-177">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="aaa7e-178">ほとんどの文字列定数は、文字列リソース ファイルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-178">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="aaa7e-179">ローカリゼーションを容易にするには、この手法に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-179">You should follow that practice for easier localization.</span></span> <span data-ttu-id="aaa7e-180">**MakeConst** アナライザー プロジェクト用に *Resources.resx* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-180">Open the *Resources.resx* file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="aaa7e-181">これでリソース エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-181">This displays the resource editor.</span></span> <span data-ttu-id="aaa7e-182">文字列リソースを次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-182">Update the string resources as follows:</span></span>

- <span data-ttu-id="aaa7e-183">`AnalyzerDescription` を ":::no-loc text="Variables that are not modified should be made constants.":::" に変更します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-183">Change `AnalyzerDescription` to ":::no-loc text="Variables that are not modified should be made constants.":::".</span></span>
- <span data-ttu-id="aaa7e-184">`AnalyzerMessageFormat` を ":::no-loc text="Variable '{0}' can be made constant":::" に変更します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-184">Change `AnalyzerMessageFormat` to ":::no-loc text="Variable '{0}' can be made constant":::".</span></span>
- <span data-ttu-id="aaa7e-185">`AnalyzerTitle` を ":::no-loc text="Variable can be made constant":::" に変更します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-185">Change `AnalyzerTitle` to ":::no-loc text="Variable can be made constant":::.</span></span>

<span data-ttu-id="aaa7e-186">完了すると、次の図のようにリソース エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![文字列リソースを更新する](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="aaa7e-188">残りの変更はアナライザー ファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="aaa7e-189">Visual Studio で *MakeConstAnalyzer.cs* を開きます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-189">Open *MakeConstAnalyzer.cs* in Visual Studio.</span></span> <span data-ttu-id="aaa7e-190">登録済みアクションを、シンボル対して動作するものから構文に対して動作するものに変更します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="aaa7e-191">`MakeConstAnalyzerAnalyzer.Initialize` メソッドで、シンボルにアクションを登録する行を見つけます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="aaa7e-192">これを次の行で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="aaa7e-193">この変更後は、`AnalyzeSymbol` メソッドを削除できます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="aaa7e-194">このアナライザーでは、<xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> ステートメントではなく <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> ステートメントが検査されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="aaa7e-195">`AnalyzeNode` に赤い波線が表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="aaa7e-196">追加したコードは、宣言されていない `AnalyzeNode` メソッドを参照しています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="aaa7e-197">次のコードを使用してそのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="aaa7e-198">次のコードに示すように、*MakeConstAnalyzer.cs* の `Category` を :::no-loc text="Usage"::: に変更します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-198">Change the `Category` to ":::no-loc text="Usage":::" in *MakeConstAnalyzer.cs* as shown in the following code:</span></span>

[!code-csharp[Category constant](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#Category  "Change category to Usage")]

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="aaa7e-199">定数の可能性があるローカル宣言を見つける</span><span class="sxs-lookup"><span data-stu-id="aaa7e-199">Find local declarations that could be const</span></span>

<span data-ttu-id="aaa7e-200">次は `AnalyzeNode` メソッドの最初のバージョンを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="aaa7e-201">次のコードのように、`const` の可能性がありますが実際はそうではない単一のローカル宣言を探します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="aaa7e-202">最初の手順は、ローカル宣言を見つけることです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-202">The first step is to find local declarations.</span></span> <span data-ttu-id="aaa7e-203">*MakeConstAnalyzer.cs* の `AnalyzeNode` に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-203">Add the following code to `AnalyzeNode` in *MakeConstAnalyzer.cs*:</span></span>

[!code-csharp[localDeclaration variable](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#LocalDeclaration  "Add localDeclaration variable")]

<span data-ttu-id="aaa7e-204">アナライザーにローカル宣言 (ローカル宣言のみ) の変更が登録されているため、このキャストは常に成功します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="aaa7e-205">他のノードの種類では `AnalyzeNode` メソッドへの呼び出しがトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="aaa7e-206">次に、`const` 修飾子の宣言を確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="aaa7e-207">見つかったら、すぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-207">If you find them, return immediately.</span></span> <span data-ttu-id="aaa7e-208">次のコードでは、ローカル宣言の `const` 修飾子を探します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

[!code-csharp[bail-out on const keyword](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#BailOutOnConst  "bail-out on const keyword")]

<span data-ttu-id="aaa7e-209">最後に、変数を `const` にすることができることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="aaa7e-210">つまり、初期化後に決して割り当てられないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="aaa7e-211"><xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> を使用していくつかのセマンティック解析を実行します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="aaa7e-212">`context` 引数を使用して、ローカル変数の宣言を `const` にすることができるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="aaa7e-213"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> は、単一のソース ファイル内のすべてのセマンティック情報を表します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="aaa7e-214">詳細については、[セマンティック モデル](../work-with-semantics.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="aaa7e-215"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> を使用して、ローカル宣言ステートメントでデータ フロー分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="aaa7e-216">次に、このデータ フロー分析の結果を使用して、ローカル変数が他の場所の新しい値で上書きされないようにします。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="aaa7e-217">変数の <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> 拡張メソッドを呼び出して変数の <xref:Microsoft.CodeAnalysis.ILocalSymbol> を取得し、データ フロー分析の <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> コレクションに含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="aaa7e-218">`AnalyzeNode` メソッドの末尾に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
VariableDeclaratorSyntax variable = localDeclaration.Declaration.Variables.Single();
ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="aaa7e-219">この追加したコードで、変数は変更されなくなります。そのため、`const` にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="aaa7e-220">それでは診断を呼び出してみましょう。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="aaa7e-221">`AnalyzeNode` の最後の行に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

[!code-csharp[Call ReportDiagnostic](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#ReportDiagnostic  "Call ReportDiagnostic")]

<span data-ttu-id="aaa7e-222"><kbd>F5</kbd> キーを押してアナライザーを実行して、進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-222">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="aaa7e-223">以前に作成したコンソール アプリケーションを読み込み、次のテスト コードを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="aaa7e-224">電球が表示され、アナライザーから診断が報告されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="aaa7e-225">ただし、電球には、テンプレートで生成されたコード修正が使用されているので、大文字にすることができることがわかります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="aaa7e-226">次のセクションでは、コード修正の記述方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="aaa7e-227">コード修正を記述する</span><span class="sxs-lookup"><span data-stu-id="aaa7e-227">Write the code fix</span></span>

<span data-ttu-id="aaa7e-228">アナライザーで、1 つまたは複数のコード修正が表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="aaa7e-229">コード修正では、報告された問題を解決する編集が定義されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="aaa7e-230">作成したアナライザーに、const キーワードを挿入するコード修正を用意することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```diff
- int x = 0;
+ const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="aaa7e-231">エディターの電球の UI からユーザーが選択すると、Visual Studio によってコードが変更されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="aaa7e-232">*CodeFixResources.resx* ファイルを開き、`CodeFixTitle` を :::no-loc text="Make constant"::: に変更します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-232">Open *CodeFixResources.resx* file and change `CodeFixTitle` to ":::no-loc text="Make constant":::".</span></span>

<span data-ttu-id="aaa7e-233">テンプレートによって追加された *MakeConstCodeFixProvider.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-233">Open the *MakeConstCodeFixProvider.cs* file added by the template.</span></span> <span data-ttu-id="aaa7e-234">このコード修正は、診断アナライザーによって生成された診断 ID に既に関連付けられていますが、まだ適切なコード変換が実装されていません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-234">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span>

<span data-ttu-id="aaa7e-235">次に `MakeUppercaseAsync` メソッドを削除します</span><span class="sxs-lookup"><span data-stu-id="aaa7e-235">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="aaa7e-236">これで適用されなくなります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-236">It no longer applies.</span></span>

<span data-ttu-id="aaa7e-237">すべてのコード修正プロバイダーは <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> から派生します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-237">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="aaa7e-238">これらはすべて <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> をオーバーライドし、使用できるコード修正を報告します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-238">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="aaa7e-239">`RegisterCodeFixesAsync` で、診断に合わせて、次のように検索している先祖ノードの種類を <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> に変更します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-239">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="aaa7e-240">次に、最後の行を変更してコード修正を登録します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-240">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="aaa7e-241">この修正で、既存の宣言に `const` 修飾子を追加した結果の新しいドキュメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-241">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="aaa7e-242">シンボル `MakeConstAsync` に追加したコードに、赤い波線が表示されている点に注目してください。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-242">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="aaa7e-243">次のコードのように、`MakeConstAsync` の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-243">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private static async Task<Document> MakeConstAsync(Document document,
    LocalDeclarationStatementSyntax localDeclaration,
    CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="aaa7e-244">新しい `MakeConstAsync` メソッドによって、ユーザーのソース ファイルを表す <xref:Microsoft.CodeAnalysis.Document> は、`const` 宣言を含む新しい <xref:Microsoft.CodeAnalysis.Document> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-244">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="aaa7e-245">宣言ステートメントの前に挿入される新しい `const` キーワード トークンを作成します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-245">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="aaa7e-246">先頭に trivia があれば、まず宣言ステートメントの最初のトークンから削除し、それを `const` トークンにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-246">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="aaa7e-247">`MakeConstAsync` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-247">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="aaa7e-248">次に、以下のコードを使用して宣言に `const` トークンを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-248">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
SyntaxTokenList newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
LocalDeclarationStatementSyntax newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="aaa7e-249">次に、C# の書式設定規則に合わせて新しい宣言の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-249">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="aaa7e-250">既存のコードに合わせて変更の書式を設定すると、エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-250">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="aaa7e-251">既存のコードの直後に次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-251">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="aaa7e-252">このコード用に新しい名前空間が必要です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-252">A new namespace is required for this code.</span></span> <span data-ttu-id="aaa7e-253">次の `using` ディレクティブをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-253">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="aaa7e-254">最後の手順は編集です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-254">The final step is to make your edit.</span></span> <span data-ttu-id="aaa7e-255">このプロセスには 3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-255">There are three steps to this process:</span></span>

1. <span data-ttu-id="aaa7e-256">既存のドキュメントのハンドルを取得する。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-256">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="aaa7e-257">既存の宣言を新しい宣言で置き換えて、新しいドキュメントを作成する。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-257">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="aaa7e-258">新しいドキュメントを返す。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-258">Return the new document.</span></span>

<span data-ttu-id="aaa7e-259">`MakeConstAsync` メソッドの末尾に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-259">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="aaa7e-260">コード修正を試す準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-260">Your code fix is ready to try.</span></span>  <span data-ttu-id="aaa7e-261"><kbd>F5</kbd> キーを押して、Visual Studio の 2 つ目のインスタンスでアナライザー プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-261">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="aaa7e-262">2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成し、定数値を使用して初期化されたローカル変数宣言をいくつか Main メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-262">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="aaa7e-263">次のように警告として報告されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-263">You'll see that they are reported as warnings as below.</span></span>

![const 警告を生成できる](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="aaa7e-265">ここでは、さまざまな作業を行いました。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-265">You've made a lot of progress.</span></span> <span data-ttu-id="aaa7e-266">`const` にすることができる宣言には、波線が表示されています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-266">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="aaa7e-267">ただし、まだするべきことがあります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-267">But there is still work to do.</span></span> <span data-ttu-id="aaa7e-268">これは、`i` で始まる宣言に `const` を追加し、次に `j` を追加し、最後に `k` を追加して改善することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-268">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="aaa7e-269">ただし、`k` で始まる `const` 修飾子を異なる順序で追加すると、アナライザーによってエラーが生成されます。`i` と `j` の両方が既に `const` でなければ、`k` を `const` と宣言できません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-269">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="aaa7e-270">変数を宣言して初期化できるさまざまな方法を確実に処理できるように、さらに分析を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-270">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-unit-tests"></a><span data-ttu-id="aaa7e-271">単体テストをビルドする</span><span class="sxs-lookup"><span data-stu-id="aaa7e-271">Build unit tests</span></span>

<span data-ttu-id="aaa7e-272">アナライザーとコード修正は、const にすることができる単一の宣言という単純なケースで動作します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-272">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="aaa7e-273">この実装によって間違いが発生する可能性のある宣言ステートメントは数多くあります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-273">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="aaa7e-274">このようなケースには、テンプレートによって作成される単体テスト ライブラリを使用して対処します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-274">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="aaa7e-275">これは、Visual Studio の 2 つ目のコピーを繰り返し開くよりもはるかに高速です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-275">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="aaa7e-276">単体テスト プロジェクトで *MakeConstUnitTests.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-276">Open the *MakeConstUnitTests.cs* file in the unit test project.</span></span> <span data-ttu-id="aaa7e-277">テンプレートによって、アナライザーとコード修正の単体テスト用に 2 つの共通パターンに従う 2 つのテストが作成されています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-277">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="aaa7e-278">`TestMethod1` は、診断を報告すべきではないときに、アナライザーから診断が報告されないようにするテストのパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-278">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="aaa7e-279">`TestMethod2` は、診断を報告し、コード修正を実行するためのパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-279">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="aaa7e-280">このテンプレートは、単体テストのために、[Microsoft.CodeAnalysis.Testing](https://github.com/dotnet/roslyn-sdk/blob/main/src/Microsoft.CodeAnalysis.Testing/README.md) パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-280">The template uses [Microsoft.CodeAnalysis.Testing](https://github.com/dotnet/roslyn-sdk/blob/main/src/Microsoft.CodeAnalysis.Testing/README.md) packages for unit testing.</span></span>

> [!TIP]
> <span data-ttu-id="aaa7e-281">テスト ライブラリでは、次のような特殊なマークアップ構文がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-281">The testing library supports a special markup syntax, including the following:</span></span>
>
> - <span data-ttu-id="aaa7e-282">`[|text|]`: 診断が `text` に報告されることを示します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-282">`[|text|]`: indicates that a diagnostic is reported for `text`.</span></span> <span data-ttu-id="aaa7e-283">既定では、このフォームは、`DiagnosticAnalyzer.SupportedDiagnostics` によって提供される `DiagnosticDescriptor` が 1 つだけのアナライザーのテストにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-283">By default, this form may only be used for testing analyzers with exactly one `DiagnosticDescriptor` provided by `DiagnosticAnalyzer.SupportedDiagnostics`.</span></span>
> - <span data-ttu-id="aaa7e-284">`{|ExpectedDiagnosticId:text|}`: <xref:Microsoft.CodeAnalysis.Diagnostic.Id> `ExpectedDiagnosticId` を使用した診断が `text` に報告されることを示します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-284">`{|ExpectedDiagnosticId:text|}`: indicates that a diagnostic with <xref:Microsoft.CodeAnalysis.Diagnostic.Id> `ExpectedDiagnosticId` is reported for `text`.</span></span>

<span data-ttu-id="aaa7e-285">`MakeConstUnitTest` クラスのテンプレート テストを次のテスト メソッドに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-285">Replace the template tests in the `MakeConstUnitTest` class with the following test method:</span></span>

[!code-csharp[test method for fix test](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "test method for fix test")]

<span data-ttu-id="aaa7e-286">このテストを実行して、合格したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-286">Run this test to make sure it passes.</span></span> <span data-ttu-id="aaa7e-287">Visual Studio で、 **[テスト]**  >  **[Windows]**  >  **[テスト エクスプローラー]** の順に選択して、**テスト エクスプローラー** を開きます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-287">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="aaa7e-288">その後、 **[すべて実行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-288">Then select **Run All**.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="aaa7e-289">有効な宣言のテストを作成する</span><span class="sxs-lookup"><span data-stu-id="aaa7e-289">Create tests for valid declarations</span></span>

<span data-ttu-id="aaa7e-290">一般的な規則として、アナライザーはできるだけ早く終了し、最低限の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-290">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="aaa7e-291">ユーザーがコードを編集すると、Visual Studio では登録済みのアナライザーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-291">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="aaa7e-292">応答性は重要な要件です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-292">Responsiveness is a key requirement.</span></span> <span data-ttu-id="aaa7e-293">診断を呼び出すべきではないコードのテストケースがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-293">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="aaa7e-294">このアナライザーは、このようなテストのうち、初期化後に変数が割り当てられるケースのテストを既に処理しています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-294">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="aaa7e-295">そのケースを表すために、次のテスト メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-295">Add the following test method to represent that case:</span></span>

[!code-csharp[variable assigned](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="aaa7e-296">このテストも合格します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-296">This test passes as well.</span></span> <span data-ttu-id="aaa7e-297">次に、まだ処理していない条件のテスト メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-297">Next, add test methods for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="aaa7e-298">既に const なので、既に `const` である宣言:</span><span class="sxs-lookup"><span data-stu-id="aaa7e-298">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="aaa7e-299">使用する価値がないため、初期化子がない宣言:</span><span class="sxs-lookup"><span data-stu-id="aaa7e-299">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="aaa7e-300">コンパイル時の定数にすることはできないため、初期化子が定数ではない宣言:</span><span class="sxs-lookup"><span data-stu-id="aaa7e-300">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="aaa7e-301">C# は複数の宣言を 1 つのステートメントとして許可するので、さらに複雑になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-301">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="aaa7e-302">次のテスト ケース文字列定数を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-302">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="aaa7e-303">変数 `i` は定数にすることができますが、変数 `j` はできません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-303">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="aaa7e-304">そのため、このステートメントを const 宣言にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-304">Therefore, this statement cannot be made a const declaration.</span></span>

<span data-ttu-id="aaa7e-305">テストをもう一度実行すると、これらの新しいテスト ケースが失敗することがわかります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-305">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="aaa7e-306">正しい宣言を無視するようにアナライザーを更新する</span><span class="sxs-lookup"><span data-stu-id="aaa7e-306">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="aaa7e-307">アナライザーの `AnalyzeNode` メソッドにいくつか拡張を追加して、これらの条件に一致するコードをフィルター処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-307">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="aaa7e-308">これらはすべて関連する条件なので、同様の変更でこれらすべての条件を修正します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-308">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="aaa7e-309">`AnalyzeNode` に次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-309">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="aaa7e-310">セマンティック分析では、単一の変数宣言を調査しました。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-310">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="aaa7e-311">このコードは、同じステートメントで宣言されたすべての変数を調査する `foreach` ループ内に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-311">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="aaa7e-312">宣言された各変数には初期化子が必要です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-312">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="aaa7e-313">宣言された各変数の初期化子は、コンパイル時定数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-313">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="aaa7e-314">`AnalyzeNode` メソッドで、元のセマンティック分析を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-314">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
VariableDeclaratorSyntax variable = localDeclaration.Declaration.Variables.Single();
ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="aaa7e-315">次のコード スニペットのようにします。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-315">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (VariableDeclaratorSyntax variable in localDeclaration.Declaration.Variables)
{
    EqualsValueClauseSyntax initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    Optional<object> constantValue = context.SemanticModel.GetConstantValue(initializer.Value, context.CancellationToken);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (VariableDeclaratorSyntax variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="aaa7e-316">最初の `foreach` ループで、構文解析を使用して各変数宣言を調査します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-316">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="aaa7e-317">最初の検査で、変数に初期化子があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-317">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="aaa7e-318">2 つ目の検査で、初期化子が定数であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-318">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="aaa7e-319">2 つ目のループには、元のセマンティック分析があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-319">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="aaa7e-320">セマンティック検査は、パフォーマンスに大きな影響があるため、別のループに配置されています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-320">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="aaa7e-321">テストをもう一度実行すると、すべてが合格になるはずです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-321">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="aaa7e-322">最後の仕上げを加える</span><span class="sxs-lookup"><span data-stu-id="aaa7e-322">Add the final polish</span></span>

<span data-ttu-id="aaa7e-323">完了までもう少しです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-323">You're almost done.</span></span> <span data-ttu-id="aaa7e-324">アナライザーが処理できる条件がまだいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-324">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="aaa7e-325">Visual Studio では、ユーザーがコードを記述しているときにアナライザーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-325">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="aaa7e-326">コンパイルされないコードに対してアナライザーが呼び出されることはよくあります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-326">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="aaa7e-327">診断アナライザーの `AnalyzeNode` メソッドは、定数値を変数型に変換できるかどうかを検査しません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-327">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="aaa7e-328">そのため、現在の実装では、int i = "abc" のような正しくない宣言でもそのままローカル定数に変換されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-328">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="aaa7e-329">この場合は、テスト メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-329">Add a test method for this case:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="aaa7e-330">また、参照型が正しく処理されません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-330">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="aaa7e-331">参照型に使用できる唯一の定数値は、文字列リテラルを許可する <xref:System.String?displayProperty=nameWithType> の場合を除き、`null` です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-331">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="aaa7e-332">つまり、`const string s = "abc"` は有効ですが、`const object s = "abc"` は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-332">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="aaa7e-333">このコード スニペットで、次の条件を検証します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-333">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="aaa7e-334">さらに徹底するには、文字列の定数宣言を作成できるように別のテストを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-334">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="aaa7e-335">次のスニペットでは、診断を呼び出すコードと、修正が適用された後のコードの両方を定義しています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-335">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="aaa7e-336">最後に、変数が `var` キーワードで宣言されている場合、コード修正で適切な処理が実行されず、C# 言語でサポートされていない `const var` 宣言が生成されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-336">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="aaa7e-337">このバグを修正するには、コード修正で `var` キーワードを推定型の名前に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-337">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="aaa7e-338">幸いにも、上記のすべてのバグは、ここで学んだテクニックを使って解決できます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-338">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="aaa7e-339">最初のバグを修正するには、まず *MakeConstAnalyzer.cs* を開き、各ローカル宣言の初期化子が検査される foreach ループを見つけて、それらに定数値が割り当てられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-339">To fix the first bug, first open *MakeConstAnalyzer.cs* and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="aaa7e-340">最初の foreach ループの _直前_ に `context.SemanticModel.GetTypeInfo()` を呼び出し、宣言されたローカル宣言の型に関する詳細情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-340">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

[!code-csharp[Retrieve type information](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#VariableConvertedType "Retrieve type information")]

<span data-ttu-id="aaa7e-341">次に、`foreach` ループ内に、各初期化子が変数型に変換できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-341">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="aaa7e-342">初期化子が定数であることを確認したら、次の検査を追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-342">Add the following check after ensuring that the initializer is a constant:</span></span>

[!code-csharp[Ensure non-user-defined conversion](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#BailOutOnUserDefinedConversion "Bail-out on user-defined conversion")]

<span data-ttu-id="aaa7e-343">次の変更は、最後の変更に基づいています。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-343">The next change builds upon the last one.</span></span> <span data-ttu-id="aaa7e-344">最初の foreach ループの中かっこの前に、定数が文字列または null の場合にローカル宣言の型を検査する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-344">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

[!code-csharp[Handle special cases](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#HandleSpecialCases "Handle special cases")]

<span data-ttu-id="aaa7e-345">`var` キーワードを正しい型名に置き換えるには、コード修正プロバイダーに少しコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-345">You must write a bit more code in your code fix provider to replace the `var` keyword with the correct type name.</span></span> <span data-ttu-id="aaa7e-346">*MakeConstCodeFixProvider.cs* に戻ります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-346">Return to *MakeConstCodeFixProvider.cs*.</span></span> <span data-ttu-id="aaa7e-347">追加するコードで、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-347">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="aaa7e-348">宣言が `var` 宣言かどうかを検査し、その場合は次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-348">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="aaa7e-349">推定型の新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-349">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="aaa7e-350">型宣言がエイリアスでないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-350">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="aaa7e-351">その場合は、`const var` を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-351">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="aaa7e-352">`var` がこのプログラムの型名でないことを確認します</span><span class="sxs-lookup"><span data-stu-id="aaa7e-352">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="aaa7e-353">(その場合、`const var` は有効です)。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-353">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="aaa7e-354">完全な型名を簡略化する</span><span class="sxs-lookup"><span data-stu-id="aaa7e-354">Simplify the full type name</span></span>

<span data-ttu-id="aaa7e-355">多数のコードが必要なようですが、</span><span class="sxs-lookup"><span data-stu-id="aaa7e-355">That sounds like a lot of code.</span></span> <span data-ttu-id="aaa7e-356">そうではありません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-356">It's not.</span></span> <span data-ttu-id="aaa7e-357">`newLocal` を宣言し、初期化する行を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-357">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="aaa7e-358">`newModifiers` の初期化直後に配置します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-358">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="aaa7e-359"><xref:Microsoft.CodeAnalysis.Simplification.Simplifier> 型を使用するには、1 つの `using` ディレクティブを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-359">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="aaa7e-360">テストを実行します。テストはすべて合格するはずです。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-360">Run your tests, and they should all pass.</span></span> <span data-ttu-id="aaa7e-361">完成したアナライザーを実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-361">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="aaa7e-362"><kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを押して、Roslyn Preview 拡張機能が読み込まれた Visual Studio の 2 つ目のインスタンスでアナライザー プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-362">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="aaa7e-363">2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成し、`int x = "abc";` を Main メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-363">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="aaa7e-364">最初のバグ修正のおかげで、このローカル変数宣言について警告は報告されません (ただし、想定どおりコンパイラ エラーが発生します)。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-364">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="aaa7e-365">次に、Main メソッドに `object s = "abc";` を追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-365">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="aaa7e-366">2 つ目のバグ修正のおかげで、警告は報告されません。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-366">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="aaa7e-367">最後に、`var` キーワードを使用する別のローカル変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-367">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="aaa7e-368">警告が報告され、左側の下部に推奨が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-368">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="aaa7e-369">波線にエディターのカレットを移動し、<kbd>Ctrl</kbd> + <kbd>.</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-369">Move the editor caret over the squiggly underline and press <kbd>Ctrl</kbd>+<kbd>.</kbd>.</span></span> <span data-ttu-id="aaa7e-370">推奨されたコード修正が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-370">to display the suggested code fix.</span></span> <span data-ttu-id="aaa7e-371">コード修正を選択して、`var` キーワードが正しく処理されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-371">Upon selecting your code fix, note that the `var` keyword is now handled correctly.</span></span>

<span data-ttu-id="aaa7e-372">最後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-372">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="aaa7e-373">これらの変更の後は、最初の 2 つの変数にのみ赤い波線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-373">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="aaa7e-374">`i` と `j` の両方に `const` を追加すると、`const` になる可能性があるので、`k` で新しい警告を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-374">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="aaa7e-375">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="aaa7e-375">Congratulations!</span></span> <span data-ttu-id="aaa7e-376">ここでは最初の .NET Compiler Platform 拡張機能を作成しました。これは、その場でコード分析を実行し、問題を検出してそれを修正する簡単な修正案を提供する拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-376">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="aaa7e-377">この過程で、.NET Compiler Platform SDK (Roslyn API) に含まれる多くのコード API を学びました。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-377">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="aaa7e-378">サンプル GitHub リポジトリの[完成したサンプル](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/Tutorials/MakeConst)に対して作業を検査することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa7e-378">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="aaa7e-379">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="aaa7e-379">Other resources</span></span>

- [<span data-ttu-id="aaa7e-380">構文解析の概要</span><span class="sxs-lookup"><span data-stu-id="aaa7e-380">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="aaa7e-381">セマンティック解析の概要</span><span class="sxs-lookup"><span data-stu-id="aaa7e-381">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
