---
title: NUnit と .NET Core による単体テスト C#
description: dotnet テストおよび NUnit を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、C# および .NET Core の単体テストの概念について説明します。
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: d471521fe324700502415c5e6fb1b28871492b9a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873446"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="3691e-103">NUnit と .NET Core による単体テスト C#</span><span class="sxs-lookup"><span data-stu-id="3691e-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="3691e-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="3691e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3691e-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/)してください。</span><span class="sxs-lookup"><span data-stu-id="3691e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="3691e-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3691e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="3691e-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3691e-107">Prerequisites</span></span>

- <span data-ttu-id="3691e-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="3691e-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="3691e-109">ユーザーが選んだテキスト エディターまたはコード エディター。</span><span class="sxs-lookup"><span data-stu-id="3691e-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3691e-110">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3691e-110">Creating the source project</span></span>

<span data-ttu-id="3691e-111">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="3691e-111">Open a shell window.</span></span> <span data-ttu-id="3691e-112">ソリューションを保存するための *unit-testing-using-nunit* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="3691e-113">この新しいディレクトリ内で、次のコマンドを実行して、クラス ライブラリとテスト プロジェクト用の新しいソリューション ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="3691e-114">次に、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="3691e-115">これまでのところ、ディレクトリとファイルの構造は次のアウトラインのようになっています。</span><span class="sxs-lookup"><span data-stu-id="3691e-115">The following outline shows the directory and file structure so far:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="3691e-116">*PrimeService* を現在のディレクトリとし、次のコマンドを実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib
```

<span data-ttu-id="3691e-117">*Class1.cs* の名前を *PrimeService.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="3691e-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="3691e-118">`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-118">You create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

<span data-ttu-id="3691e-119">*unit-testing-using-nunit* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3691e-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="3691e-120">次のコマンドを実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3691e-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="3691e-121">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3691e-121">Creating the test project</span></span>

<span data-ttu-id="3691e-122">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="3691e-123">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="3691e-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="3691e-124">*PrimeService.Tests* ディレクトリを現在のディレクトリとし、次のコマンドを使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit
```

<span data-ttu-id="3691e-125">[dotnet new](../tools/dotnet-new.md) コマンドによって、テスト ライブラリとして NUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3691e-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="3691e-126">生成されたテンプレートによって、*PrimeService.Tests.csproj* ファイル内にテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="3691e-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="3691e-127">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="3691e-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3691e-128">前の手順の `dotnet new` では Microsoft テスト SDK、NUnit テスト フレームワーク、NUnit テスト アダプターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="3691e-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="3691e-129">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="3691e-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="3691e-130">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3691e-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="3691e-131">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="3691e-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="3691e-132">ソリューションの最終的なレイアウトは次のアウトラインのようになります。</span><span class="sxs-lookup"><span data-stu-id="3691e-132">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="3691e-133">*unit-testing-vb-nunit* ディレクトリ内で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3691e-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="3691e-134">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="3691e-134">Creating the first test</span></span>

<span data-ttu-id="3691e-135">失敗するテストを 1 つ作成してそれを合格させる、というプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3691e-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="3691e-136">*PrimeService.Tests* ディレクトリ内で、*UnitTest1.cs* ファイルの名前を *PrimeService_IsPrimeShould.cs* に変更し、その内容全体を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3691e-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private PrimeService _primeService;

        [SetUp]
        public void SetUp()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="3691e-137">`[TestFixture]` 属性は、単体テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="3691e-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="3691e-138">`[Test]` 属性は、メソッドがテスト メソッドであることを表します。</span><span class="sxs-lookup"><span data-stu-id="3691e-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="3691e-139">このファイルを保存し、[`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドしてから、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="3691e-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3691e-140">NUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3691e-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3691e-141">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="3691e-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3691e-142">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="3691e-142">Your test fails.</span></span> <span data-ttu-id="3691e-143">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="3691e-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="3691e-144">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="3691e-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

<span data-ttu-id="3691e-145">*unit-testing-using-nunit* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="3691e-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3691e-146">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3691e-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="3691e-147">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3691e-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="3691e-148">成功します。</span><span class="sxs-lookup"><span data-stu-id="3691e-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="3691e-149">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="3691e-149">Adding more features</span></span>

<span data-ttu-id="3691e-150">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="3691e-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3691e-151">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="3691e-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="3691e-152">`[Test]` 属性を使用すると新しいテストを追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="3691e-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="3691e-153">一連の類似のテストを記述できるようになる、他の NUnit 属性があります。</span><span class="sxs-lookup"><span data-stu-id="3691e-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="3691e-154">`[TestCase]` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="3691e-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="3691e-155">`[TestCase]` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3691e-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="3691e-156">新しいテストを作成するのではなく、この属性を適用することで 1 つのデータ駆動テストを作成します。</span><span class="sxs-lookup"><span data-stu-id="3691e-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="3691e-157">そのデータ駆動テストとは、複数の 2 未満の値を調べて、最も小さい素数を特定するという手法です。</span><span class="sxs-lookup"><span data-stu-id="3691e-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="3691e-158">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="3691e-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="3691e-159">すべてのテストを成功させるために、*PrimeService.cs* ファイルで `Main` メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="3691e-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="3691e-160">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="3691e-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="3691e-161">[テストの最終版](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs)ができ、[ライブラリの完全な実装](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3691e-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="3691e-162">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="3691e-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="3691e-163">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="3691e-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="3691e-164">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="3691e-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
