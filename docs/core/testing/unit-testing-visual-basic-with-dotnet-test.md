---
title: dotnet テストと xUnit を使用した .NET Core での単体テスト Visual Basic
description: dotnet テストおよび xUnit を使用した Visual Basic ソリューションのサンプルを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core の単体テストの概念について説明します。
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: 67a8ea0520a0e38ff1f62cbecf82fe0b40969414
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875006"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="4db81-103">dotnet テストと xUnit を使用した Visual Basic .NET Core ライブラリでの単体テスト</span><span class="sxs-lookup"><span data-stu-id="4db81-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="4db81-104">このチュートリアルでは、単体テスト プロジェクトとライブラリ プロジェクトが含まれるソリューションを構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4db81-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="4db81-105">構築済みのソリューションを使用してチュートリアルに従う場合は、[サンプル コードを表示またはダウンロードしてください](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-using-dotnet-test/)。</span><span class="sxs-lookup"><span data-stu-id="4db81-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="4db81-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db81-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="4db81-107">ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="4db81-107">Create the solution</span></span>

<span data-ttu-id="4db81-108">このセクションでは、ソース プロジェクトとテスト プロジェクトを含むソリューションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4db81-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="4db81-109">完成したソリューションのディレクトリ構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4db81-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="4db81-110">テスト ソリューションを作成する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4db81-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="4db81-111">テスト ソリューションをワンステップで作成する手順については、[テスト ソリューションを作成するためのコマンド](#create-test-cmd)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db81-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="4db81-112">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4db81-112">Open a shell window.</span></span>
* <span data-ttu-id="4db81-113">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4db81-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="4db81-114">[`dotnet new sln`](../tools/dotnet-new.md) コマンドによって、新しいソリューションが *unit-testing-using-dotnet-test* ディレクトリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="4db81-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="4db81-115">ディレクトリを *unit-testing-using-dotnet-test* フォルダーに変更します。</span><span class="sxs-lookup"><span data-stu-id="4db81-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="4db81-116">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4db81-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="4db81-117">[`dotnet new classlib`](../tools/dotnet-new.md) コマンドによって、*PrimeService* フォルダーに新しいクラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4db81-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="4db81-118">この新しいクラス ライブラリに、テスト対象のコードが含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="4db81-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="4db81-119">*Class1.vb* の名前を *PrimeService.vb* に変更します。</span><span class="sxs-lookup"><span data-stu-id="4db81-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="4db81-120">*PrimeService.vb* のコードを、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4db81-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="4db81-121">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="4db81-121">The preceding code:</span></span>
  * <span data-ttu-id="4db81-122">実装されていないことを示すメッセージを含む <xref:System.NotImplementedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4db81-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="4db81-123">このチュートリアルの中で、後で更新します。</span><span class="sxs-lookup"><span data-stu-id="4db81-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="4db81-124">*unit-testing-using-dotnet-test* ディレクトリで、次のコマンドを実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="4db81-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="4db81-125">次のコマンドを実行して、*PrimeService.Tests* プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4db81-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="4db81-126">上記のコマンドにより、次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="4db81-126">The preceding command:</span></span>
  * <span data-ttu-id="4db81-127">*PrimeService.Tests* ディレクトリに *PrimeService.Tests* プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4db81-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="4db81-128">このテスト プロジェクトでは、テスト ライブラリとして [xUnit](https://xunit.net/) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4db81-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="4db81-129">プロジェクト ファイルに次の `<PackageReference />` 要素を追加することで、テスト ランナーを構成します。</span><span class="sxs-lookup"><span data-stu-id="4db81-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="4db81-130">"Microsoft.NET.Test.Sdk"</span><span class="sxs-lookup"><span data-stu-id="4db81-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="4db81-131">"xunit"</span><span class="sxs-lookup"><span data-stu-id="4db81-131">"xunit"</span></span>
    * <span data-ttu-id="4db81-132">"xunit.runner.visualstudio"</span><span class="sxs-lookup"><span data-stu-id="4db81-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="4db81-133">次のコマンドを実行して、ソリューション ファイルにテスト プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="4db81-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="4db81-134">*PrimeService.Tests* プロジェクトへの依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="4db81-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="4db81-135">ソリューションを作成するためのコマンド</span><span class="sxs-lookup"><span data-stu-id="4db81-135">Commands to create the solution</span></span>

<span data-ttu-id="4db81-136">このセクションでは、前のセクション内のすべてのコマンドの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="4db81-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="4db81-137">前のセクションの手順を完了している場合は、このセクションをスキップしてください。</span><span class="sxs-lookup"><span data-stu-id="4db81-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="4db81-138">次のコマンドによって、Windows コンピューター上にテスト ソリューションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4db81-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="4db81-139">macOS と Unix の場合は、`ren` コマンドを `ren` の OS バージョンに更新してファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="4db81-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="4db81-140">前のセクションの「*PrimeService.vb* 内のコードを次のコードに置き換える」の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="4db81-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="4db81-141">テストの作成</span><span class="sxs-lookup"><span data-stu-id="4db81-141">Create a test</span></span>

<span data-ttu-id="4db81-142">テスト駆動開発 (TDD) の一般的なアプローチは、ターゲット コードを実装する前にテストを記述することです。</span><span class="sxs-lookup"><span data-stu-id="4db81-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="4db81-143">このチュートリアルでは、この TDD アプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="4db81-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="4db81-144">`IsPrime` メソッドは呼び出し可能ですが、実装されていません。</span><span class="sxs-lookup"><span data-stu-id="4db81-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="4db81-145">`IsPrime` のテスト呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="4db81-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="4db81-146">TDD では、失敗することがわかっているテストを記述します。</span><span class="sxs-lookup"><span data-stu-id="4db81-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="4db81-147">テストに合格するように、ターゲット コードを更新します。</span><span class="sxs-lookup"><span data-stu-id="4db81-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="4db81-148">このアプローチを繰り返して、失敗するテストを記述した後、テストに合格するようにターゲット コードを更新します。</span><span class="sxs-lookup"><span data-stu-id="4db81-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="4db81-149">*PrimeService.Tests* プロジェクトを更新します。</span><span class="sxs-lookup"><span data-stu-id="4db81-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="4db81-150">*PrimeService.Tests/UnitTest1.vb* を削除します。</span><span class="sxs-lookup"><span data-stu-id="4db81-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="4db81-151">*PrimeService.Tests/PrimeService_IsPrimeShould.vb* ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4db81-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="4db81-152">*PrimeService_IsPrimeShould.vb* のコードを、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4db81-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="4db81-153">`[Fact]` 属性で、テスト ランナーによって実行されるテスト メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="4db81-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="4db81-154">*PrimeService.Tests* フォルダーから、`dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="4db81-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="4db81-155">[dotnet test](../tools/dotnet-test.md) コマンドで、両方のプロジェクトをビルドし、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4db81-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="4db81-156">xUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4db81-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="4db81-157">`dotnet test` で、単体テスト プロジェクトを使用するテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="4db81-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="4db81-158">`IsPrime` が実装されていないため、テストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="4db81-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="4db81-159">TDD アプローチでは、このテストに合格するのに十分なコードだけを記述します。</span><span class="sxs-lookup"><span data-stu-id="4db81-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="4db81-160">次のコードを使用して `IsPrime` を更新します。</span><span class="sxs-lookup"><span data-stu-id="4db81-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="4db81-161">`dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="4db81-161">Run `dotnet test`.</span></span> <span data-ttu-id="4db81-162">テストに合格します。</span><span class="sxs-lookup"><span data-stu-id="4db81-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="4db81-163">さらにテストを追加する</span><span class="sxs-lookup"><span data-stu-id="4db81-163">Add more tests</span></span>

<span data-ttu-id="4db81-164">0 と -1 のための素数テストを追加します。</span><span class="sxs-lookup"><span data-stu-id="4db81-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="4db81-165">前のテストをコピーし、次のコードを 0 と -1 を使用するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="4db81-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="4db81-166">パラメーターだけを変更するときにテスト コードをコピーすると、コードの重複が発生してテストが膨張します。</span><span class="sxs-lookup"><span data-stu-id="4db81-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="4db81-167">次の xUnit 属性を使用して、類似する一連のテストを記述できます。</span><span class="sxs-lookup"><span data-stu-id="4db81-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="4db81-168">`[Theory]` は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="4db81-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="4db81-169">`[InlineData]` 属性は、これらの入力の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="4db81-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="4db81-170">新しいテストを作成するのではなく、上記の xUnit 属性を適用することで、単一の理論を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4db81-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="4db81-171">以下のコードを</span><span class="sxs-lookup"><span data-stu-id="4db81-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="4db81-172">次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4db81-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="4db81-173">上記のコードでは、`[Theory]` と `[InlineData]` によって、2 未満のいくつかの値をテストできます。</span><span class="sxs-lookup"><span data-stu-id="4db81-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="4db81-174">2 は最小の素数です。</span><span class="sxs-lookup"><span data-stu-id="4db81-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="4db81-175">`dotnet test` を実行すると、2 のテストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="4db81-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="4db81-176">すべてのテストに合格するようにするには、次のコードで `IsPrime` メソッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="4db81-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="4db81-177">TDD アプローチに従って、失敗するテストをさらに追加した後、ターゲット コードを更新します。</span><span class="sxs-lookup"><span data-stu-id="4db81-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="4db81-178">[テストの最終版](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb)と、[ライブラリの完全な実装](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db81-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="4db81-179">完成した `IsPrime` メソッドは、素数性をテストするための効率的なアルゴリズムではありません。</span><span class="sxs-lookup"><span data-stu-id="4db81-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4db81-180">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="4db81-180">Additional resources</span></span>

- [<span data-ttu-id="4db81-181">xUnit.net の公式サイト</span><span class="sxs-lookup"><span data-stu-id="4db81-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="4db81-182">ASP.NET Core のコントローラー ロジックをテストする</span><span class="sxs-lookup"><span data-stu-id="4db81-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
