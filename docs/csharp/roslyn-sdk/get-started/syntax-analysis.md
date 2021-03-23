---
title: 構文解析の概要 (Roslyn API)
description: 構文ツリーの走査、クエリおよびウォークに関する概要。
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 7fea6145ed927ed197295b08ab35dbf177920061
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872510"
---
# <a name="get-started-with-syntax-analysis"></a><span data-ttu-id="0c109-103">構文解析の概要</span><span class="sxs-lookup"><span data-stu-id="0c109-103">Get started with syntax analysis</span></span>

<span data-ttu-id="0c109-104">このチュートリアルでは、**Syntax API** について学習します。</span><span class="sxs-lookup"><span data-stu-id="0c109-104">In this tutorial, you'll explore the **Syntax API**.</span></span> <span data-ttu-id="0c109-105">Syntax API では、C# または Visual Basic プログラムを記述するデータ構造へのアクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-105">The Syntax API provides access to the data structures that describe a C# or Visual Basic program.</span></span> <span data-ttu-id="0c109-106">これらのデータ構造には、あらゆるサイズのあらゆるプログラムを完全に表すことができる十分な情報があります。</span><span class="sxs-lookup"><span data-stu-id="0c109-106">These data structures have enough detail that they can fully represent any program of any size.</span></span> <span data-ttu-id="0c109-107">これらの構造では、正しくコンパイルして実行される完全なプログラムを記述できます。</span><span class="sxs-lookup"><span data-stu-id="0c109-107">These structures can describe complete programs that compile and run correctly.</span></span> <span data-ttu-id="0c109-108">エディターでは、書き込み時に、不完全なプログラムを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c109-108">They can also describe incomplete programs, as you write them, in the editor.</span></span>

<span data-ttu-id="0c109-109">この優れた式を有効にする場合、Syntax API を構成する API とデータ構造が必然的に複雑になります。</span><span class="sxs-lookup"><span data-stu-id="0c109-109">To enable this rich expression, the data structures and APIs that make up the Syntax API are necessarily complex.</span></span> <span data-ttu-id="0c109-110">まずは、一般的な "Hello World" プログラムのデータ構造がどのようになるかを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="0c109-110">Let's start with what the data structure looks like for the typical "Hello World" program:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="0c109-111">上のプログラムのテキストを見てください。</span><span class="sxs-lookup"><span data-stu-id="0c109-111">Look at the text of the previous program.</span></span> <span data-ttu-id="0c109-112">使い慣れた要素であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0c109-112">You recognize familiar elements.</span></span> <span data-ttu-id="0c109-113">テキスト全体は単一のソース ファイル (**コンパイル ユニット**) を表しています。</span><span class="sxs-lookup"><span data-stu-id="0c109-113">The entire text represents a single source file, or a **compilation unit**.</span></span> <span data-ttu-id="0c109-114">そのソース ファイルの最初の 3 行は **using ディレクティブ** です。</span><span class="sxs-lookup"><span data-stu-id="0c109-114">The first three lines of that source file are **using directives**.</span></span> <span data-ttu-id="0c109-115">残りのソースは **名前空間宣言** に含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c109-115">The remaining source is contained in a **namespace declaration**.</span></span> <span data-ttu-id="0c109-116">名前空間宣言には子 **クラス宣言** が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c109-116">The namespace declaration contains a child **class declaration**.</span></span> <span data-ttu-id="0c109-117">クラス宣言には 1 つの **メソッド宣言** が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c109-117">The class declaration contains one **method declaration**.</span></span>

<span data-ttu-id="0c109-118">Syntax API では、コンパイル ユニットを表すルートを含むツリー構造が作成されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-118">The Syntax API creates a tree structure with the root representing the compilation unit.</span></span> <span data-ttu-id="0c109-119">ツリー内のノードは、using ディレクティブ、名前空間宣言およびプログラムの他のすべての要素を表しています。</span><span class="sxs-lookup"><span data-stu-id="0c109-119">Nodes in the tree represent the using directives, namespace declaration and all the other elements of the program.</span></span> <span data-ttu-id="0c109-120">ツリー構造は最下位レベルまで続きます。文字列 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="0c109-120">The tree structure continues down to the lowest levels: the string "Hello World!"</span></span> <span data-ttu-id="0c109-121">は、**引数** の子孫である **文字列リテラル トークン** です。</span><span class="sxs-lookup"><span data-stu-id="0c109-121">is a **string literal token** that is a descendent of an **argument**.</span></span> <span data-ttu-id="0c109-122">Syntax API では、プログラムの構造体へのアクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-122">The Syntax API provides access to the structure of the program.</span></span> <span data-ttu-id="0c109-123">特定のコード プラクティスに対してクエリを実行し、ツリー全体をウォークしてコードを理解し、既存のツリーを変更して新しいツリーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-123">You can query for specific code practices, walk the entire tree to understand the code, and create new trees by modifying the existing tree.</span></span>

<span data-ttu-id="0c109-124">その簡単な説明では、Syntax API を使用してアクセスできる情報の種類の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-124">That brief description provides an overview of the kind of information accessible using the Syntax API.</span></span> <span data-ttu-id="0c109-125">Syntax API は、C# の使い慣れたコード コンストラクトを記述する正式な API にすぎません。</span><span class="sxs-lookup"><span data-stu-id="0c109-125">The Syntax API is nothing more than a formal API that describes the familiar code constructs you know from C#.</span></span> <span data-ttu-id="0c109-126">完全な機能には、改行、空白、インデントを含め、コードの書式設定方法に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c109-126">The full capabilities include information about how the code is formatted including line breaks, white space, and indenting.</span></span> <span data-ttu-id="0c109-127">この情報を使用して、人間のプログラマまたはコンパイラによって書き込まれ、読み取られるコードを完全に表すことができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-127">Using this information, you can fully represent the code as written and read by human programmers or the compiler.</span></span> <span data-ttu-id="0c109-128">この構造を使用することで、深い意味のあるレベルのソース コードと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-128">Using this structure enables you to interact with the source code on a deeply meaningful level.</span></span> <span data-ttu-id="0c109-129">テキスト文字列はもう存在しませんが、C# プログラムの構造を表すデータはあります。</span><span class="sxs-lookup"><span data-stu-id="0c109-129">It's no longer text strings, but data that represents the structure of a C# program.</span></span>

<span data-ttu-id="0c109-130">まず **.NET Compiler Platform SDK** をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c109-130">To get started, you'll need to install the **.NET Compiler Platform SDK**:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a><span data-ttu-id="0c109-131">構文ツリーについて</span><span class="sxs-lookup"><span data-stu-id="0c109-131">Understanding syntax trees</span></span>

<span data-ttu-id="0c109-132">C# コードの構造の分析には Syntax API を使用します。</span><span class="sxs-lookup"><span data-stu-id="0c109-132">You use the Syntax API for any analysis of the structure of C# code.</span></span> <span data-ttu-id="0c109-133">**Syntax API** では、パーサー、構文ツリー、および構文ツリーを分析して構築するためのユーティリティを公開します。</span><span class="sxs-lookup"><span data-stu-id="0c109-133">The **Syntax API** exposes the parsers, the syntax trees, and utilities for analyzing and constructing syntax trees.</span></span> <span data-ttu-id="0c109-134">これを使用して、特定の構文要素のコードの検索またはプログラムのコードの読み取りを行います。</span><span class="sxs-lookup"><span data-stu-id="0c109-134">It's how you search code for specific syntax elements or read the code for a program.</span></span>

<span data-ttu-id="0c109-135">構文ツリーは、C# および Visual Basic プログラムを理解するために C# および Visual Basic コンパイラで使用されるデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="0c109-135">A syntax tree is a data structure used by the C# and Visual Basic compilers to understand C# and Visual Basic programs.</span></span> <span data-ttu-id="0c109-136">構文ツリーは、プロジェクトのビルド時、または開発者が F5 キーを押したときに実行されるのと同じパーサーによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-136">Syntax trees are produced by the same parser that runs when a project is built or a developer hits F5.</span></span> <span data-ttu-id="0c109-137">構文ツリーは言語に対して完全に忠実であり、コード ファイル内のすべての情報はツリーで表されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-137">The syntax trees have full-fidelity with the language; every bit of information in a code file is represented in the tree.</span></span> <span data-ttu-id="0c109-138">構文ツリーをテキストに書き込むことで、解析された元の正確なテキストが再現されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-138">Writing a syntax tree to text reproduces the exact original text that was parsed.</span></span> <span data-ttu-id="0c109-139">構文ツリーは **不変** でもあります。構文ツリーを作成した後で変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="0c109-139">The syntax trees are also **immutable**; once created a syntax tree can never be changed.</span></span> <span data-ttu-id="0c109-140">ツリーのコンシューマーは、データが変更されないことを認識したうえで、ロックやその他のコンカレンシー手段を使用せずに、複数のスレッドでツリーを分析できます。</span><span class="sxs-lookup"><span data-stu-id="0c109-140">Consumers of the trees can analyze the trees on multiple threads, without locks or other concurrency measures, knowing the data never changes.</span></span> <span data-ttu-id="0c109-141">API を使用して、新しいツリーを作成することができます。その場合、既存のツリーを変更します。</span><span class="sxs-lookup"><span data-stu-id="0c109-141">You can use APIs to create new trees that are the result of modifying an existing tree.</span></span>

<span data-ttu-id="0c109-142">構文ツリーの 4 つの基本的な構成要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0c109-142">The four primary building blocks of syntax trees are:</span></span>

* <span data-ttu-id="0c109-143"><xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> クラス。インスタンスで解析ツリー全体を表します。</span><span class="sxs-lookup"><span data-stu-id="0c109-143">The <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> class, an instance of which represents an entire parse tree.</span></span> <span data-ttu-id="0c109-144"><xref:Microsoft.CodeAnalysis.SyntaxTree> は、言語固有の派生物を持つ抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="0c109-144"><xref:Microsoft.CodeAnalysis.SyntaxTree> is an abstract class that has language-specific derivatives.</span></span> <span data-ttu-id="0c109-145"><xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (または <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) クラスの解析メソッドを使用して、C# (または Visual Basic) のテキストを解析します。</span><span class="sxs-lookup"><span data-stu-id="0c109-145">You use the parse methods of the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (or <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) class to parse text in C# (or Visual Basic).</span></span>
* <span data-ttu-id="0c109-146"><xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> クラス。インスタンスで、宣言、ステートメント、句、および式などの構文構造を表します。</span><span class="sxs-lookup"><span data-stu-id="0c109-146">The <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> class, instances of which represent syntactic constructs such as declarations, statements, clauses, and expressions.</span></span>
* <span data-ttu-id="0c109-147"><xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> 構造。個々のキーワード、ID、演算子、または句読点を表します。</span><span class="sxs-lookup"><span data-stu-id="0c109-147">The <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> structure, which represents an individual keyword, identifier, operator, or punctuation.</span></span>
* <span data-ttu-id="0c109-148">最後は <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> 構造です。これは、トークン、プリプロセス ディレクティブ、およびコメントの間の空白など、重要でない情報を構文的に表します。</span><span class="sxs-lookup"><span data-stu-id="0c109-148">And lastly the <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> structure, which represents syntactically insignificant bits of information such as the white space between tokens, preprocessing directives, and comments.</span></span>

<span data-ttu-id="0c109-149">トリビア、トークン、およびノードは、Visual Basic または C# コードのフラグメント内のすべてを完全に表すツリーを形成するために階層的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-149">Trivia, tokens, and nodes are composed hierarchically to form a tree that completely represents everything in a fragment of Visual Basic or C# code.</span></span> <span data-ttu-id="0c109-150">この構造は、**Syntax Visualizer** ウィンドウを使用して確認することができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-150">You can see this structure using the **Syntax Visualizer** window.</span></span> <span data-ttu-id="0c109-151">Visual Studio で、 **[ビュー]**  >  **[その他のウィンドウ]**  >  **[Syntax Visualizer]\(Syntax Visualizer\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="0c109-151">In Visual Studio, choose **View** > **Other Windows** > **Syntax Visualizer**.</span></span> <span data-ttu-id="0c109-152">たとえば、**Syntax Visualizer** を使用して調べた上記の C# ソース ファイルは、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="0c109-152">For example, the preceding C# source file examined using the **Syntax Visualizer** looks like the following figure:</span></span>

<span data-ttu-id="0c109-153">**SyntaxNode**: 青 | **SyntaxToken**: 緑 | **SyntaxTrivia**: 赤 ![C# コード ファイル](media/walkthrough-csharp-syntax-figure1.png)</span><span class="sxs-lookup"><span data-stu-id="0c109-153">**SyntaxNode**: Blue | **SyntaxToken**: Green | **SyntaxTrivia**: Red ![C# Code File](media/walkthrough-csharp-syntax-figure1.png)</span></span>

<span data-ttu-id="0c109-154">このツリー構造を移動することで、ステートメント、式、トークン、またはコード ファイルのわずかな空白を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-154">By navigating this tree structure, you can find any statement, expression, token, or bit of white space in a code file.</span></span>

<span data-ttu-id="0c109-155">Syntax API を使用してコード ファイルで何でも見つけることはできますが、ほとんどのシナリオでは、コードの小さなスニペットの確認や、特定のステートメントまたはフラグメントの検索が必要です。</span><span class="sxs-lookup"><span data-stu-id="0c109-155">While you can find anything in a code file using the Syntax APIs, most scenarios involve examining small snippets of code, or searching for particular statements or fragments.</span></span> <span data-ttu-id="0c109-156">以下の 2 つの例では、コードの構造の参照、または単一ステートメントの検索を行う場合の一般的な使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-156">The two examples that follow show typical uses to browse the structure of code, or search for single statements.</span></span>

## <a name="traversing-trees"></a><span data-ttu-id="0c109-157">ツリーの走査</span><span class="sxs-lookup"><span data-stu-id="0c109-157">Traversing trees</span></span>

<span data-ttu-id="0c109-158">2 つの方法で構文ツリー内のノードを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-158">You can examine the nodes in a syntax tree in two ways.</span></span> <span data-ttu-id="0c109-159">ツリーを走査して、各ノードを調べることができます。あるいは、特定の要素やノードに対してクエリを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-159">You can traverse the tree to examine each node, or you can query for specific elements or nodes.</span></span>

### <a name="manual-traversal"></a><span data-ttu-id="0c109-160">手動による走査</span><span class="sxs-lookup"><span data-stu-id="0c109-160">Manual traversal</span></span>

<span data-ttu-id="0c109-161">このサンプルの完成したコードは、[GitHub のリポジトリ](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SyntaxQuickStart)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="0c109-161">You can see the finished code for this sample in [our GitHub repository](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SyntaxQuickStart).</span></span>

> [!NOTE]
> <span data-ttu-id="0c109-162">構文ツリー型では継承を使用して、プログラムのさまざまな場所で有効なさまざまな構文要素を記述します。</span><span class="sxs-lookup"><span data-stu-id="0c109-162">The Syntax Tree types use inheritance to describe the different syntax elements that are valid at different locations in the program.</span></span> <span data-ttu-id="0c109-163">これらの API を使用することは、多くの場合、特定の派生型にプロパティまたはコレクション メンバーをキャストすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0c109-163">Using these APIs often means casting properties or collection members to specific derived types.</span></span> <span data-ttu-id="0c109-164">次の例では、割り当てとキャストは別のステートメントであり、明示的に型指定された変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="0c109-164">In the following examples, the assignment and the casts are separate statements, using explicitly typed variables.</span></span> <span data-ttu-id="0c109-165">コードを読み取り、API の戻り値の型と返されるオブジェクトのランタイム型を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-165">You can read the code to see the return types of the API and the runtime type of the objects returned.</span></span> <span data-ttu-id="0c109-166">実際には、暗黙的に型指定された変数を使用して、API 名に依存して、調べられるオブジェクトの型を記述するのがより一般的です。</span><span class="sxs-lookup"><span data-stu-id="0c109-166">In practice, it's more common to use implicitly typed variables and rely on API names to describe the type of objects being examined.</span></span>

<span data-ttu-id="0c109-167">次のようにして、新しい C# の **Stand-Alone Code Analysis Tool** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c109-167">Create a new C# **Stand-Alone Code Analysis Tool** project:</span></span>

* <span data-ttu-id="0c109-168">Visual Studio で、 **[ファイル]**  >  **[新規]**  >  **[プロジェクト]** の順に選択して、[新しいプロジェクト] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-168">In Visual Studio, choose **File** > **New** > **Project** to display the New Project dialog.</span></span>
* <span data-ttu-id="0c109-169">**[Visual C#]**  >  **[機能拡張]** で、 **[Stand-Alone Code Analysis Tool]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c109-169">Under **Visual C#** > **Extensibility**, choose **Stand-Alone Code Analysis Tool**.</span></span>
* <span data-ttu-id="0c109-170">プロジェクトに "**SyntaxTreeManualTraversal**" という名前を付けて、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c109-170">Name your project "**SyntaxTreeManualTraversal**" and click OK.</span></span>

<span data-ttu-id="0c109-171">前述の基本的な "Hello World!" プログラムを</span><span class="sxs-lookup"><span data-stu-id="0c109-171">You're going to analyze the basic "Hello World!"</span></span> <span data-ttu-id="0c109-172">分析します。</span><span class="sxs-lookup"><span data-stu-id="0c109-172">program shown earlier.</span></span>
<span data-ttu-id="0c109-173">Hello World プログラムのテキストを `Program` クラスの定数として追加します。</span><span class="sxs-lookup"><span data-stu-id="0c109-173">Add the text for the Hello World program as a constant in your `Program` class:</span></span>

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

<span data-ttu-id="0c109-174">次に、以下のコードを追加して、`programText` 定数のコード テキストの **構文ツリー** をビルドします。</span><span class="sxs-lookup"><span data-stu-id="0c109-174">Next, add the following code to build the **syntax tree** for the code text in the `programText` constant.</span></span>  <span data-ttu-id="0c109-175">次の行を `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="0c109-175">Add the following line to your `Main` method:</span></span>

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

<span data-ttu-id="0c109-176">これら 2 行でツリーを作成し、そのツリーのルート ノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="0c109-176">Those two lines create the tree and retrieve the root node of that tree.</span></span> <span data-ttu-id="0c109-177">これでツリー内のノードを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-177">You can now examine the nodes in the tree.</span></span> <span data-ttu-id="0c109-178">以下の行を `Main` メソッドに追加して、ツリー内のルート ノードのプロパティをいくつか表示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-178">Add these lines to your `Main` method to display some of the properties of the root node in the tree:</span></span>

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

<span data-ttu-id="0c109-179">アプリケーションを実行して、このツリー内のルート ノードについて、コードで検出された内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="0c109-179">Run the application to see what your code has discovered about the root node in this tree.</span></span>

<span data-ttu-id="0c109-180">通常、コードについて学習する場合、ツリーを走査します。</span><span class="sxs-lookup"><span data-stu-id="0c109-180">Typically, you'd traverse the tree to learn about the code.</span></span> <span data-ttu-id="0c109-181">この例では、使い慣れたコードを分析して、API を調べます。</span><span class="sxs-lookup"><span data-stu-id="0c109-181">In this example, you're analyzing code you know to explore the APIs.</span></span> <span data-ttu-id="0c109-182">次のコードを追加して、`root` ノードの最初のメンバーを調べます。</span><span class="sxs-lookup"><span data-stu-id="0c109-182">Add the following code to examine the first member of the `root` node:</span></span>

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

<span data-ttu-id="0c109-183">そのメンバーは <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="0c109-183">That member is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0c109-184">`namespace HelloWorld` 宣言のスコープ内ですべてを表します。</span><span class="sxs-lookup"><span data-stu-id="0c109-184">It represents everything in the scope of the `namespace HelloWorld` declaration.</span></span> <span data-ttu-id="0c109-185">次のコードを追加して、`HelloWorld` 名前空間内で宣言されているノードを調べます。</span><span class="sxs-lookup"><span data-stu-id="0c109-185">Add the following code to examine what nodes are declared inside the `HelloWorld` namespace:</span></span>

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

<span data-ttu-id="0c109-186">プログラムを実行して、学習した内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="0c109-186">Run the program to see what you've learned.</span></span>

<span data-ttu-id="0c109-187">宣言が <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType> であることがわかったので、その型の新しい変数を宣言して、クラス宣言を調べます。</span><span class="sxs-lookup"><span data-stu-id="0c109-187">Now that you know the declaration is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, declare a new variable of that type to examine the class declaration.</span></span> <span data-ttu-id="0c109-188">このクラスには 1 つのメンバー (`Main` メソッド) のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c109-188">This class only contains one member: the `Main` method.</span></span> <span data-ttu-id="0c109-189">次のコードを追加して `Main` メソッドを見つけ、それを <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType> にキャストします。</span><span class="sxs-lookup"><span data-stu-id="0c109-189">Add the following code to find the `Main` method, and cast it to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.</span></span>

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

<span data-ttu-id="0c109-190">メソッド宣言ノードには、メソッドに関するすべての構文情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c109-190">The method declaration node contains all the syntactic information about the method.</span></span> <span data-ttu-id="0c109-191">次は、`Main` メソッドの戻り値の型、引数の数と型、およびメソッドの本文を表示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-191">Let's display the return type of the `Main` method, the number and types of the arguments, and the body text of the method.</span></span> <span data-ttu-id="0c109-192">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0c109-192">Add the following code:</span></span>

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

<span data-ttu-id="0c109-193">プログラムを実行して、このプログラムについて検出したすべての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-193">Run the program to see all the information you've discovered about this program:</span></span>

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration.
There are 1 members declared in this namespace.
The first member is a ClassDeclaration.
There are 1 members declared in the Program class.
The first member is a MethodDeclaration.
The return type of the Main method is void.
The method has 1 parameters.
The type of the args parameter is string[].
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a><span data-ttu-id="0c109-194">クエリ メソッド</span><span class="sxs-lookup"><span data-stu-id="0c109-194">Query methods</span></span>

<span data-ttu-id="0c109-195">ツリーの走査に加え、<xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> で定義されているクエリ メソッドを使用して、構文ツリーを調べることもできます。</span><span class="sxs-lookup"><span data-stu-id="0c109-195">In addition to traversing trees, you can also explore the syntax tree using the query methods defined on <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0c109-196">XPath を使い慣れていれば、これらのメソッドをすぐに使いこなすことができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-196">These methods should be immediately familiar to anyone familiar with XPath.</span></span> <span data-ttu-id="0c109-197">LINQ でこれらのメソッドを使用することで、ツリー内の内容をすばやく検索できます。</span><span class="sxs-lookup"><span data-stu-id="0c109-197">You can use these methods with LINQ to quickly find things in a tree.</span></span> <span data-ttu-id="0c109-198"><xref:Microsoft.CodeAnalysis.SyntaxNode> には、<xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>、<xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A>、<xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A> などのクエリ メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="0c109-198">The <xref:Microsoft.CodeAnalysis.SyntaxNode> has query methods such as <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> and <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.</span></span>

<span data-ttu-id="0c109-199">これらのクエリ メソッドを使用すれば、ツリーを移動せずに、`Main` メソッドに対する引数を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-199">You can use these query methods to find the argument to the `Main` method as an alternative to navigating the tree.</span></span> <span data-ttu-id="0c109-200">次のコードを `Main` メソッドの下部に追加します。</span><span class="sxs-lookup"><span data-stu-id="0c109-200">Add the following code to the bottom of your `Main` method:</span></span>

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

<span data-ttu-id="0c109-201">最初のステートメントでは LINQ 式と <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> メソッドを使用して、前の例と同じパラメーターを検索します。</span><span class="sxs-lookup"><span data-stu-id="0c109-201">The first statement uses a LINQ expression and the <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> method to locate the same parameter as in the previous example.</span></span>

<span data-ttu-id="0c109-202">プログラムを実行すると、ツリーを手動で移動する場合と同じパラメーターが LINQ 式で検出されたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="0c109-202">Run the program, and you can see that the LINQ expression found the same parameter as manually navigating the tree.</span></span>

<span data-ttu-id="0c109-203">このサンプルでは `WriteLine` ステートメントを使用して、走査された構文ツリーに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-203">The sample uses `WriteLine` statements to display information about the syntax trees as they are traversed.</span></span> <span data-ttu-id="0c109-204">デバッガーで完成したプログラムを実行して、さらに理解を深めることもできます。</span><span class="sxs-lookup"><span data-stu-id="0c109-204">You can also learn much more by running the finished program under the debugger.</span></span> <span data-ttu-id="0c109-205">hello world プログラム用に作成された構文ツリーの一部であるメソッドとプロパティをさらに調べることができます。</span><span class="sxs-lookup"><span data-stu-id="0c109-205">You can examine more of the properties and methods that are part of the syntax tree created for the hello world program.</span></span>

## <a name="syntax-walkers"></a><span data-ttu-id="0c109-206">構文ウォーカー</span><span class="sxs-lookup"><span data-stu-id="0c109-206">Syntax walkers</span></span>

<span data-ttu-id="0c109-207">多くの場合、構文ツリーで特定の型のノード (ファイル内のすべてのプロパティ宣言など) をすべて検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c109-207">Often you want to find all nodes of a specific type in a syntax tree, for example, every property declaration in a file.</span></span> <span data-ttu-id="0c109-208"><xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> クラスを拡張し、<xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> メソッドをオーバーライドして、構造を事前に認識せずに、構文ツリーのすべてのプロパティ宣言を処理します。</span><span class="sxs-lookup"><span data-stu-id="0c109-208">By extending the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> class and overriding the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> method, you process every property declaration in a syntax tree without knowing its structure beforehand.</span></span> <span data-ttu-id="0c109-209"><xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> は、ノードとその各子に再帰的にアクセスする特定の種類の <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> です。</span><span class="sxs-lookup"><span data-stu-id="0c109-209"><xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> is a specific kind of <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> that recursively visits a node and each of its children.</span></span>

<span data-ttu-id="0c109-210">この例では、構文ツリーを調べる <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> を実装します。</span><span class="sxs-lookup"><span data-stu-id="0c109-210">This example implements a <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> that examines a syntax tree.</span></span> <span data-ttu-id="0c109-211">`System` 名前空間をインポートしていない `using` ディレクティブを収集します。</span><span class="sxs-lookup"><span data-stu-id="0c109-211">It collects `using` directives it finds that aren't importing a `System` namespace.</span></span>

<span data-ttu-id="0c109-212">新しい C# の **Stand-Alone Code Analysis Tool** プロジェクトを作成し、"**SyntaxWalker**" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="0c109-212">Create a new C# **Stand-Alone Code Analysis Tool** project; name it "**SyntaxWalker**."</span></span>

<span data-ttu-id="0c109-213">このサンプルの完成したコードは、[GitHub のリポジトリ](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SyntaxQuickStart)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="0c109-213">You can see the finished code for this sample in [our GitHub repository](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SyntaxQuickStart).</span></span> <span data-ttu-id="0c109-214">GitHub のサンプルには、このチュートリアルで説明されている両方のプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c109-214">The sample on GitHub contains both projects described in this tutorial.</span></span>

<span data-ttu-id="0c109-215">上記のサンプルと同様に、分析しようとしているプログラムのテキストを保持する文字列定数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="0c109-215">As in the previous sample, you can define a string constant to hold the text of the program you're going to analyze:</span></span>

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

<span data-ttu-id="0c109-216">このソース テキストには、4 つの異なる場所 (ファイル レベル、最上位の名前空間、2 つの入れ子になった名前空間) に分散されている `using` ディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c109-216">This source text contains `using` directives scattered across four different locations: the file-level, in the top-level namespace, and in the two nested namespaces.</span></span> <span data-ttu-id="0c109-217">この例では、コードに対してクエリを実行する <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> クラスを使用する主なシナリオに焦点を当てます。</span><span class="sxs-lookup"><span data-stu-id="0c109-217">This example highlights a core scenario for using the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> class to query code.</span></span> <span data-ttu-id="0c109-218">using 宣言を検索するためにルート構文ツリー内のすべてのノードにアクセスするのは面倒です。</span><span class="sxs-lookup"><span data-stu-id="0c109-218">It would be cumbersome to visit every node in the root syntax tree to find using declarations.</span></span> <span data-ttu-id="0c109-219">代わりに、派生クラスを作成し、ツリー内の現在のノードが using ディレクティブである場合にのみ、呼び出されるメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="0c109-219">Instead, you create a derived class and override the method that gets called only when the current node in the tree is a using directive.</span></span> <span data-ttu-id="0c109-220">ビジターは他のノード型に対して何も行いません。</span><span class="sxs-lookup"><span data-stu-id="0c109-220">Your visitor does not do any work on any other node types.</span></span> <span data-ttu-id="0c109-221">この単一のメソッドで各 `using` ステートメントを調べ、`System` 名前空間にはない名前空間のコレクションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="0c109-221">This single method examines each of the `using` statements and builds a collection of the namespaces that aren't in the `System` namespace.</span></span> <span data-ttu-id="0c109-222">すべての `using` ステートメント (`using` ステートメントのみ) を調べる <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> をビルドします。</span><span class="sxs-lookup"><span data-stu-id="0c109-222">You build a <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> that examines all the `using` statements, but only the `using` statements.</span></span>

<span data-ttu-id="0c109-223">これでプログラム テキストを定義したので、`SyntaxTree` を作成して、そのツリーのルートを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c109-223">Now that you've defined the program text, you need to create a `SyntaxTree` and get the root of that tree:</span></span>

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

<span data-ttu-id="0c109-224">次は、新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c109-224">Next, create a new class.</span></span> <span data-ttu-id="0c109-225">Visual Studio で、 **[プロジェクト]**  >  **[新しい項目の追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="0c109-225">In Visual Studio, choose **Project** > **Add New Item**.</span></span> <span data-ttu-id="0c109-226">**[新しい項目の追加]** ダイアログで、ファイル名として「*UsingCollector.cs*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0c109-226">In the **Add New Item** dialog type *UsingCollector.cs* as the filename.</span></span>

<span data-ttu-id="0c109-227">`UsingCollector` クラスで `using` ビジター機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="0c109-227">You implement the `using` visitor functionality in the `UsingCollector` class.</span></span> <span data-ttu-id="0c109-228">まず、<xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> から `UsingCollector` クラスを派生させます。</span><span class="sxs-lookup"><span data-stu-id="0c109-228">Start by making the `UsingCollector` class derive from <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.</span></span>

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

<span data-ttu-id="0c109-229">収集する名前空間ノードを保持する記憶域が必要です。</span><span class="sxs-lookup"><span data-stu-id="0c109-229">You need storage to hold the namespace nodes that you're collecting.</span></span>  <span data-ttu-id="0c109-230">`UsingCollector` クラスでパブリックの読み取り専用プロパティを宣言します。その場合、以下の変数を使用して、検索する <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> ノードを格納します。</span><span class="sxs-lookup"><span data-stu-id="0c109-230">Declare a public read-only property in the `UsingCollector` class; you use this variable to store the <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> nodes you find:</span></span>

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

<span data-ttu-id="0c109-231">基本クラスの <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> では、構文ツリー内の各ノードにアクセスするロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="0c109-231">The base class, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implements the logic to visit each node in the syntax tree.</span></span> <span data-ttu-id="0c109-232">派生クラスは、対象となる特定のノードに対して呼び出されたメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="0c109-232">The derived class overrides the methods called for the specific nodes you're interested in.</span></span> <span data-ttu-id="0c109-233">この例では、`using` ディレクティブが対象となります。</span><span class="sxs-lookup"><span data-stu-id="0c109-233">In this case, you're interested in any `using` directive.</span></span> <span data-ttu-id="0c109-234">つまり、<xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c109-234">That means you must override the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> method.</span></span> <span data-ttu-id="0c109-235">このメソッドへの 1 つの引数は <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="0c109-235">The one argument to this method is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="0c109-236">これがビジターを使用する最も重要は利点です。特定のノード型に既にキャストされている引数を使用して、オーバーライドされたメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0c109-236">That's an important advantage to using the visitors: they call the overridden methods with arguments already cast to the specific node type.</span></span> <span data-ttu-id="0c109-237"><xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> クラスには、インポートされる名前空間の名前を格納する <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="0c109-237">The <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> class has a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> property that stores the name of the namespace being imported.</span></span> <span data-ttu-id="0c109-238">それは <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="0c109-238">It is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0c109-239"><xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> オーバーライドで次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0c109-239">Add the following code in the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> override:</span></span>

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

<span data-ttu-id="0c109-240">前の例と同様に、このメソッドを理解するのに役立つさまざまな `WriteLine` ステートメントを追加しました。</span><span class="sxs-lookup"><span data-stu-id="0c109-240">As with the earlier example, you've added a variety of `WriteLine` statements to aid in understanding of this method.</span></span> <span data-ttu-id="0c109-241">呼びされるタイミングと、毎回渡される引数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="0c109-241">You can see when it's called, and what arguments are passed to it each time.</span></span>

<span data-ttu-id="0c109-242">最後に、2 行のコードを追加して `UsingCollector` を作成し、ルート ノードにアクセスするようにして、`using` ステートメントをすべて収集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c109-242">Finally, you need to add two lines of code to create the `UsingCollector` and have it visit the root node, collecting all the `using` statements.</span></span> <span data-ttu-id="0c109-243">次に、`foreach` ループを追加して、コレクターが検出した `using` ステートメントをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="0c109-243">Then, add a `foreach` loop to display all the `using` statements your collector found:</span></span>

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

<span data-ttu-id="0c109-244">プログラムをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="0c109-244">Compile and run the program.</span></span> <span data-ttu-id="0c109-245">次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c109-245">You should see the following output:</span></span>

```console
        VisitUsingDirective called with System.
        VisitUsingDirective called with System.Collections.Generic.
        VisitUsingDirective called with System.Linq.
        VisitUsingDirective called with System.Text.
        VisitUsingDirective called with Microsoft.CodeAnalysis.
                Success. Adding Microsoft.CodeAnalysis.
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp.
                Success. Adding Microsoft.CodeAnalysis.CSharp.
        VisitUsingDirective called with Microsoft.
                Success. Adding Microsoft.
        VisitUsingDirective called with System.ComponentModel.
        VisitUsingDirective called with Microsoft.Win32.
                Success. Adding Microsoft.Win32.
        VisitUsingDirective called with System.Runtime.InteropServices.
        VisitUsingDirective called with System.CodeDom.
        VisitUsingDirective called with Microsoft.CSharp.
                Success. Adding Microsoft.CSharp.
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

<span data-ttu-id="0c109-246">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="0c109-246">Congratulations!</span></span> <span data-ttu-id="0c109-247">**Syntax API** を使用して、C# ソース コードで特定の種類の C# ステートメントと宣言を検索しました。</span><span class="sxs-lookup"><span data-stu-id="0c109-247">You've used the **Syntax API** to locate specific kinds of C# statements and declarations in C# source code.</span></span>
