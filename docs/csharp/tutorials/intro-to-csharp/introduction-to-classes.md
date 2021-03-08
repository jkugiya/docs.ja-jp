---
title: クラスおよびオブジェクト - C# チュートリアルの概要
description: 初めての C# プログラムを作成し、オブジェクト指向の概念を確認します
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 3da445e6c656628fffdb9ef9384fb1a1c556a2cd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255419"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="3da61-103">クラスおよびオブジェクトを使用したオブジェクト指向プログラミングについて確認します</span><span class="sxs-lookup"><span data-stu-id="3da61-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="3da61-104">このチュートリアルでは、コンソール アプリケーションを構築し、C# 言語に含まれるオブジェクト指向の基本的な機能について確認します。</span><span class="sxs-lookup"><span data-stu-id="3da61-104">In this tutorial, you'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3da61-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="3da61-105">Prerequisites</span></span>

<span data-ttu-id="3da61-106">このチュートリアルでは、ローカル開発用にセットアップされたコンピューターがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="3da61-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="3da61-107">Windows、Linux、または macOS で、.NET CLI を使用してアプリケーションを作成、ビルド、実行できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="3da61-108">Windows では、Visual Studio 2019 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-108">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="3da61-109">セットアップの手順については、「[ローカル環境をセットアップする](../../tour-of-csharp/tutorials/local-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3da61-109">For setup instructions, see [Set up your local environment](../../tour-of-csharp/tutorials/local-environment.md).</span></span>

## <a name="create-your-application"></a><span data-ttu-id="3da61-110">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="3da61-110">Create your application</span></span>

<span data-ttu-id="3da61-111">ターミナル ウィンドウで、「*classes*」という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3da61-111">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="3da61-112">ここにアプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="3da61-112">You'll build your application there.</span></span> <span data-ttu-id="3da61-113">このディレクトリに移動し、コンソール ウィンドウで「`dotnet new console`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3da61-113">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="3da61-114">このコマンドにより、アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3da61-114">This command creates your application.</span></span> <span data-ttu-id="3da61-115">*Program.cs* を開きます。</span><span class="sxs-lookup"><span data-stu-id="3da61-115">Open *Program.cs*.</span></span> <span data-ttu-id="3da61-116">内容は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3da61-116">It should look like this:</span></span>

```csharp
using System;

namespace classes
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

<span data-ttu-id="3da61-117">このチュートリアルでは、銀行口座を表す新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="3da61-117">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="3da61-118">通常、開発者は各クラスを別々のテキスト ファイルで定義します。</span><span class="sxs-lookup"><span data-stu-id="3da61-118">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="3da61-119">この方法なら、プログラムのサイズが大きくなっても管理が容易です。</span><span class="sxs-lookup"><span data-stu-id="3da61-119">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="3da61-120">*classes* ディレクトリに「*BankAccount.cs*」という名前の新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3da61-120">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="3da61-121">このファイルには、"**銀行口座**" の定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3da61-121">This file will contain the definition of a \***bank account** _.</span></span> <span data-ttu-id="3da61-122">オブジェクト指向プログラミングを使用して "_\*_クラス_\*\*" の形式で型を作成することにより、コードを整理します。</span><span class="sxs-lookup"><span data-stu-id="3da61-122">Object Oriented programming organizes code by creating types in the form of _\*_classes_\*\*.</span></span> <span data-ttu-id="3da61-123">これらのクラスには、特定のエンティティを表すコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3da61-123">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="3da61-124">`BankAccount` クラスは銀行口座を表します。</span><span class="sxs-lookup"><span data-stu-id="3da61-124">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="3da61-125">コードでは、メソッドとプロパティを使用した特定の操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="3da61-125">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="3da61-126">このチュートリアルでは、銀行口座は次の動作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3da61-126">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="3da61-127">銀行口座を一意に特定する 10 桁の数字をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3da61-127">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="3da61-128">口座の名前、または所有者の名前を格納する文字列をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3da61-128">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="3da61-129">残高を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-129">The balance can be retrieved.</span></span>
1. <span data-ttu-id="3da61-130">預金を許可します。</span><span class="sxs-lookup"><span data-stu-id="3da61-130">It accepts deposits.</span></span>
1. <span data-ttu-id="3da61-131">引き出しを許可します。</span><span class="sxs-lookup"><span data-stu-id="3da61-131">It accepts withdrawals.</span></span>
1. <span data-ttu-id="3da61-132">初期残高は正の値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-132">The initial balance must be positive.</span></span>
1. <span data-ttu-id="3da61-133">引き出しによって残高が負の値になることはありません。</span><span class="sxs-lookup"><span data-stu-id="3da61-133">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="3da61-134">銀行口座の型を定義する</span><span class="sxs-lookup"><span data-stu-id="3da61-134">Define the bank account type</span></span>

<span data-ttu-id="3da61-135">動作を定義するクラスの基本を作成することから開始できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-135">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="3da61-136">**File:New** コマンドを使用して、新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3da61-136">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="3da61-137">*BankAccount.cs* という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="3da61-137">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="3da61-138">*BankAccount.cs* ファイルに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-138">Add the following code to your *BankAccount.cs* file:</span></span>

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

<span data-ttu-id="3da61-139">先に進む前に、構築したものを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="3da61-139">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="3da61-140">`namespace` 宣言は、コードを論理的に整理する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="3da61-140">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="3da61-141">このチュートリアルで取り扱うコードは比較的小さいため、1 つの名前空間にすべてのコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="3da61-141">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="3da61-142">`public class BankAccount` は、これから作成するクラスまたは型を定義します。</span><span class="sxs-lookup"><span data-stu-id="3da61-142">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="3da61-143">クラス宣言のあとにある `{` と `}` の内側はすべて、クラスの状態と動作を定義しています。</span><span class="sxs-lookup"><span data-stu-id="3da61-143">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="3da61-144">`BankAccount` クラスには、5 つの "**メンバー**" があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-144">There are five \***members** _ of the `BankAccount` class.</span></span> <span data-ttu-id="3da61-145">最初の 3 つは "_\*_プロパティ_\*_" です。</span><span class="sxs-lookup"><span data-stu-id="3da61-145">The first three are _*_properties_*_.</span></span> <span data-ttu-id="3da61-146">プロパティはデータ要素であり、検証やその他の規則を適用するコードを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="3da61-146">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="3da61-147">最後の 2 つは "_\*_メソッド_\*\*" です。</span><span class="sxs-lookup"><span data-stu-id="3da61-147">The last two are _\*_methods_\*\*.</span></span> <span data-ttu-id="3da61-148">メソッドは 1 つの機能を実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="3da61-148">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="3da61-149">各メンバーの名前を確認すると、開発者がそのクラスの作用を把握するための十分な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="3da61-149">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="3da61-150">新しいアカウントを開く</span><span class="sxs-lookup"><span data-stu-id="3da61-150">Open a new account</span></span>

<span data-ttu-id="3da61-151">実装する最初の機能は、銀行口座を開く機能です。</span><span class="sxs-lookup"><span data-stu-id="3da61-151">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="3da61-152">顧客が口座を開く場合、初期残高や口座の (1 名または複数名の) 所有者の情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-152">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="3da61-153">`BankAccount` 型の新しいオブジェクトを作成することは、それらの値を割り当てる "\***コンストラクター** _" を定義することを意味します。</span><span class="sxs-lookup"><span data-stu-id="3da61-153">Creating a new object of the `BankAccount` type means defining a \***constructor** _ that assigns those values.</span></span> <span data-ttu-id="3da61-154">"_ \*_コンストラクター_\*\*" はクラスと同じ名前を持つメンバーです。</span><span class="sxs-lookup"><span data-stu-id="3da61-154">A _ *_constructor_*\* is a member that has the same name as the class.</span></span> <span data-ttu-id="3da61-155">これは、そのクラス型のオブジェクトを初期化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3da61-155">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="3da61-156">`BankAccount` 型に次のコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-156">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="3da61-157">`MakeDeposit` クラス宣言の上に次のコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="3da61-157">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="3da61-158">[`new`](../../language-reference/operators/new-operator.md) を使用してオブジェクトを作成すると、コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3da61-158">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="3da61-159">*Program.cs* の `Console.WriteLine("Hello World!");` の行を次のコードで置き換えます (`<name>` を自分の名前に置き換えます)。</span><span class="sxs-lookup"><span data-stu-id="3da61-159">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="3da61-160">これまでに構築したものを実行してみましょう。</span><span class="sxs-lookup"><span data-stu-id="3da61-160">Let's run what you've built so far.</span></span> <span data-ttu-id="3da61-161">Visual Studio を使用している場合は、 **[実行]** メニューから **[デバッグなしで開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3da61-161">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="3da61-162">コマンド ラインを使用している場合は、プロジェクトを作成したディレクトリで `dotnet run` を入力します。</span><span class="sxs-lookup"><span data-stu-id="3da61-162">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="3da61-163">口座番号が空であることに気付かれましたか?</span><span class="sxs-lookup"><span data-stu-id="3da61-163">Did you notice that the account number is blank?</span></span> <span data-ttu-id="3da61-164">次にこの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="3da61-164">It's time to fix that.</span></span> <span data-ttu-id="3da61-165">口座番号はオブジェクトが作成されるときに割り当てられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-165">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="3da61-166">しかし、それを作成する責任を呼び出し元に負わせるべきではありません。</span><span class="sxs-lookup"><span data-stu-id="3da61-166">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="3da61-167">`BankAccount` クラスのコードは、新しい口座番号の割り当て方を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-167">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="3da61-168">そのための簡単な方法は、10 桁の数字で始めることです。</span><span class="sxs-lookup"><span data-stu-id="3da61-168">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="3da61-169">そして、新しい口座番号が作成されるごとに値を 1 増加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-169">Increment it when each new account is created.</span></span> <span data-ttu-id="3da61-170">最後に、オブジェクトが作成されるときに現在の口座番号を格納します。</span><span class="sxs-lookup"><span data-stu-id="3da61-170">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="3da61-171">`BankAccount`クラスにメンバーの宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-171">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="3da61-172">`BankAccount` クラスの先頭の左中かっこ `{` の後に、次のコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="3da61-172">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="3da61-173">これがデータ メンバーです。</span><span class="sxs-lookup"><span data-stu-id="3da61-173">This is a data member.</span></span> <span data-ttu-id="3da61-174">これは `private` であり、`BankAccount` クラス内のコードのみがこれにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3da61-174">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="3da61-175">この方法により、プライベートな実装 (口座番号の生成方法) から (口座番号を持つなどの) パブリックな責任を分離できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-175">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="3da61-176">`static` でもあるため、すべての `BankAccount` オブジェクトによって共有されます。</span><span class="sxs-lookup"><span data-stu-id="3da61-176">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="3da61-177">静的でない変数の値は `BankAccount` オブジェクトのインスタンスごとに一意です。</span><span class="sxs-lookup"><span data-stu-id="3da61-177">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="3da61-178">次の 2 行をコンストラクターに追加して、口座番号を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3da61-178">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="3da61-179">それらは `this.Balance = initialBalance` という行の後に配置します。</span><span class="sxs-lookup"><span data-stu-id="3da61-179">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="3da61-180">「`dotnet run`」と入力して結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="3da61-180">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="3da61-181">預金と引き出しを作成する</span><span class="sxs-lookup"><span data-stu-id="3da61-181">Create deposits and withdrawals</span></span>

<span data-ttu-id="3da61-182">銀行口座クラスは、預金と引き出しを許可して正しく動作するようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-182">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="3da61-183">口座のすべてのトランザクションを記録する履歴を作成して、預金と引き出しを実装しましょう。</span><span class="sxs-lookup"><span data-stu-id="3da61-183">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="3da61-184">これには、単純にトランザクションごとに残高を更新する方法に比べていくつかのメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="3da61-184">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="3da61-185">履歴は、すべてのトランザクションを監査して毎日の残高を管理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-185">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="3da61-186">必要に応じてすべてのトランザクションの履歴から残高を計算することにより、1 つのトランザクションの中で修正されたすべてのエラーが正しく残高に反映されて次の計算に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3da61-186">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="3da61-187">トランザクションを表す新しい型を作成するところから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="3da61-187">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="3da61-188">これは一切の責任を持たない単純型です。</span><span class="sxs-lookup"><span data-stu-id="3da61-188">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="3da61-189">いくつかのプロパティが必要になります。</span><span class="sxs-lookup"><span data-stu-id="3da61-189">It needs a few properties.</span></span> <span data-ttu-id="3da61-190">「*Transaction.cs*」という名前の新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3da61-190">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="3da61-191">これに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-191">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="3da61-192">`BankAccount` クラスに `Transaction` オブジェクトの <xref:System.Collections.Generic.List%601> を追加しましょう。</span><span class="sxs-lookup"><span data-stu-id="3da61-192">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="3da61-193">*BankAccount.cs* ファイルのコンストラクターの後に次の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-193">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="3da61-194"><xref:System.Collections.Generic.List%601> クラスでは、別の名前空間をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-194">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="3da61-195">*BankAccount.cs* の最初に次を追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-195">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="3da61-196">それでは、`Balance` を正しく計算しましょう。</span><span class="sxs-lookup"><span data-stu-id="3da61-196">Now, let's correctly compute the `Balance`.</span></span> <span data-ttu-id="3da61-197">現在の残高は、すべての取引の値を合計することによって確認できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-197">The current balance can be found by summing the values of all transactions.</span></span> <span data-ttu-id="3da61-198">現在、このコードで取得できるのは口座の初期残高のみであるため、`Balance` プロパティを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-198">As the code is currently, you can only get the initial balance of the account, so you'll have to update the `Balance` property.</span></span> <span data-ttu-id="3da61-199">*BankAccount.cs* の `public decimal Balance { get; }` の行を、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3da61-199">Replace the line `public decimal Balance { get; }` in *BankAccount.cs* with the following code:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="3da61-200">この例は、***プロパティ*** の重要な一面を示しています。</span><span class="sxs-lookup"><span data-stu-id="3da61-200">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="3da61-201">これで、別のプログラマーが値を要求したときに残高が計算されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3da61-201">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="3da61-202">この計算処理は、すべてのトランザクションを列挙して、その合計値を現在の残高として提供します。</span><span class="sxs-lookup"><span data-stu-id="3da61-202">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="3da61-203">次に `MakeDeposit` メソッドと `MakeWithdrawal` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="3da61-203">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="3da61-204">これらのメソッドは、初期残高が正の値でなければならず、引き出し後の残高が負の値になってはいけない、という最後の 2 つの規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="3da61-204">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="3da61-205">これにより、***例外*** の概念が導入されます。</span><span class="sxs-lookup"><span data-stu-id="3da61-205">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="3da61-206">メソッドが作業を正常に完了できないことを示す標準的な方法は、例外をスローすることです。</span><span class="sxs-lookup"><span data-stu-id="3da61-206">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="3da61-207">例外の型とそれに関連付けられたメッセージがエラーを説明します。</span><span class="sxs-lookup"><span data-stu-id="3da61-207">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="3da61-208">`MakeDeposit` メソッドは、預金額が負の値になる場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3da61-208">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="3da61-209">`MakeWithdrawal` メソッドは、引き出し額が負の値になる場合、または引き出しを適用した結果、残高が負の値になる場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3da61-209">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="3da61-210">`allTransactions` リストの宣言の後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-210">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="3da61-211">[`throw`](../../language-reference/keywords/throw.md) ステートメントが例外を **スロー** します。</span><span class="sxs-lookup"><span data-stu-id="3da61-211">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="3da61-212">現在のブロックの実行が終了し、コントロールによってコール スタックで最初に一致した `catch` ブロックに転送されます。</span><span class="sxs-lookup"><span data-stu-id="3da61-212">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="3da61-213">あとで `catch` ブロックを追加してこのコードをテストします。</span><span class="sxs-lookup"><span data-stu-id="3da61-213">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="3da61-214">残高を直接更新するのではなく、最初のトランザクションを追加するようにするため、コンストラクターを 1 か所変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3da61-214">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="3da61-215">既に `MakeDeposit` メソッドは記述したので、このメソッドをコンストラクターから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3da61-215">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="3da61-216">完成したコンストラクターは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3da61-216">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="3da61-217"><xref:System.DateTime.Now?displayProperty=nameWithType> は、現在の日付と時刻を返すプロパティです。</span><span class="sxs-lookup"><span data-stu-id="3da61-217"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="3da61-218">新しい `BankAccount` を作成するコードの後で、`Main` メソッドにいくつかの預金と引き出しを追加することで、これをテストします。</span><span class="sxs-lookup"><span data-stu-id="3da61-218">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="3da61-219">次に、残高が負の値になっている口座を作成してみることで、エラー条件のキャッチをテストします。</span><span class="sxs-lookup"><span data-stu-id="3da61-219">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="3da61-220">追加したコードの後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-220">Add the following code after the preceding code you just added:</span></span>

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="3da61-221">[`try` と `catch` のステートメント](../../language-reference/keywords/try-catch.md)を使用して、例外をスローする可能性のあるコード ブロックをマークし、想定したエラーをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="3da61-221">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="3da61-222">同じ方法で、残高が負の値になっている場合に例外をスローするコードをテストします。</span><span class="sxs-lookup"><span data-stu-id="3da61-222">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="3da61-223">`Main` メソッドの末尾に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-223">Add the following code at the end of your `Main` method:</span></span>

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="3da61-224">ファイルを保存し、「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="3da61-224">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="3da61-225">課題 - すべてのトランザクションをログに記録する</span><span class="sxs-lookup"><span data-stu-id="3da61-225">Challenge - log all transactions</span></span>

<span data-ttu-id="3da61-226">このチュートリアルを完了すると、トランザクション履歴の `string` を作成する `GetAccountHistory` メソッドを記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3da61-226">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="3da61-227">このメソッドを `BankAccount` 型に追加します。</span><span class="sxs-lookup"><span data-stu-id="3da61-227">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="3da61-228">これは、<xref:System.Text.StringBuilder> クラスを使用して、各トランザクションを 1 行で表す文を含んだ文字列をフォーマットします。</span><span class="sxs-lookup"><span data-stu-id="3da61-228">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="3da61-229">文字列をフォーマットするコードについては、このチュートリアルで先述しました。</span><span class="sxs-lookup"><span data-stu-id="3da61-229">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="3da61-230">新しい文字の 1 つは `\t` です。</span><span class="sxs-lookup"><span data-stu-id="3da61-230">One new character is `\t`.</span></span> <span data-ttu-id="3da61-231">これはタブを挿入して出力をフォーマットします。</span><span class="sxs-lookup"><span data-stu-id="3da61-231">That inserts a tab to format the output.</span></span>

<span data-ttu-id="3da61-232">次の行を追加して、*Program.cs* でテストします。</span><span class="sxs-lookup"><span data-stu-id="3da61-232">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="3da61-233">プログラムを実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="3da61-233">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3da61-234">次の手順</span><span class="sxs-lookup"><span data-stu-id="3da61-234">Next steps</span></span>

<span data-ttu-id="3da61-235">うまくいかない場合は、このチュートリアルのソースを [GitHub リポジトリ](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-235">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="3da61-236">[オブジェクト指向プログラミング](object-oriented-programming.md)のチュートリアルに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="3da61-236">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="3da61-237">次の記事でこれらの概念の詳細を学習できます。</span><span class="sxs-lookup"><span data-stu-id="3da61-237">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="3da61-238">if と else ステートメント</span><span class="sxs-lookup"><span data-stu-id="3da61-238">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="3da61-239">while ステートメント</span><span class="sxs-lookup"><span data-stu-id="3da61-239">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="3da61-240">do ステートメント</span><span class="sxs-lookup"><span data-stu-id="3da61-240">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="3da61-241">for ステートメント</span><span class="sxs-lookup"><span data-stu-id="3da61-241">For statement</span></span>](../../language-reference/keywords/for.md)
