---
title: dotnet テストと NUnit を使用した .NET Core での単体テスト F#
description: dotnet テストおよび NUnit を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core における F# の単体テストの概念について説明します。
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 54513d3063ea0a3be8da73bcbd55962e839c6e2c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875058"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="041e0-103">dotnet テストと NUnit を使用した .NET Core での単体テスト F# ライブラリ</span><span class="sxs-lookup"><span data-stu-id="041e0-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="041e0-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="041e0-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="041e0-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp-nunit/)してください。</span><span class="sxs-lookup"><span data-stu-id="041e0-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="041e0-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="041e0-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="041e0-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="041e0-107">Prerequisites</span></span>

- <span data-ttu-id="041e0-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="041e0-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="041e0-109">ユーザーが選んだテキスト エディターまたはコード エディター。</span><span class="sxs-lookup"><span data-stu-id="041e0-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="041e0-110">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="041e0-110">Creating the source project</span></span>

<span data-ttu-id="041e0-111">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="041e0-111">Open a shell window.</span></span> <span data-ttu-id="041e0-112">ソリューションを保存するための *unit-testing-with-fsharp* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="041e0-113">この新しいディレクトリ内で、次のコマンドを実行して、クラス ライブラリとテスト プロジェクト用の新しいソリューション ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="041e0-114">次に、*MathService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="041e0-115">これまでのところ、ディレクトリとファイルの構造は次のアウトラインのようになっています。</span><span class="sxs-lookup"><span data-stu-id="041e0-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="041e0-116">*MathService* を現在のディレクトリとし、次のコマンドを実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="041e0-117">計算サービスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="041e0-118">*unit-testing-with-fsharp* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="041e0-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="041e0-119">次のコマンドを実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="041e0-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="041e0-120">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="041e0-120">Creating the test project</span></span>

<span data-ttu-id="041e0-121">次に、*MathService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="041e0-122">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="041e0-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="041e0-123">*MathService.Tests* ディレクトリを現在のディレクトリとし、次のコマンドを使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="041e0-124">これにより、テスト フレームワークとして NUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="041e0-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="041e0-125">生成されたテンプレートで、*MathServiceTests.fsproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="041e0-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="041e0-126">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="041e0-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="041e0-127">前の手順の `dotnet new` では、NUnit と NUnit のテスト アダプターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="041e0-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="041e0-128">ここで、プロジェクトに別の依存関係として `MathService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="041e0-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="041e0-129">`dotnet add reference` コマンドを使用する。</span><span class="sxs-lookup"><span data-stu-id="041e0-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="041e0-130">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="041e0-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="041e0-131">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="041e0-131">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

<span data-ttu-id="041e0-132">*unit-testing-with-fsharp* ディレクトリ内で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="041e0-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="041e0-133">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="041e0-133">Creating the first test</span></span>

<span data-ttu-id="041e0-134">失敗するテストを 1 つ作成してそれを合格させる、というプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="041e0-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="041e0-135">*UnitTest1.fs* を開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="041e0-135">Open *UnitTest1.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="041e0-136">`[<TestFixture>]` 属性は、テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="041e0-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="041e0-137">`[<Test>]` 属性は、テスト ランナーによって実行されるテスト メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="041e0-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="041e0-138">*unit-testing-with-fsharp* ディレクトリで `dotnet test` を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="041e0-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="041e0-139">NUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="041e0-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="041e0-140">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="041e0-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="041e0-141">この 2 つのテストは、最も基本的な成功テストと失敗テストです。</span><span class="sxs-lookup"><span data-stu-id="041e0-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="041e0-142">`My test` は成功し、`Fail every time` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="041e0-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="041e0-143">今度は `squaresOfOdds` メソッドのテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="041e0-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="041e0-144">`squaresOfOdds` メソッドは、入力シーケンスに含まれるすべての奇数の整数値を 2 乗した値のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="041e0-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="041e0-145">これらの関数をすべて一度に書き込むのではなく、機能を検証するテストを繰り返し作成することができます。</span><span class="sxs-lookup"><span data-stu-id="041e0-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="041e0-146">各テストを成功させることで、メソッドに必要な機能を作成することになります。</span><span class="sxs-lookup"><span data-stu-id="041e0-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="041e0-147">最も簡単に記述できるテストは、すべて偶数である数字を `squaresOfOdds` に渡して呼び出すことです。このテストの結果は、整数の空のシーケンスになります。</span><span class="sxs-lookup"><span data-stu-id="041e0-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="041e0-148">次に示すのがそのテストです。</span><span class="sxs-lookup"><span data-stu-id="041e0-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="041e0-149">`expected` シーケンスがリストに変換されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="041e0-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="041e0-150">NUnit ライブラリは、標準的な .NET 型の多くに依存しています。</span><span class="sxs-lookup"><span data-stu-id="041e0-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="041e0-151">この依存関係は、お使いのパブリック インターフェイスおよび期待される結果が、<xref:System.Collections.IEnumerable> でなく <xref:System.Collections.ICollection> をサポートしていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="041e0-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="041e0-152">テストを実行すると、失敗することがわかります。</span><span class="sxs-lookup"><span data-stu-id="041e0-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="041e0-153">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="041e0-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="041e0-154">このテストに合格するには、動作する MathService プロジェクトの *Library.fs* クラスに、ごく簡単なコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="041e0-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="041e0-155">*unit-testing-with-fsharp* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="041e0-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="041e0-156">`dotnet test` コマンドは `MathService` プロジェクトのビルドを実行してから、`MathService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="041e0-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="041e0-157">両方のプロジェクトをビルドすると、このテストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="041e0-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="041e0-158">今回は 2 つのテストが合格します。</span><span class="sxs-lookup"><span data-stu-id="041e0-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="041e0-159">要件の完成</span><span class="sxs-lookup"><span data-stu-id="041e0-159">Completing the requirements</span></span>

<span data-ttu-id="041e0-160">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="041e0-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="041e0-161">次の単純な例は、奇数は `1` のみが含まれるシーケンスで機能します。</span><span class="sxs-lookup"><span data-stu-id="041e0-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="041e0-162">数値の 1 は簡単です。なぜなら 1 の 2 乗は 1 になるためです。</span><span class="sxs-lookup"><span data-stu-id="041e0-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="041e0-163">次のテストを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="041e0-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="041e0-164">`dotnet test` を実行すると、新しいテストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="041e0-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="041e0-165">新しいテストに対応するには `squaresOfOdds` メソッドを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="041e0-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="041e0-166">このテストを成功させるには、フィルター処理でシーケンスからすべての偶数を除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="041e0-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="041e0-167">小さなフィルター関数を記述し、`Seq.filter` を使用することで実現できます。</span><span class="sxs-lookup"><span data-stu-id="041e0-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="041e0-168">`Seq.toList` を呼び出していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="041e0-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="041e0-169">これにより、<xref:System.Collections.ICollection> インターフェイスを実装するリストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="041e0-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="041e0-170">実施する手順がもう一つあります。各奇数を 2 乗します。</span><span class="sxs-lookup"><span data-stu-id="041e0-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="041e0-171">テストを新たに記述するところから始めます。</span><span class="sxs-lookup"><span data-stu-id="041e0-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="041e0-172">テストを修正するには、フィルター処理したシーケンスをパイプでつなぎ、各奇数の 2 乗を計算するマップ操作をします。</span><span class="sxs-lookup"><span data-stu-id="041e0-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="041e0-173">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="041e0-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="041e0-174">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="041e0-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="041e0-175">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="041e0-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="041e0-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="041e0-176">See also</span></span>

- [<span data-ttu-id="041e0-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="041e0-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="041e0-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="041e0-178">dotnet test</span></span>](../tools/dotnet-test.md)
