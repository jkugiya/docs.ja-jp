---
title: コレクションでの作業 - C# チュートリアルの概要
description: このチュートリアルでは、リスト コレクションについて確認して C# を学習します。
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 4ecd2cfebddf460d3766d708d2f6740bd1c6e29a
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585664"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="5aacf-103">リスト型を使用したデータ コレクションの管理について説明します</span><span class="sxs-lookup"><span data-stu-id="5aacf-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="5aacf-104">このチュートリアルでは、C# 言語の概要と <xref:System.Collections.Generic.List%601> クラスの基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5aacf-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="5aacf-105">Prerequisites</span></span>

<span data-ttu-id="5aacf-106">このチュートリアルでは、ローカル開発用にセットアップされたコンピューターがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5aacf-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="5aacf-107">Windows、Linux、または macOS で、.NET CLI を使用してアプリケーションを作成、ビルド、実行できます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="5aacf-108">Windows では、Visual Studio 2019 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-108">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="5aacf-109">セットアップの手順については、「[ローカル環境をセットアップする](local-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5aacf-109">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="5aacf-110">基本のリストの例</span><span class="sxs-lookup"><span data-stu-id="5aacf-110">A basic list example</span></span>

<span data-ttu-id="5aacf-111">*list-tutorial* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-111">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="5aacf-112">それを現在のディレクトリとし、`dotnet new console` を実行します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-112">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="5aacf-113">好みのエディターで *Program.cs* を開き、既存のコードを次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-113">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="5aacf-114">`<name>` をユーザー名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="5aacf-115">*Program.cs* を保存します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-115">Save *Program.cs*.</span></span> <span data-ttu-id="5aacf-116">コンソール ウィンドウに「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="5aacf-117">文字列のリストを作成し、そのリストに 3 つの名前を追加し、それらの名前をすべて大文字で出力しました。</span><span class="sxs-lookup"><span data-stu-id="5aacf-117">You've created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="5aacf-118">先のチュートリアルで学習した概念を使用して、リストをループしています。</span><span class="sxs-lookup"><span data-stu-id="5aacf-118">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="5aacf-119">名前を表示するコードは、[文字列補間](../../language-reference/tokens/interpolated.md)機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-119">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="5aacf-120">`string` の前に文字 `$` を配置すると、文字列宣言に C# コードを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="5aacf-121">実際の文字列は、生成する値でその C# コードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="5aacf-122">この例では、<xref:System.String.ToUpper%2A> メソッドを呼び出したため、文字列は `{name.ToUpper()}` をそれぞれの名前に置き換え、文字を大文字に変換しています。</span><span class="sxs-lookup"><span data-stu-id="5aacf-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="5aacf-123">続けて確認していきましょう。</span><span class="sxs-lookup"><span data-stu-id="5aacf-123">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="5aacf-124">リスト コンテンツを変更する</span><span class="sxs-lookup"><span data-stu-id="5aacf-124">Modify list contents</span></span>

<span data-ttu-id="5aacf-125">作成したコレクションは <xref:System.Collections.Generic.List%601> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="5aacf-126">この型は、要素のシーケンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-126">This type stores sequences of elements.</span></span> <span data-ttu-id="5aacf-127">要素の型を山かっこの内側で指定します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-127">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="5aacf-128">この <xref:System.Collections.Generic.List%601> 型の重要な点は増減が可能で、要素を追加したり削除したりできることです。</span><span class="sxs-lookup"><span data-stu-id="5aacf-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="5aacf-129">`Main` メソッドの閉じかっこ `}` の前に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-129">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="5aacf-130">さらに 2 つの名前をリストの末尾に追加しました。</span><span class="sxs-lookup"><span data-stu-id="5aacf-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="5aacf-131">また、1 つを削除しました。</span><span class="sxs-lookup"><span data-stu-id="5aacf-131">You've also removed one as well.</span></span> <span data-ttu-id="5aacf-132">ファイルを保存し、「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-132">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="5aacf-133"><xref:System.Collections.Generic.List%601> を使用すると、**インデックス** でも個々の項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="5aacf-134">リスト名に続く `[` と `]` のトークンの間にインデックスを記述します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="5aacf-135">C# では、初めのインデックスには 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="5aacf-136">追加したコードのすぐ下に次のコードを追加して試します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="5aacf-137">リストの末尾を越えてインデックスにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5aacf-137">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="5aacf-138">インデックスは 0 から始まるため、有効なインデックスの最大値はリスト内の項目の数より 1 小さくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5aacf-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="5aacf-139"><xref:System.Collections.Generic.List%601.Count%2A> プロパティを使用すれば、リストの長さを確認できます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="5aacf-140">次のコードを Main メソッドの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="5aacf-141">ファイルを保存し、もう一度「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-141">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="5aacf-142">リストを検索して並び替える</span><span class="sxs-lookup"><span data-stu-id="5aacf-142">Search and sort lists</span></span>

<span data-ttu-id="5aacf-143">サンプルでは比較的小さいリストを使用していますが、ご利用のアプリケーションでは、より多くの (場合によっては何千もの) 要素が含まれるリストを作成することもよくあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="5aacf-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="5aacf-144">そうした大規模なコレクションの中から要素を見つけるには、別々の項目をリストで検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5aacf-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="5aacf-145"><xref:System.Collections.Generic.List%601.IndexOf%2A> メソッドは項目を検索し、その項目のインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="5aacf-146">項目がリストにない場合、`IndexOf` は `-1` を返します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-146">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="5aacf-147">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-147">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="5aacf-148">同じように、リスト内の項目を並び替えできます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-148">The items in your list can be sorted as well.</span></span> <span data-ttu-id="5aacf-149"><xref:System.Collections.Generic.List%601.Sort%2A> メソッドは、リスト内のすべての項目を正規順序 (文字列の場合はアルファベット順) で並び替えます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-149">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="5aacf-150">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-150">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="5aacf-151">ファイルを保存し、「`dotnet run`」と入力してこの最新バージョンを試します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-151">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="5aacf-152">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5aacf-152">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="5aacf-153">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="5aacf-153">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="5aacf-154">`Main` メソッドの名前を `WorkingWithStrings` に変更し、`WorkingWithStrings` を呼び出す新しい `Main` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-154">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="5aacf-155">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5aacf-155">When you've finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="5aacf-156">その他の型のリスト</span><span class="sxs-lookup"><span data-stu-id="5aacf-156">Lists of other types</span></span>

<span data-ttu-id="5aacf-157">ここまでは、リスト内で `string` 型を使用してきました。</span><span class="sxs-lookup"><span data-stu-id="5aacf-157">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="5aacf-158">別の型を使用して <xref:System.Collections.Generic.List%601> を作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5aacf-158">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="5aacf-159">数値のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-159">Let's build a set of numbers.</span></span>

<span data-ttu-id="5aacf-160">新しい `Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-160">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="5aacf-161">これにより整数のリストが作成され、最初の 2 つの整数が値 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-161">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="5aacf-162">これらは、数列の 1 つである *フィボナッチ数列* の最初の 2 つの値です。</span><span class="sxs-lookup"><span data-stu-id="5aacf-162">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="5aacf-163">次のフィボナッチ数はそれぞれ、その直前の 2 つの数値の合計を取得することによって得られます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-163">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="5aacf-164">このコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-164">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="5aacf-165">ファイルを保存し、「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-165">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="5aacf-166">このセクションにだけ集中したいときは、`WorkingWithStrings();` を呼び出すコードはコメント アウトしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="5aacf-166">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="5aacf-167">`// WorkingWithStrings();` のように、呼び出しの前に `/` 文字を 2 つ記述します。</span><span class="sxs-lookup"><span data-stu-id="5aacf-167">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="5aacf-168">課題</span><span class="sxs-lookup"><span data-stu-id="5aacf-168">Challenge</span></span>

<span data-ttu-id="5aacf-169">このレッスンと以前のレッスンの中から、いくつかの概念を理解できているかどうかを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5aacf-169">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="5aacf-170">ここまでフィボナッチ数を使用して作成してきたコードを使ってください。</span><span class="sxs-lookup"><span data-stu-id="5aacf-170">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="5aacf-171">シーケンスの最初の 20 個の数を生成するコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5aacf-171">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="5aacf-172">(ヒント: フィボナッチ数の 20 番目の数は 6765 です。)</span><span class="sxs-lookup"><span data-stu-id="5aacf-172">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="5aacf-173">課題完了</span><span class="sxs-lookup"><span data-stu-id="5aacf-173">Complete challenge</span></span>

<span data-ttu-id="5aacf-174">[GitHub にある完成したサンプル コードを表示すること](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)で、ソリューションの例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-174">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="5aacf-175">ループの繰り返しごとに、リストの最後の 2 つの整数を取得して合計し、その値をリストに追加しています。</span><span class="sxs-lookup"><span data-stu-id="5aacf-175">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="5aacf-176">このループは、20 個の項目がリストに追加されるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-176">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="5aacf-177">おつかれさまでした。リストについてのチュートリアルはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="5aacf-177">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="5aacf-178">続けて独自の開発環境で[クラスの概要](introduction-to-classes.md)のチュートリアルに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-178">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="5aacf-179">`List` 型の使用方法の詳細については、[コレクション](../../../standard/collections/index.md)に関する .NET 基礎の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5aacf-179">You can learn more about working with the `List` type in the .NET fundamentals article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="5aacf-180">その他の多くのコレクション型についても学習できます。</span><span class="sxs-lookup"><span data-stu-id="5aacf-180">You'll also learn about many other collection types.</span></span>
