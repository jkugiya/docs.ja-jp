---
title: MSTest と .NET Core による単体テスト C#
description: dotnet テストおよび MSTest を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、C# および .NET Core の単体テストの概念について説明します。
author: ncarandini
ms.author: wiwagn
ms.date: 10/21/2020
ms.openlocfilehash: e2c3326778d7fc1a492062cff4f2d2ad4a61ac18
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874889"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="05d43-103">MSTest と .NET Core による単体テスト C#</span><span class="sxs-lookup"><span data-stu-id="05d43-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="05d43-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="05d43-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="05d43-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/)してください。</span><span class="sxs-lookup"><span data-stu-id="05d43-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="05d43-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05d43-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a><span data-ttu-id="05d43-107">ソース プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="05d43-107">Create the source project</span></span>

<span data-ttu-id="05d43-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="05d43-108">Open a shell window.</span></span> <span data-ttu-id="05d43-109">ソリューションを保存するための *unit-testing-using-mstest* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="05d43-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="05d43-110">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、クラス ライブラリとテスト プロジェクト用の新しいソリューション ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="05d43-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="05d43-111">次に、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="05d43-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="05d43-112">現時点のディレクトリとファイルの構造は次のアウトラインのようになっています。</span><span class="sxs-lookup"><span data-stu-id="05d43-112">The following outline shows the directory and file structure thus far:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="05d43-113">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="05d43-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="05d43-114">*Class1.cs* の名前を *PrimeService.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="05d43-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="05d43-115">`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="05d43-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="05d43-116">*unit-testing-using-mstest* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="05d43-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="05d43-117">[`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="05d43-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="create-the-test-project"></a><span data-ttu-id="05d43-118">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="05d43-118">Create the test project</span></span>

<span data-ttu-id="05d43-119">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="05d43-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="05d43-120">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="05d43-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="05d43-121">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new mstest`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="05d43-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="05d43-122">dotnet new コマンドによって、テスト ライブラリとして MSTest を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="05d43-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="05d43-123">生成されたテンプレートで、*PrimeServiceTests.csproj* ファイルのテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="05d43-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="05d43-124">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="05d43-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="05d43-125">前の手順の `dotnet new` により、MSTest SDK、MSTest テスト フレームワーク、MSTest ランナーが追加されました。</span><span class="sxs-lookup"><span data-stu-id="05d43-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="05d43-126">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="05d43-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="05d43-127">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="05d43-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="05d43-128">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="05d43-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="05d43-129">ソリューションの最終的なレイアウトは次のアウトラインのようになります。</span><span class="sxs-lookup"><span data-stu-id="05d43-129">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="05d43-130">*unit-testing-using-mstest* ディレクトリで [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="05d43-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span>

## <a name="create-the-first-test"></a><span data-ttu-id="05d43-131">最初のテストを作成する</span><span class="sxs-lookup"><span data-stu-id="05d43-131">Create the first test</span></span>

<span data-ttu-id="05d43-132">失敗するテストを 1 つ作成してそれを合格させる、というプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="05d43-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="05d43-133">*PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。コンテンツは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="05d43-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        [TestMethod]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var primeService = new PrimeService();
            bool result = primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="05d43-134">[TestClass 属性](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)は、単体テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="05d43-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="05d43-135">[TestMethod 属性](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)は、メソッドがテスト メソッドであることを示します。</span><span class="sxs-lookup"><span data-stu-id="05d43-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span>

<span data-ttu-id="05d43-136">このファイルを保存し、[`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドしてから、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="05d43-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="05d43-137">MSTest テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="05d43-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="05d43-138">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="05d43-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="05d43-139">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="05d43-139">Your test fails.</span></span> <span data-ttu-id="05d43-140">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="05d43-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="05d43-141">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="05d43-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="05d43-142">*unit-testing-using-mstest* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="05d43-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="05d43-143">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05d43-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="05d43-144">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="05d43-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="05d43-145">成功します。</span><span class="sxs-lookup"><span data-stu-id="05d43-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="05d43-146">その他の機能を追加する</span><span class="sxs-lookup"><span data-stu-id="05d43-146">Add more features</span></span>

<span data-ttu-id="05d43-147">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="05d43-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="05d43-148">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="05d43-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="05d43-149">[TestMethod 属性](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)を使用すると新しいテストを追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="05d43-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="05d43-150">一連の類似のテストを記述できるようになる、他の MSTest 属性があります。</span><span class="sxs-lookup"><span data-stu-id="05d43-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="05d43-151">[DataTestMethod 属性](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute)は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="05d43-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="05d43-152">[DataRow 属性](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute)を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="05d43-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="05d43-153">新しいテストを作成するのではなく、この 2 つの属性を適用することで 1 つのデータ駆動テストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="05d43-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="05d43-154">そのデータ駆動テストとは、複数の 2 未満の値を調べて、最も小さい素数を特定するという手法です。</span><span class="sxs-lookup"><span data-stu-id="05d43-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="05d43-155">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="05d43-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="05d43-156">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="05d43-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="05d43-157">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="05d43-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="05d43-158">[テストの最終版](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs)ができ、[ライブラリの完全な実装](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="05d43-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="05d43-159">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="05d43-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="05d43-160">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="05d43-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="05d43-161">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="05d43-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="05d43-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="05d43-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="05d43-163">単体テストでの MSTest フレームワークの使用</span><span class="sxs-lookup"><span data-stu-id="05d43-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="05d43-164">MSTest V2 テスト フレームワーク ドキュメント</span><span class="sxs-lookup"><span data-stu-id="05d43-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
