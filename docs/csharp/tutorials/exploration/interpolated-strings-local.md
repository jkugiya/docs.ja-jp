---
title: 文字列補間 - C# チュートリアル
description: このチュートリアルでは、C# で文字列補間機能を使用して、大きい文字列で書式設定された計算式の結果を含める方法を示します。
ms.date: 10/23/2018
ms.openlocfilehash: a80f6d6b118a9dfc4e9ada2122dfc374a137fb4e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103206"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="badc4-103">文字列補間を使用し、書式設定された文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="badc4-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="badc4-104">このチュートリアルでは、C# で[文字列補間](../../language-reference/tokens/interpolated.md)を使用して、単一の結果の文字列に値を挿入する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="badc4-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="badc4-105">C# コードを記述し、コードをコンパイルおよび実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="badc4-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="badc4-106">チュートリアルには、値を文字列に挿入し、それらの値の書式をさまざまな方法で設定する方法を示す、一連のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="badc4-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="badc4-107">このチュートリアルでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="badc4-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="badc4-108">Windows、Linux、または macOS 上でローカルの開発環境を設定する手順については、.NET チュートリアル [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) (10 分で Hello World) に記載されています。</span><span class="sxs-lookup"><span data-stu-id="badc4-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="badc4-109">また、使用しているブラウザーでこのチュートリアルの[対話型バージョン](interpolated-strings.yml)を完了することもできます。</span><span class="sxs-lookup"><span data-stu-id="badc4-109">You can also complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="badc4-110">挿入文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="badc4-110">Create an interpolated string</span></span>

<span data-ttu-id="badc4-111">*interpolated* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="badc4-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="badc4-112">それを現在のディレクトリにして、コンソール ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="badc4-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="badc4-113">このコマンドによって、現在のディレクトリに新しい .NET Core コンソール アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="badc4-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="badc4-114">お好みのエディターで *Program.cs* を開き、`Console.WriteLine("Hello World!");` の行を次のコードで置き換えます。`<name>` は自分の名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="badc4-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="badc4-115">コンソール ウィンドウで「`dotnet run`」と入力し、このコードを試します。</span><span class="sxs-lookup"><span data-stu-id="badc4-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="badc4-116">プログラムを実行すると、あいさつ文に自分の名前を含む単一の文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="badc4-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="badc4-117"><xref:System.Console.WriteLine%2A> メソッド呼び出しに含まれる文字列は、*挿入文字列式* です。</span><span class="sxs-lookup"><span data-stu-id="badc4-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="badc4-118">これは、埋め込みコードを含む文字列から (*結果文字列* という) 単一の文字列を構築できる一種のテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="badc4-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="badc4-119">挿入文字列は、文字列に値を挿入したり、文字列を (結合) 連結したりする場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="badc4-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="badc4-120">この簡単な例には、すべての挿入文字列に含める必要がある次の 2 つの要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="badc4-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="badc4-121">始まりの引用符文字の前の `$` で始まる文字列リテラル。</span><span class="sxs-lookup"><span data-stu-id="badc4-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="badc4-122">`$` シンボルと引用符文字の間にスペースを挿入することはできません</span><span class="sxs-lookup"><span data-stu-id="badc4-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="badc4-123">(スペースが含まれている場合の動作を確認したい場合は、`$` 文字の後にスペースを挿入し、ファイルを保存してから、コンソール ウィンドウで「`dotnet run`」と入力してプログラムを再実行します。</span><span class="sxs-lookup"><span data-stu-id="badc4-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="badc4-124">C# コンパイラには、"エラー CS1056:予期しない文字 '$' です" というエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="badc4-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="badc4-125">1 つ以上の *補間式*。</span><span class="sxs-lookup"><span data-stu-id="badc4-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="badc4-126">補間式は、始めかっこと終わりかっこ (`{` と `}`) で示されます。</span><span class="sxs-lookup"><span data-stu-id="badc4-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="badc4-127">かっこ内に (`null` を含む) 値を返す C# 式を配置できます。</span><span class="sxs-lookup"><span data-stu-id="badc4-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="badc4-128">その他のいくつかのデータ型を持つ文字列補間の例をさらにいくつか試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="badc4-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="badc4-129">さまざまなデータ型を含める</span><span class="sxs-lookup"><span data-stu-id="badc4-129">Include different data types</span></span>

<span data-ttu-id="badc4-130">前のセクションでは、文字列補間を使用して、1 つの文字列内に別の文字列を挿入しましたが、</span><span class="sxs-lookup"><span data-stu-id="badc4-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="badc4-131">補間式の結果を任意のデータ型にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="badc4-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="badc4-132">挿入文字列にさまざまなデータ型の値を含めてみましょう。</span><span class="sxs-lookup"><span data-stu-id="badc4-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="badc4-133">次の例では、最初に、`Name` [プロパティ](../../properties.md)と `ToString` [メソッド](../../methods.md)を持つ[クラス](../../programming-guide/classes-and-structs/classes.md) データ型 `Vegetable` を定義します。このメソッドは、<xref:System.Object.ToString?displayProperty=nameWithType> メソッドのビヘイビアーを[オーバーライド](../../language-reference/keywords/override.md)します。</span><span class="sxs-lookup"><span data-stu-id="badc4-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="badc4-134">[`public` アクセス修飾子](../../language-reference/keywords/public.md)により、そのメソッドは、すべてのクライアント コードで `Vegetable` インスタンスの文字列表現を取得するために使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="badc4-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="badc4-135">この例の `Vegetable.ToString` メソッドでは、`Vegetable` [コンストラクター](../../programming-guide/classes-and-structs/constructors.md)で初期化される `Name` プロパティの値を返します。</span><span class="sxs-lookup"><span data-stu-id="badc4-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="badc4-136">次に、[`new` 演算子](../../language-reference/operators/new-operator.md)を使用し、コンストラクター `Vegetable` に名前を指定することで `item` という名前の `Vegetable` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="badc4-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="badc4-137">最後に、`item` 変数を挿入文字列に含めます。ここには、<xref:System.DateTime> 値、<xref:System.Decimal> 値、`Unit` [列挙](../../language-reference/builtin-types/enum.md)値も含まれます。</span><span class="sxs-lookup"><span data-stu-id="badc4-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../language-reference/builtin-types/enum.md) value.</span></span> <span data-ttu-id="badc4-138">エディターのすべての C# コードを以下のコードに置き換えてから、`dotnet run` コマンドを使用して実行します。</span><span class="sxs-lookup"><span data-stu-id="badc4-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;

   public string Name { get; }

   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

<span data-ttu-id="badc4-139">補間文字列の挿入式 `item` は、結果の文字列のテキスト "eggplant" に解決されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="badc4-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="badc4-140">これは、式の結果の型が文字列でない場合に、結果が次の方法で文字列に解決されるためです。</span><span class="sxs-lookup"><span data-stu-id="badc4-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="badc4-141">補間式が `null` の場合、空の文字列 (""、または <xref:System.String.Empty?displayProperty=nameWithType>) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="badc4-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="badc4-142">補間式が `null` でない場合、通常、結果の型の `ToString` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="badc4-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="badc4-143">`Vegetable.ToString` メソッドの実装を更新して、これをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="badc4-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="badc4-144">すべての型にこのメソッドの実装が含まれるため、`ToString` メソッドを実装する必要なない場合があります。</span><span class="sxs-lookup"><span data-stu-id="badc4-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="badc4-145">これをテストするには、例の `Vegetable.ToString` メソッドの定義をコメント アウトします (この操作を行うには、コメント シンボル `//` を前に配置します)。</span><span class="sxs-lookup"><span data-stu-id="badc4-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="badc4-146">出力では、"eggplant" という文字列が完全修飾型名 (この例では "Vegetable") に置き換えられます。これは、<xref:System.Object.ToString?displayProperty=nameWithType> メソッドの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="badc4-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="badc4-147">列挙値の `ToString` メソッドの既定の動作は、値の文字列表現を返すことです。</span><span class="sxs-lookup"><span data-stu-id="badc4-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="badc4-148">この例の出力では、日付の精度が高すぎ ("eggplant" の価格は毎秒変更されることはありません)、価格の値は通貨の単位を示していません。</span><span class="sxs-lookup"><span data-stu-id="badc4-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="badc4-149">次のセクションでは、式の結果における文字列表現の書式を制御することで、こうした問題を修正する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="badc4-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="badc4-150">補間式の書式設定を制御する</span><span class="sxs-lookup"><span data-stu-id="badc4-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="badc4-151">前のセクションでは、適切に書式設定されていない 2 つの文字列が結果文字列に挿入されました。</span><span class="sxs-lookup"><span data-stu-id="badc4-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="badc4-152">1 つは、日付のみが適切な日時の値でした。</span><span class="sxs-lookup"><span data-stu-id="badc4-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="badc4-153">もう 1 つは、通貨単位を示さない価格でした。</span><span class="sxs-lookup"><span data-stu-id="badc4-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="badc4-154">両方の問題には簡単に対処することができます。</span><span class="sxs-lookup"><span data-stu-id="badc4-154">Both issues are easy to address.</span></span> <span data-ttu-id="badc4-155">文字列補間では、特定の型の書式設定を制御する *書式指定文字列* を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="badc4-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="badc4-156">前の例の `Console.WriteLine` 呼び出しを変更し、次の行に示すように、日付と価格の式の書式指定文字列を含めます。</span><span class="sxs-lookup"><span data-stu-id="badc4-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="badc4-157">コロン (":") と書式指定文字列を持つ補間式に従って、書式指定文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="badc4-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="badc4-158">"d" は、短い日付形式を表す[標準の日時書式設定文字列](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)です。</span><span class="sxs-lookup"><span data-stu-id="badc4-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="badc4-159">"C2" は、小数点以下が 2 桁の通貨値として数値を表す[標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md#currency-format-specifier-c)です。</span><span class="sxs-lookup"><span data-stu-id="badc4-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#currency-format-specifier-c) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="badc4-160">.NET ライブラリの多くの型で、定義済みの書式指定文字列セットがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="badc4-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="badc4-161">これらには、数値型と日時型がすべて含まれます。</span><span class="sxs-lookup"><span data-stu-id="badc4-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="badc4-162">書式指定文字列をサポートする型の完全なリストについては、「[.Net 型の書式設定](../../../standard/base-types/formatting-types.md)」記事の「[.NET クラス ライブラリの型および書式指定文字列](../../../standard/base-types/formatting-types.md#format-strings-and-net-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="badc4-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="badc4-163">テキスト エディターで書式指定文字列を変更してみて、変更するたびにプログラムを再実行し、変更が日時と数値の書式設定にどのように影響するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="badc4-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="badc4-164">`{date:d}` の "d" を "t" (短い時刻形式を表示する)、"y" (年と月を表示する)、"yyyy" (4 桁の数字として年を表示する) に変更します。</span><span class="sxs-lookup"><span data-stu-id="badc4-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="badc4-165">`{price:C2}` "C2" を "e" (指数表記の場合) と "F3" (小数点以下が 3 桁の数値の場合) に変更します。</span><span class="sxs-lookup"><span data-stu-id="badc4-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="badc4-166">書式設定を制御するだけでなく、結果の文字列に含まれる書式指定された文字列のフィールドの幅と配置を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="badc4-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="badc4-167">次のセクションでは、この方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="badc4-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="badc4-168">補間式のフィールドの幅と配置を制御する</span><span class="sxs-lookup"><span data-stu-id="badc4-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="badc4-169">通常、補間式の結果が文字列に書式設定される場合、文字列は先頭スペースおよび末尾スペースなしで結果文字列に含まれます。</span><span class="sxs-lookup"><span data-stu-id="badc4-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="badc4-170">通常、データのセットを操作する場合、フィールドの幅とテキストの配置を制御できることで、読みやすい出力を生成できます。</span><span class="sxs-lookup"><span data-stu-id="badc4-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="badc4-171">そのためには、テキスト エディターのすべてのコードを次のコードに置き換えてから、「`dotnet run`」と入力してプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="badc4-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

<span data-ttu-id="badc4-172">作成者の名前は左揃えになり、書き込まれたタイトルは右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="badc4-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="badc4-173">補間式の後にコンマ (",") を追加し、*最小* のフィールド幅を指定して、配置を指定します。</span><span class="sxs-lookup"><span data-stu-id="badc4-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="badc4-174">指定された値が正数の場合、フィールドは右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="badc4-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="badc4-175">負数の場合、フィールドは左揃えになります。</span><span class="sxs-lookup"><span data-stu-id="badc4-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="badc4-176">`{"Author",-25}` と `{title.Key,-25}` のコードから負号を削除してみて、次のコードのように、例を再実行します。</span><span class="sxs-lookup"><span data-stu-id="badc4-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="badc4-177">この場合、作成者情報は右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="badc4-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="badc4-178">単一の補間式にアラインメント指定子と書式指定文字列を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="badc4-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="badc4-179">この操作を行うには、最初に配置を指定して、その後にコロンと書式指定文字列を続けます。</span><span class="sxs-lookup"><span data-stu-id="badc4-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="badc4-180">`Main` メソッド内のすべてのコードを次のコードに置き換えると、フィールド幅が定義された 3 つの書式指定された文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="badc4-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="badc4-181">次に、`dotnet run` コマンドを入力してプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="badc4-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="badc4-182">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="badc4-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="badc4-183">文字列補間のチュートリアルはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="badc4-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="badc4-184">詳細については、[文字列補間](../../language-reference/tokens/interpolated.md)に関するトピックと「[C# における文字列補間](../string-interpolation.md)」チュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="badc4-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../string-interpolation.md) tutorial.</span></span>
