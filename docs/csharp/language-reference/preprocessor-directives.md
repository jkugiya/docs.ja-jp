---
description: 条件付きコンパイル、警告、null 許容分析などを制御するさまざまな C# プリプロセッサ ディレクティブについて学習します
title: C# プリプロセッサ ディレクティブ
ms.date: 03/17/2021
f1_keywords:
- cs.preprocessor
- '#nullable'
- '#if'
- '#else'
- '#elif'
- '#endif'
- '#define'
- '#undef'
- '#warning'
- '#error'
- '#line'
- '#region'
- '#endregion'
- '#pragma'
- '#pragma warning'
- '#pragma checksum'
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
- '#nullable directive [C#]'
- '#if directive [C#]'
- '#else directive [C#]'
- '#elif directive [C#]'
- '#endif directive [C#]'
- '#define directive [C#]'
- '#undef directive [C#]'
- '#warning directive [C#]'
- '#error directive [C#]'
- '#line directive [C#]'
- '#region directive [C#]'
- '#endregion directive [C#]'
- '#pragma directive [C#]'
- '#pragma warning [C#]'
- '#pragma checksum [C#]'
ms.openlocfilehash: 373952282a684da25414af9853e18b7bc4874108
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637658"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="634e0-103">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="634e0-103">C# preprocessor directives</span></span>

<span data-ttu-id="634e0-104">コンパイラに個別のプリプロセッサはありませんが、このセクションに示すディレクティブは、ある場合と同じように処理されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-104">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="634e0-105">これらを使用すると、条件付きコンパイルに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="634e0-105">You use them to help in conditional compilation.</span></span> <span data-ttu-id="634e0-106">C や C++ のディレクティブとは異なり、マクロを作成するのにこれらのディレクティブを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="634e0-106">Unlike C and C++ directives, you can't use these directives to create macros.</span></span> <span data-ttu-id="634e0-107">プリプロセッサ ディレクティブは、行の唯一の命令である必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-107">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="nullable-context"></a><span data-ttu-id="634e0-108">Null 許容コンテキスト</span><span class="sxs-lookup"><span data-stu-id="634e0-108">Nullable context</span></span>

<span data-ttu-id="634e0-109">`#nullable` プリプロセッサ ディレクティブは、"*Null 許容注釈コンテキスト*" と "*Null 許容警告コンテキスト*" を設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-109">The `#nullable` preprocessor directive sets the *nullable annotation context* and *nullable warning context*.</span></span> <span data-ttu-id="634e0-110">このディレクティブでは、Null 許容注釈の効果があるかどうか、および NULL 値の許容の警告が与えられるかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-110">This directive controls whether nullable annotations have effect, and whether nullability warnings are given.</span></span> <span data-ttu-id="634e0-111">各コンテキストは "*無効*" または "*有効*" になります。</span><span class="sxs-lookup"><span data-stu-id="634e0-111">Each context is either *disabled* or *enabled*.</span></span>

<span data-ttu-id="634e0-112">どちらのコンテキストもプロジェクト レベル (C# ソース コードの外部) で指定することができます。</span><span class="sxs-lookup"><span data-stu-id="634e0-112">Both contexts can be specified at the project level (outside of C# source code).</span></span> <span data-ttu-id="634e0-113">`#nullable` ディレクティブは、注釈と警告のコンテキストを制御し、プロジェクト レベルの設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-113">The `#nullable` directive controls the annotation and warning contexts and takes precedence over the project-level settings.</span></span> <span data-ttu-id="634e0-114">ディレクティブは、別のディレクティブがそれをオーバーライドするか、ソース ファイルの末尾に達するまで、制御するコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-114">A directive sets the context(s) it controls until another directive overrides it, or until the end of the source file.</span></span>

<span data-ttu-id="634e0-115">ディレクティブの効果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="634e0-115">The effect of the directives is as follows:</span></span>

- <span data-ttu-id="634e0-116">`#nullable disable`: Null 許容注釈および警告コンテキストを "*無効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-116">`#nullable disable`: Sets the nullable annotation and warning contexts to *disabled*.</span></span>
- <span data-ttu-id="634e0-117">`#nullable enable`: Null 許容注釈および警告コンテキストを "*有効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-117">`#nullable enable`: Sets the nullable annotation and warning contexts to *enabled*.</span></span>
- <span data-ttu-id="634e0-118">`#nullable restore`: Null 許容注釈および警告コンテキストを、プロジェクト設定に復元します。</span><span class="sxs-lookup"><span data-stu-id="634e0-118">`#nullable restore`: Restores the nullable annotation and warning contexts to project settings.</span></span>
- <span data-ttu-id="634e0-119">`#nullable disable annotations`: Null 許容注釈コンテキストを "*無効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-119">`#nullable disable annotations`: Sets the nullable annotation context to *disabled*.</span></span>
- <span data-ttu-id="634e0-120">`#nullable enable annotations`: Null 許容注釈コンテキストを "*有効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-120">`#nullable enable annotations`: Sets the nullable annotation context to *enabled*.</span></span>
- <span data-ttu-id="634e0-121">`#nullable restore annotations`: Null 許容注釈コンテキストを、プロジェクト設定に復元します。</span><span class="sxs-lookup"><span data-stu-id="634e0-121">`#nullable restore annotations`: Restores the nullable annotation context to project settings.</span></span>
- <span data-ttu-id="634e0-122">`#nullable disable warnings`: Null 許容警告コンテキストを "*無効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-122">`#nullable disable warnings`: Sets the nullable warning context to *disabled*.</span></span>
- <span data-ttu-id="634e0-123">`#nullable enable warnings`: Null 許容警告コンテキストを "*有効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-123">`#nullable enable warnings`: Sets the nullable warning context to *enabled*.</span></span>
- <span data-ttu-id="634e0-124">`#nullable restore warnings`: Null 許容警告コンテキストをプロジェクト設定に復元します。</span><span class="sxs-lookup"><span data-stu-id="634e0-124">`#nullable restore warnings`: Restores the nullable warning context to project settings.</span></span>

## <a name="conditional-compilation"></a><span data-ttu-id="634e0-125">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="634e0-125">Conditional compilation</span></span>

<span data-ttu-id="634e0-126">次の 4 つのプリプロセッサ ディレクティブを使用して、条件付きコンパイルを制御します。</span><span class="sxs-lookup"><span data-stu-id="634e0-126">You use four preprocessor directives to control conditional compilation:</span></span>

- <span data-ttu-id="634e0-127">`#if`: 条件付きコンパイルを開きます。コードは、指定されたシンボルが定義されている場合にのみコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="634e0-127">`#if`: Opens a conditional compilation, where code is compiled only if the specified symbol is defined.</span></span>
- <span data-ttu-id="634e0-128">`#elif`: 前の条件付きコンパイルを閉じ、指定されたシンボルが定義されているかどうかに基づいて、新しい条件付きコンパイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="634e0-128">`#elif`: Closes the preceding conditional compilation and opens a new conditional compilation based on if the specified symbol is defined.</span></span>
- <span data-ttu-id="634e0-129">`#else`: 前の条件付きコンパイルを閉じ、前に指定されたシンボルが定義されていない場合は、新しい条件付きコンパイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="634e0-129">`#else`: Closes the preceding conditional compilation and opens a new conditional compilation if the previous specified symbol isn't defined.</span></span>
- <span data-ttu-id="634e0-130">`#endif`: 前の条件付きコンパイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="634e0-130">`#endif`: Closes the preceding conditional compilation.</span></span>

<span data-ttu-id="634e0-131">C# コンパイラによって、`#if` ディレクティブ、次いで `#endif` ディレクティブが検出されると、指定されたシンボルが定義されている場合にのみ、これらのディレクティブ間のコードがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="634e0-131">When the C# compiler finds an `#if` directive, followed eventually by an `#endif` directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="634e0-132">C や C++ とは異なり、シンボルに数値を代入することはできません。</span><span class="sxs-lookup"><span data-stu-id="634e0-132">Unlike C and C++, you can't assign a numeric value to a symbol.</span></span> <span data-ttu-id="634e0-133">C# の `#if` ステートメントはブール値で、シンボルが定義されているかどうかのみをテストします。</span><span class="sxs-lookup"><span data-stu-id="634e0-133">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="634e0-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-134">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="634e0-135">[`bool`](builtin-types/bool.md) 値 `true` または `false` をテストするために、演算子 [`==` (等式)](operators/equality-operators.md#equality-operator-) および [`!=` (不等式)](operators/equality-operators.md#inequality-operator-) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="634e0-135">You can use the operators [`==` (equality)](operators/equality-operators.md#equality-operator-) and [`!=` (inequality)](operators/equality-operators.md#inequality-operator-) to test for the [`bool`](builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="634e0-136">`true` は、シンボルが定義されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="634e0-136">`true` means the symbol is defined.</span></span> <span data-ttu-id="634e0-137">ステートメント `#if DEBUG` と `#if (DEBUG == true)` の意味は同じです。</span><span class="sxs-lookup"><span data-stu-id="634e0-137">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="634e0-138">[`&&` (かつ)](operators/boolean-logical-operators.md#conditional-logical-and-operator-)、[`||` (または)](operators/boolean-logical-operators.md#conditional-logical-or-operator-)、[`!` (否定)](operators/boolean-logical-operators.md#logical-negation-operator-) の各演算子を使用すると、複数のシンボルが定義されているかどうかを評価することができます。</span><span class="sxs-lookup"><span data-stu-id="634e0-138">You can use the [`&&` (and)](operators/boolean-logical-operators.md#conditional-logical-and-operator-), [`||` (or)](operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [`!` (not)](operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="634e0-139">シンボルと演算子は、かっこを使用してグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-139">You can also group symbols and operators with parentheses.</span></span>

<span data-ttu-id="634e0-140">`#if` と `#else`、`#elif`、`#endif`、`#define`、`#undef` の各ディレクティブを組み合わせると、1 つ以上のシンボルが存在するかどうかに応じてコードを含めたり除外したりできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-140">`#if`, along with the `#else`, `#elif`, `#endif`, `#define`, and `#undef` directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="634e0-141">条件付きコンパイルは、デバッグ ビルドのコードをコンパイルする場合や、特定の構成用にコンパイルを行う場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="634e0-141">Conditional compilation can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="634e0-142">`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-142">A conditional directive beginning with an `#if` directive must explicitly be terminated with an `#endif` directive.</span></span> <span data-ttu-id="634e0-143">`#define` を使用するとシンボルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-143">`#define` lets you define a symbol.</span></span> <span data-ttu-id="634e0-144">シンボルを `#if` ディレクティブに渡す式として使用すると、この式は `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-144">By using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span> <span data-ttu-id="634e0-145">シンボルは、[**DefineConstants**](compiler-options/language.md#defineconstants) コンパイラ オプションでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-145">You can also define a symbol with the [**DefineConstants**](compiler-options/language.md#defineconstants) compiler option.</span></span> <span data-ttu-id="634e0-146">`#undef` を使うと、シンボルを未定義状態にできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-146">You can undefine a symbol with `#undef`.</span></span> <span data-ttu-id="634e0-147">`#define` を使用して作成したシンボルのスコープは、そのシンボルが定義されているファイルです。</span><span class="sxs-lookup"><span data-stu-id="634e0-147">The scope of a symbol created with `#define` is the file in which it was defined.</span></span> <span data-ttu-id="634e0-148">**DefineConstants** または `#define` で定義したシンボルは、同じ名前の変数とは競合しません。</span><span class="sxs-lookup"><span data-stu-id="634e0-148">A symbol that you define with **DefineConstants** or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="634e0-149">つまり、変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブによってのみ評価できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-149">That is, a variable name shouldn't be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="634e0-150">`#elif` を使用すると、複合条件付きディレクティブを作成できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-150">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="634e0-151">`#elif` 式が評価されるのは、前の `#if` および前の省略可能な `#elif` ディレクティブ式がいずれも `true` と評価されなかった場合です。</span><span class="sxs-lookup"><span data-stu-id="634e0-151">The `#elif` expression will be evaluated if neither the preceding `#if` nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="634e0-152">`#elif` 式が `true` と評価された場合は、`#elif` と次の条件付きディレクティブの間にあるすべてのコードが、コンパイラによって評価されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-152">If an `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="634e0-153">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-153">For example:</span></span>

```csharp
#define VC7
//...
#if debug
    Console.WriteLine("Debug build");
#elif VC7
    Console.WriteLine("Visual Studio 7");
#endif
```

<span data-ttu-id="634e0-154">`#else` を使用すると、複合条件付きディレクティブを作成できるため、前の `#if` または (省略可能な) `#elif` ディレクティブの式がいずれも `true` と評価されない場合は、コンパイラによって `#else` と次の `#endif` の間のすべてのコードが評価されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-154">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding `#if` or (optional) `#elif` directives evaluate to `true`, the compiler will evaluate all code between `#else` and the next `#endif`.</span></span> <span data-ttu-id="634e0-155">`#endif`(#endif) が、`#else` の後の次のプリプロセッサ ディレクティブになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-155">`#endif`(#endif) must be the next preprocessor directive after `#else`.</span></span>

<span data-ttu-id="634e0-156">`#endif` は、`#if` ディレクティブで始まる条件付きディレクティブの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-156">`#endif` specifies the end of a conditional directive, which began with the `#if` directive.</span></span>

<span data-ttu-id="634e0-157">ビルド システムは、SDK 型プロジェクトの各種[ターゲット フレームワーク](../../standard/frameworks.md)を表す、定義済みプリプロセッサ シンボルも認識します。</span><span class="sxs-lookup"><span data-stu-id="634e0-157">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="634e0-158">これは、複数の .NET バージョンをターゲットとできるアプリケーションを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="634e0-158">They're useful when creating applications that can target more than one .NET version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="634e0-159">従来の非 SDK スタイルのプロジェクトでは、プロジェクトの [プロパティ] ページを使用して、Visual Studio のさまざまなターゲット フレームワークの条件付きコンパイル シンボルを手動で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-159">For traditional, non-SDK-style projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="634e0-160">他の定義済みシンボルには、`DEBUG` および `TRACE` 定数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="634e0-160">Other predefined symbols include the `DEBUG` and `TRACE` constants.</span></span> <span data-ttu-id="634e0-161">`#define` を使用して、プロジェクトに設定された値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-161">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="634e0-162">たとえば、DEBUG シンボルは、ビルド構成プロパティ ("デバッグ" モードまたは "リリース" モード) に応じて自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-162">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

<span data-ttu-id="634e0-163">次の例では、ファイルで `MYTEST` シンボルを定義してから、`MYTEST` および `DEBUG` シンボルの値をテストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-163">The following example shows you how to define a `MYTEST` symbol on a file and then test the values of the `MYTEST` and `DEBUG` symbols.</span></span> <span data-ttu-id="634e0-164">この例の出力は、プロジェクトを **デバッグ** と **リリース** のどちらの構成モードでビルドしたかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="634e0-164">The output of this example depends on whether you built the project on **Debug** or **Release** configuration mode.</span></span>

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

<span data-ttu-id="634e0-165">次の例は、各種ターゲット フレームワークをテストし、可能な場合には新しい API を使用できるようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="634e0-165">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="defining-symbols"></a><span data-ttu-id="634e0-166">シンボルの定義</span><span class="sxs-lookup"><span data-stu-id="634e0-166">Defining symbols</span></span>

<span data-ttu-id="634e0-167">次の 2 つのプリプロセッサ ディレクティブを使用して、条件付きコンパイルのシンボルの定義またはその解除を行います。</span><span class="sxs-lookup"><span data-stu-id="634e0-167">You use the following two preprocessor directives to define or undefine symbols for conditional compilation:</span></span>

- <span data-ttu-id="634e0-168">`#define`: シンボルを定義します。</span><span class="sxs-lookup"><span data-stu-id="634e0-168">`#define`: Define a symbol.</span></span>
- <span data-ttu-id="634e0-169">`#undef`シンボルの定義を解除します。</span><span class="sxs-lookup"><span data-stu-id="634e0-169">`#undef`: undefine a symbol.</span></span>

<span data-ttu-id="634e0-170">`#define` は、シンボルを定義するために使用します。</span><span class="sxs-lookup"><span data-stu-id="634e0-170">You use `#define` to define a symbol.</span></span> <span data-ttu-id="634e0-171">次の例に示すように、定義したシンボルを式として `#if` ディレクティブに渡すと、式は `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-171">When you use the symbol as the expression that's passed to the `#if` directive, the expression will evaluate to `true`, as the following example shows:</span></span>

 ```csharp
 #define VERBOSE

#if VERBOSE
    Console.WriteLine("Verbose output version");
#endif

 ```

> [!NOTE]
> <span data-ttu-id="634e0-172">`#define` ディレクティブを使用して、通常 C および C++ で行うように定数値を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="634e0-172">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="634e0-173">C# の定数は、クラスまたは構造体の静的メンバーとして定義することができます。</span><span class="sxs-lookup"><span data-stu-id="634e0-173">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="634e0-174">そのような定数がいくつかある場合は、それを保持するための "Constants" クラスを個別に作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="634e0-174">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>

<span data-ttu-id="634e0-175">シンボルを使用して、コンパイル条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-175">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="634e0-176">シンボルは、`#if` または `#elif` で評価できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-176">You can test for the symbol with either `#if` or `#elif`.</span></span> <span data-ttu-id="634e0-177">また、<xref:System.Diagnostics.ConditionalAttribute> を使用して、条件付きコンパイルを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-177">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span> <span data-ttu-id="634e0-178">シンボルを定義することはできますが、シンボルに値を代入することはできません。</span><span class="sxs-lookup"><span data-stu-id="634e0-178">You can define a symbol, but you can't assign a value to a symbol.</span></span> <span data-ttu-id="634e0-179">`#define` ディレクティブは、ファイル内で、プリプロセッサ ディレクティブではない他の命令よりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-179">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span> <span data-ttu-id="634e0-180">シンボルは、[**DefineConstants**](compiler-options/language.md#defineconstants) コンパイラ オプションでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-180">You can also define a symbol with the [**DefineConstants**](compiler-options/language.md#defineconstants) compiler option.</span></span> <span data-ttu-id="634e0-181">`#undef` を使うと、シンボルを未定義状態にできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-181">You can undefine a symbol with `#undef`.</span></span>

## <a name="defining-regions"></a><span data-ttu-id="634e0-182">領域の定義</span><span class="sxs-lookup"><span data-stu-id="634e0-182">Defining regions</span></span>

<span data-ttu-id="634e0-183">次の 2 つのプリプロセッサ ディレクティブを使用して、アウトラインで折りたたむことができるコードの領域を定義できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-183">You can define regions of code that can be collapsed in an outline using the following two preprocessor directives:</span></span>

- <span data-ttu-id="634e0-184">`#region`: 領域を開始します。</span><span class="sxs-lookup"><span data-stu-id="634e0-184">`#region`: Start a region.</span></span>
- <span data-ttu-id="634e0-185">`#endregion`: 領域を終了します</span><span class="sxs-lookup"><span data-stu-id="634e0-185">`#endregion`: End a region</span></span>

<span data-ttu-id="634e0-186">`#region` を使用すると、コード ブロックを指定できます。このブロックは、コード エディターの[アウトライン](/visualstudio/ide/outlining)機能を使用して、展開や折りたたみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="634e0-186">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="634e0-187">コード ファイルが長い場合は、現在操作しているファイルの部分に集中できるように 1 つまたは複数の領域を折りたたむ (非表示にする) と便利です。</span><span class="sxs-lookup"><span data-stu-id="634e0-187">In longer code files, it's convenient to collapse or hide one or more regions so that you can focus on the part of the file that you're currently working on.</span></span> <span data-ttu-id="634e0-188">次の例では、領域を定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-188">The following example shows how to define a region:</span></span>

```csharp
#region MyClass definition
public class MyClass
{
    static void Main()
    {
    }
}
#endregion
```

<span data-ttu-id="634e0-189">`#region` ブロックは、`#endregion` ディレクティブで終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-189">A `#region` block must be terminated with an `#endregion` directive.</span></span> <span data-ttu-id="634e0-190">`#region` ブロックは、`#if` ブロックと重複することはできません。</span><span class="sxs-lookup"><span data-stu-id="634e0-190">A `#region` block can't overlap with an `#if` block.</span></span> <span data-ttu-id="634e0-191">しかし、`#region` ブロックを `#if` ブロック内に入れ子にしたり、`#if` ブロックを `#region` ブロック内に入れ子にしたりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-191">However, a `#region` block can be nested in an `#if` block, and an `#if` block can be nested in a `#region` block.</span></span>

## <a name="error-and-warning-information"></a><span data-ttu-id="634e0-192">エラーと警告の情報</span><span class="sxs-lookup"><span data-stu-id="634e0-192">Error and warning information</span></span>

<span data-ttu-id="634e0-193">次のディレクティブを使用して、ユーザー定義のコンパイラ エラーと警告を生成し、行情報を制御するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-193">You instruct the compiler to generate user-defined compiler errors and warnings, and control line information using the following directives:</span></span>

- <span data-ttu-id="634e0-194">`#error`: 指定されたメッセージでコンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="634e0-194">`#error`: Generate a compiler error with a specified message.</span></span>
- <span data-ttu-id="634e0-195">`#warning`: 特定のメッセージでコンパイラ警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="634e0-195">`#warning`: Generate a compiler warning, with a specific message.</span></span>
- <span data-ttu-id="634e0-196">`#line`: コンパイラ メッセージで出力される行番号を変更します。</span><span class="sxs-lookup"><span data-stu-id="634e0-196">`#line`: Change the line number printed with compiler messages.</span></span>

<span data-ttu-id="634e0-197">`#error` を使用すると、コード内の特定の場所からユーザー定義の [CS1029](compiler-messages/cs1029.md) エラーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-197">`#error` lets you generate a [CS1029](compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="634e0-198">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-198">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="634e0-199">コンパイラは `#error version` を特別な方法で処理し、使用されているコンパイラと言語バージョンを含むメッセージと共にコンパイラ エラー CS8304 を報告します。</span><span class="sxs-lookup"><span data-stu-id="634e0-199">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

<span data-ttu-id="634e0-200">`#warning` を使用すると、コード内の特定の場所から [CS1030](../misc/cs1030.md) レベル 1 のコンパイラの警告を生成できます。</span><span class="sxs-lookup"><span data-stu-id="634e0-200">`#warning` lets you generate a [CS1030](../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="634e0-201">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-201">For example:</span></span>

```csharp
#warning Deprecated code in this method.
```

<span data-ttu-id="634e0-202">`#line` を使用すると、コンパイラの行番号および (必要に応じて) エラーと警告に出力されるファイル名を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="634e0-202">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="634e0-203">次の例では、行番号に関連付けられている 2 つの警告を報告する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-203">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="634e0-204">`#line 200` ディレクティブは次の行番号が 200 (既定では #6) になるように強制し、次の `#line` ディレクティブまでファイル名を "Special" として報告します。</span><span class="sxs-lookup"><span data-stu-id="634e0-204">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="634e0-205">`#line default` ディレクティブは、行の番号付けをその既定の番号付けに戻します。つまり、前のディレクティブで番号が付け直された行をカウントします。</span><span class="sxs-lookup"><span data-stu-id="634e0-205">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="634e0-206">コンパイルで生成される出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="634e0-206">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

<span data-ttu-id="634e0-207">`#line` ディレクティブは、ビルド プロセスで自動化された中間ステップで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-207">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="634e0-208">たとえば、行が元のソース コード ファイルから削除されても、ファイル内の元の行番号付けに基づいてコンパイラに引き続き出力を生成させる場合は、行を削除してから `#line` を使用して元の行番号付けをシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-208">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="634e0-209">開発者がコードをステップ実行すると、`#line hidden` と次の `#line` ディレクティブ (別の `#line hidden` ディレクティブではないと仮定) の間のすべての行がステップ オーバーされるように、`#line hidden` ディレクティブによって、デバッガーに対して連続する行が非表示にされます。</span><span class="sxs-lookup"><span data-stu-id="634e0-209">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it isn't another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="634e0-210">このオプションは、ユーザー定義のコードとコンピューターによって生成されたコードを ASP.NET が区別できるようするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="634e0-210">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="634e0-211">この機能を主に使われているのは ASP.NET ですが、より多くのソース ジェネレーターで利用できる可能性はあります。</span><span class="sxs-lookup"><span data-stu-id="634e0-211">Although ASP.NET is the primary consumer of this feature, it's likely that more source generators will make use of it.</span></span>

<span data-ttu-id="634e0-212">`#line hidden` ディレクティブは、エラー報告でのファイル名や行番号には影響しません。</span><span class="sxs-lookup"><span data-stu-id="634e0-212">A `#line hidden` directive doesn't affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="634e0-213">つまり、コンパイラによって非表示のブロックでエラーが検出された場合、そのコンパイラによってエラーの現在のファイル名と行番号が報告されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-213">That is, if the compiler finds an error in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="634e0-214">`#line filename` ディレクティブは、コンパイラ出力に表示するファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="634e0-214">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="634e0-215">既定では、ソース コード ファイルの実際の名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-215">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="634e0-216">ファイル名は、二重引用符 ("") で囲み、前に行番号を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-216">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="634e0-217">次の例では、デバッガーがコード内の非表示の行を無視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-217">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="634e0-218">例を実行すると、次の 3 行のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-218">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="634e0-219">しかし、例に示されているようにブレークポイントを設定し、F10 キーを押してコードをステップ実行すると、デバッガーで非表示の行が無視されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-219">However, when you set a break point, as shown in the example, and hit F10 to step through the code, the debugger ignores the hidden line.</span></span> <span data-ttu-id="634e0-220">非表示の行にブレークポイントを設定した場合でも、デバッガーで引き続きそれが無視されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-220">Even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="pragmas"></a><span data-ttu-id="634e0-221">プラグマ</span><span class="sxs-lookup"><span data-stu-id="634e0-221">Pragmas</span></span>

<span data-ttu-id="634e0-222">`#pragma` は、ファイル内に指定され、そのファイルのコンパイルについての特別な命令をコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="634e0-222">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="634e0-223">命令はコンパイラによってサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-223">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="634e0-224">つまり、`#pragma` を使用してカスタムの前処理命令を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="634e0-224">In other words, you can't use `#pragma` to create custom preprocessing instructions.</span></span>
  
- <span data-ttu-id="634e0-225">[`#pragma warning`](#pragma-warning): 警告を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="634e0-225">[`#pragma warning`](#pragma-warning): Enable or disable warnings.</span></span>
- <span data-ttu-id="634e0-226">[`#pragma checksum`](#pragma-checksum): チェックサムを生成します。</span><span class="sxs-lookup"><span data-stu-id="634e0-226">[`#pragma checksum`](#pragma-checksum): Generate a checksum.</span></span>

```csharp
#pragma pragma-name pragma-arguments
```

<span data-ttu-id="634e0-227">ここで、`pragma-name` は認識されているプラグマの名前で、`pragma-arguments` は pragma 固有の引数です。</span><span class="sxs-lookup"><span data-stu-id="634e0-227">Where `pragma-name` is the name of a recognized pragma and `pragma-arguments` is the pragma-specific arguments.</span></span>

### <a name="pragma-warning"></a><span data-ttu-id="634e0-228">#pragma 警告</span><span class="sxs-lookup"><span data-stu-id="634e0-228">#pragma warning</span></span>

<span data-ttu-id="634e0-229">`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="634e0-229">`#pragma warning` can enable or disable certain warnings.</span></span>

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

<span data-ttu-id="634e0-230">ここで、`warning-list` は警告番号のコンマ区切りのリストです。</span><span class="sxs-lookup"><span data-stu-id="634e0-230">Where `warning-list` is a comma-separated list of warning numbers.</span></span> <span data-ttu-id="634e0-231">"CS" というプレフィックスは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="634e0-231">The "CS" prefix is optional.</span></span> <span data-ttu-id="634e0-232">警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="634e0-232">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="634e0-233">Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。</span><span class="sxs-lookup"><span data-stu-id="634e0-233">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>

<span data-ttu-id="634e0-234">`disable` は、ソース ファイルの次の行から有効になります。</span><span class="sxs-lookup"><span data-stu-id="634e0-234">The `disable` takes effect beginning on the next line of the source file.</span></span> <span data-ttu-id="634e0-235">警告は、`restore` の後の行で復元されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-235">The warning is restored on the line following the `restore`.</span></span> <span data-ttu-id="634e0-236">ファイルに `restore` が存在しない場合、警告は、同じコンパイルの以降のファイルの最初の行で既定の状態に復元されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-236">If there's no `restore` in the file, the warnings are restored to their default state at the first line of any later files in the same compilation.</span></span>

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

### <a name="pragma-checksum"></a><span data-ttu-id="634e0-237">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="634e0-237">#pragma checksum</span></span>

<span data-ttu-id="634e0-238">ASP.NET ページのデバッグに使用するソース ファイルのチェックサムを生成します。</span><span class="sxs-lookup"><span data-stu-id="634e0-238">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>

```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"
```

<span data-ttu-id="634e0-239">ここで、`"filename"` は変更または更新の監視を必要とするファイルの名前、`"{guid}"` はハッシュ アルゴリズムのグローバル一意識別子 (GUID)、`"checksum_bytes"` はチェックサムのバイト数を表す 16 進数の文字列です。</span><span class="sxs-lookup"><span data-stu-id="634e0-239">Where `"filename"` is the name of the file that requires monitoring for changes or updates, `"{guid}"` is the Globally Unique Identifier (GUID) for the hash algorithm, and `"checksum_bytes"` is the string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="634e0-240">偶数の 16 進数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="634e0-240">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="634e0-241">奇数の数値を指定すると、コンパイル時に警告が出力され、ディレクティブが無視されます。</span><span class="sxs-lookup"><span data-stu-id="634e0-241">An odd number of digits results in a compile-time warning, and the directive is ignored.</span></span>

<span data-ttu-id="634e0-242">Visual Studio デバッガーは、常に正しいソースを検出するために、チェックサムを使用します。</span><span class="sxs-lookup"><span data-stu-id="634e0-242">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="634e0-243">コンパイラはソース ファイルのチェックサムを計算し、プログラム データベース (PDB) ファイルに結果を出力します。</span><span class="sxs-lookup"><span data-stu-id="634e0-243">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="634e0-244">デバッガーは、その PDB ファイルを使用して、ソース ファイルについて計算したチェックサムと比較します。</span><span class="sxs-lookup"><span data-stu-id="634e0-244">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>

<span data-ttu-id="634e0-245">このソリューションは ASP.NET プロジェクトには使用できません。計算されたチェックサムは、.aspx ファイルではなく、生成されたソース ファイルを対象としているためです。</span><span class="sxs-lookup"><span data-stu-id="634e0-245">This solution doesn't work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="634e0-246">この問題に対応するため、`#pragma checksum` によって ASP.NET ページのチェックサムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="634e0-246">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>

<span data-ttu-id="634e0-247">Visual C# で ASP.NET プロジェクトを作成すると、生成されるソース ファイルにソースの生成元である .aspx ファイルのチェックサムが含められます。</span><span class="sxs-lookup"><span data-stu-id="634e0-247">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="634e0-248">コンパイラは、この情報を PDB ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="634e0-248">The compiler then writes this information into the PDB file.</span></span>

<span data-ttu-id="634e0-249">コンパイラによってファイルで `#pragma checksum` ディレクティブが検出されない場合、チェックサムが計算され、PDB ファイルにその値が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="634e0-249">If the compiler doesn't find a `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>

```csharp
class TestClass
{
    static int Main()
    {
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum
    }
}
```
