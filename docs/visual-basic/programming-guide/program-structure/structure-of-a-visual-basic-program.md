---
description: '詳細情報: Visual Basic プログラムの構造'
title: Visual Basic プログラムの構造
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: e5941b1cbdfdc460e3e860a5449e8ccae0673612
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468201"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="e2c24-103">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="e2c24-103">Structure of a Visual Basic Program</span></span>

<span data-ttu-id="e2c24-104">Visual Basic プログラムは、標準の構成要素から構築します。</span><span class="sxs-lookup"><span data-stu-id="e2c24-104">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="e2c24-105">"*ソリューション*" は、1 つ以上のプロジェクトで構成します。</span><span class="sxs-lookup"><span data-stu-id="e2c24-105">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="e2c24-106">"*プロジェクト*" には、1 つ以上のアセンブリを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-106">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="e2c24-107">各 "*アセンブリ*" は、1 つ以上のソース ファイルからコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e2c24-107">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="e2c24-108">"*ソース ファイル*" では、クラス、構造体、モジュール、インターフェイスの定義と実装が提供され、最終的にはすべてのコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-108">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="e2c24-109">Visual Basic プログラムのこれらの構成要素の詳細については、[ソリューションとプロジェクト](/visualstudio/ide/solutions-and-projects-in-visual-studio)および [.NET のアセンブリ](../../../standard/assembly/index.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-109">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="e2c24-110">ファイルレベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e2c24-110">File-Level Programming Elements</span></span>  

 <span data-ttu-id="e2c24-111">プロジェクトまたはファイルを起動してコード エディターを開くと、いくつかのコードが既に配置され、正しい順序で表示されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e2c24-111">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="e2c24-112">記述するすべてのコードで、次のシーケンスに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c24-112">Any code that you write should follow the following sequence:</span></span>  
  
1. <span data-ttu-id="e2c24-113">`Option` ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-113">`Option` statements</span></span>  
  
2. <span data-ttu-id="e2c24-114">`Imports` ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-114">`Imports` statements</span></span>  
  
3. <span data-ttu-id="e2c24-115">`Namespace` ステートメントと名前空間レベルの要素</span><span class="sxs-lookup"><span data-stu-id="e2c24-115">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="e2c24-116">ステートメントを異なる順序で入力すると、コンパイル エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2c24-116">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="e2c24-117">プログラムには、条件付きコンパイル ステートメントを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-117">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="e2c24-118">ソース ファイル内で、前のシーケンスのステートメントの間にこれらを挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-118">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="e2c24-119">Option ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-119">Option Statements</span></span>  

 <span data-ttu-id="e2c24-120">`Option` ステートメントを使用すると、後続のコードに対して基本ルールを確立し、構文エラーと論理エラーを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-120">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="e2c24-121">[Option Explicit ステートメント](../../language-reference/statements/option-explicit-statement.md)を使用すると、すべての変数の宣言とスペルが正しいことを保証できるため、デバッグ時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-121">The [Option Explicit Statement](../../language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="e2c24-122">[Option Strict ステートメント](../../language-reference/statements/option-strict-statement.md)を使用すると、データ型が異なる変数間の処理で発生する可能性がある論理エラーとデータ損失を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-122">The [Option Strict Statement](../../language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="e2c24-123">[Option Compare ステートメント](../../language-reference/statements/option-compare-statement.md)では、文字列を `Binary` または `Text` の値に基づいて相互比較する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2c24-123">The [Option Compare Statement](../../language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="e2c24-124">Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-124">Imports Statements</span></span>  

 <span data-ttu-id="e2c24-125">[Imports ステートメント (.NET 名前空間および型)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) を含めて、プロジェクトの外部で定義されている名前をインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-125">You can include an [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="e2c24-126">`Imports` ステートメントを使用すると、インポートする名前空間内で定義されているクラスやその他の型を、修飾することなくコード内で参照できます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-126">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="e2c24-127">`Imports` ステートメントは必要な数だけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-127">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="e2c24-128">詳細については、「[参照と Imports ステートメント](references-and-the-imports-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-128">For more information, see [References and the Imports Statement](references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="e2c24-129">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-129">Namespace Statements</span></span>  

 <span data-ttu-id="e2c24-130">名前空間を使用すると、プログラミング要素を編成、分類でき、グループ化とアクセスが容易になります。</span><span class="sxs-lookup"><span data-stu-id="e2c24-130">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="e2c24-131">[Namespace ステートメント](../../language-reference/statements/namespace-statement.md)を使用すると、特定の名前空間内の後続のステートメントを分類できます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-131">You use the [Namespace Statement](../../language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="e2c24-132">詳細については、「[Visual Basic における名前空間](namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-132">For more information, see [Namespaces in Visual Basic](namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="e2c24-133">条件付きコンパイル ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-133">Conditional Compilation Statements</span></span>  

 <span data-ttu-id="e2c24-134">条件付きコンパイル ステートメントは、ソース ファイル内のほぼどこにでも記述できます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-134">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="e2c24-135">コンパイル時に、特定の条件に応じて、コードの一部を含める、または除外することができます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-135">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="e2c24-136">条件付きコードはデバッグ モードでのみ実行されるため、アプリケーションのデバッグにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-136">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="e2c24-137">詳細については、[条件付きコンパイル](conditional-compilation.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-137">For more information, see [Conditional Compilation](conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="e2c24-138">名前空間レベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e2c24-138">Namespace-Level Programming Elements</span></span>  

 <span data-ttu-id="e2c24-139">ソース ファイル内のすべてのコードは、クラス、構造体、モジュールに含まれます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-139">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="e2c24-140">これらは "*名前空間レベル*" の要素であり、名前空間内またはソース ファイル レベルで記述することができます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-140">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="e2c24-141">他のすべてのプログラミング要素の宣言が保持されます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-141">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="e2c24-142">また、要素シグネチャを定義するが実装を提供しないインターフェイスは、モジュール レベルで記述します。</span><span class="sxs-lookup"><span data-stu-id="e2c24-142">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="e2c24-143">モジュールレベルの要素の詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-143">For more information on the module-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="e2c24-144">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-144">Class Statement</span></span>](../../language-reference/statements/class-statement.md)  
  
- [<span data-ttu-id="e2c24-145">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-145">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)  
  
- [<span data-ttu-id="e2c24-146">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-146">Module Statement</span></span>](../../language-reference/statements/module-statement.md)  
  
- [<span data-ttu-id="e2c24-147">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-147">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="e2c24-148">名前空間レベルのデータ要素は、列挙型とデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="e2c24-148">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="e2c24-149">モジュールレベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e2c24-149">Module-Level Programming Elements</span></span>  

 <span data-ttu-id="e2c24-150">プロシージャ、演算子、プロパティ、イベントは、実行可能コード (実行時にアクションを実行するステートメント) を保持できる唯一のプログラミング要素です。</span><span class="sxs-lookup"><span data-stu-id="e2c24-150">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="e2c24-151">これらは、プログラムの "*モジュールレベル*" の要素です。</span><span class="sxs-lookup"><span data-stu-id="e2c24-151">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="e2c24-152">プロシージャレベルの要素の詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-152">For more information on the procedure-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="e2c24-153">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-153">Function Statement</span></span>](../../language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="e2c24-154">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-154">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)  
  
- [<span data-ttu-id="e2c24-155">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-155">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="e2c24-156">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-156">Operator Statement</span></span>](../../language-reference/statements/operator-statement.md)  
  
- [<span data-ttu-id="e2c24-157">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-157">Property Statement</span></span>](../../language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="e2c24-158">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2c24-158">Event Statement</span></span>](../../language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="e2c24-159">モジュール レベルのデータ要素は、変数、定数、列挙型、デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="e2c24-159">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="e2c24-160">プロシージャレベルのプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="e2c24-160">Procedure-Level Programming Elements</span></span>  

 <span data-ttu-id="e2c24-161">"*プロシージャレベル*" の要素の内容の大部分は実行可能なステートメントであり、プログラムの実行時コードを構成します。</span><span class="sxs-lookup"><span data-stu-id="e2c24-161">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="e2c24-162">すべての実行可能コードは、何らかのプロシージャ (`Function`、`Sub`、`Operator`、`Get`、`Set`、`AddHandler`、`RemoveHandler`、`RaiseEvent`) 内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2c24-162">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="e2c24-163">詳細については、「[ステートメント](../language-features/statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-163">For more information, see [Statements](../language-features/statements.md).</span></span>  
  
 <span data-ttu-id="e2c24-164">プロシージャ レベルのデータ要素は、ローカル変数と定数に制限されます。</span><span class="sxs-lookup"><span data-stu-id="e2c24-164">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="e2c24-165">Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e2c24-165">The Main Procedure</span></span>  

 <span data-ttu-id="e2c24-166">`Main` プロシージャは、アプリケーションが読み込まれたときに実行される最初のコードです。</span><span class="sxs-lookup"><span data-stu-id="e2c24-166">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="e2c24-167">`Main` は、アプリケーションの開始点および全体的な制御として機能します。</span><span class="sxs-lookup"><span data-stu-id="e2c24-167">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="e2c24-168">`Main` には、次の 4 種類があります。</span><span class="sxs-lookup"><span data-stu-id="e2c24-168">There are four varieties of `Main`:</span></span>  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="e2c24-169">このプロシージャの中で最も一般的なものは `Sub Main()` です。</span><span class="sxs-lookup"><span data-stu-id="e2c24-169">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="e2c24-170">詳細については、「[Visual Basic の Main プロシージャ](main-procedure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2c24-170">For more information, see [Main Procedure in Visual Basic](main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c24-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2c24-171">See also</span></span>

- [<span data-ttu-id="e2c24-172">Visual Basic の Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e2c24-172">Main Procedure in Visual Basic</span></span>](main-procedure.md)
- [<span data-ttu-id="e2c24-173">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="e2c24-173">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="e2c24-174">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="e2c24-174">Visual Basic Limitations</span></span>](limitations.md)
