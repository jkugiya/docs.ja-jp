---
title: C# における数値 - C# の概要に関するチュートリアル
description: 数値型とその用途、プロパティ、メソッドを詳しく見ていくことで C# について学習します。
ms.date: 02/05/2021
ms.openlocfilehash: d6546fc8ac2609066a4f9b829749a4091fce7ce6
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881108"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="9a78b-103">C\# で整数と浮動小数点数を操作する</span><span class="sxs-lookup"><span data-stu-id="9a78b-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="9a78b-104">このチュートリアルでは、対話形式で C# の数値型について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="9a78b-105">少量のコードを記述したら、そのコードをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="9a78b-106">このチュートリアルには、C# の数値と算術演算に関する一連のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="9a78b-107">これらのレッスンでは、C# 言語の基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a78b-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="9a78b-108">Prerequisites</span></span>

<span data-ttu-id="9a78b-109">このチュートリアルでは、ローカル開発用にセットアップされたコンピューターがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="9a78b-110">Windows、Linux、または macOS で、.NET CLI を使用してアプリケーションを作成、ビルド、実行できます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="9a78b-111">Mac または Windows では、Visual Studio 2019 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-111">On Mac or Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="9a78b-112">セットアップの手順については、「[ローカル環境をセットアップする](local-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="9a78b-113">整数の演算の確認</span><span class="sxs-lookup"><span data-stu-id="9a78b-113">Explore integer math</span></span>

<span data-ttu-id="9a78b-114">「*numbers-quickstart*」という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-114">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="9a78b-115">それを現在のディレクトリにして、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-115">Make it the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="9a78b-116">好みのエディターで *Program.cs* を開き、ファイルの内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-116">Open *Program.cs* in your favorite editor, and replace the contents of the file with the following code:</span></span>

```csharp
using System;

int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="9a78b-117">コマンド ウィンドウで「`dotnet run`」を入力し、このコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-117">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="9a78b-118">整数を使用した基本的な算術演算の 1 つを確認しました。</span><span class="sxs-lookup"><span data-stu-id="9a78b-118">You've seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="9a78b-119">`int` 型は、**整数** を表します (ゼロ、正の整数、または負の整数)。</span><span class="sxs-lookup"><span data-stu-id="9a78b-119">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="9a78b-120">加算には `+` 記号を使用します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-120">You use the `+` symbol for addition.</span></span> <span data-ttu-id="9a78b-121">他の一般的な整数の算術演算には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-121">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="9a78b-122">`-`: 減算</span><span class="sxs-lookup"><span data-stu-id="9a78b-122">`-` for subtraction</span></span>
- <span data-ttu-id="9a78b-123">`*`: 乗算</span><span class="sxs-lookup"><span data-stu-id="9a78b-123">`*` for multiplication</span></span>
- <span data-ttu-id="9a78b-124">`/`: 除算</span><span class="sxs-lookup"><span data-stu-id="9a78b-124">`/` for division</span></span>

<span data-ttu-id="9a78b-125">まずは、上記の各種演算を実行してみます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-125">Start by exploring those different operations.</span></span> <span data-ttu-id="9a78b-126">`c` の値を記述した行の後に、次の数行を追加します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-126">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="9a78b-127">コマンド ウィンドウで「`dotnet run`」を入力し、このコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-127">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="9a78b-128">必要であれば、同じ行で複数の算術演算を記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-128">You can also experiment by writing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="9a78b-129">例として `c = a + b - 12 * 17;` を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-129">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="9a78b-130">変数と定数を混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-130">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="9a78b-131">C# (または何らかのプログラミング言語) について詳しく学習するに従い、コードを記述する際にミスをすることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="9a78b-131">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="9a78b-132">**コンパイラ** は、そうしたエラーを発見して報告します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-132">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="9a78b-133">エラー メッセージが含まれる場合は、例のコードと自分のウィンドウのコードをよく調べて、修正する箇所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-133">When the contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span> <span data-ttu-id="9a78b-134">こうした実習が C# コードの構造を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-134">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="9a78b-135">最初の手順が完了しました。</span><span class="sxs-lookup"><span data-stu-id="9a78b-135">You've finished the first step.</span></span> <span data-ttu-id="9a78b-136">次のセクションを始める前に、現在のコードを別の "*メソッド*" に移動しましょう。</span><span class="sxs-lookup"><span data-stu-id="9a78b-136">Before you start the next section, let's move the current code into a separate *method*.</span></span> <span data-ttu-id="9a78b-137">メソッドは、グループ化された一連のステートメントであり、名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-137">A method is a series of statements grouped together and given a name.</span></span> <span data-ttu-id="9a78b-138">メソッドを呼び出すには、メソッドの名前の後に `()` を記述します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-138">You call a method by writing the method's name followed by `()`.</span></span> <span data-ttu-id="9a78b-139">コードをメソッドに整理しておくと、新しい例の作業を簡単に始めることができます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-139">Organizing your code into methods makes it easier to start working with a new example.</span></span> <span data-ttu-id="9a78b-140">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-140">When you finish, your code should look like this:</span></span>

```csharp
using System;

WorkWithIntegers();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
    int c = a + b;
    Console.WriteLine(c);


    // subtraction
    c = a - b;
    Console.WriteLine(c);

    // multiplication
    c = a * b;
    Console.WriteLine(c);

    // division
    c = a / b;
    Console.WriteLine(c);
}
```

<span data-ttu-id="9a78b-141">`WorkWithIntegers();` の行でメソッドを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-141">The line `WorkWithIntegers();` invokes the method.</span></span> <span data-ttu-id="9a78b-142">その後のコードでメソッドが宣言され、定義されています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-142">The following code declares the method and defines it.</span></span>

## <a name="explore-order-of-operations"></a><span data-ttu-id="9a78b-143">演算の順序の確認</span><span class="sxs-lookup"><span data-stu-id="9a78b-143">Explore order of operations</span></span>

<span data-ttu-id="9a78b-144">`WorkingWithIntegers()` の呼び出しをコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="9a78b-144">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="9a78b-145">こうしておくと、このセクションの作業を進めるにあたって出力がすっきりします。</span><span class="sxs-lookup"><span data-stu-id="9a78b-145">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkWithIntegers();
```

<span data-ttu-id="9a78b-146">C# では、`//` の後ろが **コメント** になります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-146">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="9a78b-147">コードとしては実行せずにソース コード内に残したい任意のテキストを、コメントにすることができます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-147">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="9a78b-148">コンパイラは、コメントから実行可能コードを生成しません。</span><span class="sxs-lookup"><span data-stu-id="9a78b-148">The compiler doesn't generate any executable code from comments.</span></span> <span data-ttu-id="9a78b-149">`WorkWithIntegers()` はメソッドであるため、コメントアウトする必要があるのは 1 行だけです。</span><span class="sxs-lookup"><span data-stu-id="9a78b-149">Because `WorkWithIntegers()` is a method, you need to only comment out one line.</span></span>

<span data-ttu-id="9a78b-150">C# 言語は、数学で学んだ規則と同じ規則で各演算の優先順位を定義します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-150">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span> <span data-ttu-id="9a78b-151">乗算と除算は、加算と減算よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-151">Multiplication and division take precedence over addition and subtraction.</span></span> <span data-ttu-id="9a78b-152">`WorkWithIntegers()` の呼び出しの後に次のコードを追加し、`dotnet run` を実行して、それを調べます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-152">Explore that by adding the following code after the call to `WorkWithIntegers()`, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="9a78b-153">出力を見ると、加算の前に乗算が実行されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-153">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="9a78b-154">最初に実行したい演算を囲むように丸かっこを追加することで、演算の順序を変えることができます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-154">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="9a78b-155">次の行を追加して、もう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-155">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="9a78b-156">さまざまな演算を多数組み合わせて、他にも試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9a78b-156">Explore more by combining many different operations.</span></span> <span data-ttu-id="9a78b-157">次の行のようなものを何か追加します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-157">Add something like the following lines.</span></span> <span data-ttu-id="9a78b-158">もう一度 `dotnet run` を実行してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-158">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="9a78b-159">整数について面白い動作をしていることに気づいたでしょうか。</span><span class="sxs-lookup"><span data-stu-id="9a78b-159">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="9a78b-160">結果に小数点や小数部分が含まれると予想される場合でも、整数の除算は常に整数の結果を算出します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-160">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="9a78b-161">この動作を確認できない場合は、次のコードを試してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-161">If you haven't seen this behavior, try the following code:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="9a78b-162">もう一度 `dotnet run` を入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-162">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="9a78b-163">続行する前に、このセクションで記述したコードをすべて新しいメソッドに移します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-163">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="9a78b-164">新しいメソッドを `OrderPrecedence` とします。</span><span class="sxs-lookup"><span data-stu-id="9a78b-164">Call that new method `OrderPrecedence`.</span></span> <span data-ttu-id="9a78b-165">コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-165">Your code should look something like this:</span></span>

```csharp
using System;

// WorkWithIntegers();
OrderPrecedence();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
    int c = a + b;
    Console.WriteLine(c);


    // subtraction
    c = a - b;
    Console.WriteLine(c);

    // multiplication
    c = a * b;
    Console.WriteLine(c);

    // division
    c = a / b;
    Console.WriteLine(c);
}

void OrderPrecedence()
{
    int a = 5;
    int b = 4;
    int c = 2;
    int d = a + b * c;
    Console.WriteLine(d);

    d = (a + b) * c;
    Console.WriteLine(d);

    d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
    Console.WriteLine(d);

    int e = 7;
    int f = 4;
    int g = 3;
    int h = (e + f) / g;
    Console.WriteLine(h);
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="9a78b-166">整数の有効桁数と制限の確認</span><span class="sxs-lookup"><span data-stu-id="9a78b-166">Explore integer precision and limits</span></span>

<span data-ttu-id="9a78b-167">この最後のサンプルでは、整数の除算における結果の切り捨てについて確認します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-167">That last sample showed you that integer division truncates the result.</span></span> <span data-ttu-id="9a78b-168">**modulo** 演算子 (`%` 文字) を使用して、**剰余** を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-168">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="9a78b-169">`OrderPrecedence()` のメソッド呼び出しの後で、次のコードを試します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-169">Try the following code after the method call to `OrderPrecedence()`:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="9a78b-170">C# の整数型は算術における整数ともう 1 つ異なる点があります。それは `int` 型には最小値と最大値の制限があるということです。</span><span class="sxs-lookup"><span data-stu-id="9a78b-170">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="9a78b-171">次のコードを追加して、それらの制限を確認します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-171">Add this code to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="9a78b-172">計算によってこれらの制限を超える値が作られると、**アンダーフロー** または **オーバーフロー** の状態になります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-172">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="9a78b-173">計算の結果が 1 つの制限からもう 1 つの制限に折り返されているように見えます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-173">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="9a78b-174">次の 2 行を追加して、例を確認します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-174">Add these two lines to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="9a78b-175">計算の結果が最小値の (負の) 整数に極めて近いことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-175">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="9a78b-176">これは `min + 2` と同じです。</span><span class="sxs-lookup"><span data-stu-id="9a78b-176">It's the same as `min + 2`.</span></span> <span data-ttu-id="9a78b-177">加算演算が許容された整数値を **オーバーフロー** しました。</span><span class="sxs-lookup"><span data-stu-id="9a78b-177">The addition operation **overflowed** the allowed values for integers.</span></span> <span data-ttu-id="9a78b-178">整数がオーバーフローして最大値から最小値に ”折り返され” たため、計算結果が非常に大きな負の値になっています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-178">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="9a78b-179">他にもさまざまな制限や有効桁数を持つ数値型があり、`int` 型がご自分のニーズと合わない場合は、そちらも使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-179">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="9a78b-180">次に、その他の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-180">Let's explore those other types next.</span></span> <span data-ttu-id="9a78b-181">次のセクションを始める前に、このセクションで記述したコードを別のメソッドに移します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-181">Before you start the next section, move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="9a78b-182">これに `TestLimits` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-182">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="9a78b-183">double 型の処理</span><span class="sxs-lookup"><span data-stu-id="9a78b-183">Work with the double type</span></span>

<span data-ttu-id="9a78b-184">`double` 数値型は、倍精度浮動小数点数を表します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-184">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="9a78b-185">こうした用語を初めて見た人もいるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="9a78b-185">Those terms may be new to you.</span></span> <span data-ttu-id="9a78b-186">**浮動小数点** 数は、非常に大きな、または非常に小さな、整数ではない数値を表すのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-186">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="9a78b-187">**倍精度** は、値の保管に使用される二進数の数値を表す相対語です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-187">**Double-precision** is a relative term that describes the number of binary digits used to store the value.</span></span> <span data-ttu-id="9a78b-188">**倍精度** 数値は、**単精度** に比べ、二進数の数値が 2 倍になります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-188">**Double precision** numbers have twice the number of binary digits as **single-precision**.</span></span> <span data-ttu-id="9a78b-189">最近のコンピューターでは、単精度よりも倍精度の数値を使用する方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-189">On modern computers, it's more common to use double precision than single precision numbers.</span></span> <span data-ttu-id="9a78b-190">**単精度** 数値は、`float` キーワードを使用して宣言されます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-190">**Single precision** numbers are declared using the `float` keyword.</span></span> <span data-ttu-id="9a78b-191">確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9a78b-191">Let's explore.</span></span> <span data-ttu-id="9a78b-192">次のコードを追加して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-192">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="9a78b-193">計算結果に商の小数部分が含まれていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-193">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="9a78b-194">double 型を使用して、もう少し複雑な式を試します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-194">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="9a78b-195">double 値は整数値よりも範囲が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-195">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="9a78b-196">これまでに記述したコードの下で、次のコードを試します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-196">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="9a78b-197">これらの値は指数表記で出力されます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-197">These values are printed in scientific notation.</span></span> <span data-ttu-id="9a78b-198">`E` の左側は有効数字です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-198">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="9a78b-199">右側の数値は指数であり、10 の累乗です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-199">The number to the right is the exponent, as a power of 10.</span></span> <span data-ttu-id="9a78b-200">算術における 10 進数と同じように、C# における double には丸め誤差が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-200">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="9a78b-201">次のコードを試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9a78b-201">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="9a78b-202">`0.3` の循環小数は `1/3` と完全に同じではありません。</span><span class="sxs-lookup"><span data-stu-id="9a78b-202">You know that `0.3` repeating isn't exactly the same as `1/3`.</span></span>

<span data-ttu-id="9a78b-203">***課題***</span><span class="sxs-lookup"><span data-stu-id="9a78b-203">***Challenge***</span></span>

<span data-ttu-id="9a78b-204">`double` 型を使用して、大きい値や小さい値、乗算、除算などの計算してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9a78b-204">Try other calculations with large numbers, small numbers, multiplication, and division using the `double` type.</span></span> <span data-ttu-id="9a78b-205">もっと複雑な計算を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-205">Try more complicated calculations.</span></span> <span data-ttu-id="9a78b-206">しばらく試してみたあとは、これまでに記述したコードを新しいメソッドに移します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-206">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="9a78b-207">新しいメソッドに `WorkWithDoubles` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-207">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-decimal-types"></a><span data-ttu-id="9a78b-208">10 進型を扱う</span><span class="sxs-lookup"><span data-stu-id="9a78b-208">Work with decimal types</span></span>

<span data-ttu-id="9a78b-209">C# の基本的な数値型である整数と double について見てきました。</span><span class="sxs-lookup"><span data-stu-id="9a78b-209">You've seen the basic numeric types in C#: integers and doubles.</span></span> <span data-ttu-id="9a78b-210">もう 1 つ知っておくべき型として、`decimal` 型があります。</span><span class="sxs-lookup"><span data-stu-id="9a78b-210">There's one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="9a78b-211">`decimal` 型は、`double` 型よりも範囲は小さいですが、有効桁数が大きい型です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-211">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="9a78b-212">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="9a78b-212">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="9a78b-213">`double` 型よりも範囲が小さいことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-213">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="9a78b-214">次のコードを実行すると、decimal 型では有効桁数がより大きいことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-214">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="9a78b-215">数値の末尾の `M` は、定数では `decimal` 型を使用する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-215">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span> <span data-ttu-id="9a78b-216">それ以外の場合、コンパイラは `double` 型を想定します。</span><span class="sxs-lookup"><span data-stu-id="9a78b-216">Otherwise, the compiler assumes the `double` type.</span></span>

> [!NOTE]
> <span data-ttu-id="9a78b-217">文字 `M` は、`double` キーワードと `decimal` キーワードの間で最も視覚的に区別される文字として選択されています。</span><span class="sxs-lookup"><span data-stu-id="9a78b-217">The letter `M` was chosen as the most visually distinct letter between the `double` and `decimal` keywords.</span></span>

<span data-ttu-id="9a78b-218">decimal 型を使用した演算では、小数点の右側の桁数がより多いことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-218">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="9a78b-219">***課題***</span><span class="sxs-lookup"><span data-stu-id="9a78b-219">***Challenge***</span></span>

<span data-ttu-id="9a78b-220">さまざまな数値型を確認したので、次は半径が 2.50 センチメートルの円の面積を計算するコードを記述してみます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-220">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="9a78b-221">円の面積は、半径の 2 乗 x 円周率です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-221">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="9a78b-222">ヒント: .NET には <xref:System.Math.PI?displayProperty=nameWithType> という円周率の定数があり、その値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-222">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> <span data-ttu-id="9a78b-223"><xref:System.Math.PI?displayProperty=nameWithType> は、`System.Math` 名前空間で宣言されているすべての定数と同様に、`double` 値です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-223"><xref:System.Math.PI?displayProperty=nameWithType>, like all constants declared in the `System.Math` namespace, is a `double` value.</span></span> <span data-ttu-id="9a78b-224">そのため、この課題では `decimal` 値の代わりに `double` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-224">For that reason, you should use `double` instead of `decimal` values for this challenge.</span></span>

<span data-ttu-id="9a78b-225">答えは 19 と 20 の間になるはずです。</span><span class="sxs-lookup"><span data-stu-id="9a78b-225">You should get an answer between 19 and 20.</span></span> <span data-ttu-id="9a78b-226">[GitHub にある完成版のサンプル コード](https://github.com/dotnet/samples/tree/main/csharp/numbers-quickstart/Program.cs#L9-L11)で答えを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-226">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/main/csharp/numbers-quickstart/Program.cs#L9-L11).</span></span>

<span data-ttu-id="9a78b-227">お好みで他の数式を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="9a78b-227">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="9a78b-228">これで "C# の数値" に関するクイックスタートは終了です。</span><span class="sxs-lookup"><span data-stu-id="9a78b-228">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="9a78b-229">続けて独自の開発環境で[分岐とループ](branches-and-loops-local.md)のクイックスタートに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-229">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="9a78b-230">C# の数値の詳細については、次の記事で学習できます。</span><span class="sxs-lookup"><span data-stu-id="9a78b-230">You can learn more about numbers in C# in the following articles:</span></span>

- [<span data-ttu-id="9a78b-231">整数数値型</span><span class="sxs-lookup"><span data-stu-id="9a78b-231">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="9a78b-232">浮動小数点数値型</span><span class="sxs-lookup"><span data-stu-id="9a78b-232">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="9a78b-233">組み込みの数値変換</span><span class="sxs-lookup"><span data-stu-id="9a78b-233">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
