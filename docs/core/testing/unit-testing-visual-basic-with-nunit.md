---
title: dotnet テストと NUnit を使用した .NET Core での単体テスト Visual Basic
description: NUnit を使用した Visual Basic ソリューションのサンプルを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core の単体テストの概念について説明します。
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: 11334951d41c5cca24fcfb4853569e503cff97c5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874902"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="dcca3-103">dotnet テストと NUnit を使用した Visual Basic .NET Core ライブラリでの単体テスト</span><span class="sxs-lookup"><span data-stu-id="dcca3-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="dcca3-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="dcca3-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-nunit/)してください。</span><span class="sxs-lookup"><span data-stu-id="dcca3-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="dcca3-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcca3-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="dcca3-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="dcca3-107">Prerequisites</span></span>

- <span data-ttu-id="dcca3-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="dcca3-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="dcca3-109">ユーザーが選んだテキスト エディターまたはコード エディター。</span><span class="sxs-lookup"><span data-stu-id="dcca3-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="dcca3-110">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="dcca3-110">Creating the source project</span></span>

<span data-ttu-id="dcca3-111">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-111">Open a shell window.</span></span> <span data-ttu-id="dcca3-112">ソリューションを保存するための *unit-testing-vb-nunit* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="dcca3-113">この新しいディレクトリ内で、次のコマンドを実行して、クラス ライブラリとテスト プロジェクト用の新しいソリューション ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="dcca3-114">次に、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="dcca3-115">これまでのところ、ファイルの構造は次のアウトラインのようになっています。</span><span class="sxs-lookup"><span data-stu-id="dcca3-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="dcca3-116">*PrimeService* を現在のディレクトリとし、次のコマンドを実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang VB
```

<span data-ttu-id="dcca3-117">*Class1.VB* の名前を *PrimeService.VB* に変更します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="dcca3-118">`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="dcca3-119">*unit-testing-vb-using-mstest* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="dcca3-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="dcca3-120">次のコマンドを実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="dcca3-121">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="dcca3-121">Creating the test project</span></span>

<span data-ttu-id="dcca3-122">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="dcca3-123">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="dcca3-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="dcca3-124">*PrimeService.Tests* ディレクトリを現在のディレクトリとし、次のコマンドを使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang VB
```

<span data-ttu-id="dcca3-125">[dotnet new](../tools/dotnet-new.md) コマンドによって、テスト ライブラリとして NUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="dcca3-126">生成されたテンプレートで、*PrimeServiceTests.vbproj* ファイルのテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="dcca3-127">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="dcca3-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="dcca3-128">前の手順の `dotnet new` では、NUnit と NUnit のテスト アダプターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="dcca3-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="dcca3-129">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="dcca3-130">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="dcca3-131">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="dcca3-132">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dcca3-132">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="dcca3-133">*unit-testing-vb-nunit* ディレクトリ内で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="dcca3-134">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="dcca3-134">Creating the first test</span></span>

<span data-ttu-id="dcca3-135">失敗するテストを 1 つ作成してそれを合格させる、というプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="dcca3-136">*PrimeService.Tests* ディレクトリ内で、*UnitTest1.vb* ファイルの名前を *PrimeService_IsPrimeShould.VB* に変更し、その内容全体を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="dcca3-137">`<TestFixture>` 属性は、テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="dcca3-138">`<Test>` 属性は、テスト ランナーによって実行されるメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="dcca3-139">*unit-testing-vb-nunit* で [`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="dcca3-140">NUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dcca3-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="dcca3-141">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="dcca3-142">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-142">Your test fails.</span></span> <span data-ttu-id="dcca3-143">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="dcca3-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="dcca3-144">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="dcca3-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="dcca3-145">*unit-testing-vb-nunit* ディレクトリで `dotnet test` をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="dcca3-146">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="dcca3-147">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="dcca3-148">成功します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="dcca3-149">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="dcca3-149">Adding more features</span></span>

<span data-ttu-id="dcca3-150">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="dcca3-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="dcca3-151">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="dcca3-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="dcca3-152">`<Test>` 属性を使用すると、これらの例を新しいテストとして追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="dcca3-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="dcca3-153">一連の類似のテストを記述できるようになる、他の xUnit 属性があります。</span><span class="sxs-lookup"><span data-stu-id="dcca3-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="dcca3-154">`<TestCase>` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="dcca3-155">`<TestCase>` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="dcca3-156">新しいテストを作成する代わりに、この 2 つの属性を活用して、最も小さな素数である 2 未満の複数の値をテストする一連のテストを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="dcca3-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="dcca3-157">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="dcca3-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="dcca3-158">すべてのテストを成功させるために、*PrimeServices.cs* ファイルで `Main` メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="dcca3-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="dcca3-159">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="dcca3-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="dcca3-160">[テストの最終版](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb)ができ、[ライブラリの完全な実装](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="dcca3-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="dcca3-161">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="dcca3-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="dcca3-162">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="dcca3-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="dcca3-163">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="dcca3-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
