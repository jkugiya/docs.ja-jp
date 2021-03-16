---
title: オブジェクト指向プログラミング (C#)
description: C# は、抽象化、カプセル化、継承、ポリモーフィズムなど、オブジェクト指向プログラミングを完全にサポートします。
ms.date: 09/30/2020
ms.openlocfilehash: 57f1759edd2dd5f239e81351aed64bf061766b7b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255406"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="873e5-103">オブジェクト指向プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="873e5-103">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="873e5-104">C# はオブジェクト指向言語です。</span><span class="sxs-lookup"><span data-stu-id="873e5-104">C# is an object-oriented language.</span></span> <span data-ttu-id="873e5-105">オブジェクト指向プログラミングで使用される 4 つの主要な手法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="873e5-105">Four of the key techniques used in object-oriented programming are:</span></span>

- <span data-ttu-id="873e5-106">"*抽象化*" とは、関連するプロパティ、メソッド、およびその他のメンバーのグループが 1 つの単位またはオブジェクトとして扱われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="873e5-106">*Abstraction* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="873e5-107">"*カプセル化*" とは、型コンシューマーから不要な詳細を隠すことです。</span><span class="sxs-lookup"><span data-stu-id="873e5-107">*Encapsulation* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="873e5-108">"*継承*" は、既存のクラスに基づいて新しいクラスを作成する機能です。</span><span class="sxs-lookup"><span data-stu-id="873e5-108">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="873e5-109">"*ポリモーフィズム*" とは、同じプロパティまたはメソッドを異なる方法で実装している複数のクラスを、交換して使用できることです。</span><span class="sxs-lookup"><span data-stu-id="873e5-109">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="873e5-110">前のチュートリアルの [クラスの概要](introduction-to-classes.md)では、"*抽象化*" と "*カプセル化*" の両方について説明しました。</span><span class="sxs-lookup"><span data-stu-id="873e5-110">In the preceding tutorial, [introduction to classes](introduction-to-classes.md) you saw both *abstraction* and *encapsulation*.</span></span> <span data-ttu-id="873e5-111">`BankAccount` クラスによって、銀行口座の概念に対する抽象化が提供されました。</span><span class="sxs-lookup"><span data-stu-id="873e5-111">The `BankAccount` class provided an abstraction for the concept of a bank account.</span></span> <span data-ttu-id="873e5-112">その実装は、`BankAccount` クラスを使用したコードのいずれにも影響を与えずに変更できました。</span><span class="sxs-lookup"><span data-stu-id="873e5-112">You could modify its implementation without affecting any of the code that used the `BankAccount` class.</span></span> <span data-ttu-id="873e5-113">`BankAccount`、`Transaction` クラスの両方で、これらの概念をコードで記述するために必要なコンポーネントのカプセル化が提供されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-113">Both the `BankAccount` and `Transaction` classes provide encapsulation of the components needed to describe those concepts in code.</span></span>

<span data-ttu-id="873e5-114">このチュートリアルでは、このアプリケーションを拡張し、"*継承*" と "*ポリモーフィズム*" を使用して新機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="873e5-114">In this tutorial, you'll extend that application to make use of *inheritance* and *polymorphism* to add new features.</span></span> <span data-ttu-id="873e5-115">また、前のチュートリアルで学習した "*抽象化*" と "*カプセル化*" の手法を活用して、`BankAccount` クラスに機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="873e5-115">You'll also add features to the `BankAccount` class, taking advantage of the *abstraction* and *encapsulation* techniques you learned in the preceding tutorial.</span></span>

## <a name="create-different-types-of-accounts"></a><span data-ttu-id="873e5-116">さまざまな種類の口座を作成する</span><span class="sxs-lookup"><span data-stu-id="873e5-116">Create different types of accounts</span></span>

<span data-ttu-id="873e5-117">このプログラムを構築した後、あなたは機能を追加するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-117">After building this program, you get requests to add features to it.</span></span> <span data-ttu-id="873e5-118">これは、銀行口座の種類が 1 つしかない場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="873e5-118">It works great in the situation where there is only one bank account type.</span></span> <span data-ttu-id="873e5-119">時間の経過と共に、ニーズが変化し、関連する口座の種類が要求されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-119">Over time, needs change, and related account types are requested:</span></span>

- <span data-ttu-id="873e5-120">月末ごとに利息がつく、利息つき口座。</span><span class="sxs-lookup"><span data-stu-id="873e5-120">An interest earning account that accrues interest at the end of each month.</span></span>
- <span data-ttu-id="873e5-121">残高が負の値になる可能性のある与信枠。ただし、残高がある場合は、毎月利息を請求されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-121">A line of credit that can have a negative balance, but when there's a balance, there's an interest charge each month.</span></span>
- <span data-ttu-id="873e5-122">前払いのギフト カード口座。1 回の預金で始まり、支払いのみが可能です。</span><span class="sxs-lookup"><span data-stu-id="873e5-122">A pre-paid gift card account that starts with a single deposit, and only can be paid off.</span></span> <span data-ttu-id="873e5-123">毎月初めに 1 回補充できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-123">It can be refilled once at the start of each month.</span></span>

<span data-ttu-id="873e5-124">これらの各種口座はすべて、前のチュートリアルで定義した `BankAccount` クラスに似ています。</span><span class="sxs-lookup"><span data-stu-id="873e5-124">All of these different accounts are similar to `BankAccount` class defined in the earlier tutorial.</span></span> <span data-ttu-id="873e5-125">そのコードをコピーし、クラスの名前を変更して、変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="873e5-125">You could copy that code, rename the classes, and make modifications.</span></span> <span data-ttu-id="873e5-126">この手法は短期的にはうまくいきますが、時間の経過と共に作業量が多くなります。</span><span class="sxs-lookup"><span data-stu-id="873e5-126">That technique would work in the short term, but it would be more work over time.</span></span> <span data-ttu-id="873e5-127">あらゆる変更を、影響を受けるすべてのクラス間でコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="873e5-127">Any changes would be copied across all the affected classes.</span></span>

<span data-ttu-id="873e5-128">代わりに、前のチュートリアルで作成した `BankAccount` クラスからメソッドとデータを継承する、新しい銀行口座の種類を作成できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-128">Instead, you can create new bank account types that inherit methods and data from the `BankAccount` class created in the preceding tutorial.</span></span> <span data-ttu-id="873e5-129">これらの新しいクラスでは、各種類に必要な特定の動作で `BankAccount` クラスを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-129">These new classes can extend the `BankAccount` class with the specific behavior needed for each type:</span></span>

```csharp
public class InterestEarningAccount : BankAccount
{
}

public class LineOfCreditAccount : BankAccount
{
}

public class GiftCardAccount : BankAccount
{
}
```

<span data-ttu-id="873e5-130">これらの各クラスは、共有の "*基底クラス*" である `BankAccount` クラスから、共有の動作を "*継承*" します。</span><span class="sxs-lookup"><span data-stu-id="873e5-130">Each of these classes *inherits* the shared behavior from their shared *base class*, the `BankAccount` class.</span></span> <span data-ttu-id="873e5-131">その "*派生クラス*" ごとに、新しい異なる機能の実装を記述します。</span><span class="sxs-lookup"><span data-stu-id="873e5-131">Write the implementations for new and different functionality in each of the *derived classes*.</span></span>  <span data-ttu-id="873e5-132">これらの派生クラスには、`BankAccount` クラスで定義されているすべての動作が既に備わっています。</span><span class="sxs-lookup"><span data-stu-id="873e5-132">These derived classes already have all the behavior defined in the `BankAccount` class.</span></span>

<span data-ttu-id="873e5-133">新しいクラスは、それぞれ別のソース ファイルに作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="873e5-133">It's a good practice to create each new class in a different source file.</span></span> <span data-ttu-id="873e5-134">[Visual Studio](https://visualstudio.com) では、プロジェクトを右クリックして *[クラスの追加]* を選択すると、新しいファイルに新しいクラスを追加できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-134">In [Visual Studio](https://visualstudio.com), you can right-click on the project, and select *add class* to add a new class in a new file.</span></span> <span data-ttu-id="873e5-135">[Visual Studio Code](https://code.visualstudio.com) では、 *[ファイル]* 、 *[新規]* の順に選択すると新しいソース ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-135">In [Visual Studio Code](https://code.visualstudio.com), select *File* then *New* to create a new source file.</span></span> <span data-ttu-id="873e5-136">どちらのツールでも、クラスと一致するようにファイル名を指定します。*InterestEarningAccount.cs*、*LineOfCreditAccount.cs*、*GiftCardAccount.cs* です。</span><span class="sxs-lookup"><span data-stu-id="873e5-136">In either tool, name the file to match the class: *InterestEarningAccount.cs*, *LineOfCreditAccount.cs*, and *GiftCardAccount.cs*.</span></span>

<span data-ttu-id="873e5-137">前述のサンプルのようなクラスを作成すると、どの派生クラスもコンパイルされないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="873e5-137">When you create the classes as shown in the preceding sample, you'll find that none of your derived classes compile.</span></span> <span data-ttu-id="873e5-138">コンストラクターによって、オブジェクトの初期化が行われます。</span><span class="sxs-lookup"><span data-stu-id="873e5-138">A constructor is responsible for initializing an object.</span></span> <span data-ttu-id="873e5-139">派生クラスのコンストラクターでは、派生クラスを初期化し、その派生クラスに含まれる基底クラスのオブジェクトを初期化する方法を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="873e5-139">A derived class constructor must initialize the derived class, and provide instructions on how to initialize the base class object included in the derived class.</span></span> <span data-ttu-id="873e5-140">通常、適切な初期化は追加のコードなしで行われます。</span><span class="sxs-lookup"><span data-stu-id="873e5-140">The proper initialization normally happens without any extra code.</span></span> <span data-ttu-id="873e5-141">`BankAccount` クラスでは、次のシグネチャを持つ 1 つのパブリック コンストラクターが宣言されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-141">The `BankAccount` class declares one public constructor with the following signature:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
```

<span data-ttu-id="873e5-142">コンストラクターを自分で定義した場合、コンパイラによって既定のコンストラクターが生成されることはありません。</span><span class="sxs-lookup"><span data-stu-id="873e5-142">The compiler doesn't generate a default constructor when you define a constructor yourself.</span></span> <span data-ttu-id="873e5-143">これは、各派生クラスで明示的にこのコンストラクターを呼び出す必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="873e5-143">That means each derived class must explicitly call this constructor.</span></span> <span data-ttu-id="873e5-144">基底クラスのコンストラクターに引数を渡すことができるコンストラクターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="873e5-144">You declare a constructor that can pass arguments to the base class constructor.</span></span>  <span data-ttu-id="873e5-145">次のコードは、`InterestEarningAccount` のコンストラクターを示しています。</span><span class="sxs-lookup"><span data-stu-id="873e5-145">The following code shows the constructor for the `InterestEarningAccount`:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="DerivedConstructor":::

<span data-ttu-id="873e5-146">この新しいコンストラクターのパラメーターは、基底クラスのコンストラクターのパラメーターと型と名前が一致しています。</span><span class="sxs-lookup"><span data-stu-id="873e5-146">The parameters to this new constructor match the parameter type and names of the base class constructor.</span></span> <span data-ttu-id="873e5-147">`: base()` 構文を使用して、基底クラスのコンストラクターへの呼び出しを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="873e5-147">You use the `: base()` syntax to indicate a call to a base class constructor.</span></span> <span data-ttu-id="873e5-148">複数のコンストラクターを定義するクラスもあります。この構文を使用することで、呼び出す基底クラスのコンストラクターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-148">Some classes define multiple constructors, and this syntax enables you to pick which base class constructor you call.</span></span> <span data-ttu-id="873e5-149">コンストラクターを更新したら、各派生クラスのコードを開発できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-149">Once you've updated the constructors, you can develop the code for each of the derived classes.</span></span> <span data-ttu-id="873e5-150">新しいクラスの要件は、次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-150">The requirements for the new classes can be stated as follows:</span></span>

- <span data-ttu-id="873e5-151">利息つき口座:</span><span class="sxs-lookup"><span data-stu-id="873e5-151">An interest earning account:</span></span>
  - <span data-ttu-id="873e5-152">月末の残高の 2% が振り込まれます。</span><span class="sxs-lookup"><span data-stu-id="873e5-152">Will get a credit of 2% of the month-ending-balance.</span></span>
- <span data-ttu-id="873e5-153">与信枠:</span><span class="sxs-lookup"><span data-stu-id="873e5-153">A line of credit:</span></span>
  - <span data-ttu-id="873e5-154">残高を負の値にすることができますが、与信限度額よりも絶対値を大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="873e5-154">Can have a negative balance, but not be greater in absolute value than the credit limit.</span></span>
  - <span data-ttu-id="873e5-155">月末の残高が 0 ではない場合は、毎月利息を請求されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-155">Will incur an interest charge each month where the end of month balance isn't 0.</span></span>
  - <span data-ttu-id="873e5-156">与信限度額を超えた引き出しごとに手数料が発生します。</span><span class="sxs-lookup"><span data-stu-id="873e5-156">Will incur a fee on each withdrawal that goes over the credit limit.</span></span>
- <span data-ttu-id="873e5-157">ギフト カード口座:</span><span class="sxs-lookup"><span data-stu-id="873e5-157">A gift card account:</span></span>
  - <span data-ttu-id="873e5-158">毎月 1 回、月の最終日に指定した金額を補充できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-158">Can be refilled with a specified amount once each month, on the last day of the month.</span></span>

<span data-ttu-id="873e5-159">これら 3 種類の口座には、すべて月末ごとに実行されるアクションがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="873e5-159">You can see that all three of these account types have an action that takes places at the end of each month.</span></span> <span data-ttu-id="873e5-160">ただし、口座の種類ごとに異なるタスクが実行されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-160">However, each account type does different tasks.</span></span> <span data-ttu-id="873e5-161">このコードを実装するために、"*ポリモーフィズム*" を使用します。</span><span class="sxs-lookup"><span data-stu-id="873e5-161">You use *polymorphism* to implement this code.</span></span> <span data-ttu-id="873e5-162">`BankAccount` クラスで 1 つの `virtual` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="873e5-162">Create a single `virtual` method in the `BankAccount` class:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="DeclareMonthEndTransactions":::

<span data-ttu-id="873e5-163">前のコードでは、`virtual` キーワードを使用して、派生クラスで異なる実装を提供できる基底クラスのメソッドを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="873e5-163">The preceding code shows how you use the `virtual` keyword to declare a method in the base class that a derived class may provide a different implementation for.</span></span> <span data-ttu-id="873e5-164">`virtual` メソッドは、任意の派生クラスで再実装することを選択できるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="873e5-164">A `virtual` method is a method where any derived class may choose to reimplement.</span></span> <span data-ttu-id="873e5-165">派生クラスでは、`override` キーワードを使用して新しい実装を定義します。</span><span class="sxs-lookup"><span data-stu-id="873e5-165">The derived classes use the `override` keyword to define the new implementation.</span></span> <span data-ttu-id="873e5-166">通常、これは "基底クラスの実装のオーバーライド" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="873e5-166">Typically you refer to this as "overriding the base class implementation".</span></span> <span data-ttu-id="873e5-167">`virtual` キーワードによって、派生クラスで動作をオーバーライドする可能性があることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-167">The `virtual` keyword specifies that derived classes may override the behavior.</span></span> <span data-ttu-id="873e5-168">また、派生クラスで動作をオーバーライドしなければならない `abstract` メソッドを宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="873e5-168">You can also declare `abstract` methods where derived classes must override the behavior.</span></span> <span data-ttu-id="873e5-169">基底クラスでは `abstract` メソッドの実装が提供されません。</span><span class="sxs-lookup"><span data-stu-id="873e5-169">The base class does not provide an implementation for an `abstract` method.</span></span> <span data-ttu-id="873e5-170">次に、作成した 2 つの新しいクラスの実装を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="873e5-170">Next, you need to define the implementation for two of the new classes you've created.</span></span> <span data-ttu-id="873e5-171">まずは `InterestEarningAccount` です。</span><span class="sxs-lookup"><span data-stu-id="873e5-171">Start with the `InterestEarningAccount`:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="ApplyMonthendInterest":::

<span data-ttu-id="873e5-172">`LineOfCreditAccount` に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="873e5-172">Add the following code to the `LineOfCreditAccount`.</span></span> <span data-ttu-id="873e5-173">このコードでは、残高の符号を反転させて、口座から引き出される正の利息請求額を計算しています。</span><span class="sxs-lookup"><span data-stu-id="873e5-173">The code negates the balance to compute a positive interest charge that is withdrawn from the account:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ApplyMonthendInterest":::

<span data-ttu-id="873e5-174">`GiftCardAccount` クラスには、月末の機能を実装するために 2 つの変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="873e5-174">The `GiftCardAccount` class needs two changes to implement its month-end functionality.</span></span> <span data-ttu-id="873e5-175">最初に、毎月追加できる省略可能な金額を含めるようにコンストラクターを変更します。</span><span class="sxs-lookup"><span data-stu-id="873e5-175">First, modify the constructor to include an optional amount to add each month:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="GiftCardAccountConstruction":::

<span data-ttu-id="873e5-176">このコンストラクターでは `monthlyDeposit` の値に対して既定値が指定されています。これにより、毎月の預金がない場合に呼び出し元は `0` を省略できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-176">The constructor provides a default value for the `monthlyDeposit` value so callers can omit a `0` for no monthly deposit.</span></span> <span data-ttu-id="873e5-177">次に、`PerformMonthEndTransactions` メソッドをオーバーライドして、毎月の預金がコンストラクターで 0 以外の値に設定されていた場合にそれを追加するようにします。</span><span class="sxs-lookup"><span data-stu-id="873e5-177">Next, override the `PerformMonthEndTransactions` method to add the monthly deposit, if it was set to a non-zero value in the constructor:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="AddMonthlyDeposit":::

<span data-ttu-id="873e5-178">このオーバーライドにより、コンストラクターで設定された毎月の預金が適用されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-178">The override applies the monthly deposit set in the constructor.</span></span> <span data-ttu-id="873e5-179">次のコードを `Main` メソッドに追加して、`GiftCardAccount` と `InterestEarningAccount` に対するこれらの変更内容をテストします。</span><span class="sxs-lookup"><span data-stu-id="873e5-179">Add the following code to the `Main` method to test these changes for the `GiftCardAccount` and the `InterestEarningAccount`:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="FirstTests":::

<span data-ttu-id="873e5-180">結果を確認しましょう。</span><span class="sxs-lookup"><span data-stu-id="873e5-180">Verify the results.</span></span> <span data-ttu-id="873e5-181">次に、`LineOfCreditAccount` に対して類似した一連のテスト コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="873e5-181">Now, add a similar set of test code for the `LineOfCreditAccount`:</span></span>

```
    var lineOfCredit = new LineOfCreditAccount("line of credit", 0);
    // How much is too much to borrow?
    lineOfCredit.MakeWithdrawal(1000m, DateTime.Now, "Take out monthly advance");
    lineOfCredit.MakeDeposit(50m, DateTime.Now, "Pay back small amount");
    lineOfCredit.MakeWithdrawal(5000m, DateTime.Now, "Emergency funds for repairs");
    lineOfCredit.MakeDeposit(150m, DateTime.Now, "Partial restoration on repairs");
    lineOfCredit.PerformMonthEndTransactions();
    Console.WriteLine(lineOfCredit.GetAccountHistory());
 ```

<span data-ttu-id="873e5-182">上記のコードを追加してプログラムを実行すると、次のようなエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-182">When you add the preceding code and run the program, you'll see something like the following error:</span></span>

```console
Unhandled exception. System.ArgumentOutOfRangeException: Amount of deposit must be positive (Parameter 'amount')
   at OOProgramming.BankAccount.MakeDeposit(Decimal amount, DateTime date, String note) in BankAccount.cs:line 42
   at OOProgramming.BankAccount..ctor(String name, Decimal initialBalance) in BankAccount.cs:line 31
   at OOProgramming.LineOfCreditAccount..ctor(String name, Decimal initialBalance) in LineOfCreditAccount.cs:line 9
   at OOProgramming.Program.Main(String[] args) in Program.cs:line 29
```

> [!NOTE]
> <span data-ttu-id="873e5-183">実際の出力には、プロジェクトを含むフォルダーへの完全なパスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="873e5-183">The actual output includes the full path to the folder with the project.</span></span> <span data-ttu-id="873e5-184">簡潔にするため、フォルダー名は省略されています。</span><span class="sxs-lookup"><span data-stu-id="873e5-184">The folder names were omitted for brevity.</span></span> <span data-ttu-id="873e5-185">また、コード形式によっては、行番号が若干異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="873e5-185">Also, depending on your code format, the line numbers may be slightly different.</span></span>

<span data-ttu-id="873e5-186">このコードが失敗したのは、`BankAccount` によって初期残高は 0 より大きいと仮定されているためです。</span><span class="sxs-lookup"><span data-stu-id="873e5-186">This code fails because the `BankAccount` assumes that the initial balance must be greater than 0.</span></span> <span data-ttu-id="873e5-187">`BankAccount` クラスに織り込まれているもう 1 つの前提は、残高を負の値にすることはできないということです。</span><span class="sxs-lookup"><span data-stu-id="873e5-187">Another assumption baked into the `BankAccount` class is that the balance can't go negative.</span></span> <span data-ttu-id="873e5-188">代わりに、口座残高を超える引き出しは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-188">Instead, any withdrawal that overdraws the account is rejected.</span></span> <span data-ttu-id="873e5-189">これらの前提はどちらも変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="873e5-189">Both of those assumptions need to change.</span></span> <span data-ttu-id="873e5-190">与信枠口座は 0 から始まり、通常は残高が負になります。</span><span class="sxs-lookup"><span data-stu-id="873e5-190">The line of credit account starts at 0, and generally will have a negative balance.</span></span> <span data-ttu-id="873e5-191">また、顧客がお金を借りすぎた場合、手数料が発生します。</span><span class="sxs-lookup"><span data-stu-id="873e5-191">Also, if a customer borrows too much money, they incur a fee.</span></span> <span data-ttu-id="873e5-192">そのトランザクションは承認されます。追加料金がかかるだけです。</span><span class="sxs-lookup"><span data-stu-id="873e5-192">The transaction is accepted, it just costs more.</span></span> <span data-ttu-id="873e5-193">最初の規則は、最小残高を指定する省略可能な引数を `BankAccount` コンストラクターに追加することによって実装できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-193">The first rule can be implemented by adding an optional argument to the `BankAccount` constructor that specifies the minimum balance.</span></span> <span data-ttu-id="873e5-194">既定では、 `0`です。</span><span class="sxs-lookup"><span data-stu-id="873e5-194">The default is `0`.</span></span> <span data-ttu-id="873e5-195">2 番目の規則には、派生クラスで既定のアルゴリズムを変更できるようにするメカニズムが必要です。</span><span class="sxs-lookup"><span data-stu-id="873e5-195">The second rule requires a mechanism that enables derived classes to modify the default algorithm.</span></span> <span data-ttu-id="873e5-196">ある意味では、基底クラスが派生型に、過剰な引き出しがあった場合にどうするかを "尋ね" ます。</span><span class="sxs-lookup"><span data-stu-id="873e5-196">In a sense, the base class "asks" the derived type what should happen when there's an overdraft.</span></span> <span data-ttu-id="873e5-197">既定の動作では、例外をスローすることによってトランザクションを拒否します。</span><span class="sxs-lookup"><span data-stu-id="873e5-197">The default behavior is to reject the transaction by throwing an exception.</span></span>

<span data-ttu-id="873e5-198">まず、省略可能な `minimumBalance` パラメーターを含む 2 番目のコンストラクターを追加しましょう。</span><span class="sxs-lookup"><span data-stu-id="873e5-198">Let's start by adding a second constructor that includes an optional `minimumBalance` parameter.</span></span> <span data-ttu-id="873e5-199">この新しいコンストラクターでは、既存のコンストラクターで実行されるすべてのアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-199">This new constructor does all the actions done by the existing constructor.</span></span> <span data-ttu-id="873e5-200">さらに、最小残高のプロパティも設定されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-200">Also, it sets the minimum balance property.</span></span> <span data-ttu-id="873e5-201">既存のコンストラクターの本体をコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="873e5-201">You could copy the body of the existing constructor.</span></span> <span data-ttu-id="873e5-202">ただし、今後は 2 か所を変更しなければならなくなります。</span><span class="sxs-lookup"><span data-stu-id="873e5-202">but that means two locations to change in the future.</span></span> <span data-ttu-id="873e5-203">代わりに、"*コンストラクター チェーン*" を使用して、1 つのコンストラクターが別のコンストラクターを呼び出すようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="873e5-203">Instead, you can use *constructor chaining* to have one constructor call another.</span></span> <span data-ttu-id="873e5-204">次のコードは、2 つのコンストラクターと新しい追加フィールドを示しています。</span><span class="sxs-lookup"><span data-stu-id="873e5-204">The following code shows the two constructors and the new additional field:</span></span>

 :::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="ConstructorModifications":::

<span data-ttu-id="873e5-205">上記のコードには、2 つの新しい手法が示されています。</span><span class="sxs-lookup"><span data-stu-id="873e5-205">The preceding code shows two new techniques.</span></span> <span data-ttu-id="873e5-206">まず、`minimumBalance` フィールドは `readonly` としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="873e5-206">First, the `minimumBalance` field is marked as `readonly`.</span></span> <span data-ttu-id="873e5-207">これは、オブジェクトを構築した後はこの値を変更できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="873e5-207">That means the value cannot be changed after the object is constructed.</span></span> <span data-ttu-id="873e5-208">`BankAccount` の作成後に `minimumBalance` を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="873e5-208">Once a `BankAccount` is created, the `minimumBalance` can't change.</span></span> <span data-ttu-id="873e5-209">次に、2 つのパラメーターを受け取るコンストラクターでは、実装として `: this(name, initialBalance, 0) { }` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="873e5-209">Second, the constructor that takes two parameters uses `: this(name, initialBalance, 0) { }` as its implementation.</span></span> <span data-ttu-id="873e5-210">`: this()` 式によって、3 つのパラメーターを持つ別のコンストラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="873e5-210">The `: this()` expression calls the other constructor, the one with three parameters.</span></span> <span data-ttu-id="873e5-211">この手法を使用すると、オブジェクトを初期化するための実装を 1 つ用意して、クライアント コードでは多数のコンストラクターの中からいずれかを選択できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="873e5-211">This technique allows you to have a single implementation for initializing an object even though client code can choose one of many constructors.</span></span>

<span data-ttu-id="873e5-212">この実装では、初期残高が `0` よりも大きい場合にのみ `MakeDeposit` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-212">This implementation calls `MakeDeposit` only if the initial balance is greater than `0`.</span></span> <span data-ttu-id="873e5-213">これにより、預金は正である必要があるという規則を守りつつ、残高 `0` で与信枠口座を開設することができます。</span><span class="sxs-lookup"><span data-stu-id="873e5-213">That preserves the rule that deposits must be positive, yet lets the credit account open with a `0` balance.</span></span>

<span data-ttu-id="873e5-214">これで `BankAccount` クラスに最小残高用の読み取り専用フィールドが設定されたので、最後の変更として、`MakeWithdrawal` メソッドのハードコーディングされた `0` を `minimumBalance` に変更します。</span><span class="sxs-lookup"><span data-stu-id="873e5-214">Now that the `BankAccount` class has a read-only field for the minimum balance, the final change is to change the hard code `0` to `minimumBalance` in the `MakeWithdrawal` method:</span></span>

```csharp
if (Balance - amount < minimumBalance)
```

<span data-ttu-id="873e5-215">`BankAccount` クラスを拡張した後、次のコードに示すように、新しい基底コンストラクターを呼び出すように `LineOfCreditAccount` コンストラクターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-215">After extending the `BankAccount` class, you can modify the `LineOfCreditAccount` constructor to call the new base constructor, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ConstructLineOfCredit":::

<span data-ttu-id="873e5-216">`LineOfCreditAccount` コンストラクターでは、`minimumBalance` パラメーターの意味と一致するように、`creditLimit` パラメーターの符号が変更されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="873e5-216">Notice that the `LineOfCreditAccount` constructor changes the sign of the `creditLimit` parameter so it matches the meaning of the `minimumBalance` parameter.</span></span>

## <a name="different-overdraft-rules"></a><span data-ttu-id="873e5-217">過剰な引き出しに対する異なる規則</span><span class="sxs-lookup"><span data-stu-id="873e5-217">Different overdraft rules</span></span>

<span data-ttu-id="873e5-218">追加する最後の機能により、`LineOfCreditAccount` で、与信限度額の超過に対してトランザクションを拒否するのではなく、手数料を請求できるようになります。</span><span class="sxs-lookup"><span data-stu-id="873e5-218">The last feature to add enables the `LineOfCreditAccount` to charge a fee for going over the credit limit instead of refusing the transaction.</span></span>

<span data-ttu-id="873e5-219">1 つの手法は、必要な動作を実装する仮想関数を定義することです。</span><span class="sxs-lookup"><span data-stu-id="873e5-219">One technique is to define a virtual function where you implement the required behavior.</span></span> <span data-ttu-id="873e5-220">`BankAccount` クラスでは、`MakeWithdrawal` メソッドが 2 つのメソッドにリファクターされます。</span><span class="sxs-lookup"><span data-stu-id="873e5-220">The `BankAccount` class refactors the `MakeWithdrawal` method into two methods.</span></span> <span data-ttu-id="873e5-221">新しいメソッドでは、引き出しによって残高が最小値を下回る場合に、指定されたアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-221">The new method does the specified action when the withdrawal takes the balance below the minimum.</span></span> <span data-ttu-id="873e5-222">既存の `MakeWithdrawal` メソッドには、次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="873e5-222">The existing `MakeWithdrawal` method has the following code:</span></span>

```csharp
public void MakeWithdrawal(decimal amount, DateTime date, string note)
{
    if (amount <= 0)
    {
        throw new ArgumentOutOfRangeException(nameof(amount), "Amount of withdrawal must be positive");
    }
    if (Balance - amount < minimumBalance)
    {
        throw new InvalidOperationException("Not sufficient funds for this withdrawal");
    }
    var withdrawal = new Transaction(-amount, date, note);
    allTransactions.Add(withdrawal);
}
```

<span data-ttu-id="873e5-223">見つかったコードを次のコードと置き換えます。</span><span class="sxs-lookup"><span data-stu-id="873e5-223">Replace it with the following code:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="RefactoredMakeWithdrawal":::

<span data-ttu-id="873e5-224">追加されたメソッドは `protected` です。これは、派生クラスからのみ呼び出せることを意味します。</span><span class="sxs-lookup"><span data-stu-id="873e5-224">The added method is `protected`, which means that it can be called only from derived classes.</span></span> <span data-ttu-id="873e5-225">この宣言によって、他のクライアントがこのメソッドを呼び出せなくなります。</span><span class="sxs-lookup"><span data-stu-id="873e5-225">That declaration prevents other clients from calling the method.</span></span> <span data-ttu-id="873e5-226">これは `virtual` でもあるため、派生クラスで動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-226">It's also `virtual` so that derived classes can change the behavior.</span></span> <span data-ttu-id="873e5-227">戻り値の型は `Transaction?` です。</span><span class="sxs-lookup"><span data-stu-id="873e5-227">The return type is a `Transaction?`.</span></span> <span data-ttu-id="873e5-228">`?` の注釈は、メソッドが `null` を返す可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="873e5-228">The `?` annotation indicates that the method may return `null`.</span></span> <span data-ttu-id="873e5-229">次の実装を `LineOfCreditAccount` に追加して、引き出しの限度額を超えたときに手数料を請求します。</span><span class="sxs-lookup"><span data-stu-id="873e5-229">Add the following implementation in the `LineOfCreditAccount` to charge a fee when the withdrawal limit is exceeded:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="AddOverdraftFee":::

<span data-ttu-id="873e5-230">このオーバーライドでは、残高が過剰に引き出された場合に手数料のトランザクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-230">The override returns a fee transaction when the account is overdrawn.</span></span> <span data-ttu-id="873e5-231">引き出しが限度額を超えていない場合は、メソッドから `null` トランザクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="873e5-231">If the withdrawal doesn't go over the limit, the method returns a `null` transaction.</span></span> <span data-ttu-id="873e5-232">これは手数料が発生していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="873e5-232">That indicates there's no fee.</span></span> <span data-ttu-id="873e5-233">`Program` クラスの `Main` メソッドに次のコードを追加して、これらの変更をテストします。</span><span class="sxs-lookup"><span data-stu-id="873e5-233">Test these changes by adding the following code to your `Main` method in the `Program` class:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="TestLineOfCredit":::

<span data-ttu-id="873e5-234">プログラムを実行し、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="873e5-234">Run the program, and check the results.</span></span>

## <a name="summary"></a><span data-ttu-id="873e5-235">まとめ</span><span class="sxs-lookup"><span data-stu-id="873e5-235">Summary</span></span>

<span data-ttu-id="873e5-236">うまくいかない場合は、このチュートリアルのソースを [GitHub リポジトリ](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/object-oriented-programming)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="873e5-236">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/object-oriented-programming).</span></span>

<span data-ttu-id="873e5-237">このチュートリアルでは、オブジェクト指向プログラミングで使用される多くの手法を示しました。</span><span class="sxs-lookup"><span data-stu-id="873e5-237">This tutorial demonstrated many of the techniques used in Object-Oriented programming:</span></span>

- <span data-ttu-id="873e5-238">各クラスで多くの詳細情報を `private` にしたとき、"*抽象化*" を使用しました。</span><span class="sxs-lookup"><span data-stu-id="873e5-238">You used *Abstraction* when you kept many details `private` in each class.</span></span>
- <span data-ttu-id="873e5-239">異なる種類の口座ごとにクラスを定義したとき、"*カプセル化*" を使用しました。</span><span class="sxs-lookup"><span data-stu-id="873e5-239">You used *Encapsulation* when you defined classes for each of the different account types.</span></span> <span data-ttu-id="873e5-240">これらのクラスによって、その種類の口座の動作が記述されました。</span><span class="sxs-lookup"><span data-stu-id="873e5-240">Those classes described the behavior for that type of account.</span></span>
- <span data-ttu-id="873e5-241">`BankAccount` クラスに既に作成されている実装を活用してコードを節約したとき、"*継承*" を使用しました。</span><span class="sxs-lookup"><span data-stu-id="873e5-241">You used *Inheritance* when you leveraged the implementation already created in the `BankAccount` class to save code.</span></span>
- <span data-ttu-id="873e5-242">派生クラスでオーバーライドしてその口座の種類に固有の動作を作成できる `virtual` メソッドを作成したとき、"*ポリモーフィズム*" を使用しました。</span><span class="sxs-lookup"><span data-stu-id="873e5-242">You used *Polymorphism* when you created `virtual` methods that derived classes could override to create specific behavior for that account type.</span></span>

<span data-ttu-id="873e5-243">お疲れさまでした。これで、C# の概要に関する全チュートリアルを完了しました。</span><span class="sxs-lookup"><span data-stu-id="873e5-243">Congratulations, you've finished all of our introduction to C# tutorials.</span></span> <span data-ttu-id="873e5-244">さらに学習する場合は、その他の[チュートリアル](../index.md)をお試しください。</span><span class="sxs-lookup"><span data-stu-id="873e5-244">To learn more, try more of our [tutorials](../index.md).</span></span>
