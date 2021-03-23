---
title: dotnet テストと MSTest を使用した .NET Core での単体テスト Visual Basic
description: MSTest を使用した Visual Basic ソリューションのサンプルを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core の単体テストの概念について説明します。
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9ab85b2e688f5f31d0981fbee618212ac6ea5a19
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873498"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="24b4a-103">dotnet テストと MSTest を使用した .NET Core ライブラリでの単体テスト Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b4a-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="24b4a-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="24b4a-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-mstest/)してください。</span><span class="sxs-lookup"><span data-stu-id="24b4a-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="24b4a-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24b4a-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="24b4a-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="24b4a-107">Creating the source project</span></span>

<span data-ttu-id="24b4a-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-108">Open a shell window.</span></span> <span data-ttu-id="24b4a-109">ソリューションを保存するための *unit-testing-vb-mstest* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="24b4a-110">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、ソリューションを新たに作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="24b4a-111">こうすることで、クラス ライブラリと単体テスト プロジェクトの両方を管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="24b4a-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="24b4a-112">ソリューションのディレクトリ内で、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="24b4a-113">現時点のディレクトリとファイルの構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="24b4a-113">You have the following directory and file structure thus far:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="24b4a-114">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib -lang VB`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="24b4a-115">*Class1.VB* の名前を *PrimeService.VB* に変更します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="24b4a-116">`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="24b4a-117">*unit-testing-vb-using-mstest* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="24b4a-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="24b4a-118">[`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="24b4a-119">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="24b4a-119">Creating the test project</span></span>

<span data-ttu-id="24b4a-120">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="24b4a-121">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="24b4a-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="24b4a-122">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new mstest -lang VB`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="24b4a-123">このコマンドによって、テスト ライブラリとして MSTest を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="24b4a-124">生成されたテンプレートで、*PrimeServiceTests.vbproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="24b4a-125">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="24b4a-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="24b4a-126">前の手順の `dotnet new` によって、MSTest と MSTest ランナーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="24b4a-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="24b4a-127">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="24b4a-128">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="24b4a-129">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="24b4a-130">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="24b4a-130">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="24b4a-131">*unit-testing-vb-mstest* ディレクトリで [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="24b4a-132">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="24b4a-132">Creating the first test</span></span>

<span data-ttu-id="24b4a-133">失敗するテストを 1 つ作成してそれを合格させる、というプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="24b4a-134">*PrimeService.Tests* ディレクトリから *UnitTest1.vb* を削除し、*PrimeService_IsPrimeShould.VB* という名前の新しい Visual Basic ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="24b4a-135">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="24b4a-136">`<TestClass>` 属性は、テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="24b4a-137">`<TestMethod>` 属性は、テスト ランナーによって実行されるメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="24b4a-138">*unit-testing-vb-mstest* で [`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="24b4a-139">MSTest テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="24b4a-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="24b4a-140">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="24b4a-141">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-141">Your test fails.</span></span> <span data-ttu-id="24b4a-142">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="24b4a-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="24b4a-143">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="24b4a-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="24b4a-144">*unit-testing-vb-mstest* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="24b4a-145">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="24b4a-146">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="24b4a-147">成功します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="24b4a-148">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="24b4a-148">Adding more features</span></span>

<span data-ttu-id="24b4a-149">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="24b4a-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="24b4a-150">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="24b4a-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="24b4a-151">`<TestMethod>` 属性を使用すると、これらの例を新しいテストとして追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="24b4a-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="24b4a-152">一連の類似のテストを記述できるようになる、他の MSTest 属性があります。</span><span class="sxs-lookup"><span data-stu-id="24b4a-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="24b4a-153">`<DataTestMethod>` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="24b4a-154">`<DataRow>` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="24b4a-155">新しいテストを作成するのではなく、この 2 つの属性を適用することで 1 つの理論を作成できます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="24b4a-156">その理論とは、複数の 2 未満の値を調べて、もっとも小さい素数を特定するという手法です。</span><span class="sxs-lookup"><span data-stu-id="24b4a-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-mstest/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="24b4a-157">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="24b4a-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="24b4a-158">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="24b4a-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="24b4a-159">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="24b4a-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="24b4a-160">[テストの最終版](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb)ができ、[ライブラリの完全な実装](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="24b4a-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="24b4a-161">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="24b4a-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="24b4a-162">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="24b4a-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="24b4a-163">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="24b4a-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
