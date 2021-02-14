---
title: 最上位レベルのステートメント - C# チュートリアル
description: このチュートリアルでは、最上位レベルのステートメントを使用して、アイデアを探索しながら概念を試して証明する方法を示します
ms.date: 10/28/2020
ms.openlocfilehash: c56a40e7a9715ff0265a897c494b457a32e52df2
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585625"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a><span data-ttu-id="833b2-103">チュートリアル: 学習しながらコードをビルドするために最上位レベルのステートメントを使用してアイデアを探索する</span><span class="sxs-lookup"><span data-stu-id="833b2-103">Tutorial: Explore ideas using top-level statements to build code as you learn</span></span>

<span data-ttu-id="833b2-104">このチュートリアルで学習する内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="833b2-104">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="833b2-105">最上位レベルのステートメントの使用を制御するルールについて学習する。</span><span class="sxs-lookup"><span data-stu-id="833b2-105">Learn the rules governing your use of top-level statements.</span></span>
> - <span data-ttu-id="833b2-106">最上位レベルのステートメントを使用してアルゴリズムを探索する。</span><span class="sxs-lookup"><span data-stu-id="833b2-106">Use top-level statements to explore algorithms.</span></span>
> - <span data-ttu-id="833b2-107">探索を再利用可能なコンポーネントにリファクタリングする。</span><span class="sxs-lookup"><span data-stu-id="833b2-107">Refactor explorations into reusable components.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="833b2-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="833b2-108">Prerequisites</span></span>

<span data-ttu-id="833b2-109">お使いのマシンを、.NET 5 が実行されるように設定する必要があります。これには C# 9 コンパイラが含まれます。</span><span class="sxs-lookup"><span data-stu-id="833b2-109">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="833b2-110">C# 9 コンパイラは [Visual Studio 2019 バージョン 16.9 プレビュー 1](https://visualstudio.microsoft.com/vs/preview/) または [.NET 5.0 SDK](https://dot.net/get-dotnet5) 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-110">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="833b2-111">このチュートリアルでは、.NET と、C# と Visual Studio または .NET Core CLI のいずれかに精通していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="833b2-111">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="start-exploring"></a><span data-ttu-id="833b2-112">実際に使ってみる</span><span class="sxs-lookup"><span data-stu-id="833b2-112">Start exploring</span></span>

<span data-ttu-id="833b2-113">最上位レベルのステートメントを使用すると、プログラムのエントリ ポイントをクラスの静的メソッドに配置することによって必要とされる余分な手続きを避けることができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-113">Top-level statements enable you to avoid the extra ceremony required by placing your program's entry point in a static method in a class.</span></span> <span data-ttu-id="833b2-114">新しいコンソール アプリケーションの一般的な開始点は、次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="833b2-114">The typical starting point for a new console application looks like the following code:</span></span>

```csharp
using System;

namespace Application
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

<span data-ttu-id="833b2-115">上記のコードは、`dotnet new console` コマンドを実行し、新しいコンソール アプリケーションを作成した結果です。</span><span class="sxs-lookup"><span data-stu-id="833b2-115">The preceding code is the result of running the `dotnet new console` command and creating a new console application.</span></span> <span data-ttu-id="833b2-116">これらの 11 行には、実行可能コードが 1 行しか含まれていません。</span><span class="sxs-lookup"><span data-stu-id="833b2-116">Those 11 lines contain only one line of executable code.</span></span> <span data-ttu-id="833b2-117">そのプログラムは、新しい最上位レベルのステートメント機能を使用して簡素化できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-117">You can simplify that program with the new top-level statements feature.</span></span> <span data-ttu-id="833b2-118">これにより、このプログラム内の 2 つを除くすべての行を削除できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-118">That enables you to remove all but two of the lines in this program:</span></span>

```csharp
using System;

Console.WriteLine("Hello World!");
```

<span data-ttu-id="833b2-119">このアクションにより、新しいアイデアの探索を開始するのに必要なものが簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-119">This action simplifies what's needed to begin exploring new ideas.</span></span> <span data-ttu-id="833b2-120">最上位レベルのステートメントをスクリプト作成シナリオで、あるいは探索するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-120">You can use top-level statements for scripting scenarios, or to explore.</span></span> <span data-ttu-id="833b2-121">基本的な作業が完了したら、コードのリファクタリングを開始し、ビルドした再利用可能なコンポーネントに対してメソッド、クラス、またはその他のアセンブリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-121">Once you've got the basics working, you can start refactoring the code and create methods, classes, or other assemblies for reusable components you've built.</span></span> <span data-ttu-id="833b2-122">最上位レベルのステートメントを使用すれば、迅速な実験と初心者向けチュートリアルが可能になります。</span><span class="sxs-lookup"><span data-stu-id="833b2-122">Top-level statements do enable quick experimentation and beginner tutorials.</span></span> <span data-ttu-id="833b2-123">また、実験から完全なプログラムへのスムーズなパスが得られます。</span><span class="sxs-lookup"><span data-stu-id="833b2-123">They also provide a smooth path from experimentation to full programs.</span></span>

<span data-ttu-id="833b2-124">最上位レベルのステートメントは、ファイルに示される順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-124">Top-level statements are executed in the order they appear in the file.</span></span> <span data-ttu-id="833b2-125">最上位レベルのステートメントは、アプリケーション内の 1 つのソース ファイルのみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-125">Top-level statements can only be used in one source file in your application.</span></span> <span data-ttu-id="833b2-126">複数のファイルで使用すると、コンパイラでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="833b2-126">The compiler generates an error if you use them in more than one file.</span></span>

## <a name="build-a-magic-net-answer-machine"></a><span data-ttu-id="833b2-127">マジック .NET 回答マシンをビルドする</span><span class="sxs-lookup"><span data-stu-id="833b2-127">Build a magic .NET answer machine</span></span>

<span data-ttu-id="833b2-128">このチュートリアルでは、"はい" か "いいえ" の質問にランダムな回答で答えるコンソール アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="833b2-128">For this tutorial, let's build a console application that answers a "yes" or "no" question with a random answer.</span></span> <span data-ttu-id="833b2-129">機能は少しずつビルドしていきます。</span><span class="sxs-lookup"><span data-stu-id="833b2-129">You'll build out the functionality step by step.</span></span> <span data-ttu-id="833b2-130">一般的なプログラムの構造に必要な手続きではなく、タスクに専念できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-130">You can focus on your task rather than ceremony needed for the structure of a typical program.</span></span> <span data-ttu-id="833b2-131">その後、機能に問題がなければ、必要に応じてアプリケーションをリファクタリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-131">Then, once you're happy with the functionality, you can refactor the application as you see fit.</span></span>

<span data-ttu-id="833b2-132">まず、質問をコンソールに書き戻すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="833b2-132">A good starting point is to write the question back to the console.</span></span> <span data-ttu-id="833b2-133">まず、次のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="833b2-133">You can start by writing the following code:</span></span>

```csharp
using System;

Console.WriteLine(args);
```

<span data-ttu-id="833b2-134">`args` 変数は宣言しません。</span><span class="sxs-lookup"><span data-stu-id="833b2-134">You don't declare an `args` variable.</span></span> <span data-ttu-id="833b2-135">最上位レベルのステートメントを含む単一のソース ファイルの場合、コンパイラでコマンドライン引数を意味する `args` が認識されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-135">For the single source file that contains your top-level statements, the compiler recognizes `args` to mean the command-line arguments.</span></span> <span data-ttu-id="833b2-136">すべての C# プログラムの場合と同じように、引数の型は `string[]` となります。</span><span class="sxs-lookup"><span data-stu-id="833b2-136">The type of args is a `string[]`, as in all C# programs.</span></span>

<span data-ttu-id="833b2-137">次の `dotnet run` コマンドを実行して、コードをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-137">You can test your code by running the following `dotnet run` command:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

<span data-ttu-id="833b2-138">コマンド ラインの `--` の後の引数は、プログラムに渡されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-138">The arguments after the `--` on the command line are passed to the program.</span></span> <span data-ttu-id="833b2-139">`args` 変数の型を確認できます。それが、コンソールに出力された内容であるためです。</span><span class="sxs-lookup"><span data-stu-id="833b2-139">You can see the type of the `args` variable, because that's what's printed to the console:</span></span>

```console
System.String[]
```

<span data-ttu-id="833b2-140">コンソールに質問を書き込むには、引数を列挙し、それらをスペースで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="833b2-140">To write the question to the console, you'll need to enumerate the arguments and separate them with a space.</span></span> <span data-ttu-id="833b2-141">`WriteLine` 呼び出しを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="833b2-141">Replace the `WriteLine` call with the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="EchoInput":::

<span data-ttu-id="833b2-142">これで、プログラムを実行すると、質問が引数の文字列として正しく表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="833b2-142">Now, when you run the program, it will correctly display the question as a string of arguments.</span></span>

## <a name="respond-with-a-random-answer"></a><span data-ttu-id="833b2-143">ランダムな回答で答える</span><span class="sxs-lookup"><span data-stu-id="833b2-143">Respond with a random answer</span></span>

<span data-ttu-id="833b2-144">質問を問い返した後、ランダムな回答を生成するコードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-144">After echoing the question, you can add the code to generate the random answer.</span></span> <span data-ttu-id="833b2-145">まず、考えられる答えの配列を追加します。</span><span class="sxs-lookup"><span data-stu-id="833b2-145">Start by adding an array of possible answers:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="Answers":::

<span data-ttu-id="833b2-146">この配列には 12 個の答えが含まれており、6 個は肯定的であいまいなものであり、残りの 6 個は否定的なものです。</span><span class="sxs-lookup"><span data-stu-id="833b2-146">This array has 12 answers that are affirmative, six that are non-committal, and six that are negative.</span></span> <span data-ttu-id="833b2-147">次に、配列からランダムな回答を生成して表示する以下のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="833b2-147">Next, add the following code to generate and display a random answer from the array:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="GenerateAnswer":::

<span data-ttu-id="833b2-148">アプリケーションをもう一度実行して、結果を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-148">You can run the application again to see the results.</span></span> <span data-ttu-id="833b2-149">次の出力のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="833b2-149">You should see something like the following output:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

<span data-ttu-id="833b2-150">このコードで質問に回答しますが、もう 1 つ機能を追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="833b2-150">This code answers the questions, but let's add one more feature.</span></span> <span data-ttu-id="833b2-151">たとえば、質問アプリを使用して、答えについての考え方をシミュレートしたいとします。</span><span class="sxs-lookup"><span data-stu-id="833b2-151">You'd like your question app to simulate thinking about the answer.</span></span> <span data-ttu-id="833b2-152">これは、ASCII アニメーションを少し追加し、作業を一時中断して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-152">You can do that by adding a bit of ASCII animation, and pausing while working.</span></span>  <span data-ttu-id="833b2-153">質問を問い返す行の後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="833b2-153">Add the following code after the line that echoes the question:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

<span data-ttu-id="833b2-154">`using` ステートメントをソース ファイルの先頭に追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="833b2-154">You'll also need to add a `using` statement to the top of the source file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="833b2-155">`using` ステートメントは、ファイル内の他のどのステートメントよりも前にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="833b2-155">The `using` statements must be before any other statements in the file.</span></span> <span data-ttu-id="833b2-156">それ以外の場合、コンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="833b2-156">Otherwise, it's a compiler error.</span></span> <span data-ttu-id="833b2-157">プログラムをもう一度実行して、アニメーションを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-157">You can run the program again and see the animation.</span></span> <span data-ttu-id="833b2-158">これにより、エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="833b2-158">That makes a better experience.</span></span> <span data-ttu-id="833b2-159">ご自分の好みに合わせて遅延の長さを試してください。</span><span class="sxs-lookup"><span data-stu-id="833b2-159">Experiment with the length of the delay to match your taste.</span></span>

<span data-ttu-id="833b2-160">上のコードにより、スペースで区切られた一連の回転する行が作成されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-160">The preceding code creates a set of spinning lines separated by a space.</span></span> <span data-ttu-id="833b2-161">`await` キーワードを追加すると、`async` 修飾子を持ち、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> を返すメソッドとしてプログラムのエントリ ポイントを生成するようにコンパイラに指示されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-161">Adding the `await` keyword instructs the compiler to generate the program entry point as a method that has the `async` modifier, and returns a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span></span> <span data-ttu-id="833b2-162">このプログラムからは値が返されないため、プログラムのエントリ ポイントにより `Task` が返されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-162">This program does not return a value, so the program entry point returns a `Task`.</span></span> <span data-ttu-id="833b2-163">プログラムから整数値が返された場合は、最上位レベルのステートメントの末尾に return ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="833b2-163">If your program returns an integer value, you would add a return statement to the end of your top-level statements.</span></span> <span data-ttu-id="833b2-164">その return ステートメントにより、返す整数値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-164">That return statement would specify the integer value to return.</span></span> <span data-ttu-id="833b2-165">最上位レベルのステートメントに `await` 式が含まれている場合は、戻り値の型が <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> になります。</span><span class="sxs-lookup"><span data-stu-id="833b2-165">If your top-level statements include an `await` expression, the return type becomes <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>.</span></span>

## <a name="refactoring-for-the-future"></a><span data-ttu-id="833b2-166">今後のリファクタリング</span><span class="sxs-lookup"><span data-stu-id="833b2-166">Refactoring for the future</span></span>

<span data-ttu-id="833b2-167">プログラムのコードは次のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="833b2-167">Your program should look like the following code:</span></span>

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

<span data-ttu-id="833b2-168">上のコードは適切です。</span><span class="sxs-lookup"><span data-stu-id="833b2-168">The preceding code is reasonable.</span></span> <span data-ttu-id="833b2-169">正常に動作する。</span><span class="sxs-lookup"><span data-stu-id="833b2-169">It works.</span></span> <span data-ttu-id="833b2-170">しかし、再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="833b2-170">But it isn't reusable.</span></span> <span data-ttu-id="833b2-171">これでアプリケーションが動作するようになったので、次は再利用可能な部分を取得します。</span><span class="sxs-lookup"><span data-stu-id="833b2-171">Now that you have the application working, it's time to pull out reusable parts.</span></span>

<span data-ttu-id="833b2-172">候補の 1 つとして、待機中のアニメーションを表示するコードがあります。</span><span class="sxs-lookup"><span data-stu-id="833b2-172">One candidate is the code that displays the waiting animation.</span></span> <span data-ttu-id="833b2-173">このスニペットはメソッドになることがあります。</span><span class="sxs-lookup"><span data-stu-id="833b2-173">That snippet can become a method:</span></span>

<span data-ttu-id="833b2-174">まず、ファイルにローカル関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="833b2-174">You can start by creating a local function in your file.</span></span> <span data-ttu-id="833b2-175">現在のアニメーションを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="833b2-175">Replace the current animation with the following code:</span></span>

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

<span data-ttu-id="833b2-176">前のコードで、main メソッド内にローカル関数が作成されています。</span><span class="sxs-lookup"><span data-stu-id="833b2-176">The preceding code creates a local function inside your main method.</span></span> <span data-ttu-id="833b2-177">それでも再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="833b2-177">That's still not reusable.</span></span> <span data-ttu-id="833b2-178">そのため、そのコードをクラスに抽出します。</span><span class="sxs-lookup"><span data-stu-id="833b2-178">So, extract that code into a class.</span></span> <span data-ttu-id="833b2-179">*utilities.cs* という名前の新しいファイルを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="833b2-179">Create a new file named *utilities.cs* and add the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

<span data-ttu-id="833b2-180">最上位レベルのステートメントは 1 つのファイルにのみ含めることができ、そのファイルには名前空間や型を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="833b2-180">Top-level statements can only be in one file, and that file cannot contain namespaces or types.</span></span>

<span data-ttu-id="833b2-181">最後に、アニメーション コードをクリーンアップして、いくつか重複しているものを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-181">Finally, you can clean the animation code to remove some duplication:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Utilities.cs" ID="Animation":::

<span data-ttu-id="833b2-182">これでアプリケーションが完成し、後で使用するために再利用可能な部分がリファクタリングされました。</span><span class="sxs-lookup"><span data-stu-id="833b2-182">Now you have a complete application, and you've refactored the reusable parts for later use.</span></span> <span data-ttu-id="833b2-183">以下のメイン プログラムの完成版で示されているように、最上位レベルのステートメントから新しいユーティリティ メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-183">You can call the new utility method from your top-level statements, as shown below in the finished version of the main program:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs":::

<span data-ttu-id="833b2-184">これにより、`Utilities.ShowConsoleAnimation` の呼び出しが追加され、別の `using` ステートメントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-184">This adds the call to `Utilities.ShowConsoleAnimation`, and adds an additional `using` statement.</span></span>

## <a name="summary"></a><span data-ttu-id="833b2-185">まとめ</span><span class="sxs-lookup"><span data-stu-id="833b2-185">Summary</span></span>

<span data-ttu-id="833b2-186">最上位レベルのステートメントを利用すると、新しいアルゴリズムを探索するのに使用するシンプルなプログラムをより簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="833b2-186">Top-level statements make it easier to create simple programs for use to explore new algorithms.</span></span> <span data-ttu-id="833b2-187">異なるコード スニペットを試すことで、アルゴリズムを試してみることができます。</span><span class="sxs-lookup"><span data-stu-id="833b2-187">You can experiment with algorithms by trying different snippets of code.</span></span> <span data-ttu-id="833b2-188">動作について学習したら、コードをより保守しやすいようにリファクタリングできます。</span><span class="sxs-lookup"><span data-stu-id="833b2-188">Once you've learned what works, you can refactor the code to be more maintainable.</span></span>

<span data-ttu-id="833b2-189">最上位レベルのステートメントを使用すると、コンソール アプリケーションに基づくプログラムが簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="833b2-189">Top-level statements simplify programs that are based on console applications.</span></span> <span data-ttu-id="833b2-190">これには、Azure Functions、GitHub Actions、およびその他の小規模なユーティリティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="833b2-190">These include Azure functions, GitHub actions, and other small utilities.</span></span>
