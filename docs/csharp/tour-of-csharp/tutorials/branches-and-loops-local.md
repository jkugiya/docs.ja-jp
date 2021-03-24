---
title: 分岐とループ - C# の概要に関するチュートリアル
description: 分岐とループに関するこのチュートリアルでは、C# のコードを記述して、この言語における、ステートメントを繰り返し実行するための条件付き分岐とループに対応している構文について学習します。
ms.date: 02/05/2021
ms.openlocfilehash: ae57b370022bfc86200ca20a913d44f64e46d68d
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881121"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="1bf5c-103">分岐およびループ ステートメントを使用した条件付きロジックについて説明します</span><span class="sxs-lookup"><span data-stu-id="1bf5c-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="1bf5c-104">このチュートリアルでは、変数を調べ、その変数に基づいて実行パスを変更するコードを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="1bf5c-105">C# コードを記述し、コードをコンパイルおよび実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="1bf5c-106">チュートリアルには、C# における分岐構造とループ構造を確認する一連のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="1bf5c-107">これらのレッスンでは、C# 言語の基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bf5c-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="1bf5c-108">Prerequisites</span></span>

<span data-ttu-id="1bf5c-109">このチュートリアルでは、ローカル開発用にセットアップされたコンピューターがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="1bf5c-110">Windows、Linux、または macOS で、.NET CLI を使用してアプリケーションを作成、ビルド、実行できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="1bf5c-111">Mac と Windows では、Visual Studio 2019 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-111">On Mac and Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="1bf5c-112">セットアップの手順については、「[ローカル環境をセットアップする](local-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="1bf5c-113">`if` ステートメントを使用した条件判定</span><span class="sxs-lookup"><span data-stu-id="1bf5c-113">Make decisions using the `if` statement</span></span>

<span data-ttu-id="1bf5c-114">「*branches-tutorial*」という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-114">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="1bf5c-115">それを現在のディレクトリにして、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-115">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="1bf5c-116">このコマンドにより、現在のディレクトリに新しい .NET コンソール アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-116">This command creates a new .NET console application in the current directory.</span></span> <span data-ttu-id="1bf5c-117">好みのエディターで *Program.cs* を開き、内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-117">Open *Program.cs* in your favorite editor, and replace the contents with the following code:</span></span>

```csharp
using System;

int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="1bf5c-118">コンソール ウィンドウで「`dotnet run`」と入力し、このコードを試します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-118">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="1bf5c-119">"答えは 10 を超えています" というメッセージが</span><span class="sxs-lookup"><span data-stu-id="1bf5c-119">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="1bf5c-120">コンソールに出力されるはずです。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-120">printed to your console.</span></span> <span data-ttu-id="1bf5c-121">合計が 10 未満になるように `b` の宣言を変更します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-121">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="1bf5c-122">もう一度「`dotnet run`」を入力します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-122">Type `dotnet run` again.</span></span> <span data-ttu-id="1bf5c-123">計算結果が 10 未満であるため、何も出力されません。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-123">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="1bf5c-124">判定中の **条件** が false になっています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-124">The **condition** you're testing is false.</span></span> <span data-ttu-id="1bf5c-125">`if` ステートメントの考えられる分岐の 1 つである true 分岐のみを記述したため、実行すべきコードがありません。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-125">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="1bf5c-126">C# (または何らかのプログラミング言語) について詳しく学習するに従い、コードを記述する際にミスをすることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-126">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="1bf5c-127">コンパイラは、エラーを発見して報告します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-127">The compiler will find and report the errors.</span></span> <span data-ttu-id="1bf5c-128">エラーの出力とそのエラーを生成したコードをよく確認してください。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-128">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="1bf5c-129">通常、コンパイラ エラーは問題を発見するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-129">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="1bf5c-130">この最初のサンプルは、`if` とブール型の機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-130">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="1bf5c-131">*ブール値* は、`true` または `false` という 2 つの値のいずれかを持つことができる変数です。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-131">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="1bf5c-132">C# ではブール変数の専用の型として `bool` を定義しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-132">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="1bf5c-133">`if` ステートメントは、`bool` の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-133">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="1bf5c-134">値が `true` の場合、`if` に続くステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-134">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="1bf5c-135">それ以外の場合はスキップします。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-135">Otherwise, it's skipped.</span></span> <span data-ttu-id="1bf5c-136">条件を確認してその条件に基づいてステートメントを実行するというこのプロセスは機能的です。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-136">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="1bf5c-137">if と else を組み合わせた使用</span><span class="sxs-lookup"><span data-stu-id="1bf5c-137">Make if and else work together</span></span>

<span data-ttu-id="1bf5c-138">true 分岐と false 分岐で別々のコードを実行するには、条件が false のときに実行する `else` 分岐を作成します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-138">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="1bf5c-139">`else` 分岐を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-139">Try an `else` branch.</span></span> <span data-ttu-id="1bf5c-140">次のコードの最後の 2 行を追加します (最初の 4 行は既にあるはずです)。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-140">Add the last two lines in the code below (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="1bf5c-141">`else` キーワードに続くステートメントは、判定中の条件が `false` のときにのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-141">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="1bf5c-142">`if` と `else` をブール条件と組み合わせれば、`true` と `false` の条件を両方処理するのに必要な機能がすべて整います。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-142">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bf5c-143">`if` と `else` のステートメント内にあるインデントは、人が読みやすいようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-143">The indentation under the `if` and `else` statements is for human readers.</span></span> <span data-ttu-id="1bf5c-144">C# 言語はインデントや空白文字を重要なものとして扱いません。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-144">The C# language doesn't treat indentation or white space as significant.</span></span> <span data-ttu-id="1bf5c-145">`if` や `else` のキーワードに続くステートメントは、条件に基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-145">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="1bf5c-146">このチュートリアルのすべてのサンプルでは、一般的な記述方法に従い、ステートメントの制御フローに基づいて行にインデントを挿入しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-146">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="1bf5c-147">インデントは重要ではないため、条件に基づいて実行するブロック内に 1 つ以上のステートメントがある場合には、`{` と `}` を使用して示します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-147">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="1bf5c-148">通常、C# プログラマーは `if` と `else` の句にはこの中かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-148">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="1bf5c-149">次の例は、作成したものと同じ内容です。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-149">The following example is the same as the one you created.</span></span> <span data-ttu-id="1bf5c-150">上のコードを、次のコードに一致するように変更します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-150">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="1bf5c-151">このチュートリアルの残りの箇所では、一般に認められている記述方法に従って、すべてのコード サンプルで中かっこを使用しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-151">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="1bf5c-152">さらに複雑な条件を判定できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-152">You can test more complicated conditions.</span></span> <span data-ttu-id="1bf5c-153">これまでに記述したコードの後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-153">Add the following code after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="1bf5c-154">`==` シンボルは、"*同等性*" をテストします。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-154">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="1bf5c-155">`==` を使用すると、同等性のテストが `a = 5` で確認した割り当てと区別されます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-155">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="1bf5c-156">`&&` は "and" (および) を表します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-156">The `&&` represents "and".</span></span> <span data-ttu-id="1bf5c-157">これは、true 分岐でステートメントを実行するには、両方の条件が true になる必要があることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-157">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="1bf5c-158">また、これらの例では、ステートメントが `{` と `}` で囲まれていれば、各条件分岐に複数のステートメントを持つことができることを示しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-158">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span> <span data-ttu-id="1bf5c-159">`||` を使用して "or" (または) を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-159">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="1bf5c-160">これまでに記述したコードの下に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-160">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="1bf5c-161">`a`、`b`、および `c`の値を変更し、探索する `&&` と `||` を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-161">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="1bf5c-162">`&&` 演算子と `||` 演算子がどのように機能するかをより深く理解できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-162">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="1bf5c-163">最初の手順が完了しました。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-163">You've finished the first step.</span></span> <span data-ttu-id="1bf5c-164">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-164">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="1bf5c-165">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-165">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="1bf5c-166">`ExploreIf()` というメソッドに既存のコードを入れます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-166">Put the existing code in a method called `ExploreIf()`.</span></span> <span data-ttu-id="1bf5c-167">それをプログラムの先頭で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-167">Call it from the top of your program.</span></span> <span data-ttu-id="1bf5c-168">それらの変更を終えると、コードは次のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-168">When you finished those changes, your code should look like the following:</span></span>

```csharp
using System;

ExploreIf();

void ExploreIf()
{
    int a = 5;
    int b = 3;
    if (a + b > 10)
    {
        Console.WriteLine("The answer is greater than 10");
    }
    else
    {
        Console.WriteLine("The answer is not greater than 10");
    }

    int c = 4;
    if ((a + b + c > 10) && (a > b))
    {
        Console.WriteLine("The answer is greater than 10");
        Console.WriteLine("And the first number is greater than the second");
    }
    else
    {
        Console.WriteLine("The answer is not greater than 10");
        Console.WriteLine("Or the first number is not greater than the second");
    }

    if ((a + b + c > 10) || (a > b))
    {
        Console.WriteLine("The answer is greater than 10");
        Console.WriteLine("Or the first number is greater than the second");
    }
    else
    {
        Console.WriteLine("The answer is not greater than 10");
        Console.WriteLine("And the first number is not greater than the second");
    }
}
```

<span data-ttu-id="1bf5c-169">`ExploreIf()` の呼び出しをコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-169">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="1bf5c-170">こうしておくと、このセクションの作業を進めるにあたって出力がすっきりします。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-170">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="1bf5c-171">C# では、`//` の後ろが **コメント** になります。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-171">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="1bf5c-172">コードとしては実行せずにソース コード内に残したい任意のテキストを、コメントにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-172">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="1bf5c-173">コンパイラは、コメントから実行可能コードを生成しません。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-173">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="1bf5c-174">ループを使用した処理の繰り返し</span><span class="sxs-lookup"><span data-stu-id="1bf5c-174">Use loops to repeat operations</span></span>

<span data-ttu-id="1bf5c-175">このセクションでは **ループ** を使用してステートメントを繰り返し実行します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-175">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="1bf5c-176">`ExploreIf` の呼び出しの後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-176">Add this code after the call to `ExploreIf`:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="1bf5c-177">`while` ステートメントは、条件を確認して `while` に続くステートメントまたはステートメント ブロックを実行します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-177">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="1bf5c-178">条件が false になるまで、条件の確認とステートメントの実行を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-178">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="1bf5c-179">この例では、もう 1 つ新しい演算子が使用されています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-179">There's one other new operator in this example.</span></span> <span data-ttu-id="1bf5c-180">`counter` 変数のあとにある `++` は、**インクリメント** 演算子です。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-180">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="1bf5c-181">`counter` の値に 1 を足し、その値を `counter` 変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-181">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bf5c-182">コードを実行したときに `while` のループ条件が false に切り替わることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-182">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="1bf5c-183">それ以外の場合は、プログラムが終了することのない **無限ループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-183">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="1bf5c-184">**CTRL-C** またはその他の方法でプログラムを強制的に終了する必要があるため、このサンプルでは実践しません。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-184">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="1bf5c-185">`while` ループは、条件を判定してから `while` に続くコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-185">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="1bf5c-186">`do` ... `while` ループは、最初にコードを実行してからその条件を確認します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-186">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="1bf5c-187">*do while* ループを次のコードで示します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-187">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="1bf5c-188">この `do` ループと先述の `while` ループの出力は同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-188">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="1bf5c-189">for ループの処理</span><span class="sxs-lookup"><span data-stu-id="1bf5c-189">Work with the for loop</span></span>

<span data-ttu-id="1bf5c-190">C# では **for** ループがよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-190">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="1bf5c-191">次のコードを試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-191">Try this code:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="1bf5c-192">前のコードは、既に使用した `while` ループや `do` ループと同じ機能を持っています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-192">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="1bf5c-193">`for` ステートメントは 3 つの部分に分かれてその機能を制御します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-193">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="1bf5c-194">最初の部分は、**for 初期化子** です。`int index = 0;` は、`index` がループ変数であることを宣言し、その初期値を `0` に設定しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-194">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="1bf5c-195">2 つ目の部分は、**for 条件** です。`index < 10` は、counter の値が 10 未満である間は `for` ループが実行され続けることを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-195">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="1bf5c-196">最後の部分は、**for 反復子** です。`index++` は、`for` ステートメントに続くブロックを実行したあとにループ変数を変更する方法を指定しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-196">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="1bf5c-197">ここでは、ブロックが実行されるごとに `index` が 1 ずつ増加するよう指定しています。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-197">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="1bf5c-198">自分で試してみてください。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-198">Experiment yourself.</span></span> <span data-ttu-id="1bf5c-199">次のバリエーションをそれぞれ試してみます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-199">Try each of the following variations:</span></span>

- <span data-ttu-id="1bf5c-200">初期化子を変更して別の値で開始する。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-200">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="1bf5c-201">条件を変更して別の値で停止する。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-201">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="1bf5c-202">完了したら次に進み、学習したことを使用して自分でいくつかのコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-202">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="1bf5c-203">このチュートリアルでは説明していないループ ステートメントが1つあります。`foreach` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-203">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="1bf5c-204">`foreach` ステートメントは、一連の項目内のすべての項目に対してステートメントを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-204">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="1bf5c-205">これは、"*コレクション*" で最もよく使用されます。次のチュートリアルで説明します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-205">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="1bf5c-206">入れ子になったループの作成</span><span class="sxs-lookup"><span data-stu-id="1bf5c-206">Created nested loops</span></span>

<span data-ttu-id="1bf5c-207">`while`、`do`、または `for` ループを別のループ内に入れ子にして、外側のループの各項目を内側のループの各項目と組み合わせて使用してマトリックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-207">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="1bf5c-208">行と列を表す一連の英数字ペアを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-208">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="1bf5c-209">1 つの `for` ループで行を生成できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-209">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="1bf5c-210">別のループで列を生成できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-210">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="1bf5c-211">一方のループをもう一方のループ内に入れ子にして、ペアを形成することができます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-211">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="1bf5c-212">外側のループは、内側のループが完全に実行されるたびに 1 回インクリメントされることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-212">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="1bf5c-213">行と列の入れ子を逆にし、自分で変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-213">Reverse the row and column nesting, and see the changes for yourself.</span></span> <span data-ttu-id="1bf5c-214">終わったら、このセクションのコードを `ExploreLoops()` というメソッドに入れます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-214">When you're done, place the code from this section in a method called `ExploreLoops()`.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="1bf5c-215">分岐とループの組み合わせ</span><span class="sxs-lookup"><span data-stu-id="1bf5c-215">Combine branches and loops</span></span>

<span data-ttu-id="1bf5c-216">C# 言語における `if` ステートメントとループ構造を見てきました。では、1 から 20 の整数のうち 3 で割り切れる数の合計を求める C# コードを記述できるか確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-216">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="1bf5c-217">次にいくつかヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-217">Here are a few hints:</span></span>

- <span data-ttu-id="1bf5c-218">`%` 演算子は、除算演算の剰余を算出します。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-218">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="1bf5c-219">`if` ステートメントは、数を合計に入れるべきかどうか確認する条件を作ります。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-219">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="1bf5c-220">`for` ループは、1 から 20 までのすべての数を 1 つずつ確認する一連の手順を繰り返すのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-220">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="1bf5c-221">ご自身で試してみてください。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-221">Try it yourself.</span></span> <span data-ttu-id="1bf5c-222">そして自分がとった方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-222">Then check how you did.</span></span> <span data-ttu-id="1bf5c-223">答えは 63 になるはずです。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-223">You should get 63 for an answer.</span></span> <span data-ttu-id="1bf5c-224">[GitHub で完成版のコードを表示する](https://github.com/dotnet/samples/blob/main/csharp/branches-quickstart/Program.cs#L87-L95)と、考えられる答えの 1 つを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-224">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/blob/main/csharp/branches-quickstart/Program.cs#L87-L95).</span></span>

<span data-ttu-id="1bf5c-225">これで "分岐とループ" に関するチュートリアルは終了です。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-225">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="1bf5c-226">続けて独自の開発環境で[配列とコレクション](arrays-and-collections.md)のチュートリアルに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-226">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="1bf5c-227">次の記事でこれらの概念の詳細を学習できます。</span><span class="sxs-lookup"><span data-stu-id="1bf5c-227">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="1bf5c-228">if と else ステートメント</span><span class="sxs-lookup"><span data-stu-id="1bf5c-228">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="1bf5c-229">while ステートメント</span><span class="sxs-lookup"><span data-stu-id="1bf5c-229">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="1bf5c-230">do ステートメント</span><span class="sxs-lookup"><span data-stu-id="1bf5c-230">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="1bf5c-231">for ステートメント</span><span class="sxs-lookup"><span data-stu-id="1bf5c-231">For statement</span></span>](../../language-reference/keywords/for.md)
